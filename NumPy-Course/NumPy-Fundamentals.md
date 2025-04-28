# 📊 NumPy Fundamentals

## 1. Introduction to NumPy

### What is NumPy?

- NumPy (Numerical Python) is a fundamental package for scientific computing in Python
- Provides support for large, multi-dimensional arrays and matrices
- Includes mathematical functions to operate on these arrays

### Why Use NumPy?

- Faster than regular Python lists
- More convenient array operations
- Better memory efficiency
- Extensive mathematical functions
- Foundation for many scientific Python packages

## 2. Installation and Setup

### Installing NumPy

```python
# Using pip
pip install numpy

# Using conda
conda install numpy
```

### Importing NumPy

```python
import numpy as np  # Standard convention
```

## 3. Basic Concepts

### NumPy Arrays vs Python Lists

```python
# Python list
python_list = [1, 2, 3, 4, 5]

# NumPy array
numpy_array = np.array([1, 2, 3, 4, 5])
```

### Key Differences

- NumPy arrays are homogeneous (same data type)
- NumPy arrays are more memory efficient
- NumPy arrays support vectorized operations
- NumPy arrays have fixed size

## 4. Array Properties

### Checking Array Properties

```python
arr = np.array([1, 2, 3, 4, 5])

# Shape
print(arr.shape)  # (5,)

# Data type
print(arr.dtype)  # int64

# Size
print(arr.size)   # 5

# Number of dimensions
print(arr.ndim)   # 1
```

### Common Data Types

- `int8`, `int16`, `int32`, `int64`
- `float16`, `float32`, `float64`
- `complex64`, `complex128`
- `bool`

## 5. Array Creation

### Basic Array Creation

```python
# 1D array
arr1d = np.array([1, 2, 3, 4, 5])

# 2D array
arr2d = np.array([[1, 2, 3], [4, 5, 6]])

# 3D array
arr3d = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])
```

### Special Arrays

```python
# Zeros array
zeros = np.zeros((3, 3))

# Ones array
ones = np.ones((2, 2))

# Identity matrix
identity = np.eye(3)

# Range array
range_arr = np.arange(0, 10, 2)  # [0, 2, 4, 6, 8]

# Linear space
linspace = np.linspace(0, 1, 5)  # [0, 0.25, 0.5, 0.75, 1]
```

## 6. Basic Operations

### Arithmetic Operations

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

# Addition
print(a + b)  # [5, 7, 9]

# Subtraction
print(a - b)  # [-3, -3, -3]

# Multiplication
print(a * b)  # [4, 10, 18]

# Division
print(b / a)  # [4, 2.5, 2]
```

### Scalar Operations

```python
arr = np.array([1, 2, 3])

# Add scalar
print(arr + 2)  # [3, 4, 5]

# Multiply by scalar
print(arr * 2)  # [2, 4, 6]
```

## 7. Best Practices

### Memory Efficiency

- Use appropriate data types
- Avoid unnecessary copies
- Use in-place operations when possible

### Performance Tips

- Use vectorized operations instead of loops
- Pre-allocate arrays when possible
- Use built-in NumPy functions

### Common Pitfalls

- Mixing NumPy arrays with Python lists
- Not specifying data types
- Creating unnecessary copies

---

This file covers the fundamental concepts of NumPy. For more advanced topics, refer to the other modules in this series.
