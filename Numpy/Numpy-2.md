Here are the detailed and comprehensive revision notes based on the provided Python raw notes. The notes cover concepts, examples, and explanations in depth to serve as an effective study resource.

---

## **NumPy Basics and Array Manipulation**

### **Introduction to NumPy**
- **NumPy**: A powerful library for numerical computing in Python.
- **Documentation**: Access the NumPy docstring with `print(np.__doc__)`.
- **Creating Arrays**:
  - `np.arange(start, stop)`: Creates an array with evenly spaced values within a range.
    ```python
    data = np.arange(0, 30)
    ```
- **Reshaping Arrays**:
  - Use `.reshape(rows, columns)` to change the shape of an array without altering its data.
    ```python
    data.reshape(2, 5)
    data.reshape(-1, 6).shape  # Automatically calculates rows for 6 columns
    ```

### **Dimensions in Arrays**
- **1D Array**: A vector (e.g., `[1, 2, 3]`).
- **2D Array**: A group of 1D arrays (e.g., a matrix).
- **3D Array**: A collection of 2D arrays.
  ```python
  z = data.reshape(2, 3, 5)  # A 3D array with dimensions (2, 3, 5)
  ```

### **Array Properties**
- `.ndim`: Number of dimensions.
- `.size`: Total number of elements.
- `.shape`: Tuple representing the array's dimensions.
  ```python
  z.ndim, z.size, z.shape
  ```

---

## **Random Number Generation**

### **Single and Multiple Random Numbers**
- `np.random.rand()`: Generates random floats in the range [0, 1).
  ```python
  np.random.rand(5, 3)  # Generates a 2D array with random numbers
  ```

### **Standard Normal Distribution**
- `np.random.randn(shape)`: Generates samples from the standard normal distribution.
  ```python
  z = np.random.randn(100000)
  ```
- Visualize the distribution:
  ```python
  import seaborn as sns
  from scipy.stats import norm
  sns.distplot(z, fit=norm, kde=False)
  ```

### **Random Integers**
- `np.random.randint(low, high, size)`: Generates random integers in a specified range.
  ```python
  np.random.randint(10, 20, size=(4, 4))
  ```

### **Uniform Distribution**
- `np.random.uniform(low, high, size)`: Generates samples from a uniform distribution.
  ```python
  np.random.uniform(10, 100, (10, 10))
  ```

---

## **Array Indexing and Slicing**

### **Basic Indexing**
- Access elements using indices:
  ```python
  a[0, 1]  # Element at row 0, column 1
  a[-1, 0]  # Last row, first column
  ```

### **Advanced Indexing**
- 3D Array Indexing:
  ```python
  a3[1, :, 0]  # All rows in the 2nd group, column 0
  a3[0, 1, 0]  # Element at (0, 1, 0)
  ```

### **Slicing**
- General format: `array[start:stop:step]`
  ```python
  a[:, 1:5:2]  # Columns 1, 3 for all rows
  ```

---

## **Array Creation**

### **Special Arrays**
- **Zeros**: Create arrays filled with zeros.
  ```python
  np.zeros((2, 2))
  ```
- **Full**: Create arrays filled with a specific value.
  ```python
  np.full((5, 5), 100, dtype='int')
  ```
- **Identity Matrix**:
  ```python
  a = np.identity(5, dtype='float')
  np.fill_diagonal(a, 2.55)
  ```

---

## **Sorting and Statistical Operations**

### **Sorting**
- Sort arrays along different axes:
  ```python
  np.sort(arr, axis=0)  # Column-wise sorting
  np.sort(arr, axis=1)  # Row-wise sorting
  ```

### **Finding Extremes**
- `np.argmax(array)`: Index of the largest value.
- `np.argmin(array)`: Index of the smallest value.
  ```python
  np.argmax(arr), np.argmin(arr)
  ```

### **Statistics**
- **Sum and Mean**:
  ```python
  data.sum()  # Total sum
  data.mean()  # Average
  ```
- Row-wise and column-wise operations:
  ```python
  np.mean(data, axis=1)  # Row-wise mean
  np.mean(data, axis=0)  # Column-wise mean
  ```

---

## **Array Manipulation**

### **Concatenation**
- Combine arrays along different axes:
  ```python
  np.concatenate((a, b), axis=0)  # Vertically stack arrays
  np.concatenate((a, b), axis=1)  # Horizontally stack arrays
  ```

### **Boolean Indexing**
- Extract elements based on conditions:
  ```python
  a[(a > 10) & (a < 20)]
  divisible_by_2 = a[a % 2 == 0]
  ```

### **Swapping Rows**
- Reverse row order:
  ```python
  data[::-1]
  ```

---

## **Additional Notes**
- **Empty Arrays**: Arrays with uninitialized values.
  ```python
  np.empty((10, 5))
  ```
- **Stacking**:
  - Horizontal stacking (`np.hstack`).
  - Vertical stacking (`np.vstack`).

These notes provide an in-depth overview of NumPy operations, ensuring clarity and comprehensive coverage of the subject.