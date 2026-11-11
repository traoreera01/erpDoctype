# Référence des champs — Configuration (`setup`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `setup/` (53 DocTypes). Ne pas éditer à la main : relancer le script.

492 champs au total ; types les plus fréquents : `Text` (125), `Link` (121), `Boolean` (85), `Select` (33), `Date` (33).

## Address

*Address* — `setup/address.yaml`

- **Titre** : `address_title`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `address_title` | Address Title | Text |  |
| `address_type` | Address Type | Select — Billing · Shipping · Office · Personal · Other |  |
| `address_line1` | Address Line 1 | Text | **requis** |
| `address_line2` | Address Line 2 | Text |  |
| `city` | City | Text |  |
| `state` | State / Province | Text |  |
| `postal_code` | Postal Code | Text |  |
| `country` | Country | Link → `Country` |  |
| `email_id` | Email | Text |  |
| `phone` | Phone | Text |  |
| `is_primary_address` | Primary Address | Boolean |  |
| `is_shipping_address` | Shipping Address | Boolean |  |
| `disabled` | Disabled | Boolean |  |

## Authorization Control

*Authorization Control* — `setup/authorization_control.yaml`

- **Icône** : `shield`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `description` | Description | Text |  |

## Authorization Rule

*Authorization Rule* — `setup/authorization_rule.yaml`

- **Titre** : `transaction`
- **Icône** : `shield-check`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `transaction` | Transaction | Select — Sales Order · Purchase Order · Quotation · Delivery Note · Sales Invoice · Purchase Invoice · Purchase Receipt | **requis**; colonne de liste |
| `based_on` | Based On | Select — Grand Total · Average Discount · Customerwise Discount · Itemwise Discount · Item Group wise Discount · Not Applicable | **requis**; colonne de liste |
| `customer_or_item` | Customer or Item | Select — Customer · Item · Item Group | lecture seule; masqué |
| `master_name` | Customer / Item / Item Group | DynamicLink → `customer_or_item` | colonne de liste |
| `company` | Company | Link → `Company` | colonne de liste |
| `value` | Authorized Value | Number |  |
| `to_emp` | Applicable To (Employee) | Link → `Employee` |  |
| `system_user` | Applicable To (User) | Text |  |
| `to_designation` | Applicable To (Designation) | Link → `Designation` |  |
| `approving_user` | Approving User  (above authorized value) | Text |  |

## Auto Repeat

*Auto Repeat* — `setup/auto_repeat.yaml`

- **Titre** : `reference_doctype`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `reference_doctype` | Reference DocType | Text | **requis** |
| `reference_name` | Reference Name | Text | **requis** |
| `frequency` | Frequency | Select — Daily · Weekly · Monthly · Quarterly · Half-yearly · Yearly |  |
| `start_date` | Start Date | Date | **requis** |
| `end_date` | End Date | Date |  |
| `next_date` | Next Date | Date |  |
| `disabled` | Disabled | Boolean |  |

## Branch

*Branch* — `setup/branch.yaml`

- **Titre** : `branch`
- **Icône** : `store`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `branch` | Branch | Text | **requis**; colonne de liste |

## Brand

*Brand* — `setup/brand.yaml`

- **Titre** : `brand`
- **Icône** : `award`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `brand` | Brand Name | Text | **requis** |
| `description` | Description | LongText | colonne de liste |
| `brand_defaults` | Brand Defaults | Table → `Item Default` |  |
| `image` | Image | Image | masqué |

## Company

*Company* — `setup/company.yaml`

