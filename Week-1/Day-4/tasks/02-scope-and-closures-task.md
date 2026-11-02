# Day 4 - Task 2: Scope and Closures

## Example (already solved, for reference only)

Problem: Create a closure based counter that starts from a given number and
increases by 1 every time it is called.

```python
def make_counter(start):
    count = start

    def increment():
        nonlocal count
        count += 1
        return count

    return increment

counter = make_counter(10)
print(counter())
print(counter())
print(counter())
```

Use the same style of thinking for the tasks below. Do not look at the
example code while solving them, write your own logic.

## Your Tasks

1. Write a function that uses a global variable to keep track of how many
   times it has been called in total, across multiple calls. Call it 4
   times and print the final count.

2. Write a closure function `make_greeting(language)` that returns a
   function which greets a name in either English or Hindi depending on
   the language passed when `make_greeting` was first called. For example,
   `make_greeting("hindi")` should return a function that prints
   `Namaste, <name>` when called with a name.

3. Create two completely independent counters using the same closure
   function from the example, and prove they do not affect each other by
   calling each one a different number of times and printing both results.

4. Write a function with a nested inner function where the outer function
   has a variable `status = "pending"`. The inner function should change
   this to `"completed"` using `nonlocal`, and the outer function should
   print the final status after calling the inner function.

5. Write a small script with three variables all named `mode`, one global,
   one inside an outer function, and one inside an inner function nested
   inside that outer function. Print all three at the correct points in the
   code to clearly show the LEGB lookup order in action.

6. Write a closure based function `make_validator(min_value)` that returns a
   function which checks if a given number is greater than or equal to
   `min_value`. Create two different validators with different minimum
   values and test both with a few numbers.
