# Référence des champs — EDI (`edi`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `edi/` (2 DocTypes). Ne pas éditer à la main : relancer le script.

15 champs au total ; types les plus fréquents : `Text` (9), `LongText` (2), `Link` (2), `JSON` (1), `Code` (1).

## Code List

*Code List* — `edi/code_list.yaml`

- **Titre** : `title`
- **Icône** : `list`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text |  |
| `publisher` | Publisher | Text |  |
| `code_version` | Version | Text | colonne de liste |
| `description` | Description | LongText |  |
| `canonical_uri` | Canonical URI | Text | colonne de liste |
| `publisher_id` | Publisher ID | Text |  |
| `url` | URL | Text |  |
| `default_common_code` | Default Common Code | Link → `Common Code` | — This value shall be used when no matching Common Code for a record is found. |

## Common Code

*Common Code* — `edi/common_code.yaml`

- **Titre** : `title`
- **Icône** : `code`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `code_list` | Code List | Link → `Code List` | **requis**; colonne de liste |
| `title` | Title | Text | **requis**; colonne de liste |
| `applies_to` | Applies To | JSON |  |
| `common_code` | Common Code | Text | **requis**; colonne de liste |
| `additional_data` | Additional Data | Code | lecture seule |
| `description` | Description | LongText | colonne de liste |
| `canonical_uri` | Canonical URI | Text |  |