- **Vues** : tree (parent `parent_company`)
- **Titre** : `company_name`
- **Icône** : `building-complex`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company_name` | Company | Text | **requis** |
| `abbr` | Abbr | Text | **requis** |
| `is_group` | Is Group | Boolean | colonne de liste; défaut `non` |
| `default_finance_book` | Default Finance Book | Link → `Finance Book` |  |
| `domain` | Domain | Text |  |
| `parent_company` | Parent Company | Link → `Company` |  |
| `company_logo` | Company Logo | Image | masqué |
| `company_description` | Company Description | TextEditor |  |
| `sales_monthly_history` | Sales Monthly History | LongText | lecture seule; masqué |
| `transactions_annual_history` | Transactions Annual History | Code | lecture seule; masqué |
| `monthly_sales_target` | Monthly Sales Target | Currency | devise de `default_currency` |
| `total_monthly_sales` | Total Monthly Sales | Currency | lecture seule; devise de `default_currency` |
| `default_currency` | Default Currency | Link → `Currency` | **requis**; colonne de liste |
| `default_letter_head` | Default Letter Head (DocType) | Link → `Letter Head` |  |
| `default_holiday_list` | Default Holiday List | Link → `Holiday List` |  |
| `default_warehouse_for_sales_return` | Default Warehouse for Sales Return | Link → `Warehouse` |  |
| `country` | Country | Link → `Country` | **requis**; colonne de liste |
| `create_chart_of_accounts_based_on` | Create Chart Of Accounts Based On | Select — SYSCOHADA révisé · Standard Template · Existing Company | défaut `SYSCOHADA révisé` |
| `existing_company` | Existing Company  | Link → `Company` |  |
| `tax_id` | Tax ID | Text |  |
| `date_of_establishment` | Date of Establishment | Date |  |
| `default_bank_account` | Default Bank Account | Link → `Account` |  |
| `default_cash_account` | Default Cash Account | Link → `Account` |  |
| `default_receivable_account` | Default Receivable Account | Link → `Account` |  |
| `round_off_account` | Round Off Account | Link → `Account` |  |
| `round_off_cost_center` | Round Off Cost Center | Link → `Cost Center` |  |
| `write_off_account` | Write Off Account | Link → `Account` |  |
| `bank_charges_account` | Bank Charges Account | Link → `Account` |  |
| `exchange_gain_loss_account` | Exchange Gain / Loss Account | Link → `Account` |  |
| `exchange_gain_account` | Exchange Gain Account | Link → `Account` |  |
| `exchange_loss_account` | Exchange Loss Account | Link → `Account` |  |
| `unrealized_exchange_gain_loss_account` | Unrealized Exchange Gain/Loss Account | Link → `Account` |  |
| `allow_account_creation_against_child_company` | Allow Account Creation Against Child Company | Boolean | défaut `non` |
| `default_payable_account` | Default Payable Account | Link → `Account` |  |
| `default_expense_account` | Default Cost of Goods Sold Account | Link → `Account` |  |
| `default_income_account` | Default Income Account | Link → `Account` |  |
| `default_deferred_revenue_account` | Default Deferred Revenue Account | Link → `Account` |  |
| `default_deferred_expense_account` | Default Deferred Expense Account | Link → `Account` |  |
| `cost_center` | Default Cost Center | Link → `Cost Center` |  |
| `credit_limit` | Credit Limit | Currency | devise de `default_currency` |
| `payment_terms` | Default Payment Terms Template | Link → `Payment Terms Template` |  |
| `enable_perpetual_inventory` | Enable Perpetual Inventory | Boolean | colonne de liste; défaut `oui` |
| `default_inventory_account` | Default Inventory Account | Link → `Account` |  |
| `stock_adjustment_account` | Stock Adjustment Account | Link → `Account` |  |
| `default_purchase_price_variance_account` | Default Purchase Price Variance Account | Link → `Account` | — Used for items valued at Standard Cost: the difference between the purchase price and the standard rate is boo |
| `default_manufacturing_variance_account` | Default Manufacturing Variance Account | Link → `Account` | — For Standard Cost items: the Manufacture/Repack consumed cost vs standard rate difference is booked here. |
| `stock_received_but_not_billed` | Stock Received But Not Billed | Link → `Account` |  |
| `accumulated_depreciation_account` | Accumulated Depreciation Account | Link → `Account` |  |
| `depreciation_expense_account` | Depreciation Expense Account | Link → `Account` |  |
| `series_for_depreciation_entry` | Series for Asset Depreciation Entry (Journal Entry) | Text |  |
| `disposal_account` | Gain/Loss Account on Asset Disposal | Link → `Account` |  |
| `depreciation_cost_center` | Asset Depreciation Cost Center | Link → `Cost Center` |  |
| `capital_work_in_progress_account` | Capital Work In Progress Account | Link → `Account` |  |
| `asset_received_but_not_billed` | Asset Received But Not Billed | Link → `Account` |  |
| `date_of_incorporation` | Date of Incorporation | Date |  |
| `date_of_commencement` | Date of Commencement | Date |  |
| `phone_no` | Phone No | Text |  |
| `fax` | Fax | Text |  |
| `email` | Email | Text |  |
| `website` | Website | Text |  |
| `registration_details` | Registration Details | Code | — Company registration numbers for your reference. Tax numbers etc. |
| `lft` | Lft | Int | lecture seule; masqué |
| `rgt` | Rgt | Int | lecture seule; masqué |
| `old_parent` | old_parent | Text | lecture seule; masqué |
| `default_selling_terms` | Default Selling Terms | Link → `Terms and Conditions` |  |
| `default_buying_terms` | Default Buying Terms | Link → `Terms and Conditions` |  |
| `default_in_transit_warehouse` | Default In-Transit Warehouse | Link → `Warehouse` |  |
| `default_warehouse` | Default Warehouse | Link → `Warehouse` |  |
| `sample_retention_warehouse` | Sample Retention Warehouse | Link → `Warehouse` |  |
| `unrealized_profit_loss_account` | Unrealized Profit / Loss Account | Link → `Account` |  |
| `default_discount_account` | Default Payment Discount Account | Link → `Account` |  |
| `enable_provisional_accounting_for_non_stock_items` | Enable Provisional Accounting For Non Stock Items | Boolean | défaut `non` |
| `default_provisional_account` | Default Provisional Account | Link → `Account` |  |
| `default_advance_received_account` | Default Advance Received Account | Link → `Account` | — Only 'Payment Entries' made against this advance account are supported. |
| `default_advance_paid_account` | Default Advance Paid Account | Link → `Account` | — Only 'Payment Entries' made against this advance account are supported. |
| `book_advance_payments_in_separate_party_account` | Book Advance Payments in Separate Party Account | Boolean | défaut `non`; — Enabling this option will allow you to record - <br><br> 1. Advances Received in a <b>Liability Account</b> in |
| `auto_exchange_rate_revaluation` | Auto Create Exchange Rate Revaluation | Boolean | défaut `non` |
| `auto_err_frequency` | Frequency | Select — Daily · Weekly · Monthly |  |
| `submit_err_jv` | Submit ERR Journals? | Boolean | défaut `non`; — Upon enabling this, the JV will be submitted for a different exchange rate. |
| `reconcile_on_advance_payment_date` | Reconcile on Advance Payment Date | Boolean | masqué; défaut `non`; — If <b>Enabled</b> - Reconciliation happens on the <b>Advance Payment posting date</b><br> If <b>Disabled</b> - |
| `default_operating_cost_account` | Default Operating Cost Account | Link → `Account` |  |
| `round_off_for_opening` | Round Off for Opening | Link → `Account` |  |
| `reconciliation_takes_effect_on` | Reconciliation Takes Effect On | Select — Advance Payment Date · Oldest Of Invoice Or Advance · Reconciliation Date | défaut `Oldest Of Invoice Or Advance` |
| `reporting_currency` | Reporting Currency | Link → `Currency` | lecture seule |
| `purchase_expense_account` | Purchase Expense Account | Link → `Account` |  |
| `purchase_expense_contra_account` | Purchase Expense Contra Account | Link → `Account` |  |
| `service_expense_account` | Service Expense Account | Link → `Account` | — For service item |
| `expenses_added_to_stock_account` | Expenses Added To Stock Account | Link → `Account` |  |
| `expenses_added_to_stock_contra_account` | Expenses Added To Stock Contra Account | Link → `Account` |  |
| `enable_item_wise_inventory_account` | Enable Item-wise Inventory Account | Boolean | défaut `non`; — If enabled, the system will use the inventory account set in the Item Master or Item Group or Brand. Otherwise |
| `valuation_method` | Default Stock Valuation Method | Select — FIFO · Moving Average · LIFO | **requis**; défaut `FIFO` |
| `default_wip_warehouse` |  Default Work In Progress Warehouse  | Link → `Warehouse` |  |
| `default_fg_warehouse` | Default Finished Goods Warehouse | Link → `Warehouse` |  |
| `default_scrap_warehouse` | Default Scrap Warehouse | Link → `Warehouse` |  |
| `default_sales_contact` | Default Sales Contact | Link → `Contact` |  |
| `accounts_frozen_till_date` | Accounts Frozen Till Date | Date | — Accounting entries are frozen up to this date. Only users with the specified role can create or modify entries |
| `default_letter_head_report` | Default Letter Head (Report) | Link → `Letter Head` |  |
| `disable_sdbnb_in_sr` | Disable Stock Delivered But Not Billed in Sales Return | Boolean | défaut `non` |
| `stock_delivered_but_not_billed` | Stock Delivered But Not Billed | Link → `Account` |  |
| `enable_stock_delivered_but_not_billed` | Enable Stock Delivered But Not Billed | Boolean | défaut `non`; — If enabled, the value of goods delivered before invoicing will be recorded in the Stock Delivered But Not Bill |

## Country

*Pays* — `setup/country.yaml`

- **Numérotation** : nommé par le champ `country_code`
- **Titre** : `country_name`
- **Icône** : `globe`
- **Permissions explicites** — `read` : 1

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `country_code` | Code ISO 3166-1 | Text | **requis**; colonne de liste; — Deux lettres majuscules : CI, FR, SN. C'est le nom du document. |
| `country_name` | Nom | Text | **requis**; colonne de liste |
| `default_currency` | Devise par défaut | Link → `Currency` | colonne de liste |
| `phone_prefix` | Indicatif téléphonique | Text |  |
| `enabled` | Actif | Boolean | colonne de liste; défaut `oui` |

## Currency

*Devise* — `setup/currency.yaml`

- **Numérotation** : nommé par le champ `currency_code`
- **Titre** : `currency_name`
- **Icône** : `dollar`
- **Permissions explicites** — `read` : 1

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `currency_code` | Code ISO 4217 | Text | **requis**; colonne de liste; — Trois lettres majuscules : EUR, XOF, USD. C'est le nom du document. |
| `currency_name` | Nom | Text | **requis**; colonne de liste |
| `symbol` | Symbole | Text | colonne de liste |
| `fraction` | Fraction | Text | — Centime, cent, pesewa… |
| `fraction_units` | Unités par fraction | Int | défaut `100` |
| `enabled` | Active | Boolean | colonne de liste; défaut `oui` |

## Currency Exchange

*Currency Exchange* — `setup/currency_exchange.yaml`

- **Vues** : calendar
- **Titre** : `from_currency`
- **Icône** : `arrow-right-left`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `date` | Date | Date | **requis**; colonne de liste |
| `from_currency` | From Currency | Link → `Currency` | **requis**; colonne de liste |
| `to_currency` | To Currency | Link → `Currency` | **requis**; colonne de liste |
| `exchange_rate` | Exchange Rate | Number | **requis**; colonne de liste |
| `for_buying` | For Buying | Boolean | défaut `oui` |
| `for_selling` | For Selling | Boolean | défaut `oui` |

## Customer Group

*Customer Group* — `setup/customer_group.yaml`

- **Vues** : tree (parent `parent_customer_group`)
- **Titre** : `customer_group_name`
- **Icône** : `users`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `customer_group_name` | Customer Group Name | Text | **requis**; colonne de liste |
| `parent_customer_group` | Parent Customer Group | Link → `Customer Group` | colonne de liste |
| `is_group` | Is Group | Boolean | colonne de liste; défaut `non`; — Only leaf nodes are allowed in transaction |
| `default_price_list` | Default Price List | Link → `Price List` |  |
| `payment_terms` | Default Payment Terms Template | Link → `Payment Terms Template` |  |
| `lft` | lft | Int | masqué |
| `rgt` | rgt | Int | masqué |
| `old_parent` | old_parent | Link → `Customer Group` | masqué |
| `accounts` | Accounts | Table → `Party Account` | — Mention if non-standard receivable account applicable |
| `credit_limits` | Credit & Overdue Limits | Table → `Customer Credit Limit` |  |

## Department

*Department* — `setup/department.yaml`

- **Vues** : tree (parent `parent_department`)
- **Titre** : `department_name`
- **Icône** : `building`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `department_name` | Department | Text | **requis**; colonne de liste |
| `parent_department` | Parent Department | Link → `Department` | colonne de liste |
| `company` | Company | Link → `Company` | **requis** |
| `is_group` | Is Group | Boolean | colonne de liste; défaut `non` |
| `disabled` | Disabled | Boolean | défaut `non` |
| `lft` | lft | Int | lecture seule; masqué |
| `rgt` | rgt | Int | lecture seule; masqué |
| `old_parent` | Old Parent | Text | masqué |

## Designation

*Designation* — `setup/designation.yaml`

- **Titre** : `designation_name`
- **Icône** : `id-card`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `designation_name` | Designation | Text | **requis**; colonne de liste |
| `description` | Description | LongText |  |

## Driver

*Driver* — `setup/driver.yaml`

- **Vues** : kanban
- **Titre** : `status`
- **Icône** : `car`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — HR-DRI-.YYYY.- |  |
| `full_name` | Full Name | Text | **requis**; colonne de liste |
| `status` | Status | Select — Active · Suspended · Left | **requis**; colonne de liste |
| `transporter` | Transporter | Link → `Supplier` | — Applicable for external driver |
| `employee` | Employee | Link → `Employee` | colonne de liste |
| `cell_number` | Cellphone Number | Text |  |
| `license_number` | License Number | Text |  |
| `issuing_date` | Issuing Date | Date |  |
| `expiry_date` | Expiry Date | Date |  |
| `driving_license_category` | Driving License Category | Table → `Driving License Category` |  |
| `address` | Address | Link → `Address` |  |
| `user` | User | Text | colonne de liste |

## Driving License Category

*Driving License Category* — `setup/driving_license_category.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `class` | Driver licence class | Text | colonne de liste |
| `description` | Description | Text | colonne de liste |
| `issuing_date` | Issuing Date | Date | colonne de liste |
| `expiry_date` | Expiry Date | Date | colonne de liste |

