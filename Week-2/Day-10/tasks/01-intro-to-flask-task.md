# Day 10 - Task 1: Introduction to Flask and Routing

## Example (already solved, for reference only)

Problem: Create a basic Flask application with a route `/hello` that returns "Hello World".

```python
from flask import Flask

app = Flask(__name__)

@app.route("/hello")
def hello():
    return "Hello World"

if __name__ == "__main__":
    app.run(debug=True)
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

---

## Your Tasks

1. Explain in your own words (2-3 sentences):
   - What does a web server do?
   - What is the purpose of `@app.route("/")` in a Flask application?
2. Create a Flask application named `app.py`. Define three routes:
   - Route `/` (Home page) -> returns `"Welcome to the homepage!"`
   - Route `/contact` -> returns `"Contact us at support@example.com"`
   - Route `/help` -> returns `"This is the help page. How can we support you?"`
   Run the application, open your browser, visit all three pages, and verify they load correctly.
