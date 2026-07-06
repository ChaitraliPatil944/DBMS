# Part 2: Database Architecture

# Lesson 5: Distributed Architecture

## Learning Objectives
- Understand distributed database architecture.
- Learn how data is distributed across multiple locations.
- Explore advantages, challenges, and practical applications.

## Introduction
A **Distributed Database Architecture** stores a single logical database across multiple physical locations connected through a network. Although the data is distributed, it appears as one unified database to users.

## Architecture

```
                +----------------------+
                |   User/Application   |
                +----------+-----------+
                           |
                 -----------------------
                 |          |          |
                 v          v          v
          +-----------+ +-----------+ +-----------+
          | Server A  | | Server B  | | Server C  |
          | Database  | | Database  | | Database  |
          +-----------+ +-----------+ +-----------+
```

## Components
### 1. Client Applications
- Send requests to the distributed database.
- Access data without knowing its physical location.

### 2. Distributed Database Servers
- Store portions or replicas of the database.
- Process local queries.
- Coordinate with other servers when needed.

### 3. Communication Network
- Connects all database servers.
- Transfers queries and data securely.

## Working
1. A client sends a query.
2. The distributed DBMS identifies where the required data resides.
3. Queries are executed on one or more servers.
4. Results are combined.
5. The final result is returned to the client.

## Types of Distributed Databases
### Homogeneous
- Same DBMS at every location.
- Easier to manage.

### Heterogeneous
- Different DBMS products.
- More complex integration.

## Characteristics
- Data stored at multiple sites.
- Appears as a single database.
- Supports distributed query processing.
- High availability.
- Fault tolerance.

## Advantages
- High availability.
- Better reliability.
- Improved scalability.
- Faster local access.
- Reduced communication delays.

## Disadvantages
- Complex design.
- Higher implementation cost.
- Difficult synchronization.
- Security challenges.
- Distributed transaction management is complex.

## Real-World Applications
- Banking networks
- Airline reservation systems
- Global e-commerce platforms
- Healthcare systems
- Multi-branch organizations

## Centralized vs Distributed Database

| Feature | Centralized | Distributed |
|---------|-------------|-------------|
| Data Location | One Site | Multiple Sites |
| Availability | Lower | Higher |
| Scalability | Limited | Excellent |
| Fault Tolerance | Low | High |
| Administration | Easier | More Complex |

## Interview Questions
1. What is a distributed database?
2. Differentiate homogeneous and heterogeneous databases.
3. What are the benefits of data distribution?
4. Why are distributed transactions difficult?
5. Give real-world examples of distributed databases.

## Key Takeaways
- A distributed database stores data across multiple locations while presenting a single logical database.
- It offers high availability, scalability, and fault tolerance.
- It is widely used in modern enterprise and cloud-based applications.
