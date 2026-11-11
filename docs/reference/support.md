# Référence des champs — Support (`support`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `support/` (11 DocTypes). Ne pas éditer à la main : relancer le script.

111 champs au total ; types les plus fréquents : `Text` (37), `Link` (21), `Select` (9), `Boolean` (8), `Datetime` (7).

## Issue

*Issue* — `support/issue.yaml`

- **Vues** : kanban
- **Titre** : `subject`
- **Icône** : `ticket`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — ISS-.YYYY.- |  |
| `subject` | Subject | Text | **requis** |
| `customer` | Customer | Link → `Customer` |  |
| `raised_by` | Raised By (Email) | Text | colonne de liste |
| `status` | Status | Select — Open · Replied · On Hold · Resolved · Closed | colonne de liste; défaut `Open` |
| `priority` | Priority | Link → `Issue Priority` | colonne de liste |
| `issue_type` | Issue Type | Link → `Issue Type` |  |
| `description` | Description | TextEditor |  |
| `service_level_agreement` | Service Level Agreement | Link → `Service Level Agreement` |  |
| `response_by` | Response By | Datetime | lecture seule |
| `first_responded_on` | First Responded On | Datetime |  |
| `lead` | Lead | Link → `Lead` |  |
| `contact` | Contact | Link → `Contact` |  |
| `email_account` | Email Account | Link → `Email Account` |  |
| `customer_name` | Customer Name | Text | lecture seule; recopié de `customer.customer_name` |
| `project` | Project | Link → `Project` |  |
| `company` | Company | Link → `Company` |  |
| `resolution_details` | Resolution Details | TextEditor |  |
| `opening_date` | Opening Date | Date | lecture seule |
| `opening_time` | Opening Time | Time | lecture seule |
| `content_type` | Content Type | Text | masqué |
| `attachment` | Attachment | Attach | masqué |
| `via_customer_portal` | Via Customer Portal | Boolean | défaut `non` |
| `service_level_agreement_creation` | Service Level Agreement Creation | Datetime | lecture seule; masqué |
| `issue_split_from` | Issue Split From | Link → `Issue` | lecture seule |
| `on_hold_since` | On Hold Since | Datetime | lecture seule; masqué |
| `agreement_status` | Service Level Agreement Status | Select — First Response Due · Resolution Due · Fulfilled · Failed | lecture seule; défaut `First Response Due` |
| `sla_resolution_by` | Resolution By | Datetime | lecture seule |
| `sla_resolution_date` | Resolution Date | Datetime | lecture seule |

## Issue Priority

*Issue Priority* — `support/issue_priority.yaml`

- **Icône** : `flag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `description` | Description | LongText |  |

## Issue Type

*Issue Type* — `support/issue_type.yaml`

- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `description` | Description | LongText |  |

## Pause SLA On Status

*Pause SLA On Status* — `support/pause_sla_on_status.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `description` | Description | Text |  |

## Service Day

*Service Day* — `support/service_day.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `workday` | Workday | Select — Monday · Tuesday · Wednesday · Thursday · Friday · Saturday · Sunday | **requis**; colonne de liste |
| `start_time` | Start Time | Time | **requis**; colonne de liste |
| `end_time` | End Time | Time | **requis**; colonne de liste |

## Service Level Agreement

*Service Level Agreement* — `support/service_level_agreement.yaml`

- **Vues** : calendar, gantt
- **Titre** : `service_level`
- **Icône** : `signature`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `service_level` | Service Level Name | Text | **requis**; colonne de liste |
| `holiday_list` | Holiday List | Link → `Holiday List` | **requis** |
| `start_date` | Start Date | Date |  |
| `end_date` | End Date | Date |  |
| `support_and_resolution` | Working Hours | Table → `Service Day` |  |
| `priorities` | Priorities | Table → `Service Level Priority` |  |
| `entity` | Entity | DynamicLink → `entity_type` | colonne de liste |
| `entity_type` | Entity Type | Select — Customer · Customer Group · Territory |  |
| `default_service_level_agreement` | Default Service Level Agreement | Boolean | défaut `non` |
| `default_priority` | Default Priority | Link → `Issue Priority` | lecture seule |
| `pause_sla_on` | SLA Paused On | Table → `Pause SLA On Status` |  |
| `document_type` | Apply On | Text | **requis** |
| `enabled` | Enabled | Boolean | défaut `oui` |
| `sla_fulfilled_on` | SLA Fulfilled On | Table → `SLA Fulfilled On Status` |  |
| `apply_sla_for_resolution` | Apply SLA for Resolution Time | Boolean | défaut `oui` |
| `condition` | Condition | Code | — Simple Python Expression, Example: doc.status == 'Open' and doc.issue_type == 'Bug' |

## Service Level Priority

*Service Level Priority* — `support/service_level_priority.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `priority` | Priority | Link → `Issue Priority` | **requis**; colonne de liste |
| `default_priority` | Default Priority | Boolean | colonne de liste; défaut `non` |

