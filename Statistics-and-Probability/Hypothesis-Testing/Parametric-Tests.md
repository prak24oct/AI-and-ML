# 📊 Parametric Hypothesis Tests

## 1. One-Sample Tests

### One-Sample Z-Test

```python
import numpy as np
from scipy import stats

def one_sample_z_test(sample, pop_mean, pop_std):
    """Perform one-sample z-test"""
    n = len(sample)
    sample_mean = np.mean(sample)
    z_score = (sample_mean - pop_mean) / (pop_std / np.sqrt(n))
    p_value = 2 * (1 - stats.norm.cdf(abs(z_score)))
    return z_score, p_value

# Example
sample = np.random.normal(100, 15, 50)
z, p = one_sample_z_test(sample, 95, 15)
print(f"Z-score: {z:.3f}, p-value: {p:.3f}")
```

### One-Sample T-Test

```python
def one_sample_t_test(sample, pop_mean):
    """Perform one-sample t-test"""
    t_stat, p_value = stats.ttest_1samp(sample, pop_mean)
    return t_stat, p_value

# Example
sample = np.random.normal(0, 1, 20)
t, p = one_sample_t_test(sample, 0)
print(f"T-score: {t:.3f}, p-value: {p:.3f}")
```

## 2. Two-Sample Tests

### Independent Samples T-Test

```python
def independent_t_test(sample1, sample2, equal_var=True):
    """Perform independent samples t-test"""
    t_stat, p_value = stats.ttest_ind(sample1, sample2, equal_var=equal_var)
    return t_stat, p_value

# Example
sample1 = np.random.normal(0, 1, 30)
sample2 = np.random.normal(0.5, 1, 30)
t, p = independent_t_test(sample1, sample2)
print(f"T-score: {t:.3f}, p-value: {p:.3f}")
```

### Paired Samples T-Test

```python
def paired_t_test(sample1, sample2):
    """Perform paired samples t-test"""
    t_stat, p_value = stats.ttest_rel(sample1, sample2)
    return t_stat, p_value

# Example
before = np.random.normal(100, 15, 20)
after = before + np.random.normal(5, 3, 20)
t, p = paired_t_test(before, after)
print(f"T-score: {t:.3f}, p-value: {p:.3f}")
```

## 3. Analysis of Variance (ANOVA)

### One-Way ANOVA

```python
def one_way_anova(*samples):
    """Perform one-way ANOVA"""
    f_stat, p_value = stats.f_oneway(*samples)
    return f_stat, p_value

# Example
group1 = np.random.normal(0, 1, 30)
group2 = np.random.normal(1, 1, 30)
group3 = np.random.normal(2, 1, 30)
f, p = one_way_anova(group1, group2, group3)
print(f"F-score: {f:.3f}, p-value: {p:.3f}")
```

### Post-hoc Tests (Tukey's HSD)

```python
from statsmodels.stats.multicomp import pairwise_tukeyhsd

def tukey_hsd(*samples):
    """Perform Tukey's HSD test"""
    data = np.concatenate(samples)
    groups = np.concatenate([[f"group{i+1}"] * len(s) for i, s in enumerate(samples)])
    return pairwise_tukeyhsd(data, groups)

# Example
result = tukey_hsd(group1, group2, group3)
print(result)
```

## 4. Assumptions Checking

### Normality Test

```python
def check_normality(sample):
    """Check normality using Shapiro-Wilk test"""
    stat, p = stats.shapiro(sample)
    return stat, p

# Example
stat, p = check_normality(sample1)
print(f"Shapiro-Wilk statistic: {stat:.3f}, p-value: {p:.3f}")
```

### Homogeneity of Variance

```python
def check_homogeneity(*samples):
    """Check homogeneity of variance using Levene's test"""
    stat, p = stats.levene(*samples)
    return stat, p

# Example
stat, p = check_homogeneity(group1, group2, group3)
print(f"Levene's statistic: {stat:.3f}, p-value: {p:.3f}")
```

## 5. Effect Size Measures

### Cohen's d

```python
def cohens_d(sample1, sample2):
    """Calculate Cohen's d effect size"""
    n1, n2 = len(sample1), len(sample2)
    s1, s2 = np.var(sample1, ddof=1), np.var(sample2, ddof=1)
    pooled_std = np.sqrt(((n1-1)*s1 + (n2-1)*s2) / (n1 + n2 - 2))
    d = (np.mean(sample1) - np.mean(sample2)) / pooled_std
    return d

# Example
d = cohens_d(sample1, sample2)
print(f"Cohen's d: {d:.3f}")
```

### Eta Squared

```python
def eta_squared(f_stat, df_between, df_within):
    """Calculate eta squared effect size"""
    return (f_stat * df_between) / (f_stat * df_between + df_within)

# Example
eta2 = eta_squared(f, 2, 87)  # For one-way ANOVA example
print(f"Eta squared: {eta2:.3f}")
```

## 6. Best Practices

### Test Selection

- Check assumptions before choosing test
- Consider sample size and distribution
- Choose appropriate test based on research question
- Consider effect size requirements

### Analysis

- Report all relevant statistics
- Include effect sizes
- Provide confidence intervals
- Consider practical significance

### Common Pitfalls

- Ignoring assumptions
- Multiple comparisons without correction
- Over-reliance on p-values
- Not reporting effect sizes
- Misinterpreting results

### Reporting Results

- State hypotheses clearly
- Report test statistics and p-values
- Include effect sizes and confidence intervals
- Discuss practical implications
- Address assumptions and limitations

---

This file covers parametric hypothesis tests. For non-parametric tests, refer to the next module in this series.
