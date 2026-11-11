# Projets (`projects`)

La gestion de projets : projets, tâches arborescentes avec dépendances, feuilles de temps facturables et types d'activité.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 14 | 2 | 4 | 1 | 0 | 2 | 167 |

## Espace de travail

**Espace « Projets »** (icône `briefcase`, position 70)

- **Suivi** : [`Project`](../reference/projects.md#project) — création, [`Task`](../reference/projects.md#task) — création, [`Timesheet`](../reference/projects.md#timesheet) — création, [`Project Update`](../reference/projects.md#project-update) — création
- **Référentiel** : [`Project Template`](../reference/projects.md#project-template) — création, [`Project Type`](../reference/projects.md#project-type) — création, [`Activity Type`](../reference/projects.md#activity-type) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Activity Cost`](../reference/projects.md#activity-cost) | Activity Cost | données de base |  |  |  |
| [`Activity Type`](../reference/projects.md#activity-type) | Activity Type | données de base |  |  |  |
| [`Project`](../reference/projects.md#project) | Project | données de base |  |  |  |
| [`Project Template`](../reference/projects.md#project-template) | Project Template | données de base |  |  |  |
| [`Project Type`](../reference/projects.md#project-type) | Project Type | données de base |  |  |  |
| [`Task`](../reference/projects.md#task) | Task | données de base |  |  |  |
| [`Task Type`](../reference/projects.md#task-type) | Task Type | données de base |  |  |  |
| [`Project Template Task`](../reference/projects.md#project-template-task) | Project Template Task | enfant |  |  |  |
| [`Project User`](../reference/projects.md#project-user) | Project User | enfant |  |  |  |
| [`Task Depends On`](../reference/projects.md#task-depends-on) | Task Depends On | enfant |  |  |  |
| [`Timesheet Detail`](../reference/projects.md#timesheet-detail) | Timesheet Detail | enfant |  |  |  |
| [`Project Update`](../reference/projects.md#project-update) | Project Update | pièce | oui | `PU-{YYYY}-{#####}` |  |
| [`Timesheet`](../reference/projects.md#timesheet) | Timesheet | pièce | oui | `TIME-{YYYY}-{#####}` |  |
| [`Projects Settings`](../reference/projects.md#projects-settings) | Projects Settings | unique |  |  |  |

## Points clés

- **`Project`** : la fiche projet (vue kanban + gantt), avec utilisateurs affectés (`Project User`), modèle `Project Template` et types.
- **`Task`** : l'arborescence des tâches (`views.tree`, `Task Depends On` pour les antécédences) — cœur du suivi, consommé par `manufacturing` (ordres) et `support`.
- **`Timesheet`** (TIME-) : la feuille de temps soumise, lignes par activité (`Timesheet Detail` vers `Activity Type`), facturable vers `selling` (les lignes migrent sur la facture) et paie (`projects` alimente les bulletins).
- **`Project Update`** (PU-) : l'historique périodique d'avancement (pourcentage, coût).
- **`Activity Cost`** : le coût standard d'un type d'activité par rôle, base de la facturation des temps.

## Dépendances

- **Dépend de** : `setup` (11 liens), `selling` (3), `accounts` (3), `support` (1).
- **Requis par** : `accounts` (27), `stock` (10), `hr` (7), `buying` (5), `manufacturing` (5), `payroll` (2), `subcontracting` (4), `assets` (3), `selling` (3), `support` (1).

Détail complet : [matrice](../dependances.md#projets-projects).

## Implémentation en plugin xcore

- Ordre P5 ; module transversal — chargé tôt dans le graphe mais utilisé par tous.
- **Hooks à écrire** : recopie des lignes de feuille de temps sur la facture à sa soumission, calcul d'avancement (pourcentage des tâches terminées), contrôle de budget projet (`Project Update` + `tx.sum` sur les dépenses).

## Référence complète

[Référence — Projets](../reference/projects.md).
