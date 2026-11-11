# Référence des champs — Fabrication (`manufacturing`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `manufacturing/` (49 DocTypes). Ne pas éditer à la main : relancer le script.

712 champs au total ; types les plus fréquents : `Link` (199), `Boolean` (98), `Decimal` (79), `Text` (56), `Currency` (47).

## Blanket Order

*Blanket Order* — `manufacturing/blanket_order.yaml` · soumis

- **Numérotation** : série `BO-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `customer`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — MFG-BLR-.YYYY.- | **requis** |
| `blanket_order_type` | Order Type | Select — Selling · Purchasing | **requis**; colonne de liste |
| `customer` | Customer | Link → `Customer` |  |
| `customer_name` | Customer Name | Text | lecture seule; recopié de `customer.customer_name` |
| `supplier` | Supplier | Link → `Supplier` |  |
| `supplier_name` | Supplier Name | Text | lecture seule; recopié de `supplier.supplier_name` |
| `from_date` | From Date | Date | **requis** |
| `to_date` | To Date | Date | **requis** |
| `company` | Company | Link → `Company` | **requis** |
| `status` | Status | Select — Draft · Submitted · Closed · Cancelled | lecture seule; défaut `Draft` |
| `currency` | Currency | Link → `Currency` | **requis** |
| `conversion_rate` | Exchange Rate | Number | **requis**; — Rate at which document currency is converted to company currency |
| `selling_price_list` | Price List | Link → `Price List` |  |
| `buying_price_list` | Price List | Link → `Price List` |  |
| `price_list_currency` | Price List Currency | Link → `Currency` | lecture seule |
| `plc_conversion_rate` | Price List Exchange Rate | Number | — Rate at which Price List Currency is converted to Company Currency |
| `items` | Item | Table → `Blanket Order Item` |  |
| `tc_name` | Terms | Link → `Terms and Conditions` |  |
| `terms` | Terms and Conditions Details | TextEditor |  |
| `order_no` | Order No | Text |  |
| `order_date` | Order Date | Date |  |

## Blanket Order Item

*Blanket Order Item* — `manufacturing/blanket_order_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Item Name | Text | recopié de `item_code.item_name` |
| `qty` | Quantity | Decimal | colonne de liste |
| `stock_uom` | Stock UOM | Link → `UOM` | colonne de liste; lecture seule |
| `price_list_rate` | Price List Rate | Currency | lecture seule; devise de `parent_currency` |
| `base_price_list_rate` | Price List Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `rate` | Rate | Currency | **requis**; colonne de liste; devise de `parent_currency` |
| `base_rate` | Rate (Company Currency) | Currency | **requis**; lecture seule; devise de `parent_company.default_currency` |
| `ordered_qty` | Ordered Quantity | Decimal | colonne de liste; lecture seule |
| `closed` | Closed | Boolean | lecture seule |
| `terms_and_conditions` | Terms and Conditions | LongText |  |
| `party_item_code` | Party Item Code | Text | lecture seule |

## BOM

*BOM* — `manufacturing/bom.yaml` · soumis

