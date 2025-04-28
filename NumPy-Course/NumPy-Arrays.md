# 📊 NumPy Arrays

## 1. Array Indexing and Slicing

### Basic Indexing

```python
arr = np.array([1, 2, 3, 4, 5])

# Access single element
print(arr[0])    # 1
print(arr[-1])   # 5

# 2D array indexing
arr2d = np.array([[1, 2, 3], [4, 5, 6]])
print(arr2d[0, 1])  # 2
```

### Slicing

```python
# 1D array slicing
arr = np.array([1, 2, 3, 4, 5])
print(arr[1:4])    # [2, 3, 4]
print(arr[::2])    # [1, 3, 5]

# 2D array slicing
arr2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
print(arr2d[0:2, 1:3])  # [[2, 3], [5, 6]]
```

### Boolean Indexing

```python
arr = np.array([1, 2, 3, 4, 5])
mask = arr > 3
print(arr[mask])  # [4, 5]
```

## 2. Array Manipulation

### Reshaping Arrays

```python
arr = np.arange(6)
print(arr.reshape(2, 3))
# [[0, 1, 2],
#  [3, 4, 5]]
```

### Flattening Arrays

```python
arr2d = np.array([[1, 2, 3], [4, 5, 6]])
print(arr2d.flatten())  # [1, 2, 3, 4, 5, 6]
```

### Transposing Arrays

```python
arr = np.array([[1, 2, 3], [4, 5, 6]])
print(arr.T)
# [[1, 4],
#  [2, 5],
#  [3, 6]]
```

## 3. Array Operations

### Stacking Arrays

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

# Vertical stack
print(np.vstack((a, b)))
# [[1, 2, 3],
#  [4, 5, 6]]

# Horizontal stack
print(np.hstack((a, b)))  # [1, 2, 3, 4, 5, 6]
```

### Splitting Arrays

```python
arr = np.array([1, 2, 3, 4, 5, 6])
print(np.split(arr, 3))  # [array([1, 2]), array([3, 4]), array([5, 6])]
```

## 4. Array Broadcasting

### Basic Broadcasting

```python
a = np.array([1, 2, 3])
b = 2
print(a * b)  # [2, 4, 6]

# 2D broadcasting
a = np.array([[1, 2, 3], [4, 5, 6]])
b = np.array([1, 2, 3])
print(a + b)
# [[2, 4, 6],
#  [5, 7, 9]]
```

### Broadcasting Rules

1. Arrays must have compatible shapes
2. Dimensions are compared from right to left
3. Dimensions must be equal or one of them must be 1

## 5. Array Views and Copies

### Views

```python
arr = np.array([1, 2, 3, 4, 5])
view = arr[1:4]
view[0] = 10
print(arr)  # [1, 10, 3, 4, 5]
```

### Copies

```python
arr = np.array([1, 2, 3, 4, 5])
copy = arr[1:4].copy()
copy[0] = 10
print(arr)  # [1, 2, 3, 4, 5]
```

## 6. Array Iteration

### Basic Iteration

```python
arr = np.array([[1, 2, 3], [4, 5, 6]])
for row in arr:
    print(row)
# [1, 2, 3]
# [4, 5, 6]
```

### Using nditer

```python
arr = np.array([[1, 2, 3], [4, 5, 6]])
for x in np.nditer(arr):
    print(x)
# 1, 2, 3, 4, 5, 6
```

## 7. Best Practices

### Memory Management

- Use views when possible
- Create copies only when necessary
- Be aware of memory layout (C vs Fortran order)

### Performance Tips

- Use vectorized operations
- Avoid unnecessary copies
- Use appropriate data types
- Consider memory layout for large arrays

### Common Pitfalls

- Assuming operations create copies
- Not understanding broadcasting rules
- Mixing views and copies
- Ignoring memory layout

---

This file covers NumPy array operations and manipulation. For more advanced topics, refer to the other modules in this series.
