# Day 9 - Task 3: Scraping Etiquette

## Example (already solved, for reference only)

Problem: Define a custom user header and print the headers dictionary to see how it looks.

```python
headers = {
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64)"
}
print(headers)
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

---

## Your Tasks

1. Explain in your own words (2-3 sentences):
   - What is the purpose of a `robots.txt` file on a website?
   - Why should you use `time.sleep()` when scraping multiple pages in a loop?
2. Write a Python script that loops through a list of 3 URLs:
   - `https://jsonplaceholder.typicode.com/posts/1`
   - `https://jsonplaceholder.typicode.com/posts/2`
   - `https://jsonplaceholder.typicode.com/posts/3`
   For each URL, make a request, print the response status, and then wait for exactly 2 seconds using `time.sleep()` before the next request.
3. Write a Python script to send a `GET` request to `https://httpbin.org/headers` with a custom `User-Agent` named `"MyStudyBot/1.0"`. Parse the JSON response to prove that the server received your custom User-Agent.
