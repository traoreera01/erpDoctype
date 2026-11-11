# Référence des champs — Comptabilité (`accounts`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `accounts/` (192 DocTypes). Ne pas éditer à la main : relancer le script.

2438 champs au total ; types les plus fréquents : `Link` (639), `Boolean` (335), `Currency` (329), `Text` (313), `Select` (159).

## Account

*Account* — `accounts/account.yaml`

- **Vues** : tree (parent `parent_account`)
- **Titre** : `account_name`
- **Icône** : `vault`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `account_name` | Account Name | Text | **requis**; colonne de liste |
| `account_number` | Account Number | Text | **requis**; colonne de liste; — SYSCOHADA - every account is numbered, and its first digit is its class (1 to 9) |
| `is_group` | Is Group | Boolean | défaut `non` |
| `company` | Company | Link → `Company` | **requis** |
| `root_type` | Root Type | Select — Asset · Liability · Income · Expense · Equity | lecture seule |
| `report_type` | Report Type | Select — Balance Sheet · Profit and Loss | lecture seule |
| `account_currency` | Currency | Link → `Currency` |  |
| `parent_account` | Parent Account | Link → `Account` |  |
| `account_type` | Account Type | Select — Accumulated Depreciation · Asset Received But Not Billed · Bank · Cash · Chargeable · Capital Work in Progress · Cost of Goods Sold · Current Asset · Current Liability · Depreciation · Direct Expense · Direct Income · Equity · Expense Account · Expenses Included In Asset Valuation · Expenses Included In Valuation · Fixed Asset · Income Account · Indirect Expense · Indirect Income · Liability · Payable · Receivable · Round Off · Round Off for Opening · Stock · Stock Adjustment · Stock Received But Not Billed · Stock Delivered But Not Billed · Service Received But Not Billed · Tax · Temporary | — Setting Account Type helps in selecting this Account in transactions. |
| `tax_rate` | Tax Rate | Number | — Rate at which this tax is applied |
| `freeze_account` | Frozen | Select — No · Yes | — If the account is frozen, entries are allowed to restricted users. |
| `balance_must_be` | Balance must be | Select — Debit · Credit |  |
| `lft` | Lft | Int | lecture seule; masqué |
| `rgt` | Rgt | Int | lecture seule; masqué |
| `old_parent` | Old Parent | Text | lecture seule; masqué |
| `include_in_gross` | Include in gross | Boolean | défaut `non` |
| `disabled` | Disable | Boolean | défaut `non` |
| `account_category` | Account Category | Link → `Account Category` | — Used with Financial Report Template |

## Account Category

*Account Category* — `accounts/account_category.yaml`

- **Titre** : `account_category_name`
- **Icône** : `folder-tree`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `account_category_name` | Account Category Name | Text | **requis**; colonne de liste |
| `description` | Description | LongText |  |
| `root_type` | Root Type | Select — Asset · Liability · Income · Expense · Equity | colonne de liste |

## Account Closing Balance

*Account Closing Balance* — `accounts/account_closing_balance.yaml` · soumis

- **Numérotation** : série `ACB-{YYYY}-{#####}`
- **Titre** : `company`
- **Icône** : `scale`
- **Permissions explicites** — `write` : 0, `create` : 0, `delete` : 0, `submit` : 0, `cancel` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `closing_date` | Closing Date | Date | colonne de liste |
| `account` | Account | Link → `Account` | colonne de liste |
| `cost_center` | Cost Center | Link → `Cost Center` | colonne de liste |
| `debit` | Debit Amount | Currency | devise de `company.default_currency` |
| `credit` | Credit Amount | Currency | devise de `company.default_currency` |
| `account_currency` | Account Currency | Link → `Currency` |  |
| `debit_in_account_currency` | Debit Amount in Account Currency | Currency | devise de `account_currency` |
| `credit_in_account_currency` | Credit Amount in Account Currency | Currency | devise de `account_currency` |
| `project` | Project | Link → `Project` |  |
| `company` | Company | Link → `Company` | colonne de liste |
| `finance_book` | Finance Book | Link → `Finance Book` |  |
| `period_closing_voucher` | Period Closing Voucher | Link → `Period Closing Voucher` |  |
| `is_period_closing_voucher_entry` | Is Period Closing Voucher Entry | Boolean | défaut `non` |
| `debit_in_reporting_currency` | Debit Amount in Reporting Currency | Currency | devise de `company.reporting_currency` |
| `credit_in_reporting_currency` | Credit Amount in Reporting Currency | Currency | devise de `company.reporting_currency` |
| `reporting_currency_exchange_rate` | Reporting Currency Exchange Rate | Number |  |

## Accounting Dimension

*Accounting Dimension* — `accounts/accounting_dimension.yaml`

- **Titre** : `label`
- **Icône** : `layers`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `label` | Dimension Name | Text | colonne de liste |
| `fieldname` | Fieldname | Text | masqué |
| `document_type` | Reference Document Type | Text | **requis** |
| `disabled` | Disable | Boolean | lecture seule; masqué |
| `dimension_defaults` | Dimension Defaults | Table → `Accounting Dimension Detail` |  |

## Accounting Dimension Detail

