# Lesson 041 --- Recursive Relationships

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

After this lesson, you will understand:

-   What a Recursive Relationship is
-   Why recursive relationships are needed
-   Unary relationships in depth
-   Types of recursive relationships
-   Self-referencing foreign keys
-   ER diagram notation
-   SQL implementation
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Most relationships connect **different entity types**.

Example:

    Student -------- Enrolls -------- Course

But sometimes an entity is related to **another instance of the same
entity**.

These are called **Recursive Relationships** (also called Self
Relationships or Unary Relationships).

------------------------------------------------------------------------

# 2. What is a Recursive Relationship?

A **Recursive Relationship** occurs when an entity participates in a
relationship with itself.

The relationship is between **different instances** of the **same entity
type**.

Think of it like this:

    Employee
        |
    Manages
        |
    Employee

There is only **one entity type**: Employee.

------------------------------------------------------------------------

# 3. Why Do We Need Recursive Relationships?

Many real-world systems naturally contain hierarchies.

Examples:

-   Employees manage employees.
-   Folders contain folders.
-   Categories contain subcategories.
-   People have parents.
-   Comments reply to comments.

Without recursive relationships, these structures become difficult to
model.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Imagine your family tree.

    Grandparent
          |
       Parent
          |
        Child

Everyone is a **Person**.

The relationship is "Parent Of".

The entity never changes.

------------------------------------------------------------------------

# 5. ER Diagram Representation

            +-----------+
            | Employee  |
            +-----------+
                 ^
                 |
              Manages
                 |
                 v
            +-----------+
            | Employee  |
            +-----------+

One entity participates twice in different roles.

------------------------------------------------------------------------

# 6. Types of Recursive Relationships

    Recursive Relationships
    │
    ├── One-to-One
    ├── One-to-Many
    └── Many-to-Many

------------------------------------------------------------------------

# 7. One-to-One Recursive

Example:

    Person
        |
    Married To
        |
    Person

Business rule:

One person can be married to one person.

------------------------------------------------------------------------

# 8. One-to-Many Recursive

The most common recursive relationship.

Example:

    Manager
       |
    Manages
       |
    Employees

ASCII Diagram

    Manager
       |
      /|\
     / | \
    E1 E2 E3

One manager supervises many employees.

Each employee has one manager.

------------------------------------------------------------------------

# 9. Many-to-Many Recursive

Example:

    Person
       |
    Friends With
       |
    Person

A person can have many friends.

Every friend can also have many friends.

Other examples:

-   Researcher collaborates with Researcher
-   Student mentors Student
-   User follows User

------------------------------------------------------------------------

# 10. SQL Implementation

Employee hierarchy

``` sql
CREATE TABLE Employee (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(100),
    ManagerID INT NULL,
    FOREIGN KEY (ManagerID)
        REFERENCES Employee(EmployeeID)
);
```

Sample Data

  EmployeeID   Name      ManagerID
  ------------ --------- -----------
  1            Alice     NULL
  2            Bob       1
  3            Charlie   1
  4            David     2

Alice manages Bob and Charlie.

Bob manages David.

------------------------------------------------------------------------

# 11. Real-World Examples

## Organization

    Employee
       |
    Manages
       |
    Employee

------------------------------------------------------------------------

## File System

    Folder
       |
    Contains
       |
    Folder

------------------------------------------------------------------------

## Online Shopping

    Category
       |
    Contains
       |
    Subcategory

------------------------------------------------------------------------

## Social Media

    User
       |
    Follows
       |
    User

------------------------------------------------------------------------

## Blog

    Comment
       |
    Replies To
       |
    Comment

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Thinking two boxes mean two entity types.

In recursive relationships, both boxes represent the **same entity
type**.

❌ Creating infinite loops.

Example:

    A manages B
    B manages C
    C manages A

This creates a cycle and should usually be prevented.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is a recursive relationship?
2.  Give three real-world examples.
3.  Why is it also called a unary relationship?

### Intermediate

1.  How is a recursive relationship implemented in SQL?
2.  Explain self-referencing foreign keys.

### Advanced

Design recursive relationships for:

-   Company hierarchy
-   Folder structure
-   Social media followers
-   Product categories

------------------------------------------------------------------------

# 14. Practice Problems

Identify whether a recursive relationship exists.

1.  Employee manages Employee
2.  Student studies Course
3.  Folder contains Folder
4.  Person follows Person
5.  Department contains Employee

Draw the ER diagram and identify the cardinality.

------------------------------------------------------------------------

# Revision Notes

    Recursive Relationship

    ↓

    Entity relates to itself

    ↓

    Same Entity Type

    ↓

    Different Instances

Examples

    Employee → Manages → Employee

    Folder → Contains → Folder

    User → Follows → User

    Comment → Replies To → Comment

Memory Trick

    If both sides are the SAME entity type,

    ↓

    Recursive Relationship.

**Remember:**

> A recursive relationship connects different **instances** of the
> **same entity type**. It is widely used to model hierarchies,
> organizational structures, trees, and self-referencing data in
> relational databases.
