# Day 13 - Beautiful Soup - Scraping 

# **Web Scraping with Python**

## **1. What is Web Scraping?**

Web scraping is the process of automatically extracting data from websites using programming.

Instead of manually copying information from websites, Python can fetch web pages, extract useful information, and store it in CSV, JSON, or a database.

### **Real-world use cases**

- E-commerce product and price tracking
- Job listing collection
- News aggregation
- Market research
- Data collection for analysis

### **Web Scraping Workflow**

```
Send HTTP Request
        ↓
Receive HTML Response
        ↓
Parse HTML Content
        ↓
Extract Required Data
        ↓
Store Data (CSV / JSON / Database)
```

## **2. Python Libraries for Web Scraping**

| Library          | Purpose                                    |
| ---------------- | ------------------------------------------ |
| `requests`       | Fetch web pages and APIs                   |
| `httpx`          | Synchronous and asynchronous HTTP requests |
| `beautifulsoup4` | Parse and extract HTML data                |
| `lxml`           | Fast HTML and XML parsing                  |
| `curl_cffi`      | Advanced HTTP client                       |
| `selenium`       | Browser automation and dynamic websites    |
| `playwright`     | Modern browser automation                  |
| `scrapy`         | Large-scale web scraping and crawling      |

For this module, we will primarily use `requests`, `beautifulsoup4`, and `lxml`.

### **Installation**

Activate your virtual environment and install the packages:

```
pip install requests beautifulsoup4 lxml
```

Save the dependencies:

```
pip freeze > requirements.txt
```

## **3. Fetching Web Pages Using&#x20;**`requests`

The `requests` library allows Python to communicate with websites using HTTP requests.

```
import requestsurl = "https://quotes.toscrape.com/"response = requests.get(url, timeout=10)response.raise_for_status()print(response.status_code)print(response.text)
```

### **Important Response Properties**

| Property / Method             | Description                                    |
| ----------------------------- | ---------------------------------------------- |
| `response.status_code`        | HTTP response status                           |
| `response.text`               | HTML response content                          |
| `response.json()`             | Parse a JSON response                          |
| `response.headers`            | Response headers                               |
| `response.raise_for_status()` | Raise an error for unsuccessful HTTP responses |

### **Common HTTP Status Codes**

| Code | Meaning               |
| ---- | --------------------- |
| 200  | Success               |
| 400  | Bad Request           |
| 403  | Forbidden             |
| 404  | Not Found             |
| 429  | Too Many Requests     |
| 500  | Internal Server Error |

## **4. Introduction to BeautifulSoup**

BeautifulSoup is a Python library used to parse HTML and XML documents and extract specific information.

**BeautifulSoup does not fetch websites.** It processes HTML received from libraries such as `requests`.

### **Example**

```
from bs4 import BeautifulSouphtml = """<html>    <body>        <h1>Welcome to Python</h1>        <p>Learn Web Scraping</p>    </body></html>"""soup = BeautifulSoup(html, "lxml")print(soup.find("h1").get_text())print(soup.find("p").get_text())
```

### **Output**

```
Welcome to Python
Learn Web Scraping
```

## **5. Important BeautifulSoup Methods**

| Method         | Description                          |
| -------------- | ------------------------------------ |
| `find()`       | Find the first matching element      |
| `find_all()`   | Find all matching elements           |
| `select_one()` | Find the first matching CSS selector |
| `select()`     | Find all matching CSS selectors      |
| `get_text()`   | Extract text from an element         |
| `get()`        | Extract an attribute value           |
| `prettify()`   | Display formatted HTML               |

### **Finding Elements**

```
# Find by HTML tagsoup.find("h1")# Find all paragraphssoup.find_all("p")# Find by classsoup.find("div", class_="product")# Find by IDsoup.find("div", id="container")# Find all linkssoup.find_all("a", href=True)
```

### **CSS Selectors**

| Selector      | Description                    |
| ------------- | ------------------------------ |
| `h1`          | Select HTML tag                |
| `.product`    | Select by class                |
| `#container`  | Select by ID                   |
| `div.product` | Select div with product class  |
| `div p`       | Select paragraphs inside div   |
| `div > p`     | Select direct child paragraphs |
| `a[href]`     | Select links containing href   |

```
soup.select_one("h1")soup.select(".product")soup.select("#container")soup.select("div.product h2")
```

## **6. Practical Example — Scraping Quotes**

