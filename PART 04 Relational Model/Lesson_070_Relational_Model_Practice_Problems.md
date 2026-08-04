# Lesson 070 --- Relational Model Practice Problems

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Learning Objectives

Practice identifying relations, tuples, attributes, domains, keys,
referential relationships and relational algebra expressions through
progressively difficult problems.

------------------------------------------------------------------------

# How to Solve Any DBMS Problem

``` text
Read Requirements
       │
       ▼
Identify Relations
       │
       ▼
Identify Attributes
       │
       ▼
Choose Domains
       │
       ▼
Identify Keys
       │
       ▼
Create Relationships
       │
       ▼
Validate Integrity
```

------------------------------------------------------------------------

# Level 1 --- Basic (1--10)

### 1. Identify the Relation

    Student
    -----------------------
    ID | Name | Department

Find: - Relation - Attributes - Tuples - Degree - Cardinality

------------------------------------------------------------------------

### 2. Identify the Tuples

    ID  Name
    1   Alice
    2   Bob
    3   Neha

How many tuples are present?

------------------------------------------------------------------------

### 3. Identify the Attributes

For:

    Employee(EmployeeID, Name, Salary, Department)

List every attribute.

------------------------------------------------------------------------

### 4. Domains

Suggest domains for:

-   Age
-   Blood Group
-   Semester
-   Order Status

------------------------------------------------------------------------

### 5. Relation Schema vs Instance

Explain using one example.

------------------------------------------------------------------------

### 6. Degree & Cardinality

A table has 8 columns and 250 rows.

Find: - Degree - Cardinality

------------------------------------------------------------------------

### 7. Valid or Invalid?

    Phone = 98765,99887

Explain.

------------------------------------------------------------------------

### 8. Attribute Classification

Classify:

-   EmployeeID
-   DateOfBirth
-   Age
-   Email

as Key, Stored, Derived, etc.

------------------------------------------------------------------------

### 9. Table Design

Design a Product relation.

------------------------------------------------------------------------

### 10. Student Table

Design suitable domains for every attribute.

------------------------------------------------------------------------

# Level 2 --- Keys (11--25)

### 11.

Find all Super Keys:

    Employee(
    EmployeeID,
    Email,
    PassportNo,
    Name
    )

Assume first three are unique.

------------------------------------------------------------------------

### 12.

Identify Candidate Keys.

------------------------------------------------------------------------

### 13.

Choose the best Primary Key.

Explain why.

------------------------------------------------------------------------

### 14.

Identify Alternate Keys.

------------------------------------------------------------------------

### 15.

Should Name be a Primary Key?

Explain.

------------------------------------------------------------------------

### 16.

Design a Library table using a Surrogate Key.

------------------------------------------------------------------------

### 17.

Design an Enrollment table using a Composite Key.

------------------------------------------------------------------------

### 18.

Differentiate:

-   Candidate Key
-   Alternate Key
-   Primary Key

------------------------------------------------------------------------

### 19.

Natural or Surrogate?

Choose for:

-   Passport
-   Order
-   Employee
-   Book

------------------------------------------------------------------------

### 20--25.

For each system identify the best key:

-   Banking
-   Hospital
-   School
-   Inventory
-   Food Delivery
-   Airline

------------------------------------------------------------------------

# Level 3 --- Relationships (26--40)

### 26.

Create Student and Course tables.

Connect them.

------------------------------------------------------------------------

### 27.

Design Customer and Order tables.

Identify:

-   Parent
-   Child
-   Foreign Key

------------------------------------------------------------------------

### 28.

Explain Referential Integrity.

------------------------------------------------------------------------

### 29.

Predict result of:

    ON DELETE CASCADE

------------------------------------------------------------------------

### 30.

Predict result of:

    ON DELETE RESTRICT

------------------------------------------------------------------------

### 31.

Predict result of:

    ON DELETE SET NULL

------------------------------------------------------------------------

### 32.

Can a Foreign Key contain duplicates?

Explain.

------------------------------------------------------------------------

### 33.

Can a Foreign Key reference a UNIQUE Candidate Key?

Explain.

------------------------------------------------------------------------

### 34--40.

Design referential relationships for:

-   Hospital
-   Library
-   Railway
-   Hotel
-   Online Shopping
-   Banking
-   University ERP

------------------------------------------------------------------------

# Level 4 --- Relational Algebra (41--50)

Use the relation:

    Student(ID, Name, Dept, CGPA)

### 41.

Select all CSE students.

### 42.

Project only Name and CGPA.

### 43.

Write Union for two student tables.

### 44.

Write Difference expression.

### 45.

Find Cartesian Product of Student and Course.

### 46.

Rename Student as S.

### 47.

Convert Selection into SQL.

### 48.

Convert Projection into SQL.

### 49.

Explain why Relational Algebra is procedural.

### 50.

Differentiate SQL and Relational Algebra.

------------------------------------------------------------------------

# Challenge Problems

1.  Design a Hospital database.
2.  Design an Online Shopping database.
3.  Design a Banking database.
4.  Design a Railway Reservation database.
5.  Design a Food Delivery database.

For each provide:

-   Relations
-   Attributes
-   Domains
-   Primary Keys
-   Foreign Keys
-   Relationships

------------------------------------------------------------------------

# Self-Evaluation Checklist

``` text
□ I can identify Relations.

□ I can identify Tuples.

□ I can identify Attributes.

□ I understand Domains.

□ I can find Super Keys.

□ I can identify Candidate Keys.

□ I can choose a Primary Key.

□ I can identify Alternate Keys.

□ I can design Composite Keys.

□ I can use Foreign Keys.

□ I understand Referential Integrity.

□ I can write basic Relational Algebra expressions.
```

------------------------------------------------------------------------

# Interview Challenge

Without looking at notes, explain:

1.  Relation
2.  Tuple
3.  Attribute
4.  Domain
5.  Super Key
6.  Candidate Key
7.  Primary Key
8.  Alternate Key
9.  Foreign Key
10. Composite Key
11. Surrogate Key
12. Referential Integrity
13. Selection
14. Projection

If you can explain each with an example, you're ready for most DBMS
interviews.

------------------------------------------------------------------------

# Final Revision Flow

``` text
Relation
   │
Tuple
   │
Attribute
   │
Domain
   │
Keys
   │
Relationships
   │
Referential Integrity
   │
Relational Algebra
```

## Final Takeaway

Theory helps you understand concepts, but practice helps you recognize
patterns. The more database scenarios you solve, the easier it becomes
to design reliable schemas, choose the right keys, and answer interview
questions with confidence.
