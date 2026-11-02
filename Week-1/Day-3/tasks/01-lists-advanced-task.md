# Day 3 - Task 1: Advanced Lists

## Example (already solved, for reference only)

Problem: Given a list of numbers, create a new list that contains only the
numbers greater than 50, sorted in descending order.

```python
numbers = [12, 67, 45, 89, 23, 90, 5]
result = sorted([n for n in numbers if n > 50], reverse=True)
print(result)
```

Use the same style of thinking for the tasks below. Do not look at the example
code while solving them, write your own logic.

## Your Tasks

1. Take a list of at least 10 product prices. Create a new list that
   contains only the prices above the average price, without using a normal
   for loop to build the new list. Use a list comprehension instead.

2. Take a list of full names such as `["riya sharma", "aman gupta"]`. Create
   a new list where every name is converted to title case (first letter of
   each word capital), using a list comprehension.

3. You are given a list of 15 random integers between 1 and 100. Remove all
   duplicate values while keeping the original order of first appearance.
   Do not use `set()` for this task, write your own loop based logic.

4. Take a 3x3 matrix written as a list of lists. Write code that prints its
   transpose (rows become columns) using a nested list comprehension.

5. You are given a list of tuples where each tuple has a student name and
   their marks, for example `[("Riya", 88), ("Aman", 95), ("Sara", 72)]`.
   Sort this list so that the topper appears first, using the `key`
   parameter of `sort()` or `sorted()`.

6. Take any list of numbers. Without using `max()` or `min()` directly,
   write your own loop based logic to find the second largest number in the
   list.

7. Take two lists of equal length, one of employee names and one of their
   salaries. Print each employee name with their salary using `zip()`
   instead of using index based access.

8. Create a small "to-do list manager" using a plain list. It should support
   adding a task, removing a task by name, and printing all current tasks.
   Test it by adding 5 tasks and removing 2 of them.
