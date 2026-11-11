# Référence des champs — Utilitaires (`utilities`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `utilities/` (4 DocTypes). Ne pas éditer à la main : relancer le script.

18 champs au total ; types les plus fréquents : `Text` (6), `Number` (4), `Select` (2), `Attach` (1), `Date` (1).

## Portal User

*Portal User* — `utilities/portal_user.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `user` | User | Text | **requis**; colonne de liste |

## Rename Tool

*Rename Tool* — `utilities/rename_tool.yaml`

- **Icône** : `pencil`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `select_doctype` | Select DocType | Text | — Type of document to rename. |
| `file_to_rename` | File to Rename | Attach | — Attach a comma separated .csv file with two columns, one for the old name and one for the new name. |

## Video

*Video* — `utilities/video.yaml`

- **Titre** : `title`
- **Icône** : `video`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text | **requis**; colonne de liste |
| `provider` | Provider | Select — YouTube · Vimeo | **requis**; colonne de liste |
| `url` | URL | Text | **requis** |
| `publish_date` | Publish Date | Date | colonne de liste |
| `description` | Description | TextEditor | **requis** |
| `like_count` | Likes | Number | colonne de liste; lecture seule |
| `view_count` | Views | Number | colonne de liste; lecture seule |
| `dislike_count` | Dislikes | Number | lecture seule |
| `comment_count` | Comments | Number | lecture seule |
| `image` | Image | Image | masqué |
| `youtube_video_id` | Youtube ID | Text | lecture seule; masqué |

## Video Settings

*Video Settings* — `utilities/video_settings.yaml` · document unique

- **Icône** : `settings`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `enable_youtube_tracking` | Enable YouTube Tracking | Boolean | défaut `non` |
| `api_key` | API Key | Text |  |
| `frequency` | Frequency | Select — 1 hr · 6 hrs · Daily | défaut `1 hr` |
| `last_youtube_update` | Last YouTube Update | Datetime | lecture seule; masqué |
