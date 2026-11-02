# Day 8 - Topic 2: How the Web Works & The Requests Library

## Why this topic matters

Almost every modern application communicates over the internet. When you open a website, check your Instagram feed, or send a message, your app is communicating with a remote computer (a server) across the globe.

To write Python scripts that fetch weather data, send emails, or load live information, you need to understand how the web works and how to make **HTTP Requests** using Python's popular `requests` library.

---

## 1. The Client-Server Model (The Restaurant Analogy)

Think of the internet like a restaurant:
- **Client (You):** The customer who sits at the table and orders food. Your browser (Chrome) or Python script acts as the Client.
- **Server (Remote Computer):** The kitchen where the food is prepared. The server holds the databases, websites, and APIs.
- **Request (Order):** The order you place. You ask the waiter to bring you a specific dish.
- **Response (Food):** The food the waiter brings back from the kitchen.

---

## 2. What is HTTP?

HTTP (HyperText Transfer Protocol) is the language that clients and servers use to talk to each other. When a client sends a request, it specifies an **HTTP Method** to tell the server what action to take:

- **`GET`:** "Please send me some data/web page." (Used 90% of the time to read data).
- **`POST`:** "Please save this new data I am sending you." (Used when submitting a form, logging in, or uploading a file).

---

## 3. HTTP Status Codes

When a server replies to your request, it sends a numeric **Status Code** to indicate what happened:

- **`200 OK`:** Success! Everything went well.
- **`404 Not Found`:** The requested page/data does not exist.
- **`500 Internal Server Error`:** The server had a bug or crashed.

---

## 4. Making a GET Request in Python

To communicate with the web, we use the `requests` package (which we install via `pip`).

```python
import requests

# Send a GET request to a website
response = requests.get("https://www.google.com")

# Print the Status Code
print("Status Code:", response.status_code)  # Output: 200

# Check if the request was successful
if response.status_code == 200:
    print("Success!")
    # Print the raw HTML content of the page (truncated for readability)
    print(response.text[:200])
else:
    print("Request failed!")
```
`response.text` contains the raw text response (HTML code) sent back by the server.
