# Quick Start

## Install

```text
python -m venv .venv
.venv\Scripts\activate        # Windows
source .venv/bin/activate     # Linux / macOS
pip install -r requirements.txt
```

## Run

```text
python main.py
```

Use **File > Load Demo Dataset** to explore every feature without preparing data. The demo has
160 reviews, a sentiment label, a category group, and numeric columns.

## First five minutes

1. Click **Load Demo Dataset**.
2. Open **Preprocessing**, click **Preview (20 docs)**, then **Run Preprocessing**.
3. Open **DTM / TF-IDF** and click **Build Matrix**.
4. Run **Descriptive Statistics > Text corpus**.
5. Run **Sentiment** and inspect the Tables, Figures, and Summary tabs.
6. Open **Machine Learning**, choose the `sentiment` label column, and click **Train Model**.
7. Use **Full Report** in the Results Viewer to export a DOCX or PDF.
8. Fix a typo by double-clicking a cell on the **Data** page, then use **Export Dataset...**
   to save the edited table.

## Command line

```text
python main.py --demo
python main.py --theme dark
```

`--demo` loads the demo dataset at startup. `--theme` overrides the saved light/dark setting.

## Optional NLP data

WordNet and VADER improve lemmatization and sentiment scoring. Install them from
**Help > Download NLP Data** or run:

```text
python scripts/setup_nltk.py
```

TMApp works without this data: lemmatization falls back to stemming and sentiment falls back to
the bundled lexicon.
