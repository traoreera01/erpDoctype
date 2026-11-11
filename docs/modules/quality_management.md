# Qualité (`quality_management`)

Le système de management de la qualité : procédures, objectifs, revues, actions correctives, non-conformités, retours d'expérience et réunions qualité.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 16 | 0 | 8 | 0 | 0 | 0 | 69 |

## Espace de travail

**Espace « Qualité »** (icône `check-circle`, position 100)

- **Suivi** : [`Non Conformance`](../reference/quality_management.md#non-conformance) — création, [`Quality Action`](../reference/quality_management.md#quality-action) — création, [`Quality Review`](../reference/quality_management.md#quality-review) — création
- **Référentiel** : [`Quality Goal`](../reference/quality_management.md#quality-goal) — création, [`Quality Procedure`](../reference/quality_management.md#quality-procedure) — création, [`Quality Feedback Template`](../reference/quality_management.md#quality-feedback-template) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Non Conformance`](../reference/quality_management.md#non-conformance) | Non Conformance | données de base |  |  |  |
| [`Quality Action`](../reference/quality_management.md#quality-action) | Quality Action | données de base |  |  |  |
| [`Quality Feedback`](../reference/quality_management.md#quality-feedback) | Quality Feedback | données de base |  |  |  |
| [`Quality Feedback Template`](../reference/quality_management.md#quality-feedback-template) | Quality Feedback Template | données de base |  |  |  |
| [`Quality Goal`](../reference/quality_management.md#quality-goal) | Quality Goal | données de base |  |  |  |
| [`Quality Meeting`](../reference/quality_management.md#quality-meeting) | Quality Meeting | données de base |  |  |  |
| [`Quality Procedure`](../reference/quality_management.md#quality-procedure) | Quality Procedure | données de base |  |  |  |
| [`Quality Review`](../reference/quality_management.md#quality-review) | Quality Review | données de base |  |  |  |
| [`Quality Action Resolution`](../reference/quality_management.md#quality-action-resolution) | Quality Action Resolution | enfant |  |  |  |
| [`Quality Feedback Parameter`](../reference/quality_management.md#quality-feedback-parameter) | Quality Feedback Parameter | enfant |  |  |  |
| [`Quality Feedback Template Parameter`](../reference/quality_management.md#quality-feedback-template-parameter) | Quality Feedback Template Parameter | enfant |  |  |  |
| [`Quality Goal Objective`](../reference/quality_management.md#quality-goal-objective) | Quality Goal Objective | enfant |  |  |  |
| [`Quality Meeting Agenda`](../reference/quality_management.md#quality-meeting-agenda) | Quality Meeting Agenda | enfant |  |  |  |
| [`Quality Meeting Minutes`](../reference/quality_management.md#quality-meeting-minutes) | Quality Meeting Minutes | enfant |  |  |  |
| [`Quality Procedure Process`](../reference/quality_management.md#quality-procedure-process) | Quality Procedure Process | enfant |  |  |  |
| [`Quality Review Objective`](../reference/quality_management.md#quality-review-objective) | Quality Review Objective | enfant |  |  |  |

## Points clés

- Aucune pièce soumise : un module de suivi structuré en **procédures** (`Quality Procedure`, arborescente), **objectifs** (`Quality Goal` avec critères mesurables), **revues** et **actions** (`Quality Review`, `Quality Action`).
- **`Non Conformance`** : la non-conformité (vue kanban), reliée à un article ou un fournisseur ; **`Quality Feedback`** collecte les retours selon un gabarit de paramètres.
- **`Quality Meeting`** : ordre du jour et compte rendu en tables enfants.
- Le module ne dépend que de `setup` (2 liens) et n'est requis par personne : il se greffe sur `stock`/`buying`/`manufacturing` à l'implémentation (inspection à la réception, contrôle fournisseur).

## Dépendances

- **Dépend de** : `setup` (2 liens). **Requis par** : personne.

Détail complet : [matrice](../dependances.md#qualite-quality_management).

## Implémentation en plugin xcore

- Peut être chargé à tout moment (indépendant) ; les points de contrôle qualité sur les réceptions se posent comme hooks sur les pièces de `stock` (inspection avant acceptation) sans toucher à ce module.

## Référence complète

[Référence — Qualité](../reference/quality_management.md).
