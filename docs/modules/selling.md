# Ventes (`selling`)

Le cycle client : devis, commandes, proforma, facturation (POS), bundles et fiche client — avec les équipes de vente et les limites de crédit.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 20 | 5 | 8 | 1 | 0 | 5 | 529 |

## Espace de travail

**Espace « Ventes »** (icône `shopping-cart`, position 10)

- **Opérations** : [`Quotation`](../reference/selling.md#quotation) — création, [`Sales Order`](../reference/selling.md#sales-order) — création, [`Installation Note`](../reference/selling.md#installation-note) — création, [`Proforma Invoice`](../reference/selling.md#proforma-invoice) — création
- **Référentiel** : [`Customer`](../reference/selling.md#customer) — création, [`Product Bundle`](../reference/selling.md#product-bundle) — création, [`Industry Type`](../reference/selling.md#industry-type) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Customer`](../reference/selling.md#customer) | Customer | données de base |  |  |  |
| [`Delivery Schedule Item`](../reference/selling.md#delivery-schedule-item) | Delivery Schedule Item | données de base |  |  |  |
| [`Industry Type`](../reference/selling.md#industry-type) | Industry Type | données de base |  |  |  |
| [`Party Specific Item`](../reference/selling.md#party-specific-item) | Party Specific Item | données de base |  |  |  |
| [`Sales Partner Type`](../reference/selling.md#sales-partner-type) | Sales Partner Type | données de base |  |  |  |
| [`SMS Center`](../reference/selling.md#sms-center) | SMS Center | données de base |  |  |  |
| [`Customer Credit Limit`](../reference/selling.md#customer-credit-limit) | Customer Credit Limit | enfant |  |  |  |
| [`Installation Note Item`](../reference/selling.md#installation-note-item) | Installation Note Item | enfant |  |  |  |
| [`Product Bundle Item`](../reference/selling.md#product-bundle-item) | Product Bundle Item | enfant |  |  |  |
| [`Proforma Invoice Item`](../reference/selling.md#proforma-invoice-item) | Proforma Invoice Item | enfant |  |  |  |
| [`Quotation Item`](../reference/selling.md#quotation-item) | Quotation Item | enfant |  |  |  |
| [`Sales Order Item`](../reference/selling.md#sales-order-item) | Sales Order Item | enfant |  |  |  |
| [`Sales Team`](../reference/selling.md#sales-team) | Sales Team | enfant |  |  |  |
| [`Supplier Number At Customer`](../reference/selling.md#supplier-number-at-customer) | Supplier Number At Customer | enfant |  |  |  |
| [`Installation Note`](../reference/selling.md#installation-note) | Installation Note | pièce | oui | `IN-{YYYY}-{#####}` |  |
| [`Product Bundle`](../reference/selling.md#product-bundle) | Product Bundle | pièce | oui | `PB-{YYYY}-{#####}` |  |
| [`Proforma Invoice`](../reference/selling.md#proforma-invoice) | Proforma Invoice | pièce | oui | `PRIN-{YYYY}-{#####}` |  |
| [`Quotation`](../reference/selling.md#quotation) | Quotation | pièce | oui | `QUOT-{YYYY}-{#####}` |  |
| [`Sales Order`](../reference/selling.md#sales-order) | Sales Order | pièce | oui | `SO-{YYYY}-{#####}` |  |
| [`Selling Settings`](../reference/selling.md#selling-settings) | Selling Settings | unique |  |  |  |

## Points clés

- **Le cycle** : `Quotation` (QUOT-, 88 champs, motif de perte sur pièce) → `Sales Order` (SO-, 97 champs, vue gantt des livraisons) → `Delivery Note` et `Sales Invoice` (portées par `stock` et `accounts`), avec `Proforma Invoice` (PRIN-) en amont.
- **`Customer`** : le référentiel client — groupes, territoire, devise de facturation, comptes par société (`Party Account`), limites de crédit (`Customer Credit Limit`), blocage (`is_frozen`, `on_hold`), équipe de vente (`Sales Team` avec commissions).
- **`Product Bundle`** (PB-) : le lot de produits vendu comme un ensemble ; **`Installation Note`** (IN-) : la mise en service chez le client.
- **`Sales Partner`/`Sales Person`** (arborescence) et **`POS Invoice`/`POS Profile`** : la vente au comptoir.
- **`Customer`** lit ses contacts et adresses de `crm` et `setup` (19 liens vers chaque).

## Dépendances

- **Dépend de** : `setup` (73 liens), `accounts` (30), `stock` (22), `crm` (19), `buying` (5), `projects` (3), `manufacturing` (3), `communication` (1), `utilities` (1).
- **Requis par** : `accounts` (22), `stock` (18), `buying` (5), `crm` (4), `manufacturing` (9), `subcontracting` (2), `support` (2), `maintenance` (3), `setup` (2), `telephony` (1), `assets` (1).

Détail complet : [matrice](../dependances.md#ventes-selling).

## Implémentation en plugin xcore

- Plugin `selling`, ordre P3 avec `buying` — le premier module à exposer au Desk (ordre d'affichage 10 dans l'espace de travail).
- **Hooks à écrire** : contrôle de la limite de crédit à la soumission de la commande/facture, recopie devis → commande → facture, exigence de bon de livraison (`dn_required`), calcul des commissions `Sales Team`, écriture comptable de `Sales Invoice` (dans `accounts`).
- **`Sales Order` doit refuser la modification après confirmation** : figée par le `docstatus`, mais les quantités livrées/facturées se maintiennent par hooks (`tx.update` en `allow_on_submit`).

## Référence complète

[Référence — Ventes](../reference/selling.md).
