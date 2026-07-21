# Lesson 245 - Why Indexes

**Part:** Part 11 - Indexing

**Difficulty:** Beginner → Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 50–60 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand what an index is.
- Explain why indexes improve query performance.
- Learn how a DBMS searches data with and without indexes.
- Identify situations where indexes help or hurt performance.
- Answer interview questions related to indexing.

---

# 1. Introduction

An **Index** is a data structure that helps the DBMS locate rows quickly without scanning an entire table.

Think of an index in a book. Instead of reading every page to find "Polymorphism", you use the index to jump directly to the correct page.

Database indexes work on the same principle.

---

# 2. Why Are Indexes Needed?

Without an index, the DBMS performs a **Full Table Scan**.

Example:

```sql
SELECT *
FROM Employee
WHERE EmployeeID = 105;
```

If the table contains one million rows, the DBMS may inspect every row before finding the match.

An index allows the DBMS to jump directly to the required row.

---

# 3. Full Table Scan vs Index Scan

## Without Index

```text
Row1
Row2
Row3
...
Row999999
Row1000000
```

Time Complexity (approx.):

```
O(n)
```

## With Index

```text
Index
   │
Locate Key
   │
Jump to Data Row
```

Time Complexity (approx.):

```
O(log n)
```

for tree-based indexes.

---

# 4. How Indexes Work

```text
User Query
      │
      ▼
Optimizer
      │
Uses Index?
 ┌────┴────┐
Yes        No
│          │
Index     Table
Scan      Scan
│          │
Return Matching Rows
```

The optimizer decides whether using the index is cheaper than scanning the table.

---

# 5. Example

Create an index:

```sql
CREATE INDEX IX_Employee_Name
ON Employee(Name);
```

Query:

```sql
SELECT *
FROM Employee
WHERE Name = 'Alice';
```

The optimizer may use `IX_Employee_Name` to locate matching rows efficiently.

---

# 6. Advantages

- Faster SELECT queries.
- Faster searching and filtering.
- Better JOIN performance.
- Faster ORDER BY and GROUP BY in many cases.
- Improved overall query execution.

---

# 7. Disadvantages

- Consumes additional disk space.
- Slows INSERT operations.
- Slows UPDATE operations.
- Slows DELETE operations.
- Requires maintenance as data changes.

---

# 8. When Should You Create an Index?

Good candidates:

- Primary keys
- Foreign keys
- Frequently searched columns
- JOIN columns
- ORDER BY columns
- GROUP BY columns

Avoid indexing:

- Very small tables
- Columns with very few distinct values (in many cases)
- Frequently updated columns without read benefits

---

# 9. Real Project Examples

## Banking

Index on AccountNumber for instant account lookup.

## Telecom

Index on MobileNumber for customer search.

## E-Commerce

Index on ProductID and CustomerID.

## Hospital

Index on PatientID and AppointmentDate.

---

# 10. Performance Notes

- Indexes speed up reads but add write overhead.
- Too many indexes can reduce overall performance.
- The optimizer may ignore an index if a table scan is estimated to be cheaper.
- Regular maintenance may be required in some DBMSs.

---

# 11. Common Mistakes

- Indexing every column.
- Assuming indexes always improve performance.
- Ignoring index maintenance costs.
- Creating duplicate or unused indexes.

---

# 12. Interview Questions

## Beginner

1. What is an index?
2. Why are indexes used?
3. Does an index store table data?

## Intermediate

1. Full table scan vs index scan?
2. Why do indexes slow INSERT and UPDATE?
3. Which columns should be indexed?

## Advanced

1. How does the optimizer choose an index?
2. Why might the optimizer ignore an index?
3. Explain index selectivity.

---

# 13. Practice

```sql
CREATE INDEX IX_Customer_City
ON Customer(City);

SELECT *
FROM Customer
WHERE City = 'Pune';

DROP INDEX IX_Customer_City;
```

---

# Revision Notes

- Indexes improve search performance.
- Reduce full table scans.
- Increase storage usage.
- Improve reads but slow writes.
- Should be created strategically.

---

# Memory Trick

**INDEX = Shortcut to Data**

Instead of searching every row, the DBMS follows the shortcut.

---

# Final Takeaway

Indexes are one of the most important performance features in relational databases. By organizing lookup information separately from the table data, they enable the optimizer to locate rows efficiently and avoid expensive full table scans. In interviews, remember the core trade-off: indexes make read operations much faster, but every additional index increases the cost of INSERT, UPDATE, and DELETE operations because the index must also be maintained.
