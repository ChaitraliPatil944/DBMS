# Lesson 250 - Query Performance

**Part:** Part 11 - Indexing

**Difficulty:** Intermediate → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐ (Very High)  
**Estimated Reading Time:** 75 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand how the DBMS measures query performance.
- Identify common causes of slow queries.
- Learn optimization techniques.
- Read basic execution plans.
- Answer performance-related interview questions.

---

# 1. Introduction

**Query Performance** is the measure of how efficiently a database executes an SQL statement.

A fast query minimizes:

- CPU usage
- Memory usage
- Disk I/O
- Network transfer
- Execution time

Good performance comes from good schema design, proper indexing, efficient SQL, and an intelligent query optimizer.

---

# 2. Query Life Cycle

```text
SQL Query
    │
Parser
    │
Optimizer
    │
Execution Plan
    │
Storage Engine
    │
Disk / Memory
    │
Return Result
```

The optimizer selects what it estimates to be the lowest-cost execution plan.

---

# 3. Why Queries Become Slow

- Missing indexes
- Full table scans
- Returning unnecessary columns
- Too many joins
- Poor WHERE conditions
- Functions on indexed columns
- Large sorts
- Outdated statistics

---

# 4. Full Table Scan vs Index Scan

## Full Table Scan

```text
Query
 │
Read every row
 │
Return matching rows
```

Complexity (conceptually):

```
O(n)
```

## Index Scan

```text
Query
 │
Use Index
 │
Locate matching rows
 │
Return Result
```

Typical complexity with a B+ Tree:

```
O(log n)
```

---

# 5. Reading Execution Plans

Example:

```sql
EXPLAIN
SELECT *
FROM Employee
WHERE EmployeeID = 100;
```

Common operators:

| Operator | Meaning |
|----------|---------|
| Table Scan | Reads entire table |
| Index Scan | Scans index entries |
| Index Seek | Direct index lookup |
| Nested Loop Join | Row-by-row join |
| Hash Join | Join using hash tables |
| Sort | Orders rows |
| Aggregate | Computes SUM, AVG, COUNT, etc. |

---

# 6. SQL Optimization Tips

## Select only required columns

❌

```sql
SELECT *
FROM Customer;
```

✅

```sql
SELECT CustomerID, Name
FROM Customer;
```

---

## Filter early

```sql
SELECT *
FROM Orders
WHERE CustomerID = 101;
```

---

## Use indexes wisely

```sql
CREATE INDEX IX_Order_Customer
ON Orders(CustomerID);
```

---

## Avoid functions on indexed columns

❌

```sql
WHERE YEAR(OrderDate)=2026
```

✅

```sql
WHERE OrderDate >= '2026-01-01'
AND OrderDate < '2027-01-01'
```

---

# 7. Internal Optimizer Decisions

The optimizer estimates:

- Number of rows
- Index selectivity
- Join cost
- Disk I/O
- CPU cost
- Memory usage

It then chooses the lowest estimated cost plan.

---

# 8. Real Project Examples

### Banking

Fast account lookup using indexed AccountNumber.

### Telecom

Retrieve subscriber information by MobileNumber.

### E-Commerce

Optimize product search using CategoryID and Price indexes.

### Hospital

Quickly retrieve patient history by PatientID.

---

# 9. Performance Best Practices

- Create indexes on frequently filtered columns.
- Keep statistics updated.
- Avoid unnecessary indexes.
- Use composite indexes where appropriate.
- Review execution plans regularly.
- Limit result sets with pagination.

---

# 10. Common Mistakes

- Using SELECT *
- Ignoring execution plans
- Indexing every column
- Writing non-sargable predicates
- Using OR excessively without analysis
- Returning huge result sets unnecessarily

---

# 11. Interview Insights ⭐

## What is a Query Optimizer?

A DBMS component that evaluates different execution strategies and selects the lowest estimated cost plan.

---

## What is a SARGable query?

A query where the DBMS can efficiently use an index.

Example:

✅

```sql
WHERE Salary > 50000
```

❌

```sql
WHERE Salary + 1000 > 50000
```

---

## Why does the optimizer ignore an index?

Possible reasons:

- Table is very small.
- Low selectivity.
- Outdated statistics.
- Full scan estimated to be cheaper.

---

## Difference between Index Scan and Index Seek?

**Index Seek**

- Directly navigates to matching rows.
- Highly efficient.

**Index Scan**

- Reads many index entries sequentially.
- Faster than a table scan but more work than a seek.

---

# 12. Interview Traps 🚨

### Trap 1

> More indexes always mean faster queries.

❌ False.

Too many indexes slow writes and increase maintenance.

---

### Trap 2

> EXPLAIN executes the query.

❌ Generally, it shows the execution plan without executing the full query (behavior varies by DBMS).

---

### Trap 3

> SELECT * is always acceptable.

❌ It increases I/O and may prevent efficient index usage.

---

# 13. Practice

```sql
EXPLAIN
SELECT Name
FROM Customer
WHERE CustomerID = 10;

EXPLAIN
SELECT *
FROM Orders
WHERE OrderDate >= '2026-01-01';

EXPLAIN
SELECT ProductName
FROM Product
WHERE CategoryID = 5
AND Price > 1000;
```

---

# Revision Notes

- Analyze execution plans.
- Prefer Index Seek over Table Scan.
- Avoid SELECT *.
- Keep statistics updated.
- Write SARGable queries.

---

# Memory Trick

**FAST**

**F** → Filter early

**A** → Analyze execution plan

**S** → SARGable predicates

**T** → Target indexes wisely

---

# Final Takeaway

Excellent query performance is achieved by combining efficient SQL, appropriate indexing, accurate statistics, and a capable query optimizer. The best-performing queries minimize unnecessary work by reducing disk I/O, avoiding full table scans, and allowing the optimizer to choose efficient execution plans. Performance tuning is an ongoing process of measuring, analyzing, and refining database workloads.

---

# Quick Interview Cheat Sheet

| Question | Answer |
|----------|--------|
| First step in tuning? | Examine execution plan |
| Best operator? | Index Seek |
| Worst common operator? | Full Table Scan (for large tables) |
| What is SARGable? | Predicate that can use an index |
| Why ignore an index? | Optimizer estimates a scan is cheaper |
| Biggest beginner mistake? | SELECT * and missing indexes |
