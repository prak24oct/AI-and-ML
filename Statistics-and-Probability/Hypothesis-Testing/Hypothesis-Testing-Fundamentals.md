# 📊 Hypothesis Testing Fundamentals

## 1. Introduction to Hypothesis Testing

### What is Hypothesis Testing?

- Hypothesis testing is a statistical method used to make decisions based on data
- Helps determine whether an observed effect is real or due to chance
- Essential for data-driven decision making in AI and ML

### Key Concepts

- Population vs Sample
- Parameters vs Statistics
- Null Hypothesis (H₀) vs Alternative Hypothesis (H₁)
- Type I and Type II Errors
- Significance Level (α) and Power (1-β)

## 2. Basic Concepts

### Hypothesis Formulation

```python
# Example: Testing if a new drug improves recovery time
# H₀: μ_new = μ_old (no improvement)
# H₁: μ_new < μ_old (improvement)
```

### Types of Tests

```python
def determine_test_type(data_type, sample_size, distribution):
    """
    Determine appropriate test type based on data characteristics
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

## 3. Test Statistics and Distributions

### Z-Test

```python
import numpy as np
from scipy import stats

def z_test(sample_mean, pop_mean, pop_std, n):
    """Calculate z-score and p-value for z-test"""
    z_score = (sample_mean - pop_mean) / (pop_std / np.sqrt(n))
    p_value = 2 * (1 - stats.norm.cdf(abs(z_score)))
    return z_score, p_value

# Example
sample_mean = 100
pop_mean = 95
pop_std = 15
n = 30
z, p = z_test(sample_mean, pop_mean, pop_std, n)
print(f"Z-score: {z:.3f}, p-value: {p:.3f}")
```

### T-Test

```python
def t_test(sample, pop_mean):
    """Calculate t-score and p-value for t-test"""
    t_stat, p_value = stats.ttest_1samp(sample, pop_mean)
    return t_stat, p_value

# Example
sample = np.random.normal(0, 1, 20)
t, p = t_test(sample, 0)
print(f"T-score: {t:.3f}, p-value: {p:.3f}")
```

## 4. Errors and Power

### Type I and Type II Errors

```python
def calculate_errors(alpha, beta):
    """
    Calculate probabilities of Type I and Type II errors
    """
    type1_error = alpha
    type2_error = beta
    power = 1 - beta
    return type1_error, type2_error, power

# Example
alpha = 0.05
beta = 0.2
type1, type2, power = calculate_errors(alpha, beta)
print(f"Type I Error: {type1:.3f}")
print(f"Type II Error: {type2:.3f}")
print(f"Power: {power:.3f}")
```

### Power Analysis

```python
from statsmodels.stats.power import TTestIndPower

def calculate_sample_size(effect_size, alpha=0.05, power=0.8):
    """Calculate required sample size for t-test"""
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

## 5. Best Practices

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

This file covers fundamental hypothesis testing concepts. For more advanced topics, refer to the other modules in this series.
