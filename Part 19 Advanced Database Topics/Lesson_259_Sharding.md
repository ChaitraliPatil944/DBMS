# Lesson 259 - Sharding

**Part:** Part 19 – Advanced Database Topics

**Difficulty:** Intermediate → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 70 Minutes

---

# Learning Objectives

- Understand database sharding.
- Learn horizontal partitioning.
- Explore shard keys and routing.
- Compare sharding with replication and partitioning.
- Answer interview questions confidently.

---

# 1. Introduction

**Sharding** is the process of splitting a large database into multiple smaller databases called **shards**.

Each shard stores only a subset of the data while together they form one logical database.

Primary goals:

- Horizontal scalability
- Better performance
- Higher storage capacity
- Reduced load on a single server

---

# 2. Why Sharding?

Without sharding:

```text
Clients
   │
Large Database
```

As data grows, one server becomes a bottleneck.

With sharding:

```text
Clients
   │
Router
 ├── Shard 1
 ├── Shard 2
 └── Shard 3
```

Data is distributed across multiple servers.

---

# 3. How Sharding Works

```text
Request
   │
Shard Key
   │
Router
   │
Correct Shard
```

The router determines which shard contains the required data.

---

# 4. Shard Key

A **Shard Key** decides how data is distributed.

Example:

```text
CustomerID

1-1000  → Shard 1
1001-2000 → Shard 2
2001-3000 → Shard 3
```

A good shard key:

- Evenly distributes data
- Avoids hotspots
- Supports common queries

---

# 5. Sharding Strategies

## Range-Based

```text
1-1000
1001-2000
2001-3000
```

Simple but can create hotspots.

---

## Hash-Based

```text
Hash(CustomerID)
      │
Shard Number
```

Provides balanced distribution.

---

## Directory-Based

A lookup service maps records to shards.

---

# 6. Advantages

- Horizontal scaling
- Faster query execution
- Increased storage capacity
- Fault isolation
- Supports massive datasets

---

# 7. Challenges

- Cross-shard joins
- Resharding complexity
- Distributed transactions
- Selecting a good shard key
- Operational overhead

---

# 8. Sharding vs Replication

| Sharding | Replication |
|----------|-------------|
|Splits data|Copies data|
|Improves write scalability|Improves availability|
|Different data per server|Same data per server|
|Increases storage capacity|Provides redundancy|

---

# 9. Sharding vs Partitioning

| Sharding | Partitioning |
|----------|--------------|
|Across servers|Usually within one server|
|Horizontal scaling|Logical organization|
|Distributed|Single database instance|

---

# 10. Real-World Examples

- Amazon: Customer data across regions
- Netflix: User data distribution
- Instagram: User-based sharding
- Discord: Community distribution
- Large SaaS platforms

---

# 11. Performance Notes

- Smaller datasets per server.
- Parallel query execution.
- Better write scalability.
- Poor shard keys can cause hotspots.

---

# Interview Insights ⭐

### What is a hotspot?

One shard receives far more traffic than others due to uneven data distribution.

### Can sharding improve write performance?

Yes. Writes are distributed across multiple servers.

### Does sharding replace replication?

No. Large systems often use **both** sharding and replication.

---

# Interview Traps 🚨

- Sharding is not backup.
- Sharding is different from replication.
- Bad shard keys create severe performance issues.

---

# Practice

1. Define sharding.
2. Explain a shard key.
3. Compare range and hash sharding.
4. Differentiate sharding and replication.

---

# Revision Notes

- Horizontal scaling
- Shards
- Shard key
- Router
- Range, Hash, Directory strategies

---

# Memory Trick

**SHARD**

**S** = Split database

**H** = Horizontal scaling

**A** = Across servers

**R** = Router directs queries

**D** = Distributed storage

---

# Final Takeaway

Sharding enables databases to scale beyond the limits of a single server by distributing data across multiple machines. Choosing an effective shard key is critical because it determines load balancing, query performance, and long-term scalability. In modern distributed systems, sharding is commonly combined with replication to achieve both scalability and high availability.

---

# Quick Interview Cheat Sheet

| Question | Answer |
|----------|--------|
| What is sharding? | Splitting data across multiple servers |
| Main benefit? | Horizontal scalability |
| What decides data placement? | Shard Key |
| Common strategies? | Range, Hash, Directory |
| Replace replication? | No |
| Biggest challenge? | Choosing the right shard key |
