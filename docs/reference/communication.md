# Référence des champs — Communication (`communication`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `communication/` (4 DocTypes). Ne pas éditer à la main : relancer le script.

20 champs au total ; types les plus fréquents : `Boolean` (8), `Link` (3), `Text` (3), `Select` (2), `Time` (2).

## Communication Medium

*Communication Medium* — `communication/communication_medium.yaml`

- **Titre** : `communication_medium_type`
- **Icône** : `phone`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `communication_medium_type` | Communication Medium Type | Select — Voice · Email · Chat | **requis**; colonne de liste |
| `catch_all` | Catch All | Link → `Employee Group` | — If there is no assigned timeslot, then communication will be handled by this group |
| `provider` | Provider | Link → `Supplier` |  |
| `disabled` | Disabled | Boolean | défaut `non` |
| `timeslots` | Timeslots | Table → `Communication Medium Timeslot` |  |

## Communication Medium Timeslot

*Communication Medium Timeslot* — `communication/communication_medium_timeslot.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `day_of_week` | Day of Week | Select — Monday · Tuesday · Wednesday · Thursday · Friday · Saturday · Sunday | **requis**; colonne de liste |
| `from_time` | From Time | Time | **requis**; colonne de liste |
| `to_time` | To Time | Time | **requis**; colonne de liste |
| `employee_group` | Employee Group | Link → `Employee Group` | **requis**; colonne de liste |

## Email Account

*Email Account* — `communication/email_account.yaml`

- **Titre** : `email_account_name`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `email_account_name` | Email Account Name | Text | **requis**; colonne de liste |
| `email_id` | Email Address | Text | **requis** |
| `enable_incoming` | Enable Incoming | Boolean |  |
| `enable_outgoing` | Enable Outgoing | Boolean |  |
| `default_incoming` | Default Incoming | Boolean |  |
| `default_outgoing` | Default Outgoing | Boolean |  |
| `disabled` | Disabled | Boolean |  |

## Email Template

*Email Template* — `communication/email_template.yaml`

- **Titre** : `subject`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `subject` | Subject | Text | **requis**; colonne de liste |
| `use_html` | Use HTML | Boolean |  |
| `response` | Response | TextEditor |  |
| `enabled` | Enabled | Boolean | défaut `oui` |
