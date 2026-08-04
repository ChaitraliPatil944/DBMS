# Lesson 255 - Cassandra

**Part:** Part 18 – NoSQL

**Difficulty:** Intermediate → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐☆  
**Estimated Reading Time:** 70 Minutes

---

# Learning Objectives

- Understand Apache Cassandra.
- Learn Cassandra's architecture.
- Understand Keyspaces, Tables, and Partitions.
- Learn replication and consistency levels.
- Perform basic CQL operations.
- Answer Cassandra interview questions.

---

# 1. Introduction

**Apache Cassandra** is a distributed, column-family NoSQL database designed for handling massive amounts of data across multiple servers with no single point of failure.

It is known for:

- High availability
- Fault tolerance
- Horizontal scalability
- Fast writes
- Eventual consistency

---

# 2. Key Features

- Peer-to-peer architecture
- No master node
- Automatic replication
- Linear scalability
- Distributed storage
- Tunable consistency

---

# 3. Cassandra Architecture

```text
           Client
              │
      ┌───────┼────────┐
      │       │        │
    Node1   Node2    Node3
      │       │        │
      └───────┼────────┘
         Data Replication
```

Every node has equal responsibility.

---

# 4. Data Model

Hierarchy:

```text
Cluster
   │
Keyspace
   │
Table
   │
Rows
```

---

# 5. Key Concepts

## Keyspace

Equivalent to a database.

```sql
CREATE KEYSPACE Company;
```

---

## Table

Stores rows and columns.

```sql
CREATE TABLE Employee(
EmployeeID INT,
Name TEXT,
PRIMARY KEY(EmployeeID)
);
```

---

## Partition Key

Determines which node stores the data.

A good partition key distributes data evenly.

---

## Clustering Column

Determines the order of rows inside a partition.

---

# 6. CQL (Cassandra Query Language)

## Insert

```sql
INSERT INTO Employee(EmployeeID,Name)
VALUES(1,'Alice');
```

## Read

```sql
SELECT *
FROM Employee;
```

## Update

```sql
UPDATE Employee
SET Name='Bob'
WHERE EmployeeID=1;
```

## Delete

```sql
DELETE
FROM Employee
WHERE EmployeeID=1;
```

---

# 7. Replication

Replication ensures copies of data exist on multiple nodes.

```text
Node A
 │
 ├── Replica
 ├── Replica
 └── Replica
```

Replication improves:

- Availability
- Fault tolerance

---

# 8. Consistency Levels

Examples:

- ONE
- TWO
- THREE
- QUORUM
- ALL

Higher consistency generally increases latency.

---

# 9. Read and Write Path

```text
Client
   │
Coordinator Node
   │
Partition Key
   │
Replica Nodes
   │
Response
```

---

# 10. SQL vs Cassandra

| SQL | Cassandra |
|------|-----------|
|Database|Keyspace|
|Table|Table|
|Primary Key|Partition + Clustering Keys|
|Vertical Scaling|Horizontal Scaling|
|Strong ACID|Eventual/Tunable Consistency|

---

# 11. Real-World Uses

- Netflix
- Apple
- Uber
- Instagram
- Discord

Used for:

- Time-series data
- Messaging
- IoT
- Analytics

---

# 12. Advantages

- No single point of failure
- Massive scalability
- High write throughput
- Excellent availability
- Automatic replication

---

# 13. Limitations

- Limited joins
- Query-driven data modeling
- More storage due to denormalization
- Complex schema design

---

# Performance Notes

- Optimized for write-heavy workloads.
- Excellent for globally distributed systems.
- Handles petabytes of data.
- Designed for continuous availability.

---

# Interview Insights ⭐

### Why is Cassandra called masterless?

Every node is equal and can accept client requests.

### What is a Partition Key?

It determines which node stores the row.

### Why is Cassandra fast?

Because writes are optimized and distributed across multiple nodes.

---

# Interview Traps 🚨

- Cassandra is not a relational database.
- Tables are designed around queries.
- Denormalization is expected, not avoided.

---

# Practice

1. Create a keyspace.
2. Create a table.
3. Insert records.
4. Query data.
5. Explain the role of a partition key.

---

# Revision Notes

- Column-family database
- Keyspace
- Partition key
- Clustering column
- Peer-to-peer architecture
- Tunable consistency

---

# Memory Trick

**CASSANDRA**

**C** = Column Family

**A** = Always Available

**S** = Scalable

**S** = Shared Nothing

---

# Final Takeaway

Apache Cassandra is a highly scalable, distributed NoSQL database built for applications requiring continuous availability and high write throughput. Its masterless architecture, automatic replication, and tunable consistency make it ideal for cloud-native systems handling massive datasets across multiple geographic regions.

---

# Quick Interview Cheat Sheet

| Question | Answer |
|----------|--------|
| Database type? | Column-Family |
| Database equivalent? | Keyspace |
| Master node? | None |
| Scaling? | Horizontal |
| Partition Key? | Determines data placement |
| Consistency? | Tunable |
