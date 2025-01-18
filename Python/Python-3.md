# Python Tutorial Notes

## Number Systems

Number systems are positional systems with a specific base. Examples include:
- **Binary (Base 2)**: Uses digits 0 and 1.
- **Octal (Base 8)**: Uses digits 0 to 7.
- **Decimal (Base 10)**: Uses digits 0 to 9 (commonly used in daily life).
- **Hexadecimal (Base 16)**: Uses digits 0-9 and letters A-F.

### Conversion Examples

#### Decimal to Other Bases:
```python
num = 100  # Decimal number

# Convert decimal to octal
print(oct(num))  # Output: '0o144'

# Convert decimal to hexadecimal
print(hex(num))  # Output: '0x64'

# Convert decimal to binary
print(bin(num))  # Output: '0b1100100'
```

#### Other Bases to Decimal:
```python
# Convert hexadecimal to decimal
print(int("A", 16))  # Output: 10

# Convert octal to decimal
print(int("77", 8))  # Output: 63

# Convert binary to decimal
print(int("11", 2))  # Output: 3
```

#### Base Conversion Function:
```python
def base36_to_binary(input):
    base_10 = int(input, 36)  # Convert base 36 to base 10
    base_2 = bin(base_10)     # Convert base 10 to binary
    return base_2[2:]         # Remove '0b' prefix

print(base36_to_binary("10"))  # Output: '100100'
print(base36_to_binary("AB"))  # Output: '101110011'
```

### Assertions for Testing:
```python
assert 255 == int("11111111", 2)
assert 254 == int("FE", 16)
assert 121 == int("232", 7)
assert 675 == int("JJ", 26)
```

## Bitwise Operations
Bitwise operations manipulate individual bits of numbers. Operators include:

| Operator | Description       | Example      |
|----------|-------------------|--------------|
| `&`      | Bitwise AND       | `a & b`      |
| `|`      | Bitwise OR        | `a | b`      |
| `^`      | Bitwise XOR       | `a ^ b`      |
| `~`      | Bitwise NOT       | `~a`         |
| `<<`     | Left shift        | `a << n`     |
| `>>`     | Right shift       | `a >> n`     |

### Examples:
```python
a = 10  # Binary: 1010
b = 20  # Binary: 10100

# Bitwise AND
print(a & b)  # Output: 0

# Bitwise OR
print(a | b)  # Output: 30

# Bitwise XOR
print(a ^ b)  # Output: 30

# Left shift
print(a << 2)  # Output: 40

# Right shift
print(b >> 2)  # Output: 5
```

### Bitwise NOT:
```python
a = 10
print(~a)  # Output: -11 (adds 1 and reverses the sign)
```

## Operator Precedence
Operators are evaluated in a specific order. The precedence (highest to lowest) is:
1. Parentheses `()`
2. Exponentiation `**`
3. Unary `+`, `-`, `~`
4. Multiplication, Division `*`, `/`, `//`, `%`
5. Addition, Subtraction `+`, `-`
6. Bitwise shifts `<<`, `>>`
7. Bitwise AND `&`
8. Bitwise XOR `^`
9. Bitwise OR `|`
10. Comparison `==`, `!=`, `<`, `>`, `<=`, `>=`, `is`, `is not`, `in`, `not in`
11. Logical NOT `not`
12. Logical AND `and`
13. Logical OR `or`

### Examples:
```python
# Example 1
print(4 / (2 + 2))  # Output: 1.0

# Example 2
print(2 + 9 * ((3 * 12) - 8) / 10)  # Output: 29.6

# Example 3
print(4 + 2 ** 5 // 10)  # Output: 7
```

### Imp Link -
* https://medium.com/@coderecipe/how-python-works-for-two-variables-having-same-id-f7f92aff60ae
* https://stackoverflow.com/questions/20753364/why-is-the-id-of-a-python-class-not-unique-when-called-quickly
* https://stackoverflow.com/questions/23777801/python-slice-method-does-not-always-return-a-new-address-in-memory

## Object Reusability in Python
Certain objects in Python are reused for efficiency:

| Data Type | Reusability Rules                         |
|-----------|------------------------------------------|
| `int`     | Values from -5 to 256 are reused         |
| `float`   | Not applicable                           |
| `str`     | Strings with alphanumerics are reused    |
| `bool`    | `True` and `False` are reused           |
| `complex` | Not applicable                           |

### Examples:
```python
a = 257
b = 257
print(id(a) == id(b))  # Output: False

x = 10
y = 10
print(id(x) == id(y))  # Output: True
```

## Input and Output in Python

### Input Function:
The `input()` function takes user input as a string.
```python
a = input("Enter a number: ")
b = input("Enter another number: ")
print(int(a) + int(b))
```

### Print Function:
The `print()` function displays output.
- `end` parameter: Specifies what to print at the end (default is `\n`).
- `sep` parameter: Specifies the separator between arguments.

```python
a, b, c = 10, 20, 30

print(a, b, c, sep='**', end='!!')  # Output: 10**20**30!!
```

## String Formatting
Python supports multiple ways to format strings:

### Using `+`:
```python
first_name = "John"
last_name = "Doe"
print("My name is " + first_name + " " + last_name)
```

### Using `format()`:
```python
print("My name is {} {}".format(first_name, last_name))
```

### Using f-strings:
```python
print(f"My name is {first_name} {last_name}")
```

## Additional Concepts

### Hash Function:
The `hash()` function returns a hash value for immutable objects.
```python
print(hash("hello"))  # Example output: 99162322
```

