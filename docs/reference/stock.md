# Référence des champs — Stock (`stock`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `stock/` (76 DocTypes). Ne pas éditer à la main : relancer le script.

1404 champs au total ; types les plus fréquents : `Link` (404), `Text` (221), `Boolean` (195), `Currency` (124), `Decimal` (79).

## Batch

*Lot* — `stock/batch.yaml`

- **Numérotation** : série `BATCH-{YYYY}-{#####}`
- **Vues** : tree (parent `parent_batch`)
- **Titre** : `batch_id`
- **Icône** : `layers`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `batch_id` | N° de lot | Text | **requis**; colonne de liste; — Identifiant du lot utilisé sur les mouvements de stock. |
| `item` | Article | Link → `Item` | **requis**; colonne de liste; filtres de lien |
| `disabled` | Désactivé | Boolean | colonne de liste; défaut `non` |
| `manufacturing_date` | Date de fabrication | Date |  |
| `expiry_date` | Date d’expiration | Date | colonne de liste |
| `parent_batch` | Lot parent | Link → `Batch` |  |
| `description` | Description | LongText |  |

## Bin

*Bin* — `stock/bin.yaml`

- **Titre** : `item_code`
- **Icône** : `archive`
- **Permissions explicites** — `write` : 0, `create` : 0, `delete` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `warehouse` | Warehouse | Link → `Warehouse` | **requis**; colonne de liste; lecture seule |
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste; lecture seule |
| `reserved_qty` | Reserved Qty | Decimal | colonne de liste; lecture seule |
| `actual_qty` | Actual Qty | Decimal | colonne de liste; lecture seule |
| `ordered_qty` | Ordered Qty | Decimal | colonne de liste; lecture seule |
| `indented_qty` | Requested Qty | Decimal | lecture seule |
| `planned_qty` | Planned Qty | Decimal | lecture seule |
| `projected_qty` | Projected Qty | Decimal | lecture seule |
| `reserved_qty_for_production` | Reserved Qty for Production | Decimal | lecture seule |
| `reserved_qty_for_sub_contract` | Reserved Qty for Subcontract | Decimal | lecture seule |
| `stock_uom` | UOM | Link → `UOM` | lecture seule |
| `company` | Company | Link → `Company` | lecture seule |
| `valuation_rate` | Valuation Rate | Number | lecture seule |
| `stock_value` | Stock Value | Number | lecture seule |
| `reserved_qty_for_production_plan` | Reserved Qty for Production Plan | Decimal | lecture seule |
| `reserved_stock` | Reserved Stock | Number | lecture seule |

## Company Restriction

