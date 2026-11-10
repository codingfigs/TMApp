# Descriptive and Inferential Analysis

## Descriptive Statistics

### Text corpus

Reports documents, total tokens, vocabulary size, type-token ratio, hapax counts, token and
character distributions, sentence statistics, readability estimates, top terms, word clouds, and
document-length figures. Parsed tokens from preprocessing are used when available.

### Numeric columns

Select one or more numeric columns to obtain count, sum, mean, standard error, standard
deviation, coefficient of variation, minimum, quartiles, median, maximum, range, interquartile
range, skewness, kurtosis, missing values, histograms, and boxplots.

### DTM / TF-IDF matrix

Summarizes matrix dimensions, sparsity, non-zero cells, top weighted terms, document term counts,
and row weights. Build a matrix first.

## Bag of Words

Builds a term-frequency representation of the corpus with configurable n-grams, document
frequency limits, vocabulary size, and binary presence/absence features. Results include
vocabulary size, total and average term counts, top terms with shares, the term-frequency
distribution, cumulative vocabulary coverage, document lengths, a document-term preview, and
charts (top terms, frequency distribution, coverage, word cloud).

## Word Vectors (LSA)

Represents words as dense vectors using TF-IDF followed by truncated singular value
decomposition. Results include the model summary, leading vector dimensions, nearest neighbouring
words by cosine similarity, seed-term similarity matrices, a two-dimensional PCA word map, and an
explained-variance chart. Seed terms can be entered manually; unknown terms are reported in the
notes.

## Named Entity Recognition

Extracts people, organisations, locations, dates, times, money, percentages, email addresses, and
URLs. NLTK's part-of-speech tagger and named-entity chunker are used when their optional data is
installed; otherwise a rule-based extractor handles capitalised names, gazetteer places and
organisations, and regular-expression entities. Results include entity type summaries, entity
frequencies, mention contexts, document-level entity summaries, and charts. Original text is used
when preprocessing is available because lowercasing hides names and places.

## Bivariate Analysis

### Correlation matrix

Select at least two numeric variables and Pearson, Spearman, or Kendall correlation. The result
includes the correlation matrix, pairwise p-values, 95% confidence intervals (Pearson and
Spearman), significance flags, strength ratings, and a heatmap. Pairwise deletion is used, so each
coefficient uses available pairs.

### Cross-tabulation

Select two categorical variables. The result includes observed counts, row and column
percentages, expected counts, standardized residuals, chi-square, degrees of freedom, p-value,
Cramer's V, and a minimum-expected-count warning. At least two categories are required per
variable.

### Group comparison

Compare a numeric measure across a group variable. The result includes group summaries with
standard errors and 95% confidence intervals, Levene's test for equal variances, an
independent-samples t-test and Mann-Whitney U test for two groups, or one-way ANOVA and
Kruskal-Wallis for more than two groups plus Tukey HSD post-hoc pairwise comparisons, effect
sizes, and boxplots.

## Regression

### OLS linear regression

Enter a numeric target and numeric predictors. The result includes coefficients, standardized
coefficients (beta), standard errors, t statistics, p-values, confidence intervals, R-squared,
adjusted R-squared, F test, AIC, BIC, Durbin-Watson, Jarque-Bera, residual diagnostics, VIF,
ANOVA, influence diagnostics (Cook's distance, leverage, studentized residuals for the top 20
observations), a predictions table, coefficient plots, residual plots, and Q-Q plots.

### Logistic regression

Use a binary target. The result includes coefficients, z statistics, odds ratios, confidence
intervals, accuracy, precision, recall, F1, pseudo R-squared, log-likelihood, AIC, BIC, confusion
matrix, per-class metrics, performance across probability thresholds, ROC/AUC, coefficient plots,
and predicted probabilities. Perfect separation or constant predictors produce an explanatory
error.

## PCA

Reduce numeric variables or a text matrix. Numeric PCA standardizes variables by default. Sparse
text matrices use Truncated SVD. Results include explained variance, cumulative variance,
loadings, squared loadings (cos2), variable contributions to each component, variable
representation, component scores, scree and variance figures, and score plots.

## Factor Analysis

Exploratory factor analysis supports minres, maximum likelihood, and principal extraction with
varimax, promax, oblimin, quartimax, equamax, or no rotation. Results include KMO (overall and
per-variable), Bartlett's test, the correlation matrix and its determinant, the model chi-square
sufficiency test, RMSR, pattern loadings with communalities and uniquenesses, unrotated loadings,
the structure matrix and factor correlations for oblique rotations, total variance explained
(SS loadings and percentages), the residual correlation matrix, eigenvalues, scree plots,
communality and uniqueness figures, loadings heatmaps, and factor scores.

## Cluster Analysis

Choose numeric columns or the text matrix, then K-Means, hierarchical clustering, or DBSCAN.
Results include cluster sizes, silhouette score and per-cluster silhouette statistics where
available, within-cluster dispersion and cluster means (K-Means on numeric data), the cophenetic
correlation (hierarchical), assignments, top terms for text clusters, elbow plots, dendrograms,
silhouette plots, and scatter projections.

## Interpreting results

- Statistical significance is not effect size. Report both.
- Correlation does not imply causation.
- Check missing-data patterns before interpreting regression or factor analysis.
- Text analyses depend heavily on preprocessing and matrix settings. Compare alternatives.
- Cluster labels are arbitrary; describe clusters by their top terms or group profiles.
