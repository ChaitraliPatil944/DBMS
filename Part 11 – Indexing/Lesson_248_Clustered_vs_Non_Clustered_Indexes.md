# Lesson 248 - Clustered vs Non-Clustered Indexes

**Part:** Part 11 - Indexing

**Difficulty:** Intermediate → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐ (Very High)  
**Estimated Reading Time:** 70 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand clustered and non-clustered indexes.
- Explain their internal storage.
- Compare advantages and disadvantages.
- Decide when each type should be used.
- Answer interview questions confidently.

---

# 1. Introduction

Indexes improve data retrieval, but not all indexes store data in the same way.

The two most important index types are:

- **Clustered Index**
- **Non-Clustered Index**

The main difference is **where the actual table data is stored relative to the index**.

---

# 2. Clustered Index

A clustered index stores the table rows **in the same physical order as the index keys**.

```text
Clustered Index

[101]
[102]
[103]
[104]

↓

Table Data

101
102
103
104
```

There can usually be **only one clustered index** because the table can only have one physical ordering.

---

# 3. Non-Clustered Index

A non-clustered index is a **separate structure**.

It stores:

- Indexed key
- Row locator (RID or clustered key)

```text
Non-Clustered Index

Alice → Row 15
Bob   → Row 82
Carol → Row 34

↓

Base Table

Row 15
Row 34
Row 82
```

A table can usually have **multiple non-clustered indexes**.

---

# 4. Internal Working

## Clustered Index

```text
Query
 │
Clustered Index
 │
Directly reaches data row
 │
Return Result
```

## Non-Clustered Index

```text
Query
 │
Non-Clustered Index
 │
Find Row Pointer
 │
Go to Base Table
 │
Return Result
```

This extra lookup is often called a **Key Lookup** or **Bookmark Lookup**.

---

# 5. Example

```sql
CREATE CLUSTERED INDEX IX_Emp_ID
ON Employee(EmployeeID);

CREATE NONCLUSTERED INDEX IX_Emp_Name
ON Employee(Name);
```

---

# 6. Clustered vs Non-Clustered

| Feature | Clustered | Non-Clustered |
|---------|-----------|---------------|
|Stores data order|Yes|No|
|Separate structure|No|Yes|
|Row locator needed|No|Yes|
|Range queries|Excellent|Very Good|
|Typical count|One|Many|

---

# 7. Covering Index

A non-clustered index can become a **covering index** if it contains every column required by the query.

Example:

```sql
SELECT Name, Salary
FROM Employee
WHERE Name='Alice';
```

If the index already stores `Name` and `Salary`, the DBMS can answer the query **without visiting the base table**.

---

# 8. Advantages

## Clustered

- Fast range scans.
- Sequential storage.
- Efficient primary key access.

## Non-Clustered

- Multiple indexes allowed.
- Flexible search columns.
- Can become covering indexes.

---

# 9. Limitations

## Clustered

- Only one per table.
- Page splits may occur when inserting out-of-order values.

## Non-Clustered

- Additional storage.
- Extra lookup may be required.
- Write overhead increases with many indexes.

---

# 10. Real Project Examples

### Banking

Clustered: AccountNumber

Non-Clustered: CustomerName

### Telecom

Clustered: SubscriberID

Non-Clustered: MobileNumber, Email

### E-Commerce

Clustered: ProductID

Non-Clustered: ProductName, CategoryID

---

# 11. Performance Notes

- Clustered indexes excel at range queries.
- Non-clustered indexes are ideal for alternate search paths.
- Too many non-clustered indexes slow writes.
- Covering indexes eliminate costly key lookups.

---

# 12. Interview Insights ⭐

## Why only one clustered index?

Because table rows can only be stored in **one physical order**.

---

## Which index is created for a Primary Key?

In many DBMSs, the primary key creates a clustered index by default **if one doesn't already exist**. Exact behavior varies by DBMS.

---

## What is a Key Lookup?

After finding a row in a non-clustered index, the DBMS follows the stored pointer to retrieve remaining columns from the base table.

---

## Which index is faster?

- Equality search: Both are fast.
- Range search: Clustered usually performs better.
- Covering query: Non-clustered may be faster because no lookup is needed.

---

# 13. Interview Traps 🚨

### Trap 1

> Every table must have a clustered index.

❌ Incorrect.

Some tables are heaps (no clustered index).

---

### Trap 2

> Non-clustered indexes store complete rows.

❌ Usually they store keys plus row locators (or included columns).

---

### Trap 3

> More non-clustered indexes always improve performance.

❌ Read speed may improve, but writes become slower.

---

# 14. Practice

```sql
CREATE CLUSTERED INDEX IX_Order_ID
ON Orders(OrderID);

CREATE NONCLUSTERED INDEX IX_Order_Date
ON Orders(OrderDate);

EXPLAIN
SELECT *
FROM Orders
WHERE OrderDate='2026-01-01';
```

---

# Revision Notes

- One clustered index.
- Many non-clustered indexes.
- Clustered stores data order.
- Non-clustered stores pointers.
- Covering indexes avoid lookups.

---

# Memory Trick

**Clustered = Close to Data**

**Non-Clustered = Navigation Map**

---

# Final Takeaway

Clustered and non-clustered indexes solve different performance problems. A clustered index determines the physical ordering of table data and is highly effective for range scans and sequential access. A non-clustered index provides additional access paths by storing indexed keys with row locators, making it ideal for searching on multiple columns. Choosing the right combination is essential for balancing read performance, storage usage, and write efficiency.

---

# Quick Interview Cheat Sheet

| Question | Answer |
|----------|--------|
| How many clustered indexes? | Usually one |
| Many non-clustered indexes? | Yes |
| Which stores table order? | Clustered |
| Which uses row pointers? | Non-clustered |
| Range queries? | Clustered excels |
| Covering index? | Non-clustered index containing all required columns |
