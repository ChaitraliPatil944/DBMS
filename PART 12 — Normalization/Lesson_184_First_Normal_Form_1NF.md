# Lesson 184 --- First Normal Form (1NF)

> **Part 12 --- Normalization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What First Normal Form (1NF) is
-   Why 1NF is important
-   Rules of 1NF
-   Atomic values
-   Repeating groups
-   Converting a table into 1NF
-   Advantages and limitations
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a student table like this:

  StudentID   Name   Courses
  ----------- ------ ---------------
  101         Asha   DBMS, SQL, AI

One cell contains multiple values.

This violates **First Normal Form (1NF)**.

------------------------------------------------------------------------

# 2. What is First Normal Form?

A table is in **First Normal Form (1NF)** if:

-   Every column contains **atomic (indivisible)** values.
-   There are **no repeating groups**.
-   Every row is uniquely identifiable.

``` text
One Cell
    │
One Value
```

------------------------------------------------------------------------

# 3. Why Do We Need 1NF?

Without 1NF:

-   Searching becomes difficult.
-   Updating data becomes confusing.
-   Data redundancy increases.
-   Queries become more complex.

1NF organizes data into a predictable structure.

------------------------------------------------------------------------

# 4. Atomic Values

Atomic means a value cannot be divided further.

❌ Not Atomic

  Student   Courses
  --------- -----------
  Asha      DBMS, SQL

✅ Atomic

  Student   Course
  --------- --------
  Asha      DBMS
  Asha      SQL

------------------------------------------------------------------------

# 5. Repeating Groups

Wrong:

  OrderID   Product1   Product2   Product3
  --------- ---------- ---------- ----------

Correct:

  OrderID   Product
  --------- ----------
  1         Laptop
  1         Mouse
  1         Keyboard

------------------------------------------------------------------------

# 6. Converting to 1NF

Before:

  StudentID   Name   PhoneNumbers
  ----------- ------ --------------
  101         Asha   9876,9123

After:

  StudentID   Name   PhoneNumber
  ----------- ------ -------------
  101         Asha   9876
  101         Asha   9123

------------------------------------------------------------------------

# 7. Characteristics of 1NF

-   One value per cell
-   No repeating columns
-   Consistent data types in each column
-   Unique rows using a key

------------------------------------------------------------------------

# 8. Real-World Example

Customer table:

❌

  Customer   Emails
  ---------- -------------------------
  Rahul      a@gmail.com,b@yahoo.com

✅

  Customer   Email
  ---------- -------------
  Rahul      a@gmail.com
  Rahul      b@yahoo.com

------------------------------------------------------------------------

# 9. Advantages

-   Simple queries
-   Easier searching
-   Better consistency
-   Foundation for higher normal forms

------------------------------------------------------------------------

# 10. Limitations

Even after 1NF:

-   Partial dependency may still exist.
-   Transitive dependency may still exist.
-   Redundancy may remain.

These are solved in later normal forms.

------------------------------------------------------------------------

# 11. Best Practices

-   Store one value per field.
-   Avoid comma-separated values.
-   Design tables with clear primary keys.
-   Eliminate repeating groups.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Storing multiple phone numbers in one column.

❌ Creating Product1, Product2, Product3 columns.

❌ Assuming 1NF removes all redundancy.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is 1NF?
2.  What is an atomic value?
3.  What is a repeating group?

### Intermediate

1.  How do you convert a table into 1NF?
2.  Does 1NF remove redundancy completely?

### Advanced

1.  Why is 1NF the foundation of normalization?
2.  Can a table be in 1NF but not in 2NF?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Convert a non-atomic table into 1NF.
2.  Identify repeating groups.
3.  Explain atomicity with examples.
4.  Compare a table before and after 1NF.

------------------------------------------------------------------------

# Revision Notes

``` text
1NF
 │
Atomic Values
 │
No Repeating Groups
 │
One Value Per Cell
```

## Memory Trick

``` text
1NF

=

One

Value

Per

Cell
```

## Key Points

-   1NF requires atomic values.
-   Each cell stores exactly one value.
-   Repeating groups are removed.
-   It is the first step of normalization.
-   1NF alone does not eliminate all redundancy.

------------------------------------------------------------------------

# Final Takeaway

First Normal Form is the starting point of normalization. It ensures
that every table has a clean, consistent structure by storing only one
value in each cell and eliminating repeating groups. Once a table
satisfies 1NF, it becomes much easier to analyze dependencies and
progress to 2NF and higher normal forms.
