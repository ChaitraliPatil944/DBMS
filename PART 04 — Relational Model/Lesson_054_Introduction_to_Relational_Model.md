# Lesson 054 --- Introduction to the Relational Model

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the Relational Model is
-   Why it was invented
-   History of the Relational Model
-   Problems with earlier database models
-   Fundamental concepts
-   Why tables are used
-   Real-world examples
-   Advantages and limitations
-   Industry applications
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

In Part 03, we learned how to **design** databases using ER diagrams.

However, computers do not store ER diagrams.

Modern databases store information using **tables**.

The model that represents data using tables is called the **Relational
Model**.

It forms the foundation of almost every modern SQL database.

------------------------------------------------------------------------

# 2. A Short History

During the 1960s, databases mainly used:

-   Hierarchical Model
-   Network Model

These models worked, but they had major drawbacks:

-   Complex relationships
-   Difficult navigation
-   Poor flexibility
-   High maintenance cost

In **1970**, entity\["people","Edgar F. Codd","Relational model
pioneer"\], a researcher at entity\["company","IBM","Technology
company"\], published the paper:

> **"A Relational Model of Data for Large Shared Data Banks."**

This changed database technology forever.

------------------------------------------------------------------------

# 3. Why Was the Relational Model Invented?

Imagine a university storing data like this:

    Student

    ↓

    Course

    ↓

    Teacher

Finding information required navigating many links.

Adding new data often required changing the entire structure.

Codd proposed something much simpler:

    +-----------+
    | Student   |
    +-----------+

    +-----------+
    | Course    |
    +-----------+

    +-----------+
    | Teacher   |
    +-----------+

Separate tables connected using keys.

------------------------------------------------------------------------

# 4. What is the Relational Model?

The **Relational Model** is a logical database model that organizes data
into **relations (tables)** consisting of **rows** and **columns**.

Everything in a relational database is represented using tables.

------------------------------------------------------------------------

# 5. Fundamental Concepts

    Relational Model
    │
    ├── Relation (Table)
    ├── Tuple (Row)
    ├── Attribute (Column)
    ├── Domain
    ├── Keys
    └── Relationships

These concepts will be studied in the upcoming lessons.

------------------------------------------------------------------------

# 6. Why Tables?

Tables are:

-   Easy to understand
-   Easy to search
-   Easy to update
-   Easy to maintain

Example

    Student

    +-----------+---------+------+
    | ID | Name | Dept    |
    +-----------+---------+------+
    |101 | Alice| CSE     |
    |102 | Bob  | AIML    |
    +-----------+---------+------+

Humans naturally understand tabular information.

------------------------------------------------------------------------

# 7. Real-World Analogy

Think of an attendance register.

    Roll No

    Name

    Attendance

Every row represents one student.

Every column stores one type of information.

A database table works the same way.

------------------------------------------------------------------------

# 8. Features of the Relational Model

-   Data stored in tables
-   Relationships through keys
-   Minimal redundancy
-   Data independence
-   Easy querying using SQL
-   Supports constraints
-   Scalable and reliable

------------------------------------------------------------------------

# 9. Real-World Example

University Database

    Student
    +-----------+
    |StudentID  |
    |Name       |
    |Dept       |
    +-----------+

    Course
    +-----------+
    |CourseID   |
    |CourseName |
    +-----------+

    Enrollment
    +----------------------+
    |StudentID | CourseID  |
    +----------------------+

The Enrollment table links students and courses.

------------------------------------------------------------------------

# 10. Advantages

-   Simple design
-   High consistency
-   Reduced redundancy
-   Supports normalization
-   Easy reporting
-   Powerful SQL support

------------------------------------------------------------------------

# 11. Limitations

-   Complex joins for very large datasets
-   Not ideal for highly unstructured data
-   Horizontal scaling can be challenging

These limitations led to NoSQL databases, which we will study later.

------------------------------------------------------------------------

# 12. Industry Applications

Relational databases are widely used in:

-   Banking
-   E-commerce
-   Healthcare
-   ERP systems
-   Government systems
-   Airline reservation
-   Education portals

Popular relational databases include:

-   MySQL
-   PostgreSQL
-   Oracle Database
-   Microsoft SQL Server

------------------------------------------------------------------------

# 13. Comparison with Earlier Models

  Feature       Hierarchical   Network   Relational
  ------------- -------------- --------- ------------
  Structure     Tree           Graph     Tables
  Flexibility   Low            Medium    High
  Ease of Use   Low            Low       High
  SQL Support   No             No        Yes

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is the Relational Model?
2.  Who proposed it?
3.  Why was it introduced?

### Intermediate

1.  Why are tables used?
2.  Advantages over hierarchical databases?

### Advanced

1.  Why is the Relational Model still widely used?
2.  When would you choose a NoSQL database instead?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Explain why the Relational Model replaced earlier models.
2.  Draw a simple relational design for a library.
3.  Identify three advantages of tables.
4.  Compare the Relational Model with the Hierarchical Model.

------------------------------------------------------------------------

# Revision Notes

    Real World

    ↓

    ER Model

    ↓

    Relational Model

    ↓

    Tables

    ↓

    SQL Database

Key Ideas

    Relation = Table

    Tuple = Row

    Attribute = Column

    Domain = Allowed Values

    Keys = Unique Identification

Memory Trick

    R T A D K

    Relation
    Tuple
    Attribute
    Domain
    Keys

**Remember:**

> The ER Model helps us **design** a database. The Relational Model
> helps us **implement** that design using tables. It is the bridge
> between database concepts and practical SQL systems, which is why it
> remains the backbone of most business applications decades after its
> invention.
