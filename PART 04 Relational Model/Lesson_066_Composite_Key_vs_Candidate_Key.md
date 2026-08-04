# Lesson 066 --- Composite Key vs Candidate Key (and Other Key Comparisons)

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   Composite Key vs Candidate Key
-   Composite Key vs Primary Key
-   Composite Key vs Super Key
-   Natural Key vs Surrogate Key vs Composite Key
-   How to choose the right key
-   Industry best practices
-   SQL examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Why This Lesson?

Many students memorize key definitions but get confused when
interviewers ask:

> "Should I use a Composite Key or a Surrogate Key?"

or

> "Can a Composite Key also be a Candidate Key?"

This lesson answers those questions.

------------------------------------------------------------------------

# 2. Key Hierarchy

``` text
Super Key
    │
Remove unnecessary attributes
    ▼
Candidate Key(s)
    │
Choose one
    ▼
Primary Key

Remaining Candidate Keys
    ▼
Alternate Keys
```

A **Composite Key** can appear at multiple levels.

------------------------------------------------------------------------

# 3. Composite Key vs Candidate Key

  Composite Key                 Candidate Key
  ----------------------------- ----------------------------
  Uses two or more attributes   Minimal unique key
  May or may not be minimal     Always minimal
  Describes the structure       Describes uniqueness
  Can be a Candidate Key        May be single or composite

### Example

    Enrollment

    StudentID
    CourseID
    Semester

Candidate Key:

    (StudentID, CourseID)

Since it has multiple columns, it is also a **Composite Key**.

------------------------------------------------------------------------

# 4. Composite Key vs Primary Key

  Composite Key                Primary Key
  ---------------------------- -----------------------------------
  Two or more columns          Official identifier
  May be selected              One chosen Candidate Key
  May not be the Primary Key   Can be composite or single-column

Example:

``` sql
PRIMARY KEY(StudentID, CourseID)
```

------------------------------------------------------------------------

# 5. Composite Key vs Super Key

  Composite Key         Super Key
  --------------------- ---------------------------
  Usually minimal       May contain extra columns
  Multiple attributes   One or more attributes

Example:

Candidate/Composite Key

    (StudentID, CourseID)

Super Key

    (StudentID, CourseID, Grade)

`Grade` is unnecessary.

------------------------------------------------------------------------

# 6. Natural Key vs Surrogate Key vs Composite Key

  Natural Key        Surrogate Key           Composite Key
  ------------------ ----------------------- ------------------------------
  Real-world value   Artificial identifier   Combination of attributes
  Business meaning   No business meaning     May have business meaning
  May change         Stable                  Depends on attributes
  Example: ISBN      Example: BookID         Example: OrderID + ProductID

------------------------------------------------------------------------

# 7. When Should You Use Each?

### Use a Natural Key when

-   Value is permanent
-   Already unique
-   Rarely changes

Examples:

-   ISBN
-   VIN
-   Passport Number

------------------------------------------------------------------------

### Use a Surrogate Key when

-   Business values may change
-   Simpler joins are desired
-   Industry applications need stable IDs

Examples:

-   CustomerID
-   EmployeeID
-   OrderID

------------------------------------------------------------------------

### Use a Composite Key when

-   No single column is unique
-   Modeling junction tables
-   Representing many-to-many relationships

Examples:

-   Enrollment(StudentID, CourseID)
-   OrderDetails(OrderID, ProductID)

------------------------------------------------------------------------

# 8. Decision Tree

``` text
Can one stable attribute identify every row?

        │
   Yes ─┴─ No
   │         │
Natural?   Need multiple attributes?
   │         │
Yes         Yes
 │           │
Natural    Composite
 Key         Key

Business value unstable?

        │
      Yes
        │
   Surrogate Key
```

------------------------------------------------------------------------

# 9. Industry Examples

  System          Recommended Key
  --------------- --------------------------------------------
  Student         StudentID (Surrogate)
  Book            BookID + ISBN (Surrogate + UNIQUE Natural)
  Enrollment      Composite Key
  Order           OrderID (Surrogate)
  Order Details   Composite Key

------------------------------------------------------------------------

# 10. SQL Examples

### Composite Primary Key

``` sql
CREATE TABLE Enrollment(
 StudentID INT,
 CourseID INT,
 PRIMARY KEY(StudentID, CourseID)
);
```

### Surrogate Key

``` sql
CREATE TABLE Customer(
 CustomerID INT AUTO_INCREMENT PRIMARY KEY,
 Email VARCHAR(100) UNIQUE
);
```

------------------------------------------------------------------------

# 11. Common Interview Scenarios

**Q:** Can a Composite Key be a Candidate Key?

**A:** Yes. If it is minimal and unique.

------------------------------------------------------------------------

**Q:** Can a Composite Key be a Primary Key?

**A:** Yes.

------------------------------------------------------------------------

**Q:** Can a Candidate Key contain multiple columns?

**A:** Yes.

------------------------------------------------------------------------

**Q:** Does every Composite Key become a Primary Key?

**A:** No.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Assuming every Composite Key is a Candidate Key.

❌ Using a Composite Key when one stable attribute already exists.

❌ Replacing all Natural Keys with Surrogate Keys without keeping UNIQUE
constraints.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is a Composite Key?
2.  What is a Candidate Key?

### Intermediate

1.  Composite Key vs Candidate Key.
2.  Composite Key vs Primary Key.

### Advanced

1.  When would you avoid a Composite Key?
2.  Why do many enterprise systems prefer Surrogate Keys?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Choose the best key for:

```{=html}
<!-- -->
```
    Enrollment(StudentID, CourseID)

2.  Choose the best key for:

```{=html}
<!-- -->
```
    Customer(Name, Email, Phone)

3.  Decide whether the following should use a Natural, Surrogate, or
    Composite Key:

-   Library Book
-   Flight Booking
-   Employee
-   Order Details

------------------------------------------------------------------------

# Revision Notes

``` text
Super Key
   │
Candidate Key
   │
Primary Key

Composite Key
= Multiple columns

Natural Key
= Real-world value

Surrogate Key
= Artificial value
```

## Memory Trick

``` text
Composite = Combination

Candidate = Minimal

Primary = Chosen

Surrogate = Substitute

Natural = Real
```

## Final Takeaway

A **Composite Key** describes **how uniqueness is achieved** using
multiple attributes.

A **Candidate Key** describes **the smallest possible unique
identifier**.

A **Primary Key** is simply the Candidate Key chosen for implementation.

A **Surrogate Key** is an artificial identifier created for stability,
while a **Natural Key** comes directly from the business domain.

Choosing the right key is one of the most important design decisions in
database development. A thoughtful choice makes querying, indexing, and
maintenance much easier. A poor choice has an uncanny habit of appearing
in every future bug report.
