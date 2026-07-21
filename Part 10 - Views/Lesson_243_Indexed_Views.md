# Lesson 243 - Indexed Views

**Part:** Part 10 - Views

**Difficulty:** Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 50–65 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand what an indexed view is.
- Differentiate indexed views from simple and materialized views.
- Learn how indexed views improve query performance.
- Explain internal DBMS execution.
- Solve interview-oriented questions on indexed views.

---

# 1. Introduction

An **Indexed View** is a view that has one or more indexes created on it.

Unlike a normal view, an indexed view stores its computed result physically after creating a unique clustered index (SQL Server). The DBMS keeps the indexed view synchronized with its base tables.

Indexed views are primarily designed to accelerate complex queries involving joins and aggregations.

---

# 2. Why Use Indexed Views?

Indexed views are useful when:

- Expensive aggregation queries run frequently.
- Dashboards repeatedly execute the same reports.
- Read performance is more important than write speed.
- Query results change less frequently than they are read.

---

# 3. Simple View vs Materialized View vs Indexed View

| Feature | Simple View | Materialized View | Indexed View |
|---------|-------------|-------------------|--------------|
|Stores data|✖|✔|✔|
|Indexes allowed on stored result|Base tables only|Usually yes|Yes|
|Automatic maintenance|N/A|Depends on refresh|Maintained automatically|
|Read performance|Normal|High|Very High|
|Write overhead|Low|Refresh cost|Higher due to index maintenance|

---

# 4. Example (SQL Server)

```sql
CREATE VIEW SalesSummary
WITH SCHEMABINDING
AS
SELECT ProductID,
       COUNT_BIG(*) AS OrderCount,
       SUM(Amount) AS TotalSales
FROM dbo.Orders
GROUP BY ProductID;
GO

CREATE UNIQUE CLUSTERED INDEX IX_SalesSummary
ON SalesSummary(ProductID);
```

> Exact syntax and support vary across DBMS products.

---

# 5. Internal Working

```text
Base Tables
      │
Compute View
      │
Store Result
      │
Create Index
      │
User Query
      │
Use Indexed View
      │
Return Result
```

When eligible, the optimizer may use the indexed view instead of recomputing the original query.

---

# 6. Advantages

- Excellent performance for repeated analytical queries.
- Reduces repeated aggregations.
- Optimizer may rewrite queries automatically.
- Useful in reporting and BI systems.

---

# 7. Limitations

- Additional storage required.
- Slower INSERT, UPDATE, and DELETE operations.
- Creation rules are restrictive.
- Not supported in the same way by every DBMS.

---

# 8. Real Project Examples

## Banking

Daily branch transaction summaries.

## Telecom

Network usage statistics by region.

## E-Commerce

Product sales summaries.

## Hospital

Department-wise treatment statistics.

---

# 9. Performance Notes

- Best for read-heavy workloads.
- Base table modifications also update the indexed view.
- Proper indexing strategy remains essential.
- Monitor write overhead before deployment.

---

# 10. Common Mistakes

- Assuming every DBMS supports indexed views identically.
- Using indexed views for highly volatile tables.
- Ignoring maintenance cost during writes.
- Creating unnecessary indexed views.

---

# 11. Interview Questions

## Beginner

1. What is an indexed view?
2. How is it different from a simple view?
3. Does it store data?

## Intermediate

1. Why is it faster?
2. Why are writes slower?
3. What is SCHEMABINDING?

## Advanced

1. How does the optimizer use indexed views?
2. Indexed view vs materialized view?
3. When should indexed views be avoided?

---

# 12. Practice

```sql
-- Create a reporting view
CREATE VIEW ProductSales
AS
SELECT ProductID,
       SUM(Amount) AS TotalSales
FROM Orders
GROUP BY ProductID;

-- Create an index where supported by the DBMS.
```

---

# Revision Notes

- Indexed views store computed data with indexes.
- Excellent for repeated reporting queries.
- Increase storage and write cost.
- Optimizer can leverage them automatically.
- Support depends on the database platform.

---

# Memory Trick

**Indexed View = Stored View + Index**

Think of it as a precomputed result with a fast lookup structure.

---

# Final Takeaway

Indexed views combine the benefits of stored query results and indexing to deliver exceptional performance for recurring analytical workloads. They accelerate complex joins and aggregations but introduce additional storage and maintenance overhead whenever the underlying data changes. In interviews, remember that indexed views are a performance optimization for read-heavy systems, not a universal replacement for well-designed tables and indexes.
