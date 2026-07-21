# Lesson 230 - CROSS JOIN

**Part:** Part 8 - Joins

**Difficulty:** Beginner → Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐☆  
**Estimated Reading Time:** 35–45 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand what a CROSS JOIN is.
- Explain the Cartesian Product.
- Identify when CROSS JOIN should and should not be used.
- Understand its internal execution.
- Solve interview questions related to CROSS JOIN.

---

# 1. Introduction

A **CROSS JOIN** returns the **Cartesian Product** of two tables.

Every row from the first table is combined with **every row** from the second table.

Unlike other joins, **no matching condition is required**.

---

# 2. Why CROSS JOIN?

Sometimes applications need every possible combination.

Examples include:

- Product × Color combinations
- Product × Size combinations
- Employee × Shift schedules
- Student × Subject assignments

---

# 3. Real-World Analogy

Imagine:

3 Shirt Colors

- Red
- Blue
- Black

4 Sizes

- S
- M
- L
- XL

Possible combinations

```
3 × 4 = 12
```

A CROSS JOIN produces these combinations automatically.

---

# 4. Sample Tables

### Colors

```text
+---------+
|Color    |
+---------+
|Red      |
|Blue     |
|Black    |
+---------+
```

### Sizes

```text
+------+
|Size  |
+------+
|S     |
|M     |
|L     |
+------+
```

---

# 5. Syntax

```sql
SELECT Color,
       Size
FROM Colors
CROSS JOIN Sizes;
```

---

# 6. Result

```text
Red     S
Red     M
Red     L

Blue    S
Blue    M
Blue    L

Black   S
Black   M
Black   L
```

Total Rows

```
3 × 3 = 9
```

---

# 7. Internal Working

```
Read Table A
      │
For Every Row
      │
Read Every Row of Table B
      │
Create Combination
      │
Return All Combinations
```

Approximate Complexity

```
Rows(A) × Rows(B)
```

---

# 8. CROSS JOIN vs INNER JOIN

| Feature | INNER JOIN | CROSS JOIN |
|---------|------------|------------|
|Requires ON clause|✔|✖|
|Returns matching rows|✔|✖|
|Returns every combination|✖|✔|

---

# 9. Accidental CROSS JOIN

One of the most common SQL mistakes.

```sql
SELECT *
FROM Customer,
     Orders;
```

or

```sql
SELECT *
FROM Customer
JOIN Orders;
```

(without an ON clause in DBMSs that allow it)

This may create millions of unwanted rows.

---

# 10. Real Project Examples

## E-Commerce

Generate every Product × Size × Color combination.

## Banking

Generate branch × audit schedule combinations.

## Telecom

Generate SIM plans × regions.

## Education

Generate student × examination slot mappings.

---

# 11. Performance Notes

- CROSS JOIN grows rapidly with table size.
- Avoid on large tables unless necessary.
- Always estimate output row count before execution.
- Use filtering after CROSS JOIN only when required.

---

# 12. Common Mistakes

- Forgetting the JOIN condition and creating a Cartesian Product.
- Using CROSS JOIN instead of INNER JOIN.
- Running CROSS JOIN on large production tables.
- Ignoring exponential growth in result size.

---

# 13. Interview Questions

## Beginner

1. What is a CROSS JOIN?
2. What is a Cartesian Product?
3. Does CROSS JOIN require an ON clause?

## Intermediate

1. How many rows will a CROSS JOIN return?
2. When is CROSS JOIN useful?
3. Why is CROSS JOIN dangerous?

## Advanced

1. How does the optimizer execute CROSS JOIN?
2. How can accidental CROSS JOINs affect performance?
3. Give real-world use cases for CROSS JOIN.

---

# 14. Practice

```sql
SELECT *
FROM Colors
CROSS JOIN Sizes;

SELECT ProductName,
       ColorName
FROM Product
CROSS JOIN Color;

SELECT StudentName,
       SubjectName
FROM Student
CROSS JOIN Subject;
```

---

# Revision Notes

- CROSS JOIN returns every possible combination.
- No ON clause is required.
- Output rows = Rows(Table A) × Rows(Table B).
- Also known as the Cartesian Product.
- Can produce extremely large result sets.

---

# Memory Trick

**CROSS = Combine Everything**

Every row meets every other row.

---

# Final Takeaway

CROSS JOIN is the simplest yet potentially most expensive join because it creates every possible row combination between two tables. Although used less frequently than INNER or LEFT JOIN, it has valuable applications in scheduling, product configuration, testing, and data generation. Interviewers commonly use CROSS JOIN to test whether candidates understand Cartesian Products and can recognize accidental joins caused by missing join conditions.
