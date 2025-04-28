# 📚 Python Data Structures

## 1. Lists

### Creating Lists

```python
# Empty list
empty_list = []

# List of integers
numbers = [1, 2, 3, 4, 5]

# List of strings
fruits = ['apple', 'banana', 'orange']

# List of mixed types
mixed = [1, 'apple', 3.14, True]

# List using list() constructor
list_from_range = list(range(5))  # [0, 1, 2, 3, 4]
```

### List Operations

```python
# Indexing
fruits = ['apple', 'banana', 'orange']
print(fruits[0])    # 'apple'
print(fruits[-1])   # 'orange'

# Slicing
print(fruits[1:3])  # ['banana', 'orange']
print(fruits[::-1]) # ['orange', 'banana', 'apple']

# Concatenation
list1 = [1, 2, 3]
list2 = [4, 5, 6]
print(list1 + list2)  # [1, 2, 3, 4, 5, 6]

# Repetition
print([1, 2] * 3)  # [1, 2, 1, 2, 1, 2]
```

### List Methods

```python
# Adding elements
fruits = ['apple', 'banana']
fruits.append('orange')        # ['apple', 'banana', 'orange']
fruits.insert(1, 'kiwi')      # ['apple', 'kiwi', 'banana', 'orange']
fruits.extend(['grape', 'pear'])  # Extends with multiple items

# Removing elements
fruits.remove('banana')       # Removes first occurrence
popped = fruits.pop()         # Removes and returns last item
popped = fruits.pop(1)        # Removes and returns item at index 1
fruits.clear()                # Removes all items

# Other operations
fruits = ['apple', 'banana', 'orange']
fruits.index('banana')        # Returns index of first occurrence
fruits.count('apple')         # Counts occurrences
fruits.sort()                 # Sorts in place
fruits.reverse()              # Reverses in place
```

## 2. Tuples

### Creating Tuples

```python
# Empty tuple
empty_tuple = ()

# Single element tuple
single = (1,)  # Note the comma

# Multiple elements
coordinates = (10, 20)
colors = ('red', 'green', 'blue')

# Tuple unpacking
x, y = coordinates
```

### Tuple Operations

```python
# Indexing
colors = ('red', 'green', 'blue')
print(colors[0])    # 'red'
print(colors[-1])   # 'blue'

# Slicing
print(colors[1:3])  # ('green', 'blue')

# Concatenation
tuple1 = (1, 2)
tuple2 = (3, 4)
print(tuple1 + tuple2)  # (1, 2, 3, 4)

# Repetition
print((1, 2) * 3)  # (1, 2, 1, 2, 1, 2)
```

## 3. Dictionaries

### Creating Dictionaries

```python
# Empty dictionary
empty_dict = {}

# Dictionary with initial values
person = {
    'name': 'John',
    'age': 30,
    'city': 'New York'
}

# Using dict() constructor
person = dict(name='John', age=30, city='New York')
```

### Dictionary Operations

```python
# Accessing values
print(person['name'])  # 'John'
print(person.get('age'))  # 30
print(person.get('country', 'USA'))  # Returns 'USA' if key not found

# Adding/Updating
person['country'] = 'USA'  # Add new key-value pair
person['age'] = 31        # Update existing value

# Removing
del person['city']        # Remove key-value pair
age = person.pop('age')   # Remove and return value
person.clear()            # Remove all items
```

### Dictionary Methods

```python
# Keys, values, items
keys = person.keys()      # Returns view of keys
values = person.values()  # Returns view of values
items = person.items()    # Returns view of key-value pairs

# Other methods
person.update({'country': 'Canada'})  # Update with another dict
person.setdefault('language', 'English')  # Set default if key not exists
```

## 4. Sets

### Creating Sets

```python
# Empty set
empty_set = set()

# Set with values
fruits = {'apple', 'banana', 'orange'}

# Set from list
numbers = set([1, 2, 3, 4, 5])
```

### Set Operations

```python
# Adding elements
fruits.add('kiwi')        # Add single element
fruits.update(['grape', 'pear'])  # Add multiple elements

# Removing elements
fruits.remove('banana')   # Raises error if not found
fruits.discard('kiwi')    # No error if not found
popped = fruits.pop()     # Remove and return random element
fruits.clear()            # Remove all elements

# Set operations
set1 = {1, 2, 3}
set2 = {3, 4, 5}

print(set1.union(set2))         # {1, 2, 3, 4, 5}
print(set1.intersection(set2))  # {3}
print(set1.difference(set2))    # {1, 2}
print(set1.symmetric_difference(set2))  # {1, 2, 4, 5}
```

## 5. List Comprehensions

### Basic Comprehensions

```python
# Create list of squares
squares = [x**2 for x in range(10)]

# Create list of even numbers
evens = [x for x in range(10) if x % 2 == 0]

# Nested comprehensions
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flattened = [num for row in matrix for num in row]
```

### Dictionary Comprehensions

```python
# Create dictionary of squares
squares = {x: x**2 for x in range(5)}

# Filter dictionary
original = {'a': 1, 'b': 2, 'c': 3}
filtered = {k: v for k, v in original.items() if v > 1}
```

### Set Comprehensions

```python
# Create set of unique squares
unique_squares = {x**2 for x in range(-5, 6)}
```

## 6. Performance Considerations

### List vs Tuple

- Use tuples for fixed data (immutable)
- Use lists for dynamic data (mutable)

### Dictionary vs List

- Use dictionaries for key-value lookups
- Use lists for ordered collections

### Set Operations

- Use sets for membership testing and unique collections
- Sets are faster than lists for membership testing

## 7. Best Practices

### List Best Practices

```python
# Use list comprehensions
squares = [x**2 for x in range(10)]

# Avoid modifying list while iterating
numbers = [1, 2, 3, 4, 5]
filtered = [x for x in numbers if x > 2]

# Use enumerate for index and value
for index, value in enumerate(numbers):
    print(f"Index: {index}, Value: {value}")
```

### Dictionary Best Practices

```python
# Use get() for safe access
value = person.get('age', 0)

# Use items() for iteration
for key, value in person.items():
    print(f"{key}: {value}")

# Use dictionary comprehensions
squares = {x: x**2 for x in range(5)}
```

### Set Best Practices

```python
# Use set operations for unique collections
unique_items = set(items)

# Use set for membership testing
if item in unique_items:
    print("Found")
```

---

This file covers essential data structures in Python. For more advanced topics, refer to the other consolidated files in this series.
