# Référence des champs — CRM (`crm`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `crm/` (32 DocTypes). Ne pas éditer à la main : relancer le script.

248 champs au total ; types les plus fréquents : `Text` (83), `Link` (47), `Select` (23), `Boolean` (23), `Table` (14).

## Appointment

*Appointment* — `crm/appointment.yaml`

- **Titre** : `customer_name`
- **Icône** : `clipboard-clock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `customer_name` | Name | Text | **requis**; colonne de liste |
| `customer_phone_number` | Phone Number | Text |  |
| `customer_skype` | Skype ID | Text |  |
| `customer_details` | Details | LongText |  |
| `scheduled_time` | Scheduled Time | Datetime | **requis**; colonne de liste |
| `status` | Status | Select — Open · Unverified · Closed | **requis** |
| `calendar_event` | Calendar Event | Link → `Event` |  |
| `customer_email` | Email | Text | **requis** |
| `appointment_with` | Appointment With | Text |  |
| `party` | Party | DynamicLink → `appointment_with` |  |
| `created_through_portal` | Created through Portal | Boolean | lecture seule |
| `email_verified` | Email Verified | Boolean | lecture seule |
| `verification_token` | Verification Token | Text | lecture seule; masqué |

## Appointment Booking Settings

*Appointment Booking Settings* — `crm/appointment_booking_settings.yaml` · document unique

- **Titre** : `holiday_list`
- **Icône** : `settings`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `availability_of_slots` | Availability Of Slots | Table → `Appointment Booking Slots` |  |
| `number_of_agents` | Number of Concurrent Appointments | Int | colonne de liste; lecture seule |
| `holiday_list` | Holiday List | Link → `Holiday List` | colonne de liste |
| `appointment_duration` | Appointment Duration (In Minutes) | Int | **requis**; défaut `60` |
| `email_reminders` | Notify Via Email | Boolean | défaut `non`; — Notify customer and agent via email on the day of the appointment. |
| `advance_booking_days` | Number of days appointments can be booked in advance | Int | défaut `7` |
| `agent_list` | Agents | Table → `Assignment Rule User` | — Un agent par ligne (adresse e-mail du membre). |
| `enable_scheduling` | Enable Appointment Scheduling | Boolean | défaut `non` |
| `success_redirect_url` | Success Redirect URL | Text | — Leave blank for home. This is relative to site URL, for example "about" will redirect to "https://yoursitename |
| `verification_link_expiry_duration` | Verification Link Expiry Duration | Int | défaut `30`; — In Minutes (min: 15 mins, max: 60 mins) |
| `enable_appointment_portal` | Enable Appointment Booking Through Portal | Boolean | défaut `non` |
| `action_for_expired_unverified_appointments` | Action for Expired Unverified Appointments | Select — Mark as Closed · Delete Permanently | défaut `Mark as Closed` |

## Appointment Booking Slots

*Appointment Booking Slots* — `crm/appointment_booking_slots.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `day_of_week` | Day Of Week | Select — Sunday · Monday · Tuesday · Wednesday · Thursday · Friday · Saturday | **requis**; colonne de liste |
| `from_time` | From Time  | Time | **requis**; colonne de liste |
| `to_time` | To Time | Time | **requis**; colonne de liste |

## Assignment Rule User

*Agent affecté* — `crm/assignment_rule_user.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `user` | Membre | Text | **requis** |

## Campaign

*Campaign* — `crm/campaign.yaml`

- **Titre** : `campaign_name`
- **Icône** : `megaphone`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `campaign_name` | Campaign Name | Text | **requis** |
| `naming_series` | Naming Series | Select — SAL-CAM-.YYYY.- |  |
| `campaign_schedules` | Campaign Schedules | Table → `Campaign Email Schedule` |  |
| `description` | Description | LongText | colonne de liste |

## Campaign Email Schedule

*Campaign Email Schedule* — `crm/campaign_email_schedule.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `send_after_days` | Send After (days) | Int | **requis**; colonne de liste |
| `email_template` | Email Template | Link → `Email Template` | **requis**; colonne de liste |

## Competitor

*Competitor* — `crm/competitor.yaml`

- **Titre** : `competitor_name`
- **Icône** : `swords`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `competitor_name` | Competitor Name | Text | **requis**; colonne de liste |
| `website` | Website | Text | colonne de liste |

## Competitor Detail

