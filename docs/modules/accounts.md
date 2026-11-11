# Comptabilité (`accounts`)

Le cœur financier de l'ERP : pièces comptables (factures d'achat et de vente, écritures de journal, paiements), plan comptable SYSCOHADA, journaux immuables (`GL Entry`, `Payment Ledger Entry`) et référentiels fiscaux. Avec 192 DocTypes, c'est le plus grand module du jeu et le premier à implémenter (P1 de `process/plan-erp.md`).

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 192 | 31 | 96 | 4 | 0 | 31 | 2 438 |

## Espace de travail

**Espace « Comptabilité »** (icône `calculator`, position 40) — Comptes, écritures, factures et paiements.

- **Opérations** : [`Journal Entry`](../reference/accounts.md#journal-entry) — création, [`Sales Invoice`](../reference/accounts.md#sales-invoice) — création, [`Purchase Invoice`](../reference/accounts.md#purchase-invoice) — création, [`Payment Entry`](../reference/accounts.md#payment-entry) — création
- **Référentiel et banque** : [`Account`](../reference/accounts.md#account) — création, [`Cost Center`](../reference/accounts.md#cost-center) — création, [`Bank Transaction`](../reference/accounts.md#bank-transaction)

## DocTypes du module

Pièces comptables, journaux et référentiels — le détail de chaque champ est dans la [référence complète](../reference/accounts.md).

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Account`](../reference/accounts.md#account) | Account | données de base |  |  |  |
| [`Account Category`](../reference/accounts.md#account-category) | Account Category | données de base |  |  |  |
| [`Accounting Dimension`](../reference/accounts.md#accounting-dimension) | Accounting Dimension | données de base |  |  |  |
| [`Accounting Dimension Filter`](../reference/accounts.md#accounting-dimension-filter) | Accounting Dimension Filter | données de base |  |  |  |
| [`Accounting Period`](../reference/accounts.md#accounting-period) | Accounting Period | données de base |  |  |  |
| [`Bank`](../reference/accounts.md#bank) | Bank | données de base |  |  |  |
| [`Bank Account`](../reference/accounts.md#bank-account) | Bank Account | données de base |  |  |  |
| [`Bank Account Balance`](../reference/accounts.md#bank-account-balance) | Bank Account Balance | données de base |  |  |  |
| [`Bank Account Subtype`](../reference/accounts.md#bank-account-subtype) | Bank Account Subtype | données de base |  |  |  |
| [`Bank Account Type`](../reference/accounts.md#bank-account-type) | Bank Account Type | données de base |  |  |  |
| [`Bank Clearance`](../reference/accounts.md#bank-clearance) | Bank Clearance | données de base |  |  |  |
| [`Bank Reconciliation Tool`](../reference/accounts.md#bank-reconciliation-tool) | Bank Reconciliation Tool | données de base |  |  |  |
| [`Bank Statement Import`](../reference/accounts.md#bank-statement-import) | Bank Statement Import | données de base |  |  |  |
| [`Bank Statement Import Log`](../reference/accounts.md#bank-statement-import-log) | Bank Statement Import Log | données de base |  |  |  |
| [`Bank Transaction Rule`](../reference/accounts.md#bank-transaction-rule) | Bank Transaction Rule | données de base |  |  |  |
| [`Bisect Accounting Statements`](../reference/accounts.md#bisect-accounting-statements) | Bisect Accounting Statements | données de base |  |  |  |
| [`Bisect Nodes`](../reference/accounts.md#bisect-nodes) | Bisect Nodes | données de base |  |  |  |
| [`Chart of Accounts Importer`](../reference/accounts.md#chart-of-accounts-importer) | Chart of Accounts Importer | données de base |  |  |  |
| [`Cheque Print Template`](../reference/accounts.md#cheque-print-template) | Cheque Print Template | données de base |  |  |  |
| [`Cost Center`](../reference/accounts.md#cost-center) | Cost Center | données de base |  |  |  |
| [`Coupon Code`](../reference/accounts.md#coupon-code) | Coupon Code | données de base |  |  |  |
| [`Dunning Type`](../reference/accounts.md#dunning-type) | Dunning Type | données de base |  |  |  |
| [`Finance Book`](../reference/accounts.md#finance-book) | Finance Book | données de base |  |  |  |
| [`Financial Report Template`](../reference/accounts.md#financial-report-template) | Financial Report Template | données de base |  |  |  |
| [`Fiscal Year`](../reference/accounts.md#fiscal-year) | Fiscal Year | données de base |  |  |  |
| [`Item Tax Template`](../reference/accounts.md#item-tax-template) | Item Tax Template | données de base |  |  |  |
| [`Journal Entry Template`](../reference/accounts.md#journal-entry-template) | Journal Entry Template | données de base |  |  |  |
| [`Ledger Health`](../reference/accounts.md#ledger-health) | Ledger Health | données de base |  |  |  |
| [`Ledger Health Monitor`](../reference/accounts.md#ledger-health-monitor) | Ledger Health Monitor | données de base |  |  |  |
| [`Ledger Merge`](../reference/accounts.md#ledger-merge) | Ledger Merge | données de base |  |  |  |
| [`Loan`](../reference/accounts.md#loan) | Loan | données de base |  |  |  |
| [`Loan Product`](../reference/accounts.md#loan-product) | Loan Product | données de base |  |  |  |
| [`Loan Repayment`](../reference/accounts.md#loan-repayment) | Loan Repayment | données de base |  |  |  |
| [`Loyalty Point Entry`](../reference/accounts.md#loyalty-point-entry) | Loyalty Point Entry | données de base |  |  |  |
| [`Loyalty Program`](../reference/accounts.md#loyalty-program) | Loyalty Program | données de base |  |  |  |
| [`Mode of Payment`](../reference/accounts.md#mode-of-payment) | Mode of Payment | données de base |  |  |  |
| [`Monthly Distribution`](../reference/accounts.md#monthly-distribution) | Monthly Distribution | données de base |  |  |  |
| [`Opening Invoice Creation Tool`](../reference/accounts.md#opening-invoice-creation-tool) | Opening Invoice Creation Tool | données de base |  |  |  |
| [`Party Link`](../reference/accounts.md#party-link) | Party Link | données de base |  |  |  |
| [`Payment Gateway`](../reference/accounts.md#payment-gateway) | Payment Gateway | données de base |  |  |  |
| [`Payment Gateway Account`](../reference/accounts.md#payment-gateway-account) | Payment Gateway Account | données de base |  |  |  |
| [`Payment Reconciliation`](../reference/accounts.md#payment-reconciliation) | Payment Reconciliation | données de base |  |  |  |
| [`Payment Term`](../reference/accounts.md#payment-term) | Payment Term | données de base |  |  |  |
| [`Payment Terms Template`](../reference/accounts.md#payment-terms-template) | Payment Terms Template | données de base |  |  |  |
| [`Pegged Currencies`](../reference/accounts.md#pegged-currencies) | Pegged Currencies | données de base |  |  |  |
| [`POS Profile`](../reference/accounts.md#pos-profile) | POS Profile | données de base |  |  |  |
| [`Pricing Rule`](../reference/accounts.md#pricing-rule) | Pricing Rule | données de base |  |  |  |
| [`Process Payment Reconciliation Log`](../reference/accounts.md#process-payment-reconciliation-log) | Process Payment Reconciliation Log | données de base |  |  |  |
| [`Process Statement Of Accounts`](../reference/accounts.md#process-statement-of-accounts) | Process Statement Of Accounts | données de base |  |  |  |
| [`Promotional Scheme`](../reference/accounts.md#promotional-scheme) | Promotional Scheme | données de base |  |  |  |
| [`Purchase Taxes and Charges Template`](../reference/accounts.md#purchase-taxes-and-charges-template) | Purchase Taxes and Charges Template | données de base |  |  |  |
| [`Sales Taxes and Charges Template`](../reference/accounts.md#sales-taxes-and-charges-template) | Sales Taxes and Charges Template | données de base |  |  |  |
| [`Share Type`](../reference/accounts.md#share-type) | Share Type | données de base |  |  |  |
| [`Shareholder`](../reference/accounts.md#shareholder) | Shareholder | données de base |  |  |  |
| [`Shipping Rule`](../reference/accounts.md#shipping-rule) | Shipping Rule | données de base |  |  |  |
| [`Subscription`](../reference/accounts.md#subscription) | Subscription | données de base |  |  |  |
| [`Subscription Plan`](../reference/accounts.md#subscription-plan) | Subscription Plan | données de base |  |  |  |
| [`Tax Category`](../reference/accounts.md#tax-category) | Tax Category | données de base |  |  |  |
| [`Tax Rule`](../reference/accounts.md#tax-rule) | Tax Rule | données de base |  |  |  |
| [`Tax Withholding Category`](../reference/accounts.md#tax-withholding-category) | Tax Withholding Category | données de base |  |  |  |
| [`Tax Withholding Group`](../reference/accounts.md#tax-withholding-group) | Tax Withholding Group | données de base |  |  |  |
| [`Accounting Dimension Detail`](../reference/accounts.md#accounting-dimension-detail) | Accounting Dimension Detail | enfant |  |  |  |
| [`Advance Taxes and Charges`](../reference/accounts.md#advance-taxes-and-charges) | Advance Taxes and Charges | enfant |  |  |  |
| [`Allowed Dimension`](../reference/accounts.md#allowed-dimension) | Allowed Dimension | enfant |  |  |  |
| [`Allowed To Transact With`](../reference/accounts.md#allowed-to-transact-with) | Allowed To Transact With | enfant |  |  |  |
| [`Applicable On Account`](../reference/accounts.md#applicable-on-account) | Applicable On Account | enfant |  |  |  |
| [`Bank Clearance Detail`](../reference/accounts.md#bank-clearance-detail) | Bank Clearance Detail | enfant |  |  |  |
| [`Bank Statement Import Log Column Map`](../reference/accounts.md#bank-statement-import-log-column-map) | Bank Statement Import Log Column Map | enfant |  |  |  |
| [`Bank Transaction Mapping`](../reference/accounts.md#bank-transaction-mapping) | Bank Transaction Mapping | enfant |  |  |  |
| [`Bank Transaction Payments`](../reference/accounts.md#bank-transaction-payments) | Bank Transaction Payments | enfant |  |  |  |
| [`Bank Transaction Rule Accounts`](../reference/accounts.md#bank-transaction-rule-accounts) | Bank Transaction Rule Accounts | enfant |  |  |  |
| [`Bank Transaction Rule Description Conditions`](../reference/accounts.md#bank-transaction-rule-description-conditions) | Bank Transaction Rule Description Conditions | enfant |  |  |  |
| [`Budget Distribution`](../reference/accounts.md#budget-distribution) | Budget Distribution | enfant |  |  |  |
| [`Campaign Item`](../reference/accounts.md#campaign-item) | Campaign Item | enfant |  |  |  |
| [`Cashier Closing Payments`](../reference/accounts.md#cashier-closing-payments) | Cashier Closing Payments | enfant |  |  |  |
| [`Closed Document`](../reference/accounts.md#closed-document) | Closed Document | enfant |  |  |  |
| [`Cost Center Allocation Percentage`](../reference/accounts.md#cost-center-allocation-percentage) | Cost Center Allocation Percentage | enfant |  |  |  |
| [`Currency Exchange Settings Details`](../reference/accounts.md#currency-exchange-settings-details) | Currency Exchange Settings Details | enfant |  |  |  |
| [`Currency Exchange Settings Result`](../reference/accounts.md#currency-exchange-settings-result) | Currency Exchange Settings Result | enfant |  |  |  |
| [`Customer Group Item`](../reference/accounts.md#customer-group-item) | Customer Group Item | enfant |  |  |  |
| [`Customer Item`](../reference/accounts.md#customer-item) | Customer Item | enfant |  |  |  |
| [`Discounted Invoice`](../reference/accounts.md#discounted-invoice) | Discounted Invoice | enfant |  |  |  |
| [`Dunning Letter Text`](../reference/accounts.md#dunning-letter-text) | Dunning Letter Text | enfant |  |  |  |
| [`Exchange Rate Revaluation Account`](../reference/accounts.md#exchange-rate-revaluation-account) | Exchange Rate Revaluation Account | enfant |  |  |  |
| [`Financial Report Row`](../reference/accounts.md#financial-report-row) | Financial Report Row | enfant |  |  |  |
| [`Fiscal Year Company`](../reference/accounts.md#fiscal-year-company) | Fiscal Year Company | enfant |  |  |  |
| [`Item Tax Template Detail`](../reference/accounts.md#item-tax-template-detail) | Item Tax Template Detail | enfant |  |  |  |
| [`Item Wise Tax Detail`](../reference/accounts.md#item-wise-tax-detail) | Item Wise Tax Detail | enfant |  |  |  |
| [`Journal Entry Account`](../reference/accounts.md#journal-entry-account) | Journal Entry Account | enfant |  |  |  |
| [`Journal Entry Template Account`](../reference/accounts.md#journal-entry-template-account) | Journal Entry Template Account | enfant |  |  |  |
| [`Ledger Health Monitor Company`](../reference/accounts.md#ledger-health-monitor-company) | Ledger Health Monitor Company | enfant |  |  |  |
| [`Ledger Merge Accounts`](../reference/accounts.md#ledger-merge-accounts) | Ledger Merge Accounts | enfant |  |  |  |
| [`Loyalty Program Collection`](../reference/accounts.md#loyalty-program-collection) | Loyalty Program Collection | enfant |  |  |  |
| [`Mode of Payment Account`](../reference/accounts.md#mode-of-payment-account) | Mode of Payment Account | enfant |  |  |  |
| [`Monthly Distribution Percentage`](../reference/accounts.md#monthly-distribution-percentage) | Monthly Distribution Percentage | enfant |  |  |  |
| [`Opening Invoice Creation Tool Item`](../reference/accounts.md#opening-invoice-creation-tool-item) | Opening Invoice Creation Tool Item | enfant |  |  |  |
| [`Overdue Payment`](../reference/accounts.md#overdue-payment) | Overdue Payment | enfant |  |  |  |
| [`Party Account`](../reference/accounts.md#party-account) | Party Account | enfant |  |  |  |
| [`Payment Entry Deduction`](../reference/accounts.md#payment-entry-deduction) | Payment Entry Deduction | enfant |  |  |  |
| [`Payment Entry Reference`](../reference/accounts.md#payment-entry-reference) | Payment Entry Reference | enfant |  |  |  |
| [`Payment Order Reference`](../reference/accounts.md#payment-order-reference) | Payment Order Reference | enfant |  |  |  |
| [`Payment Reconciliation Allocation`](../reference/accounts.md#payment-reconciliation-allocation) | Payment Reconciliation Allocation | enfant |  |  |  |
| [`Payment Reconciliation Invoice`](../reference/accounts.md#payment-reconciliation-invoice) | Payment Reconciliation Invoice | enfant |  |  |  |
| [`Payment Reconciliation Payment`](../reference/accounts.md#payment-reconciliation-payment) | Payment Reconciliation Payment | enfant |  |  |  |
| [`Payment Reference`](../reference/accounts.md#payment-reference) | Payment Reference | enfant |  |  |  |
| [`Payment Schedule`](../reference/accounts.md#payment-schedule) | Payment Schedule | enfant |  |  |  |
| [`Payment Terms Template Detail`](../reference/accounts.md#payment-terms-template-detail) | Payment Terms Template Detail | enfant |  |  |  |
| [`Pegged Currency Details`](../reference/accounts.md#pegged-currency-details) | Pegged Currency Details | enfant |  |  |  |
| [`POS Closing Entry Detail`](../reference/accounts.md#pos-closing-entry-detail) | POS Closing Entry Detail | enfant |  |  |  |
| [`POS Closing Entry Taxes`](../reference/accounts.md#pos-closing-entry-taxes) | POS Closing Entry Taxes | enfant |  |  |  |
| [`POS Customer Group`](../reference/accounts.md#pos-customer-group) | POS Customer Group | enfant |  |  |  |
| [`POS Field`](../reference/accounts.md#pos-field) | POS Field | enfant |  |  |  |
| [`POS Invoice Item`](../reference/accounts.md#pos-invoice-item) | POS Invoice Item | enfant |  |  |  |
| [`POS Invoice Reference`](../reference/accounts.md#pos-invoice-reference) | POS Invoice Reference | enfant |  |  |  |
| [`POS Item Group`](../reference/accounts.md#pos-item-group) | POS Item Group | enfant |  |  |  |
| [`POS Opening Entry Detail`](../reference/accounts.md#pos-opening-entry-detail) | POS Opening Entry Detail | enfant |  |  |  |
| [`POS Payment Method`](../reference/accounts.md#pos-payment-method) | POS Payment Method | enfant |  |  |  |
| [`POS Profile User`](../reference/accounts.md#pos-profile-user) | POS Profile User | enfant |  |  |  |
| [`POS Search Fields`](../reference/accounts.md#pos-search-fields) | POS Search Fields | enfant |  |  |  |
| [`Pricing Rule Brand`](../reference/accounts.md#pricing-rule-brand) | Pricing Rule Brand | enfant |  |  |  |
| [`Pricing Rule Detail`](../reference/accounts.md#pricing-rule-detail) | Pricing Rule Detail | enfant |  |  |  |
| [`Pricing Rule Item Code`](../reference/accounts.md#pricing-rule-item-code) | Pricing Rule Item Code | enfant |  |  |  |
| [`Pricing Rule Item Group`](../reference/accounts.md#pricing-rule-item-group) | Pricing Rule Item Group | enfant |  |  |  |
| [`Process Payment Reconciliation Log Allocations`](../reference/accounts.md#process-payment-reconciliation-log-allocations) | Process Payment Reconciliation Log Allocations | enfant |  |  |  |
| [`Process Period Closing Voucher Detail`](../reference/accounts.md#process-period-closing-voucher-detail) | Process Period Closing Voucher Detail | enfant |  |  |  |
| [`Process Statement Of Accounts CC`](../reference/accounts.md#process-statement-of-accounts-cc) | Process Statement Of Accounts CC | enfant |  |  |  |
| [`Process Statement Of Accounts Customer`](../reference/accounts.md#process-statement-of-accounts-customer) | Process Statement Of Accounts Customer | enfant |  |  |  |
| [`Promotional Scheme Price Discount`](../reference/accounts.md#promotional-scheme-price-discount) | Promotional Scheme Price Discount | enfant |  |  |  |
| [`Promotional Scheme Product Discount`](../reference/accounts.md#promotional-scheme-product-discount) | Promotional Scheme Product Discount | enfant |  |  |  |
| [`PSOA Cost Center`](../reference/accounts.md#psoa-cost-center) | PSOA Cost Center | enfant |  |  |  |
| [`PSOA Project`](../reference/accounts.md#psoa-project) | PSOA Project | enfant |  |  |  |
| [`Purchase Invoice Advance`](../reference/accounts.md#purchase-invoice-advance) | Purchase Invoice Advance | enfant |  |  |  |
| [`Purchase Invoice Item`](../reference/accounts.md#purchase-invoice-item) | Purchase Invoice Item | enfant |  |  |  |
| [`Purchase Taxes and Charges`](../reference/accounts.md#purchase-taxes-and-charges) | Purchase Taxes and Charges | enfant |  |  |  |
| [`Repost Accounting Ledger Items`](../reference/accounts.md#repost-accounting-ledger-items) | Repost Accounting Ledger Items | enfant |  |  |  |
| [`Repost Allowed Types`](../reference/accounts.md#repost-allowed-types) | Repost Allowed Types | enfant |  |  |  |
| [`Repost Payment Ledger Items`](../reference/accounts.md#repost-payment-ledger-items) | Repost Payment Ledger Items | enfant |  |  |  |
| [`Sales Invoice Advance`](../reference/accounts.md#sales-invoice-advance) | Sales Invoice Advance | enfant |  |  |  |
| [`Sales Invoice Item`](../reference/accounts.md#sales-invoice-item) | Sales Invoice Item | enfant |  |  |  |
| [`Sales Invoice Payment`](../reference/accounts.md#sales-invoice-payment) | Sales Invoice Payment | enfant |  |  |  |
| [`Sales Invoice Reference`](../reference/accounts.md#sales-invoice-reference) | Sales Invoice Reference | enfant |  |  |  |
| [`Sales Invoice Timesheet`](../reference/accounts.md#sales-invoice-timesheet) | Sales Invoice Timesheet | enfant |  |  |  |
| [`Sales Partner Item`](../reference/accounts.md#sales-partner-item) | Sales Partner Item | enfant |  |  |  |
| [`Sales Taxes and Charges`](../reference/accounts.md#sales-taxes-and-charges) | Sales Taxes and Charges | enfant |  |  |  |
| [`Share Balance`](../reference/accounts.md#share-balance) | Share Balance | enfant |  |  |  |
| [`Shipping Rule Condition`](../reference/accounts.md#shipping-rule-condition) | Shipping Rule Condition | enfant |  |  |  |
| [`Shipping Rule Country`](../reference/accounts.md#shipping-rule-country) | Shipping Rule Country | enfant |  |  |  |
| [`South Africa VAT Account`](../reference/accounts.md#south-africa-vat-account) | South Africa VAT Account | enfant |  |  |  |
| [`Subscription Plan Detail`](../reference/accounts.md#subscription-plan-detail) | Subscription Plan Detail | enfant |  |  |  |
| [`Supplier Group Item`](../reference/accounts.md#supplier-group-item) | Supplier Group Item | enfant |  |  |  |
| [`Supplier Item`](../reference/accounts.md#supplier-item) | Supplier Item | enfant |  |  |  |
| [`Tax Withholding Account`](../reference/accounts.md#tax-withholding-account) | Tax Withholding Account | enfant |  |  |  |
| [`Tax Withholding Entry`](../reference/accounts.md#tax-withholding-entry) | Tax Withholding Entry | enfant |  |  |  |
| [`Tax Withholding Rate`](../reference/accounts.md#tax-withholding-rate) | Tax Withholding Rate | enfant |  |  |  |
| [`Territory Item`](../reference/accounts.md#territory-item) | Territory Item | enfant |  |  |  |
| [`Transaction Deletion Record Details`](../reference/accounts.md#transaction-deletion-record-details) | Transaction Deletion Record Details | enfant |  |  |  |
| [`Unreconcile Payment Entries`](../reference/accounts.md#unreconcile-payment-entries) | Unreconcile Payment Entries | enfant |  |  |  |
| [`Account Closing Balance`](../reference/accounts.md#account-closing-balance) | Account Closing Balance | pièce | oui | `ACB-{YYYY}-{#####}` |  |
| [`Advance Payment Ledger Entry`](../reference/accounts.md#advance-payment-ledger-entry) | Advance Payment Ledger Entry | pièce | oui | `APLE-{YYYY}-{#####}` |  |
| [`Bank Guarantee`](../reference/accounts.md#bank-guarantee) | Bank Guarantee | pièce | oui | `BG-{YYYY}-{#####}` |  |
| [`Bank Transaction`](../reference/accounts.md#bank-transaction) | Bank Transaction | pièce | oui | `BT-{YYYY}-{#####}` |  |
| [`Budget`](../reference/accounts.md#budget) | Budget | pièce | oui | `BUDG-{YYYY}-{#####}` |  |
| [`Cashier Closing`](../reference/accounts.md#cashier-closing) | Cashier Closing | pièce | oui | `CC-{YYYY}-{#####}` |  |
| [`Cost Center Allocation`](../reference/accounts.md#cost-center-allocation) | Cost Center Allocation | pièce | oui | `CCA-{YYYY}-{#####}` |  |
| [`Dunning`](../reference/accounts.md#dunning) | Dunning | pièce | oui | `DUNN-{YYYY}-{#####}` |  |
| [`Exchange Rate Revaluation`](../reference/accounts.md#exchange-rate-revaluation) | Exchange Rate Revaluation | pièce | oui | `ERR-{YYYY}-{#####}` |  |
| [`GL Entry`](../reference/accounts.md#gl-entry) | GL Entry | pièce | oui | `GE-{YYYY}-{#####}` |  |
| [`Invoice Discounting`](../reference/accounts.md#invoice-discounting) | Invoice Discounting | pièce | oui | `ID-{YYYY}-{#####}` |  |
| [`Journal Entry`](../reference/accounts.md#journal-entry) | Journal Entry | pièce | oui | `JE-{YYYY}-{#####}` |  |
| [`Payment Entry`](../reference/accounts.md#payment-entry) | Payment Entry | pièce | oui | `PE-{YYYY}-{#####}` |  |
| [`Payment Ledger Entry`](../reference/accounts.md#payment-ledger-entry) | Payment Ledger Entry | pièce | oui | `PLE-{YYYY}-{#####}` |  |
| [`Payment Order`](../reference/accounts.md#payment-order) | Payment Order | pièce | oui | `PO-{YYYY}-{#####}` |  |
| [`Payment Request`](../reference/accounts.md#payment-request) | Payment Request | pièce | oui | `PR-{YYYY}-{#####}` |  |
| [`Period Closing Voucher`](../reference/accounts.md#period-closing-voucher) | Period Closing Voucher | pièce | oui | `PCV-{YYYY}-{#####}` |  |
| [`POS Closing Entry`](../reference/accounts.md#pos-closing-entry) | POS Closing Entry | pièce | oui | `PCE-{YYYY}-{#####}` |  |
| [`POS Invoice`](../reference/accounts.md#pos-invoice) | POS Invoice | pièce | oui | `PI-{YYYY}-{#####}` |  |
| [`POS Invoice Merge Log`](../reference/accounts.md#pos-invoice-merge-log) | POS Invoice Merge Log | pièce | oui | `PIML-{YYYY}-{#####}` |  |
| [`POS Opening Entry`](../reference/accounts.md#pos-opening-entry) | POS Opening Entry | pièce | oui | `POE-{YYYY}-{#####}` |  |
| [`Process Deferred Accounting`](../reference/accounts.md#process-deferred-accounting) | Process Deferred Accounting | pièce | oui | `PDA-{YYYY}-{#####}` |  |
| [`Process Payment Reconciliation`](../reference/accounts.md#process-payment-reconciliation) | Process Payment Reconciliation | pièce | oui | `PPR-{YYYY}-{#####}` |  |
| [`Process Period Closing Voucher`](../reference/accounts.md#process-period-closing-voucher) | Process Period Closing Voucher | pièce | oui | `PPCV-{YYYY}-{#####}` |  |
| [`Process Subscription`](../reference/accounts.md#process-subscription) | Process Subscription | pièce | oui | `PRSU-{YYYY}-{#####}` |  |
| [`Purchase Invoice`](../reference/accounts.md#purchase-invoice) | Purchase Invoice | pièce | oui | `PUIN-{YYYY}-{#####}` |  |
| [`Repost Accounting Ledger`](../reference/accounts.md#repost-accounting-ledger) | Repost Accounting Ledger | pièce | oui | `RAL-{YYYY}-{#####}` |  |
| [`Repost Payment Ledger`](../reference/accounts.md#repost-payment-ledger) | Repost Payment Ledger | pièce | oui | `RPL-{YYYY}-{#####}` |  |
| [`Sales Invoice`](../reference/accounts.md#sales-invoice) | Sales Invoice | pièce | oui | `SI-{YYYY}-{#####}` |  |
| [`Share Transfer`](../reference/accounts.md#share-transfer) | Share Transfer | pièce | oui | `ST-{YYYY}-{#####}` |  |
| [`Unreconcile Payment`](../reference/accounts.md#unreconcile-payment) | Unreconcile Payment | pièce | oui | `UP-{YYYY}-{#####}` |  |
| [`Accounts Settings`](../reference/accounts.md#accounts-settings) | Accounts Settings | unique |  |  |  |
| [`Currency Exchange Settings`](../reference/accounts.md#currency-exchange-settings) | Currency Exchange Settings | unique |  |  |  |
| [`POS Settings`](../reference/accounts.md#pos-settings) | POS Settings | unique |  |  |  |
| [`Subscription Settings`](../reference/accounts.md#subscription-settings) | Subscription Settings | unique |  |  |  |

## Points clés

- **Les pièces maîtresses** : `Sales Invoice` (SI-) et `Purchase Invoice` (PI-) pour la facturation, `Journal Entry` (JV-, 131 champs) pour les écritures manuelles, `Payment Entry` (PR-) pour les encaissements/décaissements, `Purchase Receipt`/`Delivery Note` étant portés par `stock`.
- **Les journaux sont immuables** : `GL Entry`, `Payment Ledger Entry`, `Payment Reconciliation` et les tables de sous-comptes (`Accounts Ledger`,…) ferment leurs écritures humaines (`permissions` explicites) — seuls les hooks `on_submit`/`on_cancel` du plugin comptable y écrivent. Une écriture de journal cite sa pièce par `voucher_type`/`voucher_no` (`DynamicLink`).
- **Le plan SYSCOHADA** est embarqué comme données (voir le dépôt moteur, `charts/syscohada.yaml`) et se charge dans les comptes par société (`Company.default_currency`, arbres de comptes par `Account` avec vue `tree`).
- **Multi-devises** : 1 champ `currency_from` sur 4 en moyenne — facturation, rapprochement bancaire et réévaluation suivent tous la devise de la société ou du tiers.
- **Clôture et périodes** : `Fiscal Year` (hébergé dans `setup` mais piloté ici), `Period Closing Voucher`, `Bank Reconciliation` (rapprochement), `Process Deferred Accounting` (répartitions).

## Dépendances

- **Dépend de** : `setup` (215 liens — société, devise, pays…), `stock` (54), `projects` (27), `selling` (22), `crm` (19), `buying` (10), `assets` (5), `communication` (2), `regional` (1).
- **Requis par** : `stock` (57), `setup` (50), `selling` (30), `buying` (29), `assets` (28), `hr` (19), `payroll` (17), `subcontracting` (9), `regional` (5), `projects` (3), `manufacturing` (1).

Détail complet : [matrice](../dependances.md#comptabilite-accounts).

## Implémentation en plugin xcore

- Plugin `accounts` (`execution_mode: trusted`) : `load_dir` des 192 YAML, `load_workspaces`, déclaration `rbac.declare` des grants conventionnels + les grants fermés des journaux.
- **Hooks à écrire** (absents du YAML) : double écriture comptable à la soumission de chaque pièce (`Sales Invoice`, `Purchase Invoice`, `Payment Entry`, `Journal Entry`), écritures de régularisation à l'annulation, contrôle d'équilibre des lignes de journal (débit = crédit), rapprochement bancaire.
- **`cancel_ignores`** : `GL Entry`, `Payment Ledger Entry`… doivent figurer dans la liste de la pièce d'origine pour que son `on_cancel` puisse inverser ses propres écritures (garde M2 du moteur).
- La numérotation `JV-{YYYY}-{#####}` etc. est déjà déclarée dans le YAML — rien à coder.
- Traduction : le catalogue `fr.yaml` du dépôt moteur couvre ce module (T17).

## Référence complète

Chaque champ de chaque DocType : [Référence — Comptabilité](../reference/accounts.md).
