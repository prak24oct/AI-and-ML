# 🚀 Pandas Applications

This file covers practical applications of Pandas in data analysis, data cleaning, and data visualization.

## 📊 Data Analysis Applications

### 1. Exploratory Data Analysis (EDA)

```python
import pandas as pd
import numpy as np

# Load data
df = pd.read_csv('data.csv')

# Basic statistics
summary = df.describe()
correlation_matrix = df.corr()

# Data profiling
def data_profile(df):
    profile = pd.DataFrame({
        'dtype': df.dtypes,
        'missing_values': df.isnull().sum(),
        'unique_values': df.nunique(),
        'memory_usage': df.memory_usage(deep=True)
    })
    return profile

# Outlier detection
def detect_outliers(df, column):
    Q1 = df[column].quantile(0.25)
    Q3 = df[column].quantile(0.75)
    IQR = Q3 - Q1
    return df[(df[column] < Q1 - 1.5*IQR) | (df[column] > Q3 + 1.5*IQR)]
```

### 2. Time Series Analysis

```python
# Time series operations
df['date'] = pd.to_datetime(df['date'])
df.set_index('date', inplace=True)

# Resampling
daily_data = df.resample('D').mean()
monthly_data = df.resample('M').sum()

# Rolling statistics
df['rolling_mean'] = df['value'].rolling(window=7).mean()
df['rolling_std'] = df['value'].rolling(window=7).std()

# Time-based features
df['day_of_week'] = df.index.dayofweek
df['month'] = df.index.month
df['quarter'] = df.index.quarter
```

## 🧹 Data Cleaning Applications

### 1. Missing Data Handling

```python
# Identify missing values
missing_data = df.isnull().sum()

# Imputation strategies
def impute_missing(df):
    # Mean imputation for numerical columns
    numerical_cols = df.select_dtypes(include=[np.number]).columns
    df[numerical_cols] = df[numerical_cols].fillna(df[numerical_cols].mean())

    # Mode imputation for categorical columns
    categorical_cols = df.select_dtypes(include=['object']).columns
    df[categorical_cols] = df[categorical_cols].fillna(df[categorical_cols].mode().iloc[0])

    return df

# Forward/backward fill
df = df.fillna(method='ffill')  # Forward fill
df = df.fillna(method='bfill')  # Backward fill
```

### 2. Data Transformation

```python
# Feature engineering
def create_features(df):
    # Create interaction terms
    df['interaction'] = df['feature1'] * df['feature2']

    # Create polynomial features
    df['feature1_squared'] = df['feature1'] ** 2

    # Create ratio features
    df['ratio'] = df['feature1'] / df['feature2']

    return df

# Encoding categorical variables
def encode_categorical(df):
    # One-hot encoding
    df_encoded = pd.get_dummies(df, columns=['category'])

    # Label encoding
    from sklearn.preprocessing import LabelEncoder
    le = LabelEncoder()
    df['encoded_category'] = le.fit_transform(df['category'])

    return df_encoded
```

## 📈 Data Visualization Applications

### 1. Statistical Plots

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Distribution plots
def plot_distributions(df):
    numerical_cols = df.select_dtypes(include=[np.number]).columns
    for col in numerical_cols:
        plt.figure(figsize=(10, 6))
        sns.histplot(data=df, x=col, kde=True)
        plt.title(f'Distribution of {col}')
        plt.show()

# Correlation heatmap
def plot_correlation(df):
    plt.figure(figsize=(12, 8))
    sns.heatmap(df.corr(), annot=True, cmap='coolwarm')
    plt.title('Correlation Heatmap')
    plt.show()

# Box plots
def plot_boxplots(df):
    numerical_cols = df.select_dtypes(include=[np.number]).columns
    for col in numerical_cols:
        plt.figure(figsize=(10, 6))
        sns.boxplot(data=df, y=col)
        plt.title(f'Box Plot of {col}')
        plt.show()
```

### 2. Time Series Visualization

```python
# Time series plots
def plot_time_series(df):
    plt.figure(figsize=(15, 7))
    plt.plot(df.index, df['value'], label='Original')
    plt.plot(df.index, df['rolling_mean'], label='Rolling Mean')
    plt.title('Time Series Analysis')
    plt.xlabel('Date')
    plt.ylabel('Value')
    plt.legend()
    plt.show()

# Seasonal decomposition
from statsmodels.tsa.seasonal import seasonal_decompose
def decompose_time_series(df):
    decomposition = seasonal_decompose(df['value'], period=12)
    decomposition.plot()
    plt.show()
```

## 🎯 Best Practices

1. **Data Loading**

   - Use appropriate data types
   - Specify column types during loading
   - Handle missing values early

2. **Memory Management**

   - Use appropriate data types
   - Downcast numerical columns
   - Remove unnecessary columns

3. **Performance Optimization**

   - Use vectorized operations
   - Avoid iterating over rows
   - Use efficient data structures

4. **Code Organization**
   - Create reusable functions
   - Document data transformations
   - Maintain data lineage

## ⚠️ Common Pitfalls

1. **Memory Issues**

   - Loading large datasets
   - Creating unnecessary copies
   - Not using appropriate data types

2. **Performance**

   - Using loops instead of vectorized operations
   - Not using categorical data types
   - Excessive memory usage

3. **Data Quality**
   - Not handling missing values properly
   - Incorrect data type conversions
   - Not validating data transformations

## 📚 Additional Resources

- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [Pandas User Guide](https://pandas.pydata.org/docs/user_guide/index.html)
- [Pandas Cookbook](https://pandas.pydata.org/docs/user_guide/cookbook.html)
- [Pandas Tutorials](https://pandas.pydata.org/docs/getting_started/tutorials.html)
