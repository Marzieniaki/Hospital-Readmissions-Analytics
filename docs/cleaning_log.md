# Cleaning log

Total rows in `diabetic_data.csv`: 101,766 (one row = one hospital visit).
Missing values are coded as `?`.

## Step 1: Missing values

Counts checked with a SQL query in DB Browser for SQLite.

| Column | Missing count | Share of rows | Decision | Reason |
|---|---|---|---|---|
| race | 2,273 | 2.2% | Keep. Label missing values as "Unknown." | Only 2.2% is missing, so the column is still usable. Keeping "Unknown" as its own group avoids dropping visits. |
| weight | 98,569 | 96.9% | Leave out of the analysis. | Almost all values are missing, so any result would rest on about 3% of visits. |
| payer_code | 40,256 | 39.6% | Keep. Label missing values as "Unknown." | About 40% is missing. Keeping "Unknown" as its own group keeps those visits in the analysis, and the gap is stated in the write-up. |
| medical_specialty | 49,949 | 49.1% | Keep. Label missing values as "Unknown." | About half is missing. Keeping "Unknown" as its own group keeps those visits in the analysis, and the gap is stated in the write-up. |
| diag_1 | 21 | 0.02% | Keep. Label missing values as "Unknown." | Only 21 rows. Keeping the visits is simplest. |
| diag_2 | 358 | 0.35% | Keep. Label missing values as "Unknown." | Less than 1% is missing. Keeping the visits is simplest. |
| diag_3 | 1,423 | 1.4% | Keep. Label missing values as "Unknown." | Only 1.4% is missing. Keeping the visits is simplest. |

Notes:
- Gender has 3 rows marked `Unknown/Invalid`. It doesn't use `?`.
- Age has no missing values.
- In `A1Cresult` and `max_glu_serum`, `None` means the test wasn't done. It is not treated as missing.

## Step 2: Repeat patients

Decision: Keep all visits, including repeat visits by the same `patient_nbr`.

Reason: Most of the business questions are about what happens over time. For example, readmission is only visible when you can see a patient's visits in order. Keeping only the first visit would remove the readmission outcome. When a rate is reported per patient rather than per visit, count distinct `patient_nbr` values so that patients with many visits aren't counted repeatedly.

## Step 3: Code labels

Replaced codes with labels from `IDS_mapping.csv`:
