# Lesson 245 - Why Indexes

**Part:** Part 11 - Indexing

**Difficulty:** Beginner → Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐⭐ (Very High)  
**Estimated Reading Time:** 60 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand why indexes are required.
- Explain how indexes speed up queries.
- Compare indexed and non-indexed searches.
- Understand index trade-offs.
- Answer interview questions confidently.

---

# 1. Introduction

An **Index** is a special data structure that allows the DBMS to locate rows **without scanning the entire table**.

Think of an index in a database like the index at the back of a textbook.

Without an index, the DBMS performs a **Full Table Scan**.

With an index, the DBMS can jump directly to the required rows.

---

# 2. Why Do We Need Indexes?

Imagine an `Employee` table with **10 million rows**.

Query:

```sql
SELECT *
FROM Employee
WHERE EmployeeID = 1054321;
```

Without an index:

- Read row 1
- Read row 2
- Read row 3
- ...
- Continue until a match is found.

With an index:

- Navigate the index.
- Jump directly to the required row.

---

# 3. Book Analogy

```text
Book
│
├── Without Index
│     Read every page.
│
└── With Index
      Open index
      ↓
      Find topic
      ↓
      Go directly to page
```

Databases borrowed this idea because apparently reading ten million rows one by one was not considered an efficient hobby.

---

# 4. Internal Working

## Without Index

```text
Query
  │
Full Table Scan
  │
Row 1
Row 2
Row 3
...
Row N
  │
Return Result
```

Time Complexity (conceptually)

```
O(n)
```

---

## With Index

```text
Query
   │
Use Index
   │
Locate Pointer
   │
Fetch Data Row
   │
Return Result
```

Time Complexity (B+ Tree index)

```
Approximately O(log n)
```

---

# 5. Sample Table

```text
Employee
+----+---------+--------+
|ID  |Name     |Salary  |
+----+---------+--------+
|1   |Alice    |50000   |
|2   |Bob      |60000   |
|3   |Carol    |55000   |
|... |...      |...     |
```

Create an index:

```sql
CREATE INDEX IX_Employee_ID
ON Employee(EmployeeID);
```

---

# 6. What Queries Benefit?

Indexes are especially useful for:

- WHERE
- JOIN
- ORDER BY
- GROUP BY
- DISTINCT
- MIN / MAX

Example:

```sql
SELECT *
FROM Orders
WHERE CustomerID = 101;
```

---

# 7. Advantages

- Faster searches.
- Faster joins.
- Faster sorting.
- Better scalability.
- Improved reporting performance.

---

# 8. Disadvantages

- Consumes disk space.
- Slows INSERT operations.
- Slows UPDATE operations on indexed columns.
- Slows DELETE operations.
- Requires maintenance.

---

# 9. When NOT to Create an Index

Avoid indexing:

- Very small tables.
- Columns with frequent updates.
- Columns with very low selectivity (for example, a boolean flag).
- Temporary tables with short lifetimes.

---

# 10. Real Project Examples

## Banking

Search accounts by Account Number.

## Telecom

Find subscribers by Mobile Number.

## E-Commerce

Search products by SKU.

## Hospital

Retrieve patients using Patient ID.

---

# 11. Performance Comparison

| Operation | Without Index | With Index |
|-----------|---------------|------------|
|Search by Primary Key|Slow|Fast|
|JOIN|Slower|Faster|
|ORDER BY|May sort many rows|Often optimized|
|INSERT|Faster|Slightly slower|
|UPDATE|Faster|Slightly slower|

---

# 12. Common Mistakes

- Creating indexes on every column.
- Ignoring write overhead.
- Forgetting to monitor unused indexes.
- Assuming indexes always improve performance.

---

# 13. Interview Insights ⭐

## Q1. What is an Index?

**Answer:**

An index is a data structure that improves data retrieval speed by storing indexed column values with pointers to table rows.

---

## Q2. Why don't we index every column?

Because every index:

- Consumes storage.
- Must be updated during INSERT, UPDATE and DELETE.
- Can slow write-heavy workloads.

---

## Q3. Does an index store actual table data?

Usually **No**.

A traditional index stores:

- Indexed column values
- Row pointers (or row locators)

The remaining columns are fetched from the base table if required.

---

## Q4. Why is searching faster?

The DBMS doesn't scan every row.

Instead, it traverses an efficient structure (typically a **B+ Tree**) to reach the desired record quickly.

---

## Q5. Can indexes make queries slower?

Yes.

Indexes improve reads but add maintenance work during writes.

---

# 14. Interview Traps 🚨

### Trap 1

> More indexes = Better performance?

❌ Incorrect

Too many indexes increase write cost and storage.

---

### Trap 2

> Primary Keys automatically create indexes?

✅ In most DBMSs, yes (implementation details vary).

---

### Trap 3

> Does every query use an index?

❌ No.

The optimizer chooses whether using an index is cheaper than scanning the table.

---

# 15. Practice

```sql
CREATE INDEX IX_Customer_Name
ON Customer(Name);

CREATE INDEX IX_Order_Date
ON Orders(OrderDate);

SELECT *
FROM Customer
WHERE Name='Alice';
```

---

# Revision Notes

- Index = Faster lookup.
- Reduces Full Table Scans.
- Usually implemented using B+ Trees.
- Great for read-heavy workloads.
- Adds write overhead.

---

# Memory Trick

**INDEX**

**I** → Instant lookup

**N** → Navigate quickly

**D** → Direct access

**E** → Efficient search

**X** → eXtra storage required

---

# Final Takeaway

Indexes are among the most important performance optimization techniques in relational databases. They dramatically reduce search time by organizing data into efficient lookup structures instead of forcing full table scans. However, indexes are not free. Every additional index consumes storage and increases the cost of data modifications. A good database designer creates indexes selectively, balancing read performance with write efficiency.

---

# Quick Interview Cheat Sheet

| Question | Short Answer |
|----------|--------------|
| Why use indexes? | Faster retrieval |
| Default implementation? | Usually B+ Tree |
| Benefit | Fast SELECT, JOIN, ORDER BY |
| Drawback | Slower INSERT/UPDATE/DELETE |
| Store full table? | No, generally key + row locator |
| Should every column be indexed? | No |
| Most common interview topic | Full Table Scan vs Index Scan |
