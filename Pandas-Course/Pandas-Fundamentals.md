# 📊 Pandas Fundamentals

## 1. Introduction to Pandas

### What is Pandas?

- Pandas is a powerful data manipulation and analysis library for Python
- Built on top of NumPy
- Provides data structures and operations for manipulating numerical tables and time series

### Key Features

- DataFrame and Series data structures
- Data alignment and integrated handling of missing data
- Flexible reshaping and pivoting of datasets
- Label-based slicing, indexing, and subsetting
- Robust IO tools for loading data from various sources

## 2. Installation and Setup

### Installing Pandas

```python
# Using pip
pip install pandas

# Using conda
conda install pandas
```

### Importing Pandas

```python
import pandas as pd  # Standard convention
```

## 3. Series

### Creating Series

```python
# From list
s = pd.Series([1, 3, 5, 7, 9])

# From dictionary
s = pd.Series({'a': 1, 'b': 2, 'c': 3})

# With custom index
s = pd.Series([1, 2, 3], index=['a', 'b', 'c'])
```

### Series Operations

```python
s1 = pd.Series([1, 2, 3])
s2 = pd.Series([4, 5, 6])

# Arithmetic operations
print(s1 + s2)  # [5, 7, 9]
print(s1 * s2)  # [4, 10, 18]

# Statistical operations
print(s1.mean())  # 2.0
print(s1.std())   # 0.816
```

## 4. DataFrames

### Creating DataFrames

```python
# From dictionary
df = pd.DataFrame({
    'A': [1, 2, 3],
    'B': ['a', 'b', 'c'],
    'C': [1.1, 2.2, 3.3]
})

# From list of dictionaries
data = [{'A': 1, 'B': 'a'}, {'A': 2, 'B': 'b'}]
df = pd.DataFrame(data)

# From NumPy array
import numpy as np
arr = np.array([[1, 2, 3], [4, 5, 6]])
df = pd.DataFrame(arr, columns=['A', 'B', 'C'])
```

### DataFrame Properties

```python
df = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6]})

# Shape
print(df.shape)  # (3, 2)

# Columns
print(df.columns)  # Index(['A', 'B'], dtype='object')

# Index
print(df.index)  # RangeIndex(start=0, stop=3, step=1)

# Data types
print(df.dtypes)
# A    int64
# B    int64
# dtype: object
```

## 5. Basic Operations

### Selection and Indexing

```python
df = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6]})

# Column selection
print(df['A'])  # Series of column A

# Row selection
print(df.loc[0])  # First row
print(df.iloc[0])  # First row by position

# Multiple columns
print(df[['A', 'B']])

# Slicing
print(df[0:2])  # First two rows
```

### Filtering

```python
df = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6]})

# Boolean indexing
print(df[df['A'] > 1])

# Multiple conditions
print(df[(df['A'] > 1) & (df['B'] < 6)])
```

## 6. Data Input/Output

### Reading Data

```python
# CSV files
df = pd.read_csv('data.csv')

# Excel files
df = pd.read_excel('data.xlsx')

# SQL databases
import sqlite3
conn = sqlite3.connect('database.db')
df = pd.read_sql('SELECT * FROM table', conn)
```

### Writing Data

```python
# To CSV
df.to_csv('output.csv', index=False)

# To Excel
df.to_excel('output.xlsx', index=False)

# To SQL
df.to_sql('table', conn, if_exists='replace')
```

## 7. Best Practices

### Data Types

- Use appropriate data types for columns
- Convert categorical data to category type
- Use datetime for date/time data
- Consider memory usage with large datasets

### Performance Tips

- Use vectorized operations
- Avoid iterating over rows
- Use appropriate indexing methods
- Consider memory usage

### Common Pitfalls

- Not handling missing data properly
- Using loops instead of vectorized operations
- Not setting appropriate data types
- Ignoring memory usage with large datasets

---

This file covers the fundamental concepts of Pandas. For more advanced topics, refer to the other modules in this series.
