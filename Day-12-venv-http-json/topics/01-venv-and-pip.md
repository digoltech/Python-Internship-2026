
---

## 1. Why Do We Need Virtual Environments?

### The Problem with Global Python Packages

When you install a Python package normally:

```bash
pip install <package>
```

it may be installed into your global Python environment.

This can cause problems when working on multiple projects.

For example:

```text
Project A → Django 3.2
Project B → Django 4.2
```

If both projects use the same global environment, their dependencies can conflict.

Common problems include:

- ❌ Different projects require different package versions
- ❌ Installing one package can affect another project
- ❌ Global installations may require administrator permissions
- ❌ Difficult to reproduce the same environment on another machine
- ❌ Unclear which packages belong to which project

### The Solution: `venv`

Python provides a built-in tool called **`venv`** for creating isolated virtual environments.

Each project gets its own environment and dependencies:

```text
Your Computer
│
├── Project A
│   └── .venv/
│       ├── Python
│       └── Django 3.2
│
└── Project B
    └── .venv/
        ├── Python
        └── Django 4.2
```

This keeps projects isolated from each other.

> **Rule:** Always create and use a virtual environment for Python projects.

---

# 2. Creating a Virtual Environment

First, navigate to your project folder:

```bash
cd my-project
```

Then create a virtual environment named `.venv`.

### Windows

```powershell
python -m venv .venv
```

### macOS / Linux

```bash
python3 -m venv .venv
```

This creates a `.venv` folder inside your project.

### Recommended Project Structure

```text
my-project/
├── .venv/
├── src/
├── requirements.txt
├── .gitignore
└── README.md
```

> **Important:** `.venv` should **not** be committed to Git.

---

# 3. Activating the Virtual Environment

You must activate the virtual environment before installing packages or running the project.

### Windows PowerShell

```powershell
.venv\Scripts\Activate.ps1
```

### Windows Command Prompt

```cmd
.venv\Scripts\activate.bat
```

### macOS / Linux

```bash
source .venv/bin/activate
```

After activation, your terminal should show something similar to:

```text
(.venv) C:\Users\user\my-project>
```

The `(.venv)` indicates that the virtual environment is currently active.

---

# 4. Deactivating the Environment

When you are finished working:

```bash
deactivate
```

This returns you to your normal system Python environment.

---

# 5. Understanding `pip`

`pip` is Python's package manager.

It is used to install and manage third-party Python packages from the Python Package Index (PyPI).

For example:

```bash
pip install requests
```

This installs the `requests` package into your **active virtual environment**.

### Common packages

```text
requests  → HTTP/API requests
pandas    → Data analysis
flask     → Web applications
pytest    → Testing
```

---

# 6. Essential `pip` Commands

## Install a Package

Install the latest available version:

```bash
pip install requests
```

Install a specific version:

```bash
pip install pandas==2.1.0
```

Install multiple packages:

```bash
pip install flask pytest requests
```

---

## Check Installed Packages

```bash
pip list
```

Example:

```text
Package    Version
---------- -------
Flask      3.0.0
pip        24.0
requests   2.31.0
```

---

## Check Package Information

```bash
pip show requests
```

This can show information such as:

- Installed version
- Installation location
- Dependencies
- Package metadata

---

## Uninstall a Package

```bash
pip uninstall requests
```

---

## Upgrade a Package

```bash
pip install --upgrade requests
```

---

# 7. `requirements.txt`

A Python project usually contains a file named:

```text
requirements.txt
```

This file lists the packages required to run the project.

For example:

```text
Flask==3.0.0
requests==2.31.0
pandas==2.1.0
pytest==8.0.0
```

Think of `requirements.txt` as the project's **dependency list**.

Instead of telling every developer:

> "Install these 10 packages manually."

we can simply provide:

```bash
pip install -r requirements.txt
```

---

# 8. What is `pip freeze`?

`pip freeze` displays the packages installed in your current virtual environment along with their versions.

Run:

```bash
pip freeze
```

Example:

```text
certifi==2023.7.22
charset-normalizer==3.2.0
idna==3.4
requests==2.31.0
urllib3==2.0.4
```

You can save this list directly into `requirements.txt`:

```bash
pip freeze > requirements.txt
```

---

# 9. Adding a New Dependency

Suppose your project needs the `requests` package.

### Step 1 — Activate the environment

```bash
.venv\Scripts\Activate.ps1
```

### Step 2 — Install the package

```bash
pip install requests
```

