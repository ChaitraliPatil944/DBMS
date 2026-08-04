# Lesson 103 --- UPDATE Statement

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the `UPDATE` statement is
-   Why `UPDATE` is used
-   Basic syntax
-   Updating single and multiple columns
-   Using `WHERE`
-   Updating with subqueries
-   Common mistakes
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Data changes over time.

Examples:

-   Employee salary increases.
-   Customer changes address.
-   Student changes phone number.

Instead of deleting and inserting the record again, we use **UPDATE**.

------------------------------------------------------------------------

# 2. What is UPDATE?

`UPDATE` is a **DML (Data Manipulation Language)** command used to
modify existing rows in a table.

``` text
Existing Row
     │
  UPDATE
     │
Modified Row
```

------------------------------------------------------------------------

# 3. Why Do We Need UPDATE?

Without UPDATE:

-   Incorrect data stays incorrect.
-   Business changes cannot be reflected.
-   Records become outdated.

UPDATE keeps information current.

------------------------------------------------------------------------

# 4. Basic Syntax

``` sql
UPDATE table_name
SET column_name = value
WHERE condition;
```

------------------------------------------------------------------------

# 5. Update a Single Column

``` sql
UPDATE Student
SET Age = 21
WHERE StudentID = 101;
```

Before:

``` text
101  Alice 20
```

After:

``` text
101  Alice 21
```

------------------------------------------------------------------------

# 6. Update Multiple Columns

``` sql
UPDATE Employee
SET Salary = 70000,
    Department = 'HR'
WHERE EmployeeID = 1001;
```

------------------------------------------------------------------------

# 7. Why WHERE is Important

``` sql
UPDATE Employee
SET Salary = Salary + 5000
WHERE Department = 'IT';
```

Only IT employees are updated.

Without `WHERE`:

``` sql
UPDATE Employee
SET Salary = Salary + 5000;
```

Every employee receives the increase.

------------------------------------------------------------------------

# 8. UPDATE with Expressions

``` sql
UPDATE Product
SET Price = Price * 1.10;
```

Increase every price by 10%.

------------------------------------------------------------------------

# 9. UPDATE with Subquery

``` sql
UPDATE Employee
SET Department =
(
SELECT DepartmentName
FROM Department
WHERE DepartmentID = 10
)
WHERE EmployeeID = 1001;
```

Subqueries can supply new values.

------------------------------------------------------------------------

# 10. How UPDATE Works

``` text
Find Rows
    │
WHERE Filter
    │
Validate Constraints
    │
Modify Values
    │
COMMIT / ROLLBACK
```

------------------------------------------------------------------------

# 11. Real-World Example

An employee gets promoted.

``` sql
UPDATE Employee
SET Designation = 'Senior Developer',
    Salary = 90000
WHERE EmployeeID = 105;
```

Payroll and HR immediately see the updated information.

------------------------------------------------------------------------

# 12. Best Practices

-   Always test the `WHERE` condition with `SELECT` first.
-   Use transactions for large updates.
-   Update only necessary columns.
-   Keep backups before mass updates.

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Forgetting `WHERE`.

``` sql
UPDATE Student
SET Grade = 'A';
```

Every student receives grade A.

❌ Violating constraints.

``` sql
UPDATE Employee
SET Salary = -100;
```

Fails if a CHECK constraint exists.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is the `UPDATE` statement?
2.  Is UPDATE DDL or DML?
3.  Why is WHERE important?

### Intermediate

1.  Can UPDATE modify multiple columns?
2.  Can UPDATE use expressions?

### Advanced

1.  Explain UPDATE with a subquery.
2.  How can you safely perform a large UPDATE?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Update one student's age.
2.  Increase all salaries by 5%.
3.  Change a department name for selected employees.
4.  Update two columns at once.
5.  Predict the result of UPDATE without WHERE.

------------------------------------------------------------------------

# Revision Notes

``` text
UPDATE
   │
SET
   │
WHERE
   │
Rows Modified
```

## Memory Trick

``` text
UPDATE

=

Modify Existing Data
```

## Key Points

-   `UPDATE` modifies existing rows.
-   `SET` specifies new values.
-   `WHERE` determines which rows change.
-   Expressions and subqueries can be used.
-   Always verify the WHERE clause before execution.

------------------------------------------------------------------------

# Final Takeaway

The `UPDATE` statement keeps database information accurate as the real
world changes. Promotions, address changes, price revisions, and status
updates all rely on UPDATE. Used carefully, it is one of the most
valuable SQL commands. Used carelessly without a proper `WHERE` clause,
it can rewrite an entire table in seconds, and the database will
faithfully assume that was exactly what you meant.
