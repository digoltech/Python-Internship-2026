# Day 10 - Topic 2: Dynamic URL Variables & Returning JSON

## Why this topic matters

Static websites display the exact same text to every visitor. However, modern websites are dynamic—they customize pages based on user input. For example, visiting `/user/rahul` should show Rahul's page, and visiting `/user/priya` should show Priya's page.

Flask makes it easy to capture values directly from the URL path and use them inside your Python functions.

---

## 1. Dynamic Routing (Variable URLs)

To capture a variable from the URL path, we wrap it in angle brackets `<variable_name>` in the routing path. Flask will automatically pass it as an argument to the function.

```python
from flask import Flask

app = Flask(__name__)

# E.g. Visiting http://127.0.0.1:5000/greet/Rahul
@app.route("/greet/<username>")
def greet_user(username):
    # username will receive whatever was typed in that position in the URL
    return f"Hello, {username}! Welcome back to the portal."

if __name__ == "__main__":
    app.run(debug=True)
```

---

## 2. Restricting Variable Types (Integers)

You can specify a converter type to ensure the user passes the correct kind of value. For example, if you want to capture a student ID (which must be a number):

```python
from flask import Flask

app = Flask(__name__)

# converter type 'int' ensures this route only matches if the user inputs an integer
@app.route("/student/<int:student_id>")
def show_student(student_id):
    # student_id is passed as an actual Python integer
    next_id = student_id + 1
    return f"Displaying records for Student #{student_id}. Next ID is #{next_id}."

if __name__ == "__main__":
    app.run(debug=True)
```
If a user tries to visit `/student/abc`, Flask will automatically return a `404 Not Found` page because `abc` is not an integer.

---

## 3. Returning JSON (Making a simple API)

Web servers can return raw JSON data instead of text/HTML. This is how backends talk to mobile apps or frontend frameworks. In Flask, you can return a Python dictionary directly, and Flask automatically converts it to JSON format!

```python
from flask import Flask

app = Flask(__name__)

@app.route("/api/user")
def user_api():
    # Return a Python dictionary
    user_info = {
        "name": "Amit Kumar",
        "role": "Intern",
        "skills": ["Python", "SQL"],
        "active": True
    }
    return user_info  # Automatically converted to JSON!

if __name__ == "__main__":
    app.run(debug=True)
```
Navigate to `http://127.0.0.1:5000/api/user` to see how the browser renders the dictionary structure.
