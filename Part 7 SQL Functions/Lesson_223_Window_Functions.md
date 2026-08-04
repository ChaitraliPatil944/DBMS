# Lesson 223 - Window Functions

**Part:** Part 7 - SQL Functions

**Difficulty:** Intermediate → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 45–60 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand what Window Functions are.
- Explain the purpose of the OVER() clause.
- Use PARTITION BY and ORDER BY with window functions.
- Differentiate window functions from aggregate functions.
- Build running totals, rankings, and moving calculations.
- Solve common interview questions involving window functions.

---

# 1. Introduction

A **Window Function** performs calculations across a set of rows related to the current row **without collapsing the result into a single row**.

Unlike aggregate functions, window functions preserve every row.

---

# 2. Aggregate vs Window Functions

Aggregate Function

```sql
SELECT Department,
       AVG(Salary)
FROM Employee
GROUP BY Department;
```

Returns one row per department.

Window Function

```sql
SELECT Name,
       Department,
       Salary,
       AVG(Salary) OVER(PARTITION BY Department)
FROM Employee;
```

Returns every employee along with the department average.

---

# 3. Why Window Functions?

Imagine an online shopping website.

You need to display:

- Customer rank by spending
- Running sales total
- Previous order amount
- Next delivery date

Traditional GROUP BY cannot solve these while keeping all rows.

---

# 4. Anatomy of a Window Function

```sql
Function(...)
OVER(
PARTITION BY ...
ORDER BY ...
)
```

Execution Flow

```
Read Table
    │
Partition Rows
    │
Sort Each Partition
    │
Apply Window Function
    │
Return Every Row
```

---

# 5. OVER()

OVER() defines the window on which the calculation is performed.

```sql
SELECT Salary,
AVG(Salary) OVER()
FROM Employee;
```

Computes the average salary for every row.

---

# 6. PARTITION BY

PARTITION BY divides rows into logical groups.

```sql
SELECT Name,
Department,
Salary,
AVG(Salary)
OVER(PARTITION BY Department)
FROM Employee;
```

Each department has its own window.

---

# 7. ORDER BY

ORDER BY defines processing order inside the window.

```sql
SUM(Salary)
OVER(ORDER BY Salary)
```

Useful for cumulative calculations.

---

# 8. Running Total

```sql
SELECT OrderID,
Amount,
SUM(Amount)
OVER(ORDER BY OrderDate)
AS RunningTotal
FROM Orders;
```

Example

```
100
250
450
700
```

Each row includes all previous values.

---

# 9. Ranking Functions

## ROW_NUMBER()

Unique sequential number.

```sql
ROW_NUMBER()
OVER(ORDER BY Salary DESC)
```

---

## RANK()

Equal values receive the same rank.

Ranks may skip numbers.

---

## DENSE_RANK()

Equal values receive the same rank.

Ranks never skip numbers.

---

# 10. LAG() and LEAD()

LAG()

Returns previous row.

```sql
LAG(Salary)
OVER(ORDER BY Salary)
```

LEAD()

Returns next row.

```sql
LEAD(Salary)
OVER(ORDER BY Salary)
```

Useful for trend analysis.

---

# 11. FIRST_VALUE() and LAST_VALUE()

Retrieve the first or last value within a window.

Frequently used in reporting dashboards.

---

# 12. Internal Working

```
Table Scan
      │
Create Window
      │
Partition Rows
      │
Sort Rows
      │
Apply Window Function
      │
Return Original Rows
```

The original rows remain unchanged.

---

# 13. Real Project Examples

## Banking

- Customer transaction ranking
- Running account balance

## Telecom

- Monthly usage trends
- Previous recharge amount

## E-Commerce

- Top-selling products
- Running sales dashboard

## HR

- Employee salary ranking
- Department average salary

---

# 14. Performance Notes

- ORDER BY inside OVER() may require sorting.
- PARTITION BY creates logical groups and can increase memory usage.
- Indexes on partitioning and ordering columns improve performance.
- Large windows can become expensive.

---

# 15. Common Mistakes

- Confusing GROUP BY with window functions.
- Forgetting the OVER() clause.
- Using incorrect ORDER BY.
- Assuming RANK() and DENSE_RANK() behave the same.
- Ignoring sorting costs.

---

# 16. Interview Questions

## Beginner

1. What is a window function?
2. Why is OVER() required?
3. Difference between GROUP BY and window functions?

## Intermediate

1. Explain PARTITION BY.
2. Difference between ROW_NUMBER(), RANK(), and DENSE_RANK().
3. What is a running total?

## Advanced

1. How are window functions executed internally?
2. Why are window functions slower than simple SELECT statements?
3. How can indexes improve window queries?
4. Explain window frames (ROWS vs RANGE).

---

# 17. Practice

```sql
SELECT Name,
Salary,
ROW_NUMBER()
OVER(ORDER BY Salary DESC)
FROM Employee;

SELECT Department,
AVG(Salary)
OVER(PARTITION BY Department)
FROM Employee;

SELECT Amount,
SUM(Amount)
OVER(ORDER BY OrderDate)
FROM Orders;

SELECT Salary,
LAG(Salary)
OVER(ORDER BY Salary)
FROM Employee;
```

---

# Revision Notes

- Window functions keep every row.
- OVER() defines the processing window.
- PARTITION BY creates groups.
- ORDER BY controls calculation order.
- Common functions include ROW_NUMBER, RANK, DENSE_RANK, LAG, LEAD, FIRST_VALUE, LAST_VALUE, and running aggregates.

---

# Memory Trick

**OPRRLF**

- O → OVER
- P → PARTITION BY
- R → ROW_NUMBER
- R → RANK
- L → LAG / LEAD
- F → FIRST_VALUE / LAST_VALUE

---

# Final Takeaway

Window functions are among the most powerful SQL features and are heavily used in analytics, reporting, and dashboard development. They allow calculations across related rows while preserving the original dataset, making them indispensable for modern SQL development and one of the most frequently tested topics in technical interviews.
