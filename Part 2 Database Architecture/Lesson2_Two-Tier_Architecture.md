# Part 2: Database Architecture

# Lesson 2: Two-Tier Architecture

## Learning Objectives
- Understand the two-tier architecture.
- Learn how clients communicate directly with a database server.
- Explore advantages, disadvantages, use cases, and interview questions.

## Introduction
Two-Tier Architecture is a client-server architecture where the client application communicates directly with the database server. Business logic is generally implemented on the client side, while the database server stores and manages the data.

## Architecture
```
+-------------+      SQL Queries      +----------------+
| Client App  | <-------------------> | Database Server|
+-------------+                       +----------------+
```

## Components
- Client Application
- Database Server
- Network Connection

## Working
1. User interacts with the client application.
2. The client sends SQL queries to the database server.
3. The database processes the request.
4. Results are returned to the client.

## Characteristics
- Direct client-to-database communication
- Simple client-server model
- Suitable for small and medium applications
- Faster than file-based systems

## Advantages
- Better security than one-tier architecture
- Supports multiple users
- Centralized data storage
- Easier data management

## Disadvantages
- Business logic resides on clients
- Performance degrades with many users
- Difficult client maintenance
- Limited scalability

## Real-World Examples
- Banking branch software
- College management systems
- Inventory management
- Desktop ERP applications

## One-Tier vs Two-Tier

| Feature | One-Tier | Two-Tier |
|---------|----------|----------|
| Database Location | Local | Remote Server |
| Network | Not Required | Required |
| Multi-user Support | Limited | Good |
| Scalability | Low | Moderate |
| Security | Basic | Better |

## Interview Questions
1. What is a two-tier architecture?
2. Explain the role of the database server.
3. What are the advantages over one-tier architecture?
4. Why is it called client-server architecture?
5. Give two real-world examples.

## Key Takeaways
- Two-tier architecture separates the client and database.
- Clients communicate directly with the database server.
- Suitable for small to medium-sized organizations.
- Easy to develop but has scalability limitations.
