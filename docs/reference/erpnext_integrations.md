# Référence des champs — Intégrations ERPNext (`erpnext_integrations`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `erpnext_integrations/` (1 DocTypes). Ne pas éditer à la main : relancer le script.

5 champs au total ; types les plus fréquents : `Boolean` (3), `Text` (1), `Select` (1).

## Plaid Settings

*Plaid Settings* — `erpnext_integrations/plaid_settings.yaml` · document unique

- **Titre** : `plaid_client_id`
- **Icône** : `landmark`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `enabled` | Enabled | Boolean | défaut `non` |
| `automatic_sync` | Synchronize all accounts every hour | Boolean | défaut `non` |
| `plaid_client_id` | Plaid Client ID | Text | colonne de liste |
| `plaid_env` | Plaid Environment | Select — sandbox · development · production | colonne de liste |
| `enable_european_access` | Enable European Access | Boolean | défaut `non` |
