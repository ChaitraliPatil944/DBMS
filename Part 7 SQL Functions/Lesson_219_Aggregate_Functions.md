# Lesson 219 - Aggregate Functions

**Part:** Part 7 - SQL Functions

**Difficulty:** Beginner → Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 20–30 Minutes

---

# Learning Objectives

By the end of this lesson, you will be able to:

- Understand what SQL Aggregate Functions are.
- Explain how aggregate functions work internally.
- Differentiate COUNT(*), COUNT(column), and COUNT(DISTINCT column).
- Understand NULL handling in aggregate functions.
- Use GROUP BY and HAVING correctly.
- Apply aggregate functions in real-world projects.
- Answer common interview questions confidently.

---

# 1. Introduction

Aggregate functions perform calculations on **multiple rows** and return **a single result**.

Unlike scalar functions, which process one row at a time, aggregate functions summarize an entire dataset or group of rows.

Examples include:

- COUNT()
- SUM()
- AVG()
- MIN()
- MAX()

---

# 2. Why Do We Need Aggregate Functions?

Imagine an e-commerce company with millions of orders.

Instead of manually calculating:

- Total Orders
- Total Revenue
- Average Order Value
- Highest Sale

SQL can calculate them instantly using aggregate functions.

---

# 3. Real-Life Analogy

Imagine a classroom.

Instead of checking every student's marks individually, the teacher asks:

- Highest marks?
- Lowest marks?
- Average marks?
- Total students?

The teacher summarizes the entire class.

Aggregate functions do exactly that.

---

# 4. Common Aggregate Functions

| Function | Purpose |
|----------|---------|
| COUNT() | Counts rows |
| SUM() | Adds numeric values |
| AVG() | Finds average |
| MIN() | Finds minimum value |
| MAX() | Finds maximum value |

---

# 5. Sample Table

```sql
Employee

+----+--------+--------+
|ID  |Name    |Salary  |
+----+--------+--------+
|1   |Amit    |50000   |
|2   |Neha    |60000   |
|3   |Raj     |55000   |
|4   |Priya   |NULL    |
+----+--------+--------+
```

---

# 6. COUNT()

```sql
SELECT COUNT(*) FROM Employee;
```

Returns:

```
4
```

### COUNT(column)

```sql
SELECT COUNT(Salary) FROM Employee;
```

Returns:

```
3
```

NULL values are ignored.

### COUNT(DISTINCT)

```sql
SELECT COUNT(DISTINCT Salary)
FROM Employee;
```

Counts only unique non-NULL values.

---

# Interview Focus

**COUNT(*)**

- Counts every row.

**COUNT(column)**

- Counts only non-NULL values.

**COUNT(DISTINCT column)**

- Counts unique non-NULL values.

---

# 7. SUM()

```sql
SELECT SUM(Salary)
FROM Employee;
```

Result:

```
165000
```

NULL values are ignored.

---

# 8. AVG()

```sql
SELECT AVG(Salary)
FROM Employee;
```

Result:

```
55000
```

AVG ignores NULL values.

---

# 9. MIN() and MAX()

```sql
SELECT MIN(Salary), MAX(Salary)
FROM Employee;
```

Result

```
50000
60000
```

---

# 10. GROUP BY

Aggregate functions become more powerful when combined with GROUP BY.

Example:

```sql
SELECT Department,
       AVG(Salary)
FROM Employee
GROUP BY Department;
```

ASCII Flow

```
Rows
 │
 ▼
Group by Department
 │
 ▼
AVG()
 │
 ▼
One Result Per Department
```

---

# 11. HAVING

WHERE filters rows.

HAVING filters groups.

```sql
SELECT Department,
       AVG(Salary)
FROM Employee
GROUP BY Department
HAVING AVG(Salary) > 50000;
```

Execution Order

1. FROM
2. WHERE
3. GROUP BY
4. Aggregate Functions
5. HAVING
6. SELECT
7. ORDER BY

---

# 12. How SQL Executes Aggregate Functions

```
Table Scan
     │
Read Rows
     │
Ignore NULL (where applicable)
     │
Compute Aggregate
     │
Return Single Result
```

---

# 13. Real Project Examples

## Banking

- Total balance
- Average account balance
- Maximum transaction amount

## E-Commerce

- Daily revenue
- Number of orders
- Average cart value

## Telecom

- Average call duration
- Total recharge amount
- Maximum data usage

---

# 14. Performance Notes

- COUNT(*) is highly optimized by most DBMS engines.
- Indexes can improve aggregate queries.
- GROUP BY on large datasets may require sorting or hashing.

---

# 15. Common Mistakes

- Using WHERE with aggregate values instead of HAVING.
- Forgetting GROUP BY for non-aggregated columns.
- Assuming COUNT(column) counts NULL values.
- Mixing aggregated and non-aggregated columns incorrectly.

---

# 16. Interview Questions

## Beginner

1. What are aggregate functions?
2. Name five aggregate functions.
3. Does AVG() ignore NULL values?
4. Difference between COUNT(*) and COUNT(column)?

## Intermediate

1. COUNT(*) vs COUNT(1)?
2. Why does SUM() ignore NULL?
3. Difference between WHERE and HAVING?
4. Can aggregate functions be nested?

## Advanced

1. How does SQL internally execute GROUP BY?
2. Why can GROUP BY become expensive?
3. How do indexes affect aggregate queries?
4. Explain hash aggregation vs sort aggregation.

---

# 17. Practice

```sql
SELECT COUNT(*) FROM Orders;

SELECT SUM(Amount) FROM Orders;

SELECT AVG(Amount) FROM Orders;

SELECT Department,
       MAX(Salary)
FROM Employee
GROUP BY Department;
```

---

# Revision Notes

- Aggregate functions summarize data.
- NULL values are ignored except by COUNT(*).
- GROUP BY creates groups.
- HAVING filters groups.
- One aggregate result per group.

---

# Memory Trick

**CSAAM**

- C → COUNT
- S → SUM
- A → AVG
- A → Aggregate after GROUP BY
- M → MIN/MAX

---

# Final Takeaway

Aggregate functions are among the most frequently used SQL features in interviews and production systems. Mastering them requires more than memorizing syntax—you should understand NULL handling, execution order, grouping behavior, and performance implications, because these are the areas interviewers commonly explore.
