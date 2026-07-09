# Lesson 104 --- DELETE Statement

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the `DELETE` statement is
-   Why `DELETE` is used
-   Basic syntax
-   Deleting specific rows
-   Deleting all rows
-   DELETE with subqueries
-   DELETE vs TRUNCATE
-   DELETE vs DROP
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Data does not stay useful forever.

Examples:

-   A customer closes an account.
-   A product is discontinued.
-   Temporary records are no longer needed.

Instead of removing the entire table, we remove only the required rows
using **DELETE**.

------------------------------------------------------------------------

# 2. What is DELETE?

`DELETE` is a **DML (Data Manipulation Language)** command used to
remove one or more rows from a table.

``` text
Table
 │
DELETE
 │
Selected Rows Removed
 │
Table Still Exists
```

------------------------------------------------------------------------

# 3. Why Do We Need DELETE?

Without DELETE:

-   Old records accumulate.
-   Incorrect entries remain.
-   Temporary data cannot be cleaned up.

DELETE helps maintain accurate and relevant data.

------------------------------------------------------------------------

# 4. Basic Syntax

``` sql
DELETE FROM table_name
WHERE condition;
```

------------------------------------------------------------------------

# 5. Delete Specific Rows

``` sql
DELETE FROM Student
WHERE StudentID = 101;
```

Only the matching row is removed.

------------------------------------------------------------------------

# 6. Delete Multiple Rows

``` sql
DELETE FROM Employee
WHERE Department = 'HR';
```

All HR employees are removed.

------------------------------------------------------------------------

# 7. Delete All Rows

``` sql
DELETE FROM Student;
```

Result:

``` text
Table Exists

0 Rows
```

Unlike `DROP`, the table structure remains.

------------------------------------------------------------------------

# 8. DELETE with Subquery

``` sql
DELETE FROM Employee
WHERE DepartmentID IN
(
    SELECT DepartmentID
    FROM Department
    WHERE DepartmentName='Sales'
);
```

Rows can be removed based on another table.

------------------------------------------------------------------------

# 9. How DELETE Works

``` text
Find Rows
    │
WHERE Filter
    │
Check Constraints
    │
Delete Rows
    │
COMMIT / ROLLBACK
```

------------------------------------------------------------------------

# 10. DELETE vs TRUNCATE

  DELETE                  TRUNCATE
  ----------------------- -------------------------------
  DML                     DDL
  WHERE supported         WHERE not supported
  Removes selected rows   Removes all rows
  Row-by-row logging      Minimal logging in many DBMSs
  Usually slower          Usually faster

------------------------------------------------------------------------

# 11. DELETE vs DROP

  DELETE              DROP
  ------------------- ------------------------
  Removes rows        Removes table
  Structure remains   Structure removed
  DML                 DDL
  Table reusable      Table no longer exists

------------------------------------------------------------------------

# 12. Real-World Example

Delete cancelled orders older than one year.

``` sql
DELETE FROM Orders
WHERE Status='Cancelled'
AND OrderDate < '2025-01-01';
```

------------------------------------------------------------------------

# 13. Best Practices

-   Always test the condition with `SELECT` first.
-   Always use `WHERE` unless every row should be removed.
-   Use transactions for important deletions.
-   Take backups before bulk deletes.

------------------------------------------------------------------------

# 14. Common Mistakes

❌ Forgetting the WHERE clause.

``` sql
DELETE FROM Employee;
```

Every row is deleted.

❌ Confusing DELETE with DROP.

DELETE removes rows only.

DROP removes the entire table.

------------------------------------------------------------------------

# 15. Interview Questions

### Beginner

1.  What is the DELETE statement?
2.  Is DELETE DDL or DML?
3.  Why is WHERE important?

### Intermediate

1.  DELETE vs TRUNCATE?
2.  DELETE vs DROP?
3.  Can DELETE use subqueries?

### Advanced

1.  Why is DELETE slower than TRUNCATE?
2.  How do transactions improve DELETE operations?

------------------------------------------------------------------------

# 16. Practice Problems

1.  Delete one student using StudentID.
2.  Delete all inactive customers.
3.  Delete employees from the Sales department.
4.  Delete rows using a subquery.
5.  Compare DELETE, TRUNCATE, and DROP.

------------------------------------------------------------------------

# Revision Notes

``` text
DELETE
   │
WHERE
   │
Selected Rows Removed
   │
Table Remains
```

## Memory Trick

``` text
DELETE

=

Remove Data

Keep Table
```

## Key Points

-   `DELETE` removes rows, not the table.
-   `WHERE` controls which rows are deleted.
-   Without `WHERE`, every row is removed.
-   `DELETE` supports transactions and rollback before commit.
-   Use `TRUNCATE` when all rows must be removed quickly.

------------------------------------------------------------------------

# Final Takeaway

The `DELETE` statement is the standard way to remove data from a
relational database while preserving the table structure. It offers
precise control through the `WHERE` clause and integrates with
transactions, making it suitable for most day-to-day data removal tasks.
The safest habit in SQL is to write the `WHERE` clause first, verify it
with a `SELECT`, and only then replace `SELECT` with `DELETE`. Databases
are efficient, but they are not mind readers.
