# Machine Learning Prediction

## Supervised text classification

Supervised learning requires a label column with at least two classes and at least two examples
per class. Training uses a scikit-learn pipeline that vectorizes text and fits a classifier.

### Classifiers

- Logistic Regression
- Multinomial Naive Bayes
- Complement Naive Bayes
- Linear SVM
- Random Forest

### Settings

- **Features**: TF-IDF or counts. TF-IDF is the usual default.
- **Test-set share**: fraction held out for evaluation.
- **Cross-validation folds**: capped by the smallest class count.

### Outputs

- Accuracy, weighted and macro precision, recall, and F1.
- Cross-validation accuracy per fold, mean, and standard deviation.
- Per-class metrics and confusion matrix.
- Test predictions and predictions for all labeled documents.
- Top model coefficients or feature importances.
- ROC curve and AUC for binary targets.
- Confidence scores when the model exposes probabilities or decision values.

### Predict new text

After training, enter text in the prediction box and press **Predict**. The predicted class and
confidence use the fitted vectorizer and classifier.

### Simulated prediction examples

The prediction box also provides context-aware example text:

- **Random example** generates text from the vocabulary and bigram patterns of the current corpus.
- **Simulated '<class>' example** generates text from documents belonging to that label class.
- Press **Simulate** (or select another example) to fill the prediction box.
- The expected label is shown for class-specific examples so you can compare it with the
  prediction.
- Simulation uses the same text source as training (preprocessed text when available), so the
  generated example matches the model's input representation.
- If a class has too little text, a short excerpt from a real document is used instead.

## Unsupervised document clustering

Clustering does not need labels. Documents are vectorized with TF-IDF, then grouped with K-Means
or DBSCAN.

### Outputs

- Cluster sizes and noise count.
- Silhouette score when at least two clusters are found.
- Cluster assignments.
- Top terms per cluster.
- Bar charts and a two-dimensional projection.

### Method notes

- K-Means requires a chosen cluster count and assumes roughly compact clusters.
- DBSCAN finds density-based clusters and labels sparse points as noise (`-1`).
- Text clusters depend on preprocessing and vocabulary settings. Review top terms before naming
  clusters.

## Evaluation guidance

- Use a held-out test set and cross-validation, not training accuracy.
- Check per-class metrics when classes are imbalanced.
- Linear models provide interpretable top features.
- Random forests can capture non-linear interactions but are less transparent.
- Very small or duplicated datasets produce optimistic scores. Remove duplicates before training.
- Supervised labels must be consistent; label noise limits every model.
