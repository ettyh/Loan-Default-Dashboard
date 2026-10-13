# Data Cleaning (Power Query)

Raw data: 32,581 rows, 12 columns. Final data: **32,409 rows**.

| Step | Rows affected | Decision |
|---|---|---|
| Removed impossible ages (123, 144) | 5 | Data entry errors |
| Removed impossible employment length (123 years) | 2 | Data entry errors |
| Removed exact duplicate rows | 165 | Would double-count loans |
| Missing `loan_int_rate` (~10%) | kept | Deleting would lose 10% of the data; averages ignore blanks |
| Missing `person_emp_length` (~3%) | kept | Not used in the visuals |

Filtering used value checkboxes instead of number filters, so rows with blank values were not removed by accident.

## New columns

| Column | Logic |
|---|---|
| Loan Outcome | `loan_status` = 1 → "Defaulted", else "Repaid" |
| Income Band | Under 30k / 30k–50k / 50k–75k / 75k–100k / 100k+ |
| Age Group | Under 25 / 25–34 / 35–44 / 45+ |
