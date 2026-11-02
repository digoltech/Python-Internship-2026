# Day 6 - Topic 2: Introduction to Pandas (Data Analysis)

## Why this topic matters

While Python's built-in `csv` module is great for reading and writing raw CSV files, real-world data analysis requires a more powerful tool. In the industry, **Pandas** is the gold standard library for handling, analyzing, and cleaning tabular data.

Pandas introduces the **DataFrame**—a highly optimized 2D table structure (similar to an Excel sheet or SQL table) that makes data manipulation incredibly easy, fast, and readable.

---

## 1. Setting up a Dataset
Let's assume we have a CSV file named `student_results.csv` with the following contents:

```csv
Student_Name,Subject,Marks
Aarav,Maths,90
Aarav,Science,85
Ananya,Maths,95
Ananya,Science,92
Vihaan,Maths,78
Vihaan,Science,80
Diya,Maths,88
Diya,Science,96
```

---

## 2. Reading CSV and Inspecting Data
To use Pandas, we first import it (traditionally as `pd`). We can load our CSV file using `pd.read_csv()`.

```python
import pandas as pd

# Load the CSV file into a DataFrame
df = pd.read_csv("student_results.csv")

# 1. View the first few rows (default is 5)
print("--- Head ---")
print(df.head())

# 2. View the last few rows
print("\n--- Tail ---")
print(df.tail(3))  # You can specify how many rows to show

# 3. Check the dimensions of the data (rows, columns)
print("\n--- Shape ---")
print(df.shape)  # Returns a tuple: (rows, columns)

# 4. View list of columns
print("\n--- Columns ---")
print(df.columns)
```

---

## 3. Basic Data Analysis

With Pandas, we don't need loops to perform calculations. We can perform operations directly on columns.

### Finding the Average Marks
We can select a column using `df['Column_Name']` and call `.mean()` to find the average:

```python
# Calculate the overall average marks
average_marks = df['Marks'].mean()
print(f"Overall Average Marks: {average_marks:.2f}")
```

### Finding the Topper (Highest Marks and Name)
To find the student with the highest marks:
1. `df['Marks'].idxmax()` returns the index of the row with the maximum value in the `Marks` column.
2. We then use `df.loc[...]` to retrieve that entire row.

```python
# Find the row index of the maximum marks
topper_index = df['Marks'].idxmax()

# Get the student record (row) using the index
topper_record = df.loc[topper_index]

print("\n--- Topper Details ---")
print(f"Name: {topper_record['Student_Name']}")
print(f"Marks: {topper_record['Marks']}")
print(f"Subject: {topper_record['Subject']}")
```

---

## 4. Grouping Data (`groupby`)

If we want to calculate statistics per category (e.g., average marks for *each* subject), we use `.groupby()` followed by the aggregation function.

```python
# Group by 'Subject' and calculate the mean of 'Marks' for each group
subject_averages = df.groupby('Subject')['Marks'].mean()

print("\n--- Average Marks per Subject ---")
print(subject_averages)
```

**Output:**
```text
--- Average Marks per Subject ---
Subject
Maths      87.75
Science    88.25
Name: Marks, dtype: float64
```
