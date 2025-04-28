# 📊 NumPy Operations

## 1. Mathematical Operations

### Basic Math Functions

```python
arr = np.array([1, 2, 3, 4, 5])

# Sum
print(np.sum(arr))  # 15

# Mean
print(np.mean(arr))  # 3.0

# Standard deviation
print(np.std(arr))  # 1.4142135623730951

# Minimum and maximum
print(np.min(arr))  # 1
print(np.max(arr))  # 5
```

### Trigonometric Functions

```python
angles = np.array([0, np.pi/2, np.pi])

# Sine
print(np.sin(angles))  # [0, 1, 0]

# Cosine
print(np.cos(angles))  # [1, 0, -1]

# Tangent
print(np.tan(angles))  # [0, inf, 0]
```

### Exponential and Logarithmic

```python
arr = np.array([1, 2, 3])

# Exponential
print(np.exp(arr))  # [2.718, 7.389, 20.085]

# Natural logarithm
print(np.log(arr))  # [0, 0.693, 1.098]

# Base-10 logarithm
print(np.log10(arr))  # [0, 0.301, 0.477]
```

## 2. Statistical Operations

### Descriptive Statistics

```python
arr = np.array([1, 2, 3, 4, 5])

# Percentiles
print(np.percentile(arr, 50))  # 3.0 (median)

# Variance
print(np.var(arr))  # 2.0

# Histogram
hist, bins = np.histogram(arr, bins=3)
print(hist)  # [2, 2, 1]
print(bins)  # [1, 2.333, 3.666, 5]
```

### Correlation and Covariance

```python
x = np.array([1, 2, 3, 4, 5])
y = np.array([5, 4, 3, 2, 1])

# Correlation coefficient
print(np.corrcoef(x, y))  # -1.0

# Covariance matrix
print(np.cov(x, y))
```

## 3. Linear Algebra

### Matrix Operations

```python
A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])

# Matrix multiplication
print(np.dot(A, B))
# [[19, 22],
#  [43, 50]]

# Matrix inverse
print(np.linalg.inv(A))
# [[-2, 1],
#  [1.5, -0.5]]
```

### Eigenvalues and Eigenvectors

```python
A = np.array([[1, 2], [2, 1]])

# Eigenvalues and eigenvectors
eigenvalues, eigenvectors = np.linalg.eig(A)
print(eigenvalues)  # [3, -1]
print(eigenvectors)
# [[ 0.707, -0.707],
#  [ 0.707,  0.707]]
```

### Solving Linear Equations

```python
# Solve Ax = b
A = np.array([[1, 2], [3, 4]])
b = np.array([5, 6])
x = np.linalg.solve(A, b)
print(x)  # [-4, 4.5]
```

## 4. Random Number Generation

### Basic Random Numbers

```python
# Random floats in [0, 1)
print(np.random.random(3))  # [0.123, 0.456, 0.789]

# Random integers
print(np.random.randint(0, 10, 3))  # [3, 7, 2]

# Random normal distribution
print(np.random.normal(0, 1, 3))  # [-0.123, 0.456, -0.789]
```

### Random Sampling

```python
arr = np.array([1, 2, 3, 4, 5])

# Random choice
print(np.random.choice(arr, 3))  # [2, 5, 1]

# Random permutation
print(np.random.permutation(arr))  # [3, 1, 5, 2, 4]
```

## 5. Set Operations

### Unique Elements

```python
arr = np.array([1, 2, 2, 3, 3, 3])

# Unique elements
print(np.unique(arr))  # [1, 2, 3]

# Count unique elements
print(np.unique(arr, return_counts=True))
# (array([1, 2, 3]), array([1, 2, 3]))
```

### Set Operations

```python
a = np.array([1, 2, 3, 4, 5])
b = np.array([3, 4, 5, 6, 7])

# Intersection
print(np.intersect1d(a, b))  # [3, 4, 5]

# Union
print(np.union1d(a, b))  # [1, 2, 3, 4, 5, 6, 7]

# Set difference
print(np.setdiff1d(a, b))  # [1, 2]
```

## 6. Best Practices

### Performance Optimization

- Use vectorized operations
- Avoid loops when possible
- Use appropriate data types
- Consider memory layout

### Numerical Stability

- Be aware of floating-point precision
- Use appropriate scaling
- Consider numerical conditioning
- Handle edge cases

### Common Pitfalls

- Ignoring numerical precision
- Not checking array shapes
- Forgetting to handle edge cases
- Not considering memory usage

---

This file covers NumPy mathematical operations and functions. For more advanced topics, refer to the other modules in this series.
