# Architecture des définitions

Chaque fichier YAML du dépôt est **une définition de DocType** au sens du moteur [xcore-doctype](https://github.com/traoreera/doctype) : une déclaration purement descriptive qui produit le stockage, l'API CRUD, les permissions, la validation et l'interface du Desk. Cette page décrit le contrat tel qu'il est utilisé dans ce jeu ; le contrat complet (et les décisions de conception D1–D22) vit dans le dépôt moteur (`process/doctype.md`).

## Anatomie d'une définition

```yaml
schema_version: 1
name: Delivery Note                       # identifiant unique du DocType
label: Bon de livraison                   # libellé (traduit via le catalogue)
module: stock                             # = le plugin propriétaire, espace de grants
icon: warehouse                           # nom PrimeIcons pour le Desk
title_field: customer                     # colonne lisible des listes
istable: false                            # true = table enfant sans routes propres
single: false                             # true = document unique (paramètres)
submittable: true                         # cycle brouillon → soumis → annulé
naming:
  series: "DN-{YYYY}-{#####}"             # numérotation serveur, sans trou
track_changes: true                       # historique des versions
workflow:                                 # automate d'état (optionnel)
  states: [...]
  transitions: [...]
views:                                    # vues supplémentaires du Desk
  calendar: {date_field: posting_date}
fields: [...]
permissions:                              # facultatif : remplace la convention
  read: ["stock:delivery_note:read"]
  write: ["stock:delivery_note:write"]
  create: ["stock:delivery_note:write"]
  delete: ["stock:delivery_note:delete"]
```

Les clés non implémentées par le moteur sont **refusées au chargement** (schéma `extra="forbid"`) : une définition ne déclare que ce que le moteur garantit.

## Nature des DocTypes du jeu

| Nature | Clé | Nombre | Rôle |
|---|---|---|---|
| Pièce | `submittable: true` | 136 | Transaction figée à la soumission (`docstatus` 0/1/2), amendable, historisée |
| Données de base | — | 252 | Référentiels (Customer, Item, Employee…) |
| Table enfant | `istable: true` | 293 | Lignes d'une pièce, stockées dans le parent, sans routes ni droits propres |
| Document unique | `single: true` | 23 | Paramètres d'une organisation (`Company Settings`, `Stock Settings`…) |
| Virtuel | `source:` | 0 | Aucun dans ce jeu |

Une pièce **soumise** est figée : seuls ses champs `allow_on_submit` restent modifiables ; l'annulation déclenche les hooks `on_cancel` du plugin propriétaire ; un amendement copie une pièce annulée en brouillon (`-1` suffixé).

## Types de champs

23 types de champs sont utilisés dans le jeu :

`Link` (2 463) · `Text` (1 318) · `Boolean` (1 093) · `Currency` (911) · `Select` (554) · `Date` (455) · `Table` (399) · `Number` (388) · `LongText` (286) · `Decimal` (273) · `Int` (214) · `TextEditor` (183) · `DynamicLink` (85) · `Datetime` (83) · `Percent` (80) · `Time` (49) · `Code` (32) · `Image` (19) · `Attach` (17) · `JSON` (11) · `Rating` (8) · `Color` (4) · `Duration` (1)

Points notables :

- **`Link` est le type dominant** (15 % des champs) : les liens entre DocTypes sont vérifiés à l'écriture (cible existante et lisible), protègent la suppression (`document_in_use`) et tissent le graphe de [dépendances](dependances.md).
- **`DynamicLink`** (85) : la cible est nommée par un champ frère (`options` = nom du champ `Select` qui porte le nom du DocType) — typiquement `voucher_type`/`voucher_no` des journaux comptables et de stock.
- **`Currency` et `Decimal`** (1 184 combinés) : stockés en chaîne canonique à échelle exacte, jamais en flottant. `Currency` est l'égal de `Decimal` avec en plus une devise d'affichage.
- **`Table`** : pointe vers un DocType enfant (`istable`), ≤ 500 lignes par document, validées avec le modèle strict de l'enfant.

## Attributs de champs

| Attribut | Usage | Nombre |
|---|---|---|
| `required` | Champ obligatoire | omniprésent |
| `in_list_view` | Colonne de la liste par défaut | omniprésent |
| `read_only`, `hidden` | Édition/masquage côté Desk | courant |
| `fetch_from` | Recopie `lien.champ` depuis la cible à chaque écriture, écrase la valeur cliente | 123 |
| `compute` | Calcul déclaratif à vocabulaire fermé (`a * b`, `a + b - c`, `sum(table.champ)`) | 44 |
| `currency_from` | Devise d'affichage lue d'un champ, d'un saut de lien (`company.default_currency`) ou du parent (`parent_`) | 860 |
| `depends_on` | Condition de visibilité (langage `expr`, évalué serveur et navigateur) | 100 |
| `mandatory_depends_on` | Obligatoire si condition | 25 |
| `default` (`today`, `now`, littéral) | Pré-remplissage à la création | courant |
| `unique` | Unicité par organisation (clé primaire dédiée `xdt_unique`) | rare dans ce jeu |
| `set_only_once` | Posable seulement à la création | rare |
| `allow_on_submit` | Modifiable après soumission | pièces comptables notamment |
| `target_status` | Contraint le `docstatus` de la cible d'un lien | liens vers pièces |

## Numérotation

Deux mécanismes, servis par le moteur sans trou ni doublon :

- **Série** (`naming.series`, 137 DocTypes) : `SI-{YYYY}-{#####}` → `SI-2026-00001`. Le compteur est incrémenté dans la transaction du document ; les numéros ne sont jamais réutilisés. 137 préfixes distincts : `SI-` (factures de vente), `PI-` (factures d'achat), `DN-` (bons de livraison), `PUOR-` (ordres d'achat), `MAT-` (demandes), `MS-`/`MV-` (mouvements de stock), `JV-` (écritures de journal), `PR-` (reçus de paiement), `ACC-` (demandes de congés)…
- **Champ** (`naming.field`, 8 DocTypes) : le nom du document est la valeur d'un champ — `Pays.code`, `Devise.devise_code`, `UOM.uom_name`… Le Desk les propose en « création rapide » et un `Link` vers eux affiche ce titre.

Les tables enfants n'ont pas de nom propre : elles vivent dans le JSON du parent.

## Workflows

Quatre DocTypes déclarent un automate `workflow:` (états + transitions, chaque état imposant un `docstatus`) :

Les quatre automates partagent le même circuit d'approbation :

| DocType | Module | Circuit |
|---|---|---|
| `Purchase Order` | buying | Brouillon → Soumettre → À approuver → Approuver/Refuser/Reprendre → Approuvée/Refusée → Annuler |
| `Material Request` | stock | idem |
| `Expense Claim` | hr | idem |
| `Leave Application` | hr | idem |

(`stock/delivery_note.yaml` et `selling/sales_order.yaml` portent une clé `workflow:` vide, sans effet.)

Une transition est ouverte par un **grant** dédié (`<module>:<doctype>:workflow_<action>`), peut être réservée aux non-auteurs (`not_owner`) et conditionnée par une expression. Un état qui soumet ou annule la pièce déclenche les hooks `on_submit`/`on_cancel` du plugin.

## Vues Desk

Outre la liste et la fiche, un DocType peut déclarer des vues supplémentaires :

| Vue | Nombre | Exemples |
|---|---|---|
| `calendar` | 117 | pièces datées (`date_field`) : factures, congés, entretiens |
| `gantt` | 47 | `start`/`end` : projets, ordres de fabrication |
| `kanban` | 24 | pilotées par un champ `Select` (`field`) |
| `tree` | 15 | hiérarchies (`parent`) : comptes, centres de coût, territoires |

Un tableau de bord récapitulatif est généré pour chaque DocType ; les espaces de travail assemblent cartes, graphiques et raccourcis (voir les pages [modules](modules/accounts.md)).

## Permissions

Par défaut, **aucun bloc `permissions`** n'est déclaré : les grants suivent la convention du moteur, dérivée de `module` + nom du DocType :

- lecture → `<module>:<doctype>:read` ;
- écriture **et** création → `<module>:<doctype>:write` ;
- suppression → `<module>:<doctype>:delete` ;
- soumission/annulation → `<module>:<doctype>:submit` / `cancel` (pièces seulement).

25 DocTypes du jeu (journaux comptables, registres de stock, principalement) déclarent un bloc explicite — le plus souvent pour **fermer l'écriture humaine** (`write: []`, `create: []`, `delete: []`) : ces tables sont écrites par les hooks des plugins, jamais à la main. C'est le mécanisme utilisé pour `GL Entry`, `Stock Ledger Entry`, `Payment Ledger Entry`… voir les pages [Comptabilité](modules/accounts.md) et [Stock](modules/stock.md).

## Ce que le YAML ne contient pas

Les définitions sont **purement descriptives** ; en particulier :

- **aucun hook** (`validate`, `on_submit`…) n'est déclaré dans ce jeu — 0 sur 704 : la logique métier (double écriture comptable, coût moyen pondéré, soldes de stock…) vit dans les plugins, un par module ;
- pas de requêtes SQL, de rapports imprimables ou de scripts client ;
- pas de matrice de rôles : les grants sont conventionnels ou déclarés dans le `plugin.yaml` du propriétaire.

La marche à suivre pour écrire le plugin qui porte un module est décrite dans [Implémenter un module](integration.md).
