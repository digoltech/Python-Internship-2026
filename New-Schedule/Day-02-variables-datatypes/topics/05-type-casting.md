# Type Casting

## What is Type Casting

Type casting is the process of converting a value from one data type to another. Sometimes data comes in the wrong type for what you need to do with it, and you must convert it first.

## Real-Life Analogy

Imagine you receive money from a friend in a different currency. Before you can use it at a local store, you need to convert it to your local currency. Type casting works the same way — you convert data from one type to another so it can be used correctly.

## Why Type Casting is Needed

A very common real-world case: any input a user types into a program is received as a string, even if it looks like a number. If you try to do math with it directly, Python will give an error.

```python
age = "21"
print(age + 5)
```

This produces an error because you cannot add a string and an integer directly. The string `"21"` must first be converted to an integer.

## Converting String to Integer

Use `int()` to convert a string into a whole number.

```python
age = "21"
age_number = int(age)
print(age_number + 5)
```

Output:

```
26
```

## Converting String to Float

Use `float()` to convert a string into a decimal number.

```python
price = "99.99"
price_number = float(price)
print(price_number + 10)
```

Output:

```
109.99
```

## Converting Number to String

Use `str()` to convert a number into a string. This is useful when you want to combine numbers with text using concatenation.

```python
age = 21
message = "My age is " + str(age)
print(message)
```

Output:

```
My age is 21
```

Without `str(age)`, this code would produce an error, because you cannot concatenate a string and an integer directly using `+`.

## Converting Integer to Float and Float to Integer

```python
whole_number = 10
decimal_version = float(whole_number)
print(decimal_version)

decimal_number = 9.8
whole_version = int(decimal_number)
print(whole_version)
```

Output:

```
10.0
9
```

Notice that converting a float to an integer does not round the number — it simply removes everything after the decimal point. 9.8 becomes 9, not 10.

## Type Casting Errors

Not every string can be converted to a number. If the string does not represent a valid number, Python will raise an error.

```python
value = "hello"
number = int(value)
```

This produces an error because "hello" is not a number and cannot be converted.

## Quick Reference Table

| Function | Converts To | Example |
|----------|-------------|---------|
| int() | Integer | int("21") returns 21 |
| float() | Float | float("9.5") returns 9.5 |
| str() | String | str(21) returns "21" |

## Real-Life Connection

Every form on the internet that asks for your age, phone number, or pin code receives that data as text first. The application must convert it into a number before doing any calculation or validation. Type casting is something every real application depends on.

## Practice

Write a Python program that:

1. Stores the value `"45"` in a variable as a string
2. Converts it to an integer
3. Adds 5 to it
4. Prints a final sentence such as: "The updated value is 50" by combining text and the converted number using `str()`