## SLA Fulfilled On Status

*SLA Fulfilled On Status* — `support/sla_fulfilled_on_status.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `description` | Description | Text |  |

## Support Search Source

*Support Search Source* — `support/support_search_source.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `source_name` | Source Name | Text | colonne de liste |
| `source_type` | Source Type | Select — API · Link | **requis**; colonne de liste |
| `base_url` | Base URL | Text |  |
| `query_route` | Query Route String | Text |  |
| `search_term_param_name` | Search Term Param Name | Text |  |
| `response_result_key_path` | Response Result Key Path | Text |  |
| `post_route` | Post Route String | Text |  |
| `post_route_key_list` | Post Route Key List | Text |  |
| `post_title_key` | Post Title Key | Text |  |
| `post_description_key` | Post Description Key | Text |  |
| `source_doctype` | Source DocType | Text |  |
| `result_title_field` | Result Title Field | Text |  |
| `result_preview_field` | Result Preview Field | Text |  |
| `result_route_field` | Result Route Field | Text |  |

## Support Settings

*Support Settings* — `support/support_settings.yaml` · document unique

- **Icône** : `settings`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `close_issue_after_days` | Close Issue After Days | Int | défaut `7`; — Set this value to 0 to disable the feature. |
| `get_started_sections` | Get Started Sections | Code |  |
| `show_latest_forum_posts` | Show Latest Forum Posts | Boolean | défaut `non` |
| `forum_url` | Forum URL | Text |  |
| `get_latest_query` | Get Latest Query | Text |  |
| `response_key_list` | Response Key List | Text |  |
| `post_title_key` | Post Title Key | Text |  |
| `post_description_key` | Post Description Key | Text |  |
| `post_route_key` | Post Route Key | Text |  |
| `post_route_string` | Post Route String | Text |  |
| `search_apis` | Search APIs | Table → `Support Search Source` |  |
| `track_service_level_agreement` | Track Service Level Agreement | Boolean | défaut `non` |
| `allow_resetting_service_level_agreement` | Allow Resetting Service Level Agreement | Boolean | défaut `non` |
| `greeting_title` | Greeting Title | Text | défaut `We're here to help` |
| `greeting_subtitle` | Greeting Subtitle | Text | défaut `Browse help topics` |

## Warranty Claim

*Warranty Claim* — `support/warranty_claim.yaml`

- **Vues** : kanban
- **Titre** : `customer_name`
- **Icône** : `shield-alert`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — SER-WRN-.YYYY.- | **requis** |
| `status` | Status | Select — Open · Closed · Work In Progress · Cancelled | **requis**; colonne de liste; défaut `Open` |
| `complaint_date` | Issue Date | Date | **requis**; défaut `today` |
| `serial_no` | Serial No | Link → `Serial No` |  |
| `customer` | Customer | Link → `Customer` | **requis** |
| `complaint` | Issue | TextEditor | **requis** |
| `item_code` | Item Code | Link → `Item` | colonne de liste |
| `item_name` | Item Name | Text | lecture seule; recopié de `item_code.item_name` |
| `description` | Description | LongText | lecture seule |
| `warranty_amc_status` | Warranty / AMC Status | Select — Under Warranty · Out of Warranty · Under AMC · Out of AMC |  |
| `warranty_expiry_date` | Warranty Expiry Date | Date |  |
| `amc_expiry_date` | AMC Expiry Date | Date |  |
| `resolution_date` | Resolution Date | Datetime |  |
| `resolved_by` | Resolved By | Text |  |
| `resolution_details` | Resolution Details | LongText |  |
| `customer_name` | Customer Name | Text | lecture seule; recopié de `customer.customer_name` |
| `contact_person` | Contact Person | Link → `Contact` |  |
| `contact_display` | Contact | LongText | lecture seule |
| `contact_mobile` | Mobile No | Text | lecture seule |
| `contact_email` | Contact Email | Text | lecture seule |
| `territory` | Territory | Link → `Territory` | lecture seule |
| `customer_group` | Customer Group | Link → `Customer Group` | lecture seule |
| `customer_address` | Customer Address | Link → `Address` |  |
| `address_display` | Address | TextEditor | lecture seule |
| `service_address` | Service Address | LongText | — If different than customer address |
| `company` | Company | Link → `Company` | **requis** |
| `complaint_raised_by` | Raised By | Text |  |
| `from_company` | From Company | Text |  |
