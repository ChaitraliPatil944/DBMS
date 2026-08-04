# Lesson 227 - LEFT JOIN

**Part:** Part 8 - Joins

**Difficulty:** Beginner → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 45–60 Minutes

---

# Learning Objectives

After this lesson, you will be able to:

- Understand the purpose of LEFT JOIN.
- Explain how LEFT JOIN differs from INNER JOIN.
- Understand NULL values in LEFT JOIN results.
- Learn how DBMS executes LEFT JOIN internally.
- Optimize LEFT JOIN queries.
- Solve interview-oriented problems using LEFT JOIN.

---

# 1. Introduction

A **LEFT JOIN** returns:

- All rows from the **left table**
- Matching rows from the **right table**
- **NULL** values when no matching row exists in the right table

Unlike INNER JOIN, unmatched rows from the left table are never discarded.

---

# 2. Why LEFT JOIN?

Suppose an e-commerce company wants to display **every customer**, even if they have never placed an order.

An INNER JOIN hides customers without orders.

A LEFT JOIN keeps them.

---

# 3. Real-World Analogy

Imagine a school.

One register contains every student.

Another register contains library members.

The principal wants a report containing **every student**, whether they joined the library or not.

Students without memberships simply have blank library information.

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
LEFT JOIN Orders o
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
|3           |Raj   |NULL     |NULL    |
+------------+------+---------+--------+
```

Raj appears even though no order exists.

---

# 7. Internal Working

```text
Read Left Table
      │
Read Right Table
      │
Match Join Keys
      │
Return Matches
      │
If No Match
      │
Fill Right Columns with NULL
      │
Return Every Left Row
```

---

# 8. Visual Representation

```text
Customers
     │
     ├── Match Found ─────► Return Data
     │
     └── No Match ────────► Return NULL Columns
```

---

# 9. Finding Missing Records

One of the most common interview questions.

Customers without orders:

```sql
SELECT c.CustomerID,
       c.Name
FROM Customers c
LEFT JOIN Orders o
ON c.CustomerID=o.CustomerID
WHERE o.CustomerID IS NULL;
```

This pattern is heavily used in production systems.

---

# 10. Real Project Examples

## Banking

Customers without bank accounts.

## Telecom

Subscribers who have never recharged.

## E-Commerce

Customers who never placed an order.

## Hospital

Doctors without appointments.

---

# 11. Performance Notes

- Index both join columns.
- Avoid functions on join keys.
- Filter as early as possible.
- Use LEFT JOIN only when unmatched rows are required.

---

# 12. Common Mistakes

- Confusing LEFT JOIN with INNER JOIN.
- Placing right-table filters in WHERE instead of ON, unintentionally converting the query into an INNER JOIN.
- Forgetting that unmatched columns become NULL.
- Joining columns with different data types.

---

# 13. LEFT JOIN vs INNER JOIN

| Feature | INNER JOIN | LEFT JOIN |
|---------|------------|-----------|
|Returns matching rows|✔|✔|
|Returns all left rows|✖|✔|
|Returns NULL for missing right rows|✖|✔|

---

# 14. Interview Questions

## Beginner

1. What is LEFT JOIN?
2. Why are NULL values returned?
3. Difference between INNER JOIN and LEFT JOIN?

## Intermediate

1. How do you find customers without orders?
2. Why can WHERE conditions change LEFT JOIN results?
3. Can multiple LEFT JOINs be used together?

## Advanced

1. Explain how a query optimizer executes LEFT JOIN.
2. When should LEFT JOIN be avoided?
3. LEFT JOIN vs NOT EXISTS?
4. How do indexes improve LEFT JOIN performance?

---

# 15. Practice

```sql
-- Customers without orders
SELECT c.Name
FROM Customers c
LEFT JOIN Orders o
ON c.CustomerID=o.CustomerID
WHERE o.CustomerID IS NULL;

-- Employees without departments
SELECT e.Name
FROM Employee e
LEFT JOIN Department d
ON e.DepartmentID=d.DepartmentID;

-- Products without sales
SELECT p.ProductName
FROM Product p
LEFT JOIN Sales s
ON p.ProductID=s.ProductID;
```

---

# Revision Notes

- LEFT JOIN returns every row from the left table.
- Matching rows come from the right table.
- Missing matches become NULL.
- Frequently used to find missing records.
- Be careful when adding WHERE conditions on the right table.

---

# Memory Trick

**LEFT = Leave Nothing Behind (Left Table)**

Always remember: every row from the left table survives.

---

# Final Takeaway

LEFT JOIN is essential whenever your query must preserve every record from the primary table while optionally retrieving related data from another table. It is widely used for reporting, auditing, and identifying missing relationships. Interviewers frequently test LEFT JOIN together with NULL filtering because it demonstrates a solid understanding of relational database behavior beyond simple syntax.
