# Python Programming: Comprehensive Notes on Conditional Statements and Loops

## **Conditional Statements**

Conditional statements allow programs to execute certain blocks of code based on specified conditions. Python supports `if`, `else`, and `elif` constructs for decision-making.

### **Comparison and Logical Operators**
- **Comparison Operators**: `>`, `<`, `==`, `!=`, `>=`, `<=`
- **Logical Operators**: `and`, `or`, `not`
- **Boolean Literals**: `True`, `False`

### **Basic `if` Statement**
```python
a = int(input())  # Example: Input 12
b = int(input())  # Example: Input 10

if a > b:  # Condition: 12 > 10 (True)
    print("a is greater than b")
    b = 15  # Updates b to 15

print("Check is completed")
print(a, b)  # Output: 12, 15
```

### **`if-else` Statement**
```python
a, b = int(input()), int(input())

if a > b:
    print("a is greater than b")
else:
    print("b is greater than or equal to a")

print("Check is completed")
```

### **`if-elif-else` Statement**
```python
a = int(input())
b = int(input())

if a > b:
    print("a is greater than b")
elif a < b:
    print("b is greater than a")
else:
    print("b equals a")

print("Check is completed")
```

#### **Grading System Example**
```python
marks = int(input("Enter marks: "))

if marks >= 90:
    print("10 points")
elif 80 <= marks < 90:
    print("9 points")
elif 70 <= marks < 80:
    print("8 points")
elif 60 <= marks < 70:
    print("7 points")
elif 50 <= marks < 60:
    print("6 points")
elif 40 <= marks < 50:
    print("Pass")
else:
    print("Fail")
```

### **Logical Operators in Conditions**
```python
a = int(input())
b = int(input())

if a > b or a < b:  # True if a is not equal to b
    print("a not equal to b")
else:
    print("b equals a")
```

### **Equality and Inequality Operations**
```python
a = int(input())
b = int(input())

if a == b:
    print("a equals b")
else:
    print("a not equals b")
```

### **Nested `if` Statements**
```python
x = 9

if x > 4:
    print("messi")
    if x > 25:
        print("benzema")
    else:
        print("mbappe")
else:
    print("vinci jr")
```

---

## **Loops**

Loops are used for repetitive execution of a block of code.

### **Types of Loops**
1. **For Loop**: Iterates over a sequence (e.g., list, string, range).
2. **While Loop**: Repeats as long as a condition is `True`.

### **While Loop Syntax**
```python
while <condition>:
    <statements>
```

### **Basic While Loop**
```python
i = 1
while i <= 5:
    print("Hello")
    i += 1  # Increment i
```

### **Summation Examples**

#### **Sum of First N Numbers**
```python
n = int(input("Enter a number: "))
total = 0
for i in range(1, n + 1):
    total += i
print("Sum:", total)
```

#### **Sum of Squares of First N Numbers**
```python
n = int(input("Enter a number: "))
total = 0
for i in range(1, n + 1):
    total += i ** 2
print("Sum of squares:", total)
```

#### **Sum of First N Even Numbers**
```python
n = int(input("Enter a number: "))
total, count, start = 0, 0, 2
while count < n:
    total += start
    start += 2
    count += 1
print("Sum of first", n, "even numbers:", total)
```

### **Build a Simple Calculator**
```python
a = float(input("Enter first number: "))
b = float(input("Enter second number: "))
choice = int(input("Enter 1 for sum, 2 for subtraction, 3 for multiplication, 4 for division: "))

if choice == 1:
    res = a + b
elif choice == 2:
    res = a - b
elif choice == 3:
    res = a * b
elif choice == 4:
    res = a / b
else:
    res = "Invalid choice"
print("Result:", res)
```

### **Max of Three Numbers**
```python
a = int(input())
b = int(input())
c = int(input())

if a >= b and a >= c:
    print(a, "is the largest")
elif b >= c:
    print(b, "is the largest")
else:
    print(c, "is the largest")
```

### **Leap Year Check**
```python
year = int(input("Enter a year: "))

if (year % 4 == 0 and year % 100 != 0) or (year % 400 == 0):
    print("Leap Year")
else:
    print("Not a Leap Year")
```

