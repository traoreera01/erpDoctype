# Support (`support`)

Le service client : tickets (`Issue`), accords de niveau de service, réclamations sous garantie — la porte d'entrée des demandes entrantes.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 11 | 0 | 5 | 1 | 0 | 0 | 111 |

## Espace de travail

**Espace « Support »** (icône `ticket`, position 90)

- **Opérations** : [`Issue`](../reference/support.md#issue) — création, [`Warranty Claim`](../reference/support.md#warranty-claim) — création
- **Référentiel** : [`Issue Type`](../reference/support.md#issue-type) — création, [`Issue Priority`](../reference/support.md#issue-priority) — création, [`Service Level Agreement`](../reference/support.md#service-level-agreement) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Issue`](../reference/support.md#issue) | Issue | données de base |  |  |  |
| [`Issue Priority`](../reference/support.md#issue-priority) | Issue Priority | données de base |  |  |  |
| [`Issue Type`](../reference/support.md#issue-type) | Issue Type | données de base |  |  |  |
| [`Service Level Agreement`](../reference/support.md#service-level-agreement) | Service Level Agreement | données de base |  |  |  |
| [`Warranty Claim`](../reference/support.md#warranty-claim) | Warranty Claim | données de base |  |  |  |
| [`Pause SLA On Status`](../reference/support.md#pause-sla-on-status) | Pause SLA On Status | enfant |  |  |  |
| [`Service Day`](../reference/support.md#service-day) | Service Day | enfant |  |  |  |
| [`Service Level Priority`](../reference/support.md#service-level-priority) | Service Level Priority | enfant |  |  |  |
| [`SLA Fulfilled On Status`](../reference/support.md#sla-fulfilled-on-status) | SLA Fulfilled On Status | enfant |  |  |  |
| [`Support Search Source`](../reference/support.md#support-search-source) | Support Search Source | enfant |  |  |  |
| [`Support Settings`](../reference/support.md#support-settings) | Support Settings | unique |  |  |  |

## Points clés

- **`Issue`** (vue kanban) : le ticket — priorité (`Issue Priority`), type, source, objet (article/numéro de série en `DynamicLink`), client ; le suivi d'état passe par le Desk du moteur (pas de `docstatus`).
- **`Service Level Agreement`** : le contrat de service — priorités avec délais de première réponse et de résolution (`Service Level Priority`), jours/horaires de service (`Service Day`), pauses sur états.
- **`Warranty Claim`** : la réclamation sous garantie (vue kanban), vers l'article et la facture.
- **Pas de pièces soumises** : le module vit en documents ouverts ; `maintenance` lui ajoute les visites.

## Dépendances

- **Dépend de** : `setup` (6 liens), `crm` (3), `selling` (2), `stock` (2), `communication` (1), `projects` (1).
- **Requis par** : `projects` (1).

Détail complet : [matrice](../dependances.md#support-support).

## Implémentation en plugin xcore

- Ordre P5 ; `maintenance` contribue à son espace de travail.
- **Hooks à écrire** : calcul des échéances SLA à l'ouverture d'un ticket (selon l'accord du client), escalade au dépassement, vieillissement (tâche planifiée), conversion en `Warranty Claim` ou `Maintenance Visit`.

## Référence complète

[Référence — Support](../reference/support.md).
