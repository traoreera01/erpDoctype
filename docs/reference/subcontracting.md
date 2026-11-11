# Référence des champs — Sous-traitance (`subcontracting`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `subcontracting/` (13 DocTypes). Ne pas éditer à la main : relancer le script.

290 champs au total ; types les plus fréquents : `Link` (100), `Text` (41), `Decimal` (38), `Currency` (28), `Boolean` (13).

## Subcontracting BOM

*Subcontracting BOM* — `subcontracting/subcontracting_bom.yaml`

- **Titre** : `finished_good`
- **Icône** : `list-tree`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `is_active` | Is Active | Boolean | colonne de liste; défaut `oui` |
| `finished_good` | Finished Good | Link → `Item` | **requis**; colonne de liste |
| `finished_good_qty` | Finished Good Qty | Decimal | **requis**; défaut `1.000` |
| `finished_good_bom` | Finished Good BOM | Link → `BOM` | **requis**; colonne de liste |
| `service_item` | Service Item | Link → `Item` | **requis**; colonne de liste |
| `service_item_qty` | Service Item Qty | Decimal | **requis**; défaut `1.000` |
| `service_item_uom` | Service Item UOM | Link → `UOM` | **requis** |
| `conversion_factor` | Conversion Factor | Number | lecture seule; — Service Item Qty / Finished Good Qty |
| `finished_good_uom` | Finished Good UOM | Link → `UOM` | lecture seule |

## Subcontracting Inward Order

*Subcontracting Inward Order* — `subcontracting/subcontracting_inward_order.yaml` · soumis

- **Numérotation** : série `SIO-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `title`
- **Icône** : `package-plus`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text |  |
| `naming_series` | Series | Select — SCI-ORD-.YYYY.- | **requis** |
| `sales_order` | Subcontracting Sales Order | Link → `Sales Order` | **requis** |
| `customer` | Customer | Link → `Customer` | **requis**; lecture seule |
| `customer_name` | Customer Name | Text | lecture seule; recopié de `customer.customer_name` |
| `company` | Company | Link → `Company` | **requis** |
| `transaction_date` | Date | Date | **requis**; colonne de liste; défaut `today` |
| `items` | Items | Table → `Subcontracting Inward Order Item` |  |
| `service_items` | Service Items | Table → `Subcontracting Inward Order Service Item` | lecture seule |
| `received_items` | Required Items | Table → `Subcontracting Inward Order Received Item` | lecture seule |
| `status` | Status | Select — Draft · Open · Ongoing · Produced · Delivered · Returned · Cancelled · Closed | **requis**; lecture seule; défaut `Draft` |
| `per_delivered` | % Delivered | Percent | colonne de liste; lecture seule |
| `per_produced` | % Produced | Percent | colonne de liste; lecture seule |
| `per_process_loss` | % Process Loss | Percent | colonne de liste; lecture seule |
| `set_delivery_warehouse` | Set Delivery Warehouse | Link → `Warehouse` |  |
| `customer_warehouse` | Customer Warehouse | Link → `Warehouse` | **requis** |
| `per_returned` | % Returned | Percent | colonne de liste; lecture seule |
| `per_raw_material_returned` | % Raw Material Returned | Percent | colonne de liste; lecture seule |
| `per_raw_material_received` | % Raw Material Received | Percent | colonne de liste; lecture seule |
| `currency` | Customer Currency | Link → `Currency` | lecture seule; masqué |
| `secondary_items` | Secondary Items | Table → `Subcontracting Inward Order Secondary Item` |  |

## Subcontracting Inward Order Item

*Subcontracting Inward Order Item* — `subcontracting/subcontracting_inward_order_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste; lecture seule |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `qty` | Quantity | Decimal | **requis**; colonne de liste; défaut `1.000` |
| `stock_uom` | Stock UOM | Link → `UOM` | **requis**; lecture seule |
| `conversion_factor` | Conversion Factor | Number | lecture seule; masqué |
| `bom` | BOM | Link → `BOM` | **requis**; colonne de liste |
| `include_exploded_items` | Include Exploded Items | Boolean | défaut `non` |
| `delivered_qty` | Delivered Qty | Decimal | colonne de liste; lecture seule |
| `returned_qty` | Returned Qty | Decimal | lecture seule |
| `sales_order_item` | Sales Order Item | Text | lecture seule; masqué |
| `subcontracting_conversion_factor` | Subcontracting Conversion Factor | Number | lecture seule; masqué |
| `produced_qty` | Produced Qty | Decimal | lecture seule |
| `process_loss_qty` | Process Loss Qty | Decimal | lecture seule |
| `delivery_warehouse` | Delivery Warehouse | Link → `Warehouse` | **requis**; colonne de liste |

