# Day 17 - Task 1: Iterators and Generators

## Example (already solved, for reference only)

Problem: Create a generator that yields the squares of numbers from 1 to 3.

```python
def squares(n):
    for i in range(1, n + 1):
        yield i * i

for value in squares(3):
    print(value)
# Output: 1, 4, 9
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

---

## Your Tasks

1. Explain in your own words (2-3 sentences):
   - What is the difference between a normal function that uses `return` and a generator function that uses `yield`?
   - Why are generators more memory-efficient than lists when working with large data?
2. Create a custom iterator class `EvenNumbers` that generates even numbers starting from 2. It should stop after producing the first `n` even numbers (e.g., `EvenNumbers(4)` yields `2, 4, 6, 8`). Loop over it with a `for` loop and print the results.
3. Write a generator function `filter_positive(numbers)` that takes a list of integers and yields only the positive ones, one at a time. Test it with the list `[3, -1, 7, -9, 0, 5, -2]` and print each yielded value.
4. Create a generator expression that produces the first 5 cube values (`x ** 3`), then convert it into a list and print the list.
5. Write an infinite generator `natural_numbers()` that yields `1, 2, 3, ...` forever. Using a loop (or repeated `next()` calls), extract and print only the first 8 natural numbers from it.
