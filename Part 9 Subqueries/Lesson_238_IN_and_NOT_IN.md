# Lesson 238 - IN and NOT IN

**Part:** Part 9 - Subqueries

**Difficulty:** Beginner → Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 45–55 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand the IN and NOT IN operators.
- Learn how they work with subqueries.
- Compare IN, NOT IN, EXISTS, and JOIN.
- Understand NULL-related behavior.
- Solve interview-oriented SQL problems.

---

# 1. Introduction

The **IN** operator checks whether a value exists in a list or the result of a subquery.

The **NOT IN** operator checks whether a value does **not** exist in that list.

These operators are commonly used with multi-row subqueries.

---

# 2. Why IN?

Suppose an online store wants to display customers who have placed orders.

Instead of joining tables, we can compare customer IDs returned by a subquery.

```sql
SELECT Name
FROM Customer
WHERE CustomerID IN
(
    SELECT CustomerID
    FROM Orders
);
```

---

# 3. Why NOT IN?

Display customers who have never placed an order.

```sql
SELECT Name
FROM Customer
WHERE CustomerID NOT IN
(
    SELECT CustomerID
    FROM Orders
);
```

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
|102      |3           |
+---------+------------+
```

---

# 5. Results

Using `IN`

```text
Alice
Carol
```

Using `NOT IN`

```text
Bob
```

---

# 6. Internal Working

```text
Execute Subquery
        │
Return List of Values
        │
Compare Outer Value
        │
IN  → Found?
NOT IN → Not Found?
        │
Return TRUE/FALSE
```

---

# 7. IN vs EXISTS

| Feature | IN | EXISTS |
|---------|----|---------|
|Compares values|✔|✖|
|Checks row existence|✖|✔|
|Good for small result sets|✔|✔|
|Stops after first match|✖|Usually ✔|

---

# 8. NULL Trap with NOT IN

One of the most common SQL interview questions.

Suppose the subquery returns:

```text
1
3
NULL
```

Query:

```sql
SELECT Name
FROM Customer
WHERE CustomerID NOT IN
(
    SELECT CustomerID
    FROM Orders
);
```

Because the list contains **NULL**, SQL cannot determine whether a value is "not equal" to NULL.

As a result, many DBMSs return **no rows**.

Safer alternative:

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

Customers with active loans.

## Telecom

Subscribers on selected plans.

## E-Commerce

Products belonging to selected categories.

## Hospital

Patients assigned to selected doctors.

---

# 10. Performance Notes

- Index comparison columns.
- IN works well for small lookup sets.
- EXISTS is often preferred for large correlated subqueries.
- Always review execution plans.

---

# 11. Common Mistakes

- Ignoring NULL values with NOT IN.
- Using IN when EXISTS is more suitable.
- Returning unnecessary columns in the subquery.
- Comparing incompatible data types.

---

# 12. Interview Questions

## Beginner

1. What does IN do?
2. What does NOT IN do?
3. Can IN work with subqueries?

## Intermediate

1. IN vs EXISTS?
2. Why can NOT IN fail with NULL values?
3. When would you choose EXISTS instead?

## Advanced

1. How does the optimizer execute IN?
2. Why is NOT EXISTS often preferred over NOT IN?
3. Explain NULL handling with NOT IN.

---

# 13. Practice

```sql
-- Customers with orders
SELECT Name
FROM Customer
WHERE CustomerID IN
(
SELECT CustomerID
FROM Orders
);

-- Customers without orders
SELECT Name
FROM Customer
WHERE CustomerID NOT IN
(
SELECT CustomerID
FROM Orders
);

-- Products in selected categories
SELECT ProductName
FROM Product
WHERE CategoryID IN
(
SELECT CategoryID
FROM Category
WHERE CategoryName IN ('Electronics','Books')
);
```

---

# Revision Notes

- IN checks membership in a list.
- NOT IN checks absence from a list.
- Both commonly use multi-row subqueries.
- Be careful with NULL values in NOT IN.
- NOT EXISTS is usually safer when NULLs are possible.

---

# Memory Trick

**IN = Inside the List**

**NOT IN = Outside the List**

---

# Final Takeaway

The IN and NOT IN operators provide a simple way to compare values against the results of a subquery. While IN is widely used for membership checks, NOT IN requires extra care because NULL values can produce unexpected results. In production systems and technical interviews, understanding when to replace NOT IN with NOT EXISTS is an important skill for writing correct and efficient SQL queries.
