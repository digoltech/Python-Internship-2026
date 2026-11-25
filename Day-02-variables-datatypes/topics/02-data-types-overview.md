# Data Types in Python

## Why Data Types Matter

Every value in Python has a type. The type tells Python what kind of data it is dealing with, and what operations are allowed on it. You can add two numbers, but you cannot add a number and a sentence the same way — Python needs to know the type to handle this correctly.

## Real-Life Analogy

Think of a kitchen. Sugar, water, and rice are all stored differently because they behave differently. You cannot pour rice the way you pour water. Similarly, Python stores numbers, text, and true/false values differently because they behave differently.

## The Core Data Types

### 1. Integer (int)

Whole numbers, with no decimal point. Can be positive or negative.

```python
age = 21
year = 2025
temperature = -5
```

### 2. Float (float)

Numbers with a decimal point.

```python
price = 99.99
height = 5.8
pi_value = 3.14159
```

### 3. String (str)

Text data. Always written inside single or double quotes.

```python
name = "Rahul"
city = 'Mumbai'
sentence = "Python is fun"
```

### 4. Boolean (bool)

Represents one of exactly two values: `True` or `False`. Used for decisions and conditions.

```python
is_student = True
is_raining = False
```

Note that `True` and `False` start with a capital letter in Python. This is a strict syntax rule.

## Checking the Type of a Value

Python provides a built-in function called `type()` that tells you the data type of any value or variable.

```python
age = 21
name = "Rahul"
price = 99.99
is_active = True

print(type(age))
print(type(name))
print(type(price))
print(type(is_active))
```

Output:

```
<class 'int'>
<class 'str'>
<class 'float'>
<class 'bool'>
```

## Python Decides the Type Automatically

Unlike some other languages, you do not need to tell Python what type a variable will hold. Python figures it out automatically based on the value you assign. This is called dynamic typing.

```python
value = 10
print(type(value))

value = "now I am text"
print(type(value))
```

Output:

```
<class 'int'>
<class 'str'>
```

The same variable name can hold different types at different points. This is flexible, but it also means you need to be careful about what type a variable currently holds.

## Quick Reference Table

| Data Type | Example | Used For |
|-----------|---------|----------|
| int | 21, -5, 1000 | Counting, whole numbers |
| float | 3.14, 99.99 | Prices, measurements, decimals |
| str | "Hello", "Rahul" | Names, sentences, any text |
| bool | True, False | Decisions, conditions, yes/no logic |

## Practice

Create one variable of each data type covered above. Use `type()` to print the type of each one and confirm it matches what you expect.
