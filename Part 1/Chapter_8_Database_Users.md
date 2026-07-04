
# Chapter 8 – Database Users

## Learning Objectives

After completing this chapter, you will be able to:

- Identify the different types of database users.
- Understand the responsibilities of each database user.
- Explain how different users interact with a DBMS.
- Answer interview questions related to database users.

---

# 1. Introduction

A Database Management System (DBMS) is not used by a single person. In a real-world organization, many people interact with the database in different ways depending on their responsibilities.

For example, in a university:
- Students check their grades.
- Faculty upload marks.
- Administrators manage student records.
- Developers build the university portal.
- Database Administrators maintain the database.

Each of these individuals is considered a **database user**.

---

# 2. Types of Database Users

Database users can be broadly classified into the following categories:

1. Database Administrator (DBA)
2. Database Designer
3. System Analyst
4. Application Programmer (Developer)
5. End Users

---

# 3. Database Administrator (DBA)

A **Database Administrator (DBA)** is responsible for the overall management of the database.

### Responsibilities

- Install and configure DBMS software
- Create databases
- Manage users and permissions
- Monitor performance
- Perform backup and recovery
- Ensure database security
- Optimize queries and indexes
- Monitor storage usage
- Maintain availability

### Skills Required

- SQL
- Database tuning
- Security
- Backup and recovery
- Performance optimization

### Real-World Example

A bank DBA ensures that customer accounts remain secure, backups are taken regularly, and the banking database remains available 24/7.

---

# 4. Database Designer

A **Database Designer** creates the structure of the database before development begins.

### Responsibilities

- Analyze business requirements
- Design ER diagrams
- Identify entities and relationships
- Define tables
- Normalize the database
- Select appropriate data types
- Design constraints

### Deliverables

- ER Diagram
- Database Schema
- Table Design

---

# 5. System Analyst

A **System Analyst** bridges the gap between business users and developers.

### Responsibilities

- Gather requirements
- Analyze business processes
- Recommend database solutions
- Prepare system specifications
- Coordinate with developers

### Example

In a hospital management system, the system analyst identifies the data required for patient registration, billing, and appointments.

---

# 6. Application Programmer (Developer)

Application programmers develop software that communicates with the database.

### Responsibilities

- Write SQL queries
- Develop CRUD operations
- Create APIs
- Validate user input
- Handle transactions
- Test database connectivity

### Technologies

- Java
- Python
- C#
- PHP
- Node.js

---

# 7. End Users

End users interact with the database through applications rather than directly using SQL.

End users are divided into four categories.

---

## 7.1 Naïve (Parametric) Users

These users perform predefined tasks using forms or applications.

### Examples

- Bank teller
- Cashier
- Library staff
- Receptionist

---

## 7.2 Casual Users

These users occasionally access the database to retrieve information.

### Examples

- Managers
- Supervisors
- Department Heads

---

## 7.3 Sophisticated Users

These users understand database concepts and often write SQL queries.

### Examples

- Data Analysts
- Data Scientists
- Researchers

---

## 7.4 Specialized Users

These users develop advanced database applications.

### Examples

- AI Engineers
- GIS Experts
- Scientific Researchers

---

# 8. Interaction Between Users

```
Business Users
      │
      ▼
System Analyst
      │
      ▼
Database Designer
      │
      ▼
Application Programmer
      │
      ▼
Database (Managed by DBA)
      │
      ▼
End Users
```

---

# 9. Comparison Table

| User | Primary Responsibility |
|------|-------------------------|
| DBA | Database administration |
| Database Designer | Database design |
| System Analyst | Requirement analysis |
| Application Programmer | Application development |
| Naïve User | Routine operations |
| Casual User | Occasional queries |
| Sophisticated User | Complex querying and analysis |
| Specialized User | Specialized database applications |

---

# 10. Real-World Case Study

## Online Shopping System

### Database Designer
Designs product, customer, order, and payment tables.

### DBA
Maintains security, backups, and performance.

### Developer
Builds the shopping website and mobile application.

### Customer
Places orders using the application.

### Manager
Generates monthly sales reports.

---

# 11. Interview Questions

1. Who is a Database Administrator (DBA)?
2. What are the responsibilities of a DBA?
3. What is the role of a Database Designer?
4. Differentiate Database Designer and DBA.
5. What is the role of a System Analyst?
6. Who are naïve users?
7. What are sophisticated users?
8. Differentiate casual users and sophisticated users.

---

# 12. MCQs

### 1. Who is responsible for backup and recovery?

A. System Analyst

B. Database Designer

C. DBA

D. End User

**Answer:** C

---

### 2. Who designs the database schema?

A. Developer

B. Database Designer

C. Casual User

D. Naïve User

**Answer:** B

---

### 3. Which user typically writes SQL queries for analysis?

A. Naïve User

B. Casual User

C. Sophisticated User

D. Receptionist

**Answer:** C

---

# 13. Practice Exercises

1. Explain the role of a DBA.
2. Differentiate DBA and Database Designer.
3. List all types of database users with examples.
4. Explain the role of a System Analyst.
5. Draw the interaction diagram between database users.

---

# 14. Memory Trick

Remember **DDSAE**

- **D** – Database Administrator
- **D** – Database Designer
- **S** – System Analyst
- **A** – Application Programmer
- **E** – End Users

---

# 15. Chapter Summary

- A DBMS serves multiple users with different responsibilities.
- The DBA manages the database and ensures security, availability, and performance.
- The Database Designer creates the database structure.
- The System Analyst gathers and analyzes business requirements.
- Developers build applications that communicate with the database.
- End users access data through applications for daily operations.
