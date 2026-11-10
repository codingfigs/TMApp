# TMApp

**TMApp** is an open-source desktop application for text mining and statistical analysis. It
combines data import, text preprocessing, term-document modelling, named entity recognition,
descriptive and inferential statistics, topic modelling, sentiment, emotion, and opinion analysis,
and machine learning in one PyQt6 workspace.

| | |
|---|---|
| **Version** | 1.0.0 |
| **Developer** | Dr. M. Kamakshaiah (`dr.m.kamakshaiah@gmail.com`) |
| **License** | GNU General Public License v3.0 or later (`GPL-3.0-or-later`) |
| **Platform** | Windows and Linux (source) |
| **Python** | 3.11 - 3.13 |

## Highlights

- Import CSV, TSV, delimited text, and Excel workbooks, then map the text, label, group, and date
  columns.
- Edit the loaded dataset in place: cells, rows, and columns.
- Clean and tokenize text with a configurable preprocessing pipeline.
- Build count (DTM) and TF-IDF matrices, bag-of-words models, and LSA word vectors.
- Extract named entities, sentiments, emotions, and aspect-based opinions.
- Run descriptive statistics, correlations, group comparisons, regression, PCA, factor analysis,
  clustering, and topic modelling.
- Train supervised text classifiers and cluster documents without labels.
- Generate context-aware simulated prediction examples from the current corpus.
- Generate context-specific simulated corpora for sentiment, emotion, and opinion analysis,
  covering marketing, finance, IT & operations, HRM, international business, healthcare,
  education, hospitality, retail, public sector, manufacturing, and telecom.
- Explore results in a dockable viewer and export tables, figures, processed text, and full
  DOCX/PDF reports.
- Use light and dark themes, an in-app documentation viewer, dependency checks, and optional NLTK
  downloads.

## Installation

### Requirements

- Python 3.11 or newer
- Windows or Linux with a desktop session
- Dependencies pinned in [`requirements.txt`](requirements.txt): PyQt6, numpy, pandas, scipy,
  scikit-learn, statsmodels, factor_analyzer, joblib, matplotlib, seaborn, nltk, wordcloud,
  openpyxl, XlsxWriter, python-docx, reportlab

### Setup

```text
python -m venv .venv
.venv\Scripts\activate        # Windows
source .venv/bin/activate     # Linux
python -m pip install --upgrade pip
pip install -r requirements.txt
python main.py
```

Optional launch flags:

```text
python main.py --demo
python main.py --theme dark
```

Download optional NLTK data from **Help > Download NLP Data**, or run:

```text
python scripts/setup_nltk.py
```

TMApp works without NLTK data:

- Lemmatization falls back to stemming.
- Sentiment falls back to the bundled lexicon.
- Named entity recognition falls back to a rule-based extractor.

## Quick start

1. Choose **File > Import Data** or **Load Demo Dataset**.
2. Confirm the text column and optional label, group, and date mappings on the **Data** page.
3. Run **Preprocessing** and inspect the preview and summary.
4. Build a **DTM / TF-IDF** matrix if you plan to use matrix-based analyses.
5. Run any combination of analyses from the sidebar or the **Analysis** menu.
6. Inspect results in the **Results Viewer** and export a table, figure, or report.

The demo dataset contains review text, ratings, sentiment labels, categories, regions, prices, and
satisfaction scores, so every page can be tried immediately.

## Workspace model

Every action reads from and writes to a single workspace:

1. **Data** holds the imported table and the selected text, label, group, and date columns.
2. **Preprocessing** replaces the active text with cleaned tokens and aligned documents.
3. **DTM / TF-IDF** stores the current sparse text matrix and vocabulary.
4. Analyses use preprocessed text when available and fall back to raw text otherwise.
5. **Named Entity Recognition** uses the original (not lowercased) text when available.
6. **Results Viewer** collects every table, figure, and summary produced during the session.

Changing the text column, rerunning preprocessing, or editing the text column itself invalidates
the matrix and dependent derived state. Results already added to the viewer remain until cleared.

## Analysis pages

### Data

Import files, inspect the dataset profile, map text/label/group/date columns, preview the raw
table, edit cells, add or delete rows and columns, and export the dataset as CSV or Excel.

### Preprocessing

Case folding, HTML/URL/email/number/punctuation cleaning, stopwords, token-length filters,
stemming, optional WordNet lemmatization, n-grams, duplicate and empty removal, custom regular
expression rules, preview, summary, and processed-text export.

### DTM / TF-IDF

