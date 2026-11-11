# Référence des champs — Projets (`projects`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `projects/` (14 DocTypes). Ne pas éditer à la main : relancer le script.

167 champs au total ; types les plus fréquents : `Link` (32), `Currency` (28), `Text` (21), `Boolean` (15), `Date` (12).

## Activity Cost

*Activity Cost* — `projects/activity_cost.yaml`

- **Titre** : `activity_type`
- **Icône** : `coins`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `activity_type` | Activity Type | Link → `Activity Type` | **requis**; colonne de liste |
| `employee` | Employee | Link → `Employee` |  |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `billing_rate` | Billing Rate | Currency | — per hour |
| `costing_rate` | Costing Rate | Currency | — per hour |
| `title` | title | Text | lecture seule; masqué |

## Activity Type

*Activity Type* — `projects/activity_type.yaml`

- **Titre** : `activity_type`
- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `activity_type` | Activity Type | Text | **requis**; colonne de liste |
| `costing_rate` | Default Costing Rate | Currency |  |
| `billing_rate` | Default Billing Rate | Currency |  |
| `disabled` | Disabled | Boolean | défaut `non` |

## Project

*Project* — `projects/project.yaml`

- **Vues** : kanban, gantt
- **Titre** : `subject`
- **Icône** : `folder-kanban`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `project_name` | Project Name | Text | **requis** |
| `status` | Status | Select — Open · On hold · Completed · Cancelled | défaut `Open` |
| `project_type` | Project Type | Link → `Project Type` | colonne de liste |
| `is_active` | Is Active | Select — Yes · No |  |
| `percent_complete_method` | % Complete Method | Select — Manual · Task Completion · Task Progress · Task Weight | défaut `Task Completion` |
| `percent_complete` | % Completed | Percent | colonne de liste |
| `project_template` | From Template | Link → `Project Template` |  |
| `expected_start_date` | Expected Start date | Date | colonne de liste |
| `expected_end_date` | Expected End date | Date | colonne de liste |
| `priority` | Priority | Select — Low · Medium · High | défaut `Medium` |
| `department` | Department | Link → `Department` |  |
| `customer` | Customer | Link → `Customer` | colonne de liste |
| `sales_order` | Sales Order | Link → `Sales Order` |  |
| `users` | Users | Table → `Project User` | — Project will be accessible on the website to these users |
| `copied_from` | Copied From | Text | lecture seule; masqué |
| `notes` | Notes | TextEditor |  |
| `actual_start_date` | Actual Start date (via Timesheet) | Date | lecture seule |
| `actual_time` | Actual Time in hours (via Timesheet) | Number | lecture seule |
| `actual_end_date` | Actual End date (via Timesheet) | Date | lecture seule |
| `estimated_costing` | Estimated Cost | Currency | colonne de liste; devise de `company.default_currency` |
| `total_costing_amount` | Total Costing Amount (via Timesheet) | Currency | lecture seule; devise de `company.default_currency` |
| `total_purchase_cost` | Total Purchase Cost (via Purchase Invoice) | Currency | lecture seule; devise de `company.default_currency` |
| `company` | Company | Link → `Company` | **requis** |
| `total_sales_amount` | Total Sales amount (via Sales Order) | Currency | lecture seule; devise de `company.default_currency` |
| `total_billable_amount` | Total Billable amount (via Timesheet) | Currency | lecture seule; devise de `company.default_currency` |
| `total_billed_amount` | Total Billed amount (via Sales Invoice) | Currency | lecture seule; devise de `company.default_currency` |
| `total_consumed_material_cost` | Total Consumed Material Cost | Currency | lecture seule; devise de `company.default_currency` |
| `cost_center` | Default Cost Center | Link → `Cost Center` |  |
| `gross_margin` | Gross Margin | Currency | lecture seule; devise de `company.default_currency` |
| `per_gross_margin` | Gross Margin % | Percent | lecture seule |
| `collect_progress` | Email users for progress updates | Boolean | défaut `non`; — Emails the users in Portal users on the schedule below, asking for a status update. Needs email accounts set u |
| `holiday_list` | Holiday List | Link → `Holiday List` |  |
| `frequency` | Frequency to collect progress | Select — Hourly · Twice Daily · Daily · Weekly |  |
| `from_time` | From time | Time |  |
| `to_time` | To time | Time |  |
| `first_email` | First email | Time |  |
| `second_email` | Second email | Time |  |
| `daily_time_to_send` | Daily time to send | Time |  |
| `day_to_send` | Day to Send | Select — Monday · Tuesday · Wednesday · Thursday · Friday · Saturday · Sunday |  |
| `weekly_time_to_send` | Weekly time to send | Time |  |
| `message` | Message | LongText | — Message will be sent to the users to get their status on the Project |
| `naming_series` | Series | Select — PROJ-.#### | **requis** |
| `subject` | Subject | Text |  |