- **Numérotation** : série `BOM-{YYYY}-{#####}`
- **Titre** : `item_name`
- **Icône** : `list-tree`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item` | Item to manufacture | Link → `Item` | **requis**; colonne de liste; — The final item that will be produced using this BOM. |
| `item_name` | Item name | Text | lecture seule; recopié de `item.item_name` |
| `image` | Image | Image | lecture seule; masqué |
| `uom` | Unit of Measure | Link → `UOM` | lecture seule |
| `set_qty_based_on_percentage` | Set component quantities based on percentage | Boolean | défaut `non`; — Component quantities are derived from their percentage of the Output Qty. One component row can be marked as B |
| `quantity` | Quantity (Output Qty) | Decimal | **requis**; défaut `1.000`; — How many units of the final product this BOM makes. |
| `is_active` | Is active | Boolean | colonne de liste; défaut `oui` |
| `is_default` | Set as default | Boolean | colonne de liste; défaut `oui`; — This BOM will be selected by default in Work Orders etc. when the Item is selected. |
| `with_operations` | With Operations | Boolean | défaut `non`; — Manage cost of operations |
| `inspection_required` | Quality Inspection required | Boolean | défaut `non` |
| `allow_alternative_item` | Allow alternative raw material | Boolean | défaut `non`; — Enable this to select an alternative material when the required item is unavailable. |
| `quality_inspection_template` | Quality Inspection Template | Link → `Quality Inspection Template` |  |
| `company` | Company | Link → `Company` | **requis** |
| `transfer_material_against` | Transfer material against | Select — Work Order · Job Card | défaut `Work Order` |
| `conversion_rate` | Conversion rate | Number | **requis**; défaut `1.0` |
| `currency` | Currency | Link → `Currency` | **requis** |
| `rm_cost_as_per` | Rate of Materials based on | Select — Valuation Rate · Last Purchase Rate · Price List | défaut `Valuation Rate` |
| `buying_price_list` | Price List | Link → `Price List` |  |
| `routing` | Routing | Link → `Routing` |  |
| `operations` | Operations | Table → `BOM Operation` |  |
| `items` | Items | Table → `BOM Item` |  |
| `operating_cost` | Operating Cost | Currency | lecture seule; devise de `currency` |
| `raw_material_cost` | Raw Material Cost | Currency | lecture seule; devise de `currency` |
| `base_operating_cost` | Operating Cost (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_raw_material_cost` | Raw Material Cost (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `total_cost` | Total Cost | Currency | colonne de liste; lecture seule; devise de `currency` |
| `base_total_cost` | Total Cost (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `project` | Project | Link → `Project` |  |
| `description` | Item Description | TextEditor | lecture seule |
| `exploded_items` | Exploded Items | Table → `BOM Explosion Item` | lecture seule |
| `show_in_website` | Show in Website | Boolean | défaut `non` |
| `route` | Route | LongText | lecture seule |
| `website_image` | Website Image | Image | — Item Image (if not slideshow) |
| `thumbnail` | Thumbnail | Text | lecture seule |
| `web_long_description` | Website Description | TextEditor |  |
| `show_items` | Show Items | Boolean | défaut `non` |
| `show_operations` | Show Operations | Boolean | défaut `non` |
| `plc_conversion_rate` | Price List Exchange Rate | Number |  |
| `price_list_currency` | Price List Currency | Link → `Currency` | lecture seule |
| `has_variants` | Has variants | Boolean | colonne de liste; lecture seule; masqué |
| `process_loss_percentage` | % Process loss | Percent |  |
| `process_loss_qty` | Process loss qty | Decimal | lecture seule |
| `fg_based_operating_cost` | Finished goods based operating cost | Boolean | défaut `non` |
| `operating_cost_per_bom_quantity` | Operating cost per BOM quantity | Currency | devise de `currency` |
| `bom_creator` | BOM Creator | Link → `BOM Creator` | lecture seule |
| `bom_creator_item` | BOM Creator Item | Text | lecture seule |
| `track_semi_finished_goods` | Produce Item per Operation | Boolean | défaut `non`; — Each operation produces its own output item and puts it in stock, for example Cut Sheet, then Painted Sheet, t |
| `default_source_warehouse` | Default Source Warehouse | Link → `Warehouse` |  |
| `default_target_warehouse` | Default Target Warehouse | Link → `Warehouse` |  |
| `is_phantom_bom` | Set as Phantom BOM | Boolean | défaut `non`; — Enable this to define the BOM as a logical grouping of raw materials without producing an item. The Production |
| `secondary_items` | Secondary Items | Table → `BOM Secondary Item` |  |
| `secondary_items_cost` | Secondary Items Cost | Currency | lecture seule; devise de `currency` |
| `base_secondary_items_cost` | Secondary Items Cost (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `cost_allocation` | Cost allocation for Finished Good | Currency | lecture seule; devise de `currency` |
| `cost_allocation_per` | % Cost allocation for Finished Good | Percent | lecture seule |
| `backflush_based_on` | Based on | Select — BOM · Material Transferred for Manufacture | — Controls how raw materials are consumed during the ‘Manufacture’ stock entry. |

## BOM Creator

*BOM Creator* — `manufacturing/bom_creator.yaml` · soumis

- **Numérotation** : série `BC-{YYYY}-{#####}`
- **Titre** : `item_code`
- **Icône** : `list-plus`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `design_name` | Design Name | Text |  |
| `item_code` | Finished Good | Link → `Item` | **requis**; colonne de liste |
| `company` | Company | Link → `Company` | **requis** |
| `design_file` | Design File | Attach | — STEP file (.step or .stp) or CSV file. A CSV file needs a Level or Item Number column, a Part Number or Part N |
| `track_semi_finished_goods` | Produce Item per Operation | Boolean | défaut `non`; — Each operation makes an item that a later operation can use. The last operation makes the finished good. |
| `qty` | Finished Good Quantity | Decimal | **requis**; défaut `1.000`; — The BOM of the finished good is made for this quantity. Part quantities are for one finished good. |
| `items` | Items | Table → `BOM Creator Item` | masqué |
| `operations` | Operations | Table → `BOM Creator Operation` | masqué |
| `materials` | Materials | Table → `BOM Creator Material` | masqué |
| `rm_cost_as_per` | Rate Of Materials Based On | Select — Valuation Rate · Last Purchase Rate · Price List | **requis**; défaut `Valuation Rate` |
| `buying_price_list` | Price List | Link → `Price List` |  |
| `price_list_currency` | Price List Currency | Link → `Currency` | lecture seule |
| `plc_conversion_rate` | Price List Exchange Rate | Number |  |
| `set_rate_based_on_warehouse` | Set Valuation Rate Based on Source Warehouse | Boolean | défaut `non` |
| `default_warehouse` | Default Source Warehouse | Link → `Warehouse` |  |
| `currency` | Currency | Link → `Currency` | **requis** |
| `conversion_rate` | Conversion Rate | Number | défaut `1.0` |
| `raw_material_cost` | Total Cost | Currency | colonne de liste; lecture seule; devise de `currency` |
| `naming_series` | Series | Select — BOM-CRE-.YYYY.- | **requis**; masqué; défaut `BOM-CRE-.YYYY.-` |
| `item_group` | Item Group for New Items | Link → `Item Group` | — Item group of the items created from design parts. |
| `part_number` | Part Number | Text | — Part number of the top assembly in the design file. |
| `project` | Project | Link → `Project` |  |
| `is_phantom` | Is Phantom BOM | Boolean | défaut `non` |
| `routing` | Routing | Link → `Routing` | — The BOM of the finished good gets its operations from this routing. |
| `revision` | Revision | Int | colonne de liste; lecture seule |
| `previous_revision` | Previous Revision | Link → `BOM Creator` | lecture seule |
| `item_name` | Item Name | Text | lecture seule; masqué; recopié de `item_code.item_name` |
| `uom` | UOM | Link → `UOM` | lecture seule; masqué |
| `status` | Status | Select — Draft · Submitted · In Progress · Completed · Failed · Superseded · Cancelled | colonne de liste; lecture seule; défaut `Draft` |
| `remarks` | Remarks | TextEditor |  |
| `error_log` | Error Log | LongText | lecture seule |

## BOM Creator Item

*BOM Creator Item* — `manufacturing/bom_creator_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `part_number` | Part Number | Text | colonne de liste |
| `part_name` | Part Name | Text |  |
| `qty` | Quantity | Decimal | colonne de liste; défaut `1.000` |
| `design_quantity` | Design Quantity | Decimal | lecture seule; — Quantity from the design file. |
| `node_id` | Node | Int | lecture seule |
| `is_expandable` | Is Assembly | Boolean | lecture seule |
| `source` | Source | Select — CAD File · Manual | lecture seule; défaut `Manual` |
| `change_type` | Change | Select — Added · Quantity Changed | colonne de liste; lecture seule |
| `exclude_from_bom` | Exclude from BOM | Boolean | défaut `non` |
| `description` | Description | LongText |  |
| `item_code` | Item Code | Link → `Item` | colonne de liste |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `item_group` | Item Group | Link → `Item Group` | lecture seule |
| `is_phantom_item` | Is Phantom Item | Boolean | défaut `non` |
| `sourced_by_supplier` | Sourced by Supplier | Boolean | défaut `non` |
| `bom_created` | BOM Created | Boolean | masqué; défaut `non` |
| `uom` | UOM | Link → `UOM` | colonne de liste |
| `stock_qty` | Stock Qty | Decimal | lecture seule |
| `conversion_factor` | Conversion Factor | Number |  |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `rate` | Rate | Currency | lecture seule; devise de `parent_currency` |
| `amount` | Amount | Currency | lecture seule; devise de `parent_currency` |
| `base_rate` | Base Rate | Currency | masqué; devise de `parent_company.default_currency` |
| `base_amount` | Base Amount | Currency | masqué; devise de `parent_company.default_currency` |
| `do_not_explode` | Do Not Explode | Boolean | défaut `oui`; — Use the item as a raw material without its own BOM. |
| `bom_no` | BOM No | Link → `BOM` |  |
| `operation` | Operation | Link → `Operation` | — Operation of the routing that uses this material. |
| `instruction` | Instruction | LongText |  |
| `placements` | Placements in Model | JSON | masqué |

## BOM Creator Material

*BOM Creator Material* — `manufacturing/bom_creator_material.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `bom_node_id` | BOM Node | Int | défaut `0`; — Node of the design part. 0 means the finished good. |
| `operation_id` | Operation ID | Int |  |
| `from_operation_id` | Output of Operation ID | Int |  |
| `part_node_id` | Part Node | Int | colonne de liste |
| `item_code` | Item Code | Link → `Item` | colonne de liste |
| `qty` | Quantity | Decimal | **requis**; colonne de liste |
| `uom` | UOM | Link → `UOM` | colonne de liste |

## BOM Creator Operation

*BOM Creator Operation* — `manufacturing/bom_creator_operation.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `operation_id` | Operation ID | Int | lecture seule |
| `bom_node_id` | BOM Node | Int | défaut `0`; — Node of the design part. 0 means the finished good. |
| `operation` | Operation | Link → `Operation` | **requis**; colonne de liste |
| `workstation_type` | Workstation Type | Link → `Workstation Type` | colonne de liste |
| `time_in_mins` | Operation Time (Minutes) | Number | colonne de liste |
| `output_node_id` | Output Node | Int |  |
| `output_item` | Output Item | Link → `Item` | colonne de liste |
| `output_quantity` | Output Quantity | Decimal | défaut `1.000` |

## BOM Explosion Item

*BOM Explosion Item* — `manufacturing/bom_explosion_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | colonne de liste; lecture seule |
| `item_name` | Item Name | Text | colonne de liste; lecture seule; recopié de `item_code.item_name` |
| `source_warehouse` | Source Warehouse | Link → `Warehouse` | lecture seule |
| `operation` | Operation | Link → `Operation` | lecture seule |
| `description` | Description | TextEditor | colonne de liste; lecture seule |
| `stock_qty` | Stock Qty | Decimal | colonne de liste; lecture seule |
| `rate` | Rate | Currency | colonne de liste; lecture seule; devise de `parent_currency` |
| `qty_consumed_per_unit` | Qty Consumed Per Unit | Decimal | colonne de liste; lecture seule |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `amount` | Amount | Currency | colonne de liste; lecture seule; devise de `parent_currency` |
| `include_item_in_manufacturing` | Include Item In Manufacturing | Boolean | lecture seule |
| `sourced_by_supplier` | Sourced by Supplier | Boolean | lecture seule |
| `is_sub_assembly_item` | Is Sub Assembly Item | Boolean | lecture seule |

## BOM Item

*BOM Item* — `manufacturing/bom_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Item name | Text | recopié de `item_code.item_name` |
| `operation` | Item operation | Link → `Operation` |  |
| `bom_no` | BOM No | Link → `BOM` |  |
| `set_rate_of_sub_assembly_item_based_on_bom` | Set rate based on sub-assembly BOM | Boolean | défaut `oui`; — Cost this sub-assembly by rolling up its BOM cost instead of the item's own valuation or price-list rate. Appl |
| `source_warehouse` | Source Warehouse | Link → `Warehouse` |  |
| `description` | Item Description | TextEditor |  |
| `percentage` | Percentage (%) | Percent | colonne de liste |
| `qty` | Qty | Decimal | **requis**; colonne de liste |
| `uom` | UOM | Link → `UOM` | **requis**; colonne de liste |
| `stock_qty` | Stock Qty | Decimal | lecture seule |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `conversion_factor` | Conversion Factor | Number |  |
| `rate` | Rate | Currency | **requis**; colonne de liste; devise de `parent_currency` |
| `base_rate` | Basic Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `amount` | Amount | Currency | colonne de liste; lecture seule; devise de `parent_currency` |
| `base_amount` | Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `qty_consumed_per_unit` | Qty Consumed Per Unit | Decimal | lecture seule; masqué |
| `allow_alternative_item` | Allow Alternative Item | Boolean | défaut `non`; — Allow this component to be swapped for a defined alternative during production. Copied from the item's setting |
| `include_item_in_manufacturing` | Include Item in manufacturing | Boolean | défaut `non` |
| `original_item` | Original Item | Link → `Item` | lecture seule; masqué |
| `has_variants` | Has variants | Boolean | lecture seule; masqué |
| `sourced_by_supplier` | Sourced by Supplier | Boolean | défaut `non` |
| `do_not_explode` | Do not explode | Boolean | défaut `non`; — A sub-assembly is a component with its own BOM. By default it's broken down into its own raw materials; enable |
| `is_stock_item` | Is stock Item | Boolean | lecture seule |
| `operation_row_id` | Operation ID | Int |  |
| `is_sub_assembly_item` | Is sub assembly Item | Boolean | lecture seule; masqué; — Set automatically when this component is a semi-finished good produced by an operation in this BOM. It's made  |
| `is_phantom_item` | Is Phantom Item | Boolean | lecture seule; masqué; — When this is enabled it defines the BOM as a logical grouping of raw materials without producing an item. The  |
| `is_balance_item` | Is Balance Item | Boolean | défaut `non`; — This component absorbs the percentage remaining after all other percentage rows |

## BOM Operation

*BOM Operation* — `manufacturing/bom_operation.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `operation` | Operation | Link → `Operation` | **requis**; colonne de liste |
| `workstation` | Workstation | Link → `Workstation` |  |
| `description` | Description | TextEditor |  |
| `hour_rate` | Hour rate | Currency |  |
| `time_in_mins` | Operation time | Number | **requis**; colonne de liste; — In minutes |
| `fixed_time` | Fixed time | Boolean | défaut `non`; — Operation time does not depend on quantity to produce |
| `operating_cost` | Operating cost | Currency | lecture seule |
| `base_hour_rate` | Base hour rate(Company Currency) | Currency | lecture seule |
| `base_operating_cost` | Operating cost(Company Currency) | Currency | lecture seule |
| `batch_size` | Batch size | Number | défaut `1.0` |
| `sequence_id` | Sequence ID | Int | colonne de liste; — If you want to run operations in parallel, keep the same sequence ID for them. |
| `cost_per_unit` | Cost per Unit | Number | lecture seule |
| `base_cost_per_unit` | Base Cost per Unit | Number | lecture seule; masqué |
| `set_cost_based_on_bom_qty` | Set operating cost based on BOM Quantity | Boolean | défaut `non` |
| `workstation_type` | Workstation Type | Link → `Workstation Type` | colonne de liste |
| `finished_good` | Output Item | Link → `Item` | colonne de liste |
| `bom_no` | Output Item BOM | Link → `BOM` | colonne de liste; — Pick a BOM to copy its raw materials into this step. Leave it empty to add the raw materials yourself with Add |
| `finished_good_qty` | Output Qty | Decimal | colonne de liste; défaut `1.000` |
| `is_final_finished_good` | Last Step | Boolean | défaut `non`; — Tick this on the step that makes this BOM's own item. The other steps make in-between items. |
| `wip_warehouse` | WIP Warehouse | Link → `Warehouse` |  |
| `fg_warehouse` | Finished Goods Warehouse | Link → `Warehouse` |  |
| `source_warehouse` | Source Warehouse | Link → `Warehouse` |  |
| `is_subcontracted` | Is Subcontracted | Boolean | défaut `non` |
| `skip_material_transfer` |  Skip Material Transfer | Boolean | défaut `non` |
| `backflush_from_wip_warehouse` | Backflush materials from WIP Warehouse | Boolean | défaut `non` |
| `quality_inspection_required` | Quality Inspection required | Boolean | défaut `non` |
| `batch_split` | Batch split | Boolean | défaut `non`; — On completion of the Job Card, split the consumed batch into one child batch per finished piece |
| `weight_per_piece` | Weight per piece | Number | — Produced quantity is split into one batch per this many units of the finished good |

## BOM Secondary Item

*BOM Secondary Item* — `manufacturing/bom_secondary_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `secondary_item_type` | Type | Select — Co-Product · By-Product · Scrap · Additional Finished Good | **requis**; colonne de liste |
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Item Name | Text | colonne de liste; lecture seule; recopié de `item_code.item_name` |
| `cost` | Cost | Currency | **requis**; devise de `parent_currency` |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `uom` | UOM | Link → `UOM` | **requis**; colonne de liste |
| `conversion_factor` | Conversion Factor | Number | **requis**; défaut `1.0` |
| `stock_qty` | Stock Qty | Decimal | lecture seule |
| `qty` | Qty | Decimal | colonne de liste |
| `cost_allocation_per` | Cost Allocation % | Percent | **requis**; défaut `0.0` |
| `process_loss_per` | Process Loss % | Percent | **requis**; défaut `0.0` |
| `description` | Description | TextEditor |  |
| `base_cost` | Base Cost (Company Currency) | Currency | **requis**; lecture seule; masqué; devise de `parent_company.default_currency` |
| `valuation_type` | Valuation Type | Select — Valuation Rate · % of Component Cost · Manual | **requis**; défaut `Valuation Rate`; — Valuation Rate and Manual value this item on its own and deduct that cost from the raw material cost, like the |
| `process_loss_qty` | Process Loss Qty | Decimal | **requis**; lecture seule |

## BOM Update Batch

*BOM Update Batch* — `manufacturing/bom_update_batch.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `level` | Level | Int | colonne de liste |
| `batch_no` | Batch No. | Int | colonne de liste |
| `boms_updated` | BOMs Updated | LongText | colonne de liste; masqué |
| `status` | Status | Select — Pending · Completed | colonne de liste; lecture seule |

## BOM Update Log

*BOM Update Log* — `manufacturing/bom_update_log.yaml` · soumis

- **Numérotation** : série `BUL-{YYYY}-{#####}`
- **Titre** : `status`
- **Icône** : `file-clock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `current_bom` | Current BOM | Link → `BOM` | colonne de liste |
| `new_bom` | New BOM | Link → `BOM` | colonne de liste |
| `update_type` | Update Type | Select — Replace BOM · Update Cost | colonne de liste |
| `status` | Status | Select — Queued · In Progress · Completed · Failed · Cancelled |  |
| `error_log` | Error Log | Link → `Error Log` |  |
| `processed_boms` | Processed BOMs | LongText | masqué |
| `bom_batches` | Bom Batches | Table → `BOM Update Batch` |  |
| `current_level` | Current Level | Int |  |

## BOM Update Tool

*BOM Update Tool* — `manufacturing/bom_update_tool.yaml`

- **Titre** : `current_bom`
- **Icône** : `refresh-cw`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `current_bom` | Current BOM | Link → `BOM` | **requis**; colonne de liste; — The BOM which will be replaced |
| `new_bom` | New BOM | Link → `BOM` | **requis**; colonne de liste; — The new BOM after replacement |

## Downtime Entry

*Downtime Entry* — `manufacturing/downtime_entry.yaml`

- **Titre** : `operator`
- **Icône** : `clock-alert`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `workstation` | Workstation / Machine | Link → `Workstation` | **requis** |
| `from_time` | From Time | Datetime | **requis**; colonne de liste |
| `to_time` | To Time | Datetime | **requis**; colonne de liste |
| `operator` | Operator | Link → `Employee` | **requis**; colonne de liste |
| `downtime` | Downtime | Number | lecture seule; — In Mins |
| `stop_reason` | Stop Reason | Select — Excessive machine set up time · Unplanned machine maintenance · On-machine press checks · Machine operator errors · Machine malfunction · Electricity down · Other | **requis** |
| `remarks` | Remarks | LongText |  |
| `naming_series` | Naming Series | Select — DT- | **requis** |

## Job Card

*Job Card* — `manufacturing/job_card.yaml` · soumis

- **Numérotation** : série `JC-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `item_name`
- **Icône** : `clipboard-list`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `work_order` | Work Order | Link → `Work Order` | **requis**; colonne de liste |
| `bom_no` | Final BOM | Link → `BOM` | lecture seule |
| `workstation` | Workstation | Link → `Workstation` | **requis**; colonne de liste |
| `operation` | Operation | Link → `Operation` | **requis**; colonne de liste |
| `posting_date` | Posting Date | Date | défaut `today` |
| `company` | Company | Link → `Company` | **requis** |
| `for_quantity` | Qty to Manufacture | Decimal | colonne de liste |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `wip_warehouse` | WIP Warehouse | Link → `Warehouse` |  |
| `time_logs` | Time Logs | Table → `Job Card Time Log` |  |
| `total_completed_qty` | Total Completed qty | Decimal | lecture seule |
| `total_time_in_mins` | Total Time in Mins | Number | lecture seule |
| `items` | Items | Table → `Job Card Item` |  |
| `operation_id` | Operation ID | Text | lecture seule; masqué |
| `transferred_qty` | Transferred Raw Materials | Decimal | lecture seule |
| `requested_qty` | Requested Qty | Decimal | lecture seule |
| `project` | Project | Link → `Project` |  |
| `remarks` | Remarks | LongText |  |
| `status` | Status | Select — Open · Work In Progress · Partially Transferred · Material Transferred · On Hold · Submitted · To Manufacture · Cancelled · Completed | lecture seule; défaut `Open` |
| `naming_series` | Naming Series | Select — PO-JOB.##### | **requis**; défaut `PO-JOB.#####` |
| `production_item` | Final Product | Link → `Item` | lecture seule |
| `item_name` | Item Name | Text | lecture seule |
| `sequence_id` | Sequence Id | Int | lecture seule |
| `quality_inspection` | Quality Inspection | Link → `Quality Inspection` |  |
| `sub_operations` | Sub Operations | Table → `Job Card Operation` | lecture seule |
| `hour_rate` | Hour Rate | Currency | devise de `company.default_currency` |
| `is_corrective_job_card` | Is Corrective Job Card | Boolean | lecture seule |
| `for_job_card` | For Job Card | Link → `Job Card` | lecture seule |
| `for_operation` | For Operation | Link → `Operation` |  |
| `employee` | Employee | Table → `Job Card Time Log` | lecture seule |
| `serial_no` | Serial No | LongText | lecture seule; masqué |
| `batch_no` | Batch No | Link → `Batch` | lecture seule; masqué |
| `quality_inspection_template` | Quality Inspection Template | Link → `Quality Inspection Template` |  |
| `workstation_type` | Workstation Type | Link → `Workstation Type` |  |
| `expected_start_date` | Expected Start Date | Datetime |  |
| `expected_end_date` | Expected End Date | Datetime |  |
| `serial_and_batch_bundle` | Serial and Batch Bundle | Link → `Serial and Batch Bundle` | lecture seule |
| `process_loss_qty` | Process Loss qty | Decimal | lecture seule |
| `time_required` | Expected Time Required (In Mins) | Number |  |
| `scheduled_time_logs` | Scheduled Time Logs | Table → `Job Card Scheduled Time` | lecture seule |
| `actual_start_date` | Actual Start Date | Datetime | lecture seule |
| `actual_end_date` | Actual End Date | Datetime | lecture seule |
| `finished_good` | Item to Manufacture | Link → `Item` | lecture seule |
| `target_warehouse` | Target Warehouse | Link → `Warehouse` |  |
| `operation_row_id` | Operation Row ID | Int |  |
| `source_warehouse` | Source Warehouse | Link → `Warehouse` |  |
| `semi_fg_bom` | Manufacturing BOM | Link → `BOM` | lecture seule |
| `batch_split` | Batch Split | Boolean | lecture seule; masqué |
| `weight_per_piece` | Weight Per Piece | Number | lecture seule |
| `is_subcontracted` | Is Subcontracted | Boolean | lecture seule |
| `manufactured_qty` | Manufactured Qty | Decimal | lecture seule |
| `skip_material_transfer` | Skip Material Transfer to WIP | Boolean | défaut `non` |
| `backflush_from_wip_warehouse` | Backflush Materials from WIP Warehouse | Boolean | défaut `non` |
| `is_paused` | Is Paused | Boolean | lecture seule; masqué |
| `track_semi_finished_goods` | Produce Item per Operation | Boolean | lecture seule; masqué; — Each operation produces its own output item and puts it in stock, for example Cut Sheet, then Painted Sheet, t |
| `secondary_items` | Secondary Items | Table → `Job Card Secondary Item` |  |
| `pending_qty` | Pending qty | Decimal |  |

## Job Card Item

*Job Card Item* — `manufacturing/job_card_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `source_warehouse` | Source Warehouse | Link → `Warehouse` | colonne de liste |
| `uom` | UOM | Link → `UOM` |  |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `description` | Description | TextEditor | lecture seule |
| `required_qty` | Required Qty | Decimal | colonne de liste |
| `allow_alternative_item` | Allow Alternative Item | Boolean | défaut `non` |
| `item_group` | Item Group | Link → `Item Group` | lecture seule |
| `stock_uom` | Stock UOM | Link → `UOM` |  |
| `transferred_qty` | Transferred Qty | Decimal | lecture seule |
| `consumed_qty` | Consumed Qty | Decimal | lecture seule |

## Job Card Operation

*Job Card Operation* — `manufacturing/job_card_operation.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `status` | Status | Select — Complete · Pause · Pending · Work In Progress | colonne de liste; lecture seule; défaut `Pending` |
| `completed_time` | Completed Time | Text | colonne de liste; lecture seule; — In mins |
| `sub_operation` | Operation | Link → `Operation` | colonne de liste; lecture seule |
| `completed_qty` | Completed Qty | Decimal | colonne de liste; lecture seule |

## Job Card Scheduled Time

*Job Card Scheduled Time* — `manufacturing/job_card_scheduled_time.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `from_time` | From Time | Datetime | colonne de liste |
| `to_time` | To Time | Datetime | colonne de liste |
| `time_in_mins` | Time (In Mins) | Number | colonne de liste |

## Job Card Secondary Item

*Job Card Secondary Item* — `manufacturing/job_card_secondary_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Secondary Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Secondary Item Name | Text | colonne de liste; recopié de `item_code.item_name` |
| `description` | Description | LongText | lecture seule |
| `stock_qty` | Qty | Decimal | **requis**; colonne de liste |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `secondary_item_type` | Type | Select — Co-Product · By-Product · Scrap · Additional Finished Good | **requis**; colonne de liste |
| `bom_secondary_item` | BOM Secondary Item Reference | Text | lecture seule; masqué |

## Job Card Time Log

*Job Card Time Log* — `manufacturing/job_card_time_log.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `from_time` | From Time | Datetime | colonne de liste |
| `to_time` | To Time | Datetime | colonne de liste |
| `time_in_mins` | Time In Mins | Number | colonne de liste |
| `completed_qty` | Completed Qty | Decimal | colonne de liste; défaut `0.000` |
| `employee` | Employee | Link → `Employee` | colonne de liste |
| `operation` | Sub Operation | Link → `Operation` | colonne de liste |

## Manufacturing Settings

*Manufacturing Settings* — `manufacturing/manufacturing_settings.yaml` · document unique

- **Icône** : `settings`
- **Permissions explicites** — `create` : 0, `delete` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `allow_overtime` | Allow Overtime | Boolean | défaut `non`; — Plan time logs outside Workstation working hours |
| `allow_production_on_holidays` | Allow Production on Holidays | Boolean | colonne de liste; défaut `non` |
| `capacity_planning_for_days` | Capacity Planning For (Days) | Int | défaut `30`; — Plan operations X days in advance |
| `mins_between_operations` | Time Between Operations (Mins) | Int | défaut `10`; — Default: 10 mins |
| `overproduction_percentage_for_sales_order` | Overproduction Percentage For Sales Order | Percent |  |
| `overproduction_percentage_for_work_order` | Overproduction Percentage For Work Order | Percent |  |
| `backflush_raw_materials_based_on` | Backflush Raw Materials Based On | Select — BOM · Material Transferred for Manufacture | défaut `BOM` |
| `material_consumption` | Allow Continuous Material Consumption | Boolean | défaut `non`; — Allow material consumptions without immediately manufacturing finished goods against a Work Order |
| `update_bom_costs_automatically` | Update BOM Cost Automatically | Boolean | défaut `non`; — Update BOM cost automatically via scheduler, based on the latest Valuation Rate/Price List Rate/Last Purchase  |
| `disable_capacity_planning` | Disable Capacity Planning | Boolean | défaut `non` |
| `make_serial_no_batch_from_work_order` | Make Serial No / Batch from Work Order | Boolean | défaut `non`; — System will automatically create the serial numbers / batch for the Finished Good on submission of work order |
| `add_corrective_operation_cost_in_finished_good_valuation` | Add Corrective Operation Cost in Finished Good Valuation | Boolean | défaut `non` |
| `job_card_excess_transfer` | Allow Excess Material Transfer | Boolean | défaut `non`; — Allow transferring raw materials even after the Required Quantity is fulfilled |
| `get_rm_cost_from_consumption_entry` | Get Raw Materials Cost from Consumption Entry | Boolean | défaut `non` |
| `validate_components_quantities_per_bom` | Validate Components and Quantities Per BOM | Boolean | défaut `non` |
| `enforce_time_logs` | Enforce Time Logs | Boolean | défaut `non`; — Enabling this checkbox will force each Job Card Time Log to have From Time and To Time |
| `transfer_extra_materials_percentage` | Transfer Extra Raw Materials to WIP (%) | Percent | — The user will be able to transfer additional materials from the store to the Work in Progress (WIP) warehouse. |
| `allow_editing_of_items_and_quantities_in_work_order` | Allow Editing of Items and Quantities in Work Order | Boolean | défaut `non`; — If enabled, the system will allow users to edit the raw materials and their quantities in the Work Order. The  |
| `allow_alternative_finished_goods` | Allow Alternative Finished Goods | Boolean | défaut `non`; — If enabled, the produced item of a Work Order can be converted into one of its alternative items (defined via  |
| `set_op_cost_and_secondary_items_from_sub_assemblies` | Set Operating Cost / Secondary Items From Sub-assemblies | Boolean | défaut `non`; — To include sub-assembly costs and secondary items in Finished Goods on a work order without using a job card,  |

## Master Production Schedule

*Master Production Schedule* — `manufacturing/master_production_schedule.yaml`

- **Vues** : calendar, gantt
- **Titre** : `company`
- **Icône** : `calendar-range`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `items` | Items | Table → `Master Production Schedule Item` |  |
| `posting_date` | Posting Date | Date | **requis**; défaut `today` |
| `naming_series` | Naming Series | Select — MPS.YY.-.###### | **requis**; défaut `MPS.YY.-.######` |
| `parent_warehouse` | Parent Warehouse | Link → `Warehouse` | — For projected and forecast quantities, the system will consider all child warehouses under the selected parent |
| `from_date` | From Date | Date | **requis** |
| `to_date` | To Date | Date |  |
| `sales_orders` | Sales Orders | Table → `Production Plan Sales Order` |  |
| `material_requests` | Material Requests | Table → `Production Plan Material Request` |  |
| `sales_forecast` | Sales Forecast | Link → `Sales Forecast` |  |
| `select_items` | Select Items | Table → `Master Production Schedule Item` |  |

## Master Production Schedule Item

*Master Production Schedule Item* — `manufacturing/master_production_schedule_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | colonne de liste; lecture seule |
| `warehouse` | Warehouse | Link → `Warehouse` | lecture seule |
| `delivery_date` | Delivery Date | Date | colonne de liste; lecture seule |
| `planned_qty` | Planned Qty | Decimal | colonne de liste |
| `order_release_date` | Start Date | Date | colonne de liste |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `bom_no` | BOM No | Link → `BOM` | colonne de liste |
| `uom` | UOM | Link → `UOM` |  |
| `cumulative_lead_time` | Lead Time | Int | colonne de liste; lecture seule |

## Material Request Plan Item

*Material Request Plan Item* — `manufacturing/material_request_plan_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Item Name | Text | recopié de `item_code.item_name` |
| `warehouse` | For Warehouse | Link → `Warehouse` | **requis**; colonne de liste |
| `material_request_type` | Type | Select — Purchase · Material Transfer · Material Issue · Manufacture · Subcontracting · Customer Provided | colonne de liste |
| `supplier` | Supplier | Link → `Supplier` | colonne de liste |
| `quantity` | Required Qty | Decimal | **requis**; colonne de liste |
| `projected_qty` | Projected Qty | Decimal | colonne de liste; lecture seule |
| `actual_qty` | Qty In Stock | Decimal | lecture seule |
| `min_order_qty` | Minimum Order Quantity | Decimal | colonne de liste; lecture seule |
| `sales_order` | Sales Order | Link → `Sales Order` | lecture seule |
| `requested_qty` | Requested Qty | Decimal | lecture seule |
| `description` | Description | TextEditor |  |
| `uom` | UOM | Link → `UOM` | lecture seule |
| `from_warehouse` | From Warehouse | Link → `Warehouse` |  |
| `safety_stock` | Safety Stock | Number | lecture seule |
| `ordered_qty` | Ordered Qty | Decimal | lecture seule |
| `reserved_qty_for_production` | Reserved Qty for Production | Decimal | lecture seule |
| `required_bom_qty` | Reqd Qty (BOM) | Decimal | colonne de liste; lecture seule |
| `conversion_factor` | Conversion Factor | Number | lecture seule |
| `schedule_date` | Required By | Date | colonne de liste |
| `stock_reserved_qty` | Stock Reserved Qty | Decimal | lecture seule |
| `from_bom` | From BOM | Link → `BOM` | lecture seule |
| `sub_assembly_item_reference` | Sub Assembly Item Reference | Text | lecture seule; masqué |
| `main_item_code` | Main Item Code | Link → `Item` | lecture seule |

## Operation

*Operation* — `manufacturing/operation.yaml`

- **Titre** : `workstation`
- **Icône** : `cog`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `workstation` | Default Workstation | Link → `Workstation` | colonne de liste |
| `description` | Description | LongText |  |
| `work_instruction` | Work Instructions | TextEditor | — Shown to operators on the Shop Floor. Supports rich text and embedded images for step-by-step guidance. |
| `sub_operations` | Sub Operations | Table → `Sub Operation` |  |
| `total_operation_time` | Total Operation Time | Number | lecture seule; — Time in mins. |
| `batch_size` | Batch Size | Int | défaut `1` |
| `create_job_card_based_on_batch_size` | Create Job Card based on Batch Size | Boolean | défaut `non` |
| `is_corrective_operation` | Is Corrective Operation | Boolean | défaut `non` |
| `quality_inspection_template` | Quality Inspection Template | Link → `Quality Inspection Template` |  |

## Plant Floor

*Plant Floor* — `manufacturing/plant_floor.yaml`

- **Titre** : `company`
- **Icône** : `layout-grid`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `floor_name` | Floor Name | Text |  |
| `warehouse` | Warehouse | Link → `Warehouse` |  |
| `company` | Company | Link → `Company` |  |

## Production Plan

*Production Plan* — `manufacturing/production_plan.yaml` · soumis

- **Numérotation** : série `PP-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `item_code`
- **Icône** : `calendar-check`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Naming Series | Select — MFG-PP-.YYYY.- | **requis** |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `get_items_from` | Get Items From | Select — Sales Order · Material Request | colonne de liste |
| `posting_date` | Posting Date | Date | **requis**; colonne de liste; défaut `today` |
| `item_code` | Item Code | Link → `Item` | colonne de liste |
| `customer` | Customer | Link → `Customer` | colonne de liste |
| `warehouse` | Warehouse | Link → `Warehouse` |  |
| `project` | Project | Link → `Project` |  |
| `from_date` | From Date | Date |  |
| `to_date` | To Date | Date |  |
| `sales_orders` | Sales Orders | Table → `Production Plan Sales Order` |  |
| `material_requests` | Material Requests | Table → `Production Plan Material Request` |  |
| `po_items` | Assembly Items | Table → `Production Plan Item` |  |
| `include_non_stock_items` | Include Non Stock Items | Boolean | défaut `oui` |
| `include_subcontracted_items` | Include Subcontracted Items | Boolean | défaut `oui` |
| `ignore_existing_ordered_qty` | Consider Projected Qty in Calculation (RM) | Boolean | défaut `oui`; — If enabled, formula for <b>Required Qty</b>: <br> Required Qty (BOM) - <a href="https://docs.frappe.io/erpnext |
| `mr_items` | Raw Materials | Table → `Material Request Plan Item` |  |
| `total_planned_qty` | Total Planned Qty | Decimal | lecture seule |
| `total_produced_qty` | Total Produced Qty | Decimal | lecture seule |
| `status` | Status | Select — Draft · Submitted · Not Started · In Process · Completed · Closed · Cancelled · Material Requested | lecture seule; défaut `Draft` |
| `for_warehouse` | For Warehouse | Link → `Warehouse` |  |
| `raw_material_group_warehouse` | Raw Material Group Warehouse | Link → `Warehouse` | — Optional group warehouse. Raw material availability is checked across its child warehouses; material is still  |
| `warehouses` | Warehouses | Table → `Production Plan Material Request Warehouse` | lecture seule; masqué |
| `sales_order_status` | Sales Order Status | Select — To Deliver and Bill · To Bill · To Deliver |  |
| `include_safety_stock` | Include Safety Stock in Required Qty Calculation | Boolean | défaut `non` |
| `combine_items` | Consolidate Sales Order Items | Boolean | défaut `non` |
| `prod_plan_references` | Sales Order Reference | Table → `Production Plan Item Reference` | masqué |
| `sub_assembly_items` | Sub Assembly Items | Table → `Production Plan Sub Assembly Item` |  |
| `from_delivery_date` | From Delivery Date | Date |  |
| `to_delivery_date` | To Delivery Date | Date |  |
| `combine_sub_items` | Consolidate Sub Assembly Items | Boolean | défaut `non` |
| `skip_available_sub_assembly_item` | Consider Projected Qty in Calculation | Boolean | défaut `oui`; — If enabled, formula for <b>Qty to Order</b>: <br> Required Qty (BOM) - <a href="https://docs.frappe.io/erpnext |
| `sub_assembly_warehouse` | Sub Assembly Warehouse | Link → `Warehouse` | — When a parent warehouse is chosen, the system conducts Project Qty checks against the associated child warehou |
| `consider_minimum_order_qty` | Consider Minimum Order Qty | Boolean | défaut `non` |
| `reserve_stock` | Reserve Stock | Boolean | défaut `non` |
| `no_of_shifts` | No of Shifts | Int | — Used by scheduling when an item has no BOM operations: scales the Item Lead Time daily capacity to this many s |

## Production Plan Item

*Production Plan Item* — `manufacturing/production_plan_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `include_exploded_items` | Include Exploded Items | Boolean | défaut `oui` |
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `bom_no` | BOM No | Link → `BOM` | **requis**; colonne de liste |
| `planned_qty` | Planned Qty | Decimal | **requis**; colonne de liste |
| `warehouse` | Finished Goods Warehouse | Link → `Warehouse` | colonne de liste |
| `planned_start_date` | Planned Start Date | Datetime | **requis**; colonne de liste |
| `pending_qty` | Pending Qty | Decimal | lecture seule |
| `ordered_qty` | Ordered Qty | Decimal | lecture seule |
| `produced_qty` | Produced Qty | Decimal | lecture seule |
| `description` | Description | TextEditor | lecture seule |
| `stock_uom` | UOM | Link → `UOM` | **requis**; colonne de liste; lecture seule |
| `sales_order` | Sales Order | Link → `Sales Order` | lecture seule |
| `sales_order_item` | Sales Order Item | Text | masqué |
| `material_request` | Material Request | Link → `Material Request` | lecture seule |
| `material_request_item` | material_request_item | Text | masqué |
| `product_bundle_item` | Product Bundle Item | Link → `Item` | lecture seule |
| `item_reference` | Item Reference | Text | masqué |
| `temporary_name` | temporary name | Text | masqué |
| `planned_end_date` | Planned End Date | Datetime | lecture seule |

## Production Plan Item Reference

*Production Plan Item Reference* — `manufacturing/production_plan_item_reference.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `sales_order` | Sales Order Reference | Link → `Sales Order` | colonne de liste |
| `sales_order_item` | Sales Order Item | Text | colonne de liste |
| `qty` | Qty | Decimal | colonne de liste |
| `item_reference` | Item Reference | Text | colonne de liste |

## Production Plan Material Request

*Production Plan Material Request* — `manufacturing/production_plan_material_request.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `material_request` | Material Request | Link → `Material Request` | **requis**; colonne de liste |
| `material_request_date` | Material Request Date | Date | colonne de liste; lecture seule |

## Production Plan Material Request Warehouse

*Production Plan Material Request Warehouse* — `manufacturing/production_plan_material_request_warehouse.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `warehouse` | Warehouse | Link → `Warehouse` | colonne de liste |

## Production Plan Sales Order

*Production Plan Sales Order* — `manufacturing/production_plan_sales_order.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `sales_order` | Sales Order | Link → `Sales Order` | **requis**; colonne de liste |
| `sales_order_date` | Sales Order Date | Date | colonne de liste; lecture seule |
| `customer` | Customer | Link → `Customer` | colonne de liste; lecture seule |
| `grand_total` | Grand Total | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `status` | Status | Text | colonne de liste |

## Production Plan Schedule

*Production Plan Schedule* — `manufacturing/production_plan_schedule.yaml`

- **Titre** : `item_code`
- **Icône** : `calendar`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `subject` | Subject | Text | colonne de liste; lecture seule |
| `production_plan` | Production Plan | Link → `Production Plan` | **requis**; colonne de liste; lecture seule |
| `company` | Company | Link → `Company` | lecture seule |
| `row_type` | Row Type | Select — Finished Good · Sub Assembly · Raw Material | lecture seule |
| `plan_row` | Plan Row | Text | lecture seule; masqué |
| `task_key` | Task Key | Text | lecture seule; masqué |
| `item_code` | Item Code | Link → `Item` | colonne de liste; lecture seule |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `operation` | Operation | Link → `Operation` | lecture seule |
| `workstation` | Workstation | Link → `Workstation` | colonne de liste; lecture seule |
| `supplier` | Supplier | Link → `Supplier` | lecture seule |
| `from_time` | From Time | Datetime | **requis**; colonne de liste; lecture seule |
| `to_time` | To Time | Datetime | **requis**; lecture seule |
| `duration_mins` | Duration (Mins) | Number | lecture seule |

## Production Plan Sub Assembly Item

*Production Plan Sub Assembly Item* — `manufacturing/production_plan_sub_assembly_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_name` | Item Name | Text | lecture seule |
| `qty` | Qty to Order | Decimal | colonne de liste; lecture seule |
| `purchase_order` | Purchase Order | Link → `Purchase Order` | lecture seule |
| `received_qty` | Received Qty | Decimal | lecture seule |
| `bom_no` | BOM No | Link → `BOM` | colonne de liste |
| `production_plan_item` | Production Plan Item | Text | lecture seule; masqué |
| `bom_level` | Level (BOM) | Int | lecture seule |
| `uom` | UOM | Link → `UOM` | lecture seule |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `description` | description | TextEditor | lecture seule |
| `production_item` | Sub Assembly Item Code | Link → `Item` | colonne de liste; lecture seule |
| `indent` | Indent | Int |  |
| `fg_warehouse` | Target Warehouse | Link → `Warehouse` |  |
| `type_of_manufacturing` | Manufacturing Type | Select — In House · Subcontract · Material Request | colonne de liste; défaut `In House` |
| `supplier` | Supplier | Link → `Supplier` | colonne de liste |
| `schedule_date` | Schedule Date | Datetime |  |
| `actual_qty` | Actual Qty | Decimal | lecture seule |
| `projected_qty` | Projected Qty | Decimal | colonne de liste; lecture seule |
| `wo_produced_qty` | Produced Qty | Decimal | lecture seule |
| `required_qty` | Required Qty | Decimal | colonne de liste |
| `stock_reserved_qty` | Stock Reserved Qty | Decimal | lecture seule |
| `ordered_qty` | Ordered Qty | Decimal | lecture seule |
| `sales_order` | Sales Order | Link → `Sales Order` | lecture seule |
| `sales_order_item` | Sales Order Item | Text | masqué |
| `schedule_end_date` | Schedule End Date | Datetime | lecture seule |

## Routing

*Routing* — `manufacturing/routing.yaml`

- **Icône** : `route`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `routing_name` | Routing Name | Text |  |
| `disabled` | Disabled | Boolean | défaut `non` |
| `operations` | BOM Operation | Table → `BOM Operation` |  |

## Sales Forecast

*Sales Forecast* — `manufacturing/sales_forecast.yaml` · soumis

- **Numérotation** : série `SF-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `company`
- **Icône** : `trending-up`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Naming Series | Select — SF.YY.-.###### | **requis**; défaut `SF.YY.-.######` |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `posting_date` | Posting Date | Date | colonne de liste; défaut `today` |
| `selected_items` | Select Items | Table → `Sales Forecast Item` |  |
| `parent_warehouse` | Parent Warehouse | Link → `Warehouse` | **requis**; — For projected and forecast quantities, the system will consider all child warehouses under the selected parent |
| `items` | Items | Table → `Sales Forecast Item` |  |
| `from_date` | From Date | Date | **requis**; défaut `today` |
| `demand_number` | Number of Weeks / Months | Int | **requis**; défaut `6` |
| `status` | Status | Select — Planned · MPS Generated · Cancelled | colonne de liste; lecture seule |
| `frequency` | Frequency | Select — Weekly · Monthly | **requis**; défaut `Monthly` |

## Sales Forecast Item

*Sales Forecast Item* — `manufacturing/sales_forecast_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste; lecture seule |
| `item_name` | Item Name | Text | colonne de liste; lecture seule; recopié de `item_code.item_name` |
| `uom` | UOM | Link → `UOM` | colonne de liste; lecture seule |
| `delivery_date` | Delivery Date | Date | colonne de liste; lecture seule |
| `demand_qty` | Demand Qty | Decimal | colonne de liste |
| `warehouse` | Warehouse | Link → `Warehouse` | colonne de liste; lecture seule |

## Sub Operation

*Sub Operation* — `manufacturing/sub_operation.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `operation` | Operation | Link → `Operation` | **requis**; colonne de liste |
| `time_in_mins` | Operation Time | Number | colonne de liste; défaut `0.0`; — Time in mins |
| `description` | Description | LongText |  |

## Work Order

*Work Order* — `manufacturing/work_order.yaml` · soumis

- **Numérotation** : série `WO-{YYYY}-{#####}`
- **Titre** : `item_name`
- **Icône** : `factory`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — MFG-WO-.YYYY.- | **requis** |
| `status` | Status | Select — Draft · Submitted · Not Started · In Process · Stock Reserved · Stock Partially Reserved · Completed · Stopped · Closed · Cancelled | **requis**; lecture seule; défaut `Draft` |
| `production_item` | Item To Manufacture | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Item Name | Text | lecture seule |
| `image` | Image | Image | lecture seule; masqué |
| `bom_no` | BOM No | Link → `BOM` | **requis**; colonne de liste |
| `allow_alternative_item` | Allow Alternative Item | Boolean | défaut `non` |
| `use_multi_level_bom` | Use Multi-Level BOM | Boolean | défaut `oui`; — Plan material for sub-assemblies |
| `skip_transfer` | Skip Material Transfer to WIP Warehouse | Boolean | défaut `non`; — Check if material transfer entry is not required |
| `company` | Company | Link → `Company` | **requis** |
| `qty` | Qty To Manufacture | Decimal | **requis**; colonne de liste; défaut `1.000` |
| `material_transferred_for_manufacturing` | Material Transferred for Manufacturing | Number | lecture seule |
| `produced_qty` | Manufactured Qty | Decimal | lecture seule |
| `sales_order` | Sales Order | Link → `Sales Order` |  |
| `project` | Project | Link → `Project` |  |
| `from_wip_warehouse` | Backflush Raw Materials From Work-in-Progress Warehouse | Boolean | défaut `non` |
| `wip_warehouse` | Work-in-Progress Warehouse | Link → `Warehouse` | — This is a location where operations are executed. |
| `fg_warehouse` | Target Warehouse | Link → `Warehouse` | — This is a location where final product stored. |
| `scrap_warehouse` | Scrap Warehouse | Link → `Warehouse` | — This is a location where scraped materials are stored. |
| `required_items` | Required Items | Table → `Work Order Item` |  |
| `planned_start_date` | Planned Start Date | Datetime | **requis**; défaut `now` |
| `actual_start_date` | Actual Start Date | Datetime |  |
| `planned_end_date` | Planned End Date | Datetime |  |
| `actual_end_date` | Actual End Date | Datetime |  |
| `expected_delivery_date` | Expected Delivery Date | Date |  |
| `transfer_material_against` | Transfer Material Against | Select — Work Order · Job Card |  |
| `operations` | Operations | Table → `Work Order Operation` |  |
| `planned_operating_cost` | Planned Operating Cost | Currency | lecture seule; devise de `company.default_currency` |
| `actual_operating_cost` | Actual Operating Cost | Currency | lecture seule; devise de `company.default_currency` |
| `additional_operating_cost` | Additional Operating Cost | Currency | devise de `company.default_currency` |
| `total_operating_cost` | Total Operating Cost | Currency | lecture seule; devise de `company.default_currency` |
| `description` | Item Description | TextEditor | lecture seule |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `material_request` | Material Request | Link → `Material Request` | lecture seule; — Manufacture against Material Request |
| `material_request_item` | Material Request Item | Text | lecture seule; masqué |
| `sales_order_item` | Sales Order Item | Text | lecture seule; masqué |
| `production_plan` | Production Plan | Link → `Production Plan` | lecture seule |
| `production_plan_item` | Production Plan Item | Text | lecture seule |
| `product_bundle_item` | Product Bundle Item | Link → `Item` | lecture seule |
| `source_warehouse` | Default source Warehouse | Link → `Warehouse` | — This is a location where raw materials are available. |
| `lead_time` | Lead Time | Number | lecture seule; — In Mins |
| `has_serial_no` | Has Serial No | Boolean | lecture seule |
| `has_batch_no` | Has Batch No | Boolean | lecture seule |
| `batch_size` | Batch Size | Number | défaut `0.0` |
| `corrective_operation_cost` | Corrective Operation Cost | Currency | lecture seule; devise de `company.default_currency`; — From Corrective Job Card |
| `production_plan_sub_assembly_item` | Production Plan Sub Assembly Item | Text | lecture seule; masqué |
| `process_loss_qty` | Process Loss Qty | Decimal | lecture seule |
| `track_semi_finished_goods` | Produce Item per Operation | Boolean | lecture seule; masqué; — Each operation produces its own output item and puts it in stock, for example Cut Sheet, then Painted Sheet, t |
| `reserve_stock` | Reserve Stock | Boolean | défaut `non` |
| `disassembled_qty` | Disassembled Qty | Decimal | lecture seule |
| `mps` | MPS | Link → `Master Production Schedule` | lecture seule |
| `additional_transferred_qty` | Additional Transferred Qty | Decimal | lecture seule |
| `subcontracting_inward_order` | Subcontracting Inward Order | Link → `Subcontracting Inward Order` | lecture seule |
| `subcontracting_inward_order_item` | Subcontracting Inward Order Item | Text | lecture seule; masqué |
| `max_producible_qty` | Max Producible Qty | Decimal | lecture seule; masqué |
| `non_stock_items` | Additional Costs (as per BOM) | Table → `Work Order Additional Item` | lecture seule |
| `secondary_items` | Secondary Items (as per BOM) | Table → `Work Order Additional Item` | lecture seule |

## Work Order Additional Item

*Work Order Additional Item* — `manufacturing/work_order_additional_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | colonne de liste |
| `secondary_item_type` | Type | Text | colonne de liste |
| `qty` | Qty | Decimal | colonne de liste |
| `uom` | UOM | Link → `UOM` | colonne de liste |
| `amount` | Amount | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `rate` | Rate | Currency | colonne de liste; devise de `parent_company.default_currency` |

## Work Order Item

*Work Order Item* — `manufacturing/work_order_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `operation` | Operation | Link → `Operation` |  |
| `item_code` | Item Code | Link → `Item` | colonne de liste |
| `source_warehouse` | Source Warehouse | Link → `Warehouse` | colonne de liste |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `description` | Description | TextEditor | lecture seule |
| `required_qty` | Required Qty | Decimal | colonne de liste |
| `transferred_qty` | Transferred Qty | Decimal | colonne de liste; lecture seule |
| `requested_qty` | Requested Qty | Decimal | lecture seule |
| `picked_qty` | Picked Qty | Decimal | lecture seule |
| `allow_alternative_item` | Allow Alternative Item | Boolean | défaut `non` |
| `include_item_in_manufacturing` | Include Item In Manufacturing | Boolean | défaut `non` |
| `consumed_qty` | Consumed Qty | Decimal | colonne de liste; lecture seule |
| `available_qty_at_source_warehouse` | Available Qty at Source Warehouse | Decimal | lecture seule |
| `available_qty_at_wip_warehouse` | Available Qty at WIP Warehouse | Decimal | lecture seule |
| `rate` | Rate | Currency | lecture seule; devise de `parent_company.default_currency` |
| `amount` | Amount | Currency | lecture seule; devise de `parent_company.default_currency` |
| `returned_qty` | Returned Qty  | Decimal | colonne de liste; lecture seule |
| `subcontracted_qty` | Subcontracted Qty | Decimal | lecture seule |
| `operation_row_id` | Operation Row Id | Int | lecture seule |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `stock_reserved_qty` | Stock Reserved Qty | Decimal | lecture seule |
| `is_additional_item` | Is Additional Item | Boolean | lecture seule |
| `voucher_detail_reference` | Voucher Detail Reference | Text | lecture seule |
| `is_customer_provided_item` | Is Customer Provided Item | Boolean | lecture seule |

## Work Order Operation

*Work Order Operation* — `manufacturing/work_order_operation.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `operation` | Operation | Link → `Operation` | **requis**; colonne de liste |
| `bom` | BOM | Link → `BOM` |  |
| `bom_operation` | BOM Operation | Text | lecture seule; masqué |
| `description` | Operation Description | TextEditor |  |
| `completed_qty` | Completed Qty | Decimal | — Operation completed for how many finished goods? |
| `status` | Status | Select — Pending · Work in Progress · Completed | défaut `Pending` |
| `workstation` | Workstation | Link → `Workstation` | colonne de liste |
| `planned_start_time` | Planned Start Time | Datetime | lecture seule |
| `planned_end_time` | Planned End Time | Datetime | lecture seule |
| `time_in_mins` | Time | Number | **requis**; colonne de liste; — In Minutes |
| `hour_rate` | Hour Rate | Number | lecture seule |
| `planned_operating_cost` | Planned Operating Cost | Currency | lecture seule; devise de `parent_company.default_currency` |
| `actual_start_time` | Actual Start Time | Datetime | lecture seule; — Updated via 'Time Log' (In Minutes) |
| `actual_end_time` | Actual End Time | Datetime | lecture seule; — Updated via 'Time Log' (In Minutes) |
| `actual_operation_time` | Actual Operation Time | Number | lecture seule; — Updated via 'Time Log' (In Minutes) |
| `actual_operating_cost` | Actual Operating Cost | Currency | lecture seule; devise de `parent_company.default_currency`; — (Hour Rate / 60) * Actual Operation Time |
| `batch_size` | Batch Size | Number | défaut `1.0` |
| `sequence_id` | Sequence ID | Int |  |
| `workstation_type` | Workstation Type | Link → `Workstation Type` |  |
| `process_loss_qty` | Process Loss Qty | Decimal | lecture seule |
| `bom_no` | Output Item BOM | Link → `BOM` | lecture seule |
| `finished_good` | Output Item | Link → `Item` | colonne de liste; lecture seule |
| `output_qty` | Output Qty | Decimal | lecture seule; — Quantity of the output item this operation makes for the whole Work Order |
| `wip_warehouse` | WIP WH | Link → `Warehouse` |  |
| `fg_warehouse` | Finished Goods Warehouse | Link → `Warehouse` | colonne de liste |
| `source_warehouse` | Source Warehouse | Link → `Warehouse` | colonne de liste |
| `is_subcontracted` | Is Subcontracted | Boolean | lecture seule |
| `skip_material_transfer` | Skip Material Transfer | Boolean | lecture seule |
| `backflush_from_wip_warehouse` | Backflush Materials From WIP Warehouse | Boolean | lecture seule |
| `batch_split` | Batch Split | Boolean | lecture seule |
| `weight_per_piece` | Weight Per Piece | Number | lecture seule |
| `quality_inspection_required` | Quality Inspection Required | Boolean | défaut `non` |
| `pending_qty` | Pending Qty | Decimal | lecture seule |

## Workstation

*Workstation* — `manufacturing/workstation.yaml`

- **Titre** : `status`
- **Icône** : `robot-arm`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `workstation_name` | Workstation Name | Text | **requis**; colonne de liste |
| `description` | Description | LongText | colonne de liste |
| `hour_rate` | Net Hour Rate | Currency | lecture seule; — per hour |
| `working_hours` | Working Hours | Table → `Workstation Working Hour` |  |
| `holiday_list` | Holiday List | Link → `Holiday List` |  |
| `production_capacity` | Job Capacity | Int | **requis**; défaut `1`; — Run parallel job cards in a workstation |
| `workstation_type` | Workstation Type | Link → `Workstation Type` |  |
| `plant_floor` | Plant Floor | Link → `Plant Floor` |  |
| `status` | Status | Select — Production · Off · Idle · Problem · Maintenance · Setup | colonne de liste |
| `on_status_image` | Active Status | Image |  |
| `off_status_image` | Inactive Status | Image |  |
| `warehouse` | Warehouse | Link → `Warehouse` |  |
| `total_working_hours` | Total Working Hours | Number |  |
| `disabled` | Disabled | Boolean | défaut `non` |
| `workstation_costs` | Operating Components Cost | Table → `Workstation Cost` |  |

## Workstation Cost

*Workstation Cost* — `manufacturing/workstation_cost.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `operating_cost` | Operating Cost | Currency | **requis**; colonne de liste |
| `operating_component` | Operating Component | Link → `Workstation Operating Component` | **requis**; colonne de liste |

## Workstation Operating Component

*Workstation Operating Component* — `manufacturing/workstation_operating_component.yaml`

- **Titre** : `component_name`
- **Icône** : `cog`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `component_name` | Component Name | Text | **requis**; colonne de liste |
| `accounts` | Component Expense Account | Table → `Workstation Operating Component Account` |  |

## Workstation Operating Component Account

*Workstation Operating Component Account* — `manufacturing/workstation_operating_component_account.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `expense_account` | Expense Account | Link → `Account` | colonne de liste |

## Workstation Type

*Workstation Type* — `manufacturing/workstation_type.yaml`

- **Titre** : `workstation_type`
- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `workstation_type` | Workstation Type | Text | **requis**; colonne de liste |
| `hour_rate` | Net Hour Rate | Currency | lecture seule; — per hour |
| `description` | Description | LongText | colonne de liste |
| `workstation_costs` | Operating Components Cost | Table → `Workstation Cost` |  |

## Workstation Working Hour

*Workstation Working Hour* — `manufacturing/workstation_working_hour.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `start_time` | Start Time | Time | **requis**; colonne de liste |
| `end_time` | End Time | Time | **requis**; colonne de liste |
| `enabled` | Enabled | Boolean | colonne de liste; défaut `oui` |
| `hours` | Hours | Number | lecture seule |
