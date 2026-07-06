
# Chapter 7 – Types of Databases

## Learning Objectives

After completing this chapter, you will be able to:

- Understand the different types of databases.
- Identify where each database type is used.
- Compare SQL and NoSQL databases.
- Select an appropriate database for a given application.
- Answer interview questions related to database types.

---

# 1. Introduction

Databases are designed to meet different storage and application requirements. Over time, multiple database models have been developed to handle structured, semi-structured, and unstructured data efficiently.

Choosing the right database depends on the application's requirements, scalability, performance, and data structure.

---

# 2. Hierarchical Database

A hierarchical database organizes data in a tree-like structure where each child has only one parent.

### Characteristics

- Parent-child relationship
- One-to-many relationships
- Fast traversal
- Rigid structure

### Advantages

- Simple structure
- High performance for hierarchical data

### Disadvantages

- Difficult to modify
- Limited flexibility

### Applications

- Organization charts
- File systems
- XML documents

---

# 3. Network Database

A network database allows a record to have multiple parent records.

### Characteristics

- Many-to-many relationships
- Graph-like structure

### Advantages

- More flexible than hierarchical databases
- Efficient for complex relationships

### Disadvantages

- Complex implementation
- Difficult maintenance

### Applications

- Airline reservation systems
- Telecommunications

---

# 4. Relational Database (RDBMS)

A relational database stores data in tables consisting of rows and columns.

### Characteristics

- Tables
- SQL support
- Primary keys
- Foreign keys
- Relationships

### Popular Examples

- MySQL
- PostgreSQL
- Oracle Database
- Microsoft SQL Server
- SQLite

### Applications

- Banking
- Hospital Management
- ERP
- E-commerce

---

# 5. Object-Oriented Database (OODBMS)

An object-oriented database stores data as objects.

### Characteristics

- Objects
- Classes
- Inheritance
- Encapsulation

### Applications

- CAD software
- Multimedia systems
- Scientific applications

---

# 6. Object-Relational Database (ORDBMS)

Combines relational databases with object-oriented concepts.

### Features

- SQL support
- User-defined data types
- Objects within relational tables

### Example

- PostgreSQL

---

# 7. NoSQL Databases

NoSQL databases are designed for large-scale, distributed, and rapidly changing data.

### Advantages

- Horizontal scalability
- High performance
- Flexible schema

### Disadvantages

- Limited joins
- Eventual consistency in some systems

---

## 7.1 Key-Value Database

Stores data as key-value pairs.

Examples

- Redis
- Amazon DynamoDB

Applications

- Caching
- Session storage

---

## 7.2 Document Database

Stores data as JSON or BSON documents.

Examples

- MongoDB
- CouchDB

Applications

- Content management
- E-commerce
- Mobile applications

---

## 7.3 Column-Family Database

Stores data in columns instead of rows.

Examples

- Apache Cassandra
- HBase

Applications

- Big Data
- Analytics

---

## 7.4 Graph Database

Stores data as nodes and relationships.

Examples

- Neo4j
- Amazon Neptune

Applications

- Social networks
- Recommendation systems
- Fraud detection

---

# 8. Distributed Database

A distributed database stores data across multiple physical locations while appearing as a single database.

### Advantages

- High availability
- Fault tolerance
- Better scalability

### Applications

- Banking
- Cloud services

---

# 9. Centralized Database

All data is stored at one central location.

### Advantages

- Easier management
- Better consistency

### Disadvantages

- Single point of failure

---

# 10. Cloud Database

Cloud databases are hosted on cloud infrastructure.

### Advantages

- Automatic scaling
- Backup
- High availability

### Popular Services

- Amazon RDS
- Google Cloud SQL
- Azure SQL Database

---

# 11. Time-Series Database

Designed for time-stamped data.

### Examples

- InfluxDB
- TimescaleDB

### Applications

- IoT
- Weather forecasting
- Monitoring systems

---

# 12. SQL vs NoSQL

| SQL | NoSQL |
|------|--------|
| Structured | Flexible schema |
| Tables | Documents/Key-Value/Graph |
| Vertical Scaling | Horizontal Scaling |
| ACID | BASE (often) |
| SQL Queries | Database-specific APIs or query languages |

---

# 13. Comparison Table

| Database Type | Best Used For |
|---------------|---------------|
| Hierarchical | Tree structures |
| Network | Complex relationships |
| Relational | Business applications |
| Object-Oriented | Multimedia/CAD |
| Object-Relational | Enterprise applications |
| Key-Value | Caching |
| Document | Web applications |
| Column-Family | Big Data |
| Graph | Social networks |
| Distributed | Global systems |
| Cloud | Modern scalable applications |
| Time-Series | IoT and monitoring |

---

# 14. Real-World Examples

| Application | Suitable Database |
|--------------|------------------|
| Banking | Relational |
| Facebook Friend Network | Graph |
| Netflix Cache | Key-Value |
| Amazon Product Catalog | Document |
| Weather Sensors | Time-Series |

---

# 15. Interview Questions

1. What are the different types of databases?
2. What is the difference between SQL and NoSQL?
3. When would you use a graph database?
4. What is a document database?
5. Explain distributed databases.
6. Give examples of cloud databases.
7. What is the difference between hierarchical and network databases?

---

# 16. MCQs

### 1. Which database stores data in tables?

A. Graph Database

B. Relational Database

C. Document Database

D. Key-Value Database

**Answer:** B

---

### 2. Which database is best for social networks?

A. Graph Database

B. Hierarchical Database

C. Relational Database

D. File System

**Answer:** A

---

### 3. MongoDB is a:

A. Relational Database

B. Document Database

C. Graph Database

D. Time-Series Database

**Answer:** B

---

# 17. Practice Exercises

1. Compare SQL and NoSQL databases.
2. List five applications of graph databases.
3. Explain distributed databases with examples.
4. Create a table comparing all major database types.
5. Identify the best database type for an online shopping website and justify your answer.

---

# 18. Memory Trick

Remember **HR ON DCT**

- **H** – Hierarchical
- **N** – Network
- **R** – Relational
- **O** – Object-Oriented
- **N** – NoSQL
- **D** – Distributed
- **C** – Cloud
- **T** – Time-Series

---

# 19. Chapter Summary

- Databases are available in different models to address different application needs.
- Relational databases remain the most common choice for structured business data.
- NoSQL databases provide flexibility and scalability for modern web applications.
- Specialized databases such as graph and time-series databases solve domain-specific problems efficiently.
- Selecting the right database depends on data structure, scalability, consistency, and application requirements.
