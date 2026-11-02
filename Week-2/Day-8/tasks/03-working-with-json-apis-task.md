# Day 8 - Task 3: Working with JSON APIs

## Example (already solved, for reference only)

Problem: Fetch a dummy post from JSONPlaceholder API and print the title.

```python
import requests

url = "https://jsonplaceholder.typicode.com/posts/1"
response = requests.get(url)

if response.status_code == 200:
    post = response.json()
    print("Post Title:", post["title"])
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

---

## Your Tasks

1. Write a script that fetches a list of todos from `https://jsonplaceholder.typicode.com/todos` (returns a list of 200 dictionaries). 
   - Loop through the first 5 todos.
   - For each todo, print its ID, Title, and whether it is completed (`Completed: True/False`).
2. Write a script that requests details for a user with ID `5` from `https://jsonplaceholder.typicode.com/users/5`. Print the following details formatted cleanly:
   - User's Name
   - Company Name (Hint: look at the nested `"company"` dictionary keys).
3. Write a Python function `get_post_details(post_id)` that accepts an integer `post_id`. The function should fetch the post from `https://jsonplaceholder.typicode.com/posts/{post_id}` and return the dictionary. Test your function by calling it with `post_id = 12` and printing the returned result.
