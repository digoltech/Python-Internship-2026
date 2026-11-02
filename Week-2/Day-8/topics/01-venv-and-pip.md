# Day 8 - Topic 1: Packages and Virtual Environments (venv and pip)

## Why this topic matters

When building projects, you will want to use third-party libraries (like `requests` for fetching APIs, or `Flask` for building web pages). 

However, installing these libraries globally on your computer can cause conflicts. For example, Project A might need version 1.0 of a library, while Project B needs version 2.0. If you upgrade the library globally, Project A will break!

To solve this, Python developers use **Virtual Environments** (`venv`) to create isolated sandboxes for each project, and **Pip** (`pip`) to download and install packages inside those environments.

---

## 1. What is a Virtual Environment?

A virtual environment is a self-contained directory that contains its own copy of Python and its own set of installed libraries. Anything you install or delete inside this environment does not affect the rest of your computer.

---

## 2. Creating and Activating a Virtual Environment

Open your terminal, navigate to your project directory, and run the following commands:

### Step 1: Create the Environment
```bash
python -m venv myenv
```
*(This creates a folder named `myenv` in your project containing Python files).*

### Step 2: Activate the Environment
You must activate it so your terminal knows to use this isolated environment.

- **On Windows (PowerShell):**
  ```powershell
  myenv\Scripts\Activate.ps1
  ```
- **On Windows (Command Prompt):**
  ```cmd
  myenv\Scripts\activate.bat
  ```
- **On macOS/Linux:**
  ```bash
  source myenv/bin/activate
  ```

Once activated, you will see `(myenv)` written at the beginning of your terminal prompt!

### Step 3: Deactivating (To exit)
When you are done working, you can exit the environment by typing:
```bash
deactivate
```

---

## 3. Package Management with Pip

`pip` is Python's package installer. Once your virtual environment is active, you can use `pip` to install packages from PyPI (Python Package Index).

### Installing a package:
```bash
pip install requests
```

### Checking installed packages:
```bash
pip list
```

---

## 4. Sharing Your Project (`requirements.txt`)

When sharing your code on GitHub, you should **never** upload the virtual environment folder (it is too large and specific to your operating system). Instead, you share a list of the packages your project needs.

### Step 1: Export the package list
```bash
pip freeze > requirements.txt
```
This creates a simple text file named `requirements.txt` listing all installed libraries and their versions.

### Step 2: Install from a shared list
When another developer downloads your project, they can install all necessary packages in one command:
```bash
pip install -r requirements.txt
```
