# Part 2: Database Architecture

# Lesson 3: Three-Tier Architecture

## Learning Objectives
- Understand the concept of three-tier architecture.
- Learn the role of presentation, application, and database layers.
- Explore advantages, disadvantages, and real-world applications.

## Introduction
Three-tier architecture is the most widely used database architecture in modern applications. It separates the system into three independent layers, making applications more secure, scalable, and easier to maintain.

## Architecture

```
+----------------------+
| Presentation Layer   |
| (User Interface)     |
+----------+-----------+
           |
           v
+----------------------+
| Application Layer    |
| (Business Logic)     |
+----------+-----------+
           |
           v
+----------------------+
| Database Layer       |
| (DBMS & Data)        |
+----------------------+
```

## Components

### 1. Presentation Layer
- User interface
- Accepts user input
- Displays output

### 2. Application Layer
- Implements business rules
- Validates user input
- Communicates with the database

### 3. Database Layer
- Stores data
- Executes SQL queries
- Maintains integrity and security

## Working
1. User sends a request through the UI.
2. The application layer validates and processes the request.
3. SQL queries are sent to the database.
4. The database returns the requested data.
5. The application formats the response.
6. The presentation layer displays the result.

## Characteristics
- Layered architecture
- Better security
- High scalability
- Easier maintenance
- Supports distributed systems

## Advantages
- Strong security
- Easy maintenance
- Reusable business logic
- Better scalability
- Improved performance

## Disadvantages
- More complex to develop
- Higher deployment cost
- Additional communication overhead

## Real-World Examples
- Online Banking Systems
- E-commerce Websites
- University Management Systems
- Hospital Management Systems
- ERP and CRM Applications

## Two-Tier vs Three-Tier

| Feature | Two-Tier | Three-Tier |
|---------|----------|------------|
| Business Logic | Client | Application Server |
| Security | Moderate | High |
| Scalability | Moderate | Excellent |
| Maintenance | Difficult | Easy |
| Enterprise Usage | Limited | Extensive |

## Interview Questions
1. What is three-tier architecture?
2. Explain the three layers.
3. Why is an application layer required?
4. List the advantages of three-tier architecture.
5. Why is it preferred for enterprise applications?

## Key Takeaways
- Three-tier architecture separates presentation, business logic, and database.
- It improves scalability, maintainability, and security.
- It is the standard architecture used in modern enterprise applications.