## Subcontracting Inward Order Received Item

*Subcontracting Inward Order Received Item* — `subcontracting/subcontracting_inward_order_received_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `main_item_code` | Item Code | Link → `Item` | **requis**; colonne de liste; lecture seule |
| `rm_item_code` | Raw Material Item Code | Link → `Item` | **requis**; colonne de liste; lecture seule |
| `stock_uom` | Stock UOM | Link → `UOM` | **requis**; lecture seule |
| `bom_detail_no` | BOM Detail No | Text | lecture seule |
| `reference_name` | Reference Name | Text | **requis**; lecture seule |
| `required_qty` | Required Qty | Decimal | colonne de liste; lecture seule |
| `received_qty` | Received Qty | Decimal | colonne de liste; lecture seule |
| `consumed_qty` | Consumed Qty | Decimal | lecture seule |
| `returned_qty` | Returned Qty | Decimal | lecture seule |
| `work_order_qty` | Work Order Qty | Decimal | lecture seule |
| `is_customer_provided_item` | Is Customer Provided Item | Boolean | **requis**; lecture seule |
| `warehouse` | Warehouse | Link → `Warehouse` | lecture seule |
| `billed_qty` | Billed Qty | Decimal | lecture seule |
| `is_additional_item` | Is Additional Item | Boolean | lecture seule |
| `rate` | Rate | Currency | lecture seule; devise de `parent_currency` |

## Subcontracting Inward Order Secondary Item

*Subcontracting Inward Order Secondary Item* — `subcontracting/subcontracting_inward_order_secondary_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste; lecture seule |
| `stock_uom` | Stock UOM | Link → `UOM` | **requis**; lecture seule |
| `reference_name` | Reference Name | Text | **requis**; lecture seule |
| `produced_qty` | Produced Qty | Decimal | **requis**; colonne de liste; défaut `0.000` |
| `delivered_qty` | Delivered Qty | Decimal | **requis**; colonne de liste; défaut `0.000` |
| `fg_item_code` | Finished Good Item Code | Link → `Item` | **requis**; colonne de liste; lecture seule |
| `warehouse` | Warehouse | Link → `Warehouse` | **requis**; lecture seule |
| `secondary_item_type` | Type | Select — Co-Product · By-Product · Scrap · Additional Finished Good | **requis**; lecture seule |

## Subcontracting Inward Order Service Item

