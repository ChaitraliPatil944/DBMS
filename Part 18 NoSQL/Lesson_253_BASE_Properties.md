# Lesson 253 - BASE Properties

**Part:** Part 18 – NoSQL

**Difficulty:** Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 60 Minutes

---

# Learning Objectives

- Understand the BASE model.
- Compare BASE with ACID.
- Learn why NoSQL databases prefer BASE.
- Understand eventual consistency.
- Answer interview questions confidently.

---

# 1. Introduction

**BASE** is a consistency model commonly used by NoSQL databases.

It stands for:

- **B** - Basically Available
- **A** - Soft State
- **S** - Eventual Consistency

Unlike ACID, BASE favors availability and scalability over immediate consistency.

---

# 2. Why BASE?

Modern distributed systems prioritize:

- High availability
- Fault tolerance
- Horizontal scalability

Waiting for every node to synchronize can reduce availability, so many NoSQL systems adopt BASE.

---

# 3. BASE Components

## Basically Available

The system always responds to requests, although some responses may contain slightly outdated data.

Example:

A product is updated on one server while another server still shows the old price briefly.

---

## Soft State

Data may temporarily differ across nodes because synchronization happens asynchronously.

```text
Node A → Updated

Node B → Updating...

Node C → Updating...
```

---

## Eventual Consistency

Given enough time and no new updates, every node converges to the same value.

```text
Write
 │
Replication
 │
Node A ✓
Node B ✓
Node C ✓
```

---

# 4. ACID vs BASE

| Feature | ACID | BASE |
|---------|------|------|
|Consistency|Immediate|Eventual|
|Availability|Lower during failures|Higher|
|Scalability|Limited|Excellent|
|Distributed systems|Less suitable|Designed for them|
|Typical Databases|MySQL, PostgreSQL|Cassandra, DynamoDB, Redis|

---

# 5. Internal Working

```text
Client
   │
Write Request
   │
Primary Node
   │
Respond Immediately
   │
Replicate in Background
   │
Other Nodes Updated
```

---

# 6. Real-World Examples

## Social Media

A new post may appear instantly for one user and a few seconds later for another.

## E-Commerce

Inventory counts may briefly differ across regions before synchronization.

## DNS

Updates propagate gradually around the world.

---

# 7. Advantages

- High availability
- Better fault tolerance
- Excellent scalability
- Fast responses
- Suitable for cloud applications

---

# 8. Limitations

- Temporary stale reads
- Complex conflict resolution
- Not ideal for critical financial transactions

---

# 9. When to Use BASE

Choose BASE for:

- Social media
- Chat applications
- Recommendation systems
- IoT
- Analytics
- Streaming platforms

Prefer ACID for:

- Banking
- Payments
- Reservation systems
- Financial ledgers

---

# 10. Performance Notes

- Reduces synchronization delays.
- Supports global deployments.
- Enables large distributed clusters.
- Improves system uptime.

---

# Interview Insights ⭐

## What is Eventual Consistency?

All replicas eventually contain the same data if updates stop.

## Does BASE ignore consistency?

No. It delays consistency rather than guaranteeing it immediately.

## Why do NoSQL databases use BASE?

To improve scalability and availability in distributed environments.

---

# Interview Traps 🚨

❌ Eventual consistency does not mean data is permanently inconsistent.

❌ BASE is not "better" than ACID. Each solves different problems.

❌ BASE does not eliminate replication or synchronization.

---

# Practice

1. Expand BASE.
2. Compare ACID and BASE.
3. Explain eventual consistency.
4. Give applications where BASE is preferred.

---

# Revision Notes

- BASE = Basically Available, Soft State, Eventual Consistency
- Availability prioritized
- Eventual consistency
- Distributed systems

---

# Memory Trick

**BASE**

**B** = Basically Available

**A** = Always changing (Soft State)

**S** = Same eventually (Eventual Consistency)

---

# Final Takeaway

BASE is the foundation of many modern NoSQL databases. By relaxing immediate consistency requirements, it enables highly available, fault-tolerant, and horizontally scalable systems. Understanding BASE alongside ACID is essential for selecting the right database architecture for different workloads.

---

# Quick Interview Cheat Sheet

| Question | Answer |
|----------|--------|
| BASE stands for? | Basically Available, Soft State, Eventual Consistency |
| Opposite model? | ACID |
| Immediate consistency? | No |
| Main benefit? | Availability and scalability |
| Used by? | Many NoSQL databases |
