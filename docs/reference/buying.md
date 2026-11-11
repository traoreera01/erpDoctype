# Référence des champs — Achats (`buying`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `buying/` (19 DocTypes). Ne pas éditer à la main : relancer le script.

508 champs au total ; types les plus fréquents : `Link` (143), `Boolean` (72), `Currency` (72), `Text` (61), `Number` (26).

## Buying Settings

*Buying Settings* — `buying/buying_settings.yaml` · document unique

- **Icône** : `settings`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `supp_master_name` | Supplier Naming By | Select — Supplier Name · Naming Series · Auto Name | défaut `Supplier Name` |
| `supplier_group` | Default Supplier Group | Link → `Supplier Group` |  |
| `buying_price_list` | Default Buying Price List | Link → `Price List` |  |
| `po_required` | Is Purchase Order required for Purchase Invoice & Receipt creation? | Select — No · Yes |  |
| `pr_required` | Is Purchase Receipt required for Purchase Invoice creation? | Select — No · Yes |  |
| `maintain_same_rate` | Maintain same rate throughout the purchase  cycle | Boolean | défaut `non`; — Warn or stop if Item rate is changed in Purchase Invoice or Purchase Receipt generated from a Purchase Order. |
| `allow_multiple_items` | Allow Item to be added multiple times in a transaction | Boolean | défaut `non` |
| `backflush_raw_materials_of_subcontract_based_on` | Backflush raw materials of subcontract based on | Select — BOM · Material Transferred for Subcontract | défaut `BOM` |
| `over_transfer_allowance` | Over Transfer Allowance (%) | Number | — Percentage you are allowed to transfer more against the quantity ordered. For example: If you have ordered 100 |
| `maintain_same_rate_action` | Action if same rate is not maintained | Select — Stop · Warn | défaut `Stop`; — Configure the action to stop the transaction or just warn if the same rate is not maintained. |
| `bill_for_rejected_quantity_in_purchase_invoice` | Bill for rejected quantity in Purchase Invoice | Boolean | défaut `oui`; — If checked, the rejected quantity is billed anywhere in the purchase cycle. |
| `disable_last_purchase_rate` | Disable last purchase rate | Boolean | défaut `non`; — Prevents the system from automatically using the rate from the last purchase transaction when creating new pur |
| `show_pay_button` | Show pay button in Purchase Order portal | Boolean | défaut `oui` |
| `set_landed_cost_based_on_purchase_invoice_rate` | Set Landed Cost Based on Purchase Invoice Rate | Boolean | défaut `non`; — Users can enable the checkbox If they want to adjust the incoming rate (set using purchase receipt) based on t |
| `use_transaction_date_exchange_rate` | Use Transaction Date Exchange Rate | Boolean | défaut `non`; — While making a Purchase Receipt or Purchase Invoice from a Purchase Order, use the exchange rate on its postin |
| `blanket_order_allowance` | Blanket Order Allowance (%) | Number | défaut `0.0`; — Percentage you are allowed to order beyond the Blanket Order quantity. |
| `auto_create_subcontracting_order` | Auto create Subcontracting Order | Boolean | défaut `non`; — Subcontracting Order (Draft) will be auto-created on submission of Purchase Order. |
| `auto_create_purchase_receipt` | Auto create Purchase Receipt | Boolean | défaut `non`; — Purchase Receipt (Draft) will be auto-created on submission of Subcontracting Receipt. |
| `project_update_frequency` | How often should project be updated of Total Purchase Cost ? | Select — Each Transaction · Manual | défaut `Each Transaction` |
| `allow_zero_qty_in_purchase_order` | Allow Purchase Order with Zero Quantity | Boolean | défaut `non`; — Allows users to submit Purchase Orders with zero quantity. Useful when rates are fixed but the quantities are  |
| `allow_zero_qty_in_request_for_quotation` | Allow Request for Quotation with Zero Quantity | Boolean | défaut `non`; — Allows users to submit Request for Quotations with zero quantity. Useful when rates are fixed but the quantiti |
| `allow_zero_qty_in_supplier_quotation` | Allow Supplier Quotation with Zero Quantity | Boolean | défaut `non`; — Allows users to submit Supplier Quotations with zero quantity. Useful when rates are fixed but the quantities  |
| `set_valuation_rate_for_rejected_materials` | Set valuation rate for rejected Materials | Boolean | défaut `non`; — If enabled, the system will generate an accounting entry for material rejected anywhere in the purchase cycle. |
| `fixed_email` | Fixed Outgoing Email Account | Link → `Email Account` | — If set, the system does not use the user's Email or the standard outgoing Email account for sending request fo |
| `validate_consumed_qty` | Validate consumed quantity (as per BOM) | Boolean | défaut `non`; — Raw materials consumed qty will be validated based on FG BOM required qty |
| `allow_negative_rates_for_items` | Allow negative rates for Items | Boolean | défaut `non` |
| `naming_series_details` | Naming Series options | LongText | masqué |
| `over_order_allowance` | Over Order Allowance (%) | Number | — The percentage by which you are allowed to order more on a Purchase Order than the quantity requested on the o |

## Customer Number At Supplier

