# Day 9 - Task 1: Introduction to Web Scraping & BeautifulSoup

## Example (already solved, for reference only)

Problem: Parse a simple HTML string and print the text inside the header tag `<h1>`.

```python
from bs4 import BeautifulSoup

html = "<html><body><h1>Learning Scraping</h1></body></html>"
soup = BeautifulSoup(html, "html.parser")
print(soup.h1.text)
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

---

## Your Tasks

1. Given the following HTML string:
   ```python
   html_content = """
   <div class="profile-card">
       <h2 id="name">Aman Gupta</h2>
       <p class="role">Software Engineer</p>
       <p class="location">Pune, India</p>
   </div>
   """
   ```
   Write a Python script to parse this HTML using BeautifulSoup and print:
   - The name ("Aman Gupta") by searching for the ID.
   - The role ("Software Engineer") by searching for the class name.
2. Given the following HTML page:
   ```python
   html_page = """
   <html>
       <head><title>Course Syllabus</title></head>
       <body>
           <h3 class="section-title">Week 1 Topics</h3>
           <p class="topic">Basic Syntax</p>
           <p class="topic">Data Structures</p>
           <h3 class="section-title">Week 2 Topics</h3>
           <p class="topic">File I/O</p>
           <p class="topic">Web scraping</p>
       </body>
   </html>
   """
   ```
   Write a Python program that extracts and prints all elements with class `"topic"`.
