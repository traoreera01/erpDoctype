# Référence des champs — Maintenance (`maintenance`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `maintenance/` (5 DocTypes). Ne pas éditer à la main : relancer le script.

65 champs au total ; types les plus fréquents : `Link` (22), `Text` (13), `Select` (8), `Date` (6), `LongText` (6).

## Maintenance Schedule

*Maintenance Schedule* — `maintenance/maintenance_schedule.yaml` · soumis

- **Numérotation** : série `MS-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `customer_name`
- **Icône** : `calendar-check`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — MAT-MSH-.YYYY.- | **requis** |
| `customer` | Customer | Link → `Customer` |  |
| `status` | Status | Select — Draft · Submitted · Cancelled | **requis**; lecture seule; défaut `Draft` |
| `transaction_date` | Transaction Date | Date | **requis** |
| `items` | Items | Table → `Maintenance Schedule Item` |  |
| `schedules` | Schedules | Table → `Maintenance Schedule Detail` |  |
| `customer_name` | Customer Name | Text | colonne de liste; lecture seule; recopié de `customer.customer_name` |
| `contact_person` | Contact Person | Link → `Contact` |  |
| `contact_mobile` | Mobile No | Text | lecture seule; masqué |
| `contact_email` | Contact Email | Text | lecture seule; masqué |
| `contact_display` | Contact | LongText | lecture seule; masqué |
| `customer_address` | Customer Address | Link → `Address` |  |
| `address_display` | Address | TextEditor | lecture seule; masqué |
| `territory` | Territory | Link → `Territory` |  |
| `customer_group` | Customer Group | Link → `Customer Group` |  |
| `company` | Company | Link → `Company` | **requis** |

## Maintenance Schedule Detail

*Maintenance Schedule Detail* — `maintenance/maintenance_schedule_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | colonne de liste; lecture seule |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `scheduled_date` | Scheduled Date | Date | **requis**; colonne de liste |
| `actual_date` | Actual Date | Date | colonne de liste; lecture seule |
| `sales_person` | Sales Person | Link → `Sales Person` | colonne de liste |
| `serial_no` | Serial No | LongText | colonne de liste; lecture seule |
| `completion_status` | Completion Status | Select — Pending · Partially Completed · Fully Completed | colonne de liste; défaut `Pending` |
| `item_reference` | Item Reference | Text | lecture seule; masqué; — Référence de la ligne d'origine (Maintenance Schedule Item). |

## Maintenance Schedule Item

*Maintenance Schedule Item* — `maintenance/maintenance_schedule_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `item_name` | Item Name | Text | colonne de liste; lecture seule; recopié de `item_code.item_name` |
| `description` | Description | TextEditor | lecture seule |
| `start_date` | Start Date | Date | **requis**; colonne de liste |
| `end_date` | End Date | Date | **requis** |
| `periodicity` | Periodicity | Select — Weekly · Monthly · Quarterly · Half Yearly · Yearly · Random | colonne de liste |
| `no_of_visits` | No of Visits | Int | **requis**; colonne de liste |
| `sales_person` | Sales Person | Link → `Sales Person` |  |
| `serial_no` | Serial No | LongText | lecture seule |
| `sales_order` | Sales Order | Link → `Sales Order` | lecture seule |
| `serial_and_batch_bundle` | Serial and Batch Bundle | Link → `Serial and Batch Bundle` |  |

## Maintenance Visit

*Maintenance Visit* — `maintenance/maintenance_visit.yaml` · soumis

- **Numérotation** : série `MV-{YYYY}-{#####}`
- **Titre** : `status`
- **Icône** : `wrench`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — MAT-MVS-.YYYY.- | **requis** |
| `customer` | Customer | Link → `Customer` | **requis** |
| `customer_name` | Customer Name | Text | lecture seule; masqué; recopié de `customer.customer_name` |
| `address_display` | Address | TextEditor | lecture seule; masqué |
| `contact_display` | Contact | LongText | lecture seule; masqué |
| `contact_mobile` | Mobile No | Text | lecture seule; masqué |
| `contact_email` | Contact Email | Text | lecture seule; masqué |
| `mntc_date` | Maintenance Date | Date | **requis**; défaut `today` |
| `mntc_time` | Maintenance Time | Time |  |
| `completion_status` | Completion Status | Select — Partially Completed · Fully Completed | **requis**; colonne de liste |
| `maintenance_type` | Maintenance Type | Select — Scheduled · Unscheduled · Breakdown | **requis**; colonne de liste; défaut `Unscheduled` |
| `purposes` | Purposes | Table → `Maintenance Visit Purpose` |  |
| `customer_feedback` | Customer Feedback | LongText |  |
| `status` | Status | Select — Draft · Cancelled · Submitted | **requis**; lecture seule; défaut `Draft` |
| `company` | Company | Link → `Company` | **requis** |
| `customer_address` | Customer Address | Link → `Address` |  |
| `contact_person` | Contact Person | Link → `Contact` |  |
| `territory` | Territory | Link → `Territory` |  |
| `customer_group` | Customer Group | Link → `Customer Group` |  |
| `maintenance_schedule` | Maintenance Schedule | Link → `Maintenance Schedule` | lecture seule |
| `maintenance_schedule_detail` | Maintenance Schedule Detail | Text | masqué; — Référence de la ligne d'origine (Maintenance Schedule Detail). |

## Maintenance Visit Purpose

*Maintenance Visit Purpose* — `maintenance/maintenance_visit_purpose.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | colonne de liste |
| `item_name` | Item Name | Text | colonne de liste; lecture seule; recopié de `item_code.item_name` |
| `serial_no` | Serial No | Link → `Serial No` |  |
| `description` | Description | TextEditor | colonne de liste |
| `service_person` | Sales Person | Link → `Sales Person` | **requis**; colonne de liste |
| `work_done` | Work Done | LongText | **requis**; colonne de liste |
| `prevdoc_doctype` | Document Type | Text | masqué |
| `prevdoc_docname` | Against Document No | DynamicLink → `prevdoc_doctype` | masqué |
| `maintenance_schedule_detail` | Maintenance Schedule Detail | Text | masqué |
