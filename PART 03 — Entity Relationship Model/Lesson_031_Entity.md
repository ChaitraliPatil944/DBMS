# Lesson 031 --- Entity

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

After this lesson you will understand:

-   What an Entity is
-   Why entities are important
-   How to identify entities
-   Types of real-world entities
-   Entity vs Object
-   Entity naming rules
-   Real-world examples
-   ASCII diagrams
-   Interview questions
-   Practice exercises
-   Revision notes

------------------------------------------------------------------------

# 1. What is an Entity?

An **Entity** is any real-world object, person, place, thing, event, or
concept about which we want to store information in a database.

Simply put:

> If you need to save information about something, it is probably an
> entity.

Examples:

-   Student
-   Employee
-   Customer
-   Product
-   Book
-   Hospital
-   Course
-   Order

------------------------------------------------------------------------

# 2. Why Do We Need Entities?

Imagine building a Library database.

Questions:

-   Who borrows books?
-   Which books exist?
-   Who works in the library?

These become entities.

Without identifying entities first, database tables become confusing and
inconsistent.

------------------------------------------------------------------------

# 3. Real-Life Analogy

Imagine your school.

You naturally recognize:

    School
    │
    ├── Students
    ├── Teachers
    ├── Subjects
    ├── Classrooms
    └── Exams

Each of these can store information.

Therefore, each is an entity.

------------------------------------------------------------------------

# 4. Entity in an ER Diagram

Entities are represented using **rectangles**.

    +-----------+
    |  Student  |
    +-----------+

    +-----------+
    |  Course   |
    +-----------+

    +-----------+
    |  Teacher  |
    +-----------+

------------------------------------------------------------------------

# 5. Entity Stores Information

Example:

Student

    Student

    Roll No
    Name
    Age
    Department
    Phone
    Email

Every student has these properties.

Those properties are called **attributes**, which will be covered in the
next lessons.

------------------------------------------------------------------------

# 6. Real-World Examples

## Hospital

    Hospital

    Patient
    Doctor
    Medicine
    Appointment
    Ward

## Banking

    Bank

    Customer
    Account
    Loan
    Employee
    Branch

## E-Commerce

    Amazon

    Customer
    Order
    Product
    Payment
    Seller

------------------------------------------------------------------------

# 7. Entity vs Object

  Object                     Entity
  -------------------------- -------------------------
  Exists in the real world   Stored in database
  May or may not be saved    Information is stored
  Used in programming        Used in database design

Example:

Your laptop is an object.

If a company stores its details in inventory, it becomes an entity.

------------------------------------------------------------------------

# 8. How to Identify Entities?

Ask yourself:

-   Do we store information about it?
-   Does it have attributes?
-   Can it be uniquely identified?
-   Does it participate in relationships?

If the answer is mostly "Yes", it is an entity.

------------------------------------------------------------------------

# 9. Naming Rules

Good names:

-   Student
-   Employee
-   Book
-   Customer
-   Product

Avoid:

-   Student Data
-   Table1
-   Database Student
-   Student Information Details

Use singular nouns.

------------------------------------------------------------------------

# 10. Example ER Diagram

    +-----------+          Enrolls In          +----------+
    | Student   | ---------------------------> | Course   |
    +-----------+                              +----------+

Student and Course are entities.

"Enrolls In" is the relationship.

------------------------------------------------------------------------

# 11. Common Mistakes

❌ Treating attributes as entities.

Example:

    Student
    Age
    Phone

Age is **not** an entity.

Phone is **not** an entity.

Student is the entity.

------------------------------------------------------------------------

# 12. Interview Questions

### Basic

1.  What is an entity?
2.  Give five examples of entities.
3.  How is an entity represented in an ER diagram?

### Intermediate

1.  How do you identify entities in a system?
2.  Can an event be an entity?

### Advanced

Design entities for:

-   Online Food Delivery
-   ATM System
-   University ERP

------------------------------------------------------------------------

# 13. Practice

Identify entities for:

## Library

Books

Students

Librarian

Borrow Record

Fine

## Hospital

Doctor

Patient

Appointment

Medicine

Billing

------------------------------------------------------------------------

# 14. Revision Notes

    Entity

    ↓

    Anything about which
    information is stored
    inside a database.

Representation:

    +-----------+
    |  Entity   |
    +-----------+

Examples:

-   Student
-   Product
-   Employee
-   Book
-   Customer

Remember:

> If the database stores information about something, it is usually an
> Entity.