## Email Digest

*Email Digest* — `setup/email_digest.yaml`

- **Titre** : `company`
- **Icône** : `mail`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `enabled` | Enabled | Boolean | colonne de liste; défaut `non` |
| `company` | For Company | Link → `Company` | **requis**; colonne de liste |
| `frequency` | How frequently? | Select — Daily · Weekly · Monthly | **requis**; colonne de liste |
| `next_send` | Next email will be sent on: | Text | lecture seule |
| `income` | New Income | Boolean | défaut `non` |
| `expenses_booked` | New Expenses | Boolean | défaut `non` |
| `income_year_to_date` | Annual Income | Boolean | défaut `non` |
| `expense_year_to_date` | Annual Expenses | Boolean | défaut `non` |
| `bank_balance` | Bank Balance | Boolean | défaut `non` |
| `credit_balance` | Bank Credit Balance | Boolean | défaut `non` |
| `invoiced_amount` | Receivables | Boolean | défaut `non` |
| `payables` | Payables | Boolean | défaut `non` |
| `sales_orders_to_bill` | Sales Orders to Bill | Boolean | défaut `non` |
| `purchase_orders_to_bill` | Purchase Orders to Bill | Boolean | défaut `non` |
| `sales_order` | New Sales Orders | Boolean | défaut `non` |
| `purchase_order` | New Purchase Orders | Boolean | défaut `non` |
| `sales_orders_to_deliver` | Sales Orders to Deliver | Boolean | défaut `non` |
| `purchase_orders_to_receive` | Purchase Orders to Receive | Boolean | défaut `non` |
| `sales_invoice` | New Sales Invoice | Boolean | défaut `non` |
| `purchase_invoice` | New Purchase Invoice | Boolean | défaut `non` |
| `new_quotations` | New Quotations | Boolean | défaut `non` |
| `pending_quotations` | Open Quotations | Boolean | défaut `non` |
| `issue` | Open Issues | Boolean | défaut `non` |
| `project` | Open Projects | Boolean | défaut `non` |
| `purchase_orders_items_overdue` | Purchase Orders Items Overdue | Boolean | défaut `non` |
| `calendar_events` | Upcoming Calendar Events | Boolean | défaut `non` |
| `todo_list` | Open To Do | Boolean | défaut `non` |
| `notifications` | Open Notifications | Boolean | défaut `non` |
| `add_quote` | Add Quote | Boolean | défaut `non` |
| `recipients` | Recipients | Table → `Email Digest Recipient` | — Note: Email will not be sent to disabled users |

