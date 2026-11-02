# Day 5 - Topic 1: OOP Basics to Advanced

## Why this topic matters

Object Oriented Programming organizes code around objects that hold both
data and behaviour together. Almost every large Python project, from web
frameworks to game engines, is built using classes. This topic builds the
foundation needed for inheritance, polymorphism, and magic methods covered
later today.

## 1. Creating a class and an object

```python
class Student:
    def __init__(self, name, age, course):
        self.name = name
        self.age = age
        self.course = course

    def introduce(self):
        print(f"Hi, I am {self.name}, {self.age} years old, learning {self.course}")

student1 = Student("Riya", 21, "Python")
student2 = Student("Aman", 19, "Java")

student1.introduce()
student2.introduce()
```

`__init__` is the constructor, it runs automatically when a new object is
created and sets up the object's starting data. `self` refers to the
specific object the method is being called on.

## 2. Instance attributes vs class attributes

```python
class Student:
    school_name = "Greenfield Academy"

    def __init__(self, name):
        self.name = name

student1 = Student("Riya")
student2 = Student("Aman")

print(student1.school_name, student2.school_name)

student1.school_name = "Sunrise Academy"
print(student1.school_name, student2.school_name)
print(Student.school_name)
```

`school_name` is a class attribute, shared by every object unless an
individual object overrides it. After `student1.school_name = ...`, only
`student1` gets its own personal copy, `student2` and the class itself stay
unchanged.

## 3. Instance methods, class methods, and static methods

```python
class Counter:
    total_objects = 0

    def __init__(self):
        Counter.total_objects += 1

    @classmethod
    def get_total(cls):
        return cls.total_objects

    @staticmethod
    def explain():
        print("This class tracks how many objects have been created")

c1 = Counter()
c2 = Counter()
c3 = Counter()

print(Counter.get_total())
Counter.explain()
```

An instance method works on a specific object using `self`. A class method
works on the class itself using `cls`, often used to track or build data
shared across all objects. A static method does not need `self` or `cls` at
all, it is just a regular function placed inside the class for
organization.

## 4. Getters, setters, and the property decorator

```python
class BankAccount:
    def __init__(self, balance):
        self._balance = balance

    @property
    def balance(self):
        return self._balance

    @balance.setter
    def balance(self, new_value):
        if new_value < 0:
            raise ValueError("Balance cannot be negative")
        self._balance = new_value

account = BankAccount(1000)
print(account.balance)

account.balance = 1500
print(account.balance)

try:
    account.balance = -50
except ValueError as error:
    print(error)
```

`@property` lets you call a method like `account.balance` instead of
`account.balance()`, while still running validation logic behind the scenes
through the matching `@balance.setter`.

## 5. Non-public attributes and naming conventions

```python
class Employee:
    def __init__(self, name, salary):
        self.name = name
        self._salary = salary
        self.__pan_number = "ABCDE1234F"

    def show_salary(self):
        print(f"{self.name} earns {self._salary}")

employee = Employee("Sara", 50000)
employee.show_salary()
print(employee._salary)

try:
    print(employee.__pan_number)
except AttributeError as error:
    print("Cannot access directly:", error)

print(employee._Employee__pan_number)
```

A single underscore like `_salary` is a convention meaning "internal use,
please do not touch directly", but Python does not block access. A double
underscore like `__pan_number` triggers name mangling, making it much harder
to access from outside the class by accident.

## 6. Comparing objects with __eq__

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __eq__(self, other):
        return self.x == other.x and self.y == other.y

p1 = Point(2, 3)
p2 = Point(2, 3)

print(p1 == p2)
print(p1 is p2)
```

Without `__eq__`, Python would compare objects only by their memory
location, meaning `p1 == p2` would be `False` even with identical data. The
`is` operator always checks identity, never equality of values.

## 7. A complete small example

```python
class Product:
    tax_rate = 0.18

    def __init__(self, name, price, quantity):
        self.name = name
        self.price = price
        self.quantity = quantity

    @property
    def total_price(self):
        base_total = self.price * self.quantity
        return base_total + (base_total * Product.tax_rate)

    def __str__(self):
        return f"{self.name} x{self.quantity} = {self.total_price:.2f}"

cart = [
    Product("Notebook", 40, 3),
    Product("Pen", 10, 5),
    Product("Bag", 500, 1),
]

for item in cart:
    print(item)

grand_total = sum(item.total_price for item in cart)
print("Grand Total:", round(grand_total, 2))
```

This shows attributes, a property, a class attribute, and a generator
expression all working together inside one realistic example.

## Summary

- `__init__` sets up a new object, `self` always refers to the current
  object.
- Class attributes are shared across all objects unless an object overrides
  them individually.
- `@classmethod` and `@staticmethod` are used when a method does not need
  to operate on a specific object's `self` data.
- `@property` allows controlled, validated access to an attribute while
  keeping clean syntax.
- A single underscore is a convention, a double underscore triggers actual
  name mangling.
