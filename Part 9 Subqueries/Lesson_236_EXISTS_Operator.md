# Lesson 236 - EXISTS Operator

**Part:** Part 9 - Subqueries

**Difficulty:** Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 45–55 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand the EXISTS operator.
- Learn how EXISTS works with subqueries.
- Compare EXISTS with IN.
- Explain internal DBMS execution.
- Optimize EXISTS queries.
- Solve interview-oriented SQL problems.

---

# 1. Introduction

The **EXISTS** operator checks whether a subquery returns **at least one row**.

- If the subquery returns one or more rows → **TRUE**
- If the subquery returns no rows → **FALSE**

EXISTS does **not** care about the values returned. It only checks for the existence of rows.

---

# 2. Why EXISTS?

Suppose an e-commerce company wants to list customers who have placed at least one order.

Instead of counting orders, EXISTS simply checks whether a matching order exists.

This often improves performance because the database can stop searching after finding the first match.

---

# 3. Syntax

```sql
SELECT column_list
FROM TableA a
WHERE EXISTS
(
    SELECT 1
    FROM TableB b
    WHERE b.Key = a.Key
);
```

`SELECT 1` is commonly used because the returned value is ignored.

---

# 4. Sample Tables

### Customer

```text
+------------+--------+
|CustomerID  |Name    |
+------------+--------+
|1           |Alice   |
|2           |Bob     |
|3           |Carol   |
+------------+--------+
```

### Orders

```text
+---------+------------+
|OrderID  |CustomerID  |
+---------+------------+
|101      |1           |
|102      |1           |
|103      |3           |
+---------+------------+
```

---

# 5. Example

```sql
SELECT Name
FROM Customer c
WHERE EXISTS
(
SELECT 1
FROM Orders o
WHERE o.CustomerID = c.CustomerID
);
```

Result

```text
Alice
Carol
```

Bob is excluded because no matching order exists.

---

# 6. Internal Working

```text
Read Customer Row
       │
Execute Subquery
       │
Match Found?
   ┌───┴────┐
 Yes        No
 │          │
Return    Skip Row
Row
```

The database can stop scanning the subquery after the **first matching row**.

---

# 7. EXISTS vs IN

| Feature | EXISTS | IN |
|---------|--------|----|
|Checks existence|✔|✖|
|Compares values|✖|✔|
|Stops after first match|✔|Usually ✖|
|Good for correlated queries|✔|Sometimes|

---

# 8. NOT EXISTS

Return customers with no orders.

```sql
SELECT Name
FROM Customer c
WHERE NOT EXISTS
(
SELECT 1
FROM Orders o
WHERE o.CustomerID = c.CustomerID
);
```

---

# 9. Real Project Examples

## Banking

Customers with at least one active account.

## Telecom

Subscribers who have recharged.

## E-Commerce

Products that have been ordered.

## Hospital

Doctors with appointments.

---

# 10. Performance Notes

- EXISTS often performs well on large tables.
- Index correlated columns.
- The optimizer may transform EXISTS into a semi-join.
- Compare execution plans with JOIN and IN.

---

# 11. Common Mistakes

- Thinking EXISTS returns data from the subquery.
- Using EXISTS when a simple JOIN is sufficient.
- Forgetting correlation conditions.
- Confusing EXISTS with IN.

---

# 12. Interview Questions

## Beginner

1. What does EXISTS do?
2. Why is `SELECT 1` commonly used?
3. Does EXISTS care about returned values?

## Intermediate

1. EXISTS vs IN?
2. EXISTS vs JOIN?
3. What is NOT EXISTS?

## Advanced

1. How does the optimizer execute EXISTS?
2. Why can EXISTS outperform IN?
3. What is a semi-join?

---

# 13. Practice

```sql
-- Customers with orders
SELECT Name
FROM Customer c
WHERE EXISTS
(
SELECT 1
FROM Orders o
WHERE o.CustomerID = c.CustomerID
);

-- Products with sales
SELECT ProductName
FROM Product p
WHERE EXISTS
(
SELECT 1
FROM Orders o
WHERE o.ProductID = p.ProductID
);

-- Departments with employees
SELECT DepartmentName
FROM Department d
WHERE EXISTS
(
SELECT 1
FROM Employee e
WHERE e.DepartmentID = d.DepartmentID
);
```

---

# Revision Notes

- EXISTS checks whether rows exist.
- Returns TRUE or FALSE.
- Stops after the first matching row.
- Frequently used with correlated subqueries.
- NOT EXISTS finds missing relationships.

---

# Memory Trick

**EXISTS = At Least One**

If one matching row exists, the condition is TRUE.

---

# Final Takeaway

The EXISTS operator is one of the most efficient tools for checking whether related data exists. Because it only needs to find the first matching row, it often performs better than alternatives that must process every matching value. EXISTS and NOT EXISTS are widely used in production systems for validating relationships, detecting missing records, and solving interview questions involving correlated subqueries.