## Email Digest Recipient

*Email Digest Recipient* — `setup/email_digest_recipient.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `recipient` | Recipient | Text | **requis**; colonne de liste |

## Employee

*Employee* — `setup/employee.yaml`

- **Vues** : kanban, tree (parent `reports_to`)
- **Titre** : `status`
- **Icône** : `user`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Text | masqué |
| `naming_series` | Series | Select — HR-EMP- |  |
| `salutation` | Salutation | Link → `Salutation` |  |
| `first_name` | First Name | Text | **requis** |
| `middle_name` | Middle Name | Text |  |
| `last_name` | Last Name | Text |  |
| `employee_name` | Full Name | Text | colonne de liste; lecture seule |
| `image` | Image | Image | masqué |
| `company` | Company | Link → `Company` | **requis** |
| `status` | Status | Select — Active · Inactive · Suspended · Left | **requis**; défaut `Active` |
| `employee_number` | Employee Number | Text |  |
| `gender` | Gender | Link → `Gender` | **requis** |
| `date_of_birth` | Date of Birth | Date | **requis** |
| `date_of_joining` | Date of Joining | Date | **requis** |
| `emergency_phone_number` | Emergency Phone | Text |  |
| `person_to_be_contacted` | Emergency Contact Name | Text |  |
| `relation` | Relation | Text |  |
| `user_id` | User ID | Text | — System User (login) ID. If set, it will become default for all HR forms. |
| `create_user_permission` | Create User Permission | Boolean | défaut `oui`; — This will restrict user access to other employee records |
| `create_user_automatically` | Create User Automatically | Boolean | défaut `non`; — Creates a User account for this employee using the Preferred, Company, or Personal email. |
| `scheduled_confirmation_date` | Offer Date | Date |  |
| `final_confirmation_date` | Confirmation Date | Date |  |
| `contract_end_date` | Contract End Date | Date |  |
| `notice_number_of_days` | Notice (days) | Int |  |
| `date_of_retirement` | Date Of Retirement | Date |  |
| `department` | Department | Link → `Department` | colonne de liste |
| `designation` | Designation | Link → `Designation` | colonne de liste |
| `reports_to` | Reports to | Link → `Employee` |  |
| `branch` | Branch | Link → `Branch` | colonne de liste |
| `holiday_list` | Holiday List | Link → `Holiday List` | — Applicable Holiday List |
| `salary_mode` | Salary Mode | Select — Bank · Cash · Cheque |  |
| `bank_name` | Bank Name | Text | visible si `salary_mode == 'Bank'` |
| `bank_ac_no` | Bank A/C No. | Text | visible si `salary_mode == 'Bank'` |
| `cell_number` | Mobile | Text |  |
| `prefered_contact_email` | Preferred Contact Email | Select — Company Email · Personal Email · User ID |  |
| `prefered_email` | Preferred Email | Text | lecture seule |
| `company_email` | Company Email | Text | — Provide Email Address registered in company |
| `personal_email` | Personal Email | Text |  |
| `unsubscribed` | Unsubscribed | Boolean | défaut `non` |
| `permanent_accommodation_type` | Permanent Address Is | Select — Rented · Owned |  |
| `permanent_address` | Permanent Address | LongText |  |
| `current_accommodation_type` | Current Address Is | Select — Rented · Owned |  |
| `current_address` | Current Address | LongText |  |
| `bio` | Bio / Cover Letter | TextEditor | — Short biography for website and other publications. |
| `passport_number` | Passport Number | Text |  |
| `date_of_issue` | Date of Issue | Date |  |
| `valid_upto` | Valid Up To | Date |  |
| `place_of_issue` | Place of Issue | Text |  |
| `marital_status` | Marital Status | Select — Single · Married · Divorced · Widowed |  |
| `blood_group` | Blood Group | Select — A+ · A- · B+ · B- · AB+ · AB- · O+ · O- |  |
| `family_background` | Family Background | LongText | — Here you can maintain family details like name and occupation of parent, spouse and children |
| `health_details` | Health Details | LongText | — Here you can maintain height, weight, allergies, medical concerns etc |
| `education` | Education | Table → `Employee Education` |  |
| `external_work_history` | External Work History | Table → `Employee External Work History` |  |
| `internal_work_history` | Internal Work History | Table → `Employee Internal Work History` |  |
| `resignation_letter_date` | Resignation Letter Date | Date | visible si `status == 'Left'` |
| `relieving_date` | Relieving Date | Date | visible si `status == 'Left'`; obligatoire si `status == 'Left'` |
| `reason_for_leaving` | Reason for Leaving | LongText | visible si `status == 'Left'` |
| `leave_encashed` | Leave Encashed? | Select — Yes · No | visible si `status == 'Left'` |
| `encashment_date` | Encashment Date | Date | visible si `status == 'Left'` |
| `held_on` | Exit Interview Held On | Date | visible si `status == 'Left'` |
| `new_workplace` | New Workplace | Text | visible si `status == 'Left'` |
| `feedback` | Feedback | LongText | visible si `status == 'Left'` |
| `lft` | lft | Int | lecture seule; masqué |
| `rgt` | rgt | Int | lecture seule; masqué |
| `old_parent` | Old Parent | Text | masqué |
| `attendance_device_id` | Attendance Device ID (Biometric/RF tag ID) | Text |  |
| `salary_currency` | Salary Currency | Link → `Currency` |  |
| `ctc` | Cost to Company (CTC) | Currency | devise de `salary_currency` |
| `iban` | IBAN | Text | visible si `salary_mode == 'Bank'` |

## Employee Education

*Employee Education* — `setup/employee_education.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `school_univ` | School/University | LongText | colonne de liste |
| `qualification` | Qualification | Text | colonne de liste |
| `level` | Level | Select — Graduate · Post Graduate · Under Graduate | colonne de liste |
| `year_of_passing` | Year of Passing | Int | colonne de liste |
| `class_per` | Class / Percentage | Text | colonne de liste |
| `maj_opt_subj` | Major/Optional Subjects | LongText | colonne de liste |

