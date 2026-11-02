# Understanding Python Syntax

## What is Syntax

Syntax is the set of rules that define how Python code must be written. Just as every language has grammar rules, Python has syntax rules. If you break them, Python cannot understand your instructions and will throw an error.

## Rule 1 — Indentation

In most programming languages, indentation is optional and only used for readability. In Python, indentation is mandatory. It defines the structure of your code.

Correct:

```python
if True:
    print("This line is inside the if block")
```

Incorrect:

```python
if True:
print("This will cause an IndentationError")
```

The standard is to use 4 spaces for each level of indentation. VS Code handles this automatically when you press the Tab key.

## Rule 2 — Case Sensitivity

Python treats uppercase and lowercase letters as completely different. `print` is not the same as `Print` or `PRINT`.

```python
print("This works")
Print("This causes a NameError")
```

This rule applies to everything — function names, variable names, and keywords.

## Rule 3 — Strings Must Be Closed

Every string that you open with a quotation mark must be closed with the same quotation mark.

```python
print("Hello")
print('Hello')
```

Both single quotes and double quotes work. But you must be consistent — open and close with the same type.

```python
print("Hello')
```

This will cause a SyntaxError because the opening and closing quotes do not match.

## Rule 4 — No Statement Terminator Required

Many languages like Java or JavaScript require a semicolon at the end of every statement. Python does not. Each new line is treated as a new statement.

```python
print("Line one")
print("Line two")
```

## Rule 5 — Keywords are Reserved

Python has reserved words called keywords that have specific meaning in the language. You cannot use these as variable names or function names.

Examples: `if`, `else`, `for`, `while`, `True`, `False`, `None`, `and`, `or`, `not`, `import`, `return`

## Reading Error Messages

When Python finds a syntax issue, it displays an error message. These messages tell you exactly what went wrong and on which line. Learning to read them is essential.

Example error:

```
SyntaxError: EOL while scanning string literal
  File "hello.py", line 1
    print("Hello)
               ^
```

The `^` symbol points to where Python detected the problem. In this case, the string was never closed.

## Practice

Find and fix all the errors in the following code:

```python
Print("Welcome to Python")
print("Today we are learning syntax)
print("Indentation test")
    print("This line has wrong indentation")
```

There are three errors. Identify each one, explain what kind of error it is, and write the corrected version.
