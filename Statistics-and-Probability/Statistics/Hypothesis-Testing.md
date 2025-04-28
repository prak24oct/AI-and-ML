# 📊 Hypothesis Testing

## 1. Introduction to Hypothesis Testing

### Key Concepts

- Null Hypothesis (H₀) vs Alternative Hypothesis (H₁)
- Type I and Type II Errors
- Significance Level (α) and Power (1-β)
- p-values and Critical Values
- One-tailed vs Two-tailed Tests

### Test Selection Framework

```python
import numpy as np
from scipy import stats

def select_test(data_type, sample_size, distribution, comparison_type):
    """
    Framework for selecting appropriate hypothesis test
    """
    if data_type == 'continuous':
        if distribution == 'normal':
            if sample_size < 30:
                return 't-test'
            else:
                return 'z-test'
        else:
            return 'non-parametric test'
    elif data_type == 'categorical':
        return 'chi-square test'
```

## 2. Parametric Tests

### One-Sample Tests

```python
# One-Sample t-test
sample = np.random.normal(0, 1, 30)
t_stat, p_value = stats.ttest_1samp(sample, 0)
print(f"t-statistic: {t_stat:.3f}, p-value: {p_value:.3f}")

# One-Sample z-test
def z_test(sample, pop_mean, pop_std):
    z_stat = (np.mean(sample) - pop_mean) / (pop_std / np.sqrt(len(sample)))
    p_value = 2 * (1 - stats.norm.cdf(abs(z_stat)))
    return z_stat, p_value
```

### Two-Sample Tests

```python
# Independent t-test
sample1 = np.random.normal(0, 1, 30)
sample2 = np.random.normal(1, 1, 30)
t_stat, p_value = stats.ttest_ind(sample1, sample2)
print(f"Independent t-test: t={t_stat:.3f}, p={p_value:.3f}")

# Paired t-test
t_stat, p_value = stats.ttest_rel(sample1, sample2)
print(f"Paired t-test: t={t_stat:.3f}, p={p_value:.3f}")
```

### Analysis of Variance (ANOVA)

```python
# One-Way ANOVA
group1 = np.random.normal(0, 1, 30)
group2 = np.random.normal(1, 1, 30)
group3 = np.random.normal(2, 1, 30)

f_stat, p_value = stats.f_oneway(group1, group2, group3)
print(f"One-Way ANOVA: F={f_stat:.3f}, p={p_value:.3f}")

# Two-Way ANOVA
import statsmodels.api as sm
from statsmodels.formula.api import ols

data = pd.DataFrame({
    'value': np.concatenate([group1, group2, group3]),
    'group': ['A']*30 + ['B']*30 + ['C']*30,
    'block': ['X']*15 + ['Y']*15 + ['X']*15 + ['Y']*15 + ['X']*15 + ['Y']*15
})

model = ols('value ~ C(group) + C(block) + C(group):C(block)', data).fit()
anova_table = sm.stats.anova_lm(model, typ=2)
```

## 3. Non-parametric Tests

### Rank-based Tests

```python
# Wilcoxon Signed-Rank Test
stat, p_value = stats.wilcoxon(sample1, sample2)
print(f"Wilcoxon test: stat={stat:.3f}, p={p_value:.3f}")

# Mann-Whitney U Test
stat, p_value = stats.mannwhitneyu(sample1, sample2)
print(f"Mann-Whitney U: stat={stat:.3f}, p={p_value:.3f}")

# Kruskal-Wallis Test
stat, p_value = stats.kruskal(group1, group2, group3)
print(f"Kruskal-Wallis: stat={stat:.3f}, p={p_value:.3f}")
```

### Chi-square Tests

```python
# Goodness of Fit
observed = np.array([10, 20, 30, 40])
expected = np.array([25, 25, 25, 25])
chi_stat, p_value = stats.chisquare(observed, expected)
print(f"Chi-square GOF: stat={chi_stat:.3f}, p={p_value:.3f}")

# Test of Independence
table = np.array([[10, 20, 30],
                 [20, 30, 40]])
chi_stat, p_value, dof, expected = stats.chi2_contingency(table)
print(f"Chi-square independence: stat={chi_stat:.3f}, p={p_value:.3f}")
```

## 4. Power Analysis

### Sample Size Calculation

```python
def calculate_sample_size(effect_size, alpha=0.05, power=0.8):
    """Calculate required sample size for t-test"""
    from statsmodels.stats.power import TTestIndPower
    analysis = TTestIndPower()
    sample_size = analysis.solve_power(
        effect_size=effect_size,
        alpha=alpha,
        power=power,
        ratio=1.0
    )
    return int(np.ceil(sample_size))

# Example
effect_size = 0.5
sample_size = calculate_sample_size(effect_size)
print(f"Required sample size: {sample_size}")
```

### Power Calculation

```python
def calculate_power(sample_size, effect_size, alpha=0.05):
    """Calculate power for t-test"""
    from statsmodels.stats.power import TTestIndPower
    analysis = TTestIndPower()
    power = analysis.solve_power(
        effect_size=effect_size,
        nobs1=sample_size,
        alpha=alpha,
        ratio=1.0
    )
    return power

# Example
power = calculate_power(30, 0.5)
print(f"Power: {power:.3f}")
```

## 5. Multiple Testing

### Correction Methods

```python
from statsmodels.stats.multitest import multipletests

# Example p-values
p_values = [0.01, 0.04, 0.03, 0.05, 0.02]

# Bonferroni Correction
rejected, p_corrected, _, _ = multipletests(p_values, method='bonferroni')
print(f"Bonferroni corrected p-values: {p_corrected}")

# Benjamini-Hochberg Correction
rejected, p_corrected, _, _ = multipletests(p_values, method='fdr_bh')
print(f"BH corrected p-values: {p_corrected}")
```

## 6. Best Practices

### Test Selection

- Consider data type and distribution
- Check assumptions
- Choose appropriate test
- Consider sample size

### Analysis

- State clear hypotheses
- Choose appropriate significance level
- Report effect sizes
- Consider practical significance

### Common Pitfalls

- Multiple testing without correction
- P-hacking
- Ignoring assumptions
- Misinterpreting p-values
- Not reporting effect sizes

### Reporting Results

- State null and alternative hypotheses
- Report test statistic and p-value
- Include effect size
- Provide confidence intervals
- Discuss practical significance

---

This file covers comprehensive hypothesis testing concepts and their applications. For more basic statistical concepts, refer to the Statistics-Fundamentals.md file.
