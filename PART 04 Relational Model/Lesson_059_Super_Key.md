# Lesson 059 --- Super Key

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Super Key is
-   Why keys are needed
-   Characteristics of a Super Key
-   Minimal vs Non-minimal uniqueness
-   Super Key vs Candidate Key
-   Super Key vs Primary Key
-   Real-world examples
-   SQL examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a college database.

    Student

    ID   Name    Email
    101  Alice   alice@mail.com
    102  Bob     bob@mail.com

How do we uniquely identify Alice?

Using only:

    Name

is risky because two students may share the same name.

We need something unique.

That is why databases use **Keys**.

The broadest type of key is the **Super Key**.

------------------------------------------------------------------------

# 2. Why Were Keys Introduced?

Without keys:

-   Duplicate records appear
-   Updates become confusing
-   Relationships fail
-   Data integrity suffers

Keys solve these problems by uniquely identifying every tuple.

------------------------------------------------------------------------

# 3. What is a Super Key?

A **Super Key** is **any attribute or combination of attributes that
uniquely identifies every tuple in a relation.**

A Super Key may contain **extra attributes** that are not required for
uniqueness.

------------------------------------------------------------------------

# 4. Example

Relation:

    Student

    +-----+-------+-------------------+
    | ID  | Name  | Email             |
    +-----+-------+-------------------+
    |101  |Alice  |alice@mail.com     |
    |102  |Bob    |bob@mail.com       |
    +-----+-------+-------------------+

Possible Super Keys:

    StudentID

    Email

    StudentID + Name

    StudentID + Email

    StudentID + Name + Email

All uniquely identify a student.

Therefore, all are Super Keys.

------------------------------------------------------------------------

# 5. Child-Friendly Analogy

Imagine school ID cards.

Each student has:

    Roll Number

    Name

    Class

Roll Number alone identifies a student.

Adding Name and Class still identifies the same student.

    Roll Number

    ↓

    Super Key

    Roll Number + Name

    ↓

    Also Super Key

Extra information does not remove uniqueness.

------------------------------------------------------------------------

# 6. Characteristics of a Super Key

A Super Key:

-   Uniquely identifies every tuple
-   May consist of one or more attributes
-   May contain unnecessary attributes
-   Must never identify two different tuples

------------------------------------------------------------------------

# 7. Minimal vs Non-Minimal

    StudentID

Unique.

    StudentID + Name

Also unique.

But **Name** is unnecessary.

Therefore:

    StudentID

is minimal.

    StudentID + Name

is non-minimal.

This distinction leads to the **Candidate Key**, which we'll study next.

------------------------------------------------------------------------

# 8. Super Key vs Candidate Key

  Super Key                      Candidate Key
  ------------------------------ ---------------------
  Unique                         Unique
  May contain extra attributes   No extra attributes
  Can be non-minimal             Always minimal

Relationship:

    Super Keys

    ↓

    Remove unnecessary attributes

    ↓

    Candidate Keys

------------------------------------------------------------------------

# 9. Super Key vs Primary Key

  Super Key                      Primary Key
  ------------------------------ --------------------------
  Many can exist                 Only one is chosen
  May contain extra attributes   Minimal and selected
  Broad concept                  Practical implementation

Hierarchy:

    Super Key
          │
    Minimal
          ▼
    Candidate Key
          │
    Chosen
          ▼
    Primary Key

------------------------------------------------------------------------

# 10. SQL Example

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100),
    Email VARCHAR(100) UNIQUE
);
```

Possible Super Keys:

-   StudentID
-   Email
-   StudentID + Name
-   Email + Name
-   StudentID + Email

------------------------------------------------------------------------

# 11. Real-World Examples

## Banking

    AccountNo

    AccountNo + CustomerName

## Hospital

    PatientID

    PatientID + Name

## Library

    BookID

    BookID + Title

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Thinking every Super Key is a Primary Key.

❌ Thinking a Super Key must be minimal.

❌ Assuming only one Super Key exists.

A relation may have many Super Keys.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is a Super Key?
2.  Why are Super Keys needed?
3.  Give an example.

### Intermediate

1.  Super Key vs Candidate Key?
2.  Can a Super Key have extra attributes?

### Advanced

Given a relation:

    Student(ID, Email, Aadhaar, Name)

List all possible Super Keys.

------------------------------------------------------------------------

# 14. Practice Problems

1.  Identify all Super Keys for:

```{=html}
<!-- -->
```
    Employee(
    EmployeeID,
    Email,
    Phone,
    Name
    )

Assume EmployeeID and Email are unique.

2.  Which of the Super Keys are minimal?

3.  Explain why.

------------------------------------------------------------------------

# Revision Notes

    Super Key

    ↓

    Unique Identification

    ↓

    May Have Extra Attributes

Memory Trick

    Super

    =

    Superset

A Super Key is like a superset of uniqueness.

    Super Key
          │
    Remove Extra Attributes
          ▼
    Candidate Key

Key Points

-   Every Candidate Key is a Super Key.
-   Every Primary Key is a Candidate Key.
-   Not every Super Key is a Candidate Key.
-   Super Keys guarantee uniqueness, even if they contain unnecessary
    attributes.

**Remember:**

> A Super Key is any combination of attributes that uniquely identifies
> every row in a relation. It doesn't have to be efficient or minimal.
> It simply has to be unique. Databases appreciate precision. Humans
> tend to add extra columns "just to be safe," which is exactly why
> Candidate Keys were invented.
