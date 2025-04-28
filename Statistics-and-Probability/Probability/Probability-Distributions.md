# 📊 Probability Distributions

## 1. Discrete Distributions

### Binomial Distribution

```python
from scipy import stats
import numpy as np
import matplotlib.pyplot as plt

# Parameters
n = 10  # number of trials
p = 0.5  # probability of success

# Create distribution
binomial = stats.binom(n, p)

# Probability Mass Function (PMF)
x = np.arange(0, n+1)
pmf = binomial.pmf(x)

# Plot
plt.bar(x, pmf)
plt.title('Binomial Distribution (n=10, p=0.5)')
plt.xlabel('Number of Successes')
plt.ylabel('Probability')
plt.show()
```

### Poisson Distribution

```python
# Parameters
lambda_ = 3  # average rate of occurrence

# Create distribution
poisson = stats.poisson(lambda_)

# PMF
x = np.arange(0, 10)
pmf = poisson.pmf(x)

# Plot
plt.bar(x, pmf)
plt.title('Poisson Distribution (λ=3)')
plt.xlabel('Number of Events')
plt.ylabel('Probability')
plt.show()
```

### Geometric Distribution

```python
# Parameters
p = 0.3  # probability of success

# Create distribution
geometric = stats.geom(p)

# PMF
x = np.arange(1, 11)
pmf = geometric.pmf(x)

# Plot
plt.bar(x, pmf)
plt.title('Geometric Distribution (p=0.3)')
plt.xlabel('Number of Trials Until Success')
plt.ylabel('Probability')
plt.show()
```

## 2. Continuous Distributions

### Normal Distribution

```python
# Parameters
mu = 0  # mean
sigma = 1  # standard deviation

# Create distribution
normal = stats.norm(mu, sigma)

# Probability Density Function (PDF)
x = np.linspace(-4, 4, 100)
pdf = normal.pdf(x)

# Plot
plt.plot(x, pdf)
plt.title('Normal Distribution (μ=0, σ=1)')
plt.xlabel('Value')
plt.ylabel('Probability Density')
plt.show()
```

### Exponential Distribution

```python
# Parameters
lambda_ = 1  # rate parameter

# Create distribution
exponential = stats.expon(scale=1/lambda_)

# PDF
x = np.linspace(0, 5, 100)
pdf = exponential.pdf(x)

# Plot
plt.plot(x, pdf)
plt.title('Exponential Distribution (λ=1)')
plt.xlabel('Value')
plt.ylabel('Probability Density')
plt.show()
```

### Uniform Distribution

```python
# Parameters
a = 0  # lower bound
b = 1  # upper bound

# Create distribution
uniform = stats.uniform(a, b-a)

# PDF
x = np.linspace(-0.5, 1.5, 100)
pdf = uniform.pdf(x)

# Plot
plt.plot(x, pdf)
plt.title('Uniform Distribution (a=0, b=1)')
plt.xlabel('Value')
plt.ylabel('Probability Density')
plt.show()
```

## 3. Multivariate Distributions

### Multivariate Normal Distribution

```python
from scipy.stats import multivariate_normal

# Parameters
mean = [0, 0]
cov = [[1, 0.5], [0.5, 1]]

# Create distribution
mvn = multivariate_normal(mean, cov)

# PDF
x, y = np.mgrid[-3:3:.1, -3:3:.1]
pos = np.dstack((x, y))
pdf = mvn.pdf(pos)

# Plot
plt.contourf(x, y, pdf)
plt.title('Bivariate Normal Distribution')
plt.xlabel('X')
plt.ylabel('Y')
plt.colorbar()
plt.show()
```

## 4. Distribution Properties

### Moments

```python
def moments(distribution, n_samples=1000):
    samples = distribution.rvs(n_samples)
    mean = np.mean(samples)
    variance = np.var(samples)
    skewness = stats.skew(samples)
    kurtosis = stats.kurtosis(samples)
    return mean, variance, skewness, kurtosis

# Example: Normal distribution
normal = stats.norm(0, 1)
mean, var, skew, kurt = moments(normal)
print(f"Mean: {mean:.3f}, Variance: {var:.3f}, Skewness: {skew:.3f}, Kurtosis: {kurt:.3f}")
```

### Quantiles and Percentiles

```python
# Example: Normal distribution
normal = stats.norm(0, 1)

# Quantiles
q25 = normal.ppf(0.25)  # 25th percentile
q50 = normal.ppf(0.50)  # 50th percentile (median)
q75 = normal.ppf(0.75)  # 75th percentile

print(f"25th percentile: {q25:.3f}")
print(f"Median: {q50:.3f}")
print(f"75th percentile: {q75:.3f}")
```

## 5. Distribution Fitting

### Parameter Estimation

```python
# Generate sample data
data = stats.norm.rvs(loc=0, scale=1, size=1000)

# Fit normal distribution
params = stats.norm.fit(data)
print(f"Estimated parameters: μ={params[0]:.3f}, σ={params[1]:.3f}")
```

### Goodness of Fit

```python
# Kolmogorov-Smirnov test
ks_stat, p_value = stats.kstest(data, 'norm', args=params)
print(f"KS statistic: {ks_stat:.3f}, p-value: {p_value:.3f}")
```

## 6. Best Practices

### Distribution Selection

- Consider data type (discrete/continuous)
- Check distribution assumptions
- Validate fit with tests
- Consider multiple distributions

### Common Pitfalls

- Assuming normal distribution without checking
- Ignoring distribution assumptions
- Not validating parameter estimates
- Misinterpreting distribution properties

---

This file covers probability distributions and their applications. For more advanced topics, refer to the other modules in this series.
