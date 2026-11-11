# Référence des champs — Traitement en masse (`bulk_transaction`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `bulk_transaction/` (2 DocTypes). Ne pas éditer à la main : relancer le script.

12 champs au total ; types les plus fréquents : `Int` (4), `Text` (3), `Date` (2), `DynamicLink` (1), `LongText` (1).

## Bulk Transaction Log

*Bulk Transaction Log* — `bulk_transaction/bulk_transaction_log.yaml`

- **Vues** : calendar
- **Icône** : `file`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `date` | Date | Date | colonne de liste; lecture seule |
| `log_entries` | Log Entries | Int | colonne de liste; lecture seule |
| `succeeded` | Succeeded | Int | lecture seule |
| `failed` | Failed | Int | lecture seule |

## Bulk Transaction Log Detail

*Bulk Transaction Log Detail* — `bulk_transaction/bulk_transaction_log_detail.yaml`

- **Vues** : calendar
- **Titre** : `transaction_status`
- **Icône** : `file`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `transaction_name` | Name | DynamicLink → `from_doctype` | colonne de liste; lecture seule |
| `transaction_status` | Status | Text | colonne de liste; lecture seule |
| `error_description` | Error Description | LongText | lecture seule |
| `from_doctype` | From Doctype | Text | lecture seule |
| `to_doctype` | To Doctype | Text | lecture seule |
| `date` | Date  | Date | colonne de liste; lecture seule |
| `time` | Time | Time | lecture seule |
| `retried` | Retried | Int | colonne de liste; lecture seule |
