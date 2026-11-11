# Dépendances entre modules

Les dépendances naissent des **champs `Link`** : un DocType du module A qui pointe vers un DocType du module B fait dépendre A de B. Le moteur vérifie à l'écriture que la cible existe et est lisible, et **refuse la suppression** d'un document encore cité (`document_in_use`) — la protection vaut donc pour tout le jeu, à travers les frontières de modules.

## Lecture du graphe

- **« dépend de »** : liens sortants du module (ce qu'il cite).
- **« requis par »** : liens entrants (qui le cite). C'est la lecture symétrique : un module requis par beaucoup doit être chargé en premier.
- Le **nombre de liens** compte chaque champ `Link`/`DynamicLink` (y compris dans les tables enfants), pas le nombre de DocTypes.

## Synthèse

| Observation | Détail |
|---|---|
| Modules **feuilles** (aucun lien sortant) | `bulk_transaction`, `edi`, `erpnext_integrations`, `utilities` |
| Module le plus cité | `setup` (882 liens entrants), puis `stock` (258), `accounts` (248), `selling` (72) |
| Module le plus dépendant | `accounts` (355 liens sortants), puis `stock` (264), `hr` (220), `selling` (157) |
| Cycles majeurs | `setup` ↔ `accounts`, `setup` ↔ `stock`, `accounts` ↔ `selling`, `hr` ↔ `payroll`, `buying` ↔ `manufacturing` ↔ `stock` |

Les cycles ne sont pas des défauts : une pièce d'achat cite l'article (`buying` → `stock`) et l'article cite des comptes (`stock` → `accounts`) dont le plan (`setup` → …) cite des pièces. Le moteur tranche par le **chargement en modules pairs** (`load_dir(..., peers=True)`) : n'importe quel ordre de chargement des plugins fonctionne, un module en attente d'une cible devient simplement *incomplet* jusqu'à son arrivée — voir [Implémenter un module](integration.md#le-chargement-en-mode-pairs).

## Matrice « dépend de » (nombre de liens `Link` sortants)

| ↓ dépend de → | accounts | assets | bulk_transaction | buying | communication | crm | edi | erpnext_integrations | hr | maintenance | manufacturing | payroll | projects | quality_management | regional | selling | setup | stock | subcontracting | support | telephony | utilities |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **accounts** | · | 5 | · | 10 | 2 | 19 | · | · | · | · | · | · | 27 | · | 1 | 22 | 215 | 54 | · | · | · | · |
| **assets** | 28 | · | · | 1 | · | · | · | · | · | · | · | · | 3 | · | · | 1 | 18 | 12 | · | · | · | · |
| **bulk_transaction** | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · |
| **buying** | 29 | 1 | · | · | 2 | 7 | · | · | · | · | 5 | · | 5 | · | · | 5 | 60 | 25 | · | · | · | 1 |
| **communication** | · | · | · | 1 | · | · | · | · | · | · | · | · | · | · | · | · | 2 | · | · | · | · | · |
| **crm** | · | · | · | · | 1 | · | · | · | · | · | · | · | · | · | · | 4 | 21 | 1 | · | · | · | · |
| **edi** | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · |
| **erpnext_integrations** | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · |
| **hr** | 19 | 1 | · | 3 | 5 | · | · | · | · | · | · | 9 | 7 | · | · | · | 175 | 1 | · | · | · | · |
| **maintenance** | · | · | · | · | · | 2 | · | · | · | · | · | · | · | · | · | 3 | 11 | 5 | · | · | · | · |
| **manufacturing** | 1 | · | · | 5 | · | · | · | · | · | · | · | · | 5 | · | · | 9 | 49 | 77 | 1 | · | · | · |
| **payroll** | 17 | · | · | · | 3 | · | · | · | 5 | · | · | · | 2 | · | · | · | 73 | · | · | · | · | · |
| **projects** | 3 | · | · | · | · | · | · | · | · | · | · | · | · | · | · | 3 | 11 | · | · | 1 | · | · |
| **quality_management** | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | 2 | · | · | · | · | · |
| **regional** | 5 | · | · | 1 | · | · | · | · | · | · | · | · | · | · | · | · | 5 | 2 | · | · | · | · |
| **selling** | 30 | · | · | 5 | 1 | 19 | · | · | · | · | 3 | · | 3 | · | · | · | 73 | 22 | · | · | · | 1 |
| **setup** | 50 | · | · | 1 | · | 1 | · | · | · | · | · | · | · | · | · | 2 | · | 13 | · | · | · | · |
| **stock** | 57 | 8 | · | 14 | 1 | 10 | · | · | · | · | 12 | · | 10 | · | · | 18 | 131 | · | 3 | · | · | · |
| **subcontracting** | 9 | · | · | 4 | · | 2 | · | · | · | · | 6 | · | 4 | · | · | 2 | 28 | 44 | · | · | · | · |
| **support** | · | · | · | · | 1 | 3 | · | · | · | · | · | · | 1 | · | · | 2 | 6 | 2 | · | · | · | · |
| **telephony** | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | 1 | 2 | · | · | · | · | · |
| **utilities** | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · | · |

## Comptabilité (`accounts`)

**Dépend de** :
- `setup` (215 liens) — `Address`, `Auto Repeat`, `Brand`, `Company`, `Country`, `Currency` (+15 autres)
- `stock` (54 liens) — `Batch`, `Delivery Note`, `Item`, `Manufacturer`, `Material Request`, `Packed Item` (+7 autres)
- `projects` (27 liens) — `Activity Type`, `Project`, `Timesheet`
- `selling` (22 liens) — `Customer`, `Product Bundle`, `Sales Order`, `Sales Team`
- `crm` (19 liens) — `Contact`, `UTM Campaign`, `UTM Medium`, `UTM Source`
- `buying` (10 liens) — `Purchase Order`, `Purchase Receipt Item Supplied`, `Supplier`
- `assets` (5 liens) — `Asset`, `Asset Category`, `Location`
- `communication` (2 liens) — `Email Account`, `Email Template`
- `regional` (1 liens) — `Lower Deduction Certificate`

**Requis par** :
- `stock` (57 liens) — `Account`, `Cost Center`, `Item Tax Template`, `Item Wise Tax Detail`, `Journal Entry`, `Pricing Rule Detail` (+9 autres)
- `setup` (50 liens) — `Account`, `Cost Center`, `Finance Book`, `Fiscal Year`, `Monthly Distribution`, `Party Account` (+2 autres)
- `selling` (30 liens) — `Allowed To Transact With`, `Bank Account`, `Cost Center`, `Coupon Code`, `Item Tax Template`, `Item Wise Tax Detail` (+11 autres)
- `buying` (29 liens) — `Account`, `Allowed To Transact With`, `Bank Account`, `Cost Center`, `Item Tax Template`, `Item Wise Tax Detail` (+10 autres)
- `assets` (28 liens) — `Account`, `Cost Center`, `Finance Book`, `Journal Entry`, `Purchase Invoice`
- `hr` (19 liens) — `Account`, `Cost Center`, `Mode of Payment`
- `payroll` (17 liens) — `Account`, `Bank Account`, `Cost Center`, `Journal Entry`, `Mode of Payment`
- `subcontracting` (9 liens) — `Account`, `Cost Center`
- `regional` (5 liens) — `Account`, `Fiscal Year`, `South Africa VAT Account`, `Tax Withholding Category`
- `projects` (3 liens) — `Cost Center`, `Sales Invoice`
- `manufacturing` (1 liens) — `Account`

## Immobilisations (`assets`)

**Dépend de** :
- `accounts` (28 liens) — `Account`, `Cost Center`, `Finance Book`, `Journal Entry`, `Purchase Invoice`
- `setup` (18 liens) — `Company`, `Department`, `Employee`, `UOM`
- `stock` (12 liens) — `Batch`, `Item`, `Purchase Receipt`, `Serial and Batch Bundle`, `Warehouse`
- `projects` (3 liens) — `Project`
- `buying` (1 liens) — `Supplier`
- `selling` (1 liens) — `Customer`

**Requis par** :
- `stock` (8 liens) — `Asset`, `Asset Category`, `Asset Repair`, `Location`
- `accounts` (5 liens) — `Asset`, `Asset Category`, `Location`
- `buying` (1 liens) — `Asset`
- `hr` (1 liens) — `Asset Movement`

## Traitement en masse (`bulk_transaction`)

**Dépend de** : personne — module feuille.

**Requis par** : personne pour l'instant.

## Achats (`buying`)

**Dépend de** :
- `setup` (60 liens) — `Address`, `Auto Repeat`, `Brand`, `Company`, `Country`, `Currency` (+10 autres)
- `accounts` (29 liens) — `Account`, `Allowed To Transact With`, `Bank Account`, `Cost Center`, `Item Tax Template`, `Item Wise Tax Detail` (+10 autres)
- `stock` (25 liens) — `Batch`, `Company Restriction`, `Item`, `Manufacturer`, `Material Request`, `Price List` (+1 autres)
- `crm` (7 liens) — `Contact`, `Opportunity`
- `manufacturing` (5 liens) — `BOM`, `Blanket Order`, `Job Card`, `Master Production Schedule`, `Production Plan`
- `projects` (5 liens) — `Project`
- `selling` (5 liens) — `Customer`, `Product Bundle`, `Sales Order`
- `communication` (2 liens) — `Email Account`, `Email Template`
- `assets` (1 liens) — `Asset`
- `utilities` (1 liens) — `Portal User`

**Requis par** :
- `stock` (14 liens) — `Purchase Order`, `Purchase Receipt Item Supplied`, `Supplier`
- `accounts` (10 liens) — `Purchase Order`, `Purchase Receipt Item Supplied`, `Supplier`
- `manufacturing` (5 liens) — `Purchase Order`, `Supplier`
- `selling` (5 liens) — `Purchase Order`, `Supplier`, `Supplier Quotation`
- `subcontracting` (4 liens) — `Purchase Order`, `Supplier`
- `hr` (3 liens) — `Supplier`
- `assets` (1 liens) — `Supplier`
- `communication` (1 liens) — `Supplier`
- `regional` (1 liens) — `Supplier`
- `setup` (1 liens) — `Supplier`

## Communication (`communication`)

**Dépend de** :
- `setup` (2 liens) — `Employee Group`
- `buying` (1 liens) — `Supplier`

**Requis par** :
- `hr` (5 liens) — `Email Account`, `Email Template`
- `payroll` (3 liens) — `Email Account`, `Email Template`
- `accounts` (2 liens) — `Email Account`, `Email Template`
- `buying` (2 liens) — `Email Account`, `Email Template`
- `crm` (1 liens) — `Email Template`
- `selling` (1 liens) — `Email Template`
- `stock` (1 liens) — `Email Template`
- `support` (1 liens) — `Email Account`

## CRM (`crm`)

**Dépend de** :
- `setup` (21 liens) — `Address`, `Brand`, `Company`, `Country`, `Currency`, `Customer Group` (+7 autres)
- `selling` (4 liens) — `Customer`, `Industry Type`
- `communication` (1 liens) — `Email Template`
- `stock` (1 liens) — `Item`

**Requis par** :
- `accounts` (19 liens) — `Contact`, `UTM Campaign`, `UTM Medium`, `UTM Source`
- `selling` (19 liens) — `Competitor Detail`, `Contact`, `Lead`, `Market Segment`, `Opportunity`, `Prospect` (+3 autres)
- `stock` (10 liens) — `Contact`, `UTM Campaign`, `UTM Medium`, `UTM Source`
- `buying` (7 liens) — `Contact`, `Opportunity`
- `support` (3 liens) — `Contact`, `Lead`
- `maintenance` (2 liens) — `Contact`
- `subcontracting` (2 liens) — `Contact`
- `setup` (1 liens) — `Contact`

## EDI (`edi`)

**Dépend de** : personne — module feuille.

**Requis par** : personne pour l'instant.

## Intégrations ERPNext (`erpnext_integrations`)

**Dépend de** : personne — module feuille.

**Requis par** : personne pour l'instant.

## Ressources humaines (`hr`)

**Dépend de** :
- `setup` (175 liens) — `Branch`, `Company`, `Country`, `Currency`, `Department`, `Designation` (+7 autres)
- `accounts` (19 liens) — `Account`, `Cost Center`, `Mode of Payment`
- `payroll` (9 liens) — `Additional Salary`, `Payroll Entry`, `Salary Component`, `Salary Slip`, `Salary Structure`
- `projects` (7 liens) — `Project`, `Task`
- `communication` (5 liens) — `Email Account`, `Email Template`
- `buying` (3 liens) — `Supplier`
- `assets` (1 liens) — `Asset Movement`
- `stock` (1 liens) — `Delivery Trip`

**Requis par** :
- `payroll` (5 liens) — `Employee Grade`, `Employment Type`, `Leave Type`

## Maintenance (`maintenance`)

**Dépend de** :
- `setup` (11 liens) — `Address`, `Company`, `Customer Group`, `Sales Person`, `Territory`
- `stock` (5 liens) — `Item`, `Serial No`, `Serial and Batch Bundle`
- `selling` (3 liens) — `Customer`, `Sales Order`
- `crm` (2 liens) — `Contact`

**Requis par** : personne pour l'instant.

## Fabrication (`manufacturing`)

**Dépend de** :
- `stock` (77 liens) — `Batch`, `Item`, `Material Request`, `Price List`, `Quality Inspection`, `Quality Inspection Template` (+2 autres)
- `setup` (49 liens) — `Company`, `Currency`, `Employee`, `Error Log`, `Holiday List`, `Item Group` (+2 autres)
- `selling` (9 liens) — `Customer`, `Sales Order`
- `buying` (5 liens) — `Purchase Order`, `Supplier`
- `projects` (5 liens) — `Project`
- `accounts` (1 liens) — `Account`
- `subcontracting` (1 liens) — `Subcontracting Inward Order`

**Requis par** :
- `stock` (12 liens) — `BOM`, `Job Card`, `Production Plan`, `Work Order`
- `subcontracting` (6 liens) — `BOM`, `Job Card`
- `buying` (5 liens) — `BOM`, `Blanket Order`, `Job Card`, `Master Production Schedule`, `Production Plan`
- `selling` (3 liens) — `BOM`, `Blanket Order`

## Paie (`payroll`)

**Dépend de** :
- `setup` (73 liens) — `Branch`, `Company`, `Currency`, `Department`, `Designation`, `Employee` (+1 autres)
- `accounts` (17 liens) — `Account`, `Bank Account`, `Cost Center`, `Journal Entry`, `Mode of Payment`
- `hr` (5 liens) — `Employee Grade`, `Employment Type`, `Leave Type`
- `communication` (3 liens) — `Email Account`, `Email Template`
- `projects` (2 liens) — `Project`, `Timesheet`

**Requis par** :
- `hr` (9 liens) — `Additional Salary`, `Payroll Entry`, `Salary Component`, `Salary Slip`, `Salary Structure`

## Projets (`projects`)

**Dépend de** :
- `setup` (11 liens) — `Company`, `Currency`, `Department`, `Employee`, `Holiday List`
- `accounts` (3 liens) — `Cost Center`, `Sales Invoice`
- `selling` (3 liens) — `Customer`, `Sales Order`
- `support` (1 liens) — `Issue`

**Requis par** :
- `accounts` (27 liens) — `Activity Type`, `Project`, `Timesheet`
- `stock` (10 liens) — `Project`
- `hr` (7 liens) — `Project`, `Task`
- `buying` (5 liens) — `Project`
- `manufacturing` (5 liens) — `Project`
- `subcontracting` (4 liens) — `Project`
- `assets` (3 liens) — `Project`
- `selling` (3 liens) — `Project`
- `payroll` (2 liens) — `Project`, `Timesheet`
- `support` (1 liens) — `Project`

## Qualité (`quality_management`)

**Dépend de** :
- `setup` (2 liens) — `UOM`

**Requis par** : personne pour l'instant.

## Régionalisation (`regional`)

**Dépend de** :
- `accounts` (5 liens) — `Account`, `Fiscal Year`, `South Africa VAT Account`, `Tax Withholding Category`
- `setup` (5 liens) — `Company`, `Supplier Group`
- `stock` (2 liens) — `Item`, `Price List`
- `buying` (1 liens) — `Supplier`

**Requis par** :
- `accounts` (1 liens) — `Lower Deduction Certificate`

## Ventes (`selling`)

**Dépend de** :
- `setup` (73 liens) — `Address`, `Auto Repeat`, `Branch`, `Brand`, `Company`, `Currency` (+15 autres)
- `accounts` (30 liens) — `Allowed To Transact With`, `Bank Account`, `Cost Center`, `Coupon Code`, `Item Tax Template`, `Item Wise Tax Detail` (+11 autres)
- `stock` (22 liens) — `Company Restriction`, `Item`, `Material Request`, `Packed Item`, `Price List`, `Serial and Batch Bundle` (+1 autres)
- `crm` (19 liens) — `Competitor Detail`, `Contact`, `Lead`, `Market Segment`, `Opportunity`, `Prospect` (+3 autres)
- `buying` (5 liens) — `Purchase Order`, `Supplier`, `Supplier Quotation`
- `manufacturing` (3 liens) — `BOM`, `Blanket Order`
- `projects` (3 liens) — `Project`
- `communication` (1 liens) — `Email Template`
- `utilities` (1 liens) — `Portal User`

**Requis par** :
- `accounts` (22 liens) — `Customer`, `Product Bundle`, `Sales Order`, `Sales Team`
- `stock` (18 liens) — `Customer`, `Product Bundle`, `Sales Order`, `Sales Team`
- `manufacturing` (9 liens) — `Customer`, `Sales Order`
- `buying` (5 liens) — `Customer`, `Product Bundle`, `Sales Order`
- `crm` (4 liens) — `Customer`, `Industry Type`
- `maintenance` (3 liens) — `Customer`, `Sales Order`
- `projects` (3 liens) — `Customer`, `Sales Order`
- `setup` (2 liens) — `Customer Credit Limit`, `Sales Partner Type`
- `subcontracting` (2 liens) — `Customer`, `Sales Order`
- `support` (2 liens) — `Customer`
- `assets` (1 liens) — `Customer`
- `telephony` (1 liens) — `Customer`

## Configuration (`setup`)

**Dépend de** :
- `accounts` (50 liens) — `Account`, `Cost Center`, `Finance Book`, `Fiscal Year`, `Monthly Distribution`, `Party Account` (+2 autres)
- `stock` (13 liens) — `Item Default`, `Item Tax`, `Price List`, `UOM Category`, `Warehouse`
- `selling` (2 liens) — `Customer Credit Limit`, `Sales Partner Type`
- `buying` (1 liens) — `Supplier`
- `crm` (1 liens) — `Contact`

**Requis par** :
- `accounts` (215 liens) — `Address`, `Auto Repeat`, `Brand`, `Company`, `Country`, `Currency` (+15 autres)
- `hr` (175 liens) — `Branch`, `Company`, `Country`, `Currency`, `Department`, `Designation` (+7 autres)
- `stock` (131 liens) — `Address`, `Auto Repeat`, `Brand`, `Company`, `Country`, `Currency` (+14 autres)
- `payroll` (73 liens) — `Branch`, `Company`, `Currency`, `Department`, `Designation`, `Employee` (+1 autres)
- `selling` (73 liens) — `Address`, `Auto Repeat`, `Branch`, `Brand`, `Company`, `Currency` (+15 autres)
- `buying` (60 liens) — `Address`, `Auto Repeat`, `Brand`, `Company`, `Country`, `Currency` (+10 autres)
- `manufacturing` (49 liens) — `Company`, `Currency`, `Employee`, `Error Log`, `Holiday List`, `Item Group` (+2 autres)
- `subcontracting` (28 liens) — `Address`, `Auto Repeat`, `Brand`, `Company`, `Currency`, `Letter Head` (+2 autres)
- `crm` (21 liens) — `Address`, `Brand`, `Company`, `Country`, `Currency`, `Customer Group` (+7 autres)
- `assets` (18 liens) — `Company`, `Department`, `Employee`, `UOM`
- `maintenance` (11 liens) — `Address`, `Company`, `Customer Group`, `Sales Person`, `Territory`
- `projects` (11 liens) — `Company`, `Currency`, `Department`, `Employee`, `Holiday List`
- `support` (6 liens) — `Address`, `Company`, `Customer Group`, `Holiday List`, `Territory`
- `regional` (5 liens) — `Company`, `Supplier Group`
- `communication` (2 liens) — `Employee Group`
- `quality_management` (2 liens) — `UOM`
- `telephony` (2 liens) — `Employee`, `Employee Group`

## Stock (`stock`)

**Dépend de** :
- `setup` (131 liens) — `Address`, `Auto Repeat`, `Brand`, `Company`, `Country`, `Currency` (+14 autres)
- `accounts` (57 liens) — `Account`, `Cost Center`, `Item Tax Template`, `Item Wise Tax Detail`, `Journal Entry`, `Pricing Rule Detail` (+9 autres)
- `selling` (18 liens) — `Customer`, `Product Bundle`, `Sales Order`, `Sales Team`
- `buying` (14 liens) — `Purchase Order`, `Purchase Receipt Item Supplied`, `Supplier`
- `manufacturing` (12 liens) — `BOM`, `Job Card`, `Production Plan`, `Work Order`
- `crm` (10 liens) — `Contact`, `UTM Campaign`, `UTM Medium`, `UTM Source`
- `projects` (10 liens) — `Project`
- `assets` (8 liens) — `Asset`, `Asset Category`, `Asset Repair`, `Location`
- `subcontracting` (3 liens) — `Subcontracting Inward Order`, `Subcontracting Order`, `Subcontracting Receipt`
- `communication` (1 liens) — `Email Template`

**Requis par** :
- `manufacturing` (77 liens) — `Batch`, `Item`, `Material Request`, `Price List`, `Quality Inspection`, `Quality Inspection Template` (+2 autres)
- `accounts` (54 liens) — `Batch`, `Delivery Note`, `Item`, `Manufacturer`, `Material Request`, `Packed Item` (+7 autres)
- `subcontracting` (44 liens) — `Batch`, `Item`, `Landed Cost Taxes and Charges`, `Manufacturer`, `Material Request`, `Quality Inspection` (+2 autres)
- `buying` (25 liens) — `Batch`, `Company Restriction`, `Item`, `Manufacturer`, `Material Request`, `Price List` (+1 autres)
- `selling` (22 liens) — `Company Restriction`, `Item`, `Material Request`, `Packed Item`, `Price List`, `Serial and Batch Bundle` (+1 autres)
- `setup` (13 liens) — `Item Default`, `Item Tax`, `Price List`, `UOM Category`, `Warehouse`
- `assets` (12 liens) — `Batch`, `Item`, `Purchase Receipt`, `Serial and Batch Bundle`, `Warehouse`
- `maintenance` (5 liens) — `Item`, `Serial No`, `Serial and Batch Bundle`
- `regional` (2 liens) — `Item`, `Price List`
- `support` (2 liens) — `Item`, `Serial No`
- `crm` (1 liens) — `Item`
- `hr` (1 liens) — `Delivery Trip`

## Sous-traitance (`subcontracting`)

**Dépend de** :
- `stock` (44 liens) — `Batch`, `Item`, `Landed Cost Taxes and Charges`, `Manufacturer`, `Material Request`, `Quality Inspection` (+2 autres)
- `setup` (28 liens) — `Address`, `Auto Repeat`, `Brand`, `Company`, `Currency`, `Letter Head` (+2 autres)
- `accounts` (9 liens) — `Account`, `Cost Center`
- `manufacturing` (6 liens) — `BOM`, `Job Card`
- `buying` (4 liens) — `Purchase Order`, `Supplier`
- `projects` (4 liens) — `Project`
- `crm` (2 liens) — `Contact`
- `selling` (2 liens) — `Customer`, `Sales Order`

**Requis par** :
- `stock` (3 liens) — `Subcontracting Inward Order`, `Subcontracting Order`, `Subcontracting Receipt`
- `manufacturing` (1 liens) — `Subcontracting Inward Order`

## Support (`support`)

**Dépend de** :
- `setup` (6 liens) — `Address`, `Company`, `Customer Group`, `Holiday List`, `Territory`
- `crm` (3 liens) — `Contact`, `Lead`
- `selling` (2 liens) — `Customer`
- `stock` (2 liens) — `Item`, `Serial No`
- `communication` (1 liens) — `Email Account`
- `projects` (1 liens) — `Project`

**Requis par** :
- `projects` (1 liens) — `Issue`

## Téléphonie (`telephony`)

**Dépend de** :
- `setup` (2 liens) — `Employee`, `Employee Group`
- `selling` (1 liens) — `Customer`

**Requis par** : personne pour l'instant.

## Utilitaires (`utilities`)

**Dépend de** : personne — module feuille.

**Requis par** :
- `buying` (1 liens) — `Portal User`
- `selling` (1 liens) — `Portal User`

