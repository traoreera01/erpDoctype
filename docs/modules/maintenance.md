# Maintenance (`maintenance`)

La maintenance des équipements vendus ou installés chez les clients : visites, demandes d'intervention et contrats de maintenance.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 5 | 2 | 3 | 0 | 0 | 2 | 65 |

## Espace de travail

**Contribution à l'espace `support`** (aucun espace propre au module).

- **Maintenance** : [`Maintenance Schedule`](../reference/maintenance.md#maintenance-schedule) — création, [`Maintenance Visit`](../reference/maintenance.md#maintenance-visit) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Maintenance Schedule Detail`](../reference/maintenance.md#maintenance-schedule-detail) | Maintenance Schedule Detail | enfant |  |  |  |
| [`Maintenance Schedule Item`](../reference/maintenance.md#maintenance-schedule-item) | Maintenance Schedule Item | enfant |  |  |  |
| [`Maintenance Visit Purpose`](../reference/maintenance.md#maintenance-visit-purpose) | Maintenance Visit Purpose | enfant |  |  |  |
| [`Maintenance Schedule`](../reference/maintenance.md#maintenance-schedule) | Maintenance Schedule | pièce | oui | `MS-{YYYY}-{#####}` |  |
| [`Maintenance Visit`](../reference/maintenance.md#maintenance-visit) | Maintenance Visit | pièce | oui | `MV-{YYYY}-{#####}` |  |

## Points clés

- **`Maintenance Visit`** (MVP-) : rapport de visite, lignes par équipement ; **`Maintenance Schedule`** (MS-) : le plan récurrent des visites par période et équipement, enfants pour les événements.
- `Serial and Batch Bundle` (hébergé dans `stock`) identifie les équipements ; les contrats viennent de `crm` (`Contract`).
- Petit module satellite : il contribue à l'espace **Support** et dépend du cycle commercial.

## Dépendances

- **Dépend de** : `setup` (11 liens), `stock` (5), `selling` (3), `crm` (2).
- **Requis par** : personne.

Détail complet : [matrice](../dependances.md#maintenance-maintenance).

## Implémentation en plugin xcore

- Peut être porté par le plugin `support` ou en plugin satellite après le cycle commercial ; les visites planifiées se génèrent par une tâche planifiée (cron) depuis `Maintenance Schedule`.

## Référence complète

[Référence — Maintenance](../reference/maintenance.md).
