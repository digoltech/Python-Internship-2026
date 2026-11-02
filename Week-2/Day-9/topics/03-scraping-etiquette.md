# Day 9 - Topic 3: Scraping Etiquette & Being a Good Web Citizen

## Why this topic matters

Because Python makes it so easy to write a scraper, it is very easy to write code that causes trouble. If you run a fast loop that sends 10,000 requests per minute to a small website, you can crash their server. This is known as a **Denial of Service (DoS)** attack.

Web scraping is a gray area, and many websites actively block scrapers. To ensure your scripts do not get blocked, and to respect the owners of the websites you scrape, you must follow basic **scraping etiquette**.

---

## 1. Check the `robots.txt` File

Most websites have a file named `robots.txt` placed at the root level of their domain. This file lists rules for automated programs (crawlers/scrapers) about which pages they are allowed or forbidden to read.

- To check a site's rules, visit: `https://www.example.com/robots.txt`

### Common `robots.txt` syntax:
```text
User-agent: *
Disallow: /admin/
Disallow: /private-data/
```
This means: "All bots (`*`) are disallowed from scraping the `/admin/` and `/private-data/` folders." 

---

## 2. Rate Limiting (Using `time.sleep()`)

When scraping multiple pages in a loop, **never** make requests as fast as possible. Always add a small delay between each request to mimic a human user reading the pages.

```python
import time
import random
import requests

urls = [
    "https://jsonplaceholder.typicode.com/posts/1",
    "https://jsonplaceholder.typicode.com/posts/2",
    "https://jsonplaceholder.typicode.com/posts/3"
]

for url in urls:
    print("Scraping:", url)
    response = requests.get(url)
    
    # Generate a random delay between 1 and 3 seconds
    delay = random.uniform(1.0, 3.0)
    print(f"Waiting {delay:.2f} seconds before next request...")
    time.sleep(delay)
```

---

## 3. Set a Custom User-Agent

By default, when you use the requests library, Python sends a header that looks like: `User-Agent: python-requests/2.28.1`. Many firewalls immediately block this to prevent simple bot spam.

You can modify your headers to look like a standard web browser (Chrome or Firefox):

```python
import requests

url = "https://httpbin.org/user-agent"

# Custom headers mimicking a desktop Chrome browser
headers = {
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36"
}

response = requests.get(url, headers=headers)
print(response.text)
```

---

## 4. Scraping vs. API: The Golden Rule

Always remember: **If a website provides a public API, use the API instead of scraping.**
APIs are cleaner, faster, supported, and will not break when the website updates its visual layout/HTML design.
