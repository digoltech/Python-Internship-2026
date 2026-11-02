# Day 6 - Task 1: File I/O Basics

## Example (already solved, for reference only)

Problem: Create a text file named `test.txt` and write "Hello World" to it, then read the file and print its content.

```python
# Writing
with open("test.txt", "w") as file:
    file.write("Hello World")

# Reading
with open("test.txt", "r") as file:
    content = file.read()
    print(content)
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

---

## Your Tasks

1. Write a Python script that creates a file named `my_story.txt` and writes three lines about what you want to achieve with Python.
2. Read the contents of `my_story.txt` line by line using a loop and print each line with its length (character count) next to it.
3. Write a Python script that appends a fourth line containing the date "2026-07-22" to `my_story.txt`. Run the script and verify that the original content is not overwritten.
4. Create a program that reads a text file named `input.txt` and copies its contents into a new file named `copy.txt`. (Create a dummy `input.txt` file first manually to test this).
5. Write a program that counts the total number of words in a text file of your choice.
