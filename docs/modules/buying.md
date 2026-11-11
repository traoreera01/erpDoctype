# Achats (`buying`)

Le cycle fournisseur : devis, demandes de prix, commandes d'achat, factures et suivi des fournisseurs, avec réceptions portées par le module `stock`.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 19 | 4 | 9 | 1 | 1 | 4 | 508 |

## Espace de travail

**Espace « Achats »** (icône `shopping-bag`, position 15)

- **Opérations** : [`Material Request`](../reference/stock.md#material-request) — création, [`Request for Quotation`](../reference/buying.md#request-for-quotation) — création, [`Supplier Quotation`](../reference/buying.md#supplier-quotation) — création, [`Purchase Order`](../reference/buying.md#purchase-order) — création
- **Référentiel** : [`Supplier`](../reference/buying.md#supplier) — création, [`Supplier Group`](../reference/setup.md#supplier-group) — création, [`Supplier Scorecard`](../reference/buying.md#supplier-scorecard) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Supplier`](../reference/buying.md#supplier) | Supplier | données de base |  |  |  |
| [`Supplier Scorecard`](../reference/buying.md#supplier-scorecard) | Supplier Scorecard | données de base |  |  |  |
| [`Supplier Scorecard Criteria`](../reference/buying.md#supplier-scorecard-criteria) | Supplier Scorecard Criteria | données de base |  |  |  |
| [`Supplier Scorecard Standing`](../reference/buying.md#supplier-scorecard-standing) | Supplier Scorecard Standing | données de base |  |  |  |
| [`Supplier Scorecard Variable`](../reference/buying.md#supplier-scorecard-variable) | Supplier Scorecard Variable | données de base |  |  |  |
| [`Customer Number At Supplier`](../reference/buying.md#customer-number-at-supplier) | Customer Number At Supplier | enfant |  |  |  |
| [`Purchase Order Item`](../reference/buying.md#purchase-order-item) | Purchase Order Item | enfant |  |  |  |
| [`Purchase Receipt Item Supplied`](../reference/buying.md#purchase-receipt-item-supplied) | Purchase Receipt Item Supplied | enfant |  |  |  |
| [`Request for Quotation Item`](../reference/buying.md#request-for-quotation-item) | Request for Quotation Item | enfant |  |  |  |
| [`Request for Quotation Supplier`](../reference/buying.md#request-for-quotation-supplier) | Request for Quotation Supplier | enfant |  |  |  |
| [`Supplier Quotation Item`](../reference/buying.md#supplier-quotation-item) | Supplier Quotation Item | enfant |  |  |  |
| [`Supplier Scorecard Scoring Criteria`](../reference/buying.md#supplier-scorecard-scoring-criteria) | Supplier Scorecard Scoring Criteria | enfant |  |  |  |
| [`Supplier Scorecard Scoring Standing`](../reference/buying.md#supplier-scorecard-scoring-standing) | Supplier Scorecard Scoring Standing | enfant |  |  |  |
| [`Supplier Scorecard Scoring Variable`](../reference/buying.md#supplier-scorecard-scoring-variable) | Supplier Scorecard Scoring Variable | enfant |  |  |  |
| [`Purchase Order`](../reference/buying.md#purchase-order) | Purchase Order | pièce | oui | `PUOR-{YYYY}-{#####}` | workflow |
| [`Request for Quotation`](../reference/buying.md#request-for-quotation) | Request for Quotation | pièce | oui | `RQ-{YYYY}-{#####}` |  |
| [`Supplier Quotation`](../reference/buying.md#supplier-quotation) | Supplier Quotation | pièce | oui | `SQ-{YYYY}-{#####}` |  |
| [`Supplier Scorecard Period`](../reference/buying.md#supplier-scorecard-period) | Supplier Scorecard Period | pièce | oui | `SSP-{YYYY}-{#####}` |  |
| [`Buying Settings`](../reference/buying.md#buying-settings) | Buying Settings | unique |  |  |  |

## Points clés

- **Les pièces** : `Request for Quotation` (RFQ-), `Supplier Quotation` (SQ-), `Purchase Order` (PUOR-, workflow d'approbation complet), `Purchase Invoice` (PI-, portée par `accounts`).
- **`Supplier`** est le référentiel central : groupes, pièces jointes, comptes par société, conditions de paiement, évaluations (`Supplier Evaluation` + critères enfants).
- **Le workflow de `Purchase Order`** : Brouillon → À approuver → Approuvée/Refusée (reprise possible), annulation depuis l'état approuvé — la séparation de droits `not_owner` et les grants `workflow_*` sont gérés par le moteur.
- **Les modèles réutilisables** : `Purchase Taxes and Charges Template`, `Supplier Items`, prix fournisseurs (`Item Price` hébergé dans `stock`).

## Dépendances

- **Dépend de** : `setup` (60 liens), `stock` (25), `accounts` (29), `crm` (7), `manufacturing` (5), `selling` (5), `projects` (5), `communication` (2), `assets` (1), `utilities` (1).
- **Requis par** : `accounts` (10), `stock` (14), `manufacturing` (5), `selling` (5), `hr` (3), `subcontracting` (4), `regional` (1), `setup` (1), `communication` (1), `assets` (1).

Détail complet : [matrice](../dependances.md#achats-buying).

## Implémentation en plugin xcore

- Plugin `buying`, ordre P3 avec `selling` (après `setup`, `accounts`, `stock`).
- **Hooks à écrire** : comptabilisation de `Purchase Invoice` (via `accounts`), contrôle du budget dépensé sur commande, génération d'une demande de matériau depuis une commande (`Material Request` dans `stock`), notifications fournisseurs.
- La réception de marchandises vit dans `stock` (`Purchase Receipt`) : ce module ne l'héberge pas.
- Traduction `fr.yaml` disponible (T17 couvre les cinq premiers modules dont celui-ci).

## Référence complète

[Référence — Achats](../reference/buying.md).
