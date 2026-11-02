# Day 7 - Task 1: Essential Built-in Modules

## Example (already solved, for reference only)

Problem: Write a program that generates a random number between 1 and 10 and prints its square root using the `math` and `random` modules.

```python
import math
import random

num = random.randint(1, 10)
root = math.sqrt(num)
print(f"Random number: {num}, Square root: {root:.2f}")
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

---

## Your Tasks

1. Write a Python program that generates a list of 5 random integers between 10 and 50. Sort the list in ascending order and print it.
2. Ask the user for their year, month, and day of birth (using input). Write a script that calculates and prints their exact age in years today.
3. Write a dice rolling simulator game. Generate two random numbers between 1 and 6 (representing two dice) and print the sum. If the sum is 7 or 11, print "You Win!", otherwise print "Try Again!".
4. Write a program that formats the current date and time in the following format: `"Wednesday, 22-July-2026 11:30 AM"`. (Hint: check `strftime` format codes online).
