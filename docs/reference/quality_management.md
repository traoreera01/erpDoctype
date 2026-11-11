# Référence des champs — Qualité (`quality_management`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `quality_management/` (16 DocTypes). Ne pas éditer à la main : relancer le script.

69 champs au total ; types les plus fréquents : `Text` (14), `Link` (13), `Select` (13), `TextEditor` (9), `Table` (8).

## Non Conformance

*Non Conformance* — `quality_management/non_conformance.yaml`

- **Vues** : kanban
- **Titre** : `subject`
- **Icône** : `triangle-alert`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `subject` | Subject | Text | **requis**; colonne de liste |
| `procedure` | Procedure | Link → `Quality Procedure` | **requis**; colonne de liste |
| `status` | Status | Select — Open · Resolved · Cancelled | **requis**; colonne de liste |
| `details` | Details | TextEditor |  |
| `process_owner` | Process Owner | Text | lecture seule |
| `full_name` | Full Name | Text | lecture seule |
| `corrective_action` | Corrective Action | TextEditor |  |
| `preventive_action` | Preventive Action | TextEditor |  |

## Quality Action

*Quality Action* — `quality_management/quality_action.yaml`

- **Vues** : calendar
- **Titre** : `status`
- **Icône** : `check-check`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `goal` | Goal | Link → `Quality Goal` | colonne de liste |
| `date` | Date | Date | colonne de liste; lecture seule |
| `procedure` | Procedure | Link → `Quality Procedure` |  |
| `status` | Status | Select — Open · Completed | colonne de liste; lecture seule; défaut `Open` |
| `corrective_preventive` | Corrective/Preventive | Select — Corrective · Preventive | **requis**; colonne de liste; défaut `Corrective` |
| `resolutions` | Resolutions | Table → `Quality Action Resolution` |  |
| `review` | Review | Link → `Quality Review` | colonne de liste |
| `feedback` | Feedback | Link → `Quality Feedback` |  |

## Quality Action Resolution

*Quality Action Resolution* — `quality_management/quality_action_resolution.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `problem` | Problem | LongText | colonne de liste |
| `resolution` | Resolution | TextEditor | colonne de liste |
| `status` | Status | Select — Open · Completed | colonne de liste |
| `responsible` | Responsible | Text | colonne de liste |
| `completion_by` | Completion By | Date | colonne de liste |

## Quality Feedback

*Quality Feedback* — `quality_management/quality_feedback.yaml`

- **Titre** : `template`
- **Icône** : `message-square-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `template` | Template | Link → `Quality Feedback Template` | **requis**; colonne de liste |
| `parameters` | Parameters | Table → `Quality Feedback Parameter` |  |
| `document_type` | Type | Select — Customer | **requis**; colonne de liste |
| `document_name` | Feedback By | DynamicLink → `document_type` | colonne de liste |

## Quality Feedback Parameter

*Quality Feedback Parameter* — `quality_management/quality_feedback_parameter.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `parameter` | Parameter | Text | colonne de liste; lecture seule |
| `rating` | Rating | Select — 1 · 2 · 3 · 4 · 5 | colonne de liste |
| `feedback` | Feedback | TextEditor | colonne de liste |

## Quality Feedback Template

*Quality Feedback Template* — `quality_management/quality_feedback_template.yaml`

- **Titre** : `template`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `template` | Template Name | Text | **requis**; colonne de liste |
| `parameters` | Parameters | Table → `Quality Feedback Template Parameter` |  |

## Quality Feedback Template Parameter

*Quality Feedback Template Parameter* — `quality_management/quality_feedback_template_parameter.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `parameter` | Parameter | Text | **requis**; colonne de liste |

## Quality Goal

*Quality Goal* — `quality_management/quality_goal.yaml`

