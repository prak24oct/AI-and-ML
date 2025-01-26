### Python Built-in Exceptions and Exception Handling

Python provides a comprehensive set of built-in exceptions to handle errors and abnormal conditions in programs. These exceptions can be caught and handled using specific constructs to ensure smooth program execution.

---

#### **Built-in Exceptions**

1. **`Exception`**  
   - Base class for all exceptions in Python.
   - All built-in exceptions derive from this class.

2. **`ArithmeticError`**  
   - Base class for errors during numeric calculations.
   - Includes specific exceptions like:
     - **`OverflowError`**: Raised when a numeric calculation exceeds the maximum limit for a numeric type.
     - **`ZeroDivisionError`**: Raised when attempting to divide a number by zero.

3. **`ImportError`**  
   - Raised when an import statement fails to find or load a module.

4. **`KeyboardInterrupt`**  
   - Raised when the user interrupts program execution, typically by pressing `Ctrl+C`.

5. **`IndexError`**  
   - Raised when trying to access an index that is out of range in a sequence (e.g., a list or tuple).

6. **`KeyError`**  
   - Raised when trying to access a dictionary key that does not exist.

7. **`OSError`**  
   - Raised for operating system-related errors, such as file I/O issues.

8. **Other Common Exceptions**:
   - **`ValueError`**: Raised when a function receives an argument of the correct type but inappropriate value.
   - **`TypeError`**: Raised when an operation or function is applied to an object of inappropriate type.

---

#### **Exploring Built-in Exceptions**

To view all built-in exceptions available in Python:

```python
print(dir(locals()['__builtins__']))
```

---

### **Keywords for Exception Handling**

Python provides the following keywords for handling exceptions:

1. **`try`**: Defines a block of code to test for exceptions.
2. **`except`**: Defines a block of code to execute if an exception occurs.
3. **`else`**: Executes code if no exception occurs in the `try` block.
4. **`finally`**: Executes code regardless of whether an exception occurred.
5. **`raise`**: Allows manually raising exceptions.

---

### **Using `try` and `except`**

The `try` block contains code that may raise an exception, while the `except` block contains code to handle the exception.

**Example**:

```python
try:
    num1 = int(input('Enter the first number: '))
    num2 = int(input('Enter the second number: '))
    print(num1 / num2)
except ZeroDivisionError:
    print('Division by zero is not allowed.')
except ValueError:
    print('Please enter a valid number.')
```

---

### **`try`-`except`-`else`**

The `else` block runs if no exception occurs in the `try` block.

**Example**:

```python
try:
    num1 = int(input('Enter the first number: '))
    num2 = int(input('Enter the second number: '))
    result = num1 / num2
except ZeroDivisionError:
    print('Division by zero is not allowed.')
else:
    print('Result:', result)
```

---

### **`finally` Block**

The `finally` block is executed no matter what, making it useful for cleanup operations like closing files.

**Example**:

```python
try:
    f = open('test.txt', 'w')
    f.write('Hello, world!')
    num = int(input('Enter a number: '))
    result = 100 / num
except ZeroDivisionError:
    print('Cannot divide by zero.')
finally:
    f.close()
    print('File closed.')
```

---

### **Manually Raising Exceptions**

The `raise` keyword allows manually triggering exceptions.

**Example**:

```python
val = int(input("Enter a number: "))
try:
    if val == 2:
        raise ZeroDivisionError
    else:
        print("Value is not 2")
except ZeroDivisionError:
    print("A ZeroDivisionError was raised.")
```

---

### **Handling Multiple Exceptions**

You can handle multiple exceptions in a single `except` block or separate them.

**Example**:

```python
try:
    x = int(input("Enter a number: "))
    result = 100 / x
except (ValueError, ZeroDivisionError):
    print("Invalid input or division by zero.")
else:
    print("Result:", result)
```

---

### **Using Exception Objects**

You can capture exception details using an alias (`as`).

**Example**:

```python
try:
    x = int(input("Enter a number: "))
    result = 100 / x
except Exception as e:
    print("Exception caught:", e)
    print("Type of exception:", type(e))
```

---

### **Practical Examples**

1. **Retry on Exception**:
   Continuously prompt the user until valid input is provided.

   ```python
   while True:
       try:
           a = float(input("Enter the first number: "))
           b = float(input("Enter the second number: "))
           result = a / b
           print("Result:", result)
           break
       except ZeroDivisionError:
           print("Second number cannot be zero. Try again.")
       except ValueError:
           print("Invalid input. Enter numbers only.")
   ```

2. **Iterating Over a List with Exceptions**:

   ```python
   random_list = ['a', 0, 2]
   for entry in random_list:
       try:
           print("Entry:", entry)
           reciprocal = 1 / int(entry)
           break
       except Exception as e:
           print(e.__class__, "occurred. Moving to the next entry.")
   print("Reciprocal of", entry, "is", reciprocal)
   ```

---

### **Custom Exceptions**

Python allows creating user-defined exceptions by inheriting from the `Exception` class.

**Example**:

```python
class CustomError(Exception):
    pass

try:
    raise CustomError("This is a custom exception.")
except CustomError as e:
    print("Caught custom exception:", e)
```

---

### **Logging for Debugging**

