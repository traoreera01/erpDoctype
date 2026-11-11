# Traitement en masse (`bulk_transaction`)

Deux DocTypes utilitaires pour rejouer en masse les actions de workflow et de soumission sur plusieurs documents : la transaction en masse et son journal d'exécution.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 2 | 0 | 0 | 0 | 0 | 0 | 12 |

## Espace de travail

**Contribution à l'espace `setup`** (aucun espace propre au module).

- **Traitements en lot** : [`Bulk Transaction Log`](../reference/bulk_transaction.md#bulk-transaction-log) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Bulk Transaction Log`](../reference/bulk_transaction.md#bulk-transaction-log) | Bulk Transaction Log | données de base |  |  |  |
| [`Bulk Transaction Log Detail`](../reference/bulk_transaction.md#bulk-transaction-log-detail) | Bulk Transaction Log Detail | données de base |  |  |  |

## Points clés

- `Bulk Transaction` mémorise une action (soumission, annulation, transition de workflow) à rejouer sur une liste de documents ; `Bulk Transaction Log` trace chaque exécution.
- Module **feuille** : aucun lien sortant vers un autre module (les cibles sont désignées par leur nom, en `DynamicLink`).

## Dépendances

- **Dépend de** : personne.
- **Requis par** : personne — le Desk du moteur fournit déjà les actions en masse ; ce module est une file d'attente persistante pour les volumétries élevées.

Détail complet : [matrice](../dependances.md#traitement-en-masse-bulk_transaction).

## Implémentation en plugin xcore

- Peut être porté par n'importe quel plugin existant (le moteur, via `doctype_writer`, offre déjà le traitement en masse) ; en plugin dédié, un job planifié consomme la file et écrit par `writer.system` avec le module `bulk_transaction` comme périmètre.

## Référence complète

[Référence — Traitement en masse](../reference/bulk_transaction.md).
