# Day 9 - Topic 2: Extracting Web Data (Links, Lists, and Text)

## Why this topic matters

When scraping a web page, you rarely want just the text. Often, you want to collect a list of articles, scrape images, or gather links to follow them further.

To extract these details, you need to understand how to access **HTML attributes** (like the `href` in links) and navigate nested elements using BeautifulSoup.

---

## 1. Extracting Link URLs (Attributes)

In HTML, links look like this: `<a href="https://example.com">Click Here</a>`. 
The URL is stored in the `href` attribute. In BeautifulSoup, you read attributes exactly like reading keys from a Python dictionary.

```python
from bs4 import BeautifulSoup

html = """
<div class="navigation">
    <a href="https://google.com" id="link-g">Google</a>
    <a href="https://wikipedia.org" id="link-w">Wikipedia</a>
</div>
"""

soup = BeautifulSoup(html, "html.parser")

# Find the Google link
g_link = soup.find(id="link-g")

# Read the 'href' attribute
url = g_link["href"]
text = g_link.text

print(f"Text: {text} -> Destination: {url}")
```

---

## 2. Scraping Nested Lists

Often, data is grouped in list items (`<li>`) inside a bullet point container (`<ul>`).

```python
from bs4 import BeautifulSoup

html = """
<div class="syllabus">
    <h3>Day 9 Subtopics</h3>
    <ul id="topic-list">
        <li>Introduction to Scraping</li>
        <li>Extracting Links and Attributes</li>
        <li>Polite Scraping and Etiquette</li>
    </ul>
</div>
"""

soup = BeautifulSoup(html, "html.parser")

# Find the main list container
topic_list = soup.find(id="topic-list")

# Find all 'li' items inside that container
items = topic_list.find_all("li")

print("Syllabus topics:")
for item in items:
    print("-", item.text)
```

---

## 3. Combining requests and BeautifulSoup (Real-world style)

To scrape a live page, we download the page using `requests`, then pass `response.text` to BeautifulSoup.

```python
import requests
from bs4 import BeautifulSoup

# Let's request a live test site
url = "https://example.com"

try:
    response = requests.get(url)
    response.raise_for_status()
    
    # Parse the page
    soup = BeautifulSoup(response.text, "html.parser")
    
    # Extract the main heading
    heading = soup.find("h1").text
    print("Heading of example.com is:", heading)
    
    # Extract the first link in the page
    link = soup.find("a")["href"]
    print("First link goes to:", link)
    
except Exception as e:
    print("Error during scraping:", e)
```
Using this combination, you can load and extract data from any static webpage on the internet!
