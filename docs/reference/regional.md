# Référence des champs — Régionalisation (`regional`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `regional/` (5 DocTypes). Ne pas éditer à la main : relancer le script.

23 champs au total ; types les plus fréquents : `Link` (12), `Text` (3), `Date` (2), `Table` (2), `Attach` (1).

## Import Supplier Invoice

*Import Supplier Invoice* — `regional/import_supplier_invoice.yaml`

- **Titre** : `item_code`
- **Icône** : `file-input`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `item_code` | Item Code | Link → `Item` | **requis**; colonne de liste |
| `supplier_group` | Supplier Group | Link → `Supplier Group` | **requis**; colonne de liste |
| `tax_account` | Tax Account | Link → `Account` | **requis**; colonne de liste |
| `zip_file` | Zip File | Attach |  |
| `status` | Status | Text | lecture seule |
| `invoice_series` | Invoice Series | Select — ACC-PINV-.YYYY.- | **requis** |
| `default_buying_price_list` | Default Buying Price List | Link → `Price List` | **requis** |

## Lower Deduction Certificate

*Lower Deduction Certificate* — `regional/lower_deduction_certificate.yaml`

- **Vues** : calendar
- **Titre** : `certificate_no`
- **Icône** : `file-badge`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `certificate_no` | Certificate No | Text | **requis**; colonne de liste |
| `supplier` | Supplier | Link → `Supplier` | **requis**; colonne de liste |
| `pan_no` | PAN No | Text | **requis**; colonne de liste |
| `valid_upto` | Valid Up To | Date | **requis** |
| `rate` | Rate Of TDS As Per Certificate | Percent | **requis** |
| `certificate_limit` | Certificate Limit | Currency | **requis**; devise de `company.default_currency` |
| `valid_from` | Valid From | Date | **requis**; colonne de liste |
| `fiscal_year` | Fiscal Year | Link → `Fiscal Year` | **requis** |
| `tax_withholding_category` | Tax Withholding Category | Link → `Tax Withholding Category` | **requis** |
| `company` | Company | Link → `Company` | **requis** |

## South Africa VAT Settings

*South Africa VAT Settings* — `regional/south_africa_vat_settings.yaml` · document unique

- **Titre** : `company`
- **Icône** : `percent`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `vat_accounts` | VAT Accounts | Table → `South Africa VAT Account` |  |

## UAE VAT Account

*UAE VAT Account* — `regional/uae_vat_account.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `account` | Account | Link → `Account` | colonne de liste |

## UAE VAT Settings

*UAE VAT Settings* — `regional/uae_vat_settings.yaml` · document unique

- **Titre** : `company`
- **Icône** : `percent`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `uae_vat_accounts` | UAE VAT Accounts | Table → `UAE VAT Account` |  |
