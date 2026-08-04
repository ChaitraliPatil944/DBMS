# Lesson 241 - Complex Views

**Part:** Part 10 - Views

**Difficulty:** Intermediate → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 50–65 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand complex views.
- Create views using joins and aggregate functions.
- Learn why most complex views are not updatable.
- Explain internal DBMS execution.
- Solve interview-oriented questions on complex views.

---

# 1. Introduction

A **Complex View** is a view built using one or more advanced SQL features such as:

- Multiple tables (JOINs)
- Aggregate functions (`SUM`, `AVG`, `COUNT`)
- `GROUP BY`
- `HAVING`
- `DISTINCT`
- `UNION`

Unlike simple views, complex views often represent summarized or combined business data.

---

# 2. Why Use Complex Views?

Instead of writing long SQL queries repeatedly, a complex view stores the query definition and exposes a simplified interface.

Common use cases:

- Sales dashboards
- Monthly reports
- Department summaries
- Customer analytics

---

# 3. Syntax

```sql
CREATE VIEW DepartmentSalarySummary AS
SELECT DepartmentID,
       AVG(Salary) AS AverageSalary,
       COUNT(*) AS EmployeeCount
FROM Employee
GROUP BY DepartmentID;
```

Querying the view:

```sql
SELECT *
FROM DepartmentSalarySummary;
```

---

# 4. Join-Based View

```sql
CREATE VIEW CustomerOrders AS
SELECT c.CustomerID,
       c.Name,
       o.OrderID,
       o.Amount
FROM Customer c
JOIN Orders o
ON c.CustomerID = o.CustomerID;
```

---

# 5. Aggregate View

```sql
CREATE VIEW ProductSales AS
SELECT ProductID,
       SUM(Amount) AS TotalSales
FROM Orders
GROUP BY ProductID;
```

---

# 6. Internal Working

```text
User Query
      │
      ▼
Complex View
      │
Expand View Definition
      │
JOIN / GROUP BY / Aggregation
      │
Optimizer
      │
Execution Plan
      │
Base Tables
      │
Return Result
```

The optimizer treats the view definition as part of the original query and creates a single execution plan.

---

# 7. Updatability

Most complex views are **not updatable** because the DBMS cannot determine how changes should be applied to multiple rows or tables.

Generally non-updatable when using:

- JOIN
- GROUP BY
- Aggregate functions
- DISTINCT
- UNION

---

# 8. Advantages

- Simplifies reporting queries.
- Reuses complex SQL logic.
- Provides abstraction.
- Improves maintainability.
- Enhances security by exposing only required data.

---

# 9. Limitations

- Usually not updatable.
- Can become difficult to maintain if heavily nested.
- Performance depends on underlying query complexity.
- May execute slowly on very large datasets.

---

# 10. Real Project Examples

## Banking

Branch-wise total deposits.

## Telecom

Monthly recharge summary by plan.

## E-Commerce

Customer purchase history with product details.

## Hospital

Department-wise patient statistics.

---

# 11. Performance Notes

- Base table indexes are still used.
- Avoid unnecessary nested views.
- Review execution plans for expensive joins.
- Aggregate views may require sorting or hashing internally.

---

# 12. Common Mistakes

- Expecting JOIN views to be editable.
- Creating deeply nested view hierarchies.
- Assuming a view automatically improves performance.
- Forgetting that base table changes affect the view.

---

# 13. Interview Questions

## Beginner

1. What is a complex view?
2. How is it different from a simple view?
3. Can a complex view use joins?

## Intermediate

1. Why are aggregate views usually not updatable?
2. Complex view vs stored query?
3. Can indexes on base tables help?

## Advanced

1. How does the optimizer execute complex views?
2. Why can nested views hurt performance?
3. Explain view merging.

---

# 14. Practice

```sql
CREATE VIEW DepartmentSummary AS
SELECT DepartmentID,
       COUNT(*) AS Employees,
       AVG(Salary) AS AvgSalary
FROM Employee
GROUP BY DepartmentID;

SELECT *
FROM DepartmentSummary;

CREATE VIEW CustomerOrderDetails AS
SELECT c.Name,
       o.OrderID,
       o.Amount
FROM Customer c
JOIN Orders o
ON c.CustomerID = o.CustomerID;
```

---

# Revision Notes

- Complex views use joins or aggregations.
- Usually not updatable.
- Simplify reporting.
- Performance depends on underlying SQL.
- Base table indexes remain important.

---

# Memory Trick

**Simple View = One Table**

**Complex View = Many Tables or Aggregations**

---

# Final Takeaway

Complex views encapsulate sophisticated SQL involving joins, aggregations, and grouping into reusable virtual tables. They are invaluable for reporting, analytics, and business dashboards, but they rarely support direct updates because a single view row may represent data from multiple rows or tables. In interviews, remember that complex views improve readability and reuse, not raw performance, unless paired with technologies such as materialized or indexed views.
