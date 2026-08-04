# Lesson 226 - INNER JOIN

**Part:** Part 8 - Joins

**Difficulty:** Beginner → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 45–60 Minutes

---

# Learning Objectives

After this lesson, you will be able to:

- Understand what an INNER JOIN is.
- Explain how a DBMS executes an INNER JOIN internally.
- Differentiate INNER JOIN from other joins.
- Read execution flow diagrams.
- Optimize INNER JOIN queries using indexes.
- Solve interview-oriented join problems.

---

# 1. Introduction

An **INNER JOIN** returns **only the rows that have matching values in both tables**.

If there is no matching row, it is excluded from the result.

It is the most commonly used join in SQL and one of the most frequently asked interview topics.

---

# 2. Why Do We Need INNER JOIN?

Database normalization stores related information in different tables.

Instead of storing duplicate data, we connect tables using common keys.

Example:

- Customer details → Customers table
- Orders → Orders table

To display customer names with their orders, we use an INNER JOIN.

---

# 3. Real-World Analogy

Imagine a college.

One register contains **Students**.

Another register contains **Exam Results**.

Only students who appear in **both** registers will appear in the final report.

That is exactly how INNER JOIN works.

---

# 4. Sample Tables

### Customers

```text
+------------+---------+
|CustomerID  |Name     |
+------------+---------+
|1           |Amit     |
|2           |Neha     |
|3           |Raj      |
+------------+---------+
```

### Orders

```text
+---------+------------+--------+
|OrderID  |CustomerID  |Amount  |
+---------+------------+--------+
|101      |1           |500     |
|102      |2           |700     |
|103      |4           |900     |
+---------+------------+--------+
```

---

# 5. Syntax

```sql
SELECT c.CustomerID,
       c.Name,
       o.OrderID,
       o.Amount
FROM Customers c
INNER JOIN Orders o
ON c.CustomerID = o.CustomerID;
```

---

# 6. Result

```text
+------------+------+---------+--------+
|CustomerID  |Name  |OrderID  |Amount  |
+------------+------+---------+--------+
|1           |Amit  |101      |500     |
|2           |Neha  |102      |700     |
+------------+------+---------+--------+
```

Customer **Raj** has no order.

Order **103** has no matching customer.

Both are excluded.

---

# 7. How INNER JOIN Works Internally

```text
Customers
     │
     │ Match CustomerID
     ▼
Orders
     │
     ▼
Return Matching Rows Only
```

Execution Flow

```text
Read First Table
      │
Read Second Table
      │
Compare Join Keys
      │
Keep Matching Rows
      │
Discard Non-Matching Rows
      │
Return Result
```

---

# 8. Join Algorithms Used by the DBMS

A DBMS may execute an INNER JOIN using different algorithms.

## Nested Loop Join

Best for small tables.

```text
For each row in Customers
        │
Scan Orders
        │
Find Matches
```

Time Complexity (approx.)

```
O(n × m)
```

---

## Hash Join

Used for large unsorted tables.

```text
Build Hash Table
        │
Hash Join Key
        │
Probe Second Table
```

Very fast for equality joins.

---

## Merge Join

Requires sorted inputs.

```text
Sorted Table A
        │
Sorted Table B
        │
Merge Sequentially
```

Efficient when indexes already provide sorted data.

---

# 9. Real Project Examples

## Banking

Join Customers and Accounts.

## Telecom

Join Subscribers and Recharge History.

## E-Commerce

Join Customers, Orders, and Products.

## Hospital

Join Patients and Appointments.

---

# 10. Performance Notes

- Create indexes on join columns.
- Join columns should have matching data types.
- Avoid functions on join keys.
- Retrieve only required columns instead of using `SELECT *`.

---

# 11. Common Mistakes

- Forgetting the `ON` clause.
- Joining unrelated columns.
- Mixing data types.
- Assuming INNER JOIN returns all rows.
- Creating accidental Cartesian products.

---

# 12. Interview Questions

## Beginner

1. What is an INNER JOIN?
2. When should INNER JOIN be used?
3. What happens to unmatched rows?

## Intermediate

1. INNER JOIN vs LEFT JOIN?
2. Why is the `ON` clause important?
3. Can multiple INNER JOINs be used in one query?

## Advanced

1. Explain Nested Loop Join, Hash Join, and Merge Join.
2. How do indexes improve joins?
3. How does the optimizer choose a join algorithm?
4. What is the cost of joining two large tables?

---

# 13. Practice

```sql
-- Customers with Orders
SELECT c.Name,
       o.OrderID
FROM Customers c
INNER JOIN Orders o
ON c.CustomerID=o.CustomerID;

-- Employees with Departments
SELECT e.Name,
       d.DepartmentName
FROM Employee e
INNER JOIN Department d
ON e.DepartmentID=d.DepartmentID;

-- Products with Categories
SELECT p.ProductName,
       c.CategoryName
FROM Product p
INNER JOIN Category c
ON p.CategoryID=c.CategoryID;
```

---

# Revision Notes

- INNER JOIN returns only matching rows.
- Matching is determined using the `ON` condition.
- Unmatched rows are discarded.
- DBMS may use Nested Loop, Hash, or Merge Join.
- Indexes significantly improve join performance.

---

# Memory Trick

**INNER = INTERSECTION**

Think of two overlapping circles.

Only the common area is returned.

---

# Final Takeaway

INNER JOIN is the foundation of relational databases because it combines related information stored across multiple normalized tables. Beyond syntax, interviewers expect you to understand **how the database matches rows, why indexes matter, and which join algorithm the optimizer may choose**. Mastering these concepts prepares you for both SQL coding rounds and system design discussions involving relational databases.
