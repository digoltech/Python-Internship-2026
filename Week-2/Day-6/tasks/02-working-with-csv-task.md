# Day 6 - Task 2: Introduction to Pandas

## Example (already solved, for reference only)

**Problem:** We have a CSV file named `users.csv` with headings `Username` and `Role`. Load it using Pandas and display its shape and columns.

```python
import pandas as pd

# Read CSV file
df = pd.read_csv("users.csv")

# Print details
print("Shape of DataFrame:", df.shape)
print("Columns in CSV:", df.columns)
```

Use the same style of thinking for the tasks below. Do not look at the example code while solving them, write your own logic.

---

## Your Tasks

1. Create a CSV file named `products.csv` manually with the following data:
   ```csv
   ID,Name,Price
   P01,Laptop,50000
   P02,Mouse,800
   P03,Keyboard,1500
   P04,Monitor,12000
   ```
   Write a Python script using **Pandas** to read `products.csv` and display the first 2 rows using `.head()` and its total dimensions using `.shape`.

2. Write a Python script using **Pandas** to load `products.csv`, filter out and print only the rows where the `Price` is greater than `5000`. 
   *(Hint: You can filter rows using `df[df['Price'] > 5000]`)*

3. Create a CSV file named `marks.csv` manually with the following data:
   ```csv
   Student,English,Maths
   Rahul,85,90
   Priya,92,95
   Amit,78,80
   Anjali,88,95
   ```
   Write a Python script using **Pandas** that reads `marks.csv` and:
   - Calculates and prints the average marks of `Maths`.
   - Finds and prints the record (name and marks) of the topper in `Maths` using `.idxmax()`.
