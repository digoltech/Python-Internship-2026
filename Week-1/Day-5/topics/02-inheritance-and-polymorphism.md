# Day 5 - Topic 2: Inheritance and Polymorphism

## Why this topic matters

Inheritance lets a new class reuse and extend the behaviour of an existing
class instead of rewriting everything from scratch. Polymorphism lets
different classes be used through the same interface. Together they are the
core ideas behind building large, organized systems.

## 1. Basic inheritance

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def make_sound(self):
        print(f"{self.name} makes a sound")

class Dog(Animal):
    def make_sound(self):
        print(f"{self.name} barks")

class Cat(Animal):
    def make_sound(self):
        print(f"{self.name} meows")

dog = Dog("Tommy")
cat = Cat("Kitty")

dog.make_sound()
cat.make_sound()
```

`Dog` and `Cat` both inherit from `Animal`, so they automatically get the
`__init__` method, and each one overrides `make_sound` with its own version.

## 2. Using super() to extend a parent method

```python
class Animal:
    def __init__(self, name, sound):
        self.name = name
        self.sound = sound

class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name, sound="Bark")
        self.breed = breed

    def describe(self):
        print(f"{self.name} is a {self.breed} and says {self.sound}")

dog = Dog("Tommy", "Labrador")
dog.describe()
```

`super().__init__()` calls the parent class's constructor so you do not have
to repeat the same setup code again. This is one of the most common uses of
`super()`.

## 3. Method overriding with extension, not replacement

```python
class Employee:
    def __init__(self, name, base_salary):
        self.name = name
        self.base_salary = base_salary

    def calculate_salary(self):
        return self.base_salary

class Manager(Employee):
    def __init__(self, name, base_salary, bonus):
        super().__init__(name, base_salary)
        self.bonus = bonus

    def calculate_salary(self):
        base = super().calculate_salary()
        return base + self.bonus

manager = Manager("Sara", 50000, 10000)
print(manager.calculate_salary())
```

`Manager.calculate_salary` calls the parent version first using
`super().calculate_salary()` and then adds its own extra logic, instead of
completely rewriting the parent's behaviour.

## 4. Multilevel inheritance

```python
class Vehicle:
    def __init__(self, brand):
        self.brand = brand

class Car(Vehicle):
    def __init__(self, brand, model):
        super().__init__(brand)
        self.model = model

class ElectricCar(Car):
    def __init__(self, brand, model, battery_capacity):
        super().__init__(brand, model)
        self.battery_capacity = battery_capacity

    def details(self):
        print(f"{self.brand} {self.model}, battery: {self.battery_capacity} kWh")

tesla = ElectricCar("Tesla", "Model 3", 75)
tesla.details()
```

`ElectricCar` inherits from `Car`, which inherits from `Vehicle`, forming a
chain. Each level adds its own extra data on top of what it inherited.

## 5. Polymorphism through a common interface

```python
class Shape:
    def area(self):
        raise NotImplementedError("Subclasses must implement this method")

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14159 * self.radius ** 2

shapes = [Rectangle(4, 5), Circle(3), Rectangle(2, 2)]

for shape in shapes:
    print(type(shape).__name__, "area:", round(shape.area(), 2))
```

This loop calls `shape.area()` without knowing or caring whether `shape` is
a `Rectangle` or a `Circle`. Each object responds in its own way, which is
the core idea of polymorphism.

## 6. Duck typing

```python
class Duck:
    def make_sound(self):
        print("Quack")

class Robot:
    def make_sound(self):
        print("Beep boop")

def trigger_sound(entity):
    entity.make_sound()

trigger_sound(Duck())
trigger_sound(Robot())
```

Python does not check if `Duck` and `Robot` share a common parent class.
If an object has the method being called, it works. This flexible style is
called duck typing, summarized as "if it walks like a duck and talks like a
duck, treat it like a duck".

## 7. Checking types and inheritance relationships

```python
class Animal:
    pass

class Dog(Animal):
    pass

dog = Dog()

print(isinstance(dog, Dog))
print(isinstance(dog, Animal))
print(issubclass(Dog, Animal))
print(type(dog) == Dog)
```

`isinstance()` checks both the exact class and any parent classes, while
`type(dog) == Dog` only matches the exact class.

## Summary

- Inheritance lets a child class reuse a parent class's attributes and
  methods.
- `super()` calls the parent class's version of a method, often used inside
  `__init__` and inside overridden methods.
- Polymorphism allows different classes to be used through the same method
  name, with each class providing its own specific behaviour.
- Duck typing means Python cares about whether an object has the right
  method, not what class it belongs to.
