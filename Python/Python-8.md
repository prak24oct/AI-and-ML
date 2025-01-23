### **Comprehensions in Python**

**Definition:**  
Comprehensions are concise, one-line constructs in Python that can replace loops to create new sequences (like lists, dictionaries, or sets) by applying an expression to each element in an iterable.

---

### **Types of Comprehensions:**
1. **List Comprehension**
2. **Dictionary Comprehension**
3. **Set Comprehension**

---

### **Advantages of Comprehensions:**
- **Compact and Pythonic:** Comprehensions allow writing concise and readable code compared to traditional loops.
- **Faster Execution:** For simple operations, comprehensions are generally faster than using loops.

---

### **Disadvantages of Comprehensions:**
- **Reduced Readability:** Complex comprehensions can make code harder to read and understand.
- **Performance Issues:** Comprehensions with multiple conditions or nested loops may perform slower than traditional loops.

---

### **Examples and Explanations:**

#### **List Comprehension**

**Example 1: Squaring Numbers in a List**
```python
list_nums = [1, 2, 3, 4]
op_list = [i * i for i in list_nums]  # Output: [1, 4, 9, 16]
```

Equivalent using a loop:
```python
op_list = []
for i in list_nums:
    op_list.append(i * i)
```

---

**Example 2: Multiplying Numbers by 20**
```python
a = [10, 21, 24, 54, 64]
res = [num * 20 for num in a]  # Output: [200, 420, 480, 1080, 1280]
```

---

**Example 3: Filtering Even Numbers**
```python
rand_list = list(range(50, 150))
even_nums = [num for num in rand_list if num % 2 == 0]
```

Equivalent using a loop:
```python
even_nums = []
for num in rand_list:
    if num % 2 == 0:
        even_nums.append(num)
```

---

**Example 4: Nested Loops in Comprehensions**
```python
list1 = [1, 2]
list2 = [4, 5]
combinedList = [(i, j) for i in list1 for j in list2]  # Output: [(1, 4), (1, 5), (2, 4), (2, 5)]
```

Equivalent using nested loops:
```python
combinedList = []
for i in list1:
    for j in list2:
        combinedList.append((i, j))
```

---

**Example 5: Conditional Expressions in Comprehensions**
```python
some_list = [1, 4, 7, 12, 19, 22, 23, 26]
[print(ele, 'even') if ele % 2 == 0 else print(ele, 'odd') for ele in some_list]
```

---

**Example 6: Combining Multiple Loops and Conditions**
```python
result = [(x + y) for x in range(3) for y in range(3) if (x + y) % 2 == 0]
# Output: [(0, 0), (0, 2), (1, 1), (2, 0), (2, 2)]
```

---

#### **Dictionary Comprehension**

**Example 1: Mapping Numbers to Letters**
```python
result = {i: chr(65 + i) for i in range(4)}  # Output: {0: 'A', 1: 'B', 2: 'C', 3: 'D'}
```

Equivalent using a loop:
```python
result = {}
for i in range(4):
    result[i] = chr(65 + i)
```

---

**Example 2: Reversing Keys and Values**
```python
result = {k: v for v, k in result.items()}  # Reverses keys and values
```

---

**Example 3: Mapping Letters to Their Positions**
```python
import string
result = {x: ord(x) - ord('A') + 1 for x in string.ascii_uppercase[:5]}
# Output: {'A': 1, 'B': 2, 'C': 3, 'D': 4, 'E': 5}
```

---

**Example 4: Filtering with Conditions**
```python
result = {x: x**2 for x in range(5) if x % 2 == 1}
# Output: {1: 1, 3: 9}
```

---

#### **Set Comprehension**

**Example 1: Creating a Set with Doubled Values**
```python
result = {x * 2 for x in range(4)}  # Output: {0, 2, 4, 6}
```

---

### **Additional Notes:**

1. **Break and Continue in Comprehensions:**  
   These statements cannot be used directly in comprehensions. If needed, use loops instead.

2. **Generator Expressions:**  
   Similar to list comprehensions but return a generator object instead of a list.
   ```python
   result = (i * i for i in range(4))  # Creates a generator object
   ```

3. **Tips for Using Comprehensions:**
   - Use comprehensions for simple, concise operations.
   - Avoid using them for complex logic to maintain code readability.
   - Always test the performance of comprehensions vs loops for large datasets.

---
#### Here are detailed notes on comprehensions in Python for **list**, **dictionary**, and **tuple** covering the scenarios you mentioned, along with additional examples for a comprehensive understanding.


### 1. **List Comprehension**

#### a) **With Simple `if`**
```python
# Example: Extract even numbers from a list
numbers = [1, 2, 3, 4, 5, 6]
even_numbers = [num for num in numbers if num % 2 == 0]
print(even_numbers)  # Output: [2, 4, 6]
```

#### b) **With Simple `if` and `else`**
```python
# Example: Mark numbers as "Even" or "Odd"
numbers = [1, 2, 3, 4, 5, 6]
labels = ["Even" if num % 2 == 0 else "Odd" for num in numbers]
print(labels)  # Output: ['Odd', 'Even', 'Odd', 'Even', 'Odd', 'Even']
```

