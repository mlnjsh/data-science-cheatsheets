# Machine Learning Cheatsheet

## Algorithm Selection

| Problem | Try First | Then Try |
|---------|-----------|----------|
| Binary classification | Logistic Regression | Random Forest, XGBoost, SVM |
| Multi-class classification | Random Forest | XGBoost, Neural Network |
| Regression | Linear Regression | Random Forest, XGBoost, Ridge |
| Clustering | K-Means | DBSCAN, Hierarchical |
| Dimensionality reduction | PCA | t-SNE (viz), UMAP (viz) |
| Anomaly detection | Isolation Forest | One-class SVM, LOF |
| Time series | ARIMA | Prophet, LSTM |
| Text classification | TF-IDF + Logistic Reg | BERT, Fine-tuned LLM |

## Metrics

### Classification

| Metric | Formula | When to use |
|--------|---------|-------------|
| Accuracy | (TP+TN) / Total | Balanced classes |
| Precision | TP / (TP+FP) | Cost of false positives is high |
| Recall | TP / (TP+FN) | Cost of false negatives is high |
| F1 Score | 2 * P*R / (P+R) | Imbalanced classes |
| AUC-ROC | Area under ROC curve | Ranking quality |
| Log Loss | -mean(y*log(p)) | Probability calibration |

### Regression

| Metric | When to use |
|--------|-------------|
| MSE | Penalize large errors |
| RMSE | Same unit as target |
| MAE | Robust to outliers |
| R-squared | Proportion of variance explained |
| MAPE | Percentage error |

## Bias-Variance Tradeoff

```
High Bias (Underfitting)          High Variance (Overfitting)
- Training error: HIGH            - Training error: LOW
- Test error: HIGH                - Test error: HIGH
- Model too simple                - Model too complex
- Fix: more features,             - Fix: more data, regularization,
  complex model                     simpler model, dropout
```

## Cross-Validation

```python
from sklearn.model_selection import cross_val_score, StratifiedKFold

# K-Fold (default)
scores = cross_val_score(model, X, y, cv=5, scoring="accuracy")

# Stratified K-Fold (for imbalanced data)
skf = StratifiedKFold(n_splits=5, shuffle=True, random_state=42)
scores = cross_val_score(model, X, y, cv=skf)
```

## Regularization

| Type | Effect | Use when |
|------|--------|----------|
| L1 (Lasso) | Drives weights to zero (feature selection) | Many irrelevant features |
| L2 (Ridge) | Shrinks weights (no zeros) | All features somewhat useful |
| Elastic Net | L1 + L2 combined | Best of both |
| Dropout | Randomly zero neurons during training | Neural networks |
| Early stopping | Stop training when val loss increases | Any iterative model |

## Feature Engineering Tips

- **Scaling**: StandardScaler (zero mean, unit var) or MinMaxScaler (0 to 1)
- **Encoding**: One-hot for nominal, ordinal encoding for ordered categories
- **Missing values**: Median imputation (robust), model-based imputation
- **Interactions**: Multiply features together (e.g., age * income)
- **Polynomials**: Add x^2, x^3 for non-linear relationships
- **Log transform**: For skewed features (income, prices)
- **Binning**: Convert continuous to categorical (age groups)
