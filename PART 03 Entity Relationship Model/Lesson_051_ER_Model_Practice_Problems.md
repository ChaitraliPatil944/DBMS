# Lesson 051 --- ER Model Practice Problems

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson you will be able to:

-   Analyze business requirements
-   Identify entities, attributes, and relationships
-   Decide keys, cardinality, and participation
-   Design complete ER diagrams
-   Improve interview and exam problem-solving skills

------------------------------------------------------------------------

# How to Solve Every ER Problem

    Read Requirements
            │
            ▼
    Identify Nouns
            │
            ▼
    Entities
            │
            ▼
    Identify Verbs
            │
            ▼
    Relationships
            │
            ▼
    Attributes
            │
            ▼
    Primary Keys
            │
            ▼
    Cardinality
            │
            ▼
    Participation
            │
            ▼
    Draw ER Diagram

------------------------------------------------------------------------

# Level 1 --- Beginner

## Problem 1 --- Student Management

Design an ER diagram for:

-   Students enroll in courses.
-   Each course belongs to one department.

Identify: - Entities - Attributes - Keys - Relationships - Cardinality

------------------------------------------------------------------------

## Problem 2 --- Library

Requirements:

-   Books are issued to students.
-   Librarians issue books.
-   Books belong to categories.

------------------------------------------------------------------------

## Problem 3 --- Hospital

Requirements:

-   Doctors treat patients.
-   Patients receive medicines.

------------------------------------------------------------------------

## Problem 4 --- Bank

Requirements:

-   Customers own accounts.
-   Accounts belong to branches.

------------------------------------------------------------------------

## Problem 5 --- Company

Requirements:

-   Employees work in departments.
-   Managers supervise employees.

------------------------------------------------------------------------

# Level 2 --- Intermediate

## Problem 6 --- Hotel Management

-   Guests book rooms.
-   Rooms belong to room types.
-   Payments are recorded.

------------------------------------------------------------------------

## Problem 7 --- Online Shopping

-   Customers place orders.
-   Orders contain products.
-   Sellers sell products.
-   Payments are made online.

------------------------------------------------------------------------

## Problem 8 --- Airline Reservation

-   Passengers book tickets.
-   Flights use aircraft.
-   Airports connect flights.

------------------------------------------------------------------------

## Problem 9 --- Food Delivery

-   Customers order food.
-   Restaurants prepare orders.
-   Delivery partners deliver orders.

------------------------------------------------------------------------

## Problem 10 --- University ERP

-   Students enroll in subjects.
-   Faculty teach subjects.
-   Departments manage faculty.

------------------------------------------------------------------------

# Level 3 --- Advanced

## Problem 11 --- Social Media

Requirements:

-   Users follow users.
-   Users create posts.
-   Users like posts.
-   Users comment on posts.

Hint: - Identify recursive relationships.

------------------------------------------------------------------------

## Problem 12 --- Inventory System

Requirements:

-   Suppliers provide products.
-   Warehouses store products.
-   Managers approve stock transfers.

Hint: - Check if aggregation is required.

------------------------------------------------------------------------

## Problem 13 --- Railway Reservation

Requirements:

-   Passengers reserve seats.
-   Trains run on routes.
-   Routes contain stations.
-   Tickets are generated.

------------------------------------------------------------------------

## Problem 14 --- Pharmacy

Requirements:

-   Doctors prescribe medicines.
-   Patients buy medicines.
-   Pharmacists dispense medicines.

------------------------------------------------------------------------

## Problem 15 --- Cricket Tournament

Requirements:

-   Teams play matches.
-   Players belong to teams.
-   Umpires officiate matches.
-   Stadiums host matches.

------------------------------------------------------------------------

# Challenge Problems

Design complete ER diagrams for:

1.  ATM Management
2.  Movie Ticket Booking
3.  Courier Service
4.  Insurance System
5.  Vehicle Rental
6.  School ERP
7.  Gym Management
8.  Online Examination
9.  Event Management
10. Smart Parking System

For each include:

-   Entities
-   Attributes
-   Primary Keys
-   Relationships
-   Cardinality
-   Participation
-   Weak Entities (if any)
-   Generalization/Specialization (if applicable)

------------------------------------------------------------------------

# Common Tricky Questions

1.  Should "Order" be an entity or relationship?
2.  Is "Address" an entity or attribute?
3.  When should Phone Numbers be separate?
4.  When is a weak entity required?
5.  Which relationships require bridge tables?

Explain your reasoning.

------------------------------------------------------------------------

# Self-Evaluation Checklist

    □ Identified all entities

    □ Added attributes

    □ Selected primary keys

    □ Found relationships

    □ Correct cardinality

    □ Correct participation

    □ Removed duplicate entities

    □ Applied normalization-friendly design

    □ Diagram is readable

    □ Business rules are satisfied

------------------------------------------------------------------------

# Interview Practice

Time yourself.

  Difficulty       Suggested Time
  -------------- ----------------
  Beginner                 10 min
  Intermediate             20 min
  Advanced                 30 min

After drawing:

1.  Explain every entity.
2.  Justify every relationship.
3.  Explain every cardinality.
4.  Mention assumptions.

------------------------------------------------------------------------

# Revision Exercise

For each system below, write only:

-   Entities
-   Keys
-   Relationships
-   Cardinality

Systems:

-   Library
-   Hospital
-   Banking
-   University
-   Railway
-   E-commerce
-   Food Delivery
-   Hotel
-   Social Media
-   Inventory

------------------------------------------------------------------------

# Final Challenge

Choose **one** system below and complete the entire database design.

-   Hospital Management
-   Banking System
-   Railway Reservation
-   Online Shopping
-   University ERP

Deliverables:

1.  Requirements
2.  Entities
3.  Attributes
4.  Keys
5.  Relationships
6.  Cardinality
7.  Participation
8.  ER Diagram
9.  Relational Tables

------------------------------------------------------------------------

# Practice Tips

-   Start with nouns (entities).
-   Convert verbs into relationships.
-   Keep attributes atomic.
-   Avoid unnecessary entities.
-   Validate business rules before finalizing.

------------------------------------------------------------------------

# Revision Notes

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
    Relational Mapping

Memory Trick:

    R → E → A → K → R → C → P → D → M

    Requirements
    Entities
    Attributes
    Keys
    Relationships
    Cardinality
    Participation
    Diagram
    Mapping

**Remember:**

> The fastest way to improve ER modeling is by solving many different
> problem statements. Every new scenario teaches you a different
> business rule, and business rules are what shape a good database
> design.
