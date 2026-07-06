# Part 2: Database Architecture

# Lesson 1: One-Tier Architecture

## Learning Objectives
- Understand one-tier architecture.
- Learn how the database, application, and user exist on the same machine.
- Identify advantages, disadvantages, and interview questions.

## Introduction
A **One-Tier Architecture** is the simplest DBMS architecture where the user, application, and database are present on the same computer. There is no separate database server.

## Architecture
```
User
 |
Application
 |
Database
(All on the same machine)
```

## Working
1. User interacts with the application.
2. The application directly accesses the local database.
3. Results are displayed immediately.

## Characteristics
- Single computer
- No network communication
- Simple deployment
- Best for standalone applications

## Advantages
- Easy to install
- Fast local performance
- Low cost
- Easy maintenance

## Disadvantages
- Limited scalability
- Weak security
- Poor multi-user support
- Unsuitable for enterprise systems

## Real-world Examples
- SQLite
- Microsoft Access
- Student projects
- Offline desktop applications

## Interview Questions
1. What is one-tier architecture?
2. Where is the database located?
3. State two advantages.
4. Why is it not used in large organizations?

## Summary
One-tier architecture combines the user interface, business logic, and database into one system. It is ideal for learning and small standalone applications but not for large-scale production systems.
