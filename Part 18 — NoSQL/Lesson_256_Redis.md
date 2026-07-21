# Lesson 256 - Redis

**Part:** Part 18 – NoSQL

**Difficulty:** Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 65 Minutes

---

# Learning Objectives

- Understand Redis and its architecture.
- Learn Redis data structures.
- Perform basic Redis commands.
- Understand persistence, replication, and caching.
- Answer Redis interview questions.

---

# 1. Introduction

**Redis (Remote Dictionary Server)** is an in-memory Key-Value NoSQL database used for caching, session management, real-time analytics, and messaging.

Unlike traditional databases, Redis stores data primarily in RAM, making it extremely fast.

---

# 2. Key Features

- In-memory storage
- Key-Value database
- Extremely low latency
- Rich data structures
- Replication
- Persistence
- Pub/Sub messaging
- High availability

---

# 3. Redis Architecture

```text
Application
      │
Redis Client
      │
Redis Server
      │
Memory (RAM)
      │
Optional Disk Persistence
```

---

# 4. Data Structures

Redis supports multiple data types.

## String

```text
user:name = Alice
```

## List

```text
Task1
Task2
Task3
```

## Set

```text
Java
Python
SQL
```

## Hash

```text
Name → Alice
Age  → 22
City → Pune
```

## Sorted Set

Stores values with scores.

```text
Alice 90
Bob   95
```

---

# 5. Basic Commands

## SET

```bash
SET name Alice
```

## GET

```bash
GET name
```

## DEL

```bash
DEL name
```

## INCR

```bash
INCR counter
```

## EXPIRE

```bash
EXPIRE session 300
```

---

# 6. Persistence

Redis supports two persistence mechanisms.

### RDB (Snapshot)

Creates snapshots at intervals.

### AOF (Append Only File)

Logs every write operation.

Many deployments use both for better durability.

---

# 7. Replication

```text
Master
 │
 ├── Replica
 ├── Replica
 └── Replica
```

Replicas receive data from the primary server.

---

# 8. Redis Sentinel

Provides:

- Monitoring
- Automatic failover
- High availability

```text
Sentinel
   │
Primary
   │
Replicas
```

---

# 9. Redis Cluster

```text
Client
   │
Redis Cluster
 ├── Node 1
 ├── Node 2
 └── Node 3
```

Data is partitioned across multiple nodes for scalability.

---

# 10. Common Use Cases

- Caching
- Session storage
- Leaderboards
- Real-time analytics
- Rate limiting
- Chat applications
- Gaming
- Message queues

---

# 11. SQL vs Redis

| SQL | Redis |
|------|--------|
|Disk based|Memory based|
|Tables|Key-Value|
|Slower|Extremely fast|
|Complex queries|Simple lookups|
|Persistent by default|Persistence optional/configurable|

---

# 12. Advantages

- Extremely fast
- Low latency
- Rich data structures
- Easy scaling
- Excellent caching solution

---

# 13. Limitations

- Memory can be expensive
- Dataset size limited by RAM
- Not ideal for complex relational queries
- Persistence configuration requires planning

---

# Performance Notes

- Microsecond response times
- Millions of operations per second
- Ideal for read-heavy workloads
- Frequently paired with relational databases

---

# Interview Insights ⭐

### Why is Redis so fast?

Because most operations occur entirely in RAM, avoiding disk I/O.

### Is Redis only a cache?

No. It can also act as a database, message broker, and streaming platform.

### What is Redis mainly used for?

Caching, sessions, leaderboards, Pub/Sub messaging, and rate limiting.

---

# Interview Traps 🚨

- Redis is not just a cache.
- Redis supports persistence.
- Redis offers more than simple strings through advanced data structures.

---

# Practice

1. Store a value using SET.
2. Retrieve it using GET.
3. Increment a counter.
4. Set an expiration time.
5. Explain the difference between RDB and AOF.

---

# Revision Notes

- In-memory database
- Key-Value model
- Strings, Lists, Sets, Hashes, Sorted Sets
- RDB and AOF
- Replication
- Sentinel
- Cluster

---

# Memory Trick

**REDIS**

**R** = RAM

**E** = Extremely Fast

**D** = Data Structures

**I** = In-Memory

**S** = Sessions & Caching

---

# Final Takeaway

Redis is one of the fastest NoSQL databases because it stores data primarily in memory. Its support for multiple data structures, replication, persistence, clustering, and messaging makes it an essential technology for building high-performance, low-latency applications.

---

# Quick Interview Cheat Sheet

| Question | Answer |
|----------|--------|
| Database type? | Key-Value |
| Storage? | In-Memory (RAM) |
| Persistence methods? | RDB and AOF |
| High availability? | Sentinel |
| Horizontal scaling? | Redis Cluster |
| Common use? | Caching and Session Storage |
