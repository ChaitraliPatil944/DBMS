# Lesson 064 --- Composite Key

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Composite Key is
-   Why Composite Keys are needed
-   Characteristics of Composite Keys
-   Composite Key vs Primary Key
-   Composite Key vs Candidate Key
-   Composite Key vs Super Key
-   Composite Key vs Foreign Key
-   SQL implementation
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Until now, we've identified rows using a **single attribute**.

Example:

    Student
    ---------
    StudentID

But not every table can be uniquely identified using one column.

Sometimes, **two or more attributes together** uniquely identify a row.

This leads to the concept of a **Composite Key**.

------------------------------------------------------------------------

# 2. Why Do We Need Composite Keys?

Consider a student enrollment table.

    Enrollment

    StudentID

    CourseID

Can StudentID alone identify a record?

❌ No.

A student can enroll in many courses.

Can CourseID alone identify a record?

❌ No.

Many students can enroll in the same course.

But together:

    StudentID + CourseID

uniquely identify one enrollment.

------------------------------------------------------------------------

# 3. What is a Composite Key?

A **Composite Key** is a key formed by combining **two or more
attributes** to uniquely identify each tuple in a relation.

None of the individual attributes alone can uniquely identify every row.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Imagine apartment addresses.

    Building Number

    Apartment Number

Apartment 101 exists in many buildings.

Building 5 contains many apartments.

Only together:

    Building 5 + Apartment 101

identify one apartment.

Exactly like a Composite Key.

------------------------------------------------------------------------

# 5. Example

    Enrollment

    +-----------+----------+-------+
    |StudentID  |CourseID  |Grade  |
    +-----------+----------+-------+
    |101        |DB101     |A      |
    |101        |AI201     |B      |
    |102        |DB101     |A      |
    +-----------+----------+-------+

Composite Key:

    (StudentID, CourseID)

------------------------------------------------------------------------

# 6. Characteristics of a Composite Key

A Composite Key:

-   Contains two or more attributes
-   Uniquely identifies each tuple
-   Is minimal
-   Cannot contain unnecessary attributes
-   May be used as a Primary Key

------------------------------------------------------------------------

# 7. SQL Implementation

``` sql
CREATE TABLE Enrollment(
    StudentID INT,
    CourseID VARCHAR(20),
    Grade CHAR(1),
    PRIMARY KEY(StudentID, CourseID)
);
```

The database treats both columns together as the Primary Key.

------------------------------------------------------------------------

# 8. Composite Key vs Primary Key

  Composite Key                  Primary Key
  ------------------------------ ----------------------------------
  May contain multiple columns   Can contain one or more columns
  Describes the structure        Official identifier of the table

A Primary Key **can be** a Composite Key.

------------------------------------------------------------------------

# 9. Composite Key vs Candidate Key

  Composite Key                 Candidate Key
  ----------------------------- --------------------------------------
  Two or more attributes        May be single or multiple attributes
  Minimal if chosen correctly   Always minimal

------------------------------------------------------------------------

# 10. Composite Key vs Super Key

  Composite Key     Super Key
  ----------------- ------------------------------
  Usually minimal   May contain extra attributes
  Unique            Unique

Example:

Composite Key:

    (StudentID, CourseID)

Super Key:

    (StudentID, CourseID, Grade)

The extra attribute is unnecessary.

------------------------------------------------------------------------

# 11. Composite Key vs Foreign Key

  Composite Key         Foreign Key
  --------------------- --------------------------
  Identifies rows       References another table
  Usually unique        May repeat
  Part of Primary Key   Used for relationships

A composite key may also be referenced as a **composite foreign key**.

------------------------------------------------------------------------

# 12. Real-World Examples

## University

    Enrollment

    (StudentID, CourseID)

------------------------------------------------------------------------

## Online Shopping

    OrderDetails

    (OrderID, ProductID)

------------------------------------------------------------------------

## Library

    BookIssue

    (BookID, StudentID)

------------------------------------------------------------------------

## Airline Reservation

    SeatBooking

    (FlightID, SeatNumber)

------------------------------------------------------------------------

## Cricket Tournament

    MatchPlayer

    (MatchID, PlayerID)

------------------------------------------------------------------------

# 13. Advantages

-   Represents many-to-many relationships naturally
-   Prevents duplicate combinations
-   Reduces unnecessary surrogate columns
-   Preserves business rules

------------------------------------------------------------------------

# 14. Limitations

-   Larger indexes
-   More complex joins
-   Longer foreign key references
-   Slightly slower comparisons than a single-column key

------------------------------------------------------------------------

# 15. Common Mistakes

❌ Choosing attributes that are not minimal.

❌ Adding unnecessary columns.

❌ Confusing Composite Keys with Composite Attributes.

Remember:

-   Composite Attribute → One attribute split into parts.
-   Composite Key → Multiple attributes combined for uniqueness.

------------------------------------------------------------------------

# 16. Interview Questions

### Beginner

1.  What is a Composite Key?
2.  Why is it needed?
3.  Give an example.

### Intermediate

1.  Composite Key vs Primary Key?
2.  Can a Primary Key be composite?

### Advanced

Design tables for:

-   Student Enrollment
-   Order Details
-   Flight Booking

Identify the Composite Keys.

------------------------------------------------------------------------

# 17. Practice Problems

1.  Identify Composite Keys for:

```{=html}
<!-- -->
```
    OrderDetails(
    OrderID,
    ProductID,
    Quantity
    )

2.  Write SQL to create a composite primary key.

3.  Explain why StudentID alone cannot identify an enrollment.

------------------------------------------------------------------------

# Revision Notes

    Single Attribute
          │
          ▼
    Simple Key

    Two or More Attributes
          │
          ▼
    Composite Key

Memory Trick

    Composite

    =

    Combination

Quick Comparison

  Key Type        Description
  --------------- ------------------------------------
  Primary Key     Official unique identifier
  Composite Key   Combination of multiple attributes
  Candidate Key   Minimal unique key
  Super Key       Any unique combination

Key Points

-   Composite Keys use two or more attributes.
-   They uniquely identify a row together.
-   They are common in junction tables.
-   A Composite Key can serve as the Primary Key.
-   They help model many-to-many relationships correctly.

**Remember:**

> A Composite Key exists because sometimes no single attribute is
> sufficient to identify a record. By combining multiple attributes, the
> database captures the true uniqueness of the data. It's a reminder
> that context matters. One column may tell part of the story, but
> together they identify the whole record.
