# Day 3 - Topic 1: Advanced Lists

## Why this topic matters

Lists are the most used data structure in Python. In real projects you rarely
just create a list and print it. You filter it, transform it, sort it, search
it, and combine it with other lists. This topic moves beyond basic list
creation and focuses on the techniques that show up in real code and in
interviews.

## 1. Quick recap with a twist

A list can hold mixed data types and can be nested.

```python
student = ["Riya", 21, [85, 90, 78], True]
print(student[2])
print(student[2][1])
```

`student[2]` returns the inner list, and `student[2][1]` returns the second
value inside that inner list.

## 2. Slicing in depth

Slicing uses the pattern `list[start:stop:step]`.

```python
numbers = [10, 20, 30, 40, 50, 60, 70, 80]

print(numbers[2:6])
print(numbers[:4])
print(numbers[4:])
print(numbers[::2])
print(numbers[::-1])
print(numbers[-3:])
```

`numbers[::-1]` reverses the list without changing the original list, because
slicing always returns a new list.

## 3. Replacing and removing with slices

```python
data = [1, 2, 3, 4, 5]
data[1:3] = [20, 30, 40]
print(data)

data[1:4] = []
print(data)
```

You can insert more or fewer elements than you removed. This is a very
common trick for editing the middle of a list without using a loop.

## 4. List comprehensions

A list comprehension builds a new list in a single readable line. The general
shape is `[expression for item in iterable if condition]`.

```python
squares = [n * n for n in range(1, 11)]
print(squares)

even_squares = [n * n for n in range(1, 11) if n % 2 == 0]
print(even_squares)

names = ["riya", "aman", "sara", "kabir"]
capitalized = [name.title() for name in names]
print(capitalized)
```

You can also add an `if-else` inside the expression itself.

```python
marks = [45, 90, 33, 78, 55]
result = ["Pass" if m >= 40 else "Fail" for m in marks]
print(result)
```

## 5. Nested comprehensions

```python
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flattened = [value for row in matrix for value in row]
print(flattened)

transposed = [[row[i] for row in matrix] for i in range(3)]
print(transposed)
```

`flattened` turns a 2D list into a single 1D list. `transposed` swaps rows
and columns, which is how a basic matrix transpose works without using any
external library.

## 6. Sorting with custom logic

`sort()` changes the list in place, `sorted()` returns a new list.

```python
scores = [("Riya", 88), ("Aman", 95), ("Sara", 72)]

scores.sort(key=lambda item: item[1])
print(scores)

top_scorer_first = sorted(scores, key=lambda item: item[1], reverse=True)
print(top_scorer_first)

words = ["banana", "kiwi", "apple", "fig"]
words.sort(key=len)
print(words)
```

`key` tells Python exactly what value to use for comparison instead of
comparing the items directly. This is the single most useful sorting trick
in Python.

## 7. Useful built-in functions on lists

```python
prices = [199, 49, 999, 15, 320]

print(max(prices))
print(min(prices))
print(sum(prices))
print(sum(prices) / len(prices))
print(sorted(prices))
print(any(p > 900 for p in prices))
print(all(p > 0 for p in prices))
```

`any()` returns `True` if at least one value matches the condition, `all()`
returns `True` only if every value matches.

## 8. Removing duplicates while keeping order

```python
visits = ["home", "shop", "home", "cart", "shop", "checkout"]

unique_ordered = []
for page in visits:
    if page not in unique_ordered:
        unique_ordered.append(page)

print(unique_ordered)
```

Converting to a `set` also removes duplicates, but it does not guarantee the
original order, which is why this loop-based pattern is still used when order
matters.

## 9. Zipping multiple lists together

```python
names = ["Riya", "Aman", "Sara"]
marks = [88, 95, 72]

combined = list(zip(names, marks))
print(combined)

for name, mark in zip(names, marks):
    print(name, "scored", mark)
```

`zip()` pairs items from multiple lists at the same index, which avoids
manual index based loops.

## 10. List as a stack and as a queue

```python
stack = []
stack.append(10)
stack.append(20)
stack.append(30)
print(stack.pop())
print(stack)

from collections import deque
queue = deque([1, 2, 3])
queue.append(4)
print(queue.popleft())
print(queue)
```

A plain list works well as a stack because `append()` and `pop()` both work
on the end of the list in constant time. For a queue, `deque` is preferred
because removing from the front of a normal list is slow for large data.

## 11. Copying lists correctly

```python
original = [1, 2, [3, 4]]

shallow = original.copy()
shallow[0] = 100
print(original)

shallow[2][0] = 999
print(original)

import copy
deep = copy.deepcopy(original)
deep[2][0] = 1
print(original)
```

`copy()` creates a new outer list, but nested lists inside it are still
shared with the original. `copy.deepcopy()` copies every nested level so the
two lists become fully independent.

## Summary

- Slicing can read, replace, and delete parts of a list.
- List comprehensions replace many simple loops with one readable line.
- `sort()` and `sorted()` with a `key` function give you full control over
  ordering.
- `zip()`, `any()`, `all()` make working with multiple lists much shorter.
- Shallow copies are not always safe for nested lists; use `deepcopy` when
  needed.
