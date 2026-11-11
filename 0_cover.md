Assignment 2: The Dirty Ledger — Cover Sheet

- Student: Ghulam Murtaza
- ERP: 37176
- File audited: teaching_prices_messy.csv

Summary
The provided ledger (97 rows, 6 columns) was audited. I identified 5 specific data quality issues: a missing price, a comma-formatted price, an extreme outlier, a case-mismatched item label, and an exact duplicate row. 

I applied the principle: "A clean-looking table with undocumented changes is worse than a messy honest one."Therefore, I corrected only lossless formatting issues (casting types, stripping commas, fixing case). I flagged the missing price and the extreme outlier rather than deleting or imputing them, and I excluded the exact duplicate row. 

A Cleaning Code Court was held on AI-generated code. The AI suggested imputing missing prices and dropping outliers—both of which I rejected to preserve data integrity.
