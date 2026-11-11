# Référence des champs — Immobilisations (`assets`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `assets/` (25 DocTypes). Ne pas éditer à la main : relancer le script.

277 champs au total ; types les plus fréquents : `Link` (83), `Text` (48), `Currency` (36), `Select` (20), `Boolean` (20).

## Asset

*Asset* — `assets/asset.yaml` · soumis

- **Numérotation** : série `ASSE-{YYYY}-{#####}`
- **Titre** : `item_code`
- **Icône** : `building`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — ACC-ASS-.YYYY.- |  |
| `asset_name` | Asset Name | Text | **requis**; colonne de liste |
| `item_code` | Item Code | Link → `Item` | **requis** |
| `asset_category` | Asset Category | Link → `Asset Category` | colonne de liste; lecture seule |
| `asset_owner` | Asset Owner | Select — Company · Supplier · Customer | défaut `Company` |
| `asset_owner_company` | Asset Owner Company | Link → `Company` |  |
| `supplier` | Supplier | Link → `Supplier` |  |
| `customer` | Customer | Link → `Customer` |  |
| `image` | Image | Image | masqué |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `location` | Location | Link → `Location` | **requis**; colonne de liste |
| `custodian` | Custodian | Link → `Employee` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `department` | Department | Link → `Department` |  |
| `purchase_date` | Purchase Date | Date | **requis** |
| `disposal_date` | Disposal Date | Date | lecture seule |
| `journal_entry_for_scrap` | Journal Entry for Scrap | Link → `Journal Entry` | lecture seule |
| `available_for_use_date` | Available for Use Date | Date |  |
| `calculate_depreciation` | Calculate Depreciation | Boolean | défaut `non` |
| `opening_accumulated_depreciation` | Opening Accumulated Depreciation | Currency | devise de `company.default_currency` |
| `finance_books` | Finance Books | Table → `Asset Finance Book` |  |
| `depreciation_method` | Depreciation Method | Select — Straight Line · Double Declining Balance · Written Down Value · Manual |  |
| `value_after_depreciation` | Value After Depreciation | Currency | lecture seule; masqué; devise de `company.default_currency` |
| `total_number_of_depreciations` | Total Number of Depreciations | Int |  |
| `frequency_of_depreciation` | Frequency of Depreciation (Months) | Int |  |
| `next_depreciation_date` | Next Depreciation Date | Date | masqué |
| `policy_number` | Policy number | Text |  |
| `insurer` | Insurer | Text |  |
| `insured_value` | Insured value | Text |  |
| `insurance_start_date` | Insurance Start Date | Date |  |
| `insurance_end_date` | Insurance End Date | Date |  |
| `comprehensive_insurance` | Comprehensive Insurance | Text |  |
| `maintenance_required` | Maintenance Required | Boolean | défaut `non` |
| `status` | Status | Select — Draft · Submitted · Cancelled · Partially Depreciated · Fully Depreciated · Sold · Scrapped · In Maintenance · Out of Order · Issue · Receipt · Capitalized · Work In Progress | colonne de liste; lecture seule; défaut `Draft` |
| `booked_fixed_asset` | Booked Fixed Asset | Boolean | lecture seule; masqué |
| `purchase_receipt` | Purchase Receipt | Link → `Purchase Receipt` |  |
| `purchase_invoice` | Purchase Invoice | Link → `Purchase Invoice` |  |
| `default_finance_book` | Default Finance Book | Link → `Finance Book` | lecture seule; masqué |
| `split_from` | Split From | Link → `Asset` | lecture seule |
| `asset_quantity` | Asset Quantity | Int | défaut `1` |
| `depr_entry_posting_status` | Depreciation Entry Posting Status | Select — Successful · Failed | lecture seule; masqué |
| `is_fully_depreciated` | Is Fully Depreciated | Boolean | défaut `non` |
| `total_asset_cost` | Total Asset Cost | Currency | lecture seule; devise de `company.default_currency` |
| `additional_asset_cost` | Additional Asset Cost | Currency | lecture seule; devise de `company.default_currency` |
| `value_adjustment_amount` | Value Adjustment Amount | Currency | lecture seule; devise de `company.default_currency`; — Net change from Asset Value Adjustments |
| `purchase_amount` | Purchase Amount | Currency | lecture seule; masqué; devise de `company.default_currency` |
| `opening_number_of_booked_depreciations` | Opening Number of Booked Depreciations | Int |  |
| `purchase_receipt_item` | Purchase Receipt Item | Text | masqué |
| `purchase_invoice_item` | Purchase Invoice Item | Text | masqué |
| `net_purchase_amount` | Net Purchase Amount | Currency | devise de `company.default_currency` |
| `asset_type` | Asset Type | Select — Existing Asset · Composite Asset · Composite Component |  |
| `item_name` | Item Name | Text | lecture seule; masqué; recopié de `item_code.item_name` |