*Competitor Detail* — `crm/competitor_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `competitor` | Competitor | Link → `Competitor` | **requis**; colonne de liste |

## Contact

*Contact* — `crm/contact.yaml`

- **Titre** : `email_id`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `first_name` | First Name | Text | **requis** |
| `middle_name` | Middle Name | Text |  |
| `last_name` | Last Name | Text |  |
| `designation` | Designation | Text |  |
| `email_id` | Email | Text | colonne de liste |
| `phone` | Phone | Text |  |
| `mobile_no` | Mobile | Text |  |
| `is_primary_contact` | Primary Contact | Boolean |  |
| `disabled` | Disabled | Boolean |  |

## Contract

*Contract* — `crm/contract.yaml` · soumis

- **Numérotation** : série `CONT-{YYYY}-{#####}`
- **Icône** : `signature`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `party_type` | Party Type | Select — Customer · Supplier · Employee | **requis**; défaut `Customer` |
| `is_signed` | Signed | Boolean | défaut `non` |
| `party_name` | Party Name | DynamicLink → `party_type` |  |
| `party_user` | Party User | Text |  |
| `status` | Status | Select — Unsigned · Active · Inactive · Cancelled | colonne de liste; masqué |
| `fulfilment_status` | Fulfilment Status | Select — N/A · Unfulfilled · Partially Fulfilled · Fulfilled · Lapsed | colonne de liste; masqué |
| `start_date` | Start Date | Date |  |
| `end_date` | End Date | Date |  |
| `signee` | Signee | Text |  |
| `signed_on` | Signed On | Datetime | colonne de liste |
| `ip_address` | IP Address | Text | lecture seule |
| `contract_template` | Contract Template | Link → `Contract Template` |  |
| `contract_terms` | Contract Terms | TextEditor | **requis**; colonne de liste |
| `requires_fulfilment` | Requires Fulfilment | Boolean | défaut `non` |
| `fulfilment_deadline` | Fulfilment Deadline | Date |  |
| `fulfilment_terms` | Fulfilment Terms | Table → `Contract Fulfilment Checklist` |  |
| `document_type` | Document Type | Select — Quotation · Project · Sales Order · Purchase Order · Sales Invoice · Purchase Invoice |  |
| `document_name` | Document Name | DynamicLink → `document_type` | colonne de liste |
| `signed_by_company` | Signed By (Company) | Text | lecture seule |
| `party_full_name` | Party Full Name | Text | lecture seule |

## Contract Fulfilment Checklist

*Contract Fulfilment Checklist* — `crm/contract_fulfilment_checklist.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `fulfilled` | Fulfilled | Boolean | colonne de liste; défaut `non` |
| `requirement` | Requirement | Text | colonne de liste |
| `notes` | Notes | LongText | colonne de liste |

## Contract Template

*Contract Template* — `crm/contract_template.yaml`

- **Titre** : `title`
- **Icône** : `signature`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text |  |
| `contract_terms` | Contract Terms and Conditions | TextEditor |  |
| `requires_fulfilment` | Requires Fulfilment | Boolean | défaut `non` |
| `fulfilment_terms` | Fulfilment Terms and Conditions | Table → `Contract Template Fulfilment Terms` |  |

## Contract Template Fulfilment Terms

*Contract Template Fulfilment Terms* — `crm/contract_template_fulfilment_terms.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `requirement` | Requirement | Text | colonne de liste |

## CRM Note

*CRM Note* — `crm/crm_note.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `note` | Note | TextEditor | colonne de liste |
| `added_by` | Added By | Text | colonne de liste |
| `added_on` | Added On | Datetime | colonne de liste |

## CRM Settings

*CRM Settings* — `crm/crm_settings.yaml` · document unique

- **Titre** : `campaign_naming_by`
- **Icône** : `settings`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `campaign_naming_by` | Campaign Naming By | Select — Campaign Name · Naming Series | colonne de liste |
| `default_valid_till` | Default Quotation Validity Days | Text |  |
| `allow_lead_duplication_based_on_emails` | Allow Lead Duplication based on Emails | Boolean | défaut `non` |
| `auto_creation_of_contact` | Auto Creation of Contact | Boolean | défaut `oui` |
| `close_opportunity_after_days` | Close Replied Opportunity After Days | Int | défaut `15`; — Auto close Opportunity Replied after the no. of days mentioned above |
| `carry_forward_communication_and_comments` | Carry Forward Communication and Comments | Boolean | défaut `non`; — All the Comments and Emails will be copied from one document to another newly created document(Lead -> Opportu |
| `update_timestamp_on_new_communication` | Update timestamp on new communication | Boolean | défaut `non`; — Update the modified timestamp on new communications received in Lead & Opportunity. |
| `enable_opportunity_creation_from_contact_us` | Enable Opportunity Creation from Contact Us | Boolean | défaut `non` |
| `allowed_users` | Allowed Users | Table → `Frappe CRM Allowed User` | masqué |
| `enable_frappe_crm_data_synchronization` | Enable Frappe CRM Data Synchronization | Boolean | défaut `non` |

## Email Campaign

*Email Campaign* — `crm/email_campaign.yaml`

- **Titre** : `campaign_name`
- **Icône** : `mails`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `campaign_name` | Campaign | Link → `Campaign` | **requis**; colonne de liste |
| `status` | Status | Select — Scheduled · In Progress · Completed · Unsubscribed | lecture seule |
| `start_date` | Start Date | Date | **requis** |
| `end_date` | End Date | Date | lecture seule |
| `email_campaign_for` | Email Campaign For  | Select — Lead · Contact | **requis**; colonne de liste; défaut `Lead` |
| `recipient` | Recipient | DynamicLink → `email_campaign_for` |  |
| `sender` | Sender | Text |  |

## Event

*Event* — `crm/event.yaml`

- **Titre** : `subject`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `subject` | Subject | Text | **requis**; colonne de liste |
| `starts_on` | Starts On | Datetime | **requis** |
| `ends_on` | Ends On | Datetime |  |
| `event_type` | Event Type | Select — Private · Public |  |
| `status` | Status | Select — Open · Completed · Cancelled |  |
| `description` | Description | LongText |  |

## Frappe CRM Allowed User

*Frappe CRM Allowed User* — `crm/frappe_crm_allowed_user.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `user` | User | Text | **requis**; colonne de liste |

## Lead

*Lead* — `crm/lead.yaml`

- **Titre** : `lead_name`
- **Icône** : `user-plus`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — CRM-LEAD-.YYYY.- |  |
| `lead_name` | Full Name | Text | lecture seule |
| `company_name` | Organization Name | Text | colonne de liste |
| `email_id` | Email | Text |  |
| `lead_owner` | Lead Owner | Text |  |
| `status` | Status | Select — Lead · Open · Replied · Opportunity · Quotation · Lost Quotation · Interested · Converted · Do Not Contact | **requis**; colonne de liste; défaut `Lead` |
| `salutation` | Salutation | Link → `Salutation` |  |
| `gender` | Gender | Link → `Gender` |  |
| `customer` | From Customer | Link → `Customer` |  |
| `image` | Image | Image | masqué |
| `phone` | Phone | Text |  |
| `mobile_no` | Mobile No | Text |  |
| `fax` | Fax | Text |  |
| `type` | Lead Type | Select — Client · Channel Partner · Consultant |  |
| `market_segment` | Market Segment | Link → `Market Segment` |  |
| `industry` | Industry | Link → `Industry Type` |  |
| `request_type` | Request Type | Select — Product Enquiry · Request for Information · Suggestions · Other |  |
| `company` | Company | Link → `Company` |  |
| `website` | Website | Text |  |
| `territory` | Territory | Link → `Territory` | colonne de liste |
| `unsubscribed` | Unsubscribed | Boolean | défaut `non` |
| `blog_subscriber` | Blog Subscriber | Boolean | défaut `non` |
| `title` | Title | Text | lecture seule; masqué |
| `language` | Print Language | Link → `Language` |  |
| `first_name` | First Name | Text |  |
| `middle_name` | Middle Name | Text |  |
| `last_name` | Last Name | Text |  |
| `no_of_employees` | No of Employees | Select — 1-10 · 11-50 · 51-200 · 201-500 · 501-1000 · 1000+ |  |
| `whatsapp_no` | WhatsApp | Text |  |
| `phone_ext` | Phone Ext. | Text |  |
| `qualified_by` | Qualified By | Text |  |
| `qualified_on` | Qualified on | Date |  |
| `qualification_status` | Qualification Status | Select — Unqualified · In Process · Qualified |  |
| `job_title` | Job Title | Text | colonne de liste |
| `annual_revenue` | Annual Revenue | Currency | devise de `company.default_currency` |
| `notes` | Notes | Table → `CRM Note` | masqué |
| `disabled` | Disabled | Boolean | défaut `non` |
| `city` | City | Text |  |
| `state` | State/Province | Text |  |
| `country` | Country | Link → `Country` |  |
| `utm_content` | Content | Text |  |
| `utm_source` | Source | Link → `UTM Source` |  |
| `utm_medium` | Medium | Link → `UTM Medium` |  |
| `utm_campaign` | Campaign | Link → `UTM Campaign` |  |

## Market Segment

*Market Segment* — `crm/market_segment.yaml`

- **Icône** : `chart-pie`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `market_segment` | Market Segment | Text |  |

## Opportunity

*Opportunity* — `crm/opportunity.yaml`

- **Titre** : `status`
- **Icône** : `user-star`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — CRM-OPP-.YYYY.- | **requis**; colonne de liste |
| `opportunity_from` | Opportunity From | Text | **requis**; colonne de liste |
| `party_name` | Party | DynamicLink → `opportunity_from` |  |
| `customer_name` | Customer Name | Text | lecture seule; masqué |
| `title` | Title | Text | masqué |
| `opportunity_type` | Opportunity Type | Link → `Opportunity Type` | colonne de liste |
| `status` | Status | Select — Open · Quotation · Converted · Lost · Replied · Closed | **requis**; colonne de liste; défaut `Open` |
| `order_lost_reason` | Detailed Reason | LongText | lecture seule |
| `lost_on` | Lost On | Date | lecture seule; masqué |
| `expected_closing` | Expected Closing Date | Date |  |
| `currency` | Currency | Link → `Currency` |  |
| `opportunity_amount` | Opportunity Amount | Currency | devise de `currency` |
| `sales_stage` | Sales Stage | Link → `Sales Stage` |  |
| `probability` | Probability (%) | Percent | défaut `100.0` |
| `items` | Items | Table → `Opportunity Item` |  |
| `customer_address` | Customer / Lead Address | Link → `Address` | masqué |
| `address_display` | Address | TextEditor | lecture seule; masqué |
| `territory` | Territory | Link → `Territory` |  |
| `customer_group` | Customer Group | Link → `Customer Group` |  |
| `contact_person` | Contact Person | Link → `Contact` |  |
| `contact_display` | Contact | LongText | lecture seule |
| `contact_email` | Contact Email | Text |  |
| `contact_mobile` | Contact Mobile | Text |  |
| `company` | Company | Link → `Company` | **requis** |
| `transaction_date` | Opportunity Date | Date | **requis**; défaut `today` |
| `lost_reasons` | Lost Reasons | Table → `Opportunity Lost Reason Detail` | lecture seule |
| `language` | Print Language | Link → `Language` |  |
| `base_opportunity_amount` | Opportunity Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_total` | Total (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `total` | Total | Currency | lecture seule; devise de `currency` |
| `conversion_rate` | Exchange Rate | Number |  |
| `competitors` | Competitors | Table → `Competitor Detail` | lecture seule |
| `no_of_employees` | No of Employees | Select — 1-10 · 11-50 · 51-200 · 201-500 · 501-1000 · 1000+ |  |
| `annual_revenue` | Annual Revenue | Currency | devise de `currency` |
| `industry` | Industry | Link → `Industry Type` |  |
| `market_segment` | Market Segment | Link → `Market Segment` |  |
| `opportunity_owner` | Opportunity Owner | Text |  |
| `website` | Website | Text |  |
| `whatsapp` | WhatsApp | Text |  |
| `phone` | Phone | Text |  |
| `phone_ext` | Phone Ext. | Text |  |
| `job_title` | Job Title | Text |  |
| `notes` | Notes | Table → `CRM Note` | masqué |
| `city` | City | Text |  |
| `state` | State/Province | Text |  |
| `country` | Country | Link → `Country` |  |
| `utm_source` | Source | Link → `UTM Source` |  |
| `utm_campaign` | Campaign | Link → `UTM Campaign` |  |
| `utm_medium` | Medium | Link → `UTM Medium` |  |
| `utm_content` | Content | Text |  |

## Opportunity Item

*Opportunity Item* — `crm/opportunity_item.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `item_code` | Item Code | Link → `Item` | colonne de liste |
| `qty` | Qty | Decimal | colonne de liste; défaut `1.000` |
| `item_group` | Item Group | Link → `Item Group` | masqué |
| `brand` | Brand | Link → `Brand` | masqué |
| `uom` | UOM | Link → `UOM` |  |
| `item_name` | Item Name | Text |  |
| `description` | Description | TextEditor |  |
| `rate` | Rate | Currency | **requis**; colonne de liste; devise de `parent_currency` |
| `base_amount` | Amount (Company Currency) | Currency | **requis**; lecture seule; devise de `parent_company.default_currency` |
| `amount` | Amount | Currency | **requis**; colonne de liste; lecture seule; devise de `parent_currency` |
| `base_rate` | Rate (Company Currency) | Currency | **requis**; lecture seule; devise de `parent_company.default_currency` |

## Opportunity Lost Reason

*Opportunity Lost Reason* — `crm/opportunity_lost_reason.yaml`

- **Icône** : `circle-x`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `lost_reason` | Lost Reason | Text |  |

## Opportunity Lost Reason Detail

*Opportunity Lost Reason Detail* — `crm/opportunity_lost_reason_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `lost_reason` | Opportunity Lost Reason | Link → `Opportunity Lost Reason` | colonne de liste |

## Opportunity Type

*Opportunity Type* — `crm/opportunity_type.yaml`

- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `description` | Description | LongText | colonne de liste |

## Prospect

*Prospect* — `crm/prospect.yaml`

- **Titre** : `industry`
- **Icône** : `user-round-search`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company_name` | Company Name | Text |  |
| `industry` | Industry | Link → `Industry Type` | colonne de liste |
| `market_segment` | Market Segment | Link → `Market Segment` |  |
| `customer_group` | Customer Group | Link → `Customer Group` |  |
| `territory` | Territory | Link → `Territory` | colonne de liste |
| `no_of_employees` | No. of Employees | Select — 1-10 · 11-50 · 51-200 · 201-500 · 501-1000 · 1000+ |  |
| `annual_revenue` | Annual Revenue | Currency | colonne de liste; devise de `company.default_currency` |
| `fax` | Fax | Text |  |
| `website` | Website | Text |  |
| `prospect_owner` | Prospect Owner | Text |  |
| `company` | Company | Link → `Company` | **requis** |
| `opportunities` | Opportunities | Table → `Prospect Opportunity` |  |
| `leads` | leads | Table → `Prospect Lead` |  |
| `notes` | Notes | Table → `CRM Note` | masqué |

## Prospect Lead

*Prospect Lead* — `crm/prospect_lead.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `lead` | Lead | Link → `Lead` | **requis**; colonne de liste |
| `lead_name` | Lead Name | Text | colonne de liste; lecture seule; recopié de `lead.lead_name` |
| `status` | Status | Text | colonne de liste; lecture seule |
| `email` | Email | Text | colonne de liste; lecture seule |
| `mobile_no` | Mobile No | Text | colonne de liste; lecture seule |
| `lead_owner` | Lead Owner | Text | colonne de liste |

## Prospect Opportunity

*Prospect Opportunity* — `crm/prospect_opportunity.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `opportunity` | Opportunity | Link → `Opportunity` | colonne de liste |
| `amount` | Amount | Currency | colonne de liste; devise de `currency` |
| `stage` | Stage | Text | colonne de liste |
| `probability` | Probability | Percent | colonne de liste |
| `expected_closing` | Closing | Date | colonne de liste |
| `currency` | Currency | Link → `Currency` |  |
| `deal_owner` | Deal Owner | Text | colonne de liste |
| `contact_person` | Contact Person | Link → `Contact` |  |

## Sales Stage

*Sales Stage* — `crm/sales_stage.yaml`

- **Icône** : `milestone`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `stage_name` | Stage Name | Text |  |

## UTM Campaign

*UTM Campaign* — `crm/utm_campaign.yaml`

- **Titre** : `campaign_name`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `campaign_name` | Campaign Name | Text | **requis**; colonne de liste |
| `campaign_code` | Campaign Code | Text |  |
| `description` | Description | LongText |  |
| `disabled` | Disabled | Boolean |  |

## UTM Medium

*UTM Medium* — `crm/utm_medium.yaml`

- **Titre** : `medium_name`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `medium_name` | Medium Name | Text | **requis**; colonne de liste |
| `enabled` | Enabled | Boolean | défaut `oui` |

## UTM Source

*UTM Source* — `crm/utm_source.yaml`

- **Titre** : `source_name`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `source_name` | Source Name | Text | **requis**; colonne de liste |
| `enabled` | Enabled | Boolean | défaut `oui` |
