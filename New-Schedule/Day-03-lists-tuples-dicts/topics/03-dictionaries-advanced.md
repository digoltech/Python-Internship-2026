# Day 3 - Topic 3: Advanced Dictionaries

## Why this topic matters

A dictionary stores data as key-value pairs and is one of the most used
structures in real applications, from configuration files to API responses.
This topic goes beyond basic key access and focuses on patterns used in
production code.

## 1. Quick recap

```python
student = {"name": "Riya", "age": 21, "course": "Python"}
print(student["name"])
print(student.get("city", "Not Available"))
```

`get()` is safer than direct key access because it returns a default value
instead of raising an error when the key is missing.

## 2. Looping through a dictionary

```python
prices = {"pen": 10, "notebook": 40, "bag": 500}

for key in prices:
    print(key)

for key, value in prices.items():
    print(key, "costs", value)

for value in prices.values():
    print(value)
```

## 3. Dictionary comprehension

```python
numbers = [1, 2, 3, 4, 5]
squares = {n: n * n for n in numbers}
print(squares)

prices = {"pen": 10, "notebook": 40, "bag": 500}
discounted = {item: cost * 0.9 for item, cost in prices.items()}
print(discounted)

passed_only = {item: cost for item, cost in prices.items() if cost > 20}
print(passed_only)
```

## 4. Merging dictionaries

```python
defaults = {"theme": "light", "language": "en"}
user_settings = {"language": "hi", "notifications": True}

merged = {**defaults, **user_settings}
print(merged)

defaults.update(user_settings)
print(defaults)
```

When the same key appears in both dictionaries, the value from the one
written later wins.

## 5. Nested dictionaries

```python
students = {
    "101": {"name": "Riya", "marks": [85, 90, 78]},
    "102": {"name": "Aman", "marks": [70, 60, 88]},
}

print(students["101"]["name"])
print(students["102"]["marks"][1])

for roll, info in students.items():
    average = sum(info["marks"]) / len(info["marks"])
    print(roll, info["name"], round(average, 2))
```

## 6. setdefault for building grouped data

```python
words = ["apple", "banana", "avocado", "blueberry", "cherry"]

grouped = {}
for word in words:
    first_letter = word[0]
    grouped.setdefault(first_letter, []).append(word)

print(grouped)
```

`setdefault()` checks if a key exists, and if it does not, creates it with
the given default value before returning it. This avoids writing a manual
`if key not in dict` check inside the loop.

## 7. Counting with a dictionary

```python
text = "the quick brown fox jumps over the lazy dog the fox ran"
words = text.split()

frequency = {}
for word in words:
    frequency[word] = frequency.get(word, 0) + 1

print(frequency)

from collections import Counter
print(Counter(words))
print(Counter(words).most_common(2))
```

`Counter` from the `collections` module does the same job in one line and
also gives a `most_common()` method for free.

## 8. Sorting a dictionary by value

```python
marks = {"Riya": 88, "Aman": 95, "Sara": 72, "Kabir": 91}

sorted_by_marks = dict(sorted(marks.items(), key=lambda item: item[1], reverse=True))
print(sorted_by_marks)
```

Dictionaries cannot be sorted in place, so the common pattern is to sort the
`.items()` view and rebuild a new dictionary from the result.

## 9. Removing keys safely

```python
settings = {"theme": "dark", "language": "en", "beta": True}

removed_value = settings.pop("beta", None)
print(removed_value)
print(settings)

if "language" in settings:
    del settings["language"]
print(settings)
```

`pop()` with a default value never raises an error even if the key is
missing, which makes it safer than `del`.

## 10. Dictionary keys must be hashable

```python
valid = {(1, 2): "point A", "name": "Riya"}
print(valid)

try:
    invalid = {[1, 2]: "point A"}
except TypeError as error:
    print("Lists cannot be dictionary keys:", error)
```

Tuples can be dictionary keys because they are immutable, but lists cannot,
because they can change after being used as a key, which would break the
internal hashing.

## Summary

- `get()`, `pop()`, and `setdefault()` make dictionary access safer than
  direct key lookups.
- Dictionary comprehensions build filtered or transformed dictionaries in
  one line.
- `Counter` is the fastest way to count occurrences of items.
- Sorting a dictionary always means sorting its items and rebuilding a new
  dictionary.
