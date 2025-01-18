Here's a more structured and concise version of your notes, designed for easy reference and learning:

---

# Python Programming Notes

## **1. Comments in Python**
- **Single-line comments**: Use `#` to add comments.
- **Multi-line comments**: Use triple quotes (`"""`).
    ```python
    """
    This is a multi-line comment.
    It spans multiple lines.
    """
    ```

## **2. Docstrings**
- Used to provide documentation for functions, classes, methods, or modules.
    ```python
    def even_or_odd(n):
        """
        This function checks if a given number is odd or even.
        """
    print(even_or_odd.__doc__)
    ```

## **3. Importance of Comments**
- **Uncommented code**: Can be difficult to understand.
    ```python
    pi = 3.14
    r = 5
    a = r * r
    print(a)
    ```
- **Commented code**: Enhances readability.
    ```python
    pi = 3.14  # Value of pi
    r = 5  # Radius
    a = r * r  # Area of the circle
    print(a)
    ```

- **Avoid over-commenting** trivial lines, as it may reduce readability.

## **4. Data Types in Python**
### **Fundamental Data Types**
- `int`, `float`, `str`, `bool`, `complex`, `NoneType`

### **Derived Data Types**
- `list`, `tuple`, `set`, `dict`, `range`

### **Examples**
- **Integer**
    ```python
    a = 200
    print(type(a))  # Output: <class 'int'>
    ```
- **Float**
    ```python
    b = 200.5
    print(type(b))  # Output: <class 'float'>
    ```
- **Complex**
    ```python
    c = 3 + 4j
    print(c.real, c.imag)  # Real and imaginary parts
    print(c.conjugate())  # Conjugate
    ```

## **5. Arithmetic Operations**
- Addition (`+`), Subtraction (`-`), Multiplication (`*`), Division (`/`), Floor Division (`//`), Modulo (`%`), Exponentiation (`**`).

### **Examples**
```python
print(10 + 5)  # 15
print(10 / 3)  # 3.3333 (float division)
print(10 // 3)  # 3 (floor division)
print(10 % 3)  # 1 (remainder)
print(2 ** 3)  # 8 (2 raised to the power of 3)
```

## **6. Comparison Operators**
- Used to compare values: `>`, `<`, `>=`, `<=`, `==`, `!=`.
- Returns a boolean value (`True` or `False`).
    ```python
    print(10 > 5)  # True
    print(10 == 5)  # False
    print("abc" > "xyz")  # Lexicographical comparison
    ```

## **7. Type Conversion**
- Convert between data types using built-in functions: `int()`, `float()`, `str()`, etc.
    ```python
    print(int("10", 2))  # Convert binary "10" to decimal (2)
    print(hex(255))  # Convert to hexadecimal
    print(bin(10))  # Convert to binary
    ```

## **8. Functions**
### **Example 1: ASCII Distance**
- Calculate the distance between ASCII values of two characters.
    ```python
    def ascii_distance(first, second):
        """
        Returns the positive distance between ASCII values of input characters.
        """
        return abs(ord(first) - ord(second))
    ```
    **Tests:**
    ```python
    assert ascii_distance("a", "b") == 1
    assert ascii_distance("A", "a") == 32
    ```

### **Example 2: Binary Conversion**
- Convert a number to binary without the `0b` prefix.
    ```python
    def get_binary(number):
        """
        Return the binary string of a number without the 0b prefix.
        """
        return bin(number)[2:]
    ```
    **Tests:**
    ```python
    assert get_binary(5) == "101"
    assert get_binary(255) == "11111111"
    ```

### **Example 3: Base-36 to Binary**
- Convert a base-36 string to binary.
    ```python
    def base36_to_binary(input):
        """
        Convert a base-36 string to binary.
        """
        return bin(int(input, 36))[2:]
    ```
    **Tests:**
    ```python
    assert base36_to_binary("A") == "1010"
    assert base36_to_binary("Z") == "100011"
    ```

## **9. Libraries**
- Libraries are reusable code modules, e.g., `pandas`, `math`.
    ```python
    import math
    print(math.sqrt(16))  # 4.0
    ```

## **10. Miscellaneous**
- **`divmod(a, b)`**: Returns a tuple `(quotient, remainder)`.
    ```python
    print(divmod(10, 3))  # (3, 1)
    ```
- **`sys.getsizeof(obj)`**: Get memory size of an object.
    ```python
    import sys
    print(sys.getsizeof(12345))  # Size in bytes
    ```

## **11. Bitwise Operators**
- Perform operations on binary representations: `&`, `|`, `^`, `~`, `<<`, `>>`.
    ```python
    print(5 & 3)  # AND
    print(5 | 3)  # OR
    print(5 ^ 3)  # XOR
    ```

For more details, refer to the [Python documentation](https://docs.python.org/3/library/functions.html).

--- 

This format is concise and uses examples to clarify concepts, making it suitable for tutorials. Let me know if you'd like further refinements!