# 🐍 Python Applications

## 1. Web Development

### Flask Web Application

```python
from flask import Flask, render_template, request, jsonify

app = Flask(__name__)

@app.route('/')
def home():
    return render_template('index.html')

@app.route('/api/data', methods=['GET'])
def get_data():
    data = {
        'message': 'Hello from Flask!',
        'status': 'success'
    }
    return jsonify(data)

if __name__ == '__main__':
    app.run(debug=True)
```

### Django Project Structure

```python
# project/settings.py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'myapp',
]

# myapp/models.py
from django.db import models

class User(models.Model):
    name = models.CharField(max_length=100)
    email = models.EmailField(unique=True)
    created_at = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.name
```

## 2. Data Science and Machine Learning

### Data Analysis with Pandas

```python
import pandas as pd
import numpy as np

# Load and clean data
df = pd.read_csv('data.csv')
df = df.dropna()
df['date'] = pd.to_datetime(df['date'])

# Data aggregation
daily_stats = df.groupby('date').agg({
    'value': ['mean', 'std', 'count']
})

# Time series analysis
df['rolling_mean'] = df['value'].rolling(window=7).mean()
```

### Machine Learning with scikit-learn

```python
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score

# Prepare data
X = df.drop('target', axis=1)
y = df['target']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# Train model
model = RandomForestClassifier(n_estimators=100)
model.fit(X_train, y_train)

# Evaluate
predictions = model.predict(X_test)
accuracy = accuracy_score(y_test, predictions)
print(f"Accuracy: {accuracy:.3f}")
```

## 3. Automation and Scripting

### File Operations

```python
import os
import shutil
from pathlib import Path

def organize_files(source_dir, target_dir):
    """Organize files by extension"""
    for file in Path(source_dir).glob('*'):
        if file.is_file():
            ext = file.suffix[1:]  # Remove dot
            target_path = Path(target_dir) / ext
            target_path.mkdir(exist_ok=True)
            shutil.move(str(file), str(target_path / file.name))

# Example
organize_files('downloads', 'organized_files')
```

### System Automation

```python
import subprocess
import schedule
import time

def backup_database():
    """Backup database daily"""
    timestamp = time.strftime('%Y%m%d_%H%M%S')
    backup_file = f'backup_{timestamp}.sql'
    subprocess.run(['mysqldump', '-u', 'user', '-p', 'database', '>', backup_file])

# Schedule daily backup at 2 AM
schedule.every().day.at("02:00").do(backup_database)

while True:
    schedule.run_pending()
    time.sleep(60)
```

## 4. GUI Applications

### Tkinter Application

```python
import tkinter as tk
from tkinter import ttk

class CalculatorApp:
    def __init__(self, root):
        self.root = root
        self.root.title("Calculator")

        # Create display
        self.display = ttk.Entry(root, justify='right')
        self.display.grid(row=0, column=0, columnspan=4, padx=5, pady=5)

        # Create buttons
        buttons = [
            '7', '8', '9', '/',
            '4', '5', '6', '*',
            '1', '2', '3', '-',
            '0', '.', '=', '+'
        ]

        for i, text in enumerate(buttons):
            btn = ttk.Button(root, text=text, command=lambda t=text: self.on_click(t))
            btn.grid(row=i//4 + 1, column=i%4, padx=2, pady=2)

# Example
root = tk.Tk()
app = CalculatorApp(root)
root.mainloop()
```

## 5. Network Programming

### HTTP Server

```python
from http.server import HTTPServer, BaseHTTPRequestHandler
import json

class SimpleHTTPHandler(BaseHTTPRequestHandler):
    def do_GET(self):
        self.send_response(200)
        self.send_header('Content-type', 'application/json')
        self.end_headers()

        response = {
            'message': 'Hello from HTTP Server!',
            'path': self.path
        }
        self.wfile.write(json.dumps(response).encode())

# Example
server = HTTPServer(('localhost', 8000), SimpleHTTPHandler)
server.serve_forever()
```

### Socket Programming

```python
import socket

def start_server(host='localhost', port=12345):
    server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server.bind((host, port))
    server.listen(1)

    print(f"Server listening on {host}:{port}")

    while True:
        client, addr = server.accept()
        print(f"Connection from {addr}")

        data = client.recv(1024)
        print(f"Received: {data.decode()}")

        client.send(b"Message received!")
        client.close()

# Example
start_server()
```

## 6. Database Operations

### SQLite Operations

```python
import sqlite3

def create_database():
    conn = sqlite3.connect('example.db')
    cursor = conn.cursor()

    # Create table
    cursor.execute('''
        CREATE TABLE IF NOT EXISTS users (
            id INTEGER PRIMARY KEY,
            name TEXT NOT NULL,
            email TEXT UNIQUE NOT NULL
        )
    ''')

    # Insert data
    cursor.execute('INSERT INTO users (name, email) VALUES (?, ?)',
                  ('John Doe', 'john@example.com'))

    conn.commit()
    conn.close()

# Example
create_database()
```

### MongoDB Operations

```python
from pymongo import MongoClient

def mongo_operations():
    client = MongoClient('mongodb://localhost:27017/')
    db = client['example_db']
    collection = db['users']

    # Insert document
    user = {
        'name': 'Jane Doe',
        'email': 'jane@example.com',
        'age': 30
    }
    collection.insert_one(user)

    # Query documents
    results = collection.find({'age': {'$gt': 25}})
    for doc in results:
        print(doc)

# Example
mongo_operations()
```

## 7. Best Practices

### Code Organization

- Use meaningful variable and function names
- Follow PEP 8 style guide
- Write docstrings and comments
- Use type hints
- Organize code into modules and packages

### Error Handling

```python
def safe_operation():
    try:
        # Risky operation
        result = 10 / 0
    except ZeroDivisionError as e:
        print(f"Error: {e}")
    except Exception as e:
        print(f"Unexpected error: {e}")
    else:
        print("Operation successful")
    finally:
        print("Cleanup code here")
```

### Testing

```python
import unittest

class TestCalculator(unittest.TestCase):
    def test_addition(self):
        self.assertEqual(1 + 1, 2)

    def test_subtraction(self):
        self.assertEqual(3 - 1, 2)

if __name__ == '__main__':
    unittest.main()
```

### Performance Optimization

- Use list comprehensions
- Leverage built-in functions
- Use generators for large datasets
- Profile code to identify bottlenecks
- Consider using Cython for critical sections

## 8. Common Use Cases

### Data Processing

- CSV/Excel file handling
- JSON/XML parsing
- Data cleaning and transformation
- Time series analysis
- Statistical calculations

### Web Scraping

```python
import requests
from bs4 import BeautifulSoup

def scrape_website(url):
    response = requests.get(url)
    soup = BeautifulSoup(response.text, 'html.parser')

    # Extract data
    titles = [h1.text for h1 in soup.find_all('h1')]
    links = [a['href'] for a in soup.find_all('a', href=True)]

    return titles, links
```

### API Development

```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

class Item(BaseModel):
    name: str
    description: str = None
    price: float
    tax: float = None

@app.post("/items/")
async def create_item(item: Item):
    return item

@app.get("/items/{item_id}")
async def read_item(item_id: int):
    return {"item_id": item_id}
```

---

This file covers practical Python applications and real-world use cases. For more specific applications, refer to the relevant domain-specific modules.
