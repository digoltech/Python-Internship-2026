# Day 18 - Task 1: Decorators

## Example (already solved, for reference only)

Problem: Create a decorator that prints a border line before and after the function runs.

```python
def border(func):
    def wrapper(*args, **kwargs):
        print("----------")
        func(*args, **kwargs)
        print("----------")
    return wrapper

@border
def welcome():
    print("Welcome to Python!")

welcome()
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

---

## Your Tasks

1. Explain in your own words (2-3 sentences):
   - What problem do decorators solve, and why are they better than editing every function manually?
   - What is the difference between `@decorator` and writing `func = decorator(func)`?
2. Write a decorator `shout` that prints every line of the decorated function's output in **uppercase**. Apply it to a function `greet()` that prints `"hello world"`, then call it and verify the output.
3. Write a decorator `count_calls` that keeps and prints how many times the decorated function has been called. Apply it to a function `display_menu()`, then call `display_menu()` three times and check that the counter prints `1`, `2`, and `3`.
4. Write a decorator `only_positive` that works on a function accepting two numbers: if either number is negative, print `"Negative input not allowed"` and do **not** call the function; otherwise call the function normally. Apply it to a function `add(a, b)` that returns the sum, and test with both positive and negative inputs.
5. Create a decorator factory `greet_with(name)` that returns a decorator which prints `"Hello, <name>! Before execution"` before and `"Goodbye, <name>! After execution"` after the decorated function runs. Apply it with the name `"Student"` to a function `show_report()` that prints `"Generating report..."`, and run it.
