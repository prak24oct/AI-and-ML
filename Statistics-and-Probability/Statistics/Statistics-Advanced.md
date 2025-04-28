# 📊 Advanced Statistics

## 1. Bayesian Statistics

### Bayesian Inference

```python
import pymc3 as pm
import numpy as np

# Generate data
data = np.random.normal(0, 1, 100)

# Define model
with pm.Model() as model:
    # Priors
    mu = pm.Normal('mu', mu=0, sigma=1)
    sigma = pm.HalfNormal('sigma', sigma=1)

    # Likelihood
    likelihood = pm.Normal('likelihood', mu=mu, sigma=sigma, observed=data)

    # Inference
    trace = pm.sample(1000, tune=1000)
```

### Bayesian Regression

```python
# Generate data
x = np.random.normal(0, 1, 100)
y = 2 * x + np.random.normal(0, 1, 100)

# Define model
with pm.Model() as model:
    # Priors
    alpha = pm.Normal('alpha', mu=0, sigma=10)
    beta = pm.Normal('beta', mu=0, sigma=10)
    sigma = pm.HalfNormal('sigma', sigma=1)

    # Likelihood
    mu = alpha + beta * x
    likelihood = pm.Normal('likelihood', mu=mu, sigma=sigma, observed=y)

    # Inference
    trace = pm.sample(1000, tune=1000)
```

## 2. Time Series Analysis

### ARIMA Models

```python
from statsmodels.tsa.arima.model import ARIMA
import pandas as pd

# Generate time series data
dates = pd.date_range('2023-01-01', periods=100, freq='D')
data = pd.Series(np.random.normal(0, 1, 100), index=dates)

# Fit ARIMA model
model = ARIMA(data, order=(1, 1, 1))
results = model.fit()
print(results.summary())
```

### Seasonal Decomposition

```python
from statsmodels.tsa.seasonal import seasonal_decompose

# Decompose time series
decomposition = seasonal_decompose(data, model='additive', period=7)
trend = decomposition.trend
seasonal = decomposition.seasonal
residual = decomposition.resid
```

## 3. Multivariate Analysis

### Principal Component Analysis (PCA)

```python
from sklearn.decomposition import PCA
from sklearn.preprocessing import StandardScaler

# Generate data
X = np.random.normal(0, 1, (100, 5))

# Standardize data
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

# Fit PCA
pca = PCA(n_components=2)
X_pca = pca.fit_transform(X_scaled)
```

### Factor Analysis

```python
from sklearn.decomposition import FactorAnalysis

# Fit Factor Analysis
fa = FactorAnalysis(n_components=2)
X_fa = fa.fit_transform(X_scaled)
```

## 4. Non-parametric Methods

### Kernel Density Estimation

```python
from scipy.stats import gaussian_kde

# Generate data
data = np.random.normal(0, 1, 100)

# Fit KDE
kde = gaussian_kde(data)
x = np.linspace(-3, 3, 100)
y = kde(x)
```

### Bootstrap Methods

```python
def bootstrap_mean(data, n_bootstraps=1000):
    means = []
    for _ in range(n_bootstraps):
        sample = np.random.choice(data, size=len(data), replace=True)
        means.append(np.mean(sample))
    return means

# Generate data
data = np.random.normal(0, 1, 100)

# Bootstrap mean
bootstrap_means = bootstrap_mean(data)
```

## 5. Machine Learning Applications

### Feature Selection

```python
from sklearn.feature_selection import SelectKBest, f_regression

# Generate data
X = np.random.normal(0, 1, (100, 10))
y = np.random.normal(0, 1, 100)

# Select best features
selector = SelectKBest(score_func=f_regression, k=5)
X_new = selector.fit_transform(X, y)
```

### Cross-Validation

```python
from sklearn.model_selection import cross_val_score
from sklearn.linear_model import LinearRegression

# Fit model with cross-validation
model = LinearRegression()
scores = cross_val_score(model, X, y, cv=5)
print(f"Cross-validation scores: {scores}")
print(f"Mean score: {scores.mean()}")
```

## 6. Advanced Visualization

### Statistical Plots

```python
import seaborn as sns
import matplotlib.pyplot as plt

# Violin Plot
sns.violinplot(data=data)
plt.title('Violin Plot')
plt.show()

# Pair Plot
sns.pairplot(pd.DataFrame(X))
plt.show()
```

### Interactive Visualization

```python
import plotly.express as px

# 3D Scatter Plot
fig = px.scatter_3d(x=X[:, 0], y=X[:, 1], z=X[:, 2])
fig.show()
```

## 7. Best Practices

### Model Selection

- Consider model assumptions
- Use appropriate validation methods
- Compare multiple models
- Consider computational complexity

### Data Analysis

- Document analysis process
- Validate results
- Consider multiple approaches
- Check for robustness

### Common Pitfalls

- Overfitting
- Ignoring assumptions
- Not validating results
- Misinterpreting complex models

---

This file covers advanced statistical methods. For more basic concepts, refer to the other modules in this series.
