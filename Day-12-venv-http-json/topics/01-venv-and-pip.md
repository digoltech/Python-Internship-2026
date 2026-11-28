Python Package & Environment Management Guide for Interns
Welcome to the team! This guide explains how Python environments and dependencies work. By the end of this document, you will understand how to manage project dependencies safely and maintain consistent development environments.
---
1. What is `venv` and Why Is It Needed?
The Problem with Global Python
By default, when you install Python on your machine and run `pip install <package>`, that package is installed system-wide (globally).
This creates major issues:
Dependency Conflicts: If Project A requires `Django 3.2` and Project B requires `Django 4.2`, installing one will break the other.
Permission Issues: Global installs often require administrator/sudo privileges.
Lack of Reproducibility: You cannot easily tell which packages belong to which project.
The Solution: Virtual Environments (`venv`)
A virtual environment (`venv`) is an isolated, self-contained directory containing its own Python executable and package installation directory (`site-packages`).
```
Your Computer
├── Project A Directory
│   └── .venv/ (Python 3.11 + Django 3.2)
└── Project B Directory
    └── .venv/ (Python 3.11 + Django 4.2)
```
With `venv`, each project runs independently without interfering with system files or other projects.
---
2. How to Use `venv`
Step 1: Create a Virtual Environment
Navigate to your project root folder in your terminal and run:
macOS / Linux:
```bash
  python3 -m venv .venv
  ```
Windows:
```powershell
  python -m venv .venv
  ```
> **Tip:** We use `.venv` as the folder name because standard tools (like VS Code, PyCharm, git, and linters) automatically detect hidden folders starting with a dot.
Step 2: Activate the Virtual Environment
Before installing packages or running your project, you must activate the environment.
macOS / Linux (Bash/Zsh):
```bash
  source .venv/bin/activate
  ```
Windows (PowerShell):
```powershell
  .venv\Scripts\Activate.ps1
  ```
Windows (Command Prompt):
```cmd
  .venv\Scripts\activate.bat
  ```
Once activated, your terminal prompt will display `(.venv)` at the beginning:
```bash
(.venv) user@machine:~/my-project$
```
Step 3: Deactivate the Virtual Environment
When you are done working on the project, leave the environment by typing:
```bash
deactivate
```
---
3. Package Management with `pip`
What is `pip`?
`pip` stands for Package Installer for Python. It is the standard package manager for Python that connects to the Python Package Index (PyPI) to download and manage external libraries.
Why Do We Need `pip`?
Python comes with a robust standard library, but real-world development relies on third-party packages for specialized tasks (e.g., `requests` for HTTP APIs, `pandas` for data analysis, `pytest` for testing). `pip` automates downloading, installing, updating, and removing these packages.
Essential `pip` Commands & Examples
1. Installing Packages
```bash
# Install the latest version of a package
pip install requests

# Install a specific version
pip install pandas==2.1.0

# Install multiple packages at once
pip install flask pytest
```
2. Viewing Installed Packages
```bash
# List all packages installed in the active environment
pip list
```
3. Inspecting a Package
```bash
# View metadata, location, and dependencies of a package
pip show requests
```
4. Uninstalling a Package
```bash
pip uninstall requests
```
---
4. `pip freeze` & `requirements.txt`
What is `pip freeze`?
`pip freeze` is a command that inspects your current Python environment and outputs a list of all installed packages along with their exact versions, formatted as `package==version`.
Example output:
```text
certifi==2023.7.22
charset-normalizer==3.2.0
idna==3.4
requests==2.31.0
urllib3==2.0.4
```
What is `requirements.txt`?
`requirements.txt` is a standard text file stored in the root of a Python repository. It acts as a manifest listing all external packages required to run the project.
Because `.venv` folders are large and machine-specific, you should never commit `.venv` to Git. Instead, you commit `requirements.txt` so teammates can recreate the environment on their own machines.
---
5. Workflow Summary: Using `requirements.txt`
For the Developer Creating or Updating Dependencies
Activate your virtual environment:
```bash
   source .venv/bin/activate
   ```
Install necessary packages:
```bash
   pip install requests pandas
   ```
Export your installed packages to `requirements.txt`:
```bash
   pip freeze > requirements.txt
   ```
Commit `requirements.txt` to Git.
For a Teammate Cloning the Repository
Clone the repository and navigate into it:
```bash
   git clone <repo-url>
   cd <project-folder>
   ```
Create and activate a fresh virtual environment:
```bash
   python -m venv .venv
   source .venv/bin/activate
   ```
Install all project dependencies in one command:
```bash
   pip install -r requirements.txt
   ```
---
Quick Reference Checklist
Task	Command
Create environment	`python -m venv .venv`
Activate (macOS/Linux)	`source .venv/bin/activate`
Activate (Windows PS)	`.venv\Scripts\Activate.ps1`
Deactivate	`deactivate`
Install package	`pip install <package>`
Save dependencies	`pip freeze > requirements.txt`
Install dependencies	`pip install -r requirements.txt`
