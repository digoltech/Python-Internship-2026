# Day 10 - Task 3: Serving HTML Templates and Jinja2

## Example (already solved, for reference only)

Problem: Render an HTML template named `simple.html` passing a user's title.

`templates/simple.html`:
```html
<h1>Post: {{ title }}</h1>
```

`app.py`:
```python
from flask import Flask, render_template
app = Flask(__name__)

@app.route("/post")
def show_post():
    return render_template("simple.html", title="Flask Basics")
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

---

## Your Tasks

1. Explain in your own words (2-3 sentences):
   - Why do we use HTML templates instead of returning raw HTML strings inside our Python functions?
   - What is the difference between `{{ variable }}` and `{% statement %}` in Jinja2 syntax?
2. Create an HTML file named `profile.html` inside the `templates` folder. Design it to show a profile dashboard:
   - Display a heading: `"Profile Dashboard: [Name]"`
   - If the age is greater than or equal to 18, show a green message: `"Eligible to Vote"`. Otherwise, show a red message: `"Not Eligible to Vote"`.
   - List their top 3 favorite programming languages in an HTML bulleted list.
3. Write a Flask backend route `/profile` that passes data (Name, Age, and a List of 3 favorite languages) to `profile.html`. Run your app and verify that the page renders the values correctly.
