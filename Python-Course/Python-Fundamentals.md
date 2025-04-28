# 📚 Python Fundamentals & Data Types

## 1. Python Basics

### Literals

- **Integer Literals**: `99`, `99999`, `-99999`, `0`, `5`
- **Float Literals**: `99.0`, `100.99999`, `-9999.999`
- **String Literals**: `'True'`, `"afsaan"`, `"""hello"""`, `'''world'''`
- **Boolean Literals**: `True`, `False`
- **Complex Literals**: `12 + 2j`
- **None Literal**: `None`

### Variables & Constants

- **Variables**: Containers for storing data that can change
- **Constants**: Fixed values (convention: UPPERCASE names)

### Identifiers

- Rules:
  1. Can use `a-z`, `A-Z`, `0-9`, `_`
  2. Cannot use special characters
  3. Cannot start with a number
  4. Case-sensitive
  5. Cannot use reserved words

### Keywords

- **Value Keywords**: `True`, `False`, `None`
- **Operator Keywords**: `and`, `or`, `not`, `in`, `is`
- **Control Flow**: `if`, `elif`, `else`, `for`, `while`
- **Function Keywords**: `def`, `return`, `yield`
- **Import Keywords**: `import`, `from`, `as`
- **Exception Handling**: `try`, `except`, `raise`, `finally`

## 2. Data Types

### Fundamental Types

1. **Integer (int)**

   ```python
   a = 10
   print(type(a))  # <class 'int'>
   ```

2. **Float (float)**

   ```python
   b = 10.5
   print(type(b))  # <class 'float'>
   ```

3. **String (str)**

   ```python
   c = "Hello"
   print(type(c))  # <class 'str'>
   ```

4. **Boolean (bool)**

   ```python
   d = True
   print(type(d))  # <class 'bool'>
   ```

5. **Complex**
   ```python
   e = 3 + 4j
   print(type(e))  # <class 'complex'>
   ```

### Type Conversion

```python
# String to Integer
int("10")  # 10

# Integer to String
str(10)  # "10"

# Float to Integer
int(10.5)  # 10

# String to Float
float("10.5")  # 10.5
```

## 3. Operators

### Arithmetic Operators

```python
# Addition
10 + 5  # 15

# Subtraction
10 - 5  # 5

# Multiplication
10 * 5  # 50

# Division
10 / 3  # 3.333...

# Floor Division
10 // 3  # 3

# Modulo
10 % 3  # 1

# Exponentiation
2 ** 3  # 8
```

### Comparison Operators

```python
# Equal to
10 == 10  # True

# Not equal to
10 != 5  # True

# Greater than
10 > 5  # True

# Less than
10 < 5  # False

# Greater than or equal to
10 >= 10  # True

# Less than or equal to
10 <= 5  # False
```

### Logical Operators

```python
# AND
True and False  # False

# OR
True or False  # True

# NOT
not True  # False
```

## 4. Input/Output

### Input

```python
name = input("Enter your name: ")
age = int(input("Enter your age: "))
```

### Output

```python
# Basic print
print("Hello, World!")

# Print with variables
print(f"Hello, {name}!")

# Print with formatting
print("Hello, {}!".format(name))

# Print with separator
print("Hello", "World", sep=", ")  # Hello, World

# Print with end
print("Hello", end=" ")
print("World")  # Hello World
```

## 5. Memory Management

### Object Identity

```python
a = 10
b = 10
print(id(a) == id(b))  # True (small integers are reused)

c = 257
d = 257
print(id(c) == id(d))  # False (large integers are not reused)
```

### Identity vs Equality

```python
a = [1, 2, 3]
b = [1, 2, 3]
print(a == b)  # True (same values)
print(a is b)  # False (different objects)
```

## 6. Best Practices

1. **Naming Conventions**

   - Use descriptive names
   - Follow snake_case for variables and functions
   - Use UPPERCASE for constants

2. **Comments**

   - Use clear, concise comments
   - Document functions with docstrings
   - Avoid over-commenting

3. **Code Organization**

   - Use consistent indentation
   - Group related code
   - Follow PEP 8 style guide

4. **Error Handling**
   - Use try-except blocks
   - Provide meaningful error messages
   - Handle specific exceptions

---

This file covers the fundamental concepts of Python programming. For more advanced topics, refer to the other consolidated files in this series.
