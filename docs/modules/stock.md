# Stock (`stock`)

La gestion physique : articles et variantes, entrepôts arborescents, lots et numéros de série, tous les mouvements (réceptions, livraisons, transferts, ajustements), le registre immuable et les soldes.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 76 | 17 | 31 | 4 | 1 | 18 | 1 404 |

## Espace de travail

**Espace « Stock »** (icône `warehouse`, position 20) — Articles, entrepôts, lots et mouvements de stock.

- **Opérations** : [`Stock Entry`](../reference/stock.md#stock-entry) — création, [`Material Request`](../reference/stock.md#material-request) — création, [`Pick List`](../reference/stock.md#pick-list) — création, [`Stock Reconciliation`](../reference/stock.md#stock-reconciliation) — création, [`Stock Ledger Entry`](../reference/stock.md#stock-ledger-entry), [`Bin`](../reference/stock.md#bin)
- **Référentiel** : [`Item`](../reference/stock.md#item) — création, [`Batch`](../reference/stock.md#batch) — création, [`Warehouse`](../reference/stock.md#warehouse) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Batch`](../reference/stock.md#batch) | Lot | données de base |  | `BATCH-{YYYY}-{#####}` |  |
| [`Bin`](../reference/stock.md#bin) | Bin | données de base |  |  |  |
| [`Customs Tariff Number`](../reference/stock.md#customs-tariff-number) | Customs Tariff Number | données de base |  |  |  |
| [`Inventory Dimension`](../reference/stock.md#inventory-dimension) | Inventory Dimension | données de base |  |  |  |
| [`Item`](../reference/stock.md#item) | Item | données de base |  |  |  |
| [`Item Alternative`](../reference/stock.md#item-alternative) | Item Alternative | données de base |  |  |  |
| [`Item Attribute`](../reference/stock.md#item-attribute) | Item Attribute | données de base |  |  |  |
| [`Item Lead Time`](../reference/stock.md#item-lead-time) | Item Lead Time | données de base |  |  |  |
| [`Item Manufacturer`](../reference/stock.md#item-manufacturer) | Item Manufacturer | données de base |  |  |  |
| [`Item Price`](../reference/stock.md#item-price) | Item Price | données de base |  |  |  |
| [`Manufacturer`](../reference/stock.md#manufacturer) | Manufacturer | données de base |  |  |  |
| [`Price List`](../reference/stock.md#price-list) | Price List | données de base |  |  |  |
| [`Putaway Rule`](../reference/stock.md#putaway-rule) | Putaway Rule | données de base |  |  |  |
| [`Quality Inspection Parameter`](../reference/stock.md#quality-inspection-parameter) | Quality Inspection Parameter | données de base |  |  |  |
| [`Quality Inspection Parameter Group`](../reference/stock.md#quality-inspection-parameter-group) | Quality Inspection Parameter Group | données de base |  |  |  |
| [`Quality Inspection Template`](../reference/stock.md#quality-inspection-template) | Quality Inspection Template | données de base |  |  |  |
| [`Quick Stock Balance`](../reference/stock.md#quick-stock-balance) | Quick Stock Balance | données de base |  |  |  |
| [`Serial No`](../reference/stock.md#serial-no) | Serial No | données de base |  |  |  |
| [`Shipment Parcel Template`](../reference/stock.md#shipment-parcel-template) | Shipment Parcel Template | données de base |  |  |  |
| [`Stock Closing Balance`](../reference/stock.md#stock-closing-balance) | Stock Closing Balance | données de base |  |  |  |
| [`Stock Entry Type`](../reference/stock.md#stock-entry-type) | Stock Entry Type | données de base |  |  |  |
| [`UOM Category`](../reference/stock.md#uom-category) | UOM Category | données de base |  |  |  |
| [`Warehouse`](../reference/stock.md#warehouse) | Warehouse | données de base |  |  |  |
| [`Warehouse Type`](../reference/stock.md#warehouse-type) | Warehouse Type | données de base |  |  |  |
| [`Company Restriction`](../reference/stock.md#company-restriction) | Company Restriction | enfant |  |  |  |
| [`Delivery Note Item`](../reference/stock.md#delivery-note-item) | Delivery Note Item | enfant |  |  |  |
| [`Delivery Stop`](../reference/stock.md#delivery-stop) | Delivery Stop | enfant |  |  |  |
| [`Item Attribute Value`](../reference/stock.md#item-attribute-value) | Item Attribute Value | enfant |  |  |  |
| [`Item Barcode`](../reference/stock.md#item-barcode) | Item Barcode | enfant |  |  |  |
| [`Item Customer Detail`](../reference/stock.md#item-customer-detail) | Item Customer Detail | enfant |  |  |  |
| [`Item Default`](../reference/stock.md#item-default) | Item Default | enfant |  |  |  |
| [`Item Lead Time Supplier`](../reference/stock.md#item-lead-time-supplier) | Item Lead Time Supplier | enfant |  |  |  |
| [`Item Quality Inspection Parameter`](../reference/stock.md#item-quality-inspection-parameter) | Item Quality Inspection Parameter | enfant |  |  |  |
| [`Item Reorder`](../reference/stock.md#item-reorder) | Item Reorder | enfant |  |  |  |
| [`Item Supplier`](../reference/stock.md#item-supplier) | Item Supplier | enfant |  |  |  |
| [`Item Tax`](../reference/stock.md#item-tax) | Item Tax | enfant |  |  |  |
| [`Item Variant Attribute`](../reference/stock.md#item-variant-attribute) | Item Variant Attribute | enfant |  |  |  |
| [`Landed Cost Item`](../reference/stock.md#landed-cost-item) | Landed Cost Item | enfant |  |  |  |
| [`Landed Cost Purchase Receipt`](../reference/stock.md#landed-cost-purchase-receipt) | Landed Cost Purchase Receipt | enfant |  |  |  |
| [`Landed Cost Taxes and Charges`](../reference/stock.md#landed-cost-taxes-and-charges) | Landed Cost Taxes and Charges | enfant |  |  |  |
| [`Landed Cost Vendor Invoice`](../reference/stock.md#landed-cost-vendor-invoice) | Landed Cost Vendor Invoice | enfant |  |  |  |
| [`Material Request Item`](../reference/stock.md#material-request-item) | Material Request Item | enfant |  |  |  |
| [`Packed Item`](../reference/stock.md#packed-item) | Packed Item | enfant |  |  |  |
| [`Packing Slip Item`](../reference/stock.md#packing-slip-item) | Packing Slip Item | enfant |  |  |  |
| [`Pick List Item`](../reference/stock.md#pick-list-item) | Pick List Item | enfant |  |  |  |
| [`Price List Country`](../reference/stock.md#price-list-country) | Price List Country | enfant |  |  |  |
| [`Purchase Receipt Item`](../reference/stock.md#purchase-receipt-item) | Purchase Receipt Item | enfant |  |  |  |
| [`Quality Inspection Reading`](../reference/stock.md#quality-inspection-reading) | Quality Inspection Reading | enfant |  |  |  |
| [`Serial and Batch Entry`](../reference/stock.md#serial-and-batch-entry) | Serial and Batch Entry | enfant |  |  |  |
| [`Shipment Delivery Note`](../reference/stock.md#shipment-delivery-note) | Shipment Delivery Note | enfant |  |  |  |
| [`Shipment Parcel`](../reference/stock.md#shipment-parcel) | Shipment Parcel | enfant |  |  |  |
| [`Stock Entry Detail`](../reference/stock.md#stock-entry-detail) | Stock Entry Detail | enfant |  |  |  |
| [`Stock Reconciliation Item`](../reference/stock.md#stock-reconciliation-item) | Stock Reconciliation Item | enfant |  |  |  |
| [`UOM Conversion Detail`](../reference/stock.md#uom-conversion-detail) | UOM Conversion Detail | enfant |  |  |  |
| [`Variant Field`](../reference/stock.md#variant-field) | Variant Field | enfant |  |  |  |
| [`Delivery Note`](../reference/stock.md#delivery-note) | Delivery Note | pièce | oui | `DN-{YYYY}-{#####}` |  |
| [`Delivery Trip`](../reference/stock.md#delivery-trip) | Delivery Trip | pièce | oui | `DT-{YYYY}-{#####}` |  |
| [`Item Standard Cost`](../reference/stock.md#item-standard-cost) | Item Standard Cost | pièce | oui | `ISC-{YYYY}-{#####}` |  |
| [`Landed Cost Voucher`](../reference/stock.md#landed-cost-voucher) | Landed Cost Voucher | pièce | oui | `LCV-{YYYY}-{#####}` |  |
| [`Material Request`](../reference/stock.md#material-request) | Material Request | pièce | oui | `MR-{YYYY}-{#####}` | workflow |
| [`Packing Slip`](../reference/stock.md#packing-slip) | Packing Slip | pièce | oui | `PS-{YYYY}-{#####}` |  |
| [`Pick List`](../reference/stock.md#pick-list) | Pick List | pièce | oui | `PL-{YYYY}-{#####}` |  |
| [`Purchase Receipt`](../reference/stock.md#purchase-receipt) | Purchase Receipt | pièce | oui | `PURE-{YYYY}-{#####}` |  |
| [`Quality Inspection`](../reference/stock.md#quality-inspection) | Quality Inspection | pièce | oui | `QI-{YYYY}-{#####}` |  |
| [`Repost Item Valuation`](../reference/stock.md#repost-item-valuation) | Repost Item Valuation | pièce | oui | `RIV-{YYYY}-{#####}` |  |
| [`Serial and Batch Bundle`](../reference/stock.md#serial-and-batch-bundle) | Serial and Batch Bundle | pièce | oui | `SBB-{YYYY}-{#####}` |  |
| [`Shipment`](../reference/stock.md#shipment) | Shipment | pièce | oui | `SHIP-{YYYY}-{#####}` |  |
| [`Stock Closing Entry`](../reference/stock.md#stock-closing-entry) | Stock Closing Entry | pièce | oui | `SCE-{YYYY}-{#####}` |  |
| [`Stock Entry`](../reference/stock.md#stock-entry) | Stock Entry | pièce | oui | `SE-{YYYY}-{#####}` |  |
| [`Stock Ledger Entry`](../reference/stock.md#stock-ledger-entry) | Stock Ledger Entry | pièce | oui | `SLE-{YYYY}-{#####}` |  |
| [`Stock Reconciliation`](../reference/stock.md#stock-reconciliation) | Stock Reconciliation | pièce | oui | `STRE-{YYYY}-{#####}` |  |
| [`Stock Reservation Entry`](../reference/stock.md#stock-reservation-entry) | Stock Reservation Entry | pièce | oui | `SRE-{YYYY}-{#####}` |  |
| [`Delivery Settings`](../reference/stock.md#delivery-settings) | Delivery Settings | unique |  |  |  |
| [`Item Variant Settings`](../reference/stock.md#item-variant-settings) | Item Variant Settings | unique |  |  |  |
| [`Stock Reposting Settings`](../reference/stock.md#stock-reposting-settings) | Stock Reposting Settings | unique |  |  |  |
| [`Stock Settings`](../reference/stock.md#stock-settings) | Stock Settings | unique |  |  |  |

## Points clés

- **Le registre est immuable** : `Stock Ledger Entry` (SLE-) enregistre chaque mouvement (entrée/sortie, `voucher_type`/`voucher_no` en `DynamicLink`), fermé à l'écriture humaine ; `Bin` porte le solde courant par (article, entrepôt) — maintenu par les hooks, jamais édité. Vérification : la balance se recompte depuis le registre.
- **Les pièces de mouvement** : `Stock Entry` (SE-, transfert/réception/retour par `Stock Entry Type`), `Purchase Receipt` (PURE-, réception fournisseur), `Delivery Note` (DN-, livraison client), `Material Request` (MR-, **workflow d'approbation**), `Stock Reconciliation` (STRE-, inventaire), `Pick List` (PL-, prélèvement), `Landed Cost Voucher` (LCV-, frais d'approche), `Stock Closing Entry` (SCE-, clôture d'inventaire).
- **Les objets suivis** : `Item` (le référentiel central — variantes par `Item Attribute`, codes-barres, fournisseurs, réapprovisionnement), `Warehouse` (arborescent), `Batch` (BATCH-), `Serial No`, `Serial and Batch Bundle` (SBB-, le paquet de traçabilité).
- **Logistique aval** : `Delivery Trip` (DT-, tournées), `Packing Slip` (PS-), `Shipment` (SHIP-, expédition).
- **La valorisation** au coût moyen pondéré est la règle du projet (`process/plan-erp.md`) : `Item Standard Cost` (ISC-) et `Repost Item Valuation` (RIV-) servent le recalcul.
- **La qualité à la réception** : `Quality Inspection` (QI-, avec lectures paramétrées) se déclenche sur les pièces d'entrée.

## Dépendances

- **Dépend de** : `setup` (131 liens), `accounts` (57), `selling` (18), `buying` (14), `manufacturing` (12), `crm` (10), `projects` (10), `assets` (8), `subcontracting` (3), `communication` (1).
- **Requis par** : `accounts` (54), `selling` (22), `subcontracting` (44), `manufacturing` (77), `buying` (25), `maintenance` (5), `hr` (1), `crm` (1), `regional` (2), `setup` (13), `support` (2).

Détail complet : [matrice](../dependances.md#stock-stock).

## Implémentation en plugin xcore

- Plugin `stock`, **P2, juste après `accounts`** — le plugin de référence existe dans le dépôt moteur (`tests/support/plugins/stock`) : registre en écriture seule, soldes `Bin` par `tx.ensure` et verrou trié, **stock négatif refusé sous concurrence**, annulation par écritures inverses (`.rev`), pas de retour en arrière dans le temps.
- **`cancel_ignores`** : `Stock Entry` doit ignorer `Stock Ledger Entry` pour pouvoir annuler ses propres lignes de registre (M2).
- **Hooks à écrire** : écriture du registre à la soumission de chaque pièce (SE, PURE, DN, STRE…), maintien de `Bin`, contrôle de disponibilité, traçabilité lots/séries via `Serial and Batch Bundle`, valorisation au coût moyen pondéré à chaque entrée.
- Les réceptions/livraisons portent les lignes fiscales (`Item Tax` vers `accounts`) : la comptabilisation passe par le plugin `accounts`.

## Référence complète

[Référence — Stock](../reference/stock.md).