### **Palindrome Check for Strings**
```python
s = input("Enter a string: ")

if s == s[::-1]:
    print("Palindrome")
else:
    print("Not a Palindrome")
```

---

## **For Loop**

The `for` loop is used to iterate over a sequence (e.g., list, string, range).

### **Basic Syntax**
```python
for <variable> in <sequence>:
    <statements>
```

### **Example: Printing Numbers**
```python
for i in range(1, 6):  # Iterates from 1 to 5
    print(i)
```

### **Example: Iterating Over a List**
```python
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
```

---

## **While Loop**

The `while` loop executes as long as the given condition evaluates to `True`.

### **Basic Syntax**
```python
while <condition>:
    <statements>
```

### **Example: Print "Hello" Multiple Times**
```python
i = 1
while i <= 5:  # Condition: i is less than or equal to 5
    print("Hello")
    i += 1  # Increment i by 1
```

### **Why Use Loops Instead of Repetition?**
Consider the task of printing "Hello" 100 times. Writing 100 `print` statements is inefficient and hard to maintain. Instead, we can use a loop:

```python
for i in range(100):
    print("Hello")
```

---

## **Examples Using While Loops**

### **Sum of First N Numbers**
```python
n = int(input("Enter a number: "))
total = 0
i = 1

while i <= n:
    total += i
    i += 1

print("Sum of first", n, "numbers:", total)
```

### **Sum of Squares of First N Numbers**
```python
n = int(input("Enter a number: "))
total = 0
i = 1

while i <= n:
    total += i ** 2
    i += 1

print("Sum of squares of first", n, "numbers:", total)
```

### **Sum of First N Even Numbers**
```python
n = int(input("Enter a number: "))
total, count, start = 0, 0, 2

while count < n:
    total += start
    start += 2
    count += 1

print("Sum of first", n, "even numbers:", total)
```

### **Sum of First N Odd Numbers**
```python
n = int(input("Enter a number: "))
total, count, start = 0, 0, 1

while count < n:
    total += start
    start += 2
    count += 1

print("Sum of first", n, "odd numbers:", total)
```

---

## **Practical Examples Using While Loops**

### **Count Occurrences of a Character**
Count the occurrences of the letter 'p' in a string:
```python
str1 = "python is open source programming language"
l = len(str1)
c = 0

while l > 0:
    if str1[l - 1] == 'p':
        c += 1
    l -= 1

print("Occurrences of 'p':", c)
```

---

## **Compound Operators in Loops**
Python supports compound operators to simplify increment or decrement operations:
```python
i = 0
while i < 5:
    print("Hello")
    i += 1  # Increment i by 1 using the compound operator
```

---

## **Using Loops for Scalability**

Loops make code scalable and easier to maintain. For example:

### **Generate a List of First N Even Numbers**
```python
n = int(input("Enter the number of even numbers: "))
fin_list = []
total, count, start = 0, 0, 2

while count < n:
    fin_list.append(start)
    start += 2
    count += 1

print("First", n, "even numbers:", fin_list)
print("Sum:", sum(fin_list))
```

---

## **Key Points to Remember**
1. **For Loops**: Best for iterating over sequences or ranges.
2. **While Loops**: Ideal for executing code until a condition changes.
3. **Compound Operators**: Simplify increment and decrement operations.
4. **Scalability**: Loops reduce redundancy and make code maintainable.

---

These notes cover Python loops comprehensively, with examples and explanations to help you understand and apply these concepts effectively.

---

## **For Loop**

The `for` loop is used to iterate over a sequence (e.g., list, string, range).

### **Basic Syntax**
```python
for <variable> in <sequence>:
    <statements>
```

### **Key Components**
- **Iterator (`variable`)**: A placeholder that takes each value in the sequence during iteration.
- **Iterable (`sequence`)**: Any object that can return its elements one at a time (e.g., string, list, tuple, set, or range).

### **Example: Printing Numbers**
```python
for i in range(1, 6):  # Iterates from 1 to 5
    print(i)
```

### **Example: Iterating Over a List**
```python
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
```

### **Using `range()`**
The `range()` function generates a sequence of numbers. It is commonly used in loops.

#### **Syntax of `range()`**
```python
range(start, stop, step)
```
- **start**: The starting value (inclusive).
- **stop**: The ending value (exclusive).
- **step**: The increment (default is 1).

