# Day 4 - Task 3: Exception Handling

## Example (already solved, for reference only)

Problem: Write a function that safely converts a list of text values into
numbers, skipping any value that cannot be converted.

```python
def convert_to_numbers(values):
    numbers = []
    for value in values:
        try:
            numbers.append(float(value))
        except ValueError:
            print("Skipping invalid value:", value)
    return numbers

print(convert_to_numbers(["10", "20", "abc", "30.5", "xyz"]))
```

Use the same style of thinking for the tasks below. Do not look at the
example code while solving them, write your own logic.

## Your Tasks

1. Write a function `safe_division(a, b)` that returns the result of `a / b`
   and handles both `ZeroDivisionError` and `TypeError` separately with two
   different, clear error messages.

2. Write a function that takes a list and an index, and tries to access the
   value at that index. If the index does not exist, catch the
   `IndexError` and return `None` instead of letting the program crash.

3. Create a custom exception called `InvalidAgeError`. Write a function
   `register_user(age)` that raises this custom exception if the age is
   below 0 or above 120, with a clear message describing what went wrong.

4. Write a function `read_file_safely(filename)` that tries to open and read
   a file. If the file does not exist, it should catch `FileNotFoundError`
   and return the text `"File not found"` instead of crashing the program.

5. Write a loop that keeps asking the user to enter a number between 1 and
   10 until they enter a valid one. Use exception handling to deal with
   non-numeric input, and a separate check with a custom raised exception
   for numbers outside the 1 to 10 range.

6. Write a function `process_order(order)` where `order` is expected to be a
   dictionary with `"item"` and `"price"` keys. Use a `try-except-else
   -finally` block so that it prints the order details if everything is
   fine, prints a clear error if a key is missing, and always prints
   `"Processing complete"` at the very end no matter what happened.
