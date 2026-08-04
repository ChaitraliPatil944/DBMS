# Lesson 251 - Introduction to NoSQL

**Part:** Part 18 – NoSQL

**Difficulty:** Beginner → Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 70 Minutes

---

# Learning Objectives

- Understand what NoSQL is.
- Explain why NoSQL was introduced.
- Compare SQL and NoSQL.
- Identify the four NoSQL database types.
- Recognize real-world use cases.

---

# 1. What is NoSQL?

**NoSQL (Not Only SQL)** refers to databases designed for large-scale, distributed, and flexible data storage. They complement relational databases rather than replacing them.

---

# 2. Why NoSQL?

Traditional RDBMS systems become difficult to scale for internet-scale applications.

NoSQL addresses:

- Massive scalability
- Flexible schema
- High availability
- Big data
- Cloud-native applications

---

# 3. Evolution

```text
Files
  │
  ▼
Relational Databases
  │
  ▼
Internet Scale
  │
  ▼
NoSQL
```

---

# 4. Characteristics

- Flexible schema
- Horizontal scaling
- Distributed architecture
- High availability
- Fast reads and writes

---

# 5. Types of NoSQL

## Key-Value
Examples: Redis, Riak

## Document
Examples: MongoDB, CouchDB

## Column-Family
Examples: Cassandra, HBase

## Graph
Examples: Neo4j, Amazon Neptune

---

# 6. SQL vs NoSQL

| Feature | SQL | NoSQL |
|---|---|---|
| Schema | Fixed | Flexible |
| Scaling | Vertical | Horizontal |
| Data Model | Tables | Multiple Models |
| Transactions | ACID | Often BASE |
| Best For | Structured Data | Large Distributed Data |

---

# 7. Architecture

```text
Application
     │
 NoSQL Cluster
 ┌───┼───┐
Node Node Node
```

---

# 8. CRUD Example (MongoDB)

```javascript
db.users.insertOne({name:"Alice"})
db.users.find({name:"Alice"})
db.users.updateOne({name:"Alice"},{$set:{age:23}})
db.users.deleteOne({name:"Alice"})
```

---

# 9. Advantages

- Flexible schema
- Easy scaling
- High performance
- Cloud friendly

---

# 10. Limitations

- Limited joins
- Data duplication
- Product-specific features

---

# 11. Real-World Usage

| Company | Database |
|---|---|
| Netflix | Cassandra |
| Amazon | DynamoDB |
| GitHub | Redis |
| Facebook | Cassandra |
| Uber | Cassandra |

---

# 12. When to Use NoSQL

Use NoSQL for:

- Big Data
- Real-time systems
- IoT
- Social media
- Gaming
- Streaming

Use SQL for:

- Banking
- ERP
- Inventory
- Accounting

---

# Performance Notes

- Excellent horizontal scalability
- Distributed storage
- High write throughput

---

# Interview Insights ⭐

- NoSQL = Not Only SQL
- SQL and NoSQL are complementary.
- MongoDB is a document database.
- Redis is a key-value database.
- Cassandra is a column-family database.

---

# Interview Traps 🚨

- NoSQL does NOT mean "No SQL".
- NoSQL databases are not always schema-less.
- SQL is not obsolete.

---

# Practice

1. Explain NoSQL.
2. Compare SQL and NoSQL.
3. List the four NoSQL types.
4. Give two NoSQL use cases.

---

# Revision Notes

- Flexible schema
- Horizontal scaling
- Distributed systems
- Four NoSQL models

---

# Memory Trick

**KDCG**

K = Key-Value

D = Document

C = Column-Family

G = Graph

---

# Final Takeaway

NoSQL databases provide scalable and flexible data storage for modern distributed applications. They complement SQL databases and are widely used in cloud computing, big data, and real-time services.

---

# Quick Interview Cheat Sheet

| Question | Answer |
|---|---|
| NoSQL stands for? | Not Only SQL |
| Four models? | Key-Value, Document, Column-Family, Graph |
| Best document DB? | MongoDB |
| Best key-value DB? | Redis |
| Main benefit? | Horizontal scaling |