- **Titre** : `frequency`
- **Icône** : `target`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `frequency` | Monitoring Frequency | Select — None · Daily · Weekly · Monthly · Quarterly | colonne de liste; défaut `None` |
| `procedure` | Procedure | Link → `Quality Procedure` | colonne de liste |
| `date` | Date | Select — 1 · 2 · 3 · 4 · 5 · 6 · 7 · 8 · 9 · 10 · 11 · 12 · 13 · 14 · 15 · 16 · 17 · 18 · 19 · 20 · 21 · 22 · 23 · 24 · 25 · 26 · 27 · 28 · 29 · 30 · 31 |  |
| `weekday` | Weekday | Select — Monday · Tuesday · Wednesday · Thursday · Friday · Saturday · Sunday |  |
| `objectives` | Objectives | Table → `Quality Goal Objective` |  |
| `goal` | Goal | Text | **requis** |

## Quality Goal Objective

*Quality Goal Objective* — `quality_management/quality_goal_objective.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `objective` | Objective | LongText | **requis**; colonne de liste |
| `target` | Target | Text | colonne de liste |
| `uom` | UOM | Link → `UOM` | colonne de liste |

## Quality Meeting

*Quality Meeting* — `quality_management/quality_meeting.yaml`

- **Vues** : kanban
- **Titre** : `status`
- **Icône** : `users`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `status` | Status | Select — Open · Closed | défaut `Open` |
| `minutes` | Minutes | Table → `Quality Meeting Minutes` |  |
| `agenda` | Agenda | Table → `Quality Meeting Agenda` |  |

## Quality Meeting Agenda

*Quality Meeting Agenda* — `quality_management/quality_meeting_agenda.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `agenda` | Agenda | TextEditor | colonne de liste |

## Quality Meeting Minutes

*Quality Meeting Minutes* — `quality_management/quality_meeting_minutes.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `minute` | Minute | TextEditor | colonne de liste |
| `document_type` | Document Type | Select — Quality Review · Quality Action · Quality Feedback | **requis**; colonne de liste |
| `document_name` | Document Name | DynamicLink → `document_type` | colonne de liste |

## Quality Procedure

*Quality Procedure* — `quality_management/quality_procedure.yaml`

- **Vues** : tree (parent `parent_quality_procedure`)
- **Titre** : `quality_procedure_name`
- **Icône** : `clipboard-list`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `parent_quality_procedure` | Parent Procedure | Link → `Quality Procedure` |  |
| `is_group` | Is Group | Boolean | lecture seule |
| `lft` | Left Index | Int | lecture seule; masqué |
| `rgt` | Right Index | Int | lecture seule; masqué |
| `old_parent` | old_parent | Text | lecture seule; masqué |
| `processes` | Processes | Table → `Quality Procedure Process` |  |
| `quality_procedure_name` | Quality Procedure | Text | **requis**; colonne de liste |
| `process_owner` | Process Owner | Text |  |
| `process_owner_full_name` | Process Owner Full Name | Text | masqué |

## Quality Procedure Process

*Quality Procedure Process* — `quality_management/quality_procedure_process.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `process_description` | Process Description | TextEditor | colonne de liste |
| `procedure` | Sub Procedure | Link → `Quality Procedure` | colonne de liste; — Link existing Quality Procedure. |

## Quality Review

*Quality Review* — `quality_management/quality_review.yaml`

- **Vues** : calendar
- **Titre** : `status`
- **Icône** : `clipboard-check`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `date` | Date | Date | colonne de liste; lecture seule |
| `procedure` | Procedure | Link → `Quality Procedure` | lecture seule |
| `additional_information` | Additional Information | LongText |  |
| `reviews` | Reviews | Table → `Quality Review Objective` |  |
| `status` | Status | Select — Open · Passed · Failed | lecture seule; défaut `Open` |
| `goal` | Goal | Link → `Quality Goal` | **requis**; colonne de liste |

## Quality Review Objective

*Quality Review Objective* — `quality_management/quality_review_objective.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `objective` | Objective | LongText | colonne de liste; lecture seule |
| `target` | Target | Text | colonne de liste; lecture seule |
| `uom` | UOM | Link → `UOM` | colonne de liste; lecture seule |
| `review` | Review | TextEditor | colonne de liste |
| `status` | Status | Select — Open · Passed · Failed | colonne de liste; défaut `Open` |
