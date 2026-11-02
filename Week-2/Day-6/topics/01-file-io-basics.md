# Day 6 - Topic 1: File I/O Basics (Reading & Writing Files)

## Why this topic matters

In Week 1, you learned how to store data in variables, lists, and dictionaries. However, as soon as your Python program stops running, all that data is lost from the computer's temporary memory (RAM). 

To save data permanently, we must write it to files on the hard disk. Reading from and writing to files is a fundamental skill for any developer—whether you are saving user logs, reading configurations, or processing data.

---

## 1. Opening and Closing Files (The Old Way vs. The Modern Way)

To work with a file in Python, we use the built-in `open()` function. It requires the file name and the **mode** (read, write, append).

### The Old Way (Not Recommended)
```python
# Open the file
file = open("sample.txt", "r")
content = file.read()
print(content)
# You MUST close it manually
file.close()
```
*Why this is bad:* If an error occurs between `open()` and `close()`, the file stays open in memory, which can lock the file and cause memory leaks.

### The Modern Way (Context Managers - `with` statement)
The `with` keyword acts as a safety guard. It automatically closes the file for you, even if the code inside throws an error.

```python
with open("sample.txt", "r") as file:
    content = file.read()
    print(content)
# File is automatically closed here!
```

---

## 2. File Modes in Python

When opening a file, you must specify what you want to do with it:

| Mode | Name | Description | What happens if file doesn't exist? |
| :--- | :--- | :--- | :--- |
| `"r"` | **Read** | Reads the file content. (Default mode) | Raises a `FileNotFoundError` |
| `"w"` | **Write** | Overwrites/creates file. **Deletes existing content!** | Creates a new file |
| `"a"` | **Append** | Adds new content to the end of the file. | Creates a new file |

---

## 3. Writing and Appending to a File

### Writing (`"w"`)
```python
with open("notes.txt", "w") as file:
    file.write("Hello Students!\n")
    file.write("Welcome to Week 2 of Python Training.\n")
```
*Note:* The `\n` is the newline character. Unlike the `print()` function, `file.write()` does not automatically start a new line.

### Appending (`"a"`)
If we run the `"w"` code again with different text, the old text is completely erased. To keep the old text and add new text, use `"a"`.

```python
with open("notes.txt", "a") as file:
    file.write("This line is appended to the bottom!\n")
```

---

## 4. Reading Files in Different Ways

Let's assume we have a file `names.txt` with the following content:
```text
Aman
Riya
Vikram
```

### Method A: `read()` (Reads the entire file as a single string)
```python
with open("names.txt", "r") as file:
    content = file.read()
    print(content)
```

### Method B: `readlines()` (Reads the file into a list of strings)
```python
with open("names.txt", "r") as file:
    lines = file.readlines()
    print(lines)  # Output: ['Aman\n', 'Riya\n', 'Vikram\n']
```
*Note:* Each line will end with `\n`. You can remove it using `.strip()`.

### Method C: Line-by-Line Iteration (Memory Efficient)
For very large files, reading the whole file at once can freeze your computer. Instead, loop through the file object directly:

```python
with open("names.txt", "r") as file:
    for line in file:
        print(line.strip())  # strip() removes the extra newlines
```
