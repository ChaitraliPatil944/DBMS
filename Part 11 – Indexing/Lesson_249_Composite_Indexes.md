# Lesson 249 - Composite Indexes

**Part:** Part 11 - Indexing

**Difficulty:** Intermediate → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐ (Very High)  
**Estimated Reading Time:** 70 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand composite (multi-column) indexes.
- Learn the Leftmost Prefix Rule.
- Identify when composite indexes improve performance.
- Avoid common indexing mistakes.
- Answer interview questions confidently.

---

# 1. Introduction

A **Composite Index** (also called a **Multi-Column Index**) is an index built on **two or more columns**.

Instead of indexing each column separately, the DBMS stores them together in a defined order.

Example:

```sql
CREATE INDEX IX_Emp_Department_Salary
ON Employee(DepartmentID, Salary);
```

The **order of columns matters**.

---

# 2. Why Composite Indexes?

Suppose this query runs frequently:

```sql
SELECT *
FROM Employee
WHERE DepartmentID = 10
AND Salary > 60000;
```

A composite index on `(DepartmentID, Salary)` allows the DBMS to locate matching rows much faster than scanning the table.

---

# 3. Internal Structure

```text
Composite Index

DepartmentID | Salary
-------------+--------
10           | 50000
10           | 65000
10           | 80000
20           | 55000
20           | 70000
```

Keys are sorted first by **DepartmentID**, then by **Salary**.

---

# 4. Leftmost Prefix Rule ⭐

The most important interview concept.

Index:

```text
(DepartmentID, Salary, EmployeeID)
```

Efficiently supports:

```sql
WHERE DepartmentID = 10

WHERE DepartmentID = 10
AND Salary > 50000

WHERE DepartmentID = 10
AND Salary = 60000
AND EmployeeID = 5
```

Not efficiently supported:

```sql
WHERE Salary > 50000

WHERE EmployeeID = 5
```

The DBMS generally starts searching from the **leftmost indexed column**.

---

# 5. Internal Working

```text
Query
 │
Check Predicate
 │
Match Leftmost Column?
 │
Yes
 │
Traverse B+ Tree
 │
Locate Matching Keys
 │
Return Rows
```

If the leftmost prefix is missing, the optimizer may prefer a table scan or another index.

---

# 6. Composite vs Single-Column Indexes

| Feature | Single Index | Composite Index |
|---------|--------------|-----------------|
|Indexed columns|One|Multiple|
|Column order matters|No|Yes|
|Optimized for multi-column filters|Limited|Excellent|
|Storage|Lower|Higher|

---

# 7. Advantages

- Faster multi-column filtering.
- Better join performance.
- Can reduce sorting.
- May become a covering index.

---

# 8. Limitations

- Larger index size.
- Extra write overhead.
- Wrong column order reduces usefulness.
- Does not replace every single-column index.

---

# 9. Choosing Column Order

General guideline:

1. Frequently filtered columns.
2. Highly selective columns.
3. Frequently used in joins.
4. Frequently used in sorting.

Always validate with execution plans and workload patterns.

---

# 10. Real Project Examples

### Banking

(AccountNumber, BranchID)

### Telecom

(CircleID, MobileNumber)

### E-Commerce

(CategoryID, Price)

### Hospital

(DepartmentID, DoctorID)

---

# 11. Performance Notes

- Composite indexes reduce repeated index lookups.
- The optimizer may use only the leading columns.
- Covering composite indexes can eliminate table lookups.
- Avoid creating many overlapping indexes.

---

# 12. Interview Insights ⭐

## What is the Leftmost Prefix Rule?

The DBMS can efficiently use the index starting from the first indexed column and then continue to subsequent columns.

---

## Does column order matter?

✅ Yes.

`(DepartmentID, Salary)` is different from `(Salary, DepartmentID)`.

---

## Can one composite index replace multiple indexes?

Sometimes, but not always. Analyze actual query patterns before removing existing indexes.

---

## What is an overlapping index?

Two indexes sharing the same leading columns, for example:

```text
(DepartmentID)

(DepartmentID, Salary)
```

The longer index may make the shorter one unnecessary in some workloads.

---

# 13. Interview Traps 🚨

### Trap 1

> Composite indexes work regardless of column order.

❌ Incorrect.

Order is critical.

---

### Trap 2

> A three-column index automatically optimizes every query on those columns.

❌ Only queries following the leftmost prefix benefit efficiently.

---

### Trap 3

> More composite indexes always improve performance.

❌ They increase storage and write costs.

---

# 14. Practice

```sql
CREATE INDEX IX_Order_Customer_Date
ON Orders(CustomerID, OrderDate);

SELECT *
FROM Orders
WHERE CustomerID = 101
AND OrderDate >= '2026-01-01';

EXPLAIN
SELECT *
FROM Orders
WHERE OrderDate >= '2026-01-01';
```

Compare whether the composite index is used.

---

# Revision Notes

- Composite index = Multiple columns.
- Column order matters.
- Follow the Leftmost Prefix Rule.
- Excellent for common multi-column filters.
- Validate with execution plans.

---

# Memory Trick

**COMPOSITE**

**C** = Combined columns

**O** = Order matters

**M** = Multi-column

**P** = Prefix rule

---

# Final Takeaway

Composite indexes are powerful because they optimize queries that filter, join, or sort on multiple columns simultaneously. Their effectiveness depends heavily on column order and real query patterns. Understanding the Leftmost Prefix Rule is essential for designing efficient indexes and is one of the most frequently tested concepts in DBMS interviews.

---

# Quick Interview Cheat Sheet

| Question | Answer |
|----------|--------|
| Composite index? | Index on multiple columns |
| Most important rule? | Leftmost Prefix Rule |
| Does column order matter? | Yes |
| Can it become covering? | Yes |
| Main drawback? | Larger size and slower writes |
| Best use case? | Frequent multi-column queries |
