# Day 4 - Topic 3: Exception Handling

## Why this topic matters

Real programs deal with unpredictable input, missing files, network
failures, and many other situations that can crash a program. Exception
handling lets a program respond to errors gracefully instead of crashing.

## 1. Basic try and except

```python
try:
    number = int(input("Enter a number: "))
    print(100 / number)
except ZeroDivisionError as error:
    print("You cannot divide by zero:", error)
except ValueError as error:
    print("Please enter a valid number:", error)
```

Python checks each `except` block in order and runs the first one that
matches the type of error that occurred.

## 2. else and finally

```python
try:
    value = int("42")
except ValueError:
    print("Conversion failed")
else:
    print("Conversion succeeded:", value)
finally:
    print("This always runs, success or failure")
```

`else` runs only if no exception occurred. `finally` always runs, whether an
exception occurred or not, and is commonly used for cleanup work such as
closing a file or a network connection.

## 3. Catching multiple exception types together

```python
def safe_divide(a, b):
    try:
        return a / b
    except (ZeroDivisionError, TypeError) as error:
        print("Operation failed:", error)
        return None

print(safe_divide(10, 2))
print(safe_divide(10, 0))
print(safe_divide(10, "two"))
```

## 4. Catching any exception (used carefully)

```python
def risky_operation(data):
    try:
        return data[5] / data[0]
    except Exception as error:
        print("Something went wrong:", type(error).__name__, "-", error)

risky_operation([1, 2])
```

A bare `except Exception` catches almost any error, which is useful for
logging unexpected failures, but it should not be used to silently hide
bugs that should actually be fixed.

## 5. Raising your own exceptions

```python
def withdraw(balance, amount):
    if amount > balance:
        raise ValueError("Insufficient balance for this withdrawal")
    return balance - amount

try:
    withdraw(500, 1000)
except ValueError as error:
    print("Withdrawal failed:", error)
```

`raise` lets your own code trigger an exception when a rule of your program
is broken, even if Python itself would not have raised any error.

## 6. Creating a custom exception class

```python
class InsufficientFundsError(Exception):
    def __init__(self, balance, amount):
        message = f"Cannot withdraw {amount}, balance is only {balance}"
        super().__init__(message)
        self.balance = balance
        self.amount = amount

def withdraw(balance, amount):
    if amount > balance:
        raise InsufficientFundsError(balance, amount)
    return balance - amount

try:
    withdraw(500, 1000)
except InsufficientFundsError as error:
    print(error)
    print("Shortfall amount:", error.amount - error.balance)
```

A custom exception class lets you attach extra information to the error,
here `balance` and `amount`, and lets callers catch your specific error type
separately from generic Python errors.

## 7. Exception chaining with context

```python
def load_config():
    try:
        with open("settings.json") as file:
            return file.read()
    except FileNotFoundError as error:
        raise RuntimeError("Configuration could not be loaded") from error

try:
    load_config()
except RuntimeError as error:
    print(error)
    print("Original cause:", error.__cause__)
```

`raise ... from error` keeps a link to the original exception, so when
debugging later, you can see exactly what caused the higher level error.

## 8. Validating input with a loop and exceptions

```python
def get_valid_age():
    while True:
        try:
            age = int(input("Enter your age: "))
            if age <= 0:
                raise ValueError("Age must be positive")
            return age
        except ValueError as error:
            print("Invalid input, try again:", error)
```

This pattern keeps asking the user for input until a valid value is given,
instead of crashing on the first bad input.

## Summary

- `try`, `except`, `else`, and `finally` together give full control over
  error handling and cleanup.
- Multiple exception types can be caught in one block using a tuple.
- `raise` lets your own code create errors based on your program's rules.
- Custom exception classes can carry extra information about what went
  wrong.
- `raise ... from error` preserves the original cause of an error for
  easier debugging.