*Subcontracting Inward Order Service Item* — `subcontracting/subcontracting_inward_order_service_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Item Name | Text | colonne de liste; recopié de `item_code.item_name` |
| `qty` | Quantity | Decimal | **requis**; colonne de liste |
| `rate` | Rate | Currency | **requis**; colonne de liste; devise de `parent_currency` |
| `amount` | Amount | Currency | **requis**; colonne de liste; lecture seule; devise de `parent_currency` |
| `fg_item` | Finished Good Item | Link → `Item` | **requis** |
| `fg_item_qty` | Finished Good Item Quantity | Decimal | **requis**; défaut `1.000` |
| `sales_order_item` | Sales Order Item | Text | lecture seule; masqué |
| `uom` | UOM | Link → `UOM` | **requis**; lecture seule |

## Subcontracting Order

*Subcontracting Order* — `subcontracting/subcontracting_order.yaml` · soumis

- **Numérotation** : série `SUOR-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `title`
- **Icône** : `shopping-bag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text |  |
| `naming_series` | Series | Select — SC-ORD-.YYYY.- | **requis** |
| `purchase_order` | Subcontracting Purchase Order | Link → `Purchase Order` | **requis** |
| `supplier` | Job Worker | Link → `Supplier` | **requis** |
| `supplier_name` | Job Worker Name | Text | lecture seule; recopié de `supplier.supplier_name` |
| `supplier_warehouse` | Job Worker Warehouse | Link → `Warehouse` | **requis** |
| `company` | Company | Link → `Company` | **requis** |
| `transaction_date` | Date | Date | **requis**; colonne de liste; défaut `today` |
| `schedule_date` | Required By | Date | lecture seule |
| `supplier_address` | Job Worker Address | Link → `Address` |  |
| `address_display` | Job Worker Address Details | TextEditor | lecture seule |
| `contact_person` | Job Worker Contact | Link → `Contact` |  |
| `contact_display` | Contact Name | LongText | lecture seule |
| `contact_mobile` | Contact Mobile No | LongText | lecture seule |
| `contact_email` | Contact Email | LongText | lecture seule |
| `shipping_address` | Company Shipping Address | Link → `Address` |  |
| `shipping_address_display` | Shipping Address Details | TextEditor | lecture seule |
| `billing_address` | Company Billing Address | Link → `Address` |  |
| `billing_address_display` | Billing Address Details | TextEditor | lecture seule |
| `set_warehouse` | Set Target Warehouse | Link → `Warehouse` | — Sets 'Warehouse' in each row of the Items table. |
| `items` | Items | Table → `Subcontracting Order Item` |  |
| `total_qty` | Total Quantity | Decimal | lecture seule |
| `total` | Total | Currency | lecture seule; devise de `company.default_currency` |
| `service_items` | Service Items | Table → `Subcontracting Order Service Item` | lecture seule |
| `set_reserve_warehouse` | Set Reserve Warehouse | Link → `Warehouse` | — Sets 'Reserve Warehouse' in each row of the Supplied Items table. |
| `supplied_items` | Supplied Items | Table → `Subcontracting Order Supplied Item` | lecture seule |
| `additional_costs` | Additional Costs | Table → `Landed Cost Taxes and Charges` |  |
| `total_additional_costs` | Total Additional Costs | Currency | lecture seule; devise de `company.default_currency` |
| `status` | Status | Select — Draft · Open · Partially Received · Completed · Material Transferred · Partial Material Transferred · Cancelled · Closed | **requis**; lecture seule; défaut `Draft` |
| `per_received` | % Received | Percent | colonne de liste; lecture seule |
| `select_print_heading` | Print Heading | Link → `Print Heading` |  |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `distribute_additional_costs_based_on` | Distribute Additional Costs Based On  | Select — Qty · Amount | défaut `Qty` |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |
| `supplier_currency` | Job Worker Currency | Link → `Currency` | lecture seule; masqué |
| `conversion_rate` | Exchange Rate | Number | lecture seule; masqué |
| `reserve_stock` | Reserve Stock | Boolean | défaut `non` |
| `production_plan` | Production Plan | Text | lecture seule; masqué |

## Subcontracting Order Item

*Subcontracting Order Item* — `subcontracting/subcontracting_order_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste; lecture seule |
| `item_name` | Item Name | Text | recopié de `item_code.item_name` |
| `schedule_date` | Required By | Date | lecture seule |
| `expected_delivery_date` | Expected Delivery Date | Date |  |
| `description` | Description | TextEditor |  |
| `qty` | Quantity | Decimal | **requis**; colonne de liste; défaut `1.000` |
| `stock_uom` | Stock UOM | Link → `UOM` | **requis**; lecture seule |
| `conversion_factor` | Conversion Factor | Number | lecture seule; masqué |
| `rate` | Rate | Currency | **requis**; colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `amount` | Amount | Currency | **requis**; colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `warehouse` | Warehouse | Link → `Warehouse` | **requis** |
| `expense_account` | Expense Account | Link → `Account` |  |
| `manufacturer` | Manufacturer | Link → `Manufacturer` |  |
| `manufacturer_part_no` | Manufacturer Part Number | Text |  |
| `bom` | BOM | Link → `BOM` | **requis**; colonne de liste |
| `include_exploded_items` | Include Exploded Items | Boolean | défaut `non` |
| `service_cost_per_qty` | Service Cost Per Qty | Currency | **requis**; lecture seule; devise de `parent_company.default_currency` |
| `additional_cost_per_qty` | Additional Cost Per Qty | Currency | lecture seule; devise de `parent_company.default_currency` |
| `rm_cost_per_qty` | Raw Material Cost Per Qty | Currency | lecture seule; devise de `parent_company.default_currency` |
| `page_break` | Page Break | Boolean | défaut `non` |
| `received_qty` | Received Qty | Decimal | lecture seule |
| `returned_qty` | Returned Qty | Decimal | lecture seule |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |
| `material_request` | Material Request | Link → `Material Request` | lecture seule |
| `material_request_item` | Material Request Item | Text | lecture seule |
| `purchase_order_item` | Purchase Order Item | Text | lecture seule; masqué |
| `job_card` | Job Card | Link → `Job Card` | lecture seule |
| `subcontracting_conversion_factor` | Subcontracting Conversion Factor | Number | lecture seule; masqué |
| `production_plan_sub_assembly_item` | Production Plan Sub Assembly Item | Text | lecture seule; masqué |

