Here are your notes on **Pandas in Python** in a structured format:  

---

# **Pandas - Python**  
Pandas is a Python module that makes data science easy and effective. It provides powerful data structures for data manipulation and analysis.

---

## **Types of Data**  
1. **Structured Data** → Data in tabular format (e.g., databases, spreadsheets).  
2. **Semi-Structured Data** → JSON, YAML, dictionaries.  
3. **Unstructured Data** → Images, videos, audio, graph databases, QR codes.

---

## **Pandas Data Structures**  
Pandas has three primary data structures:  

1. **Series** → 1D (Single column)  
2. **DataFrame** → 2D (Table)  
3. **Panel** → 3D (Deprecated in Pandas 1.0)

### **Hierarchy of Data Structures**  
- **Series** is the most granular part.  
- **Multiple Series** form a **DataFrame** (2D Table).  
- **Multiple DataFrames** form a **Panel** (3D, now deprecated).  

---

## **Creating a Pandas Series**  

### **1. Using a List**
```python
import pandas as pd

football_data = ['Barcelona', 'PSG', 'ManU', 'Chelsea', 'ManCity', 'Bayern']
data = pd.Series(football_data)
print(data)
```

### **2. Using an Array**
```python
import numpy as np

data = pd.Series(np.arange(3) * 34, index=['Barca', 'Messi', 'Afsan'])
print(data)
```

### **3. Using a Dictionary**
```python
employee_data = {'emp1': 'Afsan', 'emp2': 'Raja', 'emp3': 'Sridevi'}
data = pd.Series(employee_data)
print(data)
```

---

## **Indexing & Slicing in Series**  

### **Indexing Types**
- **Zero-based Indexing**  
- **Custom Indexing**  

```python
data = pd.Series(football_data, index=['a', 'b', 'c', 'd', 'e', 'f'])
print(data['e'])  # Access by custom index
print(data[-3])   # Access by negative index
```

### **Slicing**
- **Zero-based Indexing** → Start (Inclusive), Stop (Exclusive).  
- **Custom Indexing** → Both Start & Stop are Inclusive.  

```python
print(data[5:0:-1])  # Reverse slicing
print(data['e':'a':-1])  # Reverse slicing with custom index
```

---

## **Creating a DataFrame**  

### **1. From a Dictionary**
```python
df_dict = {
    'Year': [1990, 1994, 1998, 2002],
    'Country': ['Italy', 'USA', 'France', 'Japan'],
    'Winner': ['Germany', 'Brazil', 'France', 'Brazil'],
    'GoalScored': [115, 141, 171, 161]
}

df = pd.DataFrame(df_dict)
print(df)
```

### **2. From a List of Tuples**
```python
df_lotuples = [
    (2002, 'Japan', 'Brazil', 161),
    (2006, 'Germany', 'Italy', 147),
    (2010, 'South Africa', 'Spain', 145),
    (2014, 'Brazil', 'Germany', 171)
]

df = pd.DataFrame(df_lotuples, columns=['Year', 'Country', 'Winner', 'GoalScored'])
print(df)
```

### **3. From a List of Dictionaries**
```python
df_lodict = [
    {'Year': 2002, 'HostCountry': 'Japan', 'Winner': 'Brazil'},
    {'Year': 2006, 'HostCountry': 'Germany', 'Winner': 'Italy'},
    {'Year': 2010, 'HostCountry': 'South Africa', 'Winner': 'Spain'},
    {'Year': 2014, 'HostCountry': 'Brazil', 'Winner': 'Germany'}
]

df = pd.DataFrame(df_lodict)
print(df)
```

---

## **Reading Data from CSV**
```python
path = 'C:/Users/navee/Documents/Python Collateral/DataSets/weather.csv'
df = pd.read_csv(path)
print(df.head())  # First 5 rows
print(df.shape)   # Shape of DataFrame
print(df.info())  # Summary of DataFrame
print(df.describe())  # Statistical summary
```

---

## **Selecting Columns in DataFrame**
```python
# Selecting a single column
print(df['stoptime'])

# Selecting multiple columns
cols = ['stoptime', 'bikeid', 'tripduration']
print(df[cols])

# Alternative method
print(df[['stoptime', 'bikeid', 'tripduration']].head(2))
```

---

## **Slicing in DataFrames**  

### **1. Normal Slicing (Row-wise)**
```python
# Syntax: df[start:stop:step]
print(df[0:5])  # First 5 rows
print(df[6:0:-2])  # Reverse slicing
```

### **2. Using `loc` (Label-based Indexing)**
```python
# Select rows based on custom index
new_df = df[0:6]
new_df.index = ['row1', 'row2', 'row3', 'row4', 'row5', 'row6']
print(new_df.loc['row1':'row5'])

# Select specific rows and columns
print(new_df.loc[['row1', 'row3'], ['tripduration', 'bikeid']])

# Filter rows based on conditions
print(new_df.loc[new_df['bikeid'] > 30000])
print(new_df.loc[(new_df['bikeid'] > 30000) & (new_df['usertype'] == 'Subscriber')])
```

### **3. Using `iloc` (Position-based Indexing)**
```python
# Syntax: df.iloc[row_start:row_stop:step, col_start:col_stop:step]
print(df.iloc[0:5, 1:3])  # Select rows 0-4 and columns 1-2
print(df.iloc[:, [0, 2, 4]])  # Select all rows and specific columns
```

---

## **Basic DataFrame Operations**
```python
print(df.shape)  # Get number of rows and columns
print(df.columns)  # Get column names
print(df.info())  # Get DataFrame summary
print(df.describe())  # Get statistics for numerical columns
```

---

## **Key Takeaways**
- **Series** → 1D labeled array  
- **DataFrame** → 2D table with labeled rows & columns  
- **Indexing** → Zero-based & Custom  
- **Slicing** → Normal, `loc`, `iloc`  
- **Data Import** → `read_csv()`, `read_excel()`  
- **Data Selection** → Columns, Rows, Filters  

---

This provides a structured summary of Pandas basics with relevant examples. Let me know if you need any modifications! 🚀