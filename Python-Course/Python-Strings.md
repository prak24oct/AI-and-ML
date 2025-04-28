# 📚 Python Strings & Text Processing

## 1. String Basics

### Creating Strings

```python
# Single quotes
s1 = 'Hello'

# Double quotes
s2 = "World"

# Triple quotes (for multiline strings)
s3 = """This is a
multiline string"""

# Raw strings (for escape characters)
s4 = r"C:\Users\Name"
```

### String Properties

- **Sequence Type**: Ordered collection of characters
- **Immutable**: Cannot be modified after creation
- **Indexable**: Access characters using indices
- **Slicable**: Extract substrings using slices

## 2. String Operations

### Indexing

```python
s = "Python"
print(s[0])    # 'P'
print(s[-1])   # 'n'
print(s[2:4])  # 'th'
```

### Slicing

```python
s = "Hello World"
print(s[0:5])    # 'Hello'
print(s[6:])     # 'World'
print(s[::-1])   # 'dlroW olleH'
print(s[::2])    # 'HloWrd'
```

### Concatenation

```python
s1 = "Hello"
s2 = "World"
print(s1 + " " + s2)  # 'Hello World'
```

### Repetition

```python
s = "Ha"
print(s * 3)  # 'HaHaHa'
```

## 3. String Methods

### Case Conversion

```python
s = "hello world"
print(s.upper())      # 'HELLO WORLD'
print(s.lower())      # 'hello world'
print(s.title())      # 'Hello World'
print(s.capitalize()) # 'Hello world'
print(s.swapcase())   # 'HELLO WORLD'
```

### Searching

```python
s = "Hello World"
print(s.find("World"))    # 6
print(s.index("World"))   # 6
print(s.count("l"))       # 3
print("World" in s)       # True
```

### Modifying

```python
s = "  Hello World  "
print(s.strip())          # 'Hello World'
print(s.replace("World", "Python"))  # '  Hello Python  '
print(s.split())          # ['Hello', 'World']
print("-".join(["Hello", "World"])) # 'Hello-World'
```

### Formatting

```python
name = "John"
age = 25

# f-strings (Python 3.6+)
print(f"My name is {name} and I'm {age} years old")

# format() method
print("My name is {} and I'm {} years old".format(name, age))

# % operator
print("My name is %s and I'm %d years old" % (name, age))
```

## 4. String Encoding

### ASCII vs Unicode

```python
# ASCII (7-bit)
print(ord('A'))  # 65
print(chr(65))   # 'A'

# Unicode
print(ord('€'))  # 8364
print(chr(8364)) # '€'
```

### Encoding/Decoding

```python
s = "Hello World"
encoded = s.encode('utf-8')
decoded = encoded.decode('utf-8')
print(encoded)  # b'Hello World'
print(decoded)  # 'Hello World'
```

## 5. Regular Expressions

### Basic Patterns

```python
import re

# Match pattern
pattern = r"\d+"
text = "There are 123 apples and 456 oranges"
matches = re.findall(pattern, text)
print(matches)  # ['123', '456']

# Search pattern
match = re.search(r"\d+", text)
if match:
    print(match.group())  # '123'
```

### Common Patterns

```python
# Email pattern
email_pattern = r"[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}"
email = "example@email.com"
print(re.match(email_pattern, email))  # Match object

# Phone number pattern
phone_pattern = r"\d{3}-\d{3}-\d{4}"
phone = "123-456-7890"
print(re.match(phone_pattern, phone))  # Match object
```

## 6. String Formatting Best Practices

### f-strings (Recommended)

```python
name = "John"
age = 25
print(f"Name: {name}, Age: {age}")
print(f"Age in 5 years: {age + 5}")
print(f"Name uppercase: {name.upper()}")
```

### Format Method

```python
# Positional arguments
print("{} is {} years old".format(name, age))

# Named arguments
print("{name} is {age} years old".format(name=name, age=age))

# Format specifications
print("Pi: {:.2f}".format(3.14159))  # Pi: 3.14
```

## 7. Common String Operations

### Splitting and Joining

```python
# Split string
s = "apple,banana,orange"
fruits = s.split(",")
print(fruits)  # ['apple', 'banana', 'orange']

# Join list
fruits = ['apple', 'banana', 'orange']
s = ",".join(fruits)
print(s)  # 'apple,banana,orange'
```

### String Validation

```python
s = "Hello123"
print(s.isalnum())  # True
print(s.isalpha())  # False
print(s.isdigit())  # False
print(s.islower())  # False
print(s.isupper())  # False
```

## 8. Performance Considerations

### String Concatenation

```python
# Bad (creates new string each time)
result = ""
for i in range(1000):
    result += str(i)

# Good (uses list and join)
result = []
for i in range(1000):
    result.append(str(i))
final = "".join(result)
```

### String Formatting

```python
# Bad (creates intermediate strings)
s = "Hello" + " " + "World"

# Good (uses f-string)
s = f"Hello World"
```

---

This file covers essential string operations and text processing in Python. For more advanced topics, refer to the other consolidated files in this series.
