# Référence des champs — Ressources humaines (`hr`)

> Page **générée** par `docs/scripts/gen_reference.py` depuis les YAML de `hr/` (114 DocTypes). Ne pas éditer à la main : relancer le script.

1049 champs au total ; types les plus fréquents : `Link` (330), `Text` (152), `Boolean` (92), `Date` (90), `Select` (79).

## Appointment Letter

*Appointment Letter* — `hr/appointment_letter.yaml`

- **Titre** : `applicant_name`
- **Icône** : `mail-check`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `applicant_name` | Applicant Name | Text | **requis**; colonne de liste; lecture seule |
| `appointment_date` | Appointment Date | Date | **requis** |
| `appointment_letter_template` | Appointment Letter Template | Link → `Appointment Letter Template` | **requis** |
| `introduction` | Introduction | LongText | **requis** |
| `job_applicant` | Job Applicant | Link → `Job Applicant` | **requis** |
| `company` | Company | Link → `Company` | **requis** |
| `closing_notes` | Closing Notes | LongText |  |
| `terms` | Terms | Table → `Appointment Letter content` |  |

## Appointment Letter content

*Appointment Letter content* — `hr/appointment_letter_content.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text | **requis**; colonne de liste |
| `description` | Description | LongText | **requis**; colonne de liste |

## Appointment Letter Template

*Appointment Letter Template* — `hr/appointment_letter_template.yaml`

- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `introduction` | Introduction | LongText | **requis**; colonne de liste |
| `closing_notes` | Closing Notes | LongText |  |
| `terms` | Terms | Table → `Appointment Letter content` |  |
| `template_name` | Template Name | Text | **requis** |

## Appraisal

*Appraisal* — `hr/appraisal.yaml` · soumis

- **Numérotation** : série `APPR-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `employee_name`
- **Icône** : `star`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — HR-APR-.YYYY.- | **requis** |
| `employee` | Employee | Link → `Employee` | **requis** |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `company` | Company | Link → `Company` | **requis** |
| `designation` | Designation | Link → `Designation` | lecture seule |
| `appraisal_cycle` | Appraisal Cycle | Link → `Appraisal Cycle` | **requis**; colonne de liste |
| `appraisal_kra` | KRA vs Goals | Table → `Appraisal KRA` |  |
| `total_score` | Total Goal Score | Number | colonne de liste; lecture seule |
| `self_score` | Total Self Score | Number | lecture seule |
| `avg_feedback_score` | Average Feedback Score | Number | lecture seule; masqué |
| `employee_image` | Employee Image | Image | masqué |
| `appraisal_template` | Appraisal Template | Link → `Appraisal Template` |  |
| `reflections` | Reflections | TextEditor |  |
| `goals` | Goals | Table → `Appraisal Goal` |  |
| `remarks` | Remarks | LongText | — Any other remarks, noteworthy effort that should go in the records |
| `rate_goals_manually` | Rate Goals Manually | Boolean | lecture seule |
| `start_date` | Start Date | Date | lecture seule |
| `end_date` | End Date | Date | lecture seule |
| `goal_score_percentage` | Goal Score (%) | Number | lecture seule |
| `self_ratings` | Self Ratings | Table → `Employee Feedback Rating` |  |
| `final_score` | Final Score | Number | colonne de liste; lecture seule; — Average of Goal Score, Feedback Score, and Self Appraisal Score |

## Appraisal Cycle

*Appraisal Cycle* — `hr/appraisal_cycle.yaml`

- **Vues** : calendar, gantt
- **Titre** : `status`
- **Icône** : `refresh-cw`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `start_date` | Start Date | Date | **requis**; colonne de liste |
| `end_date` | End Date | Date | **requis**; colonne de liste |
| `description` | Description | TextEditor |  |
| `branch` | Branch | Link → `Branch` |  |
| `department` | Department | Link → `Department` |  |
| `designation` | Designation | Link → `Designation` |  |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `appraisees` | Appraisees | Table → `Appraisee` |  |
| `cycle_name` | Cycle Name | Text | **requis**; colonne de liste |
| `kra_evaluation_method` | KRA Evaluation Method | Select — Automated Based on Goal Progress · Manual Rating | défaut `Automated Based on Goal Progress` |
| `status` | Status | Select — Not Started · In Progress · Completed | colonne de liste; lecture seule; défaut `Not Started` |
| `final_score_formula` | Final Score Formula | Code |  |
| `calculate_final_score_based_on_formula` | Calculate Final Score based on Formula | Boolean | défaut `non`; — By default, the Final Score is calculated as the average of Goal Score, Feedback Score, and Self Appraisal Sco |

## Appraisal Goal

*Appraisal Goal* — `hr/appraisal_goal.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `kra` | Goal | LongText | **requis**; colonne de liste; — Key Responsibility Area |
| `per_weightage` | Weightage (%) | Number | **requis**; colonne de liste |
| `score` | Score | Number | colonne de liste |
| `score_earned` | Score Earned | Number | colonne de liste; lecture seule |

## Appraisal KRA

*Appraisal KRA* — `hr/appraisal_kra.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `kra` | KRA | Link → `KRA` | **requis**; colonne de liste; — Key Performance Area |
| `per_weightage` | Weightage (%) | Percent | **requis**; colonne de liste |
| `goal_completion` | Goal Completion (%) | Percent | colonne de liste; lecture seule |
| `goal_score` | Goal Score (weighted) | Number | colonne de liste; lecture seule |

## Appraisal Template

*Appraisal Template* — `hr/appraisal_template.yaml`

- **Titre** : `template_title`
- **Icône** : `clipboard-list`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `description` | Description | LongText | colonne de liste |
| `goals` | KRAs | Table → `Appraisal Template Goal` |  |
| `rating_criteria` | Rating Criteria | Table → `Employee Feedback Rating` | — Criteria based on which employee should be rated in Performance Feedback and Self Appraisal |
| `template_title` | Appraisal Template Title | Text | **requis**; colonne de liste |

## Appraisal Template Goal

*Appraisal Template Goal* — `hr/appraisal_template_goal.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `per_weightage` | Weightage (%) | Percent | **requis**; colonne de liste |
| `key_result_area` | KRA | Link → `KRA` | **requis**; colonne de liste; — Key Result Area |

## Appraisee

*Appraisee* — `hr/appraisee.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | colonne de liste; lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | colonne de liste; lecture seule |
| `designation` | Designation | Text | colonne de liste; lecture seule |
| `branch` | Branch | Link → `Branch` | colonne de liste; lecture seule |
| `appraisal_template` | Appraisal Template | Link → `Appraisal Template` | colonne de liste |

## Assignment Rule Day

