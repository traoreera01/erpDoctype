# Régionalisation (`regional`)

Les spécificités fiscales et réglementaires par pays : certificats de retenue réduite et réglages TVA locaux. Le module contribue à l'espace Comptabilité.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 5 | 0 | 1 | 2 | 0 | 0 | 23 |

## Espace de travail

**Contribution à l'espace `accounts`** (aucun espace propre au module).

- **Conformité** : [`Import Supplier Invoice`](../reference/regional.md#import-supplier-invoice) — création, [`Lower Deduction Certificate`](../reference/regional.md#lower-deduction-certificate) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Import Supplier Invoice`](../reference/regional.md#import-supplier-invoice) | Import Supplier Invoice | données de base |  |  |  |
| [`Lower Deduction Certificate`](../reference/regional.md#lower-deduction-certificate) | Lower Deduction Certificate | données de base |  |  |  |
| [`UAE VAT Account`](../reference/regional.md#uae-vat-account) | UAE VAT Account | enfant |  |  |  |
| [`South Africa VAT Settings`](../reference/regional.md#south-africa-vat-settings) | South Africa VAT Settings | unique |  |  |  |
| [`UAE VAT Settings`](../reference/regional.md#uae-vat-settings) | UAE VAT Settings | unique |  |  |  |

## Points clés

- **`Lower Deduction Certificate`** : le certificat de retenue à la source réduite d'un fournisseur, appliqué aux paiements (`Payment Entry` dans `accounts`) — le seul lien entrant significatif du module.
- **`Import Supplier Invoice`** : l'import de factures fournisseurs externes.
- **Réglages nationaux** : `UAE VAT Settings` et `South Africa VAT Settings` (documents uniques) avec leurs comptes TVA par société.
- Le jeu est adapté au contexte SYSCOHADA : ces réglages sont des résidus de la migration ERPNext, à n'implémenter que si le pays visé l'exige.

## Dépendances

- **Dépend de** : `setup` (5 liens), `accounts` (5), `stock` (2), `buying` (1).
- **Requis par** : `accounts` (1 — `Lower Deduction Certificate` sur les paiements).

Détail complet : [matrice](../dependances.md#regionalisation-regional).

## Implémentation en plugin xcore

- À porter par le plugin `accounts` ou à laisser de côté dans un premier déploiement SYSCOHADA.

## Référence complète

[Référence — Régionalisation](../reference/regional.md).
