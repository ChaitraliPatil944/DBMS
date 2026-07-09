# Lesson 094 --- SQL Clauses

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What SQL clauses are
-   Why clauses are important
-   Major SQL clauses
-   SQL query execution flow
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. What are SQL Clauses?

A **clause** is a building block of an SQL statement. Each clause
performs a specific task.

``` text
SQL Query
   │
 ├── SELECT
 ├── FROM
 ├── WHERE
 ├── GROUP BY
 ├── HAVING
 ├── ORDER BY
 └── LIMIT
```

Together, these clauses form a complete query.

------------------------------------------------------------------------

# 2. Why Do We Need Clauses?

Imagine an Employee table with 1 million rows.

You may want to:

-   Retrieve only names
-   Filter IT employees
-   Group by department
-   Sort by salary
-   Display only the top 10 records

Each requirement is handled by a different clause.

------------------------------------------------------------------------

# 3. SELECT Clause

Retrieves one or more columns.

``` sql
SELECT Name, Salary
FROM Employee;
```

`*` retrieves all columns.

``` sql
SELECT *
FROM Employee;
```

------------------------------------------------------------------------

# 4. FROM Clause

Specifies the source table.

``` sql
SELECT *
FROM Student;
```

Without `FROM`, the DBMS doesn't know where to retrieve data.

------------------------------------------------------------------------

# 5. WHERE Clause

Filters rows before they are returned.

``` sql
SELECT *
FROM Employee
WHERE Salary > 50000;
```

------------------------------------------------------------------------

# 6. GROUP BY Clause

Groups rows with common values.

``` sql
SELECT Department, COUNT(*)
FROM Employee
GROUP BY Department;
```

Used with aggregate functions.

------------------------------------------------------------------------

# 7. HAVING Clause

Filters groups after `GROUP BY`.

``` sql
SELECT Department, COUNT(*)
FROM Employee
GROUP BY Department
HAVING COUNT(*) > 5;
```

Think of it as `WHERE` for groups.

------------------------------------------------------------------------

# 8. ORDER BY Clause

Sorts the result.

Ascending:

``` sql
ORDER BY Salary ASC;
```

Descending:

``` sql
ORDER BY Salary DESC;
```

------------------------------------------------------------------------

# 9. LIMIT and OFFSET

Limit the number of rows.

``` sql
SELECT *
FROM Product
LIMIT 10;
```

Skip rows:

``` sql
SELECT *
FROM Product
LIMIT 10 OFFSET 20;
```

------------------------------------------------------------------------

# 10. Complete Query Example

``` sql
SELECT Department,
       AVG(Salary) AS AvgSalary
FROM Employee
WHERE Salary > 30000
GROUP BY Department
HAVING AVG(Salary) > 50000
ORDER BY AvgSalary DESC
LIMIT 5;
```

------------------------------------------------------------------------

# 11. Logical Query Processing Order

Although we write:

``` text
SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY
LIMIT
```

The DBMS logically processes:

``` text
FROM
   │
WHERE
   │
GROUP BY
   │
HAVING
   │
SELECT
   │
ORDER BY
   │
LIMIT
```

Understanding this order helps explain many SQL errors.

------------------------------------------------------------------------

# 12. Real-World Example

Find the top 3 departments with the highest average salary.

``` sql
SELECT Department,
AVG(Salary)
FROM Employee
GROUP BY Department
ORDER BY AVG(Salary) DESC
LIMIT 3;
```

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Using `WHERE` with aggregate functions.

``` sql
WHERE COUNT(*) > 5
```

✔ Use `HAVING`.

------------------------------------------------------------------------

❌ Forgetting `GROUP BY` when selecting non-aggregated columns.

------------------------------------------------------------------------

❌ Assuming SQL executes clauses in the order they are written.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is an SQL clause?
2.  Difference between `WHERE` and `HAVING`?
3.  Purpose of `ORDER BY`?

### Intermediate

1.  Why is `GROUP BY` used?
2.  What is `LIMIT`?

### Advanced

1.  Explain SQL logical execution order.
2.  Why can't aliases usually be used in `WHERE`?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Display all students.
2.  Display employees earning more than 60000.
3.  Count employees in each department.
4.  Show departments with more than 10 employees.
5.  Display the five highest-paid employees.

------------------------------------------------------------------------

# Revision Notes

``` text
SELECT → Columns

FROM → Table

WHERE → Filter Rows

GROUP BY → Create Groups

HAVING → Filter Groups

ORDER BY → Sort

LIMIT → Restrict Rows
```

## Memory Trick

``` text
S F W G H O L

SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY
LIMIT
```

## Key Points

-   Clauses are the building blocks of SQL queries.
-   Each clause has a specific responsibility.
-   `WHERE` filters rows before grouping.
-   `HAVING` filters groups after grouping.
-   Learn both the written order and the logical execution order.

------------------------------------------------------------------------

# Final Takeaway

SQL clauses work together like stages in an assembly line. Each clause
receives data, transforms or filters it, and passes it to the next stage
until the final result is produced. Understanding the role and execution
order of these clauses makes writing complex SQL queries far easier than
memorizing isolated syntax.