*Company Restriction* — `stock/company_restriction.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |

## Customs Tariff Number

*Customs Tariff Number* — `stock/customs_tariff_number.yaml`

- **Titre** : `tariff_number`
- **Icône** : `hash`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `tariff_number` | Tariff Number | Text | **requis**; colonne de liste |
| `description` | Description | Text | colonne de liste |

## Delivery Note

*Delivery Note* — `stock/delivery_note.yaml` · soumis

- **Numérotation** : série `DN-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `customer_name`
- **Icône** : `truck`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — MAT-DN-.YYYY.- · MAT-DN-RET-.YYYY.- | **requis** |
| `customer` | Customer | Link → `Customer` | **requis** |
| `customer_name` | Customer Name | Text | lecture seule; recopié de `customer.customer_name` |
| `company` | Company | Link → `Company` | **requis** |
| `posting_date` | Date | Date | **requis**; colonne de liste; défaut `today` |
| `posting_time` | Posting Time | Time | **requis** |
| `set_posting_time` | Edit Posting Date and Time | Boolean | défaut `non` |
| `is_return` | Is Return | Boolean | lecture seule |
| `issue_credit_note` | Issue Credit Note | Boolean | défaut `non` |
| `return_against` | Return Against Delivery Note | Link → `Delivery Note` | lecture seule |
| `po_no` | Customer's Purchase Order No | LongText |  |
| `po_date` | Customer's Purchase Order Date | Date |  |
| `shipping_address_name` | Shipping Address | Link → `Address` |  |
| `shipping_address` | Shipping Address | TextEditor | lecture seule |
| `shipping_contact_person` | Shipping Contact Person | Link → `Contact` |  |
| `shipping_contact_display` | Shipping Contact | LongText | lecture seule |
| `shipping_contact_mobile` | Shipping Contact Mobile No | LongText | lecture seule |
| `shipping_contact_email` | Shipping Contact Email | Text | lecture seule; masqué |
| `contact_person` | Contact Person | Link → `Contact` |  |
| `contact_display` | Contact | LongText | lecture seule |
| `contact_mobile` | Mobile No | LongText | lecture seule; masqué |
| `contact_email` | Contact Email | Text | lecture seule; masqué |
| `customer_address` | Billing Address Name | Link → `Address` |  |
| `tax_id` | Tax Id | Text | lecture seule |
| `address_display` | Billing Address | TextEditor | lecture seule |
| `company_address` | Company Address Name | Link → `Address` |  |
| `company_address_display` | Company Address | TextEditor | lecture seule |
| `currency` | Currency | Link → `Currency` | **requis** |
| `conversion_rate` | Exchange Rate | Number | **requis**; — Rate at which customer's currency is converted to company's base currency |
| `selling_price_list` | Price List | Link → `Price List` | **requis** |
| `price_list_currency` | Price List Currency | Link → `Currency` | **requis**; lecture seule |
| `plc_conversion_rate` | Price List Exchange Rate | Number | **requis**; — Rate at which Price list currency is converted to company's base currency |
| `ignore_pricing_rule` | Ignore Pricing Rule | Boolean | défaut `non` |
| `set_warehouse` | Set Source Warehouse | Link → `Warehouse` |  |
| `scan_barcode` | Scan Barcode | Text |  |
| `items` | Delivery Note Item | Table → `Delivery Note Item` |  |
| `pricing_rules` | Pricing Rule Detail | Table → `Pricing Rule Detail` | lecture seule |
| `packed_items` | Packed Items | Table → `Packed Item` |  |
| `total_qty` | Total Quantity | Decimal | lecture seule; calculé : `sum(items.qty)` |
| `base_total` | Total (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_net_total` | Net Total (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `total` | Total | Currency | lecture seule; calculé : `sum(items.amount)`; devise de `currency` |
| `net_total` | Net Total | Currency | lecture seule; calculé : `sum(items.net_amount)`; devise de `currency` |
| `total_net_weight` | Total Net Weight | Number | lecture seule |
| `tax_category` | Tax Category | Link → `Tax Category` |  |
| `shipping_rule` | Shipping Rule | Link → `Shipping Rule` |  |
| `taxes_and_charges` | Sales Taxes and Charges Template | Link → `Sales Taxes and Charges Template` |  |
| `taxes` | Sales Taxes and Charges | Table → `Sales Taxes and Charges` |  |
| `other_charges_calculation` | Taxes and Charges Calculation | TextEditor | lecture seule |
| `base_total_taxes_and_charges` | Total Taxes and Charges (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `total_taxes_and_charges` | Total Taxes and Charges | Currency | lecture seule; devise de `currency` |
| `apply_discount_on` | Apply Additional Discount On | Select — Grand Total · Net Total | défaut `Grand Total` |
| `base_discount_amount` | Additional Discount Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `additional_discount_percentage` | Additional Discount Percentage | Number |  |
| `discount_amount` | Additional Discount Amount | Currency | devise de `currency` |
| `base_grand_total` | Grand Total | Currency | lecture seule; devise de `company.default_currency` |
| `base_rounding_adjustment` | Rounding Adjustment | Currency | lecture seule; devise de `company.default_currency` |
| `base_rounded_total` | Rounded Total | Currency | lecture seule; devise de `company.default_currency` |
| `base_in_words` | In Words | Text | lecture seule; — In Words will be visible once you save the Delivery Note. |
| `grand_total` | Grand Total | Currency | colonne de liste; lecture seule; calculé : `total + total_taxes_and_charges`; devise de `currency` |
| `rounding_adjustment` | Rounding Adjustment | Currency | lecture seule; devise de `currency` |
| `rounded_total` | Rounded Total | Currency | lecture seule; devise de `currency` |
| `in_words` | In Words | Text | lecture seule; — In Words (Export) will be visible once you save the Delivery Note. |
| `tc_name` | Terms | Link → `Terms and Conditions` |  |
| `terms` | Terms and Conditions Details | TextEditor |  |
| `transporter` | Transporter | Link → `Supplier` |  |
| `driver` | Driver | Link → `Driver` |  |
| `lr_no` | Transport Receipt No | Text |  |
| `vehicle_no` | Vehicle No | Text |  |
| `transporter_name` | Transporter Name | Text | lecture seule |
| `driver_name` | Driver Name | Text |  |
| `lr_date` | Transport Receipt Date | Date | défaut `today` |
| `project` | Project | Link → `Project` |  |
| `per_billed` | % Amount Billed | Percent | colonne de liste; lecture seule |
| `customer_group` | Customer Group | Link → `Customer Group` | masqué |
| `territory` | Territory | Link → `Territory` |  |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `select_print_heading` | Print Heading | Link → `Print Heading` |  |
| `language` | Print Language | Link → `Language` | lecture seule |
| `print_without_amount` | Print Without Amount | Boolean | défaut `non` |
| `group_same_items` | Group same items | Boolean | défaut `non` |
| `status` | Status | Select — Draft · To Bill · Partially Billed · Completed · Return · Return Issued · Cancelled · Closed | **requis**; colonne de liste; lecture seule; défaut `Draft` |
| `per_installed` | % Installed | Percent | lecture seule |
| `excise_page` | Excise Page Number | Text | masqué |
| `instructions` | Instructions | LongText |  |
| `auto_repeat` | Auto Repeat | Link → `Auto Repeat` | lecture seule |
| `sales_partner` | Sales Partner | Link → `Sales Partner` |  |
| `commission_rate` | Commission Rate (%) | Number |  |
| `total_commission` | Total Commission | Currency | devise de `currency` |
| `sales_team` | Sales Team | Table → `Sales Team` |  |
| `is_internal_customer` | Is Internal Customer | Boolean | lecture seule |
| `inter_company_reference` | Inter Company Reference | Link → `Purchase Receipt` |  |
| `per_returned` | % Returned | Percent | colonne de liste; lecture seule |
| `set_target_warehouse` | Set Target Warehouse | Link → `Warehouse` |  |
| `represents_company` | Represents Company | Link → `Company` | lecture seule; — Company which internal customer represents. |
| `disable_rounded_total` | Disable Rounded Total | Boolean | défaut `non` |
| `dispatch_address_name` | Dispatch Address Name | Link → `Address` |  |
| `dispatch_address` | Dispatch Address | TextEditor | lecture seule |
| `amount_eligible_for_commission` | Amount Eligible for Commission | Currency | lecture seule; devise de `currency` |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `incoterm` | Incoterm | Link → `Incoterm` |  |
| `named_place` | Named Place | Text |  |
| `delivery_trip` | Delivery Trip | Link → `Delivery Trip` |  |
| `utm_medium` | Medium | Link → `UTM Medium` |  |
| `utm_content` | Content | Text |  |
| `utm_source` | Source | Link → `UTM Source` |  |
| `utm_campaign` | Campaign | Link → `UTM Campaign` |  |
| `company_contact_person` | Company Contact Person | Link → `Contact` |  |
| `last_scanned_warehouse` | Last Scanned Warehouse | Text |  |
| `item_wise_tax_details` | Item Wise Tax Details | Table → `Item Wise Tax Detail` | masqué |
| `title` | Title | Text |  |

## Delivery Note Item

*Delivery Note Item* — `stock/delivery_note_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `barcode` | Barcode | Text |  |
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `is_product_bundle` | Is Product Bundle | Boolean | lecture seule; masqué |
| `product_bundle` | Product Bundle | Link → `Product Bundle` |  |
| `item_name` | Item Name | Text | recopié de `item_code.item_name` |
| `customer_item_code` | Customer's Item Code | Text | lecture seule; masqué |
| `description` | Description | TextEditor |  |
| `qty` | Quantity | Decimal | **requis**; colonne de liste |
| `stock_uom` | Stock UOM | Link → `UOM` | **requis**; lecture seule |
| `uom` | UOM | Link → `UOM` | **requis**; colonne de liste |
| `conversion_factor` | UOM Conversion Factor | Number | **requis**; lecture seule |
| `stock_qty` | Qty in Stock UOM | Decimal | lecture seule |
| `price_list_rate` | Price List Rate | Currency | lecture seule; devise de `parent_currency` |
| `base_price_list_rate` | Price List Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `margin_type` | Margin Type | Select — Percentage · Amount |  |
| `margin_rate_or_amount` | Margin Rate or Amount | Number |  |
| `rate_with_margin` | Rate With Margin | Currency | lecture seule; devise de `parent_currency` |
| `discount_percentage` | Discount (%) on Price List Rate with Margin | Number |  |
| `discount_amount` | Discount Amount | Currency | devise de `parent_currency` |
| `base_rate_with_margin` | Rate With Margin (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `rate` | Rate | Currency | colonne de liste; devise de `parent_currency` |
| `amount` | Amount | Currency | colonne de liste; lecture seule; calculé : `qty * rate`; devise de `parent_currency` |
| `base_rate` | Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_amount` | Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `pricing_rules` | Pricing Rules | LongText | lecture seule; masqué |
| `is_free_item` | Is Free Item | Boolean | lecture seule |
| `net_rate` | Net Rate | Currency | lecture seule; devise de `parent_currency` |
| `net_amount` | Net Amount | Currency | lecture seule; calculé : `amount - discount_amount`; devise de `parent_currency` |
| `base_net_rate` | Net Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_net_amount` | Net Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `weight_per_unit` | Weight Per Unit | Number |  |
| `total_weight` | Total Weight | Number | lecture seule |
| `weight_uom` | Weight UOM | Link → `UOM` |  |
| `warehouse` | Warehouse | Link → `Warehouse` | colonne de liste |
| `target_warehouse` | Target Warehouse | Link → `Warehouse` | masqué |
| `quality_inspection` | Quality Inspection | Link → `Quality Inspection` |  |
| `actual_qty` | Qty (Warehouse) | Decimal | lecture seule |
| `actual_batch_qty` | Available Batch Qty at From Warehouse | Decimal | lecture seule |
| `item_group` | Item Group | Link → `Item Group` | lecture seule; masqué |
| `brand` | Brand Name | Link → `Brand` | lecture seule; masqué |
| `item_tax_rate` | Item Tax Rate | LongText | lecture seule; masqué |
| `expense_account` | Expense Account | Link → `Account` |  |
| `item_tax_template` | Item Tax Template | Link → `Item Tax Template` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `allow_zero_valuation_rate` | Allow Zero Valuation Rate | Boolean | défaut `non` |
| `against_sales_order` | Against Sales Order | Link → `Sales Order` | lecture seule; cible submitted |
| `against_sales_invoice` | Against Sales Invoice | Link → `Sales Invoice` | lecture seule |
| `so_detail` | Against Sales Order Item | Text | lecture seule; masqué |
| `si_detail` | Against Sales Invoice Item | Text | lecture seule; masqué |
| `installed_qty` | Installed Qty | Decimal | lecture seule |
| `billed_amt` | Billed Amt | Currency | lecture seule; devise de `parent_currency` |
| `closed` | Closed | Boolean | lecture seule |
| `page_break` | Page Break | Boolean | défaut `non` |
| `project` | Project | Link → `Project` |  |
| `dn_detail` | Against Delivery Note Item | Text | lecture seule; masqué |
| `returned_qty` | Returned Qty in Stock UOM | Decimal | lecture seule |
| `incoming_rate` | Incoming Rate | Currency | lecture seule; devise de `parent_currency` |
| `stock_uom_rate` | Rate of Stock UOM | Currency | lecture seule; devise de `parent_currency` |
| `grant_commission` | Grant Commission | Boolean | lecture seule |
| `pick_list_item` | Pick List Item | Text | lecture seule; masqué |
| `purchase_order` | Purchase Order | Link → `Purchase Order` | lecture seule |
| `purchase_order_item` | Purchase Order Item | Text | lecture seule |
| `has_item_scanned` | Has Item Scanned | Boolean | lecture seule |
| `material_request` | Material Request | Link → `Material Request` |  |
| `material_request_item` | Material Request Item | Text |  |
| `received_qty` | Received Qty | Decimal | lecture seule |
| `packed_qty` | Packed Qty | Decimal | lecture seule |
| `serial_and_batch_bundle` | Serial and Batch Bundle | Link → `Serial and Batch Bundle` |  |
| `serial_no` | Serial No | LongText |  |
| `batch_no` | Batch No | Link → `Batch` |  |
| `use_serial_batch_fields` | Use Serial No / Batch Fields | Boolean | défaut `non` |
| `distributed_discount_amount` | Distributed Discount Amount | Currency | devise de `parent_currency` |
| `mapped_additional_discount_amount` | Additional Discount per Stock Unit | Currency | lecture seule; devise de `parent_currency`; — Tax-exclusive additional discount carried from a source document, per stock unit. |
| `company_total_stock` | Qty (Company) | Number | lecture seule |
| `against_pick_list` | Against Pick List | Link → `Pick List` | lecture seule |

## Delivery Settings

*Delivery Settings* — `stock/delivery_settings.yaml` · document unique

- **Icône** : `settings`
- **Permissions explicites** — `create` : 0, `delete` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `dispatch_template` | Dispatch Notification Template | Link → `Email Template` |  |
| `dispatch_attachment` | Dispatch Notification Attachment | Link → `Print Format` | — Leave blank to use the standard Delivery Note format |
| `send_with_attachment` | Send with Attachment | Boolean | défaut `non` |
| `stop_delay` | Delay between Delivery Stops | Int | — In minutes |

## Delivery Stop

*Delivery Stop* — `stock/delivery_stop.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `customer` | Customer | Link → `Customer` | colonne de liste |
| `address` | Address Name | Link → `Address` | **requis**; colonne de liste |
| `locked` | Locked | Boolean | colonne de liste; défaut `non` |
| `customer_address` | Customer Address | TextEditor | lecture seule |
| `visited` | Visited | Boolean | défaut `non` |
| `delivery_note` | Delivery Note | Link → `Delivery Note` | colonne de liste; lecture seule |
| `grand_total` | Grand Total | Currency | lecture seule; devise de `parent_company.default_currency` |
| `contact` | Contact Name | Link → `Contact` |  |
| `email_sent_to` | Email sent to | Text | lecture seule |
| `customer_contact` | Customer Contact | TextEditor | lecture seule |
| `distance` | Distance | Number | lecture seule |
| `estimated_arrival` | Estimated Arrival | Datetime | colonne de liste |
| `lat` | Latitude | Number | masqué |
| `uom` | UOM | Link → `UOM` | lecture seule |
| `lng` | Longitude | Number | masqué |
| `details` | Details | TextEditor |  |

## Delivery Trip

*Delivery Trip* — `stock/delivery_trip.yaml` · soumis

- **Numérotation** : série `DT-{YYYY}-{#####}`
- **Titre** : `status`
- **Icône** : `route`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — MAT-DT-.YYYY.- |  |
| `company` | Company | Link → `Company` | **requis** |
| `email_notification_sent` | Initial Email Notification Sent | Boolean | lecture seule |
| `driver` | Driver | Link → `Driver` |  |
| `driver_name` | Driver Name | Text | colonne de liste; lecture seule |
| `total_distance` | Total Estimated Distance | Number | lecture seule |
| `uom` | Distance UOM | Link → `UOM` | lecture seule |
| `vehicle` | Vehicle | Link → `Vehicle` | **requis** |
| `departure_time` | Departure Time | Datetime | **requis**; colonne de liste |
| `delivery_stops` | Delivery Stop | Table → `Delivery Stop` |  |
| `status` | Status | Select — Draft · Scheduled · In Transit · Completed · Cancelled | lecture seule |
| `driver_address` | Driver Address | Link → `Address` |  |
| `driver_email` | Driver Email | Text | lecture seule |
| `employee` | Employee | Link → `Employee` | lecture seule |

## Inventory Dimension

*Inventory Dimension* — `stock/inventory_dimension.yaml`

- **Titre** : `reference_document`
- **Icône** : `layers`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `reference_document` | Reference Document | Text | **requis**; colonne de liste |
| `dimension_name` | Dimension Name | Text | **requis**; colonne de liste |
| `document_type` | Apply to Document | Text |  |
| `istable` |  Is Child Table | Boolean | lecture seule; masqué |
| `condition` | Conditional Rule | Code |  |
| `apply_to_all_doctypes` | Apply to All Inventory Documents | Boolean | défaut `oui` |
| `target_fieldname` | Target Fieldname (Stock Ledger Entry) | Text | lecture seule |
| `source_fieldname` | Source Fieldname | Text | lecture seule |
| `type_of_transaction` | Type of Transaction | Select — Inward · Outward · Both |  |
| `mandatory_depends_on` | Mandatory Depends On | LongText | — To apply condition on parent field use parent.field_name and to apply condition on child table use doc.field_n |
| `reqd` | Mandatory | Boolean | défaut `non` |
| `validate_negative_stock` | Validate Negative Stock | Boolean | défaut `non` |

## Item

*Item* — `stock/item.yaml`

- **Titre** : `item_code`
- **Icône** : `package`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — STO-ITEM-.YYYY.- |  |
| `item_code` | Item Code | Text | **requis** |
| `variant_of` | Variant Of | Link → `Item` | lecture seule; — If item is a variant of another item then description, image, pricing, taxes etc will be set from the template |
| `item_name` | Item Name | Text |  |
| `item_group` | Item Group | Link → `Item Group` | **requis**; colonne de liste |
| `stock_uom` | Default Unit of Measure | Link → `UOM` | **requis**; colonne de liste |
| `disabled` | Disabled | Boolean | défaut `non`; — Disabled items cannot be selected in any transaction. |
| `allow_alternative_item` | Allow Alternative Item | Boolean | défaut `non`; — Allow substituting this item with an alternative from the Item Alternative list when stock is unavailable. |
| `is_stock_item` | Maintain Stock | Boolean | défaut `oui`; — ERPNext will make a stock ledger entry for each transaction of this item. Keep unchecked for non-stock or serv |
| `include_item_in_manufacturing` | Include Item In Manufacturing | Boolean | défaut `oui`; — Enable for raw material items used in BOM. Uncheck for additional services like 'washing' used in manufacturin |
| `opening_stock` | Opening Stock | Number | masqué |
| `valuation_rate` | Valuation Rate | Currency |  |
| `standard_rate` | Standard Selling Rate | Currency | — Creates an Item Price automatically when the item is saved |
| `is_fixed_asset` | Is Fixed Asset | Boolean | colonne de liste; défaut `non`; — Enable if this item is a company asset like machinery or furniture. |
| `asset_category` | Asset Category | Link → `Asset Category` | visible si `is_fixed_asset`; obligatoire si `is_fixed_asset` |
| `image` | Image | Image | masqué |
| `brand` | Brand | Link → `Brand` |  |
| `description` | Description | TextEditor |  |
| `barcodes` | Barcodes | Table → `Item Barcode` |  |
| `shelf_life_in_days` | Shelf Life In Days | Int | visible si `is_stock_item` |
| `end_of_life` | End of Life | Date | défaut `2099-12-31`; — Defines the date after which the item can no longer be used in transactions or manufacturing |
| `default_material_request_type` | Default Material Request Type | Select — Purchase · Material Transfer · Material Issue · Manufacture · Customer Provided | défaut `Purchase` |
| `valuation_method` | Valuation Method | Select — FIFO · Moving Average · LIFO · Standard Cost | visible si `is_stock_item`; — Serialized items are valued at Moving Average once stock transactions exist and Serial No Wise Valuation is di |
| `warranty_period` | Warranty Period (in days) | Text |  |
| `weight_per_unit` | Weight Per Unit | Number |  |
| `weight_uom` | Weight UOM | Link → `UOM` |  |
| `reorder_levels` | Reorder level based on Warehouse | Table → `Item Reorder` | — Will also apply for variants unless overridden |
| `uoms` | Uoms | Table → `UOM Conversion Detail` |  |
| `has_batch_no` | Has Batch No | Boolean | défaut `non`; visible si `is_stock_item`; — Track this item in batches. Cannot be changed after a stock transaction exists. |
| `create_new_batch` | Automatically Create New Batch | Boolean | défaut `non`; visible si `has_batch_no`; — Batch number will be auto-created in format AAAA.00001 if not specified in transactions. Leave blank to always |
| `batch_number_series` | Batch Number Series | Text | visible si `has_batch_no`; — Example: ABCD.#####. If series is set and Batch No is not mentioned in transactions, then automatic batch numb |
| `has_expiry_date` | Has Expiry Date | Boolean | défaut `non`; visible si `has_batch_no`; — Batch number will be created based on expiry date. Expiry dates can be set in the Batch master. |
| `retain_sample` | Retain Sample | Boolean | défaut `non`; visible si `has_batch_no`; — Enable to reserve a small sample from each batch for any analysis arising ahead |
| `sample_quantity` | Max Sample Quantity | Int | visible si `retain_sample`; — Maximum sample quantity that can be retained |
| `has_serial_no` | Has Serial No | Boolean | défaut `non`; visible si `is_stock_item`; — Track each unit with a unique serial number for warranty and return tracking. Cannot be changed after a stock  |
| `serial_no_series` | Serial Number Series | Text | visible si `has_serial_no`; — Example: ABCD.##### If series is set and Serial No is not mentioned in transactions, then automatic serial num |
| `use_serial_no_wise_valuation` | Use Serial No Wise Valuation | Boolean | défaut `oui`; visible si `has_serial_no`; — Value every outward movement at each Serial No's own incoming rate. If unchecked, the item is valued at Moving |
| `has_variants` | Has Variants | Boolean | défaut `non`; — If this item has variants, then it cannot be selected in sales orders etc. |
| `variant_based_on` | Variant Based On | Select — Item Attribute · Manufacturer | défaut `Item Attribute`; visible si `has_variants` |
| `attributes` | Variant Attributes | Table → `Item Variant Attribute` | masqué |
| `item_defaults` | Item Defaults | Table → `Item Default` |  |
| `is_purchase_item` | Allow Purchase | Boolean | défaut `oui`; — Allow this item to be used in purchase transactions. |
| `purchase_uom` | Default Purchase Unit of Measure | Link → `UOM` | visible si `is_purchase_item` |
| `min_order_qty` | Minimum Order Qty | Decimal | défaut `0.000`; visible si `is_purchase_item`; — Minimum quantity should be as per Stock UOM |
| `safety_stock` | Safety Stock | Number | — Minimum stock level to maintain as a buffer. Used to calculate recommended reorder level: Reorder Level = Safe |
| `lead_time_days` | Lead Time in days | Int | visible si `is_purchase_item`; — Average time taken by the supplier to deliver |
| `last_purchase_rate` | Last Purchase Rate | Number | lecture seule; — The rate at which this item was last purchased via a Purchase Invoice. Auto-updated by the system. |
| `is_customer_provided_item` | Is Customer Provided Item | Boolean | défaut `non`; — Enable if this item is provided by a customer and received via Stock Entry. |
| `delivered_by_supplier` | Delivered by Supplier (Drop Ship) | Boolean | défaut `non`; — If checked, this item is treated as drop-shipped by default in Sales Orders, Sales Invoices and Purchase Order |
| `supplier_items` | Item Supplier | Table → `Item Supplier` |  |
| `country_of_origin` | Country of Origin | Link → `Country` |  |
| `customs_tariff_number` | Customs Tariff Number | Link → `Customs Tariff Number` |  |
| `sales_uom` | Default Sales Unit of Measure | Link → `UOM` | visible si `is_sales_item` |
| `is_sales_item` | Allow Sales | Boolean | colonne de liste; défaut `oui`; — Allow this item to be used in sales transactions. |
| `max_discount` | Max Discount (%) | Number | visible si `is_sales_item`; — Maximum discount % allowed when selling this item. Eg: if set to 20%, a discount greater than 20% cannot be ap |
| `enable_deferred_revenue` | Enable Deferred Revenue | Boolean | défaut `non`; — Income from this item will be recognized over a period of months instead of all at once. Eg: annual subscripti |
| `no_of_months` | No of Months (Revenue) | Int | visible si `enable_deferred_revenue` |
| `enable_deferred_expense` | Enable Deferred Expense | Boolean | défaut `non`; — Expense for this item will be recognized over a period of months. Eg: prepaid insurance or annual software lic |
| `no_of_months_exp` | No of Months (Expense) | Int | visible si `enable_deferred_expense` |
| `customer_items` | Customer Items | Table → `Item Customer Detail` |  |
| `taxes` | Taxes | Table → `Item Tax` | — Will also apply for variants |
| `inspection_required_before_purchase` | Inspection Required before Purchase | Boolean | défaut `non`; — A quality inspection must be completed before generating a Purchase Receipt for this item. |
| `inspection_required_before_delivery` | Inspection Required before Delivery | Boolean | défaut `non`; — A quality inspection must be completed before generating a Delivery Note for this item. |
| `quality_inspection_template` | Quality Inspection Template | Link → `Quality Inspection Template` |  |
| `default_bom` | Default BOM | Link → `BOM` | lecture seule |
| `is_sub_contracted_item` | Is Subcontracted Item | Boolean | défaut `non`; — Enable if a vendor manufactures this item for you. You can choose to provide them raw materials using the defa |
| `customer_code` | Customer Code | LongText | masqué |
| `total_projected_qty` | Total Projected Qty | Decimal | lecture seule; masqué |
| `over_delivery_receipt_allowance` | Over Delivery/Receipt Allowance (%) | Number | — Percentage by which over-delivery or over-receipt is allowed against a Sales/Purchase Order for this item. If  |
| `over_billing_allowance` | Over Billing Allowance (%) | Number | — Percentage by which over-billing is allowed against a Sales/Purchase Order for this item. If not set, value fr |
| `auto_create_assets` | Auto create assets on purchase | Boolean | défaut `non`; visible si `is_fixed_asset` |
| `default_item_manufacturer` | Default Item Manufacturer | Link → `Manufacturer` | lecture seule |
| `default_manufacturer_part_no` | Default Manufacturer Part No | Text | lecture seule |
| `grant_commission` | Grant Commission | Boolean | défaut `oui`; — If enabled, sales from this item will be included in Sales Person and Sales Partner commission calculations |
| `is_grouped_asset` | Create Grouped Asset | Boolean | défaut `non`; visible si `is_fixed_asset`; — Creates a single grouped asset instead of individual assets when purchased in bulk. |
| `allow_negative_stock` | Allow Negative Stock | Boolean | défaut `non`; visible si `is_stock_item`; — Allow stock to go below zero for this item, even if negative stock is disabled in Stock Settings. |
| `purchase_tax_withholding_category` | Purchase Tax Withholding Category | Link → `Tax Withholding Category` |  |
| `sales_tax_withholding_category` | Sales Tax Withholding Category | Link → `Tax Withholding Category` |  |
| `restrict_to_companies` | Restrict to Companies | Boolean | défaut `non`; — If checked, this Item is only available for transactions in the companies listed below. |
| `allowed_companies` | Allowed Companies | Table → `Company Restriction` |  |

## Item Alternative

*Item Alternative* — `stock/item_alternative.yaml`

- **Titre** : `item_code`
- **Icône** : `replace`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `alternative_item_code` | Alternative Item Code | Link → `Item` | **requis**; colonne de liste |
| `two_way` | Two-way | Boolean | défaut `non` |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `alternative_item_name` | Alternative Item Name | Text | lecture seule |

## Item Attribute

*Item Attribute* — `stock/item_attribute.yaml`

- **Titre** : `attribute_name`
- **Icône** : `tags`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `attribute_name` | Attribute Name | Text | **requis**; colonne de liste |
| `numeric_values` | Numeric Values | Boolean | défaut `non` |
| `from_range` | From Range | Number | défaut `0.0` |
| `increment` | Increment | Number | défaut `0.0` |
| `to_range` | To Range | Number | défaut `0.0` |
| `item_attribute_values` | Item Attribute Values | Table → `Item Attribute Value` |  |
| `disabled` | Disabled | Boolean | défaut `non` |

## Item Attribute Value

*Item Attribute Value* — `stock/item_attribute_value.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `attribute_value` | Attribute Value | Text | **requis**; colonne de liste |
| `abbr` | Abbreviation | Text | **requis**; colonne de liste; — This will be appended to the Item Code of the variant. For example, if your abbreviation is "SM", and the item |

## Item Barcode

*Item Barcode* — `stock/item_barcode.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `barcode` | Barcode | Text | **requis**; colonne de liste |
| `barcode_type` | Barcode Type | Select — EAN · UPC-A · CODE-39 · EAN-13 · EAN-8 · GS1 · GTIN · GTIN-14 · ISBN · ISBN-10 · ISBN-13 · ISSN · JAN · PZN · UPC | colonne de liste |
| `uom` | UOM | Link → `UOM` | colonne de liste |

## Item Customer Detail

*Item Customer Detail* — `stock/item_customer_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `customer_name` | Customer Name | Link → `Customer` | colonne de liste |
| `customer_group` | Customer Group | Link → `Customer Group` | colonne de liste |
| `ref_code` | Ref Code | Text | **requis**; colonne de liste; — Enter the Item Code that this customer uses at their end. This will be shown in Sales Orders for the customer' |

## Item Default

*Item Default* — `stock/item_default.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `default_warehouse` | Warehouse | Link → `Warehouse` | colonne de liste |
| `default_price_list` | Price List | Link → `Price List` | colonne de liste; — Default price list for buying or selling this item |
| `default_discount_account` | Discount Account | Link → `Account` |  |
| `default_inventory_account` | Inventory Account | Link → `Account` | — Stock account where inventory value for this item will be tracked |
| `inventory_account_currency` | Inventory Account Currency | Link → `Currency` | lecture seule |
| `vf_default_warehouse` | Warehouse | Text | lecture seule |
| `vf_default_price_list` | Price List | Text | lecture seule |
| `vf_default_discount_account` | Discount Account | Text | lecture seule |
| `vf_default_inventory_account` | Inventory Account | Text | lecture seule |
| `buying_cost_center` | Buying Cost Center | Link → `Cost Center` | — Cost center used for tracking purchase expenses for this item |
| `default_supplier` | Supplier | Link → `Supplier` | — This supplier will be auto-selected in new purchase transactions |
| `expense_account` | Expense Account | Link → `Account` | — Account where the cost of this item will be debited on purchase |
| `default_provisional_account` | Provisional Account (Service) | Link → `Account` | — Provisional liability account used for service items before invoice is received |
| `purchase_expense_account` | Purchase Expense Account | Link → `Account` | — Account to record additional purchase expenses like freight or customs |
| `purchase_expense_contra_account` | Purchase Expense Contra Account | Link → `Account` | — Used to balance the books when recording extra purchase costs |
| `expenses_added_to_stock_account` | Expenses Added To Stock Account | Link → `Account` | — Account to track value added to stock via Stock Entry, Stock Reconciliation or Landed Cost Voucher |
| `expenses_added_to_stock_contra_account` | Expenses Added To Stock Contra Account | Link → `Account` | — Used to balance the books when recording expenses added to stock |
| `purchase_price_variance_account` | Purchase Price Variance Account | Link → `Account` | — For Standard Cost items: the purchase price vs standard rate difference is booked here. Falls back to the Comp |
| `manufacturing_variance_account` | Manufacturing Variance Account | Link → `Account` | — For Standard Cost items: the Manufacture/Repack consumed cost vs standard rate difference is booked here. Fall |
| `vf_buying_cost_center` | Buying Cost Center | Text | lecture seule |
| `vf_default_supplier` | Supplier | Text | lecture seule |
| `vf_expense_account` | Expense Account | Text | lecture seule |
| `vf_default_provisional_account` | Provisional Account (Service) | Text | lecture seule |
| `vf_purchase_expense_account` | Purchase Expense Account | Text | lecture seule |
| `vf_purchase_expense_contra_account` | Purchase Expense Contra Account | Text | lecture seule |
| `vf_expenses_added_to_stock_account` | Expenses Added To Stock Account | Text | lecture seule |
| `vf_expenses_added_to_stock_contra_account` | Expenses Added To Stock Contra Account | Text | lecture seule |
| `selling_cost_center` | Selling Cost Center | Link → `Cost Center` | — Cost center used for tracking sales revenue for this item |
| `income_account` | Income Account | Link → `Account` | — Account where revenue from selling this item will be credited |
| `vf_selling_cost_center` | Selling Cost Center | Text | lecture seule |
| `vf_income_account` | Income Account | Text | lecture seule |
| `default_cogs_account` | COGS Account | Link → `Account` | — Account where cost of goods sold will be posted when this item is sold |
| `vf_default_cogs_account` | COGS Account | Text | lecture seule |
| `deferred_expense_account` | Expense Account | Link → `Account` |  |
| `deferred_revenue_account` | Revenue Account | Link → `Account` |  |
| `vf_deferred_expense_account` | Deferred Expense Account | Text | lecture seule |
| `vf_deferred_revenue_account` | Deferred Revenue Account | Text | lecture seule |

## Item Lead Time

*Item Lead Time* — `stock/item_lead_time.yaml`

- **Titre** : `item_code`
- **Icône** : `clock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` |  |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `buffer_time` | Buffer Time | Int | colonne de liste; — In Days |
| `no_of_shift` | No of Shift | Int | défaut `1` |
| `manufacturing_time_in_mins` | Manufacturing Time | Int | — Per Unit Time in Mins |
| `total_workstation_time` | Total Workstation Time (In Hours) | Int | — Per Day Shift Time (In Hours) * No of Workstations * No of Shift |
| `daily_yield` | Daily Yield (%) | Percent | défaut `90.0`; — (Good Units Produced / Total Units Produced) × 100 |
| `capacity_per_day` | Capacity | Int | colonne de liste; — (Daily Yield * No of Units Produced) / 100 |
| `no_of_units_produced` | No of Units Produced | Int | — (Total Workstation Time / Manufacturing Time) * 60 |
| `purchase_time` | Purchase Time | Int | colonne de liste; — In Days |
| `shift_time_in_hours` | Shift Time (In Hours) | Int | — Per Day |
| `no_of_workstations` | No of Workstations | Int | — Similar types of workstations where the same operations run in parallel. |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `supplier_lead_times` | Supplier Lead Times | Table → `Item Lead Time Supplier` | — Overrides the Purchase Time above for the selected supplier. The row marked as default is used when no supplie |

## Item Lead Time Supplier

*Item Lead Time Supplier* — `stock/item_lead_time_supplier.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `supplier` | Supplier | Link → `Supplier` | **requis**; colonne de liste |
| `purchase_time` | Purchase Time (Days) | Int | colonne de liste |
| `buffer_time` | Buffer Time (Days) | Int | colonne de liste |
| `is_default` | Is Default | Boolean | colonne de liste; défaut `non` |

## Item Manufacturer

*Item Manufacturer* — `stock/item_manufacturer.yaml`

- **Titre** : `item_code`
- **Icône** : `factory`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `manufacturer` | Manufacturer | Link → `Manufacturer` | **requis**; colonne de liste |
| `manufacturer_part_no` | Manufacturer Part Number | Text | **requis**; colonne de liste |
| `item_code` | Item Code | Link → `Item` | **requis** |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `description` | Description | LongText | lecture seule |
| `is_default` | Is Default | Boolean | colonne de liste; défaut `non` |

## Item Price

*Item Price* — `stock/item_price.yaml`

- **Vues** : calendar
- **Titre** : `item_code`
- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `uom` | UOM | Link → `UOM` | **requis** |
| `packing_unit` | Packing Unit | Int | défaut `0`; — Quantity  that must be bought or sold per UOM |
| `item_name` | Item Name | Text | colonne de liste; lecture seule; recopié de `item_code.item_name` |
| `brand` | Brand | Link → `Brand` | colonne de liste; lecture seule |
| `item_description` | Item Description | TextEditor | lecture seule |
| `price_list` | Price List | Link → `Price List` | **requis**; colonne de liste |
| `customer` | Customer | Link → `Customer` |  |
| `supplier` | Supplier | Link → `Supplier` |  |
| `buying` | Buying | Boolean | lecture seule |
| `selling` | Selling | Boolean | lecture seule |
| `currency` | Currency | Link → `Currency` | lecture seule |
| `price_list_rate` | Rate | Currency | **requis**; colonne de liste; devise de `currency` |
| `valid_from` | Valid From | Date | défaut `today` |
| `lead_time_days` | Lead Time in days | Int | défaut `0` |
| `valid_upto` | Valid Up To | Date |  |
| `note` | Note | LongText |  |
| `reference` | Reference | Text | colonne de liste |
| `batch_no` | Batch No | Link → `Batch` |  |

## Item Quality Inspection Parameter

*Item Quality Inspection Parameter* — `stock/item_quality_inspection_parameter.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `specification` | Parameter | Link → `Quality Inspection Parameter` | **requis**; colonne de liste |
| `value` | Acceptance Criteria Value | Text | colonne de liste |
| `acceptance_formula` | Acceptance Criteria Formula | Code | — Simple Python formula applied on Reading fields.<br> Numeric eg. 1: <b>reading_1 &gt; 0.2 and reading_1 &lt; 0 |
| `formula_based_criteria` | Formula Based Criteria | Boolean | défaut `non` |
| `min_value` | Minimum Value | Number | colonne de liste |
| `max_value` | Maximum Value | Number | colonne de liste |
| `numeric` | Numeric | Boolean | colonne de liste; défaut `oui` |
| `parameter_group` | Parameter Group | Link → `Quality Inspection Parameter Group` | lecture seule |

## Item Reorder

*Item Reorder* — `stock/item_reorder.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `warehouse_group` | Check Availability in Warehouse | Link → `Warehouse` | colonne de liste |
| `warehouse` | Request for | Link → `Warehouse` | **requis**; colonne de liste |
| `warehouse_reorder_level` | Re-order Level | Number | colonne de liste |
| `warehouse_reorder_qty` | Re-order Qty | Decimal | colonne de liste |
| `material_request_type` | Material Request Type | Select — Purchase · Transfer · Material Issue · Manufacture | **requis**; colonne de liste |

## Item Standard Cost

*Item Standard Cost* — `stock/item_standard_cost.yaml` · soumis

- **Numérotation** : série `ISC-{YYYY}-{#####}`
- **Titre** : `item_code`
- **Icône** : `coins`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — ISC-.YYYY.- | **requis**; défaut `ISC-.YYYY.-` |
| `item_code` | Item | Link → `Item` | **requis**; colonne de liste |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `standard_rate` | Standard Valuation Rate | Currency | **requis**; colonne de liste; devise de `company.default_currency` |
| `effective_date` | Effective Date | Date | **requis**; colonne de liste; défaut `today` |
| `revaluation_entry` | Revaluation Entry | Link → `Stock Reconciliation` | lecture seule; — Stock Reconciliation that revalues on-hand stock to this standard rate: auto-created when the rate is changed  |

## Item Supplier

*Item Supplier* — `stock/item_supplier.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `supplier` | Supplier | Link → `Supplier` | **requis**; colonne de liste |
| `supplier_part_no` | Supplier Part Number | Text | colonne de liste |

## Item Tax

*Item Tax* — `stock/item_tax.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_tax_template` | Item Tax Template | Link → `Item Tax Template` | **requis**; colonne de liste |
| `tax_category` | Tax Category | Link → `Tax Category` | colonne de liste |
| `valid_from` | Valid From | Date | colonne de liste |
| `maximum_net_rate` | Maximum Net Rate | Number | colonne de liste |
| `minimum_net_rate` | Minimum Net Rate | Number | colonne de liste |

## Item Variant Attribute

*Item Variant Attribute* — `stock/item_variant_attribute.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `variant_of` | Variant Of | Link → `Item` |  |
| `attribute` | Attribute | Link → `Item Attribute` | **requis**; colonne de liste |
| `attribute_value` | Attribute Value | Text | colonne de liste |
| `numeric_values` | Numeric Values | Boolean | défaut `non` |
| `from_range` | From Range | Number |  |
| `increment` | Increment | Number |  |
| `to_range` | To Range | Number |  |
| `disabled` | Disabled | Boolean | défaut `non` |

## Item Variant Settings

*Item Variant Settings* — `stock/item_variant_settings.yaml` · document unique

- **Icône** : `settings`
- **Permissions explicites** — `create` : 0, `delete` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `do_not_update_variants` | Do not update variants on save | Boolean | défaut `non`; — Fields will be copied over only at time of creation. |
| `allow_rename_attribute_value` | Allow Rename Attribute Value | Boolean | défaut `non`; — Rename Attribute Value in Item Attribute. |
| `fields` | Fields | Table → `Variant Field` |  |
| `allow_different_uom` | Allow Variant UOM to be different from Template UOM | Boolean | défaut `non` |

## Landed Cost Item

*Landed Cost Item* — `stock/landed_cost_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste; lecture seule |
| `description` | Description | TextEditor | colonne de liste; lecture seule |
| `receipt_document_type` | Receipt Document Type | Text | lecture seule |
| `receipt_document` | Receipt Document | DynamicLink → `receipt_document_type` | lecture seule |
| `qty` | Qty | Decimal | colonne de liste; lecture seule |
| `rate` | Rate | Currency | lecture seule; devise de `parent_company.default_currency` |
| `amount` | Amount | Currency | **requis**; colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `applicable_charges` | Applicable Charges | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `purchase_receipt_item` | Purchase Receipt Item | Text | lecture seule; masqué |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `is_fixed_asset` | Is Fixed Asset | Boolean | lecture seule; masqué |
| `stock_entry_item` | Stock Entry Item | Text | lecture seule |

## Landed Cost Purchase Receipt

*Landed Cost Purchase Receipt* — `stock/landed_cost_purchase_receipt.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `receipt_document_type` | Receipt Document Type | Text | **requis**; colonne de liste |
| `receipt_document` | Receipt Document | DynamicLink → `receipt_document_type` | **requis**; colonne de liste |
| `supplier` | Supplier | Link → `Supplier` | colonne de liste; lecture seule |
| `posting_date` | Posting Date | Date | lecture seule |
| `grand_total` | Grand Total | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |

## Landed Cost Taxes and Charges

*Landed Cost Taxes and Charges* — `stock/landed_cost_taxes_and_charges.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `description` | Description | LongText | **requis**; colonne de liste |
| `amount` | Amount | Currency | **requis**; colonne de liste |
| `expense_account` | Expense Account | Link → `Account` | colonne de liste |
| `account_currency` | Account Currency | Link → `Currency` | lecture seule |
| `exchange_rate` | Exchange Rate | Number |  |
| `base_amount` | Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `has_corrective_cost` | Has Corrective Cost | Boolean | lecture seule |
| `has_operating_cost` | Has Operating Cost | Boolean | lecture seule |
| `operation_id` | Operation ID | Text | lecture seule; masqué |
| `qty` | Qty | Decimal | lecture seule; masqué |
| `operating_component` | Operating Component | Text | lecture seule; masqué |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |

## Landed Cost Vendor Invoice

*Landed Cost Vendor Invoice* — `stock/landed_cost_vendor_invoice.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `vendor_invoice` | Vendor Invoice | Link → `Purchase Invoice` | colonne de liste |
| `amount` | Amount (Company Currency) | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |

## Landed Cost Voucher

*Landed Cost Voucher* — `stock/landed_cost_voucher.yaml` · soumis

- **Numérotation** : série `LCV-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `company`
- **Icône** : `ship`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — MAT-LCV-.YYYY.- | **requis** |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `purchase_receipts` | Vouchers | Table → `Landed Cost Purchase Receipt` |  |
| `items` | Receipt Items | Table → `Landed Cost Item` |  |
| `taxes` | Landed Cost | Table → `Landed Cost Taxes and Charges` |  |
| `total_taxes_and_charges` | Total Landed Cost (Company Currency) | Currency | **requis**; lecture seule; devise de `company.default_currency` |
| `distribute_charges_based_on` | Distribute Charges Based On | Select — Qty · Amount · Distribute Manually | **requis** |
| `posting_date` | Posting Date | Date | **requis**; défaut `today` |
| `vendor_invoices` | Vendor Invoices | Table → `Landed Cost Vendor Invoice` |  |
| `total_vendor_invoices_cost` | Total Vendor Invoices Cost (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |

## Manufacturer

*Manufacturer* — `stock/manufacturer.yaml`

- **Titre** : `full_name`
- **Icône** : `factory`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `short_name` | Short Name | Text | **requis**; — Limited to 12 characters |
| `full_name` | Full Name | Text | colonne de liste |
| `website` | Website | Text |  |
| `country` | Country | Link → `Country` |  |
| `logo` | Logo | Image |  |
| `notes` | Notes | LongText |  |

## Material Request

*Material Request* — `stock/material_request.yaml` · soumis

- **Numérotation** : série `MR-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `status`
- **Icône** : `clipboard-list`
- **Workflow** : États : Brouillon → À approuver → Approuvée → Refusée → Annulée
- **Workflow** : Actions : `Annuler`, `Approuver`, `Refuser`, `Reprendre`, `Soumettre`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — MAT-MR-.YYYY.- | **requis** |
| `title` | Title | Text | masqué |
| `material_request_type` | Purpose | Select — Purchase · Material Transfer · Material Issue · Manufacture · Subcontracting · Customer Provided | **requis**; colonne de liste |
| `customer` | Customer | Link → `Customer` | visible si `material_request_type == 'Customer Provided'`; obligatoire si `material_request_type == 'Customer Provided'` |
| `schedule_date` | Required By | Date | colonne de liste |
| `company` | Company | Link → `Company` | **requis** |
| `scan_barcode` | Scan Barcode | Text |  |
| `items` | Items | Table → `Material Request Item` |  |
| `transaction_date` | Transaction Date | Date | **requis**; colonne de liste; défaut `today` |
| `status` | Status | Select — Draft · Submitted · Stopped · Cancelled · Pending · Partially Ordered · Partially Received · Ordered · Issued · Transferred · Received | lecture seule |
| `per_ordered` | % Ordered | Percent | lecture seule |
| `per_received` | % Received | Percent | lecture seule |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `select_print_heading` | Print Heading | Link → `Print Heading` |  |
| `tc_name` | Terms | Link → `Terms and Conditions` |  |
| `terms` | Terms and Conditions Content | TextEditor |  |
| `job_card` | Job Card | Link → `Job Card` | lecture seule |
| `set_warehouse` | Set Target Warehouse | Link → `Warehouse` |  |
| `set_from_warehouse` | Set Source Warehouse | Link → `Warehouse` | visible si `material_request_type == 'Material Transfer'` |
| `transfer_status` | Transfer Status | Select — Not Started · In Transit · Completed | lecture seule |
| `work_order` | Work Order | Link → `Work Order` | lecture seule |
| `buying_price_list` | Price List | Link → `Price List` |  |
| `last_scanned_warehouse` | Last Scanned Warehouse | Text |  |
| `auto_created_via_reorder` | Auto Created (Reorder) | Boolean | lecture seule |

## Material Request Item

*Material Request Item* — `stock/material_request_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Item Name | Text | recopié de `item_code.item_name` |
| `description` | Description | TextEditor |  |
| `qty` | Quantity | Decimal | **requis**; colonne de liste |
| `uom` | UOM | Link → `UOM` | **requis**; colonne de liste |
| `conversion_factor` | UOM Conversion Factor | Number | **requis** |
| `stock_uom` | Stock UOM | Link → `UOM` | **requis**; lecture seule |
| `warehouse` | Target Warehouse | Link → `Warehouse` | colonne de liste |
| `schedule_date` | Required By | Date | **requis**; colonne de liste |
| `rate` | Rate | Currency | devise de `parent_company.default_currency` |
| `amount` | Amount | Currency | lecture seule; devise de `parent_company.default_currency` |
| `stock_qty` | Stock Qty | Decimal | lecture seule |
| `item_group` | Item Group | Link → `Item Group` | lecture seule |
| `brand` | Brand | Link → `Brand` | lecture seule |
| `lead_time_date` | Lead Time Date | Date | lecture seule |
| `sales_order` | Sales Order | Link → `Sales Order` | lecture seule |
| `sales_order_item` | Sales Order Item | Text | lecture seule; masqué |
| `project` | Project | Link → `Project` |  |
| `production_plan` | Production Plan | Link → `Production Plan` | lecture seule |
| `material_request_plan_item` | Material Request Plan Item | Text | lecture seule |
| `min_order_qty` | Min Order Qty | Decimal | lecture seule |
| `projected_qty` | Projected Qty | Decimal | lecture seule |
| `actual_qty` | Actual Qty | Decimal | lecture seule |
| `ordered_qty` | Completed Qty | Decimal | lecture seule |
| `expense_account` | Expense Account | Link → `Account` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `page_break` | Page Break | Boolean | défaut `non` |
| `received_qty` | Received Qty | Decimal | lecture seule |
| `manufacturer` | Manufacturer | Link → `Manufacturer` |  |
| `manufacturer_part_no` | Manufacturer Part Number | Text | lecture seule |
| `from_warehouse` | Source Warehouse | Link → `Warehouse` |  |
| `bom_no` | BOM No | Link → `BOM` |  |
| `job_card_item` | Job Card Item | Text | masqué |
| `wip_composite_asset` | WIP Composite Asset | Link → `Asset` |  |
| `price_list_rate` | Price List Rate | Currency | lecture seule; masqué; devise de `parent_company.default_currency` |
| `reorder_level` | Reorder Level | Number | lecture seule |
| `reorder_qty` | Reorder Qty | Decimal | lecture seule |
| `projected_on_hand` | Projected On Hand | Number | lecture seule; — If the reorder check is set at the Group warehouse level, the available quantity becomes the sum of the projec |
| `picked_qty` | Picked Qty | Decimal | lecture seule; masqué |
| `packed_item` | Packed Item | Text | lecture seule; masqué |

## Packed Item

*Packed Item* — `stock/packed_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `packed_parent_item` | Parent Item | Link → `Item` | colonne de liste; lecture seule |
| `item_code` | Item Code | Link → `Item` | colonne de liste; lecture seule |
| `product_bundle` | Product Bundle | Link → `Product Bundle` | lecture seule; — Product Bundle version this row was packed from |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `description` | Description | TextEditor | colonne de liste |
| `warehouse` | From Warehouse | Link → `Warehouse` |  |
| `target_warehouse` | To Warehouse (Optional) | Link → `Warehouse` |  |
| `qty` | Qty | Decimal | colonne de liste; lecture seule |
| `serial_no` | Serial No | LongText |  |
| `batch_no` | Batch No | Link → `Batch` |  |
| `actual_qty` | Actual Qty | Decimal | lecture seule |
| `projected_qty` | Projected Qty | Decimal | lecture seule |
| `uom` | UOM | Link → `UOM` | lecture seule |
| `page_break` | Page Break | Boolean | lecture seule |
| `prevdoc_doctype` | Prevdoc DocType | Text | lecture seule; masqué |
| `actual_batch_qty` | Actual Batch Quantity | Decimal | lecture seule |
| `incoming_rate` | Incoming Rate | Currency | lecture seule; devise de `parent_currency` |
| `conversion_factor` | Conversion Factor | Number |  |
| `rate` | Rate | Currency | colonne de liste; lecture seule; devise de `parent_currency` |
| `ordered_qty` | Ordered Qty | Decimal | lecture seule |
| `picked_qty` | Picked Qty | Decimal | lecture seule |
| `packed_qty` | Packed Qty | Decimal | lecture seule |
| `received_qty` | Received Qty | Decimal | lecture seule |
| `serial_and_batch_bundle` | Serial and Batch Bundle | Link → `Serial and Batch Bundle` |  |
| `use_serial_batch_fields` | Use Serial No / Batch Fields | Boolean | défaut `non` |
| `delivered_by_supplier` | Supplier delivers to Customer | Boolean | lecture seule |
| `requested_qty` | Requested Qty | Decimal | lecture seule |
| `reserve_stock` | Reserve Stock | Boolean | défaut `non` |

## Packing Slip

*Packing Slip* — `stock/packing_slip.yaml` · soumis

- **Numérotation** : série `PS-{YYYY}-{#####}`
- **Titre** : `delivery_note`
- **Icône** : `package`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `delivery_note` | Delivery Note | Link → `Delivery Note` | **requis**; colonne de liste; — Indicates that the package is a part of this delivery (Only Draft) |
| `naming_series` | Series | Select — MAT-PAC-.YYYY.- | **requis** |
| `from_case_no` | From Package No. | Int | **requis**; colonne de liste; — Identification of the package for the delivery (for print) |
| `to_case_no` | To Package No. | Int | colonne de liste; — If more than one package of the same type (for print) |
| `items` | Items | Table → `Packing Slip Item` |  |
| `net_weight_pkg` | Net Weight | Number | lecture seule; — The net weight of this package. (calculated automatically as sum of net weight of items) |
| `net_weight_uom` | Net Weight UOM | Link → `UOM` | lecture seule |
| `gross_weight_pkg` | Gross Weight | Number | — The gross weight of the package. Usually net weight + packaging material weight. (for print) |
| `gross_weight_uom` | Gross Weight UOM | Link → `UOM` |  |
| `letter_head` | Letter Head | Link → `Letter Head` |  |

## Packing Slip Item

*Packing Slip Item* — `stock/packing_slip_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Item Name | Text | colonne de liste; lecture seule; recopié de `item_code.item_name` |
| `batch_no` | Batch No | Link → `Batch` |  |
| `description` | Description | TextEditor |  |
| `qty` | Quantity | Decimal | **requis**; colonne de liste |
| `net_weight` | Net Weight | Number | colonne de liste |
| `stock_uom` | UOM | Link → `UOM` | lecture seule |
| `weight_uom` | Weight UOM | Link → `UOM` |  |
| `page_break` | Page Break | Boolean | colonne de liste; défaut `non` |
| `dn_detail` | Delivery Note Item | Text | colonne de liste; lecture seule; masqué |
| `pi_detail` | Delivery Note Packed Item | Text | lecture seule; masqué |

## Pick List

*Pick List* — `stock/pick_list.yaml` · soumis

- **Numérotation** : série `PL-{YYYY}-{#####}`
- **Titre** : `customer_name`
- **Icône** : `list-checks`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `parent_warehouse` | Warehouse | Link → `Warehouse` | — Items under this warehouse will be suggested |
| `customer` | Customer | Link → `Customer` | colonne de liste |
| `work_order` | Work Order | Link → `Work Order` |  |
| `locations` | Item Locations | Table → `Pick List Item` |  |
| `for_qty` | Qty of Finished Goods Item | Decimal | lecture seule; — Qty of raw materials will be decided based on the qty of the Finished Goods Item |
| `purpose` | Purpose | Select — Material Transfer for Manufacture · Material Transfer · Delivery | défaut `Material Transfer for Manufacture` |
| `material_request` | Material Request | Link → `Material Request` |  |
| `naming_series` | Series | Select — STO-PICK-.YYYY.- | **requis** |
| `group_same_items` | Group Same Items | Boolean | défaut `non` |
| `scan_barcode` | Scan Barcode | Text |  |
| `scan_mode` | Scan Mode | Boolean | défaut `non`; — If checked, picked qty won't automatically be fulfilled on submit of pick list. |
| `prompt_qty` | Prompt Qty | Boolean | défaut `non` |
| `customer_name` | Customer Name | Text | lecture seule; recopié de `customer.customer_name` |
| `status` | Status | Select — Draft · Open · Partly Delivered · Partially Transferred · Completed · Cancelled | **requis**; lecture seule; masqué; défaut `Draft` |
| `consider_rejected_warehouses` | Consider Rejected Warehouses | Boolean | défaut `non`; — Enable it if users want to consider rejected materials to dispatch. |
| `pick_manually` | Pick Manually | Boolean | défaut `non`; — If enabled then system won't override the picked qty / batches / serial numbers / warehouse. |
| `ignore_pricing_rule` | Ignore Pricing Rule | Boolean | défaut `non`; — If enabled then system won't apply the pricing rule on the delivery note which will be create from the pick li |
| `delivery_status` | Delivery Status | Select — Not Delivered · Fully Delivered · Partly Delivered | masqué |
| `per_delivered` | % Delivered | Percent | lecture seule; — % of materials delivered against this Pick List |

## Pick List Item

*Pick List Item* — `stock/pick_list_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `qty` | Qty | Decimal | **requis**; colonne de liste; défaut `1.000` |
| `picked_qty` | Picked Qty (in Stock UOM) | Decimal | colonne de liste |
| `warehouse` | Warehouse | Link → `Warehouse` | colonne de liste; lecture seule |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `description` | Description | LongText | lecture seule |
| `serial_no` | Serial No | LongText |  |
| `batch_no` | Batch No | Link → `Batch` |  |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `uom` | UOM | Link → `UOM` |  |
| `conversion_factor` | UOM Conversion Factor | Number | lecture seule |
| `stock_qty` | Qty (in Stock UOM) | Decimal | colonne de liste; lecture seule |
| `item_code` | Item | Link → `Item` | **requis**; colonne de liste |
| `sales_order` | Sales Order | Link → `Sales Order` | lecture seule |
| `sales_order_item` | Sales Order Item | Text | lecture seule; masqué |
| `material_request` | Material Request | Link → `Material Request` | lecture seule |
| `material_request_item` | Material Request Item | Text | lecture seule |
| `item_group` | Item Group | Text | lecture seule |
| `product_bundle_item` | Product Bundle Item | Text | lecture seule; masqué; — product bundle item row's name in sales order. Also indicates that picked item is to be used for a product bun |
| `serial_and_batch_bundle` | Serial and Batch Bundle | Link → `Serial and Batch Bundle` |  |
| `stock_reserved_qty` | Stock Reserved Qty (in Stock UOM) | Decimal | lecture seule |
| `use_serial_batch_fields` | Use Serial No / Batch Fields | Boolean | défaut `non` |
| `delivered_qty` | Delivered Qty (in Stock UOM) | Decimal | lecture seule |
| `transferred_qty` | Transferred Qty (in Stock UOM) | Decimal | lecture seule |
| `actual_qty` | Qty (Warehouse) | Decimal | lecture seule |
| `company_total_stock` | Qty (Company) | Number | lecture seule |

## Price List

*Price List* — `stock/price_list.yaml`

- **Titre** : `currency`
- **Icône** : `tags`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `enabled` | Enabled | Boolean | défaut `oui` |
| `price_list_name` | Price List Name | Text | **requis** |
| `currency` | Currency | Link → `Currency` | **requis**; colonne de liste |
| `buying` | Buying | Boolean | colonne de liste; défaut `non` |
| `selling` | Selling | Boolean | colonne de liste; défaut `non` |
| `price_not_uom_dependent` | Price Not UOM Dependent | Boolean | défaut `non` |
| `countries` | Applicable for Countries | Table → `Price List Country` |  |

## Price List Country

*Price List Country* — `stock/price_list_country.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `country` | Country | Link → `Country` | **requis**; colonne de liste |

## Purchase Receipt

*Purchase Receipt* — `stock/purchase_receipt.yaml` · soumis

- **Numérotation** : série `PURE-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `supplier_name`
- **Icône** : `package-check`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text |  |
| `naming_series` | Series | Select — MAT-PRE-.YYYY.- · MAT-PR-RET-.YYYY.- | **requis** |
| `supplier` | Supplier | Link → `Supplier` | **requis** |
| `supplier_name` | Supplier Name | Text | lecture seule; recopié de `supplier.supplier_name` |
| `supplier_delivery_note` | Supplier Delivery Note | Text |  |
| `posting_date` | Date | Date | **requis**; colonne de liste; défaut `today` |
| `posting_time` | Posting Time | Time | **requis** |
| `set_posting_time` | Edit Posting Date and Time | Boolean | défaut `non` |
| `company` | Company | Link → `Company` | **requis** |
| `is_return` | Is Return | Boolean | lecture seule |
| `return_against` | Return Against Purchase Receipt | Link → `Purchase Receipt` | lecture seule |
| `supplier_address` | Supplier Address | Link → `Address` |  |
| `contact_person` | Contact Person | Link → `Contact` |  |
| `address_display` | Address | TextEditor | lecture seule |
| `contact_display` | Contact | LongText | lecture seule |
| `contact_mobile` | Mobile No | LongText | lecture seule |
| `contact_email` | Contact Email | LongText | lecture seule |
| `shipping_address` | Shipping Address Template | Link → `Address` |  |
| `shipping_address_display` | Shipping Address | TextEditor | lecture seule |
| `currency` | Currency | Link → `Currency` | **requis** |
| `conversion_rate` | Exchange Rate | Number | **requis**; — Rate at which supplier's currency is converted to company's base currency |
| `use_transaction_date_exchange_rate` | Use Transaction Date Exchange Rate | Boolean | lecture seule |
| `buying_price_list` | Price List | Link → `Price List` |  |
| `price_list_currency` | Price List Currency | Link → `Currency` | lecture seule |
| `plc_conversion_rate` | Price List Exchange Rate | Number |  |
| `ignore_pricing_rule` | Ignore Pricing Rule | Boolean | défaut `non` |
| `set_warehouse` | Accepted Warehouse | Link → `Warehouse` |  |
| `rejected_warehouse` | Rejected Warehouse | Link → `Warehouse` |  |
| `is_subcontracted` | Is Subcontracted | Boolean | lecture seule |
| `supplier_warehouse` | Supplier Warehouse | Link → `Warehouse` |  |
| `items` | Items | Table → `Purchase Receipt Item` |  |
| `pricing_rules` | Pricing Rule Detail | Table → `Pricing Rule Detail` | lecture seule |
| `supplied_items` | Consumed Items | Table → `Purchase Receipt Item Supplied` |  |
| `total_qty` | Total Quantity | Decimal | lecture seule; calculé : `sum(items.qty)` |
| `base_total` | Total (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_net_total` | Net Total (Company Currency) | Currency | **requis**; lecture seule; devise de `company.default_currency` |
| `total` | Total | Currency | lecture seule; calculé : `sum(items.amount)`; devise de `currency` |
| `net_total` | Net Total | Currency | lecture seule; calculé : `sum(items.net_amount)`; devise de `currency` |
| `total_net_weight` | Total Net Weight | Number | lecture seule |
| `tax_category` | Tax Category | Link → `Tax Category` |  |
| `shipping_rule` | Shipping Rule | Link → `Shipping Rule` |  |
| `taxes_and_charges` | Purchase Taxes and Charges Template | Link → `Purchase Taxes and Charges Template` |  |
| `taxes` | Purchase Taxes and Charges | Table → `Purchase Taxes and Charges` |  |
| `other_charges_calculation` | Taxes and Charges Calculation | TextEditor | lecture seule |
| `base_taxes_and_charges_added` | Taxes and Charges Added (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_taxes_and_charges_deducted` | Taxes and Charges Deducted (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_total_taxes_and_charges` | Total Taxes and Charges (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `taxes_and_charges_added` | Taxes and Charges Added | Currency | lecture seule; devise de `currency` |
| `taxes_and_charges_deducted` | Taxes and Charges Deducted | Currency | lecture seule; devise de `currency` |
| `total_taxes_and_charges` | Total Taxes and Charges | Currency | lecture seule; devise de `currency` |
| `apply_discount_on` | Apply Additional Discount On | Select — Grand Total · Net Total | défaut `Grand Total` |
| `base_discount_amount` | Additional Discount Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `additional_discount_percentage` | Additional Discount Percentage | Number |  |
| `discount_amount` | Additional Discount Amount | Currency | devise de `currency` |
| `base_grand_total` | Grand Total | Currency | lecture seule; devise de `company.default_currency` |
| `base_rounding_adjustment` | Rounding Adjustment | Currency | lecture seule; devise de `company.default_currency` |
| `base_in_words` | In Words | Text | lecture seule |
| `base_rounded_total` | Rounded Total | Currency | lecture seule; devise de `company.default_currency` |
| `grand_total` | Grand Total | Currency | colonne de liste; lecture seule; calculé : `total + total_taxes_and_charges`; devise de `currency` |
| `rounding_adjustment` | Rounding Adjustment | Currency | lecture seule; devise de `currency` |
| `rounded_total` | Rounded Total | Currency | lecture seule; devise de `currency` |
| `in_words` | In Words | Text | lecture seule |
| `disable_rounded_total` | Disable Rounded Total | Boolean | défaut `non` |
| `tc_name` | Terms | Link → `Terms and Conditions` |  |
| `terms` | Terms and Conditions | TextEditor |  |
| `status` | Status | Select — Draft · Partly Billed · To Bill · Completed · Return · Return Issued · Cancelled · Closed | **requis**; lecture seule; défaut `Draft` |
| `range` | Range | Text | masqué |
| `project` | Project | Link → `Project` |  |
| `per_billed` | % Amount Billed | Percent | colonne de liste; lecture seule |
| `auto_repeat` | Auto Repeat | Link → `Auto Repeat` | lecture seule |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `select_print_heading` | Print Heading | Link → `Print Heading` |  |
| `language` | Print Language | Text | lecture seule |
| `group_same_items` | Group same items | Boolean | défaut `non` |
| `instructions` | Instructions | LongText |  |
| `remarks` | Remarks | LongText |  |
| `transporter_name` | Transporter Name | Text |  |
| `lr_no` | Vehicle Number | Text |  |
| `lr_date` | Vehicle Date | Date |  |
| `is_internal_supplier` | Is Internal Supplier | Boolean | lecture seule |
| `inter_company_reference` | Inter Company Reference | Link → `Delivery Note` | lecture seule |
| `scan_barcode` | Scan Barcode | Text |  |
| `billing_address` | Billing Address | Link → `Address` |  |
| `billing_address_display` | Billing Address | TextEditor | lecture seule |
| `apply_putaway_rule` | Apply Putaway Rule | Boolean | défaut `non` |
| `per_returned` | % Returned | Percent | colonne de liste; lecture seule |
| `set_from_warehouse` | Set From Warehouse | Link → `Warehouse` |  |
| `represents_company` | Represents Company | Link → `Company` | lecture seule |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `incoterm` | Incoterm | Link → `Incoterm` |  |
| `named_place` | Named Place | Text |  |
| `subcontracting_receipt` | Subcontracting Receipt | Link → `Subcontracting Receipt` | lecture seule |
| `dispatch_address` | Dispatch Address Template | Link → `Address` |  |
| `dispatch_address_display` | Dispatch Address | TextEditor | lecture seule |
| `last_scanned_warehouse` | Last Scanned Warehouse | Text |  |
| `item_wise_tax_details` | Item Wise Tax Details | Table → `Item Wise Tax Detail` | masqué |

## Purchase Receipt Item

*Purchase Receipt Item* — `stock/purchase_receipt_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `barcode` | Barcode | Text |  |
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `supplier_part_no` | Supplier Part Number | Text | lecture seule; masqué |
| `item_name` | Item Name | Text | recopié de `item_code.item_name` |
| `description` | Description | TextEditor |  |
| `received_qty` | Received Quantity | Decimal | **requis**; lecture seule |
| `qty` | Accepted Quantity | Decimal | colonne de liste |
| `rejected_qty` | Rejected Quantity | Decimal | colonne de liste |
| `uom` | UOM | Link → `UOM` | **requis** |
| `stock_uom` | Stock UOM | Link → `UOM` | **requis**; lecture seule |
| `conversion_factor` | Conversion Factor | Number | **requis** |
| `retain_sample` | Retain Sample | Boolean | lecture seule |
| `sample_quantity` | Sample Quantity | Int |  |
| `price_list_rate` | Price List Rate | Currency | devise de `parent_currency` |
| `discount_percentage` | Discount on Price List Rate (%) | Percent |  |
| `discount_amount` | Discount Amount | Currency | devise de `parent_currency` |
| `base_price_list_rate` | Price List Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `rate` | Rate | Currency | colonne de liste; devise de `parent_currency` |
| `amount` | Amount | Currency | colonne de liste; lecture seule; calculé : `qty * rate`; devise de `parent_currency` |
| `base_rate` | Rate (Company Currency) | Currency | **requis**; lecture seule; devise de `parent_company.default_currency` |
| `base_amount` | Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `pricing_rules` | Pricing Rules | LongText | lecture seule; masqué |
| `is_free_item` | Is Free Item | Boolean | lecture seule |
| `net_rate` | Net Rate | Currency | lecture seule; devise de `parent_currency` |
| `net_amount` | Net Amount | Currency | lecture seule; calculé : `amount - discount_amount`; devise de `parent_currency` |
| `base_net_rate` | Net Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_net_amount` | Net Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `weight_per_unit` | Weight Per Unit | Number |  |
| `total_weight` | Total Weight | Number | lecture seule |
| `weight_uom` | Weight UOM | Link → `UOM` |  |
| `warehouse` | Accepted Warehouse | Link → `Warehouse` | colonne de liste |
| `rejected_warehouse` | Rejected Warehouse | Link → `Warehouse` |  |
| `quality_inspection` | Quality Inspection | Link → `Quality Inspection` |  |
| `is_fixed_asset` | Is Fixed Asset | Boolean | lecture seule; masqué |
| `purchase_order` | Purchase Order | Link → `Purchase Order` | lecture seule; cible submitted |
| `schedule_date` | Required By | Date | lecture seule |
| `stock_qty` | Accepted Qty in Stock UOM | Decimal | lecture seule |
| `item_tax_template` | Item Tax Template | Link → `Item Tax Template` |  |
| `project` | Project | Link → `Project` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `purchase_order_item` | Purchase Order Item | Text | lecture seule; masqué |
| `allow_zero_valuation_rate` | Allow Zero Valuation Rate | Boolean | défaut `non` |
| `billed_amt` | Billed Amt | Currency | lecture seule; devise de `parent_currency` |
| `closed` | Closed | Boolean | lecture seule |
| `landed_cost_voucher_amount` | Landed Cost Voucher Amount | Currency | lecture seule; devise de `parent_currency` |
| `brand` | Brand | Link → `Brand` | lecture seule; masqué |
| `item_group` | Item Group | Link → `Item Group` | lecture seule |
| `rm_supp_cost` | Raw Materials Supplied Cost | Currency | lecture seule; masqué; devise de `parent_currency` |
| `item_tax_amount` | Item Tax Amount Included in Value | Currency | lecture seule; masqué; devise de `parent_currency` |
| `valuation_rate` | Valuation Rate | Currency | lecture seule; masqué; devise de `parent_currency` |
| `item_tax_rate` | Item Tax Rate | Code | lecture seule; masqué; — Tax detail table fetched from item master as a string and stored in this field. Used for Taxes and Charges |
| `page_break` | Page Break | Boolean | défaut `non` |
| `material_request` | Material Request | Link → `Material Request` | lecture seule |
| `material_request_item` | Material Request Item | Text | lecture seule; masqué |
| `expense_account` | Expense Account | Link → `Account` |  |
| `manufacturer` | Manufacturer | Link → `Manufacturer` |  |
| `manufacturer_part_no` | Manufacturer Part Number | Text |  |
| `asset_location` | Asset Location | Link → `Location` |  |
| `asset_category` | Asset Category | Link → `Asset Category` | lecture seule |
| `from_warehouse` | From Warehouse | Link → `Warehouse` | masqué |
| `purchase_receipt_item` | Purchase Receipt Item | Text | lecture seule; masqué |
| `putaway_rule` | Putaway Rule | Link → `Putaway Rule` | lecture seule |
| `returned_qty` | Returned Qty in Stock UOM | Decimal | lecture seule |
| `received_stock_qty` | Received Qty in Stock UOM | Decimal | lecture seule |
| `stock_uom_rate` | Rate of Stock UOM | Currency | lecture seule; devise de `parent_currency` |
| `delivery_note_item` | Delivery Note Item | Text | lecture seule |
| `delivery_note_packed_item` | Delivery Note Packed Item | Text | lecture seule |
| `margin_type` | Margin Type | Select — Percentage · Amount |  |
| `margin_rate_or_amount` | Margin Rate or Amount | Number |  |
| `rate_with_margin` | Rate With Margin | Currency | lecture seule; devise de `parent_currency` |
| `base_rate_with_margin` | Rate With Margin (Company Currency) | Currency | devise de `parent_company.default_currency` |
| `purchase_invoice` | Purchase Invoice | Link → `Purchase Invoice` | lecture seule |
| `purchase_invoice_item` | Purchase Invoice Item | Text | lecture seule; masqué |
| `product_bundle` | Product Bundle | Link → `Product Bundle` | lecture seule; masqué; — Product Bundle version this row was packed from |
| `provisional_expense_account` | Provisional Expense Account | Link → `Account` |  |
| `has_item_scanned` | Has Item Scanned | Boolean | lecture seule |
| `serial_and_batch_bundle` | Serial and Batch Bundle | Link → `Serial and Batch Bundle` |  |
| `serial_no` | Serial No | LongText |  |
| `rejected_serial_no` | Rejected Serial No | LongText |  |
| `batch_no` | Batch No | Link → `Batch` |  |
| `rejected_serial_and_batch_bundle` | Rejected Serial and Batch Bundle | Link → `Serial and Batch Bundle` |  |
| `wip_composite_asset` | WIP Composite Asset | Link → `Asset` |  |
| `sales_order` | Sales Order | Link → `Sales Order` | lecture seule |
| `sales_order_item` | Sales Order Item | Text | lecture seule; masqué |
| `subcontracting_receipt_item` | Subcontracting Receipt Item | Text | lecture seule; masqué |
| `use_serial_batch_fields` | Use Serial No / Batch Fields | Boolean | défaut `non` |
| `return_qty_from_rejected_warehouse` | Return Qty from Rejected Warehouse | Boolean | lecture seule |
| `sales_incoming_rate` | Sales Incoming Rate | Currency | masqué; devise de `parent_currency`; — Valuation rate for the item as per Sales Invoice (Only for Internal Transfers) |
| `distributed_discount_amount` | Distributed Discount Amount | Currency | devise de `parent_currency` |
| `mapped_additional_discount_amount` | Additional Discount per Stock Unit | Currency | lecture seule; devise de `parent_currency`; — Tax-exclusive additional discount carried from a source document, per stock unit. |
| `amount_difference_with_purchase_invoice` | Amount Difference with Purchase Invoice | Currency | lecture seule; devise de `parent_currency` |

## Putaway Rule

*Putaway Rule* — `stock/putaway_rule.yaml`

- **Titre** : `item_code`
- **Icône** : `archive`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item | Link → `Item` | **requis** |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `warehouse` | Warehouse | Link → `Warehouse` | **requis**; colonne de liste |
| `capacity` | Capacity | Number | **requis**; colonne de liste; défaut `0.0` |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `priority` | Priority | Int | colonne de liste; défaut `1` |
| `company` | Company | Link → `Company` | **requis** |
| `disable` | Disable | Boolean | défaut `non` |
| `uom` | UOM | Link → `UOM` |  |
| `stock_capacity` | Capacity in Stock UOM | Number | lecture seule |
| `conversion_factor` | Conversion Factor | Number | lecture seule |

## Quality Inspection

*Quality Inspection* — `stock/quality_inspection.yaml` · soumis

- **Numérotation** : série `QI-{YYYY}-{#####}`
- **Vues** : kanban
- **Titre** : `item_code`
- **Icône** : `clipboard-check`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — MAT-QA-.YYYY.- | **requis** |
| `report_date` | Report Date | Date | **requis**; colonne de liste; défaut `today` |
| `inspection_type` | Inspection Type | Select — Incoming · Outgoing · In Process | **requis**; colonne de liste |
| `reference_type` | Reference Type | Text | **requis** |
| `reference_name` | Reference Name | DynamicLink → `reference_type` | **requis**; colonne de liste |
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_serial_no` | Item Serial No | Link → `Serial No` |  |
| `batch_no` | Batch No | Link → `Batch` |  |
| `sample_size` | Sample Size | Number | **requis**; défaut `1.0` |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `description` | Description | LongText |  |
| `inspected_by` | Inspected By | Text | **requis** |
| `verified_by` | Verified By | Text |  |
| `bom_no` | BOM No | Link → `BOM` | lecture seule |
| `remarks` | Remarks | LongText |  |
| `quality_inspection_template` | Quality Inspection Template | Link → `Quality Inspection Template` |  |
| `readings` | Readings | Table → `Quality Inspection Reading` |  |
| `status` | Status | Select — Accepted · Rejected · Cancelled | **requis**; défaut `Accepted` |
| `manual_inspection` | Manual Inspection | Boolean | défaut `non` |
| `child_row_reference` | Child Row Reference | Text | lecture seule; masqué |
| `company` | Company | Link → `Company` |  |
| `letter_head` | Letter Head | Link → `Letter Head` |  |

## Quality Inspection Parameter

*Quality Inspection Parameter* — `stock/quality_inspection_parameter.yaml`

- **Titre** : `parameter`
- **Icône** : `clipboard-list`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `parameter` | Parameter | Text | **requis**; colonne de liste |
| `description` | Description | TextEditor |  |
| `parameter_group` | Parameter Group | Link → `Quality Inspection Parameter Group` | colonne de liste |

## Quality Inspection Parameter Group

*Quality Inspection Parameter Group* — `stock/quality_inspection_parameter_group.yaml`

- **Titre** : `group_name`
- **Icône** : `clipboard-list`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `group_name` | Parameter Group Name | Text | **requis**; colonne de liste |

## Quality Inspection Reading

*Quality Inspection Reading* — `stock/quality_inspection_reading.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `specification` | Parameter | Link → `Quality Inspection Parameter` | **requis**; colonne de liste |
| `value` | Acceptance Criteria Value | Text |  |
| `reading_1` | Reading 1 | Text | colonne de liste |
| `reading_2` | Reading 2 | Text |  |
| `reading_3` | Reading 3 | Text |  |
| `reading_4` | Reading 4 | Text |  |
| `reading_5` | Reading 5 | Text |  |
| `reading_6` | Reading 6 | Text |  |
| `reading_7` | Reading 7 | Text |  |
| `reading_8` | Reading 8 | Text |  |
| `reading_9` | Reading 9 | Text |  |
| `reading_10` | Reading 10 | Text |  |
| `status` | Status | Select — Accepted · Rejected | colonne de liste; défaut `Accepted` |
| `acceptance_formula` | Acceptance Criteria Formula | Code | — Simple Python formula applied on Reading fields.<br> Numeric eg. 1: <b>reading_1 &gt; 0.2 and reading_1 &lt; 0 |
| `formula_based_criteria` | Formula Based Criteria | Boolean | défaut `non` |
| `min_value` | Minimum Value | Number | — Applied on each reading. |
| `max_value` | Maximum Value | Number | — Applied on each reading. |
| `reading_value` | Reading Value | Text | colonne de liste |
| `manual_inspection` | Manual Inspection | Boolean | défaut `non`; — Set the status manually. |
| `numeric` | Numeric | Boolean | colonne de liste; défaut `oui` |
| `parameter_group` | Parameter Group | Link → `Quality Inspection Parameter Group` | lecture seule |

## Quality Inspection Template

*Quality Inspection Template* — `stock/quality_inspection_template.yaml`

- **Titre** : `quality_inspection_template_name`
- **Icône** : `clipboard-list`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `quality_inspection_template_name` | Quality Inspection Template Name | Text | **requis**; colonne de liste |
| `item_quality_inspection_parameter` | Item Quality Inspection Parameter | Table → `Item Quality Inspection Parameter` |  |

## Quick Stock Balance

*Quick Stock Balance* — `stock/quick_stock_balance.yaml`

- **Vues** : calendar
- **Titre** : `item_name`
- **Icône** : `scale`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `warehouse` | Warehouse | Link → `Warehouse` | **requis**; colonne de liste |
| `item` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_barcode` | Item Barcode | Text |  |
| `item_name` | Item Name | Text | lecture seule; recopié de `item.item_name` |
| `item_description` | Item Description | LongText | lecture seule |
| `qty` | Available Quantity | Decimal | lecture seule |
| `value` | Stock Value | Currency | lecture seule |
| `image` | Image View | Image |  |
| `date` | Date | Date | **requis**; colonne de liste; défaut `today` |

## Repost Item Valuation

*Repost Item Valuation* — `stock/repost_item_valuation.yaml` · soumis

- **Numérotation** : série `RIV-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `item_code`
- **Icône** : `refresh-cw`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` |  |
| `warehouse` | Warehouse | Link → `Warehouse` |  |
| `posting_date` | Posting Date | Date | **requis** |
| `posting_time` | Posting Time | Time |  |
| `status` | Status | Select — Queued · In Progress · Completed · Skipped · Failed · Cancelled | colonne de liste; lecture seule; défaut `Queued` |
| `error_log` | Error Log | LongText | lecture seule |
| `company` | Company | Link → `Company` |  |
| `voucher_type` | Voucher Type | Text | colonne de liste |
| `voucher_no` | Voucher No | DynamicLink → `voucher_type` | colonne de liste |
| `based_on` | Based On | Select — Transaction · Item and Warehouse | **requis**; défaut `Transaction` |
| `allow_negative_stock` | Allow Negative Stock | Boolean | défaut `oui` |
| `via_landed_cost_voucher` | Via Landed Cost Voucher | Boolean | défaut `non` |
| `allow_zero_rate` | Allow Zero Rate | Boolean | défaut `non` |
| `items_to_be_repost` | Items to Be Repost | Code | lecture seule; masqué |
| `current_index` | Current Index | Int | lecture seule; masqué |
| `gl_reposting_index` | GL reposting index | Int | lecture seule; masqué |
| `total_reposting_count` | No of Items to Repost | Int | lecture seule |
| `recreate_stock_ledgers` | Recreate Stock Ledgers | Boolean | défaut `non` |
| `reposting_reference` | Reposting Reference | Text | lecture seule |
| `repost_only_accounting_ledgers` | Repost Only Accounting Ledgers | Boolean | défaut `non`; — Stock Ledgers won’t be reposted. |
| `total_vouchers` | Total Ledgers | Int | lecture seule |
| `vouchers_posted` | Ledgers Posted | Int | lecture seule |
| `reposting_data_file` | Reposting Data File | Attach | lecture seule |
| `recalculate_valuation_rate` | Recalculate Valuation Rate | Boolean | défaut `non`; — Only works for Purchase Receipt, Purchase Invoice with Update Stock and Stock Entry with no row that has both  |

## Serial and Batch Bundle

*Serial and Batch Bundle* — `stock/serial_and_batch_bundle.yaml` · soumis

- **Numérotation** : série `SBB-{YYYY}-{#####}`
- **Titre** : `item_code`
- **Icône** : `layers`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `item_group` | Item Group | Link → `Item Group` | masqué |
| `has_serial_no` | Has Serial No | Boolean | lecture seule |
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `has_batch_no` | Has Batch No | Boolean | lecture seule |
| `voucher_type` | Voucher Type | Text | **requis**; colonne de liste |
| `voucher_no` | Voucher No | DynamicLink → `voucher_type` |  |
| `is_cancelled` | Is Cancelled | Boolean | lecture seule |
| `avg_rate` | Avg Rate | Number | lecture seule |
| `total_amount` | Total Amount | Number | lecture seule |
| `total_qty` | Total Qty | Decimal | lecture seule |
| `warehouse` | Warehouse | Link → `Warehouse` | colonne de liste |
| `type_of_transaction` | Type of Transaction | Select — Inward · Outward · Maintenance · Asset Repair | **requis** |
| `is_rejected` | Is Rejected | Boolean | lecture seule |
| `voucher_detail_no` | Voucher Detail No | Text | lecture seule |
| `entries` | Entries | Table → `Serial and Batch Entry` |  |
| `returned_against` | Returned Against | Text | lecture seule |
| `naming_series` | Naming Series | Select — SABB-.######## | défaut `SABB-.########` |
| `is_packed` | Is Packed | Boolean | défaut `non` |
| `posting_datetime` | Posting Datetime | Datetime |  |

## Serial and Batch Entry

*Serial and Batch Entry* — `stock/serial_and_batch_entry.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `serial_no` | Serial No | Link → `Serial No` | colonne de liste |
| `batch_no` | Batch No | Link → `Batch` | colonne de liste |
| `qty` | Qty | Decimal | colonne de liste; défaut `1.000` |
| `warehouse` | Warehouse | Link → `Warehouse` | colonne de liste |
| `incoming_rate` | Valuation Rate | Number | lecture seule |
| `outgoing_rate` | Outgoing Rate | Number | lecture seule; masqué |
| `stock_value_difference` | Change in Stock Value | Number | lecture seule |
| `is_outward` | Is Outward | Boolean | lecture seule; masqué |
| `stock_queue` | FIFO Stock Queue (qty, rate) | LongText | lecture seule |
| `delivered_qty` | Delivered Qty | Decimal | lecture seule |
| `reference_for_reservation` | Reference for Reservation | Text | lecture seule; masqué |
| `posting_datetime` | Posting Datetime | Datetime | lecture seule |
| `voucher_type` | Voucher Type | Text | lecture seule |
| `voucher_no` | Voucher No | Text | lecture seule |
| `voucher_detail_no` | Voucher Detail No | Text | lecture seule |
| `type_of_transaction` | Type of Transaction | Text | lecture seule |
| `is_cancelled` | Is Cancelled | Boolean | lecture seule |
| `item_code` | Item Code | Link → `Item` | lecture seule |
| `fg_serial_no` | Finished Good Serial No | Link → `Serial No` | lecture seule; — Finished good serial no this raw material was consumed into (Manufacture / Repack) |
| `fg_batch_no` | Finished Good Batch No | Link → `Batch` | lecture seule; — Finished good batch this raw material was consumed into (Manufacture / Repack) |

## Serial No

*Serial No* — `stock/serial_no.yaml`

- **Vues** : calendar
- **Titre** : `item_code`
- **Icône** : `hash`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `serial_no` | Serial No | Text | **requis**; colonne de liste |
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `description` | Description | LongText | lecture seule |
| `item_group` | Item Group | Link → `Item Group` | lecture seule |
| `brand` | Brand | Link → `Brand` | lecture seule |
| `asset` | Asset | Link → `Asset` | lecture seule |
| `asset_status` | Asset Status | Select — Issue · Receipt · Transfer | lecture seule |
| `location` | Location | Link → `Location` | lecture seule |
| `employee` | Employee | Link → `Employee` | lecture seule |
| `maintenance_status` | Maintenance Status | Select — Under Warranty · Out of Warranty · Under AMC · Out of AMC | lecture seule |
| `warranty_period` | Warranty Period (Days) | Int | lecture seule |
| `warranty_expiry_date` | Warranty Expiry Date | Date |  |
| `amc_expiry_date` | AMC Expiry Date | Date |  |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `work_order` | Work Order | Link → `Work Order` |  |
| `warehouse` | Warehouse | Link → `Warehouse` | colonne de liste; lecture seule |
| `batch_no` | Batch No | Link → `Batch` | lecture seule |
| `purchase_rate` | Incoming Rate | Number | lecture seule |
| `status` | Status | Select — Active · Inactive · Consumed · Delivered · Expired | colonne de liste; lecture seule |
| `customer` | Customer | Link → `Customer` | lecture seule |
| `reference_doctype` | Source Document Type | Text | lecture seule |
| `reference_name` | Source Document Name | DynamicLink → `reference_doctype` | lecture seule |
| `posting_date` | Posting Date | Date | lecture seule |

## Shipment

*Shipment* — `stock/shipment.yaml` · soumis

- **Numérotation** : série `SHIP-{YYYY}-{#####}`
- **Titre** : `status`
- **Icône** : `truck`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `pickup_from_type` | Pickup from | Select — Company · Customer · Supplier | défaut `Company` |
| `pickup_company` | Company | Link → `Company` |  |
| `pickup_customer` | Customer | Link → `Customer` |  |
| `pickup_supplier` | Supplier | Link → `Supplier` |  |
| `pickup` | Pickup From | Text | colonne de liste; lecture seule; masqué |
| `pickup_address_name` | Address | Link → `Address` | **requis** |
| `pickup_address` | Pickup Address | TextEditor | lecture seule |
| `pickup_contact_name` | Contact | Link → `Contact` |  |
| `pickup_contact_email` | Contact Email | Text | lecture seule; masqué |
| `pickup_contact` | Pickup Contact | TextEditor | lecture seule |
| `delivery_to_type` | Delivery to | Select — Company · Customer · Supplier | défaut `Customer` |
| `delivery_company` | Company | Link → `Company` |  |
| `delivery_customer` | Customer | Link → `Customer` |  |
| `delivery_supplier` | Supplier | Link → `Supplier` |  |
| `delivery_to` | Delivery To | Text | colonne de liste; lecture seule; masqué |
| `delivery_address_name` | Address | Link → `Address` | **requis** |
| `delivery_address` | Delivery Address | TextEditor | lecture seule |
| `delivery_contact_name` | Contact | Link → `Contact` |  |
| `delivery_contact_email` | Contact Email | Text | lecture seule; masqué |
| `delivery_contact` | Delivery Contact | TextEditor | lecture seule |
| `shipment_parcel` | Shipment Parcel | Table → `Shipment Parcel` |  |
| `parcel_template` | Parcel Template | Link → `Shipment Parcel Template` |  |
| `pallets` | Pallets | Select — No · Yes | défaut `No` |
| `value_of_goods` | Value of Goods | Currency | **requis** |
| `pickup_date` | Pickup Date | Date | **requis**; colonne de liste |
| `pickup_from` | Pickup from | Time | **requis** |
| `pickup_to` | Pickup to | Time | **requis** |
| `shipment_type` | Shipment Type | Select — Goods · Documents | défaut `Goods` |
| `pickup_type` | Pickup Type | Select — Pickup · Self delivery | défaut `Pickup` |
| `description_of_content` | Description of Content | LongText | **requis** |
| `service_provider` | Service Provider | Text |  |
| `shipment_id` | Shipment ID | Text |  |
| `shipment_amount` | Shipment Amount | Currency |  |
| `status` | Status | Select — Draft · Submitted · Booked · Cancelled · Completed | lecture seule |
| `tracking_url` | Tracking URL | LongText | lecture seule; masqué |
| `carrier` | Carrier | Text |  |
| `carrier_service` | Carrier Service | Text |  |
| `awb_number` | AWB Number | Text |  |
| `tracking_status` | Tracking Status | Select — In Progress · Delivered · Returned · Lost |  |
| `tracking_status_info` | Tracking Status Info | Text | lecture seule |
| `incoterm` | Incoterm | Link → `Incoterm` |  |
| `shipment_delivery_note` | Shipment Delivery Note | Table → `Shipment Delivery Note` |  |
| `pickup_contact_person` | Pickup Contact Person | Text |  |
| `total_weight` | Total Weight (kg) | Number | lecture seule |

## Shipment Delivery Note

*Shipment Delivery Note* — `stock/shipment_delivery_note.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `delivery_note` | Delivery Note | Link → `Delivery Note` | **requis**; colonne de liste |
| `grand_total` | Value | Currency | colonne de liste; lecture seule |

## Shipment Parcel

*Shipment Parcel* — `stock/shipment_parcel.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `length` | Length (cm) | Number | colonne de liste |
| `width` | Width (cm) | Number | colonne de liste |
| `height` | Height (cm) | Number | colonne de liste |
| `weight` | Weight (kg) | Number | **requis**; colonne de liste |
| `count` | Count | Int | **requis**; colonne de liste; défaut `1` |

## Shipment Parcel Template

*Shipment Parcel Template* — `stock/shipment_parcel_template.yaml`

- **Titre** : `parcel_template_name`
- **Icône** : `package`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `length` | Length (cm) | Number | **requis**; colonne de liste |
| `width` | Width (cm) | Number | **requis**; colonne de liste |
| `height` | Height (cm) | Number | **requis**; colonne de liste |
| `weight` | Weight (kg) | Number | **requis**; colonne de liste |
| `parcel_template_name` | Parcel Template Name | Text | **requis**; colonne de liste |

## Stock Closing Balance

*Stock Closing Balance* — `stock/stock_closing_balance.yaml`

- **Vues** : calendar
- **Titre** : `item_code`
- **Icône** : `lock`
- **Permissions explicites** — `write` : 0, `create` : 0, `delete` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | colonne de liste; lecture seule |
| `warehouse` | Warehouse | Link → `Warehouse` | colonne de liste; lecture seule |
| `posting_date` | Posting Date | Date | colonne de liste; lecture seule |
| `posting_time` | Posting Time | Time | lecture seule |
| `posting_datetime` | Posting Datetime | Datetime | lecture seule |
| `actual_qty` | Qty Change | Decimal | colonne de liste; lecture seule |
| `valuation_rate` | Valuation Rate | Currency | lecture seule; devise de `company.default_currency` |
| `stock_value` | Balance Stock Value | Currency | lecture seule; devise de `company.default_currency` |
| `company` | Company | Link → `Company` | lecture seule |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `stock_value_difference` | Change in Stock Value | Currency | lecture seule; devise de `company.default_currency` |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `item_group` | Item Group | Link → `Item Group` | lecture seule |
| `stock_closing_entry` | Stock Closing Entry | Link → `Stock Closing Entry` | lecture seule |
| `inventory_dimension_key` | Inventory Dimension key | LongText | lecture seule |
| `batch_no` | Batch No | Link → `Batch` | lecture seule |
| `fifo_queue` | FIFO Queue | LongText | lecture seule |

## Stock Closing Entry

*Stock Closing Entry* — `stock/stock_closing_entry.yaml` · soumis

- **Numérotation** : série `SCE-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `status`
- **Icône** : `lock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Naming Series | Select — CBAL-.##### |  |
| `company` | Company | Link → `Company` | **requis** |
| `status` | Status | Select — Draft · Queued · In Progress · Completed · Outdated · Failed · Cancelled | colonne de liste; lecture seule; défaut `Draft` |
| `from_date` | From Date | Date | lecture seule; — Set automatically to the day after the previous Stock Closing Entry, or to the first stock transaction's date |
| `to_date` | To Date | Date | **requis** |

## Stock Entry

*Stock Entry* — `stock/stock_entry.yaml` · soumis

- **Numérotation** : série `SE-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `supplier_name`
- **Icône** : `arrow-left-right`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — MAT-STE-.YYYY.- | **requis** |
| `stock_entry_type` | Stock Entry Type | Link → `Stock Entry Type` | **requis**; colonne de liste |
| `weight_per_piece` | Weight Per Piece | Number | masqué; — Splits the produced quantity into one batch per this many units |
| `outgoing_stock_entry` | Stock Entry (Outward GIT) | Link → `Stock Entry` | lecture seule |
| `source_stock_entry` | Source Stock Entry (Manufacture) | Link → `Stock Entry` |  |
| `purpose` | Purpose | Select — Material Issue · Material Receipt · Material Transfer · Material Transfer for Manufacture · Material Consumption for Manufacture · Manufacture · Repack · Send to Subcontractor · Disassemble · Receive from Customer · Return Raw Material to Customer · Subcontracting Delivery · Subcontracting Return | colonne de liste; lecture seule; masqué |
| `company` | Company | Link → `Company` | **requis** |
| `work_order` | Work Order | Link → `Work Order` | visible si `purpose in ['Material Transfer for Manufacture', 'Manufacture', 'Material Consumption for Manufacture']` |
| `is_fg_conversion` | Is Finished Good Conversion | Boolean | lecture seule; masqué |
| `purchase_order` | Purchase Order | Link → `Purchase Order` |  |
| `subcontracting_order` | Subcontracting Order | Link → `Subcontracting Order` | lecture seule |
| `delivery_note_no` | Delivery Note No | Link → `Delivery Note` | lecture seule |
| `sales_invoice_no` | Sales Invoice No | Link → `Sales Invoice` | lecture seule |
| `purchase_receipt_no` | Purchase Receipt No | Link → `Purchase Receipt` | lecture seule |
| `posting_date` | Posting Date | Date | défaut `today` |
| `posting_time` | Posting Time | Time |  |
| `set_posting_time` | Edit Posting Date and Time | Boolean | défaut `non` |
| `inspection_required` | Inspection Required | Boolean | défaut `non` |
| `from_bom` | From BOM | Boolean | défaut `non` |
| `bom_no` | BOM No | Link → `BOM` | visible si `from_bom`; obligatoire si `from_bom` |
| `fg_completed_qty` | Finished Good Quantity  | Decimal | visible si `from_bom`; — As per Stock UOM |
| `use_multi_level_bom` | Use Multi-Level BOM | Boolean | défaut `oui`; visible si `from_bom`; — Including items for sub assemblies |
| `from_warehouse` | Default Source Warehouse | Link → `Warehouse` | colonne de liste; — Sets 'Source Warehouse' in each row of the items table. |
| `source_warehouse_address` | Source Warehouse Address Link | Link → `Address` |  |
| `source_address_display` | Source Warehouse Address | TextEditor | lecture seule |
| `to_warehouse` | Default Target Warehouse | Link → `Warehouse` | colonne de liste; — Sets 'Target Warehouse' in each row of the items table. |
| `target_warehouse_address` | Target Warehouse Address Link | Link → `Address` |  |
| `target_address_display` | Target Warehouse Address | TextEditor | lecture seule |
| `scan_barcode` | Scan Barcode | Text |  |
| `items` | Items | Table → `Stock Entry Detail` |  |
| `total_incoming_value` | Total Incoming Value (Receipt) | Currency | lecture seule; devise de `company.default_currency` |
| `total_outgoing_value` | Total Outgoing Value (Consumption) | Currency | lecture seule; devise de `company.default_currency` |
| `value_difference` | Total Value Difference (Incoming - Outgoing) | Currency | lecture seule; devise de `company.default_currency` |
| `additional_costs` | Additional Costs | Table → `Landed Cost Taxes and Charges` |  |
| `total_additional_costs` | Total Additional Costs | Currency | lecture seule; devise de `company.default_currency` |
| `supplier` | Supplier | Link → `Supplier` |  |
| `supplier_name` | Supplier Name | Text | lecture seule; recopié de `supplier.supplier_name` |
| `supplier_address` | Supplier Address | Link → `Address` |  |
| `address_display` | Address | TextEditor |  |
| `select_print_heading` | Print Heading | Link → `Print Heading` |  |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `is_opening` | Is Opening | Select — No · Yes |  |
| `project` | Project | Link → `Project` |  |
| `remarks` | Remarks | LongText |  |
| `per_transferred` | Per Transferred | Percent | colonne de liste; lecture seule |
| `total_amount` | Total Amount | Currency | lecture seule; devise de `company.default_currency` |
| `job_card` | Job Card | Link → `Job Card` | lecture seule |
| `credit_note` | Credit Note | Link → `Journal Entry` | masqué |
| `pick_list` | Pick List | Link → `Pick List` | lecture seule |
| `add_to_transit` | Add to Transit | Boolean | défaut `non` |
| `apply_putaway_rule` | Apply Putaway Rule | Boolean | défaut `non` |
| `is_return` | Is Return | Boolean | colonne de liste; lecture seule; masqué |
| `process_loss_qty` | Process Loss Qty | Decimal | lecture seule |
| `process_loss_percentage` | % Process Loss | Percent | lecture seule |
| `asset_repair` | Asset Repair | Link → `Asset Repair` | lecture seule |
| `last_scanned_warehouse` | Last Scanned Warehouse | Text |  |
| `is_additional_transfer_entry` | Is Additional Transfer Entry | Boolean | lecture seule; masqué |
| `subcontracting_inward_order` | Subcontracting Inward Order | Link → `Subcontracting Inward Order` | lecture seule |
| `cost_center` | Cost Center | Link → `Cost Center` |  |

## Stock Entry Detail

*Stock Entry Detail* — `stock/stock_entry_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `barcode` | Barcode | Text |  |
| `s_warehouse` | Source Warehouse | Link → `Warehouse` | colonne de liste |
| `t_warehouse` | Target Warehouse | Link → `Warehouse` | colonne de liste |
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `description` | Description | TextEditor |  |
| `qty` | Qty | Decimal | **requis**; colonne de liste |
| `basic_rate` | Basic Rate (as per Stock UOM) | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `basic_amount` | Basic Amount | Currency | lecture seule; devise de `parent_company.default_currency` |
| `additional_cost` | Additional Cost | Currency | lecture seule; devise de `parent_company.default_currency` |
| `amount` | Amount | Currency | lecture seule; devise de `parent_company.default_currency` |
| `valuation_rate` | Valuation Rate | Currency | lecture seule; devise de `parent_company.default_currency` |
| `uom` | UOM | Link → `UOM` | **requis** |
| `conversion_factor` | Conversion Factor | Number | **requis** |
| `stock_uom` | Stock UOM | Link → `UOM` | **requis**; lecture seule |
| `transfer_qty` | Qty as per Stock UOM | Decimal | lecture seule |
| `retain_sample` | Retain Sample | Boolean | lecture seule |
| `sample_quantity` | Sample Quantity | Int |  |
| `serial_no` | Serial No | LongText |  |
| `batch_no` | Batch No | Link → `Batch` |  |
| `quality_inspection` | Quality Inspection | Link → `Quality Inspection` |  |
| `expense_account` | Difference Account | Link → `Account` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `allow_zero_valuation_rate` | Allow Zero Valuation Rate | Boolean | défaut `non` |
| `actual_qty` | Actual Qty (at source/target) | Decimal | lecture seule |
| `bom_no` | BOM No | Link → `BOM` | masqué; — BOM No. for a Finished Good Item |
| `allow_alternative_item` | Allow Alternative Item | Boolean | lecture seule |
| `material_request` | Material Request | Link → `Material Request` | lecture seule; masqué; cible submitted; — Material Request used to make this Stock Entry |
| `material_request_item` | Material Request Item | Text | lecture seule; masqué; — Référence de la ligne d'origine (Material Request Item). |
| `pick_list_item` | Pick List Item | Text | lecture seule; masqué; — Référence de la ligne d'origine (Pick List Item). |
| `original_item` | Original Item | Link → `Item` | lecture seule; masqué |
| `subcontracted_item` | Subcontracted Item | Link → `Item` |  |
| `against_stock_entry` | Against Stock Entry | Link → `Stock Entry` | lecture seule |
| `ste_detail` | Stock Entry Child | Text | lecture seule |
| `transferred_qty` | Transferred Qty | Decimal | lecture seule |
| `item_group` | Item Group | Text |  |
| `reference_purchase_receipt` | Reference Purchase Receipt | Link → `Purchase Receipt` | lecture seule |
| `project` | Project | Link → `Project` |  |
| `po_detail` | PO Supplied Item | Text | lecture seule; masqué |
| `sco_rm_detail` | SCO Supplied Item | Text | lecture seule; masqué |
| `set_basic_rate_manually` | Set Basic Rate Manually | Boolean | défaut `non` |
| `putaway_rule` | Putaway Rule | Link → `Putaway Rule` | lecture seule |
| `is_finished_item` | Is Finished Item | Boolean | défaut `non` |
| `job_card_item` | Job Card Item | Text | lecture seule; masqué |
| `has_item_scanned` | Has Item Scanned | Boolean | lecture seule |
| `serial_and_batch_bundle` | Serial and Batch Bundle | Link → `Serial and Batch Bundle` |  |
| `use_serial_batch_fields` | Use Serial No / Batch Fields | Boolean | défaut `non` |
| `landed_cost_voucher_amount` | Landed Cost Voucher Amount | Currency | lecture seule; devise de `parent_company.default_currency` |
| `customer_provided_item_cost` | Customer Provided Item Cost | Currency | lecture seule; devise de `parent_company.default_currency` |
| `scio_detail` | SCIO Detail | Text | lecture seule; masqué |
| `against_fg` | Against Finished Good | Text | — Référence de la ligne d'origine (Subcontracting Inward Order Item). |
| `secondary_item_type` | Type | Select — Co-Product · By-Product · Scrap · Additional Finished Good |  |
| `bom_secondary_item` | BOM Secondary Item | Text | lecture seule; masqué |
| `valuation_type` | Valuation Type | Select — Valuation Rate · % of Component Cost · Manual |  |

## Stock Entry Type

*Stock Entry Type* — `stock/stock_entry_type.yaml`

- **Titre** : `purpose`
- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `purpose` | Purpose | Select — Material Issue · Material Receipt · Material Transfer · Material Transfer for Manufacture · Material Consumption for Manufacture · Manufacture · Repack · Send to Subcontractor · Disassemble · Receive from Customer · Return Raw Material to Customer · Subcontracting Delivery · Subcontracting Return | **requis**; colonne de liste; défaut `Material Issue` |
| `add_to_transit` | Add to Transit | Boolean | défaut `non` |
| `batch_split` | Batch Split | Boolean | lecture seule; — On submission of the stock entry, the consumed batch is split into one child batch per finished piece |
| `is_standard` | Is Standard | Boolean | lecture seule |

## Stock Ledger Entry

*Stock Ledger Entry* — `stock/stock_ledger_entry.yaml` · soumis

- **Numérotation** : série `SLE-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `item_code`
- **Icône** : `book-open`
- **Permissions explicites** — `write` : 0, `create` : 0, `delete` : 0, `submit` : 0, `cancel` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | colonne de liste; lecture seule |
| `serial_no` | Serial No | LongText | lecture seule |
| `batch_no` | Batch No | Text | lecture seule |
| `warehouse` | Warehouse | Link → `Warehouse` | colonne de liste; lecture seule |
| `posting_date` | Posting Date | Date | colonne de liste; lecture seule |
| `posting_time` | Posting Time | Time | lecture seule |
| `voucher_type` | Voucher Type | Text | lecture seule |
| `voucher_no` | Voucher No | DynamicLink → `voucher_type` | colonne de liste; lecture seule |
| `voucher_detail_no` | Voucher Detail No | Text | lecture seule |
| `actual_qty` | Qty Change | Decimal | colonne de liste; lecture seule |
| `incoming_rate` | Incoming Rate | Currency | colonne de liste; lecture seule; devise de `company.default_currency` |
| `outgoing_rate` | Outgoing Rate | Currency | lecture seule; devise de `company.default_currency` |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `qty_after_transaction` | Qty After Transaction | Decimal | lecture seule |
| `valuation_rate` | Average Rate | Currency | lecture seule; devise de `company.default_currency` |
| `stock_value` | Balance Stock Value | Currency | lecture seule; devise de `company.default_currency` |
| `stock_value_difference` | Change in Stock Value | Currency | lecture seule; devise de `company.default_currency` |
| `stock_queue` | FIFO Stock Queue (qty, rate) | LongText | lecture seule |
| `project` | Project | Link → `Project` |  |
| `company` | Company | Link → `Company` | lecture seule |
| `fiscal_year` | Fiscal Year | Text | lecture seule |
| `is_cancelled` | Is Cancelled | Boolean | défaut `non` |
| `to_rename` | To Rename | Boolean | masqué; défaut `oui` |
| `dependant_sle_voucher_detail_no` | Dependant SLE Voucher Detail No | Text |  |
| `recalculate_rate` | Recalculate Incoming/Outgoing Rate | Boolean | lecture seule |
| `serial_and_batch_bundle` | Serial and Batch Bundle | Link → `Serial and Batch Bundle` |  |
| `has_batch_no` | Has Batch No | Boolean | défaut `non` |
| `has_serial_no` | Has Serial No | Boolean | défaut `non` |
| `is_adjustment_entry` | Is Adjustment Entry | Boolean | défaut `non` |
| `auto_created_serial_and_batch_bundle` | Auto Created Serial and Batch Bundle | Boolean | défaut `non` |
| `posting_datetime` | Posting Datetime | Datetime |  |

## Stock Reconciliation

*Stock Reconciliation* — `stock/stock_reconciliation.yaml` · soumis

- **Numérotation** : série `STRE-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `naming_series`
- **Icône** : `scale`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — MAT-RECO-.YYYY.- | **requis** |
| `company` | Company | Link → `Company` | **requis** |
| `purpose` | Purpose | Select — Opening Stock · Stock Reconciliation · Adjustment Entry | **requis** |
| `posting_date` | Posting Date | Date | **requis**; colonne de liste; défaut `today` |
| `posting_time` | Posting Time | Time | **requis**; colonne de liste |
| `set_posting_time` | Edit Posting Date and Time | Boolean | défaut `non` |
| `items` | Items | Table → `Stock Reconciliation Item` |  |
| `expense_account` | Difference Account | Link → `Account` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `difference_amount` | Difference Amount | Currency | lecture seule; devise de `company.default_currency` |
| `scan_barcode` | Scan Barcode | Text |  |
| `scan_mode` | Scan Mode | Boolean | défaut `non`; — Disables auto-fetching of existing quantity |
| `set_warehouse` | Default Warehouse | Link → `Warehouse` |  |
| `last_scanned_warehouse` | Last Scanned Warehouse | Text |  |

## Stock Reconciliation Item

*Stock Reconciliation Item* — `stock/stock_reconciliation_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `barcode` | Barcode | Text |  |
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `warehouse` | Warehouse | Link → `Warehouse` | **requis**; colonne de liste |
| `qty` | Quantity | Decimal | colonne de liste |
| `stock_uom` | Stock UOM | Link → `UOM` | colonne de liste; lecture seule |
| `valuation_rate` | Valuation Rate | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `amount` | Amount | Currency | lecture seule; devise de `parent_company.default_currency` |
| `serial_no` | Serial No | LongText |  |
| `current_qty` | Current Qty | Decimal | lecture seule |
| `current_serial_no` | Current Serial No | LongText | lecture seule |
| `current_valuation_rate` | Current Valuation Rate | Currency | lecture seule; devise de `parent_company.default_currency` |
| `current_amount` | Current Amount | Currency | lecture seule; devise de `parent_company.default_currency` |
| `quantity_difference` | Quantity Difference | Text | lecture seule |
| `amount_difference` | Amount Difference | Currency | lecture seule; devise de `parent_company.default_currency` |
| `batch_no` | Batch No | Link → `Batch` |  |
| `allow_zero_valuation_rate` | Allow Zero Valuation Rate | Boolean | défaut `non` |
| `has_item_scanned` | Has Item Scanned | Text | lecture seule |
| `serial_and_batch_bundle` | Serial / Batch Bundle | Link → `Serial and Batch Bundle` |  |
| `current_serial_and_batch_bundle` | Current Serial / Batch Bundle | Link → `Serial and Batch Bundle` | lecture seule |
| `item_group` | Item Group | Link → `Item Group` |  |
| `use_serial_batch_fields` | Use Serial No / Batch Fields | Boolean | défaut `non` |
| `reconcile_all_serial_batch` | Reconcile All Serial Nos / Batches | Boolean | défaut `non` |

## Stock Reposting Settings

*Stock Reposting Settings* — `stock/stock_reposting_settings.yaml` · document unique

- **Icône** : `settings`
- **Permissions explicites** — `create` : 0, `delete` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `start_time` | Start Time | Time |  |
| `end_time` | End Time | Time |  |
| `limits_dont_apply_on` | Limits don't apply on | Select — Monday · Tuesday · Wednesday · Thursday · Friday · Saturday · Sunday |  |
| `limit_reposting_timeslot` | Limit timeslot for Stock Reposting | Boolean | défaut `non` |
| `item_based_reposting` | Use Item based reposting | Boolean | défaut `oui` |
| `enable_parallel_reposting` | Enable Parallel Reposting | Boolean | défaut `non` |
| `no_of_parallel_reposting` | No of Parallel Reposting (Per Item) | Int | défaut `4` |
| `enable_separate_reposting_for_gl` | Enable Separate Reposting for GL | Boolean | défaut `non` |
| `do_not_fetch_incoming_rate_from_serial_no` | Do not fetch incoming rate from Serial No | Boolean | défaut `non`; — For legacy serial nos, do not fetch incoming rate from serial no and calculate it based on the inward transact |
| `repost_incorrect_valuation_entries` | Auto Repost Incorrect Valuation Entries (Weekly) | Boolean | défaut `non`; — If enabled, a weekly scheduler scans the Stock Ledger Variance for item-warehouses with incorrect valuation in |

## Stock Reservation Entry

*Stock Reservation Entry* — `stock/stock_reservation_entry.yaml` · soumis

- **Numérotation** : série `SRE-{YYYY}-{#####}`
- **Titre** : `item_code`
- **Icône** : `bookmark`
- **Permissions explicites** — `write` : 0, `create` : 0, `delete` : 0, `submit` : 0, `cancel` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | colonne de liste; lecture seule |
| `warehouse` | Warehouse | Link → `Warehouse` | colonne de liste; lecture seule |
| `voucher_type` | Voucher Type | Text | lecture seule |
| `voucher_no` | Voucher No | DynamicLink → `voucher_type` | lecture seule |
| `voucher_detail_no` | Voucher Detail No | Text | lecture seule |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `project` | Project | Link → `Project` | lecture seule |
| `company` | Company | Link → `Company` | lecture seule |
| `reserved_qty` | Reserved Qty | Decimal | colonne de liste; lecture seule |
| `status` | Status | Select — Draft · Partially Reserved · Reserved · Partially Delivered · Partially Used · Delivered · Cancelled · Closed | lecture seule; défaut `Draft` |
| `delivered_qty` | Delivered Qty | Decimal | lecture seule |
| `available_qty` | Available Qty to Reserve | Decimal | lecture seule |
| `voucher_qty` | Voucher Qty | Decimal | lecture seule |
| `has_serial_no` | Has Serial No | Boolean | lecture seule |
| `has_batch_no` | Has Batch No | Boolean | lecture seule |
| `sb_entries` | Sb Entries | Table → `Serial and Batch Entry` |  |
| `reservation_based_on` | Reservation Based On | Select — Qty · Serial and Batch | lecture seule; défaut `Qty` |
| `from_voucher_type` | From Voucher Type | Text | lecture seule |
| `from_voucher_detail_no` | From Voucher Detail No | Text | lecture seule |
| `from_voucher_no` | From Voucher No | DynamicLink → `from_voucher_type` | lecture seule |
| `consumed_qty` | Consumed Qty | Decimal |  |
| `transferred_qty` | Transferred Qty | Decimal |  |

## Stock Settings

*Stock Settings* — `stock/stock_settings.yaml` · document unique

- **Titre** : `item_group`
- **Icône** : `settings`
- **Permissions explicites** — `create` : 0, `delete` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_naming_by` | Item Naming By | Select — Item Code · Naming Series | colonne de liste; défaut `Item Code` |
| `item_group` | Default Item Group | Link → `Item Group` | colonne de liste |
| `stock_uom` | Default Stock UOM | Link → `UOM` | colonne de liste |
| `valuation_method` | Default Valuation Method | Select — FIFO · Moving Average · LIFO · Standard Cost |  |
| `over_delivery_receipt_allowance` | Over Delivery/Receipt Allowance (%) | Number | — The percentage you are allowed to receive or deliver more against the quantity ordered. For example, if you ha |
| `action_if_quality_inspection_is_not_submitted` | Action if Quality Inspection is not submitted | Select — Stop · Warn | défaut `Stop` |
| `show_barcode_field` | Show barcode field in stock transactions | Boolean | défaut `oui` |
| `clean_description_html` | Convert Item description to clean HTML in transactions | Boolean | défaut `oui` |
| `auto_insert_price_list_rate_if_missing` | Auto insert Item Price if missing | Boolean | défaut `non` |
| `allow_negative_stock` | Allow negative stock | Boolean | défaut `non`; — This can be enabled at specific Item level as well |
| `auto_indent` | Raise Material Request when stock reaches re-order level | Boolean | défaut `non`; — This option is useful if you want to ensure a constant supply of raw materials/products and avoid shortage. A  |
| `reorder_email_notify` | Notify by email on creation of automatic Material Request | Boolean | défaut `non`; — An email will be sent to notify the User with the role 'Purchase Manager' when an automatic Material Request i |
| `stock_frozen_upto` | Stock frozen up to | Date | — No stock transactions can be created or modified before this date. |
| `stock_frozen_upto_days` | Freeze stocks older than (days) | Int | — Stock transactions that are older than the mentioned days cannot be modified. |
| `use_naming_series` | Have default Naming Series for Batch ID? | Boolean | défaut `non`; — This will be applied if no naming series is configured in Item master |
| `naming_series_prefix` | Naming Series Prefix | Text | défaut `BATCH-` |
| `disable_serial_no_and_batch_selector` | Disable Serial No and Batch selector | Boolean | défaut `non`; — If enabled, users must enter Serial No. / Batch data manually instead of using the selector dialog. |
| `action_if_quality_inspection_is_rejected` | Action if Quality Inspection is rejected | Select — Stop · Warn | défaut `Stop` |
| `mr_qty_allowance` | Over Transfer Allowance (%) | Decimal | — The percentage you are allowed to transfer more against the quantity ordered. For example, if you have ordered |
| `update_existing_price_list_rate` | Update existing Price List Rate | Boolean | défaut `non` |
| `enable_stock_reservation` | Enable stock reservation | Boolean | défaut `non`; — Allows to keep aside a specific quantity of inventory for a particular order. |
| `allow_partial_reservation` | Allow partial reservation | Boolean | défaut `oui`; — Partial stock can be reserved. For example, If you have a Sales Order of 100 units and the Available Stock is  |
| `pick_serial_and_batch_based_on` | Pick Serial / Batch Based On | Select — FIFO · LIFO · Expiry | défaut `FIFO` |
| `auto_create_serial_and_batch_bundle_for_outward` | Auto create Serial and Batch Bundle for outward | Boolean | défaut `oui` |
| `auto_reserve_serial_and_batch` | Auto reserve Serial and Batch Nos | Boolean | défaut `oui`; — Serial and Batch Nos will be auto-reserved based on <b>Pick Serial / Batch Based On</b> |
| `allow_to_edit_stock_uom_qty_for_sales` | Allow to edit stock UOM qty for Sales documents | Boolean | défaut `non` |
| `allow_to_edit_stock_uom_qty_for_purchase` | Allow to edit stock UOM qty for Purchase documents | Boolean | défaut `non` |
| `allow_to_edit_stock_uom_qty_for_stock_entry` | Allow to edit stock UOM qty for Stock Entry | Boolean | défaut `non` |
| `auto_reserve_stock_for_sales_order_on_purchase` | Auto reserve Stock for Sales Order on Purchase | Boolean | défaut `non`; — Stock will be reserved on submission of <b>Purchase Receipt</b> created against Material Request for Sales Ord |
| `use_serial_batch_fields` | Use Serial / Batch fields | Boolean | défaut `oui`; — On submission of the stock transaction, system will auto create the Serial and Batch Bundle based on the Seria |
| `do_not_update_serial_batch_on_creation_of_auto_bundle` | Do not update Serial / Batch on creation of auto bundle | Boolean | défaut `oui`; — If enabled, do not update serial / batch values in the stock transactions on creation of auto Serial   / Batch |
| `allow_internal_transfer_at_arms_length_price` | Allow internal transfers at user-defined rate | Boolean | défaut `non`; — If enabled, the item rate won't adjust to the valuation rate during internal transfers, but accounting will st |
| `do_not_use_batchwise_valuation` | Do not use Batch-wise Valuation | Boolean | défaut `non`; — If enabled, the system will use the moving average valuation method to calculate the valuation rate for the ba |
| `over_picking_allowance` | Over Picking Allowance (%) | Percent | — The percentage you are allowed to pick more items in the pick list than the ordered quantity. |
| `allow_existing_serial_no` | Allow existing Serial No to be Manufactured/Received again | Boolean | défaut `oui` |
| `auto_reserve_stock` | Auto reserve stock | Boolean | défaut `non`; — Upon submission of the Sales Order, Work Order, or Production Plan, the system will automatically reserve the  |
| `set_serial_and_batch_bundle_naming_based_on_naming_series` | Set Serial and Batch Bundle Naming Based on Naming Series | Boolean | défaut `non` |
| `allow_uom_with_conversion_rate_defined_in_item` | Allow UOM with conversion rate defined in Item | Boolean | défaut `non`; — If enabled, the system will allow selecting UOMs in sales and purchase transactions only if the conversion rat |
| `allow_to_make_quality_inspection_after_purchase_or_delivery` | Allow to make Quality Inspection after Purchase / Delivery | Boolean | défaut `non` |
| `update_price_list_based_on` | Update Price List based on | Select — Rate · Price List Rate | défaut `Rate` |
| `validate_material_transfer_warehouses` | Validate Material Transfer warehouses | Boolean | défaut `non`; — If enabled, the source and target warehouse in the Material Transfer Stock Entry must be different else an err |
| `allow_negative_stock_for_batch` | Allow negative stock for Batch | Boolean | défaut `non`; — If enabled, the system will allow negative stock entries for the batch. But, this may lead to incorrect valuat |
| `enable_serial_and_batch_no_for_item` | Activate Serial / Batch No for Item | Boolean | défaut `non` |
| `naming_series_details` | Naming Series options | LongText | lecture seule; masqué |
| `naming_series_preview` | Naming Series options | LongText | lecture seule; masqué |
| `use_inline_serial_batch_editor` | Use Inline Serial / Batch Editor | Boolean | défaut `oui`; — Show an inline editable table for serial numbers / batches on the item row instead of the dialog |
| `auto_map_raw_materials_to_finished_goods` | Auto Map Raw Materials to Finished Goods | Boolean | défaut `non`; — On submit of a Manufacture / Repack entry, map the raw material serial / batch nos that were not mapped in dra |

## UOM Category

*UOM Category* — `stock/uom_category.yaml`

- **Titre** : `category_name`
- **Icône** : `ruler`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `category_name` | Category Name | Text | **requis**; colonne de liste |

## UOM Conversion Detail

*UOM Conversion Detail* — `stock/uom_conversion_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `uom` | UOM | Link → `UOM` | **requis**; colonne de liste |
| `conversion_factor` | Conversion Factor | Number | colonne de liste |

## Variant Field

*Variant Field* — `stock/variant_field.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `field_name` | Field Name | Text | **requis**; colonne de liste |

## Warehouse

*Warehouse* — `stock/warehouse.yaml`

- **Vues** : tree (parent `parent_warehouse`)
- **Titre** : `warehouse_name`
- **Icône** : `warehouse`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `warehouse_name` | Warehouse Name | Text | **requis** |
| `is_group` | Is Group Warehouse | Boolean | colonne de liste; défaut `non` |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `disabled` | Disabled | Boolean | masqué; défaut `non` |
| `account` | Account | Link → `Account` | colonne de liste; — If blank, parent Warehouse Account or company default will be considered in transactions |
| `email_id` | Email Address | Text | masqué |
| `phone_no` | Phone No | Text |  |
| `mobile_no` | Mobile No | Text |  |
| `address_line_1` | Address Line 1 | Text |  |
| `address_line_2` | Address Line 2 | Text |  |
| `city` | City | Text |  |
| `state` | State/Province | Text |  |
| `pin` | PIN | Text |  |
| `parent_warehouse` | Parent Warehouse | Link → `Warehouse` |  |
| `lft` | lft | Int | lecture seule; masqué |
| `rgt` | rgt | Int | lecture seule; masqué |
| `old_parent` | Old Parent | Link → `Warehouse` | lecture seule; masqué |
| `warehouse_type` | Warehouse Type | Link → `Warehouse Type` |  |
| `default_in_transit_warehouse` | Default In-Transit Warehouse | Link → `Warehouse` |  |
| `is_rejected_warehouse` | Is Rejected Warehouse | Boolean | défaut `non`; — If yes, then this warehouse will be used to store rejected materials |
| `customer` | Customer | Link → `Customer` | — Only to be used for Subcontracting Inward. |

## Warehouse Type

*Warehouse Type* — `stock/warehouse_type.yaml`

- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `description` | Description | LongText |  |
