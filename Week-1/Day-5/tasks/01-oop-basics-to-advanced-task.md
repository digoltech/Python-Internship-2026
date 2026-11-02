# Day 5 - Task 1: OOP Basics to Advanced

## Example (already solved, for reference only)

Problem: Create a class `Book` with a title, author, and price. Add a
property that returns the price with 5 percent tax included.

```python
class Book:
    def __init__(self, title, author, price):
        self.title = title
        self.author = author
        self.price = price

    @property
    def price_with_tax(self):
        return self.price * 1.05

book = Book("Atomic Habits", "James Clear", 399)
print(book.price_with_tax)
```

Use the same style of thinking for the tasks below. Do not look at the
example code while solving them, write your own logic.

## Your Tasks

1. Create a class `Car` with attributes `brand`, `model`, and `year`. Add a
   method `display_info()` that prints all three values in a single
   formatted sentence. Create 3 different car objects and call the method
   on each.

2. Create a class `Counter` that uses a class attribute to track how many
   `Counter` objects have been created so far, across the entire program.
   Add a class method that returns this total count. Create 5 objects and
   print the final count.

3. Create a class `Circle` with a `radius` attribute. Add a property called
   `area` and another property called `circumference`, both calculated from
   the radius, instead of storing them as plain attributes.

4. Create a class `Employee` with a private attribute for salary using
   double underscore naming. Add a getter method to read the salary and a
   setter method that only allows the salary to increase, never decrease.
   Test both a valid increase and an invalid attempt to decrease it.

5. Create a class `Temperature` with a property `celsius` that has a setter
   which raises a `ValueError` if the value is below -273.15. Add a second
   read-only property `kelvin` that is calculated from `celsius`.

6. Create a class `Rectangle` with `width` and `height`. Implement `__eq__`
   so that two rectangles are considered equal if they have the same area,
   even if their width and height are different. Test this with two
   rectangles of different shapes but equal area.

7. Build a small `Library` class that stores a list of book titles using a
   private internal list. It should have methods to add a book, remove a
   book by title, and list all books, with the internal list never being
   directly accessible from outside the class.
