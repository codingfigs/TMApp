# DTM and TF-IDF Guide

The **DTM / TF-IDF** page converts documents into a numeric matrix. Rows are documents and
columns are terms.

## Count matrix (DTM)

A count matrix stores how often each term occurs in each document. It is appropriate for LDA
topic modeling and raw term-frequency summaries. Enable **Binary features** to store presence or
absence instead of counts.

## TF-IDF

TF-IDF weights terms by term frequency and inverse document frequency. Common terms receive less
weight, making distinctive terms more prominent. It is a strong default for clustering, PCA, and
linear classifiers.

**Sublinear TF scaling** uses `1 + log(tf)` instead of raw term frequency, which reduces the
influence of repeated words. It is enabled by default for TF-IDF.

## Settings

- **N-gram range**: minimum and maximum n-gram length. Use 1-1 for unigrams, 1-2 for unigrams and
  bigrams.
- **Min document frequency**: a term must appear in at least this many documents. Raising it
  reduces vocabulary and noise.
- **Max document frequency (share)**: terms appearing in a larger share of documents are removed.
  Values near 1 keep almost everything.
- **Max features**: keeps the highest-scoring terms. Use 0 for no limit, but very large
  vocabularies slow later analyses.

## Matrix outputs

- **Matrix statistics**: documents, terms, non-zero cells, sparsity, total weight, and average
  term counts.
- **Top terms by weight**: the highest-weight vocabulary.
- **Matrix preview**: a dense view of the first documents and the 40 highest-weight terms.
- **Document lengths**: unique terms and row weight per document.
- **Top terms** and **row weight** figures.

## Exports

**Export Dense Matrix** writes a capped dense table to CSV or Excel. The default cap is 5,000
documents and 1,000 terms, ordered by term weight. **Save Sparse NPZ** writes the full SciPy
sparse matrix for use in Python.

## Reuse by other analyses

The built matrix is reused by:

- Descriptive matrix statistics.
- PCA on the text matrix (via Truncated SVD).
- Cluster analysis on documents.
- Topic modeling and sentiment remain available from text directly.

Rebuilding the matrix replaces the previous one. Rerunning preprocessing invalidates it.