*Accounting Dimension Detail* — `accounts/accounting_dimension_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | colonne de liste |
| `reference_document` | Reference Document | Text | lecture seule; masqué |
| `default_dimension` | Default Dimension | DynamicLink → `reference_document` | colonne de liste |
| `mandatory_for_bs` | Mandatory For Balance Sheet | Boolean | colonne de liste; défaut `non` |
| `mandatory_for_pl` | Mandatory For Profit and Loss Account | Boolean | colonne de liste; défaut `non` |
| `automatically_post_balancing_accounting_entry` | Automatically post balancing accounting entry | Boolean | défaut `non` |
| `offsetting_account` | Offsetting Account | Link → `Account` |  |

## Accounting Dimension Filter

*Accounting Dimension Filter* — `accounts/accounting_dimension_filter.yaml`

- **Titre** : `company`
- **Icône** : `funnel`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `allow_or_restrict` | Allow Or Restrict Dimension | Select — Allow · Restrict | **requis** |
| `accounts` | Applicable On Account | Table → `Applicable On Account` |  |
| `dimensions` | Applicable Dimension | Table → `Allowed Dimension` |  |
| `disabled` | Disabled | Boolean | défaut `non` |
| `company` | Company | Link → `Company` | **requis** |
| `apply_restriction_on_values` | Apply restriction on dimension values | Boolean | défaut `oui` |
| `fieldname` | Fieldname | Text | masqué |

## Accounting Period

*Accounting Period* — `accounts/accounting_period.yaml`

- **Vues** : calendar, gantt
- **Titre** : `company`
- **Icône** : `calendar-range`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `period_name` | Period Name | Text | **requis** |
| `start_date` | Start Date | Date | **requis**; colonne de liste |
| `end_date` | End Date | Date | **requis**; colonne de liste |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `disabled` | Disabled | Boolean | colonne de liste; défaut `non` |
| `closed_documents` | Closed Documents | Table → `Closed Document` |  |

## Accounts Settings

*Accounts Settings* — `accounts/accounts_settings.yaml` · document unique

- **Icône** : `settings`
- **Permissions explicites** — `create` : 0, `delete` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `determine_address_tax_category_from` | Determine Address Tax Category from | Select — Billing Address · Shipping Address | défaut `Billing Address`; — Address used to determine Tax Category in transactions |
| `check_supplier_invoice_uniqueness` | Check Supplier invoice number uniqueness | Boolean | défaut `non`; — Enabling this ensures each Purchase Invoice has a unique value in Supplier Invoice No. field within a particul |
| `make_payment_via_journal_entry` | Make Payment via Journal Entry | Boolean | masqué; défaut `non` |
| `unlink_payment_on_cancellation_of_invoice` | Unlink Payment on cancellation of invoice | Boolean | défaut `oui` |
| `unlink_advance_payment_on_cancelation_of_order` | Unlink Advance Payment on cancellation of order | Boolean | défaut `oui` |
| `book_asset_depreciation_entry_automatically` | Book Asset Depreciation entry automatically | Boolean | défaut `oui` |
| `add_taxes_from_item_tax_template` | Automatically add Taxes and Charges from Item Tax Template | Boolean | défaut `oui` |
| `show_inclusive_tax_in_print` | Show inclusive tax in print | Boolean | défaut `non` |
| `show_payment_schedule_in_print` | Show Payment Schedule in print | Boolean | défaut `non` |
| `allow_stale` | Allow Stale Exchange Rates | Boolean | colonne de liste; défaut `oui`; — System will use the latest saved Currency Exchange rate on or before the transaction date, however old it is.  |
| `stale_days` | Stale Days | Int | défaut `1` |
| `automatically_fetch_payment_terms` | Automatically fetch Payment Terms from Order/Quotation | Boolean | défaut `non`; — Payment Terms from orders will be fetched into the invoices as is |
| `over_billing_allowance` | Over Billing Allowance (%) | Currency | — The percentage you are allowed to bill more against the amount ordered. For example, if the order value is $10 |
| `automatically_process_deferred_accounting_entry` | Automatically process deferred Accounting entry | Boolean | défaut `oui` |
| `book_deferred_entries_via_journal_entry` | Book deferred entries via Journal Entry | Boolean | défaut `non`; — If this is unchecked, direct GL entries will be created to book deferred revenue or expense |
| `submit_journal_entries` | Submit Journal entries | Boolean | défaut `non`; — If this is unchecked Journal Entries will be saved in a Draft state and will have to be submitted manually |
| `book_deferred_entries_based_on` | Book Deferred entries based on | Select — Days · Months | défaut `Days`; — If "Months" is selected, a fixed amount will be booked as deferred revenue or expense for each month irrespect |
| `delete_linked_ledger_entries` | Delete Accounting and Stock Ledger entries on deletion of transaction | Boolean | défaut `non` |
| `enable_overdue_billing_threshold` | Prevent Sales Invoice when Customer is Overdue | Boolean | défaut `non`; — Enabling this option prevents the creation of a new Sales Invoice when the customer has an overdue limit set a |
| `enable_common_party_accounting` | Enable Common Party Accounting | Boolean | défaut `non`; — Learn about <a href="https://docs.frappe.io/erpnext/user/manual/en/common_party_accounting" rel="noopener nore |
| `allow_multi_currency_invoices_against_single_party_account` | Allow multi-currency invoices against single party account  | Boolean | défaut `non`; — Enabling this will allow creation of multi-currency invoices against single party account in company currency |
| `show_balance_in_coa` | Show balances in Chart of Accounts | Boolean | défaut `oui` |
| `book_tax_discount_loss` | Book tax loss on early payment discount | Boolean | défaut `non`; — Split Early Payment Discount Loss into Income and Tax Loss |
| `merge_similar_account_heads` | Merge similar Account Heads | Boolean | défaut `non`; — Merge rows with the same account head in the ledger for Journal Entries and Payment Entries only. |
| `auto_reconcile_payments` | Auto reconcile Payments | Boolean | défaut `non` |
| `show_taxes_as_table_in_print` | Show taxes as table in print | Boolean | défaut `non` |
| `enable_party_matching` | Enable Automatic Party Matching | Boolean | défaut `non`; — Auto match and set the Party in Bank Transactions |
| `enable_fuzzy_matching` | Enable Fuzzy Matching | Boolean | défaut `non`; — Approximately match the description/party name against parties |
| `ignore_account_closing_balance` | Ignore Account closing balance | Boolean | défaut `non`; — Financial reports will be generated using GL Entry doctypes (should be enabled if Period Closing Voucher is no |
| `round_row_wise_tax` | Round tax amount row-wise | Boolean | défaut `non`; — Tax Amount will be rounded on a row(items) level |
| `general_ledger_remarks_length` | General Ledger remarks length | Int | défaut `0`; — Truncates 'Remarks' column to set character length |
| `receivable_payable_remarks_length` | Accounts Receivable / Payable remarks length | Int | défaut `0`; — Truncates 'Remarks' column to set character length |
| `enable_immutable_ledger` | Enable Immutable Ledger | Boolean | défaut `non`; — On enabling this cancellation entries will be posted on the actual cancellation date and reports will consider |
| `calculate_depr_using_total_days` | Calculate daily depreciation using total days in depreciation period | Boolean | défaut `non`; — Enable this option to calculate daily depreciation by considering the total number of days in the entire depre |
| `create_pr_in_draft_status` | Create payment requests in Draft status | Boolean | défaut `oui`; — Payment Requests made from Sales / Purchase Invoice will be put in Draft explicitly |
| `auto_reconciliation_job_trigger` | Auto Reconciliation job trigger | Int | défaut `15`; — Interval should be between 1 to 59 MInutes |
| `reconciliation_queue_size` | Reconciliation queue size | Int | défaut `5`; — Documents Processed on each trigger. Queue Size should be between 5 and 100 |
| `ignore_is_opening_check_for_reporting` | Ignore Is Opening check for reporting | Boolean | défaut `non`; — Ignores legacy Is Opening field in GL Entry that allows adding opening balance post the system is in use while |
| `exchange_gain_loss_posting_date` | Posting Date inheritance for exchange gain / loss | Select — Invoice · Payment · Reconciliation Date | défaut `Payment`; — Only applies for Normal Payments |
| `receivable_payable_fetch_method` | Data fetch method | Select — Buffered Cursor · UnBuffered Cursor | défaut `Buffered Cursor` |
| `maintain_same_internal_transaction_rate` | Maintain same rate throughout internal Transaction | Boolean | défaut `non` |
| `maintain_same_rate_action` | Action if same rate is not maintained throughout internal transaction | Select — Stop · Warn | défaut `Stop` |
| `confirm_before_resetting_posting_date` | Confirm before resetting posting date | Boolean | défaut `oui`; — If enabled, user will be alerted before resetting posting date to current date in relevant transactions |
| `allow_pegged_currencies_exchange_rates` | Allow Implicit Pegged Currency Conversion | Boolean | défaut `non`; — System will do an implicit conversion using the pegged currency. <br> Ex: Instead of AED -&gt; INR, system wil |
| `add_taxes_from_taxes_and_charges_template` | Automatically add taxes from Taxes and Charges Template | Boolean | défaut `non`; — If no taxes are set, and Taxes and Charges Template is selected, the system will automatically apply the taxes |
| `fetch_valuation_rate_for_internal_transaction` | Fetch valuation rate for internal Transaction | Boolean | défaut `non` |
| `use_legacy_budget_controller` | Use legacy Budget Controller | Boolean | défaut `non`; — Enable this if you are experiencing issues with the new budget controller. Uses the older budget validation lo |
| `use_legacy_controller_for_pcv` | Use legacy controller for Period Closing Voucher | Boolean | défaut `oui` |
| `pcv_job_timeout` | PCV Job Timeout (seconds) | Int | défaut `3600`; — Timeout (in seconds) for each background job enqueued by Process Period Closing Voucher |
| `default_ageing_range` | Default Ageing Range | Text | défaut `30, 60, 90, 120` |
| `enable_discounts_and_margin` | Enable Discounts and Margin | Boolean | défaut `non`; — Apply discounts and margins on products |
| `enable_loyalty_point_program` | Enable Loyalty Point Program | Boolean | défaut `non` |
| `enable_accounting_dimensions` | Enable Accounting Dimensions | Boolean | défaut `non`; — Enable cost center, projects and other custom accounting dimensions |
| `enable_subscription` | Enable Subscription | Boolean | défaut `oui`; — Enable Subscription tracking in invoice |
| `fetch_payment_schedule_in_payment_request` | Fetch Payment Schedule in Payment Request | Boolean | défaut `oui` |
| `transfer_match_days` | Match transfers within 'N' days | Int | défaut `3`; — Number of days to consider for matching transfers across bank accounts |
| `automatically_run_rules_on_unreconciled_transactions` | Automatically run rules on unreconciled transactions | Boolean | défaut `oui`; — If enabled, rule matching algorithm will run every hour |
| `repost_allowed_types` | Allowed DocTypes | Table → `Repost Allowed Types` |  |
| `preview_mode` | Preview mode | Boolean | défaut `non`; — Runs a preview check on save before submission without making any actual changes. |
| `book_stock_expense_gl_entries` | Book Stock Expense GL Entries | Boolean | défaut `non`; — Books Purchase Expense and Expenses Added To Stock account pairs against stock value. On enabling this, the ac |
| `disable_include_dimensions` | Disable "Consider Accounting Dimension" Filter | Boolean | défaut `non` |

## Advance Payment Ledger Entry

*Advance Payment Ledger Entry* — `accounts/advance_payment_ledger_entry.yaml` · soumis

- **Numérotation** : série `APLE-{YYYY}-{#####}`
- **Titre** : `company`
- **Icône** : `book-open`
- **Permissions explicites** — `write` : 0, `create` : 0, `delete` : 0, `submit` : 0, `cancel` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `voucher_type` | Voucher Type | Text | lecture seule |
| `voucher_no` | Voucher No | DynamicLink → `voucher_type` | lecture seule |
| `against_voucher_type` | Against Voucher Type | Text | lecture seule |
| `against_voucher_no` | Against Voucher No | DynamicLink → `against_voucher_type` | lecture seule |
| `amount` | Amount | Currency | lecture seule; devise de `currency` |
| `currency` | Currency | Link → `Currency` | lecture seule |
| `event` | Event | Text | lecture seule |
| `company` | Company | Link → `Company` | lecture seule |
| `delinked` | DeLinked | Boolean | lecture seule |
| `base_amount` | Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `exchange_rate` | Exchange Rate | Number | lecture seule |

## Advance Taxes and Charges

*Advance Taxes and Charges* — `accounts/advance_taxes_and_charges.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `charge_type` | Type | Select — Actual · On Paid Amount · On Previous Row Amount · On Previous Row Total | **requis**; colonne de liste |
| `row_id` | Reference Row # | Text |  |
| `account_head` | Account Head | Link → `Account` | **requis**; colonne de liste |
| `description` | Description | LongText | **requis** |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |
| `rate` | Tax Rate | Number | colonne de liste |
| `tax_amount` | Amount | Currency | colonne de liste; devise de `currency` |
| `total` | Total | Currency | colonne de liste; lecture seule; devise de `currency` |
| `base_tax_amount` | Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_total` | Total (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `add_deduct_tax` | Add Or Deduct | Select — Add · Deduct | **requis** |
| `included_in_paid_amount` | Considered In Paid Amount | Boolean | défaut `non` |
| `currency` | Account Currency | Link → `Currency` | lecture seule |
| `net_amount` | Net Amount | Currency | colonne de liste; lecture seule; devise de `currency` |
| `base_net_amount` | Net Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `set_by_item_tax_template` | Set by Item Tax Template | Boolean | lecture seule; masqué |
| `is_tax_withholding_account` | Is Tax Withholding Account | Boolean | lecture seule |

## Allowed Dimension

*Allowed Dimension* — `accounts/allowed_dimension.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `accounting_dimension` | Accounting Dimension | Text | lecture seule |
| `dimension_value` | Dimension Value | DynamicLink → `accounting_dimension` | colonne de liste |

## Allowed To Transact With

*Allowed To Transact With* — `accounts/allowed_to_transact_with.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |

## Applicable On Account

*Applicable On Account* — `accounts/applicable_on_account.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `applicable_on_account` | Accounts | Link → `Account` | **requis**; colonne de liste |
| `is_mandatory` | Is Mandatory | Boolean | colonne de liste; défaut `non` |

## Bank

*Bank* — `accounts/bank.yaml`

- **Titre** : `swift_number`
- **Icône** : `landmark`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `bank_name` | Bank Name | Text | **requis** |
| `swift_number` | SWIFT number | Text | colonne de liste |
| `website` | Website | Text |  |
| `bank_transaction_mapping` | Bank Transaction Mapping | Table → `Bank Transaction Mapping` |  |
| `plaid_access_token` | Plaid Access Token | Text | lecture seule; masqué |

## Bank Account

*Bank Account* — `accounts/bank_account.yaml`

- **Titre** : `account_name`
- **Icône** : `credit-card`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `account_name` | Account Name | Text | **requis**; colonne de liste |
| `account` | Company Account | Link → `Account` | colonne de liste |
| `bank` | Bank | Link → `Bank` | **requis** |
| `account_type` | Account Type | Link → `Bank Account Type` |  |
| `account_subtype` | Account Subtype | Link → `Bank Account Subtype` |  |
| `is_default` | Is Default Account | Boolean | défaut `non` |
| `is_company_account` | Is Company Account | Boolean | défaut `non`; — Setting the account as a Company Account is necessary for Bank Reconciliation |
| `company` | Company | Link → `Company` | colonne de liste |
| `party_type` | Party Type | Text |  |
| `party` | Party | DynamicLink → `party_type` |  |
| `iban` | IBAN | Text | colonne de liste |
| `bank_account_no` | Bank Account No | Text | colonne de liste |
| `integration_id` | Integration ID | Text | lecture seule; masqué |
| `last_integration_date` | Last Integration Date | Date | — Change this date manually to setup the next synchronization start date |
| `mask` | Mask | Text | lecture seule |
| `branch_code` | Branch Code | Text |  |
| `disabled` | Disabled | Boolean | défaut `non` |
| `is_credit_card` | Is Credit Card | Boolean | défaut `non`; — If checked, journal entries made using bank reconciliation will be of type "Credit Card Entry" |

## Bank Account Balance

*Bank Account Balance* — `accounts/bank_account_balance.yaml`

- **Vues** : calendar
- **Titre** : `company`
- **Icône** : `wallet`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `bank_account` | Bank Account | Link → `Bank Account` | **requis**; colonne de liste |
| `date` | Date | Date | **requis**; colonne de liste |
| `balance` | Balance | Currency | **requis**; colonne de liste; devise de `company.default_currency` |
| `company` | Company | Link → `Company` | lecture seule |

## Bank Account Subtype

*Bank Account Subtype* — `accounts/bank_account_subtype.yaml`

- **Icône** : `credit-card`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `account_subtype` | Account Subtype | Text |  |

## Bank Account Type

*Bank Account Type* — `accounts/bank_account_type.yaml`

- **Icône** : `credit-card`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `account_type` | Account Type | Text |  |

## Bank Clearance

*Bank Clearance* — `accounts/bank_clearance.yaml`

- **Vues** : calendar, gantt
- **Titre** : `account`
- **Icône** : `badge-check`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `account` | Account | Link → `Account` | **requis**; colonne de liste |
| `account_currency` | Account Currency | Link → `Currency` | masqué |
| `from_date` | From Date | Date | **requis**; colonne de liste |
| `to_date` | To Date | Date | **requis**; colonne de liste |
| `bank_account` | Bank Account | Link → `Bank Account` | — Select the Bank Account to reconcile. |
| `include_reconciled_entries` | Include Reconciled Entries | Boolean | colonne de liste; défaut `non` |
| `include_pos_transactions` | Include POS Transactions | Boolean | défaut `non` |
| `payment_entries` | Payment Entries | Table → `Bank Clearance Detail` |  |

## Bank Clearance Detail

*Bank Clearance Detail* — `accounts/bank_clearance_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `payment_document` | Payment Document | Text |  |
| `payment_entry` | Payment Entry | DynamicLink → `payment_document` | colonne de liste |
| `against_account` | Against Account | Text | colonne de liste; lecture seule |
| `amount` | Amount | Text | colonne de liste; lecture seule |
| `posting_date` | Posting Date | Date | lecture seule |
| `cheque_number` | Cheque Number | Text | colonne de liste; lecture seule |
| `cheque_date` | Cheque Date | Date | colonne de liste; lecture seule |
| `clearance_date` | Clearance Date | Date | colonne de liste |

## Bank Guarantee

*Bank Guarantee* — `accounts/bank_guarantee.yaml` · soumis

- **Numérotation** : série `BG-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `customer`
- **Icône** : `shield-check`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `bg_type` | Bank Guarantee Type | Select — Receiving · Providing | **requis** |
| `reference_doctype` | Reference Document Type | Text |  |
| `reference_docname` | Reference Document Name | DynamicLink → `reference_doctype` |  |
| `customer` | Customer | Link → `Customer` |  |
| `supplier` | Supplier | Link → `Supplier` |  |
| `project` | Project | Link → `Project` |  |
| `amount` | Amount | Currency | **requis**; colonne de liste |
| `start_date` | Start Date | Date | **requis** |
| `validity` | Validity in Days | Int |  |
| `end_date` | End Date | Date | lecture seule |
| `bank` | Bank | Link → `Bank` |  |
| `bank_account` | Bank Account | Link → `Bank Account` |  |
| `account` | Account | Link → `Account` | lecture seule |
| `bank_account_no` | Bank Account No | Text | lecture seule |
| `iban` | IBAN | Text | lecture seule |
| `branch_code` | Branch Code | Text | lecture seule |
| `swift_number` | SWIFT number | Text | lecture seule |
| `more_information` | Clauses and Conditions | TextEditor |  |
| `bank_guarantee_number` | Bank Guarantee Number | Text |  |
| `name_of_beneficiary` | Name of Beneficiary | Text |  |
| `margin_money` | Margin Money | Currency |  |
| `charges` | Charges Incurred | Currency |  |
| `fixed_deposit_number` | Fixed Deposit Number | Text |  |

## Bank Reconciliation Tool

*Bank Reconciliation Tool* — `accounts/bank_reconciliation_tool.yaml`

- **Titre** : `company`
- **Icône** : `arrow-left-right`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` |  |
| `bank_account` | Bank Account | Link → `Bank Account` |  |
| `bank_statement_from_date` | From Date | Date |  |
| `bank_statement_to_date` | To Date | Date |  |
| `account_opening_balance` | Account Opening Balance | Currency | lecture seule; devise de `account_currency` |
| `bank_statement_closing_balance` | Closing Balance | Currency | devise de `account_currency` |
| `from_reference_date` | From Reference Date | Date |  |
| `to_reference_date` | To Reference Date | Date |  |
| `filter_by_reference_date` | Filter by Reference Date | Boolean | défaut `non` |
| `account_currency` | Account Currency | Link → `Currency` | masqué |

## Bank Statement Import

*Bank Statement Import* — `accounts/bank_statement_import.yaml`

- **Titre** : `company`
- **Icône** : `file-down`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis** |
| `bank_account` | Bank Account | Link → `Bank Account` | **requis** |
| `bank` | Bank | Link → `Bank` | lecture seule |
| `import_file` | Import File | Attach | colonne de liste |
| `template_options` | Template Options | Code | lecture seule; masqué |
| `status` | Status | Select — Pending · Success · Partial Success · Error | lecture seule; masqué; défaut `Pending` |
| `template_warnings` | Template Warnings | Code | masqué |
| `show_failed_logs` | Show Failed Logs | Boolean | défaut `non` |
| `google_sheets_url` | Import from Google Sheets | Text | — Must be a publicly accessible Google Sheets URL and adding Bank Account column is necessary for importing via  |
| `reference_doctype` | Document Type | Text | **requis**; colonne de liste; masqué |
| `import_type` | Import Type | Select — Insert New Records · Update Existing Records | **requis**; colonne de liste; masqué; défaut `Insert New Records` |
| `submit_after_import` | Submit After Import | Boolean | masqué; défaut `oui` |
| `mute_emails` | Don't Send Emails | Boolean | masqué; défaut `oui` |
| `custom_delimiters` | Custom delimiters | Boolean | défaut `non` |
| `delimiter_options` | Delimiter options | Text | défaut `,;\t\|`; — If your CSV uses a different delimiter, add that character here, ensuring no spaces or additional characters a |
| `use_csv_sniffer` | Use CSV Sniffer | Boolean | masqué; défaut `non` |
| `import_mt940_fromat` | Import MT940 Format | Boolean | défaut `non` |

## Bank Statement Import Log

*Bank Statement Import Log* — `accounts/bank_statement_import_log.yaml`

- **Vues** : calendar, gantt
- **Titre** : `status`
- **Icône** : `file-clock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `bank_account` | Bank Account | Link → `Bank Account` | **requis**; colonne de liste |
| `number_of_transactions` | Number of Transactions | Int | colonne de liste; lecture seule |
| `closing_balance` | Closing Balance | Currency | colonne de liste; devise de `currency` |
| `start_date` | Start Date | Date | colonne de liste; lecture seule |
| `end_date` | End Date | Date | colonne de liste; lecture seule |
| `file` | File | Attach | **requis** |
| `detected_date_format` | Detected Date Format | Text | lecture seule |
| `detected_amount_format` | Detected Amount Format | Select — Separate columns for withdrawal and deposit · Amount column has "CR"/"DR" values · Amount column has positive/negative values · Transaction type column has "CR"/"DR" values · Transaction type column has "Deposit"/"Withdrawal" values · Transaction type column has "C"/"D" values | lecture seule |
| `detected_header_index` | Detected Header Index | Int | lecture seule |
| `detected_transaction_starting_index` | Detected Transaction Starting Index | Int | lecture seule |
| `detected_transaction_ending_index` | Detected Transaction Ending Index | Int | lecture seule |
| `column_mapping` | Column Mapping | Table → `Bank Statement Import Log Column Map` |  |
| `pdf_tables` | PDF Tables | JSON | lecture seule; — Per-table extraction data for PDF statements (rows, bbox, page image, column mapping). Edited via the banking  |
| `status` | Status | Select — Not Started · Completed | lecture seule; défaut `Not Started` |
| `currency` | Currency | Link → `Currency` | lecture seule |
| `total_debits` | Total Debits | Currency | lecture seule; devise de `currency` |
| `total_credits` | Total Credits | Currency | lecture seule; devise de `currency` |
| `total_debit_transactions` | Total Debit Transactions | Int | lecture seule |
| `total_credit_transactions` | Total Credit Transactions | Int | lecture seule |

## Bank Statement Import Log Column Map

*Bank Statement Import Log Column Map* — `accounts/bank_statement_import_log_column_map.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `header_text` | Header Text | Text | **requis**; colonne de liste |
| `maps_to` | Maps To | Select — Do not import · Date · Withdrawal · Deposit · Amount · Description · Reference · Transaction Type · Debit/Credit · Balance · Included Fee · Excluded Fee · Party Name/Account Holder · Party Account No. · Party IBAN | **requis**; colonne de liste |
| `index` | Index | Int | **requis**; colonne de liste |
| `variable` | Variable | Text |  |

## Bank Transaction

*Bank Transaction* — `accounts/bank_transaction.yaml` · soumis

- **Numérotation** : série `BT-{YYYY}-{#####}`
- **Vues** : kanban, calendar
- **Titre** : `company`
- **Icône** : `arrow-left-right`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — ACC-BTN-.YYYY.- | **requis**; défaut `ACC-BTN-.YYYY.-` |
| `date` | Date | Date |  |
| `status` | Status | Select — Pending · Settled · Unreconciled · Reconciled · Cancelled | défaut `Pending` |
| `bank_account` | Bank Account | Link → `Bank Account` |  |
| `company` | Company | Link → `Company` | lecture seule |
| `currency` | Currency | Link → `Currency` |  |
| `description` | Description | LongText | colonne de liste |
| `reference_number` | Reference Number | LongText |  |
| `transaction_id` | Transaction ID | Text | lecture seule |
| `payment_entries` | Payment Entries | Table → `Bank Transaction Payments` |  |
| `allocated_amount` | Allocated Amount | Currency | lecture seule; devise de `currency` |
| `unallocated_amount` | Unallocated Amount | Currency | lecture seule; devise de `currency` |
| `party_type` | Party Type | Text |  |
| `party` | Party | DynamicLink → `party_type` |  |
| `deposit` | Deposit | Currency | colonne de liste; devise de `currency` |
| `withdrawal` | Withdrawal | Currency | colonne de liste; devise de `currency` |
| `transaction_type` | Transaction Type | Text |  |
| `bank_party_name` | Party Name/Account Holder (Bank Statement) | Text |  |
| `bank_party_iban` | Party IBAN (Bank Statement) | Text |  |
| `bank_party_account_number` | Party Account No. (Bank Statement) | Text |  |
| `included_fee` | Included Fee | Currency | devise de `currency` |
| `excluded_fee` | Excluded Fee | Currency | devise de `currency`; — On save, the Excluded Fee will be converted to an Included Fee. |
| `is_rule_evaluated` | Is Rule Evaluated | Boolean | lecture seule |
| `matched_transaction_rule` | Matched Transaction Rule | Link → `Bank Transaction Rule` | lecture seule |

## Bank Transaction Mapping

*Bank Transaction Mapping* — `accounts/bank_transaction_mapping.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `file_field` | Column in Bank File | Text | **requis**; colonne de liste |

## Bank Transaction Payments

*Bank Transaction Payments* — `accounts/bank_transaction_payments.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `payment_document` | Payment Document | Text | **requis**; colonne de liste |
| `payment_entry` | Payment Entry | DynamicLink → `payment_document` | colonne de liste |
| `allocated_amount` | Allocated Amount | Currency | **requis**; colonne de liste; devise de `parent_currency` |
| `clearance_date` | Clearance Date | Date | lecture seule |
| `reconciliation_type` | Reconciliation Type | Select — Matched · Voucher Created | lecture seule; défaut `Matched` |

## Bank Transaction Rule

*Bank Transaction Rule* — `accounts/bank_transaction_rule.yaml`

- **Titre** : `company`
- **Icône** : `zap`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `rule_name` | Rule Name | Text | **requis**; colonne de liste |
| `transaction_type` | Transaction Type | Select — Any · Withdrawal · Deposit | **requis**; défaut `Any` |
| `min_amount` | Min Amount | Currency | devise de `company.default_currency` |
| `max_amount` | Max Amount | Currency | devise de `company.default_currency` |
| `rule_description` | Rule Description | LongText |  |
| `description_rules` | Description Rules | Table → `Bank Transaction Rule Description Conditions` |  |
| `classify_as` | Classify As | Select — Bank Entry · Payment Entry · Transfer | **requis** |
| `account` | Account | Link → `Account` |  |
| `party_type` | Party Type | Text |  |
| `party` | Party | DynamicLink → `party_type` |  |
| `priority` | Priority | Int | **requis** |
| `company` | Company | Link → `Company` | **requis** |
| `bank_entry_type` | Bank Entry Type | Select — Single Account · Multiple Accounts |  |
| `accounts` | Accounts | Table → `Bank Transaction Rule Accounts` |  |

## Bank Transaction Rule Accounts

*Bank Transaction Rule Accounts* — `accounts/bank_transaction_rule_accounts.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `account` | Account | Link → `Account` | **requis**; colonne de liste |
| `party_type` | Party Type | Text |  |
| `party` | Party | DynamicLink → `party_type` |  |
| `debit` | Debit | Text |  |
| `credit` | Credit | Text |  |
| `user_remark` | User Remark | LongText |  |

## Bank Transaction Rule Description Conditions

*Bank Transaction Rule Description Conditions* — `accounts/bank_transaction_rule_description_conditions.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `check` | Check | Select — Contains · Starts With · Ends With · Regex | **requis**; colonne de liste |
| `value` | Value | LongText | **requis**; colonne de liste |

## Bisect Accounting Statements

*Bisect Accounting Statements* — `accounts/bisect_accounting_statements.yaml`

- **Titre** : `company`
- **Icône** : `split`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `from_date` | From Date | Datetime |  |
| `to_date` | To Date | Datetime |  |
| `algorithm` | Algorithm | Select — BFS · DFS | défaut `BFS` |
| `current_node` | Current Node | Link → `Bisect Nodes` |  |
| `current_from_date` | Current From Date | Datetime | lecture seule |
| `current_to_date` | Current To Date | Datetime | lecture seule |
| `p_l_summary` | P L Summary | Number | lecture seule |
| `b_s_summary` | B S Summary | Number | lecture seule |
| `difference` | Difference | Number | lecture seule |
| `company` | Company | Link → `Company` |  |

## Bisect Nodes

*Bisect Nodes* — `accounts/bisect_nodes.yaml`

- **Icône** : `git-branch`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `root` | Root | Link → `Bisect Nodes` |  |
| `left_child` | Left Child | Link → `Bisect Nodes` |  |
| `right_child` | Right Child | Link → `Bisect Nodes` |  |
| `period_from_date` | Period_from_date | Datetime |  |
| `period_to_date` | Period To Date | Datetime |  |
| `difference` | Difference | Number |  |
| `balance_sheet_summary` | Balance Sheet Summary | Number |  |
| `profit_loss_summary` | Profit and Loss Summary | Number |  |
| `generated` | Generated | Boolean | défaut `non` |

## Budget

*Budget* — `accounts/budget.yaml` · soumis

- **Numérotation** : série `BUDG-{YYYY}-{#####}`
- **Titre** : `company`
- **Icône** : `piggy-bank`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `budget_against` | Budget Against | Select — Cost Center · Project | **requis**; colonne de liste; défaut `Cost Center` |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |
| `applicable_on_material_request` | Applicable on Material Request | Boolean | défaut `non` |
| `action_if_annual_budget_exceeded_on_mr` | Action if Annual Budget Exceeded on MR | Select — Stop · Warn · Ignore | défaut `Stop` |
| `action_if_accumulated_monthly_budget_exceeded_on_mr` | Action if Accumulated Monthly Budget Exceeded on MR | Select — Stop · Warn · Ignore | défaut `Warn` |
| `applicable_on_purchase_order` | Applicable on Purchase Order | Boolean | défaut `non` |
| `action_if_annual_budget_exceeded_on_po` | Action if Annual Budget Exceeded on PO | Select — Stop · Warn · Ignore | défaut `Stop` |
| `action_if_accumulated_monthly_budget_exceeded_on_po` | Action if Accumulated Monthly Budget Exceeded on PO | Select — Stop · Warn · Ignore | défaut `Warn` |
| `applicable_on_booking_actual_expenses` | Applicable on booking actual expenses | Boolean | défaut `non` |
| `action_if_annual_budget_exceeded` | Action if Annual Budget Exceeded on Actual | Select — Stop · Warn · Ignore | défaut `Stop` |
| `action_if_accumulated_monthly_budget_exceeded` | Action if Accumulated Monthly Budget Exceeded on Actual | Select — Stop · Warn · Ignore | défaut `Warn` |
| `naming_series` | Series | Select — BUDGET-.######## | **requis**; défaut `BUDGET-.########` |
| `applicable_on_cumulative_expense` | Applicable on Cumulative Expense | Boolean | défaut `non`; — (Purchase Order + Material Request + Actual Expense) |
| `action_if_annual_exceeded_on_cumulative_expense` | Action if Anual Budget Exceeded on Cumulative Expense | Select — Stop · Warn · Ignore |  |
| `action_if_accumulated_monthly_exceeded_on_cumulative_expense` | Action if Accumulative Monthly Budget Exceeded on Cumulative Expense | Select — Stop · Warn · Ignore |  |
| `budget_distribution` | Budget Distribution | Table → `Budget Distribution` |  |
| `account` | Account | Link → `Account` | **requis**; colonne de liste |
| `budget_amount` | Budget Amount | Currency | **requis**; devise de `company.default_currency` |
| `revision_of` | Revision Of | Text | lecture seule |
| `distribute_equally` | Distribute Equally | Boolean | défaut `oui` |
| `from_fiscal_year` | From Fiscal Year | Link → `Fiscal Year` | **requis** |
| `to_fiscal_year` | To Fiscal Year | Link → `Fiscal Year` | **requis** |
| `budget_start_date` | Budget Start Date | Date | masqué |
| `budget_end_date` | Budget End Date | Date | masqué |
| `distribution_frequency` | Distribution Frequency | Select — Monthly · Quarterly · Half-Yearly · Yearly | **requis**; défaut `Monthly` |
| `budget_distribution_total` | Budget Distribution Total | Currency | lecture seule; devise de `company.default_currency` |

## Budget Distribution

*Budget Distribution* — `accounts/budget_distribution.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `start_date` | Start Date | Date | **requis**; colonne de liste; lecture seule |
| `end_date` | End Date | Date | **requis**; colonne de liste; lecture seule |
| `amount` | Amount | Currency | **requis**; colonne de liste; devise de `parent_company.default_currency` |
| `percent` | Percent | Percent | **requis**; colonne de liste |

## Campaign Item

*Campaign Item* — `accounts/campaign_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `campaign` | Campaign | Link → `UTM Campaign` | colonne de liste |

## Cashier Closing

*Cashier Closing* — `accounts/cashier_closing.yaml` · soumis

- **Numérotation** : série `CC-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `user`
- **Icône** : `lock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — POS-CLO- | lecture seule; défaut `POS-CLO-` |
| `user` | User | Text | **requis**; colonne de liste; lecture seule |
| `date` | Date | Date | lecture seule |
| `from_time` | From Time | Time | **requis** |
| `time` | To Time | Time | **requis** |
| `expense` | Expense | Number | défaut `0.0` |
| `custody` | Custody | Number | défaut `0.0` |
| `returns` | Returns | Number | défaut `0.0` |
| `outstanding_amount` | Outstanding Amount | Number | lecture seule |
| `payments` | Payments | Table → `Cashier Closing Payments` |  |
| `net_amount` | Net Amount | Number | colonne de liste; lecture seule |

## Cashier Closing Payments

*Cashier Closing Payments* — `accounts/cashier_closing_payments.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` | **requis**; colonne de liste |
| `amount` | Amount | Number | colonne de liste; défaut `0.0` |

## Chart of Accounts Importer

*Chart of Accounts Importer* — `accounts/chart_of_accounts_importer.yaml`

- **Titre** : `company`
- **Icône** : `file-input`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | colonne de liste |
| `import_file` | Attach custom Chart of Accounts file | Attach |  |

## Cheque Print Template

*Cheque Print Template* — `accounts/cheque_print_template.yaml`

- **Titre** : `bank_name`
- **Icône** : `printer`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `has_print_format` | Has Print Format | Boolean | lecture seule; masqué |
| `bank_name` | Bank Name | Text | **requis**; colonne de liste |
| `cheque_size` | Cheque Size | Select — Regular · A4 | défaut `Regular` |
| `starting_position_from_top_edge` | Starting position from top edge | Number |  |
| `cheque_width` | Cheque Width | Number | défaut `20.0` |
| `cheque_height` | Cheque Height | Number | défaut `9.0` |
| `scanned_cheque` | Scanned Cheque | Attach |  |
| `is_account_payable` | Is Account Payable | Boolean | défaut `oui` |
| `acc_pay_dist_from_top_edge` | Distance from top edge | Number | défaut `1.0` |
| `acc_pay_dist_from_left_edge` | Distance from left edge | Number | défaut `9.0` |
| `message_to_show` | Message to show | Text | défaut `Acc. Payee` |
| `date_dist_from_top_edge` | Distance from top edge | Number | défaut `1.0` |
| `date_dist_from_left_edge` | Starting location from left edge | Number | défaut `15.0` |
| `payer_name_from_top_edge` | Distance from top edge | Number | défaut `2.0` |
| `payer_name_from_left_edge` | Starting location from left edge | Number | défaut `3.0` |
| `amt_in_words_from_top_edge` | Distance from top edge | Number | défaut `3.0` |
| `amt_in_words_from_left_edge` | Starting location from left edge | Number | défaut `4.0` |
| `amt_in_word_width` | Width of amount in word | Number | défaut `15.0` |
| `amt_in_words_line_spacing` | Line spacing for amount in words | Number | défaut `0.5` |
| `amt_in_figures_from_top_edge` | Distance from top edge | Number | défaut `3.5` |
| `amt_in_figures_from_left_edge` | Starting location from left edge | Number | défaut `16.0` |
| `acc_no_dist_from_top_edge` | Distance from top edge | Number | défaut `5.0` |
| `acc_no_dist_from_left_edge` | Starting location from left edge | Number | défaut `4.0` |
| `signatory_from_top_edge` | Distance from top edge | Number | défaut `6.0` |
| `signatory_from_left_edge` | Starting location from left edge | Number | défaut `15.0` |

## Closed Document

*Closed Document* — `accounts/closed_document.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `document_type` | Document Type | Text | **requis**; colonne de liste |
| `closed` | Closed | Boolean | colonne de liste; défaut `non` |

## Cost Center

*Cost Center* — `accounts/cost_center.yaml`

- **Vues** : tree (parent `parent_cost_center`)
- **Titre** : `company`
- **Icône** : `chart-pie`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `cost_center_name` | Cost Center Name | Text | **requis**; colonne de liste |
| `cost_center_number` | Cost Center Number | Text | colonne de liste |
| `parent_cost_center` | Parent Cost Center | Link → `Cost Center` | colonne de liste |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `is_group` | Is Group | Boolean | défaut `non` |
| `lft` | lft | Int | masqué |
| `rgt` | rgt | Int | masqué |
| `old_parent` | old_parent | Link → `Cost Center` | masqué |
| `disabled` | Disabled | Boolean | défaut `non` |

## Cost Center Allocation

*Cost Center Allocation* — `accounts/cost_center_allocation.yaml` · soumis

- **Numérotation** : série `CCA-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `company`
- **Icône** : `chart-pie`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `main_cost_center` | Main Cost Center | Link → `Cost Center` | **requis**; colonne de liste |
| `valid_from` | Valid From | Date | **requis**; colonne de liste; défaut `today` |
| `company` | Company | Link → `Company` | **requis** |
| `allocation_percentages` | Cost Center Allocation Percentages | Table → `Cost Center Allocation Percentage` |  |

## Cost Center Allocation Percentage

*Cost Center Allocation Percentage* — `accounts/cost_center_allocation_percentage.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `cost_center` | Cost Center | Link → `Cost Center` | **requis**; colonne de liste |
| `percentage` | Percentage (%) | Percent | **requis**; colonne de liste |

## Coupon Code

*Coupon Code* — `accounts/coupon_code.yaml`

- **Vues** : calendar
- **Titre** : `customer`
- **Icône** : `ticket-percent`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `coupon_name` | Coupon Name | Text | **requis**; — e.g. "Summer Holiday 2019 Offer 20" |
| `coupon_type` | Coupon Type | Select — Promotional · Gift Card | **requis**; colonne de liste |
| `customer` | Customer | Link → `Customer` |  |
| `coupon_code` | Coupon Code | Text | — unique e.g. SAVE20  To be used to get discount |
| `pricing_rule` | Pricing Rule | Link → `Pricing Rule` |  |
| `valid_from` | Valid From | Date | colonne de liste |
| `valid_upto` | Valid Up To | Date |  |
| `maximum_use` | Maximum Use | Int |  |
| `used` | Used | Int | lecture seule |
| `description` | Coupon Description | TextEditor |  |
| `from_external_ecomm_platform` | From External Ecomm Platform | Boolean | défaut `non` |

## Currency Exchange Settings

*Currency Exchange Settings* — `accounts/currency_exchange_settings.yaml` · document unique

- **Titre** : `api_endpoint`
- **Icône** : `refresh-cw`
- **Permissions explicites** — `create` : 0, `delete` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `api_endpoint` | API Endpoint | Text | **requis**; colonne de liste |
| `url` | Example URL | Text | lecture seule |
| `req_params` | Parameters | Table → `Currency Exchange Settings Details` |  |
| `result_key` | Result Key | Table → `Currency Exchange Settings Result` |  |
| `service_provider` | Service Provider | Select — frankfurter.dev · exchangerate.host · frankfurter.dev - v2 · Custom | **requis** |
| `disabled` | Disabled | Boolean | défaut `non` |
| `access_key` | Access Key | Text |  |
| `use_http` | Use HTTP Protocol | Boolean | défaut `non` |

## Currency Exchange Settings Details

*Currency Exchange Settings Details* — `accounts/currency_exchange_settings_details.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `key` | Key | Text | **requis**; colonne de liste |
| `value` | Value | Text | **requis**; colonne de liste |

## Currency Exchange Settings Result

*Currency Exchange Settings Result* — `accounts/currency_exchange_settings_result.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `key` | Key | Text | **requis**; colonne de liste |

## Customer Group Item

*Customer Group Item* — `accounts/customer_group_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `customer_group` | Customer Group | Link → `Customer Group` | colonne de liste |

## Customer Item

*Customer Item* — `accounts/customer_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `customer` | Customer  | Link → `Customer` | colonne de liste |

## Discounted Invoice

*Discounted Invoice* — `accounts/discounted_invoice.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `sales_invoice` | Invoice | Link → `Sales Invoice` | **requis**; colonne de liste |
| `customer` | Customer | Link → `Customer` | colonne de liste; lecture seule |
| `posting_date` | Date | Date | colonne de liste; lecture seule |
| `outstanding_amount` | Outstanding Amount | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `debit_to` | Debit to | Link → `Account` | lecture seule |

## Dunning

*Dunning* — `accounts/dunning.yaml` · soumis

- **Numérotation** : série `DUNN-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `customer`
- **Icône** : `bell-ring`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis** |
| `naming_series` | Series | Select — DUNN-.MM.-.YY.- | défaut `DUNN-.MM.-.YY.-` |
| `customer_name` | Customer Name | Text | colonne de liste; lecture seule; recopié de `customer.customer_name` |
| `posting_date` | Date | Date | **requis**; défaut `today` |
| `dunning_type` | Dunning Type | Link → `Dunning Type` | colonne de liste |
| `dunning_fee` | Dunning Fee | Currency | devise de `currency` |
| `language` | Print Language | Link → `Language` |  |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `body_text` | Body Text | TextEditor |  |
| `closing_text` | Closing Text | TextEditor |  |
| `posting_time` | Posting Time | Time |  |
| `rate_of_interest` | Rate of Interest (%) Yearly | Number | défaut `0.0` |
| `address_display` | Address | TextEditor | lecture seule |
| `contact_display` | Contact | LongText | lecture seule |
| `contact_mobile` | Mobile No | LongText | lecture seule |
| `company_address_display` | Company Address Display | TextEditor | lecture seule |
| `contact_email` | Contact Email | Text | lecture seule |
| `customer` | Customer | Link → `Customer` | **requis** |
| `grand_total` | Grand Total | Currency | lecture seule; devise de `currency` |
| `status` | Status | Select — Draft · Resolved · Unresolved · Cancelled | lecture seule; défaut `Draft` |
| `income_account` | Income Account | Link → `Account` | — For dunning fee and interest |
| `overdue_payments` | Overdue Payments | Table → `Overdue Payment` |  |
| `total_interest` | Total Interest | Currency | lecture seule; devise de `currency` |
| `total_outstanding` | Total Outstanding | Currency | lecture seule; devise de `currency` |
| `customer_address` | Customer Address | Link → `Address` |  |
| `contact_person` | Contact Person | Link → `Contact` |  |
| `dunning_amount` | Dunning Amount | Currency | lecture seule; devise de `currency` |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `spacer` | Spacer | Text | lecture seule; masqué |
| `company_address` | Company Address | Link → `Address` |  |
| `currency` | Currency | Link → `Currency` |  |
| `conversion_rate` | Conversion Rate | Number |  |
| `base_dunning_amount` | Dunning Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |

## Dunning Letter Text

*Dunning Letter Text* — `accounts/dunning_letter_text.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `language` | Language | Link → `Language` | colonne de liste |
| `is_default_language` | Is Default Language | Boolean | défaut `non` |
| `body_text` | Body Text | TextEditor | colonne de liste; — Letter or Email Body Text |
| `closing_text` | Closing Text | TextEditor | colonne de liste; — Letter or Email Closing Text |

## Dunning Type

*Dunning Type* — `accounts/dunning_type.yaml`

- **Titre** : `company`
- **Icône** : `bell`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `dunning_type` | Dunning Type | Text | **requis**; colonne de liste |
| `dunning_fee` | Dunning Fee | Currency | colonne de liste; devise de `company.default_currency` |
| `dunning_letter_text` | Dunning Letter Text | Table → `Dunning Letter Text` |  |
| `rate_of_interest` | Rate of Interest (%) Yearly | Number | colonne de liste |
| `is_default` | Is Default | Boolean | défaut `non` |
| `income_account` | Income Account | Link → `Account` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `company` | Company | Link → `Company` | **requis** |

## Exchange Rate Revaluation

*Exchange Rate Revaluation* — `accounts/exchange_rate_revaluation.yaml` · soumis

- **Numérotation** : série `ERR-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `company`
- **Icône** : `arrow-right-left`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `posting_date` | Posting Date | Date | **requis**; colonne de liste; défaut `today` |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `accounts` | Exchange Rate Revaluation Account | Table → `Exchange Rate Revaluation Account` |  |
| `gain_loss_unbooked` | Gain/Loss from Revaluation | Currency | lecture seule; devise de `company.default_currency` |
| `gain_loss_booked` | Gain/Loss already booked | Currency | lecture seule; devise de `company.default_currency`; — Gain/Loss accumulated in foreign currency account. Accounts with '0' balance in either Base or Account currenc |
| `total_gain_loss` | Total Gain/Loss | Currency | lecture seule; devise de `company.default_currency` |
| `rounding_loss_allowance` | Rounding Loss Allowance | Number | défaut `0.05`; — Only values between [0,1) are allowed. Like {0.00, 0.04, 0.09, ...} Ex: If allowance is set at 0.07, accounts  |

## Exchange Rate Revaluation Account

*Exchange Rate Revaluation Account* — `accounts/exchange_rate_revaluation_account.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `account` | Account | Link → `Account` | **requis**; colonne de liste |
| `party_type` | Party Type | Text |  |
| `party` | Party | DynamicLink → `party_type` |  |
| `account_currency` | Account Currency | Link → `Currency` | lecture seule |
| `balance_in_account_currency` | Balance In Account Currency | Currency | lecture seule; devise de `account_currency` |
| `current_exchange_rate` | Current Exchange Rate | Number | lecture seule |
| `balance_in_base_currency` | Balance In Base Currency | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `new_exchange_rate` | New Exchange Rate | Number | **requis**; colonne de liste |
| `new_balance_in_base_currency` | New Balance In Base Currency | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `gain_loss` | Gain/Loss | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `zero_balance` | Zero Balance | Boolean | défaut `non`; — This Account has '0' balance in either Base Currency or Account Currency |
| `new_balance_in_account_currency` | New Balance In Account Currency | Currency | lecture seule; devise de `account_currency` |

## Finance Book

*Finance Book* — `accounts/finance_book.yaml`

- **Icône** : `book`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `finance_book_name` | Name | Text |  |

## Financial Report Row

*Financial Report Row* — `accounts/financial_report_row.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `reference_code` | Line Reference | Text | colonne de liste; — Code to reference this line in formulas (e.g., REV100, EXP200, ASSET100) |
| `display_name` | Display Name | Text | colonne de liste; — Text displayed on the financial statement (e.g., 'Total Revenue', 'Cash and Cash Equivalents') |
| `indentation_level` | Indent Level | Int | colonne de liste; — Indentation level: 0 = Main heading, 1 = Sub-category, 2 = Individual accounts, etc. |
| `data_source` | Data Source | Select — Account Data · Calculated Amount · Custom API · Blank Line · Column Break · Section Break | colonne de liste; — How this line gets its data |
| `balance_type` | Balance Type | Select — Opening Balance · Closing Balance · Period Movement (Debits - Credits) | colonne de liste; — Opening Balance = Start of period, Closing Balance = End of period, Period Movement = Net change during period |
| `bold_text` | Bold Text | Boolean | défaut `non`; — Bold text for emphasis (totals, major headings) |
| `italic_text` | Italic Text | Boolean | défaut `non`; — Italic text for subtotals or notes |
| `hidden_calculation` | Hidden Line (Internal Use Only) | Boolean | défaut `non`; — Calculate but don't show on final report |
| `hide_when_empty` | Hide If Zero | Boolean | défaut `non`; — Hide this line if amount is zero |
| `reverse_sign` | Reverse Sign | Boolean | colonne de liste; défaut `non`; — Show negative values as positive (for expenses in P&L) |
| `calculation_formula` | Formula or Account Filter | Code |  |
| `include_in_charts` | Include in Charts | Boolean | défaut `non`; — If enabled, this row's values will be displayed on financial charts |
| `color` | Color | Color | — Color to highlight values (e.g., red for exceptions) |
| `fieldtype` | Value Type | Select — Currency · Float · Int · Percent | — How to format and present values in the financial report (only if different from column fieldtype) |
| `advanced_filtering` | Advanced Filtering | Boolean | défaut `non`; — Use <strong>Python</strong> filters to get Accounts |

## Financial Report Template

*Financial Report Template* — `accounts/financial_report_template.yaml`

- **Titre** : `template_name`
- **Icône** : `file-spreadsheet`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `template_name` | Template Name | Text | **requis**; colonne de liste; — Descriptive name for your template (e.g., 'Standard P&L', 'Detailed Balance Sheet') |
| `report_type` | Report Type | Select — Profit and Loss Statement · Balance Sheet · Cash Flow · Custom Financial Statement | **requis**; colonne de liste; — Type of financial statement this template generates |
| `module` | Module (for Export) | Link → `Module Def` |  |
| `rows` | Report Line Items | Table → `Financial Report Row` |  |
| `disabled` | Disabled | Boolean | défaut `non`; — Disable template to prevent use in reports |

## Fiscal Year

*Fiscal Year* — `accounts/fiscal_year.yaml`

- **Titre** : `year`
- **Icône** : `calendar`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `year` | Year Name | Text | **requis**; colonne de liste; — For e.g. 2012, 2012-13 |
| `disabled` | Disabled | Boolean | défaut `non` |
| `year_start_date` | Year Start Date | Date | **requis**; colonne de liste |
| `year_end_date` | Year End Date | Date | **requis**; colonne de liste |
| `companies` | Companies | Table → `Fiscal Year Company` |  |
| `auto_created` | Auto Created | Boolean | lecture seule; masqué |
| `is_short_year` | Is Short/Long Year | Boolean | défaut `non`; — More/Less than 12 months. |

## Fiscal Year Company

*Fiscal Year Company* — `accounts/fiscal_year_company.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |

## GL Entry

*GL Entry* — `accounts/gl_entry.yaml` · soumis

- **Numérotation** : série `GE-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `company`
- **Icône** : `book-open`
- **Permissions explicites** — `write` : 0, `create` : 0, `delete` : 0, `submit` : 0, `cancel` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `posting_date` | Posting Date | Date | colonne de liste |
| `transaction_date` | Transaction Date | Date | colonne de liste |
| `account` | Account | Link → `Account` | colonne de liste |
| `party_type` | Party Type | Text |  |
| `party` | Party | DynamicLink → `party_type` |  |
| `cost_center` | Cost Center | Link → `Cost Center` | colonne de liste |
| `debit` | Debit Amount | Currency | devise de `company.default_currency` |
| `credit` | Credit Amount | Currency | devise de `company.default_currency` |
| `account_currency` | Account Currency | Link → `Currency` |  |
| `debit_in_account_currency` | Debit Amount in Account Currency | Currency | devise de `account_currency` |
| `credit_in_account_currency` | Credit Amount in Account Currency | Currency | devise de `account_currency` |
| `against` | Against | LongText |  |
| `against_voucher_type` | Against Voucher Type | Text |  |
| `against_voucher` | Against Voucher | DynamicLink → `against_voucher_type` |  |
| `voucher_type` | Voucher Type | Text |  |
| `voucher_no` | Voucher No | DynamicLink → `voucher_type` |  |
| `voucher_detail_no` | Voucher Detail No | Text | lecture seule |
| `project` | Project | Link → `Project` |  |
| `remarks` | Remarks | LongText |  |
| `is_opening` | Is Opening | Select — No · Yes |  |
| `is_advance` | Is Advance | Select — No · Yes |  |
| `fiscal_year` | Fiscal Year | Link → `Fiscal Year` |  |
| `company` | Company | Link → `Company` |  |
| `finance_book` | Finance Book | Link → `Finance Book` |  |
| `to_rename` | To Rename | Boolean | masqué; défaut `oui` |
| `due_date` | Due Date | Date |  |
| `is_cancelled` | Is Cancelled | Boolean | défaut `non` |
| `transaction_currency` | Transaction Currency | Link → `Currency` |  |
| `transaction_exchange_rate` | Transaction Exchange Rate | Number |  |
| `debit_in_transaction_currency` | Debit Amount in Transaction Currency | Currency | devise de `transaction_currency` |
| `credit_in_transaction_currency` | Credit Amount in Transaction Currency | Currency | devise de `transaction_currency` |
| `voucher_subtype` | Voucher Subtype | LongText |  |
| `debit_in_reporting_currency` | Debit Amount in Reporting Currency | Currency | devise de `company.reporting_currency` |
| `credit_in_reporting_currency` | Credit Amount in Reporting Currency | Currency | devise de `company.reporting_currency` |
| `reporting_currency_exchange_rate` | Reporting Currency Exchange Rate | Number |  |

## Invoice Discounting

*Invoice Discounting* — `accounts/invoice_discounting.yaml` · soumis

- **Numérotation** : série `ID-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `company`
- **Icône** : `ticket-percent`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `posting_date` | Posting Date | Date | **requis**; colonne de liste; défaut `today` |
| `loan_start_date` | Loan Start Date | Date |  |
| `loan_period` | Loan Period (Days) | Int |  |
| `loan_end_date` | Loan End Date | Date | lecture seule |
| `status` | Status | Select — Draft · Sanctioned · Disbursed · Settled · Cancelled | lecture seule |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `invoices` | Invoices | Table → `Discounted Invoice` |  |
| `total_amount` | Total Amount | Currency | lecture seule; devise de `company.default_currency` |
| `bank_charges` | Bank Charges | Currency | devise de `company.default_currency` |
| `short_term_loan` | Short Term Loan Account | Link → `Account` | **requis** |
| `bank_account` | Bank Account | Link → `Account` | **requis** |
| `bank_charges_account` | Bank Charges Account | Link → `Account` | **requis** |
| `accounts_receivable_credit` | Accounts Receivable Credit Account | Link → `Account` | **requis** |
| `accounts_receivable_discounted` | Accounts Receivable Discounted Account | Link → `Account` | **requis** |
| `accounts_receivable_unpaid` | Accounts Receivable Unpaid Account | Link → `Account` | **requis** |

## Item Tax Template

*Item Tax Template* — `accounts/item_tax_template.yaml`

- **Titre** : `company`
- **Icône** : `circle-percent`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text | **requis**; colonne de liste |
| `taxes` | Tax Rates | Table → `Item Tax Template Detail` |  |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `disabled` | Disabled | Boolean | défaut `non` |

## Item Tax Template Detail

*Item Tax Template Detail* — `accounts/item_tax_template_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `tax_type` | Tax | Link → `Account` | **requis**; colonne de liste |
| `tax_rate` | Tax Rate | Number | colonne de liste |
| `not_applicable` | Not Applicable | Boolean | colonne de liste; défaut `non`; — Check if this tax is not applicable to items (distinct from 0% rate) |

## Item Wise Tax Detail

*Item Wise Tax Detail* — `accounts/item_wise_tax_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_row` | Item Row | Text | **requis**; colonne de liste |
| `tax_row` | Tax Row | Text | **requis**; colonne de liste |
| `rate` | Tax Rate | Number | colonne de liste |
| `amount` | Tax Amount | Currency | colonne de liste; devise de `parent_currency` |
| `taxable_amount` | Taxable Amount | Currency | colonne de liste; devise de `parent_currency` |

## Journal Entry

*Journal Entry* — `accounts/journal_entry.yaml` · soumis

- **Numérotation** : série `JE-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `company`
- **Icône** : `notebook-pen`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text | masqué |
| `voucher_type` | Entry Type | Select — Journal Entry · Inter Company Journal Entry · Bank Entry · Cash Entry · Credit Card Entry · Debit Note · Credit Note · Contra Entry · Excise Entry · Write Off Entry · Opening Entry · Depreciation Entry · Asset Disposal · Periodic Accounting Entry · Exchange Rate Revaluation · Exchange Gain Or Loss · Deferred Revenue · Deferred Expense | **requis**; défaut `Journal Entry` |
| `naming_series` | Series | Select — ACC-JV-.YYYY.- | **requis** |
| `posting_date` | Posting Date | Date | **requis** |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `finance_book` | Finance Book | Link → `Finance Book` | lecture seule |
| `accounts` | Accounting Entries | Table → `Journal Entry Account` |  |
| `cheque_no` | Reference Number | Text | visible si `voucher_type in ['Bank Entry', 'Credit Card Entry']`; obligatoire si `voucher_type == 'Bank Entry'` |
| `cheque_date` | Reference Date | Date | visible si `voucher_type in ['Bank Entry', 'Credit Card Entry']`; obligatoire si `voucher_type == 'Bank Entry'` |
| `user_remark` | User Remark | LongText | masqué |
| `total_debit` | Total Debit | Currency | colonne de liste; lecture seule; devise de `company.default_currency` |
| `total_credit` | Total Credit | Currency | lecture seule; devise de `company.default_currency` |
| `difference` | Difference (Dr - Cr) | Currency | lecture seule; devise de `company.default_currency` |
| `multi_currency` | Multi Currency | Boolean | défaut `non` |
| `total_amount_currency` | Total Amount Currency | Link → `Currency` | lecture seule; masqué |
| `total_amount` | Total Amount | Currency | lecture seule; masqué; devise de `total_amount_currency` |
| `total_amount_in_words` | Total Amount in Words | Text | lecture seule; masqué |
| `clearance_date` | Clearance Date | Date | lecture seule |
| `remark` | Remark | LongText |  |
| `inter_company_journal_entry_reference` | Inter Company Journal Entry Reference | Link → `Journal Entry` | lecture seule; visible si `voucher_type == 'Inter Company Journal Entry'` |
| `bill_no` | Bill No | Text |  |
| `bill_date` | Bill Date | Date |  |
| `due_date` | Due Date | Date |  |
| `write_off_based_on` | Write Off Based On | Select — Accounts Receivable · Accounts Payable | défaut `Accounts Receivable`; visible si `voucher_type == 'Write Off Entry'` |
| `write_off_amount` | Write Off Amount | Currency | devise de `company.default_currency`; visible si `voucher_type == 'Write Off Entry'` |
| `pay_to_recd_from` | Pay To / Recd From | Text |  |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `select_print_heading` | Print Heading | Link → `Print Heading` |  |
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` |  |
| `payment_order` | Payment Order | Link → `Payment Order` | lecture seule |
| `is_opening` | Is Opening | Select — No · Yes | défaut `No` |
| `stock_entry` | Stock Entry | Link → `Stock Entry` | lecture seule |
| `auto_repeat` | Auto Repeat | Link → `Auto Repeat` | lecture seule |
| `from_template` | From Template | Link → `Journal Entry Template` |  |
| `tax_withholding_category` | Tax Withholding Category | Link → `Tax Withholding Category` |  |
| `apply_tds` | Consider for Tax Withholding  | Boolean | défaut `non` |
| `reversal_of` | Reversal Of | Link → `Journal Entry` | lecture seule |
| `process_deferred_accounting` | Process Deferred Accounting | Link → `Process Deferred Accounting` | lecture seule |
| `is_system_generated` | Is System Generated | Boolean | lecture seule |
| `periodic_entry_difference_account` | Periodic Entry Difference Account | Link → `Account` | visible si `voucher_type == 'Periodic Accounting Entry'` |
| `for_all_stock_asset_accounts` | For All Stock Asset Accounts | Boolean | défaut `oui`; visible si `voucher_type == 'Periodic Accounting Entry'` |
| `stock_asset_account` | Stock Asset Account | Link → `Account` | visible si `voucher_type == 'Periodic Accounting Entry'` |
| `party_not_required` | Party Not Required | Boolean | masqué; défaut `non` |
| `tax_withholding_group` | Tax Withholding Group | Link → `Tax Withholding Group` |  |
| `ignore_tax_withholding_threshold` | Ignore Tax Withholding Threshold | Boolean | défaut `non` |
| `override_tax_withholding_entries` | Edit Tax Withholding Entries | Boolean | défaut `non` |
| `tax_withholding_entries` | Tax Withholding Entries | Table → `Tax Withholding Entry` |  |
| `custom_remark` | Custom Remark | Boolean | défaut `non` |

## Journal Entry Account

*Journal Entry Account* — `accounts/journal_entry_account.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `account` | Account | Link → `Account` | **requis**; colonne de liste |
| `account_type` | Account Type | Text | masqué |
| `cost_center` | Cost Center | Link → `Cost Center` | — If Income or Expense |
| `party_type` | Party Type | Text | colonne de liste |
| `party` | Party | DynamicLink → `party_type` | colonne de liste |
| `account_currency` | Account Currency | Link → `Currency` | lecture seule |
| `exchange_rate` | Exchange Rate | Number |  |
| `debit_in_account_currency` | Debit | Currency | colonne de liste; devise de `account_currency` |
| `debit` | Debit in Company Currency | Currency | lecture seule; devise de `parent_company.default_currency` |
| `credit_in_account_currency` | Credit | Currency | colonne de liste; devise de `account_currency` |
| `credit` | Credit in Company Currency | Currency | lecture seule; devise de `parent_company.default_currency` |
| `reference_type` | Reference Type | Text |  |
| `reference_name` | Reference Name | DynamicLink → `reference_type` |  |
| `reference_due_date` | Reference Due Date | Date |  |
| `project` | Project | Link → `Project` |  |
| `is_advance` | Is Advance | Select — No · Yes |  |
| `user_remark` | User Remark | LongText |  |
| `against_account` | Against Account | LongText | masqué |
| `bank_account` | Bank Account | Link → `Bank Account` |  |
| `reference_detail_no` | Reference Detail No | Text | masqué |
| `advance_voucher_type` | Advance Voucher Type | Text | lecture seule |
| `advance_voucher_no` | Advance Voucher No | DynamicLink → `advance_voucher_type` | lecture seule |
| `is_tax_withholding_account` | Is Tax Withholding Account | Boolean | lecture seule |

## Journal Entry Template

*Journal Entry Template* — `accounts/journal_entry_template.yaml`

- **Titre** : `company`
- **Icône** : `notebook-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `voucher_type` | Journal Entry Type | Select — Journal Entry · Inter Company Journal Entry · Bank Entry · Cash Entry · Credit Card Entry · Debit Note · Credit Note · Contra Entry · Excise Entry · Write Off Entry · Opening Entry · Depreciation Entry · Exchange Rate Revaluation | **requis**; colonne de liste |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `is_opening` | Is Opening | Select — No · Yes | défaut `No` |
| `accounts` | Accounting Entries | Table → `Journal Entry Template Account` |  |
| `template_title` | Template Title | Text | **requis** |
| `multi_currency` | Multi Currency | Boolean | défaut `non` |

## Journal Entry Template Account

*Journal Entry Template Account* — `accounts/journal_entry_template_account.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `account` | Account | Link → `Account` | **requis**; colonne de liste |
| `party_type` | Party Type | Text | colonne de liste |
| `party` | Party | DynamicLink → `party_type` | colonne de liste |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |

## Ledger Health

*Ledger Health* — `accounts/ledger_health.yaml`

- **Icône** : `heart-pulse`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `voucher_type` | Voucher Type | Text |  |
| `voucher_no` | Voucher No | Text |  |
| `debit_credit_mismatch` | Debit-Credit mismatch | Boolean | défaut `non` |
| `checked_on` | Checked On | Datetime |  |
| `general_and_payment_ledger_mismatch` | General and Payment Ledger mismatch | Boolean | défaut `non` |

## Ledger Health Monitor

*Ledger Health Monitor* — `accounts/ledger_health_monitor.yaml`

- **Icône** : `activity`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `enable_health_monitor` | Enable Health Monitor | Boolean | défaut `non` |
| `debit_credit_mismatch` | Debit-Credit Mismatch | Boolean | défaut `non` |
| `general_and_payment_ledger_mismatch` | Discrepancy between General and Payment Ledger | Boolean | défaut `non` |
| `monitor_for_last_x_days` | Monitor for Last 'X' days | Int | **requis**; colonne de liste; défaut `60` |
| `companies` | Companies | Table → `Ledger Health Monitor Company` |  |

## Ledger Health Monitor Company

*Ledger Health Monitor Company* — `accounts/ledger_health_monitor_company.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | colonne de liste |

## Ledger Merge

*Ledger Merge* — `accounts/ledger_merge.yaml`

- **Titre** : `account_name`
- **Icône** : `merge`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `account` | Account | Link → `Account` | **requis** |
| `merge_accounts` | Accounts to Merge | Table → `Ledger Merge Accounts` |  |
| `company` | Company | Link → `Company` | **requis** |
| `status` | Status | Select — Pending · Success · Partial Success · Error | colonne de liste; lecture seule |
| `root_type` | Root Type | Select — Asset · Liability · Income · Expense · Equity | **requis** |
| `account_name` | Account Name | Text | **requis**; lecture seule |
| `is_group` | Is Group | Boolean | lecture seule |

## Ledger Merge Accounts

*Ledger Merge Accounts* — `accounts/ledger_merge_accounts.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `account` | Account | Link → `Account` | **requis**; colonne de liste |
| `merged` | Merged | Boolean | colonne de liste; lecture seule |
| `account_name` | Account Name | Text | **requis**; lecture seule |

## Loan

*Loan* — `accounts/loan.yaml`

- **Titre** : `applicant`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `applicant_type` | Applicant Type | Select — Employee · Customer · Member | **requis** |
| `applicant` | Applicant | Text | **requis**; colonne de liste |
| `company` | Company | Link → `Company` | **requis** |
| `loan_product` | Loan Product | Link → `Loan Product` | **requis** |
| `loan_amount` | Loan Amount | Currency | **requis**; devise de `company.default_currency` |
| `rate_of_interest` | Rate of Interest | Percent |  |
| `posting_date` | Posting Date | Date | **requis** |
| `repayment_periods` | Repayment Periods | Int |  |
| `status` | Status | Select — Draft · Sanctioned ·  disbursed · Closed · Written Off | colonne de liste |

## Loan Product

*Loan Product* — `accounts/loan_product.yaml`

- **Titre** : `product_name`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `product_name` | Product Name | Text | **requis**; colonne de liste |
| `company` | Company | Link → `Company` | **requis** |
| `rate_of_interest` | Rate of Interest | Percent |  |
| `maximum_loan_amount` | Maximum Loan Amount | Currency | devise de `company.default_currency` |
| `repayment_method` | Repayment Method | Select — Repay Over Number of Periods · Repay Fixed Amount per Period |  |
| `is_active` | Active | Boolean | défaut `oui` |

## Loan Repayment

*Loan Repayment* — `accounts/loan_repayment.yaml`

- **Titre** : `loan`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `loan` | Loan | Link → `Loan` | **requis**; colonne de liste |
| `posting_date` | Posting Date | Date | **requis** |
| `amount_paid` | Amount Paid | Currency | **requis** |
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` |  |
| `reference_number` | Reference Number | Text |  |
| `status` | Status | Select — Draft · Paid · Unpaid · Cancelled |  |

## Loyalty Point Entry

*Loyalty Point Entry* — `accounts/loyalty_point_entry.yaml`

- **Vues** : calendar
- **Titre** : `customer`
- **Icône** : `star`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `loyalty_program` | Loyalty Program | Link → `Loyalty Program` | **requis** |
| `loyalty_program_tier` | Loyalty Program Tier | Text |  |
| `customer` | Customer | Link → `Customer` | **requis**; colonne de liste |
| `redeem_against` | Redeem Against | Link → `Loyalty Point Entry` |  |
| `loyalty_points` | Loyalty Points | Int | **requis**; colonne de liste |
| `purchase_amount` | Purchase Amount | Currency | devise de `company.default_currency` |
| `expiry_date` | Expiry Date | Date | **requis**; colonne de liste |
| `posting_date` | Posting Date | Date | **requis** |
| `company` | Company | Link → `Company` | **requis** |
| `invoice_type` | Invoice Type | Text | **requis** |
| `invoice` | Invoice | DynamicLink → `invoice_type` | colonne de liste |
| `discretionary_reason` | Discretionary Reason | Text |  |

## Loyalty Program

*Loyalty Program* — `accounts/loyalty_program.yaml`

- **Vues** : calendar, gantt
- **Titre** : `company`
- **Icône** : `gift`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `loyalty_program_name` | Loyalty Program Name | Text | **requis**; colonne de liste |
| `loyalty_program_type` | Loyalty Program Type | Select — Single Tier Program · Multiple Tier Program |  |
| `from_date` | From Date | Date | **requis** |
| `to_date` | To Date | Date |  |
| `customer_group` | Customer Group | Link → `Customer Group` |  |
| `customer_territory` | Customer Territory | Link → `Territory` |  |
| `auto_opt_in` | Auto Opt In (For all customers) | Boolean | défaut `non` |
| `collection_rules` | Collection Rules | Table → `Loyalty Program Collection` |  |
| `conversion_factor` | Conversion Factor | Number | — 1 Loyalty Points = How much base currency? |
| `expiry_duration` | Expiry Duration (in days) | Int |  |
| `expense_account` | Expense Account | Link → `Account` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `company` | Company | Link → `Company` |  |
| `project` | Project | Link → `Project` |  |

## Loyalty Program Collection

*Loyalty Program Collection* — `accounts/loyalty_program_collection.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `tier_name` | Tier Name | Text | **requis**; colonne de liste |
| `min_spent` | Minimum Total Spent | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `collection_factor` | Collection Factor (=1 LP) | Currency | **requis**; colonne de liste; devise de `parent_company.default_currency`; — For how much spent = 1 Loyalty Point |

## Mode of Payment

*Mode of Payment* — `accounts/mode_of_payment.yaml`

- **Titre** : `mode_of_payment`
- **Icône** : `wallet`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `mode_of_payment` | Mode of Payment | Text | **requis**; colonne de liste |
| `type` | Type | Select — Cash · Bank · General · Phone |  |
| `accounts` | Accounts | Table → `Mode of Payment Account` |  |
| `enabled` | Enabled | Boolean | défaut `oui` |

## Mode of Payment Account

*Mode of Payment Account* — `accounts/mode_of_payment_account.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | colonne de liste |
| `default_account` | Default Account | Link → `Account` | colonne de liste; — Default account will be automatically updated in POS Invoice when this mode is selected. |

## Monthly Distribution

*Monthly Distribution* — `accounts/monthly_distribution.yaml`

- **Titre** : `distribution_id`
- **Icône** : `chart-bar`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `distribution_id` | Distribution Name | Text | **requis**; colonne de liste; — Name of the Monthly Distribution |
| `fiscal_year` | Fiscal Year | Link → `Fiscal Year` | colonne de liste |
| `percentages` | Monthly Distribution Percentages | Table → `Monthly Distribution Percentage` |  |

## Monthly Distribution Percentage

*Monthly Distribution Percentage* — `accounts/monthly_distribution_percentage.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `month` | Month | Text | **requis**; colonne de liste; lecture seule |
| `percentage_allocation` | Percentage Allocation | Number | colonne de liste |

## Opening Invoice Creation Tool

*Opening Invoice Creation Tool* — `accounts/opening_invoice_creation_tool.yaml`

- **Titre** : `company`
- **Icône** : `file-plus`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `create_missing_party` | Create Missing Party | Boolean | défaut `non` |
| `invoice_type` | Invoice Type | Select — Sales · Purchase | **requis**; colonne de liste |
| `invoices` | Invoices | Table → `Opening Invoice Creation Tool Item` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |

## Opening Invoice Creation Tool Item

*Opening Invoice Creation Tool Item* — `accounts/opening_invoice_creation_tool_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `party_type` | Party Type | Text | lecture seule; masqué |
| `party` | Party ID | DynamicLink → `party_type` | colonne de liste |
| `temporary_opening_account` | Temporary Opening Account | Link → `Account` |  |
| `posting_date` | Posting Date | Date | colonne de liste |
| `due_date` | Due Date | Date | colonne de liste |
| `item_name` | Item Name | Text | colonne de liste; défaut `Opening Invoice Item` |
| `currency` | Currency | Link → `Currency` | colonne de liste; — Currency of the outstanding amount. Defaults to the Company currency. |
| `outstanding_amount` | Outstanding Amount | Currency | **requis**; colonne de liste; devise de `currency` |
| `qty` | Quantity | Text | défaut `1`; — Must be positive. If the unit rate would change the opening amount through rounding, the invoice uses quantity |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `invoice_number` | Invoice Number | Text | — Reference number of the invoice from the previous system |
| `supplier_invoice_date` | Supplier Invoice Date | Date |  |
| `party_name` | Party Name | Text | colonne de liste |
| `project` | Project | Link → `Project` |  |

## Overdue Payment

*Overdue Payment* — `accounts/overdue_payment.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `payment_term` | Payment Term | Link → `Payment Term` | lecture seule |
| `description` | Description | LongText | lecture seule |
| `due_date` | Due Date | Date | lecture seule |
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` | lecture seule |
| `invoice_portion` | Invoice Portion | Percent | lecture seule |
| `payment_amount` | Payment Amount | Currency | lecture seule; devise de `parent_currency` |
| `outstanding` | Outstanding | Currency | colonne de liste; lecture seule; devise de `parent_currency` |
| `paid_amount` | Paid Amount | Currency | devise de `parent_currency` |
| `discounted_amount` | Discounted Amount | Currency | lecture seule; devise de `parent_currency` |
| `sales_invoice` | Sales Invoice | Link → `Sales Invoice` | **requis**; colonne de liste; lecture seule |
| `payment_schedule` | Payment Schedule | Text | lecture seule |
| `overdue_days` | Overdue Days | Text | colonne de liste; lecture seule |
| `dunning_level` | Dunning Level | Int | colonne de liste; lecture seule |
| `interest` | Interest | Currency | colonne de liste; lecture seule; devise de `parent_currency` |

## Party Account

*Party Account* — `accounts/party_account.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `account` | Default Account | Link → `Account` | colonne de liste |
| `advance_account` | Advance Account | Link → `Account` | colonne de liste |

## Party Link

*Party Link* — `accounts/party_link.yaml`

- **Titre** : `primary_role`
- **Icône** : `link`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `primary_role` | Primary Role | Text | **requis**; colonne de liste |
| `secondary_role` | Secondary Role | Text |  |
| `primary_party` | Primary Party | DynamicLink → `primary_role` |  |
| `secondary_party` | Secondary Party | DynamicLink → `secondary_role` |  |

## Payment Entry

*Payment Entry* — `accounts/payment_entry.yaml` · soumis

- **Numérotation** : série `PE-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `company`
- **Icône** : `banknote`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — ACC-PAY-.YYYY.- | **requis** |
| `payment_type` | Payment Type | Select — Receive · Pay · Internal Transfer | **requis**; colonne de liste |
| `posting_date` | Posting Date | Date | **requis**; colonne de liste; défaut `today` |
| `company` | Company | Link → `Company` | **requis** |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` |  |
| `party_type` | Party Type | Text | visible si `payment_type != 'Internal Transfer'`; obligatoire si `payment_type != 'Internal Transfer'` |
| `party` | Party | DynamicLink → `party_type` | visible si `payment_type != 'Internal Transfer'`; obligatoire si `payment_type != 'Internal Transfer'` |
| `party_name` | Party Name | Text | visible si `payment_type != 'Internal Transfer'` |
| `contact_person` | Contact | Link → `Contact` | visible si `party` |
| `contact_email` | Email | Text | lecture seule; visible si `party` |
| `paid_from` | Account Paid From | Link → `Account` | **requis**; colonne de liste |
| `paid_from_account_currency` | Account Currency (From) | Link → `Currency` | **requis**; lecture seule |
| `paid_from_bank_account` | Bank Account (From) | Link → `Bank Account` | lecture seule |
| `paid_to` | Account Paid To | Link → `Account` | **requis**; colonne de liste |
| `paid_to_account_currency` | Account Currency (To) | Link → `Currency` | **requis**; lecture seule |
| `paid_to_bank_account` | Bank Account (To) | Link → `Bank Account` | lecture seule |
| `paid_amount` | Paid Amount | Currency | **requis**; devise de `paid_from_account_currency` |
| `source_exchange_rate` | Source Exchange Rate | Number | **requis** |
| `base_paid_amount` | Paid Amount (Company Currency) | Currency | **requis**; lecture seule; devise de `company.default_currency` |
| `received_amount` | Received Amount | Currency | **requis**; devise de `paid_to_account_currency` |
| `target_exchange_rate` | Target Exchange Rate | Number | **requis** |
| `base_received_amount` | Received Amount (Company Currency) | Currency | **requis**; lecture seule; devise de `company.default_currency` |
| `references` | Payment References | Table → `Payment Entry Reference` |  |
| `total_allocated_amount` | Total Allocated Amount | Currency | lecture seule; devise de `company.default_currency` |
| `base_total_allocated_amount` | Total Allocated Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `unallocated_amount` | Unallocated Amount | Currency | devise de `company.default_currency` |
| `difference_amount` | Difference Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `deductions` | Payment Deductions or Loss | Table → `Payment Entry Deduction` |  |
| `reference_no` | Cheque/Reference No | Text |  |
| `reference_date` | Cheque/Reference Date | Date |  |
| `clearance_date` | Clearance Date | Date | lecture seule |
| `project` | Project | Link → `Project` |  |
| `remarks` | Remarks | LongText |  |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `print_heading` | Print Heading | Link → `Print Heading` |  |
| `bank` | Bank | Text | lecture seule |
| `bank_account_no` | Bank Account No | Text | lecture seule |
| `payment_order` | Payment Order | Link → `Payment Order` | lecture seule |
| `auto_repeat` | Auto Repeat | Link → `Auto Repeat` | lecture seule |
| `title` | Title | Text | lecture seule; masqué |
| `bank_account` | Company Bank Account | Link → `Bank Account` |  |
| `party_bank_account` | Party Bank Account | Link → `Bank Account` | visible si `party` |
| `payment_order_status` | Payment Order Status | Select — Initiated · Payment Ordered | lecture seule; masqué |
| `status` | Status | Select — Draft · Submitted · Cancelled | lecture seule; défaut `Draft` |
| `custom_remarks` | Custom Remarks | Boolean | défaut `non` |
| `tax_withholding_category` | Tax Withholding Category | Link → `Tax Withholding Category` |  |
| `purchase_taxes_and_charges_template` | Purchase Taxes and Charges Template | Link → `Purchase Taxes and Charges Template` |  |
| `sales_taxes_and_charges_template` | Sales Taxes and Charges Template | Link → `Sales Taxes and Charges Template` |  |
| `taxes` | Advance Taxes and Charges | Table → `Advance Taxes and Charges` |  |
| `base_total_taxes_and_charges` | Total Taxes and Charges (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `total_taxes_and_charges` | Total Taxes and Charges | Currency | lecture seule; devise de `company.default_currency` |
| `paid_amount_after_tax` | Paid Amount After Tax | Currency | lecture seule; masqué; devise de `paid_from_account_currency` |
| `base_paid_amount_after_tax` | Paid Amount After Tax (Company Currency) | Currency | lecture seule; masqué; devise de `company.default_currency` |
| `received_amount_after_tax` | Received Amount After Tax | Currency | lecture seule; masqué; devise de `paid_to_account_currency` |
| `base_received_amount_after_tax` | Received Amount After Tax (Company Currency) | Currency | lecture seule; masqué; devise de `company.default_currency` |
| `paid_from_account_type` | Paid From Account Type | Text | masqué |
| `paid_to_account_type` | Paid To Account Type | Text | masqué |
| `book_advance_payments_in_separate_party_account` | Book Advance Payments in Separate Party Account | Boolean | lecture seule |
| `base_in_words` | In Words (Company Currency) | LongText | lecture seule |
| `in_words` | In Words | LongText | lecture seule |
| `reconcile_on_advance_payment_date` | Reconcile on Advance Payment Date | Boolean | lecture seule; masqué |
| `is_opening` | Is Opening | Select — No · Yes | défaut `No` |
| `apply_tds` | Consider for Tax Withholding | Boolean | défaut `non` |
| `tax_withholding_group` | Tax Withholding Group | Link → `Tax Withholding Group` |  |
| `ignore_tax_withholding_threshold` | Ignore Tax Withholding Threshold | Boolean | défaut `non` |
| `tax_withholding_entries` | Tax Withholding Entries | Table → `Tax Withholding Entry` |  |
| `override_tax_withholding_entries` | Edit Tax Withholding Entries | Boolean | défaut `non` |

## Payment Entry Deduction

*Payment Entry Deduction* — `accounts/payment_entry_deduction.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `account` | Account | Link → `Account` | **requis**; colonne de liste |
| `cost_center` | Cost Center | Link → `Cost Center` | **requis**; colonne de liste |
| `amount` | Amount (Company Currency) | Currency | **requis**; colonne de liste; devise de `parent_company.default_currency` |
| `description` | Description | LongText |  |
| `is_exchange_gain_loss` | System Generated | Boolean | lecture seule |
| `dunning` | Dunning | Link → `Dunning` | lecture seule |

## Payment Entry Reference

*Payment Entry Reference* — `accounts/payment_entry_reference.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `reference_doctype` | Type | Text | **requis**; colonne de liste |
| `reference_name` | Name | DynamicLink → `reference_doctype` | colonne de liste |
| `due_date` | Due Date | Date | colonne de liste; lecture seule |
| `bill_no` | Supplier Invoice No | Text | lecture seule |
| `total_amount` | Grand Total | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `outstanding_amount` | Outstanding | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `allocated_amount` | Allocated | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `exchange_rate` | Exchange Rate | Number | lecture seule |
| `payment_term` | Payment Term | Link → `Payment Term` |  |
| `exchange_gain_loss` | Exchange Gain/Loss | Currency | lecture seule; devise de `parent_company.default_currency` |
| `account` | Account | Link → `Account` |  |
| `account_type` | Account Type | Text |  |
| `payment_type` | Payment Type | Text |  |
| `payment_request` | Payment Request | Link → `Payment Request` |  |
| `payment_term_outstanding` | Payment Term Outstanding | Number | lecture seule |
| `payment_request_outstanding` | Payment Request Outstanding | Number | lecture seule |
| `reconcile_effect_on` | Reconcile Effect On | Date | lecture seule |
| `advance_voucher_type` | Advance Voucher Type | Text | lecture seule |
| `advance_voucher_no` | Advance Voucher No | DynamicLink → `advance_voucher_type` | lecture seule |

## Payment Gateway

*Payment Gateway* — `accounts/payment_gateway.yaml`

- **Titre** : `gateway`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `gateway` | Gateway | Text | **requis**; colonne de liste |
| `gateway_settings` | Gateway Settings | JSON |  |
| `enabled` | Enabled | Boolean | défaut `oui` |

## Payment Gateway Account

*Payment Gateway Account* — `accounts/payment_gateway_account.yaml`

- **Titre** : `company`
- **Icône** : `credit-card`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `payment_gateway` | Payment Gateway | Link → `Payment Gateway` | **requis**; colonne de liste |
| `is_default` | Is Default | Boolean | défaut `non` |
| `payment_account` | Payment Account | Link → `Account` | **requis**; colonne de liste |
| `currency` | Currency | Text | lecture seule |
| `message` | Default Payment Request Message | LongText | défaut `Please click on the link below to make your payment` |
| `payment_channel` | Payment Channel | Select — Email · Phone · Other | défaut `Email` |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |

## Payment Ledger Entry

*Payment Ledger Entry* — `accounts/payment_ledger_entry.yaml` · soumis

- **Numérotation** : série `PLE-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `company`
- **Icône** : `book-open`
- **Permissions explicites** — `write` : 0, `create` : 0, `delete` : 0, `submit` : 0, `cancel` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `posting_date` | Posting Date | Date |  |
| `account_type` | Account Type | Select — Receivable · Payable |  |
| `account` | Account | Link → `Account` |  |
| `party_type` | Party Type | Text |  |
| `party` | Party | DynamicLink → `party_type` |  |
| `voucher_type` | Voucher Type | Text |  |
| `voucher_no` | Voucher No | DynamicLink → `voucher_type` | colonne de liste |
| `against_voucher_type` | Against Voucher Type | Text |  |
| `against_voucher_no` | Against Voucher No | DynamicLink → `against_voucher_type` | colonne de liste |
| `amount` | Amount | Currency | colonne de liste; devise de `company.default_currency` |
| `account_currency` | Currency | Link → `Currency` |  |
| `amount_in_account_currency` | Amount in Account Currency | Currency | devise de `account_currency` |
| `delinked` | DeLinked | Boolean | colonne de liste; défaut `non` |
| `company` | Company | Link → `Company` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |
| `due_date` | Due Date | Date |  |
| `finance_book` | Finance Book | Link → `Finance Book` |  |
| `remarks` | Remarks | LongText |  |
| `voucher_detail_no` | Voucher Detail No | Text |  |

## Payment Order

*Payment Order* — `accounts/payment_order.yaml` · soumis

- **Numérotation** : série `PO-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `company`
- **Icône** : `send`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — PMO- | **requis**; défaut `PMO-` |
| `company` | Company | Link → `Company` | **requis** |
| `party` | Supplier | Link → `Supplier` | colonne de liste |
| `posting_date` | Posting Date | Date | colonne de liste; défaut `today` |
| `references` | Payment Order Reference | Table → `Payment Order Reference` |  |
| `payment_order_type` | Payment Order Type | Select — Payment Request · Payment Entry | **requis**; lecture seule |
| `company_bank_account` | Company Bank Account | Link → `Bank Account` | **requis** |
| `company_bank` | Bank | Link → `Bank` | colonne de liste |
| `account` | Account | Text |  |

## Payment Order Reference

*Payment Order Reference* — `accounts/payment_order_reference.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `reference_doctype` | Type | Text | **requis**; colonne de liste; lecture seule |
| `reference_name` | Name | DynamicLink → `reference_doctype` | colonne de liste; lecture seule |
| `amount` | Amount | Currency | **requis**; colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `supplier` | Supplier | Link → `Supplier` | lecture seule |
| `payment_request` | Payment Request | Link → `Payment Request` | lecture seule |
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` | lecture seule |
| `bank_account` | Bank Account | Link → `Bank Account` | **requis**; lecture seule |
| `account` | Account | Link → `Account` | lecture seule |
| `payment_reference` | Payment Reference | Text | lecture seule |

## Payment Reconciliation

*Payment Reconciliation* — `accounts/payment_reconciliation.yaml`

- **Titre** : `company`
- **Icône** : `arrow-left-right`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis** |
| `party_type` | Party Type | Text | **requis** |
| `party` | Party | DynamicLink → `party_type` |  |
| `receivable_payable_account` | Receivable / Payable Account | Link → `Account` | **requis** |
| `currency` | Currency | Link → `Currency` | lecture seule; masqué |
| `bank_cash_account` | Bank / Cash Account | Link → `Account` | colonne de liste; — This filter will be applied to Journal Entry. |
| `payments` | Payments | Table → `Payment Reconciliation Payment` |  |
| `total_invoice_amount` | Total Invoice Amount | Currency | lecture seule; devise de `currency` |
| `total_payment_amount` | Total Payment Amount | Currency | lecture seule; devise de `currency` |
| `difference_amount` | Difference Amount | Currency | lecture seule; devise de `currency` |
| `invoices` | Invoices | Table → `Payment Reconciliation Invoice` |  |
| `allocation` | Allocation | Table → `Payment Reconciliation Allocation` |  |
| `from_invoice_date` | From Invoice Date | Date | colonne de liste |
| `to_invoice_date` | To Invoice Date | Date | colonne de liste |
| `minimum_invoice_amount` | Minimum Invoice Amount | Currency | devise de `currency` |
| `invoice_limit` | Invoice Limit | Int | défaut `50`; — System will fetch all the entries if limit value is zero. |
| `from_payment_date` | From Payment Date | Date |  |
| `to_payment_date` | To Payment Date | Date |  |
| `minimum_payment_amount` | Minimum Payment Amount | Currency | devise de `currency` |
| `maximum_payment_amount` | Maximum Payment Amount | Currency | devise de `currency` |
| `payment_limit` | Payment Limit | Int | défaut `50`; — System will fetch all the entries if limit value is zero. |
| `maximum_invoice_amount` | Maximum Invoice Amount | Currency | devise de `currency` |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |
| `default_advance_account` | Default Advance Account | Link → `Account` | — Only 'Payment Entries' made against this advance account are supported. |
| `invoice_name` | Filter on Invoice | Text |  |
| `payment_name` | Filter on Payment | Text |  |

## Payment Reconciliation Allocation

*Payment Reconciliation Allocation* — `accounts/payment_reconciliation_allocation.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `invoice_number` | Invoice Number | DynamicLink → `invoice_type` | colonne de liste; lecture seule |
| `allocated_amount` | Allocated Amount | Currency | **requis**; colonne de liste; devise de `currency` |
| `difference_account` | Difference Account | Link → `Account` | lecture seule |
| `difference_amount` | Difference Amount | Currency | colonne de liste; lecture seule; devise de `currency` |
| `reference_name` | Reference Name | DynamicLink → `reference_type` | colonne de liste; lecture seule |
| `is_advance` | Is Advance | Text | lecture seule; masqué |
| `reference_type` | Reference Type | Text | **requis**; lecture seule |
| `invoice_type` | Invoice Type | Text | **requis**; lecture seule |
| `unreconciled_amount` | Unreconciled Amount | Currency | lecture seule; masqué; devise de `currency` |
| `amount` | Amount | Currency | lecture seule; masqué; devise de `currency` |
| `reference_row` | Reference Row | Text | lecture seule; masqué |
| `currency` | Currency | Link → `Currency` | masqué |
| `exchange_rate` | Exchange Rate | Number | lecture seule |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `gain_loss_posting_date` | Difference Posting Date | Date |  |
| `debit_or_credit_note_posting_date` | Debit / Credit Note Posting Date | Date |  |

## Payment Reconciliation Invoice

*Payment Reconciliation Invoice* — `accounts/payment_reconciliation_invoice.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `invoice_type` | Invoice Type | Text | colonne de liste; lecture seule |
| `invoice_number` | Invoice Number | DynamicLink → `invoice_type` | colonne de liste; lecture seule |
| `invoice_date` | Invoice Date | Date | colonne de liste; lecture seule |
| `amount` | Amount | Currency | lecture seule; devise de `currency` |
| `outstanding_amount` | Outstanding Amount | Currency | colonne de liste; lecture seule; devise de `currency` |
| `currency` | Currency | Link → `Currency` | masqué |
| `exchange_rate` | Exchange Rate | Number | masqué |

## Payment Reconciliation Payment

*Payment Reconciliation Payment* — `accounts/payment_reconciliation_payment.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `reference_type` | Reference Type | Text | lecture seule |
| `reference_name` | Reference Name | DynamicLink → `reference_type` | colonne de liste; lecture seule |
| `posting_date` | Posting Date | Date | colonne de liste; lecture seule |
| `is_advance` | Is Advance | Text | lecture seule; masqué |
| `reference_row` | Reference Row | Text | lecture seule; masqué |
| `amount` | Amount | Currency | colonne de liste; lecture seule; devise de `currency` |
| `currency` | Currency | Link → `Currency` | masqué |
| `difference_amount` | Difference Amount | Currency | lecture seule; devise de `currency` |
| `exchange_rate` | Exchange Rate | Number | masqué |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `remarks` | Remarks | LongText | lecture seule |

## Payment Reference

*Payment Reference* — `accounts/payment_reference.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `payment_term` | Payment Term | Link → `Payment Term` | colonne de liste |
| `description` | Description | LongText | colonne de liste |
| `due_date` | Due Date | Date | colonne de liste |
| `amount` | Amount | Currency | colonne de liste; devise de `currency` |
| `currency` | Currency | Link → `Currency` | lecture seule; masqué |
| `payment_schedule` | Payment Schedule | Text | lecture seule; — Référence de la ligne d'origine (Payment Schedule). |

## Payment Request

*Payment Request* — `accounts/payment_request.yaml` · soumis

- **Numérotation** : série `PR-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `company`
- **Icône** : `hand-coins`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `payment_request_type` | Payment Request Type | Select — Outward · Inward | **requis**; défaut `Inward` |
| `transaction_date` | Transaction Date | Date |  |
| `naming_series` | Series | Select — ACC-PRQ-.YYYY.- | **requis**; colonne de liste |
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` |  |
| `party_type` | Party Type | Text |  |
| `party` | Party | DynamicLink → `party_type` |  |
| `reference_doctype` | Reference Doctype | Text | lecture seule |
| `reference_name` | Reference Name | DynamicLink → `reference_doctype` | lecture seule |
| `grand_total` | Amount | Currency | **requis**; devise de `currency`; — Amount in transaction currency |
| `is_a_subscription` | Is a Subscription | Boolean | défaut `non` |
| `currency` | Transaction Currency | Link → `Currency` | lecture seule |
| `subscription_plans` | Subscription Plans | Table → `Subscription Plan Detail` |  |
| `bank_account` | Bank Account | Link → `Bank Account` |  |
| `bank` | Bank | Link → `Bank` | lecture seule |
| `bank_account_no` | Bank Account No | Text | lecture seule |
| `account` | Account | Text | lecture seule |
| `iban` | IBAN | Text | lecture seule |
| `branch_code` | Branch Code | Text | lecture seule |
| `swift_number` | SWIFT Number | Text | lecture seule |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |
| `email_to` | To | Text |  |
| `subject` | Subject | Text |  |
| `payment_gateway_account` | Payment Gateway Account | Link → `Payment Gateway Account` |  |
| `status` | Status | Select — Draft · Requested · Initiated · Partially Paid · Payment Ordered · Paid · Failed · Cancelled | lecture seule; masqué; défaut `Draft` |
| `make_sales_invoice` | Make Sales Invoice | Boolean | lecture seule; masqué |
| `message` | Message | LongText |  |
| `mute_email` | Mute Email | Boolean | lecture seule; masqué |
| `payment_url` | Payment URL | Text | lecture seule |
| `payment_gateway` | Payment Gateway | Text | lecture seule |
| `payment_account` | Payment Account | Text | lecture seule |
| `payment_channel` | Payment Channel | Select — Email · Phone · Other | lecture seule |
| `payment_order` | Payment Order | Link → `Payment Order` | lecture seule |
| `failed_reason` | Reason for Failure | Text | lecture seule; masqué |
| `outstanding_amount` | Outstanding Amount | Currency | lecture seule; devise de `party_account_currency`; — Amount in party's bank account currency |
| `company` | Company | Link → `Company` | lecture seule |
| `party_account_currency` | Party Account Currency | Link → `Currency` | lecture seule |
| `party_name` | Party Name | Text | lecture seule |
| `phone_number` | Phone Number | Text |  |
| `payment_reference` | Payment Reference | Table → `Payment Reference` | lecture seule |

## Payment Schedule

*Payment Schedule* — `accounts/payment_schedule.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `payment_term` | Payment Term | Link → `Payment Term` | colonne de liste |
| `description` | Description | LongText | colonne de liste |
| `due_date` | Due Date | Date | **requis**; colonne de liste |
| `invoice_portion` | Invoice Portion | Percent | colonne de liste |
| `payment_amount` | Payment Amount | Currency | **requis**; colonne de liste; devise de `parent_currency` |
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` |  |
| `paid_amount` | Paid Amount | Currency | devise de `parent_currency` |
| `discounted_amount` | Discounted Amount | Currency | lecture seule; devise de `parent_currency` |
| `outstanding` | Outstanding | Currency | lecture seule; devise de `parent_currency` |
| `discount_date` | Discount Date | Date |  |
| `discount_type` | Discount Type | Select — Percentage · Amount | défaut `Percentage` |
| `discount` | Discount | Number |  |
| `base_payment_amount` | Payment Amount (Company Currency) | Currency | devise de `parent_company.default_currency` |
| `base_outstanding` | Outstanding (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_paid_amount` | Paid Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `due_date_based_on` | Due Date Based On | Select — Day(s) after invoice date · Day(s) after the end of the invoice month · Month(s) after the end of the invoice month | lecture seule |
| `credit_days` | Credit Days | Int | lecture seule |
| `credit_months` | Credit Months | Int | lecture seule |
| `discount_validity_based_on` | Discount Validity Based On | Select — Day(s) after invoice date · Day(s) after the end of the invoice month · Month(s) after the end of the invoice month | lecture seule |
| `discount_validity` | Discount Validity | Int | lecture seule |

## Payment Term

*Payment Term* — `accounts/payment_term.yaml`

- **Icône** : `calendar-clock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `payment_term_name` | Payment Term Name | Text |  |
| `invoice_portion` | Invoice Portion (%) | Number |  |
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` |  |
| `due_date_based_on` | Due Date Based On | Select — Day(s) after invoice date · Day(s) after the end of the invoice month · Month(s) after the end of the invoice month |  |
| `credit_days` | Credit Days | Int |  |
| `credit_months` | Credit Months | Int |  |
| `description` | Description | LongText |  |
| `discount_type` | Discount Type | Select — Percentage · Amount | défaut `Percentage` |
| `discount` | Discount | Number |  |
| `discount_validity_based_on` | Discount Validity Based On | Select — Day(s) after invoice date · Day(s) after the end of the invoice month · Month(s) after the end of the invoice month | défaut `Day(s) after invoice date` |
| `discount_validity` | Discount Validity | Int |  |

## Payment Terms Template

*Payment Terms Template* — `accounts/payment_terms_template.yaml`

- **Icône** : `calendar-clock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `template_name` | Template Name | Text |  |
| `terms` | Payment Terms | Table → `Payment Terms Template Detail` |  |
| `allocate_payment_based_on_payment_terms` | Allocate Payment Based On Payment Terms | Boolean | défaut `non`; — If this checkbox is checked, paid amount will be splitted and allocated as per the amounts in payment schedule |

## Payment Terms Template Detail

*Payment Terms Template Detail* — `accounts/payment_terms_template_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `payment_term` | Payment Term | Link → `Payment Term` | colonne de liste |
| `description` | Description | LongText | colonne de liste |
| `invoice_portion` | Invoice Portion (%) | Number | **requis**; colonne de liste |
| `due_date_based_on` | Due Date Based On | Select — Day(s) after invoice date · Day(s) after the end of the invoice month · Month(s) after the end of the invoice month | **requis**; colonne de liste |
| `credit_days` | Credit Days | Int | colonne de liste; défaut `0` |
| `credit_months` | Credit Months | Int | défaut `0` |
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` |  |
| `discount_type` | Discount Type | Select — Percentage · Amount | défaut `Percentage` |
| `discount` | Discount | Number |  |
| `discount_validity_based_on` | Discount Validity Based On | Select — Day(s) after invoice date · Day(s) after the end of the invoice month · Month(s) after the end of the invoice month | défaut `Day(s) after invoice date` |
| `discount_validity` | Discount Validity | Int |  |

## Pegged Currencies

*Pegged Currencies* — `accounts/pegged_currencies.yaml`

- **Icône** : `anchor`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `pegged_currency_item` | Pegged Currency Item | Table → `Pegged Currency Details` |  |

## Pegged Currency Details

*Pegged Currency Details* — `accounts/pegged_currency_details.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `source_currency` | Currency | Link → `Currency` | colonne de liste |
| `pegged_exchange_rate` | Exchange Rate | Text | colonne de liste |
| `pegged_against` | Pegged Against | Link → `Currency` | colonne de liste |

## Period Closing Voucher

*Period Closing Voucher* — `accounts/period_closing_voucher.yaml` · soumis

- **Numérotation** : série `PCV-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `company`
- **Icône** : `folder-lock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `transaction_date` | Transaction Date | Date | défaut `today` |
| `fiscal_year` | Fiscal Year | Link → `Fiscal Year` | **requis**; colonne de liste |
| `company` | Company | Link → `Company` | **requis** |
| `closing_account_head` | Closing Account Head | Link → `Account` | **requis**; — The account head under Liability or Equity, in which Profit/Loss will be booked |
| `stock_value_difference` | Accepted Stock Value Difference | Currency | lecture seule; devise de `company.default_currency`; — Difference between the Stock Asset accounts balance and the Stock Balance value accepted while submitting |
| `remarks` | Remarks | LongText | **requis** |
| `gle_processing_status` | GL Entry Processing Status | Select — In Progress · Completed · Failed | lecture seule |
| `error_message` | Error Message | LongText | lecture seule |
| `period_end_date` | Period End Date | Date | **requis** |
| `period_start_date` | Period Start Date | Date | **requis** |

## POS Closing Entry

*POS Closing Entry* — `accounts/pos_closing_entry.yaml` · soumis

- **Numérotation** : série `PCE-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `company`
- **Icône** : `book-lock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `period_start_date` | Period Start Date | Datetime | **requis**; colonne de liste; lecture seule |
| `period_end_date` | Period End Date | Datetime | **requis**; colonne de liste |
| `posting_date` | Posting Date | Date | **requis**; colonne de liste; défaut `today` |
| `company` | Company | Link → `Company` | **requis**; lecture seule |
| `pos_profile` | POS Profile | Link → `POS Profile` | **requis**; colonne de liste; lecture seule |
| `user` | Cashier | Text | **requis**; lecture seule |
| `payment_reconciliation` | Payment Reconciliation | Table → `POS Closing Entry Detail` |  |
| `grand_total` | Grand Total | Currency | lecture seule; devise de `company.default_currency` |
| `net_total` | Net Total | Currency | lecture seule; devise de `company.default_currency` |
| `total_quantity` | Total Quantity | Decimal | lecture seule |
| `taxes` | Taxes | Table → `POS Closing Entry Taxes` | lecture seule |
| `pos_opening_entry` | POS Opening Entry | Link → `POS Opening Entry` | **requis** |
| `status` | Status | Select — Draft · Submitted · Queued · Failed · Cancelled | lecture seule; masqué; défaut `Draft` |
| `error_message` | Error | LongText | lecture seule |
| `posting_time` | Posting Time | Time | **requis** |
| `pos_invoices` | POS Transactions | Table → `POS Invoice Reference` | lecture seule |
| `sales_invoices` | Sales Invoice Transactions | Table → `Sales Invoice Reference` | lecture seule |
| `total_taxes_and_charges` | Total Taxes and Charges | Currency | lecture seule; devise de `company.default_currency` |

## POS Closing Entry Detail

*POS Closing Entry Detail* — `accounts/pos_closing_entry_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` | **requis**; colonne de liste |
| `expected_amount` | Expected Amount | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `difference` | Difference | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `opening_amount` | Opening Amount | Currency | **requis**; colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `closing_amount` | Closing Amount | Currency | **requis**; colonne de liste; devise de `parent_company.default_currency` |

## POS Closing Entry Taxes

*POS Closing Entry Taxes* — `accounts/pos_closing_entry_taxes.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `amount` | Amount | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `account_head` | Account Head | Link → `Account` | colonne de liste; lecture seule |

## POS Customer Group

*POS Customer Group* — `accounts/pos_customer_group.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `customer_group` | Customer Group | Link → `Customer Group` | **requis**; colonne de liste |

## POS Field

*POS Field* — `accounts/pos_field.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `fieldtype` | Fieldtype | Text | colonne de liste; lecture seule |
| `label` | Label | Text | colonne de liste; lecture seule |
| `options` | Options | LongText | colonne de liste; lecture seule |
| `reqd` | Mandatory | Boolean | défaut `non` |
| `read_only` | Read Only | Boolean | défaut `non` |
| `default_value` | Default Value | Text |  |

## POS Invoice

*POS Invoice* — `accounts/pos_invoice.yaml` · soumis

- **Numérotation** : série `PI-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `customer`
- **Icône** : `receipt-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — ACC-PSINV-.YYYY.- | **requis** |
| `customer` | Customer | Link → `Customer` |  |
| `customer_name` | Customer Name | Text | lecture seule; recopié de `customer.customer_name` |
| `tax_id` | Tax Id | Text | lecture seule |
| `is_pos` | Include Payment (POS) | Boolean | **requis**; lecture seule |
| `pos_profile` | POS Profile | Link → `POS Profile` |  |
| `is_return` | Is Return (Credit Note) | Boolean | défaut `non` |
| `company` | Company | Link → `Company` | **requis** |
| `posting_date` | Date | Date | **requis**; défaut `today` |
| `posting_time` | Posting Time | Time |  |
| `set_posting_time` | Edit Posting Date and Time | Boolean | défaut `non` |
| `due_date` | Payment Due Date | Date |  |
| `return_against` | Return Against | Link → `POS Invoice` | lecture seule |
| `update_billed_amount_in_sales_order` | Update Billed Amount in Sales Order | Boolean | défaut `non` |
| `project` | Project | Link → `Project` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `po_no` | Customer's Purchase Order | Text |  |
| `po_date` | Customer's Purchase Order Date | Date |  |
| `customer_address` | Customer Address | Link → `Address` |  |
| `address_display` | Address | TextEditor | lecture seule |
| `contact_person` | Contact Person | Link → `Contact` |  |
| `contact_display` | Contact | LongText | lecture seule |
| `contact_mobile` | Mobile No | Text | lecture seule; masqué |
| `contact_email` | Contact Email | Text | lecture seule; masqué |
| `territory` | Territory | Link → `Territory` |  |
| `shipping_address_name` | Shipping Address Name | Link → `Address` |  |
| `shipping_address` | Shipping Address | TextEditor | lecture seule |
| `company_address` | Company Address Name | Link → `Address` |  |
| `company_address_display` | Company Address | TextEditor | lecture seule; masqué |
| `currency` | Currency | Link → `Currency` | **requis** |
| `conversion_rate` | Exchange Rate | Number | **requis**; — Rate at which Customer Currency is converted to customer's base currency |
| `selling_price_list` | Price List | Link → `Price List` | **requis** |
| `price_list_currency` | Price List Currency | Link → `Currency` | **requis**; lecture seule |
| `plc_conversion_rate` | Price List Exchange Rate | Number | **requis**; — Rate at which Price list currency is converted to customer's base currency |
| `ignore_pricing_rule` | Ignore Pricing Rule | Boolean | défaut `non` |
| `set_warehouse` | Source Warehouse | Link → `Warehouse` |  |
| `update_stock` | Update Stock | Boolean | défaut `non` |
| `scan_barcode` | Scan Barcode | Text |  |
| `items` | Items | Table → `POS Invoice Item` |  |
| `pricing_rules` | Pricing Rule Detail | Table → `Pricing Rule Detail` | lecture seule |
| `packed_items` | Packed Items | Table → `Packed Item` |  |
| `timesheets` | Time Sheets | Table → `Sales Invoice Timesheet` |  |
| `total_billing_amount` | Total Billing Amount | Currency | lecture seule; devise de `currency` |
| `total_qty` | Total Quantity | Decimal | lecture seule |
| `base_total` | Total (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_net_total` | Net Total (Company Currency) | Currency | **requis**; lecture seule; devise de `company.default_currency` |
| `total` | Total | Currency | lecture seule; devise de `currency` |
| `net_total` | Net Total | Currency | lecture seule; devise de `currency` |
| `total_net_weight` | Total Net Weight | Number | lecture seule |
| `taxes_and_charges` | Sales Taxes and Charges Template | Link → `Sales Taxes and Charges Template` |  |
| `shipping_rule` | Shipping Rule | Link → `Shipping Rule` |  |
| `tax_category` | Tax Category | Link → `Tax Category` |  |
| `taxes` | Sales Taxes and Charges | Table → `Sales Taxes and Charges` |  |
| `other_charges_calculation` | Taxes and Charges Calculation | TextEditor | lecture seule |
| `base_total_taxes_and_charges` | Total Taxes and Charges (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `total_taxes_and_charges` | Total Taxes and Charges | Currency | lecture seule; devise de `currency` |
| `loyalty_points` | Loyalty Points | Int |  |
| `loyalty_amount` | Loyalty Amount | Currency | lecture seule; devise de `currency` |
| `redeem_loyalty_points` | Redeem Loyalty Points | Boolean | défaut `non` |
| `loyalty_program` | Loyalty Program | Link → `Loyalty Program` | lecture seule |
| `loyalty_redemption_account` | Redemption Account | Link → `Account` |  |
| `loyalty_redemption_cost_center` | Redemption Cost Center | Link → `Cost Center` |  |
| `apply_discount_on` | Apply Additional Discount On | Select — Grand Total · Net Total | défaut `Grand Total` |
| `base_discount_amount` | Additional Discount Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `additional_discount_percentage` | Additional Discount Percentage | Number |  |
| `discount_amount` | Additional Discount Amount | Currency | devise de `currency` |
| `base_grand_total` | Grand Total (Company Currency) | Currency | **requis**; lecture seule; devise de `company.default_currency` |
| `base_rounding_adjustment` | Rounding Adjustment (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_rounded_total` | Rounded Total (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_in_words` | In Words (Company Currency) | Text | lecture seule; — In Words will be visible once you save the Sales Invoice. |
| `grand_total` | Grand Total | Currency | **requis**; colonne de liste; lecture seule; devise de `currency` |
| `rounding_adjustment` | Rounding Adjustment | Currency | lecture seule; devise de `currency` |
| `rounded_total` | Rounded Total | Currency | lecture seule; devise de `currency` |
| `in_words` | In Words | Text | lecture seule |
| `total_advance` | Total Advance | Currency | lecture seule; devise de `currency` |
| `outstanding_amount` | Outstanding Amount | Currency | lecture seule; devise de `party_account_currency` |
| `allocate_advances_automatically` | Allocate Advances Automatically (FIFO) | Boolean | défaut `non` |
| `advances` | Advances | Table → `Sales Invoice Advance` |  |
| `payment_terms_template` | Payment Terms Template | Link → `Payment Terms Template` |  |
| `payment_schedule` | Payment Schedule | Table → `Payment Schedule` |  |
| `cash_bank_account` | Cash/Bank Account | Link → `Account` | masqué |
| `payments` | Sales Invoice Payment | Table → `Sales Invoice Payment` |  |
| `base_paid_amount` | Paid Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `paid_amount` | Paid Amount | Currency | lecture seule; devise de `currency` |
| `base_change_amount` | Base Change Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `change_amount` | Change Amount | Currency | devise de `currency` |
| `account_for_change_amount` | Account for Change Amount | Link → `Account` |  |
| `write_off_amount` | Write Off Amount | Currency | devise de `currency` |
| `base_write_off_amount` | Write Off Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `write_off_outstanding_amount_automatically` | Write Off Outstanding Amount | Boolean | défaut `non` |
| `write_off_account` | Write Off Account | Link → `Account` |  |
| `write_off_cost_center` | Write Off Cost Center | Link → `Cost Center` |  |
| `tc_name` | Terms | Link → `Terms and Conditions` |  |
| `terms` | Terms and Conditions Details | TextEditor |  |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `group_same_items` | Group same items | Boolean | défaut `non` |
| `language` | Print Language | Text | lecture seule |
| `select_print_heading` | Print Heading | Link → `Print Heading` |  |
| `inter_company_invoice_reference` | Inter Company Invoice Reference | Link → `Purchase Invoice` | lecture seule |
| `customer_group` | Customer Group | Link → `Customer Group` | masqué |
| `is_discounted` | Is Discounted | Boolean | lecture seule |
| `status` | Status | Select — Draft · Return · Credit Note Issued · Consolidated · Submitted · Paid · Partly Paid · Unpaid · Partly Paid and Discounted · Unpaid and Discounted · Overdue and Discounted · Overdue · Cancelled | lecture seule; défaut `Draft` |
| `debit_to` | Debit To | Link → `Account` | **requis** |
| `party_account_currency` | Party Account Currency | Link → `Currency` | lecture seule; masqué |
| `is_opening` | Is Opening Entry | Select — No · Yes | défaut `No` |
| `remarks` | Remarks | LongText |  |
| `sales_partner` | Sales Partner | Link → `Sales Partner` |  |
| `commission_rate` | Commission Rate (%) | Number |  |
| `total_commission` | Total Commission | Currency | devise de `currency` |
| `sales_team` | Sales Team | Table → `Sales Team` |  |
| `from_date` | From Date | Date |  |
| `to_date` | To Date | Date |  |
| `auto_repeat` | Auto Repeat | Link → `Auto Repeat` | lecture seule |
| `against_income_account` | Against Income Account | LongText | masqué |
| `consolidated_invoice` | Consolidated Sales Invoice | Link → `Sales Invoice` | lecture seule |
| `coupon_code` | Coupon Code | Link → `Coupon Code` |  |
| `amount_eligible_for_commission` | Amount Eligible for Commission | Currency | lecture seule; devise de `currency` |
| `update_billed_amount_in_delivery_note` | Update Billed Amount in Delivery Note | Boolean | défaut `oui` |
| `utm_medium` | Medium | Link → `UTM Medium` |  |
| `utm_campaign` | Campaign | Link → `UTM Campaign` |  |
| `utm_source` | Source | Link → `UTM Source` |  |
| `company_contact_person` | Company Contact Person | Link → `Contact` |  |
| `last_scanned_warehouse` | Last Scanned Warehouse | Text |  |
| `item_wise_tax_details` | Item Wise Tax Details | Table → `Item Wise Tax Detail` | masqué |
| `title` | Title | Text |  |

## POS Invoice Item

*POS Invoice Item* — `accounts/pos_invoice_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `barcode` | Barcode | Text |  |
| `item_code` | Item | Link → `Item` | colonne de liste |
| `is_product_bundle` | Is Product Bundle | Boolean | lecture seule; masqué |
| `product_bundle` | Product Bundle | Link → `Product Bundle` |  |
| `item_name` | Item Name | Text | **requis** |
| `customer_item_code` | Customer's Item Code | Text | lecture seule; masqué |
| `description` | Description | TextEditor |  |
| `item_group` | Item Group | Link → `Item Group` | lecture seule; masqué |
| `brand` | Brand Name | Text | masqué |
| `qty` | Quantity | Decimal | colonne de liste |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `uom` | UOM | Link → `UOM` | **requis** |
| `conversion_factor` | UOM Conversion Factor | Number | **requis** |
| `stock_qty` | Qty as per Stock UOM | Decimal | lecture seule |
| `price_list_rate` | Price List Rate | Currency | lecture seule; devise de `parent_currency` |
| `base_price_list_rate` | Price List Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `margin_type` | Margin Type | Select — Percentage · Amount |  |
| `margin_rate_or_amount` | Margin Rate or Amount | Number |  |
| `rate_with_margin` | Rate With Margin | Currency | lecture seule; devise de `parent_currency` |
| `discount_percentage` | Discount (%) on Price List Rate with Margin | Percent |  |
| `discount_amount` | Discount Amount | Currency | devise de `parent_currency` |
| `base_rate_with_margin` | Rate With Margin (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `rate` | Rate | Currency | **requis**; colonne de liste; devise de `parent_currency` |
| `amount` | Amount | Currency | **requis**; colonne de liste; lecture seule; devise de `parent_currency` |
| `item_tax_template` | Item Tax Template | Link → `Item Tax Template` |  |
| `base_rate` | Rate (Company Currency) | Currency | **requis**; lecture seule; devise de `parent_company.default_currency` |
| `base_amount` | Amount (Company Currency) | Currency | **requis**; lecture seule; devise de `parent_company.default_currency` |
| `pricing_rules` | Pricing Rules | LongText | lecture seule; masqué |
| `is_free_item` | Is Free Item | Boolean | lecture seule |
| `net_rate` | Net Rate | Currency | lecture seule; devise de `parent_currency` |
| `net_amount` | Net Amount | Currency | lecture seule; devise de `parent_currency` |
| `base_net_rate` | Net Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_net_amount` | Net Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `delivered_by_supplier` | Delivered By Supplier | Boolean | lecture seule |
| `income_account` | Income Account | Link → `Account` | **requis** |
| `is_fixed_asset` | Is Fixed Asset | Boolean | lecture seule; masqué |
| `asset` | Asset | Link → `Asset` |  |
| `finance_book` | Finance Book | Link → `Finance Book` |  |
| `expense_account` | Expense Account | Link → `Account` |  |
| `deferred_revenue_account` | Deferred Revenue Account | Link → `Account` |  |
| `service_stop_date` | Service Stop Date | Date |  |
| `enable_deferred_revenue` | Enable Deferred Revenue | Boolean | défaut `non` |
| `service_start_date` | Service Start Date | Date |  |
| `service_end_date` | Service End Date | Date |  |
| `weight_per_unit` | Weight Per Unit | Number | lecture seule |
| `total_weight` | Total Weight | Number | lecture seule |
| `weight_uom` | Weight UOM | Link → `UOM` | lecture seule |
| `warehouse` | Warehouse | Link → `Warehouse` | colonne de liste |
| `target_warehouse` | Customer Warehouse (Optional) | Link → `Warehouse` | masqué |
| `quality_inspection` | Quality Inspection | Link → `Quality Inspection` |  |
| `batch_no` | Batch No | Link → `Batch` |  |
| `allow_zero_valuation_rate` | Allow Zero Valuation Rate | Boolean | défaut `non` |
| `serial_no` | Serial No | LongText | colonne de liste |
| `item_tax_rate` | Item Tax Rate | LongText | lecture seule; masqué |
| `actual_batch_qty` | Available Batch Qty at Warehouse | Decimal | lecture seule |
| `actual_qty` | Available Qty at Warehouse | Decimal | lecture seule |
| `sales_order` | Sales Order | Link → `Sales Order` | lecture seule |
| `so_detail` | Sales Order Item | Text | lecture seule; masqué |
| `delivery_note` | Delivery Note | Link → `Delivery Note` | lecture seule |
| `dn_detail` | Delivery Note Item | Text | lecture seule; masqué |
| `delivered_qty` | Delivered Qty | Decimal | lecture seule |
| `cost_center` | Cost Center | Link → `Cost Center` | **requis** |
| `page_break` | Page Break | Boolean | défaut `non` |
| `project` | Project | Link → `Project` |  |
| `pos_invoice_item` | POS Invoice Item | Text | lecture seule |
| `grant_commission` | Grant Commission | Boolean | lecture seule |
| `has_item_scanned` | Has Item Scanned | Boolean | lecture seule |
| `serial_and_batch_bundle` | Serial and Batch Bundle | Link → `Serial and Batch Bundle` |  |
| `use_serial_batch_fields` | Use Serial No / Batch Fields | Boolean | défaut `non` |
| `distributed_discount_amount` | Distributed Discount Amount | Currency | devise de `parent_currency` |
| `mapped_additional_discount_amount` | Additional Discount per Stock Unit | Currency | lecture seule; devise de `parent_currency`; — Tax-exclusive additional discount carried from a source document, per stock unit. |

## POS Invoice Merge Log

*POS Invoice Merge Log* — `accounts/pos_invoice_merge_log.yaml` · soumis

- **Numérotation** : série `PIML-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `customer`
- **Icône** : `merge`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `posting_date` | Posting Date | Date | **requis**; colonne de liste |
| `customer` | Customer | Link → `Customer` | **requis**; colonne de liste |
| `pos_invoices` | POS Invoices | Table → `POS Invoice Reference` |  |
| `consolidated_invoice` | Consolidated Sales Invoice | Link → `Sales Invoice` | lecture seule |
| `consolidated_credit_note` | Consolidated Credit Note | Link → `Sales Invoice` | lecture seule |
| `pos_closing_entry` | POS Closing Entry | Link → `POS Closing Entry` |  |
| `merge_invoices_based_on` | Merge Invoices Based On | Select — Customer · Customer Group | **requis** |
| `customer_group` | Customer Group | Link → `Customer Group` |  |
| `posting_time` | Posting Time | Time | **requis** |
| `company` | Company | Link → `Company` | **requis** |

## POS Invoice Reference

*POS Invoice Reference* — `accounts/pos_invoice_reference.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `pos_invoice` | POS Invoice | Link → `POS Invoice` | **requis**; colonne de liste |
| `customer` | Customer | Link → `Customer` | **requis**; lecture seule |
| `posting_date` | Date | Date | **requis**; colonne de liste |
| `grand_total` | Amount | Currency | **requis**; colonne de liste; devise de `parent_company.default_currency` |
| `is_return` | Is Return | Boolean | lecture seule |
| `return_against` | Return Against | Link → `POS Invoice` | lecture seule |

## POS Item Group

*POS Item Group* — `accounts/pos_item_group.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_group` | Item Group | Link → `Item Group` | **requis**; colonne de liste |

## POS Opening Entry

*POS Opening Entry* — `accounts/pos_opening_entry.yaml` · soumis

- **Numérotation** : série `POE-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `company`
- **Icône** : `folder-open`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `period_start_date` | Period Start Date | Datetime | **requis**; colonne de liste |
| `period_end_date` | Period End Date | Date | colonne de liste; lecture seule |
| `posting_date` | Posting Date | Date | **requis**; colonne de liste; défaut `today` |
| `company` | Company | Link → `Company` | **requis** |
| `pos_profile` | POS Profile | Link → `POS Profile` | **requis**; colonne de liste |
| `user` | Cashier | Text | **requis** |
| `set_posting_date` | Set Posting Date | Boolean | défaut `non` |
| `status` | Status | Select — Draft · Open · Closed · Cancelled | lecture seule; masqué; défaut `Draft` |
| `pos_closing_entry` | POS Closing Entry | Text | lecture seule |
| `balance_details` | Opening Balance Details | Table → `POS Opening Entry Detail` |  |

## POS Opening Entry Detail

*POS Opening Entry Detail* — `accounts/pos_opening_entry_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` | **requis**; colonne de liste |
| `opening_amount` | Opening Amount | Currency | **requis**; colonne de liste; devise de `parent_company.default_currency` |

## POS Payment Method

*POS Payment Method* — `accounts/pos_payment_method.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `default` | Default | Boolean | colonne de liste; défaut `non` |
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` | **requis**; colonne de liste |
| `allow_in_returns` | Allow In Returns | Boolean | colonne de liste; défaut `non` |

## POS Profile

*POS Profile* — `accounts/pos_profile.yaml`

- **Titre** : `customer`
- **Icône** : `monitor`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `disabled` | Disabled | Boolean | défaut `non` |
| `customer` | Customer | Link → `Customer` |  |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `country` | Country | Text | lecture seule |
| `company_address` | Company Address | Link → `Address` |  |
| `applicable_for_users` | Applicable for Users | Table → `POS Profile User` |  |
| `payments` | Payment Methods | Table → `POS Payment Method` |  |
| `item_groups` | Item Groups | Table → `POS Item Group` | — Only show Items from these Item Groups |
| `customer_groups` | Customer Groups | Table → `POS Customer Group` | — Only show Customer of these Customer Groups |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `tc_name` | Terms and Conditions | Link → `Terms and Conditions` |  |
| `select_print_heading` | Print Heading | Link → `Print Heading` |  |
| `selling_price_list` | Price List | Link → `Price List` |  |
| `currency` | Currency | Link → `Currency` | **requis** |
| `write_off_account` | Write Off Account | Link → `Account` | **requis** |
| `write_off_cost_center` | Write Off Cost Center | Link → `Cost Center` | **requis** |
| `account_for_change_amount` | Account for Change Amount | Link → `Account` |  |
| `income_account` | Income Account | Link → `Account` |  |
| `expense_account` | Expense Account | Link → `Account` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `taxes_and_charges` | Taxes and Charges | Link → `Sales Taxes and Charges Template` |  |
| `apply_discount_on` | Apply Discount On | Select — Grand Total · Net Total | défaut `Grand Total` |
| `tax_category` | Tax Category | Link → `Tax Category` |  |
| `print_format` | Print Format | Link → `Print Format` |  |
| `receipt_email_template` | Receipt Email Template | Link → `Email Template` | — Subject and message for receipts emailed from the POS. The template gets the invoice as doc. A message typed b |
| `warehouse` | Warehouse | Link → `Warehouse` | **requis** |
| `ignore_pricing_rule` | Ignore Pricing Rule | Boolean | défaut `non` |
| `update_stock` | Update Stock | Boolean | lecture seule; masqué |
| `hide_unavailable_items` | Hide Unavailable Items | Boolean | défaut `non` |
| `hide_images` | Hide Images | Boolean | défaut `non` |
| `auto_add_item_to_cart` | Automatically Add Filtered Item To Cart | Boolean | défaut `non` |
| `allow_rate_change` | Allow User to Edit Rate | Boolean | défaut `non` |
| `allow_discount_change` | Allow User to Edit Discount | Boolean | défaut `non` |
| `validate_stock_on_save` | Validate Stock on Save | Boolean | défaut `non` |
| `write_off_limit` | Write Off Limit | Currency | **requis**; devise de `currency`; — Auto write off precision loss while consolidation |
| `disable_rounded_total` | Disable Rounded Total | Boolean | défaut `non`; — If enabled, the consolidated invoices will have rounded total disabled |
| `utm_campaign` | Campaign | Link → `UTM Campaign` |  |
| `utm_source` | Source | Link → `UTM Source` |  |
| `utm_medium` | Medium | Link → `UTM Campaign` |  |
| `print_receipt_on_order_complete` | Print Receipt on Order Complete | Boolean | défaut `non` |
| `project` | Project | Link → `Project` |  |
| `set_grand_total_to_default_mop` | Set Grand Total to Default Payment Method | Boolean | défaut `oui` |
| `action_on_new_invoice` | Action on New Invoice | Select — Always Ask · Save Changes and Load New Invoice · Discard Changes and Load New Invoice | défaut `Always Ask` |
| `allow_partial_payment` | Allow Partial Payment | Boolean | défaut `non`; — Applicable only on Transactions made using POS |
| `allow_warehouse_change` | Allow User to Edit Warehouse | Boolean | défaut `non` |

## POS Profile User

*POS Profile User* — `accounts/pos_profile_user.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `default` | Default | Boolean | colonne de liste; défaut `non` |
| `user` | User | Text | colonne de liste |

## POS Search Fields

*POS Search Fields* — `accounts/pos_search_fields.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `fieldname` | Fieldname | Text | colonne de liste; lecture seule |

## POS Settings

*POS Settings* — `accounts/pos_settings.yaml` · document unique

- **Icône** : `settings`
- **Permissions explicites** — `create` : 0, `delete` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `invoice_fields` | POS Additional Fields | Table → `POS Field` |  |
| `pos_search_fields` | POS Search Fields | Table → `POS Search Fields` |  |
| `invoice_type` | Invoice Type Created via POS Screen | Select — Sales Invoice · POS Invoice | défaut `Sales Invoice`; — The system will create a Sales Invoice or a POS Invoice from the POS interface based on this setting. For high |
| `post_change_gl_entries` | Create Ledger Entries for Change Amount | Boolean | défaut `non`; — If enabled, ledger entries will be posted for change amount in POS transactions |

## Pricing Rule

*Pricing Rule* — `accounts/pricing_rule.yaml`

- **Vues** : calendar
- **Titre** : `customer`
- **Icône** : `badge-percent`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text | **requis** |
| `disable` | Disable | Boolean | défaut `non` |
| `apply_on` | Apply On | Select — Item Code · Item Group · Brand · Transaction | **requis**; colonne de liste; défaut `Item Code` |
| `price_or_product_discount` | Price or Product Discount | Select — Price · Product | **requis** |
| `warehouse` | Warehouse | Link → `Warehouse` |  |
| `items` | Apply Rule On Item Code | Table → `Pricing Rule Item Code` |  |
| `item_groups` | Apply Rule On Item Group | Table → `Pricing Rule Item Group` |  |
| `brands` | Apply Rule On Brand | Table → `Pricing Rule Brand` |  |
| `mixed_conditions` | Mixed Conditions | Boolean | défaut `non`; — Conditions will be applied on all the selected items combined. |
| `is_cumulative` | Is Cumulative | Boolean | défaut `non` |
| `coupon_code_based` | Coupon Code Based | Boolean | défaut `non` |
| `apply_rule_on_other` | Apply Rule On Other | Select — Item Code · Item Group · Brand |  |
| `other_item_code` | Item Code | Link → `Item` |  |
| `other_item_group` | Item Group | Link → `Item Group` |  |
| `other_brand` | Brand | Link → `Brand` |  |
| `selling` | Selling | Boolean | défaut `non` |
| `buying` | Buying | Boolean | défaut `non` |
| `applicable_for` | Applicable For | Select — Customer · Customer Group · Territory · Sales Partner · Campaign · Supplier · Supplier Group |  |
| `customer` | Customer | Link → `Customer` |  |
| `customer_group` | Customer Group | Link → `Customer Group` |  |
| `territory` | Territory | Link → `Territory` |  |
| `sales_partner` | Sales Partner | Link → `Sales Partner` |  |
| `campaign` | Campaign | Link → `UTM Campaign` |  |
| `supplier` | Supplier | Link → `Supplier` |  |
| `supplier_group` | Supplier Group | Link → `Supplier Group` |  |
| `min_qty` | Min Qty (As Per Stock UOM) | Decimal |  |
| `max_qty` | Max Qty (As Per Stock UOM) | Decimal |  |
| `min_amt` | Min Amt | Currency | devise de `currency` |
| `max_amt` | Max Amt | Currency | devise de `currency` |
| `valid_from` | Valid From | Date | défaut `today` |
| `valid_upto` | Valid Up To | Date |  |
| `company` | Company | Link → `Company` |  |
| `currency` | Currency | Link → `Currency` | **requis** |
| `margin_type` | Margin Type | Select — Percentage · Amount | défaut `Percentage` |
| `margin_rate_or_amount` | Margin Rate or Amount | Number | défaut `0.0` |
| `rate_or_discount` | Rate or Discount | Select — Rate · Discount Percentage · Discount Amount | défaut `Discount Percentage` |
| `apply_discount_on` | Apply Discount On | Select — Grand Total · Net Total | défaut `Grand Total` |
| `rate` | Rate | Currency | devise de `currency` |
| `discount_amount` | Discount Amount | Currency | devise de `currency` |
| `discount_percentage` | Discount Percentage | Number |  |
| `for_price_list` | For Price List | Link → `Price List` |  |
| `same_item` | Same Item | Boolean | défaut `non` |
| `free_item` | Free Item | Link → `Item` |  |
| `free_qty` | Qty | Decimal | défaut `0.000` |
| `free_item_uom` | UOM | Link → `UOM` |  |
| `free_item_rate` | Free Item Rate | Currency | devise de `currency`; — If rate is zero then item will be treated as "Free Item" |
| `threshold_percentage` | Threshold for Suggestion (In Percentage) | Percent | — System will notify to increase or decrease quantity or amount |
| `priority` | Priority | Select — 1 · 2 · 3 · 4 · 5 · 6 · 7 · 8 · 9 · 10 · 11 · 12 · 13 · 14 · 15 · 16 · 17 · 18 · 19 · 20 | — Higher the number, higher the priority |
| `apply_multiple_pricing_rules` | Apply Multiple Pricing Rules | Boolean | défaut `non` |
| `apply_discount_on_rate` | Apply Discount on Discounted Rate | Boolean | défaut `non` |
| `validate_applied_rule` | Validate Applied Rule | Boolean | défaut `non`; — If enabled, then system will only validate the pricing rule and not apply automatically. User has to manually  |
| `rule_description` | Rule Description | LongText |  |
| `promotional_scheme_id` | Promotional Scheme Id | Text | lecture seule; masqué |
| `promotional_scheme` | Promotional Scheme | Link → `Promotional Scheme` | lecture seule |
| `condition` | Condition | Code | — Simple Python Expression, Example: territory != 'All Territories' |
| `is_recursive` | Is Recursive | Boolean | défaut `non`; — Discounts to be applied in sequential ranges like buy 1 get 1, buy 2 get 2, buy 3 get 3 and so on |
| `naming_series` | Naming Series | Select — PRLE-.#### | défaut `PRLE-.####` |
| `round_free_qty` | Round Free Qty | Boolean | défaut `non` |
| `recurse_for` | Recurse Every (As Per Transaction UOM) | Number | — Give free item for every N quantity |
| `apply_recursion_over` | Apply Recursion Over (As Per Transaction UOM) | Number | défaut `0.0`; — Qty for which recursion isn't applicable. |
| `has_priority` | Has Priority | Boolean | défaut `non`; — Enable this checkbox even if you want to set the zero priority |
| `dont_enforce_free_item_qty` | Don't Enforce Free Item Qty | Boolean | défaut `non` |

## Pricing Rule Brand

*Pricing Rule Brand* — `accounts/pricing_rule_brand.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `brand` | Brand | Link → `Brand` | colonne de liste |
| `uom` | UOM | Link → `UOM` | colonne de liste |

## Pricing Rule Detail

*Pricing Rule Detail* — `accounts/pricing_rule_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `pricing_rule` | Pricing Rule | Link → `Pricing Rule` | colonne de liste; lecture seule |
| `item_code` | Item Code | Text | colonne de liste; lecture seule |
| `margin_type` | Margin Type | Text | lecture seule; masqué |
| `rate_or_discount` | Rate or Discount | Text | lecture seule; masqué |
| `child_docname` | Child Docname | Text | lecture seule; masqué |
| `rule_applied` | Rule Applied | Boolean | lecture seule |

## Pricing Rule Item Code

*Pricing Rule Item Code* — `accounts/pricing_rule_item_code.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | colonne de liste |
| `uom` | UOM | Link → `UOM` | colonne de liste |

## Pricing Rule Item Group

*Pricing Rule Item Group* — `accounts/pricing_rule_item_group.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_group` | Item Group | Link → `Item Group` | colonne de liste |
| `uom` | UOM | Link → `UOM` | colonne de liste |

## Process Deferred Accounting

*Process Deferred Accounting* — `accounts/process_deferred_accounting.yaml` · soumis

- **Numérotation** : série `PDA-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `company`
- **Icône** : `list-clock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `type` | Type | Select — Income · Expense | **requis**; colonne de liste |
| `start_date` | Service Start Date | Date | **requis**; colonne de liste |
| `end_date` | Service End Date | Date | **requis**; colonne de liste |
| `posting_date` | Posting Date | Date | **requis**; colonne de liste; défaut `today` |
| `account` | Account | Link → `Account` |  |
| `company` | Company | Link → `Company` | **requis** |

## Process Payment Reconciliation

*Process Payment Reconciliation* — `accounts/process_payment_reconciliation.yaml` · soumis

- **Numérotation** : série `PPR-{YYYY}-{#####}`
- **Titre** : `company`
- **Icône** : `scale`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `status` | Status | Select — Queued · Running · Paused · Completed · Partially Reconciled · Failed · Cancelled | lecture seule |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `party_type` | Party Type | Text | **requis**; colonne de liste |
| `party` | Party | DynamicLink → `party_type` | colonne de liste |
| `receivable_payable_account` | Receivable/Payable Account | Link → `Account` | **requis**; colonne de liste |
| `from_invoice_date` | From Invoice Date | Date |  |
| `to_invoice_date` | To Invoice Date | Date |  |
| `from_payment_date` | From Payment Date | Date |  |
| `to_payment_date` | To Payment Date | Date |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `bank_cash_account` | Bank/Cash Account | Link → `Account` |  |
| `error_log` | Error Log | LongText |  |
| `default_advance_account` | Default Advance Account | Link → `Account` | — Only 'Payment Entries' made against this advance account are supported. |

## Process Payment Reconciliation Log

*Process Payment Reconciliation Log* — `accounts/process_payment_reconciliation_log.yaml`

- **Titre** : `status`
- **Icône** : `file-clock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `allocations` | Allocations | Table → `Process Payment Reconciliation Log Allocations` | lecture seule |
| `reconciled` | Reconciled | Boolean | lecture seule; — All allocations have been successfully reconciled |
| `total_allocations` | Total Allocations | Int | colonne de liste; lecture seule |
| `allocated` | Allocated | Boolean | lecture seule; — Invoices and Payments have been Fetched and Allocated |
| `reconciled_entries` | Reconciled Entries | Int | colonne de liste; lecture seule |
| `error_log` | Reconciliation Error Log | LongText | lecture seule |
| `process_pr` | Parent Document | Link → `Process Payment Reconciliation` | **requis**; colonne de liste; lecture seule |
| `status` | Status | Select — Running · Paused · Reconciled · Partially Reconciled · Failed · Cancelled | lecture seule |

## Process Payment Reconciliation Log Allocations

*Process Payment Reconciliation Log Allocations* — `accounts/process_payment_reconciliation_log_allocations.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `reference_type` | Reference Type | Text | **requis**; lecture seule |
| `reference_name` | Reference Name | DynamicLink → `reference_type` | colonne de liste; lecture seule |
| `reference_row` | Reference Row | Text | lecture seule; masqué |
| `invoice_type` | Invoice Type | Text | **requis**; lecture seule |
| `invoice_number` | Invoice Number | DynamicLink → `invoice_type` | colonne de liste; lecture seule |
| `allocated_amount` | Allocated Amount | Currency | **requis**; colonne de liste |
| `unreconciled_amount` | Unreconciled Amount | Currency | lecture seule; masqué |
| `amount` | Amount | Currency | lecture seule; masqué |
| `is_advance` | Is Advance | Text | lecture seule; masqué |
| `difference_amount` | Difference Amount | Currency | colonne de liste; lecture seule |
| `difference_account` | Difference Account | Link → `Account` | lecture seule |
| `exchange_rate` | Exchange Rate | Number | lecture seule |
| `currency` | Currency | Link → `Currency` | masqué |
| `reconciled` | Reconciled | Boolean | colonne de liste; défaut `non` |
| `gain_loss_posting_date` | Difference Posting Date | Date |  |

## Process Period Closing Voucher

*Process Period Closing Voucher* — `accounts/process_period_closing_voucher.yaml` · soumis

- **Numérotation** : série `PPCV-{YYYY}-{#####}`
- **Vues** : kanban
- **Titre** : `status`
- **Icône** : `lock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `parent_pcv` | PCV | Link → `Period Closing Voucher` | **requis**; colonne de liste |
| `status` | Status | Select — Queued · Running · Paused · Completed · Cancelled | défaut `Queued` |
| `p_l_closing_balance` | P&L Closing Balance | JSON |  |
| `normal_balances` | Dates to Process | Table → `Process Period Closing Voucher Detail` |  |
| `z_opening_balances` | Opening Balances | Table → `Process Period Closing Voucher Detail` |  |
| `bs_closing_balance` | Balance Sheet Closing Balance | JSON |  |

## Process Period Closing Voucher Detail

*Process Period Closing Voucher Detail* — `accounts/process_period_closing_voucher_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `processing_date` | Processing Date | Date | colonne de liste |
| `status` | Status | Select — Queued · Running · Paused · Completed · Cancelled | colonne de liste; défaut `Queued` |
| `closing_balance` | Closing Balance | JSON | colonne de liste |
| `report_type` | Report Type | Select — Profit and Loss · Balance Sheet | colonne de liste; défaut `Profit and Loss` |

## Process Statement Of Accounts

*Process Statement Of Accounts* — `accounts/process_statement_of_accounts.yaml`

- **Vues** : calendar, gantt
- **Titre** : `company`
- **Icône** : `mail`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `frequency` | Frequency | Select — Daily · Weekly · Biweekly · Monthly · Quarterly |  |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `from_date` | From Date | Date |  |
| `to_date` | To Date | Date |  |
| `cost_center` | Cost Center | Table → `PSOA Cost Center` |  |
| `project` | Project | Table → `PSOA Project` |  |
| `customer_collection` | Select Customers By | Text |  |
| `collection_name` | Recipient | DynamicLink → `customer_collection` |  |
| `account` | Account | Link → `Account` |  |
| `finance_book` | Finance Book | Link → `Finance Book` |  |
| `orientation` | Orientation | Select — Landscape · Portrait |  |
| `start_date` | Start Date | Date | défaut `today` |
| `currency` | Currency | Link → `Currency` |  |
| `include_ageing` | Include Ageing Summary | Boolean | colonne de liste; défaut `non` |
| `ageing_based_on` | Ageing Based On | Select — Due Date · Posting Date | défaut `Due Date` |
| `enable_auto_email` | Enable Auto Email | Boolean | colonne de liste; défaut `non` |
| `primary_mandatory` | Send To Primary Contact | Boolean | défaut `oui`; — A customer must have primary contact email. |
| `cc_to` | CC To | Table → `Process Statement Of Accounts CC` |  |
| `filter_duration` | Filter Duration (Months) | Int | défaut `1` |
| `customers` | Customers | Table → `Process Statement Of Accounts Customer` |  |
| `subject` | Subject | Text |  |
| `body` | Body | TextEditor |  |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `terms_and_conditions` | Terms and Conditions | Link → `Terms and Conditions` |  |
| `include_break` | Page Break After Each SoA | Boolean | défaut `oui` |
| `show_net_values_in_party_account` | Show Net Values in Party Account | Boolean | défaut `non` |
| `sender` | Sender | Link → `Email Account` |  |
| `report` | Report | Select — General Ledger · Accounts Receivable | **requis** |
| `posting_date` | Posting Date | Date | défaut `today` |
| `payment_terms_template` | Payment Terms Template | Link → `Payment Terms Template` |  |
| `sales_partner` | Sales Partner | Link → `Sales Partner` |  |
| `sales_person` | Sales Person | Link → `Sales Person` |  |
| `territory` | Territory | Link → `Territory` |  |
| `based_on_payment_terms` | Based On Payment Terms | Boolean | défaut `non` |
| `pdf_name` | PDF Name | Text |  |
| `ignore_exchange_rate_revaluation_journals` | Ignore Exchange Rate Revaluation and Gain / Loss Journals | Boolean | défaut `non` |
| `ignore_cr_dr_notes` | Ignore System Generated Credit / Debit Notes | Boolean | défaut `non` |
| `show_remarks` | Show Remarks | Boolean | défaut `non` |
| `categorize_by` | Categorize By | Select — Categorize by Voucher · Categorize by Voucher (Consolidated) | défaut `Categorize by Voucher (Consolidated)` |
| `show_future_payments` | Show Future Payments | Boolean | défaut `non` |
| `print_format` | Print Format | Link → `Print Format` |  |
| `show_opening_entries` | Show Opening Entries | Boolean | défaut `non` |

## Process Statement Of Accounts CC

*Process Statement Of Accounts CC* — `accounts/process_statement_of_accounts_cc.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `cc` | CC | Text | colonne de liste |

## Process Statement Of Accounts Customer

*Process Statement Of Accounts Customer* — `accounts/process_statement_of_accounts_customer.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `customer` | Customer | Link → `Customer` | **requis**; colonne de liste |
| `primary_email` | Primary Contact Email | Text | colonne de liste; lecture seule |
| `billing_email` | Billing Email | Text | colonne de liste |
| `customer_name` | Customer Name | Text | lecture seule; recopié de `customer.customer_name` |

## Process Subscription

*Process Subscription* — `accounts/process_subscription.yaml` · soumis

- **Numérotation** : série `PRSU-{YYYY}-{#####}`
- **Vues** : calendar
- **Icône** : `repeat`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `posting_date` | Posting Date | Date | **requis**; colonne de liste |
| `subscription` | Subscription | Link → `Subscription` |  |

## Promotional Scheme

*Promotional Scheme* — `accounts/promotional_scheme.yaml`

- **Vues** : calendar
- **Titre** : `company`
- **Icône** : `megaphone`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `apply_on` | Apply On | Select — Item Code · Item Group · Brand · Transaction | **requis**; colonne de liste; défaut `Item Code` |
| `disable` | Disable | Boolean | défaut `non` |
| `items` | Pricing Rule Item Code | Table → `Pricing Rule Item Code` |  |
| `item_groups` | Pricing Rule Item Group | Table → `Pricing Rule Item Group` |  |
| `brands` | Pricing Rule Brand | Table → `Pricing Rule Brand` |  |
| `mixed_conditions` | Mixed Conditions | Boolean | défaut `non` |
| `is_cumulative` | Is Cumulative | Boolean | défaut `non` |
| `apply_rule_on_other` | Apply Rule On Other | Select — Item Code · Item Group · Brand |  |
| `other_item_code` | Item Code | Link → `Item` |  |
| `other_item_group` | Item Group | Link → `Item Group` |  |
| `other_brand` | Brand | Link → `Brand` |  |
| `selling` | Selling | Boolean | défaut `non` |
| `buying` | Buying | Boolean | défaut `non` |
| `applicable_for` | Applicable For | Select — Customer · Customer Group · Territory · Sales Partner · Campaign · Supplier · Supplier Group |  |
| `customer` | Customer | Table → `Customer Item` |  |
| `customer_group` | Customer Group | Table → `Customer Group Item` |  |
| `territory` | Territory | Table → `Territory Item` |  |
| `sales_partner` | Sales Partner | Table → `Sales Partner Item` |  |
| `campaign` | Campaign | Table → `Campaign Item` |  |
| `supplier` | Supplier | Table → `Supplier Item` |  |
| `supplier_group` | Supplier Group | Table → `Supplier Group Item` |  |
| `valid_from` | Valid From | Date | défaut `today` |
| `valid_upto` | Valid Up To | Date |  |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `currency` | Currency | Link → `Currency` |  |
| `price_discount_slabs` | Promotional Scheme Price Discount | Table → `Promotional Scheme Price Discount` |  |
| `product_discount_slabs` | Promotional Scheme Product Discount | Table → `Promotional Scheme Product Discount` |  |

## Promotional Scheme Price Discount

*Promotional Scheme Price Discount* — `accounts/promotional_scheme_price_discount.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `disable` | Disable | Boolean | défaut `non` |
| `rule_description` | Rule Description | LongText | **requis** |
| `min_qty` | Min Qty | Decimal | colonne de liste; défaut `0.000` |
| `max_qty` | Max Qty | Decimal | colonne de liste; défaut `0.000` |
| `min_amount` | Min Amount | Currency | colonne de liste; devise de `parent_currency` |
| `max_amount` | Max Amount | Currency | colonne de liste; devise de `parent_currency` |
| `rate_or_discount` | Discount Type | Select — Rate · Discount Percentage · Discount Amount | colonne de liste; défaut `Discount Percentage` |
| `rate` | Rate | Currency | devise de `parent_currency` |
| `discount_amount` | Discount Amount | Currency | devise de `parent_currency` |
| `discount_percentage` | Discount Percentage | Number |  |
| `for_price_list` | For Price List | Link → `Price List` |  |
| `warehouse` | Warehouse | Link → `Warehouse` |  |
| `threshold_percentage` | Threshold for Suggestion | Percent |  |
| `validate_applied_rule` | Validate Applied Rule | Boolean | défaut `non` |
| `priority` | Priority | Select — 1 · 2 · 3 · 4 · 5 · 6 · 7 · 8 · 9 · 10 · 11 · 12 · 13 · 14 · 15 · 16 · 17 · 18 · 19 · 20 |  |
| `apply_multiple_pricing_rules` | Apply Multiple Pricing Rules | Boolean | défaut `non` |
| `apply_discount_on_rate` | Apply Discount on Rate | Boolean | défaut `non` |

## Promotional Scheme Product Discount

*Promotional Scheme Product Discount* — `accounts/promotional_scheme_product_discount.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `disable` | Disable | Boolean | défaut `non` |
| `rule_description` | Rule Description | LongText | **requis** |
| `min_qty` | Min Qty | Decimal | colonne de liste; défaut `0.000` |
| `max_qty` | Max Qty | Decimal | colonne de liste; défaut `0.000` |
| `min_amount` | Min Amount | Currency | colonne de liste; devise de `parent_currency` |
| `max_amount` | Max Amount | Currency | colonne de liste; devise de `parent_currency` |
| `same_item` | Same Item | Boolean | défaut `non` |
| `free_item` | Item Code | Link → `Item` | colonne de liste |
| `free_qty` | Qty | Decimal | colonne de liste |
| `free_item_uom` | UOM | Link → `UOM` |  |
| `free_item_rate` | Rate | Currency | devise de `parent_currency` |
| `warehouse` | Warehouse | Link → `Warehouse` |  |
| `threshold_percentage` | Threshold for Suggestion | Percent |  |
| `priority` | Priority | Select — 1 · 2 · 3 · 4 · 5 · 6 · 7 · 8 · 9 · 10 · 11 · 12 · 13 · 14 · 15 · 16 · 17 · 18 · 19 · 20 |  |
| `apply_multiple_pricing_rules` | Apply Multiple Pricing Rules | Boolean | défaut `non` |
| `is_recursive` | Is Recursive | Boolean | défaut `non`; — Discounts to be applied in sequential ranges like buy 1 get 1, buy 2 get 2, buy 3 get 3 and so on |
| `recurse_for` | Recurse Every (As Per Transaction UOM) | Number | défaut `0.0`; — Give free item for every N quantity |
| `apply_recursion_over` | Apply Recursion Over (As Per Transaction UOM) | Number | défaut `0.0`; — Qty for which recursion isn't applicable. |
| `round_free_qty` | Round Free Qty | Boolean | défaut `non` |

## PSOA Cost Center

*PSOA Cost Center* — `accounts/psoa_cost_center.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `cost_center_name` | Cost Center | Link → `Cost Center` | **requis**; colonne de liste |

## PSOA Project

*PSOA Project* — `accounts/psoa_project.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `project_name` | Project | Link → `Project` |  |

## Purchase Invoice

*Purchase Invoice* — `accounts/purchase_invoice.yaml` · soumis

- **Numérotation** : série `PUIN-{YYYY}-{#####}`
- **Vues** : kanban, calendar, gantt
- **Titre** : `supplier`
- **Icône** : `receipt-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text |  |
| `naming_series` | Series | Select — ACC-PINV-.YYYY.- · ACC-PINV-RET-.YYYY.- | **requis** |
| `supplier` | Supplier | Link → `Supplier` | **requis** |
| `supplier_name` | Supplier Name | Text | lecture seule; recopié de `supplier.supplier_name` |
| `tax_id` | Tax Id | Text | lecture seule |
| `due_date` | Due Date | Date | colonne de liste |
| `is_paid` | Is Paid | Boolean | défaut `non` |
| `is_return` | Is Return (Debit Note) | Boolean | défaut `non` |
| `apply_tds` | Consider for Tax Withholding | Boolean | défaut `non` |
| `company` | Company | Link → `Company` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `posting_date` | Posting Date | Date | **requis**; colonne de liste; défaut `today` |
| `posting_time` | Posting Time | Time |  |
| `set_posting_time` | Edit Posting Date and Time | Boolean | défaut `non` |
| `on_hold` | Hold Invoice | Boolean | défaut `non` |
| `release_date` | Release Date | Date | visible si `on_hold`; — Once set, this invoice will be on hold till the set date |
| `hold_comment` | Reason For Putting On Hold | LongText | visible si `on_hold` |
| `bill_no` | Supplier Invoice No | Text | colonne de liste |
| `bill_date` | Supplier Invoice Date | Date | visible si `bill_no` |
| `return_against` | Return Against Purchase Invoice | Link → `Purchase Invoice` | lecture seule; visible si `is_return`; obligatoire si `is_return` |
| `update_billed_amount_in_purchase_order` | Update Billed Amount in Purchase Order | Boolean | défaut `non` |
| `update_billed_amount_in_purchase_receipt` | Update Billed Amount in Purchase Receipt | Boolean | défaut `oui` |
| `supplier_address` | Select Supplier Address | Link → `Address` |  |
| `address_display` | Address | TextEditor | lecture seule |
| `contact_person` | Contact Person | Link → `Contact` |  |
| `contact_display` | Contact | LongText | lecture seule |
| `contact_mobile` | Mobile No | LongText | lecture seule |
| `contact_email` | Contact Email | LongText | lecture seule |
| `shipping_address` | Select Shipping Address | Link → `Address` |  |
| `shipping_address_display` | Shipping Address | TextEditor | lecture seule |
| `currency` | Currency | Link → `Currency` |  |
| `conversion_rate` | Exchange Rate | Number |  |
| `buying_price_list` | Price List | Link → `Price List` |  |
| `price_list_currency` | Price List Currency | Link → `Currency` | lecture seule |
| `plc_conversion_rate` | Price List Exchange Rate | Number |  |
| `ignore_pricing_rule` | Ignore Pricing Rule | Boolean | défaut `non` |
| `set_warehouse` | Set Accepted Warehouse | Link → `Warehouse` | visible si `update_stock` |
| `rejected_warehouse` | Rejected Warehouse | Link → `Warehouse` | visible si `update_stock` |
| `is_subcontracted` | Is Subcontracted | Boolean | lecture seule |
| `update_stock` | Update Stock | Boolean | défaut `non`; — If checked, updates inventory; stock and accounting entries are created together. Leave unchecked if a Purchas |
| `scan_barcode` | Scan Barcode | Text |  |
| `items` | Items | Table → `Purchase Invoice Item` |  |
| `pricing_rules` | Pricing Rule Detail | Table → `Pricing Rule Detail` | lecture seule |
| `supplied_items` | Supplied Items | Table → `Purchase Receipt Item Supplied` |  |
| `total_qty` | Total Quantity | Decimal | lecture seule; calculé : `sum(items.qty)` |
| `base_total` | Total (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_net_total` | Net Total (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
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
| `base_rounded_total` | Rounded Total | Currency | lecture seule; devise de `company.default_currency` |
| `base_in_words` | In Words | Text | lecture seule |
| `grand_total` | Grand Total | Currency | colonne de liste; lecture seule; calculé : `total + total_taxes_and_charges`; devise de `currency` |
| `rounding_adjustment` | Rounding Adjustment | Currency | lecture seule; devise de `currency` |
| `rounded_total` | Rounded Total | Currency | lecture seule; devise de `currency` |
| `in_words` | In Words | Text | lecture seule |
| `total_advance` | Total Advance | Currency | lecture seule; devise de `currency` |
| `outstanding_amount` | Outstanding Amount | Currency | lecture seule; calculé : `grand_total - total_advance - paid_amount - write_off_amount`; devise de `party_account_currency` |
| `disable_rounded_total` | Disable Rounded Total | Boolean | défaut `non` |
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` | visible si `is_paid` |
| `cash_bank_account` | Cash/Bank Account | Link → `Account` | visible si `is_paid`; obligatoire si `is_paid` |
| `clearance_date` | Clearance Date | Date | lecture seule |
| `paid_amount` | Paid Amount | Currency | devise de `currency` |
| `base_paid_amount` | Paid Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `write_off_amount` | Write Off Amount | Currency | devise de `currency` |
| `base_write_off_amount` | Write Off Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `write_off_account` | Write Off Account | Link → `Account` |  |
| `write_off_cost_center` | Write Off Cost Center | Link → `Cost Center` |  |
| `allocate_advances_automatically` | Set Advances and Allocate (FIFO) | Boolean | défaut `non` |
| `advances` | Advances | Table → `Purchase Invoice Advance` |  |
| `payment_terms_template` | Payment Terms Template | Link → `Payment Terms Template` |  |
| `payment_schedule` | Payment Schedule | Table → `Payment Schedule` |  |
| `tc_name` | Terms | Link → `Terms and Conditions` |  |
| `terms` | Terms and Conditions | TextEditor |  |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `group_same_items` | Group same items | Boolean | défaut `non` |
| `select_print_heading` | Print Heading | Link → `Print Heading` |  |
| `language` | Print Language | Text | lecture seule |
| `is_internal_supplier` | Is Internal Supplier | Boolean | lecture seule |
| `credit_to` | Credit To | Link → `Account` | **requis** |
| `party_account_currency` | Party Account Currency | Link → `Currency` | lecture seule; masqué |
| `is_opening` | Is Opening Entry | Select — No · Yes | défaut `No` |
| `against_expense_account` | Against Expense Account | LongText | masqué |
| `status` | Status | Select — Draft · Return · Debit Note Issued · Submitted · Paid · Partly Paid · Unpaid · Overdue · Cancelled · Internal Transfer | défaut `Draft` |
| `inter_company_invoice_reference` | Inter Company Invoice Reference | Link → `Sales Invoice` | lecture seule; visible si `is_internal_supplier` |
| `remarks` | Remarks | LongText |  |
| `from_date` | From Date | Date | — Start date of current invoice's period |
| `to_date` | To Date | Date | — End date of current invoice's period |
| `auto_repeat` | Auto Repeat | Link → `Auto Repeat` | lecture seule |
| `billing_address` | Select Billing Address | Link → `Address` |  |
| `billing_address_display` | Billing Address | TextEditor | lecture seule |
| `project` | Project | Link → `Project` |  |
| `unrealized_profit_loss_account` | Unrealized Profit / Loss Account | Link → `Account` | visible si `is_internal_supplier`; — Unrealized Profit/Loss account for intra-company transfers |
| `represents_company` | Represents Company | Link → `Company` | lecture seule; visible si `is_internal_supplier`; obligatoire si `is_internal_supplier`; — Company which internal supplier represents |
| `set_from_warehouse` | Set From Warehouse | Link → `Warehouse` |  |
| `supplier_warehouse` | Supplier Warehouse | Link → `Warehouse` | visible si `is_subcontracted` |
| `per_received` | Per Received | Percent | lecture seule; masqué |
| `ignore_default_payment_terms_template` | Ignore Default Payment Terms Template | Boolean | lecture seule; masqué |
| `subscription` | Subscription | Link → `Subscription` |  |
| `incoterm` | Incoterm | Link → `Incoterm` |  |
| `named_place` | Named Place | Text |  |
| `only_include_allocated_payments` | Only Include Allocated Payments | Boolean | défaut `non`; — Advance payments allocated against orders will only be fetched |
| `use_company_roundoff_cost_center` | Use Company Default Round Off Cost Center | Boolean | défaut `non` |
| `use_transaction_date_exchange_rate` | Use Transaction Date Exchange Rate | Boolean | lecture seule |
| `supplier_group` | Supplier Group | Link → `Supplier Group` |  |
| `update_outstanding_for_self` | Update Outstanding for Self | Boolean | défaut `oui`; — Debit Note will update it's own outstanding amount, even if 'Return Against' is specified. |
| `sender` | Sender | Text |  |
| `dispatch_address_display` | Dispatch Address | TextEditor | lecture seule |
| `dispatch_address` | Select Dispatch Address  | Link → `Address` |  |
| `last_scanned_warehouse` | Last Scanned Warehouse | Text |  |
| `claimed_landed_cost_amount` | Claimed Landed Cost Amount (Company Currency) | Currency | lecture seule; devise de `currency` |
| `item_wise_tax_details` | Item Wise Tax Details | Table → `Item Wise Tax Detail` | masqué |
| `tax_withholding_group` | Tax Withholding Group | Link → `Tax Withholding Group` |  |
| `tax_withholding_entries` | Tax Withholding Entries | Table → `Tax Withholding Entry` |  |
| `ignore_tax_withholding_threshold` | Ignore Tax Withholding Threshold | Boolean | défaut `non` |
| `override_tax_withholding_entries` | Edit Tax Withholding Entries | Boolean | défaut `non` |

## Purchase Invoice Advance

*Purchase Invoice Advance* — `accounts/purchase_invoice_advance.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `reference_type` | Reference Type | Text | lecture seule |
| `reference_name` | Reference Name | DynamicLink → `reference_type` | colonne de liste; lecture seule |
| `remarks` | Remarks | LongText | colonne de liste; lecture seule |
| `reference_row` | Reference Row | Text | lecture seule; masqué |
| `advance_amount` | Advance Amount | Currency | colonne de liste; lecture seule; devise de `parent_currency` |
| `allocated_amount` | Allocated Amount | Currency | colonne de liste; devise de `parent_currency` |
| `exchange_gain_loss` | Exchange Gain/Loss | Currency | lecture seule; devise de `parent_currency` |
| `ref_exchange_rate` | Reference Exchange Rate | Number | lecture seule |
| `difference_posting_date` | Difference Posting Date | Date | colonne de liste |

## Purchase Invoice Item

*Purchase Invoice Item* — `accounts/purchase_invoice_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item | Link → `Item` | colonne de liste |
| `item_name` | Item Name | Text | **requis** |
| `description` | Description | TextEditor |  |
| `received_qty` | Received Qty | Decimal | lecture seule |
| `qty` | Accepted Qty | Decimal | **requis**; colonne de liste |
| `rejected_qty` | Rejected Qty | Decimal |  |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `uom` | UOM | Link → `UOM` | **requis** |
| `conversion_factor` | UOM Conversion Factor | Number | **requis**; lecture seule |
| `stock_qty` | Accepted Qty in Stock UOM | Decimal | **requis**; lecture seule |
| `price_list_rate` | Price List Rate | Currency | devise de `parent_currency` |
| `discount_percentage` | Discount on Price List Rate (%) | Percent |  |
| `discount_amount` | Discount Amount | Currency | devise de `parent_currency` |
| `base_price_list_rate` | Price List Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `rate` | Rate | Currency | **requis**; colonne de liste; devise de `parent_currency` |
| `amount` | Amount | Currency | colonne de liste; lecture seule; calculé : `qty * rate`; devise de `parent_currency` |
| `base_rate` | Rate (Company Currency) | Currency | **requis**; lecture seule; devise de `parent_company.default_currency` |
| `base_amount` | Amount (Company Currency) | Currency | **requis**; lecture seule; devise de `parent_company.default_currency` |
| `pricing_rules` | Pricing Rules | LongText | lecture seule; masqué |
| `is_free_item` | Is Free Item | Boolean | lecture seule |
| `net_rate` | Net Rate | Currency | lecture seule; devise de `parent_currency` |
| `net_amount` | Net Amount | Currency | lecture seule; calculé : `amount - discount_amount`; devise de `parent_currency` |
| `base_net_rate` | Net Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_net_amount` | Net Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `weight_per_unit` | Weight Per Unit | Number |  |
| `total_weight` | Total Weight | Number | lecture seule |
| `weight_uom` | Weight UOM | Link → `UOM` |  |
| `warehouse` | Accepted Warehouse | Link → `Warehouse` |  |
| `rejected_warehouse` | Rejected Warehouse | Link → `Warehouse` |  |
| `quality_inspection` | Quality Inspection | Link → `Quality Inspection` |  |
| `batch_no` | Batch No | Link → `Batch` |  |
| `serial_no` | Serial No | LongText |  |
| `rejected_serial_no` | Rejected Serial No | LongText |  |
| `expense_account` | Expense Head | Link → `Account` |  |
| `item_tax_template` | Item Tax Template | Link → `Item Tax Template` |  |
| `project` | Project | Link → `Project` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `deferred_expense_account` | Deferred Expense Account | Link → `Account` | visible si `enable_deferred_expense`; obligatoire si `enable_deferred_expense` |
| `service_stop_date` | Service Stop Date | Date | visible si `enable_deferred_expense` |
| `enable_deferred_expense` | Enable Deferred Expense | Boolean | défaut `non` |
| `service_start_date` | Service Start Date | Date | visible si `enable_deferred_expense`; obligatoire si `enable_deferred_expense` |
| `service_end_date` | Service End Date | Date | visible si `enable_deferred_expense`; obligatoire si `enable_deferred_expense` |
| `allow_zero_valuation_rate` | Allow Zero Valuation Rate | Boolean | défaut `non` |
| `brand` | Brand | Link → `Brand` | masqué |
| `item_group` | Item Group | Link → `Item Group` | lecture seule |
| `item_tax_rate` | Item Tax Rate | Code | lecture seule; masqué; — Tax detail table fetched from item master as a string and stored in this field. Used for Taxes and Charges |
| `item_tax_amount` | Item Tax Amount Included in Value | Currency | lecture seule; masqué; devise de `parent_currency` |
| `purchase_order` | Purchase Order | Link → `Purchase Order` | lecture seule; cible submitted |
| `include_exploded_items` | Include Exploded Items | Boolean | lecture seule |
| `is_fixed_asset` | Is Fixed Asset | Boolean | lecture seule; masqué |
| `asset_location` | Asset Location | Link → `Location` | visible si `is_fixed_asset` |
| `po_detail` | Purchase Order Item | Text | lecture seule; masqué |
| `purchase_receipt` | Purchase Receipt | Link → `Purchase Receipt` | lecture seule; cible submitted |
| `page_break` | Page Break | Boolean | défaut `non` |
| `pr_detail` | Purchase Receipt Detail | Text | lecture seule; masqué |
| `valuation_rate` | Valuation Rate | Currency | lecture seule; masqué; devise de `parent_currency` |
| `rm_supp_cost` | Raw Materials Supplied Cost | Currency | lecture seule; masqué; devise de `parent_currency` |
| `landed_cost_voucher_amount` | Landed Cost Voucher Amount | Currency | lecture seule; devise de `parent_currency` |
| `manufacturer` | Manufacturer | Link → `Manufacturer` |  |
| `manufacturer_part_no` | Manufacturer Part Number | Text |  |
| `asset_category` | Asset Category | Link → `Asset Category` | lecture seule; visible si `is_fixed_asset` |
| `from_warehouse` | From Warehouse | Link → `Warehouse` |  |
| `purchase_invoice_item` | Purchase Invoice Item | Text | lecture seule |
| `stock_uom_rate` | Rate of Stock UOM | Currency | lecture seule; devise de `parent_currency` |
| `sales_invoice_item` | Sales Invoice Item | Text | lecture seule |
| `margin_type` | Margin Type | Select — Percentage · Amount |  |
| `margin_rate_or_amount` | Margin Rate or Amount | Number |  |
| `rate_with_margin` | Rate With Margin | Currency | lecture seule; devise de `parent_currency` |
| `base_rate_with_margin` | Rate With Margin (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `product_bundle` | Product Bundle | Link → `Product Bundle` | lecture seule; masqué; — Product Bundle version this row was packed from |
| `apply_tds` | Consider for Tax Withholding | Boolean | défaut `oui` |
| `serial_and_batch_bundle` | Serial and Batch Bundle | Link → `Serial and Batch Bundle` |  |
| `rejected_serial_and_batch_bundle` | Rejected Serial and Batch Bundle | Link → `Serial and Batch Bundle` |  |
| `wip_composite_asset` | WIP Composite Asset | Link → `Asset` |  |
| `use_serial_batch_fields` | Use Serial No / Batch Fields | Boolean | défaut `non` |
| `material_request` | Material Request | Link → `Material Request` | lecture seule |
| `material_request_item` | Material Request Item | Text | lecture seule; masqué |
| `sales_incoming_rate` | Sales Incoming Rate | Currency | masqué; devise de `parent_currency`; — Valuation rate for the item as per Sales Invoice (Only for Internal Transfers) |
| `distributed_discount_amount` | Distributed Discount Amount | Currency | devise de `parent_currency` |
| `mapped_additional_discount_amount` | Additional Discount per Stock Unit | Currency | lecture seule; devise de `parent_currency`; — Tax-exclusive additional discount carried from a source document, per stock unit. |
| `tax_withholding_category` | Tax Withholding Category | Link → `Tax Withholding Category` |  |
| `delivered_by_supplier` | Delivered by Supplier | Boolean | lecture seule; masqué |

## Purchase Taxes and Charges

*Purchase Taxes and Charges* — `accounts/purchase_taxes_and_charges.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `category` | Consider Tax or Charge for | Select — Valuation and Total · Valuation · Total | **requis**; défaut `Total` |
| `add_deduct_tax` | Add or Deduct | Select — Add · Deduct | **requis**; défaut `Add` |
| `charge_type` | Type | Select — Actual · On Net Total · On Previous Row Amount · On Previous Row Total · On Item Quantity | **requis**; colonne de liste; défaut `On Net Total` |
| `row_id` | Reference Row # | Text |  |
| `allocate_full_amount_to_stock_items` | Allocate Full Amount to Stock Items | Boolean | défaut `oui`; — If checked, the entire amount (e.g. Freight) is allocated to the valuation of stock & asset items only. If unc |
| `included_in_print_rate` | Is this Tax included in Basic Rate? | Boolean | défaut `non`; — If checked, the tax amount will be considered as already included in the Print Rate / Print Amount |
| `account_head` | Account Head | Link → `Account` | **requis**; colonne de liste |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `description` | Description | LongText | **requis** |
| `rate` | Tax Rate | Number | colonne de liste |
| `tax_amount` | Amount | Currency | colonne de liste |
| `tax_amount_after_discount_amount` | Tax Amount After Discount Amount | Currency | lecture seule |
| `total` | Total | Currency | colonne de liste; lecture seule |
| `base_tax_amount` | Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_total` | Total (Company Currency) | Currency | masqué; devise de `parent_company.default_currency` |
| `base_tax_amount_after_discount_amount` | Tax Amount After Discount Amount | Currency | lecture seule; devise de `parent_company.default_currency` |
| `project` | Project | Link → `Project` |  |
| `included_in_paid_amount` | Considered In Paid Amount | Boolean | défaut `non`; — If checked, the tax amount will be considered as already included in the Paid Amount in Payment Entry |
| `account_currency` | Account Currency | Link → `Currency` | lecture seule |
| `is_tax_withholding_account` | Is Tax Withholding Account | Boolean | lecture seule |
| `net_amount` | Net Amount | Currency | colonne de liste; lecture seule |
| `base_net_amount` | Net Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `set_by_item_tax_template` | Set by Item Tax Template | Boolean | lecture seule; masqué |
| `dont_recompute_tax` | Don't Recompute Tax | Boolean | lecture seule; masqué |

## Purchase Taxes and Charges Template

*Purchase Taxes and Charges Template* — `accounts/purchase_taxes_and_charges_template.yaml`

- **Titre** : `company`
- **Icône** : `badge-percent`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text | **requis** |
| `is_default` | Default | Boolean | colonne de liste; défaut `non` |
| `disabled` | Disabled | Boolean | colonne de liste; défaut `non` |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `taxes` | Purchase Taxes and Charges | Table → `Purchase Taxes and Charges` |  |
| `tax_category` | Tax Category | Link → `Tax Category` |  |

## Repost Accounting Ledger

*Repost Accounting Ledger* — `accounts/repost_accounting_ledger.yaml` · soumis

- **Numérotation** : série `RAL-{YYYY}-{#####}`
- **Titre** : `company`
- **Icône** : `list-restart`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | colonne de liste |
| `vouchers` | Vouchers | Table → `Repost Accounting Ledger Items` |  |
| `delete_cancelled_entries` | Delete Cancelled Ledger Entries | Boolean | défaut `non` |
| `error_log` | Error Log | Code | lecture seule |
| `status` | Status | Select — Queued · In Progress · Partially Reposted · Completed · Failed · Cancelled | colonne de liste; lecture seule |
| `scheduled_job` | Scheduled Job | Link → `RQ Job` | lecture seule; masqué |

## Repost Accounting Ledger Items

*Repost Accounting Ledger Items* — `accounts/repost_accounting_ledger_items.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `voucher_type` | Voucher Type | Text | **requis**; colonne de liste |
| `voucher_no` | Voucher No | DynamicLink → `voucher_type` | colonne de liste |
| `status` | Status | Select — Pending · Reposted · Skipped · Failed | colonne de liste; lecture seule; défaut `Pending` |
| `traceback` | Traceback | Code | lecture seule |

## Repost Allowed Types

*Repost Allowed Types* — `accounts/repost_allowed_types.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `document_type` | Doctype | Text | colonne de liste |

## Repost Payment Ledger

*Repost Payment Ledger* — `accounts/repost_payment_ledger.yaml` · soumis

- **Numérotation** : série `RPL-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `company`
- **Icône** : `list-restart`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `posting_date` | Posting Date | Date | **requis**; défaut `today` |
| `voucher_type` | Voucher Type | Text |  |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `repost_vouchers` | Selected Vouchers | Table → `Repost Payment Ledger Items` |  |
| `repost_status` | Repost Status | Select — Queued · Failed · Completed | lecture seule |
| `add_manually` | Add Manually | Boolean | défaut `non`; — Ignore Voucher Type filter and Select Vouchers Manually |
| `repost_error_log` | Repost Error Log | LongText |  |

## Repost Payment Ledger Items

*Repost Payment Ledger Items* — `accounts/repost_payment_ledger_items.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `voucher_type` | Voucher Type | Text |  |
| `voucher_no` | Voucher No | DynamicLink → `voucher_type` |  |

## Sales Invoice

*Sales Invoice* — `accounts/sales_invoice.yaml` · soumis

- **Numérotation** : série `SI-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `customer`
- **Icône** : `receipt-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — ACC-SINV-.YYYY.- · ACC-SINV-RET-.YYYY.- | **requis** |
| `customer` | Customer | Link → `Customer` | **requis** |
| `customer_name` | Customer Name | Text | lecture seule; recopié de `customer.customer_name` |
| `tax_id` | Tax Id | Text | lecture seule |
| `project` | Project | Link → `Project` |  |
| `is_pos` | Include Payment (POS) | Boolean | défaut `non` |
| `pos_profile` | POS Profile | Link → `POS Profile` | visible si `is_pos`; obligatoire si `is_pos` |
| `is_return` | Is Return (Credit Note) | Boolean | défaut `non` |
| `company` | Company | Link → `Company` | **requis** |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `posting_date` | Posting Date | Date | **requis**; colonne de liste; défaut `today` |
| `posting_time` | Posting Time | Time |  |
| `set_posting_time` | Edit Posting Date and Time | Boolean | défaut `non` |
| `due_date` | Payment Due Date | Date | colonne de liste |
| `return_against` | Return Against | Link → `Sales Invoice` | visible si `is_return`; obligatoire si `is_return` |
| `update_billed_amount_in_sales_order` | Update Billed Amount in Sales Order | Boolean | défaut `non` |
| `po_no` | Customer's Purchase Order | Text |  |
| `po_date` | Customer's Purchase Order Date | Date | visible si `po_no` |
| `customer_address` | Customer Address | Link → `Address` |  |
| `address_display` | Address | TextEditor | lecture seule |
| `contact_person` | Contact Person | Link → `Contact` |  |
| `contact_display` | Contact | LongText | lecture seule |
| `contact_mobile` | Mobile No | LongText | lecture seule; masqué |
| `contact_email` | Contact Email | Text | lecture seule; masqué |
| `territory` | Territory | Link → `Territory` |  |
| `shipping_address_name` | Shipping Address Name | Link → `Address` |  |
| `shipping_address` | Shipping Address | TextEditor | lecture seule |
| `shipping_contact_person` | Shipping Contact Person | Link → `Contact` |  |
| `shipping_contact_display` | Shipping Contact | LongText | lecture seule |
| `shipping_contact_mobile` | Shipping Contact Mobile No | LongText | lecture seule |
| `shipping_contact_email` | Shipping Contact Email | Text | lecture seule; masqué |
| `company_address` | Company Address Name | Link → `Address` |  |
| `company_address_display` | Company Address | TextEditor | lecture seule |
| `currency` | Currency | Link → `Currency` | **requis** |
| `conversion_rate` | Exchange Rate | Number | **requis**; — Rate at which Customer Currency is converted to customer's base currency |
| `selling_price_list` | Price List | Link → `Price List` | **requis** |
| `price_list_currency` | Price List Currency | Link → `Currency` | **requis**; lecture seule |
| `plc_conversion_rate` | Price List Exchange Rate | Number | **requis**; — Rate at which Price list currency is converted to customer's base currency |
| `ignore_pricing_rule` | Ignore Pricing Rule | Boolean | défaut `non` |
| `set_warehouse` | Source Warehouse | Link → `Warehouse` | visible si `update_stock` |
| `update_stock` | Update Stock | Boolean | défaut `non`; — If checked, updates inventory; stock and accounting entries are created together. Leave unchecked if a Deliver |
| `scan_barcode` | Scan Barcode | Text |  |
| `items` | Items | Table → `Sales Invoice Item` |  |
| `pricing_rules` | Pricing Rule Detail | Table → `Pricing Rule Detail` | lecture seule |
| `packed_items` | Packed Items | Table → `Packed Item` |  |
| `timesheets` | Time Sheets | Table → `Sales Invoice Timesheet` |  |
| `total_billing_amount` | Total Billing Amount | Currency | lecture seule; devise de `currency` |
| `total_qty` | Total Quantity | Decimal | lecture seule; calculé : `sum(items.qty)` |
| `base_total` | Total (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_net_total` | Net Total (Company Currency) | Currency | **requis**; lecture seule; devise de `company.default_currency` |
| `total` | Total | Currency | lecture seule; calculé : `sum(items.amount)`; devise de `currency` |
| `net_total` | Net Total | Currency | lecture seule; calculé : `sum(items.net_amount)`; devise de `currency` |
| `total_net_weight` | Total Net Weight | Number | lecture seule |
| `taxes_and_charges` | Sales Taxes and Charges Template | Link → `Sales Taxes and Charges Template` |  |
| `shipping_rule` | Shipping Rule | Link → `Shipping Rule` |  |
| `tax_category` | Tax Category | Link → `Tax Category` |  |
| `taxes` | Sales Taxes and Charges | Table → `Sales Taxes and Charges` |  |
| `other_charges_calculation` | Taxes and Charges Calculation | TextEditor | lecture seule |
| `base_total_taxes_and_charges` | Total Taxes and Charges (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `total_taxes_and_charges` | Total Taxes and Charges | Currency | lecture seule; devise de `currency` |
| `loyalty_points` | Loyalty Points | Int | visible si `redeem_loyalty_points` |
| `loyalty_amount` | Loyalty Amount | Currency | lecture seule; devise de `currency` |
| `redeem_loyalty_points` | Redeem Loyalty Points | Boolean | défaut `non` |
| `loyalty_program` | Loyalty Program | Link → `Loyalty Program` | visible si `redeem_loyalty_points` |
| `loyalty_redemption_account` | Redemption Account | Link → `Account` | visible si `redeem_loyalty_points` |
| `loyalty_redemption_cost_center` | Redemption Cost Center | Link → `Cost Center` | visible si `redeem_loyalty_points` |
| `apply_discount_on` | Apply Additional Discount On | Select — Grand Total · Net Total | défaut `Grand Total` |
| `base_discount_amount` | Additional Discount Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `additional_discount_percentage` | Additional Discount Percentage | Number |  |
| `discount_amount` | Additional Discount Amount | Currency | devise de `currency` |
| `base_grand_total` | Grand Total | Currency | **requis**; lecture seule; devise de `company.default_currency` |
| `base_rounding_adjustment` | Rounding Adjustment | Currency | lecture seule; devise de `company.default_currency` |
| `base_rounded_total` | Rounded Total | Currency | lecture seule; devise de `company.default_currency` |
| `base_in_words` | In Words | LongText | lecture seule; — In Words will be visible once you save the Sales Invoice. |
| `grand_total` | Grand Total | Currency | colonne de liste; lecture seule; calculé : `total + total_taxes_and_charges`; devise de `currency` |
| `rounding_adjustment` | Rounding Adjustment | Currency | lecture seule; devise de `currency` |
| `rounded_total` | Rounded Total | Currency | lecture seule; devise de `currency` |
| `in_words` | In Words | LongText | lecture seule |
| `total_advance` | Total Advance | Currency | lecture seule; devise de `currency` |
| `outstanding_amount` | Outstanding Amount | Currency | lecture seule; calculé : `grand_total - total_advance - paid_amount - write_off_amount`; devise de `party_account_currency` |
| `allocate_advances_automatically` | Allocate Advances Automatically (FIFO) | Boolean | défaut `non` |
| `advances` | Advances | Table → `Sales Invoice Advance` |  |
| `payment_terms_template` | Payment Terms Template | Link → `Payment Terms Template` |  |
| `payment_schedule` | Payment Schedule | Table → `Payment Schedule` |  |
| `cash_bank_account` | Cash/Bank Account | Link → `Account` | masqué; visible si `is_pos` |
| `payments` | Sales Invoice Payment | Table → `Sales Invoice Payment` |  |
| `base_paid_amount` | Paid Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `paid_amount` | Paid Amount | Currency | lecture seule; devise de `currency` |
| `base_change_amount` | Base Change Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `change_amount` | Change Amount | Currency | devise de `currency` |
| `account_for_change_amount` | Account for Change Amount | Link → `Account` | visible si `is_pos` |
| `write_off_amount` | Write Off Amount | Currency | devise de `currency` |
| `base_write_off_amount` | Write Off Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `write_off_outstanding_amount_automatically` | Write Off Outstanding Amount | Boolean | défaut `non` |
| `write_off_account` | Write Off Account | Link → `Account` |  |
| `write_off_cost_center` | Write Off Cost Center | Link → `Cost Center` |  |
| `tc_name` | Terms | Link → `Terms and Conditions` |  |
| `terms` | Terms and Conditions Details | TextEditor |  |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `group_same_items` | Group same items | Boolean | défaut `non` |
| `language` | Print Language | Link → `Language` | lecture seule |
| `select_print_heading` | Print Heading | Link → `Print Heading` |  |
| `inter_company_invoice_reference` | Inter Company Invoice Reference | Link → `Purchase Invoice` | lecture seule; visible si `is_internal_customer` |
| `customer_group` | Customer Group | Link → `Customer Group` | masqué |
| `is_discounted` | Is Discounted | Boolean | lecture seule |
| `status` | Status | Select — Draft · Return · Credit Note Issued · Submitted · Paid · Partly Paid · Unpaid · Unpaid and Discounted · Partly Paid and Discounted · Overdue and Discounted · Overdue · Cancelled · Internal Transfer | colonne de liste; lecture seule; défaut `Draft` |
| `debit_to` | Debit To | Link → `Account` | **requis** |
| `party_account_currency` | Party Account Currency | Link → `Currency` | lecture seule; masqué |
| `is_opening` | Is Opening Entry | Select — No · Yes | masqué; défaut `No` |
| `remarks` | Remarks | LongText |  |
| `sales_partner` | Sales Partner | Link → `Sales Partner` |  |
| `commission_rate` | Commission Rate (%) | Number |  |
| `total_commission` | Total Commission | Currency | devise de `currency` |
| `sales_team` | Sales Contributions and Incentives | Table → `Sales Team` |  |
| `from_date` | From Date | Date |  |
| `to_date` | To Date | Date |  |
| `auto_repeat` | Auto Repeat | Link → `Auto Repeat` | lecture seule |
| `against_income_account` | Against Income Account | LongText | masqué |
| `is_consolidated` | Is Consolidated | Boolean | lecture seule |
| `is_internal_customer` | Is Internal Customer | Boolean | lecture seule |
| `company_tax_id` | Company Tax ID | Text | lecture seule |
| `unrealized_profit_loss_account` | Unrealized Profit / Loss Account | Link → `Account` | visible si `is_internal_customer`; — Unrealized Profit / Loss account for intra-company transfers |
| `represents_company` | Represents Company | Link → `Company` | lecture seule; visible si `is_internal_customer`; obligatoire si `is_internal_customer`; — Company which internal customer represents |
| `set_target_warehouse` | Set Target Warehouse | Link → `Warehouse` | visible si `is_internal_customer` |
| `is_debit_note` | Is Rate Adjustment Entry (Debit Note) | Boolean | défaut `non`; — Issue a debit note against an existing Sales Invoice to adjust the rate. The quantity will be retained from th |
| `disable_rounded_total` | Disable Rounded Total | Boolean | défaut `non` |
| `additional_discount_account` | Discount Account | Link → `Account` | masqué |
| `dispatch_address_name` | Dispatch Address Name | Link → `Address` |  |
| `dispatch_address` | Dispatch Address | TextEditor | lecture seule |
| `ignore_default_payment_terms_template` | Ignore Default Payment Terms Template | Boolean | lecture seule; masqué |
| `total_billing_hours` | Total Billing Hours | Number | lecture seule |
| `amount_eligible_for_commission` | Amount Eligible for Commission | Currency | lecture seule; devise de `currency` |
| `subscription` | Subscription | Link → `Subscription` |  |
| `is_cash_or_non_trade_discount` | Is Cash or Non Trade Discount | Boolean | défaut `non` |
| `incoterm` | Incoterm | Link → `Incoterm` |  |
| `named_place` | Named Place | Text |  |
| `only_include_allocated_payments` | Only Include Allocated Payments | Boolean | défaut `non`; — Advance payments allocated against orders will only be fetched |
| `use_company_roundoff_cost_center` | Use Company default Cost Center for Round off | Boolean | défaut `non` |
| `update_billed_amount_in_delivery_note` | Update Billed Amount in Delivery Note | Boolean | défaut `oui` |
| `dont_create_loyalty_points` | Don't Create Loyalty Points | Boolean | défaut `non` |
| `coupon_code` | Coupon Code | Link → `Coupon Code` |  |
| `update_outstanding_for_self` | Update Outstanding for Self | Boolean | défaut `oui`; — Credit Note will update it's own outstanding amount, even if 'Return Against' is specified. |
| `utm_medium` | Medium | Link → `UTM Medium` |  |
| `utm_content` | Content | Text |  |
| `utm_campaign` | Campaign | Link → `UTM Campaign` |  |
| `utm_source` | Source | Link → `UTM Source` |  |
| `company_contact_person` | Company Contact Person | Link → `Contact` |  |
| `is_created_using_pos` | Is created using POS | Boolean | masqué; défaut `non` |
| `pos_closing_entry` | POS Closing Entry | Link → `POS Closing Entry` | masqué |
| `last_scanned_warehouse` | Last Scanned Warehouse | Text |  |
| `has_subcontracted` | Has Subcontracted | Boolean | lecture seule; masqué |
| `item_wise_tax_details` | Item Wise Tax Details | Table → `Item Wise Tax Detail` | masqué |
| `apply_tds` | Consider for Tax Withholding | Boolean | défaut `non` |
| `tax_withholding_group` | Tax Withholding Group | Link → `Tax Withholding Group` |  |
| `tax_withholding_entries` | Tax Withholding Entries | Table → `Tax Withholding Entry` |  |
| `ignore_tax_withholding_threshold` | Ignore Tax Withholding Threshold | Boolean | défaut `non` |
| `override_tax_withholding_entries` | Edit Tax Withholding Entries | Boolean | défaut `non` |
| `title` | Title | Text |  |

## Sales Invoice Advance

*Sales Invoice Advance* — `accounts/sales_invoice_advance.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `reference_type` | Reference Type | Text | lecture seule |
| `reference_name` | Reference Name | DynamicLink → `reference_type` | colonne de liste; lecture seule |
| `remarks` | Remarks | LongText | colonne de liste; lecture seule |
| `reference_row` | Reference Row | Text | lecture seule; masqué |
| `advance_amount` | Advance amount | Currency | colonne de liste; lecture seule; devise de `parent_currency` |
| `allocated_amount` | Allocated amount | Currency | colonne de liste; devise de `parent_currency` |
| `exchange_gain_loss` | Exchange Gain/Loss | Currency | lecture seule; devise de `parent_currency` |
| `ref_exchange_rate` | Reference Exchange Rate | Number | lecture seule |
| `difference_posting_date` | Difference Posting Date | Date | colonne de liste |

## Sales Invoice Item

*Sales Invoice Item* — `accounts/sales_invoice_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `barcode` | Barcode | Text |  |
| `item_code` | Item | Link → `Item` | colonne de liste |
| `is_product_bundle` | Is Product Bundle | Boolean | lecture seule; masqué |
| `product_bundle` | Product Bundle | Link → `Product Bundle` |  |
| `item_name` | Item Name | Text | **requis** |
| `customer_item_code` | Customer's Item Code | Text | lecture seule; masqué |
| `description` | Description | TextEditor |  |
| `qty` | Quantity | Decimal | colonne de liste |
| `stock_uom` | Stock UOM | Link → `UOM` | lecture seule |
| `uom` | UOM | Link → `UOM` | **requis** |
| `conversion_factor` | UOM Conversion Factor | Number | **requis** |
| `stock_qty` | Qty as per Stock UOM | Decimal | lecture seule |
| `price_list_rate` | Price List Rate | Currency | lecture seule; devise de `parent_currency` |
| `base_price_list_rate` | Price List Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `margin_type` | Margin Type | Select — Percentage · Amount |  |
| `margin_rate_or_amount` | Margin Rate or Amount | Number |  |
| `rate_with_margin` | Rate With Margin | Currency | lecture seule; devise de `parent_currency` |
| `discount_percentage` | Discount (%) on Price List Rate with Margin | Percent |  |
| `discount_amount` | Discount Amount | Currency | devise de `parent_currency` |
| `base_rate_with_margin` | Rate With Margin (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `rate` | Rate | Currency | **requis**; colonne de liste; devise de `parent_currency` |
| `amount` | Amount | Currency | colonne de liste; lecture seule; calculé : `qty * rate`; devise de `parent_currency` |
| `base_rate` | Rate (Company Currency) | Currency | **requis**; lecture seule; devise de `parent_company.default_currency` |
| `base_amount` | Amount (Company Currency) | Currency | **requis**; lecture seule; devise de `parent_company.default_currency` |
| `pricing_rules` | Pricing Rules | LongText | lecture seule; masqué |
| `is_free_item` | Is Free Item | Boolean | lecture seule |
| `net_rate` | Net Rate | Currency | lecture seule; devise de `parent_currency` |
| `net_amount` | Net Amount | Currency | lecture seule; calculé : `amount - discount_amount`; devise de `parent_currency` |
| `base_net_rate` | Net Rate (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_net_amount` | Net Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `delivered_by_supplier` | Delivered By Supplier | Boolean | lecture seule |
| `income_account` | Income Account | Link → `Account` | **requis** |
| `expense_account` | Expense Account | Link → `Account` |  |
| `item_tax_template` | Item Tax Template | Link → `Item Tax Template` |  |
| `cost_center` | Cost Center | Link → `Cost Center` | **requis** |
| `deferred_revenue_account` | Deferred Revenue Account | Link → `Account` | visible si `enable_deferred_revenue`; obligatoire si `enable_deferred_revenue` |
| `service_stop_date` | Service Stop Date | Date | visible si `enable_deferred_revenue` |
| `enable_deferred_revenue` | Enable Deferred Revenue | Boolean | défaut `non` |
| `service_start_date` | Service Start Date | Date | visible si `enable_deferred_revenue`; obligatoire si `enable_deferred_revenue` |
| `service_end_date` | Service End Date | Date | visible si `enable_deferred_revenue`; obligatoire si `enable_deferred_revenue` |
| `weight_per_unit` | Weight Per Unit | Number | lecture seule |
| `total_weight` | Total Weight | Number | lecture seule |
| `weight_uom` | Weight UOM | Link → `UOM` | lecture seule |
| `warehouse` | Warehouse | Link → `Warehouse` | colonne de liste |
| `target_warehouse` | Target Warehouse | Link → `Warehouse` | masqué |
| `quality_inspection` | Quality Inspection | Link → `Quality Inspection` |  |
| `batch_no` | Batch No | Link → `Batch` |  |
| `allow_zero_valuation_rate` | Allow Zero Valuation Rate | Boolean | défaut `non` |
| `serial_no` | Serial No | LongText |  |
| `item_group` | Item Group | Link → `Item Group` | lecture seule; masqué |
| `brand` | Brand Name | Text | masqué |
| `item_tax_rate` | Item Tax Rate | LongText | lecture seule; masqué |
| `actual_batch_qty` | Available Batch Qty at Warehouse | Decimal | lecture seule |
| `actual_qty` | Qty (Warehouse) | Decimal | lecture seule |
| `sales_order` | Sales Order | Link → `Sales Order` | lecture seule; cible submitted |
| `so_detail` | Sales Order Item | Text | lecture seule; masqué |
| `delivery_note` | Delivery Note | Link → `Delivery Note` | lecture seule; cible submitted |
| `dn_detail` | Delivery Note Item | Text | lecture seule; masqué |
| `delivered_qty` | Delivered Qty | Decimal | lecture seule |
| `is_fixed_asset` | Is Fixed Asset | Boolean | lecture seule; masqué |
| `asset` | Asset | Link → `Asset` | visible si `is_fixed_asset` |
| `page_break` | Page Break | Boolean | défaut `non` |
| `finance_book` | Finance Book | Link → `Finance Book` |  |
| `asset_gross_value` | Asset Gross Value | Currency | lecture seule; masqué; devise de `parent_currency` |
| `asset_value_after_depreciation` | Asset Value After Depreciation | Currency | lecture seule; masqué; devise de `parent_currency` |
| `project` | Project | Link → `Project` |  |
| `sales_invoice_item` | Sales Invoice Item | Text | lecture seule |
| `incoming_rate` | Incoming Rate (Costing) | Currency | devise de `parent_currency` |
| `stock_uom_rate` | Rate of Stock UOM | Currency | lecture seule; devise de `parent_currency` |
| `discount_account` | Discount Account | Link → `Account` | masqué |
| `grant_commission` | Grant Commission | Boolean | lecture seule |
| `purchase_order` | Purchase Order | Link → `Purchase Order` | lecture seule |
| `purchase_order_item` | Purchase Order Item | Text | lecture seule |
| `has_item_scanned` | Has Item Scanned | Boolean | lecture seule |
| `serial_and_batch_bundle` | Serial and Batch Bundle | Link → `Serial and Batch Bundle` |  |
| `use_serial_batch_fields` | Use Serial No / Batch Fields | Boolean | défaut `non` |
| `distributed_discount_amount` | Distributed Discount Amount | Currency | lecture seule; devise de `parent_currency` |
| `mapped_additional_discount_amount` | Additional Discount per Stock Unit | Currency | lecture seule; devise de `parent_currency`; — Tax-exclusive additional discount carried from a source document, per stock unit. |
| `company_total_stock` | Qty (Company) | Number | lecture seule |
| `pos_invoice_item` | POS Invoice Item | Text | lecture seule |
| `pos_invoice` | POS Invoice | Link → `POS Invoice` |  |
| `scio_detail` | SCIO Detail | Text | lecture seule; masqué |
| `tax_withholding_category` | Tax Withholding Category | Link → `Tax Withholding Category` |  |
| `apply_tds` | Consider for Tax Withholding | Boolean | lecture seule |
| `against_pick_list` | Against Pick List | Link → `Pick List` | lecture seule; masqué |
| `pick_list_item` | Pick List Item | Text | lecture seule; masqué |

## Sales Invoice Payment

*Sales Invoice Payment* — `accounts/sales_invoice_payment.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` | **requis**; colonne de liste |
| `amount` | Amount | Currency | **requis**; colonne de liste; devise de `parent_currency` |
| `account` | Account | Link → `Account` | lecture seule |
| `type` | Type | Text | lecture seule |
| `base_amount` | Base Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `clearance_date` | Clearance Date | Date | lecture seule |
| `default` | Default | Boolean | lecture seule; masqué |
| `reference_no` | Reference No | Text |  |

## Sales Invoice Reference

*Sales Invoice Reference* — `accounts/sales_invoice_reference.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `sales_invoice` | Sales Invoice | Link → `Sales Invoice` | **requis**; colonne de liste |
| `posting_date` | Date | Date | **requis**; colonne de liste |
| `customer` | Customer | Link → `Customer` | **requis**; lecture seule |
| `is_return` | Is Return | Boolean | lecture seule |
| `return_against` | Return Against | Link → `Sales Invoice` | lecture seule |
| `grand_total` | Amount | Currency | **requis**; colonne de liste; devise de `parent_company.default_currency` |

## Sales Invoice Timesheet

*Sales Invoice Timesheet* — `accounts/sales_invoice_timesheet.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `time_sheet` | Time Sheet | Link → `Timesheet` | colonne de liste; lecture seule |
| `billing_hours` | Billing Hours | Number | colonne de liste; lecture seule |
| `billing_amount` | Billing Amount | Currency | colonne de liste; lecture seule; devise de `parent_currency` |
| `timesheet_detail` | Timesheet Detail | Text | lecture seule; masqué |
| `activity_type` | Activity Type | Link → `Activity Type` | colonne de liste; lecture seule |
| `description` | Description | LongText | colonne de liste; lecture seule |
| `from_time` | From Time | Datetime |  |
| `to_time` | To Time | Datetime |  |
| `project_name` | Project Name | Text | lecture seule |

## Sales Partner Item

*Sales Partner Item* — `accounts/sales_partner_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `sales_partner` | Sales Partner  | Link → `Sales Partner` | colonne de liste |

## Sales Taxes and Charges

*Sales Taxes and Charges* — `accounts/sales_taxes_and_charges.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `charge_type` | Type | Select — Actual · On Net Total · On Previous Row Amount · On Previous Row Total · On Item Quantity | **requis**; colonne de liste |
| `row_id` | Reference Row # | Text |  |
| `account_head` | Account Head | Link → `Account` | **requis**; colonne de liste |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `description` | Description | LongText | **requis** |
| `included_in_print_rate` | Is this Tax included in Basic Rate? | Boolean | défaut `non`; — If checked, the tax amount will be considered as already included in the Print Rate / Print Amount |
| `rate` | Tax Rate | Number | colonne de liste |
| `tax_amount` | Amount | Currency | colonne de liste |
| `total` | Total | Currency | colonne de liste; lecture seule |
| `tax_amount_after_discount_amount` | Tax Amount After Discount Amount | Currency | lecture seule |
| `base_tax_amount` | Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_total` | Total (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_tax_amount_after_discount_amount` | Tax Amount After Discount Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `project` | Project | Link → `Project` |  |
| `included_in_paid_amount` | Considered In Paid Amount | Boolean | défaut `non`; — If checked, the tax amount will be considered as already included in the Paid Amount in Payment Entry |
| `dont_recompute_tax` | Don't Recompute Tax | Boolean | lecture seule; masqué |
| `account_currency` | Account Currency | Link → `Currency` | lecture seule |
| `net_amount` | Net Amount | Currency | colonne de liste; lecture seule |
| `base_net_amount` | Net Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `set_by_item_tax_template` | Set by Item Tax Template | Boolean | lecture seule; masqué |
| `is_tax_withholding_account` | Is Tax Withholding Account | Boolean | lecture seule |

## Sales Taxes and Charges Template

*Sales Taxes and Charges Template* — `accounts/sales_taxes_and_charges_template.yaml`

- **Titre** : `company`
- **Icône** : `badge-percent`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text | **requis** |
| `is_default` | Default | Boolean | colonne de liste; défaut `non` |
| `disabled` | Disabled | Boolean | défaut `non` |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `taxes` | Sales Taxes and Charges | Table → `Sales Taxes and Charges` | — * Will be calculated in the transaction. |
| `tax_category` | Tax Category | Link → `Tax Category` |  |

## Share Balance

*Share Balance* — `accounts/share_balance.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `share_type` | Share Type | Link → `Share Type` | **requis**; colonne de liste; lecture seule |
| `from_no` | From No | Int | **requis**; lecture seule |
| `rate` | Rate | Currency | **requis**; colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `no_of_shares` | No of Shares | Int | **requis**; colonne de liste; lecture seule |
| `to_no` | To No | Int | **requis**; lecture seule |
| `amount` | Amount | Currency | **requis**; colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `is_company` | Is Company | Boolean | lecture seule; masqué |
| `current_state` | Current State | Select — Issued · Purchased | lecture seule; masqué |

## Share Transfer

*Share Transfer* — `accounts/share_transfer.yaml` · soumis

- **Numérotation** : série `ST-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `company`
- **Icône** : `arrow-right-left`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `transfer_type` | Transfer Type | Select — Issue · Purchase · Transfer | **requis**; colonne de liste |
| `date` | Date | Date | **requis** |
| `from_shareholder` | From Shareholder | Link → `Shareholder` |  |
| `from_folio_no` | From Folio No | Text |  |
| `equity_or_liability_account` | Equity/Liability Account | Link → `Account` | **requis** |
| `asset_account` | Asset Account | Link → `Account` |  |
| `to_shareholder` | To Shareholder | Link → `Shareholder` |  |
| `to_folio_no` | To Folio No | Text |  |
| `share_type` | Share Type | Link → `Share Type` | **requis** |
| `from_no` | From No | Int | **requis**; — (including) |
| `rate` | Rate | Currency | **requis**; devise de `company.default_currency` |
| `no_of_shares` | No of Shares | Int | **requis** |
| `to_no` | To No | Int | **requis**; — (including) |
| `amount` | Amount | Currency | lecture seule; devise de `company.default_currency` |
| `company` | Company | Link → `Company` | **requis** |
| `remarks` | Remarks | LongText |  |

## Share Type

*Share Type* — `accounts/share_type.yaml`

- **Titre** : `title`
- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text | **requis**; colonne de liste |
| `description` | Description | LongText |  |

## Shareholder

*Shareholder* — `accounts/shareholder.yaml`

- **Titre** : `company`
- **Icône** : `user-star`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text | **requis** |
| `naming_series` | Naming Series | Select — ACC-SH-.YYYY.- |  |
| `folio_no` | Folio no. | Text | lecture seule |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `is_company` | Is Company | Boolean | lecture seule; masqué |
| `share_balance` | Share Balance | Table → `Share Balance` | lecture seule |
| `contact_list` | Contact List | Code | lecture seule; masqué; — Hidden list maintaining the list of contacts linked to Shareholder |

## Shipping Rule

*Shipping Rule* — `accounts/shipping_rule.yaml`

- **Titre** : `company`
- **Icône** : `truck`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `label` | Shipping Rule Label | Text | **requis**; — example: Next Day Shipping |
| `disabled` | Disabled | Boolean | défaut `non` |
| `shipping_rule_type` | Shipping Rule Type | Select — Selling · Buying |  |
| `company` | Company | Link → `Company` | **requis** |
| `account` | Shipping Account | Link → `Account` | **requis** |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `calculate_based_on` | Calculate Based On | Select — Fixed · Net Total · Net Weight | colonne de liste; défaut `Fixed` |
| `shipping_amount` | Shipping Amount | Currency | devise de `company.default_currency` |
| `conditions` | Shipping Rule Conditions | Table → `Shipping Rule Condition` |  |
| `countries` | Valid for Countries | Table → `Shipping Rule Country` |  |
| `project` | Project | Link → `Project` |  |

## Shipping Rule Condition

*Shipping Rule Condition* — `accounts/shipping_rule_condition.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `from_value` | From Value | Number | **requis**; colonne de liste |
| `to_value` | To Value | Number | colonne de liste |
| `shipping_amount` | Shipping Amount | Currency | **requis**; colonne de liste; devise de `parent_company.default_currency` |

## Shipping Rule Country

*Shipping Rule Country* — `accounts/shipping_rule_country.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `country` | Country | Link → `Country` | **requis**; colonne de liste |

## South Africa VAT Account

*South Africa VAT Account* — `accounts/south_africa_vat_account.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `account` | Account | Link → `Account` | colonne de liste |

## Subscription

*Subscription* — `accounts/subscription.yaml`

- **Vues** : calendar, gantt
- **Titre** : `company`
- **Icône** : `calendar-sync`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `status` | Status | Select — Trialing · Active · Grace Period · Cancelled · Unpaid · Completed · Refunded | lecture seule |
| `cancelation_date` | Cancelation Date | Date | lecture seule |
| `trial_period_start` | Trial Period Start Date | Date |  |
| `trial_period_end` | Trial Period End Date | Date |  |
| `current_invoice_start` | Current Invoice Start | Date | lecture seule |
| `current_invoice_end` | Current Invoice End | Date | lecture seule |
| `next_billing_period_start` | Next Billing Period Start | Date | lecture seule |
| `next_billing_period_end` | Next Billing Period End | Date | lecture seule |
| `days_until_due` | Days Until Due | Int | défaut `0`; — Number of days that the subscriber has to pay invoices generated by this subscription |
| `cancel_at_period_end` | Cancel When Period Ends | Boolean | défaut `non` |
| `plans` | Plans | Table → `Subscription Plan Detail` |  |
| `apply_additional_discount` | Apply Additional Discount On | Select — Grand Total · Net Total |  |
| `additional_discount_percentage` | Additional Discount Percentage | Percent |  |
| `additional_discount_amount` | Additional Discount Amount | Currency | devise de `company.default_currency` |
| `party_type` | Party Type | Text | **requis** |
| `party` | Party | DynamicLink → `party_type` | colonne de liste |
| `sales_tax_template` | Sales Taxes and Charges Template | Link → `Sales Taxes and Charges Template` |  |
| `purchase_tax_template` | Purchase Taxes and Charges Template | Link → `Purchase Taxes and Charges Template` |  |
| `follow_calendar_months` | Follow Calendar Months | Boolean | défaut `non`; — If this is checked subsequent new invoices will be created on calendar  month and quarter start dates irrespec |
| `generate_new_invoices_past_due_date` | Bill Even If Previous Invoice Unpaid | Boolean | défaut `non`; — New invoices will be generated as per schedule even if current invoices are unpaid or past due date |
| `end_date` | Subscription End Date | Date |  |
| `start_date` | Subscription Start Date | Date |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `company` | Company | Link → `Company` |  |
| `submit_invoice` | Submit Generated Invoices | Boolean | défaut `oui` |
| `generate_invoice_at` | Generate Invoice At | Select — Postpaid (bill at period end) · Prepaid (bill at period start) · Bill N days before period start | **requis**; défaut `Postpaid (bill at period end)` |
| `number_of_days` | Number of Days | Int |  |

## Subscription Plan

*Subscription Plan* — `accounts/subscription_plan.yaml`

- **Titre** : `plan_name`
- **Icône** : `calendar-sync`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `plan_name` | Plan Name | Text | **requis**; colonne de liste |
| `currency` | Currency | Link → `Currency` | **requis** |
| `item` | Item | Link → `Item` | **requis**; colonne de liste |
| `price_determination` | Subscription Price Based On | Select — Fixed Rate · Based On Price List · Monthly Rate | **requis** |
| `cost` | Cost | Currency | colonne de liste; devise de `currency` |
| `price_list` | Price List | Link → `Price List` |  |
| `billing_interval` | Billing Interval | Select — Day · Week · Month · Year | **requis**; colonne de liste; défaut `Day` |
| `billing_interval_count` | Billing Interval Count | Int | **requis**; défaut `1`; — Number of intervals for the interval field e.g if Interval is 'Days' and Billing Interval Count is 3, invoices |
| `payment_gateway` | Payment Gateway | Link → `Payment Gateway Account` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `product_price_id` | Product Price ID | Text |  |

## Subscription Plan Detail

*Subscription Plan Detail* — `accounts/subscription_plan_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `qty` | Quantity | Int | **requis**; colonne de liste |
| `plan` | Plan | Link → `Subscription Plan` | **requis**; colonne de liste |

## Subscription Settings

*Subscription Settings* — `accounts/subscription_settings.yaml` · document unique

- **Icône** : `settings`
- **Permissions explicites** — `create` : 0, `delete` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `grace_period` | Grace Period | Int | défaut `1`; — Number of days after the invoice due date before canceling the subscription or marking it as unpaid |
| `cancel_after_grace` | Cancel Subscription After Grace Period | Boolean | défaut `non` |
| `prorate` | Prorate | Boolean | défaut `oui` |

## Supplier Group Item

*Supplier Group Item* — `accounts/supplier_group_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `supplier_group` | Supplier Group | Link → `Supplier Group` | colonne de liste |

## Supplier Item

*Supplier Item* — `accounts/supplier_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `supplier` | Supplier | Link → `Supplier` | colonne de liste |

## Tax Category

*Tax Category* — `accounts/tax_category.yaml`

- **Titre** : `title`
- **Icône** : `badge-percent`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text | **requis**; colonne de liste |
| `disabled` | Disabled | Boolean | défaut `non` |

## Tax Rule

*Tax Rule* — `accounts/tax_rule.yaml`

- **Vues** : calendar, gantt
- **Titre** : `customer`
- **Icône** : `badge-percent`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `tax_type` | Tax Type | Select — Sales · Purchase | colonne de liste; défaut `Sales` |
| `use_for_shopping_cart` | Use for Shopping Cart | Boolean | défaut `oui` |
| `sales_tax_template` | Sales Tax Template | Link → `Sales Taxes and Charges Template` |  |
| `purchase_tax_template` | Purchase Tax Template | Link → `Purchase Taxes and Charges Template` |  |
| `customer` | Customer | Link → `Customer` |  |
| `supplier` | Supplier | Link → `Supplier` |  |
| `item` | Item | Link → `Item` |  |
| `billing_city` | Billing City | Text |  |
| `billing_county` | Billing County | Text |  |
| `billing_state` | Billing State | Text |  |
| `billing_zipcode` | Billing Zipcode | Text |  |
| `billing_country` | Billing Country | Link → `Country` |  |
| `tax_category` | Tax Category | Link → `Tax Category` |  |
| `customer_group` | Customer Group | Link → `Customer Group` |  |
| `supplier_group` | Supplier Group | Link → `Supplier Group` |  |
| `item_group` | Item Group | Link → `Item Group` |  |
| `shipping_city` | Shipping City | Text |  |
| `shipping_county` | Shipping County | Text |  |
| `shipping_state` | Shipping State | Text |  |
| `shipping_zipcode` | Shipping Zipcode | Text |  |
| `shipping_country` | Shipping Country | Link → `Country` |  |
| `from_date` | From Date | Date |  |
| `to_date` | To Date | Date |  |
| `priority` | Priority | Int | défaut `1` |
| `company` | Company | Link → `Company` |  |

## Tax Withholding Account

*Tax Withholding Account* — `accounts/tax_withholding_account.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `account` | Account | Link → `Account` | **requis**; colonne de liste |

## Tax Withholding Category

*Tax Withholding Category* — `accounts/tax_withholding_category.yaml`

- **Titre** : `category_name`
- **Icône** : `badge-percent`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `category_name` | Category Name | Text | colonne de liste |
| `rates` | Rates | Table → `Tax Withholding Rate` |  |
| `accounts` | Accounts | Table → `Tax Withholding Account` |  |
| `tax_on_excess_amount` | Only Deduct Tax On Excess Amount  | Boolean | défaut `non`; — Tax withheld only for amount exceeding cumulative threshold |
| `round_off_tax_amount` | Round Off Tax Amount | Boolean | défaut `non`; — Checking this will round off the tax amount to the nearest integer |
| `tax_deduction_basis` | Deduct Tax On Basis | Select — Gross Total · Net Total | **requis**; défaut `Net Total` |
| `disable_cumulative_threshold` | Disable Cumulative Threshold | Boolean | défaut `non`; — When checked, only transaction threshold will be applied for transaction individually |
| `disable_transaction_threshold` | Disable Transaction Threshold | Boolean | défaut `non`; — When checked, only cumulative threshold will be applied |

## Tax Withholding Entry

*Tax Withholding Entry* — `accounts/tax_withholding_entry.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `party_type` | Party Type | Text | lecture seule |
| `party` | Party | DynamicLink → `party_type` | lecture seule |
| `tax_id` | Tax ID | Text | lecture seule |
| `tax_withholding_category` | Tax Withholding Category | Link → `Tax Withholding Category` | colonne de liste; lecture seule |
| `tax_rate` | Tax Rate | Percent | colonne de liste |
| `taxable_amount` | Base Taxable Amount | Currency | colonne de liste; devise de `currency` |
| `lower_deduction_certificate` | Lower Deduction Certificate | Link → `Lower Deduction Certificate` | lecture seule |
| `status` | Status | Select — Settled · Under Withheld · Over Withheld · Duplicate · Cancelled | lecture seule |
| `currency` | Currency | Link → `Currency` | lecture seule |
| `conversion_rate` | Exchange Rate | Number | lecture seule |
| `withholding_doctype` | Withholding Document Type | Text |  |
| `withholding_name` | Withholding Document Name | DynamicLink → `withholding_doctype` |  |
| `taxable_doctype` | Taxable Document Type | Text |  |
| `taxable_name` | Taxable Document Name | DynamicLink → `taxable_doctype` | colonne de liste |
| `taxable_date` | Taxable Date | Date | lecture seule |
| `withholding_date` | Withholding Date | Date | lecture seule |
| `under_withheld_reason` | Under Withheld Reason | Select — Threshold Exemption · Lower Deduction Certificate | lecture seule |
| `withholding_amount` | Base Tax Withheld | Currency | colonne de liste; lecture seule; devise de `currency` |
| `tax_withholding_group` | Tax Withholding Group | Link → `Tax Withholding Group` | colonne de liste; lecture seule |
| `company` | Company | Link → `Company` |  |
| `created_by_migration` | Created By Migration | Boolean | lecture seule; masqué |

## Tax Withholding Group

*Tax Withholding Group* — `accounts/tax_withholding_group.yaml`

- **Titre** : `group_name`
- **Icône** : `badge-percent`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `group_name` | Group Name | Text | **requis**; colonne de liste |

## Tax Withholding Rate

*Tax Withholding Rate* — `accounts/tax_withholding_rate.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `tax_withholding_rate` | Tax Withholding Rate | Number | **requis**; colonne de liste |
| `single_threshold` | Transaction Threshold | Number | colonne de liste |
| `cumulative_threshold` | Cumulative Threshold | Number | colonne de liste |
| `from_date` | From Date | Date | **requis**; colonne de liste |
| `to_date` | To Date | Date | **requis**; colonne de liste |
| `tax_withholding_group` | Tax Withholding Group | Link → `Tax Withholding Group` | colonne de liste |

## Territory Item

*Territory Item* — `accounts/territory_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `territory` | Territory | Link → `Territory` | colonne de liste |

## Transaction Deletion Record Details

*Transaction Deletion Record Details* — `accounts/transaction_deletion_record_details.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `doctype_name` | DocType | Text | **requis**; colonne de liste; lecture seule |
| `docfield_name` | DocField | Text | lecture seule |
| `no_of_docs` | No of Docs | Int | colonne de liste; lecture seule |
| `done` | Done | Boolean | colonne de liste; lecture seule |

## Unreconcile Payment

*Unreconcile Payment* — `accounts/unreconcile_payment.yaml` · soumis

- **Numérotation** : série `UP-{YYYY}-{#####}`
- **Titre** : `company`
- **Icône** : `unlink`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` |  |
| `voucher_type` | Voucher Type | Text |  |
| `voucher_no` | Voucher No | DynamicLink → `voucher_type` |  |
| `allocations` | Allocations | Table → `Unreconcile Payment Entries` |  |

## Unreconcile Payment Entries

*Unreconcile Payment Entries* — `accounts/unreconcile_payment_entries.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `reference_name` | Reference Name | DynamicLink → `reference_doctype` | colonne de liste |
| `allocated_amount` | Allocated Amount | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `unlinked` | Unlinked | Boolean | colonne de liste; lecture seule |
| `reference_doctype` | Reference Type | Text | colonne de liste |
| `account` | Account | Text |  |
| `party_type` | Party Type | Text |  |
| `party` | Party | Text |  |
| `account_currency` | Account Currency | Link → `Currency` | lecture seule |
