# Implémenter un module en plugin xcore-doctype

Un dossier de ce dépôt (`stock/`, `accounts/`…) ne fait rien seul : il décrit la structure. Pour obtenir une application qui tourne, chaque module devient **un plugin xcore** qui charge ses définitions, déclare ses grants à l'authentification, son espace de travail — et porte en code la logique métier que le YAML ne contient pas. Ce guide décrit la marche à suivre ; la stratégie d'ensemble (un plugin par module, ordre P0–P5) est dans `process/plan-erp.md` du dépôt moteur.

## Le principe : un plugin par module

- **le `module:` de chaque DocType doit valoir le nom du plugin** (ex. plugin `stock` → `module: stock`) : c'est l'espace de nom des grants, un plugin ne peut pas écrire dans celui d'un autre ;
- le plugin **charge ses YAML** par `doctype_registry.load_dir` et son espace par `load_workspaces` ;
- le plugin **déclare les grants** exigés par ses DocTypes à l'authentification (`rbac.declare`, une seule fois, via le service `doctype_grants`) ;
- la **logique métier** (écritures comptables, mouvements de stock, invariants) vit dans des **hooks** enregistrés par le plugin ;
- les modules se référencent en **cycle** → chargement en mode *pairs* (voir plus bas).

## Gabarit minimal (module « YAML seul »)

La plupart des modules commencent comme le plugin `hr` des tests du moteur : quelques lignes de Python, tout le reste en YAML.

```
mon-module/
├── plugin.yaml
├── doctypes/            ← un copie du dossier de ce dépôt (ex. stock/)
├── workspaces/stock.yaml
└── src/
    └── main.py
```

```yaml title="plugin.yaml"
name: stock                      # = le `module:` des DocTypes chargés
version: 0.1.0
author: auteur@example.com
description: "Plugin du module Stock : articles, entrepôts, mouvements, registre."
framework_version: ">=2.9"
execution_mode: trusted          # requis : les hooks transactionnels sont du code de confiance
entry_point: src/main.py
requires: [xcore-doctype, auth]   # + les modules cités (voir Dépendances)
```

```python title="src/main.py"
"""Plugin propriétaire du module `stock`."""
from pathlib import Path

from xcore.sdk import AutoDispatchMixin, TrustedBase

DOCTYPES = Path(__file__).resolve().parent.parent / "doctypes"
AUTH = "auth"  # le `name:` du plugin d'authentification


class Plugin(AutoDispatchMixin, TrustedBase):
    async def on_load(self) -> None:
        me = self.ctx.name
        registry = self.get_service("doctype_registry")
        registry.load_dir(me, DOCTYPES)                                # les définitions
        registry.load_workspaces(me, DOCTYPES.parent / "workspaces")   # APRÈS les DocTypes
        grants = self.get_service("doctype_grants").for_plugin(me)    # les grants du YAML
        await self.ctx.events.emit("rbac.declare", {"plugin": me, "grants": grants}, source=me)

    async def on_unload(self) -> None:
        self.get_service("doctype_registry").unregister_owner(self.ctx.name)
```

Points de vigilance :

- `load_workspaces` se fait **après** `load_dir` (les raccourcis visent des DocTypes chargés) ;
- la déclaration `rbac.declare` part **une seule fois** par plugin, avec **tous** les grants du module — l'authentification désactive les grants manquants de la liste qu'elle reçoit ;
- sans bloc `permissions` dans le YAML, les grants suivent la **convention** `stock:<doctype>:read|write|delete` (+ `submit`/`cancel` sur les pièces) : rien à écrire ;
- les 25 DocTypes du jeu qui **ferment** leurs écritures (`GL Entry`, `Stock Ledger Entry`…) sont écrits par les hooks du plugin, jamais par un utilisateur.

## Le chargement en mode pairs

Les modules se citent en cycle (`setup` ↔ `accounts` ↔ `stock`…). Le paramètre `peers=True` l'absorbe :

```python
registry.load_dir(me, DOCTYPES, peers=True)
```

- un lien vers un module **pas encore chargé** ne fait pas échouer le chargement : le DocType devient *incomplet* (lecture seule, écritures refusées 503 en nommant le pair manquant) ;
- quand le pair arrive, le DocType se complète automatiquement — **n'importe quel ordre de démarrage des plugins fonctionne** ;
- les cibles de liens restent tout de même **validées** : une cible inconnue de tous les modules chargés est une erreur de chargement, pas une attente.

Le `requires:` du `plugin.yaml` liste les modules dont les DocTypes sont les cibles des liens (matrice complète en [Dépendances](dependances.md)) :

