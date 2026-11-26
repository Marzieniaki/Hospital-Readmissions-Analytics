# Cleaning log

Total rows in `diabetic_data.csv`: 101,766 (one row = one hospital visit).
Missing values are coded as `?`.

## Step 1: Missing values

Counts checked with a SQL query in DB Browser for SQLite.

| Column | Missing count | Share of rows | Decision | Reason |
|---|---|---|---|---|
| race | 2,273 | 2.2% | | |
| weight | 98,569 | 96.9% | | |
| payer_code | 40,256 | 39.6% | | |
| medical_specialty | 49,949 | 49.1% | | |
| diag_1 | 21 | 0.02% | | |
| diag_2 | 358 | 0.35% | | |
| diag_3 | 1,423 | 1.4% | | |

Notes:
- Gender has 3 rows marked `Unknown/Invalid`. It doesn't use `?`.
- Age has no missing values.
- In `A1Cresult` and `max_glu_serum`, `None` means the test wasn't done. It is not treated as missing.

## Step 2: Repeat patients

Decision on repeat visits by the same `patient_nbr`:

Reason:

## Step 3: Code labels

Replaced codes with labels from `IDS_mapping.csv`:
