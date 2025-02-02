# Comprehensive Revision Notes on Pandas in Python

## Introduction
Pandas is a powerful data manipulation library in Python, providing data structures and functions for efficiently handling structured data. This document covers key Pandas operations including sorting, joins, handling missing values, applying functions, grouping data, and working with timestamps.

## 1. Importing Required Libraries
### Definition:
Importing libraries is the first step before using Pandas functionalities.

```python
import pandas as pd
import os
```
These libraries are essential for data manipulation (`pandas`) and handling file paths (`os`).

## 2. Sorting DataFrames
### Definition:
Sorting is the process of arranging data in a specified order based on column values.

### Key Points:
- `sort_values(by=column_name)` sorts a DataFrame by a specified column.
- `ascending=False` sorts in descending order.
- Multiple columns can be used for sorting.
- The index can be reset after sorting.

### Examples:
```python
df.sort_values(by='duration', inplace=True)
```
This sorts the `df` DataFrame based on the `duration` column in ascending order.

```python
df.sort_values(by='duration', ascending=False, inplace=True)
```
Sorting `duration` in descending order.

```python
df.sort_values(by=['genre', 'star_rating'], ascending=False, inplace=True)
```
Sorting by multiple columns: first by `genre` and then by `star_rating` in descending order.

### Resetting Index:
```python
df.reset_index(drop=True, inplace=True)
```
The `drop=True` parameter ensures the old index is discarded.

### Sorting with Multiple Conditions:
```python
df.sort_values(by=['genre', 'star_rating', 'duration'], ascending=[True, False, True], inplace=True)
```
This sorts by `genre` (ascending), `star_rating` (descending), and `duration` (ascending).

## 3. Joining DataFrames
### Definition:
Joining is the process of merging two or more DataFrames based on a common key.

### Types of Joins:
- **One-to-One Join**: Matching rows based on a common column.
- **Many-to-One Join**: Merging a DataFrame with unique keys into one with repeated keys.
- **Many-to-Many Join**: Matching multiple rows from both DataFrames.

### Example of `merge()`:
```python
left = pd.DataFrame({'key': ['K0', 'K1', 'K2', 'K3'],
                     'A': ['A0', 'A1', 'A2', 'A3'],
                     'B': ['B0', 'B1', 'B2', 'B3']})

right = pd.DataFrame({'key': ['K0', 'K11', 'K2', 'K3'],
                      'C': ['C0', 'C1', 'C2', 'C3'],
                      'D': ['D0', 'D1', 'D2', 'D3']})

result = pd.merge(left, right, on='key')
print(result)
```

### Different Merge Types:
```python
pd.merge(df1, df2, how='inner', on='city')
pd.merge(df1, df2, how='left', on='city')
pd.merge(df1, df2, how='right', on='city')
pd.merge(df1, df2, how='outer', on='city', indicator=True)
```
The `indicator=True` parameter adds a column showing the origin of each row.

## 4. Handling Missing Values
### Definition:
Missing values occur when data is not available in a dataset. Pandas provides methods to handle them efficiently.

### Functions for Handling Missing Data:
- **`isnull()`**: Detects missing values.
- **`notnull()`**: Detects non-missing values.
- **`dropna()`**: Drops missing values.
- **`fillna()`**: Fills missing values with specified values.
- **`replace()`**: Replaces missing values with alternative data.
- **`interpolate()`**: Estimates missing values using interpolation.

### Example:
```python
df.isnull().sum()  # Count NaN values per column
```

Filling missing values:
```python
df.fillna(0, inplace=True)  # Replace NaN with 0
df.fillna(df.mean(), inplace=True)  # Fill with column mean
```

Forward and backward filling:
```python
df.fillna(method='ffill')  # Forward fill
df.fillna(method='bfill')  # Backward fill
```

Dropping missing values:
```python
df.dropna(inplace=True)  # Remove rows with missing values
```

## 5. Applying Functions
### Definition:
Applying functions allows transformations and custom computations on DataFrame columns.

### Example:
```python
def categorize(num):
    if num < 2000:
        return "Low"
    elif num < 4000:
        return "Normal"
    else:
        return "High"

df['Category'] = df['Balance'].apply(categorize)
```

Lambda function example:
```python
df['TEMP'] = df['Second Score'].apply(lambda x: "High" if x > 50 else "Low")
```

## 6. Grouping Data
### Definition:
Grouping allows aggregation of data based on categorical variables.

### Example:
```python
df.groupby('genre')['star_rating'].mean()
```
This calculates the average `star_rating` for each `genre`.

## 7. TimeStamp Handling
### Definition:
Timestamps help in working with time-series data for filtering and transformations.

### Example:
```python
df['date_column'] = pd.to_datetime(df['date_column'])  # Convert to datetime
```
Filtering by date range:
```python
df[df['date_column'] > '2022-01-01']
```
Extracting components:
```python
df['Year'] = df['date_column'].dt.year
df['Month'] = df['date_column'].dt.month
df['Day'] = df['date_column'].dt.day
```

## 8. Concatenation of DataFrames
### Definition:
Concatenation is used to stack DataFrames vertically or horizontally.

### Example:
```python
df_list = [df1, df2, df3]
result = pd.concat(df_list)
```
This stacks `df1`, `df2`, and `df3` vertically.

## Summary
- **Sorting**: `sort_values()` for ordering DataFrames.
- **Joining**: `merge()` and `join()` for relational operations.
- **Handling Missing Values**: `isnull()`, `fillna()`, `dropna()`.
- **Apply Functions**: `apply()` for transforming data.
- **Grouping**: `groupby()` for aggregations.
- **Timestamps**: `pd.to_datetime()` for handling dates.
- **Concatenation**: `concat()` for combining DataFrames.

These concepts form the foundation for efficient data manipulation in Pandas.

---

