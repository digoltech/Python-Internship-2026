# Day 3 - Topic 2: Tuples and Sets

## Part A: Tuples

### Why tuples exist

A tuple looks like a list but cannot be changed after creation. This makes it
useful for data that should stay fixed, such as coordinates, RGB colors, or a
record returned from a function.

```python
point = (4, 7)
color = (255, 0, 0)
person = ("Riya", 21, "Pune")
```

### Tuples are immutable

```python
point = (4, 7)
try:
    point[0] = 10
except TypeError as error:
    print("Cannot modify a tuple:", error)
```

If a tuple holds a mutable object such as a list, that inner object can
still change, only the tuple's own slots cannot be reassigned.

```python
record = ("Riya", [85, 90, 78])
record[1].append(100)
print(record)
```

### Tuple unpacking

```python
person = ("Riya", 21, "Pune")
name, age, city = person
print(name, age, city)

first, *rest = (1, 2, 3, 4, 5)
print(first)
print(rest)

a, b = 5, 10
a, b = b, a
print(a, b)
```

The `*rest` syntax collects all remaining values into a list. This is very
useful when you do not know exactly how many values are coming.

### Tuples in function returns

```python
def min_max(numbers):
    return min(numbers), max(numbers)

low, high = min_max([4, 8, 1, 9, 3])
print(low, high)
```

A function can only return one value, but that value can be a tuple holding
several pieces of data, which is why this pattern is so common.

### Why use a tuple over a list

```python
import sys

sample_list = [1, 2, 3, 4, 5]
sample_tuple = (1, 2, 3, 4, 5)

print(sys.getsizeof(sample_list))
print(sys.getsizeof(sample_tuple))
```

Tuples take less memory than lists with the same data and are slightly
faster to create, because Python does not need to reserve extra space for
future growth.

## Part B: Sets

### Why sets exist

A set stores only unique values with no fixed order, and is built for very
fast membership checks.

```python
fruits = {"apple", "banana", "apple", "mango", "banana"}
print(fruits)
```

Duplicate values are automatically dropped.

### Fast membership testing

```python
allowed_users = {"riya", "aman", "sara", "kabir"}

username = "aman"
if username in allowed_users:
    print("Access granted")
else:
    print("Access denied")
```

Checking membership in a set is much faster than checking membership in a
list once the data grows large, because a set uses hashing internally.

### Core set operations

```python
python_devs = {"riya", "aman", "sara"}
java_devs = {"sara", "kabir", "riya"}

print(python_devs.union(java_devs))
print(python_devs.intersection(java_devs))
print(python_devs.difference(java_devs))
print(python_devs.symmetric_difference(java_devs))
```

- `union` combines both sets.
- `intersection` keeps only values present in both.
- `difference` keeps values that are only in the first set.
- `symmetric_difference` keeps values that are in exactly one of the sets.

### Modifying a set

```python
skills = {"python", "sql"}
skills.add("git")
skills.update(["docker", "linux"])
skills.discard("sql")
print(skills)
```

`discard()` is safer than `remove()` because it does not raise an error if
the value is missing.

### Removing duplicates from a list using a set

```python
emails = ["a@mail.com", "b@mail.com", "a@mail.com", "c@mail.com"]
unique_emails = list(set(emails))
print(unique_emails)
```

This is the fastest way to remove duplicates when the original order does
not matter.

### Set comprehension

```python
numbers = [1, 2, 2, 3, 4, 4, 5]
even_set = {n for n in numbers if n % 2 == 0}
print(even_set)
```

### Frozenset for a read-only set

```python
locked_permissions = frozenset(["read", "write"])
print(locked_permissions)
```

A `frozenset` behaves like a set but cannot be modified, which makes it safe
to use as a dictionary key or inside another set.

## Summary

- Tuples are immutable, slightly faster, and signal that data should not
  change.
- Unpacking with `*rest` is a clean way to split a sequence of unknown
  length.
- Sets remove duplicates automatically and give very fast membership checks.
- `union`, `intersection`, `difference`, and `symmetric_difference` are the
  four core set operations used to compare two groups of data.
