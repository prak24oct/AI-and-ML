### Comprehensive Revision Notes: **NumPy**

---

### **What is NumPy?**

NumPy, short for **Numerical Python**, is a powerful library in Python used for numerical computations, particularly involving arrays. It provides an efficient and convenient way to handle large datasets and perform mathematical operations on them.

#### **Key Features of NumPy:**
1. **Array-Oriented Computation:** Designed to perform computations on arrays, making it faster than Python's native data structures.
2. **Handles Large Data:** Efficiently processes large datasets due to its underlying C implementation.
3. **Rich Mathematical Operations:** Includes a vast array of methods for mathematical, statistical, and logical operations.

---

### **Why Use NumPy?**
- **Performance:** NumPy arrays (`ndarray`) are faster and more memory-efficient than Python lists.
- **Convenience:** Simplifies mathematical operations on large datasets.
- **Versatility:** Supports multi-dimensional arrays and a variety of mathematical functions.
- **Integration:** Works seamlessly with other scientific libraries like SciPy, Matplotlib, and pandas.

---

### **Creating NumPy Arrays**

#### **1. Using Lists or Tuples**
You can create NumPy arrays from Python lists or tuples using the `np.array()` function.

**Example:**
```python
import numpy as np

# From a list
a = [1, 2, 3, 4, 5]
array = np.array(a)
print(array, type(array))  # Output: [1 2 3 4 5] <class 'numpy.ndarray'>

# From a tuple
array_from_tuple = np.array((1, 2, 3))
print(array_from_tuple)  # Output: [1 2 3]
```

**Multidimensional Array Example:**
```python
a = [[1, 2, 3, 4], [3, 4, 5, 6], [5, 7, 8, 9]]
array = np.array(a)
print(array.shape)  # Output: (3, 4)
```

---

### **Array Attributes**

1. **Shape:** Represents the dimensions of the array.
   ```python
   print(array.shape)  # Output: (3, 4)
   ```

2. **Size:** Total number of elements in the array.
   ```python
   print(array.size)  # Output: 12
   ```

3. **Dimensions:** Number of dimensions of the array.
   ```python
   print(array.ndim)  # Output: 2
   ```

---

### **Types of Arrays**

#### **1. Scalars, Vectors, and Matrices**
- **Scalar:** A single value (0-dimensional).
- **Vector:** A 1D array (e.g., `[1, 2, 3]`).
- **Matrix:** A 2D array (e.g., `[[1, 2], [3, 4]]`).

#### **2. Higher Dimensions**
- **3D Array:** Each row contains a 2D array.
- **4D Array:** Each row contains a 3D array.

---

### **Special Array Creation Methods**

#### **1. `np.linspace()`**
Creates an array of evenly spaced values between a start and end point.

**Syntax:** `np.linspace(start, end, num_divisions)`

**Example:**
```python
array = np.linspace(1, 20, 10)
print(array)  # Output: [1.   3.11 5.22 ... 18.89 20.]
```

#### **2. `np.zeros()`**
Creates an array filled with zeros.

**Example:**
```python
zeros_array = np.zeros((3, 4))
print(zeros_array)
```

#### **3. `np.zeros_like()`**
Creates an array of zeros with the same shape as another array.

**Example:**
```python
data = np.linspace(0, 10, 5)
zeros_like_data = np.zeros_like(data)
print(zeros_like_data)  # Output: [0. 0. 0. 0. 0.]
```

#### **4. `np.ones()`**
Creates an array filled with ones.

**Example:**
```python
ones_array = np.ones((2, 3))
print(ones_array)
```

#### **5. `np.ones_like()`**
Creates an array of ones with the same shape as another array.

**Example:**
```python
array = np.array([[1, 2], [3, 4]])
ones_like_array = np.ones_like(array)
print(ones_like_array)
```

#### **6. `np.eye()`**
Creates an identity matrix.

**Example:**
```python
identity_matrix = np.eye(3)
print(identity_matrix)
```

#### **7. `np.random.random_integers()`**
Generates random integers within a specified range.

**Example:**
```python
random_array = np.random.random_integers(10000, 99999, size=5)
print(random_array)
```

---

### **Reshaping Arrays**

The `reshape()` method changes the shape of an array without altering its data.

**Example:**
```python
data = np.arange(10)
reshaped_data = data.reshape(2, 5)
print(reshaped_data)
```

---

### **Dimensionality Examples**

1. **1D Array:**
   ```python
   data = np.array([1, 2, 3, 4])
   print(data.ndim)  # Output: 1
   ```

2. **2D Array:**
   ```python
   data = np.array([[1, 2], [3, 4]])
   print(data.ndim)  # Output: 2
   ```

3. **3D Array:**
   ```python
   data = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])
   print(data.ndim)  # Output: 3
   ```

---

### **Practical Applications of NumPy**
1. **Data Preprocessing:** Used for handling numerical datasets in machine learning pipelines.
2. **Mathematical Computations:** Simplifies operations like matrix multiplication, finding determinants, and solving linear equations.
3. **Scientific Simulations:** Used in fields like physics and engineering for simulations.

---

### **Key Resources**
- [NumPy Documentation](https://numpy.org/doc/)
- [NumPy Cheat Sheet](https://www.datacamp.com/cheat-sheet/numpy-cheat-sheet)

By understanding and applying these concepts, you can leverage NumPy to efficiently handle and process numerical data in Python.