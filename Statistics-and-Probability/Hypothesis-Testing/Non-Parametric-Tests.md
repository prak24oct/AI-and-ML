# 📊 Non-Parametric Hypothesis Tests

## 1. One-Sample Tests

### Sign Test

```python
import numpy as np
from scipy import stats

def sign_test(sample, median=0):
    """Perform sign test"""
    n = len(sample)
    pos = sum(1 for x in sample if x > median)
    neg = sum(1 for x in sample if x < median)
    p_value = stats.binom_test(min(pos, neg), n=pos+neg, p=0.5)
    return p_value

# Example
sample = np.random.normal(0, 1, 20)
p = sign_test(sample)
print(f"p-value: {p:.3f}")
```

### Wilcoxon Signed-Rank Test

```python
def wilcoxon_signed_rank(sample, median=0):
    """Perform Wilcoxon signed-rank test"""
    stat, p_value = stats.wilcoxon(sample - median)
    return stat, p_value

# Example
stat, p = wilcoxon_signed_rank(sample)
print(f"Statistic: {stat:.3f}, p-value: {p:.3f}")
```

## 2. Two-Sample Tests

### Mann-Whitney U Test

```python
def mann_whitney_u(sample1, sample2):
    """Perform Mann-Whitney U test"""
    stat, p_value = stats.mannwhitneyu(sample1, sample2)
    return stat, p_value

# Example
sample1 = np.random.normal(0, 1, 30)
sample2 = np.random.normal(0.5, 1, 30)
stat, p = mann_whitney_u(sample1, sample2)
print(f"U statistic: {stat:.3f}, p-value: {p:.3f}")
```

### Wilcoxon Rank-Sum Test

```python
def wilcoxon_rank_sum(sample1, sample2):
    """Perform Wilcoxon rank-sum test"""
    stat, p_value = stats.ranksums(sample1, sample2)
    return stat, p_value

# Example
stat, p = wilcoxon_rank_sum(sample1, sample2)
print(f"Statistic: {stat:.3f}, p-value: {p:.3f}")
```

## 3. Multiple Sample Tests

### Kruskal-Wallis Test

```python
def kruskal_wallis(*samples):
    """Perform Kruskal-Wallis test"""
    stat, p_value = stats.kruskal(*samples)
    return stat, p_value

# Example
group1 = np.random.normal(0, 1, 30)
group2 = np.random.normal(1, 1, 30)
group3 = np.random.normal(2, 1, 30)
stat, p = kruskal_wallis(group1, group2, group3)
print(f"Statistic: {stat:.3f}, p-value: {p:.3f}")
```

### Friedman Test

```python
def friedman_test(*samples):
    """Perform Friedman test"""
    stat, p_value = stats.friedmanchisquare(*samples)
    return stat, p_value

# Example
stat, p = friedman_test(group1, group2, group3)
print(f"Statistic: {stat:.3f}, p-value: {p:.3f}")
```

## 4. Correlation Tests

### Spearman's Rank Correlation

```python
def spearman_correlation(x, y):
    """Calculate Spearman's rank correlation"""
    stat, p_value = stats.spearmanr(x, y)
    return stat, p_value

# Example
x = np.random.normal(0, 1, 50)
y = x + np.random.normal(0, 0.5, 50)
stat, p = spearman_correlation(x, y)
print(f"Correlation: {stat:.3f}, p-value: {p:.3f}")
```

### Kendall's Tau

```python
def kendall_tau(x, y):
    """Calculate Kendall's tau"""
    stat, p_value = stats.kendalltau(x, y)
    return stat, p_value

# Example
stat, p = kendall_tau(x, y)
print(f"Tau: {stat:.3f}, p-value: {p:.3f}")
```

## 5. Goodness-of-Fit Tests

### Kolmogorov-Smirnov Test

```python
def kolmogorov_smirnov(sample, dist='norm'):
    """Perform Kolmogorov-Smirnov test"""
    if dist == 'norm':
        stat, p_value = stats.kstest(sample, 'norm')
    elif dist == 'expon':
        stat, p_value = stats.kstest(sample, 'expon')
    return stat, p_value

# Example
stat, p = kolmogorov_smirnov(sample)
print(f"Statistic: {stat:.3f}, p-value: {p:.3f}")
```

### Chi-Square Goodness-of-Fit Test

```python
def chi_square_gof(observed, expected):
    """Perform chi-square goodness-of-fit test"""
    stat, p_value = stats.chisquare(observed, expected)
    return stat, p_value

# Example
observed = [10, 20, 30, 40]
expected = [25, 25, 25, 25]
stat, p = chi_square_gof(observed, expected)
print(f"Statistic: {stat:.3f}, p-value: {p:.3f}")
```

## 6. Best Practices

### Test Selection

- Use when parametric assumptions are violated
- Consider sample size and distribution
- Choose appropriate test based on data type
- Consider power of the test

### Analysis

- Report test statistics and p-values
- Include effect sizes when possible
- Consider ties in rank-based tests
- Check for outliers

### Common Pitfalls

- Using parametric tests when assumptions are violated
- Ignoring ties in rank-based tests
- Not considering power of the test
- Misinterpreting results
- Not reporting effect sizes

### Reporting Results

- State hypotheses clearly
- Report test statistics and p-values
- Include effect sizes when possible
- Discuss practical implications
- Address limitations

---

This file covers non-parametric hypothesis tests. For more advanced topics, refer to the next module in this series.
