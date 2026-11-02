# Day 9 - Topic 1: Introduction to Web Scraping & BeautifulSoup

## Why this topic matters

Not all websites provide a neat and clean JSON API for us to load their data. In many cases, the data we want is locked inside the visual layout of a standard web page (HTML).

**Web Scraping** is the technique of using a Python script to download a web page and automatically extract the pieces of information we need. In this topic, we will learn how HTML is structured and how Python's `BeautifulSoup` library helps us navigate and parse it.

---

## 1. A Quick Intro to HTML (The Skeleton of a Web Page)

HTML (HyperText Markup Language) uses **tags** to structure content. A tag typically looks like this:
```html
<tagname class="classname" id="unique-id">Content inside the tag</tagname>
```

Common HTML tags you will see:
- `<h1>`, `<h2>`, `<h3>`...: Headings.
- `<p>`: Paragraphs of text.
- `<a>`: Anchor tags (links). The link destination is stored in the `href` attribute: `<a href="https://google.com">Google</a>`.
- `<ul>`, `<li>`: Bullet point lists.
- `<div>`: Division (a box/container used to group other elements).

---

## 2. Setting Up BeautifulSoup

`BeautifulSoup` (part of the `beautifulsoup4` package) is the most popular library for parsing HTML in Python.

Let's install it first (inside your virtual environment):
```bash
pip install beautifulsoup4
```

---

## 3. Parsing a Simple HTML String

Before scraping live websites, let's understand how BeautifulSoup parses HTML using a simple string.

```python
from bs4 import BeautifulSoup

# A string containing HTML structure
html_doc = """
<html>
  <head><title>My Study Portal</title></head>
  <body>
    <h1 id="main-heading">Welcome Students</h1>
    <p class="description">This is Day 9 of our Python basic training course.</p>
    <p class="description">We are learning BeautifulSoup today!</p>
    <a href="https://python.org" id="python-link">Visit Python Official Site</a>
  </body>
</html>
"""

# Feed the HTML document to BeautifulSoup
soup = BeautifulSoup(html_doc, "html.parser")

# 1. Get the title tag and its text
title_tag = soup.title
print("Title Tag:", title_tag)        # Output: <title>My Study Portal</title>
print("Title Text:", title_tag.text)  # Output: My Study Portal

# 2. Find an element by its ID
heading = soup.find(id="main-heading")
print("Heading Text:", heading.text)  # Output: Welcome Students

# 3. Find the first occurrence of a tag
first_p = soup.find("p")
print("First Paragraph:", first_p.text)

# 4. Find all occurrences of a class name
descriptions = soup.find_all("p", class_="description")
print("Found descriptions:")
for p in descriptions:
    print("-", p.text)
```
Notice how we used `class_` instead of `class`. This is because `class` is a reserved keyword in Python, so BeautifulSoup uses `class_` with an underscore to identify HTML class names.
