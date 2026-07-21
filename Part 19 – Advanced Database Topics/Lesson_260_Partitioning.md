# Lesson 260 - Partitioning

**Part:** Part 19 – Advanced Database Topics

**Difficulty:** Intermediate → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 70 Minutes

---

# Learning Objectives

- Understand database partitioning.
- Learn different partitioning strategies.
- Compare partitioning with sharding.
- Understand partition pruning.
- Answer interview questions confidently.

---

# 1. Introduction

**Partitioning** is the process of dividing a large database table into smaller logical pieces called **partitions**.

Although the data is physically separated, the database still treats it as a single table.

Main goals:

- Improve query performance
- Simplify maintenance
- Reduce I/O
- Handle large datasets efficiently

---

# 2. Why Partitioning?

Without partitioning:

```text
Orders Table

10 Million Rows

↓

Full Scan
```

With partitioning:

```text
Orders

├── 2023
├── 2024
└── 2025
```

Only the required partition is accessed.

---

# 3. Internal Architecture

```text
Application
     │
Orders Table
     │
Partition Manager
     │
 ├── Partition 1
 ├── Partition 2
 └── Partition 3
```

The DBMS automatically routes queries to the correct partition.

---

# 4. Types of Partitioning

## Range Partitioning

Rows are divided by ranges.

Example:

```text
2023
2024
2025
```

Ideal for date-based data.

---

## List Partitioning

Rows belong to predefined groups.

```text
North
South
East
West
```

Useful for regions or categories.

---

## Hash Partitioning

A hash function distributes rows evenly.

```text
Hash(CustomerID)
      │
Partition
```

Provides balanced storage.

---

## Composite Partitioning

Combines two or more strategies.

Example:

Range → Hash

```text
2025
  │
Hash(CustomerID)
```

---

# 5. Partition Pruning

One of the biggest advantages.

Example:

```sql
SELECT *
FROM Orders
WHERE OrderYear = 2025;
```

The DBMS scans only the 2025 partition instead of the entire table.

---

# 6. Partitioning vs Sharding

| Partitioning | Sharding |
|--------------|----------|
|Within one database|Across multiple servers|
|Logical division|Distributed division|
|Managed by DBMS|Managed by distributed architecture|
|Improves performance|Improves scalability|

---

# 7. Advantages

- Faster queries
- Easier maintenance
- Smaller indexes
- Faster backups
- Efficient archiving

---

# 8. Challenges

- Choosing the right partition key
- Cross-partition queries
- Repartitioning overhead
- Uneven data distribution

---

# 9. Real-World Examples

### Banking

Transactions partitioned by year.

### E-Commerce

Orders partitioned by month.

### Telecom

Call records partitioned by region.

### Healthcare

Patient records partitioned by hospital.

---

# 10. Performance Notes

- Partition pruning reduces disk I/O.
- Indexes become smaller.
- Maintenance operations affect only selected partitions.
- Very large tables become easier to manage.

---

# Interview Insights ⭐

### What is partition pruning?

The optimizer skips irrelevant partitions and scans only those needed by the query.

### Does partitioning always improve performance?

No. It depends on query patterns and partition design.

### Can partitioning and sharding be used together?

Yes. Many enterprise systems partition data inside each shard.

---

# Interview Traps 🚨

- Partitioning does not automatically distribute data across servers.
- Partitioning is different from replication.
- Bad partition keys reduce performance benefits.

---

# Practice

1. Define partitioning.
2. Explain range partitioning.
3. Compare partitioning and sharding.
4. What is partition pruning?

---

# Revision Notes

- Logical table division
- Range, List, Hash, Composite
- Partition pruning
- Better query performance
- Easier maintenance

---

# Memory Trick

**PART**

**P** = Partition table

**A** = Access fewer rows

**R** = Reduce I/O

**T** = Table remains logical

---

# Final Takeaway

Partitioning improves the performance and manageability of very large database tables by dividing them into smaller logical units. Features like partition pruning allow the optimizer to access only relevant partitions, significantly reducing query execution time. While partitioning enhances performance within a database instance, it is often combined with sharding for large-scale distributed systems.

---

# Quick Interview Cheat Sheet

| Question | Answer |
|----------|--------|
| What is partitioning? | Dividing a table into logical partitions |
| Main benefit? | Faster queries |
| Best feature? | Partition pruning |
| Common types? | Range, List, Hash, Composite |
| Same as sharding? | No |
| Can both be combined? | Yes |
