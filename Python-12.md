# **Regular Expressions (Regex) in Python**

## **Introduction**
Regular Expressions (Regex) are powerful tools for string matching, searching, and manipulation. They are widely used for tasks like pattern recognition, input validation, and text parsing.

The Python `re` module provides support for working with regex patterns. To use regex, you must first import the `re` module:
```python
import re
```

---

## **Regex Syntax and Special Characters**

### **Special Characters**
1. **`.`**: Matches any character except a newline (`\n`).
2. **`\d`**: Matches any digit (0-9).
3. **`\D`**: Matches any non-digit character.
4. **`\w`**: Matches any word character (a-z, A-Z, 0-9, `_`).
5. **`\W`**: Matches any non-word character.
6. **`\s`**: Matches any whitespace character (space, tab, newline).
7. **`\S`**: Matches any non-whitespace character.
8. **`\b`**: Matches a word boundary (position between a word and a non-word character).
9. **`\B`**: Matches where there is no word boundary.
10. **`^`**: Matches the start of a string.
11. **`$`**: Matches the end of a string.
12. **`[]`**: Matches any character inside the brackets.
    - Example: `[abc]` matches `a`, `b`, or `c`.
13. **`[^ ]`**: Matches any character not inside the brackets.
14. **`|`**: Acts as a logical OR operator.
15. **`( )`**: Groups a pattern for extraction or logical operations.

---

### **Quantifiers**
1. **`*`**: Matches 0 or more occurrences of the preceding character or group.
2. **`+`**: Matches 1 or more occurrences.
3. **`?`**: Matches 0 or 1 occurrence.
4. **`{n}`**: Matches exactly `n` occurrences.
5. **`{n,m}`**: Matches between `n` and `m` occurrences.

---

## **Common Regex Patterns**
- **Email Validation**:
  ```regex
  [a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+
  ```

---

## **Using Regex in Python**

### **Basic Workflow**
1. **Compile a Pattern**:
   Use `re.compile()` to create a regex pattern object.
   ```python
   pattern = re.compile('123')
   ```

2. **Find Matches**:
   Use methods like `finditer()` to find all matches in the text.
   ```python
   matches = pattern.finditer(text_to_search)
   for match in matches:
       print(match)
   ```

3. **Access Match Details**:
   Each match object contains information about the match, such as its position in the string:
   ```python
   match.start(), match.end(), match.group()
   ```

---

## **Examples and Explanations**

### **Matching Any Character Except Newline (`.`)**
```python
pattern = re.compile(r'.')
matches = pattern.finditer('Hello Good Morning, its 9:00 A\n')
for match in matches:
    print(match)
```

### **Digit Matching (`\d`)**
```python
pattern = re.compile(r'\d\d')
matches = pattern.finditer('Hello Its 9 00 AM and 25th September 2022')
for match in matches:
    print(match)
```

### **Non-Digit Matching (`\D`)**
```python
pattern = re.compile(r'\D')
matches = pattern.finditer('Hello Its 9 00 AM and 25th September 2022')
for match in matches:
    print(match)
```

### **Word Character Matching (`\w`)**
```python
pattern = re.compile(r'\wo')
matches = pattern.finditer('hello,--- good morning 25092022')
for match in matches:
    print(match)
```

### **Non-Word Character Matching (`\W`)**
```python
pattern = re.compile(r'\W')
matches = pattern.finditer(' hello   good ')
for match in matches:
    print(match)
```

### **Whitespace Matching (`\s`)**
```python
pattern = re.compile(r'\s')
matches = pattern.finditer(' Hello \t good morning\n')
for match in matches:
    print(match)
```

### **Word Boundary Matching (`\b`)**
```python
text_data = 'cat catherine catholic wildcat copycat uncatchable'
pattern = re.compile(r'cat\b')
matches = pattern.finditer(text_data)
for match in matches:
    print(match)
```

### **Not a Word Boundary (`\B`)**
```python
pattern = re.compile('\Bcat')
matches = pattern.finditer('cat catherine catholic wildcat copycat uncatchable')
for match in matches:
    print(match)
```

---

## **Advanced Examples**

### **Extracting Phone Numbers**
Match phone numbers in different formats:
```python
pattern = re.compile(r'\d{3}[-*.]\d{3}[-*.]\d{4}')
matches = pattern.finditer(text_to_search)
for match in matches:
    print(match)
```

### **Matching Specific Characters**
```python
pattern = re.compile(r'[cfmp]at')
matches = pattern.finditer('cat fat mat pat bat')
for match in matches:
    print(match)
```

