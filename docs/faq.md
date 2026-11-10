# FAQ and Troubleshooting

## Why is my text column empty?

Choose a text column on the Data page or in the import dialog. The text column must contain
non-empty cells. Whitespace-only cells are treated as empty.

## Why did preprocessing remove every document?

The combination of stopword removal, short-token filtering, punctuation removal, and custom regex
may have removed all tokens. Lower the minimum token length, disable aggressive cleaning, or
inspect the custom regex. Use Preview first.

## Why is lemmatization not working?

WordNet data is optional. Install it from **Help > Download NLP Data**. Until then, lemmatization
falls back to stemming and the result includes a warning.

## Why is sentiment using the fallback lexicon?

VADER data is not installed. Install it from **Help > Download NLP Data**, or choose VADER and
follow the warning. The bundled lexicon is deterministic and works offline.

## Why can't I train a classifier?

Supervised training needs:

- A mapped label column.
- At least 10 labeled non-empty documents.
- At least two classes.
- At least two examples per class.

If a class is rare, merge classes or collect more examples.

## Why did logistic regression fail?

Logistic regression needs a binary target. Perfect separation, constant predictors, or too few
observations also prevent estimation. Choose different predictors, combine rare classes, or use a
penalized classifier on the Machine Learning page.

## Why is the matrix invalid after preprocessing?

The matrix depends on the exact processed documents and vocabulary. Rerunning preprocessing or
changing the text column invalidates it. Rebuild the matrix after preprocessing.

## Why do reports show only part of a large table?

Reports and table previews cap very long tables for readability. Export the table result or the
full report for the available result data. Source data remains unchanged.

## Where are my exported files?

TMApp does not move files. Exports go exactly to the paths selected in the save dialogs.

## Can I use this commercially?

The application is licensed under GPL-3.0-or-later. Review the license with your legal advisor.
If you distribute a modified version or an executable, the GPL requires corresponding source
availability and license notices.

## How do I reset the application layout?

Close TMApp and delete or edit its settings. On Windows, settings are stored under the registry
key for organization `TMApp` and application `TMApp`. Delete the geometry and window state values
to restore the default layout.

## How do I report a problem?

Include the exact action, the error dialog text, the Python version, the operating system, and a
small non-confidential sample that reproduces the issue.
