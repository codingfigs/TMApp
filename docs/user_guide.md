# TMApp User Guide

TMApp is a desktop application for text mining and statistical analysis. It combines text
preprocessing, document-term matrices, bag-of-words and word-vector models, named entity
recognition, descriptive and inferential statistics, topic modeling, sentiment, emotion, and
opinion analysis, and machine learning in one workspace.

## Workspace model

Every action reads from and writes to a single **Workspace**:

1. **Data** holds the imported table, the selected text column, and optional label, group, and
   date columns.
2. **Preprocessing** replaces the active text with cleaned tokens and aligned documents.
3. **DTM / TF-IDF** stores the current sparse text matrix and its vocabulary.
4. Analyses use the preprocessed text when available and fall back to the raw text otherwise.
5. **Results Viewer** collects every table, figure, and summary produced during the session.

Changing the text column, rerunning preprocessing, or editing the text column itself
invalidates the matrix, sentiment frame, and machine-learning state. Results already added to
the viewer are kept until you clear them.

## Recommended workflow

1. **File > Import Data** or **Load Demo Dataset**. For Sentiment, Emotion Detection, or Opinion
   Mining without an external file, use the page's **Simulated dataset** controls to generate a
   labelled corpus for a business context and load it into the workspace.
2. Confirm the text column and optional mappings on the **Data** page.
3. Run **Preprocessing** and inspect the preview and summary.
4. Build a **DTM / TF-IDF** matrix if you plan to use text analyses.
5. Run any combination of analyses from the sidebar.
6. Export a single result, a full report, or the processed text.

## Editing the dataset

The **Data** page edits the loaded dataset in place:

- **Cells**: double-click a cell (or press F2) and type a new value. Values must match the
  column type; whole-number columns automatically widen to decimals when needed, and
  unparsable text converts the column to text.
- **Rows**: **Add Row** appends a row at the end, prefilled with each column's most frequent
  value (median for decimals, blank for the text column) so it lines up with the current
  data, and opens the first cell for typing; press Tab to move across the row. Select rows
  (click row headers or cells) and delete them.
- **Columns**: **Add Column** creates a text, categorical, integer, or decimal column and fills
  it with simulated data (random integers or decimals in a range, random category choices,
  or sequential labels), a constant value, or missing values. Rename a column, or select
  columns (click column headers or cells) and delete them. Column mappings follow renames,
  and deleting the text column automatically picks a replacement.

Editing the text column, adding or deleting rows, or deleting the text column resets
preprocessing and matrix state; editing other columns keeps it. Use **Export Dataset...** on
the Data page or in the **File** menu to save the edited table as CSV or Excel.

## Pages

- **Data**: file import, dataset profile, text/label/group/date mapping, a raw preview, and
  in-place editing (cells, rows, and columns) with dataset export.
- **Preprocessing**: cleaning, stopwords, token length, stemming/lemmatization, n-grams,
  duplicate removal, custom regex rules, preview, run, and export.
- **DTM / TF-IDF**: count or TF-IDF matrix settings, matrix statistics, top terms, dense export,
  and sparse NPZ export.
- **Bag of Words**: term-frequency vocabulary, top terms, coverage, document lengths, and word
  clouds.
- **Word Vectors**: LSA word embeddings with nearest neighbours, a 2D word map, and similarity
  heatmaps.
- **Named Entity Recognition**: people, organisations, locations, dates, money, emails, and URLs
  from the original text, with NLTK or a rule-based fallback.
- **Descriptive Statistics**: corpus statistics, numeric summaries, and matrix summaries.
- **Bivariate Analysis**: correlation matrices, cross-tabulation with chi-square, and group
  comparisons.
- **Regression**: OLS with diagnostics and logistic regression for binary targets.
- **PCA**: numeric variables or a sparse text matrix.
- **Factor Analysis**: exploratory factor analysis with rotations and adequacy tests.
- **Clustering**: K-Means, hierarchical, and DBSCAN on rows or documents.
- **Topic Modeling**: LDA and NMF with topic-term and document-topic tables.
- **Sentiment**: VADER when installed, bundled lexicon fallback, optional group and date columns.
- **Emotion Detection**: dominant emotion per document using a bundled eight-emotion lexicon,
  with optional group comparisons.
- **Opinion Mining**: aspect-opinion pairs, aspect polarity summaries, and opinion charts.
- **Machine Learning**: supervised text classification and unsupervised document clustering,
  plus prediction for new text after training a supervised model. The prediction box can generate
  context-aware simulated examples from the corpus, optionally from a chosen label class.

Each of the Sentiment, Emotion Detection, and Opinion Mining pages also includes simulated-dataset
controls: choose a business context such as Marketing, Finance, IT & Operations, HRM, or
International Business, generate a labelled corpus, and load it into the workspace (optionally
running the page's analysis immediately). Each corpus has a text column, sentiment and emotion
targets, a context-specific group column, dates, satisfaction, and response-time metrics.

## Results Viewer

- **History** keeps every result bundle from the session.
- **Tables** displays the selected table. Long tables are previewed; exports contain the result
  object data available to the viewer.
- **Figures** renders matplotlib figures with pan, zoom, and save controls.
- **Summary** shows the analysis parameters, notes, and warnings.
- **Export Table** writes CSV or Excel. **Export Figure** writes PNG. **Export Report** writes
  DOCX or PDF for the current result. **Full Report** combines all session results.

## Menus

- **File**: import, demo data, dataset export, processed-text export, sparse matrix export,
  report export, clear session, and exit.
- **Analysis**: jump to any analysis page (shortcuts Ctrl+1 through Ctrl+9 for the first nine).
- **View**: toggle the Results Viewer and switch between light and dark themes.
- **Docs**: open any guide in the built-in markdown viewer.
- **Help**: download optional NLTK data, check dependencies, open licenses, and view About.

## Data privacy

TMApp runs locally. It does not upload your data. The only network operation is the optional
NLTK download initiated from **Help > Download NLP Data**. Reports and exports are written only
to the paths you choose.
