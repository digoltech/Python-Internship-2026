# Day 10 - Topic 3: Serving HTML Templates and Jinja2

## Why this topic matters

Returning HTML as a string inside your Python function (e.g. `return "<h1>Hello</h1>"`) becomes extremely messy when building complex pages. 

The standard approach is to separate your **business logic** (Python) from the **user interface** (HTML files). Flask uses a rendering engine called **Jinja2** that reads HTML files and dynamically inserts Python variables, runs loops, or checks conditional statements directly inside the HTML before sending it to the user.

---

## 1. Creating the Templates Folder

By default, Flask searches for HTML files inside a directory named **`templates`**. You must create this folder in the same directory as your `app.py`.

```text
my_project/
│
├── app.py
└── templates/
    └── index.html
```

---

## 2. Rendering a Basic Template

### Step 1: Create `templates/index.html`
```html
<!DOCTYPE html>
<html>
<head>
    <title>Student Page</title>
</head>
<body>
    <!-- Jinja2 Syntax: {{ variable_name }} is used to print values -->
    <h1>Welcome, {{ name }}!</h1>
    <p>Your current course score is: {{ score }}%</p>
</body>
</html>
```

### Step 2: Create `app.py`
We use `render_template` to load the HTML file and pass variables to it:

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route("/score/<username>")
def show_score(username):
    # Pass Python variables to the HTML template
    return render_template("index.html", name=username, score=85)

if __name__ == "__main__":
    app.run(debug=True)
```

---

## 3. Jinja2 Loops and Conditionals

Jinja2 templates allow you to use basic control flows like loops and if-statements using the `{% ... %}` syntax.

### Dynamic Template (`templates/report.html`):
```html
<!DOCTYPE html>
<html>
<head>
    <title>Report Card</title>
</head>
<body>
    <h1>Report Card</h1>
    
    <!-- If Statement -->
    {% if marks >= 40 %}
        <h3 style="color: green;">Status: PASS</h3>
    {% else %}
        <h3 style="color: red;">Status: FAIL</h3>
    {% endif %}

    <hr>

    <h3>Topics Learned:</h3>
    <ul>
        <!-- For Loop -->
        {% for topic in topics %}
            <li>{{ topic }}</li>
        {% endfor %}
    </ul>
</body>
</html>
```

### Python backend (`app.py`):
```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route("/report")
def report():
    topics_list = ["File Handling", "APIs", "Web Scraping", "Flask Basics"]
    return render_template(
        "report.html", 
        marks=75, 
        topics=topics_list
    )

if __name__ == "__main__":
    app.run(debug=True)
```
This powerful templating feature allows you to display database items, custom tables, or user reports dynamically!
