# Working with Strings

## What is a String

A string is a sequence of characters used to represent text. In Python, anything inside single quotes or double quotes is treated as a string.

```python
name = "Rahul"
greeting = 'Hello there'
```

## Single Quotes vs Double Quotes

Both work exactly the same way in Python. The choice is mostly personal preference, but consistency matters.

```python
text1 = "This works"
text2 = 'This also works'
```

One case where the choice matters — if your text contains an apostrophe, use double quotes to avoid conflict.

```python
sentence = "It's a sunny day"
```

## String Concatenation

Joining two or more strings together using the `+` operator is called concatenation.

```python
first_name = "Rahul"
last_name = "Sharma"
full_name = first_name + " " + last_name
print(full_name)
```

Output:

```
Rahul Sharma
```

Notice the `" "` in the middle — without it, the names would join with no space, producing `RahulSharma`.

## String Length

The `len()` function tells you how many characters are in a string, including spaces.

```python
name = "Rahul"
print(len(name))
```

Output:

```
5
```

## Accessing Characters by Position (Indexing)

Every character in a string has a position number, called an index. Indexing starts at 0, not 1.

```python
name = "Python"
print(name[0])
print(name[1])
print(name[5])
```

Output:

```
P
y
n
```

| Character | P | y | t | h | o | n |
|-----------|---|---|---|---|---|---|
| Index | 0 | 1 | 2 | 3 | 4 | 5 |

## Negative Indexing

Python also allows accessing characters from the end using negative numbers. `-1` refers to the last character.

```python
name = "Python"
print(name[-1])
print(name[-2])
```

Output:

```
n
o
```

## Common String Methods

A method is a built-in action you can perform on a value. String methods are called using a dot after the string.

```python
text = "Hello World"

print(text.upper())
print(text.lower())
print(text.replace("World", "Python"))
print(text.strip())
```

Output:

```
HELLO WORLD
hello world
Hello Python
Hello World
```

`upper()` converts all characters to uppercase.

`lower()` converts all characters to lowercase.

`replace(old, new)` replaces one part of the string with another.

`strip()` removes extra spaces from the beginning and end of a string.

## Real-Life Connection

Every time you type your name into a form, search something on Google, or send a text message, that data is being handled as a string somewhere in the program. Strings are the most commonly used data type in real applications.

## Practice

Create a variable with your full name. Then write code that:

1. Prints the total number of characters in your name
2. Prints your name in all uppercase
3. Prints only the first character of your name
4. Prints only the last character of your name
