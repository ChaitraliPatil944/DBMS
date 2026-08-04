# Lesson 087 --- Mini Assignment

> **Part 05 --- Constraints**

------------------------------------------------------------------------

# Assignment Objective

This assignment combines everything learned in the Constraints chapter
into practical database design tasks similar to university exams,
technical interviews, and industry assessments.

You will design databases, choose appropriate constraints, write SQL,
and justify your design decisions.

------------------------------------------------------------------------

# Instructions

-   Read each case study carefully.
-   Identify the required tables.
-   Define appropriate columns and data types.
-   Apply suitable constraints.
-   Draw a simple ER diagram (optional).
-   Write SQL `CREATE TABLE` statements.
-   Explain why each constraint was chosen.

------------------------------------------------------------------------

# Case Study 1 --- University Management System

## Scenario

A university wants to manage:

-   Students
-   Departments
-   Courses
-   Faculty
-   Enrollments

### Tasks

1.  Identify all tables.
2.  Choose a PRIMARY KEY for each table.
3.  Add FOREIGN KEY relationships.
4.  Make student email unique.
5.  Ensure semester is between 1 and 8.
6.  Default country should be 'India'.
7.  Student name must not be NULL.

------------------------------------------------------------------------

# Case Study 2 --- Hospital Management System

## Scenario

A hospital stores:

-   Patients
-   Doctors
-   Appointments
-   Departments

### Tasks

1.  Design the tables.
2.  Apply PRIMARY KEY constraints.
3.  Link appointments with doctors and patients.
4.  Restrict patient age to positive values.
5.  Default appointment status to 'Scheduled'.
6.  Make doctor's license number UNIQUE.

------------------------------------------------------------------------

# Case Study 3 --- Banking System

## Scenario

The bank stores:

-   Customers
-   Accounts
-   Transactions
-   Branches

### Tasks

1.  Create all tables.
2.  Every account belongs to one customer.
3.  Balance cannot be negative.
4.  Account status defaults to 'Active'.
5.  Account number must be UNIQUE.
6.  Prevent orphan accounts.

------------------------------------------------------------------------

# Case Study 4 --- E-Commerce System

## Scenario

Design tables for:

-   Customers
-   Products
-   Orders
-   OrderItems

### Tasks

1.  Create relationships.
2.  Quantity must be greater than zero.
3.  Price must not be negative.
4.  Order status defaults to 'Pending'.
5.  Product SKU must be UNIQUE.

------------------------------------------------------------------------

# Case Study 5 --- Library Management System

## Scenario

Design tables for:

-   Books
-   Members
-   Borrow
-   Authors

### Tasks

1.  Create relationships.
2.  ISBN must be UNIQUE.
3.  Member name is mandatory.
4.  Borrow date defaults to CURRENT_DATE.
5.  Fine cannot be negative.

------------------------------------------------------------------------

# SQL Coding Tasks

Write SQL for:

1.  Student table with PRIMARY KEY, NOT NULL, UNIQUE.
2.  Employee table with CHECK.
3.  Orders table with DEFAULT.
4.  Customer and Orders using FOREIGN KEY.
5.  Enrollment using Composite PRIMARY KEY.

------------------------------------------------------------------------

# Constraint Selection Exercise

Choose the best constraint(s):

  Requirement                         Constraint
  ----------------------------------- ------------
  Unique login email                  ?
  Every employee needs an ID          ?
  Product quantity \> 0               ?
  Every order belongs to a customer   ?
  Default account status              ?
  Mandatory customer name             ?

------------------------------------------------------------------------

# Viva Questions

1.  What is a constraint?
2.  Why are constraints important?
3.  PRIMARY KEY vs UNIQUE?
4.  FOREIGN KEY vs PRIMARY KEY?
5.  CHECK vs NOT NULL?
6.  Entity Integrity vs Referential Integrity?
7.  Can a FOREIGN KEY reference a UNIQUE column?
8.  Why is DEFAULT useful?
9.  What is an orphan record?
10. Which constraint prevents duplicate emails?

------------------------------------------------------------------------

# Bonus Challenge

Design your own database for one of the following:

-   Movie Ticket Booking
-   Gym Management
-   Restaurant Management
-   Hotel Booking
-   Online Examination
-   Vehicle Rental
-   Inventory Management

Requirements:

-   Minimum 5 tables
-   At least 3 FOREIGN KEY relationships
-   Use every major constraint:
    -   PRIMARY KEY
    -   FOREIGN KEY
    -   UNIQUE
    -   NOT NULL
    -   CHECK
    -   DEFAULT

------------------------------------------------------------------------

# Submission Checklist

``` text
✓ Tables identified

✓ Data types selected

✓ PRIMARY KEY added

✓ FOREIGN KEY added

✓ UNIQUE constraints added

✓ NOT NULL constraints added

✓ CHECK constraints added

✓ DEFAULT constraints added

✓ SQL syntax verified

✓ Business rules explained
```

------------------------------------------------------------------------

# Evaluation Rubric

  Criteria                          Marks
  ----------------------------- ---------
  Table Design                         20
  Constraint Selection                 20
  SQL Syntax                           20
  Relationships                        15
  Business Rule Validation             15
  Explanation & Documentation          10
  **Total**                       **100**

------------------------------------------------------------------------

# Final Takeaway

Designing a database is much more than creating tables. A well-designed
schema captures real-world business rules through carefully selected
constraints. This assignment encourages you to think like a database
designer rather than someone simply writing SQL. The more reasoning you
put into each constraint, the stronger your understanding becomes, and
the fewer unpleasant surprises your future applications will encounter.
