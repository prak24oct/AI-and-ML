# 📊 Hypothesis Testing Applications

## 1. Multiple Testing

### Bonferroni Correction

```python
import numpy as np
from scipy import stats

def bonferroni_correction(p_values, alpha=0.05):
    """Apply Bonferroni correction"""
    n_tests = len(p_values)
    corrected_alpha = alpha / n_tests
    significant = [p < corrected_alpha for p in p_values]
    return corrected_alpha, significant

# Example
p_values = [0.01, 0.03, 0.04, 0.06]
alpha, significant = bonferroni_correction(p_values)
print(f"Corrected alpha: {alpha:.3f}")
print(f"Significant results: {significant}")
```

### False Discovery Rate (FDR)

```python
def benjamini_hochberg(p_values, alpha=0.05):
    """Apply Benjamini-Hochberg procedure"""
    n = len(p_values)
    sorted_p = np.sort(p_values)
    ranks = np.arange(1, n+1)
    critical_values = alpha * ranks / n
    significant = sorted_p <= critical_values
    return critical_values, significant

# Example
critical_values, significant = benjamini_hochberg(p_values)
print(f"Critical values: {critical_values}")
print(f"Significant results: {significant}")
```

## 2. Bayesian Hypothesis Testing

### Bayes Factor

```python
from scipy.stats import norm

def bayes_factor(sample, prior_mean, prior_std, null_mean=0):
    """Calculate Bayes factor"""
    n = len(sample)
    sample_mean = np.mean(sample)
    sample_std = np.std(sample, ddof=1)

    # Calculate likelihood under null
    null_likelihood = norm.pdf(sample_mean, null_mean, sample_std/np.sqrt(n))

    # Calculate likelihood under alternative
    alt_likelihood = norm.pdf(sample_mean, prior_mean, np.sqrt(prior_std**2 + (sample_std**2/n)))

    return alt_likelihood / null_likelihood

# Example
sample = np.random.normal(0.5, 1, 30)
bf = bayes_factor(sample, 0, 1)
print(f"Bayes Factor: {bf:.3f}")
```

## 3. Sequential Testing

### Sequential Probability Ratio Test (SPRT)

```python
def sequential_test(sample, alpha=0.05, beta=0.2, effect_size=0.5):
    """Perform sequential probability ratio test"""
    n = len(sample)
    sample_mean = np.mean(sample)
    sample_std = np.std(sample, ddof=1)

    # Calculate likelihood ratio
    lr = np.exp(n * (effect_size * sample_mean - effect_size**2/2))

    # Calculate boundaries
    a = beta / (1 - alpha)
    b = (1 - beta) / alpha

    if lr >= b:
        return "Reject H0"
    elif lr <= a:
        return "Accept H0"
    else:
        return "Continue sampling"

# Example
result = sequential_test(sample)
print(f"Test result: {result}")
```

## 4. Power Analysis

### Sample Size Calculation

```python
from statsmodels.stats.power import TTestIndPower

def calculate_sample_size(effect_size, alpha=0.05, power=0.8, ratio=1.0):
    """Calculate required sample size"""
    analysis = TTestIndPower()
    n = analysis.solve_power(
        effect_size=effect_size,
        alpha=alpha,
        power=power,
        ratio=ratio
    )
    return int(np.ceil(n))

# Example
effect_size = 0.5
n = calculate_sample_size(effect_size)
print(f"Required sample size: {n}")
```

### Power Curve

```python
import matplotlib.pyplot as plt

def plot_power_curve(effect_sizes, alpha=0.05, power=0.8):
    """Plot power curve"""
    analysis = TTestIndPower()
    sample_sizes = [calculate_sample_size(e, alpha, power) for e in effect_sizes]

    plt.figure(figsize=(10, 6))
    plt.plot(effect_sizes, sample_sizes)
    plt.xlabel('Effect Size')
    plt.ylabel('Required Sample Size')
    plt.title('Power Curve')
    plt.grid(True)
    plt.show()

# Example
effect_sizes = np.linspace(0.1, 1.0, 10)
plot_power_curve(effect_sizes)
```

## 5. Practical Applications

### A/B Testing

```python
def ab_test(control, treatment, alpha=0.05):
    """Perform A/B test"""
    # Check assumptions
    _, p_norm = stats.shapiro(control)
    _, p_var = stats.levene(control, treatment)

    if p_norm > alpha and p_var > alpha:
        # Use t-test
        stat, p = stats.ttest_ind(control, treatment)
    else:
        # Use Mann-Whitney U test
        stat, p = stats.mannwhitneyu(control, treatment)

    # Calculate effect size
    d = cohens_d(control, treatment)

    return stat, p, d

# Example
control = np.random.normal(100, 15, 100)
treatment = np.random.normal(105, 15, 100)
stat, p, d = ab_test(control, treatment)
print(f"Test statistic: {stat:.3f}")
print(f"p-value: {p:.3f}")
print(f"Effect size (Cohen's d): {d:.3f}")
```

### Time Series Analysis

```python
def time_series_test(series, alpha=0.05):
    """Perform time series hypothesis test"""
    # Check stationarity
    from statsmodels.tsa.stattools import adfuller
    adf_stat, adf_p = adfuller(series)

    # Check autocorrelation
    from statsmodels.stats.stattools import durbin_watson
    dw_stat = durbin_watson(series)

    return adf_stat, adf_p, dw_stat

# Example
series = np.random.normal(0, 1, 100)
adf_stat, adf_p, dw_stat = time_series_test(series)
print(f"ADF statistic: {adf_stat:.3f}")
print(f"ADF p-value: {adf_p:.3f}")
print(f"Durbin-Watson statistic: {dw_stat:.3f}")
```

## 6. Best Practices

### Test Selection

- Consider research question and data type
- Check assumptions carefully
- Choose appropriate test based on sample size
- Consider multiple testing corrections

### Analysis

- Report all relevant statistics
- Include effect sizes and confidence intervals
- Consider practical significance
- Document assumptions and limitations

### Common Pitfalls

- Multiple testing without correction
- Ignoring assumptions
- Over-reliance on p-values
- Not considering effect sizes
- Misinterpreting results

### Reporting Results

- State hypotheses clearly
- Report all test statistics
- Include effect sizes and confidence intervals
- Discuss practical implications
- Address limitations and assumptions

---

This file covers practical applications and advanced topics in hypothesis testing. For more specific applications, refer to the relevant domain-specific modules.