#### **Example: Using `range()`**
```python
for i in range(5):  # Iterates from 0 to 4
    print("hello")

for i in range(35, 41, 2):  # Iterates over [35, 37, 39]
    print(i)
```

### **Special Use of Underscore (`_`)**
When the loop variable is not needed, use `_` as a placeholder:
```python
for _ in range(5):
    print("hello")
```

---

## **Control Statements in Loops**

Control statements modify the flow of execution within loops:

### **`continue` Statement**
Skips the remaining code in the current iteration and moves to the next iteration.

#### **Example: Skipping Specific Values**
```python
for val in "string":
    if val == "i":
        continue
    print(val)

print("The end")
```

### **`break` Statement**
Terminates the loop prematurely when a condition is met.

#### **Example: Breaking Out of a Loop**
```python
for i in range(10):
    if i == 5:
        break
    print(i)
```

---

## **While Loop**

The `while` loop executes as long as the given condition evaluates to `True`.

### **Basic Syntax**
```python
while <condition>:
    <statements>
```

### **Example: Print "Hello" Multiple Times**
```python
i = 1
while i <= 5:  # Condition: i is less than or equal to 5
    print("Hello")
    i += 1  # Increment i by 1
```

### **Using `continue` in a While Loop**
Skips the rest of the code in the current iteration and moves to the next iteration.

#### **Example: Skipping Multiples of 7**
```python
i = 1
while i <= 10:
    if i % 7 == 0:
        i += 1
        continue
    print(i)
    i += 1
```

---

## **Examples of Practical Use Cases**

### **Sum of First N Even Numbers**
#### **Using a `for` Loop**
```python
n = int(input("Enter a number: "))
r = range(2, n * 2 + 1, 2)

print(list(r))
total = 0
for i in r:
    total += i
print("Sum of first", n, "even numbers:", total)
```

#### **Using a `while` Loop**
```python
n = int(input("Enter a number: "))
total, count, start = 0, 0, 2

while count < n:
    total += start
    start += 2
    count += 1

print("Sum of first", n, "even numbers:", total)
```

### **Fibonacci Series**
#### **Generating the First 20 Fibonacci Numbers**
```python
def fibonacci_series(n):
    a, b = 0, 1
    series = []
    for _ in range(n):
        series.append(a)
        a, b = b, a + b
    return series

print(fibonacci_series(20))
```

#### **Finding the 40th Fibonacci Number**
```python
def fibonacci_nth(n):
    a, b = 0, 1
    for _ in range(2, n + 1):
        a, b = b, a + b
    return b

print(fibonacci_nth(40))
```

### **Prime Number Check**
```python
def is_prime(num):
    if num < 2:
        return False
    for i in range(2, int(num ** 0.5) + 1):
        if num % i == 0:
            return False
    return True

number = int(input("Enter a number: "))
print("Prime:" if is_prime(number) else "Not Prime")
```

### **Count Digits in a Number**
```python
num = int(input("Enter a number: "))
digit_count = 0

while num > 0:
    num //= 10
    digit_count += 1

print("Number of digits:", digit_count)
```

---

## **Key Takeaways**

1. **For Loops**: Ideal for iterating over sequences or ranges.
2. **While Loops**: Useful when the number of iterations depends on a condition.
3. **Control Statements**: Use `break` to exit a loop and `continue` to skip the rest of the current iteration.
4. **Practical Applications**: Loops are versatile and can be used for calculations, data processing, and more.
5. **Scalability**: Loops make repetitive tasks manageable and code easier to maintain.

These notes cover Python loops comprehensively, with examples and explanations to help you understand and apply these concepts effectively.



## **Concepts Recap**

### **Conditional Statements**
- Use `if`, `else`, `elif` for decision-making.
- Logical operators (`and`, `or`, `not`) enhance condition checks.

### **Loops**
- Use `for` and `while` loops for repetitive tasks.
- Examples include summation, calculations, and checking properties (e.g., leap year, palindrome).

### **Applications**
- Grading systems, calculators, finding maximum numbers, leap year checks, and palindrome detection.

---

These notes provide a structured overview of Python's conditional statements and loops, complete with examples and explanations for each concept.

---
