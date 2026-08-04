# Lesson 247 - Hash Indexes

**Part:** Part 11 - Indexing

**Difficulty:** Intermediate → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐☆ (High)  
**Estimated Reading Time:** 60–70 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand Hash Indexes and hashing.
- Explain hash functions and bucket storage.
- Compare Hash Indexes with B+ Tree Indexes.
- Identify when hash indexes should and should not be used.
- Answer interview questions confidently.

---

# 1. Introduction

A **Hash Index** uses a **hash function** to map a search key directly to a storage location called a **bucket**.

Instead of traversing a tree, the DBMS computes a hash value and jumps directly to the bucket.

Hash indexes are optimized for **exact-match searches**.

---

# 2. Why Hash Indexes?

Example:

```sql
SELECT *
FROM Customer
WHERE CustomerID = 1001;
```

The DBMS computes:

```text
Hash(1001) → Bucket 27
```

Then it searches only Bucket 27 instead of scanning the table.

---

# 3. Internal Structure

```text
CustomerID
     │
Hash Function
     │
Hash Value
     │
Bucket
     │
Row Pointer
     │
Table Row
```

---

# 4. Hash Function

A hash function converts a key into a bucket number.

Example:

```text
Hash(Key) = Key MOD 10

1001 → 1
2021 → 1
3055 → 5
```

Different keys may map to the same bucket.

---

# 5. Hash Collision

A **collision** occurs when multiple keys produce the same bucket.

```text
Bucket 1

1001
 ↓
2021
 ↓
9011
```

Collision handling techniques include:

- Chaining
- Overflow pages
- Open addressing (implementation dependent)

---

# 6. Internal Working

## Equality Search

```text
Query
 │
Hash Function
 │
Bucket Number
 │
Bucket Scan
 │
Return Row
```

Average complexity:

```text
O(1)
```

---

# 7. Why Hash Indexes Cannot Handle Range Queries

Query:

```sql
SELECT *
FROM Product
WHERE Price BETWEEN 1000 AND 5000;
```

Hash values are **not ordered**.

```text
1000 → Bucket 3
1500 → Bucket 9
2000 → Bucket 1
2500 → Bucket 5
```

The DBMS cannot scan values in sorted order.

---

# 8. Hash Index vs B+ Tree

| Feature | Hash Index | B+ Tree |
|---------|------------|----------|
|Equality search|Excellent|Excellent|
|Range query|Poor|Excellent|
|ORDER BY|No|Yes|
|GROUP BY|Limited|Excellent|
|Traversal|Unordered|Sorted|
|Typical complexity|O(1)|O(log n)|

---

# 9. Advantages

- Extremely fast equality lookups.
- Simple bucket access.
- Good for primary key lookups.
- Minimal tree traversal overhead.

---

# 10. Limitations

- No efficient range scans.
- Cannot efficiently support ordered results.
- Performance degrades with excessive collisions.
- Support varies across DBMSs.

---

# 11. Real Project Examples

## Banking

Lookup account by account number.

## Telecom

Search subscriber by SIM ID.

## E-Commerce

Find product using SKU.

## Hospital

Locate patient using Patient ID.

---

# 12. Performance Notes

- Works best with uniformly distributed keys.
- Good hash functions reduce collisions.
- Bucket overflow increases lookup time.
- Poor choice for analytical workloads.

---

# 13. Interview Insights ⭐

## When should you use a Hash Index?

When queries are primarily:

```sql
WHERE ID = ?
```

or other exact-match lookups.

---

## Why can't Hash Indexes support ORDER BY?

Buckets are unordered. The hash value destroys the natural ordering of keys.

---

## Which is faster for equality search?

Hash Indexes are generally faster for pure equality lookups.

---

## Which is preferred by most relational databases?

B+ Trees, because they support equality, range queries, sorting, and joins.

---

# 14. Interview Traps 🚨

### Trap 1

> Are Hash Indexes always better than B+ Trees?

❌ No.

They are better only for equality searches.

---

### Trap 2

> Can a Hash Index execute:

```sql
WHERE Salary > 50000
```

❌ Inefficient.

Use a B+ Tree.

---

### Trap 3

> Complexity is always O(1)?

❌ Average case is O(1). Heavy collisions can increase lookup time.

---

# 15. Practice

```sql
-- Equality lookup
SELECT *
FROM Customer
WHERE CustomerID = 101;

-- Compare with a range query
SELECT *
FROM Product
WHERE Price BETWEEN 1000 AND 5000;
```

Identify which query benefits from a hash index.

---

# Revision Notes

- Hash Index = Equality search.
- Uses buckets.
- Relies on hash functions.
- Suffers from collisions.
- Not suitable for range queries.

---

# Memory Trick

**HASH**

**H** → Hash function

**A** → Average O(1)

**S** → Same bucket collisions

**H** → Handles equality searches

---

# Final Takeaway

Hash indexes provide extremely fast exact-match lookups by computing a hash value that directly identifies the bucket containing the desired row. Their simplicity makes them highly efficient for equality predicates, but because hash values are unordered, they perform poorly for range queries, sorting, and ordered traversals. In practice, hash indexes complement rather than replace B+ Tree indexes.

---

# Quick Interview Cheat Sheet

| Question | Answer |
|----------|--------|
| Best for? | Equality search |
| Time complexity | Average O(1) |
| Range queries | Not efficient |
| ORDER BY support | No |
| Main issue | Hash collisions |
| Default in most DBMS? | No, B+ Trees are usually default |