*Jour de répartition* — `hr/assignment_rule_day.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `day` | Jour | Select — Monday · Tuesday · Wednesday · Thursday · Friday · Saturday · Sunday | **requis** |

## Attendance

*Attendance* — `hr/attendance.yaml` · soumis

- **Numérotation** : série `ATTE-{YYYY}-{#####}`
- **Vues** : kanban, calendar
- **Titre** : `employee_name`
- **Icône** : `calendar-check`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — HR-ATT-.YYYY.- | **requis** |
| `employee` | Employee | Link → `Employee` | **requis** |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `working_hours` | Working Hours | Number | lecture seule |
| `status` | Status | Select — Present · Absent · On Leave · Half Day · Work From Home | **requis**; défaut `Present` |
| `leave_type` | Leave Type | Link → `Leave Type` |  |
| `leave_application` | Leave Application | Link → `Leave Application` | lecture seule |
| `attendance_date` | Attendance Date | Date | **requis**; colonne de liste |
| `company` | Company | Link → `Company` | **requis**; lecture seule |
| `department` | Department | Link → `Department` | lecture seule |
| `shift` | Shift | Link → `Shift Type` |  |
| `attendance_request` | Attendance Request | Link → `Attendance Request` | lecture seule |
| `late_entry` | Late Entry | Boolean | défaut `non` |
| `early_exit` | Early Exit | Boolean | défaut `non` |
| `in_time` | In Time | Datetime | lecture seule |
| `out_time` | Out Time | Datetime | lecture seule |
| `half_day_status` | Status for Other Half | Select — Present · Absent |  |
| `modify_half_day_status` | modify_half_day_status | Boolean | masqué; défaut `non` |
| `overtime_type` | Overtime Type | Link → `Overtime Type` | lecture seule |
| `standard_working_hours` | Standard Working Hours | Number | lecture seule |
| `actual_overtime_duration` | Actual Overtime Duration | Number | lecture seule |

## Attendance Request

*Attendance Request* — `hr/attendance_request.yaml` · soumis

- **Numérotation** : série `ATRE-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `employee_name`
- **Icône** : `calendar-plus`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `company` | Company | Link → `Company` | **requis** |
| `from_date` | From Date | Date | **requis**; colonne de liste |
| `to_date` | To Date | Date | **requis**; colonne de liste |
| `half_day` | Half Day | Boolean | défaut `non` |
| `half_day_date` | Half Day Date | Date |  |
| `reason` | Reason | Select — Work From Home · On Duty | **requis**; colonne de liste |
| `explanation` | Explanation | LongText |  |
| `shift` | Shift | Link → `Shift Type` | — Note: Shift will not be overwritten in existing attendance records |
| `include_holidays` | Include Holidays | Boolean | défaut `non`; — Select if any of the days selected for request are holidays |

## Compensatory Leave Request

*Compensatory Leave Request* — `hr/compensatory_leave_request.yaml` · soumis

- **Numérotation** : série `CLR-{YYYY}-{#####}`
- **Titre** : `employee_name`
- **Icône** : `calendar-plus-2`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `leave_type` | Leave Type | Link → `Leave Type` |  |
| `leave_allocation` | Leave Allocation | Link → `Leave Allocation` | lecture seule |
| `work_from_date` | Work From Date | Date | **requis** |
| `work_end_date` | Work End Date | Date | **requis** |
| `half_day` | Half Day | Boolean | défaut `non` |
| `half_day_date` | Half Day Date | Date |  |
| `reason` | Reason | LongText | **requis** |

## Earned Leave Schedule

*Earned Leave Schedule* — `hr/earned_leave_schedule.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `allocation_date` | Allocation Date | Date | colonne de liste; lecture seule |
| `number_of_leaves` | Number of Leaves | Number | colonne de liste; lecture seule |
| `is_allocated` | Is Allocated | Boolean | colonne de liste; lecture seule |
| `failure_reason` | Failure Reason | LongText | lecture seule |
| `allocated_via` | Allocated Via | Select — Scheduler · Leave Policy Assignment · Manually | colonne de liste; lecture seule |
| `attempted` | Attempted | Boolean | lecture seule; masqué |
| `failed` | Failed | Boolean | lecture seule; masqué |

## Employee Advance

*Employee Advance* — `hr/employee_advance.yaml` · soumis

- **Numérotation** : série `EA-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `employee_name`
- **Icône** : `hand-coins`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — HR-EAD-.YYYY.- |  |
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `posting_date` | Posting Date | Date | **requis**; colonne de liste; défaut `today` |
| `department` | Department | Link → `Department` | lecture seule |
| `purpose` | Purpose | LongText | **requis**; colonne de liste |
| `advance_amount` | Advance Amount | Currency | **requis**; colonne de liste; devise de `currency`; — Amount of expense |
| `claimed_amount` | Claimed Amount | Currency | lecture seule; devise de `currency`; — Amount claimed via Expense Claim |
| `status` | Status | Select — Draft · Paid · Partially Paid · Unpaid · Claimed · Returned · Partly Claimed and Returned · Cancelled | lecture seule |
| `company` | Company | Link → `Company` | **requis**; lecture seule |
| `advance_account` | Advance Account | Link → `Account` |  |
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` |  |
| `return_amount` | Returned Amount | Currency | lecture seule; devise de `currency`; — Amount scheduled for deduction via salary |
| `repay_unclaimed_amount_from_salary` | Repay Unclaimed Amount from Salary | Boolean | défaut `non` |
| `pending_amount` | Pending Amount | Currency | lecture seule; devise de `currency`; — Pending (unpaid) amount from previous advances |
| `currency` | Currency | Link → `Currency` | **requis** |
| `base_paid_amount` | Paid Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency`; — Amount that has been paid against this advance |
| `paid_amount` | Paid Amount | Currency | lecture seule; devise de `currency`; — Amount that has been paid against this advance |

## Employee Attendance Tool

*Employee Attendance Tool* — `hr/employee_attendance_tool.yaml`

- **Vues** : calendar
- **Titre** : `status`
- **Icône** : `list-checks`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `date` | Date | Date | défaut `today` |
| `department` | Department | Link → `Department` |  |
| `branch` | Branch | Link → `Branch` |  |
| `company` | Company | Link → `Company` |  |
| `status` | Status | Select — Present · Absent · Half Day · Work From Home | colonne de liste |
| `late_entry` | Late Entry | Boolean | défaut `non` |
| `early_exit` | Early Exit | Boolean | défaut `non` |
| `shift` | Shift | Link → `Shift Type` |  |
| `employment_type` | Employment Type | Link → `Employment Type` |  |
| `designation` | Designation | Link → `Designation` |  |
| `employee_grade` | Employee Grade | Link → `Employee Grade` |  |
| `half_day_status` | Status for Other Half | Select — Present · Absent |  |
| `filter_by_shift` | Filter by Shift | Boolean | défaut `non` |

## Employee Boarding Activity

*Employee Boarding Activity* — `hr/employee_boarding_activity.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `activity_name` | Activity Name | Text | **requis**; colonne de liste |
| `user` | User | Text | colonne de liste |
| `task` | Task | Link → `Task` | lecture seule |
| `task_weight` | Task Weight | Number |  |
| `required_for_employee_creation` | Required for Employee Creation | Boolean | défaut `non`; — Applicable in the case of Employee Onboarding |
| `description` | Description | TextEditor |  |
| `duration` | Duration (Days) | Int | colonne de liste |
| `begin_on` | Begin On (Days) | Int | colonne de liste |

## Employee Checkin

*Employee Checkin* — `hr/employee_checkin.yaml`

- **Titre** : `employee_name`
- **Icône** : `fingerprint-pattern`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis** |
| `employee_name` | Employee Name | Text | colonne de liste; lecture seule; recopié de `employee.employee_name` |
| `log_type` | Log Type | Select — IN · OUT | colonne de liste |
| `shift` | Shift | Link → `Shift Type` | lecture seule |
| `time` | Time | Datetime | **requis**; colonne de liste |
| `device_id` | Location / Device ID | Text |  |
| `skip_auto_attendance` | Skip Auto Attendance | Boolean | défaut `non` |
| `attendance` | Attendance Marked | Link → `Attendance` | lecture seule |
| `shift_start` | Shift Start | Datetime | masqué |
| `shift_end` | Shift End | Datetime | masqué |
| `shift_actual_start` | Shift Actual Start | Datetime | masqué |
| `shift_actual_end` | Shift Actual End | Datetime | masqué |
| `geolocation` | Geolocation | JSON | lecture seule |
| `latitude` | Latitude | Number | lecture seule |
| `longitude` | Longitude | Number | lecture seule |
| `offshift` | Off-shift | Boolean | lecture seule; masqué |
| `overtime_type` | Overtime Type | Link → `Overtime Type` | masqué |

## Employee Feedback Criteria

*Employee Feedback Criteria* — `hr/employee_feedback_criteria.yaml`

- **Titre** : `criteria`
- **Icône** : `list-ordered`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `criteria` | Criteria | Text | **requis**; colonne de liste |

## Employee Feedback Rating

*Employee Feedback Rating* — `hr/employee_feedback_rating.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `rating` | Rating | Rating | colonne de liste |
| `criteria` | Criteria | Link → `Employee Feedback Criteria` | **requis**; colonne de liste |
| `per_weightage` | Weightage (%) | Percent | **requis**; colonne de liste |

## Employee Grade

*Employee Grade* — `hr/employee_grade.yaml`

- **Icône** : `layers`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `default_salary_structure` | Default Salary Structure | Link → `Salary Structure` |  |
| `default_base_pay` | Default Base Pay | Currency | devise de `currency` |
| `currency` | Currency | Link → `Currency` | lecture seule; masqué |

## Employee Grievance

*Employee Grievance* — `hr/employee_grievance.yaml` · soumis

- **Numérotation** : série `EG-{YYYY}-{#####}`
- **Vues** : kanban, calendar
- **Titre** : `employee_name`
- **Icône** : `message-square-warning`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `grievance_type` | Grievance Type | Link → `Grievance Type` | **requis**; colonne de liste |
| `date` | Date  | Date | **requis**; colonne de liste |
| `status` | Status | Select — Open · Investigated · Resolved · Invalid · Cancelled | **requis**; colonne de liste; défaut `Open` |
| `description` | Description | LongText | **requis** |
| `cause_of_grievance` | Cause of Grievance | LongText |  |
| `resolved_by` | Resolved By | Text |  |
| `employee_responsible` | Employee Responsible  | Link → `Employee` |  |
| `resolution_detail` | Resolution Details | LongText |  |
| `resolution_date` | Resolution Date | Date |  |
| `grievance_against` | Grievance Against | DynamicLink → `grievance_against_party` |  |
| `raised_by` | Raised By | Link → `Employee` | **requis** |
| `designation` | Designation | Link → `Designation` | lecture seule |
| `reports_to` | Reports To | Link → `Employee` | lecture seule |
| `grievance_against_party` | Grievance Against Party | Text | **requis**; colonne de liste |
| `associated_document_type` | Associated Document Type | Text |  |
| `associated_document` | Associated Document | DynamicLink → `associated_document_type` |  |
| `employee_name` | Employee Name | Text | lecture seule |
| `subject` | Subject | Text | **requis** |

## Employee Health Insurance

*Employee Health Insurance* — `hr/employee_health_insurance.yaml`

- **Titre** : `health_insurance_name`
- **Icône** : `heart-pulse`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `health_insurance_name` | Health Insurance Name | Text | **requis**; colonne de liste |

## Employee Onboarding

*Employee Onboarding* — `hr/employee_onboarding.yaml` · soumis

- **Numérotation** : série `EO-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `employee_name`
- **Icône** : `user-plus`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `job_offer` | Job Offer | Link → `Job Offer` | **requis** |
| `job_applicant` | Job Applicant | Link → `Job Applicant` |  |
| `employee_name` | Employee Name | Text | **requis**; colonne de liste |
| `employee` | Employee | Link → `Employee` | lecture seule |
| `date_of_joining` | Date of Joining | Date | **requis**; colonne de liste |
| `boarding_status` | Boarding Status | Select — Pending · In Process · Completed | lecture seule; défaut `Pending` |
| `notify_users_by_email` | Notify users by email | Boolean | défaut `non` |
| `employee_onboarding_template` | Employee Onboarding Template | Link → `Employee Onboarding Template` |  |
| `company` | Company | Link → `Company` | **requis** |
| `department` | Department | Link → `Department` | colonne de liste |
| `designation` | Designation | Link → `Designation` | colonne de liste |
| `employee_grade` | Employee Grade | Link → `Employee Grade` |  |
| `project` | Project | Link → `Project` | lecture seule |
| `activities` | Activities | Table → `Employee Boarding Activity` |  |
| `boarding_begins_on` | Onboarding Begins On | Date | **requis** |
| `holiday_list` | Holiday List | Link → `Holiday List` |  |

## Employee Onboarding Template

*Employee Onboarding Template* — `hr/employee_onboarding_template.yaml`

- **Titre** : `title`
- **Icône** : `clipboard-list`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text | **requis**; colonne de liste |
| `company` | Company | Link → `Company` |  |
| `department` | Department | Link → `Department` | colonne de liste |
| `designation` | Designation | Link → `Designation` | colonne de liste |
| `employee_grade` | Employee Grade | Link → `Employee Grade` | colonne de liste |
| `activities` | Activities | Table → `Employee Boarding Activity` |  |

## Employee Performance Feedback

*Employee Performance Feedback* — `hr/employee_performance_feedback.yaml` · soumis

- **Numérotation** : série `EPF-{YYYY}-{#####}`
- **Titre** : `employee_name`
- **Icône** : `message-square-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `total_score` | Total Score | Number | colonne de liste; lecture seule |
| `feedback` | Feedback | TextEditor | **requis** |
| `added_on` | Added On | Datetime | **requis** |
| `employee` | For Employee | Link → `Employee` | **requis**; colonne de liste |
| `appraisal` | Appraisal | Link → `Appraisal` | **requis** |
| `reviewer_designation` | Designation | Link → `Designation` | lecture seule |
| `reviewer` | Reviewer | Link → `Employee` | **requis** |
| `reviewer_name` | Reviewer Name | Text | colonne de liste; lecture seule |
| `department` | Department | Link → `Department` | lecture seule |
| `designation` | Designation | Link → `Designation` | lecture seule |
| `appraisal_cycle` | Appraisal Cycle | Link → `Appraisal Cycle` | colonne de liste; lecture seule |
| `feedback_ratings` | Feedback Ratings | Table → `Employee Feedback Rating` |  |
| `user` | User | Text | lecture seule |
| `company` | Company | Link → `Company` | **requis**; lecture seule |

## Employee Promotion

*Employee Promotion* — `hr/employee_promotion.yaml` · soumis

- **Numérotation** : série `EP-{YYYY}-{#####}`
- **Titre** : `employee_name`
- **Icône** : `trending-up`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `promotion_date` | Promotion Date | Date | **requis** |
| `company` | Company | Link → `Company` |  |
| `promotion_details` | Promotion Details | Table → `Employee Property History` |  |
| `salary_currency` | Salary Currency | Link → `Currency` | lecture seule |
| `current_ctc` | Current CTC | Currency | devise de `salary_currency` |
| `revised_ctc` | Revised CTC | Currency | devise de `salary_currency` |

## Employee Property History

*Employee Property History* — `hr/employee_property_history.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `property` | Property | Text | colonne de liste; lecture seule |
| `current` | Current | Text | colonne de liste; lecture seule |
| `new` | New | Text | colonne de liste; lecture seule |
| `fieldname` | Field Name | Text | lecture seule; masqué |

## Employee Referral

*Employee Referral* — `hr/employee_referral.yaml` · soumis

- **Numérotation** : série `ER-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `status`
- **Icône** : `user-round-plus`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `first_name` | First Name  | Text | **requis** |
| `last_name` | Last Name | Text | **requis** |
| `full_name` | Full Name | Text | colonne de liste; lecture seule |
| `contact_no` | Contact No. | Text |  |
| `current_employer` | Current Employer  | Text |  |
| `date` | Date | Date | **requis** |
| `status` | Status | Select — Pending · In Process · Accepted · Rejected · Cancelled | **requis**; lecture seule |
| `current_job_title` | Current Job Title | Text |  |
| `resume` | Resume | Attach |  |
| `department` | Department | Link → `Department` | lecture seule |
| `work_references` | Work References | TextEditor |  |
| `for_designation` | For Designation  | Link → `Designation` | **requis**; colonne de liste |
| `email` | Email | Text | **requis**; colonne de liste |
| `is_applicable_for_referral_bonus` | Is Applicable for Referral Bonus | Boolean | défaut `oui` |
| `qualification_reason` | Why is this Candidate Qualified for this Position? | TextEditor |  |
| `referrer` | Referrer | Link → `Employee` | **requis** |
| `referrer_name` | Referrer Name | Text | colonne de liste; lecture seule |
| `resume_link` | Resume Link | Text |  |
| `referral_payment_status` | Referral Bonus Payment Status | Select — Unpaid · Paid | lecture seule |

## Employee Separation

*Employee Separation* — `hr/employee_separation.yaml` · soumis

- **Numérotation** : série `ES-{YYYY}-{#####}`
- **Titre** : `employee_name`
- **Icône** : `user-minus`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis** |
| `employee_name` | Employee Name | Text | colonne de liste; lecture seule; recopié de `employee.employee_name` |
| `resignation_letter_date` | Resignation Letter Date | Date | colonne de liste; lecture seule |
| `boarding_status` | Status | Select — Pending · In Process · Completed | lecture seule; défaut `Pending` |
| `notify_users_by_email` | Notify users by email | Boolean | défaut `non` |
| `employee_separation_template` | Employee Separation Template | Link → `Employee Separation Template` |  |
| `company` | Company | Link → `Company` | **requis** |
| `project` | Project | Link → `Project` | lecture seule |
| `department` | Department | Link → `Department` | colonne de liste; lecture seule |
| `designation` | Designation | Link → `Designation` | colonne de liste; lecture seule |
| `employee_grade` | Employee Grade | Link → `Employee Grade` | lecture seule |
| `activities` | Activities | Table → `Employee Boarding Activity` |  |
| `exit_interview` | Exit Interview Summary | TextEditor |  |
| `boarding_begins_on` | Separation Begins On | Date | **requis** |

## Employee Separation Template

*Employee Separation Template* — `hr/employee_separation_template.yaml`

- **Titre** : `title`
- **Icône** : `clipboard-list`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text | **requis**; colonne de liste |
| `company` | Company | Link → `Company` |  |
| `department` | Department | Link → `Department` | colonne de liste |
| `designation` | Designation | Link → `Designation` | colonne de liste |
| `employee_grade` | Employee Grade | Link → `Employee Grade` | colonne de liste |
| `activities` | Activities | Table → `Employee Boarding Activity` |  |

## Employee Skill

*Employee Skill* — `hr/employee_skill.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `skill` | Skill | Link → `Skill` | **requis**; colonne de liste |
| `proficiency` | Proficiency | Rating | **requis**; colonne de liste |
| `evaluation_date` | Evaluation Date | Date | colonne de liste |

## Employee Skill Map

*Employee Skill Map* — `hr/employee_skill_map.yaml`

- **Titre** : `employee_name`
- **Icône** : `network`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` |  |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `designation` | Designation | Text | lecture seule |
| `employee_skills` | Employee Skills | Table → `Employee Skill` |  |
| `trainings` | Trainings | Table → `Employee Training` |  |

## Employee Training

*Employee Training* — `hr/employee_training.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `training` | Training | Link → `Training Event` | colonne de liste |
| `training_date` | Training Date | Date | colonne de liste |

## Employee Transfer

*Employee Transfer* — `hr/employee_transfer.yaml` · soumis

- **Numérotation** : série `ET-{YYYY}-{#####}`
- **Titre** : `employee_name`
- **Icône** : `arrow-right-left`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `transfer_date` | Transfer Date | Date | **requis** |
| `company` | Company | Link → `Company` |  |
| `new_company` | New Company | Link → `Company` |  |
| `department` | Department | Link → `Department` | lecture seule |
| `transfer_details` | Employee Transfer Detail | Table → `Employee Property History` |  |
| `reallocate_leaves` | Re-allocate Leaves | Boolean | masqué; défaut `non` |
| `create_new_employee_id` | Create New Employee Id | Boolean | défaut `non` |
| `new_employee_id` | New Employee ID | Link → `Employee` | lecture seule |

## Employment Type

*Employment Type* — `hr/employment_type.yaml`

- **Titre** : `employee_type_name`
- **Icône** : `briefcase`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee_type_name` | Employment Type | Text | **requis**; colonne de liste |

## Exit Interview

*Exit Interview* — `hr/exit_interview.yaml` · soumis

- **Numérotation** : série `EXIN-{YYYY}-{#####}`
- **Vues** : kanban, calendar
- **Titre** : `employee_name`
- **Icône** : `door-open`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `relieving_date` | Relieving Date | Date | colonne de liste; lecture seule |
| `company` | Company | Link → `Company` | **requis** |
| `date` | Date | Date | colonne de liste |
| `ref_doctype` | Reference Document Type | Text |  |
| `reference_document_name` | Reference Document Name | DynamicLink → `ref_doctype` | colonne de liste |
| `interviewers` | Interviewers | Table → `Interviewer` |  |
| `date_of_joining` | Date of Joining | Date | lecture seule |
| `reports_to` | Reports To | Link → `Employee` | lecture seule |
| `designation` | Designation | Link → `Designation` | lecture seule |
| `naming_series` | Naming Series | Select — HR-EXIT-INT- |  |
| `questionnaire_email_sent` | Questionnaire Email Sent | Boolean | lecture seule |
| `email` | Email ID | Text | lecture seule |
| `status` | Status | Select — Pending · Scheduled · Completed · Cancelled | **requis**; colonne de liste |
| `employee_status` | Final Decision | Select — Employee Retained · Exit Confirmed | colonne de liste |
| `interview_summary` | Interview Summary | TextEditor |  |

## Expected Skill Set

*Expected Skill Set* — `hr/expected_skill_set.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `skill` | Skill | Link → `Skill` | **requis**; colonne de liste |
| `description` | Description | LongText | colonne de liste |

## Expense Claim

*Expense Claim* — `hr/expense_claim.yaml` · soumis

- **Numérotation** : série `EC-{YYYY}-{#####}`
- **Vues** : kanban, calendar
- **Titre** : `employee_name`
- **Icône** : `receipt`
- **Workflow** : États : Brouillon → À approuver → Approuvée → Refusée → Annulée
- **Workflow** : Actions : `Annuler`, `Approuver`, `Refuser`, `Reprendre`, `Soumettre`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — HR-EXP-.YYYY.- | **requis** |
| `employee` | From Employee | Link → `Employee` | **requis** |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` |  |
| `expense_approver` | Expense Approver | Text |  |
| `approval_status` | Approval Status | Select — Draft · Approved · Rejected · Cancelled | défaut `Draft` |
| `total_claimed_amount` | Total Claimed Amount | Currency | colonne de liste; lecture seule; devise de `currency` |
| `total_sanctioned_amount` | Total Sanctioned Amount | Currency | lecture seule; devise de `currency` |
| `is_paid` | Is Paid | Boolean | défaut `non` |
| `expenses` | Expenses | Table → `Expense Claim Detail` |  |
| `posting_date` | Posting Date | Date | **requis**; défaut `today` |
| `vehicle_log` | Vehicle Log | Link → `Vehicle Log` | lecture seule |
| `project` | Project | Link → `Project` |  |
| `task` | Task | Link → `Task` |  |
| `total_amount_reimbursed` | Total Amount Reimbursed | Currency | colonne de liste; lecture seule; devise de `currency` |
| `remark` | Remark | LongText |  |
| `company` | Company | Link → `Company` | **requis** |
| `mode_of_payment` | Mode of Payment | Link → `Mode of Payment` |  |
| `clearance_date` | Clearance Date | Date |  |
| `payable_account` | Payable Account | Link → `Account` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `status` | Status | Select — Draft · Paid · Partially Paid · Unpaid · Rejected · Submitted · Cancelled | colonne de liste; lecture seule; défaut `Draft` |
| `advances` | Advances | Table → `Expense Claim Advance` |  |
| `total_advance_amount` | Total Advance Amount | Currency | lecture seule; devise de `currency` |
| `taxes` | Expense Taxes and Charges | Table → `Expense Taxes and Charges` |  |
| `grand_total` | Grand Total | Currency | colonne de liste; lecture seule; devise de `currency` |
| `total_taxes_and_charges` | Total Taxes and Charges | Currency | lecture seule; devise de `currency` |
| `delivery_trip` | Delivery Trip | Link → `Delivery Trip` |  |
| `currency` | Currency | Link → `Currency` | **requis** |
| `exchange_rate` | Exchange Rate | Number | **requis** |
| `base_total_sanctioned_amount` | Total Sanctioned Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_grand_total` | Grand Total (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_total_advance_amount` | Total Advance Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_total_taxes_and_charges` | Total Taxes and Charges (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `base_total_claimed_amount` | Total Claimed Amount (Company Currency) | Currency | lecture seule; devise de `company.default_currency` |
| `bank_or_cash_account` | Bank / Cash Account | Link → `Account` |  |
| `gain_loss_account` | Gain Loss Account | Link → `Account` |  |
| `total_exchange_gain_loss` | Total Exchange Gain/Loss | Currency | lecture seule; devise de `currency` |

## Expense Claim Account

*Expense Claim Account* — `hr/expense_claim_account.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | colonne de liste |
| `default_account` | Default Account | Link → `Account` | **requis**; colonne de liste |

## Expense Claim Advance

*Expense Claim Advance* — `hr/expense_claim_advance.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee_advance` | Employee Advance | Link → `Employee Advance` | **requis**; colonne de liste |
| `posting_date` | Posting Date | Date | colonne de liste; lecture seule |
| `advance_paid` | Advance Paid | Currency | colonne de liste; lecture seule; devise de `parent_currency` |
| `unclaimed_amount` | Unclaimed Amount | Currency | **requis**; colonne de liste; lecture seule; devise de `parent_currency` |
| `allocated_amount` | Allocated Amount | Currency | colonne de liste; devise de `parent_currency` |
| `advance_account` | Advance Account | Link → `Account` | masqué |
| `return_amount` | Returned Amount | Currency | lecture seule; devise de `parent_currency` |
| `base_advance_paid` | Advance Paid (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_unclaimed_amount` | Unclaimed Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_allocated_amount` | Allocated Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `exchange_rate` | Exchange Rate | Number | lecture seule; — Exchange rate of Payment Entry against Employee Advance |
| `exchange_gain_loss` | Exchange Gain/Loss | Currency | lecture seule; devise de `parent_currency` |
| `payment_entry_reference` | Payment Entry Reference | Text | lecture seule; masqué |
| `reference_type` | Reference Type | Select — Payment Entry · Journal Entry | lecture seule |
| `reference_name` | Reference Name | DynamicLink → `reference_type` | lecture seule |

## Expense Claim Detail

*Expense Claim Detail* — `hr/expense_claim_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `expense_date` | Expense Date | Date | colonne de liste |
| `expense_type` | Expense Claim Type | Link → `Expense Claim Type` | **requis**; colonne de liste |
| `default_account` | Default Account | Link → `Account` | lecture seule; masqué |
| `description` | Description | TextEditor | colonne de liste |
| `amount` | Amount | Currency | **requis**; colonne de liste; devise de `parent_currency` |
| `sanctioned_amount` | Sanctioned Amount | Currency | colonne de liste; devise de `parent_currency` |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `project` | Project | Link → `Project` |  |
| `base_amount` | Amount (Company Currency) | Currency | devise de `parent_company.default_currency` |
| `base_sanctioned_amount` | Sanctioned Amount (Company Currency) | Currency | devise de `parent_company.default_currency` |

## Expense Claim Type

*Expense Claim Type* — `hr/expense_claim_type.yaml`

- **Titre** : `expense_type`
- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `expense_type` | Expense Claim Type | Text | **requis**; colonne de liste |
| `description` | Description | LongText |  |
| `accounts` | Accounts | Table → `Expense Claim Account` |  |
| `deferred_expense_account` | Deferred Expense Account | Boolean | défaut `non` |

## Expense Taxes and Charges

*Expense Taxes and Charges* — `hr/expense_taxes_and_charges.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `account_head` | Account Head | Link → `Account` | **requis**; colonne de liste |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `description` | Description | LongText | **requis** |
| `rate` | Rate | Number | colonne de liste |
| `tax_amount` | Amount | Currency | colonne de liste; devise de `parent_currency` |
| `total` | Total | Currency | colonne de liste; lecture seule; devise de `parent_currency` |
| `project` | Project | Link → `Project` |  |
| `base_total` | Total (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |
| `base_tax_amount` | Amount (Company Currency) | Currency | lecture seule; devise de `parent_company.default_currency` |

## Full and Final Asset

*Full and Final Asset* — `hr/full_and_final_asset.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `reference` | Reference | Link → `Asset Movement` | **requis**; colonne de liste; lecture seule |
| `status` | Status | Select — Owned · Returned | **requis**; colonne de liste |
| `description` | Description | LongText |  |
| `asset_name` | Asset Name | Text | colonne de liste; lecture seule |
| `date` | Date | Datetime | lecture seule |
| `action` | Action | Select — Return · Recover Cost | **requis**; colonne de liste; défaut `Return` |
| `cost` | Cost | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `account` | Account | Link → `Account` | colonne de liste |
| `actual_cost` | Actual Cost | Currency | lecture seule; devise de `parent_company.default_currency` |

## Full and Final Outstanding Statement

*Full and Final Outstanding Statement* — `hr/full_and_final_outstanding_statement.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `status` | Status | Select — Settled · Unsettled | colonne de liste; défaut `Unsettled` |
| `remark` | Remark | LongText |  |
| `reference_document` | Reference Document | DynamicLink → `reference_document_type` | colonne de liste |
| `component` | Component | Text | **requis**; colonne de liste |
| `account` | Account | Link → `Account` | colonne de liste |
| `amount` | Amount | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `reference_document_type` | Reference Document Type | Text | colonne de liste |
| `paid_via_salary_slip` | Paid via Salary Slip | Boolean | défaut `non` |

## Full and Final Statement

*Full and Final Statement* — `hr/full_and_final_statement.yaml` · soumis

- **Numérotation** : série `FFS-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `employee_name`
- **Icône** : `file-check`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `designation` | Designation | Link → `Designation` | lecture seule |
| `status` | Status | Select — Paid · Unpaid · Cancelled | lecture seule; défaut `Unpaid` |
| `department` | Department | Link → `Department` | lecture seule |
| `assets_allocated` | Assets Allocated | Table → `Full and Final Asset` |  |
| `relieving_date` | Relieving Date  | Date | lecture seule |
| `date_of_joining` | Date of Joining | Date | lecture seule |
| `company` | Company | Link → `Company` | colonne de liste; lecture seule |
| `payables` | Payables | Table → `Full and Final Outstanding Statement` |  |
| `receivables` | Receivables | Table → `Full and Final Outstanding Statement` |  |
| `transaction_date` | Transaction Date | Date | **requis** |
| `total_payable_amount` | Total Payable Amount | Currency | colonne de liste; lecture seule; devise de `company.default_currency` |
| `total_receivable_amount` | Total Receivable Amount | Currency | colonne de liste; lecture seule; devise de `company.default_currency` |
| `total_asset_recovery_cost` | Total Asset Recovery Cost | Currency | lecture seule; devise de `company.default_currency` |

## Goal

*Goal* — `hr/goal.yaml`

- **Vues** : calendar, gantt
- **Titre** : `employee_name`
- **Icône** : `target`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis** |
| `start_date` | Start Date | Date | **requis** |
| `progress` | Progress | Percent | colonne de liste |
| `status` | Status | Select — Pending · In Progress · Completed · Archived · Closed | colonne de liste; lecture seule; défaut `Pending` |
| `description` | Description | TextEditor |  |
| `lft` | Left | Int | lecture seule; masqué |
| `rgt` | Right | Int | lecture seule; masqué |
| `is_group` | Is Group | Boolean | colonne de liste; défaut `non` |
| `old_parent` | Old Parent | Link → `Goal` | masqué |
| `parent_goal` | Parent Goal | Link → `Goal` |  |
| `kra` | KRA | Link → `KRA` |  |
| `appraisal_cycle` | Appraisal Cycle | Link → `Appraisal Cycle` |  |
| `employee_name` | Employee Name | Text | colonne de liste; lecture seule; recopié de `employee.employee_name` |
| `user` | User | Text | lecture seule |
| `end_date` | End Date | Date | colonne de liste |
| `goal_name` | Goal | Text | **requis**; colonne de liste |
| `company` | Company | Link → `Company` | lecture seule |

## Grievance Type

*Grievance Type* — `hr/grievance_type.yaml`

- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `description` | Description | LongText |  |

## Holiday List Assignment

*Holiday List Assignment* — `hr/holiday_list_assignment.yaml` · soumis

- **Numérotation** : série `HLA-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `holiday_list`
- **Icône** : `calendar-off`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `holiday_list` | Holiday List | Link → `Holiday List` | **requis**; colonne de liste |
| `naming_series` | Naming Series | Select — HR-HLA-.YYYY.- | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; masqué |
| `assigned_to` | Assigned To | DynamicLink → `applicable_for` | colonne de liste |
| `employee_company` | Employee Company | Link → `Company` | lecture seule; masqué |
| `applicable_for` | Applicable For | Select — Employee · Company | **requis** |
| `holiday_list_start` | Holiday List Start | Date |  |
| `holiday_list_end` | Holiday List End | Date |  |
| `from_date` | Assignment Starts From | Date | **requis** |

## HR Settings

*HR Settings* — `hr/hr_settings.yaml` · document unique

- **Icône** : `settings`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `retirement_age` | Retirement Age (In Years) | Text |  |
| `emp_created_by` | Employee Naming By | Select — Naming Series · Employee Number · Full Name | défaut `Naming Series`; — Employee records are created using the selected option |
| `expense_approver_mandatory_in_expense_claim` | Expense Approver Mandatory In Expense Claim | Boolean | défaut `non` |
| `leave_approver_mandatory_in_leave_application` | Leave Approver Mandatory In Leave Application | Boolean | défaut `non` |
| `show_leaves_of_all_department_members_in_calendar` | Show Leaves Of All Department Members In Calendar | Boolean | défaut `non` |
| `auto_leave_encashment` | Auto Leave Encashment | Boolean | défaut `non` |
| `standard_working_hours` | Standard Working Hours | Number |  |
| `remind_before` | Remind Before | Time | défaut `00:15:00` |
| `send_holiday_reminders` | Holidays | Boolean | défaut `oui` |
| `send_work_anniversary_reminders` | Work Anniversaries  | Boolean | défaut `oui` |
| `frequency` | Set the frequency for holiday reminders | Select — Weekly · Monthly | défaut `Weekly` |
| `send_birthday_reminders` | Birthdays | Boolean | défaut `oui` |
| `send_interview_reminder` | Send Interview Reminder | Boolean | défaut `non` |
| `send_interview_feedback_reminder` | Send Interview Feedback Reminder | Boolean | défaut `non` |
| `feedback_reminder_notification_template` | Feedback Reminder Notification Template | Link → `Email Template` |  |
| `interview_reminder_template` | Interview Reminder Notification Template | Link → `Email Template` |  |
| `restrict_backdated_leave_application` | Restrict Backdated Leave Application | Boolean | défaut `non` |
| `check_vacancies` | Check Vacancies On Job Offer Creation | Boolean | défaut `non` |
| `exit_questionnaire_web_form` | Exit Questionnaire Web Form | Link → `Web Form` |  |
| `exit_questionnaire_notification_template` | Exit Questionnaire Notification Template | Link → `Email Template` |  |
| `sender` | Sender | Link → `Email Account` |  |
| `sender_email` | Sender Email | Text | lecture seule |
| `hiring_sender` | Sender | Link → `Email Account` |  |
| `hiring_sender_email` | Sender Email | Text | lecture seule |
| `allow_multiple_shift_assignments` | Allow Multiple Shift Assignments for Same Date | Boolean | défaut `non` |
| `allow_employee_checkin_from_mobile_app` | Allow Employee Checkin from Mobile App | Boolean | défaut `oui` |
| `allow_geolocation_tracking` | Allow Geolocation Tracking | Boolean | défaut `non` |
| `unlink_payment_on_cancellation_of_employee_advance` |  Unlink Payment on Cancellation of Employee Advance | Boolean | défaut `non` |
| `enable_multi_currency_expense_claim` | Enable Multi-Currency Expense Claims | Boolean | défaut `non`; — Allow expense claims to be raised in a currency other than the company currency |
| `prevent_self_leave_approval` | Prevent self approval for leaves even if user has permissions | Boolean | défaut `non` |
| `prevent_self_expense_approval` | Prevent self approval for expense claims even if user has permissions | Boolean | défaut `non` |

## HR Telemetry Milestone

*HR Telemetry Milestone* — `hr/hr_telemetry_milestone.yaml`

- **Titre** : `event`
- **Icône** : `flag`
- **Permissions explicites** — `write` : 0, `create` : 0, `delete` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `event` | Event | Text | **requis**; colonne de liste |

## Identification Document Type

*Identification Document Type* — `hr/identification_document_type.yaml`

- **Icône** : `id-card`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `identification_document_type` | Identification Document Type | Text |  |

## Interest

*Interest* — `hr/interest.yaml`

- **Titre** : `interest`
- **Icône** : `heart`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `interest` | Interest | Text | **requis**; colonne de liste |

## Interview

*Interview* — `hr/interview.yaml` · soumis

- **Numérotation** : série `INTE-{YYYY}-{#####}`
- **Vues** : kanban
- **Titre** : `status`
- **Icône** : `messages-square`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `job_applicant` | Job Applicant | Link → `Job Applicant` | **requis**; colonne de liste |
| `job_opening` | Job Opening | Link → `Job Opening` | lecture seule |
| `status` | Status | Select — Pending · Under Review · Cleared · Rejected · Cancelled | **requis**; colonne de liste; défaut `Pending` |
| `average_rating` | Obtained Average Rating | Rating | colonne de liste; lecture seule |
| `interview_summary` | Interview Summary | LongText |  |
| `resume_link` | Resume link | Text |  |
| `expected_average_rating` | Expected Average Rating | Rating | lecture seule |
| `designation` | Designation | Link → `Designation` | colonne de liste; lecture seule |
| `scheduled_on` | Scheduled On | Date | **requis**; colonne de liste |
| `reminded` | Reminded | Boolean | masqué; défaut `non` |
| `from_time` | From Time | Time | **requis**; colonne de liste |
| `to_time` | To Time | Time | **requis**; colonne de liste |
| `interview_details` | Interviewers | Table → `Interview Detail` |  |
| `interview_type` | Interview Type | Link → `Interview Type` | **requis**; colonne de liste |

## Interview Detail

*Interview Detail* — `hr/interview_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `interviewer` | Interviewer | Text | colonne de liste |

## Interview Feedback

*Interview Feedback* — `hr/interview_feedback.yaml` · soumis

- **Numérotation** : série `IF-{YYYY}-{#####}`
- **Titre** : `interview`
- **Icône** : `message-square-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `interview` | Interview | Link → `Interview` | **requis**; colonne de liste |
| `interviewer` | Interviewer | Text | **requis**; colonne de liste |
| `skill_assessment` | Skill Assessment | Table → `Skill Assessment` |  |
| `average_rating` | Average Rating | Rating | colonne de liste; lecture seule |
| `feedback` | Feedback | LongText |  |
| `result` | Result | Select — Cleared · Rejected | **requis**; colonne de liste |
| `job_applicant` | Job Applicant | Link → `Job Applicant` | colonne de liste; lecture seule |
| `interview_type` | Interview Type | Link → `Interview Type` | **requis**; colonne de liste; lecture seule |

## Interview Type

*Interview Type* — `hr/interview_type.yaml`

- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `designation` | Designation | Link → `Designation` |  |
| `expected_skill_set` | Expected Skillset | Table → `Expected Skill Set` |  |
| `expected_average_rating` | Expected Average Rating | Rating |  |
| `interviewers` | Interviewers | Table → `Interviewer` |  |
| `description` | Description | LongText |  |
| `interview_type_name` | Interview Type Name | Text |  |

## Interviewer

*Interviewer* — `hr/interviewer.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `user` | User | Text | colonne de liste |

## Job Applicant

*Job Applicant* — `hr/job_applicant.yaml`

- **Vues** : kanban
- **Titre** : `applicant_name`
- **Icône** : `user-round`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `applicant_name` | Full Name | Text | **requis** |
| `email_id` | Email Address | Text | **requis** |
| `status` | Status | Select — Open · Replied · Shortlisted · Rejected · Hold · Accepted | **requis**; colonne de liste |
| `job_title` | Job Opening | Link → `Job Opening` | colonne de liste |
| `source` | Source | Link → `Job Applicant Source` |  |
| `source_name` | Source Name | Link → `Employee` |  |
| `cover_letter` | Cover Letter | LongText |  |
| `resume_attachment` | Attachment | Attach |  |
| `notes` | Notes | Text | lecture seule |
| `phone_number` | Phone Number | Text |  |
| `country` | Country | Link → `Country` |  |
| `resume_link` | Link | Text |  |
| `applicant_rating` | Applicant Rating | Rating | colonne de liste |
| `lower_range` | Lower Range | Currency | devise de `currency` |
| `upper_range` | Upper Range | Currency | devise de `currency` |
| `currency` | Currency | Link → `Currency` |  |
| `employee_referral` | Employee Referral | Link → `Employee Referral` | lecture seule |
| `designation` | Designation | Link → `Designation` |  |

## Job Applicant Source

*Job Applicant Source* — `hr/job_applicant_source.yaml`

- **Titre** : `source_name`
- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `source_name` | Source Name | Text | **requis**; colonne de liste |
| `details` | Details | TextEditor |  |

## Job Offer

*Job Offer* — `hr/job_offer.yaml` · soumis

- **Numérotation** : série `JO-{YYYY}-{#####}`
- **Vues** : kanban, calendar
- **Titre** : `applicant_name`
- **Icône** : `handshake`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `job_applicant` | Job Applicant | Link → `Job Applicant` |  |
| `applicant_name` | Applicant Name | Text | **requis**; colonne de liste |
| `applicant_email` | Applicant Email Address | Text | **requis** |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `status` | Status | Select — Draft · Ready to Send · Awaiting Response · Accepted · Rejected · Cancelled | défaut `Draft` |
| `offer_date` | Offer Date | Date | **requis** |
| `offer_valid_till` | Offer Valid Till | Date |  |
| `designation` | Designation | Link → `Designation` | **requis**; colonne de liste |
| `department` | Department | Link → `Department` |  |
| `grade` | Employee Grade | Link → `Employee Grade` |  |
| `employment_type` | Employment Type | Link → `Employment Type` |  |
| `branch` | Branch | Link → `Branch` |  |
| `reports_to` | Reports To | Link → `Employee` |  |
| `date_of_joining` | Date of Joining | Date |  |
| `salary_structure` | Salary Structure | Link → `Salary Structure` |  |
| `currency` | Currency | Link → `Currency` | lecture seule |
| `calculate_component_amount_from` | Calculate Component Amount From | Select — Base and Variable · CTC |  |
| `base` | Base | Currency | devise de `currency` |
| `variable` | Variable | Currency | devise de `currency` |
| `ctc` | Total Cost to Company (CTC) | Currency | devise de `currency` |
| `gross` | Gross Pay | Currency | lecture seule; masqué; devise de `currency`; — Gross earnings for one payroll cycle, before deductions. Shown as a row in the break-up; kept as a field becau |
| `ctc_breakup` | CTC Break-up | Table → `Job Offer Component` |  |
| `weekly_off_days` | Weekly Off | Text | — Comma separated, for example: Saturday, Sunday |
| `total_public_holidays` | Public Holidays | Int | — Holidays in the year other than weekly offs |
| `leave_allocations` | Leave Allocations | Table → `Leave Policy Detail` | lecture seule |
| `leave_policy` | Leave Policy | Link → `Leave Policy` |  |
| `holiday_list` | Holiday List | Link → `Holiday List` |  |
| `probation_period_days` | Probation Period (Days) | Int | défaut `90` |
| `notice_period_during_probation` | Notice Period During Probation (Days) | Int |  |
| `notice_number_of_days` | Notice Period (Days) | Int | défaut `30` |
| `working_hours` | Working Hours | Number | défaut `8.0` |
| `job_offer_term_template` | Job Offer Term Template | Link → `Job Offer Term Template` |  |
| `offer_terms` | Job Offer Terms | Table → `Job Offer Term` |  |
| `select_terms` | Select Terms and Conditions | Link → `Terms and Conditions` |  |
| `terms` | Terms and Conditions | TextEditor |  |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `offer_letter_print_format` | Print Format | Link → `Print Format` |  |
| `signature` | Sign to show on offer letter | Image |  |

## Job Offer Component

*Job Offer Component* — `hr/job_offer_component.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `fixed_components` | Fixed Components | Text | **requis**; colonne de liste |
| `per_cycle` | Per Cycle | Currency | colonne de liste; devise de `currency` |
| `yearly` | Yearly | Currency | colonne de liste; devise de `currency` |
| `currency` | Currency | Link → `Currency` | lecture seule; masqué |
| `is_summary` | Is Summary | Boolean | lecture seule; masqué; — Set by the system on total rows. A row added by hand is a component. |

## Job Offer Term

*Job Offer Term* — `hr/job_offer_term.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `offer_term` | Offer Term | Link → `Offer Term` | **requis**; colonne de liste |
| `value` | Value / Description | LongText | **requis**; colonne de liste |

## Job Offer Term Template

*Job Offer Term Template* — `hr/job_offer_term_template.yaml`

- **Titre** : `title`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text |  |
| `offer_terms` | Offer Terms | Table → `Job Offer Term` |  |

## Job Opening

*Job Opening* — `hr/job_opening.yaml`

- **Titre** : `job_title`
- **Icône** : `briefcase-business`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `job_title` | Job Title | Text | **requis**; colonne de liste |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `status` | Status | Select — Open · Closed | colonne de liste; masqué |
| `designation` | Designation | Link → `Designation` | **requis**; colonne de liste |
| `department` | Department | Link → `Department` | colonne de liste |
| `staffing_plan` | Staffing Plan | Link → `Staffing Plan` | lecture seule |
| `planned_vacancies` | Planned number of Positions | Int | lecture seule |
| `publish` | Publish on website | Boolean | colonne de liste; défaut `non` |
| `route` | Route | Text |  |
| `description` | Description | TextEditor | colonne de liste; — Job profile, qualifications required etc. |
| `currency` | Currency | Link → `Currency` |  |
| `lower_range` | Lower Range | Currency | devise de `currency` |
| `upper_range` | Upper Range | Currency | devise de `currency` |
| `job_application_route` | Application Web Form Route | Text | — Route to the custom Job Application Webform |
| `publish_salary_range` | Publish Salary Range | Boolean | défaut `non` |
| `job_requisition` | Job Requisition | Link → `Job Requisition` | lecture seule |
| `vacancies` | Vacancies | Int | lecture seule |
| `posted_on` | Posted On | Datetime |  |
| `closes_on` | Closes On | Date | — If set, the job opening will be closed automatically after this date |
| `employment_type` | Employment Type | Link → `Employment Type` | colonne de liste |
| `location` | Location | Link → `Branch` |  |
| `closed_on` | Closed On | Date |  |
| `salary_per` | Salary Paid Per | Select — Month · Year | défaut `Month` |
| `publish_applications_received` | Publish Applications Received | Boolean | défaut `oui`; — If enabled, the total no. of applications received for this opening will be displayed on the website |
| `prevent_duplicate_applicant` | Prevent Duplicate Applications | Boolean | défaut `non`; — If enabled, candidates who have already applied with the same email address will not be allowed to apply again |
| `job_opening_template` | Job Opening Template | Link → `Job Opening Template` |  |

## Job Opening Template

*Job Opening Template* — `hr/job_opening_template.yaml`

- **Titre** : `department`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `department` | Department | Link → `Department` | colonne de liste |
| `employment_type` | Employment Type | Link → `Employment Type` |  |
| `location` | Location | Link → `Branch` |  |
| `template_title` | Template Title | Text | **requis**; colonne de liste |
| `description` | Description | TextEditor |  |
| `designation` | Designation | Link → `Designation` |  |
| `currency` | Currency | Link → `Currency` |  |
| `upper_range` | Upper Range | Currency | devise de `currency` |
| `lower_range` | Lower Range | Currency | devise de `currency` |
| `salary_per` | Salary Paid Per | Select — Month · Year | défaut `Month` |
| `publish_salary_range` | Publish Salary Range | Boolean | défaut `non` |

## Job Requisition

*Job Requisition* — `hr/job_requisition.yaml`

- **Vues** : kanban, calendar
- **Titre** : `status`
- **Icône** : `clipboard-pen`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `designation` | Designation | Link → `Designation` | **requis**; colonne de liste |
| `no_of_positions` | No of. Positions | Int | **requis**; colonne de liste |
| `expected_compensation` | Expected Compensation | Currency | **requis**; colonne de liste; devise de `company.default_currency` |
| `status` | Status | Select — Pending · Open & Approved · Rejected · Filled · On Hold · Cancelled | **requis**; colonne de liste |
| `company` | Company | Link → `Company` | **requis** |
| `requested_by` | Requested By | Link → `Employee` | **requis** |
| `requested_by_name` | Requested By (Name) | Text | colonne de liste; lecture seule |
| `requested_by_dept` | Department | Link → `Department` | lecture seule |
| `requested_by_designation` | Designation | Link → `Designation` | lecture seule |
| `posting_date` | Posting Date | Date | **requis**; défaut `today` |
| `expected_by` | Expected By | Date | colonne de liste |
| `completed_on` | Completed On | Date |  |
| `description` | Job Description | TextEditor | **requis** |
| `naming_series` | Naming Series | Select — HR-HIREQ- |  |
| `reason_for_requesting` | Reason for Requesting | LongText |  |
| `department` | Department | Link → `Department` |  |
| `time_to_fill` | Time to Fill | Duration | lecture seule; — Time taken to fill the open positions |

## KRA

*KRA* — `hr/kra.yaml`

- **Titre** : `title`
- **Icône** : `crosshair`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `title` | Title | Text | **requis**; colonne de liste |
| `description` | Description | LongText |  |

## Leave Adjustment

*Leave Adjustment* — `hr/leave_adjustment.yaml` · soumis

- **Numérotation** : série `LA-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `employee_name`
- **Icône** : `sliders-horizontal`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis** |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `leave_type` | Leave Type | Link → `Leave Type` | **requis** |
| `leave_allocation` | Allocation to Adjust | Link → `Leave Allocation` | **requis**; lecture seule |
| `from_date` | From Date | Date | lecture seule |
| `naming_series` | Series | Select — HR-LAD-.YYYY.- | **requis**; colonne de liste |
| `to_date` | To Date | Date | lecture seule |
| `allocated_leaves` | Allocated Leaves | Number | lecture seule |
| `posting_date` | Posting Date | Date | **requis**; défaut `today` |
| `leaves_to_adjust` | Leaves to Adjust | Number | **requis** |
| `adjustment_type` | Adjustment Type | Select — Allocate · Reduce | **requis** |
| `leaves_after_adjustment` | Leaves After Adjustment | Number | lecture seule |
| `reason_for_adjustment` | Reason for Adjustment | LongText |  |
| `company` | Company | Link → `Company` | lecture seule |

## Leave Allocation

*Leave Allocation* — `hr/leave_allocation.yaml` · soumis

- **Numérotation** : série `LEAL-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `employee_name`
- **Icône** : `calendar-range`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — HR-LAL-.YYYY.- | **requis** |
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | colonne de liste; lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `leave_type` | Leave Type | Link → `Leave Type` | **requis**; colonne de liste |
| `from_date` | From Date | Date | **requis** |
| `to_date` | To Date | Date | **requis** |
| `new_leaves_allocated` | New Leaves Allocated | Number |  |
| `carry_forward` | Add unused leaves from previous allocations | Boolean | défaut `non` |
| `unused_leaves` | Unused leaves | Number | lecture seule |
| `total_leaves_allocated` | Total Leaves Allocated | Number | **requis**; lecture seule |
| `total_leaves_encashed` | Total Leaves Encashed | Number | lecture seule |
| `compensatory_request` | Compensatory Leave Request | Link → `Compensatory Leave Request` | lecture seule |
| `leave_period` | Leave Period | Link → `Leave Period` | lecture seule |
| `leave_policy` | Leave Policy | Link → `Leave Policy` | lecture seule; masqué |
| `expired` | Expired | Boolean | lecture seule; masqué |
| `description` | Description | LongText |  |
| `carry_forwarded_leaves_count` | Carry Forwarded Leaves | Number | lecture seule |
| `leave_policy_assignment` | Leave Policy Assignment | Link → `Leave Policy Assignment` | lecture seule |
| `company` | Company | Link → `Company` | **requis**; lecture seule |
| `earned_leave_schedule` | Earned Leave Schedule | Table → `Earned Leave Schedule` | lecture seule |

## Leave Application

*Leave Application* — `hr/leave_application.yaml` · soumis

- **Numérotation** : série `LEAP-{YYYY}-{#####}`
- **Vues** : kanban, calendar, gantt
- **Titre** : `employee_name`
- **Icône** : `plane`
- **Workflow** : États : Brouillon → À approuver → Approuvée → Refusée → Annulée
- **Workflow** : Actions : `Annuler`, `Approuver`, `Refuser`, `Reprendre`, `Soumettre`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — HR-LAP-.YYYY.- | **requis** |
| `employee` | Employee | Link → `Employee` | **requis** |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `employee_email` | Employee Email | Text | lecture seule; masqué |
| `leave_type` | Leave Type | Link → `Leave Type` | **requis** |
| `department` | Department | Link → `Department` | lecture seule |
| `leave_balance` | Leave Balance Before Application | Number | lecture seule |
| `from_date` | From Date | Date | **requis**; colonne de liste |
| `to_date` | To Date | Date | **requis** |
| `half_day` | Half Day | Boolean | défaut `non` |
| `half_day_date` | Half Day Date | Date | visible si `half_day`; obligatoire si `half_day` |
| `total_leave_days` | Total Leave Days | Number | colonne de liste; lecture seule |
| `description` | Reason | LongText |  |
| `leave_approver` | Leave Approver | Text |  |
| `leave_approver_name` | Leave Approver Name | Text | lecture seule |
| `status` | Status | Select — Open · Approved · Rejected · Cancelled | **requis**; défaut `Open` |
| `posting_date` | Posting Date | Date | **requis**; défaut `today` |
| `company` | Company | Link → `Company` | **requis**; lecture seule |
| `follow_via_email` | Follow via Email | Boolean | défaut `oui` |
| `salary_slip` | Salary Slip | Link → `Salary Slip` |  |
| `letter_head` | Letter Head | Link → `Letter Head` |  |
| `color` | Color | Color |  |

## Leave Block List

*Leave Block List* — `hr/leave_block_list.yaml`

- **Titre** : `leave_block_list_name`
- **Icône** : `calendar-x`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `leave_block_list_name` | Leave Block List Name | Text | **requis**; colonne de liste |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `applies_to_all_departments` | Applies to Company | Boolean | colonne de liste; défaut `non`; — If not checked, the list will have to be added to each Department where it has to be applied. |
| `leave_block_list_dates` | Leave Block List Dates | Table → `Leave Block List Date` |  |
| `leave_block_list_allowed` | Leave Block List Allowed | Table → `Leave Block List Allow` |  |
| `leave_type` | Leave Type | Link → `Leave Type` |  |

## Leave Block List Allow

*Leave Block List Allow* — `hr/leave_block_list_allow.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `allow_user` | Allow User | Text | **requis**; colonne de liste |

## Leave Block List Date

*Leave Block List Date* — `hr/leave_block_list_date.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `block_date` | Block Date | Date | **requis**; colonne de liste |
| `reason` | Reason | LongText | **requis**; colonne de liste |

## Leave Control Panel

*Leave Control Panel* — `hr/leave_control_panel.yaml`

- **Vues** : calendar, gantt
- **Titre** : `employment_type`
- **Icône** : `settings-2`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` |  |
| `employment_type` | Employment Type | Link → `Employment Type` | colonne de liste |
| `branch` | Branch | Link → `Branch` | colonne de liste |
| `department` | Department | Link → `Department` | colonne de liste |
| `designation` | Designation | Link → `Designation` | colonne de liste |
| `employee_grade` | Employee Grade | Link → `Employee Grade` |  |
| `from_date` | From Date | Date | défaut `today` |
| `to_date` | To Date | Date |  |
| `leave_policy` | Leave Policy | Link → `Leave Policy` |  |
| `leave_type` | Leave Type | Link → `Leave Type` |  |
| `carry_forward` | Carry Forward | Boolean | défaut `oui`; — Add unused leaves from previous leave period's allocation to this allocation |
| `no_of_days` | New Leaves Allocated (In Days) | Number |  |
| `dates_based_on` | Dates Based On | Select — Leave Period · Joining Date · Custom Range | défaut `Leave Period` |
| `leave_period` | Leave Period | Link → `Leave Period` |  |
| `allocate_based_on_leave_policy` | Allocate Based On Leave Policy | Boolean | défaut `oui` |

## Leave Encashment

*Leave Encashment* — `hr/leave_encashment.yaml` · soumis

- **Numérotation** : série `LE-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `employee_name`
- **Icône** : `banknote`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `leave_period` | Leave Period | Link → `Leave Period` | **requis**; colonne de liste |
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `leave_type` | Leave Type | Link → `Leave Type` | **requis**; colonne de liste |
| `leave_allocation` | Leave Allocation | Link → `Leave Allocation` | lecture seule |
| `leave_balance` | Leave Balance | Number | lecture seule |
| `encashment_amount` | Encashment Amount | Currency | colonne de liste; lecture seule; devise de `currency` |
| `encashment_date` | Encashment Date | Date | défaut `today` |
| `additional_salary` | Additional Salary | Link → `Additional Salary` | lecture seule |
| `currency` | Currency | Link → `Currency` | **requis**; lecture seule |
| `company` | Company | Link → `Company` | **requis** |
| `encashment_days` | Encashment Days | Number |  |
| `actual_encashable_days` | Actual Encashable Days | Number | lecture seule; — Number of leaves eligible for encashment based on leave type settings |
| `payable_account` | Payable Account | Link → `Account` |  |
| `pay_via_payment_entry` | Pay via Payment Entry | Boolean | défaut `non`; — Process leave encashment via a separate Payment Entry instead of Salary Slip |
| `paid_amount` | Paid Amount | Currency | lecture seule; devise de `currency`; — Amount paid against this encashment |
| `status` | Status | Select — Draft · Unpaid · Paid · Submitted · Cancelled | lecture seule |
| `posting_date` | Posting Date | Date | défaut `today` |
| `expense_account` | Expense Account | Link → `Account` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |

## Leave Ledger Entry

*Leave Ledger Entry* — `hr/leave_ledger_entry.yaml` · soumis

- **Numérotation** : série `LLE-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `employee_name`
- **Icône** : `book-open`
- **Permissions explicites** — `write` : 0, `create` : 0, `delete` : 0, `submit` : 0, `cancel` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | colonne de liste |
| `employee_name` | Employee Name | Text |  |
| `leave_type` | Leave Type | Link → `Leave Type` | colonne de liste |
| `transaction_type` | Transaction Type | Text |  |
| `transaction_name` | Transaction Name | DynamicLink → `transaction_type` |  |
| `leaves` | Leaves | Number | colonne de liste |
| `from_date` | From Date | Date |  |
| `to_date` | To Date | Date |  |
| `is_carry_forward` | Is Carry Forward | Boolean | défaut `non` |
| `is_expired` | Is Expired | Boolean | défaut `non` |
| `is_lwp` | Is Leave Without Pay | Boolean | défaut `non` |
| `holiday_list` | Holiday List | Link → `Holiday List` |  |
| `company` | Company | Link → `Company` | **requis**; lecture seule |

## Leave Period

*Leave Period* — `hr/leave_period.yaml`

- **Vues** : calendar, gantt
- **Titre** : `company`
- **Icône** : `calendar-range`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `from_date` | From Date | Date | **requis**; colonne de liste |
| `to_date` | To Date | Date | **requis**; colonne de liste |
| `is_active` | Is Active | Boolean | défaut `non` |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `optional_holiday_list` | Holiday List for Optional Leave | Link → `Holiday List` |  |

## Leave Policy

*Leave Policy* — `hr/leave_policy.yaml` · soumis

- **Numérotation** : série `LP-{YYYY}-{#####}`
- **Titre** : `title`
- **Icône** : `scroll-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `leave_policy_details` | Leave Policy Details | Table → `Leave Policy Detail` |  |
| `title` | Leave Policy Name | Text | **requis**; colonne de liste |

## Leave Policy Assignment

*Leave Policy Assignment* — `hr/leave_policy_assignment.yaml` · soumis

- **Numérotation** : série `LPA-{YYYY}-{#####}`
- **Titre** : `employee_name`
- **Icône** : `user-check`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee name | Text | lecture seule; recopié de `employee.employee_name` |
| `leave_policy` | Leave Policy | Link → `Leave Policy` | **requis**; colonne de liste |
| `assignment_based_on` | Assignment based on | Select — Leave Period · Joining Date |  |
| `leave_period` | Leave Period | Link → `Leave Period` |  |
| `effective_from` | Effective From | Date | **requis** |
| `effective_to` | Effective To | Date | **requis** |
| `company` | Company | Link → `Company` | lecture seule |
| `carry_forward` | Add unused leaves from previous allocations | Boolean | défaut `non` |
| `leaves_allocated` | Leaves Allocated | Boolean | masqué; défaut `non` |

## Leave Policy Detail

*Leave Policy Detail* — `hr/leave_policy_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `leave_type` | Leave Type | Link → `Leave Type` | **requis**; colonne de liste |
| `annual_allocation` | Annual Allocation | Number | **requis**; colonne de liste |

## Leave Type

*Leave Type* — `hr/leave_type.yaml`

- **Titre** : `leave_type_name`
- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `leave_type_name` | Leave Type Name | Text | **requis**; colonne de liste |
| `max_leaves_allowed` | Maximum Leave Allocation Allowed per Leave Period | Number |  |
| `applicable_after` | Allow Leave Application After (Calendar Days) | Int | — Minimum calendar days required since Date of Joining to apply for this leave |
| `max_continuous_days_allowed` | Maximum Consecutive Leaves Allowed | Int | colonne de liste |
| `is_carry_forward` | Carry Forward | Boolean | colonne de liste; défaut `non` |
| `is_lwp` | Is Leave Without Pay | Boolean | défaut `non` |
| `is_optional_leave` | Leave for optional holiday | Boolean | défaut `non`; — These leaves are holidays permitted by the company however, availing it is optional for an Employee. |
| `allow_negative` | Allow Negative Balance | Boolean | défaut `non` |
| `include_holiday` | Include holidays within leaves as leaves | Boolean | défaut `non` |
| `is_compensatory` | Is Compensatory | Boolean | défaut `non` |
| `expire_carry_forwarded_leaves_after_days` | Expire Carry Forwarded Leaves (Days) | Int | — Calculated in days |
| `allow_encashment` | Allow Encashment | Boolean | défaut `non` |
| `earning_component` | Earning Component | Link → `Salary Component` |  |
| `is_earned_leave` | Is Earned Leave | Boolean | défaut `non` |
| `earned_leave_frequency` | Earned Leave Frequency | Select — Monthly · Quarterly · Half-Yearly · Yearly |  |
| `rounding` | Rounding | Select — 0.25 · 0.5 · 1.0 |  |
| `maximum_carry_forwarded_leaves` | Maximum Carry Forwarded Leaves | Number |  |
| `is_ppl` | Is Partially Paid Leave | Boolean | défaut `non` |
| `fraction_of_daily_salary_per_leave` | Fraction of Daily Salary per Leave | Number | — Fraction of one day's salary that is paid for each day of this leave. For example, 0.60 pays 60% of the daily  |
| `allow_over_allocation` | Allow Over Allocation | Boolean | défaut `non`; — Allows allocating more leaves than the number of days in the allocation period. |
| `allocate_on_day` | Allocate on Day | Select — First Day · Last Day · Date of Joining | défaut `Last Day`; — The day of the month when leaves should be allocated |
| `max_encashable_leaves` | Maximum Encashable Leaves | Int |  |
| `non_encashable_leaves` | Non-Encashable Leaves | Int | — Indicates the number of leaves that cannot be encashed from the leave balance. E.g. with a leave balance of 10 |

## Offer Term

*Offer Term* — `hr/offer_term.yaml`

- **Titre** : `offer_term`
- **Icône** : `file-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `offer_term` | Offer Term | Text | **requis**; colonne de liste |

## Overtime Details

*Overtime Details* — `hr/overtime_details.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `reference_document` | Reference Document | Link → `Attendance` | colonne de liste; lecture seule |
| `date` | Date | Date | **requis**; colonne de liste |
| `overtime_type` | Overtime Type | Link → `Overtime Type` | **requis**; colonne de liste |
| `overtime_duration` | Overtime Duration | Number | **requis**; colonne de liste |
| `maximum_overtime_hours_allowed` | Maximum Overtime Hours Allowed | Number | lecture seule |
| `standard_working_hours` | Standard Working Hours | Number | **requis** |

## Overtime Salary Component

*Overtime Salary Component* — `hr/overtime_salary_component.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `salary_component` | Salary Component | Link → `Salary Component` | **requis**; colonne de liste |

## Overtime Slip

*Overtime Slip* — `hr/overtime_slip.yaml` · soumis

- **Numérotation** : série `OS-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `employee_name`
- **Icône** : `timer`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `posting_date` | Posting Date | Date | **requis**; colonne de liste; défaut `today` |
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` |  |
| `company` | Company | Link → `Company` | **requis** |
| `overtime_details` | Overtime Details | Table → `Overtime Details` |  |
| `total_overtime_duration` | Total Overtime Duration | Number | lecture seule |
| `salary_slip` | Salary Slip | Link → `Salary Slip` | lecture seule |
| `start_date` | Start Date | Date | **requis** |
| `end_date` | End Date | Date | **requis** |
| `payroll_entry` | Payroll Entry | Link → `Payroll Entry` | lecture seule |
| `submitted_via_payroll_entry` | Submitted via Payroll Entry | Boolean | masqué; défaut `non` |

## Overtime Type

*Overtime Type* — `hr/overtime_type.yaml`

- **Titre** : `overtime_salary_component`
- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `overtime_salary_component` | Overtime Salary Component | Link → `Salary Component` | **requis**; colonne de liste; — Overtime earnings will be booked under this salary component for payout. |
| `applicable_salary_component` | Applicable Salary Components | Table → `Overtime Salary Component` | — Select the salary components whose total will be used from the salary slip to calculate the hourly overtime ra |
| `maximum_overtime_hours_allowed` | Maximum Overtime Hours Allowed Per Day | Number |  |
| `standard_multiplier` | Standard Multiplier | Number | **requis** |
| `applicable_for_weekend` | Apply for Weekend | Boolean | **requis**; défaut `non`; — Enable this to use a specific multiplier for weekends. If unchecked, the standard multiplier will be used inst |
| `weekend_multiplier` | Weekend Multiplier | Number |  |
| `applicable_for_public_holiday` | Apply for Public Holiday | Boolean | défaut `non`; — Enable this to use a specific multiplier for public holidays. If unchecked, the standard multiplier will be us |
| `public_holiday_multiplier` | Public Holiday Multiplier | Number |  |
| `hourly_rate` | Hourly Rate | Currency |  |
| `overtime_calculation_method` | Overtime Amount Calculation | Select — Salary Component Based · Fixed Hourly Rate | défaut `Salary Component Based`; — Choose how the hourly overtime amount is calculated: <ol style="padding-left:15px"><li>Fixed Hourly Rate: A fi |

## Purpose of Travel

*Purpose of Travel* — `hr/purpose_of_travel.yaml`

- **Icône** : `tag`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `purpose_of_travel` | Purpose of Travel | Text |  |

## PWA Notification

*PWA Notification* — `hr/pwa_notification.yaml`

- **Titre** : `from_user`
- **Icône** : `bell`
- **Permissions explicites** — `write` : 0, `create` : 0, `delete` : 0

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `from_user` | From User | Text | colonne de liste |
| `to_user` | To User | Text | colonne de liste |
| `message` | Message | TextEditor |  |
| `read` | Read | Boolean | défaut `non` |
| `reference_document_type` | Reference Document Type | Text | colonne de liste |
| `reference_document_name` | Reference Document Name | Text | colonne de liste |

## Shift Assignment

*Shift Assignment* — `hr/shift_assignment.yaml` · soumis

- **Numérotation** : série `SA-{YYYY}-{#####}`
- **Vues** : kanban, calendar, gantt
- **Titre** : `employee_name`
- **Icône** : `user-check`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis** |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `shift_type` | Shift Type | Link → `Shift Type` | **requis**; colonne de liste |
| `company` | Company | Link → `Company` | **requis** |
| `shift_request` | Shift Request | Link → `Shift Request` | lecture seule |
| `start_date` | Start Date | Date | **requis**; colonne de liste |
| `end_date` | End Date | Date |  |
| `status` | Status | Select — Active · Inactive | défaut `Active` |
| `shift_location` | Shift Location | Link → `Shift Location` |  |
| `shift_schedule_assignment` | Shift Schedule Assignment | Link → `Shift Schedule Assignment` | lecture seule |
| `overtime_type` | Overtime Type | Link → `Overtime Type` |  |

## Shift Assignment Tool

*Shift Assignment Tool* — `hr/shift_assignment_tool.yaml`

- **Vues** : kanban, calendar, gantt
- **Titre** : `status`
- **Icône** : `users`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `action` | Action | Select — Assign Shift · Assign Shift Schedule · Process Shift Requests | **requis**; colonne de liste; défaut `Assign Shift` |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `shift_type` | Shift Type | Link → `Shift Type` | colonne de liste |
| `status` | Status | Select — Active · Inactive | défaut `Active`; — When set to 'Inactive', employees with conflicting active shifts will not be excluded. |
| `start_date` | Start Date | Date | colonne de liste |
| `end_date` | End Date | Date |  |
| `branch` | Branch | Link → `Branch` |  |
| `department` | Department | Link → `Department` |  |
| `designation` | Designation | Link → `Designation` |  |
| `employment_type` | Employment Type | Link → `Employment Type` |  |
| `shift_type_filter` | Shift Type | Link → `Shift Type` |  |
| `approver` | Approver | Text |  |
| `from_date` | From Date | Date | — Shift Requests ending before this date will be excluded. |
| `to_date` | To Date | Date | — Shift Requests starting after this date will be excluded. |
| `grade` | Employee Grade | Link → `Employee Grade` |  |
| `shift_location` | Shift Location | Link → `Shift Location` |  |
| `shift_schedule` | Shift Schedule | Link → `Shift Schedule` |  |

## Shift Location

*Shift Location* — `hr/shift_location.yaml`

- **Titre** : `location_name`
- **Icône** : `map-pin`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `location_name` | Location Name | Text | **requis**; colonne de liste |
| `checkin_radius` | Checkin Radius | Int | — Radius within which check-in is allowed (in meters) |
| `longitude` | Longitude | Number |  |
| `geolocation` | Geolocation | JSON |  |
| `latitude` | Latitude | Number |  |

## Shift Request

*Shift Request* — `hr/shift_request.yaml` · soumis

- **Numérotation** : série `SR-{YYYY}-{#####}`
- **Vues** : kanban, calendar, gantt
- **Titre** : `employee_name`
- **Icône** : `calendar-clock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `shift_type` | Shift Type | Link → `Shift Type` | **requis**; colonne de liste |
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `from_date` | From Date | Date | **requis** |
| `to_date` | To Date | Date |  |
| `status` | Status | Select — Draft · Approved · Rejected | **requis**; défaut `Draft` |
| `approver` | Approver | Text | **requis** |

## Shift Schedule

*Shift Schedule* — `hr/shift_schedule.yaml` · soumis

- **Numérotation** : série `SHSC-{YYYY}-{#####}`
- **Titre** : `frequency`
- **Icône** : `calendar-days`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `frequency` | Frequency | Select — Every Week · Every 2 Weeks · Every 3 Weeks · Every 4 Weeks | **requis**; colonne de liste |
| `repeat_on_days` | Repeat On Days | Table → `Assignment Rule Day` |  |
| `shift_type` | Shift Type | Link → `Shift Type` | **requis**; colonne de liste |

## Shift Schedule Assignment

*Shift Schedule Assignment* — `hr/shift_schedule_assignment.yaml`

- **Titre** : `employee_name`
- **Icône** : `calendar-check-2`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `enabled` | Enabled | Boolean | défaut `oui`; — Select this if you want shift assignments to be automatically created indefinitely. |
| `create_shifts_after` | Create Shifts After | Date | défaut `today`; — New shift assignments will be created after this date. |
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `company` | Company | Link → `Company` | **requis**; colonne de liste; lecture seule |
| `shift_status` | Shift Status | Select — Active · Inactive | défaut `Active` |
| `shift_schedule` | Shift Schedule | Link → `Shift Schedule` | **requis** |
| `shift_location` | Shift Location | Link → `Shift Location` |  |

## Shift Type

*Shift Type* — `hr/shift_type.yaml`

- **Icône** : `clock`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `start_time` | Start Time | Time | **requis**; colonne de liste |
| `end_time` | End Time | Time | **requis**; colonne de liste |
| `holiday_list` | Holiday List | Link → `Holiday List` |  |
| `determine_check_in_and_check_out` | Determine Check-in and Check-out | Select — Alternating entries as IN and OUT during the same shift · Strictly based on Log Type in Employee Checkin |  |
| `working_hours_calculation_based_on` | Working Hours Calculation Based On | Select — First Check-in and Last Check-out · Every Valid Check-in and Check-out |  |
| `working_hours_threshold_for_half_day` | Working Hours Threshold for Half Day | Number | — Working hours below which Half Day is marked. (Zero to disable) |
| `working_hours_threshold_for_absent` | Working Hours Threshold for Absent | Number | — Working hours below which Absent is marked. (Zero to disable) |
| `begin_check_in_before_shift_start_time` | Begin check-in before shift start time (in minutes) | Int | défaut `60`; — The time before the shift start time during which Employee Check-in is considered for attendance. |
| `late_entry_grace_period` | Late Entry Grace Period | Int | — The time after the shift start time when check-in is considered as late (in minutes). |
| `early_exit_grace_period` | Early Exit Grace Period | Int | — The time before the shift end time when check-out is considered as early (in minutes). |
| `allow_check_out_after_shift_end_time` | Allow check-out after shift end time (in minutes) | Int | défaut `60`; — Time after the end of shift during which check-out is considered for attendance. |
| `enable_auto_attendance` | Enable Auto Attendance | Boolean | défaut `non`; — Mark attendance based on 'Employee Checkin' for Employees assigned to this shift. |
| `process_attendance_after` | Process Attendance After | Date | défaut `today`; — Attendance will be marked automatically only after this date. |
| `last_sync_of_checkin` | Last Sync of Checkin | Datetime | — Last Known Successful Sync of Employee Checkin. Reset this only if you are sure that all Logs are synced from  |
| `mark_auto_attendance_on_holidays` | Mark Auto Attendance on Holidays | Boolean | défaut `non`; — If enabled, auto attendance will be marked on holidays if Employee Checkins exist |
| `absent_buffer_days` | Absent Buffer (Days) | Int | défaut `1`; — Number of days after the shift ends before marking Absent for missing attendance. Set to 0 to mark Absent on t |
| `enable_late_entry_marking` | Enable Late Entry Marking | Boolean | défaut `non` |
| `enable_early_exit_marking` | Enable Early Exit Marking | Boolean | défaut `non` |
| `color` | Roster Color | Select — Blue · Cyan · Fuchsia · Green · Lime · Orange · Pink · Red · Violet · Yellow | défaut `Blue` |
| `auto_update_last_sync` | Automatically update Last Sync of Checkin | Boolean | défaut `non`; — Recommended for a single biometric device / checkins via mobile app |
| `allow_overtime` | Allow Overtime | Boolean | défaut `non` |
| `overtime_type` | Overtime Type | Link → `Overtime Type` |  |

## Skill

*Skill* — `hr/skill.yaml`

- **Icône** : `sparkles`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `skill_name` | Skill Name | Text |  |
| `description` | Description | LongText |  |

## Skill Assessment

*Skill Assessment* — `hr/skill_assessment.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `skill` | Skill | Link → `Skill` | **requis**; colonne de liste; lecture seule |
| `rating` | Rating | Rating | **requis**; colonne de liste |

## Staffing Plan

*Staffing Plan* — `hr/staffing_plan.yaml` · soumis

- **Numérotation** : série `SP-{YYYY}-{#####}`
- **Vues** : calendar, gantt
- **Titre** : `company`
- **Icône** : `users`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `department` | Department | Link → `Department` |  |
| `from_date` | From Date | Date | **requis** |
| `to_date` | To Date | Date | **requis** |
| `staffing_details` | Staffing Details | Table → `Staffing Plan Detail` |  |
| `total_estimated_budget` | Total Estimated Budget | Currency | lecture seule; devise de `company.default_currency` |

## Staffing Plan Detail

*Staffing Plan Detail* — `hr/staffing_plan_detail.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `designation` | Designation | Link → `Designation` | **requis**; colonne de liste |
| `number_of_positions` | Number Of Positions | Int | colonne de liste; lecture seule |
| `estimated_cost_per_position` | Estimated Cost Per Position | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `current_count` | Current Count | Int | lecture seule |
| `current_openings` | Current Openings | Int | lecture seule |
| `vacancies` | Vacancies | Int | colonne de liste |
| `total_estimated_cost` | Total Estimated Cost | Currency | colonne de liste; lecture seule; devise de `parent_company.default_currency` |

## Training Event

*Training Event* — `hr/training_event.yaml` · soumis

- **Numérotation** : série `TE-{YYYY}-{#####}`
- **Titre** : `event_name`
- **Icône** : `presentation`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `event_name` | Event Name | Text | **requis**; colonne de liste |
| `training_program` | Training Program | Link → `Training Program` |  |
| `event_status` | Event Status | Select — Scheduled · Completed · Cancelled | **requis**; colonne de liste |
| `has_certificate` | Has Certificate | Boolean | défaut `non` |
| `type` | Type | Select — Seminar · Theory · Workshop · Conference · Exam · Internet · Self-Study | **requis**; colonne de liste |
| `level` | Level | Select — Beginner · Intermediate · Advance |  |
| `company` | Company | Link → `Company` |  |
| `trainer_name` | Trainer Name | Text |  |
| `trainer_email` | Trainer Email | Text |  |
| `supplier` | Supplier | Link → `Supplier` |  |
| `contact_number` | Contact Number | Text |  |
| `course` | Course | Text |  |
| `location` | Location | Text | **requis**; colonne de liste |
| `start_time` | Start Time | Datetime | **requis** |
| `end_time` | End Time | Datetime | **requis** |
| `introduction` | Introduction | TextEditor | **requis** |
| `employees` | Employees | Table → `Training Event Employee` |  |
| `employee_emails` | Employee Emails | LongText | masqué |

## Training Event Employee

*Training Event Employee* — `hr/training_event_employee.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `status` | Status | Select — Open · Invited · Completed · Feedback Submitted | colonne de liste; défaut `Open` |
| `attendance` | Attendance | Select — Present · Absent | colonne de liste |
| `is_mandatory` | Is Mandatory | Boolean | colonne de liste; défaut `oui` |

## Training Feedback

*Training Feedback* — `hr/training_feedback.yaml` · soumis

- **Numérotation** : série `TF-{YYYY}-{#####}`
- **Titre** : `employee_name`
- **Icône** : `message-square-text`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | **requis** |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `course` | Course | Text | lecture seule |
| `training_event` | Training Event | Link → `Training Event` | **requis** |
| `event_name` | Event Name | Text | colonne de liste; lecture seule |
| `trainer_name` | Trainer Name | Text | colonne de liste; lecture seule |
| `feedback` | Feedback | LongText | **requis** |

## Training Program

*Training Program* — `hr/training_program.yaml`

- **Vues** : kanban
- **Titre** : `status`
- **Icône** : `graduation-cap`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `training_program` | Training Program | Text | **requis**; colonne de liste |
| `status` | Status | Select — Scheduled · Completed · Cancelled | colonne de liste; défaut `Scheduled` |
| `company` | Company | Link → `Company` | **requis**; colonne de liste |
| `trainer_name` | Trainer Name | Text |  |
| `trainer_email` | Trainer Email | Text |  |
| `supplier` | Supplier | Link → `Supplier` |  |
| `contact_number` | Contact Number | Text |  |
| `description` | Description | TextEditor | **requis** |

## Training Result

*Training Result* — `hr/training_result.yaml` · soumis

- **Numérotation** : série `TR-{YYYY}-{#####}`
- **Titre** : `training_event`
- **Icône** : `award`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `training_event` | Training Event | Link → `Training Event` | **requis**; colonne de liste |
| `employees` | Employees | Table → `Training Result Employee` |  |
| `employee_emails` | Employee Emails | LongText | masqué |

## Training Result Employee

*Training Result Employee* — `hr/training_result_employee.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `employee` | Employee | Link → `Employee` | colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `department` | Department | Link → `Department` | lecture seule |
| `hours` | Hours | Number | colonne de liste |
| `grade` | Grade | Text | colonne de liste |
| `comments` | Comments | LongText | colonne de liste |

## Travel Itinerary

*Travel Itinerary* — `hr/travel_itinerary.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `travel_from` | Travel From | Text | colonne de liste |
| `travel_to` | Travel To | Text | colonne de liste |
| `mode_of_travel` | Mode of Travel | Select — Flight · Train · Taxi · Rented Car | colonne de liste |
| `meal_preference` | Meal Preference | Select — Vegetarian · Non-Vegetarian · Gluten Free · Non Diary |  |
| `travel_advance_required` | Travel Advance Required | Boolean | défaut `non` |
| `advance_amount` | Advance Amount | Text |  |
| `departure_date` | Departure Datetime | Datetime | colonne de liste |
| `arrival_date` | Arrival Datetime | Datetime |  |
| `lodging_required` | Lodging Required | Boolean | défaut `non` |
| `preferred_area_for_lodging` | Preferred Area for Lodging | Text |  |
| `check_in_date` | Check-in Date | Date |  |
| `check_out_date` | Check-out Date | Date |  |
| `other_details` | Other Details | LongText |  |

## Travel Request

*Travel Request* — `hr/travel_request.yaml` · soumis

- **Numérotation** : série `TRRE-{YYYY}-{#####}`
- **Titre** : `employee_name`
- **Icône** : `plane-takeoff`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `travel_type` | Travel Type | Select — Domestic · International | **requis**; colonne de liste |
| `travel_funding` | Travel Funding | Select — Require Full Funding · Fully Sponsored · Partially Sponsored, Require Partial Funding |  |
| `travel_proof` | Copy of Invitation/Announcement | Attach |  |
| `purpose_of_travel` | Purpose of Travel | Link → `Purpose of Travel` | **requis**; colonne de liste |
| `details_of_sponsor` | Details of Sponsor (Name, Location) | Text |  |
| `description` | Any other details | LongText |  |
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `employee_name` | Employee Name | Text | lecture seule; recopié de `employee.employee_name` |
| `cell_number` | Contact Number | Text |  |
| `prefered_email` | Contact Email | Text |  |
| `date_of_birth` | Date of Birth | Date | lecture seule |
| `personal_id_type` | Identification Document Type | Link → `Identification Document Type` |  |
| `personal_id_number` | Identification Document Number | Text |  |
| `passport_number` | Passport Number | Text |  |
| `itinerary` | Itinerary | Table → `Travel Itinerary` |  |
| `cost_center` | Cost Center | Link → `Cost Center` |  |
| `costings` | Costing | Table → `Travel Request Costing` |  |
| `name_of_organizer` | Name of Organizer | Text |  |
| `address_of_organizer` | Address of Organizer | Text |  |
| `other_details` | Other Details | LongText |  |
| `company` | Company | Link → `Company` | lecture seule |

## Travel Request Costing

*Travel Request Costing* — `hr/travel_request_costing.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `expense_type` | Expense Type | Link → `Expense Claim Type` | colonne de liste |
| `sponsored_amount` | Sponsored Amount | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `funded_amount` | Funded Amount | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `total_amount` | Total Amount | Currency | colonne de liste; devise de `parent_company.default_currency` |
| `comments` | Comments | LongText |  |

## Vehicle Log

*Vehicle Log* — `hr/vehicle_log.yaml` · soumis

- **Numérotation** : série `VL-{YYYY}-{#####}`
- **Vues** : calendar
- **Titre** : `employee`
- **Icône** : `car`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `naming_series` | Series | Select — HR-VLOG-.YYYY.- | **requis** |
| `license_plate` | License Plate | Link → `Vehicle` | **requis**; colonne de liste |
| `employee` | Employee | Link → `Employee` | **requis**; colonne de liste |
| `model` | Model | Text | lecture seule |
| `make` | Make | Text | lecture seule |
| `date` | Date | Date | **requis** |
| `odometer` | Current Odometer value  | Int | **requis** |
| `fuel_qty` | Fuel Qty | Decimal |  |
| `price` | Fuel Price | Currency |  |
| `supplier` | Supplier | Link → `Supplier` |  |
| `invoice` | Invoice Ref | Text |  |
| `service_detail` | Service Detail | Table → `Vehicle Service` |  |
| `last_odometer` | Last Odometer Value  | Int | **requis**; lecture seule |

## Vehicle Service

*Vehicle Service* — `hr/vehicle_service.yaml` · table enfant

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `service_item` | Service Item | Link → `Vehicle Service Item` | **requis**; colonne de liste |
| `type` | Type | Select — Inspection · Service · Change | **requis**; colonne de liste |
| `frequency` | Frequency | Select — Mileage · Monthly · Quarterly · Half Yearly · Yearly | **requis**; colonne de liste |
| `expense_amount` | Expense | Currency | **requis**; colonne de liste |

## Vehicle Service Item

*Vehicle Service Item* — `hr/vehicle_service_item.yaml`

- **Titre** : `service_item`
- **Icône** : `wrench`

| Champ | Libellé | Type | Attributs |
|---|---|---|---|
| `service_item` | Service Item | Text | **requis**; colonne de liste |
