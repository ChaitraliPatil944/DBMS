# Lesson 234 - Scalar Subqueries

**Part:** Part 9 - Subqueries

**Difficulty:** Beginner → Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 45–60 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand what a scalar subquery is.
- Learn where scalar subqueries can be used.
- Compare scalar subqueries with joins.
- Understand how the DBMS executes scalar subqueries.
- Optimize scalar subquery performance.
- Solve interview-oriented SQL problems.

---

# 1. Introduction

A **Scalar Subquery** is a subquery that returns **exactly one row and one column**.

Because it produces a single value, it can be used anywhere a literal value is expected.

Examples include:

- SELECT
- WHERE
- HAVING
- ORDER BY

---

# 2. Why Scalar Subqueries?

Instead of hardcoding values, queries can calculate them dynamically.

Example:

> Find employees whose salary is greater than the average salary.

The average salary changes over time, so calculating it inside the query is more reliable.

---

# 3. Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name >
(
    SELECT AVG(column_name)
    FROM table_name
);
```

The inner query returns one value.

The outer query compares each row against that value.

---

# 4. Example

### Employee

```text
+------------+--------+--------+
|EmployeeID  |Name    |Salary  |
+------------+--------+--------+
|1           |Alice   |40000   |
|2           |Bob     |55000   |
|3           |Carol   |70000   |
+------------+--------+--------+
```

Query:

```sql
SELECT Name,
       Salary
FROM Employee
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employee
);
```

Result:

```text
+--------+--------+
|Name    |Salary  |
+--------+--------+
|Bob     |55000   |
|Carol   |70000   |
+--------+--------+
```

---

# 5. Execution Flow

```text
Execute Inner Query
        │
Return Single Value
        │
Outer Query Uses Value
        │
Return Final Result
```

The scalar subquery executes first because the outer query depends on its value.

---

# 6. Internal Working

For an **uncorrelated** scalar subquery:

```text
Optimizer
      │
Execute Inner Query Once
      │
Store Result
      │
Execute Outer Query
      │
Compare Against Stored Value
```

Since the result is constant, most DBMSs evaluate it only once.

---

# 7. Common Uses

## WHERE Clause

```sql
SELECT *
FROM Employee
WHERE Salary >
(
SELECT AVG(Salary)
FROM Employee
);
```

## SELECT Clause

```sql
SELECT Name,
       Salary,
(
SELECT AVG(Salary)
FROM Employee
) AS AverageSalary
FROM Employee;
```

## HAVING Clause

```sql
SELECT DepartmentID,
       AVG(Salary)
FROM Employee
GROUP BY DepartmentID
HAVING AVG(Salary) >
(
SELECT AVG(Salary)
FROM Employee
);
```

---

# 8. Scalar Subquery vs JOIN

| Feature | Scalar Subquery | JOIN |
|---------|-----------------|------|
|Returns one value|✔|✖|
|Can replace constants|✔|✖|
|Returns related rows|✖|✔|
|Often easier for aggregate comparisons|✔|Sometimes|

---

# 9. Real Project Examples

## Banking

Find accounts with balances above the average balance.

## Telecom

Find subscribers with recharge amounts above the average recharge.

## E-Commerce

Find products priced above the average product price.

## Hospital

Find doctors earning more than the average salary.

---

# 10. Performance Notes

- Uncorrelated scalar subqueries are usually executed once.
- Indexes on filtered columns improve performance.
- Avoid repeating identical scalar subqueries unnecessarily.
- Compare execution plans when choosing between joins and subqueries.

---

# 11. Common Mistakes

- Returning multiple rows from a scalar subquery.
- Returning multiple columns.
- Using scalar subqueries where joins are more appropriate.
- Forgetting that the outer query expects exactly one value.

---

# 12. Interview Questions

## Beginner

1. What is a scalar subquery?
2. How many rows and columns can it return?
3. Where can scalar subqueries be used?

## Intermediate

1. Scalar subquery vs JOIN?
2. Scalar subquery vs correlated subquery?
3. Why is AVG() commonly used with scalar subqueries?

## Advanced

1. How does the optimizer execute an uncorrelated scalar subquery?
2. What happens if the subquery returns multiple rows?
3. How can scalar subqueries impact performance?

---

# 13. Practice

```sql
-- Products above average price
SELECT ProductName,
       Price
FROM Product
WHERE Price >
(
SELECT AVG(Price)
FROM Product
);

-- Employees earning above average
SELECT Name
FROM Employee
WHERE Salary >
(
SELECT AVG(Salary)
FROM Employee
);

-- Orders above average amount
SELECT *
FROM Orders
WHERE Amount >
(
SELECT AVG(Amount)
FROM Orders
);
```

---

# Revision Notes

- Scalar subquery returns exactly one row and one column.
- Often used with aggregate functions.
- Usually executes before the outer query.
- Best suited for comparisons against calculated values.

---

# Memory Trick

**Scalar = Single Value**

One row. One column. One value.

---

# Final Takeaway

Scalar subqueries are one of the simplest and most useful forms of subqueries because they return a single value that can be used anywhere a constant is expected. They are frequently used with aggregate functions such as `AVG()`, `MAX()`, and `MIN()` to create dynamic queries that automatically adapt as data changes. Understanding when a scalar subquery is appropriate, and when a join is a better choice, is an important skill for SQL interviews and real-world database development.