## Employee External Work History

*Employee External Work History* — `setup/employee_external_work_history.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company_name` | Company | Text | colonne de liste |
| `designation` | Designation | Text | colonne de liste |
| `salary` | Salary | Currency | colonne de liste; devise de `parent_salary_currency` |
| `address` | Address | LongText | colonne de liste |
| `contact` | Contact | Text | colonne de liste |
| `total_experience` | Total Experience | Text | colonne de liste |

## Employee Group

*Employee Group* — `setup/employee_group.yaml`

- **Titre** : `employee_group_name`
- **Icône** : `users`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee_group_name` | Name | Text | **requis**; colonne de liste |
| `employee_list` | Employee | Table → `Employee Group Table` |  |

## Employee Group Table

*Employee Group Table* — `setup/employee_group_table.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | colonne de liste |
| `employee_name` | Employee Name | Text | colonne de liste |
| `user_id` | ERPNext User ID | Text | colonne de liste; lecture seule |

## Employee Internal Work History

*Employee Internal Work History* — `setup/employee_internal_work_history.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `branch` | Branch | Link → `Branch` | colonne de liste |
| `department` | Department | Link → `Department` | colonne de liste |
| `designation` | Designation | Link → `Designation` | colonne de liste |
| `from_date` | From Date | Date | colonne de liste |
| `to_date` | To Date | Date | colonne de liste |

## Error Log

*Error Log* — `setup/error_log.yaml`

- **Titre** : `method`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `method` | Method | Text | colonne de liste |
| `error` | Error | LongText |  |
| `seen` | Seen | Boolean |  |
| `reference_doctype` | Reference DocType | Text |  |
| `reference_name` | Reference Name | Text |  |

## Gender

*Gender* — `setup/gender.yaml`

- **Numérotation** : nommé par le champ `gender`
- **Titre** : `gender`
- **Icône** : `users`
- **Permissions explicites** — `read` : 1

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `gender` | Gender | Text | **requis**; colonne de liste; unique |
| `enabled` | Enabled | Boolean | défaut `oui` |

## Global Defaults

*Global Defaults* — `setup/global_defaults.yaml`

- **Titre** : `default_currency`
- **Icône** : `settings`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `default_company` | Default Company | Link → `Company` |  |
| `country` | Default Country | Link → `Country` |  |
| `default_distance_unit` | Default Distance Unit | Link → `UOM` |  |
| `default_currency` | Default Currency | Link → `Currency` | **requis**; colonne de liste |
| `hide_currency_symbol` | Hide Currency Symbol | Boolean | colonne de liste; défaut `non`; — Do not show any symbol like $ etc next to currencies. |
| `disable_rounded_total` | Disable Rounded Total | Boolean | colonne de liste; défaut `non`; — If disable, 'Rounded Total' field will not be visible in any transaction |
| `disable_in_words` | Disable In Words | Boolean | colonne de liste; défaut `non`; — If disable, 'In Words' field will not be visible in any transaction |
| `demo_company` | Demo Company | Link → `Company` | lecture seule; masqué |
| `use_posting_datetime_for_naming_documents` | Use Posting Date for Naming Documents | Boolean | défaut `oui`; — When checked, the system will use the posting date of the document for naming instead of the creation date. |
| `enable_item_search_index` | Enable Item Search Index | Boolean | défaut `non`; — Speeds up Item search on large catalogues. Requires a single app server: the index is a file on that server's  |

## Holiday

*Holiday* — `setup/holiday.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `holiday_date` | Date | Date | **requis**; colonne de liste |
| `description` | Description | TextEditor | **requis**; colonne de liste |
| `weekly_off` | Weekly Off | Boolean | défaut `non` |
| `is_half_day` | Is Half Day | Boolean | colonne de liste; défaut `non` |

