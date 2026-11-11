# Immobilisations (`assets`)

Gestion du parc d'immobilisations : fiches d'actif, catégories avec barèmes d'amortissement, mouvements (acquisition, cession, réévaluation, split) et tableaux d'amortissement qui écrivent en comptabilité.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 25 | 8 | 11 | 0 | 0 | 8 | 277 |

## Espace de travail

**Espace « Immobilisations »** (icône `building`, position 80)

- **Opérations** : [`Asset`](../reference/assets.md#asset) — création, [`Asset Movement`](../reference/assets.md#asset-movement) — création, [`Asset Repair`](../reference/assets.md#asset-repair) — création, [`Asset Value Adjustment`](../reference/assets.md#asset-value-adjustment) — création
- **Maintenance** : [`Asset Maintenance`](../reference/assets.md#asset-maintenance) — création, [`Asset Maintenance Log`](../reference/assets.md#asset-maintenance-log) — création
- **Référentiel** : [`Asset Category`](../reference/assets.md#asset-category) — création, [`Location`](../reference/assets.md#location) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Asset Activity`](../reference/assets.md#asset-activity) | Asset Activity | données de base |  |  |  |
| [`Asset Category`](../reference/assets.md#asset-category) | Asset Category | données de base |  |  |  |
| [`Asset Maintenance`](../reference/assets.md#asset-maintenance) | Asset Maintenance | données de base |  |  |  |
| [`Asset Maintenance Team`](../reference/assets.md#asset-maintenance-team) | Asset Maintenance Team | données de base |  |  |  |
| [`Asset Shift Factor`](../reference/assets.md#asset-shift-factor) | Asset Shift Factor | données de base |  |  |  |
| [`Location`](../reference/assets.md#location) | Location | données de base |  |  |  |
| [`Asset Capitalization Asset Item`](../reference/assets.md#asset-capitalization-asset-item) | Asset Capitalization Asset Item | enfant |  |  |  |
| [`Asset Capitalization Service Item`](../reference/assets.md#asset-capitalization-service-item) | Asset Capitalization Service Item | enfant |  |  |  |
| [`Asset Capitalization Stock Item`](../reference/assets.md#asset-capitalization-stock-item) | Asset Capitalization Stock Item | enfant |  |  |  |
| [`Asset Category Account`](../reference/assets.md#asset-category-account) | Asset Category Account | enfant |  |  |  |
| [`Asset Finance Book`](../reference/assets.md#asset-finance-book) | Asset Finance Book | enfant |  |  |  |
| [`Asset Maintenance Task`](../reference/assets.md#asset-maintenance-task) | Asset Maintenance Task | enfant |  |  |  |
| [`Asset Movement Item`](../reference/assets.md#asset-movement-item) | Asset Movement Item | enfant |  |  |  |
| [`Asset Repair Consumed Item`](../reference/assets.md#asset-repair-consumed-item) | Asset Repair Consumed Item | enfant |  |  |  |
| [`Asset Repair Purchase Invoice`](../reference/assets.md#asset-repair-purchase-invoice) | Asset Repair Purchase Invoice | enfant |  |  |  |
| [`Depreciation Schedule`](../reference/assets.md#depreciation-schedule) | Depreciation Schedule | enfant |  |  |  |
| [`Maintenance Team Member`](../reference/assets.md#maintenance-team-member) | Maintenance Team Member | enfant |  |  |  |
| [`Asset`](../reference/assets.md#asset) | Asset | pièce | oui | `ASSE-{YYYY}-{#####}` |  |
| [`Asset Capitalization`](../reference/assets.md#asset-capitalization) | Asset Capitalization | pièce | oui | `AC-{YYYY}-{#####}` |  |
| [`Asset Depreciation Schedule`](../reference/assets.md#asset-depreciation-schedule) | Asset Depreciation Schedule | pièce | oui | `ADS-{YYYY}-{#####}` |  |
| [`Asset Maintenance Log`](../reference/assets.md#asset-maintenance-log) | Asset Maintenance Log | pièce | oui | `AML-{YYYY}-{#####}` |  |
| [`Asset Movement`](../reference/assets.md#asset-movement) | Asset Movement | pièce | oui | `AM-{YYYY}-{#####}` |  |
| [`Asset Repair`](../reference/assets.md#asset-repair) | Asset Repair | pièce | oui | `AR-{YYYY}-{#####}` |  |
| [`Asset Shift Allocation`](../reference/assets.md#asset-shift-allocation) | Asset Shift Allocation | pièce | oui | `ASA-{YYYY}-{#####}` |  |
| [`Asset Value Adjustment`](../reference/assets.md#asset-value-adjustment) | Asset Value Adjustment | pièce | oui | `AVA-{YYYY}-{#####}` |  |

## Points clés

- **`Asset`** (ASSE-) : la fiche centrale — catégorie, coût d'acquisition, statut, emplacement ; chaque modification passe par une pièce `Asset Modification Log`.
- **Les mouvements sont des pièces** : `Asset Acquisition`/`Asset Sale`/`Asset Value Adjustment`/`Asset Repair`/`Asset Capitalization`… toutes soumises et toutes numérotées (AS-, AC-, ADS-, …).
- **L'amortissement** : la catégorie porte le barème (`Asset Category`, procédure et comptes), la pièce `Asset Depreciation Schedule` déroule les lignes planifiées ; chaque poste validé écrit sa dotation en comptabilité (`Journal Entry`).
- **Liens comptables forts** : 28 des liens sortants pointent vers `accounts` (comptes, journaux, centre de coût) — ce module ne se conçoit qu'après la comptabilité.

## Dépendances

- **Dépend de** : `accounts` (28 liens), `setup` (18), `stock` (12), `projects` (3), `buying` (1), `selling` (1).
- **Requis par** : `accounts` (5 — `Asset`, `Asset Category`, `Location`…), `stock` (8), `hr` (1), `buying` (1).

Détail complet : [matrice](../dependances.md#immobilisations-assets).

## Implémentation en plugin xcore

- Plugin `assets` ; l'ordre de déploiement est P5 (après `setup`, `accounts`, `stock`).
- **Hooks à écrire** : génération du plan d'amortissement à la création d'un actif, dotation comptable à chaque échéance validée, écritures d'acquisition/cession à la soumission des pièces correspondantes.
- Le coût d'acquisition peut provenir d'une facture d'achat (`Purchase Invoice` via `accounts`/`buying`) : le hook doit le recopier.

## Référence complète

[Référence — Immobilisations](../reference/assets.md).
