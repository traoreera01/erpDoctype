# Paie (`payroll`)

La rémunération : structures de salaire et composantes, bulletins, entrées de paie en masse, avantages, retenues et exonerations fiscales, primes et indemnités de fin de contrat.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 42 | 17 | 17 | 1 | 0 | 17 | 444 |

## Espace de travail

**Espace « Paie »** (icône `wallet`, position 60) — Préparation des paies, bulletins et éléments de rémunération.

- **Traitement de la paie** : [`Payroll Entry`](../reference/payroll.md#payroll-entry) — création, [`Salary Slip`](../reference/payroll.md#salary-slip) — création, [`Additional Salary`](../reference/payroll.md#additional-salary) — création, [`Employee Benefit Application`](../reference/payroll.md#employee-benefit-application) — création
- **Référentiel** : [`Salary Structure`](../reference/payroll.md#salary-structure) — création, [`Salary Component`](../reference/payroll.md#salary-component) — création, [`Payroll Period`](../reference/payroll.md#payroll-period) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Bulk Salary Structure Assignment`](../reference/payroll.md#bulk-salary-structure-assignment) | Bulk Salary Structure Assignment | données de base |  |  |  |
| [`Employee Benefit Ledger`](../reference/payroll.md#employee-benefit-ledger) | Employee Benefit Ledger | données de base |  |  |  |
| [`Employee Tax Exemption Category`](../reference/payroll.md#employee-tax-exemption-category) | Employee Tax Exemption Category | données de base |  |  |  |
| [`Employee Tax Exemption Sub Category`](../reference/payroll.md#employee-tax-exemption-sub-category) | Employee Tax Exemption Sub Category | données de base |  |  |  |
| [`Gratuity Rule`](../reference/payroll.md#gratuity-rule) | Gratuity Rule | données de base |  |  |  |
| [`Payroll Period`](../reference/payroll.md#payroll-period) | Payroll Period | données de base |  |  |  |
| [`Salary Component`](../reference/payroll.md#salary-component) | Salary Component | données de base |  |  |  |
| [`Employee Benefit Application Detail`](../reference/payroll.md#employee-benefit-application-detail) | Employee Benefit Application Detail | enfant |  |  |  |
| [`Employee Benefit Detail`](../reference/payroll.md#employee-benefit-detail) | Employee Benefit Detail | enfant |  |  |  |
| [`Employee Cost Center`](../reference/payroll.md#employee-cost-center) | Employee Cost Center | enfant |  |  |  |
| [`Employee Tax Exemption Declaration Category`](../reference/payroll.md#employee-tax-exemption-declaration-category) | Employee Tax Exemption Declaration Category | enfant |  |  |  |
| [`Employee Tax Exemption Proof Submission Detail`](../reference/payroll.md#employee-tax-exemption-proof-submission-detail) | Employee Tax Exemption Proof Submission Detail | enfant |  |  |  |
| [`Gratuity Applicable Component`](../reference/payroll.md#gratuity-applicable-component) | Gratuity Applicable Component | enfant |  |  |  |
| [`Gratuity Rule Slab`](../reference/payroll.md#gratuity-rule-slab) | Gratuity Rule Slab | enfant |  |  |  |
| [`Income Tax Slab Other Charges`](../reference/payroll.md#income-tax-slab-other-charges) | Income Tax Slab Other Charges | enfant |  |  |  |
| [`Payroll Correction Child`](../reference/payroll.md#payroll-correction-child) | Payroll Correction Child | enfant |  |  |  |
| [`Payroll Employee Detail`](../reference/payroll.md#payroll-employee-detail) | Payroll Employee Detail | enfant |  |  |  |
| [`Payroll Period Date`](../reference/payroll.md#payroll-period-date) | Payroll Period Date | enfant |  |  |  |
| [`Salary Component Account`](../reference/payroll.md#salary-component-account) | Salary Component Account | enfant |  |  |  |
| [`Salary Detail`](../reference/payroll.md#salary-detail) | Salary Detail | enfant |  |  |  |
| [`Salary Slip Leave`](../reference/payroll.md#salary-slip-leave) | Salary Slip Leave | enfant |  |  |  |
| [`Salary Slip Timesheet`](../reference/payroll.md#salary-slip-timesheet) | Salary Slip Timesheet | enfant |  |  |  |
| [`Salary Withholding Cycle`](../reference/payroll.md#salary-withholding-cycle) | Salary Withholding Cycle | enfant |  |  |  |
| [`Taxable Salary Slab`](../reference/payroll.md#taxable-salary-slab) | Taxable Salary Slab | enfant |  |  |  |
| [`Additional Salary`](../reference/payroll.md#additional-salary) | Additional Salary | pièce | oui | `AS-{YYYY}-{#####}` |  |
| [`Arrear`](../reference/payroll.md#arrear) | Arrear | pièce | oui | `ARRE-{YYYY}-{#####}` |  |
| [`Employee Benefit Application`](../reference/payroll.md#employee-benefit-application) | Employee Benefit Application | pièce | oui | `EBA-{YYYY}-{#####}` |  |
| [`Employee Benefit Claim`](../reference/payroll.md#employee-benefit-claim) | Employee Benefit Claim | pièce | oui | `EBC-{YYYY}-{#####}` |  |
| [`Employee Incentive`](../reference/payroll.md#employee-incentive) | Employee Incentive | pièce | oui | `EI-{YYYY}-{#####}` |  |
| [`Employee Other Income`](../reference/payroll.md#employee-other-income) | Employee Other Income | pièce | oui | `EOI-{YYYY}-{#####}` |  |
| [`Employee Tax Exemption Declaration`](../reference/payroll.md#employee-tax-exemption-declaration) | Employee Tax Exemption Declaration | pièce | oui | `ETED-{YYYY}-{#####}` |  |
| [`Employee Tax Exemption Proof Submission`](../reference/payroll.md#employee-tax-exemption-proof-submission) | Employee Tax Exemption Proof Submission | pièce | oui | `ETEPS-{YYYY}-{#####}` |  |
| [`Gratuity`](../reference/payroll.md#gratuity) | Gratuity | pièce | oui | `GRAT-{YYYY}-{#####}` |  |
| [`Income Tax Slab`](../reference/payroll.md#income-tax-slab) | Income Tax Slab | pièce | oui | `ITS-{YYYY}-{#####}` |  |
| [`Payroll Correction`](../reference/payroll.md#payroll-correction) | Payroll Correction | pièce | oui | `PC-{YYYY}-{#####}` |  |
| [`Payroll Entry`](../reference/payroll.md#payroll-entry) | Payroll Entry | pièce | oui | `PAEN-{YYYY}-{#####}` |  |
| [`Retention Bonus`](../reference/payroll.md#retention-bonus) | Retention Bonus | pièce | oui | `RB-{YYYY}-{#####}` |  |
| [`Salary Slip`](../reference/payroll.md#salary-slip) | Salary Slip | pièce | oui | `SS-{YYYY}-{#####}` |  |
| [`Salary Structure`](../reference/payroll.md#salary-structure) | Salary Structure | pièce | oui | `SAST-{YYYY}-{#####}` |  |
| [`Salary Structure Assignment`](../reference/payroll.md#salary-structure-assignment) | Salary Structure Assignment | pièce | oui | `SSA-{YYYY}-{#####}` |  |
| [`Salary Withholding`](../reference/payroll.md#salary-withholding) | Salary Withholding | pièce | oui | `SW-{YYYY}-{#####}` |  |
| [`Payroll Settings`](../reference/payroll.md#payroll-settings) | Payroll Settings | unique |  |  |  |

## Points clés

- **Le trio central** : `Salary Structure` (SAST-, les composantes de gains et retenues avec formules `compute`) → `Salary Structure Assignment` (SSA-, rattachée à un employé pour une période) → `Salary Slip` (SS-, le bulletin calculé, avec temps et congés reportés).
- **`Payroll Entry`** (PAEN-) : la paie mensuelle en masse — elle énumère les employés (`Payroll Employee Detail`) et génère les bulletins à sa soumission.
- **Les composantes variables** : `Additional Salary` (AS-), `Employee Incentive` (EI-), `Retention Bonus` (RB-), `Employee Benefit Application/Claim` (EBA-/EBC-), `Salary Withholding` (SW-, salaire retenu) — toutes des pièces soumises qui entrent dans le calcul du bulletin.
- **La fiscalité** : `Income Tax Slab` (ITS-, barèmes), déclarations et justificatifs d'exonération (`Employee Tax Exemption Declaration/Proof Submission`), `Payroll Period` (les périodes).
- **`Salary Component`** : le référentiel des rubriques, chacune reliée à son compte comptable (`Salary Component Account`) — la passerelle vers `accounts`.

## Dépendances

- **Dépend de** : `setup` (73 liens), `accounts` (17), `hr` (5), `communication` (3), `projects` (2).
- **Requis par** : `hr` (9 — `hr` référence les bulletins dans l'historique de salaire de l'employé).

Détail complet : [matrice](../dependances.md#paie-payroll).

## Implémentation en plugin xcore

- Plugin `payroll`, ordre P4 avec `hr` — le cycle hr ↔ payroll (9 liens chaque sens) exige le mode pairs.
- **Hooks à écrire** : génération des bulletins à la soumission de `Payroll Entry` (calcul par structure + composantes variables de la période), provision comptable de la masse salariale (`Journal Entry` dans `accounts`), régularisation à l'annulation, accumulation des avantages sur `Employee Benefit Ledger`.
- **Invariant sensible** : un bulletin par employé et par période — à garantir par un champ `unique` ou le contrôle transactionnel `tx.find` du moteur.

## Référence complète

[Référence — Paie](../reference/payroll.md).
