Here are your tutable notes, structured with all the concepts, examples, and explanations from your provided content:

---

### **Sequential Data Types → Data Structures → Derived Data Types**

**Examples:**
- **Lists**
- **Strings**
- **Tuples**
- **Dictionary**
- **Sets**
- **frozenset**

---

## **Strings in Python**

### **Definition**
A string is a sequence of characters. Computers store and manipulate characters as numbers (binary). Encoding converts characters to numbers, and decoding reverses this process. Popular encodings include **ASCII** and **Unicode**.

- **Python Strings**: Sequences of Unicode characters.

📖 **References**:
- [Unicode How-To](https://docs.python.org/3.3/howto/unicode.html)
- [Text Sequence Type - str](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str)

---

### **Creating Strings**
Strings can be created using:
1. **Single Quotes**: `'example'`
2. **Double Quotes**: `"example"`
3. **Triple Single Quotes**: `'''example'''`
4. **Triple Double Quotes**: `"""example"""` (commonly used for multiline strings or docstrings)

**Example:**
```python
myStr = 'Hello World'
print(type(myStr).__name__)  # Output: str

myStr = """Hello World"""
print(type(myStr).__name__)  # Output: str
```

---

### **Special Characters in Strings**
#### Single Quotes in Output: `hello 'world'!`
1. Use double quotes or triple quotes:
   ```python
   s = "hello 'world'!"
   print(s)
   ```
2. Use escape characters:
   ```python
   s = 'hello \'world\'!'
   print(s)
   ```

#### Double Quotes in Output: `hello "world"!`
1. Use single quotes or triple quotes:
   ```python
   s = 'hello "world"!'
   print(s)
   ```
2. Use escape characters:
   ```python
   s = "hello \"world\"!"
   print(s)
   ```

#### Multiline Example with Quotes:
```python
s = '''Hello, Virat is the """GOAT""" in cricket'''
print(s)

s = r"Hello \nworld"
print(s)  # Output: Hello \nworld
```

---

### **String Properties**
1. **Sequence Data Type**: Strings allow indexing and slicing.
2. **Immutable**: Strings cannot be changed after creation.
3. **Supports Operations**:
   - Indexing
   - Slicing
   - Concatenation
   - Repetition
   - Membership
   - Identity

---

### **Accessing Characters**
#### Indexing
- **Positive Indexing**: Starts from `0` (left to right).
- **Negative Indexing**: Starts from `-1` (right to left).

**Example:**
```python
myString = "Hello"
print(myString[0])   # Output: H
print(myString[-1])  # Output: o
```

---

### **Slicing**
Extract a substring using:
```python
string[start:stop:step]
```
- **Default Start**: `0`
- **Default Stop**: `len(string)`
- **Step**: Determines direction and interval.

**Examples:**
```python
a = 'python class'
print(a[7:])         # Output: class
print(a[-5::1])      # Output: class
print(a[::-1])       # Output: ssalc nohtyp
```

---

### **String Methods**
#### Case Conversion
1. `capitalize()`: Capitalizes the first letter.
   ```python
   print("hello".capitalize())  # Output: Hello
   ```
2. `upper()`: Converts all characters to uppercase.
   ```python
   print("hello".upper())  # Output: HELLO
   ```
3. `lower()`: Converts all characters to lowercase.
   ```python
   print("HELLO".lower())  # Output: hello
   ```
4. `swapcase()`: Swaps case of all characters.
   ```python
   print("Hello".swapcase())  # Output: hELLO
   ```
5. `title()`: Capitalizes the first letter of each word.
   ```python
   print("hello world".title())  # Output: Hello World
   ```

---

### **Length of Strings**
The `len()` function returns the length of a string.
```python
s = "Hello"
print(len(s))  # Output: 5
```

---

### **String Comparisons**
Strings are compared based on their Unicode values.
```python
a = 'python'
b = 'cython'

print(a == b)  # Output: False
print(a > b)   # Output: True
```

---

### **String Immutability**
Strings cannot be modified in place:
```python
s = 'Hello'
# s[1] = 'e'  # This will raise a TypeError
```

---

### **Advanced Slicing Examples**
1. Reverse a string:
   ```python
   s = "python class"
   print(s[::-1])  # Output: ssalc nohtyp
   ```
2. Extract every second character:
   ```python
   print(s[::2])  # Output: pto ls
   ```

---

### **Finding String Methods**
Use `dir()` to list all methods available for strings:
```python
import os
print(dir(str))
```

---

These notes cover the essential concepts, examples, and methods related to strings in Python, providing a comprehensive guide for learning and revision.