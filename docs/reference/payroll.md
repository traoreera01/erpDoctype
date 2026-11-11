# Référence des champs — Paie (`payroll`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `payroll/` (42 DocTypes). Ne pas éditer à la main : relancer le script.

444 champs au total ; types les plus fréquents : `Link` (136), `Currency` (83), `Boolean` (59), `Text` (38), `Date` (34).

## Additional Salary

*Additional Salary* — `payroll/additional_salary.yaml` · soumis

- **Numérotation** : série `AS-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `employee_name`
- **Icône** : `circle-plus`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — HR-ADS-.YY.-.MM.- | **requis** |
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `salary_component` | Salary Component | Link → `Salary Component` | **requis**; colonne de liste |
| `amount` | Amount | Currency | **requis**; colonne de liste; devise de `currency` |
| `overwrite_salary_structure_amount` | Overwrite Salary Structure Amount | Boolean | défaut `oui` |
| `deduct_full_tax_on_selected_payroll_date` | Deduct Full Tax on Selected Payroll Date | Boolean | défaut `non` |
| `payroll_date` | Payroll Date | Date | colonne de liste; — The date on which Salary Component with Amount will contribute for Earnings/Deduction in Salary Slip. |
| `employee_name` | Employee Name | Text | colonne de liste; lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `company` | Company | Link → `Company` | **requis** |
| `type` | Salary Component Type | Text | lecture seule |
| `is_recurring` | Is Recurring | Boolean | défaut `non` |
| `from_date` | From Date | Date |  |
| `to_date` | To Date | Date |  |
| `ref_doctype` | Reference Document Type | Text | lecture seule |
| `ref_docname` | Reference Document | DynamicLink → `ref_doctype` | lecture seule |
| `currency` | Currency | Link → `Currency` | **requis**; lecture seule |
| `disabled` | Disabled | Boolean | défaut `non` |

## Arrear

*Arrear* — `payroll/arrear.yaml` · soumis

- **Numérotation** : série `ARRE-{YYYY}-{#####}`
- **Titre** : `employee_name`
- **Icône** : `rotate-ccw-clock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `company` | Company | Link → `Company` | **requis** |
| `payroll_period` | Payroll Period | Link → `Payroll Period` | **requis** |
| `payroll_date` | Payroll Date | Date | **requis** |
| `arrear_start_date` | Arrear Start Date | Date | **requis**; — Salary slips starting on or after this date will be considered for arrear calculations |
| `salary_structure` | Salary Structure | Link → `Salary Structure` | **requis** |
| `currency` | Currency | Link → `Currency` | **requis**; lecture seule |
| `earning_arrears` | Earning Arrears | Table → `Payroll Correction Child` |  |
| `deduction_arrears` | Deduction Arrears | Table → `Payroll Correction Child` |  |
| `accrual_arrears` | Accrual Arrears | Table → `Payroll Correction Child` |  |

## Bulk Salary Structure Assignment

*Bulk Salary Structure Assignment* — `payroll/bulk_salary_structure_assignment.yaml`

- **Vues** : calendar
- **Titre** : `salary_structure`
- **Icône** : `users`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `salary_structure` | Salary Structure | Link → `Salary Structure` | **requis**; colonne de liste |
| `from_date` | From Date | Date | **requis**; colonne de liste |
| `income_tax_slab` | Income Tax Slab | Link → `Income Tax Slab` |  |
| `payroll_payable_account` | Payroll Payable Account | Link → `Account` |  |
| `branch` | Branch | Link → `Branch` |  |
| `department` | Department | Link → `Department` |  |
| `designation` | Designation | Link → `Designation` |  |
| `company` | Company | Link → `Company` | **requis**; lecture seule |
| `employment_type` | Employment Type | Link → `Employment Type` |  |
| `grade` | Employee Grade | Link → `Employee Grade` |  |
| `currency` | Currency | Link → `Currency` | lecture seule |

## Employee Benefit Application

*Employee Benefit Application* — `payroll/employee_benefit_application.yaml` · soumis

- **Numérotation** : série `EBA-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `employee_name`
- **Icône** : `gift`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `max_benefits` | Max Benefits (Yearly) | Currency | lecture seule; devise de `currency` |
| `remaining_benefit` | Remaining Benefits (Yearly) | Currency | lecture seule; devise de `currency` |
| `date` | Date | Date | **requis**; défaut `today` |
| `payroll_period` | Payroll Period | Link → `Payroll Period` | **requis**; colonne de liste |
| `department` | Department | Link → `Department` | lecture seule |
| `employee_benefits` | Flexible Benefits | Table → `Employee Benefit Application Detail` |  |
| `total_amount` | Total Amount | Currency | lecture seule; devise de `currency` |
| `currency` | Currency | Link → `Currency` | **requis**; lecture seule |
| `company` | Company | Link → `Company` | **requis** |

## Employee Benefit Application Detail

*Employee Benefit Application Detail* — `payroll/employee_benefit_application_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `max_benefit_amount` | Max Benefit Amount | Currency | **requis**; colonne de liste; lecture seule; devise de `parent_currency` |
| `amount` | Amount | Currency | **requis**; colonne de liste; devise de `parent_currency` |
| `salary_component` | Earning Component | Link → `Salary Component` | **requis**; colonne de liste; lecture seule |

## Employee Benefit Claim

*Employee Benefit Claim* — `payroll/employee_benefit_claim.yaml` · soumis

- **Numérotation** : série `EBC-{YYYY}-{#####}`
- **Titre** : `employee_name`
- **Icône** : `receipt`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `earning_component` | Claim Benefit For | Link → `Salary Component` | **requis**; colonne de liste |
| `max_amount_eligible` | Max Amount Eligible For Claim | Currency | lecture seule; devise de `currency` |
| `claimed_amount` | Claimed Amount | Currency | **requis**; colonne de liste; devise de `currency` |
| `attachments` | Attachments | Attach |  |
| `currency` | Currency | Link → `Currency` | **requis**; lecture seule |
| `company` | Company | Link → `Company` | **requis** |
| `payroll_date` | Payroll Date | Date | **requis**; défaut `today` |
| `yearly_benefit` | Yearly Amount | Currency | lecture seule; devise de `currency` |

## Employee Benefit Detail

*Employee Benefit Detail* — `payroll/employee_benefit_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `salary_component` | Earning Component | Link → `Salary Component` | **requis**; colonne de liste |
| `amount` | Benefit Amount | Currency | **requis**; colonne de liste; devise de `parent_currency` |

## Employee Benefit Ledger

*Employee Benefit Ledger* — `payroll/employee_benefit_ledger.yaml`

- **Vues** : calendar
- **Titre** : `employee_name`
- **Icône** : `book-open`
- **Permissions explicites** — `write` : 0, `create` : 0, `delete` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | colonne de liste |
| `employee_name` | Employee Name | Text |  |
| `company` | Company | Text |  |
| `transaction_type` | Transaction Type | Select — Accrual · Payout | colonne de liste |
| `posting_date` | Posting Date | Date | défaut `today` |
| `yearly_benefit` | Yearly Benefit | Currency |  |
| `payroll_period` | Payroll Period | Link → `Payroll Period` |  |
| `remarks` | Remarks | Text |  |
| `amount` | Amount | Currency | colonne de liste |
| `salary_component` | Salary Component | Link → `Salary Component` | colonne de liste |
| `salary_slip` | Salary Slip | Link → `Salary Slip` |  |
| `flexible_benefit` | Flexible Benefit | Boolean | défaut `non`; — Enabled only for Employee Benefit components from Salary Structure Assignment |
| `reference_doctype` | Reference Doctype | Text |  |
| `reference_document` | Reference Document | DynamicLink → `reference_doctype` |  |

## Employee Cost Center

*Employee Cost Center* — `payroll/employee_cost_center.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `cost_center` | Cost Center | Link → `Cost Center` | **requis**; colonne de liste |
| `percentage` | Percentage (%) | Int | **requis**; colonne de liste |

## Employee Incentive

*Employee Incentive* — `payroll/employee_incentive.yaml` · soumis

- **Numérotation** : série `EI-{YYYY}-{#####}`
- **Titre** : `employee_name`
- **Icône** : `badge-dollar-sign`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `incentive_amount` | Incentive Amount | Currency | **requis**; devise de `currency` |
| `payroll_date` | Payroll Date | Date | **requis** |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `salary_component` | Salary Component | Link → `Salary Component` | **requis** |
| `currency` | Currency | Link → `Currency` | **requis**; lecture seule |
| `company` | Company | Link → `Company` | **requis** |

## Employee Other Income

*Employee Other Income* — `payroll/employee_other_income.yaml` · soumis

- **Numérotation** : série `EOI-{YYYY}-{#####}`
- **Titre** : `employee_name`
- **Icône** : `coins`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `payroll_period` | Payroll Period | Link → `Payroll Period` | **requis**; colonne de liste |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `source` | Source | Text |  |
| `amount` | Amount | Currency | **requis**; colonne de liste; devise de `company.default_currency` |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |

## Employee Tax Exemption Category

*Employee Tax Exemption Category* — `payroll/employee_tax_exemption_category.yaml`

- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `max_amount` | Max Exemption Amount | Currency | colonne de liste |
| `is_active` | Is Active | Boolean | défaut `oui` |
| `description` | Description | LongText |  |

## Employee Tax Exemption Declaration

*Employee Tax Exemption Declaration* — `payroll/employee_tax_exemption_declaration.yaml` · soumis

- **Numérotation** : série `ETED-{YYYY}-{#####}`
- **Titre** : `employee_name`
- **Icône** : `file-pen-line`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `payroll_period` | Payroll Period | Link → `Payroll Period` | **requis**; colonne de liste |
| `company` | Company | Link → `Company` |  |
| `declarations` | Declarations | Table → `Employee Tax Exemption Declaration Category` |  |
| `total_declared_amount` | Total Declared Amount | Currency | lecture seule; devise de `currency` |
| `total_exemption_amount` | Total Exemption Amount | Currency | lecture seule; devise de `currency` |
| `currency` | Currency | Link → `Currency` | **requis** |

## Employee Tax Exemption Declaration Category

*Employee Tax Exemption Declaration Category* — `payroll/employee_tax_exemption_declaration_category.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `exemption_sub_category` | Exemption Sub Category | Link → `Employee Tax Exemption Sub Category` | **requis**; colonne de liste |
| `exemption_category` | Exemption Category | Link → `Employee Tax Exemption Category` | **requis**; colonne de liste; lecture seule |
| `max_amount` | Maximum Exempted Amount | Currency | **requis**; colonne de liste; lecture seule; devise de `parent_currency` |
| `amount` | Declared Amount | Currency | **requis**; colonne de liste; devise de `parent_currency` |

## Employee Tax Exemption Proof Submission

*Employee Tax Exemption Proof Submission* — `payroll/employee_tax_exemption_proof_submission.yaml` · soumis

- **Numérotation** : série `ETEPS-{YYYY}-{#####}`
- **Titre** : `employee_name`
- **Icône** : `file-check`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `submission_date` | Submission Date | Date | **requis**; défaut `today` |
| `payroll_period` | Payroll Period | Link → `Payroll Period` | **requis**; colonne de liste |
| `company` | Company | Link → `Company` | **requis**; lecture seule |
| `tax_exemption_proofs` | Tax Exemption Proofs | Table → `Employee Tax Exemption Proof Submission Detail` |  |
| `total_actual_amount` | Total Actual Amount | Currency | lecture seule; devise de `currency` |
| `exemption_amount` | Total Exemption Amount | Currency | lecture seule; devise de `currency` |
| `attachments` | Attachments | Attach |  |
| `currency` | Currency | Link → `Currency` | **requis** |

## Employee Tax Exemption Proof Submission Detail

*Employee Tax Exemption Proof Submission Detail* — `payroll/employee_tax_exemption_proof_submission_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `exemption_sub_category` | Exemption Sub Category | Link → `Employee Tax Exemption Sub Category` | **requis**; colonne de liste |
| `exemption_category` | Exemption Category | Text | **requis**; colonne de liste; lecture seule |
| `max_amount` | Maximum Exemption Amount | Currency | **requis**; colonne de liste; lecture seule; devise de `parent_currency` |
| `type_of_proof` | Type of Proof | Text | **requis**; colonne de liste |
| `amount` | Actual Amount | Currency | colonne de liste; devise de `parent_currency` |

## Employee Tax Exemption Sub Category

*Employee Tax Exemption Sub Category* — `payroll/employee_tax_exemption_sub_category.yaml`

- **Titre** : `exemption_category`
- **Icône** : `tags`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `exemption_category` | Tax Exemption Category | Link → `Employee Tax Exemption Category` | **requis**; colonne de liste |
| `max_amount` | Max Exemption Amount | Currency | colonne de liste |
| `is_active` | Is Active | Boolean | défaut `oui` |
| `description` | Description | LongText |  |

## Gratuity

*Gratuity* — `payroll/gratuity.yaml` · soumis

- **Numérotation** : série `GRAT-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `employee_name`
- **Icône** : `piggy-bank`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `company` | Company | Link → `Company` | **requis**; lecture seule |
| `posting_date` | Posting date | Date | **requis** |
| `current_work_experience` | Current Work Experience | Number | défaut `0.0` |
| `amount` | Total Amount | Currency | **requis**; lecture seule; devise de `company.default_currency` |
| `status` | Status | Select — Draft · Unpaid · Paid · Submitted · Cancelled | colonne de liste; lecture seule; défaut `Draft` |
| `expense_account` | Expense Account | Link → `Account` |  |
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` |  |
| `gratuity_rule` | Gratuity Rule | Link → `Gratuity Rule` | **requis** |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `designation` | Designation | Text | lecture seule |
| `paid_amount` | Paid Amount | Currency | lecture seule; devise de `company.default_currency` |
| `payable_account` | Payable Account | Link → `Account` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `pay_via_salary_slip` | Pay via Salary Slip | Boolean | défaut `oui` |
| `payroll_date` | Payroll Date | Date |  |
| `salary_component` | Salary Component | Link → `Salary Component` |  |

## Gratuity Applicable Component

*Gratuity Applicable Component* — `payroll/gratuity_applicable_component.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `salary_component` | Salary Component  | Link → `Salary Component` | **requis**; colonne de liste |

## Gratuity Rule

*Gratuity Rule* — `payroll/gratuity_rule.yaml`

- **Titre** : `calculate_gratuity_amount_based_on`
- **Icône** : `scale`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `disable` | Disable | Boolean | défaut `non` |
| `calculate_gratuity_amount_based_on` | Calculate Gratuity Amount Based On | Select — Current Slab · Sum of all previous slabs | **requis**; colonne de liste |
| `applicable_earnings_component` | Applicable Earnings Component | Table → `Gratuity Applicable Component` | — Salary components should be part of the Salary Structure. |
| `gratuity_rule_slabs` | Current Work Experience | Table → `Gratuity Rule Slab` | — Set "From(Year)" and "To(Year)" to 0 for no upper and lower limit. |
| `work_experience_calculation_function` | Work Experience Calculation Method | Select — Round off Work Experience · Take Exact Completed Years · Manual | défaut `Round off Work Experience` |
| `total_working_days_per_year` | Total working Days Per Year | Number | défaut `365.0` |
| `minimum_year_for_gratuity` | Minimum Year for Gratuity | Int |  |

## Gratuity Rule Slab

*Gratuity Rule Slab* — `payroll/gratuity_rule_slab.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `fraction_of_applicable_earnings` | Fraction of Applicable Earnings  | Number | **requis**; colonne de liste |
| `from_year` | From(Year) | Int | **requis**; colonne de liste; lecture seule |
| `to_year` | To(Year) | Int | **requis**; colonne de liste; défaut `0` |

## Income Tax Slab

*Income Tax Slab* — `payroll/income_tax_slab.yaml` · soumis

- **Numérotation** : série `ITS-{YYYY}-{#####}`
- **Icône** : `badge-percent`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `effective_from` | Effective from | Date | **requis**; colonne de liste |
| `allow_tax_exemption` | Allow Tax Exemption | Boolean | défaut `non`; — If enabled, Tax Exemption Declaration will be considered for income tax calculation. |
| `slabs` | Taxable Salary Slabs | Table → `Taxable Salary Slab` |  |
| `disabled` | Disabled | Boolean | défaut `non` |
| `standard_tax_exemption_amount` | Standard Tax Exemption Amount | Currency | devise de `currency` |
| `company` | Company | Link → `Company` |  |
| `other_taxes_and_charges` | Other Taxes and Charges | Table → `Income Tax Slab Other Charges` |  |
| `currency` | Currency | Link → `Currency` | **requis** |
| `tax_relief_limit` | Taxable Income Relief Threshold Limit | Currency | devise de `currency`; — Maximum annual taxable income eligible for full tax relief. No tax is applied if income does not exceed this l |

## Income Tax Slab Other Charges

*Income Tax Slab Other Charges* — `payroll/income_tax_slab_other_charges.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `description` | Description | Text | **requis**; colonne de liste |
| `percent` | Percent | Percent | **requis**; colonne de liste |
| `min_taxable_income` | Min Taxable Income | Currency | colonne de liste; devise de `parent_currency` |
| `max_taxable_income` | Max Taxable Income | Currency | colonne de liste; devise de `parent_currency` |

## Payroll Correction

*Payroll Correction* — `payroll/payroll_correction.yaml` · soumis

- **Numérotation** : série `PC-{YYYY}-{#####}`
- **Titre** : `employee_name`
- **Icône** : `file-diff`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | colonne de liste; lecture seule; recopié de `employee.employee_name` |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `currency` | Currency | Link → `Currency` |  |
| `payroll_period` | Payroll Period | Link → `Payroll Period` | **requis**; colonne de liste |
| `salary_slip_reference` | Salary Slip Reference | Link → `Salary Slip` | **requis**; lecture seule |
| `working_days` | Working Days | Number | lecture seule |
| `lwp_days` | Total Days Without Pay | Number | lecture seule |
| `days_to_reverse` | Days to Reverse | Number | **requis**; colonne de liste; — Enter the number of Leave Without Pay (LWP) days you want to reverse. This value cannot exceed the total LWP d |
| `earning_arrears` | Earning Arrears | Table → `Payroll Correction Child` | lecture seule |
| `deduction_arrears` | Deduction Arrears | Table → `Payroll Correction Child` | lecture seule |
| `payroll_date` | Payroll Date | Date | **requis**; — Choose the date on which you want to create these components as arrears. |
| `accrual_arrears` | Accrual Arrears | Table → `Payroll Correction Child` | lecture seule |
| `payment_days` | Payment Days | Number | lecture seule |

## Payroll Correction Child

*Payroll Correction Child* — `payroll/payroll_correction_child.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `salary_component` | Salary Component | Link → `Salary Component` | **requis**; colonne de liste |
| `amount` | Amount | Number | **requis**; colonne de liste |

## Payroll Employee Detail

*Payroll Employee Detail* — `payroll/payroll_employee_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | colonne de liste |
| `employee_name` | Employee Name | Text | colonne de liste; lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | colonne de liste; lecture seule |
| `designation` | Designation | Text | colonne de liste; lecture seule |
| `is_salary_withheld` | Is Salary Withheld | Boolean | colonne de liste; défaut `non` |

## Payroll Entry

*Payroll Entry* — `payroll/payroll_entry.yaml` · soumis

- **Numérotation** : série `PAEN-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `status`
- **Icône** : `wallet`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `posting_date` | Posting Date | Date | **requis**; défaut `today` |
| `payroll_frequency` | Payroll Frequency | Select — Monthly · Fortnightly · Bimonthly · Weekly · Daily |  |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `branch` | Branch | Link → `Branch` | colonne de liste |
| `department` | Department | Link → `Department` |  |
| `designation` | Designation | Link → `Designation` |  |
| `number_of_employees` | Number Of Employees | Int | lecture seule |
| `employees` | Employees | Table → `Payroll Employee Detail` |  |
| `validate_attendance` | Validate Attendance | Boolean | défaut `non` |
| `salary_slip_based_on_timesheet` | Salary Slip Based on Timesheet | Boolean | défaut `non` |
| `start_date` | Start Date | Date | **requis** |
| `end_date` | End Date | Date | **requis** |
| `deduct_tax_for_unsubmitted_tax_exemption_proof` | Deduct Tax For Unsubmitted Tax Exemption Proof | Boolean | défaut `non` |
| `cost_center` | Cost Center | Link → `Cost Center` | **requis** |
| `project` | Project | Link → `Project` |  |
| `payment_account` | Payment Account | Link → `Account` | — Select Payment Account to make Bank Entry |
| `salary_slips_created` | Salary Slips Created | Boolean | lecture seule; masqué |
| `salary_slips_submitted` | Salary Slips Submitted | Boolean | lecture seule; masqué |
| `bank_account` | Bank Account | Link → `Bank Account` |  |
| `currency` | Currency | Link → `Currency` | **requis**; colonne de liste |
| `exchange_rate` | Exchange Rate | Number | **requis** |
| `payroll_payable_account` | Payroll Payable Account | Link → `Account` | **requis** |
| `error_message` | Error Message | TextEditor | lecture seule |
| `status` | Status | Select — Draft · Submitted · Cancelled · Queued · Failed | lecture seule |
| `grade` | Grade | Link → `Employee Grade` |  |
| `overtime_step` | Overtime Slip Step | Select — Create · Submit |  |

## Payroll Period

*Payroll Period* — `payroll/payroll_period.yaml`

- **Vues** : calendar, gantt
- **Titre** : `company`
- **Icône** : `calendar-range`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `start_date` | Start Date | Date | **requis** |
| `end_date` | End Date | Date | **requis** |
| `periods` | Payroll Periods | Table → `Payroll Period Date` |  |

## Payroll Period Date

*Payroll Period Date* — `payroll/payroll_period_date.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `start_date` | Start Date | Date | **requis**; colonne de liste |
| `end_date` | End Date | Date | **requis**; colonne de liste |

## Payroll Settings

*Payroll Settings* — `payroll/payroll_settings.yaml` · document unique

- **Titre** : `password_policy`
- **Icône** : `settings`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `payroll_based_on` | Calculate Payroll Working Days Based On | Select — Leave · Attendance | défaut `Leave` |
| `max_working_hours_against_timesheet` | Max working hours against Timesheet | Number |  |
| `include_holidays_in_total_working_days` | Include holidays in Total no. of Working Days | Boolean | défaut `non`; — If enabled, total no. of working days will include holidays, and this will reduce the value of Salary Per Day |
| `disable_rounded_total` | Disable Rounded Total | Boolean | défaut `non`; — If checked, hides and disables Rounded Total field in Salary Slips |
| `daily_wages_fraction_for_half_day` | Fraction of Daily Salary for Half Day | Number | défaut `0.5`; — The fraction of daily wages to be paid for half-day attendance |
| `email_salary_slip_to_employee` | Email Salary Slip to Employee | Boolean | défaut `oui`; — Emails salary slip to employee based on preferred email selected in Employee |
| `encrypt_salary_slips_in_emails` | Encrypt Salary Slips in Emails | Boolean | défaut `non`; — The salary slip emailed to the employee will be password protected, the password will be generated based on th |
| `password_policy` | Password Policy | Text | colonne de liste; — <b>Example:</b> SAL-{first_name}-{date_of_birth.year} <br>This will generate a password like SAL-Jane-1972 |
| `consider_unmarked_attendance_as` | Consider Unmarked Attendance As | Select — Present · Absent |  |
| `show_leave_balances_in_salary_slip` | Show Leave Balances in Salary Slip | Boolean | défaut `non` |
| `process_payroll_accounting_entry_based_on_employee` | Process Payroll Accounting Entry based on Employee | Boolean | défaut `non`; — If checked, Payroll Payable will be booked against each employee |
| `consider_marked_attendance_on_holidays` | Consider Marked Attendance on Holidays | Boolean | défaut `non`; — If enabled, deducts payment days for absent attendance on holidays. By default, holidays are considered as pai |
| `sender` | Sender | Link → `Email Account` |  |
| `sender_email` | Sender Email | Text | lecture seule |
| `email_template` | Email Template | Link → `Email Template` |  |
| `create_overtime_slip` | Create Overtime Slip For Eligible Employee(s) | Boolean | défaut `non`; — If checked, overtime slip creation can be handled as part of payroll processing |
| `sender_copy` | Sender Copy | Link → `Email Account` |  |
| `mandatory_benefit_application` | Mandatory Benefit Application | Boolean | défaut `non`; — If checked, flexible benefits are considered only if benefit application exists |

## Retention Bonus

*Retention Bonus* — `payroll/retention_bonus.yaml` · soumis

- **Numérotation** : série `RB-{YYYY}-{#####}`
- **Titre** : `employee_name`
- **Icône** : `gem`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis** |
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `bonus_payment_date` | Bonus Payment Date | Date | **requis**; colonne de liste |
| `bonus_amount` | Bonus Amount | Currency | **requis**; devise de `currency` |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `date_of_joining` | Date of Joining | Text | lecture seule |
| `salary_component` | Salary Component | Link → `Salary Component` | **requis** |
| `currency` | Currency | Link → `Currency` | **requis**; lecture seule |

## Salary Component

*Salary Component* — `payroll/salary_component.yaml`

- **Titre** : `salary_component`
- **Icône** : `puzzle`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `salary_component` | Name | Text | **requis**; colonne de liste |
| `salary_component_abbr` | Abbr | Text | **requis**; colonne de liste |
| `type` | Type | Select — Earning · Deduction · Employer Contribution | **requis** |
| `is_tax_applicable` | Is Tax Applicable | Boolean | défaut `oui` |
| `depends_on_payment_days` | Depends on Payment Days | Boolean | défaut `oui` |
| `do_not_include_in_total` | Do Not Include in Total | Boolean | défaut `non` |
| `deduct_full_tax_on_selected_payroll_date` | Deduct Full Tax on Selected Payroll Date | Boolean | défaut `non` |
| `disabled` | Disabled | Boolean | défaut `non` |
| `description` | Description | LongText | colonne de liste |
| `statistical_component` | Statistical Component | Boolean | défaut `non`; — If enabled, the value specified or calculated in this component will not contribute to the earnings or deducti |
| `is_flexible_benefit` | Is Flexible Benefit | Boolean | défaut `non` |
| `max_benefit_amount` | Max Benefit Amount (Yearly) | Currency | — If greater than zero, this sets the maximum benefit amount assignable to any employee |
| `variable_based_on_taxable_salary` | Variable Based On Taxable Salary | Boolean | défaut `non`; — If enabled, the component will be considered as a tax component and the amount will be auto-calculated as per  |
| `accounts` | Accounts | Table → `Salary Component Account` |  |
| `condition` | Condition | Code |  |
| `amount_based_on_formula` | Amount based on formula | Boolean | défaut `non` |
| `formula` | Formula | Code |  |
| `amount` | Amount | Currency |  |
| `round_to_the_nearest_integer` | Round to the Nearest Integer | Boolean | défaut `non` |
| `exempted_from_income_tax` | Exempted from Income Tax | Boolean | défaut `non`; — If checked, the full amount will be deducted from taxable income before calculating income tax without any dec |
| `is_income_tax_component` | Is Income Tax Component | Boolean | défaut `non`; — If enabled, the component will be considered in the Income Tax Deductions report |
| `remove_if_zero_valued` | Remove if Zero Valued | Boolean | défaut `oui`; — If enabled, the component will not be displayed in the salary slip if the amount is zero |
| `do_not_include_in_accounts` | Do Not Include in Accounting Entries | Boolean | défaut `non`; — If enabled, the amount will be excluded from accounting entries during Journal Entry creation. |
| `arrear_component` | Arrear Component | Boolean | défaut `non`; — If enabled, this component will be included in arrear calculations |
| `accrual_component` | Accrual Component | Boolean | défaut `non`; — If enabled, this component allows to accrue amounts without adding them to earnings. The accrued balance is tr |
| `payout_method` | Payout Method | Select — Accrue and payout at end of payroll period · Accrue per cycle, pay only on claim · Allow claim for full benefit amount |  |
| `final_cycle_accrual_payout` | Payout Unclaimed Amount in Final Payroll Cycle | Boolean | défaut `non` |

## Salary Component Account

*Salary Component Account* — `payroll/salary_component_account.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | colonne de liste |
| `account` | Account | Link → `Account` | colonne de liste; — Default Bank / Cash account will be automatically updated in Salary Journal Entry when this mode is selected. |
| `liability_account` | Liability Account | Link → `Account` | colonne de liste; — Liability account credited for employer contributions. Applicable only for Employer Contribution components, w |

## Salary Detail

*Salary Detail* — `payroll/salary_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `salary_component` | Component | Link → `Salary Component` | **requis**; colonne de liste |
| `abbr` | Abbr | Text | colonne de liste; lecture seule |
| `statistical_component` | Statistical Component | Boolean | défaut `non`; — If selected, the value specified or calculated in this component will not contribute to the earnings or deduct |
| `is_tax_applicable` | Is Tax Applicable | Boolean | colonne de liste; lecture seule |
| `is_flexible_benefit` | Is Flexible Benefit | Boolean | lecture seule |
| `variable_based_on_taxable_salary` | Variable Based On Taxable Salary | Boolean | lecture seule |
| `depends_on_payment_days` | Depends on Payment Days | Boolean | colonne de liste; lecture seule |
| `deduct_full_tax_on_selected_payroll_date` | Deduct Full Tax on Selected Payroll Date | Boolean | lecture seule |
| `condition` | Condition | Code |  |
| `amount_based_on_formula` | Amount based on formula | Boolean | défaut `non` |
| `formula` | Formula | Code |  |
| `amount` | Amount | Currency | colonne de liste; devise de `parent_currency` |
| `do_not_include_in_total` | Do not include in total | Boolean | défaut `non` |
| `default_amount` | Default Amount | Currency | devise de `parent_currency` |
| `additional_amount` | Additional Amount | Currency | lecture seule; masqué; devise de `parent_currency` |
| `tax_on_flexible_benefit` | Tax on flexible benefit | Currency | lecture seule; devise de `parent_currency` |
| `tax_on_additional_salary` | Tax on additional salary | Currency | lecture seule; devise de `parent_currency` |
| `additional_salary` | Additional Salary  | Link → `Additional Salary` | lecture seule |
| `exempted_from_income_tax` | Exempted from Income Tax | Boolean | lecture seule |
| `year_to_date` | Year To Date | Currency | lecture seule; devise de `parent_currency`; — Total salary booked against this component for this employee from the beginning of the year (payroll period or |
| `is_recurring_additional_salary` | Is Recurring Additional Salary | Boolean | lecture seule |
| `do_not_include_in_accounts` | Do Not Include in Accounting Entries | Boolean | défaut `non`; — If enabled, the amount will be excluded from accounting entries during Journal Entry creation. |
| `accrual_component` | Accrual Component | Boolean | colonne de liste; lecture seule |

## Salary Slip

*Salary Slip* — `payroll/salary_slip.yaml` · soumis

- **Numérotation** : série `SS-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `employee_name`
- **Icône** : `receipt-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `posting_date` | Posting Date | Date | **requis**; colonne de liste; défaut `today` |
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | colonne de liste; lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `designation` | Designation | Link → `Designation` | lecture seule |
| `branch` | Branch | Link → `Branch` | lecture seule |
| `status` | Status | Select — Draft · Submitted · Cancelled · Withheld | lecture seule |
| `journal_entry` | Journal Entry | Link → `Journal Entry` |  |
| `payroll_entry` | Payroll Entry | Link → `Payroll Entry` | lecture seule |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `salary_slip_based_on_timesheet` | Salary Slip Based on Timesheet | Boolean | lecture seule |
| `start_date` | Start Date | Date |  |
| `end_date` | End Date | Date |  |
| `salary_structure` | Salary Structure | Link → `Salary Structure` | **requis**; colonne de liste; lecture seule |
| `payroll_frequency` | Payroll Frequency | Select — Monthly · Fortnightly · Bimonthly · Weekly · Daily |  |
| `total_working_days` | Working Days | Number | **requis**; lecture seule |
| `leave_without_pay` | Leave Without Pay | Number |  |
| `payment_days` | Payment Days | Number | **requis**; lecture seule |
| `timesheets` | Salary Slip Timesheet | Table → `Salary Slip Timesheet` |  |
| `total_working_hours` | Total Working Hours | Number |  |
| `hour_rate` | Hour Rate | Currency | devise de `currency` |
| `bank_name` | Bank Name | Text |  |
| `bank_account_no` | Bank Account No | Text |  |
| `deduct_tax_for_unsubmitted_tax_exemption_proof` | Deduct Tax For Unsubmitted Tax Exemption Proof | Boolean | défaut `non` |
| `earnings` | Earnings | Table → `Salary Detail` |  |
| `deductions` | Deductions | Table → `Salary Detail` |  |
| `gross_pay` | Gross Pay | Currency | lecture seule; devise de `currency` |
| `net_pay` | Net Pay | Currency | lecture seule; devise de `currency` |
| `rounded_total` | Rounded Total | Currency | lecture seule; devise de `currency` |
| `absent_days` | Absent Days | Number | lecture seule |
| `unmarked_days` | Unmarked days | Number | masqué |
| `currency` | Currency | Link → `Currency` | **requis**; lecture seule |
| `total_deduction` | Total Deduction | Currency | lecture seule; devise de `currency` |
| `total_in_words` | Total in words | Text | lecture seule |
| `base_hour_rate` | Hour Rate (Company Currency) | Currency | devise de `company.default_currency` |
| `base_gross_pay` | Gross Pay (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `exchange_rate` | Exchange Rate | Number | **requis**; masqué; défaut `1.0` |
| `base_total_deduction` | Total Deduction (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_net_pay` | Net Pay (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_rounded_total` | Rounded Total (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_total_in_words` | Total in words (Company Currency) | Text | lecture seule |
| `year_to_date` | Year To Date | Currency | lecture seule; devise de `currency`; — Total salary booked for this employee from the beginning of the year (payroll period or fiscal year) up to the |
| `month_to_date` | Month To Date | Currency | lecture seule; devise de `currency`; — Total salary booked for this employee from the beginning of the month up to the current salary slip's end date |
| `base_year_to_date` | Year To Date(Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_month_to_date` | Month To Date(Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `leave_details` | Leave Details | Table → `Salary Slip Leave` | lecture seule |
| `gross_year_to_date` | Gross Year To Date | Currency | lecture seule; devise de `currency` |
| `base_gross_year_to_date` | Gross Year To Date(Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `ctc` | CTC | Currency | lecture seule; devise de `currency` |
| `income_from_other_sources` | Income from Other Sources | Currency | lecture seule; devise de `currency` |
| `total_earnings` | Total Earnings | Currency | lecture seule; devise de `currency` |
| `non_taxable_earnings` | Non Taxable Earnings | Currency | lecture seule; devise de `currency` |
| `deductions_before_tax_calculation` | Deductions before tax calculation | Currency | lecture seule; devise de `currency` |
| `tax_exemption_declaration` | Tax Exemption Declaration | Currency | lecture seule; devise de `currency` |
| `standard_tax_exemption_amount` | Standard Tax Exemption Amount | Currency | lecture seule; devise de `currency` |
| `annual_taxable_amount` | Annual Taxable Amount | Currency | lecture seule; devise de `currency` |
| `income_tax_deducted_till_date` | Income Tax Deducted Till Date | Currency | lecture seule; devise de `currency` |
| `future_income_tax_deductions` | Future Income Tax | Currency | lecture seule; devise de `currency` |
| `current_month_income_tax` | Current Month Income Tax | Currency | lecture seule; devise de `currency` |
| `total_income_tax` | Total Income Tax | Currency | lecture seule; devise de `currency` |
| `salary_withholding` | Salary Withholding | Link → `Salary Withholding` | lecture seule |
| `salary_withholding_cycle` | Salary Withholding Cycle | Text | lecture seule; masqué |
| `current_payroll_period` | Current Payroll Period | Link → `Payroll Period` | lecture seule; masqué |
| `accrued_benefits` | Accrued Benefits | Table → `Employee Benefit Detail` | lecture seule |
| `employer_contributions` | Employer Contributions | Table → `Salary Detail` |  |

## Salary Slip Leave

*Salary Slip Leave* — `payroll/salary_slip_leave.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `leave_type` | Leave Type | Link → `Leave Type` | colonne de liste; lecture seule |
| `total_allocated_leaves` | Total Allocated Leave(s) | Number | colonne de liste; lecture seule |
| `expired_leaves` | Expired Leave(s) | Number | colonne de liste; lecture seule |
| `used_leaves` | Used Leave(s) | Number | colonne de liste; lecture seule |
| `pending_leaves` | Leave(s) Pending Approval | Number | colonne de liste; lecture seule |
| `available_leaves` | Available Leave(s) | Number | colonne de liste; lecture seule |

## Salary Slip Timesheet

*Salary Slip Timesheet* — `payroll/salary_slip_timesheet.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `time_sheet` | Time Sheet | Link → `Timesheet` | **requis**; colonne de liste |
| `working_hours` | Working Hours | Number | colonne de liste; lecture seule |

## Salary Structure

*Salary Structure* — `payroll/salary_structure.yaml` · soumis

- **Numérotation** : série `SAST-{YYYY}-{#####}`
- **Titre** : `is_active`
- **Icône** : `layout-list`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis** |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `is_active` | Is Active | Select — Yes · No | **requis**; colonne de liste; défaut `Yes` |
| `payroll_frequency` | Payroll Frequency | Select — Monthly · Fortnightly · Bimonthly · Weekly · Daily | défaut `Monthly` |
| `is_default` | Is Default | Select — Yes · No | lecture seule; masqué; défaut `No` |
| `salary_slip_based_on_timesheet` | Salary Slip Based on Timesheet | Boolean | défaut `non` |
| `salary_component` | Salary Component | Link → `Salary Component` | — Salary Component for timesheet based payroll. |
| `hour_rate` | Hour Rate | Currency | devise de `currency` |
| `leave_encashment_amount_per_day` | Leave Encashment Amount Per Day | Currency | devise de `currency` |
| `max_benefits` | Max Benefits (Amount) | Currency | devise de `currency` |
| `earnings` | Earnings | Table → `Salary Detail` |  |
| `deductions` | Deductions | Table → `Salary Detail` |  |
| `employer_contributions` | Employer Contributions | Table → `Salary Detail` |  |
| `total_earning` | Total Earning | Currency | lecture seule; masqué; devise de `currency` |
| `total_deduction` | Total Deduction | Currency | lecture seule; masqué; devise de `currency` |
| `net_pay` | Net Pay | Currency | lecture seule; masqué; devise de `currency` |
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` |  |
| `payment_account` | Payment Account | Link → `Account` |  |
| `currency` | Currency | Link → `Currency` | **requis** |
| `employee_benefits` | Flexible Benefits | Table → `Employee Benefit Detail` | — Enter yearly benefit amounts |

## Salary Structure Assignment

*Salary Structure Assignment* — `payroll/salary_structure_assignment.yaml` · soumis

- **Numérotation** : série `SSA-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `employee_name`
- **Icône** : `user-check`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `designation` | Designation | Link → `Designation` | lecture seule |
| `salary_structure` | Salary Structure | Link → `Salary Structure` | **requis**; colonne de liste |
| `from_date` | From Date | Date | **requis** |
| `company` | Company | Link → `Company` | **requis** |
| `base` | Base | Currency | devise de `currency` |
| `annual_gross_earning` | Annual Gross Earning | Currency | lecture seule; devise de `currency` |
| `ctc` | Total Cost To Company (CTC) | Currency | lecture seule; devise de `currency` |
| `variable` | Variable | Currency | devise de `currency` |
| `income_tax_slab` | Income Tax Slab | Link → `Income Tax Slab` |  |
| `currency` | Currency | Link → `Currency` | **requis**; lecture seule |
| `payroll_payable_account` | Payroll Payable Account | Link → `Account` |  |
| `payroll_cost_centers` | Cost Centers | Table → `Employee Cost Center` |  |
| `grade` | Grade | Link → `Employee Grade` | lecture seule |
| `tax_deducted_till_date` | Tax Deducted Till Date | Currency | devise de `currency` |
| `taxable_earnings_till_date` | Taxable Earnings Till Date | Currency | devise de `currency` |
| `employee_benefits` | Flexible Benefits | Table → `Employee Benefit Detail` |  |
| `max_benefits` | Maximum Benefit Amount | Currency | devise de `currency` |
| `leave_encashment_amount_per_day` | Leave Encashment Amount Per Day | Currency | devise de `currency` |

## Salary Withholding

*Salary Withholding* — `payroll/salary_withholding.yaml` · soumis

- **Numérotation** : série `SW-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `employee_name`
- **Icône** : `hand`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis** |
| `employee_name` | Employee Name | Text | colonne de liste; lecture seule; recopié de `employee.employee_name` |
| `company` | Company | Link → `Company` | colonne de liste; lecture seule |
| `payroll_frequency` | Payroll Frequency | Select — Monthly · Fortnightly · Bimonthly · Weekly · Daily | lecture seule |
| `number_of_withholding_cycles` | Number of Withholding Cycles | Int | **requis** |
| `posting_date` | Posting Date | Date | **requis**; défaut `today` |
| `from_date` | From Date | Date | **requis** |
| `to_date` | To Date | Date | **requis**; lecture seule |
| `date_of_joining` | Date of Joining | Date | lecture seule |
| `relieving_date` | Relieving Date | Date | colonne de liste; lecture seule |
| `reason_for_withholding_salary` | Reason for Withholding Salary | LongText |  |
| `cycles` | Cycles | Table → `Salary Withholding Cycle` | lecture seule |
| `status` | Status | Select — Draft · Withheld · Released · Cancelled | colonne de liste; lecture seule; défaut `Draft` |

## Salary Withholding Cycle

*Salary Withholding Cycle* — `payroll/salary_withholding_cycle.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `from_date` | From Date | Date | **requis**; colonne de liste |
| `to_date` | To Date | Date | **requis**; colonne de liste |
| `is_salary_released` | Is Salary Released | Boolean | colonne de liste; lecture seule |
| `journal_entry` | Journal Entry | Link → `Journal Entry` | colonne de liste; lecture seule |

## Taxable Salary Slab

*Taxable Salary Slab* — `payroll/taxable_salary_slab.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `from_amount` | From Amount | Currency | **requis**; colonne de liste; devise de `parent_currency` |
| `to_amount` | To Amount | Currency | colonne de liste; devise de `parent_currency` |
| `percent_deduction` | Percent Deduction | Percent | **requis**; colonne de liste; défaut `0.0` |
| `condition` | Condition | Code | colonne de liste |
