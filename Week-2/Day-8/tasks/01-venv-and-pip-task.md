# Day 8 - Task 1: Packages and Virtual Environments

## Example (already solved, for reference only)

Problem: Create a requirements file containing `requests` version 2.28.1.

In your terminal (with your virtual environment active):
```bash
pip install requests==2.28.1
pip freeze > requirements.txt
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

---

## Your Tasks

1. In your terminal, create a new virtual environment named `test_env`.
2. Activate `test_env` (write down the exact activation command for your operating system).
3. Inside your active environment, check your starting package list using `pip list`.
4. Install a popular library named `colorama` (used for colored console text) using `pip install colorama`.
5. Export your active environment configuration to a file named `my_packages.txt` (instead of requirements.txt) using `pip freeze`.
6. Deactivate your virtual environment and delete the `test_env` folder manually from your system.