## Holiday List

*Holiday List* — `setup/holiday_list.yaml`

- **Vues** : calendar, gantt
- **Titre** : `holiday_list_name`
- **Icône** : `calendar-off`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `holiday_list_name` | Holiday List Name | Text | **requis** |
| `from_date` | From Date | Date | **requis**; colonne de liste |
| `to_date` | To Date | Date | **requis**; colonne de liste |
| `total_holidays` | Total Holidays | Number | colonne de liste; lecture seule |
| `weekly_off` | Weekly Off | Select — Sunday · Monday · Tuesday · Wednesday · Thursday · Friday · Saturday |  |
| `holidays` | Holidays | Table → `Holiday` |  |
| `color` | Color | Color |  |
| `country` | Country | Text |  |
| `subdivision` | Subdivision | Text |  |
| `is_half_day` | Is Half Day | Boolean | défaut `non` |

## Incoterm

*Incoterm* — `setup/incoterm.yaml`

- **Titre** : `title`
- **Icône** : `ship`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `code` | Code | Text | **requis**; colonne de liste |
| `title` | Title | Text | **requis**; colonne de liste |
| `description` | Description | LongText |  |

## Item Group

*Item Group* — `setup/item_group.yaml`

- **Vues** : tree (parent `parent_item_group`)
- **Titre** : `item_group_name`
- **Icône** : `boxes`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_group_name` | Item Group Name | Text | **requis**; colonne de liste |
| `parent_item_group` | Parent Item Group | Link → `Item Group` | colonne de liste |
| `is_group` | Is Group | Boolean | colonne de liste; défaut `non`; — Only leaf nodes are allowed in transaction |
| `image` | Image | Image | masqué |
| `item_group_defaults` | Item Group Defaults | Table → `Item Default` |  |
| `taxes` | Taxes | Table → `Item Tax` |  |
| `lft` | lft | Int | masqué |
| `rgt` | rgt | Int | masqué |
| `old_parent` | old_parent | Link → `Item Group` | masqué |

## Language

*Language* — `setup/language.yaml`

- **Numérotation** : nommé par le champ `language_code`
- **Titre** : `language_name`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `language_name` | Language Name | Text | **requis**; colonne de liste |
| `language_code` | Language Code | Text | **requis**; unique |
| `enabled` | Enabled | Boolean | défaut `oui` |

## Letter Head

*Letter Head* — `setup/letter_head.yaml`

- **Titre** : `letter_head_name`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `letter_head_name` | Letter Head Name | Text | **requis**; colonne de liste |
| `is_default` | Default | Boolean |  |
| `disabled` | Disabled | Boolean |  |
| `content` | Content | TextEditor |  |
| `footer` | Footer | TextEditor |  |

## Module Def

*Module Def* — `setup/module_def.yaml`

- **Numérotation** : nommé par le champ `module_name`
- **Titre** : `module_name`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `module_name` | Module Name | Text | **requis**; colonne de liste; unique |
| `app_name` | App Name | Text |  |
| `custom` | Custom | Boolean |  |

## Party Type

*Party Type* — `setup/party_type.yaml`

- **Titre** : `party_type`
- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `party_type` | Party Type | Text | **requis**; colonne de liste |
| `account_type` | Account Type | Select — Payable · Receivable | **requis**; colonne de liste |

## Print Format

*Print Format* — `setup/print_format.yaml`

- **Titre** : `format_name`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `format_name` | Format Name | Text | **requis**; colonne de liste |
| `doc_type` | DocType | Text | **requis** |
| `standard` | Standard | Boolean |  |
| `disabled` | Disabled | Boolean |  |
| `format_data` | Format Data | JSON |  |

## Print Heading

*Print Heading* — `setup/print_heading.yaml`

- **Titre** : `print_heading`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `print_heading` | Print Heading | Text | **requis**; colonne de liste |
| `disabled` | Disabled | Boolean |  |

## Quotation Lost Reason

*Quotation Lost Reason* — `setup/quotation_lost_reason.yaml`

- **Titre** : `order_lost_reason`
- **Icône** : `circle-x`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `order_lost_reason` | Quotation Lost Reason | Text | **requis**; colonne de liste |

## Quotation Lost Reason Detail

*Quotation Lost Reason Detail* — `setup/quotation_lost_reason_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `lost_reason` | Quotation Lost Reason | Link → `Quotation Lost Reason` | colonne de liste |

