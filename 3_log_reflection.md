3 — Court Verdicts, Log Rows, Reflection

Court Verdicts (AI Cleaning Code)

| AI Line (Simulated) | Claim | Verdict | Evidence / Reason |
| `df.drop_duplicates()` | Remove dupes | **KEEP** | Removed exactly 1 row (97→96). The duplicate was a byte-identical copy of a prior record. |
| `df['item'] = df['item'].str.title()` | Standardise text | **KEEP** | Fixed "oil b" to "Oil B". Counts are now uniform (24 of each item). |
| `df['price'].str.replace(',', '')` | Clean numbers | **KEEP** | "1,250" successfully cast to float 1250.0. |
| `df['price'].fillna(df['price'].median())` | Impute missing | **REJECT** | Fabricates a price for Pulse C. Instead, I retained the `NaN` and added `flag_price_missing`. |
| `df = df[df['price'] < 5000]` | Drop outliers | **REJECT** | Deleted the 9999 Sweetener D row. I retained it and added `flag_price_outlier` because we cannot assume it isn't a genuine data point. |
| `df.dropna()` | Drop missing rows | **REJECT** | Would delete a valid observation (Pulse C) just because one cell is missing. |

Cleaning Log
- Rows:97 (before) → 96 (after). 1 exact duplicate removed.
- Missing values: 1 missing price retained and flagged.
- Item counts: All 4 items now appear exactly 24 times.
- Labels: "oil b" corrected to "Oil B" (lossless).
- Numbers: Price text "1,250" cast to float `1250.0` (value unchanged).

Reflection
Differences from AI: The AI's standard approach was to drop missing rows and drop outliers to make the data "clean." I rejected this because in an audit, deleting the 9999 outlier and imputing the missing Pulse C price hides the exact anomalies Ms. Noor needs to know about. Flagging is better supported than deleting.
What I missed alone: The AI correctly reminded me to check if the 97th row was a duplicate and prompted me to standardise the item casing before running a final count.
