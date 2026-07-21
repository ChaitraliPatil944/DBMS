# Lesson 252 - CAP Theorem

**Part:** Part 18 – NoSQL

**Difficulty:** Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 60 Minutes

---

# Learning Objectives

- Understand the CAP Theorem.
- Explain Consistency, Availability, and Partition Tolerance.
- Identify trade-offs in distributed systems.
- Relate CAP to popular NoSQL databases.
- Answer interview questions confidently.

---

# 1. Introduction

The **CAP Theorem**, proposed by Eric Brewer, states that a distributed database cannot simultaneously guarantee all three of the following during a network partition:

- **C** - Consistency
- **A** - Availability
- **P** - Partition Tolerance

When a partition occurs, a system must choose between Consistency and Availability.

---

# 2. The Three Properties

## Consistency (C)

Every client sees the same data after an update.

```text
Write → All users read latest value
```

Example: Banking balances.

---

## Availability (A)

Every request receives a response, even if some nodes have stale data.

```text
Request
   │
Response Always Returned
```

Example: Social media feeds.

---

## Partition Tolerance (P)

The system continues working even when communication between nodes fails.

```text
Node A  X  Node B
(Network Failure)

System Continues
```

---

# 3. Why Partition Tolerance Matters

In distributed systems, network failures are inevitable.

Because partitions cannot be completely avoided, modern distributed databases generally assume **P** is mandatory.

---

# 4. CAP Triangle

```text
        Consistency
            /\
           /  \
          /    \
Availability----Partition
```

During a partition, only **CP** or **AP** can be achieved.

---

# 5. CP Systems

Prioritize:

- Consistency
- Partition Tolerance

May reject requests until data is synchronized.

Examples:

- MongoDB (configurable)
- HBase
- ZooKeeper

Suitable for:

- Banking
- Inventory
- Financial systems

---

# 6. AP Systems

Prioritize:

- Availability
- Partition Tolerance

Data eventually becomes consistent.

Examples:

- Cassandra
- DynamoDB (configurable)
- Riak

Suitable for:

- Social media
- Streaming
- Messaging

---

# 7. CA Systems

Consistency + Availability are possible only when partitions do not exist.

Traditional single-server relational databases approximate CA.

---

# 8. CAP in Action

Imagine two data centers.

```text
User A
  │
Node 1

XXXX Network Failure XXXX

Node 2
  │
User B
```

Choices:

- Wait for synchronization (CP)
- Continue serving requests (AP)

---

# 9. Real-World Examples

| Application | Preferred Model |
|-------------|-----------------|
| Banking | CP |
| Hospital Records | CP |
| WhatsApp Presence | AP |
| Facebook Feed | AP |
| Netflix Recommendations | AP |

---

# 10. CAP vs ACID

| CAP | ACID |
|-----|------|
| Distributed systems | Transactions |
| Network failures | Database correctness |
| C,A,P trade-offs | Atomicity, Consistency, Isolation, Durability |

---

# 11. Performance Notes

- CP systems may have higher latency.
- AP systems provide better uptime.
- Partition tolerance is essential for distributed databases.

---

# Interview Insights ⭐

### Can a system have C, A and P together?

No, not during a network partition.

### Which property is usually non-negotiable?

Partition Tolerance.

### Why do NoSQL databases often choose AP?

To maximize availability in globally distributed systems.

---

# Interview Traps 🚨

❌ CAP does not say databases permanently choose only two properties.

❌ Without a partition, systems may provide both consistency and availability.

❌ CAP is about distributed systems, not standalone databases.

---

# Practice

1. Define CAP Theorem.
2. Explain CP vs AP.
3. Why is Partition Tolerance important?
4. Give two CP and two AP databases.

---

# Revision Notes

- CAP = Consistency, Availability, Partition Tolerance
- During partition choose CP or AP
- Modern distributed databases assume Partition Tolerance

---

# Memory Trick

**CAP**

**C** = Correct Data

**A** = Always Respond

**P** = Partition Survives

---

# Final Takeaway

The CAP Theorem explains the fundamental trade-offs in distributed databases. Since network partitions are unavoidable, modern systems typically prioritize Partition Tolerance and then balance either Consistency (CP) or Availability (AP) according to business requirements.

---

# Quick Interview Cheat Sheet

| Question | Answer |
|----------|--------|
| Who proposed CAP? | Eric Brewer |
| Full form? | Consistency, Availability, Partition Tolerance |
| During partition choose? | CP or AP |
| Banking prefers? | CP |
| Social media prefers? | AP |
