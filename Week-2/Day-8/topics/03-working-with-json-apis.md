# Day 8 - Topic 3: Working with JSON APIs

## Why this topic matters

When developers share data between systems, they rarely send full HTML web pages. HTML contains styling and layout, which is useless for a script that just wants raw information.

Instead, servers send data formatted as **JSON** (JavaScript Object Notation). JSON looks almost exactly like a Python dictionary: it contains key-value pairs. An **API (Application Programming Interface)** is the URL endpoint that serves this raw data.

---

## 1. What does JSON look like?

Here is a simple JSON response:
```json
{
  "name": "Rahul",
  "age": 20,
  "skills": ["Python", "SQL"],
  "is_student": true
}
```
In Python, we convert this directly into a standard Python dictionary so we can read values using keys.

---

## 2. Fetching JSON from a Free API

We will use a free, safe API called **JSONPlaceholder**, which is designed for developers to test their code.

```python
import requests

# Fetch a dummy user profile
url = "https://jsonplaceholder.typicode.com/users/1"
response = requests.get(url)

if response.status_code == 200:
    # Convert the JSON response into a Python dictionary
    user_data = response.json()
    
    # Check what type of object it is
    print("Type of user_data:", type(user_data))  # Output: <class 'dict'>
    
    # Read values from the dictionary
    name = user_data["name"]
    email = user_data["email"]
    city = user_data["address"]["city"]  # Nested dictionary access
    
    print(f"Name: {name}")
    print(f"Email: {email}")
    print(f"City: {city}")
else:
    print(f"Failed to fetch data. Status: {response.status_code}")
```

---

## 3. Handling API Request Errors Safely

APIs can fail due to internet issues, wrong URLs, or offline servers. We should protect our code from crashing by using a try-except block combined with `raise_for_status()`.

```python
import requests

# A non-existent URL to test error handling
invalid_url = "https://jsonplaceholder.typicode.com/invalidpage"

try:
    response = requests.get(invalid_url)
    
    # This raises an exception if the status code is 4xx or 5xx
    response.raise_for_status()
    
    data = response.json()
    print(data)
except requests.exceptions.HTTPError as error:
    print("HTTP Error occurred:", error)
except Exception as err:
    print("An error occurred:", err)
```
This is how professional code is written to handle unstable internet connections or API downtimes!
