# Sous-traitance (`subcontracting`)

La fabrication externalisée : commandes de sous-traitance, envoi de composants au sous-traitant, réception des produits transformés et suivi des fournitures en cours chez le tiers.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 13 | 3 | 9 | 0 | 0 | 3 | 290 |

## Espace de travail

**Espace « Sous-traitance »** (icône `sitemap`, position 110)

- **Opérations** : [`Subcontracting Order`](../reference/subcontracting.md#subcontracting-order) — création, [`Subcontracting Receipt`](../reference/subcontracting.md#subcontracting-receipt) — création, [`Subcontracting Inward Order`](../reference/subcontracting.md#subcontracting-inward-order) — création
- **Référentiel** : [`Subcontracting BOM`](../reference/subcontracting.md#subcontracting-bom) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Subcontracting BOM`](../reference/subcontracting.md#subcontracting-bom) | Subcontracting BOM | données de base |  |  |  |
| [`Subcontracting Inward Order Item`](../reference/subcontracting.md#subcontracting-inward-order-item) | Subcontracting Inward Order Item | enfant |  |  |  |
| [`Subcontracting Inward Order Received Item`](../reference/subcontracting.md#subcontracting-inward-order-received-item) | Subcontracting Inward Order Received Item | enfant |  |  |  |
| [`Subcontracting Inward Order Secondary Item`](../reference/subcontracting.md#subcontracting-inward-order-secondary-item) | Subcontracting Inward Order Secondary Item | enfant |  |  |  |
| [`Subcontracting Inward Order Service Item`](../reference/subcontracting.md#subcontracting-inward-order-service-item) | Subcontracting Inward Order Service Item | enfant |  |  |  |
| [`Subcontracting Order Item`](../reference/subcontracting.md#subcontracting-order-item) | Subcontracting Order Item | enfant |  |  |  |
| [`Subcontracting Order Service Item`](../reference/subcontracting.md#subcontracting-order-service-item) | Subcontracting Order Service Item | enfant |  |  |  |
| [`Subcontracting Order Supplied Item`](../reference/subcontracting.md#subcontracting-order-supplied-item) | Subcontracting Order Supplied Item | enfant |  |  |  |
| [`Subcontracting Receipt Item`](../reference/subcontracting.md#subcontracting-receipt-item) | Subcontracting Receipt Item | enfant |  |  |  |
| [`Subcontracting Receipt Supplied Item`](../reference/subcontracting.md#subcontracting-receipt-supplied-item) | Subcontracting Receipt Supplied Item | enfant |  |  |  |
| [`Subcontracting Inward Order`](../reference/subcontracting.md#subcontracting-inward-order) | Subcontracting Inward Order | pièce | oui | `SIO-{YYYY}-{#####}` |  |
| [`Subcontracting Order`](../reference/subcontracting.md#subcontracting-order) | Subcontracting Order | pièce | oui | `SUOR-{YYYY}-{#####}` |  |
| [`Subcontracting Receipt`](../reference/subcontracting.md#subcontracting-receipt) | Subcontracting Receipt | pièce | oui | `SURE-{YYYY}-{#####}` |  |

## Points clés

- **Le cycle** : `Subcontracting Order` (SUOR-, la commande au sous-traitant avec services et composants fournis) → transfert des composants vers l'entrepôt du fournisseur (`Stock Entry` dans `stock`) → `Subcontracting Receipt` (SURE-, la réception du produit fini, avec consommation des composants fournis).
- **`Subcontracting Inward Order`** (SIO-) : la vue inverse — la prestation reçue d'un tiers pour ses propres besoins.
- **`Subcontracting BOM`** : la nomenclature décrivant ce que le sous-traitant assemble ; 9 tables enfants portent les lignes d'items, de services et de composants.
- Module fortement couplé à `stock` (44 liens sortants) : tous les flux physiques passent par les pièces de mouvement.

## Dépendances

- **Dépend de** : `stock` (44 liens), `setup` (28), `accounts` (9), `manufacturing` (6), `buying` (4), `projects` (4), `selling` (2), `crm` (2).
- **Requis par** : `stock` (3), `manufacturing` (1).

Détail complet : [matrice](../dependances.md#sous-traitance-subcontracting).

## Implémentation en plugin xcore

- Ordre P5, après `stock` et `buying` ; le fournisseur sous-traitant est un `Supplier` (`buying`).
- **Hooks à écrire** : transfert automatique des composants à la soumission de la commande, consommation à la réception, contrôle du ratio composants/produits, réévaluation du stock en cours chez le sous-traitant.

## Référence complète

[Référence — Sous-traitance](../reference/subcontracting.md).
