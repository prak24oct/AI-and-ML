# 📚 Python Object-Oriented Programming & Advanced Concepts

## 1. Classes and Objects

### Basic Class Definition

```python
class Dog:
    # Class attribute
    species = "Canis familiaris"

    def __init__(self, name, age):
        # Instance attributes
        self.name = name
        self.age = age

    # Instance method
    def description(self):
        return f"{self.name} is {self.age} years old"

    # Another instance method
    def speak(self, sound):
        return f"{self.name} says {sound}"
```

### Creating Objects

```python
# Create instances
buddy = Dog("Buddy", 9)
miles = Dog("Miles", 4)

# Access attributes
print(buddy.name)  # Buddy
print(buddy.age)   # 9

# Call methods
print(buddy.description())  # Buddy is 9 years old
print(buddy.speak("Woof"))  # Buddy says Woof
```

## 2. Inheritance

### Basic Inheritance

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        raise NotImplementedError("Subclass must implement abstract method")

class Dog(Animal):
    def speak(self):
        return f"{self.name} says Woof!"

class Cat(Animal):
    def speak(self):
        return f"{self.name} says Meow!"
```

### Multiple Inheritance

```python
class A:
    def method(self):
        print("A method")

class B:
    def method(self):
        print("B method")

class C(A, B):
    pass

c = C()
c.method()  # A method (due to MRO)
```

## 3. Special Methods

### Magic Methods

```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __repr__(self):
        return f"Vector({self.x}, {self.y})"

    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)

    def __mul__(self, scalar):
        return Vector(self.x * scalar, self.y * scalar)

    def __len__(self):
        return 2

    def __getitem__(self, index):
        if index == 0:
            return self.x
        elif index == 1:
            return self.y
        else:
            raise IndexError("Index out of range")
```

## 4. Properties and Descriptors

### Properties

```python
class Circle:
    def __init__(self, radius):
        self._radius = radius

    @property
    def radius(self):
        return self._radius

    @radius.setter
    def radius(self, value):
        if value < 0:
            raise ValueError("Radius cannot be negative")
        self._radius = value

    @property
    def area(self):
        return 3.14 * self._radius ** 2
```

### Descriptors

```python
class PositiveNumber:
    def __set_name__(self, owner, name):
        self.name = name

    def __get__(self, obj, objtype=None):
        return obj.__dict__[self.name]

    def __set__(self, obj, value):
        if value < 0:
            raise ValueError("Value cannot be negative")
        obj.__dict__[self.name] = value

class Person:
    age = PositiveNumber()
    height = PositiveNumber()
```

## 5. Abstract Base Classes

### ABC Module

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

    @abstractmethod
    def perimeter(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

    def perimeter(self):
        return 2 * (self.width + self.height)
```

## 6. Context Managers

### Using with Statement

```python
# Using context manager
with open('file.txt', 'r') as file:
    content = file.read()

# Custom context manager
class FileHandler:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode

    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file

    def __exit__(self, exc_type, exc_val, exc_tb):
        self.file.close()

# Using custom context manager
with FileHandler('file.txt', 'r') as file:
    content = file.read()
```

## 7. Metaclasses

### Basic Metaclass

```python
class Meta(type):
    def __new__(cls, name, bases, dct):
        print(f"Creating class {name}")
        return super().__new__(cls, name, bases, dct)

class MyClass(metaclass=Meta):
    pass
```

## 8. Advanced Concepts

### Class Methods and Static Methods

```python
class MyClass:
    @classmethod
    def class_method(cls):
        print(f"Called class method of {cls.__name__}")

    @staticmethod
    def static_method():
        print("Called static method")

# Usage
MyClass.class_method()
MyClass.static_method()
```

### Data Classes

```python
from dataclasses import dataclass

@dataclass
class Point:
    x: float
    y: float
    z: float = 0.0  # Default value

    def distance(self):
        return (self.x**2 + self.y**2 + self.z**2)**0.5
```

## 9. Best Practices

### Class Design

```python
# Use meaningful names
class BankAccount:
    def __init__(self, account_number, balance):
        self.account_number = account_number
        self.balance = balance

# Use type hints
class Employee:
    def __init__(self, name: str, age: int, salary: float):
        self.name = name
        self.age = age
        self.salary = salary

# Document classes
class Rectangle:
    """
    A class representing a rectangle.

    Attributes:
        width: The width of the rectangle
        height: The height of the rectangle
    """
    def __init__(self, width: float, height: float):
        self.width = width
        self.height = height
```

### Inheritance Best Practices

```python
# Use composition over inheritance
class Engine:
    def start(self):
        print("Engine started")

class Car:
    def __init__(self):
        self.engine = Engine()

    def start(self):
        self.engine.start()

# Use abstract base classes for interfaces
from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def speak(self):
        pass
```

### Magic Methods Best Practices

```python
# Implement __repr__ for debugging
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __repr__(self):
        return f"Point({self.x}, {self.y})"

# Use __str__ for user-friendly output
    def __str__(self):
        return f"Point at ({self.x}, {self.y})"
```

## 10. Design Patterns

### Singleton Pattern

```python
class Singleton:
    _instance = None

    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance
```

### Factory Pattern

```python
class AnimalFactory:
    @staticmethod
    def create_animal(animal_type):
        if animal_type == "dog":
            return Dog()
        elif animal_type == "cat":
            return Cat()
        else:
            raise ValueError(f"Unknown animal type: {animal_type}")
```

### Observer Pattern

```python
class Subject:
    def __init__(self):
        self._observers = []

    def attach(self, observer):
        self._observers.append(observer)

    def notify(self):
        for observer in self._observers:
            observer.update(self)

class Observer:
    def update(self, subject):
        pass
```

---

This file covers essential object-oriented programming and advanced concepts in Python. For more basic topics, refer to the other consolidated files in this series.
