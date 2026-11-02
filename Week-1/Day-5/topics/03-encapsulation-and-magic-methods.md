# Day 5 - Topic 3: Encapsulation and Magic Methods

## Why this topic matters

Encapsulation protects an object's internal data from being changed in
unsafe ways from outside the class. Magic methods, also called dunder
methods because of their double underscore naming, let your own classes
work naturally with Python's built-in syntax like `print()`, `+`, `len()`,
and `==`.

## 1. Encapsulation with validation

```python
class Temperature:
    def __init__(self, celsius):
        self.celsius = celsius

    @property
    def celsius(self):
        return self._celsius

    @celsius.setter
    def celsius(self, value):
        if value < -273.15:
            raise ValueError("Temperature cannot go below absolute zero")
        self._celsius = value

    @property
    def fahrenheit(self):
        return (self._celsius * 9 / 5) + 32

temp = Temperature(25)
print(temp.fahrenheit)

try:
    temp.celsius = -500
except ValueError as error:
    print(error)
```

The real data lives in `_celsius`, but it is always accessed and changed
through the controlled `celsius` property, which enforces the rule that
temperature cannot go below absolute zero.

## 2. __str__ and __repr__

```python
class Product:
    def __init__(self, name, price):
        self.name = name
        self.price = price

    def __str__(self):
        return f"{self.name} priced at {self.price}"

    def __repr__(self):
        return f"Product(name={self.name!r}, price={self.price!r})"

product = Product("Laptop", 55000)
print(product)
print(str(product))
print(repr(product))
```

`__str__` controls what `print()` shows, meant for end users. `__repr__` is
meant for developers and debugging, and should ideally show enough detail to
recreate the object.

## 3. __len__ and __getitem__

```python
class Playlist:
    def __init__(self, songs):
        self.songs = songs

    def __len__(self):
        return len(self.songs)

    def __getitem__(self, index):
        return self.songs[index]

playlist = Playlist(["Song A", "Song B", "Song C"])

print(len(playlist))
print(playlist[0])

for song in playlist:
    print(song)
```

Implementing `__getitem__` automatically makes the object usable in a `for`
loop as well, even without writing `__iter__` separately, because Python
falls back to repeated indexing starting from 0.

## 4. Operator overloading with __add__

```python
class Money:
    def __init__(self, amount):
        self.amount = amount

    def __add__(self, other):
        return Money(self.amount + other.amount)

    def __str__(self):
        return f"Rs {self.amount}"

wallet1 = Money(500)
wallet2 = Money(300)

combined = wallet1 + wallet2
print(combined)
```

Defining `__add__` lets two `Money` objects be combined using the normal `+`
operator instead of writing a separate method like `add_money()`.

## 5. Comparison operators

```python
class Product:
    def __init__(self, name, price):
        self.name = name
        self.price = price

    def __eq__(self, other):
        return self.price == other.price

    def __lt__(self, other):
        return self.price < other.price

    def __str__(self):
        return f"{self.name}: {self.price}"

p1 = Product("Pen", 10)
p2 = Product("Notebook", 40)

print(p1 == p2)
print(p1 < p2)
print(sorted([p2, p1], key=lambda p: p.price))
```

Once `__lt__` is implemented, objects of this class can be compared and even
sorted using normal Python syntax.

## 6. Context managers with __enter__ and __exit__

```python
class ManagedFile:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode

    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file

    def __exit__(self, exc_type, exc_value, traceback):
        self.file.close()
        print("File closed automatically")

with ManagedFile("notes.txt", "w") as file:
    file.write("Learning magic methods")
```

`__enter__` runs when the `with` block starts, and `__exit__` runs
automatically when the block ends, even if an error occurred inside it, which
guarantees the file always gets closed properly.

## 7. Putting several magic methods together

```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)

    def __eq__(self, other):
        return self.x == other.x and self.y == other.y

    def __str__(self):
        return f"Vector({self.x}, {self.y})"

v1 = Vector(2, 3)
v2 = Vector(4, 1)

v3 = v1 + v2
print(v3)
print(v1 == Vector(2, 3))
```

This is a classic example used to teach magic methods, because a vector
naturally supports addition and equality in a way that feels intuitive once
`__add__` and `__eq__` are defined.

## Summary

- Encapsulation hides direct access to internal data and routes changes
  through validated properties.
- `__str__` is for readable output, `__repr__` is for debugging detail.
- `__len__` and `__getitem__` let custom objects work with `len()`,
  indexing, and loops.
- `__add__`, `__eq__`, and `__lt__` allow custom objects to use normal
  Python operators.
- `__enter__` and `__exit__` allow a class to support the `with` statement
  for guaranteed cleanup.
