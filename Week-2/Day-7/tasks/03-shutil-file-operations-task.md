# Day 7 - Task 3: High-Level File Operations (shutil)

## Example (already solved, for reference only)

Problem: Copy a file named `notes.txt` to a folder named `backup_folder`.

```python
import shutil
import os

if not os.path.exists("backup_folder"):
    os.mkdir("backup_folder")

shutil.copy("notes.txt", "backup_folder/notes.txt")
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

---

## Your Tasks

1. Write a script that creates a backup of a file named `important.txt` by copying it as `important_backup.txt`. Ensure the backup includes file creation/modification metadata (use the appropriate copy function).
2. Create a folder named `organized_dir`. Inside it, manually create 3 text files (`a.txt`, `b.txt`, `c.txt`) and 2 image files (`pic1.png`, `pic2.png`). Write a Python script using `shutil` and `os` (or `pathlib`) that:
   - Creates a subfolder `organized_dir/TextFiles` and moves all `.txt` files there.
   - Creates a subfolder `organized_dir/ImageFiles` and moves all `.png` files there.
3. Write a program that compresses the entire `organized_dir` folder into a single zip file named `organized_backup.zip`.
4. Once the zip backup is verified, delete the `organized_dir` directory and all its subfolders programmatically using Python.