## RQ Job

*RQ Job* — `setup/rq_job.yaml`

- **Numérotation** : nommé par le champ `job_id`
- **Titre** : `job_id`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `job_id` | Job ID | Text | **requis**; colonne de liste; unique |
| `status` | Status | Select — Queued · Started · Finished · Failed |  |
| `queue` | Queue | Text |  |
| `method` | Method | Text |  |
| `creation_time` | Creation Time | Datetime |  |
| `ended_at` | Ended At | Datetime |  |
| `exc_info` | Error Details | LongText |  |

## Sales Partner

*Sales Partner* — `setup/sales_partner.yaml`

- **Titre** : `partner_type`
- **Icône** : `handshake`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `partner_name` | Sales Partner Name | Text | **requis** |
| `partner_type` | Partner Type | Link → `Sales Partner Type` | colonne de liste |
| `territory` | Territory | Link → `Territory` | **requis**; colonne de liste |
| `commission_rate` | Commission Rate | Number | **requis** |
| `targets` | Targets | Table → `Target Detail` |  |
| `show_in_website` | Show In Website | Boolean | défaut `non` |
| `referral_code` | Referral Code | Text | — To Track inbound purchase |
| `route` | Route | Text |  |
| `logo` | Logo | Attach |  |
| `partner_website` | Partner website | Text |  |
| `introduction` | Introduction | LongText |  |
| `description` | Description | TextEditor |  |

## Sales Person

*Sales Person* — `setup/sales_person.yaml`

- **Vues** : tree (parent `parent_sales_person`)
- **Titre** : `sales_person_name`
- **Icône** : `user-round`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `sales_person_name` | Sales Person Name | Text | **requis**; colonne de liste |
| `parent_sales_person` | Parent Sales Person | Link → `Sales Person` | colonne de liste; — Select company name first. |
| `commission_rate` | Commission Rate | Percent |  |
| `is_group` | Is Group | Boolean | **requis**; colonne de liste; défaut `non` |
| `enabled` | Enabled | Boolean | défaut `oui` |
| `employee` | Employee | Link → `Employee` |  |
| `department` | Department | Link → `Department` | lecture seule |
| `lft` | lft | Int | masqué |
| `rgt` | rgt | Int | masqué |
| `old_parent` | old_parent | Text | masqué |
| `targets` | Targets | Table → `Target Detail` |  |

## Salutation

*Salutation* — `setup/salutation.yaml`

- **Numérotation** : nommé par le champ `salutation`
- **Titre** : `salutation`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `salutation` | Salutation | Text | **requis**; colonne de liste; unique |
| `enabled` | Enabled | Boolean | défaut `oui` |

## Supplier Group

*Supplier Group* — `setup/supplier_group.yaml`

- **Vues** : tree (parent `parent_supplier_group`)
- **Titre** : `parent_supplier_group`
- **Icône** : `users`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `supplier_group_name` | Supplier Group Name | Text | **requis** |
| `parent_supplier_group` | Parent Supplier Group | Link → `Supplier Group` | colonne de liste |
| `is_group` | Is Group | Boolean | colonne de liste; défaut `non`; — Only leaf nodes are allowed in transaction |
| `payment_terms` | Default Payment Terms Template | Link → `Payment Terms Template` |  |
| `accounts` | Accounts | Table → `Party Account` | — Mention if non-standard receivable account applicable |
| `lft` | lft | Int | masqué |
| `rgt` | rgt | Int | masqué |
| `old_parent` | Old Parent | Link → `Supplier Group` | masqué |

## Target Detail

*Target Detail* — `setup/target_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_group` | Item Group | Link → `Item Group` | colonne de liste |
| `fiscal_year` | Fiscal Year | Link → `Fiscal Year` | **requis**; colonne de liste |
| `target_qty` | Target Qty | Decimal | colonne de liste |
| `target_amount` | Target  Amount | Number | colonne de liste |
| `distribution_id` | Target Distribution | Link → `Monthly Distribution` | **requis**; colonne de liste |

## Terms and Conditions

*Terms and Conditions* — `setup/terms_and_conditions.yaml`

- **Titre** : `title`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text | **requis** |
| `disabled` | Disabled | Boolean | défaut `non` |
| `terms` | Terms and Conditions | TextEditor |  |
| `selling` | Selling | Boolean | colonne de liste; défaut `oui` |
| `buying` | Buying | Boolean | colonne de liste; défaut `oui` |
| `copy_attachments_to_transaction` | Copy Attachments to Transaction | Boolean | défaut `non` |

## Territory

*Territory* — `setup/territory.yaml`