## Project Template

*Project Template* — `projects/project_template.yaml`

- **Titre** : `project_type`
- **Icône** : `folder`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `project_type` | Project Type | Link → `Project Type` | colonne de liste |
| `tasks` | Tasks | Table → `Project Template Task` |  |
| `disabled` | Disabled | Boolean | défaut `non` |

## Project Template Task

*Project Template Task* — `projects/project_template_task.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `task` | Task | Link → `Task` | **requis**; colonne de liste |
| `subject` | Subject | Text | colonne de liste; lecture seule |

## Project Type

*Project Type* — `projects/project_type.yaml`

- **Titre** : `project_type`
- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `project_type` | Project Type | Text | **requis**; colonne de liste |
| `description` | Description | LongText |  |

## Project Update

*Project Update* — `projects/project_update.yaml` · soumis

- **Numérotation** : série `PU-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `project`
- **Icône** : `message-square`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Text | masqué |
| `project` | Project | Link → `Project` | **requis**; colonne de liste |
| `sent` | Sent | Boolean | lecture seule |
| `date` | Date | Date | lecture seule |
| `time` | Time | Time | lecture seule |
| `users` | Users | Table → `Project User` |  |

## Project User

*Project User* — `projects/project_user.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `user` | User | Text | **requis**; colonne de liste |
| `email` | Email | Text | lecture seule |
| `image` | Image | Text | lecture seule; masqué |
| `full_name` | Full Name | Text | colonne de liste; lecture seule |
| `welcome_email_sent` | Welcome email sent | Boolean | défaut `non` |
| `view_attachments` | View attachments | Boolean | colonne de liste; défaut `non` |
| `hide_timesheets` | Hide timesheets | Boolean | défaut `non` |
| `project_status` | Project Status | TextEditor |  |

## Projects Settings

*Projects Settings* — `projects/projects_settings.yaml` · document unique

- **Icône** : `settings`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `ignore_user_time_overlap` | Ignore User Time Overlap | Boolean | défaut `non` |
| `ignore_employee_time_overlap` | Ignore Employee Time Overlap | Boolean | défaut `non` |
| `fetch_timesheet_in_sales_invoice` | Fetch Timesheet in Sales Invoice | Boolean | défaut `non`; — Enabling the check box will fetch timesheet on select of a Project in Sales Invoice |

## Task

*Task* — `projects/task.yaml`

- **Vues** : tree (parent `parent_task`)
- **Titre** : `subject`
- **Icône** : `list-checks`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `subject` | Subject | Text | **requis** |
| `project` | Project | Link → `Project` | colonne de liste |
| `issue` | Issue | Link → `Issue` |  |
| `type` | Type | Link → `Task Type` |  |
| `is_group` | Is Group | Boolean | colonne de liste; défaut `non` |
| `status` | Status | Select — Open · Working · Pending Review · Overdue · Template · Completed · Cancelled | colonne de liste |
| `priority` | Priority | Select — Low · Medium · High · Urgent | colonne de liste |
| `color` | Color | Color |  |
| `parent_task` | Parent Task | Link → `Task` |  |
| `exp_start_date` | Expected Start Date | Datetime |  |
| `expected_time` | Expected Time (in hours) | Number | défaut `0.0` |
| `task_weight` | Weight | Number |  |
| `exp_end_date` | Expected End Date | Datetime |  |
| `progress` | % Progress | Percent |  |
| `is_milestone` | Is Milestone | Boolean | colonne de liste; défaut `non` |
| `description` | Task Description | TextEditor |  |
| `depends_on` | Dependent Tasks | Table → `Task Depends On` |  |
| `depends_on_tasks` | Depends on Tasks | Code | lecture seule; masqué |
| `act_start_date` | Actual Start Date (via Timesheet) | Date | lecture seule |
| `actual_time` | Actual Time in Hours (via Timesheet) | Number | lecture seule |
| `act_end_date` | Actual End Date (via Timesheet) | Date | lecture seule |
| `total_costing_amount` | Total Costing Amount (via Timesheet) | Currency | lecture seule; devise de `company.default_currency` |
| `total_billing_amount` | Total Billable Amount (via Timesheet) | Currency | lecture seule; devise de `company.default_currency` |
| `review_date` | Review Date | Date |  |
| `closing_date` | Closing Date | Date |  |
| `department` | Department | Link → `Department` |  |
| `company` | Company | Link → `Company` |  |
| `lft` | lft | Int | lecture seule; masqué |
| `rgt` | rgt | Int | lecture seule; masqué |
| `old_parent` | Old Parent | Text | lecture seule; masqué |
| `completed_by` | Completed By | Text |  |
| `is_template` | Is Template | Boolean | défaut `non` |
| `start` | Begin On (Days) | Int |  |
| `duration` | Duration (Days) | Int |  |
| `completed_on` | Completed On | Date |  |
| `template_task` | Template Task | Text | masqué |

## Task Depends On

*Task Depends On* — `projects/task_depends_on.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `task` | Task | Link → `Task` | colonne de liste |
| `subject` | Subject | LongText | colonne de liste; lecture seule |
| `project` | Project | LongText | lecture seule |

