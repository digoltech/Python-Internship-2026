# Day 17 - Topic 1: Iterators and Generators

## Why this topic matters

So far you have stored data in lists, tuples, and dictionaries. But what if you need to loop over a million items? Creating a list with a million numbers in memory can slow down or even crash your program.

**Iterators** and **Generators** solve this problem. An iterator lets you fetch items **one at a time**, and a generator is the easiest way to create one. Instead of building the whole sequence in memory, a generator produces each value **only when you ask for it**. This concept powers many built-in features of Python, like `for` loops, `zip()`, and file reading.

---

## 1. What is an Iterator?

An **iterator** is an object that returns data from a collection, **one element at a time**, and remembers its position between calls. You create one using `iter()` and fetch the next value using `next()`.

```python
numbers = [10, 20, 30]

# iter() creates an iterator object from the list
my_iterator = iter(numbers)

print(next(my_iterator))  # 10
print(next(my_iterator))  # 20
print(next(my_iterator))  # 30
# print(next(my_iterator))  # Raises StopIteration error - no more items!
```

A `for` loop works internally in exactly this way — it keeps calling `next()` until the iterator is exhausted.

```python
my_iterator = iter([1, 2, 3])

for item in my_iterator:
    print(item)
# Output: 1, 2, 3 (printed line by line)
```

---

## 2. Making Your Own Iterator with a Class

Any class that defines `__iter__()` and `__next__()` becomes an iterator. This is useful when you want to generate a **custom sequence** without storing it in a list.

```python
class CountDown:
    def __init__(self, start):
        self.current = start

    def __iter__(self):
        return self

    def __next__(self):
        if self.current <= 0:
            raise StopIteration  # Tells the loop: "I'm done!"
        value = self.current
        self.current -= 1
        return value

# Loop over 5, 4, 3, 2, 1 without creating a list
for num in CountDown(5):
    print(num)
```

---

## 3. The Problem Generators Solve

Writing a full iterator class with `__iter__` and `__next__` is verbose. **Generators** let you write the same logic in a simple function using the `yield` keyword.

```python
def countdown(start):
    # yield pauses the function and sends a value back,
    # keeping the function's state alive for the next call
    while start > 0:
        yield start
        start -= 1

for num in countdown(5):
    print(num)
# Output: 5, 4, 3, 2, 1
```

Key differences from a normal function:

| Normal function (`return`) | Generator function (`yield`) |
|---|---|
| Runs fully, returns once | Pauses at each `yield` |
| Returns a single value | Produces a sequence of values |
| Stores all results in memory | Stores only one value at a time |

```python
def square_numbers(n):
    for i in range(n):
        yield i * i

# Each call to next() runs the function until the next yield
gen = square_numbers(4)
print(next(gen))  # 0
print(next(gen))  # 1
print(next(gen))  # 4
```

---

## 4. Generator Expressions

Just like list comprehensions, generators have their own short syntax using **round brackets** `()`. Notice the difference in memory usage:

```python
# List comprehension: creates the full list in memory at once
square_list = [x * x for x in range(1000000)]

# Generator expression: creates one value at a time when needed
square_gen = (x * x for x in range(1000000))

print(type(square_list))  # <class 'list'>
print(type(square_gen))   # <class 'generator'>
```

You can loop over the generator directly, or convert it when you really need a list:

```python
gen = (x * x for x in range(5))

for value in gen:
    print(value)   # 0, 1, 4, 9, 16

# Convert to list only if needed
square_list = list((x * x for x in range(5)))
```

---

## 5. Why Generators Matter: Memory Efficiency

Suppose you want to read a file with 10 million lines. Loading it into a list would consume huge amounts of RAM. Generators process **one line at a time**.

```python
def read_large_file(file_path):
    with open(file_path, "r") as file:
        for line in file:
            yield line.strip()

# Only one line is held in memory at any moment
for line in read_large_file("large_data.txt"):
    print(line)
```

Other real-world uses of generators:

- Processing data from APIs or databases in chunks
- Infinite sequences (e.g., Fibonacci numbers — a list can't be infinite!)
- Pipelines where you chain generators together for filtering and transforming data

```python
def fibonacci():
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a + b

# Take the first 6 Fibonacci numbers from an infinite generator
fib = fibonacci()
result = [next(fib) for _ in range(6)]
print(result)  # [0, 1, 1, 2, 3, 5]
```

---

## Quick Recap

- An **iterator** is an object that produces items one at a time using `next()`.
- `iter()` converts a collection into an iterator; the loop ends with `StopIteration`.
- A **generator** is a simpler way to build iterators using a function with `yield`.
- **Generator expressions** `(... for ...)` create generators without a separate function.
- Generators are **lazy** — they compute values on demand and save memory.
