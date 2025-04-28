# 📊 NumPy Advanced Topics

## 1. Advanced Broadcasting

### Complex Broadcasting Rules

```python
# Broadcasting with different dimensions
a = np.array([1, 2, 3])  # shape (3,)
b = np.array([[1], [2], [3]])  # shape (3, 1)
print(a + b)
# [[2, 3, 4],
#  [3, 4, 5],
#  [4, 5, 6]]
```

### Broadcasting with Multiple Dimensions

```python
# 3D broadcasting
a = np.ones((2, 3, 4))
b = np.array([1, 2, 3, 4])  # shape (4,)
print(a + b)  # shape (2, 3, 4)
```

## 2. Memory Management

### Memory Layout

```python
# C-contiguous array
arr_c = np.array([[1, 2, 3], [4, 5, 6]], order='C')
print(arr_c.flags['C_CONTIGUOUS'])  # True

# F-contiguous array
arr_f = np.array([[1, 2, 3], [4, 5, 6]], order='F')
print(arr_f.flags['F_CONTIGUOUS'])  # True
```

### Memory Views

```python
arr = np.array([1, 2, 3, 4, 5])
view = arr[1:4]  # Creates a view
view[0] = 10  # Modifies original array
print(arr)  # [1, 10, 3, 4, 5]
```

## 3. Performance Optimization

### Vectorization

```python
# Non-vectorized (slow)
arr = np.random.random(1000000)
result = np.zeros_like(arr)
for i in range(len(arr)):
    result[i] = arr[i] * 2

# Vectorized (fast)
result = arr * 2
```

### Using Numba

```python
from numba import jit

@jit(nopython=True)
def fast_function(arr):
    result = np.zeros_like(arr)
    for i in range(len(arr)):
        result[i] = arr[i] * 2
    return result
```

## 4. Advanced Array Manipulation

### Structured Arrays

```python
# Create structured array
dtype = [('name', 'S10'), ('age', 'i4'), ('weight', 'f4')]
data = np.array([('Alice', 25, 55.5), ('Bob', 30, 75.0)], dtype=dtype)

# Access fields
print(data['name'])  # [b'Alice' b'Bob']
print(data['age'])   # [25 30]
```

### Masked Arrays

```python
# Create masked array
arr = np.array([1, 2, 3, 4, 5])
mask = [True, False, True, False, True]
masked_arr = np.ma.masked_array(arr, mask=mask)
print(masked_arr)  # [-- 2 -- 4 --]
```

## 5. File I/O

### Binary Files

```python
# Save array to binary file
arr = np.array([1, 2, 3, 4, 5])
np.save('array.npy', arr)

# Load array from binary file
loaded_arr = np.load('array.npy')
```

### Text Files

```python
# Save array to text file
arr = np.array([[1, 2, 3], [4, 5, 6]])
np.savetxt('array.txt', arr, delimiter=',')

# Load array from text file
loaded_arr = np.loadtxt('array.txt', delimiter=',')
```

## 6. Advanced Indexing

### Boolean Indexing

```python
arr = np.array([1, 2, 3, 4, 5])
mask = arr > 3
print(arr[mask])  # [4, 5]
```

### Fancy Indexing

```python
arr = np.array([1, 2, 3, 4, 5])
indices = [0, 2, 4]
print(arr[indices])  # [1, 3, 5]
```

## 7. Universal Functions (ufuncs)

### Creating Custom ufuncs

```python
def my_func(x):
    return x * 2 + 1

my_ufunc = np.frompyfunc(my_func, 1, 1)
arr = np.array([1, 2, 3])
print(my_ufunc(arr))  # [3, 5, 7]
```

### ufunc Methods

```python
arr = np.array([1, 2, 3, 4, 5])

# Reduce
print(np.add.reduce(arr))  # 15

# Accumulate
print(np.add.accumulate(arr))  # [1, 3, 6, 10, 15]

# Outer
print(np.multiply.outer(arr, arr))
# [[1, 2, 3, 4, 5],
#  [2, 4, 6, 8, 10],
#  [3, 6, 9, 12, 15],
#  [4, 8, 12, 16, 20],
#  [5, 10, 15, 20, 25]]
```

## 8. Best Practices

### Performance Tips

- Use appropriate data types
- Minimize memory copies
- Use vectorized operations
- Consider memory layout
- Profile your code

### Memory Management

- Use views when possible
- Be aware of memory layout
- Monitor memory usage
- Clean up large arrays
- Use appropriate data types

### Common Pitfalls

- Ignoring memory layout
- Unnecessary copying
- Inefficient operations
- Memory leaks
- Type mismatches

---

This file covers advanced NumPy topics. For more basic concepts, refer to the other modules in this series.
