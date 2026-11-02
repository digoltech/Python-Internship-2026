# Day 3 - Task 3: Advanced Dictionaries

## Example (already solved, for reference only)

Problem: Given a sentence, count how many times each word appears and print
the two most common words.

```python
from collections import Counter

sentence = "data is the new oil and data is everywhere around us"
words = sentence.split()
counts = Counter(words)
print(counts.most_common(2))
```

Use the same style of thinking for the tasks below. Do not look at the
example code while solving them, write your own logic.

## Your Tasks

1. Create a dictionary that stores at least 5 products as keys and their
   prices as values. Write a dictionary comprehension that creates a new
   dictionary containing only the products priced above 100.

2. You are given a list of student dictionaries, for example
   `[{"name": "Riya", "marks": 88}, {"name": "Aman", "marks": 95}]`.
   Write code that finds the student with the highest marks without using
   `max()` directly on the marks, use your own loop based comparison.

3. Build a nested dictionary that represents a small library, where each key
   is a book ID and each value is another dictionary containing the title,
   author, and number of available copies. Write code that reduces the
   available copies of one specific book by 1, as if it was just issued.

4. Take a list of words with repeated letters such as
   `["apple", "ant", "banana", "bat", "cat", "carrot"]`. Group these words
   by their first letter into a dictionary where each key is a letter and
   the value is a list of words, using `setdefault()`.

5. Two dictionaries represent default settings and user-chosen settings for
   an app. Merge them so that user settings override the defaults wherever
   they overlap, and print the final combined settings.

6. Create a dictionary of employee names and their salaries. Sort this
   dictionary by salary in descending order and print the top 3 highest
   paid employees only.

7. Write a small "inventory system" using a dictionary where the product
   name is the key and the quantity is the value. It should support adding
   new stock, reducing stock when an item is sold, and safely handling the
   case where someone tries to sell a product that does not exist in the
   dictionary.
