# Part 2: Database Architecture

# Lesson 4: Client–Server Model

## Learning Objectives
- Understand the Client–Server Model.
- Learn the roles of clients and servers.
- Understand request-response communication.
- Explore advantages, disadvantages, and real-world applications.

## Introduction
The Client–Server Model is a distributed computing architecture in which a client requests services or resources from a server. The server processes the request and sends the appropriate response back to the client. Most modern database applications use this architecture.

## Basic Architecture

```
+-----------+        Request        +------------------+
|  Client   | --------------------> | Database Server  |
| (Browser/ | <-------------------- |  (DBMS)          |
| Desktop)  |        Response       +------------------+
+-----------+
```

## Components

### 1. Client
- User interface
- Accepts user input
- Sends requests to the server
- Displays results

### 2. Server
- Hosts the database
- Executes SQL queries
- Performs authentication
- Manages transactions and security

### 3. Network
- Connects clients and servers
- Transfers requests and responses
- Can be LAN, WAN, or the Internet

## Working Process
1. The user interacts with the client application.
2. The client sends a request to the database server.
3. The server validates the request.
4. SQL queries are executed.
5. The server returns the requested data.
6. The client displays the results.

## Characteristics
- Centralized database
- Multiple clients can connect simultaneously
- Data consistency
- Secure access control
- Network-based communication

## Advantages
- Centralized data management
- Better security
- Easy backup and recovery
- Supports multiple users
- Easier maintenance

## Disadvantages
- Server failure affects all clients
- Network dependency
- Higher infrastructure cost
- Performance depends on server capacity

## Real-World Examples
- Banking Systems
- E-commerce Websites
- University ERP Systems
- Railway Reservation Systems
- Hospital Management Systems

## Client vs Server

| Feature | Client | Server |
|---------|--------|--------|
| Role | Requests Services | Provides Services |
| Processing | User Interaction | Data Processing |
| Stores Database | No | Yes |
| Executes SQL | Sends Queries | Processes Queries |

## Interview Questions
1. What is the Client–Server Model?
2. Explain the responsibilities of a client.
3. Explain the responsibilities of a database server.
4. What are the advantages of the Client–Server Model?
5. Give three real-world examples.

## Key Takeaways
- The Client–Server Model is the foundation of modern database applications.
- Clients request services, while servers process requests and manage data.
- It provides better scalability, security, and centralized management than standalone systems.
