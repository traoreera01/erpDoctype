# Référence des champs — Ventes (`selling`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `selling/` (20 DocTypes). Ne pas éditer à la main : relancer le script.

529 champs au total ; types les plus fréquents : `Link` (152), `Currency` (78), `Boolean` (65), `Text` (56), `Decimal` (29).

## Customer

*Customer* — `selling/customer.yaml`

- **Titre** : `customer_name`
- **Icône** : `user-round`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — CUST-.YYYY.- |  |
| `customer_name` | Customer Name | Text | **requis** |
| `gender` | Gender | Link → `Gender` | visible si `customer_type == 'Individual'` |
| `customer_type` | Customer Type | Select — Company · Individual · Partnership | **requis**; colonne de liste; défaut `Company` |
| `default_bank_account` | Company Bank Account | Link → `Bank Account` | — Pre-filled on payment entries for this customer. Must be a company account. |
| `lead_name` | Lead | Link → `Lead` | lecture seule |
| `image` | Image | Image | masqué |
| `account_manager` | Account Manager | Text |  |
| `customer_group` | Customer Group | Link → `Customer Group` | colonne de liste |
| `territory` | Territory | Link → `Territory` | colonne de liste |
| `tax_id` | Tax ID | Text |  |
| `tax_category` | Tax Category | Link → `Tax Category` | — Controls which tax template is auto-applied when this customer is selected on a transaction. |
| `disabled` | Disabled | Boolean | défaut `non`; — Blocks this customer from being used on any new transaction. |
| `is_internal_customer` | Is Internal Customer | Boolean | défaut `non`; — Mark if this customer represents an internal company. Enables inter-company transactions. |
| `represents_company` | Represents Company | Link → `Company` | visible si `is_internal_customer`; obligatoire si `is_internal_customer`; — Select the related company that this Customer represents for inter-company transactions. |
| `companies` | Allowed to transact with | Table → `Allowed To Transact With` |  |
| `default_currency` | Billing Currency | Link → `Currency` | colonne de liste; — All invoices and orders for this customer will be created in this currency. |
| `default_price_list` | Price List | Link → `Price List` | — Fetched automatically on sales orders and invoices for this customer. |
| `language` | Print Language | Link → `Language` |  |
| `website` | Website | Text |  |
| `customer_primary_contact` | Customer Primary Contact | Link → `Contact` | masqué; — Reselect, if the chosen contact is edited after save |
| `mobile_no` | Mobile No | Text | lecture seule; masqué |
| `email_id` | Email Id | Text | lecture seule; masqué |
| `customer_primary_address` | Customer Primary Address | Link → `Address` | masqué; — Reselect, if the chosen address is edited after save |
| `primary_address` | Primary Address | TextEditor | lecture seule; masqué |
| `accounts` | Default Accounts | Table → `Party Account` | — If set, accounting entries for this customer will post to these accounts instead of the company default. |
| `payment_terms` | Payment Terms Template | Link → `Payment Terms Template` | — Defines when payment is due (e.g. Net 30, 50% advance). Applied automatically on invoices for this customer. |
| `customer_details` | Customer Details | LongText | — Internal notes about this customer. Not visible on transactions or the portal. |
| `market_segment` | Market Segment | Link → `Market Segment` | — Classify the type of market this customer belongs to, used for sales analysis and targeting. |
| `industry` | Industry | Link → `Industry Type` |  |
| `is_frozen` | Is Frozen | Boolean | défaut `non`; — Blocks new transactions and further accounting entries on this customer's account. Only users with the role se |
| `on_hold` | Block Customer | Boolean | défaut `non`; — Blocks saving or submitting Sales Orders, Delivery Notes, Sales Invoices and POS Invoices for this customer. |
| `release_date` | Release Date | Date | visible si `on_hold`; — Leave blank if the Customer is blocked indefinitely |
| `loyalty_program` | Loyalty Program | Link → `Loyalty Program` | — Loyalty scheme this customer earns points under. Auto-assigned if a matching program exists. |
| `loyalty_program_tier` | Loyalty Program Tier | Text | lecture seule; — Current tier based on accumulated points. Updated automatically on each invoice. |
| `default_sales_partner` | Sales Partner | Link → `Sales Partner` |  |
| `default_commission_rate` | Commission Rate | Number |  |
| `sales_team` | Sales Team | Table → `Sales Team` | — Split commission credit across multiple sales persons. |
| `customer_pos_id` | Customer POS ID | Text | lecture seule |
| `credit_limits` | Credit & Overdue Limits | Table → `Customer Credit Limit` | — Transactions are blocked when the outstanding balance exceeds the credit limit. When Restrict Customer Over Bi |
| `so_required` | Allow sales invoice creation without sales order | Boolean | défaut `non` |
| `dn_required` | Allow sales invoice creation without delivery note | Boolean | défaut `non` |
| `tax_withholding_category` | Tax Withholding Category | Link → `Tax Withholding Category` | — TDS/TCS is calculated at the rate defined here on every payment from this customer. |
| `opportunity_name` | Opportunity | Link → `Opportunity` | lecture seule |
| `restrict_to_companies` | Restrict to Companies | Boolean | défaut `non`; — If checked, this Customer is only available for transactions in the companies listed below. |
| `allowed_companies` | Allowed Companies | Table → `Company Restriction` |  |
| `portal_users` | Customer Portal Users | Table → `Portal User` |  |
| `prospect_name` | Prospect | Link → `Prospect` | lecture seule |
| `first_name` | First Name | Text | lecture seule; masqué |
| `last_name` | Last Name | Text | lecture seule; masqué |
| `supplier_numbers` | Supplier Numbers | Table → `Supplier Number At Customer` | — Numbers this customer uses to identify your company in their own system. |
| `tax_withholding_group` | Tax Withholding Group | Link → `Tax Withholding Group` | — Select the group first to filter the applicable withholding categories below. |
| `alias` | Alias | Text |  |