Website: [https://quotes.toscrape.com/](https://quotes.toscrape.com/?utm_source=chatgpt.com)

### **Objective**

Extract quote text, author name, and tags from a website.

```
import requestsfrom bs4 import BeautifulSoupurl = "https://quotes.toscrape.com/"response = requests.get(url, timeout=10)response.raise_for_status()soup = BeautifulSoup(response.text, "lxml")quotes = soup.select(".quote")for quote in quotes:    text = quote.select_one(".text")    author = quote.select_one(".author")    tags = quote.select(".tag")    print("Quote:", text.get_text(strip=True) if text else "")    print("Author:", author.get_text(strip=True) if author else "")    print("Tags:", [tag.get_text(strip=True) for tag in tags])    print("-" * 50)
```

### **Expected Output**

```
Quote: “The world as we have created it...”
Author: Albert Einstein
Tags: ['change', 'deep-thoughts', 'thinking', 'world']
--------------------------------------------------
```

## **7. Practical Example — Scraping Products**

Website: [https://books.toscrape.com/](https://books.toscrape.com/?utm_source=chatgpt.com)

### **Objective**

Extract book titles, prices, availability, and product URLs.

```
import requestsfrom bs4 import BeautifulSoupfrom urllib.parse import urljoinurl = "https://books.toscrape.com/"response = requests.get(url, timeout=10)response.raise_for_status()soup = BeautifulSoup(response.content, "lxml")books = soup.select(".product_pod")for book in books:    title = book.select_one("h3 a").get("title")    price = book.select_one(".price_color").get_text(strip=True)    availability = book.select_one(".availability").get_text(strip=True)    link = book.select_one("h3 a").get("href")    product_url = urljoin(url, link)    print("Title:", title)    print("Price:", price)    print("Availability:", availability)    print("URL:", product_url)    print("-" * 50)
```

### **Why Use&#x20;**`urljoin()`**?**

Websites often contain relative URLs.

```
from urllib.parse import urljoinurl = urljoin(    "https://example.com/",    "/products/123")print(url)
```

Output:

```
https://example.com/products/123
```

## **8. Saving Scraped Data**

### **Saving Data to CSV**

```
import csvproducts = [    ["Laptop", 50000],    ["Mobile", 20000],    ["Keyboard", 1500]]with open("products.csv", "w", newline="", encoding="utf-8") as file:    writer = csv.writer(file)    writer.writerow(["Name", "Price"])    writer.writerows(products)
```

### **Saving Data to JSON**

```
import jsonproducts = [    {"name": "Laptop", "price": 50000},    {"name": "Mobile", "price": 20000}]with open("products.json", "w", encoding="utf-8") as file:    json.dump(products, file, indent=4)
```

## **9. Pagination — Scraping Multiple Pages**

Many websites divide their content into multiple pages.

For example:

```
https://quotes.toscrape.com/page/1/
https://quotes.toscrape.com/page/2/
https://quotes.toscrape.com/page/3/
```

### **Example**

```
import requestsimport timefrom bs4 import BeautifulSoupfor page in range(1, 4):    url = f"https://quotes.toscrape.com/page/{page}/"    response = requests.get(url, timeout=10)    response.raise_for_status()    soup = BeautifulSoup(response.text, "lxml")    quotes = soup.select(".quote .text")    for quote in quotes:        print(quote.get_text(strip=True))    time.sleep(1)
```

## **10. Error Handling**

Web requests can fail because of network issues, unavailable websites, or server errors.

```
import requeststry:    response = requests.get(        "https://quotes.toscrape.com/",        timeout=10    )    response.raise_for_status()    print("Request successful")except requests.exceptions.Timeout:    print("Request timed out")except requests.exceptions.RequestException as error:    print("Request failed:", error)
```

### **Handling Missing HTML Elements**

```
title = soup.find("h1")if title:    print(title.get_text(strip=True))else:    print("Title not found")
```

## **11. Static vs Dynamic Websites**

| Feature                       | Static Website             | Dynamic Website             |
| ----------------------------- | -------------------------- | --------------------------- |
| Content                       | Available in HTML response | May load through JavaScript |
| JavaScript execution required | Usually no                 | Sometimes                   |
| Recommended tools             | Requests + BeautifulSoup   | Playwright / Selenium       |
| Scraping speed                | Generally faster           | Generally slower            |
| Complexity                    | Low                        | Medium to High              |

If the required data is not available in the initial HTML response, check whether the website provides an authorized API before using browser automation.

## **12. Best Practices**

- Always use a virtual environment.
- Always specify a request timeout.
- Check HTTP response status before parsing.
- Handle missing HTML elements.
- Add delays between requests and respect rate limits.
- Respect `robots.txt`, website terms, and access restrictions.
- Prefer authorized APIs when available.
- Avoid collecting sensitive or private information.
- Use an identifiable User-Agent when appropriate.
- Do not bypass CAPTCHAs or access restrictions.

## **13. Practical Tasks**

### **Task 1 — Quote Scraper (Easy)**

Website: [https://quotes.toscrape.com/](https://quotes.toscrape.com/?utm_source=chatgpt.com)

Requirements:

- Extract all quotes from the first page.
- Extract author names and tags.
- Store the data in `quotes.json`.
- Display the total number of extracted quotes.

### **Task 2 — Book Scraper (Medium)**

Website: [https://books.toscrape.com/](https://books.toscrape.com/?utm_source=chatgpt.com)

Requirements:

- Extract book titles, prices, availability, and ratings.
- Extract product URLs.
- Scrape the first five pages.
- Save the data in `books.csv`.
- Display the total number of books.
- Find the most expensive and cheapest books.

### **Task 3 — Advanced Quote Scraper (Medium)**

Website: [https://quotes.toscrape.com/](https://quotes.toscrape.com/?utm_source=chatgpt.com)

Requirements:

- Scrape all pages using pagination.
- Automatically detect the next page.
- Handle network errors and missing elements.
- Prevent duplicate records.
- Add a delay between requests.
- Export data into both CSV and JSON formats.

## **14. Revision Questions**

1. What is web scraping?
2. What is the difference between `requests` and BeautifulSoup?
3. What is the difference between `find()` and `find_all()`?
4. What is the difference between `select()` and `select_one()`?
5. Why do we use `urljoin()`?
6. What is pagination?
7. Why should we use request timeouts?
8. What is the difference between static and dynamic websites?
9. Why is error handling important in web scraping?
10. When should we use Selenium or Playwright instead of BeautifulSoup?

**Official Documentation**

- [Requests](https://requests.readthedocs.io/?utm_source=chatgpt.com)
- [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/?utm_source=chatgpt.com)
- [Playwright](https://playwright.dev/python/?utm_source=chatgpt.com)
- [Scrapy](https://docs.scrapy.org/?utm_source=chatgpt.com)

*Note: This module focuses on beginner-to-intermediate web scraping. Browser automation and asynchronous scraping are reserved for subsequent modules. Live website examples have not been execution-tested.*
