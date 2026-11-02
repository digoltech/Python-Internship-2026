# Day 10 - Topic 1: Introduction to Flask and Routing

## Why this topic matters

So far, all the Python scripts you have written run in your console/terminal. However, in the real world, most software is accessed through a browser.

**Flask** is a micro web framework for Python. It allows you to write Python scripts that turn your computer into a local **web server**. When a user types your URL into their browser, your Python script runs, processes their request, and sends back a response (like text, JSON, or a web page).

---

## 1. Setting Up Flask

Flask is a third-party library, so we install it inside our active virtual environment using `pip`:

```bash
pip install flask
```

---

## 2. Your First Flask Web Server

Let's write a minimal web server in Python. Create a file named `app.py`:

```python
from flask import Flask

# Initialize the Flask application
app = Flask(__name__)

# Define the Home route (/)
@app.route("/")
def home():
    return "Hello Students! Welcome to your first Python-powered Web Page."

# Run the server when this script is executed directly
if __name__ == "__main__":
    app.run(debug=True)
```

---

## 3. How to Run and View Your Web App

1. In your terminal (with your virtual environment active), run your app:
   ```bash
   python app.py
   ```
2. You will see output telling you that the server is running, usually at:
   `http://127.0.0.1:5000/` (or `localhost:5000`).
3. Open your web browser (Chrome/Edge/Firefox) and navigate to that address.
4. You will see the text "Hello Students! Welcome to your first Python-powered Web Page." displayed on the screen!

---

## 4. What is Routing?

**Routing** means mapping a specific URL path typed by the user to a specific Python function that should run. 

For example, we can add a `/about` page:

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "Welcome to the Home Page!"

# This function runs only when the user visits http://127.0.0.1:5000/about
@app.route("/about")
def about_page():
    return "This is the About Us section. We are teaching Python basics."

if __name__ == "__main__":
    app.run(debug=True)
```
Now, if you go to `http://127.0.0.1:5000/about` in your browser, the `about_page()` function runs and displays the text!
