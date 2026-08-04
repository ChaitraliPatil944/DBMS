# Lesson 258 - Replication

**Part:** Part 19 – Advanced Database Topics

**Difficulty:** Intermediate → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 70 Minutes

---

# Learning Objectives

- Understand database replication.
- Learn why replication is used.
- Differentiate replication models.
- Understand synchronous vs asynchronous replication.
- Answer interview questions confidently.

---

# 1. Introduction

**Replication** is the process of copying data from one database server to one or more other database servers.

Its primary goals are:

- High Availability
- Fault Tolerance
- Disaster Recovery
- Read Scalability
- Data Redundancy

Replication ensures multiple copies of data are available across different servers or locations.

---

# 2. Why Replication?

Without replication:

```text
Client
  │
Database

Server Failure

Application Stops
```

With replication:

```text
Client
   │
Primary
  / \
Replica Replica

Primary fails
     │
Replica becomes Primary
```

---

# 3. Replication Architecture

```text
           Clients
              │
         Primary Server
         /     |      \
 Replica1 Replica2 Replica3
```

The primary handles writes while replicas receive copies of the updated data.

---

# 4. Types of Replication

## Master-Slave (Primary-Replica)

```text
Primary
 │
 ├── Replica
 ├── Replica
 └── Replica
```

Advantages

- Simple
- Fast reads
- Easy implementation

Disadvantages

- Single write node
- Primary failure requires failover

---

## Multi-Master Replication

```text
Node A ↔ Node B ↔ Node C
```

Every node accepts reads and writes.

Advantages

- High availability
- Better write scalability

Disadvantages

- Conflict resolution required
- More complex architecture

---

# 5. Synchronous Replication

```text
Client
 │
Primary
 │
Replica
 │
ACK
 │
Client Response
```

Characteristics

- Strong consistency
- Higher latency
- Safer transactions

Used in:

- Banking
- Financial systems

---

# 6. Asynchronous Replication

```text
Client
 │
Primary
 │
Client Response
 │
Background Replication
 │
Replica
```

Characteristics

- Faster writes
- Slight replication delay
- Eventual consistency

Used in:

- Social media
- E-commerce
- Streaming

---

# 7. Read and Write Flow

Write Operation

```text
Client
 │
Primary
 │
Replicas
```

Read Operation

```text
Client
 │
Nearest Replica
```

This improves read performance.

---

# 8. Replication vs Backup

| Replication | Backup |
|-------------|--------|
|Real-time copy|Point-in-time copy|
|Supports high availability|Used for recovery|
|Automatic updates|Manual or scheduled|
|Not a replacement for backups|Protects against accidental deletion|

---

# 9. Advantages

- High availability
- Fault tolerance
- Faster reads
- Disaster recovery
- Geographic distribution

---

# 10. Limitations

- Increased storage
- Replication lag
- Network bandwidth usage
- Conflict handling in multi-master systems

---

# 11. Real-World Examples

### Banking

Primary database with synchronous replicas.

### Netflix

Replicated databases across regions.

### Amazon

Distributed replicas for global services.

### WhatsApp

Replication ensures high availability.

---

# 12. Performance Notes

- Replicas improve read throughput.
- Synchronous replication increases latency.
- Asynchronous replication improves performance but may temporarily expose stale data.
- Monitor replication lag continuously.

---

# Interview Insights ⭐

### Why use replication?

To improve availability, reliability, and read scalability.

### Does replication replace backups?

No.

Replication copies mistakes as well as valid updates. Backups provide historical recovery points.

### Which replication is faster?

Asynchronous replication.

### Which is safer?

Synchronous replication.

---

# Interview Traps 🚨

- Replication is not the same as backup.
- More replicas do not automatically improve write performance.
- Replication does not prevent accidental data deletion.

---

# Practice

1. Define replication.
2. Compare synchronous and asynchronous replication.
3. Explain primary-replica architecture.
4. Why are backups still necessary?

---

# Revision Notes

- Primary → Replica
- High availability
- Disaster recovery
- Read scalability
- Synchronous vs Asynchronous

---

# Memory Trick

**REPLICA**

**R** = Redundancy

**E** = Extra Copies

**P** = Primary

**L** = Low Downtime

**I** = Increased Availability

**C** = Continuous Synchronization

**A** = Automatic Replication

---

# Final Takeaway

Replication is one of the most important techniques used in modern database systems to improve availability, fault tolerance, and read performance. Choosing between synchronous and asynchronous replication depends on the application's consistency requirements and tolerance for latency. While replication keeps systems running during failures, it should always be complemented with proper backup strategies.

---

# Quick Interview Cheat Sheet

| Question | Answer |
|----------|--------|
| What is replication? | Maintaining multiple copies of data |
| Main benefit? | High availability |
| Fastest replication? | Asynchronous |
| Safest replication? | Synchronous |
| Does replication replace backup? | No |
| Write node in Primary-Replica? | Primary |
