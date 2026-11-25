# Installing Python, VS Code, Git, and GitHub

## What You Are Installing and Why

**Python** — The language engine. Without this, your computer cannot run Python code.

**VS Code (Visual Studio Code)** — The code editor. This is where you will write your code. Think of it as Microsoft Word, but for writing programs.

**Python Extension for VS Code** — Adds Python-specific features to VS Code like syntax highlighting, auto-complete, and the ability to run Python files directly.

**Git** — A version control system. It tracks every change you make to your code over time. Think of it as a detailed save history for your project.

**GitHub** — A website that stores your Git projects online. Think of it as Google Drive, but built specifically for code. It lets you back up your work, share it with others, and collaborate.

## Step 1 — Install Python

1. Go to python.org/downloads
2. Download the latest stable version for your operating system
3. Run the installer
4. On Windows, check the box that says "Add Python to PATH" before clicking Install — this step is critical
5. Once installed, open your terminal or command prompt and type:

```
python --version
```

You should see the Python version number printed. If you do, the installation worked.

## Step 2 — Install VS Code

1. Go to code.visualstudio.com
2. Download the version for your operating system
3. Run the installer with default settings
4. Open VS Code after installation

## Step 3 — Install the Python Extension in VS Code

1. Open VS Code
2. Click the Extensions icon on the left sidebar (it looks like four squares)
3. Search for "Python"
4. Install the extension published by Microsoft
5. Restart VS Code

## Step 4 — Install Git

1. Go to git-scm.com/downloads
2. Download the version for your operating system
3. Run the installer with default settings
4. Open your terminal and type:

```
git --version
```

You should see the Git version number. If you do, the installation worked.

## Step 5 — Create a GitHub Account

1. Go to github.com
2. Click "Sign Up"
3. Enter your email, create a password, and choose a username
4. Verify your email address
5. Your GitHub account is ready

## Step 6 — Connect Git to GitHub in VS Code

Open the terminal inside VS Code (Terminal menu, then New Terminal) and run these two commands. Replace the name and email with your own:

```
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

This links your local Git activity to your GitHub account.

## Verification Checklist

Before moving on, confirm all of the following:

- Running `python --version` in the terminal shows a version number
- Running `git --version` in the terminal shows a version number
- VS Code opens without errors
- The Python extension is visible in VS Code's Extensions panel
- Your GitHub account is accessible at github.com