## Asset Activity

*Asset Activity* — `assets/asset_activity.yaml`

- **Titre** : `asset`
- **Icône** : `activity`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `asset` | Asset | Link → `Asset` | **requis**; colonne de liste; lecture seule |
| `subject` | Subject | TextEditor | **requis**; colonne de liste; lecture seule |
| `date` | Date | Datetime | **requis**; colonne de liste; lecture seule |
| `user` | User | Text | **requis**; colonne de liste; lecture seule |

## Asset Capitalization

*Asset Capitalization* — `assets/asset_capitalization.yaml` · soumis

- **Numérotation** : série `AC-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `target_asset`
- **Icône** : `trending-up`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text | masqué |
| `target_item_code` | Target Item Code | Link → `Item` | lecture seule; masqué |
| `target_asset` | Target Asset | Link → `Asset` | **requis** |
| `target_asset_name` | Asset Name | Text | lecture seule |
| `company` | Company | Link → `Company` | **requis** |
| `posting_date` | Posting Date | Date | **requis**; colonne de liste; défaut `today` |
| `posting_time` | Posting Time | Time | **requis** |
| `set_posting_time` | Edit Posting Date and Time | Boolean | défaut `non` |
| `naming_series` | Series | Select — ACC-ASC-.YYYY.- | **requis** |
| `stock_items` | Stock Items | Table → `Asset Capitalization Stock Item` |  |
| `asset_items` | Assets | Table → `Asset Capitalization Asset Item` |  |
| `stock_items_total` | Consumed Stock Total Value | Currency | lecture seule; devise de `company.default_currency` |
| `asset_items_total` | Consumed Asset Total Value | Currency | lecture seule; devise de `company.default_currency` |
| `finance_book` | Finance Book | Link → `Finance Book` |  |
| `service_items` | Services | Table → `Asset Capitalization Service Item` |  |
| `service_items_total` | Service Expense Total Amount | Currency | lecture seule; devise de `company.default_currency` |
| `total_value` | Total Value | Currency | lecture seule; devise de `company.default_currency` |
| `target_incoming_rate` | Target Incoming Rate | Currency | lecture seule; devise de `company.default_currency` |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |
| `target_fixed_asset_account` | Target Fixed Asset Account | Link → `Account` | lecture seule |

## Asset Capitalization Asset Item

*Asset Capitalization Asset Item* — `assets/asset_capitalization_asset_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `asset` | Asset | Link → `Asset` | **requis**; colonne de liste |
| `asset_name` | Asset Name | Text | colonne de liste; lecture seule |
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste; lecture seule |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `asset_value` | Asset Value | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `fixed_asset_account` | Fixed Asset Account | Link → `Account` | lecture seule |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |
| `finance_book` | Finance Book | Link → `Finance Book` |  |
| `current_asset_value` | Current Asset Value | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |

## Asset Capitalization Service Item

*Asset Capitalization Service Item* — `assets/asset_capitalization_service_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | colonne de liste |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `expense_account` | Expense Account | Link → `Account` | **requis**; colonne de liste |
| `qty` | Qty | Decimal | colonne de liste; défaut `1.000` |
| `uom` | UOM | Link → `UOM` | colonne de liste |
| `rate` | Rate | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `amount` | Amount | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `cost_center` | Cost Center | Link → `Cost Center` |  |

## Asset Capitalization Stock Item

*Asset Capitalization Stock Item* — `assets/asset_capitalization_stock_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `warehouse` | Warehouse | Link → `Warehouse` | **requis**; colonne de liste |
| `batch_no` | Batch No | Link → `Batch` |  |
| `stock_qty` | Quantity | Decimal | colonne de liste |
| `stock_uom` | Stock UOM | Link → `UOM` | **requis**; colonne de liste; lecture seule |
| `valuation_rate` | Valuation Rate | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `amount` | Amount | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `serial_no` | Serial No | LongText |  |
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `actual_qty` | Actual Qty in Warehouse | Decimal | lecture seule |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `serial_and_batch_bundle` | Serial and Batch Bundle | Link → `Serial and Batch Bundle` |  |
| `use_serial_batch_fields` | Use Serial No / Batch Fields | Boolean | défaut `non` |
| `purchase_receipt_item` | Purchase Receipt Item | Text | masqué |

