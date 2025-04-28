# 📚 Python Control Flow & Functions

## 1. Conditional Statements

### if-elif-else

```python
# Basic if statement
age = 18
if age >= 18:
    print("You are an adult")

# if-else statement
if age >= 18:
    print("You are an adult")
else:
    print("You are a minor")

# if-elif-else statement
score = 85
if score >= 90:
    print("Grade: A")
elif score >= 80:
    print("Grade: B")
elif score >= 70:
    print("Grade: C")
else:
    print("Grade: F")
```

### Ternary Operator

```python
# Traditional if-else
if age >= 18:
    status = "adult"
else:
    status = "minor"

# Ternary operator
status = "adult" if age >= 18 else "minor"
```

## 2. Loops

### for Loop

```python
# Basic for loop
for i in range(5):
    print(i)

# Iterating over a list
fruits = ['apple', 'banana', 'orange']
for fruit in fruits:
    print(fruit)

# Using enumerate
for index, fruit in enumerate(fruits):
    print(f"Index: {index}, Fruit: {fruit}")

# Nested loops
for i in range(3):
    for j in range(3):
        print(f"({i}, {j})")
```

### while Loop

```python
# Basic while loop
count = 0
while count < 5:
    print(count)
    count += 1

# Using break
while True:
    user_input = input("Enter 'quit' to exit: ")
    if user_input == 'quit':
        break
    print(f"You entered: {user_input}")

# Using continue
count = 0
while count < 5:
    count += 1
    if count == 3:
        continue
    print(count)
```

### Loop Control Statements

```python
# break statement
for i in range(10):
    if i == 5:
        break
    print(i)

# continue statement
for i in range(10):
    if i % 2 == 0:
        continue
    print(i)

# else clause
for i in range(5):
    print(i)
else:
    print("Loop completed")
```

## 3. Functions

### Function Definition

```python
# Basic function
def greet():
    print("Hello, World!")

# Function with parameters
def greet(name):
    print(f"Hello, {name}!")

# Function with default parameters
def greet(name="World"):
    print(f"Hello, {name}!")

# Function with return value
def add(a, b):
    return a + b
```

### Function Arguments

```python
# Positional arguments
def describe_pet(animal_type, pet_name):
    print(f"I have a {animal_type} named {pet_name}")

# Keyword arguments
describe_pet(animal_type="hamster", pet_name="Harry")
describe_pet(pet_name="Harry", animal_type="hamster")

# Arbitrary arguments
def make_pizza(*toppings):
    print("Making a pizza with:")
    for topping in toppings:
        print(f"- {topping}")

# Arbitrary keyword arguments
def build_profile(first, last, **user_info):
    profile = {}
    profile['first_name'] = first
    profile['last_name'] = last
    for key, value in user_info.items():
        profile[key] = value
    return profile
```

### Lambda Functions

```python
# Basic lambda
square = lambda x: x ** 2
print(square(5))  # 25

# Lambda with multiple arguments
add = lambda x, y: x + y
print(add(3, 4))  # 7

# Using lambda with filter
numbers = [1, 2, 3, 4, 5]
evens = list(filter(lambda x: x % 2 == 0, numbers))

# Using lambda with map
squares = list(map(lambda x: x ** 2, numbers))
```

## 4. Exception Handling

### try-except

```python
# Basic try-except
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")

# Multiple exceptions
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
except ValueError:
    print("Invalid value")

# Generic exception
try:
    result = 10 / 0
except Exception as e:
    print(f"An error occurred: {e}")

# else clause
try:
    result = 10 / 2
except ZeroDivisionError:
    print("Cannot divide by zero")
else:
    print(f"Result: {result}")

# finally clause
try:
    result = 10 / 2
except ZeroDivisionError:
    print("Cannot divide by zero")
finally:
    print("This will always execute")
```

### Raising Exceptions

```python
# Raise exception
def validate_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative")
    return age

# Custom exception
class InvalidAgeError(Exception):
    pass

def validate_age(age):
    if age < 0:
        raise InvalidAgeError("Age cannot be negative")
    return age
```

## 5. Generators

### Generator Functions

```python
# Basic generator
def count_up_to(n):
    i = 1
    while i <= n:
        yield i
        i += 1

# Using generator
for number in count_up_to(5):
    print(number)

# Generator expression
squares = (x**2 for x in range(5))
for square in squares:
    print(square)
```

### Generator Methods

```python
def number_generator():
    yield 1
    yield 2
    yield 3

gen = number_generator()
print(next(gen))  # 1
print(next(gen))  # 2
print(next(gen))  # 3
```

## 6. Decorators

### Basic Decorator

```python
def my_decorator(func):
    def wrapper():
        print("Something is happening before the function is called.")
        func()
        print("Something is happening after the function is called.")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
```

### Decorator with Arguments

```python
def repeat(num_times):
    def decorator_repeat(func):
        def wrapper(*args, **kwargs):
            for _ in range(num_times):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator_repeat

@repeat(num_times=3)
def greet(name):
    print(f"Hello {name}")

greet("World")
```

## 7. Best Practices

### Function Best Practices

```python
# Use meaningful names
def calculate_area(width, height):
    return width * height

# Use type hints
def greet(name: str) -> str:
    return f"Hello, {name}!"

# Document functions
def add(a: float, b: float) -> float:
    """
    Add two numbers together.

    Args:
        a: First number
        b: Second number

    Returns:
        Sum of a and b
    """
    return a + b
```

### Loop Best Practices

```python
# Use enumerate for index and value
for index, value in enumerate(items):
    print(f"Index: {index}, Value: {value}")

# Use zip for parallel iteration
names = ['Alice', 'Bob', 'Charlie']
ages = [25, 30, 35]
for name, age in zip(names, ages):
    print(f"{name} is {age} years old")

# Use list comprehensions when possible
squares = [x**2 for x in range(10)]
```

### Exception Handling Best Practices

```python
# Be specific with exceptions
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")

# Don't catch all exceptions
try:
    result = 10 / 0
except Exception:  # Too broad
    print("An error occurred")

# Use finally for cleanup
file = open('example.txt', 'r')
try:
    content = file.read()
finally:
    file.close()
```

---

This file covers essential control flow and function concepts in Python. For more advanced topics, refer to the other consolidated files in this series.
