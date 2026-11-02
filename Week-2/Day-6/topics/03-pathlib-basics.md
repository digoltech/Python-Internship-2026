# Day 6 - Topic 3: Path Management with pathlib

## Why this topic matters

When working with files, you need to tell Python *where* the file is located. 

Different operating systems write file paths differently:
- Windows uses backslashes: `C:\Users\Student\document.txt`
- macOS and Linux use forward slashes: `/Users/Student/document.txt`

If you hardcode paths using slashes, your code will crash when run on another system. Python's modern `pathlib` module solves this problem perfectly by treating paths as objects rather than strings.

---

## 1. Absolute vs. Relative Paths

Before using `pathlib`, you must understand two terms:

1. **Absolute Path:** The complete address of a file starting from the root folder (e.g., drive letters like `C:\` on Windows or `/` on macOS).
   - Example: `C:\Projects\PythonCourse\Week-2\Day-6\data.txt`
2. **Relative Path:** The address of a file relative to the directory where your python script is currently running.
   - Example: `data.txt` (meaning "in the same folder as this script")
   - Example: `../data.txt` (meaning "go one folder up, and find data.txt")

---

## 2. Importing `Path` and Basic Path Creation

```python
from pathlib import Path

# Create a Path object representing the current working directory
current_dir = Path.cwd()
print("Current Working Directory:", current_dir)

# Create a path reference to a file named "info.txt" in the current folder
file_path = Path("info.txt")
print("File Path:", file_path)
```

---

## 3. Joining Paths Safely (The `/` Operator)

With `pathlib`, you can join paths using the forward slash `/` operator, no matter what operating system you are on. Python will automatically convert it to the correct system slash under the hood.

```python
from pathlib import Path

# Create a path representing a subfolder and a file inside it
folder_path = Path("my_data")
file_path = folder_path / "records.txt"

print(file_path)
# On Windows, this prints: my_data\records.txt
# On macOS/Linux, this prints: my_data/records.txt
```

---

## 4. Useful Path Properties and Methods

```python
from pathlib import Path

path = Path("my_data/records.txt")

# Check if a file or folder actually exists
print("Exists?:", path.exists())

# Check if it is a file or a folder
print("Is File?:", path.is_file())
print("Is Directory?:", path.is_dir())

# Extract name, extension, and parent folder
print("File Name:", path.name)       # Output: records.txt
print("Extension:", path.suffix)     # Output: .txt
print("Parent Folder:", path.parent)  # Output: my_data
```

---

## 5. Creating and Deleting Directories

You can create directories directly from Python:

```python
from pathlib import Path

# Create a folder named 'logs' if it doesn't already exist
logs_folder = Path("logs")
logs_folder.mkdir(exist_ok=True) 

# exist_ok=True prevents Python from throwing an error if the folder is already there.
```
