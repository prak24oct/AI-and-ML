# 🚀 NumPy Applications

This file covers practical applications of NumPy in various domains, including data science, machine learning, and scientific computing.

## 📊 Data Science Applications

### 1. Data Preprocessing

```python
import numpy as np

# Handling missing values
data = np.array([1, 2, np.nan, 4, 5])
mean = np.nanmean(data)
filled_data = np.nan_to_num(data, nan=mean)

# Data normalization
data = np.array([1, 2, 3, 4, 5])
normalized = (data - np.mean(data)) / np.std(data)

# Feature scaling
data = np.array([[1, 2], [3, 4], [5, 6]])
min_vals = np.min(data, axis=0)
max_vals = np.max(data, axis=0)
scaled = (data - min_vals) / (max_vals - min_vals)
```

### 2. Statistical Analysis

```python
# Descriptive statistics
data = np.random.normal(0, 1, 1000)
mean = np.mean(data)
median = np.median(data)
std = np.std(data)
percentiles = np.percentile(data, [25, 50, 75])

# Correlation analysis
x = np.random.rand(100)
y = np.random.rand(100)
correlation = np.corrcoef(x, y)[0, 1]
```

## 🤖 Machine Learning Applications

### 1. Linear Algebra Operations

```python
# Matrix operations for linear regression
X = np.random.rand(100, 3)
y = np.random.rand(100)
theta = np.linalg.inv(X.T @ X) @ X.T @ y

# Eigenvalue decomposition
A = np.random.rand(3, 3)
eigenvalues, eigenvectors = np.linalg.eig(A)
```

### 2. Neural Networks

```python
# Activation functions
def sigmoid(x):
    return 1 / (1 + np.exp(-x))

def relu(x):
    return np.maximum(0, x)

# Forward propagation
def forward_prop(X, W1, b1, W2, b2):
    Z1 = X @ W1 + b1
    A1 = relu(Z1)
    Z2 = A1 @ W2 + b2
    A2 = sigmoid(Z2)
    return A2
```

## 🔬 Scientific Computing

### 1. Signal Processing

```python
# Fourier transform
t = np.linspace(0, 1, 1000)
signal = np.sin(2 * np.pi * 5 * t)
freq = np.fft.fft(signal)
freq_magnitude = np.abs(freq)

# Convolution
kernel = np.array([1, 2, 1]) / 4
signal = np.random.rand(100)
convolved = np.convolve(signal, kernel, mode='same')
```

### 2. Image Processing

```python
# Image manipulation
def rgb_to_grayscale(image):
    return np.dot(image[...,:3], [0.2989, 0.5870, 0.1140])

def apply_filter(image, kernel):
    return np.convolve2d(image, kernel, mode='same')

# Edge detection
sobel_x = np.array([[-1, 0, 1], [-2, 0, 2], [-1, 0, 1]])
sobel_y = np.array([[-1, -2, -1], [0, 0, 0], [1, 2, 1]])
```

## 📈 Financial Applications

### 1. Portfolio Optimization

```python
# Portfolio returns
returns = np.random.normal(0.001, 0.02, (100, 3))
portfolio_weights = np.array([0.3, 0.4, 0.3])
portfolio_returns = returns @ portfolio_weights

# Risk metrics
volatility = np.std(portfolio_returns)
sharpe_ratio = np.mean(portfolio_returns) / volatility
```

### 2. Time Series Analysis

```python
# Moving averages
def moving_average(data, window):
    return np.convolve(data, np.ones(window)/window, mode='valid')

# Exponential smoothing
def exponential_smoothing(data, alpha):
    smoothed = np.zeros_like(data)
    smoothed[0] = data[0]
    for i in range(1, len(data)):
        smoothed[i] = alpha * data[i] + (1 - alpha) * smoothed[i-1]
    return smoothed
```

## 🎯 Best Practices

1. **Vectorization**

   - Use vectorized operations instead of loops
   - Leverage broadcasting for efficient computations
   - Utilize NumPy's built-in functions

2. **Memory Management**

   - Use appropriate data types
   - Avoid unnecessary copies
   - Pre-allocate arrays when possible

3. **Performance Optimization**

   - Use in-place operations
   - Minimize memory allocations
   - Profile code for bottlenecks

4. **Code Organization**
   - Use meaningful variable names
   - Add comments for complex operations
   - Document function parameters and returns

## ⚠️ Common Pitfalls

1. **Memory Issues**

   - Avoid large temporary arrays
   - Use views instead of copies when possible
   - Monitor memory usage

2. **Numerical Stability**

   - Be aware of floating-point precision
   - Use appropriate numerical methods
   - Handle edge cases properly

3. **Performance**
   - Avoid unnecessary type conversions
   - Minimize array reshaping
   - Use appropriate algorithms

## 📚 Additional Resources

- [NumPy Documentation](https://numpy.org/doc/stable/)
- [SciPy Documentation](https://docs.scipy.org/doc/scipy/)
- [NumPy User Guide](https://numpy.org/doc/stable/user/index.html)
- [NumPy Tutorials](https://numpy.org/doc/stable/user/tutorials.html)