### Step 3 — Update `requirements.txt`

```bash
pip freeze > requirements.txt
```

### Step 4 — Commit the updated file

```bash
git add requirements.txt
git commit -m "Add requests dependency"
```

> **Important:** Whenever you add or remove a project dependency, make sure `requirements.txt` is updated.

---

# 10. Setting Up an Existing Project

When you clone an existing Python project, you normally need to create a fresh environment.

### Step 1 — Clone the repository

```bash
git clone <repo-url>
```

### Step 2 — Enter the project

```bash
cd <project-folder>
```

### Step 3 — Create a virtual environment

```bash
python -m venv .venv
```

### Step 4 — Activate it

**Windows:**

```powershell
.venv\Scripts\Activate.ps1
```

**macOS/Linux:**

```bash
source .venv/bin/activate
```

### Step 5 — Install project dependencies

```bash
pip install -r requirements.txt
```

### Step 6 — Run the project

Follow the project's `README.md` for the appropriate command.

---

# 11. `.gitignore`

Never commit your virtual environment to Git.

Add the following to `.gitignore`:

```gitignore
.venv/
__pycache__/
*.pyc
.env
```

Your repository should contain:

```text
my-project/
├── .gitignore
├── requirements.txt
├── README.md
└── src/
```

Not:

```text
my-project/
├── .venv/          ❌
├── requirements.txt
└── src/
```

---

# 12. Recommended Daily Workflow

Whenever you start working on a Python project:

### 1. Open the project

```bash
cd my-project
```

### 2. Activate the environment

```powershell
.venv\Scripts\Activate.ps1
```

### 3. Check that it is active

You should see:

```text
(.venv)
```

### 4. Install dependencies if required

```bash
pip install -r requirements.txt
```

### 5. Work on the project

Write code, run tests, install required packages, etc.

### 6. If you add a new package

```bash
pip install <package>
pip freeze > requirements.txt
```

### 7. Before pushing code

Check that:

```text
requirements.txt
```

is updated and:

```text
.venv/
```

is not being committed.

---

# 13. Quick Reference

| Task | Command |
|---|---|
| Create environment | `python -m venv .venv` |
| Activate — Windows | `.venv\Scripts\Activate.ps1` |
| Activate — macOS/Linux | `source .venv/bin/activate` |
| Deactivate | `deactivate` |
| Install package | `pip install <package>` |
| Install specific version | `pip install package==1.2.3` |
| Upgrade package | `pip install --upgrade <package>` |
| List packages | `pip list` |
| Package information | `pip show <package>` |
| Uninstall package | `pip uninstall <package>` |
| Export dependencies | `pip freeze > requirements.txt` |
| Install project dependencies | `pip install -r requirements.txt` |

---

# 14. Common Mistakes to Avoid

### ❌ Installing packages globally

Avoid:

```bash
pip install requests
```

when your virtual environment is not activated.

Make sure you see:

```text
(.venv)
```

before installing project dependencies.

---

### ❌ Committing `.venv`

Never push:

```text
.venv/
```

to Git.

It is machine-specific and can be recreated using:

```bash
python -m venv .venv
```

---

### ❌ Forgetting to update `requirements.txt`

If you install:

```bash
pip install requests
```

remember to update:

```bash
pip freeze > requirements.txt
```

---

### ❌ Using the wrong Python environment

If you have multiple Python installations, verify which Python is being used.

Windows:

```powershell
where python
```

macOS/Linux:

```bash
which python
```

You can also check the Python version:

```bash
python --version
```

---

# 15. Final Checklist

Before starting development:

- [ ] Python is installed
- [ ] `.venv` is created
- [ ] `.venv` is activated
- [ ] Dependencies are installed
- [ ] `requirements.txt` exists
- [ ] `.venv/` is included in `.gitignore`

Before pushing code:

- [ ] New dependencies are added to `requirements.txt`
- [ ] `.venv/` is not committed
- [ ] Code runs correctly inside the virtual environment
- [ ] Tests pass, if applicable
- [ ] Git changes have been reviewed

---

## The Basic Workflow

```text
Clone Project
     ↓
Create .venv
     ↓
Activate .venv
     ↓
Install requirements.txt
     ↓
Develop & Test
     ↓
Install new packages if needed
     ↓
Update requirements.txt
     ↓
Commit & Push
```

### Remember

> **One project → One virtual environment → One dependency list**

This keeps Python projects clean, reproducible, and safe to work on as a team.
