
# Chapter 11 – Three-Schema Architecture

## Learning Objectives

After completing this chapter, you will be able to:

- Understand the ANSI/SPARC Three-Schema Architecture.
- Explain the External, Conceptual, and Internal levels.
- Understand Data Independence and its types.
- Explain schema and instance.
- Draw the Three-Schema Architecture diagram.
- Answer interview questions confidently.

---

# 1. Introduction

One of the biggest challenges in database systems is ensuring that changes made to the database do not affect all users and applications.

To solve this problem, the **ANSI/SPARC Three-Schema Architecture** divides a database into three different levels of abstraction.

This architecture separates how users view data from how the data is physically stored.

---

# 2. What is a Schema?

A **schema** is the logical blueprint or structure of a database.

It defines:

- Tables
- Columns
- Data types
- Relationships
- Constraints
- Views

### Example

Student Table

| StudentID | Name | Department |
|------------|------|------------|
| INT | VARCHAR | VARCHAR |

The above structure is part of the database schema.

---

# 3. What is an Instance?

An **instance** is the actual data stored in the database at a particular moment.

### Example

| StudentID | Name | Department |
|------------|------|------------|
| 101 | Alice | CSE |
| 102 | Bob | IT |

Schema rarely changes, while instances change frequently.

---

# 4. Three-Schema Architecture

The architecture consists of three levels:

1. External Level
2. Conceptual Level
3. Internal Level

---

# 5. External Level (View Level)

The external level is the highest level of abstraction.

It defines how individual users view the database.

Different users may have different views of the same database.

### Example

A college database:

- Student sees marks.
- Faculty sees attendance and marks.
- Accounts department sees fee details.

Each user sees only the information required for their job.

### Advantages

- Security
- Simplicity
- Personalized views

---

# 6. Conceptual Level (Logical Level)

The conceptual level describes the complete logical structure of the database.

It includes:

- Entities
- Relationships
- Constraints
- Data types

This level hides physical storage details.

### Example

A university database contains:

- Students
- Courses
- Faculty
- Departments
- Results

The conceptual schema defines how these entities relate to one another.

---

# 7. Internal Level (Physical Level)

The internal level describes how data is physically stored.

It includes:

- Storage structures
- Indexes
- File organization
- Compression
- Encryption
- Storage blocks

Database administrators mainly work at this level.

---

# 8. Three-Schema Architecture Diagram

```
                 Users
                   │
        ┌──────────┴──────────┐
        │                     │
        ▼                     ▼
 External View 1      External View 2
        │                     │
        └──────────┬──────────┘
                   ▼
         Conceptual Schema
                   │
                   ▼
          Internal Schema
                   │
                   ▼
          Physical Storage
```

---

# 9. Data Independence

Data Independence means changes at one level should not affect other levels.

This is one of the biggest advantages of the Three-Schema Architecture.

---

# 10. Types of Data Independence

## 10.1 Physical Data Independence

Changes in physical storage do not affect the conceptual schema.

### Examples

- Changing indexes
- Moving files
- Compression
- Partitioning

Applications continue to work without modification.

---

## 10.2 Logical Data Independence

Changes in the conceptual schema do not affect external views.

### Examples

- Adding new columns
- Adding new tables
- Creating relationships

Users continue accessing their required data without changing applications.

---

# 11. Physical vs Logical Data Independence

| Physical | Logical |
|----------|---------|
| Internal → Conceptual | Conceptual → External |
| Easier to achieve | More difficult |
| Storage changes | Structure changes |
| More common | Less common |

---

# 12. Advantages of Three-Schema Architecture

- Data Independence
- Better Security
- Multiple User Views
- Easier Maintenance
- Better Scalability
- Reduced Application Changes
- Improved Flexibility

---

# 13. Real-World Example

## Banking System

### Customer View

- Balance
- Transactions

### Employee View

- Customer Information
- Account Details

### DBA View

- Storage
- Indexes
- Backups
- Performance

All users interact with the same database but see different information.

---

# 14. Common Interview Questions

1. What is Three-Schema Architecture?
2. Explain the three levels.
3. What is schema?
4. What is an instance?
5. Explain Physical Data Independence.
6. Explain Logical Data Independence.
7. Why is Three-Schema Architecture important?

---

# 15. MCQs

### 1. Which level interacts directly with users?

A. Internal

B. External

C. Physical

D. Storage

**Answer:** B

---

### 2. Which level hides physical storage?

A. Internal

B. Conceptual

C. Disk

D. File

**Answer:** B

---

### 3. Which type of data independence is easier to achieve?

A. Logical

B. Physical

C. Conceptual

D. External

**Answer:** B

---

# 16. Practice Exercises

1. Draw the Three-Schema Architecture.
2. Explain the difference between schema and instance.
3. Differentiate logical and physical data independence.
4. Explain the architecture using a banking example.
5. List five advantages of the Three-Schema Architecture.

---

# 17. Memory Trick

Remember **ECI**

- **E** = External
- **C** = Conceptual
- **I** = Internal

For Data Independence:

**PL**

- **P** = Physical (Internal → Conceptual)
- **L** = Logical (Conceptual → External)

---

# 18. Chapter Summary

The Three-Schema Architecture separates a database into External, Conceptual, and Internal levels to provide abstraction, flexibility, and data independence. It allows different users to have customized views while shielding applications from changes in database structure and physical storage. Understanding this architecture is essential for database design and is one of the most frequently asked topics in DBMS interviews.
