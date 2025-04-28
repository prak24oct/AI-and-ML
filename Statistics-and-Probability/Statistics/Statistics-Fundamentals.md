# 📊 Statistics Fundamentals

## 1. Introduction to Statistics

### What is Statistics?

- Statistics is the science of collecting, analyzing, interpreting, and presenting data
- Two main branches: Descriptive and Inferential Statistics
- Essential for data analysis and decision making

### Key Concepts

- Population vs Sample
- Parameters vs Statistics
- Variables: Categorical and Numerical
- Data Types: Nominal, Ordinal, Interval, Ratio

## 2. Descriptive Statistics

### Measures of Central Tendency

```python
import numpy as np
from scipy import stats

data = [1, 2, 3, 4, 5, 5, 6, 7, 8, 9]

# Mean
mean = np.mean(data)  # 5.0

# Median
median = np.median(data)  # 5.0

# Mode
mode = stats.mode(data)  # 5
```

### Measures of Dispersion

```python
# Range
range_val = max(data) - min(data)  # 8

# Variance
variance = np.var(data)  # 6.0

# Standard Deviation
std_dev = np.std(data)  # 2.449

# Interquartile Range (IQR)
q1 = np.percentile(data, 25)  # 3.5
q3 = np.percentile(data, 75)  # 6.5
iqr = q3 - q1  # 3.0
```

### Data Visualization

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Histogram
plt.hist(data, bins=5)
plt.title('Data Distribution')
plt.show()

# Box Plot
sns.boxplot(data)
plt.title('Box Plot')
plt.show()
```

## 3. Probability Distributions

### Discrete Distributions

```python
# Binomial Distribution
n, p = 10, 0.5
binomial = stats.binom(n, p)
print(binomial.pmf(5))  # Probability of 5 successes

# Poisson Distribution
lambda_ = 3
poisson = stats.poisson(lambda_)
print(poisson.pmf(2))  # Probability of 2 events
```

### Continuous Distributions

```python
# Normal Distribution
mu, sigma = 0, 1
normal = stats.norm(mu, sigma)
print(normal.pdf(0))  # Probability density at 0

# Exponential Distribution
lambda_ = 1
exponential = stats.expon(scale=1/lambda_)
print(exponential.pdf(1))  # Probability density at 1
```

## 4. Correlation and Covariance

### Correlation

```python
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]

# Pearson Correlation
corr = np.corrcoef(x, y)[0, 1]  # 1.0

# Spearman Correlation
corr_spearman = stats.spearmanr(x, y)[0]  # 1.0
```

### Covariance

```python
# Covariance Matrix
cov_matrix = np.cov(x, y)
print(cov_matrix)
```

## 5. Data Types and Scales

### Categorical Data

```python
# Nominal Data
colors = ['red', 'blue', 'green', 'red']

# Ordinal Data
grades = ['A', 'B', 'C', 'D', 'F']
```

### Numerical Data

```python
# Discrete Data
counts = [1, 2, 3, 4, 5]

# Continuous Data
measurements = [1.5, 2.3, 3.7, 4.1, 5.9]
```

## 6. Best Practices

### Data Collection

- Define clear objectives
- Choose appropriate sampling methods
- Ensure data quality
- Document data collection process

### Data Analysis

- Check assumptions
- Use appropriate statistical methods
- Validate results
- Document analysis process

### Common Pitfalls

- Ignoring data quality
- Using inappropriate statistical methods
- Misinterpreting results
- Not checking assumptions

---

This file covers fundamental statistics concepts. For more advanced topics, refer to the other modules in this series.
