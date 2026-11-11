# Communication (`communication`)

Les objets partagés de messagerie : comptes e-mail, modèles de message et commentaires, consommés par tous les autres modules.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 4 | 0 | 1 | 0 | 0 | 0 | 20 |

## Espace de travail

**Contribution à l'espace `setup`** (aucun espace propre au module).

- **Messagerie** : [`Email Account`](../reference/communication.md#email-account) — création, [`Email Template`](../reference/communication.md#email-template) — création, [`Communication Medium`](../reference/communication.md#communication-medium) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Communication Medium`](../reference/communication.md#communication-medium) | Communication Medium | données de base |  |  |  |
| [`Email Account`](../reference/communication.md#email-account) | Email Account | données de base |  |  |  |
| [`Email Template`](../reference/communication.md#email-template) | Email Template | données de base |  |  |  |
| [`Communication Medium Timeslot`](../reference/communication.md#communication-medium-timeslot) | Communication Medium Timeslot | enfant |  |  |  |

## Points clés

- `Email Account` (compte expéditeur avec réponses), `Email Template` (modèle avec sujet et corps), `Communication` (échange rattaché à un document via `reference_doctype`/`reference_name` en `DynamicLink`) et leur enfant `Email Attachment`.
- Le moteur du Desk fournit déjà les **commentaires, mentions et pièces jointes** natifs (`xdt_comment`…) : ce module ne duplique pas cette mécanique, il la complète pour les canaux e-mail proprement dits.

## Dépendances

- **Dépend de** : `setup` (2 liens), `buying` (1).
- **Requis par** : `accounts` (2), `hr` (5), `payroll` (3), `buying` (2), `crm` (1), `selling` (1), `stock` (1), `support` (1).

Détail complet : [matrice](../dependances.md#communication-communication).

## Implémentation en plugin xcore

- Petites dépendances, chargement tôt : peut être porté avec `setup` (sa contribution va d'ailleurs à l'espace Configuration).
- Le rendu d'un modèle à l'envoi passe par l'extension `ext.email` de l'hôte — pas de hook métier à écrire dans le plugin, juste l'exposition des DocTypes.

## Référence complète

[Référence — Communication](../reference/communication.md).