## Subcontracting Order Service Item

*Subcontracting Order Service Item* — `subcontracting/subcontracting_order_service_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Item Name | Text | colonne de liste; recopié de `item_code.item_name` |
| `qty` | Quantity | Decimal | **requis**; colonne de liste |
| `rate` | Rate | Currency | **requis**; colonne de liste; devise de `parent_supplier_currency` |
| `amount` | Amount | Currency | **requis**; colonne de liste; lecture seule; devise de `parent_supplier_currency` |
| `base_rate` | Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_amount` | Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `fg_item` | Finished Good Item | Link → `Item` | **requis** |
| `fg_item_qty` | Finished Good Item Quantity | Decimal | **requis**; défaut `1.000` |
| `purchase_order_item` | Purchase Order Item | Text | lecture seule; masqué |
| `material_request` | Material Request | Link → `Material Request` | lecture seule |
| `material_request_item` | Material Request Item | Text | lecture seule |

## Subcontracting Order Supplied Item

*Subcontracting Order Supplied Item* — `subcontracting/subcontracting_order_supplied_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `main_item_code` | Item Code | Link → `Item` | colonne de liste; lecture seule |
| `rm_item_code` | Raw Material Item Code | Link → `Item` | colonne de liste; lecture seule |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `conversion_factor` | Conversion Factor | Number | lecture seule; masqué |
| `reserve_warehouse` | Reserve Warehouse | Link → `Warehouse` | colonne de liste |
| `bom_detail_no` | BOM Detail No | Text | lecture seule |
| `reference_name` | Reference Name | Text | lecture seule |
| `rate` | Rate | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `amount` | Amount | Currency | lecture seule; devise de `parent_company.default_currency` |
| `required_qty` | Required Qty | Decimal | colonne de liste; lecture seule |
| `supplied_qty` | Supplied Qty | Decimal | colonne de liste; lecture seule |
| `consumed_qty` | Consumed Qty | Decimal | lecture seule |
| `returned_qty` | Returned Qty | Decimal | lecture seule |
| `total_supplied_qty` | Total Supplied Qty | Decimal | lecture seule; masqué |
| `stock_reserved_qty` | Reserved Qty | Decimal | lecture seule |

## Subcontracting Receipt

*Subcontracting Receipt* — `subcontracting/subcontracting_receipt.yaml` · soumis

- **Numérotation** : série `SURE-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `title`
- **Icône** : `package-check`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text |  |
| `naming_series` | Series | Select — MAT-SCR-.YYYY.- · MAT-SCR-RET-.YYYY.- | **requis** |
| `supplier` | Job Worker | Link → `Supplier` | **requis** |
| `supplier_name` | Job Worker Name | Text | lecture seule; recopié de `supplier.supplier_name` |
| `posting_date` | Date | Date | **requis**; colonne de liste; défaut `today` |
| `posting_time` | Posting Time | Time | **requis**; — Time at which materials were received |
| `company` | Company | Link → `Company` | **requis** |
| `supplier_address` | Select Job Worker Address | Link → `Address` |  |
| `contact_person` | Contact Person | Link → `Contact` |  |
| `address_display` | Address | TextEditor | lecture seule |
| `contact_display` | Contact | LongText | lecture seule |
| `contact_mobile` | Mobile No | LongText | lecture seule |
| `contact_email` | Contact Email | LongText | lecture seule |
| `shipping_address` | Select Shipping Address | Link → `Address` |  |
| `shipping_address_display` | Shipping Address | TextEditor | lecture seule |
| `set_warehouse` | Accepted Warehouse | Link → `Warehouse` | — Sets 'Accepted Warehouse' in each row of the Items table. |
| `rejected_warehouse` | Rejected Warehouse | Link → `Warehouse` | — Sets 'Rejected Warehouse' in each row of the Items table. |
| `supplier_warehouse` | Job Worker Warehouse | Link → `Warehouse` |  |
| `items` | Items | Table → `Subcontracting Receipt Item` |  |
| `supplied_items` | Consumed Items | Table → `Subcontracting Receipt Supplied Item` |  |
| `total_qty` | Total Quantity | Decimal | lecture seule |
| `total` | Total | Currency | lecture seule; devise de `company.default_currency` |
| `in_words` | In Words | Text | lecture seule |
| `bill_no` | Bill No | Text | masqué |
| `bill_date` | Bill Date | Date | masqué |
| `status` | Status | Select — Draft · Completed · Return · Return Issued · Cancelled · Closed | **requis**; lecture seule; défaut `Draft` |
| `range` | Range | Text | masqué |
| `auto_repeat` | Auto Repeat | Link → `Auto Repeat` | lecture seule |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `select_print_heading` | Print Heading | Link → `Print Heading` |  |
| `language` | Print Language | Text | lecture seule |
| `instructions` | Instructions | LongText |  |
| `remarks` | Remarks | LongText |  |
| `transporter_name` | Transporter Name | Text |  |
| `lr_no` | Vehicle Number | Text |  |
| `lr_date` | Vehicle Date | Date |  |
| `billing_address` | Select Billing Address | Link → `Address` |  |
| `billing_address_display` | Billing Address | TextEditor | lecture seule |
| `represents_company` | Represents Company | Link → `Company` | lecture seule |
| `is_return` | Is Return | Boolean | lecture seule |
| `return_against` | Return Against Subcontracting Receipt | Link → `Subcontracting Receipt` | lecture seule |
| `per_returned` | % Returned | Percent | colonne de liste; lecture seule |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |
| `distribute_additional_costs_based_on` | Distribute Additional Costs Based On  | Select — Qty · Amount | défaut `Qty` |
| `additional_costs` | Additional Costs | Table → `Landed Cost Taxes and Charges` |  |
| `total_additional_costs` | Total Additional Costs | Currency | lecture seule; devise de `company.default_currency` |
| `set_posting_time` | Edit Posting Date and Time | Boolean | défaut `non` |
| `supplier_delivery_note` | Job Worker Delivery Note | Text |  |

