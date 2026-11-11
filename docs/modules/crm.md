# CRM (`crm`)

La prospection commerciale : pistes, opportunités, contacts, clients potentiels, campagnes, rendez-vous et contrats renouvelables.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 32 | 1 | 12 | 2 | 0 | 1 | 248 |

## Espace de travail

**Espace « CRM »** (icône `users`, position 12)

- **Prospection** : [`Lead`](../reference/crm.md#lead) — création, [`Opportunity`](../reference/crm.md#opportunity) — création, [`Prospect`](../reference/crm.md#prospect) — création, [`Contract`](../reference/crm.md#contract) — création
- **Référentiel** : [`Contact`](../reference/crm.md#contact) — création, [`Campaign`](../reference/crm.md#campaign) — création, [`Appointment`](../reference/crm.md#appointment) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Appointment`](../reference/crm.md#appointment) | Appointment | données de base |  |  |  |
| [`Campaign`](../reference/crm.md#campaign) | Campaign | données de base |  |  |  |
| [`Competitor`](../reference/crm.md#competitor) | Competitor | données de base |  |  |  |
| [`Contact`](../reference/crm.md#contact) | Contact | données de base |  |  |  |
| [`Contract Template`](../reference/crm.md#contract-template) | Contract Template | données de base |  |  |  |
| [`Email Campaign`](../reference/crm.md#email-campaign) | Email Campaign | données de base |  |  |  |
| [`Event`](../reference/crm.md#event) | Event | données de base |  |  |  |
| [`Lead`](../reference/crm.md#lead) | Lead | données de base |  |  |  |
| [`Market Segment`](../reference/crm.md#market-segment) | Market Segment | données de base |  |  |  |
| [`Opportunity`](../reference/crm.md#opportunity) | Opportunity | données de base |  |  |  |
| [`Opportunity Lost Reason`](../reference/crm.md#opportunity-lost-reason) | Opportunity Lost Reason | données de base |  |  |  |
| [`Opportunity Type`](../reference/crm.md#opportunity-type) | Opportunity Type | données de base |  |  |  |
| [`Prospect`](../reference/crm.md#prospect) | Prospect | données de base |  |  |  |
| [`Sales Stage`](../reference/crm.md#sales-stage) | Sales Stage | données de base |  |  |  |
| [`UTM Campaign`](../reference/crm.md#utm-campaign) | UTM Campaign | données de base |  |  |  |
| [`UTM Medium`](../reference/crm.md#utm-medium) | UTM Medium | données de base |  |  |  |
| [`UTM Source`](../reference/crm.md#utm-source) | UTM Source | données de base |  |  |  |
| [`Appointment Booking Slots`](../reference/crm.md#appointment-booking-slots) | Appointment Booking Slots | enfant |  |  |  |
| [`Assignment Rule User`](../reference/crm.md#assignment-rule-user) | Agent affecté | enfant |  |  |  |
| [`Campaign Email Schedule`](../reference/crm.md#campaign-email-schedule) | Campaign Email Schedule | enfant |  |  |  |
| [`Competitor Detail`](../reference/crm.md#competitor-detail) | Competitor Detail | enfant |  |  |  |
| [`Contract Fulfilment Checklist`](../reference/crm.md#contract-fulfilment-checklist) | Contract Fulfilment Checklist | enfant |  |  |  |
| [`Contract Template Fulfilment Terms`](../reference/crm.md#contract-template-fulfilment-terms) | Contract Template Fulfilment Terms | enfant |  |  |  |
| [`CRM Note`](../reference/crm.md#crm-note) | CRM Note | enfant |  |  |  |
| [`Frappe CRM Allowed User`](../reference/crm.md#frappe-crm-allowed-user) | Frappe CRM Allowed User | enfant |  |  |  |
| [`Opportunity Item`](../reference/crm.md#opportunity-item) | Opportunity Item | enfant |  |  |  |
| [`Opportunity Lost Reason Detail`](../reference/crm.md#opportunity-lost-reason-detail) | Opportunity Lost Reason Detail | enfant |  |  |  |
| [`Prospect Lead`](../reference/crm.md#prospect-lead) | Prospect Lead | enfant |  |  |  |
| [`Prospect Opportunity`](../reference/crm.md#prospect-opportunity) | Prospect Opportunity | enfant |  |  |  |
| [`Contract`](../reference/crm.md#contract) | Contract | pièce | oui | `CONT-{YYYY}-{#####}` |  |
| [`Appointment Booking Settings`](../reference/crm.md#appointment-booking-settings) | Appointment Booking Settings | unique |  |  |  |
| [`CRM Settings`](../reference/crm.md#crm-settings) | CRM Settings | unique |  |  |  |

## Points clés

- **L'entonnoir** : `Lead` (CRM-) → `Opportunity` (OPP-) → conversion en `Customer` (`selling`) ; `Prospect` sert d'étape intermédiaire multi-opportunités.
- **`Contract`** est la seule pièce soumise du module : le contrat renouvelable, avec échéances (`Contract` enfants dates) et facturation récurrente (`Sales Invoice` via `selling`).
- **Le référentiel partagé** : `Contact` (carnet d'adresses), `Address` (hébergée dans `setup`), `Campaign` et la suite UTM (`UTM Campaign`/`UTM Medium`/`UTM Source`) pour l'attribution.
- **`Appointment`** : le rendez-vous planifié (vue calendrier), relié aux pistes et opportunités.

## Dépendances

- **Dépend de** : `setup` (21 liens), `selling` (4), `communication` (1), `stock` (1).
- **Requis par** : `selling` (19), `accounts` (19), `stock` (10), `buying` (7), `support` (3), `maintenance` (2), `subcontracting` (2), `setup` (1).

Détail complet : [matrice](../dependances.md#crm-crm).

## Implémentation en plugin xcore

- Plugin `crm`, ordre P3 avec le cycle commercial — mais il peut précéder `selling` (ses liens vers `selling` ne sont que des `DynamicLink` de conversion).
- **Hooks à écrire** : conversion pistes → opportunités → client (création du `Customer` dans `selling` via `tx`), renouvellement des contrats (tâche planifiée), notifications de relance.
- `telephony` contribue à son espace de travail ; `maintenance` dépend de ses contacts.

## Référence complète

[Référence — CRM](../reference/crm.md).