#### c) **With Nested `if` and `else`**
```python
# Example: Categorize numbers as "Small Even", "Small Odd", or "Large"
numbers = [1, 2, 15, 18, 7, 8]
categories = [
    "Small Even" if num < 10 and num % 2 == 0 
    else "Small Odd" if num < 10 
    else "Large" 
    for num in numbers
]
print(categories)  # Output: ['Small Odd', 'Small Even', 'Large', 'Large', 'Small Odd', 'Small Even']
```

#### d) **Other Variations**
- **With multiple loops**:
```python
# Example: Generate coordinate pairs
coordinates = [(x, y) for x in range(3) for y in range(2)]
print(coordinates)  # Output: [(0, 0), (0, 1), (1, 0), (1, 1), (2, 0), (2, 1)]
```

---

### 2. **Dictionary Comprehension**

#### a) **With Simple `if`**
```python
# Example: Filter dictionary for even values
numbers = {'a': 1, 'b': 2, 'c': 3, 'd': 4}
even_numbers = {key: value for key, value in numbers.items() if value % 2 == 0}
print(even_numbers)  # Output: {'b': 2, 'd': 4'}
```

#### b) **With Simple `if` and `else`**
```python
# Example: Map values to "Even" or "Odd"
numbers = {'a': 1, 'b': 2, 'c': 3, 'd': 4}
labels = {key: "Even" if value % 2 == 0 else "Odd" for key, value in numbers.items()}
print(labels)  # Output: {'a': 'Odd', 'b': 'Even', 'c': 'Odd', 'd': 'Even'}
```

#### c) **With Nested `if` and `else`**
```python
# Example: Categorize numbers based on value
numbers = {'a': 5, 'b': 15, 'c': 8, 'd': 3}
categories = {
    key: "Small" if value < 10 
    else "Medium" if value < 20 
    else "Large" 
    for key, value in numbers.items()
}
print(categories)  # Output: {'a': 'Small', 'b': 'Medium', 'c': 'Small', 'd': 'Small'}
```

#### d) **Other Variations**
- **Inverting keys and values**:
```python
# Example: Swap keys and values
numbers = {'a': 1, 'b': 2, 'c': 3}
inverted = {value: key for key, value in numbers.items()}
print(inverted)  # Output: {1: 'a', 2: 'b', 3: 'c'}
```

---

### 3. **Tuple Comprehension**

#### Note: Tuple comprehensions do not exist directly. Instead, a generator expression is used to create tuples.

#### a) **With Simple `if`**
```python
# Example: Extract even numbers into a tuple
numbers = [1, 2, 3, 4, 5, 6]
even_numbers = tuple(num for num in numbers if num % 2 == 0)
print(even_numbers)  # Output: (2, 4, 6)
```

#### b) **With Simple `if` and `else`**
```python
# Example: Mark numbers as "Even" or "Odd" in a tuple
numbers = [1, 2, 3, 4, 5, 6]
labels = tuple("Even" if num % 2 == 0 else "Odd" for num in numbers)
print(labels)  # Output: ('Odd', 'Even', 'Odd', 'Even', 'Odd', 'Even')
```

#### c) **With Nested `if` and `else`**
```python
# Example: Categorize numbers into a tuple
numbers = [1, 2, 15, 18, 7, 8]
categories = tuple(
    "Small Even" if num < 10 and num % 2 == 0 
    else "Small Odd" if num < 10 
    else "Large" 
    for num in numbers
)
print(categories)  # Output: ('Small Odd', 'Small Even', 'Large', 'Large', 'Small Odd', 'Small Even')
```

#### d) **Other Variations**
- **With multiple loops**:
```python
# Example: Generate coordinate pairs as a tuple
coordinates = tuple((x, y) for x in range(3) for y in range(2))
print(coordinates)  # Output: ((0, 0), (0, 1), (1, 0), (1, 1), (2, 0), (2, 1))
```

---

### Summary Table of Comprehensions

| Type          | Data Structure | Example Use Case                               |
|---------------|----------------|-----------------------------------------------|
| **List**      | `[]`           | Filtering or transforming lists               |
| **Dictionary**| `{}`           | Mapping keys to values or transforming values |
| **Tuple**     | `()` (via generator) | Creating immutable sequences with conditions |

These examples demonstrate how comprehensions simplify the creation of lists, dictionaries, and tuples (via generators) with conditional logic and looping constructs.

---
### Python Functions - Comprehensive Revision Notes :

### **Definition and Purpose**
A **function** is a block of organized, reusable code that performs a specific task. Functions allow programs to be modular, reducing redundancy and improving readability. They help in decomposing complex problems into smaller, manageable pieces.

### **Syntax of a Function**

```python
def function_name(parameters):
    """
    Docstring
    """
    Statement(s)
```

1. **`def` keyword**: Marks the start of the function definition.
2. **Function name**: Should be descriptive and adhere to Python naming conventions.
3. **Parameters**: Optional variables passed to the function for processing.
4. **Colon (`:`)**: Indicates the end of the function header.
5. **Docstring**: Optional, used for documenting the purpose of the function.
6. **Statements**: The body of the function that performs the defined task.
7. **Return statement**: Optional, returns a value to the caller.

