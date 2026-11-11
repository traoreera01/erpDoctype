# Référence des champs — Téléphonie (`telephony`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `telephony/` (5 DocTypes). Ne pas éditer à la main : relancer le script.

30 champs au total ; types les plus fréquents : `Text` (14), `Select` (5), `Link` (4), `Datetime` (2), `Time` (2).

## Call Log

*Call Log* — `telephony/call_log.yaml`

- **Titre** : `status`
- **Icône** : `phone`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `id` | ID | Text | lecture seule |
| `from` | From | Text | colonne de liste; lecture seule |
| `to` | To | Text | colonne de liste; lecture seule |
| `status` | Status | Select — Ringing · In Progress · Completed · Failed · Busy · No Answer · Queued · Cancelled | colonne de liste; lecture seule |
| `recording_url` | Recording URL | Text | masqué |
| `medium` | Medium | Text | lecture seule |
| `type` | Type | Select — Incoming · Outgoing | lecture seule |
| `links` | Links | JSON |  |
| `summary` | Summary | LongText |  |
| `start_time` | Start Time | Datetime | lecture seule |
| `end_time` | End Time | Datetime | lecture seule |
| `customer` | Customer | Link → `Customer` | lecture seule |
| `employee_user_id` | Employee User Id | Text | masqué |
| `type_of_call` | Type Of Call | Link → `Telephony Call Type` |  |
| `call_received_by` | Call Received By | Link → `Employee` | lecture seule |

## Incoming Call Handling Schedule

*Incoming Call Handling Schedule* — `telephony/incoming_call_handling_schedule.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `day_of_week` | Day Of Week | Select — Monday · Tuesday · Wednesday · Thursday · Friday · Saturday · Sunday | **requis**; colonne de liste |
| `from_time` | From Time | Time | **requis**; colonne de liste |
| `to_time` | To Time | Time | **requis**; colonne de liste |
| `agent_group` | Agent Group | Link → `Employee Group` | **requis**; colonne de liste |

## Incoming Call Settings

*Incoming Call Settings* — `telephony/incoming_call_settings.yaml` · document unique

- **Titre** : `call_routing`
- **Icône** : `phone-incoming`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `call_routing` | Call Routing | Select — Sequential · Simultaneous | colonne de liste; défaut `Sequential` |
| `greeting_message` | Greeting Message | Text |  |
| `agent_busy_message` | Agent Busy Message | Text |  |
| `agent_unavailable_message` | Agent Unavailable Message | Text |  |
| `call_handling_schedule` | Call Handling Schedule | Table → `Incoming Call Handling Schedule` |  |

## Telephony Call Type

*Telephony Call Type* — `telephony/telephony_call_type.yaml` · soumis

- **Numérotation** : série `TCT-{YYYY}-{#####}`
- **Titre** : `call_type`
- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `call_type` | Call Type | Text | **requis**; colonne de liste |

## Voice Call Settings

*Voice Call Settings* — `telephony/voice_call_settings.yaml` · document unique

- **Titre** : `user`
- **Icône** : `phone-call`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `user` | User | Text | **requis**; colonne de liste |
| `greeting_message` | Greeting Message | Text |  |
| `agent_busy_message` | Agent Busy Message | Text |  |
| `agent_unavailable_message` | Agent Unavailable Message | Text |  |
| `call_receiving_device` | Call Receiving Device | Select — Computer · Phone | défaut `Computer` |
