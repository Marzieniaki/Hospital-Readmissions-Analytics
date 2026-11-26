# Data dictionary

One row = one hospital visit (encounter). The same patient can appear in several rows.

Source: `data/raw/diabetic_data.csv`: 101,766 rows and 50 columns.
Code labels: `data/raw/IDS_mapping.csv`.
A `?` value means the information is missing or unknown.

| # | Column | Type | Meaning in plain words | Values in the data |
|---|---|---|---|---|
| 1 | encounter_id | ID (a label, not for math) | A number that identifies each hospital visit. Every row has a different one. | Unique per row |
| 2 | patient_nbr | ID (a label, not for math) | A number that identifies each patient. The same patient can have several visits, so this number can repeat. | 71,518 patients |
| 3 | race | Categorical | The patient's race group. `?` means unknown. | Caucasian, AfricanAmerican, Hispanic, Asian, Other, `?` |
| 4 | gender | Categorical | The patient's gender. | Female, Male, Unknown/Invalid |
| 5 | age | Categorical (ordered age ranges) | The patient's age range. `[70-80)` means 70 up to, but not including, 80. | [0-10) to [90-100) |
| 6 | weight | Categorical (ordered weight ranges) | The patient's weight range, in pounds. Mostly missing. | Ranges such as [75-100), or `?` |
| 7 | admission_type_id | Categorical (coded) | The type of admission, as a code. Look up the label in IDS_mapping.csv. | 1 to 8 |
| 8 | discharge_disposition_id | Categorical (coded) | Where the patient went when leaving the hospital, as a code. Look up the label in IDS_mapping.csv. | 26 codes |
| 9 | admission_source_id | Categorical (coded) | How or from where the patient arrived, as a code. Look up the label in IDS_mapping.csv. | 17 codes |
| 10 | time_in_hospital | Integer (days) | Number of days the patient stayed in the hospital. | 1 to 14 days |
| 11 | payer_code | Categorical | The insurance or payer type, as a code. `?` means missing. | Codes such as MC and HM, or `?` |
| 12 | medical_specialty | Categorical | The specialty of the doctor who admitted the patient. `?` means missing. | 73 specialties, or `?` |
| 13 | num_lab_procedures | Integer (count) | Number of lab tests done during the visit. | Counts |
| 14 | num_procedures | Integer (count) | Number of non-lab procedures done during the visit. | 0 to 6 |
| 15 | num_medications | Integer (count) | Number of different medicines given during the visit. | Counts |
| 16 | number_outpatient | Integer (count) | Number of outpatient visits in the year before this visit. | Counts |
| 17 | number_emergency | Integer (count) | Number of emergency visits in the year before this visit. | Counts |
| 18 | number_inpatient | Integer (count) | Number of hospital stays in the year before this visit. | Counts |
| 19 | diag_1 | Categorical (diagnosis code) | Main diagnosis, coded as the first three digits of the ICD-9 code. `?` means missing. | Codes such as 428 |
| 20 | diag_2 | Categorical (diagnosis code) | Second diagnosis, coded as the first three digits of the ICD-9 code. `?` means missing. | Codes such as 276 |
| 21 | diag_3 | Categorical (diagnosis code) | Third diagnosis, coded as the first three digits of the ICD-9 code. `?` means missing. The UCI page says there are 954 distinct values, but the file has 790. Note this in your write-up. | Codes such as 250 |
| 22 | number_diagnoses | Integer (count) | Number of diagnoses recorded for the visit. | 1 to 16 |
| 23 | max_glu_serum | Categorical (ordered test result) | Highest glucose test result: `>200` or `>300`, `Norm` for normal, or `None` if the test wasn't done. | None, Norm, >200, >300 |
| 24 | A1Cresult | Categorical (ordered test result) | A1C test result, which shows average blood sugar over the past few months: `>8` (above 8%), `>7` (above 7% but below 8%), `Norm` (below 7%), or `None` if the test wasn't done. | None, Norm, >7, >8 |
| 25 | metformin | Categorical (ordered dose change) | Diabetes medicine. `No` = not prescribed, `Steady` = same dose, `Up` = dose increased, `Down` = dose decreased. | No, Steady, Up, Down |
| 26 | repaglinide | Categorical (ordered dose change) | Diabetes medicine (same values as metformin). | No, Steady, Up, Down |
| 27 | nateglinide | Categorical (ordered dose change) | Diabetes medicine (same values as metformin). | No, Steady, Up, Down |
| 28 | chlorpropamide | Categorical (ordered dose change) | Diabetes medicine (same values as metformin). | No, Steady, Up, Down |
| 29 | glimepiride | Categorical (ordered dose change) | Diabetes medicine (same values as metformin). | No, Steady, Up, Down |
| 30 | acetohexamide | Categorical (ordered dose change) | Diabetes medicine. Almost always `No`. | No, Steady |
| 31 | glipizide | Categorical (ordered dose change) | Diabetes medicine (same values as metformin). | No, Steady, Up, Down |
| 32 | glyburide | Categorical (ordered dose change) | Diabetes medicine (same values as metformin). | No, Steady, Up, Down |
| 33 | tolbutamide | Categorical (ordered dose change) | Diabetes medicine. Almost always `No`. | No, Steady |
| 34 | pioglitazone | Categorical (ordered dose change) | Diabetes medicine (same values as metformin). | No, Steady, Up, Down |
| 35 | rosiglitazone | Categorical (ordered dose change) | Diabetes medicine (same values as metformin). | No, Steady, Up, Down |
| 36 | acarbose | Categorical (ordered dose change) | Diabetes medicine (same values as metformin). | No, Steady, Up, Down |
| 37 | miglitol | Categorical (ordered dose change) | Diabetes medicine (same values as metformin). | No, Steady, Up, Down |
| 38 | troglitazone | Categorical (ordered dose change) | Diabetes medicine. Almost always `No`. | No, Steady |
| 39 | tolazamide | Categorical (ordered dose change) | Diabetes medicine (same values as metformin). | No, Steady, Up |
| 40 | examide | Categorical (ordered dose change) | Diabetes medicine. Always `No` in this data. | No |
| 41 | citoglipton | Categorical (ordered dose change) | Diabetes medicine. Always `No` in this data. | No |
| 42 | insulin | Categorical (ordered dose change) | Insulin. Same values as metformin. | No, Steady, Up, Down |
| 43 | glyburide-metformin | Categorical (ordered dose change) | Combination medicine. Same values as metformin. | No, Steady, Up, Down |
| 44 | glipizide-metformin | Categorical (ordered dose change) | Combination medicine. Almost always `No`. | No, Steady |
| 45 | glimepiride-pioglitazone | Categorical (ordered dose change) | Combination medicine. Almost always `No`. | No, Steady |
| 46 | metformin-rosiglitazone | Categorical (ordered dose change) | Combination medicine. Almost always `No`. | No, Steady |
| 47 | metformin-pioglitazone | Categorical (ordered dose change) | Combination medicine. Almost always `No`. | No, Steady |
| 48 | change | Categorical (binary) | Whether there was a change in diabetes medicines during the visit, either the dose or the medicine itself. `Ch` = change, `No` = no change. | Ch, No |
| 49 | diabetesMed | Categorical (binary) | Whether any diabetes medicine was prescribed. | Yes, No |
| 50 | readmitted | Categorical (target) | Whether the patient came back to the hospital. `NO` = no record of readmission, `<30` = readmitted within 30 days, `>30` = readmitted after 30 days. The UCI page writes this value as `No`, but the file uses `NO`. | NO, <30, >30 |

## Notes
- Verify the meanings of codes like `MC` and `HM` (column 11) on the UCI dataset page before you use them in your write-up.
- Columns 25 to 47 describe medicines. Many of them are `No` for almost every row. Check how many rows each one has before you use it.
- Medicine columns (25 to 47), as the UCI page defines them: the value says whether the drug was prescribed, or whether its dose changed during the encounter. `Up` = dose increased, `Down` = dose decreased, `Steady` = dose unchanged, `No` = not prescribed. These columns have no missing values (`?`).