## Asset Category

*Asset Category* — `assets/asset_category.yaml`

- **Titre** : `asset_category_name`
- **Icône** : `folder`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `asset_category_name` | Asset Category Name | Text | **requis**; colonne de liste |
| `finance_books` | Finance Books | Table → `Asset Finance Book` |  |
| `accounts` | Accounts | Table → `Asset Category Account` |  |
| `enable_cwip_accounting` | Enable Capital Work in Progress Accounting | Boolean | défaut `non` |
| `non_depreciable_category` | Non Depreciable Category | Boolean | défaut `non` |

## Asset Category Account

*Asset Category Account* — `assets/asset_category_account.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company_name` | Company | Link → `Company` | **requis**; colonne de liste |
| `fixed_asset_account` | Fixed Asset Account | Link → `Account` | **requis**; colonne de liste |
| `accumulated_depreciation_account` | Accumulated Depreciation Account | Link → `Account` | colonne de liste |
| `depreciation_expense_account` | Depreciation Expense Account | Link → `Account` | colonne de liste |
| `capital_work_in_progress_account` | Capital Work In Progress Account | Link → `Account` | colonne de liste |

## Asset Depreciation Schedule

*Asset Depreciation Schedule* — `assets/asset_depreciation_schedule.yaml` · soumis

- **Numérotation** : série `ADS-{YYYY}-{#####}`
- **Titre** : `asset`
- **Icône** : `trending-down`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `asset` | Asset | Link → `Asset` | **requis**; colonne de liste |
| `naming_series` | Naming Series | Select — ACC-ADS-.YYYY.- |  |
| `finance_book` | Finance Book | Link → `Finance Book` |  |
| `depreciation_method` | Depreciation Method | Select — Straight Line · Double Declining Balance · Written Down Value · Manual | lecture seule |
| `rate_of_depreciation` | Rate of Depreciation | Percent | lecture seule; — In Percentage |
| `total_number_of_depreciations` | Total Number of Depreciations | Int | lecture seule |
| `depreciation_schedule` | Depreciation Schedule | Table → `Depreciation Schedule` |  |
| `notes` | Notes | TextEditor | lecture seule |
| `status` | Status | Select — Draft · Active · Cancelled | lecture seule; masqué |
| `frequency_of_depreciation` | Frequency of Depreciation (Months) | Int | lecture seule |
| `expected_value_after_useful_life` | Expected Value After Useful Life | Currency | lecture seule; devise de `company.default_currency` |
| `finance_book_id` | Finance Book Id | Int | lecture seule; masqué |
| `opening_accumulated_depreciation` | Opening Accumulated Depreciation | Currency | lecture seule; masqué; devise de `company.default_currency` |
| `opening_number_of_booked_depreciations` | Opening Number of Booked Depreciations | Int | lecture seule; masqué |
| `daily_prorata_based` | Depreciate based on daily pro-rata | Boolean | lecture seule |
| `shift_based` | Depreciate based on shifts | Boolean | lecture seule |
| `company` | Company | Link → `Company` | lecture seule |
| `value_after_depreciation` | Value After Depreciation | Currency | lecture seule; devise de `company.default_currency` |
| `net_purchase_amount` | Net Purchase Amount | Currency | lecture seule; masqué; devise de `company.default_currency` |

## Asset Finance Book

