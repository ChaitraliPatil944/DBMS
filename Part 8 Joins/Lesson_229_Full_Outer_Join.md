# Lesson 229 - FULL OUTER JOIN

**Part:** Part 8 - Joins

**Difficulty:** Beginner → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐☆  
**Estimated Reading Time:** 45–55 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand FULL OUTER JOIN.
- Differentiate it from INNER, LEFT, and RIGHT JOIN.
- Explain how a DBMS executes a FULL OUTER JOIN.
- Identify real-world use cases.
- Understand DBMS support and alternatives.
- Solve interview-oriented SQL problems.

---

# 1. Introduction

A **FULL OUTER JOIN** returns:

- All matching rows from both tables.
- All unmatched rows from the left table.
- All unmatched rows from the right table.

Whenever a matching row does not exist, the missing columns are filled with **NULL**.

It combines the behavior of **LEFT JOIN** and **RIGHT JOIN**.

---

# 2. Why FULL OUTER JOIN?

Imagine an HR system.

One table stores Employees.

Another table stores Parking Passes.

Management wants:

- Employees without parking passes.
- Parking passes assigned correctly.
- Parking passes that are not assigned.

A FULL OUTER JOIN displays every record from both tables.

---

# 3. Real-World Analogy

Imagine two guest lists.

- Wedding Guests
- Hotel Guests

A combined report should show:

- People in both lists.
- Guests only attending the wedding.
- Guests only staying at the hotel.

Nothing is discarded.

---

# 4. Sample Tables

### Employees

```text
+------------+---------+
|EmployeeID  |Name     |
+------------+---------+
|1           |Amit     |
|2           |Neha     |
|3           |Raj      |
+------------+---------+
```

### ParkingPass

```text
+------------+----------+
|EmployeeID  |PassID    |
+------------+----------+
|1           |P101      |
|4           |P102      |
+------------+----------+
```

---

# 5. Syntax

```sql
SELECT e.EmployeeID,
       e.Name,
       p.PassID
FROM Employee e
FULL OUTER JOIN ParkingPass p
ON e.EmployeeID = p.EmployeeID;
```

> **Note:** MySQL does **not** support `FULL OUTER JOIN` directly. It is supported in PostgreSQL, SQL Server, and Oracle.

---

# 6. Result

```text
+------------+------+--------+
|EmployeeID  |Name  |PassID  |
+------------+------+--------+
|1           |Amit  |P101    |
|2           |Neha  |NULL    |
|3           |Raj   |NULL    |
|NULL        |NULL  |P102    |
+------------+------+--------+
```

---

# 7. Internal Working

```text
LEFT JOIN Result
        │
        ▼
RIGHT JOIN Result
        │
        ▼
Remove Duplicate Matches
        │
        ▼
Return Combined Output
```

Conceptually, FULL OUTER JOIN combines both sides while avoiding duplicate matched rows.

---

# 8. Visual Representation

```text
Left Table
     │
     ├─────────────┐
     │             │
Matching Rows      │
     │             │
     └─────────────┤
                   ▼
Right Table

Return EVERYTHING
```

---

# 9. FULL OUTER JOIN in MySQL

Since MySQL does not support FULL OUTER JOIN directly, it can be simulated.

```sql
SELECT *
FROM A
LEFT JOIN B
ON A.ID = B.ID

UNION

SELECT *
FROM A
RIGHT JOIN B
ON A.ID = B.ID;
```

This is one of the most common interview questions.

---

# 10. Real Project Examples

## Banking

- Customers and loan records.
- Display unmatched customers and orphan loans.

## Telecom

- Subscribers and SIM inventory.

## E-Commerce

- Products and inventory records.

## Hospital

- Doctors and assigned departments.

---

# 11. Performance Notes

- FULL OUTER JOIN is more expensive than INNER JOIN.
- It may require processing unmatched rows from both tables.
- Proper indexing on join keys improves performance.
- UNION-based implementations can be slower on large datasets.

---

# 12. Common Mistakes

- Assuming MySQL supports FULL OUTER JOIN.
- Forgetting duplicate removal when using UNION.
- Confusing FULL OUTER JOIN with CROSS JOIN.
- Using it when INNER or LEFT JOIN is sufficient.

---

# 13. Comparison of Joins

| Join Type | Left Rows | Right Rows | Matching Rows |
|-----------|:---------:|:----------:|:-------------:|
|INNER JOIN|✖|✖|✔|
|LEFT JOIN|✔|✖|✔|
|RIGHT JOIN|✖|✔|✔|
|FULL OUTER JOIN|✔|✔|✔|

---

# 14. Interview Questions

## Beginner

1. What is a FULL OUTER JOIN?
2. Which rows are returned?
3. How is it different from INNER JOIN?

## Intermediate

1. Does MySQL support FULL OUTER JOIN?
2. How can it be simulated?
3. FULL OUTER JOIN vs UNION?

## Advanced

1. How does the optimizer execute FULL OUTER JOIN?
2. Why is FULL OUTER JOIN more expensive?
3. When should FULL OUTER JOIN be avoided?
4. Explain a production use case.

---

# 15. Practice

```sql
-- Employees and Parking Passes
SELECT *
FROM Employee
FULL OUTER JOIN ParkingPass
ON Employee.EmployeeID=ParkingPass.EmployeeID;

-- MySQL Equivalent
SELECT *
FROM Employee
LEFT JOIN ParkingPass
ON Employee.EmployeeID=ParkingPass.EmployeeID

UNION

SELECT *
FROM Employee
RIGHT JOIN ParkingPass
ON Employee.EmployeeID=ParkingPass.EmployeeID;
```

---

# Revision Notes

- FULL OUTER JOIN returns all rows from both tables.
- Missing matches are filled with NULL values.
- It combines LEFT JOIN and RIGHT JOIN behavior.
- MySQL requires a UNION-based workaround.

---

# Memory Trick

**FULL = Everything From Both Tables**

Nothing is discarded.

---

# Final Takeaway

FULL OUTER JOIN provides the complete picture by returning every row from both participating tables, regardless of whether a match exists. It is especially useful for reconciliation, auditing, and data comparison tasks. In interviews, the most frequently asked question is how to implement a FULL OUTER JOIN in MySQL, making the UNION-based solution an important technique to remember.
