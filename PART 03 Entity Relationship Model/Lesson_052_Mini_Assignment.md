# Lesson 052 --- Mini Assignment (Capstone Project)

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Objective

Apply everything learned in Part 3 by designing a complete database from
a real-world problem statement.

This assignment simulates a **college practical exam**, **placement
interview**, or **industry requirement gathering session**.

------------------------------------------------------------------------

# Project: Online Library Management System

## Problem Statement

A university wants to build an Online Library Management System.

Requirements:

-   Students register with the library.
-   Librarians manage books.
-   Books belong to categories.
-   Authors write books.
-   Students borrow and return books.
-   Fines are charged for late returns.
-   Each borrow transaction has an issue date and return date.

------------------------------------------------------------------------

# Step 1 --- Identify Entities

    Student
    Book
    Author
    Category
    Librarian
    Borrow
    Fine

------------------------------------------------------------------------

# Step 2 --- Identify Attributes

## Student

    StudentID (PK)
    Name
    Email
    Phone
    Department

## Book

    BookID (PK)
    Title
    ISBN
    PublicationYear

## Author

    AuthorID (PK)
    AuthorName

## Category

    CategoryID (PK)
    CategoryName

## Librarian

    LibrarianID (PK)
    Name
    Email

## Borrow

    BorrowID (PK)
    IssueDate
    ReturnDate
    Status

## Fine

    FineID (PK)
    Amount
    PaidStatus

------------------------------------------------------------------------

# Step 3 --- Identify Relationships

    Student ---- Borrows ---- Book

    Book ---- Written By ---- Author

    Book ---- Belongs To ---- Category

    Librarian ---- Issues ---- Borrow

    Borrow ---- Generates ---- Fine

------------------------------------------------------------------------

# Step 4 --- Decide Cardinality

  Relationship         Cardinality
  -------------------- -------------
  Student → Borrow     1 : N
  Book → Borrow        1 : N
  Author → Book        1 : N
  Category → Book      1 : N
  Librarian → Borrow   1 : N
  Borrow → Fine        1 : 0..1

------------------------------------------------------------------------

# Step 5 --- Participation

  Entity    Participation
  --------- ---------------
  Student   Partial
  Book      Total
  Borrow    Total
  Fine      Partial

------------------------------------------------------------------------

# Step 6 --- ASCII ER Diagram

    Author -------- Writes -------- Book -------- BelongsTo -------- Category
                                     |
                                  Borrowed By
                                     |
                                  Student
                                     |
                                 Issued By
                                     |
                                 Librarian
                                     |
                               Generates
                                     |
                                   Fine

------------------------------------------------------------------------

# Step 7 --- Relational Mapping

``` sql
Student(StudentID, Name, Email, Phone, Department)

Author(AuthorID, AuthorName)

Category(CategoryID, CategoryName)

Book(BookID, Title, ISBN, PublicationYear,
     AuthorID, CategoryID)

Librarian(LibrarianID, Name, Email)

Borrow(BorrowID, StudentID, BookID,
       LibrarianID, IssueDate,
       ReturnDate, Status)

Fine(FineID, BorrowID, Amount, PaidStatus)
```

------------------------------------------------------------------------

# Step 8 --- Design Validation Checklist

    ✓ Every entity has a primary key

    ✓ Relationships identified

    ✓ Correct cardinality

    ✓ Correct participation

    ✓ No duplicate entities

    ✓ Attributes are atomic

    ✓ Foreign keys defined

------------------------------------------------------------------------

# Extension Tasks

Add support for:

-   Reservations
-   Multiple library branches
-   E-books
-   Notifications
-   Membership plans

Update the ER diagram after each enhancement.

------------------------------------------------------------------------

# Interview Challenge

Explain:

1.  Why is **Borrow** an entity instead of just a relationship?
2.  Why is **Fine** optional?
3.  Why is **Author--Book** not Many-to-Many in this simplified model?
4.  How would the design change if one book had multiple authors?

------------------------------------------------------------------------

# Bonus Assignment

Choose **ONE** system below and repeat the complete workflow.

-   Hospital Management
-   Food Delivery
-   Railway Reservation
-   Banking
-   University ERP
-   Hotel Management
-   Movie Ticket Booking
-   Social Media

Deliver:

1.  Requirements
2.  Entities
3.  Attributes
4.  Keys
5.  Relationships
6.  Cardinality
7.  Participation
8.  ER Diagram
9.  Relational Schema
10. Assumptions

------------------------------------------------------------------------

# Evaluation Rubric

  Criteria                    Marks
  ----------------------- ---------
  Entity Identification          10
  Attributes                     10
  Keys                           10
  Relationships                  15
  Cardinality                    15
  Participation                  10
  ER Diagram                     20
  Relational Mapping             10
  Explanation                    10
  **Total**                 **100**

------------------------------------------------------------------------

# Common Mistakes

-   Missing bridge entities
-   Wrong cardinality
-   Forgetting foreign keys
-   Treating attributes as entities
-   Ignoring business rules

------------------------------------------------------------------------

# Revision Summary

    Requirements
          ↓
    Entities
          ↓
    Attributes
          ↓
    Keys
          ↓
    Relationships
          ↓
    Cardinality
          ↓
    Participation
          ↓
    ER Diagram
          ↓
    Relational Tables

## Final Takeaway

A successful database designer does not start with SQL.

They begin by understanding the business problem, identifying the
real-world objects, defining how they interact, validating the rules,
and only then converting the design into relational tables.

This disciplined workflow is what separates a maintainable database from
one that slowly evolves into a museum of emergency fixes.
