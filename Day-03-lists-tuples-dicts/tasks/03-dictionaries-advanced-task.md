# Day 3 - Task 3: Advanced Dictionaries

## Example (already solved, for reference only)

Problem: Count how many times each word appears in a sentence using a dictionary.

```python
text = "the cat sat on the mat the cat ran"
words = text.split()
frequency = {}
for word in words:
    frequency[word] = frequency.get(word, 0) + 1
print(frequency)
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

## Your Tasks

1. Take a dictionary of student names and their marks. Using a dictionary comprehension, create a new dictionary that only contains students who scored above 75.

2. You are given two dictionaries: `default_settings` and `user_settings`. Merge them into one dictionary where values from `user_settings` override `default_settings` when the same key exists. Do this using the `{**a, **b}` syntax.

3. Take a list of words and build a dictionary that groups them by their first letter. Each key should be a letter, and each value should be a list of words starting with that letter. Use `setdefault()` for this.

4. Given a dictionary of product names and their prices, sort the dictionary so that the most expensive product appears first. Print the sorted dictionary.

5. You are given a nested dictionary representing a class roster. Each student has a name and a list of marks. Write code that calculates each student's average mark and prints it alongside their name.

6. Take a dictionary of employee names and their departments. Write code that removes an employee by name using `pop()` without raising an error if the name doesn't exist. Also remove a key using `del` only if it exists — verify both cases work correctly.

7. Create a dictionary from two lists of equal length: one of keys and one of values, using `zip()` and `dict()`. Then add a new key-value pair to it and print the result.
