# Lesson 270 - DBMS Revision Sheets

**Part:** Part 20 – Interview Preparation

**Difficulty:** Final Revision  
**Interview Frequency:** ⭐⭐⭐⭐⭐

---

# Learning Objectives

- Revise the complete DBMS syllabus quickly.
- Recall important interview concepts.
- Memorize key comparisons and formulas.
- Prepare for last-minute placement revision.

---

# 1. DBMS One-Page Summary

- DBMS manages data efficiently.
- RDBMS stores data in tables with relationships.
- SQL is the standard language for relational databases.
- Transactions ensure reliable data processing.
- Indexes improve search performance.
- Normalization reduces redundancy.
- NoSQL supports scalability and flexible schemas.

---

# 2. SQL Quick Revision

## DDL
- CREATE
- ALTER
- DROP
- TRUNCATE

## DML
- INSERT
- UPDATE
- DELETE
- SELECT

## DCL
- GRANT
- REVOKE

## TCL
- COMMIT
- ROLLBACK
- SAVEPOINT

---

# 3. Keys

| Key | Purpose |
|------|---------|
| Primary Key | Uniquely identifies a row |
| Foreign Key | Maintains relationships |
| Candidate Key | Possible primary key |
| Super Key | Unique identifier |
| Composite Key | Multiple columns |
| Alternate Key | Candidate key not selected |

---

# 4. Joins

- INNER JOIN → Matching rows
- LEFT JOIN → All left rows
- RIGHT JOIN → All right rows
- FULL JOIN → All matching + non-matching
- CROSS JOIN → Cartesian Product
- SELF JOIN → Same table

---

# 5. Normal Forms

- 1NF → Atomic values
- 2NF → Remove partial dependency
- 3NF → Remove transitive dependency
- BCNF → Stronger than 3NF

---

# 6. ACID

- **A**tomicity
- **C**onsistency
- **I**solation
- **D**urability

---

# 7. Isolation Problems

- Dirty Read
- Non-Repeatable Read
- Phantom Read
- Lost Update

---

# 8. Indexes

- Clustered
- Non-Clustered
- Composite
- Covering
- B+ Tree
- Hash Index

---

# 9. NoSQL Snapshot

| Type | Example |
|------|---------|
| Key-Value | Redis |
| Document | MongoDB |
| Column Family | Cassandra |
| Graph | Neo4j |

---

# 10. Distributed Databases

- Replication → Copies data
- Sharding → Splits data
- Partitioning → Divides tables
- Load Balancer → Distributes traffic
- Caching → Faster reads

---

# 11. Data Platforms

| Technology | Best For |
|------------|----------|
| OLTP | Transactions |
| OLAP | Analytics |
| Data Warehouse | Historical reporting |
| Data Lake | Raw big data |

---

# 12. Frequently Confused Topics

| Compare | Difference |
|----------|------------|
| DELETE vs TRUNCATE | DML vs DDL-like operation |
| DROP vs TRUNCATE | Removes object vs removes rows |
| WHERE vs HAVING | Before vs after grouping |
| SQL vs NoSQL | Structured vs flexible |
| Replication vs Sharding | Copies vs splits data |
| Vertical vs Horizontal Scaling | Bigger server vs more servers |

---

# Memory Tricks

## ACID
A C I D

## CAP
Consistency
Availability
Partition Tolerance

## BASE
Basically Available
Soft State
Eventual Consistency

---

# Last-Minute Interview Checklist

- Revise SQL joins
- Practice SQL queries
- Review normalization
- Understand ACID
- Revise indexing
- Learn NoSQL basics
- Compare scaling techniques
- Explain concepts with examples

---

# Final Takeaway

Use this revision sheet the day before an interview to refresh every major DBMS topic in under an hour. Focus on understanding comparisons and explaining concepts clearly rather than memorizing definitions.

---

# Quick Interview Cheat Sheet

| Topic | Must Know |
|--------|-----------|
| SQL | ⭐⭐⭐⭐⭐ |
| Joins | ⭐⭐⭐⭐⭐ |
| Normalization | ⭐⭐⭐⭐☆ |
| Transactions | ⭐⭐⭐⭐⭐ |
| Indexing | ⭐⭐⭐⭐⭐ |
| NoSQL | ⭐⭐⭐⭐☆ |
| Scaling | ⭐⭐⭐⭐☆ |
