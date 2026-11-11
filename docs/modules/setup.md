# Configuration (`setup`)

La base commune à tous les modules : société et référentiels partagés (pays, devises, groupes, unités), adressage, autorisations, modèles d'impression et utilitaires système. C'est le module le plus cité du jeu (882 liens entrants) et le premier à charger (P0).

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 53 | 1 | 11 | 0 | 0 | 1 | 492 |

## Espace de travail

**Espace « Configuration »** (icône `cog`, position 200)

- **Organisation** : [`Company`](../reference/setup.md#company) — création, [`Address`](../reference/setup.md#address) — création, [`Branch`](../reference/setup.md#branch) — création, [`Department`](../reference/setup.md#department) — création
- **Référentiel** : [`Item Group`](../reference/setup.md#item-group) — création, [`Currency`](../reference/setup.md#currency) — création, [`Country`](../reference/setup.md#country) — création, [`UOM`](../reference/setup.md#uom) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Address`](../reference/setup.md#address) | Address | données de base |  |  |  |
| [`Authorization Control`](../reference/setup.md#authorization-control) | Authorization Control | données de base |  |  |  |
| [`Authorization Rule`](../reference/setup.md#authorization-rule) | Authorization Rule | données de base |  |  |  |
| [`Auto Repeat`](../reference/setup.md#auto-repeat) | Auto Repeat | données de base |  |  |  |
| [`Branch`](../reference/setup.md#branch) | Branch | données de base |  |  |  |
| [`Brand`](../reference/setup.md#brand) | Brand | données de base |  |  |  |
| [`Company`](../reference/setup.md#company) | Company | données de base |  |  |  |
| [`Country`](../reference/setup.md#country) | Pays | données de base |  | champ `country_code` |  |
| [`Currency`](../reference/setup.md#currency) | Devise | données de base |  | champ `currency_code` |  |
| [`Currency Exchange`](../reference/setup.md#currency-exchange) | Currency Exchange | données de base |  |  |  |
| [`Customer Group`](../reference/setup.md#customer-group) | Customer Group | données de base |  |  |  |
| [`Department`](../reference/setup.md#department) | Department | données de base |  |  |  |
| [`Designation`](../reference/setup.md#designation) | Designation | données de base |  |  |  |
| [`Driver`](../reference/setup.md#driver) | Driver | données de base |  |  |  |
| [`Email Digest`](../reference/setup.md#email-digest) | Email Digest | données de base |  |  |  |
| [`Employee`](../reference/setup.md#employee) | Employee | données de base |  |  |  |
| [`Employee Group`](../reference/setup.md#employee-group) | Employee Group | données de base |  |  |  |
| [`Error Log`](../reference/setup.md#error-log) | Error Log | données de base |  |  |  |
| [`Gender`](../reference/setup.md#gender) | Gender | données de base |  | champ `gender` |  |
| [`Global Defaults`](../reference/setup.md#global-defaults) | Global Defaults | données de base |  |  |  |
| [`Holiday List`](../reference/setup.md#holiday-list) | Holiday List | données de base |  |  |  |
| [`Incoterm`](../reference/setup.md#incoterm) | Incoterm | données de base |  |  |  |
| [`Item Group`](../reference/setup.md#item-group) | Item Group | données de base |  |  |  |
| [`Language`](../reference/setup.md#language) | Language | données de base |  | champ `language_code` |  |
| [`Letter Head`](../reference/setup.md#letter-head) | Letter Head | données de base |  |  |  |
| [`Module Def`](../reference/setup.md#module-def) | Module Def | données de base |  | champ `module_name` |  |
| [`Party Type`](../reference/setup.md#party-type) | Party Type | données de base |  |  |  |
| [`Print Format`](../reference/setup.md#print-format) | Print Format | données de base |  |  |  |
| [`Print Heading`](../reference/setup.md#print-heading) | Print Heading | données de base |  |  |  |
| [`Quotation Lost Reason`](../reference/setup.md#quotation-lost-reason) | Quotation Lost Reason | données de base |  |  |  |
| [`RQ Job`](../reference/setup.md#rq-job) | RQ Job | données de base |  | champ `job_id` |  |
| [`Sales Partner`](../reference/setup.md#sales-partner) | Sales Partner | données de base |  |  |  |
| [`Sales Person`](../reference/setup.md#sales-person) | Sales Person | données de base |  |  |  |
| [`Salutation`](../reference/setup.md#salutation) | Salutation | données de base |  | champ `salutation` |  |
| [`Supplier Group`](../reference/setup.md#supplier-group) | Supplier Group | données de base |  |  |  |
| [`Terms and Conditions`](../reference/setup.md#terms-and-conditions) | Terms and Conditions | données de base |  |  |  |
| [`Territory`](../reference/setup.md#territory) | Territory | données de base |  |  |  |
| [`UOM`](../reference/setup.md#uom) | UOM | données de base |  |  |  |
| [`UOM Conversion Factor`](../reference/setup.md#uom-conversion-factor) | UOM Conversion Factor | données de base |  |  |  |
| [`Vehicle`](../reference/setup.md#vehicle) | Vehicle | données de base |  |  |  |
| [`Web Form`](../reference/setup.md#web-form) | Web Form | données de base |  | champ `route` |  |
| [`Driving License Category`](../reference/setup.md#driving-license-category) | Driving License Category | enfant |  |  |  |
| [`Email Digest Recipient`](../reference/setup.md#email-digest-recipient) | Email Digest Recipient | enfant |  |  |  |
| [`Employee Education`](../reference/setup.md#employee-education) | Employee Education | enfant |  |  |  |
| [`Employee External Work History`](../reference/setup.md#employee-external-work-history) | Employee External Work History | enfant |  |  |  |
| [`Employee Group Table`](../reference/setup.md#employee-group-table) | Employee Group Table | enfant |  |  |  |
| [`Employee Internal Work History`](../reference/setup.md#employee-internal-work-history) | Employee Internal Work History | enfant |  |  |  |
| [`Holiday`](../reference/setup.md#holiday) | Holiday | enfant |  |  |  |
| [`Quotation Lost Reason Detail`](../reference/setup.md#quotation-lost-reason-detail) | Quotation Lost Reason Detail | enfant |  |  |  |
| [`Target Detail`](../reference/setup.md#target-detail) | Target Detail | enfant |  |  |  |
| [`Transaction Deletion Record Item`](../reference/setup.md#transaction-deletion-record-item) | Transaction Deletion Record Item | enfant |  |  |  |
| [`Transaction Deletion Record To Delete`](../reference/setup.md#transaction-deletion-record-to-delete) | Transaction Deletion Record To Delete | enfant |  |  |  |
| [`Transaction Deletion Record`](../reference/setup.md#transaction-deletion-record) | Transaction Deletion Record | pièce | oui | `TDR-{YYYY}-{#####}` |  |

## Points clés

- **`Company`** (arborescente) : la société — devise par défaut, exercice fiscal, comptes par défaut ; tout le jeu en dépend. `Global Defaults` porte la société courante.
- **Référentiels nommés par champ** (`naming.field`) : `Country` (`country_code`), `Currency` (`currency_code`), `Language`, `Gender`, `Salutation`, `UOM`, `Module Def`… les cibles de liens les plus citées.
- **Hiérarchies arborescentes** (`views.tree`) : `Customer Group`, `Supplier Group`, `Item Group`, `Department`, `Territory`, `Sales Person`.
- **`Address`** : l'adresse partagée, liée à tout tiers (client, fournisseur, contact, employé).
- **Personnel de base** : `Employee`, `Department`, `Designation`, `Branch` (les DocTypes RH propres sont dans `hr` — `setup` héberge la version générique des tables d'employés pour les besoins transverses).
- **Système** : `Auto Repeat` (récurrence), `Error Log`, `Transaction Deletion Record` (TDR-, la seule pièce), `Print Format`/`Print Heading`/`Letter Head` (impression — le moteur fournit ses propres modèles), `Authorization Control`/`Authorization Rule`.
- **Conventions commerciales** : `Incoterm`, `Terms and Conditions`, `UOM Conversion Factor`, `Currency Exchange` (taux).

## Dépendances

- **Dépend de** : `accounts` (50 liens — comptes par société), `stock` (13), `selling` (2), `crm` (1), `buying` (1) — les cycles setup ↔ accounts et setup ↔ stock sont les plus chargés du jeu.
- **Requis par** : **tous les autres modules** sauf `edi`, `erpnext_integrations`, `bulk_transaction` (882 liens entrants au total).

Détail complet : [matrice](../dependances.md#configuration-setup).

## Implémentation en plugin xcore

- Plugin `setup`, **P0, chargé en premier** ; ses 4 contributions viennent s'ajouter à son espace (`bulk_transaction`, `communication`, `edi`, `utilities`).
- Le cycle avec `accounts`/`stock` impose le **mode pairs** dès le premier plugin : une société cite des comptes, les comptes citent des sociétés.
- **Hooks à écrire** : taux de change à la date (cherché dans `Currency Exchange`, sinon service externe), récurrences `Auto Repeat`, création des comptes par défaut d'une nouvelle société (à partir du plan SYSCOHADA).
- Le catalogue SYSCOHADA et les traductions `fr.yaml` de ce module vivent dans le dépôt moteur.

## Référence complète

[Référence — Configuration](../reference/setup.md).
