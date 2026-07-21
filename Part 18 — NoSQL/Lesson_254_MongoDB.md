# Lesson 254 - MongoDB

**Part:** Part 18 – NoSQL

**Difficulty:** Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 75 Minutes

---

# Learning Objectives

- Understand MongoDB architecture.
- Learn collections, documents, and BSON.
- Perform CRUD operations.
- Understand indexing and replication basics.
- Answer MongoDB interview questions.

---

# 1. Introduction

**MongoDB** is a popular **Document-Oriented NoSQL Database**.

Instead of storing data in rows and columns, MongoDB stores data as **JSON-like BSON documents**.

It is widely used in cloud-native, web, mobile, AI, and big-data applications.

---

# 2. Features

- Document database
- Flexible schema
- Horizontal scaling
- High availability
- Automatic replication
- Rich indexing
- Aggregation framework

---

# 3. MongoDB Architecture

```text
Application
      │
MongoDB Driver
      │
MongoDB Server
      │
Database
      │
Collection
      │
Document (BSON)
```

---

# 4. Database Structure

```text
Database
 ├── users
 ├── orders
 └── products

Collection
 ├── Document 1
 ├── Document 2
 └── Document 3
```

---

# 5. BSON

MongoDB stores documents internally as **BSON (Binary JSON)**.

Example:

```json
{
  "_id": 1,
  "name": "Alice",
  "age": 22,
  "skills": ["Java","MongoDB"]
}
```

Advantages:

- Faster parsing
- Supports additional data types
- Efficient storage

---

# 6. CRUD Operations

## Create

```javascript
db.users.insertOne({
 name:"Alice",
 age:22
})
```

## Read

```javascript
db.users.find()

db.users.find({age:22})
```

## Update

```javascript
db.users.updateOne(
 {name:"Alice"},
 {$set:{age:23}}
)
```

## Delete

```javascript
db.users.deleteOne({name:"Alice"})
```

---

# 7. Query Operators

```javascript
$gt
$lt
$gte
$lte
$in
$and
$or
```

Example:

```javascript
db.users.find({
 age:{$gt:20}
})
```

---

# 8. Indexing

```javascript
db.users.createIndex({
 name:1
})
```

Benefits:

- Faster queries
- Better sorting
- Efficient filtering

---

# 9. Replication

MongoDB uses **Replica Sets**.

```text
Primary
 │
 ├── Secondary
 └── Secondary
```

Primary accepts writes.

Secondaries replicate data.

---

# 10. Sharding

For very large databases:

```text
Router
 │
 ├── Shard 1
 ├── Shard 2
 └── Shard 3
```

Data is distributed across multiple servers.

---

# 11. SQL vs MongoDB

| SQL | MongoDB |
|------|----------|
|Table|Collection|
|Row|Document|
|Column|Field|
|JOIN|Embedding/References|
|Schema|Flexible|

---

# 12. Real-World Uses

- E-commerce catalogs
- Chat applications
- CMS
- IoT
- Analytics
- AI applications

Companies:

- Adobe
- eBay
- Coinbase
- Bosch

---

# 13. Advantages

- Flexible schema
- Fast development
- Horizontal scaling
- Rich query language
- High availability

---

# 14. Limitations

- Complex joins are limited
- Data duplication may occur
- Transactions are available but relational databases remain preferable for some workloads

---

# Performance Notes

- Excellent read performance
- Powerful indexing
- Aggregation pipeline
- Built for distributed deployments

---

# Interview Insights ⭐

### Why BSON instead of JSON?

BSON is binary, compact, and supports additional data types.

### Collection vs Document?

A collection contains documents, similar to a table containing rows.

### Can MongoDB support transactions?

Yes. Modern MongoDB versions support multi-document ACID transactions.

---

# Interview Traps 🚨

- MongoDB is **not** schema-less. It has a flexible schema.
- Collections do not require identical document structures.
- MongoDB supports indexes just like relational databases.

---

# Practice

1. Create a collection.
2. Insert three documents.
3. Query using $gt.
4. Update one document.
5. Create an index.

---

# Revision Notes

- Document database
- BSON storage
- Collection = Table
- Document = Row
- Replica Sets
- Sharding

---

# Memory Trick

**MongoDB**

**M** = Multiple documents

**O** = Object (BSON)

**N** = NoSQL

**G** = Good scalability

---

# Final Takeaway

MongoDB is the most widely used document-oriented NoSQL database. Its flexible schema, BSON storage, indexing, replication, and sharding capabilities make it an excellent choice for scalable modern applications that require rapid development and distributed deployment.

---

# Quick Interview Cheat Sheet

| Question | Answer |
|----------|--------|
| Database type? | Document Database |
| Storage format? | BSON |
| Table equivalent? | Collection |
| Row equivalent? | Document |
| Replication? | Replica Set |
| Horizontal scaling? | Sharding |
