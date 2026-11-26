# Hospital Readmissions Analytics

SQL star schema and dashboard for 30-day hospital readmissions.

**Status:** In progress (Phase 0: setup)

## Data

Source: "Diabetes 130-US hospitals for years 1999–2008", UCI Machine Learning Repository.
Link: https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008
License: Creative Commons Attribution 4.0 International (CC BY 4.0)


The raw file is kept unedited in `data/raw/`.

### Dataset notes (from the UCI page)

- **What one row is:** a hospital admission (an inpatient encounter) for a patient diagnosed with diabetes.
- **Who is in it:** only encounters that met all five criteria: (1) an inpatient admission, (2) a diabetes diagnosis entered during the encounter, (3) a stay of 1 to 14 days, (4) lab tests performed, and (5) medications given. The results describe this group, not all hospital patients.
- **Time and place:** 10 years of care (1999 to 2008) at 130 US hospitals and integrated delivery networks.
- **Sensitive information:** the data includes age, gender, and race. Don't try to identify anyone, and mention this in your write-up.
- **Splits:** the UCI page gives no recommended split. Use a standard train/test split, or train/validation/test if you build a model.

## Business questions

1. [To be written in Phase 1]

## Project structure

```
data/raw/        Raw dataset (unedited)
data/processed/  Cleaned data
sql/             Schema, load, and analysis SQL
docs/            Data dictionary, cleaning log, schema diagram, results
dashboard/       Power BI or Tableau file and screenshots
```

## How to run

[To be written in Phase 8]