Build a count document-term matrix or a TF-IDF matrix with configurable n-grams, document
frequency limits, vocabulary size, binary features, and sublinear TF scaling. Inspect matrix
statistics, top terms, previews, and document lengths; export dense tables or sparse NPZ files.

### Bag of Words

Build a term-frequency model and review vocabulary size, top terms with shares, the term-frequency
distribution, cumulative vocabulary coverage, document lengths, a document-term preview, and
word clouds.

### Word Vectors (LSA)

Represent words as dense vectors using TF-IDF followed by truncated singular value decomposition.
Inspect nearest neighbouring words, leading vector dimensions, seed-term similarity, a
two-dimensional word map, and explained variance. Seed terms can be entered manually; unknown
terms are reported.

### Named Entity Recognition

Extract people, organisations, locations, dates, times, money, percentages, email addresses, and
URLs. NLTK models are used when installed; otherwise a rule-based extractor handles capitalised
names, gazetteer places and organisations, and regular-expression entities. Results include entity
type summaries, frequencies, mention contexts, document summaries, and charts.

### Descriptive Statistics

Corpus statistics, numeric summaries, and matrix summaries, including distributions, readability
estimates, top terms, word clouds, and document-length figures.

### Bivariate Analysis

Correlation matrices (Pearson, Spearman, Kendall), cross-tabulation with chi-square and Cramer's V,
and group comparisons with t-tests, ANOVA, Mann-Whitney U, Kruskal-Wallis, effect sizes, and
boxplots.

### Regression

OLS regression with coefficients, standardised coefficients, diagnostics, VIF, influence
measures, predictions, and residual/Q-Q plots. Logistic regression with odds ratios, threshold
performance, ROC/AUC, and predicted probabilities.

### PCA

Reduce numeric variables or a sparse text matrix. Results include explained variance, loadings,
squared loadings, variable contributions, scores, scree plots, and score plots.

### Factor Analysis

Exploratory factor analysis with minres, maximum likelihood, or principal extraction and varimax,
promax, oblimin, quartimax, equamax, or no rotation. Includes KMO, Bartlett's test, loadings,
communalities, uniquenesses, variance explained, residual correlations, and factor scores.

### Clustering

K-Means, hierarchical clustering, and DBSCAN on numeric columns or documents. Includes cluster
sizes, silhouette statistics, assignments, top terms for text clusters, elbow plots, dendrograms,
and scatter projections.

### Topic Modeling

LDA and NMF with topic-term weights, document-topic distributions, dominant topics, representative
documents, coherence metrics, topic bar charts, and heatmaps.

### Sentiment

Score each document with VADER when installed, or with the bundled lexicon fallback. Includes
negative/neutral/positive scores, compound scores, labels, extreme documents, top terms, optional
group summaries, and date trends.

### Emotion Detection

Assign each document a dominant emotion from a bundled eight-emotion lexicon: joy, trust, fear,
surprise, sadness, disgust, anger, and anticipation. Includes emotion word counts, intensities,
document-level scores, optional group comparisons, and charts.

### Opinion Mining

Link sentiment-bearing opinion words to nearby aspects. Aspect candidates come from
part-of-speech noun tags when available, otherwise from a frequency heuristic. Includes aspect
summaries, aspect-opinion pairs, polarity distribution, document summaries, and charts.

### Simulated corpora

The Sentiment, Emotion Detection, and Opinion Mining pages include simulated-dataset controls:

- Choose a business context (for example, Marketing, Finance, IT & Operations, HRM, or
  International Business).
- Choose the number of documents.
- Press **Load Dataset** to replace the current workspace dataset with a synthetic corpus, or
  **Load & Analyze** to run the page's analysis immediately.
- Each corpus contains labelled text, sentiment and emotion targets, a context-specific group
  column, dates, satisfaction, and response-time metrics, so every NLP page can be exercised
  without importing an external file.

### Machine Learning

Train supervised classifiers (logistic regression, multinomial and complement naive Bayes, linear
SVM, random forest) on a mapped label column, or cluster documents with K-Means or DBSCAN.
Prediction outputs include per-class probabilities and confidence.

The prediction box includes a **Simulated example** selector:

- Choose a **Random example** or a specific label class.
- Press **Simulate** to generate a short text from a bigram model trained on the current corpus.
- The example follows the vocabulary and style of the loaded dataset and the selected class.
- Press **Predict** to classify the generated text with the trained model.

## Results and exports

