### Detailed Revision Notes: Time Complexity

#### **Definition of Time Complexity**
Time complexity is a measure of the computational time an algorithm takes to run as a function of the size of the input. It is expressed as a function \( T(n) \), where \( n \) is the size of the input.

#### **Big O Notation**
Big O Notation is a mathematical representation used to describe the upper bound of an algorithm's running time. It expresses how the runtime grows relative to the input size \( n \), focusing on the number of operations required. For instance:
- \( O(1) \): Constant time – no dependency on input size.
- \( O(n) \): Linear time – runtime grows proportionally with input size.
- \( O(\log n) \): Logarithmic time – runtime grows logarithmically as input size increases.
- \( O(n^2) \): Quadratic time – runtime grows quadratically with input size.
- \( O(n^3) \): Cubic time – runtime grows cubically with input size.

Big O helps compare algorithms by focusing on their efficiency and scalability, ignoring lower-order terms and constants.

#### **Types of Time Complexities**

1. **Constant Time – \( O(1) \)**
   - The algorithm executes in the same amount of time, regardless of input size.
   - Example:
     ```python
     def factorial(n):
         return 1  # Constant operation
     ```
   - Every operation takes a fixed amount of time.

2. **Linear Time – \( O(n) \)**
   - The runtime grows linearly with the input size.
   - Example:
     ```python
     for i in range(n):
         print("hello")
     ```
   - If \( n = 10 \), it takes 10 seconds; if \( n = 100 \), it takes 100 seconds.

3. **Logarithmic Time – \( O(\log n) \)**
   - The runtime grows logarithmically as the input size increases, often seen in algorithms that repeatedly divide the input.
   - Example: Binary search
     ```python
     A = [1, 2, 3, 6, 7, 54, 56, 87, 765, 788, 12312]
     target = 34
     # Divide the list into halves until the target is found.
     ```

4. **Quadratic Time – \( O(n^2) \)**
   - The runtime grows quadratically with the input size, often occurring in nested loops.
   - Example:
     ```python
     for i in range(n):
         for j in range(n):
             print("1", end=",")
     ```
   - For \( n = 10 \), runtime = \( 10 \times 10 = 100 \) seconds.
   - For \( n = 100 \), runtime = \( 100 \times 100 = 10,000 \) seconds.

5. **Cubic Time – \( O(n^3) \)**
   - The runtime grows cubically with the input size, often occurring in triple nested loops.
   - Example:
     ```python
     for i in range(n):
         for j in range(n):
             for k in range(n):
                 print("1", end=",")
     ```
   - For \( n = 10 \), runtime = \( 10 \times 10 \times 10 = 1,000 \) seconds.

#### **Practical Examples**

1. **Constant Time Example**
   ```python
   def factorial(n):
       fact = 1
       i = 1
       while i <= n:
           fact *= i  # O(1) operation
           i += 1     # O(1) operation
       return fact
   ```

2. **Linear Time Example**
   ```python
   for i in range(35):
       print("hello")  # Executes 35 times (O(n))
   ```

3. **Quadratic Time Example**
   ```python
   for i in range(10):  # Outer loop
       for j in range(10):  # Inner loop
           print("1", end=",")  # Executes 10 * 10 = 100 times (O(n^2))
   ```

4. **Logarithmic Time Example**
   Binary search divides the input into halves:
   ```python
   A = [1, 3, 5, 7, 9, 11, 13]
   target = 7
   # Divide into [1, 3, 5] and [7, 9, 11, 13] until the target is found.
   ```

#### **Execution Time Analysis**
The `%time` and `%%time` commands in Python can be used to measure execution time for snippets of code.

- **Single operation (O(1)):**
  ```python
  %time print('hello world')
  ```
  Output: Takes constant time.

- **Linear operation (O(n)):**
  ```python
  %%time
  for i in range(15):
      print('hello world')
  ```
  Output: Grows linearly with the number of iterations.

- **Quadratic operation (O(n^2)):**
  ```python
  %%time
  for i in range(15):
      for j in range(15):
          print('hello world')
  ```
  Output: Grows quadratically as iterations increase.

- **Cubic operation (O(n^3)):**
  ```python
  %%time
  for i in range(15):
      for j in range(15):
          for k in range(15):
              print('hello world')
  ```
  Output: Grows cubically with the number of nested loops.

#### **Links for Further Learning**
- [Big O Cheat Sheet](https://www.bigocheatsheet.com/)
- [StackOverflow Explanation of O(log n)](https://stackoverflow.com/questions/2307283/what-does-olog-n-mean-exactly)

#### **Version Control in Git**
Git is a distributed version control system that tracks changes in files and coordinates work among multiple developers. It ensures code consistency and allows rollback to previous versions.

- Learn more: [Git Basics](https://www.atlassian.com/git/tutorials/what-is-version-control)

---

These notes comprehensively cover the topic of time complexity, providing examples, explanations, and practical insights into analyzing algorithm performance.