### `eval()` Function:
The `eval()` function evaluates a string as a Python expression.
```python
a = eval(input("Enter a number: "))
b = eval(input("Enter another number: "))
print(a + b)
```

### Memory Management:
- Python reuses memory for small integers and certain strings.
- Use `id()` to check the memory address of an object.
```python
a = 10
b = 10
print(id(a) == id(b))  # Output: True
```

### Comparsion operator -> is and === 
In Python, the expression `c is d` checks whether the two variables `c` and `d` refer to the **same object in memory**. It is a comparison of object identity, not equality of values.

### Key Points:
1. **Object Identity**:
   - `is` compares the memory addresses of the objects that `c` and `d` refer to.
   - If `c is d` evaluates to `True`, it means both `c` and `d` point to the same memory location.

2. **Equality (`==`) vs. Identity (`is`)**:
   - `==` checks if the values of the objects are the same (i.e., equality).
   - `is` checks if the objects themselves are the same (i.e., identity).

### Example:
```python
c = [1, 2, 3]
d = [1, 2, 3]

print(c == d)  # True, because their values are the same.
print(c is d)  # False, because they are different objects in memory.

# Now assign c to d
d = c
print(c is d)  # True, because now both refer to the same object.
```

### When `is` Returns `True`:
- When two variables point to the same object:
  ```python
  c = 42
  d = 42
  print(c is d)  # True, because Python optimizes small integers (-5 to 256).
  ```

- For immutable objects like strings and small integers, Python may reuse objects for optimization (interning):
  ```python
  c = "hello"
  d = "hello"
  print(c is d)  # True, because Python reuses the same string object.
  ```

### When to Use `is`:
- Use `is` when checking for **identity**, such as:
  - Comparing to `None`:
    ```python
    if c is None:
        print("c is None")
    ```
  - Checking if two variables point to the same object.

For most cases, prefer `==` for value comparison unless object identity is specifically needed.


Here's an explanation and completed version of the code you provided, covering identity (`is`) and equality (`==`) in Python, with the placeholders filled and detailed comments for clarity.

### Code with Completed Assertions and Explanation

```python
def test_identity_equality_lists():
    a = []
    b = []
    # `a` and `b` are separate list objects with the same value but different memory locations.
    assert False == (a is b)  # True when id(a) == id(b), but here they are different.
    assert True == (a == b)  # True because the values of `a` and `b` are equal.

    a.append("one")
    # After modifying `a`, `b` remains unchanged as they are different objects.
    assert False == (a is b)  # `a` and `b` still have different memory locations.
    assert False == (a == b)  # Now their values are no longer equal.

    c = []
    d = c  # `d` is assigned to the same object as `c`.
    assert True == (c is d)  # `c` and `d` point to the same object.
    assert True == (c == d)  # Their values are equal as they refer to the same object.

    c.append("one")
    # Modifying `c` also modifies `d` because they refer to the same object.
    assert True == (c is d)  # `c` and `d` are still the same object.
    assert True == (c == d)  # Their values remain equal as they are the same object.

def test_identity_equality_string():
    a = b = "hello"
    # Python interns small strings, so `a` and `b` point to the same object.
    assert True == (a is b)  # `a` and `b` are the same object.
    assert True == (a == b)  # Their values are equal.

    c = "hello"
    d = "".join(["hel", "lo"])  # Creates a new string object.
    assert False == (c is d)  # `c` and `d` are different objects.
    assert True == (c == d)  # Their values are equal.

def test_identity_equality_numbers():
    a = b = 10000
    # Large integers are not always interned, so `a` and `b` may or may not be the same object.
    assert True == (a is b)  # In CPython, integers assigned in the same line point to the same object.
    assert True == (a == b)  # Their values are equal.

    c = 10000
    d = int("10000")  # Creates a new integer object.
    assert False == (c is d)  # `c` and `d` are different objects in memory.
    assert True == (c == d)  # Their values are equal.

def test_identity_equality_small_numbers():
    a = b = 10
    # Small integers (-5 to 256) are interned by Python.
    assert True == (a is b)  # `a` and `b` are the same object.
    assert True == (a == b)  # Their values are equal.

    c = 10
    d = int("10")  # Creates a new integer object, but for small integers, interning applies.
    assert True == (c is d)  # Small integers are interned, so `c` and `d` point to the same object.
    assert True == (c == d)  # Their values are equal.

def test_identity_equality_None():
    a = b = None
    # `None` is a singleton in Python.
    assert True == (a is b)  # `a` and `b` point to the same `None` object.
    assert True == (a == b)  # Their values are equal.

    a = None
    b = None
    assert True == (a is b)  # Still points to the same `None` object.
    assert True == (a == b)  # Values are equal.
```

---

### Key Concepts Highlighted in the Tests:

1. **Identity (`is`)**:
   - Checks whether two variables point to the same object in memory.
   - `is` evaluates to `True` when `id(a) == id(b)`.

2. **Equality (`==`)**:
   - Compares the values of two objects.
   - `==` evaluates to `True` when the values of `a` and `b` are the same.

3. **String Interning**:
   - Python reuses immutable strings to optimize memory for small or commonly used strings.

4. **Integer Interning**:
   - Python pre-allocates small integers in the range `-5` to `256` for performance reasons.

5. **`None` Singleton**:
   - `None` is a unique singleton in Python, so all references to `None` are the same object.

---

For more on Python operators, you can refer to the [W3Schools Python Assignment Operators](https://www.w3schools.com/python/gloss_python_assignment_operators.asp).