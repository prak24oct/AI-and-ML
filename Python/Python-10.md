# Detailed Revision Notes on File Handling in Python

File handling in Python provides a mechanism to work with files for reading, writing, appending, and more. It is essential for performing input/output operations with persistent storage. Below are comprehensive notes on file handling concepts, examples, and methods.

---

## **Basics of File Handling**

1. **Opening and Closing Files**
   - To work with a file, it must be opened first using the `open()` function.
   - Syntax:
     ```python
     f = open(filename.ext, 'mode')
     f.close()
     ```
   - Always close a file using `f.close()` to ensure changes are saved and resources are freed.

2. **Data Read Format**
   - Data read from a file is always in string format unless processed further.

---

## **Modes of File Operation**

Python provides different modes for working with text and binary files:

### **Text File Modes**
- `'r'` : Read-only mode. Opens the file for reading. File must exist.
- `'w'` : Write-only mode. Creates a new file or overwrites an existing file.
- `'a'` : Append mode. Writes at the end of the file without modifying existing content.
- `'r+'`: Read and write mode. File must exist.
- `'w+'`: Write and read mode. Creates or overwrites the file.
- `'a+'`: Append and read mode. Appends data and allows reading.

### **Binary File Modes**
- `'rb'` : Read-only mode for binary files.
- `'wb'` : Write-only mode for binary files.
- `'ab'` : Append mode for binary files.
- `'r+b'`: Read and write mode for binary files.
- `'w+b'`: Write and read mode for binary files.
- `'a+b'`: Append and read mode for binary files.

---

## **File Object Methods**

### **Reading Methods**
1. `read()`:
   - Reads the entire content of the file.
   - Can take an optional argument to specify the number of characters to read.
   ```python
   f = open('data.txt', 'r')
   content = f.read(100)  # Reads first 100 characters
   f.close()
   ```

2. `readline()`:
   - Reads the current line from the file.
   ```python
   f = open('data.txt', 'r')
   line = f.readline()
   f.close()
   ```

3. `readlines()`:
   - Reads all lines and returns a list where each line is an element.
   ```python
   f = open('data.txt', 'r')
   lines = f.readlines()
   f.close()
   ```

### **Writing Methods**
1. `write()`:
   - Writes a string to the file.
   ```python
   f = open('write.txt', 'w')
   f.write('Hello, World!')
   f.close()
   ```

2. `writelines()`:
   - Writes a list of strings to the file.
   ```python
   f = open('write.txt', 'w')
   f.writelines(['Line 1\n', 'Line 2\n'])
   f.close()
   ```

### **Cursor Control Methods**
1. `tell()`:
   - Returns the current position of the cursor in the file.
   ```python
   f = open('data.txt', 'r')
   print(f.tell())  # Output: Cursor position
   f.close()
   ```

2. `seek(offset)`:
   - Moves the cursor to a specific position in the file.
   ```python
   f = open('data.txt', 'r')
   f.seek(10)  # Moves the cursor to the 10th byte
   f.close()
   ```

---

## **Modes in Detail**

### **1. Read Mode (`'r'`)**
- Opens a file for reading.
- File must exist; otherwise, a `FileNotFoundError` is raised.
- Cursor starts at the beginning of the file.

Example:
```python
f = open('read.txt', 'r')
print(f.read())  # Reads the entire file content
f.seek(0)
print(f.read(5))  # Reads the first 5 characters
f.close()
```

---

### **2. Write Mode (`'w'`)**
- Opens a file for writing.
- Deletes existing content if the file exists.
- Creates a new file if it does not exist.

Example:
```python
f = open('write.txt', 'w')
f.write('Good Morning!')
f.close()
```

---

### **3. Append Mode (`'a'`)**
- Opens a file for appending data at the end.
- Creates a new file if it does not exist.
- `seek()` does not affect the position; data is always written at the end.

Example:
```python
f = open('append.txt', 'a')
f.write('Appending new content.\n')
f.close()
```

---

### **4. Write and Read Mode (`'w+'`)**
- Opens a file for both writing and reading.
- Deletes existing content if the file exists.
- Creates a new file if it does not exist.

Example:
```python
f = open('write_read.txt', 'w+')
f.write('Hello')
f.seek(0)
print(f.read())  # Output: Hello
f.close()
```

---

### **5. Read and Write Mode (`'r+'`)**
- Opens a file for both reading and writing.
- File must exist.

Example:
```python
f = open('read_write.txt', 'r+')
print(f.read())
f.write('Added content.')
f.seek(0)
print(f.read())
f.close()
```

---

### **6. Append and Read Mode (`'a+'`)**
- Opens a file for both appending and reading.
- Creates a new file if it does not exist.
- Data is always appended at the end; `seek()` does not affect writing position.

Example:
```python
f = open('append_read.txt', 'a+')
f.write('Appended content.\n')
f.seek(0)
print(f.read())
f.close()
```

---

## **Using the `with` Statement**

- The `with` statement simplifies file handling by automatically closing the file after the block is executed.
- Ensures proper resource management.

Example:
```python
with open('data.txt', 'r') as f:
    content = f.read()
    print(content)
# File is automatically closed here
```

---

## **Practical Examples**

1. **Counting Characters, Words, and Lines**
   ```python
   with open('data.txt', 'r') as f:
       no_of_char = len(f.read())
       f.seek(0)
       no_of_words = len(f.read().split())
       f.seek(0)
       no_of_lines = len(f.readlines())
   print(no_of_char, no_of_words, no_of_lines)
   ```

2. **Writing Multiple Lines**
   ```python
   f = open('multi_line.txt', 'w')
   f.writelines(['Line 1\n', 'Line 2\n', 'Line 3\n'])
   f.close()
   ```

---

## **Key Differences Between `open()` and `with open()`**
| Feature           | `open()`                     | `with open()`               |
|--------------------|------------------------------|-----------------------------|
| File Closing       | Manual (`f.close()`)         | Automatic                   |
| Resource Handling  | May cause resource leakage   | Ensures proper cleanup      |
| Simplicity         | More verbose                | Concise and safer           |

---

This guide provides a complete overview of file handling in Python, ensuring a deep understanding of its modes, methods, and practical applications.