## Task Type

*Task Type* — `projects/task_type.yaml`

- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `weight` | Weight | Number |  |
| `description` | Description | LongText |  |

## Timesheet

*Timesheet* — `projects/timesheet.yaml` · soumis

- **Numérotation** : série `TIME-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `status`
- **Icône** : `clock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text | masqué |
| `naming_series` | Series | Select — TS-.YYYY.- | **requis** |
| `company` | Company | Link → `Company` |  |
| `sales_invoice` | Sales Invoice | Link → `Sales Invoice` | lecture seule |
| `status` | Status | Select — Draft · Submitted · Partially Billed · Billed · Payslip · Completed · Cancelled | lecture seule; défaut `Draft` |
| `employee` | Employee | Link → `Employee` |  |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `user` | User | Text | lecture seule |
| `start_date` | Start Date | Date | colonne de liste; lecture seule |
| `end_date` | End Date | Date | lecture seule |
| `time_logs` | Time Sheets | Table → `Timesheet Detail` |  |
| `total_hours` | Total Working Hours | Number | lecture seule |
| `total_billable_hours` | Total Billable Hours | Number | lecture seule |
| `total_billed_hours` | Total Billed Hours | Number | lecture seule |
| `total_costing_amount` | Total Costing Amount | Currency | lecture seule; devise de `currency` |
| `total_billable_amount` | Total Billable Amount | Currency | lecture seule; devise de `currency` |
| `total_billed_amount` | Total Billed Amount | Currency | lecture seule; devise de `currency` |
| `per_billed` | % Amount Billed | Percent | colonne de liste; lecture seule |
| `note` | Note | TextEditor |  |
| `parent_project` | Project | Link → `Project` |  |
| `customer` | Customer | Link → `Customer` |  |
| `currency` | Currency | Link → `Currency` |  |
| `base_total_costing_amount` | Base Total Costing Amount | Currency | lecture seule; devise de `company.default_currency` |
| `base_total_billable_amount` | Base Total Billable Amount | Currency | lecture seule; devise de `company.default_currency` |
| `base_total_billed_amount` | Base Total Billed Amount | Currency | lecture seule; devise de `company.default_currency` |
| `exchange_rate` | Exchange Rate | Number | défaut `1.0` |

## Timesheet Detail

*Timesheet Detail* — `projects/timesheet_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `activity_type` | Activity Type | Link → `Activity Type` | colonne de liste |
| `from_time` | From Time | Datetime | colonne de liste |
| `expected_hours` | Expected Hrs | Number |  |
| `hours` | Hrs | Number | colonne de liste |
| `to_time` | To Time | Datetime |  |
| `completed` | Completed | Boolean | défaut `non` |
| `project` | Project | Link → `Project` | colonne de liste |
| `task` | Task | Link → `Task` |  |
| `billing_hours` | Billing Hours | Number |  |
| `billing_rate` | Billing Rate | Currency | devise de `parent_currency` |
| `billing_amount` | Billing Amount | Currency | lecture seule; devise de `parent_currency` |
| `costing_rate` | Costing Rate | Currency | devise de `parent_currency` |
| `costing_amount` | Costing Amount | Currency | lecture seule; devise de `parent_currency` |
| `sales_invoice` | Sales Invoice | Link → `Sales Invoice` | lecture seule |
| `is_billable` | Is Billable | Boolean | colonne de liste; défaut `non` |
| `project_name` | Project Name | Text | lecture seule; recopié de `project.project_name` |
| `description` | Description | LongText |  |
| `base_billing_rate` | Billing Rate | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_billing_amount` | Billing Amount | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_costing_rate` | Costing Rate | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_costing_amount` | Costing Amount | Currency | lecture seule; devise de `parent_company.default_currency` |
