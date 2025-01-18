Here's a detailed review of the lecture notes on Python components, including all the provided concepts and code examples:

---

## **Components of Python**

### **1. Literals**
Literals are fixed values assigned to variables or used directly in Python. They can be of various types:
- **Integer Literals**: Values without decimal points.  
  Examples: `99`, `99999`, `-99999`, `0`, `5`
- **Float Literals**: Values with decimal points.  
  Examples: `99.0`, `100.99999`, `-9999.999`
- **String Literals**: Text enclosed in single, double, or triple quotes.  
  Examples: `'True'`, `"afsaan"`, `"""hello"""`, `'''world'''`
- **Boolean Literals**: `True` and `False`.  
  Examples: `True`, `False`
- **Complex Literals**: Numbers in the form `a + bj`, where `a` is the real part and `b` is the imaginary part.  
  Example: `12 + 2j`
- **None Literal**: Represents the absence of a value.  
  Example: `None`

#### **Code Examples:**
```python
complx = 12 + 2j  # Complex literal
print('12asd')    # String literal
print('''hello''')  # String literal
True  # Boolean literal
False  # Boolean literal
```

---

### **2. Constants and Variables**
- **Constants**: Fixed values that do not change during program execution. Python does not have a native way to declare constants but uses naming conventions (e.g., uppercase variable names).
- **Variables**: Containers for storing data that can change during program execution.

---

### **3. Identifiers**
Identifiers are names used to identify variables, constants, functions, classes, etc.

#### **Rules for Identifiers:**
1. Can use `a-z`, `A-Z`, `0-9`, `_`.
2. Cannot use special characters (`@`, `#`, `-`, etc.).
3. Cannot start with a number.
4. Are case-sensitive.
5. Can be of any length.
6. Cannot use reserved words (keywords).

#### **Code Examples:**
```python
abc = 1
__abc__ = 2
_abc = 3
abc_ = 4
a_b_c = 5

a = 10
A = 20
print(a)  # 10
print(A)  # 20
```

---

### **4. Reserved Words (Keywords)**
Reserved words are predefined and used for specific purposes in Python. They cannot be used as identifiers.

#### **Types of Keywords:**
- **Value Keywords**: `True`, `False`, `None`
- **Operator Keywords**: `and`, `or`, `not`, `in`, `is`
- **Control Flow Keywords**: `if`, `elif`, `else`
- **Iterator Keywords**: `for`, `while`, `break`, `continue`
- **Structural Keywords**: `def`, `class`, `pass`, `with`, `lambda`, `as`
- **Return Keywords**: `return`, `yield`
- **Import Keywords**: `import`, `from`, `as`
- **Exception Handling Keywords**: `try`, `except`, `raise`, `finally`, `assert`

#### **Code Examples:**
```python
import keyword
print(keyword.kwlist)  # List of all keywords
print(keyword.iskeyword("try"))  # Check if "try" is a keyword
```

---

### **5. Statements and Expressions**
- **Expression**: Produces a value.  
  Examples: `10`, `"hello" + 'world'`, `10 + 20`
- **Statement**: Executes an action but does not necessarily produce a value.  
  Example: `a = 10`

#### **Code Examples:**
```python
10  # Expression
"hello" + "world"  # Expression
a = 10  # Statement

for i in range(5):  # Statement
    pass
```

---

### **6. Blocks and Indentation**
Python uses indentation to define blocks of code. Each block must have consistent indentation.

#### **Code Examples:**
```python
print('hi')
print('hello')
if 10 > 2:
    print('inside if')
    print('inside if 1')
print('bye')
print('see you')
```
**Output:**
```
hi
hello
inside if
inside if 1
bye
see you
```

---


---

### **7. Libraries**
Python libraries provide reusable code for various functionalities, similar to `#include` in C.

#### **Code Example:**
```python
import keyword
print(keyword.kwlist)  # Print all Python keywords
```

---

### **File Types**
- **Python files**: `.py` (used in all environments)
- **Interactive Python notebooks**: `.ipynb` (used with Anaconda)

---

This review captures the concepts, rules, and examples provided in the lecture notes, offering a comprehensive summary for study and reference.