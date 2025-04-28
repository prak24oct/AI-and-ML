# 📊 Advanced Hypothesis Testing Methods

## 1. Confidence Intervals

### Parametric Confidence Intervals

```python
import numpy as np
from scipy import stats

def confidence_interval(sample, confidence=0.95):
    """Calculate confidence interval for mean"""
    n = len(sample)
    mean = np.mean(sample)
    std = np.std(sample, ddof=1)
    se = std / np.sqrt(n)
    t_crit = stats.t.ppf((1 + confidence) / 2, df=n-1)
    margin = t_crit * se
    return mean - margin, mean + margin

# Example
sample = np.random.normal(0, 1, 30)
lower, upper = confidence_interval(sample)
print(f"95% CI: [{lower:.3f}, {upper:.3f}]")
```

### Non-parametric Confidence Intervals

```python
def bootstrap_ci(sample, confidence=0.95, n_bootstrap=1000):
    """Calculate bootstrap confidence interval"""
    means = []
    for _ in range(n_bootstrap):
        resample = np.random.choice(sample, size=len(sample), replace=True)
        means.append(np.mean(resample))
    lower = np.percentile(means, (1-confidence)/2 * 100)
    upper = np.percentile(means, (1+confidence)/2 * 100)
    return lower, upper

# Example
lower, upper = bootstrap_ci(sample)
print(f"Bootstrap 95% CI: [{lower:.3f}, {upper:.3f}]")
```

## 2. Resampling Methods

### Permutation Tests

```python
def permutation_test(sample1, sample2, n_permutations=1000):
    """Perform permutation test"""
    observed_diff = np.mean(sample1) - np.mean(sample2)
    combined = np.concatenate([sample1, sample2])
    perm_diffs = []

    for _ in range(n_permutations):
        perm = np.random.permutation(combined)
        perm1 = perm[:len(sample1)]
        perm2 = perm[len(sample1):]
        perm_diffs.append(np.mean(perm1) - np.mean(perm2))

    p_value = np.mean(np.abs(perm_diffs) >= np.abs(observed_diff))
    return observed_diff, p_value

# Example
sample1 = np.random.normal(0, 1, 20)
sample2 = np.random.normal(0.5, 1, 20)
diff, p = permutation_test(sample1, sample2)
print(f"Observed difference: {diff:.3f}")
print(f"p-value: {p:.3f}")
```

### Jackknife Estimation

```python
def jackknife_estimate(sample, func=np.mean):
    """Calculate jackknife estimate and standard error"""
    n = len(sample)
    estimates = []

    for i in range(n):
        jackknife_sample = np.delete(sample, i)
        estimates.append(func(jackknife_sample))

    estimate = func(sample)
    se = np.sqrt((n-1)/n * np.sum((estimates - np.mean(estimates))**2))
    return estimate, se

# Example
estimate, se = jackknife_estimate(sample)
print(f"Estimate: {estimate:.3f}")
print(f"Standard Error: {se:.3f}")
```

## 3. Advanced Applications

### Survival Analysis

```python
from lifelines import KaplanMeierFitter
import pandas as pd

def survival_analysis(times, events, groups=None):
    """Perform survival analysis"""
    kmf = KaplanMeierFitter()

    if groups is None:
        kmf.fit(times, events)
        return kmf

    results = {}
    for group in np.unique(groups):
        mask = groups == group
        kmf.fit(times[mask], events[mask], label=f'Group {group}')
        results[group] = kmf

    return results

# Example
times = np.random.exponential(10, 100)
events = np.random.binomial(1, 0.8, 100)
groups = np.random.binomial(1, 0.5, 100)
results = survival_analysis(times, events, groups)
```

### Multivariate Testing

```python
from scipy.stats import multivariate_normal

def hotelling_t2(sample1, sample2):
    """Perform Hotelling's T-squared test"""
    n1, n2 = len(sample1), len(sample2)
    mean1, mean2 = np.mean(sample1, axis=0), np.mean(sample2, axis=0)
    cov1 = np.cov(sample1, rowvar=False)
    cov2 = np.cov(sample2, rowvar=False)

    pooled_cov = ((n1-1)*cov1 + (n2-1)*cov2) / (n1 + n2 - 2)
    diff = mean1 - mean2

    t2 = (n1*n2)/(n1+n2) * diff.T @ np.linalg.inv(pooled_cov) @ diff
    f = (n1+n2-p-1)/((n1+n2-2)*p) * t2
    p_value = 1 - stats.f.cdf(f, p, n1+n2-p-1)

    return t2, p_value

# Example
sample1 = multivariate_normal.rvs(mean=[0,0], cov=[[1,0.5],[0.5,1]], size=30)
sample2 = multivariate_normal.rvs(mean=[0.5,0.5], cov=[[1,0.5],[0.5,1]], size=30)
t2, p = hotelling_t2(sample1, sample2)
print(f"T-squared: {t2:.3f}")
print(f"p-value: {p:.3f}")
```

## 4. Best Practices

### Advanced Test Selection

- Consider multivariate nature of data
- Account for dependencies in data
- Choose appropriate resampling method
- Consider computational complexity

### Analysis

- Report confidence intervals
- Include effect sizes
- Consider multiple comparisons
- Document assumptions

### Common Pitfalls

- Ignoring dependencies in data
- Not considering computational costs
- Over-reliance on asymptotic results
- Not validating assumptions

### Reporting Results

- State all assumptions
- Report confidence intervals
- Include effect sizes
- Discuss practical significance
- Address limitations

---

This file covers advanced topics and methods in hypothesis testing. For specific applications, refer to the relevant domain-specific modules.
