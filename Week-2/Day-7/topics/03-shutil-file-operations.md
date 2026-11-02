# Day 7 - Topic 3: High-Level File Operations (shutil module)

## Why this topic matters

While standard file methods like `open()` and `Path.write_text()` let you read and edit the **contents** of a file, they cannot copy a file, move a file, or create a zip archive. 

For high-level operations on files and entire directories, Python provides the `shutil` (Shell Utilities) module. This is extremely useful for automating backups, cleaning folders, and organizing files.

---

## 1. Copying Files

`shutil` provides simple functions to copy files:

```python
import shutil

# Copy a file to another location
# If the destination file already exists, it will be overwritten!
shutil.copy("source.txt", "destination.txt")

# shutil.copy() copies the file content and permissions.
# shutil.copy2() copies content along with metadata (creation time, edit time).
```

---

## 2. Moving and Renaming Files

To move a file from one folder to another, or to rename a file, we use `shutil.move()`.

```python
import shutil

# Move a file to another folder
shutil.move("notes.txt", "backup/notes.txt")

# You can also use it to rename a file
shutil.move("old_name.txt", "new_name.txt")
```

---

## 3. Deleting Directories (Folders) Safely

Python's built-in `os.rmdir()` only deletes empty folders. If a folder contains files, it will crash. `shutil.rmtree()` deletes the entire directory tree (the folder and everything inside it).

> [!WARNING]
> `shutil.rmtree()` is permanent! Files deleted using this method do NOT go to the Recycle Bin. Use it with extreme caution.

```python
import shutil

# Deletes the 'temp_data' folder and all files inside it
shutil.rmtree("temp_data")
```

---

## 4. Archiving (Creating Zip Files)

You can compress folders into zip files using a single line of code:

```python
import shutil

# Parameters: (zip_name, format, folder_to_compress)
shutil.make_archive("my_backup", "zip", "project_folder")

# This creates a file named "my_backup.zip" containing everything from "project_folder".
```
