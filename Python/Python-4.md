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



 Here is the completed explanation and filled-in assertions:

---

### **Indexing in Strings**

```python
string = "Hello"
assert 'H' == string[0]  # True: The first character is 'H'
assert 'e' == string[1]  # True: The second character is 'e'
assert 'l' == string[2]  # True: The third character is 'l'
assert 'l' == string[3]  # True: The fourth character is 'l'
assert 'o' == string[4]  # True: The fifth character is 'o'
```

---

```python
assert 'o' == string[-1]  # True: The last character is 'o'
assert 'l' == string[-2]  # True: The second-to-last character is 'l'
assert 'l' == string[-3]  # True: The third-to-last character is 'l'
assert 'e' == string[-4]  # True: The fourth-to-last character is 'e'
assert 'H' == string[-5]  # True: The fifth-to-last character is 'H'
assert 'H' == string[-0]  # True: -0 is equivalent to 0, so it points to 'H'
```

---

```python
assert 5 == len(string)  # True: The length of "Hello" is 5
```

---

### **Character Type**

```python
first_char = string[0]
assert 'str' == type(first_char).__name__  # True: The type of 'H' is 'str'
assert 'str' == type('a').__name__  # True: The type of 'a' is 'str'
assert 'str' == type("a").__name__  # True: Double quotes also create a string
```

---

### **Slicing in Strings**

```python
string = "Hello world"
assert '' == string[0:0]  # True: No characters between indices 0 and 0
assert 'He' == string[0:2]  # True: Characters from index 0 to 1
assert 'ello' == string[1:5]  # True: Characters from index 1 to 4
assert 'ello worl' == string[1:-1]  # True: Characters from index 1 to second-to-last
assert 'llo wor' == string[2:-2]  # True: Characters from index 2 to third-to-last
```

---

```python
assert '' == string[:0]  # True: Slices up to index 0 (empty string)
assert 'Hell' == string[:4]  # True: Slices up to index 4
assert 'Hello worl' == string[:-1]  # True: Slices up to the second-to-last character
```

---

```python
assert 'Hello world' == string[0:]  # True: Slices from index 0 to the end
assert 'o world' == string[4:]  # True: Slices from index 4 to the end
assert 'd' == string[-1:]  # True: Slices from the last character to the end
```

---

```python
assert '' == string[:0] + string[0:]  # True: Concatenating slices reconstructs the string
assert 'H' == string[:1] + string[1:]  # True: Splits and reconstructs at index 1
assert 'He' == string[:2] + string[2:]  # True: Splits and reconstructs at index 2
assert 'Hel' == string[:3] + string[3:]  # True: Splits and reconstructs at index 3
```

---

### **String Methods**

```python
s = 'this is the python class. llll'
s1 = 'this is THE python class'

# Capitalize
assert 'This is the python class. llll' == s.capitalize()
assert 'This is the python class' == s1.capitalize()

# Upper
assert 'THIS IS THE PYTHON CLASS. LLLL' == s.upper()
assert 'THIS IS THE PYTHON CLASS' == s1.upper()

# Lower
assert 'this is the python class. llll' == s.lower()
assert 'this is the python class' == s1.lower()

# Swapcase
assert 'THIS IS THE PYTHON CLASS. LLLL' == s.swapcase()
assert 'this is the python class' == s1.swapcase()

# Title
assert 'This Is The Python Class. Llll' == s.title()
assert 'This Is The Python Class' == s1.title()
```

---

### **Boolean String Methods**

```python
s = 'hello world'
assert not s.startswith('ello')  # True: 'hello world' does not start with 'ello'
assert s.startswith('o ', 4, 10)  # True: Substring from index 4 to 10 starts with 'o '

assert s.endswith('rld')  # True: 'hello world' ends with 'rld'
assert not s.endswith('rl', 4, 10)  # True: Substring from index 4 to 10 does not end with 'rl'
```

---
