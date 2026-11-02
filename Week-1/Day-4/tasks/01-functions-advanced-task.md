# Day 4 - Task 1: Functions - Advanced

## Example (already solved, for reference only)

Problem: Write a function that accepts any number of numbers and returns
their average.

```python
def average(*numbers):
    if len(numbers) == 0:
        return 0
    return sum(numbers) / len(numbers)

print(average(10, 20, 30))
print(average(5, 15))
```

Use the same style of thinking for the tasks below. Do not look at the
example code while solving them, write your own logic.

## Your Tasks

1. Write a function `build_invoice` that accepts a customer name as a
   normal parameter, any number of item prices using `*args`, and any number
   of extra details such as discount or tax using `**kwargs`. The function
   should print the customer name, the total of all item prices, and all
   the extra details.

2. Write a function `apply_discount(price, percent=10)` where the discount
   percent has a default value of 10. Call it once using only the price, and
   once using both arguments with the discount passed as a keyword argument.

3. Using `map()` and a lambda, convert a list of temperatures in Celsius
   into Fahrenheit, where the formula is `(celsius * 9/5) + 32`.

4. Using `filter()` and a lambda, take a list of usernames and keep only the
   ones that are at least 6 characters long.

5. Using `functools.reduce()`, find the largest number in a list without
   using the built in `max()` function.

6. Write a recursive function that calculates the sum of all numbers from 1
   to n, where n is passed as an argument. Do not use a loop or the formula
   `n * (n + 1) / 2`, the function must call itself.

7. Write a decorator called `timer` that prints how long a function took to
   run in seconds. Apply it to a function that calculates the sum of numbers
   from 1 to 1000000.

8. Write a decorator called `require_positive` that checks if all arguments
   passed to a function are positive numbers. If any argument is negative or
   zero, it should print an error message and not call the original
   function at all. Apply it to a simple `divide(a, b)` function.
