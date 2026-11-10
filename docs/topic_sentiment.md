# Topic Modeling and Sentiment

## Topic modeling

TMApp offers two methods:

- **LDA (Latent Dirichlet Allocation)** models documents as mixtures of topics over term counts.
- **NMF (Non-negative Matrix Factorization)** factorizes a TF-IDF matrix into topics and
  document weights.

### Settings

- **Topics**: number of topics to extract. NMF is capped so it does not exceed the number of
  documents or terms.
- **Terms per topic**: how many top terms to display.
- **Max vocabulary**: maximum number of terms retained.
- **Min document frequency**: terms must appear in at least this many documents.
- **Max document frequency (share)**: removes terms that are too common.

Preprocessed text is strongly recommended. Raw text produces noisy topics because of casing,
punctuation, and stopwords.

### Outputs

- Topic-term weights and ranked terms per topic.
- Document-topic distributions.
- Dominant topic per document.
- Representative documents (highest weight) per topic.
- Coherence and model metrics.
- Topic bar charts and a heatmap.

Topic numbers are arbitrary labels. Interpret each topic from its highest-weight terms and
example documents.

## Sentiment analysis

Each document receives negative, neutral, and positive scores, a compound score, and a label
using thresholds of +0.05 and -0.05.

### Analyzers

- **Auto (VADER if available)** uses NLTK VADER when its data is installed.
- **VADER** forces VADER or reports that it is unavailable.
- **Bundled lexicon** uses the packaged sentiment lexicon with simple negation and intensifier
  handling.

### Outputs

- Document-level scores and labels.
- Sentiment counts and percentages.
- Mean, median, standard deviation, and compound distribution.
- The most positive and most negative documents.
- Top positive and negative terms.
- Group summaries when a group column is mapped.
- Sentiment trends over time when a date column is mapped.

### Limitations

Lexicon methods miss sarcasm, domain-specific polarity, and complex negation. VADER is tuned for
social-media text. Validate results on a labeled sample before drawing conclusions.

## Emotion detection

Each document is scored against a bundled emotion lexicon covering joy, trust, fear, surprise,
sadness, disgust, anger, and anticipation. Outputs include the dominant emotion per document,
emotion word counts, positive and negative intensity, document-level scores, mean emotion scores,
optional group summaries, and charts (dominant emotions, intensities, document profiles).

Negation is handled with a simple window, but sarcasm and mixed emotions are only partly
captured. Use emotion detection together with sentiment and opinion mining rather than in
isolation.

## Opinion mining

Opinion mining links sentiment-bearing words to nearby aspects. Aspect candidates come from
part-of-speech noun tags when available, otherwise from a frequency heuristic; consecutive nouns
are joined (for example, "battery life"). Outputs include aspect summaries with positive,
negative, and neutral counts and mean scores, aspect-opinion pairs, polarity distribution,
document-level summaries, and charts (aspect mentions, aspect sentiment, polarity).

A wider context window captures more distant opinions but can attach an opinion to the wrong
aspect. Inspect the aspect-opinion table before interpreting the summary.

## Combining methods

A useful sequence is:

1. Preprocess and inspect corpus statistics.
2. Build a TF-IDF matrix.
3. Cluster documents to find broad groups.
4. Run topic modeling to describe themes.
5. Score sentiment within topics or groups.
6. Train a supervised classifier if labeled examples exist.

## Simulated corpora

The Sentiment, Emotion Detection, and Opinion Mining pages can generate labelled simulated
corpora without an external file. Choose a business context such as:

- Marketing
- Finance
- IT & Operations
- HRM
- International Business
- Healthcare
- Education
- Hospitality & Travel
- Retail & E-commerce
- Public Sector
- Manufacturing & Supply Chain
- Telecom & Media

Each generated corpus contains sentiment and emotion targets, a context-specific group column,
dates, satisfaction, and response-time metrics. Use **Load Dataset** to replace the workspace
dataset, or **Load & Analyze** to run the current page immediately.