### **Exclude Specific Characters**
```python
pattern = re.compile(r'[^b]at')
matches = pattern.finditer('cat fat mat pat bat')
for match in matches:
    print(match)
```

---

## **Practical Applications**

### **Validating Names**
Match titles followed by names:
```python
pattern = re.compile(r'M[rs]\.? [A-Z][a-z]*')
matches = pattern.finditer('Mr. Schafer, Ms Davis, Mrs. Robinson')
for match in matches:
    print(match)
```

### **Search for Specific Patterns**
Find all three-digit numbers:
```python
pattern = re.compile(r'\d{3}')
matches = pattern.finditer(text_to_search)
for match in matches:
    print(match)
```

---

## **Useful Resources**
For further reading and interactive practice:
- [W3Schools Python Regex](https://www.w3schools.com/python/python_regex.asp)

---

These notes provide an in-depth understanding of regular expressions, their syntax, and their applications in Python. With examples and explanations, they aim to serve as a comprehensive resource for mastering regex.

---

# Comprehensive Revision Notes: Python Concepts

## 1. **Enumerate**

### Overview:
The `enumerate()` function in Python is used to iterate over a sequence (like a list, tuple, or string) while keeping track of both the index and the value of each item. It is particularly useful in loops where the index of elements is required.

### Syntax:
```python
enumerate(iterable, start=0)
```
- **iterable**: The collection you want to loop through.
- **start**: The starting index (default is 0).

### Example:
#### Without `enumerate`:
```python
rand_list = [1, 2, 3, 4, 5, 57, 54, 45, 2, 34132]

for i in rand_list:
    print(i)  # Prints each element in the list
```

#### With `enumerate`:
```python
a = [1, 4, 5, 3, 2, 5, 6, 7, 8, 3, 9, 1, 2, 3]

# Find all the indices of the element 3
for i in enumerate(a):
    print(i)  # Prints tuples of (index, value)

# Output:
# (0, 1)
# (1, 4)
# ...
# (3, 3)

for index, ele in enumerate(a):
    print(index, ele)  # Separately prints index and value

# Find indices where the value is 3
for index, ele in enumerate(a):
    if ele == 3:
        print(index)  # Prints the index of each occurrence of 3
```

### Key Points:
- `enumerate()` simplifies the process of accessing indices and values simultaneously.
- Useful for tasks like searching for specific values and tracking their positions in a collection.

---

## 2. **File and Directory Management with `os` Module**

### Overview:
The `os` module in Python provides functions to interact with the operating system, enabling tasks such as navigating directories, creating/deleting files, and renaming files or directories.

### Common Functions:
#### 1. **Get Current Working Directory:**
```python
import os
print(os.getcwd())  # Prints the current working directory
```

#### 2. **Change Directory:**
```python
os.chdir(r'C:\Users\navee\Documents\Python Scripts')
print(os.getcwd())  # Verifies the directory change
```

#### 3. **List Directory Contents:**
```python
print(os.listdir())  # Lists all files and directories in the current directory
```

#### 4. **Create a Directory:**
```python
os.mkdir('Demo for directories in python')  # Creates a new directory
```

#### 5. **Rename a Directory or File:**
```python
os.rename('Test dir', 'to be deleted')  # Renames 'Test dir' to 'to be deleted'
```

#### 6. **Delete Files and Directories:**
- **Delete a file:**
```python
os.remove('rand.bmp')  # Removes the file 'rand.bmp'
```

- **Delete an empty directory:**
```python
os.rmdir('to be deleted')  # Deletes an empty directory
```

### Example Workflow:
```python
import os

# Navigate to a specific directory
os.chdir(r'C:\Users\navee\Documents\File Handling and Packages demo')

# List contents of the directory
print(os.listdir())

# Create a new directory
os.mkdir('Demo Directory')

# Rename the directory
os.rename('Demo Directory', 'Renamed Directory')

# Delete the renamed directory
os.rmdir('Renamed Directory')
```

---

## 3. **Advanced Directory Management with `shutil` Module**

### Overview:
The `shutil` module provides additional file and directory operations, such as copying, moving, and removing non-empty directories.

### Common Functions:
#### 1. **Remove a Non-Empty Directory:**
```python
import shutil

shutil.rmtree('Package1')  # Removes the non-empty directory 'Package1'
```

### Comparison with `os`:
- `os.rmdir()` can only remove empty directories.
- `shutil.rmtree()` can remove directories regardless of their contents.

### Example:
```python
import shutil

# Remove a directory with files
shutil.rmtree('NonEmptyDir')
```

---

## Key Takeaways:
- Use `enumerate()` to simplify loops requiring indices and values.
- The `os` module is essential for basic file and directory management.
- The `shutil` module extends functionality for more complex operations, such as handling non-empty directories.

---

### Revision Notes: Iterators and Generators in Python

---

#### **1. Iterators**
An **iterator** is an object in Python that allows traversal through elements in a collection (like a list or tuple) one at a time. Iterators implement the `__iter__()` and `__next__()` methods.

##### **Key Concepts**
- **Iterable vs Iterator**: 
  - An **iterable** is an object that can return an iterator (e.g., lists, tuples, strings).
  - An **iterator** is the object used to iterate over an iterable.

- **Creating an Iterator**:
  - Use the `iter()` function to create an iterator from an iterable.
  - Use the `next()` function to retrieve the next element from the iterator.

##### **Example**
```python
my_list = [4, 7, 0, 3, 1, 5, 'asdsd', 6, 7, 8, 8, 0, 8, 8]
my_iter = iter(my_list)

# Access elements using next()
print(next(my_iter))  # Output: 4
print(next(my_iter))  # Output: 7

# Iterate through the rest of the iterator
for i in my_iter:
    print(i)
```

##### **Using `next()` with a Default Value**
- You can provide a default value to `next()` to handle the end of the iterator gracefully.
```python
next(my_iter, 'end of iterator')  # Output: 'end of iterator'
```

---

#### **2. Generators**
A **generator** is a special type of iterator that is defined using a function. Instead of returning values with `return`, a generator uses the `yield` keyword to produce a series of values lazily, one at a time.

##### **Key Characteristics**
- **Lazy Evaluation**: Generators do not compute all their values at once; they yield values one at a time as needed.
- **State Retention**: A generator function retains its state between `yield` calls.

##### **Creating a Generator**
- Define a function with the `yield` keyword.
- Each call to `yield` pauses the function and saves its state for the next iteration.

##### **Example**
```python
def temp():
    yield 1
    print('hello')
    yield 22
    yield 33
    yield 44

values = temp()

# Access values using next()
print(next(values))  # Output: 1
print(next(values))  # Output: 'hello' followed by 22
```

---

#### **3. Generator for Squares**
This generator yields the square of numbers from 1 to 10.

##### **Example**
```python
def sq():
    n = 1
    while n <= 10:
        sq = n * n
        yield sq
        n += 1

z = sq()

# Access squares using next()
print(next(z))  # Output: 1
print(next(z))  # Output: 4
```

---

#### **4. Iterating Over Generators**
Generators can be iterated over just like iterators. Once a generator is exhausted, it cannot be reused unless reinitialized.

##### **Example**
```python
for value in temp():
    print(value)
```

---

#### **5. Type Checking**
Use the `type()` function to check the type of an object:
```python
print(type(values))  # Output: <class 'generator'>
```

---

#### **6. Converting Iterators and Generators**
- Generators and iterators can be converted into lists using the `list()` function.
```python
list_values = list(temp())  # Converts the generator output into a list
print(list_values)  # Output: [1, 22, 33, 44]
```

---

#### **7. Sorting a List**
Python lists can be sorted using the `sort()` method, which modifies the list in place.

##### **Example**
```python
l = [1, 2, 3, 4, 5]
l.sort()
print(l)  # Output: [1, 2, 3, 4, 5]
```

---

#### **8. Summary of Key Functions**
- **`iter(obj)`**: Converts an iterable into an iterator.
- **`next(iterator, default)`**: Retrieves the next item from the iterator. Returns `default` if the iterator is exhausted.
- **`yield`**: Used in a generator to produce values lazily.

---

#### **9. Practical Example: Iterating Over a List**
```python
list1 = [25, 78, 'coding', 'is', 'noice']
z = iter(list1)

# Access elements using next()
print(next(z))  # Output: 25
print(next(z))  # Output: 78
```

Using `iter()` and `next()` helps control iteration manually, offering flexibility in handling collections and sequences.

---

These notes provide an in-depth understanding of iterators and generators, their use cases, and practical implementations in Python.

---

### Revision Notes: Sorting in Python

Sorting is a fundamental operation in Python that allows us to organize data in a specified order. Python provides built-in methods for sorting sequences such as lists, strings, and tuples. These methods can be customized to suit various use cases.

---

#### **1. Sorting a List In-Place with `.sort()`**
The `sort()` method is used to sort a list in place. It modifies the original list and does not return a new list.

##### **Example**
```python
l = [1, 2, 3, 4, 5]
l.sort()
print(l)  # Output: [1, 2, 3, 4, 5]
```

- **Key Characteristics**:
  - Works only on lists.
  - Modifies the original list.
  - Returns `None`.

---

#### **2. Using the `sorted()` Function**
The `sorted()` function creates a new sorted list from any iterable (e.g., strings, tuples, or lists) without modifying the original data.

##### **Example**
```python
val = '34521'
sorted_val = sorted(val)
print(sorted_val)  # Output: ['1', '2', '3', '4', '5']
```

- **Key Characteristics**:
  - Works on any iterable (e.g., strings, lists, tuples).
  - Returns a new list.
  - Does not modify the original iterable.

##### **Help Documentation**
You can view the detailed documentation for `sorted()` using the `help()` function:
```python
help(sorted)
```

---

#### **3. Sorting Strings**
Strings can be sorted character by character. Sorting is based on the Unicode code point of each character.

##### **Example**
```python
string_number_value = '34521'
print(sorted(string_number_value))  # Output: ['1', '2', '3', '4', '5']

string_value = 'abcdefABCD'
print(sorted(string_value))  
# Output: ['A', 'B', 'C', 'D', 'a', 'b', 'c', 'd', 'e', 'f']
```

- **Unicode Sorting**:
  - Uppercase letters (A-Z) have lower Unicode values than lowercase letters (a-z).
  - Example: `'A' < 'a'`.

##### **Unicode Representation**
To understand the sorting order, we can view the Unicode values of characters:
```python
[(i, ord(i)) for i in 'abcdefABCD']
# Output: [('a', 97), ('b', 98), ('c', 99), ('d', 100), ('e', 101), ('f', 102), 
#          ('A', 65), ('B', 66), ('C', 67), ('D', 68)]
```

---

#### **4. Sorting Words**
Words can be sorted alphabetically or based on specific criteria such as length.

##### **Example: Sorting Words Alphabetically**
```python
z = 'I like to sort'.split()
print(sorted(z))  # Output: ['I', 'like', 'sort', 'to']
```

##### **Example: Sorting Words by Length**
Use the `key` parameter to specify a custom sorting criterion:
```python
words = ['banana', 'pie', 'Washington', 'book']
sorted_by_length = sorted(words, key=len)
print(sorted_by_length)  # Output: ['pie', 'book', 'banana', 'Washington']
```

---

#### **5. Sorting with Custom Functions**
You can use a custom function with the `key` parameter to define a unique sorting order.

##### **Example: Sorting by Reversed Words**
```python
def reverse_word(word):
    return word[::-1]

words = ['banana', 'pie', 'Washington', 'book']
sorted_by_reverse = sorted(words, key=reverse_word)
print(sorted_by_reverse)
# Output: ['banana', 'Washington', 'pie', 'book']
```

##### **Using Lambda Functions**
A lambda function can be used as a concise alternative to a named function:
```python
sorted_by_length = sorted(words, key=lambda x: len(x))
print(sorted_by_length)  # Output: ['pie', 'book', 'banana', 'Washington']
```

---

#### **6. Sorting Mixed Data Types**
Python can sort lists containing mixed data types only if the types are comparable. For example:
```python
sorted(['hhhhhd', 'hhhhha', 'hhhhhc', 'hhhhhb'])
# Output: ['hhhhha', 'hhhhhb', 'hhhhhc', 'hhhhhd']

# Sorting a list with None will raise an error unless the list is explicitly comparable.
# Example:
# sorted([None, 223])  # Raises a TypeError
```

---

#### **7. Summary of Sorting Techniques**
| **Method**     | **Modifies Original?** | **Returns New List?** | **Applicable to**   |
|-----------------|-------------------------|------------------------|---------------------|
| `list.sort()`   | Yes                     | No                     | Lists only          |
| `sorted()`      | No                      | Yes                    | Any iterable        |

---

#### **8. Key Parameters in Sorting**
The `key` parameter in both `sort()` and `sorted()` allows customization of sorting logic:
- **`key=len`**: Sort by length of elements.
- **Custom Functions**: Use functions or lambdas to define complex sorting logic.

##### **Example**
```python
words = ['banana', 'pie', 'Washington', 'book']
print(sorted(words, key=lambda x: x[::-1]))  # Sort by reversed strings
```

These notes provide a comprehensive understanding of sorting operations in Python, including examples, advanced use cases, and the role of the `key` parameter for customization.
