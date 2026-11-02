# Day 7 - Topic 2: System Interaction (os and sys modules)

## Why this topic matters

Python programs do not run in a vacuum; they run inside an Operating System (like Windows or macOS). 

To interact with the environment, read system configurations, or pass commands to your script from the terminal, Python provides two essential modules:
- `os`: For interacting with the Operating System (folder structures, environment variables).
- `sys`: For interacting with the Python runtime engine (command-line arguments, system settings).

---

## 1. The `os` Module (Operating System Operations)

The `os` module allows you to perform basic terminal actions programmatically.

```python
import os

# Get the current logged-in username
username = os.getlogin()
print("Current User:", username)

# List all files and folders in the current directory
contents = os.listdir(".")  # "." refers to the current folder
print("Folder contents:", contents)

# Create a folder (old way, though pathlib is now preferred!)
if not os.path.exists("test_folder"):
    os.mkdir("test_folder")
```

---

## 2. Environment Variables

Environment variables are global settings stored by your operating system. They are often used to store sensitive configuration like API keys, database passwords, or mode settings.

```python
import os

# Get the value of the 'PATH' environment variable
system_path = os.environ.get("PATH")
print("System PATH is configured.")
```

---

## 3. The `sys` Module (System Arguments & Runtime)

The `sys` module allows your Python script to interact with the command line interface (CLI).

### Command Line Arguments (`sys.argv`)
When you run a Python script, you can pass arguments to it directly from the terminal:
```bash
python greet.py Rahul 20
```

Inside `greet.py`, you can capture `Rahul` and `20` using `sys.argv`:

```python
import sys

# sys.argv is a list containing the script name and all arguments
print("Arguments passed:", sys.argv)

# The first item is always the script name itself
script_name = sys.argv[0]

# Check if arguments were passed
if len(sys.argv) > 1:
    user_name = sys.argv[1]
    print(f"Hello, {user_name}!")
else:
    print("No name argument was passed to the script.")
```

### Exiting a Program early (`sys.exit()`)
You can stop execution immediately when an error or condition occurs:

```python
import sys

age = 15
if age < 18:
    print("Error: You must be 18 to run this program.")
    sys.exit()  # Stops execution right here!

print("Welcome to the dashboard!")  # This line will not run if age < 18
```
