# Preprocessing Reference

Preprocessing converts raw documents into normalized text and token lists. The results replace
the raw text for later analyses until you change the text column or rerun the pipeline.

## Cleaning tasks

- **Lowercase** reduces case variants.
- **Remove HTML tags** strips markup such as `<p>` and `<br>`.
- **Remove URLs** removes `http`, `https`, and `www` addresses.
- **Remove emails** removes address-like tokens.
- **Remove @mentions / #hashtags** removes social-media markers and their attached text.
- **Remove numbers** deletes digit runs.
- **Remove punctuation** deletes punctuation characters.
- **Remove special characters** removes non-alphanumeric symbols left after cleaning.
- **Normalize whitespace** collapses repeated spaces and trims edges.

## Tokenization and vocabulary

- **Remove English stopwords** uses the bundled scikit-learn English list. Custom stopwords are
  added as a comma-separated list.
- **Min token length** drops short tokens. The default of 2 removes single letters.
- **Max token length** of 0 means no limit.
- **Stemming** applies Snowball English stemming, which reduces words to stems that may not be
  dictionary words.
- **Lemmatization** uses WordNet when installed and falls back to stemming with a warning.
- **N-gram max** controls the largest n-gram. Choosing 2 or 3 adds bigrams or trigrams to the
  token stream. N-grams improve topic labels but increase vocabulary size.

## Document handling

- **Drop duplicate documents** compares processed text and keeps the first occurrence.
- **Drop documents that become empty** removes rows with no remaining tokens.
- **Custom regex** runs before tokenization. Use Python regular-expression syntax. The
  replacement can be empty to delete matches.

## Preview versus run

**Preview (20 docs)** processes only the first 20 non-empty documents and shows original,
processed, token, and token-count columns. **Run Preprocessing** processes the full corpus in a
background worker with progress.

## Warnings

Warnings are shown under the preview and stored in the result bundle. Common warnings:

- WordNet is unavailable; lemmatization fell back to stemming.
- The custom regex is invalid.
- All documents became empty under the selected rules.

## Practical defaults

The defaults are suitable for reviews and survey text: lowercase, HTML/URL/email/number
removal, punctuation and special-character removal, whitespace normalization, stopword removal,
minimum token length 2, no stemming, no lemmatization, unigrams, duplicate and empty removal.

For search-like bag-of-words models, keep unigrams. For topic labels, try bigrams with a larger
minimum document frequency in the DTM step.
