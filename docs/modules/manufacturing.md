# Fabrication (`manufacturing`)

La production : nomenclatures (BOM), ordres de fabrication, gammes, postes de travail, cartes d'opération et planification de la production.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 49 | 8 | 30 | 1 | 0 | 8 | 712 |

## Espace de travail

**Espace « Fabrication »** (icône `cog`, position 30) — Nomenclatures, ordres de fabrication et suivi des opérations.

- **Planification et production** : [`Production Plan`](../reference/manufacturing.md#production-plan) — création, [`Work Order`](../reference/manufacturing.md#work-order) — création, [`Job Card`](../reference/manufacturing.md#job-card) — création, [`Downtime Entry`](../reference/manufacturing.md#downtime-entry) — création
- **Référentiel** : [`BOM`](../reference/manufacturing.md#bom) — création, [`Operation`](../reference/manufacturing.md#operation) — création, [`Workstation`](../reference/manufacturing.md#workstation) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`BOM Update Tool`](../reference/manufacturing.md#bom-update-tool) | BOM Update Tool | données de base |  |  |  |
| [`Downtime Entry`](../reference/manufacturing.md#downtime-entry) | Downtime Entry | données de base |  |  |  |
| [`Master Production Schedule`](../reference/manufacturing.md#master-production-schedule) | Master Production Schedule | données de base |  |  |  |
| [`Operation`](../reference/manufacturing.md#operation) | Operation | données de base |  |  |  |
| [`Plant Floor`](../reference/manufacturing.md#plant-floor) | Plant Floor | données de base |  |  |  |
| [`Production Plan Schedule`](../reference/manufacturing.md#production-plan-schedule) | Production Plan Schedule | données de base |  |  |  |
| [`Routing`](../reference/manufacturing.md#routing) | Routing | données de base |  |  |  |
| [`Workstation`](../reference/manufacturing.md#workstation) | Workstation | données de base |  |  |  |
| [`Workstation Operating Component`](../reference/manufacturing.md#workstation-operating-component) | Workstation Operating Component | données de base |  |  |  |
| [`Workstation Type`](../reference/manufacturing.md#workstation-type) | Workstation Type | données de base |  |  |  |
| [`Blanket Order Item`](../reference/manufacturing.md#blanket-order-item) | Blanket Order Item | enfant |  |  |  |
| [`BOM Creator Item`](../reference/manufacturing.md#bom-creator-item) | BOM Creator Item | enfant |  |  |  |
| [`BOM Creator Material`](../reference/manufacturing.md#bom-creator-material) | BOM Creator Material | enfant |  |  |  |
| [`BOM Creator Operation`](../reference/manufacturing.md#bom-creator-operation) | BOM Creator Operation | enfant |  |  |  |
| [`BOM Explosion Item`](../reference/manufacturing.md#bom-explosion-item) | BOM Explosion Item | enfant |  |  |  |
| [`BOM Item`](../reference/manufacturing.md#bom-item) | BOM Item | enfant |  |  |  |
| [`BOM Operation`](../reference/manufacturing.md#bom-operation) | BOM Operation | enfant |  |  |  |
| [`BOM Secondary Item`](../reference/manufacturing.md#bom-secondary-item) | BOM Secondary Item | enfant |  |  |  |
| [`BOM Update Batch`](../reference/manufacturing.md#bom-update-batch) | BOM Update Batch | enfant |  |  |  |
| [`Job Card Item`](../reference/manufacturing.md#job-card-item) | Job Card Item | enfant |  |  |  |
| [`Job Card Operation`](../reference/manufacturing.md#job-card-operation) | Job Card Operation | enfant |  |  |  |
| [`Job Card Scheduled Time`](../reference/manufacturing.md#job-card-scheduled-time) | Job Card Scheduled Time | enfant |  |  |  |
| [`Job Card Secondary Item`](../reference/manufacturing.md#job-card-secondary-item) | Job Card Secondary Item | enfant |  |  |  |
| [`Job Card Time Log`](../reference/manufacturing.md#job-card-time-log) | Job Card Time Log | enfant |  |  |  |
| [`Master Production Schedule Item`](../reference/manufacturing.md#master-production-schedule-item) | Master Production Schedule Item | enfant |  |  |  |
| [`Material Request Plan Item`](../reference/manufacturing.md#material-request-plan-item) | Material Request Plan Item | enfant |  |  |  |
| [`Production Plan Item`](../reference/manufacturing.md#production-plan-item) | Production Plan Item | enfant |  |  |  |
| [`Production Plan Item Reference`](../reference/manufacturing.md#production-plan-item-reference) | Production Plan Item Reference | enfant |  |  |  |
| [`Production Plan Material Request`](../reference/manufacturing.md#production-plan-material-request) | Production Plan Material Request | enfant |  |  |  |
| [`Production Plan Material Request Warehouse`](../reference/manufacturing.md#production-plan-material-request-warehouse) | Production Plan Material Request Warehouse | enfant |  |  |  |
| [`Production Plan Sales Order`](../reference/manufacturing.md#production-plan-sales-order) | Production Plan Sales Order | enfant |  |  |  |
| [`Production Plan Sub Assembly Item`](../reference/manufacturing.md#production-plan-sub-assembly-item) | Production Plan Sub Assembly Item | enfant |  |  |  |
| [`Sales Forecast Item`](../reference/manufacturing.md#sales-forecast-item) | Sales Forecast Item | enfant |  |  |  |
| [`Sub Operation`](../reference/manufacturing.md#sub-operation) | Sub Operation | enfant |  |  |  |
| [`Work Order Additional Item`](../reference/manufacturing.md#work-order-additional-item) | Work Order Additional Item | enfant |  |  |  |
| [`Work Order Item`](../reference/manufacturing.md#work-order-item) | Work Order Item | enfant |  |  |  |
| [`Work Order Operation`](../reference/manufacturing.md#work-order-operation) | Work Order Operation | enfant |  |  |  |
| [`Workstation Cost`](../reference/manufacturing.md#workstation-cost) | Workstation Cost | enfant |  |  |  |
| [`Workstation Operating Component Account`](../reference/manufacturing.md#workstation-operating-component-account) | Workstation Operating Component Account | enfant |  |  |  |
| [`Workstation Working Hour`](../reference/manufacturing.md#workstation-working-hour) | Workstation Working Hour | enfant |  |  |  |
| [`Blanket Order`](../reference/manufacturing.md#blanket-order) | Blanket Order | pièce | oui | `BO-{YYYY}-{#####}` |  |
| [`BOM`](../reference/manufacturing.md#bom) | BOM | pièce | oui | `BOM-{YYYY}-{#####}` |  |
| [`BOM Creator`](../reference/manufacturing.md#bom-creator) | BOM Creator | pièce | oui | `BC-{YYYY}-{#####}` |  |
| [`BOM Update Log`](../reference/manufacturing.md#bom-update-log) | BOM Update Log | pièce | oui | `BUL-{YYYY}-{#####}` |  |
| [`Job Card`](../reference/manufacturing.md#job-card) | Job Card | pièce | oui | `JC-{YYYY}-{#####}` |  |
| [`Production Plan`](../reference/manufacturing.md#production-plan) | Production Plan | pièce | oui | `PP-{YYYY}-{#####}` |  |
| [`Sales Forecast`](../reference/manufacturing.md#sales-forecast) | Sales Forecast | pièce | oui | `SF-{YYYY}-{#####}` |  |
| [`Work Order`](../reference/manufacturing.md#work-order) | Work Order | pièce | oui | `WO-{YYYY}-{#####}` |  |
| [`Manufacturing Settings`](../reference/manufacturing.md#manufacturing-settings) | Manufacturing Settings | unique |  |  |  |

## Points clés

- **La chaîne** : `Production Plan` (PP-, alimenté par les commandes de vente ou une prévision `Sales Forecast`) → `Work Order` (WO-, l'ordre de fabrication) → `Job Card` (JC-, le suivi temps réel par opération) → réception de production dans `stock` (`Stock Entry`).
- **`BOM`** (BOM-) : la nomenclature — composants (`BOM Item`), opérations (`BOM Operation`), avec explosée `BOM Explosion Item` ; le coût de fabrication y est calculé (champs `compute`).
- **Les ressources** : `Workstation`/`Workstation Type` (coûts horaires et comptes), `Operation`, `Routing` (gammes), `Plant Floor` (atelier).
- **`Blanket Order`** (BO-) : la commande cadre multi-livrables, achats ou ventes.
- **30 tables enfants** : le module est massivement structuré en lignes — chaque pièce porte ses items, opérations et temps.

## Dépendances

- **Dépend de** : `stock` (77 liens — articles, entrepôts, mouvements), `setup` (49), `selling` (9), `buying` (5), `projects` (5), `accounts` (1), `subcontracting` (1).
- **Requis par** : `stock` (12), `subcontracting` (6), `buying` (5), `selling` (3).

Détail complet : [matrice](../dependances.md#fabrication-manufacturing).

## Implémentation en plugin xcore

- Plugin `manufacturing`, ordre P5 (après `stock` et le cycle commercial).
- **Hooks à écrire** : explosion du BOM à la soumission de l'ordre (consommation des composants par `Stock Entry` dans `stock`), réception du produit fini, calcul des coûts (main d'œuvre par `Job Card Time Log`, frais de poste), réservation de capacité des postes de travail.
- La planification (MPS, `Production Plan`) écrit des `Material Request` via `tx` — le moteur fournit la lecture transactionnelle.

## Référence complète

[Référence — Fabrication](../reference/manufacturing.md).
