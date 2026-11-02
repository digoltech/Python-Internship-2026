# Day 5 - Task 3: Encapsulation and Magic Methods

## Example (already solved, for reference only)

Problem: Create a class `Fraction` that stores a numerator and denominator,
and implement `__str__` so printing it shows it in the form `numerator/denominator`.

```python
class Fraction:
    def __init__(self, numerator, denominator):
        self.numerator = numerator
        self.denominator = denominator

    def __str__(self):
        return f"{self.numerator}/{self.denominator}"

half = Fraction(1, 2)
print(half)
```

Use the same style of thinking for the tasks below. Do not look at the
example code while solving them, write your own logic.

## Your Tasks

1. Create a class `Wallet` with a private balance attribute. Add deposit
   and withdraw methods that validate the amount is positive, and a
   property that returns the current balance without allowing it to be set
   directly from outside the class.

2. Create a class `Fraction` with `numerator` and `denominator`. Implement
   `__add__` so two fractions can be added together using the `+` operator,
   following the rule `a/b + c/d = (a*d + c*b) / (b*d)`.

3. Create a class `Inventory` that stores a list of items internally.
   Implement `__len__` so that calling `len()` on an inventory object
   returns the number of items, and implement `__getitem__` so that
   indexing the object returns the item at that position.

4. Create a class `Point` with `x` and `y`. Implement `__eq__` so two points
   are equal only if both coordinates match, and implement `__str__` so
   printing a point shows it in the form `(x, y)`.

5. Create a class `Stack` that stores items internally using a private
   list. Implement `push`, `pop`, and `__str__` so that printing the stack
   shows all current items in a readable format.

6. Create a class `Money` with an amount and a currency. Implement `__lt__`
   and `__gt__` so two `Money` objects with the same currency can be
   compared directly using `<` and `>`. If the currencies are different,
   raise a `ValueError` instead of comparing the amounts.

7. Build a context manager class called `Timer` using `__enter__` and
   `__exit__` that prints how much time passed between entering and
   exiting the `with` block. Test it by running a loop of 1 million
   iterations inside the `with` block.
