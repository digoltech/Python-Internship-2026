# Day 6 - Task 3: Path Management with pathlib

## Example (already solved, for reference only)

Problem: Create a path object representing a file `config.json` inside a folder named `settings`, and check if the parent folder exists.

```python
from pathlib import Path

config_path = Path("settings") / "config.json"
print("Parent folder exists:", config_path.parent.exists())
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

---

## Your Tasks

1. Write a script that checks if a folder named `backup` exists in your current folder. If it does not exist, use `pathlib` to create it.
2. In the same folder where your Python script runs, search and print the file size and suffix (extension) of a file named `notes.txt`. (Create `notes.txt` first if it isn't there).
3. Write a program that takes a relative file path (like `data/raw_data.txt`) and prints its absolute (full) path on your system using `pathlib`'s `.resolve()` or `.absolute()` method.
