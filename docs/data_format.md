# Data Import and File Formats

## Supported files

- CSV, TSV, and delimited text (`.csv`, `.tsv`, `.txt`)
- Excel workbooks (`.xlsx`, `.xls`, `.xlsm`)

The import dialog lists workbook sheets and lets you choose the delimiter, encoding, and whether
the first row is a header. A preview appears before loading.

## Table shape

TMApp expects a rectangular table with one row per document or observation:

| review_text | rating | sentiment | category | price |
|---|---|---|---|---|
| Excellent product | 5 | positive | Home | 29.99 |
| Arrived damaged | 1 | negative | Home | 34.50 |

- **Text column** (required): the cell text analyzed by preprocessing and text methods.
- **Label column** (optional): class labels for supervised machine learning.
- **Group column** (optional): categories used by sentiment summaries and group comparisons.
- **Date column** (optional): dates used for sentiment trends.

Empty text values are ignored by text analyses. Rows with missing labels are ignored by
supervised training. Missing numeric values are removed per analysis.

## Editing after import

Loaded datasets can be edited on the **Data** page: cell values (double-click), added or
deleted rows, and added, renamed, or deleted columns. Numeric columns widen automatically when
a decimal or missing value is entered. Use **Export Dataset...** to save an edited copy; the
original file on disk is never modified by editing.

## CSV encoding and delimiters

Use the encoding list when a file contains accented or non-Latin characters. `utf-8-sig` handles
Excel-exported UTF-8 files with a byte-order mark. Auto delimiter detection covers commas, tabs,
semicolons, and pipes.

## Excel tips

- Use one header row and avoid merged cells.
- Remove charts, images, and notes above the header if they create empty columns.
- Keep formulas evaluated; pandas reads stored values, not Excel calculation results.
- Select the correct sheet before loading.

## Text quality

Preprocessing handles HTML, URLs, emails, punctuation, and case, but source quality still
matters. Remove template boilerplate and duplicated headers when possible. Duplicate detection
in preprocessing compares processed documents, not raw rows.

## Size guidance

TMApp is designed for typical survey, review, and document datasets. Text matrices remain sparse,
but very large corpora (hundreds of thousands of long documents) increase memory use in
descriptive statistics, reports, and dense preview tables. These views cap rows, but the source
data remains in memory for the session.
