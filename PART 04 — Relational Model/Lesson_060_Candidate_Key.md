# Lesson 060 --- Candidate Key

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Candidate Key is
-   Why Candidate Keys are needed
-   Minimal Super Key concept
-   Characteristics of Candidate Keys
-   How to identify Candidate Keys
-   Candidate Key vs Super Key
-   Candidate Key vs Primary Key
-   Real-world examples
-   SQL examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

In the previous lesson, we learned that a **Super Key** uniquely
identifies every tuple.

However, many Super Keys contain unnecessary attributes.

Example:

    StudentID

and

    StudentID + Name

Both uniquely identify a student.

But adding **Name** is unnecessary.

To eliminate unnecessary attributes, we use **Candidate Keys**.

------------------------------------------------------------------------

# 2. What is a Candidate Key?

A **Candidate Key** is a **minimal Super Key**.

It uniquely identifies every tuple **without containing any unnecessary
attributes**.

Think of it as the **smallest possible unique identifier**.

------------------------------------------------------------------------

# 3. Why Do We Need Candidate Keys?

Without Candidate Keys:

    StudentID + Name + Email + Phone

works as a Super Key.

But it is inefficient.

Candidate Keys help us choose the simplest unique identifier.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Imagine every student has:

    Roll Number
    Name
    Class

To identify a student:

    Roll Number

is enough.

Using

    Roll Number + Name + Class

also works, but carries extra baggage.

The simplest unique identifier becomes the Candidate Key.

------------------------------------------------------------------------

# 5. Characteristics of a Candidate Key

A Candidate Key:

-   Uniquely identifies every tuple
-   Is minimal
-   Contains no unnecessary attributes
-   Cannot contain duplicate values
-   Cannot be reduced further

------------------------------------------------------------------------

# 6. Candidate Key is a Minimal Super Key

    Super Keys

    StudentID

    StudentID + Name

    StudentID + Email

    StudentID + Name + Email

    ↓

    Remove unnecessary attributes

    ↓

    Candidate Key

    StudentID

------------------------------------------------------------------------

# 7. Multiple Candidate Keys

A relation can have more than one Candidate Key.

Example:

    Student

    StudentID
    Email
    AadhaarNumber
    Name

Assume these are unique:

-   StudentID
-   Email
-   AadhaarNumber

Candidate Keys:

    StudentID

    Email

    AadhaarNumber

------------------------------------------------------------------------

# 8. Candidate Key vs Super Key

  Candidate Key             Super Key
  ------------------------- ----------------------------------
  Minimal                   May contain extra attributes
  Unique                    Unique
  No redundant attributes   May contain redundant attributes

------------------------------------------------------------------------

# 9. Candidate Key vs Primary Key

  Candidate Key      Primary Key
  ------------------ ---------------------------
  Many may exist     Only one is selected
  All are eligible   Chosen for implementation

Hierarchy:

    Super Key
         │
    Minimal
         ▼
    Candidate Key
         │
    Selected
         ▼
    Primary Key

------------------------------------------------------------------------

# 10. How to Identify Candidate Keys

Step 1

Find all unique attributes.

Step 2

Generate Super Keys.

Step 3

Remove unnecessary attributes.

Step 4

The remaining minimal keys are Candidate Keys.

------------------------------------------------------------------------

# 11. SQL Example

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Email VARCHAR(100) UNIQUE,
    Aadhaar VARCHAR(20) UNIQUE,
    Name VARCHAR(100)
);
```

Candidate Keys:

-   StudentID
-   Email
-   Aadhaar

Only one becomes the Primary Key.

------------------------------------------------------------------------

# 12. Real-World Examples

## Banking

Candidate Keys:

-   Account Number
-   UPI ID

## Hospital

Candidate Keys:

-   PatientID
-   National ID

## Library

Candidate Keys:

-   BookID
-   ISBN

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Assuming there can be only one Candidate Key.

❌ Confusing Candidate Key with Primary Key.

❌ Forgetting the word **minimal**.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is a Candidate Key?
2.  Why is it called a minimal Super Key?

### Intermediate

1.  Candidate Key vs Super Key?
2.  Candidate Key vs Primary Key?

### Advanced

Given:

    Employee(
    EmployeeID,
    Email,
    PassportNo,
    Name
    )

Assume EmployeeID, Email, and PassportNo are unique.

List all Candidate Keys.

------------------------------------------------------------------------

# 15. Practice Problems

1.  Identify Candidate Keys for:

```{=html}
<!-- -->
```
    Book(
    BookID,
    ISBN,
    Title,
    Author
    )

2.  Find all Super Keys.

3.  Remove unnecessary attributes.

4.  Explain why the remaining keys are Candidate Keys.

------------------------------------------------------------------------

# Revision Notes

    Super Key

    ↓

    Remove Extra Attributes

    ↓

    Candidate Key

    ↓

    Choose One

    ↓

    Primary Key

Memory Trick

    Candidate

    =

    Capable

    Eligible

    Minimal

Key Points

-   Every Candidate Key is a Super Key.
-   Every Primary Key is a Candidate Key.
-   A relation may have multiple Candidate Keys.
-   Candidate Keys contain no redundant attributes.

**Remember:**

> A Candidate Key is the cleanest and smallest unique identifier
> available in a relation. It represents the best possible choices for
> uniquely identifying records. The database later selects one of these
> as the Primary Key, leaving the others as Alternate Keys. Simplicity
> is valuable. Databases, unlike people, genuinely appreciate doing less
> work when the result is identical.
