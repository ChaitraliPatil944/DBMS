# Lesson 035 --- Types of Attributes

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   Why attributes are classified into different types
-   Simple (Atomic) Attribute
-   Composite Attribute
-   Single-Valued Attribute
-   Multi-Valued Attribute
-   Derived Attribute
-   Stored Attribute
-   Key Attribute
-   Optional (Null) Attribute
-   Complex Attribute
-   ER Diagram symbols
-   SQL mapping
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

In the previous lesson, we learned that an **Attribute** describes an
entity.

However, not every attribute behaves the same way.

Some attributes contain only one value.

Some contain multiple values.

Some can be calculated.

Some are made up of smaller attributes.

Therefore, ER Models classify attributes into different types.

------------------------------------------------------------------------

# 2. Classification of Attributes

                    Attributes
                         │
     ┌───────────────────┼────────────────────┐
     │                   │                    │
    Simple          Composite          Single-Valued
     │
     ├──────────────┐
     │              │
    Multi-Valued  Derived
     │              │
    Stored      Key Attribute
     │
    Optional (Null)
     │
    Complex

------------------------------------------------------------------------

# 3. Simple (Atomic) Attribute

A **Simple Attribute** cannot be divided further.

Example:

    Age

    Gender

    Salary

    Price

ER Representation

    Age
     ○
     |
    Student

SQL

``` sql
Age INT
```

------------------------------------------------------------------------

# 4. Composite Attribute

A **Composite Attribute** can be divided into smaller meaningful parts.

Example:

    Name

    ↓

    First Name
    Middle Name
    Last Name

Another example:

    Address

    ↓

    House Number
    Street
    City
    State
    Country
    PIN Code

ER Diagram

              Name
               ○
          /    |    \
     First  Middle  Last

SQL

``` sql
FirstName
MiddleName
LastName
```

------------------------------------------------------------------------

# 5. Single-Valued Attribute

Stores only **one value** for each entity.

Example

    Roll Number

    Age

    Date of Birth

Each student has only one roll number.

------------------------------------------------------------------------

# 6. Multi-Valued Attribute

Stores **multiple values**.

Example

    Phone Numbers

    ↓

    9876543210

    9988776655

    9123456789

Another example

    Skills

    ↓

    Python

    Java

    SQL

ER Representation

Multi-valued attributes use a **double oval**.

ASCII

    ((Phone))
          |
       Student

SQL

Usually implemented using another table.

    Student

    StudentID

    StudentPhone

    StudentID
    Phone

------------------------------------------------------------------------

# 7. Stored Attribute

A **Stored Attribute** keeps the original value.

Example

    Date of Birth

This value is stored permanently.

------------------------------------------------------------------------

# 8. Derived Attribute

A **Derived Attribute** is calculated from another attribute.

Example

    Date of Birth

    ↓

    Age

Age changes every year.

It is better calculated instead of stored.

ER Representation

Derived attributes use a **dashed oval**.

ASCII

    - - Age - -
          |
       Student

SQL Example

``` sql
SELECT
TIMESTAMPDIFF(YEAR, DOB, CURDATE()) AS Age
FROM Student;
```

------------------------------------------------------------------------

# 9. Key Attribute

A **Key Attribute** uniquely identifies an entity.

Example

    StudentID

    EmployeeID

    ISBN

ER Representation

The attribute name is **underlined**.

ASCII

    StudentID
    =========
         |
      Student

------------------------------------------------------------------------

# 10. Optional (Null) Attribute

Some attributes are optional.

Example

    Middle Name

    Apartment Number

    Secondary Email

Not every person has one.

SQL

``` sql
MiddleName VARCHAR(50) NULL
```

------------------------------------------------------------------------

# 11. Complex Attribute

A **Complex Attribute** combines both:

-   Composite Attribute
-   Multi-Valued Attribute

Example

    Addresses

    ↓

    Home Address

    Office Address

    ↓

    House
    Street
    City

It is both:

-   Multi-valued
-   Composite

------------------------------------------------------------------------

# 12. Complete Example

Student

                        Student
                            |
         ---------------------------------------
         |        |         |          |       |
     StudentID  Name     DOB      Phone     Address
                  |                   ||
         ----------------       ---------------
         |      |      |        Home    Office
       First  Middle  Last

StudentID → Key Attribute

Name → Composite

DOB → Stored

Age → Derived

Phone → Multi-valued

Address → Complex

------------------------------------------------------------------------

# 13. Summary Table

  Attribute Type   Example
  ---------------- --------------------
  Simple           Age
  Composite        Name
  Single-Valued    Roll Number
  Multi-Valued     Phone Numbers
  Stored           Date of Birth
  Derived          Age
  Key              StudentID
  Optional         Middle Name
  Complex          Multiple Addresses

------------------------------------------------------------------------

# 14. Common Mistakes

❌ Storing Age instead of Date of Birth.

Age changes every year.

Store DOB and calculate Age.

❌ Making Phone Number a single attribute.

A person may have multiple phone numbers.

------------------------------------------------------------------------

# 15. Interview Questions

### Beginner

1.  What is a Composite Attribute?
2.  What is a Derived Attribute?
3.  Give examples of Multi-Valued Attributes.

### Intermediate

1.  Why should Age be derived?
2.  Difference between Stored and Derived Attributes?
3.  How are Multi-Valued Attributes represented?

### Advanced

Design attributes for:

-   Hospital
-   Banking
-   Airline
-   Online Shopping

Identify every attribute type.

------------------------------------------------------------------------

# 16. Practice Problems

Classify the following.

1.  StudentID
2.  Name
3.  Address
4.  Date of Birth
5.  Age
6.  Email
7.  Phone Numbers
8.  Skills
9.  Passport Number
10. Previous Addresses

------------------------------------------------------------------------

# Revision Notes

    Attributes

    ├── Simple
    ├── Composite
    ├── Single-Valued
    ├── Multi-Valued
    ├── Stored
    ├── Derived
    ├── Key
    ├── Optional
    └── Complex

Quick Memory Trick

    Simple → Cannot divide

    Composite → Can divide

    Single → One value

    Multi → Many values

    Stored → Saved

    Derived → Calculated

    Key → Unique

    Optional → May be NULL

    Complex → Composite + Multi-valued

**Remember:**

> Choosing the correct attribute type leads to cleaner ER diagrams,
> better database design, and fewer normalization problems later.