*Customer Number At Supplier* — `buying/customer_number_at_supplier.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | colonne de liste |
| `customer_number` | Customer Number | Text | colonne de liste |

## Purchase Order

*Purchase Order* — `buying/purchase_order.yaml` · soumis

- **Numérotation** : série `PUOR-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `title`
- **Icône** : `shopping-cart`
- **Workflow** : États : Brouillon → À approuver → Approuvée → Refusée → Annulée
- **Workflow** : Actions : `Annuler`, `Approuver`, `Refuser`, `Reprendre`, `Soumettre`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text |  |
| `naming_series` | Series | Select — PUR-ORD-.YYYY.- | **requis** |
| `supplier` | Supplier | Link → `Supplier` | **requis** |
| `supplier_name` | Supplier Name | Text | lecture seule; recopié de `supplier.supplier_name` |
| `company` | Company | Link → `Company` | **requis** |
| `transaction_date` | Date | Date | **requis**; colonne de liste; défaut `today` |
| `schedule_date` | Required By | Date | colonne de liste |
| `order_confirmation_no` | Order Confirmation No | Text |  |
| `order_confirmation_date` | Order Confirmation Date | Date | visible si `order_confirmation_no` |
| `customer` | Customer | Link → `Customer` | lecture seule |
| `customer_name` | Customer Name | Text | lecture seule; recopié de `customer.customer_name` |
| `customer_contact_person` | Customer Contact | Link → `Contact` |  |
| `customer_contact_display` | Customer Contact | LongText |  |
| `customer_contact_mobile` | Customer Mobile No | LongText | masqué |
| `customer_contact_email` | Customer Contact Email | Code | masqué |
| `supplier_address` | Supplier Address | Link → `Address` |  |
| `contact_person` | Supplier Contact | Link → `Contact` |  |
| `address_display` | Supplier Address Details | TextEditor | lecture seule |
| `contact_display` | Contact Name | LongText | lecture seule |
| `contact_mobile` | Contact Mobile No | LongText | lecture seule |
| `contact_email` | Contact Email | LongText | lecture seule |
| `shipping_address` | Shipping Address | Link → `Address` |  |
| `shipping_address_display` | Shipping Address Details | TextEditor | lecture seule |
| `currency` | Currency | Link → `Currency` | **requis** |
| `conversion_rate` | Exchange Rate | Number | **requis** |
| `buying_price_list` | Price List | Link → `Price List` |  |
| `price_list_currency` | Price List Currency | Link → `Currency` | lecture seule |
| `plc_conversion_rate` | Price List Exchange Rate | Number |  |
| `ignore_pricing_rule` | Ignore Pricing Rule | Boolean | défaut `non` |
| `set_warehouse` | Set Target Warehouse | Link → `Warehouse` |  |
| `is_subcontracted` | Is Subcontracted | Boolean | défaut `non` |
| `supplier_warehouse` | Supplier Warehouse | Link → `Warehouse` | visible si `is_subcontracted`; obligatoire si `is_subcontracted` |
| `scan_barcode` | Scan Barcode | Text |  |
| `items` | Items | Table → `Purchase Order Item` |  |
| `pricing_rules` | Purchase Order Pricing Rule | Table → `Pricing Rule Detail` | lecture seule |
| `total_qty` | Total Quantity | Decimal | lecture seule; calculé : `sum(items.qty)` |
| `base_total` | Total (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_net_total` | Net Total (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `total` | Total | Currency | lecture seule; calculé : `sum(items.amount)`; devise de `currency` |
| `net_total` | Net Total | Currency | lecture seule; calculé : `sum(items.net_amount)`; devise de `currency` |
| `total_net_weight` | Total Net Weight | Number | lecture seule |
| `taxes_and_charges` | Purchase Taxes and Charges Template | Link → `Purchase Taxes and Charges Template` |  |
| `shipping_rule` | Shipping Rule | Link → `Shipping Rule` |  |
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
| `disable_rounded_total` | Disable Rounded Total | Boolean | défaut `non` |
| `in_words` | In Words | Text | lecture seule |
| `advance_paid` | Advance Paid (Company Currency) | Currency | lecture seule; devise de `party_account_currency` |
| `payment_terms_template` | Payment Terms Template | Link → `Payment Terms Template` |  |
| `payment_schedule` | Payment Schedule | Table → `Payment Schedule` |  |
| `tc_name` | Terms | Link → `Terms and Conditions` |  |
| `terms` | Terms and Conditions | TextEditor |  |
| `status` | Status | Select — Draft · On Hold · To Pay · To Receive and Bill · To Bill · To Receive · Completed · Cancelled · Closed · Delivered | **requis**; lecture seule; défaut `Draft` |
| `ref_sq` | Supplier Quotation | Link → `Supplier Quotation` | lecture seule |
| `party_account_currency` | Party Account Currency | Link → `Currency` | lecture seule; masqué |
| `inter_company_order_reference` | Inter Company Order Reference | Link → `Sales Order` | lecture seule |
| `remarks` | Remarks | LongText |  |
| `per_received` | % Received | Percent | colonne de liste; lecture seule |
| `per_billed` | % Billed | Percent | colonne de liste; lecture seule |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `select_print_heading` | Print Heading | Link → `Print Heading` |  |
| `group_same_items` | Group same items | Boolean | défaut `non` |
| `language` | Print Language | Text |  |
| `from_date` | From Date | Date |  |
| `to_date` | To Date | Date |  |
| `auto_repeat` | Auto Repeat | Link → `Auto Repeat` | lecture seule |
| `tax_category` | Tax Category | Link → `Tax Category` |  |
| `set_reserve_warehouse` | Set Reserve Warehouse | Link → `Warehouse` |  |
| `billing_address` | Company Billing Address | Link → `Address` |  |
| `billing_address_display` | Billing Address Details | TextEditor | lecture seule |
| `is_internal_supplier` | Is Internal Supplier | Boolean | lecture seule |
| `represents_company` | Represents Company | Link → `Company` | lecture seule |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |
| `set_from_warehouse` | Set From Warehouse | Link → `Warehouse` |  |
| `incoterm` | Incoterm | Link → `Incoterm` |  |
| `named_place` | Named Place | Text |  |
| `advance_payment_status` | Advance Payment Status | Select — Not Initiated · Initiated · Partially Paid · Fully Paid | masqué |
| `has_unit_price_items` | Has Unit Price Items | Boolean | masqué; défaut `non` |
| `dispatch_address` | Dispatch Address | Link → `Address` |  |
| `dispatch_address_display` | Dispatch Address Details | TextEditor | lecture seule |
| `supplier_group` | Supplier Group | Link → `Supplier Group` | masqué |
| `last_scanned_warehouse` | Last Scanned Warehouse | Text |  |
| `mps` | MPS | Link → `Master Production Schedule` | lecture seule |
| `item_wise_tax_details` | Item Wise Tax Details | Table → `Item Wise Tax Detail` | masqué |
| `transaction_time` | Time | Time |  |

## Purchase Order Item

*Purchase Order Item* — `buying/purchase_order_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `supplier_part_no` | Supplier Part Number | Text | lecture seule; masqué |
| `item_name` | Item Name | Text | recopié de `item_code.item_name` |
| `schedule_date` | Required By | Date | **requis**; colonne de liste |
| `expected_delivery_date` | Expected Delivery Date | Date |  |
| `description` | Description | TextEditor |  |
| `qty` | Quantity | Decimal | **requis**; colonne de liste |
| `stock_uom` | Stock UOM | Link → `UOM` | **requis**; lecture seule |
| `uom` | UOM | Link → `UOM` | **requis**; colonne de liste |
| `conversion_factor` | UOM Conversion Factor | Number | **requis** |
| `price_list_rate` | Price List Rate | Currency | devise de `parent_currency` |
| `discount_percentage` | Discount on Price List Rate (%) | Percent |  |
| `discount_amount` | Discount Amount | Currency | devise de `parent_currency` |
| `last_purchase_rate` | Last Purchase Rate | Currency | lecture seule; devise de `parent_currency` |
| `base_price_list_rate` | Price List Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `rate` | Rate | Currency | colonne de liste; devise de `parent_currency` |
| `amount` | Amount | Currency | colonne de liste; lecture seule; calculé : `qty * rate`; devise de `parent_currency` |
| `base_rate` | Rate (Company Currency) | Currency | **requis**; lecture seule; devise de `parent_company.default_currency` |
| `base_amount` | Amount (Company Currency) | Currency | **requis**; lecture seule; devise de `parent_company.default_currency` |
| `pricing_rules` | Pricing Rules | LongText | lecture seule; masqué |
| `is_free_item` | Is Free Item | Boolean | lecture seule |
| `net_rate` | Net Rate | Currency | lecture seule; devise de `parent_currency` |
| `net_amount` | Net Amount | Currency | lecture seule; calculé : `amount - discount_amount`; devise de `parent_currency` |
| `base_net_rate` | Net Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_net_amount` | Net Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `weight_per_unit` | Weight Per Unit | Number | lecture seule |
| `total_weight` | Total Weight | Number | lecture seule |
| `weight_uom` | Weight UOM | Link → `UOM` | lecture seule |
| `warehouse` | Target Warehouse | Link → `Warehouse` | colonne de liste |
| `project` | Project | Link → `Project` |  |
| `material_request` | Material Request | Link → `Material Request` | lecture seule; cible submitted |
| `material_request_item` | Material Request Item | Text | lecture seule; masqué |
| `sales_order` | Sales Order | Link → `Sales Order` |  |
| `sales_order_item` | Sales Order Item | Text | lecture seule; masqué |
| `supplier_quotation` | Supplier Quotation | Link → `Supplier Quotation` | lecture seule; cible submitted |
| `supplier_quotation_item` | Supplier Quotation Item | Text | lecture seule; masqué; — Référence de la ligne d'origine (Supplier Quotation Item). |
| `delivered_by_supplier` | To be Delivered to Customer | Boolean | défaut `non` |
| `blanket_order` | Blanket Order | Link → `Blanket Order` |  |
| `blanket_order_rate` | Blanket Order Rate | Currency | lecture seule; devise de `parent_currency` |
| `item_group` | Item Group | Link → `Item Group` | lecture seule; masqué |
| `brand` | Brand | Link → `Brand` | lecture seule; masqué |
| `bom` | BOM | Link → `BOM` | lecture seule |
| `stock_qty` | Qty in Stock UOM | Decimal | lecture seule |
| `received_qty` | Received Qty | Decimal | lecture seule |
| `returned_qty` | Returned Qty | Decimal | lecture seule |
| `billed_amt` | Billed Amount | Currency | lecture seule; devise de `parent_currency` |
| `closed` | Closed | Boolean | lecture seule |
| `item_tax_rate` | Item Tax Rate | Code | lecture seule; masqué; — Tax detail table fetched from item master as a string and stored in this field. Used for Taxes and Charges |
| `expense_account` | Expense Account | Link → `Account` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `page_break` | Page Break | Boolean | défaut `non` |
| `item_tax_template` | Item Tax Template | Link → `Item Tax Template` |  |
| `manufacturer` | Manufacturer | Link → `Manufacturer` |  |
| `manufacturer_part_no` | Manufacturer Part Number | Text |  |
| `against_blanket_order` | Against Blanket Order | Boolean | défaut `non` |
| `is_fixed_asset` | Is Fixed Asset | Boolean | lecture seule |
| `stock_uom_rate` | Rate of Stock UOM | Currency | lecture seule; devise de `parent_currency` |
| `actual_qty` | Available Qty at Target Warehouse | Decimal | lecture seule |
| `company_total_stock` | Available Qty at Company | Number | lecture seule |
| `margin_type` | Margin Type | Select — Percentage · Amount |  |
| `margin_rate_or_amount` | Margin Rate or Amount | Number |  |
| `rate_with_margin` | Rate With Margin | Currency | lecture seule; devise de `parent_currency` |
| `base_rate_with_margin` | Rate With Margin (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `production_plan` | Production Plan | Link → `Production Plan` | lecture seule |
| `production_plan_item` | Production Plan Item | Text | lecture seule; masqué |
| `production_plan_sub_assembly_item` | Production Plan Sub Assembly Item | Text | lecture seule; masqué |
| `product_bundle` | Product Bundle | Link → `Product Bundle` | lecture seule; masqué; — Product Bundle version this row was packed from |
| `sales_order_packed_item` | Sales Order Packed Item | Text |  |
| `fg_item` | Finished Good | Link → `Item` |  |
| `fg_item_qty` | Finished Good Qty | Decimal | défaut `1.000` |
| `from_warehouse` | From Warehouse | Link → `Warehouse` |  |
| `wip_composite_asset` | WIP Composite Asset | Link → `Asset` |  |
| `job_card` | Job Card | Link → `Job Card` | lecture seule |
| `distributed_discount_amount` | Distributed Discount Amount | Currency | devise de `parent_currency` |
| `mapped_additional_discount_amount` | Additional Discount per Stock Unit | Currency | lecture seule; devise de `parent_currency`; — Tax-exclusive additional discount carried from a source document, per stock unit. |
| `subcontracted_qty` | Subcontracted Quantity | Decimal | lecture seule |

## Purchase Receipt Item Supplied

*Purchase Receipt Item Supplied* — `buying/purchase_receipt_item_supplied.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `main_item_code` | Item Code | Link → `Item` | colonne de liste; lecture seule |
| `rm_item_code` | Raw Material Item Code | Link → `Item` | colonne de liste; lecture seule |
| `description` | Description | TextEditor | lecture seule |
| `batch_no` | Batch No | Link → `Batch` |  |
| `serial_no` | Serial No | LongText |  |
| `required_qty` | Available Qty For Consumption | Decimal | colonne de liste; lecture seule |
| `consumed_qty` | Qty to Be Consumed | Decimal | **requis**; colonne de liste |
| `stock_uom` | Stock Uom | Link → `UOM` | lecture seule |
| `rate` | Rate | Currency | lecture seule; devise de `parent_currency` |
| `amount` | Amount | Currency | lecture seule; devise de `parent_currency` |
| `conversion_factor` | Conversion Factor | Number | lecture seule; masqué |
| `current_stock` | Current Stock | Number | colonne de liste; lecture seule |
| `reference_name` | Reference Name | Text | colonne de liste; lecture seule; masqué |
| `bom_detail_no` | BOM Detail No | Text | colonne de liste; lecture seule; masqué |
| `item_name` | Item Name | Text | lecture seule |
| `purchase_order` | Purchase Order | Link → `Purchase Order` | lecture seule; masqué |

## Request for Quotation

*Request for Quotation* — `buying/request_for_quotation.yaml` · soumis

- **Numérotation** : série `RQ-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `title`
- **Icône** : `file-question-mark`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — PUR-RFQ-.YYYY.- | **requis** |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `vendor` | Supplier | Link → `Supplier` | colonne de liste; lecture seule; masqué; — For individual supplier |
| `transaction_date` | Date | Date | **requis**; colonne de liste; défaut `today` |
| `suppliers` | Suppliers | Table → `Request for Quotation Supplier` |  |
| `items` | Items | Table → `Request for Quotation Item` |  |
| `email_template` | Email Template | Link → `Email Template` |  |
| `message_for_supplier` | Message for Supplier | TextEditor |  |
| `tc_name` | Terms | Link → `Terms and Conditions` |  |
| `terms` | Terms and Conditions | TextEditor |  |
| `select_print_heading` | Print Heading | Link → `Print Heading` |  |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `opportunity` | Opportunity | Link → `Opportunity` | lecture seule |
| `status` | Status | Select — Draft · Submitted · Cancelled | **requis**; colonne de liste; lecture seule |
| `schedule_date` | Required Date | Date | colonne de liste |
| `incoterm` | Incoterm | Link → `Incoterm` |  |
| `named_place` | Named Place | Text |  |
| `send_attached_files` | Send Attached Files | Boolean | défaut `oui`; — If enabled, all files attached to this document will be attached to each email |
| `send_document_print` | Send Document Print | Boolean | défaut `non`; — If enabled, a print of this document will be attached to each email |
| `billing_address` | Company Billing Address | Link → `Address` |  |
| `billing_address_display` | Billing Address Details | TextEditor | lecture seule |
| `has_unit_price_items` | Has Unit Price Items | Boolean | masqué; défaut `non` |
| `subject` | Subject | Text | **requis**; défaut `Request for Quotation` |
| `mfs_html` | Message for Supplier | Code |  |
| `use_html` | Use HTML | Boolean | masqué; défaut `non` |
| `shipping_address` | Company Shipping Address | Link → `Address` |  |
| `shipping_address_display` | Shipping Address Details | TextEditor | lecture seule |
| `title` | Title | Text |  |

## Request for Quotation Item

*Request for Quotation Item* — `buying/request_for_quotation_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `supplier_part_no` | Supplier Part No | Text | lecture seule; masqué |
| `item_name` | Item Name | Text | recopié de `item_code.item_name` |
| `description` | Description | TextEditor |  |
| `qty` | Quantity | Decimal | **requis**; colonne de liste |
| `schedule_date` | Required Date | Date | **requis**; colonne de liste |
| `uom` | UOM | Link → `UOM` | **requis**; colonne de liste |
| `warehouse` | Warehouse | Link → `Warehouse` | colonne de liste |
| `project_name` | Project | Link → `Project` |  |
| `material_request` | Material Request | Link → `Material Request` | lecture seule |
| `material_request_item` | Material Request Item | Text | masqué |
| `brand` | Brand | Link → `Brand` | lecture seule |
| `item_group` | Item Group | Link → `Item Group` | lecture seule |
| `page_break` | Page Break | Boolean | défaut `non` |
| `stock_uom` | Stock UOM | Link → `UOM` | **requis**; lecture seule |
| `conversion_factor` | UOM Conversion Factor | Number | **requis**; lecture seule |
| `stock_qty` | Qty as per Stock UOM | Decimal | lecture seule |
| `cost_center` | Cost Center | Link → `Cost Center` |  |

## Request for Quotation Supplier

*Request for Quotation Supplier* — `buying/request_for_quotation_supplier.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `send_email` | Send Email | Boolean | colonne de liste; défaut `oui` |
| `email_sent` | Email Sent | Boolean | lecture seule |
| `supplier` | Supplier | Link → `Supplier` | **requis**; colonne de liste |
| `contact` | Contact | Link → `Contact` | colonne de liste |
| `quote_status` | Quote Status | Select — Pending · Received | lecture seule |
| `supplier_name` | Supplier Name | Text | lecture seule; recopié de `supplier.supplier_name` |
| `email_id` | Email ID | Text | colonne de liste |

## Supplier

*Supplier* — `buying/supplier.yaml`

- **Titre** : `supplier_name`
- **Icône** : `truck`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — SUP-.YYYY.- |  |
| `supplier_name` | Supplier Name | Text | **requis** |
| `country` | Country | Link → `Country` |  |
| `default_bank_account` | Company Bank Account | Link → `Bank Account` |  |
| `tax_id` | Tax ID | Text | — Supplier's tax identification number (e.g. PAN, VAT, GST) |
| `tax_category` | Tax Category | Link → `Tax Category` | — Determines which tax rules apply to this supplier |
| `tax_withholding_category` | Tax Withholding Category | Link → `Tax Withholding Category` | — TDS / withholding tax category applied when paying this supplier |
| `is_transporter` | Is Transporter | Boolean | défaut `non`; — Enable to make this supplier selectable as a transporter on Delivery Notes and Stock Entries |
| `is_internal_supplier` | Is Internal Supplier | Boolean | défaut `non`; — Used for inter-company transactions |
| `represents_company` | Represents Company | Link → `Company` | visible si `is_internal_supplier`; obligatoire si `is_internal_supplier`; — Select the related company that this Supplier represents for inter-company transactions. |
| `image` | Image | Image | masqué |
| `supplier_group` | Supplier Group | Link → `Supplier Group` | colonne de liste |
| `supplier_type` | Supplier Type | Select — Company · Individual · Partnership | **requis**; colonne de liste; défaut `Company` |
| `language` | Print Language | Link → `Language` |  |
| `disabled` | Disabled | Boolean | défaut `non`; — Disabled suppliers are hidden from selection in new transactions but remain in historical records |
| `warn_rfqs` | Warn RFQs | Boolean | lecture seule; masqué |
| `warn_pos` | Warn POs | Boolean | lecture seule; masqué |
| `prevent_rfqs` | Prevent RFQs | Boolean | lecture seule; masqué |
| `prevent_pos` | Prevent POs | Boolean | lecture seule; masqué |
| `companies` | Allowed to transact with | Table → `Allowed To Transact With` |  |
| `default_currency` | Billing Currency | Link → `Currency` | colonne de liste |
| `default_price_list` | Price List | Link → `Price List` |  |
| `payment_terms` | Payment Terms Template | Link → `Payment Terms Template` |  |
| `on_hold` | Block Supplier | Boolean | défaut `non`; — When enabled, transactions with this supplier will be blocked based on the Hold Type below |
| `hold_type` | Hold Type | Select — All · Invoices · Payments | défaut `All`; visible si `on_hold`; obligatoire si `on_hold` |
| `release_date` | Release Date | Date | visible si `on_hold`; — Leave blank if the Supplier is blocked indefinitely |
| `accounts` | Per-Company Accounts | Table → `Party Account` | — Override the default payable / advance accounts on a per-company basis. Leave blank to use each company's defa |
| `website` | Website | Text |  |
| `supplier_details` | Supplier Details | LongText | — General information about your Supplier |
| `is_frozen` | Is Frozen | Boolean | défaut `non`; — Frozen suppliers block new transactions and ledger entries until unfrozen. Only users with the role set in Com |
| `allow_purchase_invoice_creation_without_purchase_order` | Allow purchase invoice creation without purchase order | Boolean | défaut `non` |
| `allow_purchase_invoice_creation_without_purchase_receipt` | Allow purchase invoice creation without purchase receipt | Boolean | défaut `non` |
| `supplier_primary_contact` | Primary Contact | Link → `Contact` | masqué; — Reselect, if the chosen contact is edited after save |
| `mobile_no` | Mobile No | Text | lecture seule; masqué |
| `email_id` | Email ID | Text | lecture seule; masqué |
| `primary_address` | Primary Address Preview | TextEditor | lecture seule; masqué |
| `supplier_primary_address` | Primary Address | Link → `Address` | masqué; — Reselect, if the chosen address is edited after save |
| `restrict_to_companies` | Restrict to Companies | Boolean | défaut `non`; — If checked, this Supplier is only available for transactions in the companies listed below. |
| `allowed_companies` | Allowed Companies | Table → `Company Restriction` |  |
| `portal_users` | Supplier Portal Users | Table → `Portal User` |  |
| `customer_numbers` | Customer Numbers | Table → `Customer Number At Supplier` | — Account / customer numbers assigned to your companies by this supplier (for reconciliation on their statements |
| `tax_withholding_group` | Tax Withholding Group | Link → `Tax Withholding Group` | — Used to pick the correct rate row inside the Tax Withholding Category for this supplier (e.g. Company vs Indiv |
| `gender` | Gender | Link → `Gender` |  |
| `alias` | Alias | Text |  |

## Supplier Quotation

*Supplier Quotation* — `buying/supplier_quotation.yaml` · soumis

- **Numérotation** : série `SQ-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `title`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text |  |
| `naming_series` | Series | Select — PUR-SQTN-.YYYY.- | **requis** |
| `supplier` | Supplier | Link → `Supplier` | **requis** |
| `supplier_name` | Supplier Name | Text | lecture seule; recopié de `supplier.supplier_name` |
| `transaction_date` | Date | Date | **requis**; colonne de liste; défaut `today` |
| `company` | Company | Link → `Company` | **requis** |
| `supplier_address` | Supplier Address | Link → `Address` |  |
| `contact_person` | Contact Person | Link → `Contact` |  |
| `address_display` | Address | TextEditor | lecture seule |
| `contact_display` | Contact | LongText | lecture seule |
| `contact_mobile` | Mobile No | LongText | lecture seule |
| `contact_email` | Contact Email | Text | lecture seule |
| `currency` | Currency | Link → `Currency` | **requis** |
| `conversion_rate` | Exchange Rate | Number | **requis** |
| `buying_price_list` | Price List | Link → `Price List` |  |
| `price_list_currency` | Price List Currency | Link → `Currency` | lecture seule |
| `plc_conversion_rate` | Price List Exchange Rate | Number |  |
| `ignore_pricing_rule` | Ignore Pricing Rule | Boolean | défaut `non` |
| `items` | Items | Table → `Supplier Quotation Item` |  |
| `pricing_rules` | Pricing Rule Detail | Table → `Pricing Rule Detail` | lecture seule |
| `total_qty` | Total Quantity | Decimal | lecture seule |
| `base_total` | Total (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_net_total` | Net Total (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `total` | Total | Currency | lecture seule; devise de `currency` |
| `net_total` | Net Total | Currency | lecture seule; devise de `currency` |
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
| `base_grand_total` | Grand Total (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_rounding_adjustment` | Rounding Adjustment (Company Currency | Currency | lecture seule; devise de `company.default_currency` |
| `base_in_words` | In Words (Company Currency) | Text | lecture seule |
| `base_rounded_total` | Rounded Total (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `grand_total` | Grand Total | Currency | colonne de liste; lecture seule; devise de `currency` |
| `rounding_adjustment` | Rounding Adjustment | Currency | lecture seule; devise de `currency` |
| `rounded_total` | Rounded Total | Currency | lecture seule; devise de `currency` |
| `in_words` | In Words | Text | lecture seule |
| `disable_rounded_total` | Disable Rounded Total | Boolean | défaut `non` |
| `tc_name` | Terms Template | Link → `Terms and Conditions` |  |
| `terms` | Terms and Conditions | TextEditor |  |
| `select_print_heading` | Print Heading | Link → `Print Heading` |  |
| `group_same_items` | Group same items | Boolean | défaut `non` |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `language` | Print Language | Text | lecture seule |
| `auto_repeat` | Auto Repeat | Link → `Auto Repeat` | lecture seule |
| `status` | Status | Select — Draft · Submitted · Partially Ordered · Ordered · Stopped · Cancelled · Expired | **requis**; lecture seule |
| `is_subcontracted` | Is Subcontracted | Boolean | défaut `non` |
| `opportunity` | Opportunity | Link → `Opportunity` | lecture seule |
| `valid_till` | Valid Till | Date | colonne de liste |
| `quotation_number` | Quotation Number | Text |  |
| `incoterm` | Incoterm | Link → `Incoterm` |  |
| `named_place` | Named Place | Text |  |
| `shipping_address` | Shipping Address | Link → `Address` |  |
| `shipping_address_display` | Shipping Address Details | TextEditor | lecture seule |
| `billing_address` | Company Billing Address | Link → `Address` |  |
| `billing_address_display` | Billing Address Details | TextEditor | lecture seule |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |
| `has_unit_price_items` | Has Unit Price Items | Boolean | masqué; défaut `non` |
| `item_wise_tax_details` | Item Wise Tax Details | Table → `Item Wise Tax Detail` | masqué |

## Supplier Quotation Item

*Supplier Quotation Item* — `buying/supplier_quotation_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `supplier_part_no` | Supplier Part Number | Text | lecture seule; masqué |
| `item_name` | Item Name | Text | recopié de `item_code.item_name` |
| `lead_time_days` | Supplier Lead Time (days) | Int |  |
| `description` | Description | TextEditor |  |
| `qty` | Quantity | Decimal | **requis**; colonne de liste |
| `stock_uom` | Stock UOM | Link → `UOM` | **requis**; lecture seule |
| `price_list_rate` | Price List Rate | Currency | devise de `parent_currency` |
| `discount_percentage` | Discount on Price List Rate (%) | Percent |  |
| `discount_amount` | Discount Amount | Currency | devise de `parent_currency` |
| `uom` | UOM | Link → `UOM` | **requis**; colonne de liste |
| `conversion_factor` | UOM Conversion Factor | Number | **requis**; lecture seule |
| `stock_qty` | Qty as per Stock UOM | Decimal | lecture seule |
| `ordered_qty` | Ordered Qty | Decimal | **requis**; lecture seule; masqué |
| `base_price_list_rate` | Price List Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `rate` | Rate | Currency | colonne de liste; devise de `parent_currency` |
| `amount` | Amount | Currency | colonne de liste; lecture seule; devise de `parent_currency` |
| `base_rate` | Rate (Company Currency) | Currency | **requis**; lecture seule; devise de `parent_company.default_currency` |
| `base_amount` | Amount (Company Currency) | Currency | **requis**; lecture seule; devise de `parent_company.default_currency` |
| `pricing_rules` | Pricing Rules | LongText | lecture seule; masqué |
| `net_rate` | Net Rate | Currency | lecture seule; devise de `parent_currency` |
| `net_amount` | Net Amount | Currency | lecture seule; devise de `parent_currency` |
| `base_net_rate` | Net Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_net_amount` | Net Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `weight_per_unit` | Weight Per Unit | Number | lecture seule |
| `total_weight` | Total Weight | Number | lecture seule |
| `weight_uom` | Weight UOM | Link → `UOM` | lecture seule |
| `warehouse` | Warehouse | Link → `Warehouse` | colonne de liste |
| `project` | Project | Link → `Project` |  |
| `prevdoc_doctype` | Reference Document Type | Text | lecture seule; masqué |
| `material_request` | Material Request | Link → `Material Request` | lecture seule |
| `sales_order` | Sales Order | Link → `Sales Order` | lecture seule |
| `request_for_quotation` | Request for Quotation | Link → `Request for Quotation` | lecture seule |
| `item_tax_template` | Item Tax Template | Link → `Item Tax Template` |  |
| `material_request_item` | Material Request Item | Text | lecture seule; masqué |
| `request_for_quotation_item` | Request for Quotation Item | Text | lecture seule; masqué |
| `brand` | Brand | Link → `Brand` | lecture seule |
| `item_group` | Item Group | Link → `Item Group` | lecture seule |
| `item_tax_rate` | Item Tax Rate | Code | lecture seule; masqué; — Tax detail table fetched from item master as a string and stored in this field. Used for Taxes and Charges |
| `page_break` | Page Break | Boolean | défaut `non` |
| `manufacturer` | Manufacturer | Link → `Manufacturer` |  |
| `manufacturer_part_no` | Manufacturer Part Number | Text |  |
| `is_free_item` | Is Free Item | Boolean | lecture seule |
| `expected_delivery_date` | Expected Delivery Date | Date |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `distributed_discount_amount` | Distributed Discount Amount | Currency | devise de `parent_currency` |
| `mapped_additional_discount_amount` | Additional Discount per Stock Unit | Currency | lecture seule; devise de `parent_currency`; — Tax-exclusive additional discount carried from a source document, per stock unit. |
| `margin_type` | Margin Type | Select — Percentage · Amount |  |
| `margin_rate_or_amount` | Margin Rate or Amount | Number |  |
| `rate_with_margin` | Rate With Margin | Currency | lecture seule; devise de `parent_currency` |

## Supplier Scorecard

*Supplier Scorecard* — `buying/supplier_scorecard.yaml`

- **Titre** : `period`
- **Icône** : `award`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `supplier` | Supplier | Link → `Supplier` |  |
| `supplier_score` | Supplier Score | Text | lecture seule |
| `indicator_color` | Indicator Color | Text | masqué |
| `status` | Status | Text | masqué |
| `period` | Evaluation Period | Select — Per Week · Per Month · Per Year | **requis**; colonne de liste; défaut `Per Month` |
| `weighting_function` | Weighting Function | LongText | **requis**; défaut `{total_score} * max( 0, min ( 1 , (12 - {period_number}) / 12) )`; — Scorecard variables can be used, as well as: {total_score} (the total score from that period), {period_number} |
| `standings` | Scoring Standings | Table → `Supplier Scorecard Scoring Standing` |  |
| `criteria` | Scoring Criteria | Table → `Supplier Scorecard Scoring Criteria` |  |
| `warn_rfqs` | Warn for new Request for Quotations | Boolean | lecture seule |
| `warn_pos` | Warn for new Purchase Orders | Boolean | lecture seule |
| `prevent_rfqs` | Prevent RFQs | Boolean | lecture seule |
| `prevent_pos` | Prevent POs | Boolean | lecture seule |
| `notify_supplier` | Notify Supplier | Boolean | lecture seule; masqué |
| `notify_employee` | Notify Employee | Boolean | lecture seule; masqué |
| `employee` | Employee | Link → `Employee` | lecture seule; masqué |

## Supplier Scorecard Criteria

*Supplier Scorecard Criteria* — `buying/supplier_scorecard_criteria.yaml`

- **Titre** : `criteria_name`
- **Icône** : `list-checks`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `criteria_name` | Criteria Name | Text | **requis** |
| `max_score` | Max Score | Number | **requis**; colonne de liste; défaut `100.0` |
| `formula` | Criteria Formula | LongText | **requis**; colonne de liste |
| `weight` | Criteria Weight | Percent |  |

## Supplier Scorecard Period

*Supplier Scorecard Period* — `buying/supplier_scorecard_period.yaml` · soumis

- **Numérotation** : série `SSP-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `supplier`
- **Icône** : `calendar-range`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `supplier` | Supplier | Link → `Supplier` | **requis**; colonne de liste; lecture seule |
| `naming_series` | Naming Series | Select — PU-SSP-.YYYY.- | **requis** |
| `total_score` | Period Score | Percent | colonne de liste; lecture seule |
| `start_date` | Start Date | Date | **requis**; colonne de liste |
| `end_date` | End Date | Date | **requis** |
| `criteria` | Criteria | Table → `Supplier Scorecard Scoring Criteria` |  |
| `variables` | Variables | Table → `Supplier Scorecard Scoring Variable` |  |
| `scorecard` | Supplier Scorecard Setup | Link → `Supplier Scorecard` | **requis** |

## Supplier Scorecard Scoring Criteria

*Supplier Scorecard Scoring Criteria* — `buying/supplier_scorecard_scoring_criteria.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `criteria_name` | Criteria Name | Link → `Supplier Scorecard Criteria` | **requis**; colonne de liste |
| `score` | Score | Percent | colonne de liste; lecture seule; masqué |
| `weight` | Criteria Weight | Percent | **requis**; colonne de liste |
| `max_score` | Max Score | Number | lecture seule; masqué |
| `formula` | Criteria Formula | LongText | lecture seule; masqué |

## Supplier Scorecard Scoring Standing

*Supplier Scorecard Scoring Standing* — `buying/supplier_scorecard_scoring_standing.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `standing_name` | Standing Name | Link → `Supplier Scorecard Standing` | colonne de liste |
| `standing_color` | Color | Select — Blue · Purple · Green · Yellow · Orange · Red |  |
| `min_grade` | Min Grade | Percent | colonne de liste |
| `max_grade` | Max Grade | Percent | colonne de liste |
| `warn_rfqs` | Warn RFQs | Boolean | défaut `non` |
| `warn_pos` | Warn Purchase Orders | Boolean | défaut `non` |
| `prevent_rfqs` | Prevent RFQs | Boolean | défaut `non` |
| `prevent_pos` | Prevent Purchase Orders | Boolean | défaut `non` |
| `notify_supplier` | Notify Supplier | Boolean | masqué; défaut `non` |
| `notify_employee` | Notify Employee | Boolean | masqué; défaut `non` |
| `employee_link` | Employee  | Link → `Employee` | masqué |

## Supplier Scorecard Scoring Variable

*Supplier Scorecard Scoring Variable* — `buying/supplier_scorecard_scoring_variable.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `variable_label` | Variable Name | Link → `Supplier Scorecard Variable` | **requis**; colonne de liste; lecture seule |
| `description` | Description | LongText | lecture seule |
| `value` | Value | Number | colonne de liste; lecture seule |
| `param_name` | Parameter Name | Text | lecture seule; masqué |
| `path` | Path | Text | lecture seule; masqué |

## Supplier Scorecard Standing

*Supplier Scorecard Standing* — `buying/supplier_scorecard_standing.yaml`

- **Icône** : `podium`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `standing_name` | Standing Name | Text |  |
| `standing_color` | Color | Select — Blue · Purple · Green · Yellow · Orange · Red |  |
| `min_grade` | Min Grade | Percent |  |
| `max_grade` | Max Grade | Percent |  |
| `warn_rfqs` | Warn RFQs | Boolean | défaut `non` |
| `warn_pos` | Warn Purchase Orders | Boolean | défaut `non` |
| `prevent_rfqs` | Prevent RFQs | Boolean | défaut `non` |
| `prevent_pos` | Prevent Purchase Orders | Boolean | défaut `non` |
| `notify_supplier` | Notify Supplier | Boolean | masqué; défaut `non` |
| `notify_employee` | Notify Other | Boolean | masqué; défaut `non` |
| `employee_link` | Other | Link → `Employee` | masqué |

## Supplier Scorecard Variable

*Supplier Scorecard Variable* — `buying/supplier_scorecard_variable.yaml`

- **Titre** : `param_name`
- **Icône** : `variable`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `variable_label` | Variable Name | Text | **requis** |
| `is_custom` | Custom? | Boolean | défaut `non` |
| `param_name` | Parameter Name | Text | **requis**; colonne de liste |
| `path` | Path | Text | **requis** |
| `description` | Description | LongText |  |