- **History** keeps every result bundle from the session.
- **Tables** displays the selected table; long tables are previewed for safety.
- **Figures** renders matplotlib figures with pan, zoom, and save controls.
- **Summary** shows analysis parameters, notes, and warnings.
- **Export Table**: CSV or Excel for the selected table.
- **Export Figure**: PNG for the selected figure.
- **Export Report**: DOCX or PDF for the current result.
- **Full Report**: DOCX or PDF combining all session results. Exports run in the background with
  progress in the status bar.
- **Export Processed Text**: CSV, XLSX, DOCX, or PDF.
- **Save Sparse Matrix**: NPZ for the full SciPy sparse matrix.

Reports include dataset context, parameters, notes, tables, figures, and a license footer.

## Menus

- **File**: import, demo data, dataset export, processed-text export, sparse matrix export,
  report export, clear session, and exit.
- **Analysis**: jump to any analysis page (Ctrl+1 through Ctrl+9 for the first nine).
- **View**: toggle the Results Viewer and switch between light and dark themes.
- **Docs**: open any guide in the built-in markdown viewer.
- **Help**: download optional NLTK data, check dependencies, open licenses, and view About.

## Documentation

| Guide | Description |
|---|---|
| [Quick start](docs/quick_start.md) | Short walkthrough of the main workflow |
| [User guide](docs/user_guide.md) | Workspace model, pages, menus, and editing |
| [Data format](docs/data_format.md) | Supported files and column conventions |
| [Preprocessing](docs/preprocessing.md) | Cleaning, tokenisation, and options |
| [DTM / TF-IDF](docs/dtm.md) | Matrix construction and interpretation |
| [Analysis](docs/analysis.md) | Statistics, BoW, word vectors, NER, PCA, EFA, clustering |
| [Topic and sentiment](docs/topic_sentiment.md) | Topic models, sentiment, emotion, and opinion |
| [Machine learning](docs/ml.md) | Supervised and unsupervised text modelling |
| [FAQ](docs/faq.md) | Common questions and troubleshooting |
| [Shortcuts](docs/shortcuts.md) | Keyboard shortcuts |

## Project structure

```text
TMApp/
  main.py                     Application entry point
  app/
    config.py                 Metadata, paths, About text
    data/                     Loaders, demo data, workspace state
    nlp/                      Resources, preprocessing, vectorization, simulation
    analysis/                 Statistics, plots, BoW, word vectors, NER, opinion, emotion
    reporting/                CSV/XLSX/PNG, DOCX/PDF reporting
    ui/                       Theme, workers, panels, dialogs, main window
    resources/                Bundled sentiment and emotion lexicons
  docs/                       Markdown documentation
  packaging/                  PyInstaller spec and build scripts
  scripts/                    NLTK setup and dependency checks
  tests/                      pytest suite
```

## Development

Install development dependencies:

```text
pip install -r requirements-dev.txt
```

Run the test suite:

```text
python -m pytest -q
```

Check installed dependencies and optional NLTK data:

```text
python scripts/check_dependencies.py
```

## Packaging

Build a distributable application with PyInstaller:

```text
python -m PyInstaller packaging/tmapp.spec
```

Windows helper:

```powershell
powershell -ExecutionPolicy Bypass -File packaging/build_windows.ps1
```

Linux helper:

```text
bash packaging/build_linux.sh
```

The output is `dist/TMApp/`. Documentation, the bundled lexicons, and license files are included.
NLTK corpora are not bundled because they are optional and separately licensed; users can download
them from the Help menu.

## Data privacy

TMApp runs locally and does not upload your data. The only network operation is the optional NLTK
download initiated from **Help > Download NLP Data**. Reports and exports are written only to the
paths you choose.

## Limitations

- Lexicon sentiment, emotion, and opinion methods miss sarcasm and complex domain-specific
  polarity.
- NER quality depends on capitalisation and on whether optional NLTK models are installed.
- LSA word vectors capture co-occurrence patterns, not the full semantics of neural embeddings.
- Very large corpora increase memory use in descriptive reports and dense matrix previews.

## License

TMApp is free software distributed under the **GNU General Public License v3.0 or later**. See
[`LICENSE`](LICENSE) for the full text and [`THIRD_PARTY_LICENSES.md`](THIRD_PARTY_LICENSES.md)
for third-party notices.

Because TMApp uses PyQt6 under the GPL, distributed binaries must comply with the GPL, including
making the corresponding source available and preserving license notices.

## Author

**Dr. M. Kamakshaiah**  
Email: `dr.m.kamakshaiah@gmail.com`
