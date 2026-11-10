# Documentation du jeu ERP DocTypes

> Ce document accompagne les définitions YAML de ce dépôt. Les mécanismes de validation, stockage, droits, hooks et interface sont fournis par xcore-doctype et les plugins consommateurs, pas par ce jeu de fichiers.

## État de l'extraction

Le jeu a été extrait du dépôt xcore-doctype le 10 novembre 2026. L'extraction initiale contient 704 fichiers YAML dans 22 répertoires de modules. Les définitions ont été migrées depuis ERPNext (référence d'origine documentée dans l'historique du projet moteur), puis transformées pour respecter le schéma et les capacités de xcore-doctype.

La référence technique complète et l'historique des transformations ont été conservés depuis le dépôt source. La présente copie devra être mise à jour lorsque les définitions évoluent ; le dépôt source du moteur utilise un sous-module pointant sur un commit précis.

## Organisation

Chaque dossier de premier niveau correspond à un domaine ou module :

- `accounts/`, `buying/`, `selling/`, `stock/`, `assets/`, `payroll/`, `hr/` ;
- `crm/`, `communication/`, `support/`, `projects/`, `maintenance/`, `manufacturing/`, `quality_management/` ;
- `setup/`, `regional/`, `utilities/`, `telephony/`, `edi/`, `bulk_transaction/`, `erpnext_integrations/`, `subcontracting/`.

Les fichiers sont des définitions DocType YAML. Les espaces de travail, traductions, données de plan comptable et plugins ne sont pas inclus dans ce dépôt, sauf s'ils sont explicitement ajoutés dans le futur.

## Chargement

Le moteur peut charger récursivement un répertoire de définitions opérateur puis valider les liens après l'enregistrement de l'ensemble. Pour un déploiement modulaire, chaque plugin propriétaire charge son dossier de module, déclare les grants de son namespace et les dépendances nécessaires. Les modules qui se référencent en cycle doivent utiliser le mécanisme de modules pairs de xcore-doctype (`load_dir(..., peers=True)`).

Ne pas charger simultanément les mêmes définitions depuis la racine du dépôt moteur et depuis ce sous-module : cela créerait des définitions en double.

## Principales adaptations de schéma

Les transformations documentées dans l'historique et dans le guide du moteur comprennent notamment :

- harmonisation des référentiels et des noms de champs liés ;
- retrait des liens vers des types externes absents ou non adressables ;
- adoption de `Decimal` pour les quantités et valeurs exactes, avec échelles déclarées ;
- numérotation des pièces, champs `compute`, `fetch_from`, conditions et devise d'affichage lorsque le schéma le permet ;
- correction des vues arborescentes erronées et des champs système dupliqués ;
- traduction française des libellés dans un catalogue séparé, non embarqué ici.

Le document détaillé de migration, ses contrôles et les décisions sont conservés dans le dépôt moteur : [`process/erp-doctypes.md`](https://github.com/traoreera/doctype/blob/master/process/erp-doctypes.md).

## Validation

Valider les définitions contre la version du moteur utilisée par le plugin consommateur. Les vérifications doivent couvrir au minimum : parsing strict, types enfants, cibles Link/DynamicLink, conditions/calculs, filtres, numérotation, champs monétaires et cohérence de la déclaration des grants. Un passage des contrôles structurels ne valide pas les règles métier ou la conformité comptable.

Le plan comptable SYSCOHADA, quand il est consommé par l'ERP, doit être validé par un expert-comptable compétent avant tout usage en production ; il n'est pas inclus dans ce dépôt.

## Périmètre et limites

Ces fichiers ne constituent pas à eux seuls un ERP opérationnel. Les hooks de comptabilisation, valorisation, stock, clôture, paie, workflows de déploiement et tests métier appartiennent aux plugins ERP séparés. Une définition marquée `submittable` n'implémente pas automatiquement la comptabilisation attendue.

Pour le contrat courant du moteur, les instructions d'installation et les exemples, consulter le [guide xcore-doctype](https://github.com/traoreera/doctype/blob/master/docs/guide.md) et le [plan d'intégration ERP](https://github.com/traoreera/doctype/blob/master/process/plan-erp.md).
