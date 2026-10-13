# Loan Default Risk Dashboard (Power BI)

An interactive Power BI dashboard analysing **32,409 personal loans** to find which borrower and loan characteristics are linked to a higher risk of default.

![Loan Default Risk Dashboard](images/dashboard.png)

**Overall default rate: 21.87%** (about 1 in 5 loans).

---

## Key findings

**1. Debt consolidation loans default the most.**
Debt consolidation loans had a 28.7% default rate, compared with 14.9% for venture and 17.3% for education loans, almost double. One possible reason: education and venture loans are investments in future income, while debt consolidation borrowers are already struggling with debt, and the new loan may create a false sense of security that leads to more borrowing.

**2. Default risk jumps sharply between Grade C and Grade D.**
Default rates rise gradually from Grade A (10.0%) to Grade C (20.8%), then nearly triple to 59.0% at Grade D, reaching 98.4% at Grade G. The grading system clearly separates safe and risky borrowers, and D is where the risk becomes serious. A lender could use Grade D as the cut-off for stricter checks or higher interest rates.

**3. Lower income means much higher default risk.**
Borrowers earning under 30k defaulted at 47.2%, about 5 times the rate of those earning 100k+ (9.0%). The rate falls steadily with every income band. A likely reason is that lower earners have less room in their budget to keep up with repayments when something unexpected happens.

**4. Renters default about 4× more often than outright homeowners.**
Renters had a 31.6% default rate, compared with 12.6% for mortgage holders and 7.5% for those who own their home outright.

---

## What I did

1. **Cleaned the data in Power Query.** I removed 172 invalid or duplicate rows (impossible ages and employment lengths, plus exact duplicates). I kept rows with missing interest rates to avoid losing 10% of the data. Details: [`docs/data_cleaning.md`](docs/data_cleaning.md)
2. **Engineered features.** I created `Income Band`, `Age Group` and `Loan Outcome` columns with conditional logic.
3. **Wrote DAX measures** for Total Loans, Defaulted Loans, Default Rate, Avg Loan Amount and Avg Interest Rate. Details: [`docs/dax_measures.md`](docs/dax_measures.md)
4. **Built a one-page dashboard** with 4 KPI cards, 4 charts and 2 slicers (Age Group, Previous Default) that filter every visual at once.

## Tools

Power BI Desktop · Power Query · DAX

## Data

[Credit Risk Dataset](https://www.kaggle.com/datasets/laotse/credit-risk-dataset) by laotse on Kaggle: 32,581 loan records with 12 columns, including borrower age, income, home ownership, loan purpose, loan grade, loan amount, interest rate and loan status (default or not).

## Files

```
├── Loan Default Dashboard.pbix   Power BI file (open with Power BI Desktop)
├── images/dashboard.png
└── docs/
    ├── data_cleaning.md
    └── dax_measures.md
```

## Limitations

- The dashboard shows **associations, not causes**. For example, low-grade loans may default more partly because they also go to lower-income borrowers.
- The reasons given in the findings are possible explanations, not conclusions proven by the data.
- The dataset has no dates, so trends over time can't be analysed.
