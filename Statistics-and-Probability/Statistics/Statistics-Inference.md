# 📊 Statistical Inference

## 1. Sampling and Estimation

### Sampling Methods

```python
import numpy as np
from scipy import stats

# Simple Random Sampling
population = np.arange(100)
sample = np.random.choice(population, size=10, replace=False)

# Stratified Sampling
strata = np.array(['A', 'B', 'C', 'D'])
sample_stratified = np.random.choice(strata, size=10, p=[0.25, 0.25, 0.25, 0.25])
```

### Point Estimation

```python
# Sample Mean
sample_mean = np.mean(sample)

# Sample Variance
sample_var = np.var(sample, ddof=1)  # Unbiased estimator
```

### Interval Estimation

```python
# Confidence Interval for Mean
confidence = 0.95
n = len(sample)
std_err = np.std(sample, ddof=1) / np.sqrt(n)
ci = stats.t.interval(confidence, n-1, loc=sample_mean, scale=std_err)
```

## 2. Hypothesis Testing

### One-Sample Tests

```python
# One-Sample t-test
sample = np.random.normal(0, 1, 30)
t_stat, p_value = stats.ttest_1samp(sample, 0)
print(f"t-statistic: {t_stat}, p-value: {p_value}")

# One-Sample Proportion Test
successes = 15
trials = 100
prop_stat, prop_pval = stats.binomtest(successes, trials, p=0.1)
```

### Two-Sample Tests

```python
# Independent t-test
sample1 = np.random.normal(0, 1, 30)
sample2 = np.random.normal(1, 1, 30)
t_stat, p_value = stats.ttest_ind(sample1, sample2)

# Paired t-test
t_stat, p_value = stats.ttest_rel(sample1, sample2)
```

### Non-parametric Tests

```python
# Wilcoxon Signed-Rank Test
stat, p_value = stats.wilcoxon(sample1, sample2)

# Mann-Whitney U Test
stat, p_value = stats.mannwhitneyu(sample1, sample2)
```

## 3. Analysis of Variance (ANOVA)

### One-Way ANOVA

```python
group1 = np.random.normal(0, 1, 30)
group2 = np.random.normal(1, 1, 30)
group3 = np.random.normal(2, 1, 30)

f_stat, p_value = stats.f_oneway(group1, group2, group3)
```

### Two-Way ANOVA

```python
import statsmodels.api as sm
from statsmodels.formula.api import ols

# Create data
data = pd.DataFrame({
    'value': np.concatenate([group1, group2, group3]),
    'group': ['A']*30 + ['B']*30 + ['C']*30,
    'block': ['X']*15 + ['Y']*15 + ['X']*15 + ['Y']*15 + ['X']*15 + ['Y']*15
})

# Fit model
model = ols('value ~ C(group) + C(block) + C(group):C(block)', data).fit()
anova_table = sm.stats.anova_lm(model, typ=2)
```

## 4. Regression Analysis

### Linear Regression

```python
import statsmodels.api as sm

# Generate data
x = np.random.normal(0, 1, 100)
y = 2 * x + np.random.normal(0, 1, 100)

# Fit model
X = sm.add_constant(x)
model = sm.OLS(y, X).fit()
print(model.summary())
```

### Multiple Regression

```python
# Generate data
x1 = np.random.normal(0, 1, 100)
x2 = np.random.normal(0, 1, 100)
y = 2 * x1 + 3 * x2 + np.random.normal(0, 1, 100)

# Fit model
X = sm.add_constant(np.column_stack((x1, x2)))
model = sm.OLS(y, X).fit()
print(model.summary())
```

## 5. Chi-Square Tests

### Goodness of Fit

```python
observed = np.array([10, 20, 30, 40])
expected = np.array([25, 25, 25, 25])
chi_stat, p_value = stats.chisquare(observed, expected)
```

### Test of Independence

```python
# Create contingency table
table = np.array([[10, 20, 30],
                 [20, 30, 40]])

chi_stat, p_value, dof, expected = stats.chi2_contingency(table)
```

## 6. Best Practices

### Hypothesis Testing

- State clear hypotheses
- Choose appropriate test
- Check assumptions
- Interpret results carefully

### Regression Analysis

- Check model assumptions
- Validate model fit
- Consider multicollinearity
- Check for outliers

### Common Pitfalls

- Multiple testing issues
- P-hacking
- Ignoring assumptions
- Misinterpreting p-values

---

This file covers statistical inference concepts. For more advanced topics, refer to the other modules in this series.