*Asset Finance Book* — `assets/asset_finance_book.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `finance_book` | Finance Book | Link → `Finance Book` | colonne de liste |
| `depreciation_method` | Depreciation Method | Select — Straight Line · Double Declining Balance · Written Down Value · Manual | **requis**; colonne de liste |
| `total_number_of_depreciations` | Total Number of Depreciations | Int | **requis**; colonne de liste |
| `frequency_of_depreciation` | Frequency of Depreciation (Months) | Int | **requis**; colonne de liste |
| `depreciation_start_date` | Depreciation Posting Date | Date | colonne de liste |
| `expected_value_after_useful_life` | Salvage Value | Currency | — Expected Value After Useful Life |
| `value_after_depreciation` | Value After Depreciation | Currency | lecture seule |
| `value_adjustment_amount` | Value Adjustment Amount | Currency | lecture seule; — Net change from Asset Value Adjustments |
| `rate_of_depreciation` | Rate of Depreciation (%) | Percent |  |
| `is_rate_of_depreciation_entered` | Is Rate of Depreciation Entered | Boolean | lecture seule; masqué |
| `salvage_value_percentage` | Salvage Value Percentage | Percent |  |
| `daily_prorata_based` | Depreciate based on daily pro-rata | Boolean | défaut `non` |
| `shift_based` | Depreciate based on shifts | Boolean | défaut `non` |
| `total_number_of_booked_depreciations` | Total Number of Booked Depreciations  | Int | lecture seule |
| `increase_in_asset_life` | Increase In Asset Life (Months) | Int | lecture seule; — via Asset Repair |

## Asset Maintenance

*Asset Maintenance* — `assets/asset_maintenance.yaml`

- **Titre** : `item_code`
- **Icône** : `wrench`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `asset_name` | Asset Name | Link → `Asset` | **requis**; colonne de liste |
| `asset_category` | Asset Category | Link → `Asset Category` | lecture seule |
| `item_code` | Item Code | Text | lecture seule |
| `item_name` | Item Name | Text | lecture seule |
| `company` | Company | Link → `Company` | **requis** |
| `maintenance_team` | Maintenance Team | Link → `Asset Maintenance Team` | **requis**; colonne de liste |
| `maintenance_manager` | Maintenance Manager | Text | lecture seule; masqué |
| `maintenance_manager_name` | Maintenance Manager Name | Text | lecture seule |
| `asset_maintenance_tasks` | Maintenance Tasks | Table → `Asset Maintenance Task` |  |

## Asset Maintenance Log

*Asset Maintenance Log* — `assets/asset_maintenance_log.yaml` · soumis

- **Numérotation** : série `AML-{YYYY}-{#####}`
- **Titre** : `item_code`
- **Icône** : `file-clock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `asset_maintenance` | Asset Maintenance | Link → `Asset Maintenance` |  |
| `naming_series` | Series | Select — ACC-AML-.YYYY.- | **requis** |
| `asset_name` | Asset Name | Text | lecture seule |
| `item_code` | Item Code | Text | lecture seule |
| `item_name` | Item Name | Text | lecture seule |
| `task` | Task | Text | — Référence de la ligne d'origine (Asset Maintenance Task). |
| `maintenance_type` | Maintenance Type | Text | lecture seule |
| `periodicity` | Periodicity | Text | lecture seule |
| `assign_to_name` | Assign To | Text | lecture seule |
| `due_date` | Due Date | Date | colonne de liste; lecture seule |
| `completion_date` | Completion Date | Date | colonne de liste |
| `maintenance_status` | Maintenance Status | Select — Planned · Completed · Cancelled · Overdue | **requis** |
| `has_certificate` | Has Certificate  | Boolean | défaut `non` |
| `certificate_attachement` | Certificate | Attach |  |
| `description` | Description | Text | lecture seule |
| `actions_performed` | Actions performed | TextEditor |  |
| `task_name` | Task Name | Text | lecture seule |
| `task_assignee_email` | Task Assignee Email | Text | lecture seule |

## Asset Maintenance Task

*Asset Maintenance Task* — `assets/asset_maintenance_task.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `maintenance_task` | Maintenance Task | Text | **requis**; colonne de liste |
| `maintenance_type` | Maintenance Type | Select — Preventive Maintenance · Calibration |  |
| `maintenance_status` | Maintenance Status | Select — Planned · Overdue · Cancelled | **requis**; colonne de liste |
| `start_date` | Start Date | Date | **requis** |
| `periodicity` | Periodicity | Select — Daily · Weekly · Monthly · Quarterly · Half-yearly · Yearly · 2 Yearly · 3 Yearly | **requis**; colonne de liste |
| `end_date` | End Date | Date |  |
| `certificate_required` | Certificate Required | Boolean | défaut `non` |
| `assign_to` | Assign To | Text | colonne de liste |
| `assign_to_name` | Assign to Name | Text | lecture seule |
| `next_due_date` | Next Due Date | Date | colonne de liste |
| `last_completion_date` | Last Completion Date | Date | colonne de liste |
| `description` | Description | TextEditor |  |

## Asset Maintenance Team

*Asset Maintenance Team* — `assets/asset_maintenance_team.yaml`

- **Titre** : `maintenance_team_name`
- **Icône** : `user-group`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `maintenance_team_name` | Maintenance Team Name | Text | **requis**; colonne de liste |
| `maintenance_manager` | Maintenance Manager | Text |  |
| `maintenance_manager_name` | Maintenance Manager Name | Text | lecture seule |
| `company` | Company | Link → `Company` | **requis** |
| `maintenance_team_members` | Maintenance Team Members | Table → `Maintenance Team Member` |  |

## Asset Movement

*Asset Movement* — `assets/asset_movement.yaml` · soumis

- **Numérotation** : série `AM-{YYYY}-{#####}`
- **Titre** : `company`
- **Icône** : `move`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `purpose` | Purpose | Select — Issue · Receipt · Transfer · Transfer and Issue | **requis**; colonne de liste |
| `transaction_date` | Transaction Date | Datetime | **requis**; colonne de liste |
| `reference_doctype` | Reference Document Type | Text |  |
| `reference_name` | Reference Document Name | DynamicLink → `reference_doctype` |  |
| `assets` | Assets | Table → `Asset Movement Item` |  |

## Asset Movement Item

*Asset Movement Item* — `assets/asset_movement_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `asset` | Asset | Link → `Asset` | **requis**; colonne de liste |
| `asset_name` | Asset Name | Text | lecture seule |
| `source_location` | Source Location | Link → `Location` | colonne de liste |
| `target_location` | Target Location | Link → `Location` | colonne de liste |
| `from_employee` | From Employee | Link → `Employee` | colonne de liste |
| `to_employee` | To Employee | Link → `Employee` | colonne de liste |
| `company` | Company | Link → `Company` | lecture seule; masqué |

## Asset Repair

*Asset Repair* — `assets/asset_repair.yaml` · soumis

- **Numérotation** : série `AR-{YYYY}-{#####}`
- **Titre** : `asset_name`
- **Icône** : `wrench`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — ACC-ASR-.YYYY.- | **requis** |
| `failure_date` | Failure Date | Datetime | **requis** |
| `completion_date` | Completion Date | Datetime |  |
| `repair_status` | Repair Status | Select — Pending · Completed · Cancelled | défaut `Pending` |
| `description` | Error Description | LongText |  |
| `actions_performed` | Actions performed | LongText |  |
| `downtime` | Downtime | Text | colonne de liste; lecture seule |
| `repair_cost` | Repair Cost | Currency | lecture seule; devise de `company.default_currency` |
| `asset` | Asset | Link → `Asset` | **requis**; colonne de liste |
| `asset_name` | Asset Name | Text | lecture seule |
| `capitalize_repair_cost` | Capitalize Repair Cost | Boolean | défaut `non` |
| `stock_items` | Stock Items | Table → `Asset Repair Consumed Item` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |
| `total_repair_cost` | Total Repair Cost | Currency | lecture seule; devise de `company.default_currency` |
| `increase_in_asset_life` | Increase In Asset Life(Months) | Int |  |
| `asset_value_updated` | Asset Value Updated | Boolean | lecture seule; masqué |
| `company` | Company | Link → `Company` |  |
| `invoices` | Repair Purchase Invoices | Table → `Asset Repair Purchase Invoice` |  |
| `consumed_items_cost` | Consumed Items Cost | Currency | devise de `company.default_currency` |

## Asset Repair Consumed Item

*Asset Repair Consumed Item* — `assets/asset_repair_consumed_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `valuation_rate` | Valuation Rate | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `consumed_quantity` | Consumed Quantity | Text | colonne de liste |
| `total_value` | Total Value | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |
| `serial_no` | Serial No | LongText | masqué |
| `item_code` | Item | Link → `Item` | **requis**; colonne de liste |
| `serial_and_batch_bundle` | Serial and Batch Bundle | Link → `Serial and Batch Bundle` |  |
| `warehouse` | Warehouse | Link → `Warehouse` | **requis**; colonne de liste |

## Asset Repair Purchase Invoice

*Asset Repair Purchase Invoice* — `assets/asset_repair_purchase_invoice.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `purchase_invoice` | Purchase Invoice | Link → `Purchase Invoice` | colonne de liste |
| `expense_account` | Expense Account | Link → `Account` | **requis**; colonne de liste |
| `repair_cost` | Repair Cost | Currency | **requis**; colonne de liste; devise de `parent_company.default_currency` |

## Asset Shift Allocation

*Asset Shift Allocation* — `assets/asset_shift_allocation.yaml` · soumis

- **Numérotation** : série `ASA-{YYYY}-{#####}`
- **Titre** : `asset`
- **Icône** : `clipboard-clock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `asset` | Asset | Link → `Asset` | **requis**; colonne de liste |
| `finance_book` | Finance Book | Link → `Finance Book` |  |
| `previous_depreciation_schedule` | Previous Depreciation Schedule | Link → `Asset Depreciation Schedule` | lecture seule; — The depreciation schedule this allocation replaced, restored when the allocation is cancelled |
| `depreciation_schedule` | Depreciation Schedule | Table → `Depreciation Schedule` | lecture seule |
| `naming_series` | Naming Series | Select — ACC-ASA-.YYYY.- | **requis** |

## Asset Shift Factor

*Asset Shift Factor* — `assets/asset_shift_factor.yaml`

- **Titre** : `shift_name`
- **Icône** : `gauge`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `shift_name` | Shift Name | Text | **requis**; colonne de liste |
| `shift_factor` | Shift Factor | Number | **requis**; colonne de liste |
| `default` | Default | Boolean | colonne de liste; défaut `non` |

## Asset Value Adjustment

*Asset Value Adjustment* — `assets/asset_value_adjustment.yaml` · soumis

- **Numérotation** : série `AVA-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `finance_book`
- **Icône** : `sliders-horizontal`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` |  |
| `asset` | Asset | Link → `Asset` | **requis** |
| `asset_category` | Asset Category | Text | lecture seule |
| `finance_book` | Finance Book | Link → `Finance Book` | colonne de liste |
| `journal_entry` | Journal Entry | Link → `Journal Entry` | lecture seule |
| `date` | Date | Date | **requis** |
| `current_asset_value` | Current Asset Value | Currency | **requis**; colonne de liste; lecture seule; devise de `company.default_currency` |
| `new_asset_value` | New Asset Value | Currency | **requis**; colonne de liste; devise de `company.default_currency` |
| `difference_amount` | Difference Amount | Currency | lecture seule; devise de `company.default_currency` |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `difference_account` | Difference Account | Link → `Account` | **requis** |

## Depreciation Schedule

*Depreciation Schedule* — `assets/depreciation_schedule.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `schedule_date` | Schedule Date | Date | **requis**; colonne de liste |
| `depreciation_amount` | Depreciation Amount | Currency | **requis**; colonne de liste |
| `accumulated_depreciation_amount` | Accumulated Depreciation Amount | Currency | colonne de liste; lecture seule |
| `journal_entry` | Journal Entry | Link → `Journal Entry` | colonne de liste; lecture seule |
| `shift` | Shift | Link → `Asset Shift Factor` |  |

## Location

*Location* — `assets/location.yaml`

- **Vues** : tree (parent `parent_location`)
- **Titre** : `location_name`
- **Icône** : `map-pin`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `location_name` | Location Name | Text | **requis**; colonne de liste |
| `parent_location` | Parent Location | Link → `Location` |  |
| `is_container` | Is Container | Boolean | défaut `non`; — Check if it is a hydroponic unit |
| `is_group` | Is Group | Boolean | colonne de liste; défaut `non` |
| `latitude` | Latitude | Number |  |
| `longitude` | Longitude | Number |  |
| `area` | Area | Number | lecture seule |
| `area_uom` | Area UOM | Link → `UOM` |  |
| `lft` | lft | Int | lecture seule; masqué |
| `rgt` | rgt | Int | lecture seule; masqué |
| `old_parent` | Old Parent | Text | lecture seule; masqué |

## Maintenance Team Member

*Maintenance Team Member* — `assets/maintenance_team_member.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `team_member` | Team Member | Text | **requis**; colonne de liste |
| `full_name` | Full Name | Text | colonne de liste; lecture seule |
