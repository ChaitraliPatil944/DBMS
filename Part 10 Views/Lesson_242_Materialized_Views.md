# Lesson 242 - Materialized Views

**Part:** Part 10 - Views

**Difficulty:** Intermediate → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 50–65 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand what a materialized view is.
- Differentiate materialized views from simple views.
- Learn refresh mechanisms.
- Explain internal DBMS storage and execution.
- Answer interview questions on materialized views.

---

# 1. Introduction

A **Materialized View** is a database object that **stores the result of a query physically on disk**.

Unlike a simple view, which stores only the SQL definition, a materialized view stores the actual query results.

This provides much faster read performance for expensive queries.

---

# 2. Why Use Materialized Views?

Materialized views are useful when:

- Queries involve complex joins.
- Large aggregations are executed repeatedly.
- Reports are generated frequently.
- Real-time data is not always required.

The trade-off is additional storage and refresh overhead.

---

# 3. Simple View vs Materialized View

| Feature | Simple View | Materialized View |
|--------|-------------|-------------------|
|Stores query definition|✔|✔|
|Stores query results|✖|✔|
|Uses disk space|Minimal|Yes|
|Always latest data|✔|Only after refresh|
|Read performance|Depends on query|Usually much faster|

---

# 4. Syntax (Oracle Example)

```sql
CREATE MATERIALIZED VIEW MonthlySales
AS
SELECT ProductID,
       SUM(Amount) AS TotalSales
FROM Orders
GROUP BY ProductID;
```

Refreshing:

```sql
REFRESH MATERIALIZED VIEW MonthlySales;
```

> Syntax varies across database systems.

---

# 5. Internal Working

```text
Base Tables
      │
Execute Query
      │
Store Result
      │
Materialized View
      │
User Query
      │
Read Stored Data
```

Unlike ordinary views, the DBMS reads precomputed data instead of re-executing the full query every time.

---

# 6. Refresh Types

### Complete Refresh

Rebuilds the entire materialized view.

### Fast (Incremental) Refresh

Applies only the changes since the last refresh.

### On Demand

Refresh occurs only when requested.

### Scheduled Refresh

Refresh runs automatically at predefined intervals.

---

# 7. Advantages

- Faster reporting.
- Reduced execution time for complex queries.
- Lower CPU usage for repeated analytics.
- Excellent for dashboards and BI workloads.

---

# 8. Limitations

- Consumes storage.
- Data can become stale.
- Refresh operations may be expensive.
- Not supported identically by every DBMS.

---

# 9. Real Project Examples

## Banking

Daily branch transaction summaries.

## Telecom

Hourly recharge statistics.

## E-Commerce

Daily product sales dashboard.

## Hospital

Daily patient admission reports.

---

# 10. Performance Notes

- Best suited for read-heavy workloads.
- Fast refresh reduces maintenance cost.
- Indexes can be created on materialized views in many DBMSs.
- Balance refresh frequency with data freshness requirements.

---

# 11. Common Mistakes

- Assuming data updates automatically.
- Refreshing too frequently.
- Using materialized views for highly volatile data.
- Ignoring storage overhead.

---

# 12. Interview Questions

## Beginner

1. What is a materialized view?
2. How is it different from a simple view?
3. Does it store data?

## Intermediate

1. Why is it faster?
2. What is a refresh?
3. Complete vs fast refresh?

## Advanced

1. When would you choose a materialized view?
2. What are the trade-offs?
3. Can indexes improve materialized view performance?

---

# 13. Practice

```sql
CREATE MATERIALIZED VIEW ProductSalesSummary
AS
SELECT ProductID,
       SUM(Amount) AS TotalSales
FROM Orders
GROUP BY ProductID;

SELECT *
FROM ProductSalesSummary;
```

---

# Revision Notes

- Materialized views store query results.
- Improve read performance.
- Require refreshes.
- Consume storage.
- Ideal for reporting and analytics.

---

# Memory Trick

**Materialized = Material Stored**

If it's materialized, the result already exists on disk.

---

# Final Takeaway

Materialized views trade storage and refresh overhead for significantly faster query performance. They are especially valuable in reporting systems, business intelligence platforms, and data warehouses where expensive aggregations are queried repeatedly. In interviews, remember the key distinction: a simple view stores only the SQL definition, while a materialized view stores the computed result set and must be refreshed to stay synchronized with its base tables.
