# 📊 Pandas Data Manipulation

## 1. Data Cleaning

### Handling Missing Data

```python
df = pd.DataFrame({'A': [1, np.nan, 3], 'B': [4, 5, np.nan]})

# Check for missing values
print(df.isnull())
print(df.isnull().sum())

# Drop missing values
df_drop = df.dropna()  # Drop rows with any NaN
df_drop_col = df.dropna(axis=1)  # Drop columns with any NaN

# Fill missing values
df_fill = df.fillna(0)  # Fill with 0
df_fill_mean = df.fillna(df.mean())  # Fill with mean
```

### Data Type Conversion

```python
# Convert to numeric
df['A'] = pd.to_numeric(df['A'], errors='coerce')

# Convert to datetime
df['date'] = pd.to_datetime(df['date'])

# Convert to category
df['category'] = df['category'].astype('category')
```

### String Operations

```python
df = pd.DataFrame({'text': ['Hello', 'World', 'Python']})

# String methods
df['lower'] = df['text'].str.lower()
df['upper'] = df['text'].str.upper()
df['length'] = df['text'].str.len()

# String contains
df['has_p'] = df['text'].str.contains('P')
```

## 2. Data Transformation

### Applying Functions

```python
df = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6]})

# Apply function to column
df['A_squared'] = df['A'].apply(lambda x: x**2)

# Apply function to each element
df = df.applymap(lambda x: x + 1)
```

### GroupBy Operations

```python
df = pd.DataFrame({
    'group': ['A', 'A', 'B', 'B'],
    'value': [1, 2, 3, 4]
})

# Group by and aggregate
grouped = df.groupby('group').agg({
    'value': ['sum', 'mean', 'count']
})

# Multiple aggregations
grouped = df.groupby('group').agg({
    'value': ['sum', 'mean', 'count']
})
```

### Pivot Tables

```python
df = pd.DataFrame({
    'date': ['2023-01-01', '2023-01-01', '2023-01-02'],
    'category': ['A', 'B', 'A'],
    'value': [1, 2, 3]
})

# Create pivot table
pivot = pd.pivot_table(
    df,
    values='value',
    index='date',
    columns='category',
    aggfunc='sum'
)
```

## 3. Data Operations

### Merging DataFrames

```python
df1 = pd.DataFrame({'key': ['A', 'B'], 'value1': [1, 2]})
df2 = pd.DataFrame({'key': ['A', 'B'], 'value2': [3, 4]})

# Inner join
merged = pd.merge(df1, df2, on='key')

# Left join
merged = pd.merge(df1, df2, on='key', how='left')

# Outer join
merged = pd.merge(df1, df2, on='key', how='outer')
```

### Concatenation

```python
df1 = pd.DataFrame({'A': [1, 2], 'B': [3, 4]})
df2 = pd.DataFrame({'A': [5, 6], 'B': [7, 8]})

# Vertical concatenation
concat = pd.concat([df1, df2], axis=0)

# Horizontal concatenation
concat = pd.concat([df1, df2], axis=1)
```

### Sorting

```python
df = pd.DataFrame({
    'A': [3, 1, 2],
    'B': [6, 4, 5]
})

# Sort by column
sorted_df = df.sort_values('A')

# Sort by multiple columns
sorted_df = df.sort_values(['A', 'B'])
```

## 4. Time Series Operations

### Date Range

```python
# Create date range
dates = pd.date_range('2023-01-01', periods=5, freq='D')

# Create DataFrame with dates
df = pd.DataFrame({
    'date': dates,
    'value': [1, 2, 3, 4, 5]
})
```

### Resampling

```python
df = pd.DataFrame({
    'date': pd.date_range('2023-01-01', periods=100, freq='D'),
    'value': np.random.randn(100)
})

# Resample to monthly
monthly = df.set_index('date').resample('M').mean()

# Resample to weekly
weekly = df.set_index('date').resample('W').sum()
```

### Rolling Windows

```python
df = pd.DataFrame({
    'value': np.random.randn(100)
})

# Rolling mean
df['rolling_mean'] = df['value'].rolling(window=5).mean()

# Rolling sum
df['rolling_sum'] = df['value'].rolling(window=5).sum()
```

## 5. Best Practices

### Data Cleaning

- Handle missing data appropriately
- Convert data types correctly
- Clean text data consistently
- Document data cleaning steps

### Performance Tips

- Use vectorized operations
- Avoid loops
- Use appropriate data types
- Consider memory usage

### Common Pitfalls

- Not handling missing data properly
- Using inefficient operations
- Not documenting transformations
- Ignoring data type conversions

---

This file covers data manipulation in Pandas. For more advanced topics, refer to the other modules in this series.
