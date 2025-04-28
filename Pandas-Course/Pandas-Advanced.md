# 📊 Pandas Advanced Topics

## 1. Advanced Indexing

### MultiIndex

```python
# Create MultiIndex
index = pd.MultiIndex.from_tuples([
    ('A', 1), ('A', 2),
    ('B', 1), ('B', 2)
], names=['letter', 'number'])

df = pd.DataFrame({
    'value': [1, 2, 3, 4]
}, index=index)

# Access MultiIndex
print(df.loc['A'])  # All rows with letter 'A'
print(df.loc[('A', 1)])  # Specific row
```

### Advanced Selection

```python
df = pd.DataFrame({
    'A': [1, 2, 3, 4],
    'B': ['a', 'b', 'c', 'd']
})

# Query method
filtered = df.query('A > 2')

# Where method
masked = df.where(df['A'] > 2)

# Select by data type
numeric = df.select_dtypes(include=['number'])
```

## 2. Performance Optimization

### Memory Usage

```python
df = pd.DataFrame({
    'A': [1, 2, 3],
    'B': ['a', 'b', 'c']
})

# Check memory usage
print(df.memory_usage())

# Optimize data types
df['A'] = df['A'].astype('int8')
df['B'] = df['B'].astype('category')
```

### Vectorized Operations

```python
# Slow: Using apply
df['result'] = df.apply(lambda row: row['A'] * row['B'], axis=1)

# Fast: Vectorized operation
df['result'] = df['A'] * df['B']
```

### Using Numba

```python
from numba import jit

@jit(nopython=True)
def custom_function(x):
    return x * 2 + 1

df['result'] = custom_function(df['A'].values)
```

## 3. Custom Functions

### Custom Aggregations

```python
def custom_agg(x):
    return {
        'mean': x.mean(),
        'std': x.std(),
        'count': x.count()
    }

df = pd.DataFrame({
    'group': ['A', 'A', 'B', 'B'],
    'value': [1, 2, 3, 4]
})

result = df.groupby('group')['value'].agg(custom_agg)
```

### Custom Transformations

```python
def custom_transform(x):
    return (x - x.mean()) / x.std()

df = pd.DataFrame({
    'A': [1, 2, 3, 4, 5]
})

df['normalized'] = df['A'].transform(custom_transform)
```

## 4. Advanced Data Operations

### Window Functions

```python
df = pd.DataFrame({
    'value': np.random.randn(100)
})

# Expanding window
df['expanding_mean'] = df['value'].expanding().mean()

# Rolling window with custom function
def custom_roll(x):
    return np.sum(x) / len(x)

df['custom_roll'] = df['value'].rolling(5).apply(custom_roll)
```

### Time Series Analysis

```python
df = pd.DataFrame({
    'date': pd.date_range('2023-01-01', periods=100, freq='D'),
    'value': np.random.randn(100)
})

# Time-based operations
df['day_of_week'] = df['date'].dt.dayofweek
df['month'] = df['date'].dt.month

# Time zone handling
df['date'] = df['date'].dt.tz_localize('UTC')
df['date'] = df['date'].dt.tz_convert('US/Eastern')
```

## 5. Advanced Visualization

### Custom Plotting

```python
import matplotlib.pyplot as plt

df = pd.DataFrame({
    'x': range(10),
    'y': np.random.randn(10)
})

# Custom plot function
def custom_plot(df):
    fig, ax = plt.subplots()
    ax.plot(df['x'], df['y'])
    ax.set_title('Custom Plot')
    return fig

custom_plot(df)
```

### Interactive Visualization

```python
import plotly.express as px

df = pd.DataFrame({
    'x': range(10),
    'y': np.random.randn(10),
    'category': ['A', 'B'] * 5
})

# Interactive plot
fig = px.scatter(df, x='x', y='y', color='category')
fig.show()
```

## 6. Advanced IO Operations

### Reading Large Files

```python
# Read in chunks
chunk_size = 1000
for chunk in pd.read_csv('large_file.csv', chunksize=chunk_size):
    process_chunk(chunk)

# Use dask for parallel processing
import dask.dataframe as dd
df = dd.read_csv('large_file.csv')
```

### Custom File Formats

```python
# Read from custom format
def custom_reader(file_path):
    with open(file_path, 'r') as f:
        data = f.read().split('\n')
    return pd.DataFrame({'data': data})

df = custom_reader('custom_file.txt')
```

## 7. Best Practices

### Performance Optimization

- Use appropriate data types
- Minimize memory copies
- Use vectorized operations
- Consider parallel processing
- Profile your code

### Memory Management

- Monitor memory usage
- Clean up large DataFrames
- Use appropriate data types
- Consider chunked processing
- Use garbage collection

### Common Pitfalls

- Not optimizing data types
- Using inefficient operations
- Not handling memory properly
- Ignoring performance bottlenecks
- Not documenting custom functions

---

This file covers advanced Pandas topics. For more basic concepts, refer to the other modules in this series.
