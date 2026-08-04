# Lesson 246 - B+ Trees

**Part:** Part 11 - Indexing

**Difficulty:** Intermediate → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐ (Extremely High)  
**Estimated Reading Time:** 75 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand the B+ Tree data structure.
- Explain why DBMSs prefer B+ Trees for indexes.
- Understand search, insertion, deletion, and range queries.
- Compare B+ Trees with Binary Search Trees and B-Trees.
- Answer interview questions confidently.

---

# 1. Introduction

A **B+ Tree** is the most common data structure used to implement indexes in relational databases.

Popular DBMSs such as **MySQL (InnoDB)**, **PostgreSQL**, **Oracle**, and **SQL Server** primarily use B+ Tree indexes because they provide:

- Fast searches
- Efficient insertions and deletions
- Excellent range query performance
- Balanced height

Unlike a Binary Search Tree, a B+ Tree remains balanced as data grows.

---

# 2. Why Not Store Data in a Simple Binary Search Tree?

A Binary Search Tree can become skewed.

```text
10
 \
 20
   \
   30
     \
     40
```

Searching can degrade to:

```
O(n)
```

A B+ Tree automatically balances itself.

---

# 3. Structure of a B+ Tree

```text
                 [40 | 70]
                /     |      \
         [10 20]   [45 60]   [80 90]

Leaf Level
+-----+     +------+     +------+
|10 20| --> |45 60| -->  |80 90|
+-----+     +------+     +------+
```

Important:

- Internal nodes store **keys only**.
- Leaf nodes store **keys + row pointers**.
- Leaf nodes are linked together.

---

# 4. Internal Components

## Root Node

Starting point.

## Internal Nodes

Contain separator keys.

## Leaf Nodes

Contain:

- Indexed values
- Row locators (or complete records depending on implementation)

Leaf nodes are linked sequentially.

---

# 5. Internal Working

### Search

```text
Root
 │
Compare Key
 │
Choose Child
 │
Leaf Node
 │
Return Row Pointer
 │
Fetch Record
```

Average complexity:

```
O(log n)
```

---

# 6. Why Leaf Nodes are Linked

Range query:

```sql
SELECT *
FROM Employee
WHERE Salary BETWEEN 50000 AND 70000;
```

Execution:

```text
Locate 50000
      │
Move through linked leaves
      │
55000
60000
65000
70000
```

The DBMS avoids returning to parent nodes repeatedly.

---

# 7. Search Example

Find EmployeeID = 65

```text
Root
[40 | 70]

65 > 40
65 < 70

↓

Middle Child

↓

Leaf

↓

Found
```

---

# 8. Insert Operation

1. Locate leaf.
2. Insert key.
3. Overflow?
4. Split node.
5. Promote middle key.
6. Repeat upward if needed.

```text
Before

[10 20 30]

Insert 40

↓

Overflow

↓

Split

[10 20]
   ↑
 Promote
   ↓
[30 40]
```

---

# 9. Delete Operation

1. Delete key.
2. Underflow?
3. Borrow from sibling.
4. Merge if necessary.
5. Update parent.

The tree always remains balanced.

---

# 10. Why DBMS Uses B+ Trees

- Predictable height.
- Few disk reads.
- Excellent caching.
- Fast range scans.
- Efficient ordered traversal.

---

# 11. B+ Tree vs B-Tree

| Feature | B+ Tree | B-Tree |
|---------|----------|---------|
|Data in internal nodes|No|Yes|
|Data in leaf nodes|Yes|Yes|
|Leaf linked list|Yes|Usually No|
|Range queries|Excellent|Good|
|DBMS usage|Very Common|Less Common|

---

# 12. B+ Tree vs Binary Search Tree

| Feature | BST | B+ Tree |
|---------|-----|----------|
|Balanced|Not always|Always|
|Disk optimized|No|Yes|
|Range queries|Poor|Excellent|
|Height|Can become large|Very small|

---

# 13. Real Project Examples

## Banking

Account number lookup.

## Telecom

Subscriber search.

## E-Commerce

Product search by SKU.

## Hospital

Patient ID lookup.

---

# 14. Performance Notes

- Millions of rows usually require only a few node traversals.
- Wide nodes reduce tree height.
- Sequential leaf nodes improve range scans.
- Ideal for OLTP systems.

---

# 15. Interview Insights ⭐

## Why are B+ Trees preferred over Hash Indexes?

Because B+ Trees support:

- Equality search
- Range search
- ORDER BY
- GROUP BY

Hash indexes mainly support equality lookups.

---

## Why are leaf nodes linked?

To perform efficient sequential scans without climbing back through parent nodes.

---

## Why are internal nodes smaller?

They store only keys, allowing more keys per page and reducing tree height.

---

## What determines B+ Tree height?

- Number of rows
- Page size
- Key size
- Fan-out (children per node)

---

# 16. Interview Traps 🚨

### Trap 1

> Does every database use B+ Trees?

❌ No.

Although most relational databases use them as the default index type, other index structures (Hash, Bitmap, GiST, GIN, etc.) also exist.

---

### Trap 2

> Is B+ Tree search O(1)?

❌ No.

Typical complexity:

```
O(log n)
```

---

### Trap 3

> Why not use Binary Search Trees?

BSTs are not optimized for disk storage and may become unbalanced.

---

# 17. Practice

```sql
CREATE INDEX IX_Product_Name
ON Product(ProductName);

EXPLAIN
SELECT *
FROM Product
WHERE ProductName='Laptop';
```

Observe how the optimizer chooses an index scan.

---

# Revision Notes

- Default index structure in many DBMSs.
- Balanced tree.
- Linked leaf nodes.
- Excellent for range queries.
- Few disk reads.

---

# Memory Trick

**B+ Tree**

**B** = Balanced

**+** = Linked leaf pages

**Tree** = Fast hierarchical search

---

# Final Takeaway

B+ Trees are the backbone of modern relational database indexing. Their balanced structure minimizes disk I/O, while linked leaf nodes make range queries exceptionally efficient. This combination of predictable search performance, fast updates, and ordered traversal explains why B+ Trees remain the default index implementation in most enterprise database systems.

---

# Quick Interview Cheat Sheet

| Question | Answer |
|----------|--------|
| Default index structure? | B+ Tree |
| Search complexity? | O(log n) |
| Range query support? | Excellent |
| Leaf nodes linked? | Yes |
| Balanced? | Always |
| Why better than BST? | Smaller height and disk optimization |
| Why not Hash? | B+ Trees support range searches |
