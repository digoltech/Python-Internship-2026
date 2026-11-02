# Day 9 - Task 2: Extracting Web Data

## Example (already solved, for reference only)

Problem: Extract a link destination from a link tag.

```python
from bs4 import BeautifulSoup

html = '<a href="https://www.wikipedia.org" id="wiki-link">Wiki</a>'
soup = BeautifulSoup(html, "html.parser")
link = soup.find(id="wiki-link")
print("URL:", link["href"])
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

---

## Your Tasks

1. Given the following HTML menu block:
   ```python
   html_menu = """
   <ul class="nav-links">
       <li><a href="/home">Home</a></li>
       <li><a href="/about">About Us</a></li>
       <li><a href="/contact">Contact</a></li>
   </ul>
   """
   ```
   Write a Python script that extracts and prints all link destinations (e.g. `/home`, `/about`, `/contact`) from the anchor (`<a>`) tags.
2. Write a Python script that makes a live `GET` request to `https://example.com`. Extract and print:
   - The main title text of the page.
   - The destination URL of the link present on that page.
