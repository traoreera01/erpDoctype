# ERP DocTypes pour xcore-doctype

Ce dépôt contient le jeu de définitions DocType ERP utilisé par le projet [xcore-doctype](https://github.com/traoreera/doctype). Il s'agit de fichiers YAML déclaratifs, organisés par module métier ; ce dépôt ne contient ni le moteur d'exécution ni les plugins métier qui mettent en œuvre les règles comptables et opérationnelles.

## Contenu

- 704 définitions réparties dans 22 modules (`accounts/`, `stock/`, `selling/`, etc.) au moment de l'extraction initiale.
- Schémas adaptés au contrat xcore-doctype, avec des types numériques exacts, des conditions et calculs pris en charge par le moteur, et des relations entre modules.
- Ces définitions sont des données de configuration, pas une application ERP complète. Les hooks métier, écritures comptables et traitements transactionnels résident dans les plugins de l'ERP.

La documentation complète du jeu est dans [`docs/`](docs/index.md), au format MkDocs :

- [`docs/index.md`](docs/index.md) — vue d'ensemble et chiffres clés ;
- [`docs/architecture.md`](docs/architecture.md) — le contrat de schéma tel qu'utilisé par le jeu (types de champs, numérotation, workflows, vues, permissions) ;
- [`docs/dependances.md`](docs/dependances.md) — matrice complète des dépendances entre modules dans les deux sens ;
- [`docs/integration.md`](docs/integration.md) — implémenter chaque module en plugin xcore (gabarit, grants, hooks, traductions, validation) ;
- [`docs/modules/`](docs/modules/) — 22 pages, une par module ;
- [`docs/reference/`](docs/reference/) — la référence de chaque champ de chaque DocType, **générée** par [`docs/scripts/gen_reference.py`](docs/scripts/gen_reference.py).

La documentation de migration et des transformations est dans [`docs/erp-doctypes.md`](docs/erp-doctypes.md), conservée depuis le dépôt moteur. Le contrat du schéma et les versions du moteur sont documentés dans le [guide xcore-doctype](https://github.com/traoreera/doctype/blob/master/docs/guide.md).

Pour construire ce site localement : `pip install mkdocs && mkdocs build -f mkdocs.cnf` (ou `mkdocs serve -f mkdocs.cnf`) à la racine du dépôt. La configuration s'appelle `mkdocs.cnf` — et pas `mkdocs.yml` — et le site se construit **hors** de l'arbre (`.doctypes-site/` à côté du dépôt) : le moteur lit tout fichier `.yaml`/`.yml`/`.json` de l'arbre comme une définition de DocType, ni la configuration ni le build ne doivent donc vivre dedans.

## Utilisation dans un plugin xcore

Copier ou référencer le ou les dossiers de modules dans le répertoire `doctypes/` du plugin correspondant. Chaque plugin propriétaire doit charger ses définitions sous son propre nom, publier les grants du namespace et déclarer les dépendances entre modules. Les modules qui se référencent mutuellement doivent utiliser le mécanisme de chargement des modules pairs (`peers=True`) décrit dans le guide du moteur.

Le dépôt moteur référence ici un commit précis comme sous-module Git. Pour obtenir les définitions dans un clone de ce dépôt, initialiser les sous-modules :

```sh
git submodule update --init --recursive
```

Pour valider des définitions avec le moteur, utiliser la commande `xcore-doctype check` documentée par le projet moteur ; la validation doit être faite avec la version de moteur ciblée par le plugin consommateur.

## Développement

- Garder les fichiers organisés par module, avec les noms de fichier en `snake_case` correspondant au DocType.
- Modifier les schémas de façon déclarative ; ne pas y ajouter de code Python ni de logique métier.
- Tester toute modification avec la commande de validation du moteur et les invariants applicables.
- Signaler dans la documentation les changements incompatibles du schéma et la version minimale requise de xcore-doctype.

## Provenance et licence

Le jeu a été migré à partir de définitions ERPNext puis adapté pour le schéma xcore-doctype. Voir [`docs/erp-doctypes.md`](docs/erp-doctypes.md) pour la provenance, l'état mesuré et les adaptations. ERPNext est distribué sous GPL-3.0 ; les fichiers dérivés conservent les obligations de licence applicables. La licence du moteur xcore-doctype (MIT) ne relicencie pas ces définitions. Consulter [`LICENSE`](LICENSE) et les avis de copyright/provenance avant toute redistribution ou réutilisation.

## Dépôt source

- Dépôt : <https://github.com/traoreera01/erpDoctype>
- Moteur : <https://github.com/traoreera/doctype>