For detailed exception handling and debugging, use the `logging` module. Refer to [Real Python's logging guide](https://realpython.com/python-logging/) for more information.

---

### **Conclusion**

Exception handling is a critical feature of Python that ensures programs run smoothly even when unexpected conditions arise. By mastering these concepts, you can write robust and error-tolerant code.

---

Here is a detailed and comprehensive revision of the provided Python notes on classes, enriched with additional concepts, examples, and explanations:

---

# **Classes in Python**

## **Introduction to Classes**

Python is an object-oriented programming language, meaning it organizes code around objects and their interactions. Classes are fundamental building blocks in this paradigm. 

- A **class** acts as a blueprint for creating objects.
- Objects are instances of a class, each with its own properties (attributes) and behaviors (methods).

### **Why Use Classes?**
- **Reusability**: Code written in classes can be reused across different parts of the program.
- **Encapsulation**: Classes encapsulate data and methods, providing better modularity.
- **Abstraction**: They help in hiding implementation details from the user.
- **Inheritance and Polymorphism**: Classes support these advanced OOP features to simplify code and improve maintainability.

---

## **Defining a Class**

A class is defined using the `class` keyword. Here’s a simple example:

```python
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def display_info(self):
        print(f"Name: {self.name}, Age: {self.age}")

# Creating objects (instances)
student1 = Student("Alice", 20)
student2 = Student("Bob", 22)

student1.display_info()
student2.display_info()
```

### **Key Components of a Class**
1. **Attributes**: Variables that hold data about the object.
2. **Methods**: Functions defined within a class to perform operations.
3. **Constructor (`__init__`)**: A special method used to initialize attributes of an object.

---

## **Example: Basic Class**

```python
class Calculator:
    def add(self, a, b):
        return a + b

    def subtract(self, a, b):
        return a - b

# Using the class
calc = Calculator()
print(calc.add(10, 5))        # Output: 15
print(calc.subtract(10, 5))   # Output: 5
```

---

## **The `self` Keyword**

- The `self` keyword represents the instance of the class. 
- It is used to access attributes and methods of the class in Python.
- Although it is a convention to name it `self`, you can use any other valid identifier.

### **Example: Understanding `self`**

```python
class Demo:
    def __init__(self, value):
        self.value = value  # `self.value` refers to the instance variable

    def show_value(self):
        print(f"The value is: {self.value}")

obj = Demo(42)
obj.show_value()  # Output: The value is: 42
```

---

## **Creating Multiple Instances**

You can create multiple objects from a single class definition. Each object has its own copy of attributes.

```python
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age

students = [
    Student("Alice", 20),
    Student("Bob", 22),
    Student("Charlie", 21)
]

for student in students:
    print(f"Name: {student.name}, Age: {student.age}")
```

---

## **Advanced Topics**

### **Class Attributes vs Instance Attributes**

- **Class Attributes**: Shared across all instances of the class.
- **Instance Attributes**: Unique to each instance.

```python
class Demo:
    class_attribute = "Shared"

    def __init__(self, instance_value):
        self.instance_attribute = instance_value

obj1 = Demo("Instance 1")
obj2 = Demo("Instance 2")

print(obj1.class_attribute)  # Output: Shared
print(obj1.instance_attribute)  # Output: Instance 1
```

### **Inheritance**

Inheritance allows a class (child) to inherit attributes and methods from another class (parent).

#### **Single Inheritance**

```python
class Parent:
    def greet(self):
        print("Hello from Parent!")

class Child(Parent):
    def greet_child(self):
        print("Hello from Child!")

child = Child()
child.greet()       # Output: Hello from Parent!
child.greet_child() # Output: Hello from Child!
```

#### **Multiple Inheritance**

```python
class A:
    def feature1(self):
        print("Feature 1")

class B:
    def feature2(self):
        print("Feature 2")

class C(A, B):
    def feature3(self):
        print("Feature 3")

obj = C()
obj.feature1()
obj.feature2()
obj.feature3()
```

---

### **Encapsulation**

Encapsulation restricts access to certain attributes or methods to prevent accidental modification.

- **Private Members**: Prefixed with `__` (double underscore).

```python
class Demo:
    def __init__(self):
        self.__private = "Private"

    def get_private(self):
        return self.__private

obj = Demo()
print(obj.get_private())  # Accessing private member
```

---

### **Polymorphism**

Polymorphism allows methods in different classes to have the same name but behave differently.

```python
class Cat:
    def sound(self):
        print("Meow")

class Dog:
    def sound(self):
        print("Bark")

for animal in [Cat(), Dog()]:
    animal.sound()
```

---

### **Instances as Return Values**

Methods can return class instances, enabling chaining or reuse.

```python
class Demo:
    def __init__(self, value):
        self.value = value

    def increment(self):
        return Demo(self.value + 1)

obj = Demo(5)
new_obj = obj.increment()
print(new_obj.value)  # Output: 6
```

---

### **Examples and Practice**

#### **Basic Calculator**

```python
class Calculator:
    def add(self, a, b):
        return a + b

    def subtract(self, a, b):
        return a - b

calc = Calculator()
print(calc.add(10, 5))        # Output: 15
print(calc.subtract(10, 5))   # Output: 5
```

#### **Inheritance with Overriding**

```python
class Parent:
    def greet(self):
        print("Hello from Parent!")

class Child(Parent):
    def greet(self):
        print("Hello from Child!")

obj = Child()
obj.greet()  # Output: Hello from Child!
```

---

## **Conclusion**

Classes are a powerful way to organize and structure Python programs. By mastering concepts like inheritance, encapsulation, and polymorphism, you can write more modular, reusable, and maintainable code. Practice creating classes, objects, and exploring advanced features to deepen your understanding of Python's object-oriented capabilities.