# What are Variables

## Definition

A variable is a name given to a location in memory that stores a value. Instead of remembering where data is stored in the computer's memory, you give it a name and refer to that name in your code.

## Real-Life Analogy

Think of a variable as a labeled box. If you have a box labeled "age" and you put the number 21 inside it, you do not need to know which shelf the box is sitting on. You just say "open the box labeled age" and you get 21.

```python
age = 21
```

Here, `age` is the label on the box, and `21` is what is stored inside it.

## Creating a Variable

In Python, you create a variable by choosing a name and assigning it a value using the `=` sign.

```python
name = "Rahul"
age = 21
city = "Mumbai"
```

The `=` sign here does not mean "equal to" like in mathematics. It means "assign the value on the right to the name on the left."

## Using a Variable

Once a variable is created, you can use its name anywhere in your code instead of typing the value again.

```python
name = "Rahul"
print(name)
print("My name is", name)
```

Output:

```
Rahul
My name is Rahul
```

## Variables Can Change

A variable is called a variable because its value can change during the program.

```python
score = 50
print(score)

score = 80
print(score)
```

Output:

```
50
80
```

The second assignment overwrites the first one. Python does not keep a history — only the most recent value remains.

## Rules for Naming Variables

- A variable name can contain letters, numbers, and underscores
- A variable name cannot start with a number
- A variable name cannot contain spaces
- A variable name cannot be a Python keyword such as `if`, `for`, `True`
- Variable names are case sensitive, so `age` and `Age` are different variables

Valid names:

```python
student_name = "Aman"
score1 = 90
_temp = 10
```

Invalid names:

```python
1score = 90
student name = "Aman"
for = 5
```

## Naming Convention

Python developers follow a style called snake_case for variable names — all lowercase, words separated by underscores.

```python
first_name = "Priya"
total_marks = 450
is_passed = True
```

This is not a strict rule enforced by Python, but it is the standard convention followed across the industry. Following it makes your code readable to other developers.

## Multiple Assignment

Python allows you to assign values to multiple variables in a single line.

```python
x, y, z = 10, 20, 30
print(x, y, z)
```

Output:

```
10 20 30
```

## Practice

Create variables to store the following information about a student, then print them in a single readable sentence using one `print` statement:

- Name
- Roll number
- Favorite subject