---

### **Example**

```python
def print_name(name):
    """
    This function gives a customized greeting message.
    Input: name (str) - Name of the user
    Output: None
    """
    print("Hello " + str(name))

# Function call
print_name('Kohli')
```

---

### **Docstring**
- The first string after the function header is the **docstring**.
- It documents what the function does, its inputs, and outputs.
- Written in triple quotes (`"""`) to support multi-line text.

Example:

```python
print(print_name.__doc__)  # Prints the docstring of the function
```

---

### **Return Statement**

- The **`return`** statement exits the function and optionally sends a value back to the caller.

**Syntax**:
```python
return [expression]
```

- If no `return` statement is present, the function returns `None`.

Example:

```python
def get_sum(lst):
    """
    Returns the sum and length of a list.
    """
    total = 0
    for num in lst:
        total += num
    return total, len(lst)

result = get_sum([1, 2, 3, 4])
print(result)  # Output: (10, 4)
```

---

### **Types of Functions**

1. **Built-in Functions**: Predefined in Python, e.g., `sum()`, `min()`, `max()`, `range()`.
2. **User-defined Functions**: Created by users for specific tasks.

---

### **Advantages of User-defined Functions**

1. Decomposes large programs into smaller segments.
2. Avoids repetition by reusing code.
3. Simplifies debugging and maintenance.
4. Enables collaboration by dividing tasks into functions.

---

### **Function Examples**

#### 1. Simple Function
```python
def product_numbers(a, b):
    """
    Returns the product of two numbers.
    """
    return a * b

print(product_numbers(10, 20))  # Output: 200
```

#### 2. Check Even or Odd
```python
def odd_even(num):
    if num % 2 == 0:
        print("Even")
    else:
        print("Odd")

odd_even(34)  # Output: Even
```

#### 3. Default Arguments
```python
def greet(name, msg="Good Morning"):
    """
    Greets a person with the provided message.
    Defaults to "Good Morning" if no message is provided.
    """
    print(f"Hello {name}, {msg}")

greet("Kohli")  # Output: Hello Kohli, Good Morning
greet("Kohli", "All the best for Asia Cup 22")
```

---

### **Types of Arguments**

1. **Positional Arguments**: Order matters, and the number of arguments must match the parameters.

   Example:
   ```python
   def employee(name, age, salary):
       print(name, age, salary)

   employee('Kohli', 30, 50000)
   ```

2. **Default Arguments**: Provide default values for parameters.

   Example:
   ```python
   def employee(name, age, salary, location='Bangalore'):
       print(name, age, salary, location)

   employee('Mesh', 24, 46000)  # Uses default location
   employee('Mesh', 24, 46000, 'Hyderabad')  # Overrides default
   ```

3. **Keyword Arguments**: Parameters are specified by name, improving readability.

   Example:
   ```python
   def calculation(a, b, c=0, d=0):
       result = a * b - c + d
       print(result)

   calculation(a=3, b=2, c=4)
   ```

4. **Variable-length Arguments**:
   - **`*args`**: Non-keyworded variable arguments.
   - **`**kwargs`**: Keyworded variable arguments.

   Examples:
   ```python
   def add(*args):
       return sum(args)

   print(add(1, 2, 3))  # Output: 6

   def greet(**kwargs):
       print(kwargs)

   greet(name="Kohli", msg="Good Night")  # Output: {'name': 'Kohli', 'msg': 'Good Night'}
   ```

---

### **Practical Functions**

#### Factorial Function
```python
def factorial(num):
    fact = 1
    for i in range(1, num + 1):
        fact *= i
    return fact

print(factorial(5))  # Output: 120
```

#### Arithmetic Sum
```python
def sum_arithmetic(*args):
    return sum(args)

print(sum_arithmetic(1, 2, 3, 4))  # Output: 10
```

#### Simple Calculator
```python
def calculator(a, b, operation):
    if operation == 'add':
        return a + b
    elif operation == 'subtract':
        return a - b
    elif operation == 'multiply':
        return a * b
    elif operation == 'divide':
        return a / b
    else:
        return "Invalid operation"

print(calculator(10, 5, 'add'))  # Output: 15
```

---

### **Best Practices**

1. **Use descriptive names** for functions and parameters.
2. Always document your functions with **docstrings**.
3. Keep functions **short and focused** on a single task.
4. Use **default arguments** to handle optional parameters.
5. Avoid using **global variables** inside functions.

---

This comprehensive guide covers the foundational and advanced aspects of Python functions, making it a valuable resource for in-depth revision and practical application.

---

### **Difference Between *args and **kwargs in Python

The key difference between `*args` and `**kwargs` lies in the data structure used to store the arguments. `*args` collects all positional arguments passed to the function into a **tuple**, which is ordered and accessed using indices. In contrast, `**kwargs` gathers all keyword arguments into a **dictionary**, where each argument is stored as a key-value pair, allowing access by key. This distinction makes `*args` suitable for handling an ordered list of arguments, while `**kwargs` is ideal for managing named arguments with flexible names.

--- 
