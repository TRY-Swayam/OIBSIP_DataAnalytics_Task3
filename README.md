# Cleaning Data
**Oasis Infobyte SIP — Data Analytics (Level 1, Task 3)**

## Objective
Turn a deliberately messy retail dataset into a clean, analysis-ready one and document every decision.

## Files
- `messy_retail_data.csv` — input (2,580 rows, with injected problems)
- `Cleaning_Data.ipynb` — the full cleaning workflow with justifications
- `cleaned_retail_data.csv` — output (2,500 rows)

## Problems found and how they were fixed
| Problem | Fix |
|---|---|
| 80 duplicate rows | Removed |
| Gender written as male / M / MALE / f / ... | Mapped to `Male` / `Female` |
| Category with inconsistent case and trailing spaces | Trimmed and title-cased |
| Dates in two formats (YYYY-MM-DD and DD/MM/YYYY) | Parsed each format, converted to datetime |
| Prices stored as text (`Rs.1234.50`) | Prefix stripped, converted to float |
| Impossible ages (-5, 150, 999) | Set to missing, imputed with the median |
| Price outliers (15 entries) | Detected with the IQR method per product, re-imputed with the product median |
| Missing Age / Category / Price | Median / mode / product-median imputation (justified in the notebook) |
| `Total Amount` inconsistent after fixes | Recalculated as Quantity × Price per Unit |

## Before vs. after
| | Before | After |
|---|---|---|
| Rows | 2,580 | 2,500 |
| Duplicate rows | 80 | 0 |
| Null values | 367 | 0 |
| Columns with correct dtype | 2/5 | 5/5 |

## Tools
Python, pandas, NumPy, Jupyter Notebook
