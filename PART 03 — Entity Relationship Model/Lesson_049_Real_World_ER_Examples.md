# Lesson 049 --- Real-World ER Diagram Examples

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will be able to:

-   Analyze real-world systems
-   Identify entities, attributes, and relationships
-   Choose appropriate keys
-   Determine cardinality and participation
-   Design interview-ready ER diagrams
-   Convert requirements into database models

------------------------------------------------------------------------

# 1. Introduction

The best way to master ER modeling is by solving real-world problems.

In this lesson, we'll design ER models for common systems frequently
asked in university exams and technical interviews.

------------------------------------------------------------------------

# Example 1 --- Library Management System

## Requirements

-   Students borrow books.
-   Books belong to categories.
-   Librarians issue books.
-   Books are written by authors.

### Entities

    Student
    Book
    Author
    Category
    Librarian
    Issue

### Relationships

    Student ---- Borrows ---- Book

    Book ---- Written By ---- Author

    Book ---- Belongs To ---- Category

    Librarian ---- Issues ---- Book

### Simplified ER Diagram

    Student ---- Borrows ---- Book ---- BelongsTo ---- Category
                         |
                      Issued By
                         |
                    Librarian

------------------------------------------------------------------------

# Example 2 --- Hospital Management System

## Requirements

-   Doctors treat patients.
-   Patients receive medicines.
-   Appointments are scheduled.
-   Bills are generated.

### Entities

    Doctor
    Patient
    Appointment
    Medicine
    Bill

### ER Diagram

    Doctor ---- Treats ---- Patient
       |
    Schedules
       |
    Appointment

    Patient ---- Receives ---- Medicine

    Patient ---- Pays ---- Bill

------------------------------------------------------------------------

# Example 3 --- University Management System

## Requirements

-   Students enroll in courses.
-   Faculty teach courses.
-   Departments offer courses.

### Entities

    Student
    Faculty
    Course
    Department

### ER Diagram

    Student ---- Enrolls ---- Course

    Faculty ---- Teaches ---- Course

    Department ---- Offers ---- Course

------------------------------------------------------------------------

# Example 4 --- Online Shopping System

## Requirements

-   Customers place orders.
-   Orders contain products.
-   Sellers sell products.
-   Customers make payments.

### Entities

    Customer
    Order
    Product
    Seller
    Payment

### ER Diagram

    Customer ---- Places ---- Order
    Order ---- Contains ---- Product
    Seller ---- Sells ---- Product
    Customer ---- Makes ---- Payment

------------------------------------------------------------------------

# Example 5 --- Banking System

## Requirements

-   Customers own accounts.
-   Accounts belong to branches.
-   Customers apply for loans.
-   Employees process loans.

### Entities

    Customer
    Account
    Branch
    Loan
    Employee

### ER Diagram

    Customer ---- Owns ---- Account

    Branch ---- Maintains ---- Account

    Customer ---- Applies ---- Loan

    Employee ---- Processes ---- Loan

------------------------------------------------------------------------

# Example 6 --- Railway Reservation System

## Requirements

-   Passengers book tickets.
-   Trains run on routes.
-   Tickets belong to passengers.

### Entities

    Passenger
    Ticket
    Train
    Route
    Station

### ER Diagram

    Passenger ---- Books ---- Ticket

    Ticket ---- For ---- Train

    Train ---- Runs On ---- Route

    Route ---- Contains ---- Station

------------------------------------------------------------------------

# Example 7 --- Food Delivery Application

## Requirements

-   Customers order food.
-   Restaurants prepare food.
-   Delivery partners deliver orders.
-   Payments are completed.

### Entities

    Customer
    Restaurant
    Order
    DeliveryPartner
    Payment

### ER Diagram

    Customer ---- Places ---- Order

    Restaurant ---- Prepares ---- Order

    DeliveryPartner ---- Delivers ---- Order

    Customer ---- Makes ---- Payment

------------------------------------------------------------------------

# Example 8 --- Movie Ticket Booking

### Entities

    Customer
    Movie
    Theatre
    Screen
    Seat
    Ticket
    Payment

### ER Diagram

    Customer ---- Books ---- Ticket

    Ticket ---- For ---- Movie

    Movie ---- Shown In ---- Screen

    Screen ---- Located In ---- Theatre

    Ticket ---- Allocates ---- Seat

------------------------------------------------------------------------

# Common Design Tips

    Requirements
          ↓
    Identify Nouns
          ↓
    Entities

    Identify Verbs
          ↓
    Relationships

    Find Details
          ↓
    Attributes

    Choose Keys
          ↓
    Primary Keys

    Apply Rules
          ↓
    Cardinality + Participation

------------------------------------------------------------------------

# Common Mistakes

-   Creating entities for simple attributes.
-   Missing primary keys.
-   Incorrect many-to-many relationships.
-   Forgetting bridge tables.
-   Ignoring business rules.

------------------------------------------------------------------------

# Interview Questions

### Beginner

1.  Design an ER diagram for a Library.
2.  Identify entities in a Hospital system.

### Intermediate

1.  Model an Online Shopping application.
2.  Explain the cardinality in a University database.

### Advanced

Design complete ER diagrams for:

-   Hotel Management
-   ATM System
-   Airline Reservation
-   Social Media Platform
-   Inventory Management

Explain all assumptions.

------------------------------------------------------------------------

# Practice Problems

Design ER diagrams for:

1.  Gym Management
2.  School ERP
3.  Pharmacy
4.  Insurance System
5.  Vehicle Rental
6.  Cricket Tournament
7.  Online Examination
8.  Courier Service

For each system identify:

-   Entities
-   Attributes
-   Keys
-   Relationships
-   Cardinality
-   Participation

------------------------------------------------------------------------

# Revision Notes

    Real World Problem
            ↓
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

## Quick Interview Checklist

    ✓ Read requirements carefully
    ✓ Find nouns → Entities
    ✓ Find verbs → Relationships
    ✓ Add attributes
    ✓ Select primary keys
    ✓ Decide cardinality
    ✓ Decide participation
    ✓ Validate business rules

**Remember:**

> Every real-world database begins as a conversation about a business
> problem. An ER diagram translates that conversation into a structured
> model that developers can implement as relational tables. The diagram
> is the blueprint. SQL is the building. Skip the blueprint, and the
> building tends to lean in fascinating but expensive directions.
