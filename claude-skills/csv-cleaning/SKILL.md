---
name: csv-cleaning
description: Use when the user hands over a messy CSV/TSV/spreadsheet and wants it cleaned - fix headers, types, duplicates, blanks, inconsistent formats. Trigger on "clean this csv / fix this data / dedupe / normalize", or when a file has malformed rows, mixed formats, or junk before you can analyze it.
---

# CSV Cleaning

Turn a messy table into clean, typed, analysis-ready data. Show what changed - never silently drop rows.

## Pipeline

1. **Profile first.** Load with pandas. Report: shape, column names, dtypes, % missing per column,
   duplicate count, and 5 sample rows. Understand before touching.
2. **Fix structure.**
   - strip whitespace from headers, snake_case them
   - detect a misplaced header row / junk rows above the real data and drop them
   - split merged columns, unmerge wrongly-joined fields
3. **Fix types.**
   - numbers: strip `$ , %` and cast to numeric
   - dates: parse to ISO `YYYY-MM-DD`
   - booleans: map yes/no/1/0/true/false consistently
4. **Fix values.**
   - trim whitespace, standardize case for categoricals
   - normalize obvious variants ("USA"/"U.S."/"United States" -> one)
   - handle missing: fill, flag, or drop - and say which and why
5. **Dedupe.** Report how many duplicates and on which keys.

## Rules

- **Log every change.** End with a short changelog: rows in -> rows out, columns renamed,
  types fixed, dupes removed, missing handled.
- Never delete data without stating the count and reason.
- Keep a copy of any rows you quarantine (e.g. `rejected_rows.csv`).

## Output

The cleaned file (`<name>_clean.csv`) + a plain-language changelog of what you did.
