# Day 8 - Task 2: How the Web Works & The Requests Library

## Example (already solved, for reference only)

Problem: Write a program that makes a request to a website and prints the first 50 characters of the response text if the request succeeds.

```python
import requests

url = "https://www.wikipedia.org"
response = requests.get(url)

if response.status_code == 200:
    print(response.text[:50])
else:
    print("Failed with status:", response.status_code)
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

---

## Your Tasks

1. Explain in your own words (2-3 sentences):
   - What is the difference between a Client and a Server?
   - What does an HTTP `GET` request do?
2. Write a Python script that attempts to send a `GET` request to `https://httpbin.org/status/404` (a dummy site that always returns a 404 error). Print the status code and an appropriate error message based on the code.
3. Write a script that checks if a website is online. Take a website URL as user input (e.g., `https://www.github.com`). Perform a `GET` request and check if the status code is exactly `200`. Print `"Website is Online"` or `"Website is Offline"`. Protect your script from crashing using a simple `try-except` block in case the URL is invalid or the connection fails.
