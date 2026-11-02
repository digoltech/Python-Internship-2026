# Day 10 - Task 2: Dynamic URL Variables & Returning JSON

## Example (already solved, for reference only)

Problem: Create a route that takes a string name and returns it in uppercase.

```python
from flask import Flask

app = Flask(__name__)

@app.route("/upper/<text>")
def convert_upper(text):
    return text.upper()
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

---

## Your Tasks

1. Write a Flask route `/square/<int:number>` that takes an integer parameter and returns a string message displaying the square of the number. E.g. Visiting `/square/5` should display `"The square of 5 is 25"`.
2. Write a Flask route `/api/status` that returns a dictionary containing status information about your server. It should include the keys: `"status"` (value: `"active"`), `"uptime"` (value: `"24h"`), and `"version"` (value: `1.0`). Verify that Flask serves this as JSON.
3. Write a Flask route `/add/<int:num1>/<int:num2>` that accepts two integers in the URL and returns a string showing their sum. E.g., visiting `/add/10/20` should display `"10 + 20 = 30"`.