```yaml
requires: [xcore-doctype, auth, setup, accounts]   # stock cite setup, accounts, selling…
```

## La logique métier : les hooks

Le jeu de définitions ne porte **aucune règle d'écriture** — c'est la règle du projet. Le plugin enregistre des hooks par **nom**, jamais par chemin d'import (décision D16 du moteur) :

```python
async def stock_entry_on_submit(event):        # POST/PUT du registre à la soumission
    tx = event.tx                              # écritures DANS la transaction
    for line in event.doc["items"]:
        await tx.create("Stock Ledger Entry", {
            "voucher_type": event.doctype, "voucher_no": event.name,
            "item_code": line["item_code"], "warehouse": line["warehouse"],
            "qty": line["qty"], ...})
    # ... maintien du solde, refus du stock négatif : raise DocumentValidationError
```

```python
# dans on_load, AVANT load_dir (un hook manquant refuse les sauvegardes, 503)
self.get_service("doctype_hooks").register("stock.entry_submit", stock_entry_on_submit, owner=me)
```

Les onze événements disponibles : `before_insert`, `after_insert`, `validate`, `before_save`, `after_save`, `on_trash`, `after_delete`, `on_submit`, `before_cancel`, `on_cancel`, `on_update_after_submit` (les hooks `action:` sont sandboxés et hors transaction ; les hooks transactionnels exigent `execution_mode: trusted`).

À l'intérieur d'un hook, `event.tx` est la **seule** porte d'écriture : `get`, `create`, `ensure`, `update`, `find`, `sum` — validés et historisés comme toute écriture, dans la même transaction que la pièce.

### Les pièces qui cite­nt leur source : `cancel_ignores`

`GL Entry`, `Stock Ledger Entry`… sont des pièces **soumises** qui citent leur pièce d'origine (`voucher_type`/`voucher_no` en `DynamicLink`). Or le moteur refuse d'annuler une pièce encore citée par une pièce soumise — c'est le garde-fou M2. Chaque registre déclare donc dans son YAML :

```yaml
cancel_ignores: [Stock Ledger Entry]   # mes propres écritures, que mon on_cancel inverse
```

…ce que ce jeu ne déclare pas encore (il vit dans le plugin) : **à l'implémentation, reprendre les listes de `process/plan-erp.md`** (ledger stock → `Stock Ledger Entry` ; comptabilité → `GL Entry`, `Payment Ledger Entry`, …).

## Traductions

Les libellés sont en anglais dans les YAML ; le catalogue français vit dans `translations/fr.yaml` du plugin (clé = texte source, traductions par contexte) :

```python
registry.load_translations(me, DOCTYPES.parent / "translations")
```

Un catalogue `fr.yaml` couvrant les cinq premiers modules (T17 du plan ERP) existe dans le dépôt moteur ; l'adapter par module. Ne jamais traduire les **valeurs** (options de `Select`, états de workflow) : ce sont des données.

## Validation

Chaque module se vérifie en ligne de commande, depuis le dépôt moteur :

```bash
# les DocTypes du plugin, avec les dossiers de ses pairs en --with
xcore-doctype check doctypes/stock --owner stock \
    --with doctypes/setup --with doctypes/accounts   # … tous les modules cités
```

`--owner` valide en plus `workspaces/` (raccourcis vers des DocTypes chargés) et les blocs de contribution. En test, le dépôt moteur charge le jeu complet en mode pairs et le compare à un chargement unique (`test_peer_modules.py`) : **ne pas charger ce sous-module et une copie dans le même hôte** (doublons de définitions).

## Ordre de déploiement (P0–P5)

Le plan ERP du dépôt moteur recommande d'implémenter les modules dans cet ordre — chaque étape s'appuie sur la précédente :

| Étape | Modules | Apporte |
|---|---|---|
| P0 | `setup` | la base commune : sociétés, référentiels partagés |
| P1 | `accounts` | comptabilité (SYSCOHADA), journaux, rapprochement |
| P2 | `stock` | articles, entrepôts, registre, valorisation au coût moyen pondéré |
| P3 | `selling` + `buying` | le cycle commercial (devis, commandes, factures, fournisseurs) |
| P4 | `hr` + `payroll` | personnel, congés, notes de frais, paie |
| P5 | `manufacturing`, `projects`, `assets`, … | le reste du graphe, par besoin |

Les quatre changements moteur qui conditionnent ce plan (lecture transactionnelle `tx.find`/`tx.sum`, garde M2 avec `cancel_ignores`, `currency_from`, service `doctype_writer`) sont implémentés dans le dépôt moteur — ce sous-module n'a rien à faire pour eux.
