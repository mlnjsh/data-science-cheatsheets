# Statistics Cheatsheet

## Descriptive Statistics

| Measure | What it tells you |
|---------|-------------------|
| Mean | Central tendency (sensitive to outliers) |
| Median | Central tendency (robust to outliers) |
| Mode | Most frequent value |
| Std Dev | Average distance from mean |
| Variance | Std dev squared |
| IQR | Q3 - Q1, spread of middle 50% |
| Skewness | Asymmetry (0 = symmetric) |
| Kurtosis | Tail heaviness (3 = normal) |

## Common Distributions

| Distribution | Parameters | Use Case |
|-------------|------------|----------|
| Normal | mu, sigma | Heights, errors, natural phenomena |
| Bernoulli | p | Single yes/no trial |
| Binomial | n, p | Number of successes in n trials |
| Poisson | lambda | Count of rare events |
| Exponential | lambda | Time between events |
| Uniform | a, b | Equal probability in range |
| Beta | alpha, beta | Probabilities (Bayesian prior) |

## Hypothesis Testing

| Test | When to use |
|------|-------------|
| t-test (1 sample) | Compare sample mean to known value |
| t-test (2 sample) | Compare means of two groups |
| Paired t-test | Before/after measurements |
| Chi-square | Categorical variable independence |
| ANOVA | Compare means of 3+ groups |
| Mann-Whitney U | Non-parametric alternative to t-test |
| Wilcoxon | Non-parametric paired test |

## Key Concepts

- **p-value**: Probability of seeing data this extreme if null hypothesis is true
- **Significance level (alpha)**: Threshold for rejecting null (usually 0.05)
- **Type I error**: False positive (reject true null)
- **Type II error**: False negative (fail to reject false null)
- **Power**: 1 - P(Type II error), probability of detecting real effect
- **Effect size**: Magnitude of difference (Cohen's d, R-squared)

## Confidence Intervals

```
95% CI = mean +/- 1.96 * (std / sqrt(n))
99% CI = mean +/- 2.576 * (std / sqrt(n))
```

Interpretation: If we repeated the experiment many times, 95% of the intervals would contain the true parameter.

## Correlation

| Type | When to use | Range |
|------|-------------|-------|
| Pearson | Linear relationship, continuous | [-1, 1] |
| Spearman | Monotonic relationship, ordinal | [-1, 1] |
| Kendall | Small samples, ordinal | [-1, 1] |

**Correlation does not imply causation!**