- **Vues** : tree (parent `parent_territory`)
- **Titre** : `territory_name`
- **Icône** : `map`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `territory_name` | Territory Name | Text | **requis**; colonne de liste |
| `parent_territory` | Parent Territory | Link → `Territory` | colonne de liste |
| `is_group` | Is Group | Boolean | colonne de liste; défaut `non`; — Only leaf nodes are allowed in transaction |
| `territory_manager` | Territory Manager | Link → `Sales Person` | colonne de liste; — For reference |
| `lft` | lft | Int | masqué |
| `rgt` | rgt | Int | masqué |
| `old_parent` | old_parent | Link → `Territory` | masqué |
| `targets` | Targets | Table → `Target Detail` |  |

## Transaction Deletion Record

*Transaction Deletion Record* — `setup/transaction_deletion_record.yaml` · soumis

- **Numérotation** : série `TDR-{YYYY}-{#####}`
- **Titre** : `status`
- **Icône** : `trash`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `doctypes` | Summary | Table → `Transaction Deletion Record Details` | lecture seule |
| `doctypes_to_delete` | DocTypes To Delete | Table → `Transaction Deletion Record To Delete` |  |
| `doctypes_to_be_ignored` | Excluded DocTypes | Table → `Transaction Deletion Record Item` | — DocTypes that will NOT be deleted. |
| `status` | Status | Select — Queued · Running · Failed · Completed · Cancelled | lecture seule |
| `delete_bin_data_status` | Delete Bins | Select — Pending · Completed · Skipped | lecture seule; défaut `Pending` |
| `delete_leads_and_addresses_status` | Delete Leads and Addresses | Select — Pending · Completed · Skipped | lecture seule; défaut `Pending` |
| `reset_company_default_values_status` | Reset Company Default Values | Select — Pending · Completed · Skipped | lecture seule; défaut `Pending` |
| `clear_notifications_status` | Clear Notifications | Select — Pending · Completed · Skipped | lecture seule; défaut `Pending` |
| `initialize_doctypes_table_status` | Initialize Summary Table | Select — Pending · Completed · Skipped | lecture seule; défaut `Pending` |
| `delete_transactions_status` | Delete Transactions | Select — Pending · Completed · Skipped | lecture seule; défaut `Pending` |
| `error_log` | Error Log | LongText |  |
| `process_in_single_transaction` | Process in Single Transaction | Boolean | lecture seule; masqué |

## Transaction Deletion Record Item

*Transaction Deletion Record Item* — `setup/transaction_deletion_record_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `doctype_name` | DocType | Text | **requis**; colonne de liste |

## Transaction Deletion Record To Delete

*Transaction Deletion Record To Delete* — `setup/transaction_deletion_record_to_delete.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `doctype_name` | DocType | Text | colonne de liste |
| `company_field` | Company Field | Text | colonne de liste; — Company link field name used for filtering (optional - leave empty to delete all records) |
| `document_count` | Document Count | Int | colonne de liste; lecture seule |
| `child_doctypes` | Child DocTypes | LongText | colonne de liste; lecture seule; — Child tables that will also be deleted |
| `deleted` | Deleted | Boolean | colonne de liste; lecture seule |

## UOM

*UOM* — `setup/uom.yaml`

- **Titre** : `uom_name`
- **Icône** : `ruler`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `uom_name` | UOM Name | Text | **requis**; colonne de liste |
| `must_be_whole_number` | Must be Whole Number | Boolean | défaut `non`; — Check this to disallow fractions. (for Nos) |
| `enabled` | Enabled | Boolean | défaut `oui` |
| `symbol` | Symbol | Text |  |
| `common_code` | Common Code | Text | — According to CEFACT/ICG/2010/IC013 or CEFACT/ICG/2010/IC010 |
| `description` | Description | LongText |  |
| `category` | Category | Link → `UOM Category` | colonne de liste |

## UOM Conversion Factor

*UOM Conversion Factor* — `setup/uom_conversion_factor.yaml`

- **Titre** : `category`
- **Icône** : `ruler`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `category` | Category | Link → `UOM Category` | **requis**; colonne de liste |
| `from_uom` | From | Link → `UOM` | **requis**; colonne de liste |
| `to_uom` | To | Link → `UOM` | **requis**; colonne de liste |
| `value` | Value | Number | **requis**; colonne de liste |

## Vehicle

*Vehicle* — `setup/vehicle.yaml`

- **Vues** : calendar, gantt
- **Titre** : `model`
- **Icône** : `car`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `license_plate` | License Plate | Text | **requis** |
| `make` | Make | Text | **requis** |
| `model` | Model | Text | **requis**; colonne de liste |
| `last_odometer` | Odometer Value (Last) | Int | **requis**; colonne de liste |
| `acquisition_date` | Acquisition Date | Date |  |
| `location` | Location | Text |  |
| `chassis_no` | Chassis No | Text |  |
| `vehicle_value` | Vehicle Value | Currency | colonne de liste; devise de `company.default_currency` |
| `employee` | Employee | Link → `Employee` |  |
| `insurance_company` | Insurance Company | Text |  |
| `policy_no` | Policy No | Text |  |
| `start_date` | Start Date | Date |  |
| `end_date` | End Date | Date |  |
| `fuel_type` | Fuel Type | Select — Petrol · Diesel · Natural Gas · Electric | **requis**; colonne de liste |
| `uom` | Fuel UOM | Link → `UOM` | **requis**; colonne de liste |
| `carbon_check_date` | Last Carbon Check | Date |  |
| `color` | Color | Text |  |
| `wheels` | Wheels | Int |  |
| `doors` | Doors | Int |  |
| `company` | Company | Link → `Company` |  |

## Web Form

*Web Form* — `setup/web_form.yaml`

- **Numérotation** : nommé par le champ `route`
- **Titre** : `title`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text | **requis**; colonne de liste |
| `route` | Route | Text | **requis**; unique |
| `doc_type` | DocType | Text | **requis** |
| `published` | Published | Boolean |  |
| `login_required` | Login Required | Boolean |  |
| `success_message` | Success Message | LongText |  |
