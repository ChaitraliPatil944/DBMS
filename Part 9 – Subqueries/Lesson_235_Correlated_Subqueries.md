# Lesson 235 - Correlated Subqueries

**Part:** Part 9 - Subqueries

**Difficulty:** Intermediate → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 50–60 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand correlated subqueries.
- Differentiate correlated and uncorrelated subqueries.
- Explain internal DBMS execution.
- Identify performance implications.
- Rewrite correlated subqueries using JOINs when appropriate.
- Solve interview-oriented SQL problems.

---

# 1. Introduction

A **Correlated Subquery** is a subquery that **depends on the outer query**.

Unlike a scalar (uncorrelated) subquery, it cannot execute independently because it references columns from the outer query.

The inner query is evaluated repeatedly, typically once for each row processed by the outer query.

---

# 2. Why Correlated Subqueries?

Use correlated subqueries when the comparison value is different for every outer row.

Example:

> Find employees whose salary is greater than the average salary of **their own department**.

Each department has a different average salary.

---

# 3. Syntax

```sql
SELECT e1.Name,
       e1.Salary
FROM Employee e1
WHERE e1.Salary >
(
    SELECT AVG(e2.Salary)
    FROM Employee e2
    WHERE e2.DepartmentID = e1.DepartmentID
);
```

The inner query references `e1.DepartmentID`, making it correlated.

---

# 4. Sample Data

```text
Employee
+----+-------+--------+--------------+
|ID  |Name   |Salary  |DepartmentID  |
+----+-------+--------+--------------+
|1   |Alice  |50000   |10            |
|2   |Bob    |60000   |10            |
|3   |Carol  |70000   |20            |
|4   |David  |65000   |20            |
+----+-------+--------+--------------+
```

---

# 5. Execution Flow

```text
Outer Query Reads Row
        │
Pass DepartmentID
        │
Execute Inner Query
        │
Return Department Average
        │
Compare Salary
        │
Repeat For Next Row
```

---

# 6. Internal Working

```text
Read Employee Row
        │
Run Inner Query
        │
Calculate Matching Result
        │
Return Decision
        │
Repeat Until End
```

Unlike uncorrelated subqueries, the optimizer generally cannot evaluate the inner query just once because the input changes for every outer row.

---

# 7. Correlated vs Uncorrelated

| Feature | Correlated | Uncorrelated |
|---------|------------|--------------|
|Depends on outer query|✔|✖|
|Runs once|✖|Usually ✔|
|Runs per outer row|✔|✖|
|Performance|Usually slower|Usually faster|

---

# 8. Real Project Examples

## Banking

Accounts above the average balance of their branch.

## Telecom

Subscribers whose monthly usage exceeds the average usage for their plan.

## E-Commerce

Products priced above the average price in their category.

## Hospital

Doctors earning more than the average salary in their department.

---

# 9. Performance Notes

- May execute the inner query many times.
- Index columns used in the correlation predicate.
- Consider rewriting with JOINs or Common Table Expressions for large datasets.
- Always compare execution plans.

---

# 10. Common Mistakes

- Confusing correlated and scalar subqueries.
- Returning multiple rows when a single value is expected.
- Ignoring performance on large tables.
- Missing indexes on correlated columns.

---

# 11. JOIN Alternative

```sql
SELECT e.Name,
       e.Salary
FROM Employee e
JOIN (
    SELECT DepartmentID,
           AVG(Salary) AS AvgSalary
    FROM Employee
    GROUP BY DepartmentID
) d
ON e.DepartmentID = d.DepartmentID
WHERE e.Salary > d.AvgSalary;
```

This approach can be more efficient for large datasets.

---

# 12. Interview Questions

## Beginner

1. What is a correlated subquery?
2. Why can't it run independently?
3. How is it different from a scalar subquery?

## Intermediate

1. Why is it usually slower?
2. When should you use a correlated subquery?
3. Can it be rewritten using JOINs?

## Advanced

1. How does the optimizer execute correlated subqueries?
2. What indexes improve performance?
3. When would you prefer a window function instead?

---

# 13. Practice

```sql
-- Products above category average
SELECT p1.ProductName,
       p1.Price
FROM Product p1
WHERE p1.Price >
(
SELECT AVG(p2.Price)
FROM Product p2
WHERE p2.CategoryID = p1.CategoryID
);

-- Employees above department average
SELECT e1.Name,
       e1.Salary
FROM Employee e1
WHERE e1.Salary >
(
SELECT AVG(e2.Salary)
FROM Employee e2
WHERE e2.DepartmentID = e1.DepartmentID
);
```

---

# Revision Notes

- Correlated subqueries depend on the outer query.
- The inner query is evaluated repeatedly.
- Useful for row-by-row comparisons.
- May be slower than JOIN-based alternatives.

---

# Memory Trick

**Correlated = Connected**

The inner query cannot live without the outer query.

---

# Final Takeaway

Correlated subqueries are powerful because they evaluate data in the context of each row processed by the outer query. This makes them ideal for solving group-wise comparison problems, but it also makes them more expensive than uncorrelated subqueries. In interviews, you should be able to explain not only the syntax, but also why correlated subqueries are slower and how they can often be rewritten using JOINs or window functions for better performance.
