# DAX Measures

All measures are created on the `credit_risk_dataset` table.

| Measure | Formula | Purpose |
|---|---|---|
| Total Loans | `COUNTROWS(credit_risk_dataset)` | Number of loans after cleaning |
| Defaulted Loans | `CALCULATE(COUNTROWS(credit_risk_dataset), credit_risk_dataset[loan_status] = 1)` | Loans where the borrower defaulted |
| Default Rate | `DIVIDE([Defaulted Loans], [Total Loans])` | Main KPI. `DIVIDE` returns blank instead of an error if a filter leaves zero loans |
| Avg Loan Amount | `AVERAGE(credit_risk_dataset[loan_amnt])` | Average loan size |
| Avg Interest Rate | `AVERAGE(credit_risk_dataset[loan_int_rate])` | Average interest rate (%); blanks are ignored |

Every chart on the dashboard uses **Default Rate** as its value, so the slicers (Age Group, Previous Default) recalculate all charts and cards at once.
