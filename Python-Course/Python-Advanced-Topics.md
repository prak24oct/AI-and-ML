# 📚 Python Advanced Topics

## 1. File I/O

### Reading Files

```python
# Basic file reading
with open('file.txt', 'r') as file:
    content = file.read()

# Reading line by line
with open('file.txt', 'r') as file:
    for line in file:
        print(line.strip())

# Reading specific number of characters
with open('file.txt', 'r') as file:
    chunk = file.read(100)  # Read first 100 characters
```

### Writing Files

```python
# Basic file writing
with open('file.txt', 'w') as file:
    file.write('Hello, World!')

# Appending to file
with open('file.txt', 'a') as file:
    file.write('\nNew line')

# Writing multiple lines
lines = ['Line 1', 'Line 2', 'Line 3']
with open('file.txt', 'w') as file:
    file.write('\n'.join(lines))
```

### File Modes

```python
# Common file modes
'r'  # Read (default)
'w'  # Write (truncate)
'a'  # Append
'x'  # Exclusive creation
'b'  # Binary mode
't'  # Text mode (default)
'+'  # Update (read/write)
```

## 2. Modules and Packages

### Creating Modules

```python
# mymodule.py
def greet(name):
    return f"Hello, {name}!"

def add(a, b):
    return a + b

if __name__ == "__main__":
    print("This runs when module is executed directly")
```

### Importing Modules

```python
# Import entire module
import math
print(math.sqrt(16))

# Import specific functions
from math import sqrt, pi
print(sqrt(16))
print(pi)

# Import with alias
import numpy as np
import pandas as pd

# Import all (not recommended)
from math import *
```

### Creating Packages

```python
# Directory structure
mypackage/
    __init__.py
    module1.py
    module2.py
    subpackage/
        __init__.py
        module3.py

# __init__.py can be empty or contain:
__version__ = '1.0'
from .module1 import *
from .module2 import *
```

## 3. Standard Library

### Common Modules

```python
# os - Operating system interface
import os
print(os.getcwd())
os.mkdir('new_dir')

# sys - System-specific parameters
import sys
print(sys.version)
print(sys.argv)

# datetime - Date and time
from datetime import datetime
now = datetime.now()
print(now.strftime("%Y-%m-%d %H:%M:%S"))

# json - JSON data handling
import json
data = {'name': 'John', 'age': 30}
json_str = json.dumps(data)
parsed = json.loads(json_str)

# random - Random number generation
import random
print(random.randint(1, 10))
print(random.choice(['a', 'b', 'c']))

# re - Regular expressions
import re
pattern = r'\d+'
matches = re.findall(pattern, '123 abc 456')
```

## 4. Virtual Environments

### Creating and Managing

```bash
# Create virtual environment
python -m venv myenv

# Activate (Windows)
myenv\Scripts\activate

# Activate (Unix/MacOS)
source myenv/bin/activate

# Deactivate
deactivate
```

### Requirements Management

```bash
# Generate requirements.txt
pip freeze > requirements.txt

# Install from requirements.txt
pip install -r requirements.txt
```

## 5. Testing

### Unit Testing

```python
import unittest

def add(a, b):
    return a + b

class TestAdd(unittest.TestCase):
    def test_add_positive(self):
        self.assertEqual(add(2, 3), 5)

    def test_add_negative(self):
        self.assertEqual(add(-1, -1), -2)

    def test_add_zero(self):
        self.assertEqual(add(0, 0), 0)

if __name__ == '__main__':
    unittest.main()
```

### pytest

```python
# test_example.py
def test_add():
    assert add(2, 3) == 5

def test_add_negative():
    assert add(-1, -1) == -2

# Run with pytest
# pytest test_example.py
```

## 6. Debugging

### pdb - Python Debugger

```python
import pdb

def complex_function():
    pdb.set_trace()  # Set breakpoint
    # Rest of the code
```

### Common Debugging Commands

```python
# In pdb shell
n  # Next line
s  # Step into
c  # Continue
p  # Print variable
l  # List code
q  # Quit
```

## 7. Logging

### Basic Logging

```python
import logging

# Configure logging
logging.basicConfig(
    level=logging.INFO,
    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s'
)

# Create logger
logger = logging.getLogger(__name__)

# Log messages
logger.debug("Debug message")
logger.info("Info message")
logger.warning("Warning message")
logger.error("Error message")
logger.critical("Critical message")
```

## 8. Performance Optimization

### Profiling

```python
import cProfile

def slow_function():
    # Some slow code
    pass

# Profile the function
cProfile.run('slow_function()')
```

### Memory Profiling

```python
from memory_profiler import profile

@profile
def memory_intensive_function():
    # Memory intensive code
    pass
```

## 9. Best Practices

### Code Organization

```python
# Follow PEP 8 style guide
# Use meaningful names
# Write docstrings
# Keep functions small and focused
# Use type hints
```

### Error Handling

```python
# Be specific with exceptions
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")

# Use context managers for resources
with open('file.txt', 'r') as file:
    content = file.read()
```

### Documentation

```python
def complex_function(param1: int, param2: str) -> float:
    """
    Brief description of the function.

    Args:
        param1: Description of first parameter
        param2: Description of second parameter

    Returns:
        Description of return value

    Raises:
        ValueError: If parameters are invalid
    """
    pass
```

---

This file covers advanced Python topics including file I/O, modules, standard library, virtual environments, testing, and debugging. For more basic topics, refer to the other consolidated files in this series.
