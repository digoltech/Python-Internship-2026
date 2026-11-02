# Day 7 - Topic 1: Essential Built-in Modules (math, random, datetime)

## Why this topic matters

You don't need to write every piece of logic from scratch. Python comes with "batteries included," meaning it has a rich set of built-in libraries (the Standard Library) that solve common problems—from complex math, generating random values, to handling dates and times. 

Knowing how to import and use these modules saves you time and ensures your code is highly optimized.

---

## 1. The `math` Module (For Mathematical Operations)

The standard mathematical operators (`+`, `-`, `*`, `/`) cover basic math, but for advanced functions like square roots, trigonometric ratios, or rounding, we use the `math` module.

```python
import math

# Rounding numbers
print(math.floor(4.7))  # Output: 4 (rounds down)
print(math.ceil(4.1))   # Output: 5 (rounds up)

# Square root and power
print(math.sqrt(25))    # Output: 5.0
print(math.pow(2, 3))   # Output: 8.0 (2 raised to power 3)

# Mathematical Constants
print(math.pi)          # Output: 3.141592653589793
```

---

## 2. The `random` Module (For Randomness)

Whether you are building a game (like rock-paper-scissors or rolling dice) or shuffling a list, the `random` module is your best friend.

```python
import random

# Generate a random float between 0.0 and 1.0
print(random.random())

# Generate a random integer between a range (inclusive)
# Example: Rolling a 6-sided die
die_roll = random.randint(1, 6)
print("You rolled:", die_roll)

# Pick a random item from a list
fruits = ["Apple", "Banana", "Cherry", "Orange"]
picked_fruit = random.choice(fruits)
print("Picked fruit:", picked_fruit)

# Shuffle a list in-place
numbers = [1, 2, 3, 4, 5]
random.shuffle(numbers)
print("Shuffled list:", numbers)
```

---

## 3. The `datetime` Module (For Date & Time)

Handling time can be complicated because of timezones, leap years, and calendar differences. The `datetime` module makes working with dates, time, and formatting easy.

```python
from datetime import datetime, date

# Get the current date and time
now = datetime.now()
print("Now:", now)

# Get just today's date
today = date.today()
print("Today's Date:", today)

# Creating a specific date (Year, Month, Day)
birthday = date(2005, 10, 15)
print("Birthday:", birthday)

# Formatting Date as a readable String (strftime - String Format Time)
# %d = day, %B = month name, %Y = 4-digit year
formatted_date = now.strftime("%d-%B-%Y")
print("Readable Date:", formatted_date)  # Example: 22-July-2026
```
💡 **Memory Trick:** `strftime` stands for **str**ing **f**rom **time** (converts date object into a string).
