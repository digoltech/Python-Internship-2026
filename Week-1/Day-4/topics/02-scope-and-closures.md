# Day 4 - Topic 2: Scope and Closures

## Why this topic matters

Scope decides where a variable can be accessed from. Many confusing bugs in
beginner code happen because of a misunderstanding of scope. This topic also
covers closures, which are the foundation behind how decorators work.

## 1. Local scope

```python
def calculate():
    result = 100
    print(result)

calculate()

try:
    print(result)
except NameError as error:
    print("Cannot access local variable from outside:", error)
```

A variable created inside a function exists only inside that function and
disappears once the function finishes running.

## 2. Global scope

```python
app_name = "Internship Portal"

def show_app_name():
    print(app_name)

show_app_name()
```

A variable created outside any function is global and can be read inside
any function.

## 3. The global keyword

```python
counter = 0

def increase():
    global counter
    counter += 1

increase()
increase()
increase()
print(counter)
```

Without the `global` keyword, `counter += 1` inside the function would try
to create a new local variable called `counter` and would raise an error,
because Python would try to read it before assigning it.

## 4. LEGB rule

Python looks up a variable name in this exact order: Local, Enclosing,
Global, Built-in.

```python
value = "global value"

def outer():
    value = "enclosing value"

    def inner():
        value = "local value"
        print(value)

    inner()
    print(value)

outer()
print(value)
```

Each `value` here is a completely separate variable living in its own
scope. The innermost scope always wins first when Python looks up a name.

## 5. Enclosing scope and nonlocal

```python
def outer_counter():
    count = 0

    def increment():
        nonlocal count
        count += 1
        return count

    return increment

counter = outer_counter()
print(counter())
print(counter())
print(counter())
```

`nonlocal` lets an inner function modify a variable that belongs to its
enclosing function, not the global scope.

## 6. Closures

```python
def make_multiplier(factor):
    def multiply(number):
        return number * factor
    return multiply

double = make_multiplier(2)
triple = make_multiplier(3)

print(double(10))
print(triple(10))
```

A closure is an inner function that remembers the variables from its
enclosing function, even after the outer function has already finished
running. `double` and `triple` each remember their own separate `factor`
value.

## 7. A practical closure example

```python
def create_bank_account(balance):
    def deposit(amount):
        nonlocal balance
        balance += amount
        return balance

    def withdraw(amount):
        nonlocal balance
        if amount > balance:
            return "Insufficient funds"
        balance -= amount
        return balance

    return deposit, withdraw

deposit, withdraw = create_bank_account(1000)
print(deposit(500))
print(withdraw(2000))
print(withdraw(300))
```

This shows how closures can keep private state, here `balance`, without
needing a class. Each call to `create_bank_account` creates a completely new
and independent `balance`.

## 8. Built-in scope

```python
print(len("python"))
print(max(3, 9, 1))
```

`len` and `max` are not defined by you, they come from Python's built-in
scope, which is the last place Python checks when looking up a name.

## Summary

- Local variables exist only inside the function that creates them.
- `global` allows a function to modify a global variable.
- `nonlocal` allows a nested function to modify a variable in its enclosing
  function.
- A closure is a function that remembers values from its enclosing scope
  even after that scope has finished executing.
- Closures are the foundation behind how decorators are able to wrap
  another function.