## Customer Credit Limit

*Customer Credit Limit* — `selling/customer_credit_limit.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `credit_limit` | Credit Limit | Currency | colonne de liste; devise de `company.default_currency` |
| `overdue_billing_threshold` | Overdue Limit | Currency | colonne de liste; masqué; devise de `company.default_currency`; — New Sales Invoices are blocked when the customer's overdue amount exceeds this. Requires 'Restrict Customer Ov |
| `company` | Company | Link → `Company` | colonne de liste |
| `bypass_credit_limit_check` | Bypass credit limit check at sales order | Boolean | colonne de liste; défaut `non` |

## Delivery Schedule Item

*Delivery Schedule Item* — `selling/delivery_schedule_item.yaml`

- **Vues** : calendar
- **Titre** : `item_code`
- **Icône** : `file`
- **Permissions explicites** — `write` : 0, `create` : 0, `delete` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | lecture seule |
| `qty` | Qty | Decimal | colonne de liste; lecture seule |
| `conversion_factor` | Conversion Factor | Number | lecture seule |
| `stock_qty` | Stock Qty | Decimal | lecture seule |
| `delivery_date` | Delivery Date | Date | colonne de liste; lecture seule |
| `sales_order` | Sales Order | Link → `Sales Order` | lecture seule |
| `sales_order_item` | Sales Order Item | Text | lecture seule |
| `warehouse` | Warehouse | Link → `Warehouse` | lecture seule |
| `uom` | UOM | Link → `UOM` | colonne de liste; lecture seule |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |

## Industry Type

*Industry Type* — `selling/industry_type.yaml`

- **Titre** : `industry`
- **Icône** : `factory`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `industry` | Industry | Text | **requis**; colonne de liste |

## Installation Note

*Installation Note* — `selling/installation_note.yaml` · soumis

- **Numérotation** : série `IN-{YYYY}-{#####}`
- **Titre** : `customer_name`
- **Icône** : `wrench`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — MAT-INS-.YYYY.- | **requis** |
| `customer` | Customer | Link → `Customer` | **requis** |
| `customer_address` | Customer Address | Link → `Address` |  |
| `contact_person` | Contact Person | Link → `Contact` |  |
| `customer_name` | Name | Text | lecture seule; recopié de `customer.customer_name` |
| `address_display` | Address | TextEditor | lecture seule; masqué |
| `contact_display` | Contact | LongText | lecture seule; masqué |
| `contact_mobile` | Mobile No | LongText | lecture seule |
| `contact_email` | Contact Email | Text | lecture seule |
| `territory` | Territory | Link → `Territory` | **requis** |
| `customer_group` | Customer Group | Link → `Customer Group` |  |
| `inst_date` | Installation Date | Date | **requis** |
| `inst_time` | Installation Time | Time |  |
| `status` | Status | Select — Draft · Submitted · Cancelled | **requis**; lecture seule; défaut `Draft` |
| `company` | Company | Link → `Company` | **requis** |
| `remarks` | Remarks | LongText | colonne de liste |
| `items` | Items | Table → `Installation Note Item` |  |
| `project` | Project | Link → `Project` |  |

## Installation Note Item

*Installation Note Item* — `selling/installation_note_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `serial_no` | Serial No | LongText |  |
| `qty` | Installed Qty | Decimal | **requis**; colonne de liste |
| `description` | Description | TextEditor | colonne de liste; lecture seule |
| `prevdoc_detail_docname` | Against Document Detail No | Text | lecture seule; masqué |
| `prevdoc_docname` | Against Document No | Text | lecture seule; masqué |
| `prevdoc_doctype` | Document Type | Text | lecture seule; masqué |
| `serial_and_batch_bundle` | Serial and Batch Bundle | Link → `Serial and Batch Bundle` |  |

## Party Specific Item

*Party Specific Item* — `selling/party_specific_item.yaml`

- **Titre** : `party_type`
- **Icône** : `package`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `party_type` | Party Type | Select — Customer · Customer Group · Supplier · Supplier Group | **requis**; colonne de liste |
| `party` | Party Name | DynamicLink → `party_type` | colonne de liste |
| `restrict_based_on` | Restrict Items Based On | Select — Item · Item Group · Brand | **requis**; colonne de liste |
| `based_on_value` | Based On Value | DynamicLink → `restrict_based_on` | colonne de liste |

## Product Bundle

*Product Bundle* — `selling/product_bundle.yaml` · soumis

- **Numérotation** : série `PB-{YYYY}-{#####}`
- **Titre** : `new_item_code`
- **Icône** : `boxes`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `new_item_code` | Parent Item | Link → `Item` | **requis**; colonne de liste |
| `description` | Description | Text | colonne de liste |
| `items` | Items | Table → `Product Bundle Item` |  |
| `is_active` | Is Active | Boolean | colonne de liste; défaut `oui`; — Only one version of a Product Bundle can be active at a time for a given Parent Item. Activating a version dea |
| `disabled` | Disabled | Boolean | défaut `non`; — A disabled Product Bundle cannot be selected in transactions. |

## Product Bundle Item

*Product Bundle Item* — `selling/product_bundle_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item | Link → `Item` | **requis**; colonne de liste |
| `qty` | Qty | Decimal | **requis**; colonne de liste |
| `description` | Description | TextEditor | colonne de liste |
| `rate` | Rate | Number | masqué |
| `uom` | UOM | Link → `UOM` | colonne de liste; lecture seule |

## Proforma Invoice

*Proforma Invoice* — `selling/proforma_invoice.yaml` · soumis

- **Numérotation** : série `PRIN-{YYYY}-{#####}`
- **Titre** : `customer_name`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — PRO-.YYYY.- | **requis** |
| `sales_order` | Sales Order | Link → `Sales Order` | **requis**; colonne de liste; lecture seule |
| `customer` | Customer | Link → `Customer` | colonne de liste; lecture seule |
| `customer_name` | Customer Name | Text | lecture seule; recopié de `customer.customer_name` |
| `proforma_date` | Date | Date | **requis**; colonne de liste; défaut `today` |
| `company` | Company | Link → `Company` | **requis**; lecture seule |
| `currency` | Currency | Link → `Currency` | lecture seule |
| `based_on` | Based On | Select — Quantity · Amount | lecture seule; défaut `Quantity` |
| `hide_item_qty` | Hide Item Quantity in Print | Boolean | lecture seule; — Hide the item quantity and rate on the printed proforma. |
| `items` | Items | Table → `Proforma Invoice Item` |  |
| `total_qty` | Total Quantity | Decimal | lecture seule |
| `grand_total` | Grand Total | Currency | colonne de liste; lecture seule; devise de `currency` |
| `print_format` | Print Format | Link → `Print Format` | lecture seule |
| `letter_head` | Letter Head | Link → `Letter Head` | lecture seule |
| `proforma_pdf` | Proforma PDF | Attach | lecture seule |
| `status` | Status | Select — Draft · Issued · Cancelled | colonne de liste; lecture seule; défaut `Draft` |
| `sent_on` | Sent On | Datetime | lecture seule |
| `emailed_to` | Emailed To | LongText | lecture seule |

## Proforma Invoice Item

*Proforma Invoice Item* — `selling/proforma_invoice_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Item Name | Text | colonne de liste; lecture seule; recopié de `item_code.item_name` |
| `description` | Description | TextEditor |  |
| `qty` | Quantity | Decimal | **requis**; colonne de liste |
| `uom` | UOM | Link → `UOM` | lecture seule |
| `rate` | Rate | Currency | colonne de liste; lecture seule; devise de `parent_currency` |
| `amount` | Amount | Currency | colonne de liste; lecture seule; devise de `parent_currency` |
| `so_detail` | Sales Order Item | Text | lecture seule |

## Quotation

*Quotation* — `selling/quotation.yaml` · soumis

- **Numérotation** : série `QUOT-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `title`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — SAL-QTN-.YYYY.- | **requis** |
| `quotation_to` | Quotation To | Text | **requis** |
| `party_name` | Party | DynamicLink → `quotation_to` |  |
| `customer_name` | Customer Name | Text | lecture seule; masqué |
| `revision_of` | Revision Of | Link → `Quotation` | lecture seule |
| `is_latest_revision` | Is Latest Revision | Boolean | lecture seule; masqué |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `transaction_date` | Date | Date | **requis**; colonne de liste; défaut `today` |
| `valid_till` | Valid Till | Date |  |
| `is_active` | Is Active | Boolean | défaut `oui` |
| `order_type` | Order Type | Select — Sales · Maintenance · Shopping Cart | **requis**; défaut `Sales` |
| `customer_address` | Customer Address | Link → `Address` |  |
| `address_display` | Address | TextEditor | lecture seule |
| `contact_person` | Contact Person | Link → `Contact` |  |
| `contact_display` | Contact | LongText | lecture seule |
| `contact_mobile` | Mobile No | LongText | lecture seule |
| `contact_email` | Contact Email | Text | lecture seule; masqué |
| `shipping_address_name` | Shipping Address | Link → `Address` |  |
| `shipping_address` | Shipping Address | TextEditor | lecture seule |
| `customer_group` | Customer Group | Link → `Customer Group` | masqué |
| `territory` | Territory | Link → `Territory` |  |
| `currency` | Currency | Link → `Currency` | **requis** |
| `conversion_rate` | Exchange Rate | Number | **requis**; — Rate at which customer's currency is converted to company's base currency |
| `selling_price_list` | Price List | Link → `Price List` | **requis** |
| `price_list_currency` | Price List Currency | Link → `Currency` | **requis**; lecture seule |
| `plc_conversion_rate` | Price List Exchange Rate | Number | **requis**; — Rate at which Price list currency is converted to company's base currency |
| `ignore_pricing_rule` | Ignore Pricing Rule | Boolean | défaut `non` |
| `items` | Items | Table → `Quotation Item` |  |
| `pricing_rules` | Pricing Rule Detail | Table → `Pricing Rule Detail` | lecture seule |
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
| `coupon_code` | Coupon Code | Link → `Coupon Code` |  |
| `referral_sales_partner` | Referral Sales Partner | Link → `Sales Partner` |  |
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
| `payment_terms_template` | Payment Terms Template | Link → `Payment Terms Template` |  |
| `payment_schedule` | Payment Schedule | Table → `Payment Schedule` |  |
| `tc_name` | Terms | Link → `Terms and Conditions` |  |
| `terms` | Term Details | TextEditor |  |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `group_same_items` | Group same items | Boolean | défaut `non` |
| `select_print_heading` | Print Heading | Link → `Print Heading` |  |
| `language` | Print Language | Link → `Language` | lecture seule |
| `auto_repeat` | Auto Repeat | Link → `Auto Repeat` | lecture seule |
| `order_lost_reason` | Detailed Reason | LongText |  |
| `status` | Status | Select — Draft · Open · Replied · Partially Ordered · Ordered · Lost · Cancelled · Expired | **requis**; colonne de liste; lecture seule; défaut `Draft` |
| `enq_det` | Opportunity Item | LongText | lecture seule; masqué |
| `supplier_quotation` | Supplier Quotation | Link → `Supplier Quotation` |  |
| `opportunity` | Opportunity | Link → `Opportunity` | lecture seule |
| `lost_reasons` | Lost Reasons | Table → `Quotation Lost Reason Detail` | lecture seule |
| `packed_items` | Bundle Items | Table → `Packed Item` |  |
| `competitors` | Competitors | Table → `Competitor Detail` |  |
| `company_address` | Company Address Name | Link → `Address` |  |
| `company_address_display` | Company Address | TextEditor | lecture seule |
| `scan_barcode` | Scan Barcode | Text |  |
| `incoterm` | Incoterm | Link → `Incoterm` |  |
| `named_place` | Named Place | Text |  |
| `utm_campaign` | Campaign | Link → `UTM Campaign` |  |
| `utm_source` | Source | Link → `UTM Source` |  |
| `utm_medium` | Medium | Link → `UTM Medium` |  |
| `utm_content` | Content | Text |  |
| `disable_rounded_total` | Disable Rounded Total | Boolean | défaut `non` |
| `company_contact_person` | Company Contact Person | Link → `Contact` |  |
| `has_unit_price_items` | Has Unit Price Items | Boolean | masqué; défaut `non` |
| `last_scanned_warehouse` | Last Scanned Warehouse | Text |  |
| `item_wise_tax_details` | Item Wise Tax Details | Table → `Item Wise Tax Detail` | masqué |
| `title` | Title | Text |  |

## Quotation Item

*Quotation Item* — `selling/quotation_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | colonne de liste |
| `is_product_bundle` | Is Product Bundle | Boolean | lecture seule; masqué |
| `product_bundle` | Product Bundle | Link → `Product Bundle` |  |
| `customer_item_code` | Customer's Item Code | Text | lecture seule; masqué |
| `item_name` | Item Name | Text | **requis** |
| `description` | Description | TextEditor |  |
| `qty` | Quantity | Decimal | **requis**; colonne de liste |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `uom` | UOM | Link → `UOM` | **requis** |
| `conversion_factor` | UOM Conversion Factor | Number | **requis**; lecture seule |
| `stock_qty` | Qty as per Stock UOM | Decimal | lecture seule |
| `price_list_rate` | Price List Rate | Currency | lecture seule; devise de `parent_currency` |
| `base_price_list_rate` | Price List Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `margin_type` | Margin Type | Select — Percentage · Amount |  |
| `margin_rate_or_amount` | Margin Rate or Amount | Number |  |
| `rate_with_margin` | Rate With Margin | Currency | lecture seule; devise de `parent_currency` |
| `discount_percentage` | Discount (%) on Price List Rate with Margin | Percent |  |
| `discount_amount` | Discount Amount | Currency | devise de `parent_currency` |
| `base_rate_with_margin` | Rate With Margin (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `rate` | Rate | Currency | colonne de liste; devise de `parent_currency` |
| `net_rate` | Net Rate | Currency | lecture seule; devise de `parent_currency` |
| `amount` | Amount | Currency | colonne de liste; lecture seule; calculé : `qty * rate`; devise de `parent_currency` |
| `net_amount` | Net Amount | Currency | lecture seule; calculé : `amount - discount_amount`; devise de `parent_currency` |
| `base_rate` | Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_net_rate` | Net Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_amount` | Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_net_amount` | Net Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `pricing_rules` | Pricing Rules | LongText | lecture seule; masqué |
| `is_free_item` | Is Free Item | Boolean | lecture seule |
| `weight_per_unit` | Weight Per Unit | Number | lecture seule |
| `total_weight` | Total Weight | Number | lecture seule |
| `weight_uom` | Weight UOM | Link → `UOM` | lecture seule |
| `warehouse` | Warehouse | Link → `Warehouse` |  |
| `projected_qty` | Projected Qty | Decimal | lecture seule |
| `actual_qty` | Qty (Warehouse) | Decimal | lecture seule |
| `prevdoc_doctype` | Against Doctype | Text | lecture seule; masqué |
| `prevdoc_docname` | Against Docname | DynamicLink → `prevdoc_doctype` | lecture seule |
| `item_tax_rate` | Item Tax Rate | Code | lecture seule; masqué |
| `item_tax_template` | Item Tax Template | Link → `Item Tax Template` |  |
| `page_break` | Page Break | Boolean | défaut `non` |
| `item_group` | Item Group | Link → `Item Group` | lecture seule; masqué |
| `brand` | Brand | Link → `Brand` | lecture seule; masqué |
| `additional_notes` | Additional Notes | LongText |  |
| `blanket_order` | Blanket Order | Link → `Blanket Order` |  |
| `blanket_order_rate` | Blanket Order Rate | Currency | lecture seule; devise de `parent_currency` |
| `against_blanket_order` | Against Blanket Order | Boolean | défaut `non` |
| `valuation_rate` | Valuation Rate | Currency | lecture seule; devise de `parent_currency` |
| `gross_profit` | Gross Profit | Currency | lecture seule; devise de `parent_currency` |
| `stock_uom_rate` | Rate of Stock UOM | Currency | lecture seule; devise de `parent_currency` |
| `is_alternative` | Is Alternative | Boolean | défaut `non` |
| `has_alternative_item` | Has Alternative Item | Boolean | lecture seule; masqué |
| `distributed_discount_amount` | Distributed Discount Amount | Currency | devise de `parent_currency` |
| `mapped_additional_discount_amount` | Additional Discount per Stock Unit | Currency | lecture seule; devise de `parent_currency`; — Tax-exclusive additional discount carried from a source document, per stock unit. |
| `company_total_stock` | Qty (Company) | Number | lecture seule |
| `ordered_qty` | Ordered Qty | Decimal | **requis**; lecture seule; masqué |

## Sales Order

*Sales Order* — `selling/sales_order.yaml` · soumis

- **Numérotation** : série `SO-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `title`
- **Icône** : `shopping-cart`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — SAL-ORD-.YYYY.- | **requis** |
| `customer` | Customer | Link → `Customer` | **requis** |
| `customer_name` | Customer Name | Text | lecture seule; recopié de `customer.customer_name` |
| `order_type` | Order Type | Select — Sales · Maintenance · Shopping Cart | **requis**; défaut `Sales` |
| `company` | Company | Link → `Company` | **requis** |
| `transaction_date` | Date | Date | **requis**; défaut `today` |
| `delivery_date` | Delivery Date | Date | colonne de liste |
| `po_no` | Customer's Purchase Order | Text |  |
| `po_date` | Customer's Purchase Order Date | Date |  |
| `tax_id` | Tax Id | Text | lecture seule |
| `customer_address` | Customer Address | Link → `Address` |  |
| `address_display` | Address | TextEditor | lecture seule |
| `contact_person` | Contact Person | Link → `Contact` |  |
| `contact_display` | Contact | LongText | lecture seule |
| `contact_mobile` | Mobile No | LongText | lecture seule |
| `contact_email` | Contact Email | Text | lecture seule; masqué |
| `company_address_display` | Company Address | TextEditor | lecture seule |
| `company_address` | Company Address Name | Link → `Address` |  |
| `shipping_address_name` | Shipping Address Name | Link → `Address` |  |
| `shipping_address` | Shipping Address | TextEditor | lecture seule |
| `shipping_contact_person` | Shipping Contact Person | Link → `Contact` |  |
| `shipping_contact_display` | Shipping Contact | LongText | lecture seule |
| `shipping_contact_mobile` | Shipping Contact Mobile No | LongText | lecture seule |
| `shipping_contact_email` | Shipping Contact Email | Text | lecture seule; masqué |
| `customer_group` | Customer Group | Link → `Customer Group` | masqué |
| `territory` | Territory | Link → `Territory` |  |
| `currency` | Currency | Link → `Currency` | **requis** |
| `conversion_rate` | Exchange Rate | Number | **requis**; — Rate at which customer's currency is converted to company's base currency |
| `selling_price_list` | Price List | Link → `Price List` | **requis** |
| `price_list_currency` | Price List Currency | Link → `Currency` | **requis**; lecture seule |
| `plc_conversion_rate` | Price List Exchange Rate | Number | **requis**; — Rate at which Price list currency is converted to company's base currency |
| `ignore_pricing_rule` | Ignore Pricing Rule | Boolean | défaut `non` |
| `set_warehouse` | Set Source Warehouse | Link → `Warehouse` |  |
| `scan_barcode` | Scan Barcode | Text |  |
| `items` | Items | Table → `Sales Order Item` |  |
| `pricing_rules` | Pricing Rule Detail | Table → `Pricing Rule Detail` | lecture seule |
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
| `loyalty_points` | Loyalty Points | Int | lecture seule; masqué |
| `loyalty_amount` | Loyalty Amount | Currency | lecture seule; masqué; devise de `currency` |
| `coupon_code` | Coupon Code | Link → `Coupon Code` |  |
| `apply_discount_on` | Apply Additional Discount On | Select — Grand Total · Net Total | défaut `Grand Total` |
| `base_discount_amount` | Additional Discount Amount | Currency | lecture seule; devise de `company.default_currency` |
| `additional_discount_percentage` | Additional Discount Percentage | Number |  |
| `discount_amount` | Additional Discount Amount | Currency | devise de `currency`; — Applying a Discount Amount? When this Sales Order is partially fulfilled through multiple Delivery Notes and S |
| `base_grand_total` | Grand Total | Currency | lecture seule; devise de `company.default_currency` |
| `base_rounding_adjustment` | Rounding Adjustment | Currency | lecture seule; devise de `company.default_currency` |
| `base_rounded_total` | Rounded Total | Currency | lecture seule; devise de `company.default_currency` |
| `base_in_words` | In Words | Text | lecture seule; — In Words will be visible once you save the Sales Order. |
| `grand_total` | Grand Total | Currency | colonne de liste; lecture seule; calculé : `total + total_taxes_and_charges`; devise de `currency` |
| `rounding_adjustment` | Rounding Adjustment | Currency | lecture seule; devise de `currency` |
| `rounded_total` | Rounded Total | Currency | lecture seule; devise de `currency` |
| `in_words` | In Words | Text | lecture seule |
| `advance_paid` | Advance Paid | Currency | lecture seule; devise de `party_account_currency` |
| `packed_items` | Packed Items | Table → `Packed Item` |  |
| `payment_terms_template` | Payment Terms Template | Link → `Payment Terms Template` |  |
| `payment_schedule` | Payment Schedule | Table → `Payment Schedule` |  |
| `tc_name` | Terms | Link → `Terms and Conditions` |  |
| `terms` | Terms and Conditions Details | TextEditor |  |
| `inter_company_order_reference` | Inter Company Order Reference | Link → `Purchase Order` | lecture seule |
| `project` | Project | Link → `Project` |  |
| `party_account_currency` | Party Account Currency | Link → `Currency` | lecture seule; masqué |
| `language` | Print Language | Link → `Language` | lecture seule |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `select_print_heading` | Print Heading | Link → `Print Heading` |  |
| `group_same_items` | Group same items | Boolean | défaut `non` |
| `status` | Status | Select — Draft · On Hold · To Pay · To Deliver and Bill · To Bill · To Deliver · Completed · Cancelled · Closed | **requis**; colonne de liste; lecture seule; défaut `Draft` |
| `delivery_status` | Delivery Status | Select — Not Delivered · Fully Delivered · Partly Delivered · Closed · Not Applicable | masqué |
| `per_delivered` | %  Delivered | Percent | colonne de liste; lecture seule; — % of materials delivered against this Sales Order |
| `per_billed` | % Amount Billed | Percent | colonne de liste; lecture seule; — % of materials billed against this Sales Order |
| `billing_status` | Billing Status | Select — Not Billed · Fully Billed · Partly Billed · Closed | masqué |
| `sales_partner` | Sales Partner | Link → `Sales Partner` |  |
| `commission_rate` | Commission Rate | Number |  |
| `total_commission` | Total Commission | Currency | devise de `currency` |
| `sales_team` | Sales Team | Table → `Sales Team` |  |
| `from_date` | From Date | Date |  |
| `to_date` | To Date | Date |  |
| `auto_repeat` | Auto Repeat | Link → `Auto Repeat` |  |
| `contact_phone` | Phone | Text | lecture seule |
| `is_internal_customer` | Is Internal Customer | Boolean | lecture seule |
| `represents_company` | Represents Company | Link → `Company` | lecture seule |
| `disable_rounded_total` | Disable Rounded Total | Boolean | défaut `non` |
| `dispatch_address_name` | Dispatch Address Name | Link → `Address` |  |
| `dispatch_address` | Dispatch Address | TextEditor | lecture seule |
| `amount_eligible_for_commission` | Amount Eligible for Commission | Currency | lecture seule; devise de `currency` |
| `per_picked` | % Picked | Percent | lecture seule |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `incoterm` | Incoterm | Link → `Incoterm` |  |
| `named_place` | Named Place | Text |  |
| `reserve_stock` | Reserve Stock | Boolean | défaut `non`; — If checked, Stock will be reserved on <b>Submit</b> |
| `advance_payment_status` | Advance Payment Status | Select — Not Requested · Requested · Partially Paid · Fully Paid | masqué |
| `utm_medium` | Medium | Link → `UTM Medium` |  |
| `utm_content` | Content | Text |  |
| `utm_source` | Source | Link → `UTM Source` |  |
| `utm_campaign` | Campaign | Link → `UTM Campaign` |  |
| `company_contact_person` | Company Contact Person | Link → `Contact` |  |
| `skip_delivery_note` | Skip Delivery Note | Boolean | lecture seule; masqué |
| `has_unit_price_items` | Has Unit Price Items | Boolean | masqué; défaut `non` |
| `last_scanned_warehouse` | Last Scanned Warehouse | Text |  |
| `is_subcontracted` | Is Subcontracted | Boolean | défaut `non` |
| `item_wise_tax_details` | Item Wise Tax Details | Table → `Item Wise Tax Detail` | masqué |
| `transaction_time` | Time | Time |  |
| `ignore_default_payment_terms_template` | Ignore Default Payment Terms Template | Boolean | lecture seule; masqué |
| `title` | Title | Text |  |

## Sales Order Item

*Sales Order Item* — `selling/sales_order_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `is_product_bundle` | Is Product Bundle | Boolean | lecture seule; masqué |
| `product_bundle` | Product Bundle | Link → `Product Bundle` |  |
| `customer_item_code` | Customer's Item Code | Text | lecture seule; masqué |
| `item_name` | Item Name | Text | recopié de `item_code.item_name` |
| `description` | Description | TextEditor |  |
| `delivery_date` | Delivery Date | Date | colonne de liste |
| `qty` | Quantity | Decimal | **requis**; colonne de liste |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `uom` | UOM | Link → `UOM` | **requis** |
| `conversion_factor` | UOM Conversion Factor | Number | **requis**; lecture seule |
| `stock_qty` | Qty as per Stock UOM | Decimal | lecture seule |
| `price_list_rate` | Price List Rate | Currency | lecture seule; devise de `parent_currency` |
| `base_price_list_rate` | Price List Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `margin_type` | Margin Type | Select — Percentage · Amount |  |
| `margin_rate_or_amount` | Margin Rate or Amount | Number |  |
| `rate_with_margin` | Rate With Margin | Currency | lecture seule; devise de `parent_currency` |
| `discount_percentage` | Discount (%) on Price List Rate with Margin | Percent |  |
| `discount_amount` | Discount Amount | Currency | devise de `parent_currency` |
| `base_rate_with_margin` | Rate With Margin (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `rate` | Rate | Currency | colonne de liste; devise de `parent_currency` |
| `amount` | Amount | Currency | colonne de liste; lecture seule; calculé : `qty * rate`; devise de `parent_currency` |
| `base_rate` | Basic Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_amount` | Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `pricing_rules` | Pricing Rules | LongText | lecture seule; masqué |
| `is_free_item` | Is Free Item | Boolean | lecture seule |
| `net_rate` | Net Rate | Currency | lecture seule; devise de `parent_currency` |
| `net_amount` | Net Amount | Currency | lecture seule; calculé : `amount - discount_amount`; devise de `parent_currency` |
| `base_net_rate` | Net Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_net_amount` | Net Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `delivered_by_supplier` | Supplier delivers to Customer | Boolean | défaut `non` |
| `skip_delivery` | Skip Delivery | Boolean | lecture seule; masqué |
| `supplier` | Supplier | Link → `Supplier` |  |
| `weight_per_unit` | Weight Per Unit | Number |  |
| `total_weight` | Total Weight | Number | lecture seule |
| `weight_uom` | Weight UOM | Link → `UOM` |  |
| `warehouse` | Source Warehouse | Link → `Warehouse` |  |
| `target_warehouse` | Customer Warehouse (Optional) | Link → `Warehouse` | masqué |
| `prevdoc_docname` | Quotation | Link → `Quotation` | lecture seule; cible submitted |
| `brand` | Brand Name | Link → `Brand` | lecture seule; masqué |
| `item_group` | Item Group | Link → `Item Group` | lecture seule; masqué |
| `billed_amt` | Billed Amt | Currency | lecture seule; devise de `parent_currency` |
| `closed` | Closed | Boolean | lecture seule |
| `valuation_rate` | Valuation Rate | Currency | lecture seule; devise de `parent_currency` |
| `gross_profit` | Gross Profit | Currency | lecture seule; devise de `parent_currency` |
| `blanket_order` | Blanket Order | Link → `Blanket Order` |  |
| `blanket_order_rate` | Blanket Order Rate | Currency | lecture seule; devise de `parent_currency` |
| `projected_qty` | Projected Qty | Decimal | lecture seule |
| `actual_qty` | Qty (Warehouse) | Decimal | lecture seule |
| `ordered_qty` | Ordered Qty | Decimal | lecture seule |
| `delivered_qty` | Delivered Qty | Decimal | lecture seule |
| `work_order_qty` | Work Order Qty | Decimal | lecture seule |
| `returned_qty` | Returned Qty | Decimal | lecture seule |
| `item_tax_template` | Item Tax Template | Link → `Item Tax Template` |  |
| `page_break` | Page Break | Boolean | défaut `non` |
| `planned_qty` | Planned Quantity | Decimal | lecture seule; masqué; — For Production |
| `produced_qty` | Produced Quantity | Decimal | lecture seule; masqué; — For Production |
| `item_tax_rate` | Item Tax Rate | Code | lecture seule; masqué |
| `transaction_date` | Sales Order Date | Date | lecture seule; masqué; — Used for Production Plan |
| `additional_notes` | Additional Notes | LongText |  |
| `against_blanket_order` | Against Blanket Order | Boolean | défaut `non` |
| `bom_no` | BOM No | Link → `BOM` |  |
| `stock_uom_rate` | Rate of Stock UOM | Currency | lecture seule; devise de `parent_currency` |
| `grant_commission` | Grant Commission | Boolean | lecture seule |
| `picked_qty` | Picked Qty (in Stock UOM) | Decimal | lecture seule |
| `purchase_order` | Purchase Order | Link → `Purchase Order` | lecture seule |
| `purchase_order_item` | Purchase Order Item | Text | lecture seule |
| `quotation_item` | quotation_item | Text | lecture seule; masqué |
| `material_request` | Material Request | Link → `Material Request` |  |
| `material_request_item` | Material Request Item | Text |  |
| `reserve_stock` | Reserve Stock | Boolean | défaut `oui` |
| `stock_reserved_qty` | Stock Reserved Qty (in Stock UOM) | Decimal | lecture seule |
| `production_plan_qty` | Production Plan Qty | Decimal | lecture seule |
| `is_stock_item` | Is Stock Item | Boolean | masqué; défaut `non` |
| `distributed_discount_amount` | Distributed Discount Amount | Currency | devise de `parent_currency` |
| `mapped_additional_discount_amount` | Additional Discount per Stock Unit | Currency | lecture seule; devise de `parent_currency`; — Tax-exclusive additional discount carried from a source document, per stock unit. |
| `company_total_stock` | Qty (Company) | Number | lecture seule |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |
| `subcontracted_qty` | Subcontracted Quantity | Decimal | lecture seule |
| `fg_item` | Finished Good | Link → `Item` |  |
| `fg_item_qty` | Finished Good Qty | Decimal |  |
| `requested_qty` | Requested Qty | Decimal | lecture seule |

## Sales Partner Type

*Sales Partner Type* — `selling/sales_partner_type.yaml`

- **Titre** : `sales_partner_type`
- **Icône** : `handshake`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `sales_partner_type` | Sales Partner Type | Text | **requis**; colonne de liste |

## Sales Team

*Sales Team* — `selling/sales_team.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `sales_person` | Sales Person | Link → `Sales Person` | **requis**; colonne de liste |
| `contact_no` | Contact No. | Text | colonne de liste; masqué |
| `allocated_percentage` | Contribution (%) | Number | colonne de liste |
| `allocated_amount` | Contribution to Net Total | Currency | colonne de liste; lecture seule |
| `commission_rate` | Commission Rate | Percent | colonne de liste; lecture seule |
| `incentives` | Incentives | Currency | colonne de liste |

## Selling Settings

*Selling Settings* — `selling/selling_settings.yaml` · document unique

- **Titre** : `cust_master_name`
- **Icône** : `settings`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `cust_master_name` | Customer Naming By | Select — Customer Name · Naming Series · Auto Name | colonne de liste; défaut `Customer Name` |
| `customer_group` | Default Customer Group | Link → `Customer Group` | colonne de liste |
| `territory` | Default Territory | Link → `Territory` | colonne de liste |
| `selling_price_list` | Default Price List | Link → `Price List` | colonne de liste |
| `so_required` | Is Sales Order required to create Sales Invoice/Delivery Note? | Select — No · Yes |  |
| `dn_required` | Is Delivery Note required to create Sales Invoice? | Select — No · Yes |  |
| `skip_delivery_note_for_service_items` | Skip Delivery Note Creation for Service Items | Boolean | défaut `non`; — Non-stock items will not require a Delivery Note. Sales Orders will be marked as Completed once all stock item |
| `sales_update_frequency` | How often should sales data be updated in Company/Project? | Select — Monthly · Each Transaction · Daily | **requis**; défaut `Daily`; — The frequency at which project progress and company transaction details will be updated. Set it to daily or mo |
| `maintain_same_sales_rate` | Maintain same rate throughout sales cycle | Boolean | défaut `non`; — Warn or stop if Item rate is changed in Delivery Notes and Sales Invoices generated from a Sales Order. |
| `editable_price_list_rate` | Allow editing Price List rate in transactions | Boolean | défaut `non` |
| `allow_multiple_items` | Allow same Item to be added multiple times in a transaction | Boolean | défaut `non` |
| `allow_against_multiple_purchase_orders` | Allow multiple Sales Orders against a customer's Purchase Order | Boolean | défaut `non` |
| `validate_selling_price` | Validate selling price for Item against purchase or valuation rate | Boolean | défaut `non`; — Enable this to block transactions where the selling price is less than the purchase or valuation rate |
| `hide_tax_id` | Hide Customer's Tax ID from sales transactions | Boolean | défaut `non`; — Most Customers have a unique Tax ID that is fetched into selling transactions. Enable this setting if you do n |
| `maintain_same_rate_action` | Action if same rate is not maintained throughout sales cycle | Select — Stop · Warn | défaut `Stop` |
| `editable_bundle_item_rates` | Calculate Product Bundle price based on child Item's rates | Boolean | défaut `non`; — Enabling this will do the following: <ul style="padding-left:16px"> <li>Make the rate column of all Packed/Bun |
| `enable_discount_accounting` | Enable discount accounting for selling | Boolean | défaut `non`; — If enabled, additional ledger entries will be made for discounts in a separate Discount Account |
| `allow_sales_order_creation_for_expired_quotation` | Allow Sales Order creation for expired Quotation | Boolean | défaut `non`; — This allows creation of sales orders from quotations that have passed their expiration date, providing flexibi |
| `dont_reserve_sales_order_qty_on_sales_return` | Don't reserve Sales Order qty on sales return | Boolean | défaut `non`; — Prevents the automatic reservation of stock quantities from sales orders when processing sales returns. |
| `allow_negative_rates_for_items` | Allow negative rates for Items | Boolean | défaut `non`; — Enable this option to permit the use of negative rates for items in sales transactions. This setting is useful |
| `blanket_order_allowance` | Blanket Order Allowance (%) | Number | — Percentage you are allowed to sell beyond the Blanket Order quantity. |
| `enable_cutoff_date_on_bulk_delivery_note_creation` | Enable cut-off date on creating bulk Delivery Notes | Boolean | défaut `non`; — When enabled, it adds a cutoff date filter to Delivery Notes created in bulk from Sales Orders. This allows yo |
| `allow_zero_qty_in_sales_order` | Allow Sales Order with zero quantity | Boolean | défaut `non` |
| `allow_zero_qty_in_quotation` | Allow Quotation with zero quantity | Boolean | défaut `non` |
| `allow_delivery_of_overproduced_qty` | Allow delivery of overproduced quantity | Boolean | défaut `non`; — If enabled, system will allow user to deliver the entire quantity of the finished goods produced against the S |
| `fallback_to_default_price_list` | Use prices from Default Price List as fallback | Boolean | défaut `non`; — If no Item Price is found for an item in the Price List set in the transaction, prices from the Default Price  |
| `use_legacy_js_reactivity` | Use Legacy (Client side) Reactivity | Boolean | défaut `non` |
| `set_zero_rate_for_expired_batch` | Set incoming rate as zero for expired Batch | Boolean | défaut `non`; — If enabled, system will set incoming rate as zero for stand-alone credit notes with expired batch item. |
| `enable_tracking_sales_commissions` | Enable tracking sales commissions | Boolean | défaut `non`; — Manage sales partner's and sales team's commissions |
| `enable_utm` | Enable UTM | Boolean | défaut `non`; — Enable Urchin Tracking Module parameters in Quotation, Sales Order, Sales Invoice, POS Invoice, Lead,  and Del |
| `deliver_secondary_items` | Deliver secondary Items | Boolean | défaut `non`; — If enabled, the Secondary Items generated against a Finished Good will also be added in the Stock Entry when d |
| `enable_proforma_invoice` | Enable Proforma Invoice | Boolean | défaut `non`; — Allow issuing Proforma Invoices against a Sales Order. |
| `default_proforma_print_format` | Default Proforma Print Format | Link → `Print Format` | — Default print format used when generating a Proforma Invoice PDF. |
| `proforma_email_template` | Proforma Email Template | Link → `Email Template` | — Subject and message used when emailing a Proforma Invoice. The template gets the Proforma Invoice as doc, e.g. |
| `naming_series_details` | Naming Series options | LongText | lecture seule; masqué |

## SMS Center

*SMS Center* — `selling/sms_center.yaml`

- **Titre** : `send_to`
- **Icône** : `message-square`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `send_to` | Send To | Select — All Contact · All Customer Contact · All Supplier Contact · All Sales Partner Contact · All Lead (Open) · All Employee (Active) · All Sales Person | colonne de liste |
| `customer` | Customer | Link → `Customer` | colonne de liste |
| `supplier` | Supplier | Link → `Supplier` | colonne de liste |
| `sales_partner` | Sales Partner | Link → `Sales Partner` |  |
| `department` | Department | Link → `Department` | colonne de liste |
| `branch` | Branch | Link → `Branch` |  |
| `receiver_list` | Receiver List | Code |  |
| `message` | Message | LongText | **requis**; — Messages greater than 160 characters will be split into multiple messages |
| `total_characters` | Total Characters | Int | lecture seule |
| `total_messages` | Total Message(s) | Int | lecture seule |

## Supplier Number At Customer

*Supplier Number At Customer* — `selling/supplier_number_at_customer.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | colonne de liste |
| `supplier_number` | Supplier Number | Text | colonne de liste |
