# Working with Numbers

## Two Types of Numbers

Python has two primary numeric types you will use constantly: `int` for whole numbers and `float` for decimal numbers.

```python
whole_number = 10
decimal_number = 10.5
```

## Basic Arithmetic

Python supports all standard mathematical operations.

```python
a = 10
b = 3

print(a + b)
print(a - b)
print(a * b)
print(a / b)
```

Output:

```
13
7
30
3.3333333333333335
```

## Division Produces a Float

Notice that even though `a` and `b` are both integers, dividing them with `/` produces a float. This is the standard division operator and it always returns a decimal result in Python.

## Floor Division

If you want only the whole number part of a division, without the decimal, use `//`.

```python
print(10 // 3)
```

Output:

```
3
```

This is called floor division — it divides and then rounds down to the nearest whole number.

## Modulus (Remainder)

The `%` operator gives you the remainder after division. This is extremely useful for tasks like checking if a number is even or odd.

```python
print(10 % 3)
```

Output:

```
1
```

10 divided by 3 is 3 with a remainder of 1.

## Real-Life Example for Modulus

Checking even or odd is one of the most common uses of modulus. Any number divided by 2 with a remainder of 0 is even.

```python
number = 7
print(number % 2)
```

Output:

```
1
```

Since the remainder is 1, not 0, the number is odd.

## Exponents (Power)

The `**` operator raises a number to a power.

```python
print(2 ** 3)
print(5 ** 2)
```

Output:

```
8
25
```

2 to the power of 3 is 8. 5 to the power of 2 is 25.

## Order of Operations

Python follows the standard mathematical order of operations — multiplication and division happen before addition and subtraction, unless parentheses say otherwise.

```python
result = 10 + 5 * 2
print(result)

result_with_brackets = (10 + 5) * 2
print(result_with_brackets)
```

Output:

```
20
30
```

In the first case, `5 * 2` is calculated first, giving 10, then `10 + 10` gives 20.

In the second case, the parentheses force `10 + 5` to be calculated first, giving 15, then `15 * 2` gives 30.

## Real-Life Connection

A shopping cart calculating total price with tax, a calorie tracker summing your meals, or a banking app calculating interest — all of these rely on the exact same arithmetic operations you just learned.

## Practice

A movie ticket costs 250 rupees. Write a Python program that calculates and prints the total cost for 4 tickets, including an 18 percent tax. Use variables for the ticket price, number of tickets, and tax percentage — do not hardcode the final number.
