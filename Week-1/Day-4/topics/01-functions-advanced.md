# Day 4 - Topic 1: Functions - Advanced

## Why this topic matters

Almost every real Python project is built from functions calling other
functions. Knowing only the basic `def name(parameters):` syntax is not
enough for production code. This topic covers the function features that
make code flexible and reusable.

## 1. Default and keyword arguments

```python
def greet(name, greeting="Hello"):
    print(greeting, name)

greet("Riya")
greet("Aman", "Welcome")
greet(name="Sara", greeting="Hi")
```

Default values let a parameter be optional. Keyword arguments let you call a
function without worrying about the order of parameters.

## 2. *args for variable positional arguments

```python
def total_marks(*marks):
    print(type(marks))
    return sum(marks)

print(total_marks(80, 90, 70))
print(total_marks(60, 70, 80, 90, 100))
```

`*marks` collects any number of positional arguments into a tuple, so the
function works no matter how many values are passed.

## 3. **kwargs for variable keyword arguments

```python
def create_profile(**details):
    for key, value in details.items():
        print(key, ":", value)

create_profile(name="Riya", age=21, city="Pune")
```

`**details` collects keyword arguments into a dictionary, which is very
useful when a function needs to accept flexible, named settings.

## 4. Combining all parameter types

```python
def book_order(book_id, *extra_ids, customer="Guest", **shipping_info):
    print("Main book:", book_id)
    print("Extra books:", extra_ids)
    print("Customer:", customer)
    print("Shipping info:", shipping_info)

book_order(101, 102, 103, customer="Riya", city="Pune", express=True)
```

The required parameter order is always: normal parameters, then `*args`,
then keyword only or default parameters, then `**kwargs`.

## 5. Lambda functions

```python
square = lambda x: x * x
print(square(5))

add = lambda a, b: a + b
print(add(4, 7))

people = [("Riya", 21), ("Aman", 19), ("Sara", 25)]
people.sort(key=lambda person: person[1])
print(people)
```

A lambda is a small, unnamed function written in a single expression, mostly
used when a short function is needed temporarily, such as inside `sort()`,
`map()`, or `filter()`.

## 6. map, filter, and reduce

```python
numbers = [1, 2, 3, 4, 5]

squared = list(map(lambda n: n * n, numbers))
print(squared)

even_only = list(filter(lambda n: n % 2 == 0, numbers))
print(even_only)

from functools import reduce
total = reduce(lambda a, b: a + b, numbers)
print(total)
```

`map()` transforms every item, `filter()` keeps only the items that match a
condition, and `reduce()` combines all items into a single final value.

## 7. Recursion

```python
def factorial(n):
    if n == 0 or n == 1:
        return 1
    return n * factorial(n - 1)

print(factorial(5))

def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)

print([fibonacci(i) for i in range(8)])
```

A recursive function calls itself with a smaller input until it reaches a
base case that stops the recursion. Without a proper base case, recursion
will run forever and eventually crash the program.

## 8. Function annotations and type hints

```python
def calculate_price(quantity: int, rate: float) -> float:
    return quantity * rate

print(calculate_price(3, 49.5))
```

Type hints do not force a data type at runtime, but they make the function
signature much clearer for anyone reading the code, and they help tools
catch mistakes before the code even runs.

## 9. Decorators

```python
def log_call(func):
    def wrapper(*args, **kwargs):
        print("Calling", func.__name__)
        result = func(*args, **kwargs)
        print(func.__name__, "finished")
        return result
    return wrapper

@log_call
def add_numbers(a, b):
    return a + b

print(add_numbers(5, 9))
```

A decorator is a function that wraps another function to add extra
behaviour, such as logging, timing, or access checks, without changing the
original function's code. The `@log_call` line above `add_numbers` is just
a shorter way of writing `add_numbers = log_call(add_numbers)`.

## 10. The walrus operator

```python
data = [10, 25, 40, 55, 70]

if (count := len(data)) > 3:
    print("List has", count, "items, which is more than 3")
```

The walrus operator `:=` assigns a value to a variable as part of a larger
expression, which avoids calculating the same value twice.

## Summary

- `*args` and `**kwargs` make functions flexible with unknown numbers of
  inputs.
- Lambda functions are short, throwaway functions used inline.
- `map`, `filter`, and `reduce` are functional programming tools for
  transforming data without writing loops.
- Recursion solves a problem by reducing it into smaller versions of itself.
- Decorators add reusable behaviour around existing functions.
