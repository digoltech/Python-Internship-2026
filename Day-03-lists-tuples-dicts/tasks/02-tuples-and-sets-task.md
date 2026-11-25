# Day 3 - Task 2: Tuples and Sets

## Example (already solved, for reference only)

Problem: You have two sets of skills from two different employees. Print the
skills that both employees have in common, and the skills that are unique to
the first employee.

```python
employee_a = {"python", "sql", "excel", "git"}
employee_b = {"python", "java", "git", "docker"}

common_skills = employee_a.intersection(employee_b)
unique_to_a = employee_a.difference(employee_b)

print(common_skills)
print(unique_to_a)
```

Use the same style of thinking for the tasks below. Do not look at the
example code while solving them, write your own logic.

## Your Tasks

1. Write a function that takes a list of student marks and returns a tuple
   containing the lowest mark, the highest mark, and the average mark. Call
   the function and unpack the result into three separate variables.

2. Create a tuple representing a product record with name, price, and
   quantity. Try to change the price directly and observe the error. Then
   write the correct way to "update" a product record by creating a new
   tuple instead.

3. You are given a list of (latitude, longitude) tuples representing visited
   locations, for example `[(12.9, 77.5), (19.0, 72.8)]`. Write code that
   unpacks each tuple inside a loop and prints them in the format
   `Latitude: x, Longitude: y`.

4. Take two sets of email addresses, one representing newsletter subscribers
   and one representing customers who made a purchase. Find subscribers who
   never made a purchase, and customers who made a purchase but never
   subscribed.

5. You are given a list of website visitor IDs which contains many repeated
   values. Use a set to find how many unique visitors there were, and also
   print the count of unique visitors.

6. Build a simple permission system using sets. Create a set of permissions
   for an "admin" role and a set of permissions for an "editor" role. Write
   code that checks if a given user, who has only "editor" permissions, can
   perform an action that requires "admin" permissions.

7. Write a function that accepts any list and returns a `frozenset` made
   from it. Explain in a one line comment inside your answer file (not
   inside the code) why a frozenset is useful when you want to use the
   result as a dictionary key later.