## Subcontracting Receipt Item

*Subcontracting Receipt Item* — `subcontracting/subcontracting_receipt_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Item Name | Text | recopié de `item_code.item_name` |
| `description` | Description | TextEditor |  |
| `received_qty` | Qty (As per BOM) | Decimal | **requis**; lecture seule |
| `qty` | Accepted Qty | Decimal | colonne de liste |
| `rejected_qty` | Rejected Qty | Decimal | colonne de liste |
| `stock_uom` | Stock UOM | Link → `UOM` | **requis**; lecture seule |
| `conversion_factor` | Conversion Factor | Number | lecture seule; masqué |
| `rate` | Rate | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `amount` | Amount | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `rm_cost_per_qty` | Raw Material Cost Per Qty | Currency | lecture seule; devise de `parent_company.default_currency` |
| `service_cost_per_qty` | Service Cost Per Qty | Currency | **requis**; lecture seule; devise de `parent_company.default_currency` |
| `additional_cost_per_qty` | Additional Cost Per Qty | Currency | lecture seule; devise de `parent_company.default_currency` |
| `warehouse` | Accepted Warehouse | Link → `Warehouse` | colonne de liste |
| `rejected_warehouse` | Rejected Warehouse | Link → `Warehouse` |  |
| `quality_inspection` | Quality Inspection | Link → `Quality Inspection` |  |
| `subcontracting_order` | Subcontracting Order | Link → `Subcontracting Order` | lecture seule |
| `schedule_date` | Required By | Date | lecture seule |
| `serial_no` | Serial No | LongText |  |
| `batch_no` | Batch No | Link → `Batch` |  |
| `rejected_serial_no` | Rejected Serial No | LongText |  |
| `subcontracting_order_item` | Subcontracting Order Item | Text | lecture seule; masqué |
| `bom` | BOM | Link → `BOM` |  |
| `brand` | Brand | Link → `Brand` | lecture seule; masqué |
| `rm_supp_cost` | Raw Materials Supplied Cost | Currency | lecture seule; masqué; devise de `parent_company.default_currency` |
| `expense_account` | Expense Account | Link → `Account` |  |
| `manufacturer` | Manufacturer | Link → `Manufacturer` |  |
| `manufacturer_part_no` | Manufacturer Part Number | Text |  |
| `subcontracting_receipt_item` | Subcontracting Receipt Item | Text | lecture seule; masqué |
| `project` | Project | Link → `Project` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `page_break` | Page Break | Boolean | défaut `non` |
| `returned_qty` | Returned Qty | Decimal | lecture seule |
| `serial_and_batch_bundle` | Serial and Batch Bundle | Link → `Serial and Batch Bundle` |  |
| `rejected_serial_and_batch_bundle` | Rejected Serial and Batch Bundle | Link → `Serial and Batch Bundle` |  |
| `reference_name` | Reference Name | Text | lecture seule; masqué |
| `purchase_order_item` | Purchase Order Item | Text | lecture seule; masqué |
| `purchase_order` | Purchase Order | Link → `Purchase Order` | lecture seule; masqué |
| `include_exploded_items` | Include Exploded Items | Boolean | défaut `non` |
| `use_serial_batch_fields` | Use Serial No / Batch Fields | Boolean | défaut `non` |
| `job_card` | Job Card | Link → `Job Card` | lecture seule |
| `landed_cost_voucher_amount` | Landed Cost Voucher Amount | Currency | lecture seule; devise de `parent_company.default_currency` |
| `service_expense_account` | Service Expense Account | Link → `Account` |  |
| `secondary_item_type` | Type | Select — Co-Product · By-Product · Scrap · Additional Finished Good | lecture seule |
| `secondary_items_cost_per_qty` | Secondary Items Cost Per Qty | Currency | lecture seule; devise de `parent_company.default_currency` |
| `valuation_type` | Valuation Type | Select — Valuation Rate · % of Component Cost · Manual | lecture seule |
| `bom_secondary_item` | BOM Secondary Item | Text | lecture seule; masqué |
| `process_loss_qty` | Process Loss Qty | Decimal | défaut `0.000` |

## Subcontracting Receipt Supplied Item

*Subcontracting Receipt Supplied Item* — `subcontracting/subcontracting_receipt_supplied_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `main_item_code` | Item Code | Link → `Item` | colonne de liste; lecture seule |
| `rm_item_code` | Raw Material Item Code | Link → `Item` | colonne de liste; lecture seule |
| `description` | Description | TextEditor | lecture seule |
| `batch_no` | Batch No | Link → `Batch` |  |
| `serial_no` | Serial No | LongText |  |
| `required_qty` | Required Qty | Decimal | colonne de liste; lecture seule |
| `consumed_qty` | Consumed Qty | Decimal | **requis**; colonne de liste; lecture seule |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `rate` | Rate | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `amount` | Amount | Currency | lecture seule; devise de `parent_company.default_currency` |
| `conversion_factor` | Conversion Factor | Number | lecture seule; masqué |
| `current_stock` | Current Stock | Number | lecture seule |
| `reference_name` | Reference Name | Text | colonne de liste; lecture seule; masqué |
| `bom_detail_no` | BOM Detail No | Text | colonne de liste; lecture seule; masqué |
| `item_name` | Item Name | Text | lecture seule |
| `subcontracting_order` | Subcontracting Order | Link → `Subcontracting Order` | lecture seule; masqué |
| `available_qty_for_consumption` | Available Qty For Consumption | Decimal | lecture seule |
| `serial_and_batch_bundle` | Serial / Batch Bundle | Link → `Serial and Batch Bundle` | colonne de liste |
| `use_serial_batch_fields` | Use Serial No / Batch Fields | Boolean | défaut `non` |
| `expense_account` | Expense Account | Link → `Account` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
