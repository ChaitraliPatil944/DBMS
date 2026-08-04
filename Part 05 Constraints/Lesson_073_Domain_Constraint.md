# Lesson 073 --- Domain Constraint

> **Part 05 --- Constraints**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Domain Constraint is
-   Why Domain Constraints are important
-   Mathematical origin from Set Theory
-   Domain vs Data Type
-   Valid and invalid domain values
-   SQL implementation
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Suppose a Student table allows the following data:

``` text
Age = Banana
Semester = 25
BloodGroup = Purple
```

The database stores data, but the data is meaningless.

A **Domain Constraint** prevents this by allowing only valid values.

------------------------------------------------------------------------

# 2. What is a Domain Constraint?

A **Domain Constraint** ensures that every value stored in an attribute
belongs to its predefined **domain** (allowed set of values).

``` text
Attribute
    │
Allowed Values (Domain)
    │
Only Valid Data
```

------------------------------------------------------------------------

# 3. Mathematical Origin

The idea comes from **Set Theory**.

Example:

``` text
Semester Domain

{1,2,3,4,5,6,7,8}
```

Only these values belong to the domain.

------------------------------------------------------------------------

# 4. Why Do We Need Domain Constraints?

Without domain constraints:

-   Invalid values are accepted.
-   Reports become unreliable.
-   Business rules are violated.

With domain constraints:

-   Data stays meaningful.
-   Errors are prevented early.
-   Data quality improves.

------------------------------------------------------------------------

# 5. Child-Friendly Analogy

Imagine a multiple-choice exam.

Question:

``` text
Gender
```

Allowed answers:

``` text
Male
Female
Other
```

If someone writes:

``` text
Elephant
```

the answer is rejected.

That is exactly how a Domain Constraint works.

------------------------------------------------------------------------

# 6. Domain vs Data Type

  Data Type                Domain Constraint
  ------------------------ -----------------------------
  Defines storage format   Defines allowed values
  INT                      0--100
  VARCHAR                  Only valid department names
  DATE                     Valid date range

Example:

``` text
Age

INT
↓

18–60
```

The data type says **number**.

The domain says **which numbers**.

------------------------------------------------------------------------

# 7. Valid vs Invalid Values

  Attribute     Valid    Invalid
  ------------- -------- ---------
  Age           21       Apple
  Semester      5        15
  Blood Group   O+       Blue
  Status        Active   Flying

------------------------------------------------------------------------

# 8. SQL Implementation

## Example 1: Age

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Age INT CHECK (Age BETWEEN 16 AND 60)
);
```

------------------------------------------------------------------------

## Example 2: Department

``` sql
CREATE TABLE Student(
    Department VARCHAR(20)
    CHECK (Department IN
    ('CSE','IT','ECE','AIML'))
);
```

------------------------------------------------------------------------

## Example 3: Order Status

``` sql
CREATE TABLE Orders(
    Status VARCHAR(20)
    CHECK (Status IN
    ('Pending','Packed','Shipped','Delivered','Cancelled'))
);
```

------------------------------------------------------------------------

# 9. How Domain Constraints Work

``` text
User Input
     │
     ▼
Domain Validation
     │
 ┌───┴────┐
 │        │
Valid   Invalid
 │        │
 ▼        ▼
Stored  Rejected
```

------------------------------------------------------------------------

# 10. Real-World Examples

## Banking

Account Type

``` text
Savings
Current
Salary
```

------------------------------------------------------------------------

## Hospital

Blood Group

``` text
A+
A-
B+
B-
AB+
AB-
O+
O-
```

------------------------------------------------------------------------

## University

Semester

``` text
1–8
```

------------------------------------------------------------------------

## E-commerce

Order Status

``` text
Pending
Packed
Shipped
Delivered
Cancelled
```

------------------------------------------------------------------------

# 11. Advantages

-   Prevents invalid data
-   Improves consistency
-   Enforces business rules
-   Simplifies validation
-   Improves reporting accuracy

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Assuming `INT` alone prevents bad values.

❌ Forgetting to validate text values.

❌ Using inconsistent spellings:

``` text
CSE
Computer Science
Comp Sci
```

Choose one standardized domain.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is a Domain Constraint?
2.  Why is it needed?
3.  Domain vs Data Type?

### Intermediate

1.  How is a Domain Constraint implemented?
2.  Give three real-world examples.

### Advanced

1.  Design a domain for an airline booking system.
2.  How do domain constraints improve data integrity?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Design domains for:

    -   Age
    -   Salary
    -   Product Category
    -   Payment Status

2.  Write SQL using `CHECK`.

3.  Identify whether the following values violate their domains.

------------------------------------------------------------------------

# Revision Notes

``` text
Domain
    │
Allowed Values
    │
Constraint
    │
Valid Data
```

## Memory Trick

``` text
D A V

Domain
Allowed
Values
```

## Key Points

-   Every attribute has a domain.
-   Domain Constraints ensure values belong to that domain.
-   Data types and domain constraints work together.
-   `CHECK` is commonly used to enforce domains.
-   Strong domains improve database quality.

------------------------------------------------------------------------

# Final Takeaway

A Domain Constraint is the database's first line of defense against
invalid information. It ensures every value stored in a column makes
sense according to the business rules. The earlier invalid data is
stopped, the fewer problems appear later in reports, analytics, and
applications. Databases are remarkably patient, but they still prefer
"Age = 21" over "Age = Banana."
