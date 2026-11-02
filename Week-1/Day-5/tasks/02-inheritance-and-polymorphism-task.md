# Day 5 - Task 2: Inheritance and Polymorphism

## Example (already solved, for reference only)

Problem: Create a base class `Shape` with a method `area` that returns 0 by
default, then create a `Square` subclass that overrides it correctly.

```python
class Shape:
    def area(self):
        return 0

class Square(Shape):
    def __init__(self, side):
        self.side = side

    def area(self):
        return self.side ** 2

square = Square(5)
print(square.area())
```

Use the same style of thinking for the tasks below. Do not look at the
example code while solving them, write your own logic.

## Your Tasks

1. Create a base class `Person` with `name` and `age`. Create a subclass
   `Student` that adds a `course` attribute using `super().__init__()` to
   set up the inherited attributes, and adds its own method `study()`.

2. Create a base class `Employee` with a method `calculate_salary()` that
   returns a fixed base salary. Create two subclasses, `Developer` and
   `Designer`, each overriding `calculate_salary()` with their own bonus
   logic added on top of the base salary using `super()`.

3. Create a base class `Account` with a method `get_interest_rate()` that
   returns 4. Create two subclasses, `SavingsAccount` and `FixedDeposit`,
   each overriding the method with a different rate. Put all three account
   types in a list and loop through them calling `get_interest_rate()` on
   each, without checking the type manually.

4. Create three unrelated classes, `Bird`, `Airplane`, and `Drone`, each
   with their own version of a method called `fly()`. Write a function that
   accepts any object and calls `.fly()` on it, then test it with all
   three, to demonstrate duck typing.

5. Build a 3 level inheritance chain: `Vehicle` to `Car` to `SportsCar`,
   where each level adds one new attribute, and `SportsCar` has a method
   that prints information using data from all three levels.

6. Create a base class `Notification` with a method `send()` that prints a
   generic message. Create subclasses `EmailNotification` and
   `SMSNotification`, each overriding `send()` with their own specific
   message. Store several notification objects in a list and send all of
   them in a single loop.
