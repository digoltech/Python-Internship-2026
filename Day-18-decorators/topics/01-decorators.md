# Day 18 - Topic 1: Decorators

## Why this topic matters

Imagine you have 10 functions, and you want to add the same extra behaviour to all of them — for example, printing `"Function started"` before running and `"Function finished"` after. Without help, you would have to edit every single function, repeating the same code again and again.

A **decorator** lets you **wrap** a function with extra logic without changing the function itself. Decorators are one of Python's most elegant features, and you have already used many of them without knowing it — like `@app.route()` in Flask or `@property` in OOP.

---

## 1. Functions are First-Class Objects

In Python, functions are ordinary objects. You can:

- Assign a function to a variable
- Pass a function as an argument to another function
- Return a function from inside another function

```python
def greet():
    return "Hello!"

# Assigning a function to a new variable (no parentheses!)
say_hello = greet
print(say_hello())  # Hello!

# Returning a function
def outer():
    def inner():
        return "I am inside outer()"
    return inner

my_func = outer()
print(my_func())  # I am inside outer()
```

This ability is the foundation of decorators.

---

## 2. Simple Decorator Function

A decorator is a function that takes a function as input, defines a **wrapper** inside it, and returns the wrapper.

```python
def my_decorator(func):
    def wrapper():
        print("Something before the function runs")
        func()                      # Call the original function
        print("Something after the function runs")
    return wrapper

def say_hello():
    print("Hello, Students!")

# Applying the decorator manually
say_hello = my_decorator(say_hello)
say_hello()
```

Output:

```text
Something before the function runs
Hello, Students!
Something after the function runs
```

---

## 3. The @ Syntax (Syntactic Sugar)

Python provides a shortcut for applying a decorator: place `@decorator_name` on the line directly above the function definition.

```python
def my_decorator(func):
    def wrapper():
        print("Something before the function runs")
        func()
        print("Something after the function runs")
    return wrapper

@my_decorator
def say_hello():
    print("Hello, Students!")

say_hello()
```

`@my_decorator` above `say_hello` is exactly the same as writing `say_hello = my_decorator(say_hello)` at the end of the function definition.

---

## 4. Decorators that Accept Arguments (`*args`, `**kwargs`)

If the decorated function receives parameters, the wrapper must forward them using `*args` (positional) and `**kwargs` (keyword arguments).

```python
def greet_only(func):
    def wrapper(*args, **kwargs):
        print("Welcome!")
        func(*args, **kwargs)
    return wrapper

@greet_only
def introduce(name, age):
    print(f"My name is {name} and I am {age} years old.")

introduce("Rahul", 21)
# Output:
# Welcome!
# My name is Rahul and I am 21 years old.
```

---

## 5. Returning Values from Decorated Functions

Don't forget to **return** the result of the original function, otherwise the decorated function will always give `None`.

```python
def add_one(func):
    def wrapper(*args, **kwargs):
        result = func(*args, **kwargs)
        return result + 1
    return wrapper

@add_one
def add(a, b):
    return a + b

print(add(2, 3))  # 6  (5 + 1)
```

---

## 6. Decorators with Arguments (A Decorator Factory)

When the decorator itself needs configuration (like a message), you add **one more layer** of functions:

```python
def repeat(times):
    # This outer function receives the decorator's argument
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(times):
                func(*args, **kwargs)
        return wrapper
    return decorator

@repeat(times=3)
def say_hi():
    print("Hi!")

say_hi()
# Output: Hi! (printed 3 times)
```

---

## 7. Real-World Use Cases

- **Logging / debugging** — record when a function starts and ends
- **Timing** — measure how long a function takes
- **Access control** — check permissions before running a route (like Flask's `@login_required`)
- **Caching** — store results of expensive calculations

```python
import time

def timer(func):
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        print(f"Function took {time.time() - start:.4f} seconds")
        return result
    return wrapper

@timer
def slow_sum(n):
    return sum(range(n))

slow_sum(1000000)
```

---

## Quick Recap

- Functions in Python are **first-class objects** — they can be assigned, passed, and returned.
- A **decorator** wraps a function to add behaviour without modifying its code.
- `@decorator` is shorthand for `func = decorator(func)`.
- Use `*args, **kwargs` in wrappers to support functions with parameters.
- Always **return** the original function's result.
- Decorators that take arguments need an extra function layer (decorator factory).
