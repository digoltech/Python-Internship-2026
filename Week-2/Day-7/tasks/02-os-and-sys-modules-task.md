# Day 7 - Task 2: System Interaction (os and sys)

## Example (already solved, for reference only)

Problem: Write a program that checks if a file name is passed as a command-line argument. If not, exit the script.

```python
import sys

if len(sys.argv) < 2:
    print("Error: Please provide a filename.")
    sys.exit()

print("Filename provided:", sys.argv[1])
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

---

## Your Tasks

1. Write a script `print_env.py` that checks if an environment variable named `USER_KEY` exists. If it does, print it. If it doesn't, print "Key not found".
2. Write a Python script that lists all the files in your current working directory and prints only the files that end with `.py`.
3. Create a CLI script `calculator.py` that takes three command-line arguments: a number, an operator (`+` or `-`), and another number, and prints the result. E.g., running `python calculator.py 5 + 3` should print `8`. If the user doesn't pass 3 arguments, print a helpful error message and exit using `sys.exit()`.
