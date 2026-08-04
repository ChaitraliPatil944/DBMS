# Lesson 082 --- DEFAULT Constraint

> **Part 05 --- Constraints**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the DEFAULT constraint is
-   Why DEFAULT is useful
-   How DEFAULT values work
-   DEFAULT vs NOT NULL
-   DEFAULT with functions
-   SQL implementation
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Suppose an online shopping website creates a new order.

The developer forgets to enter the order status.

Without a default value:

``` text
Status = NULL
```

With a DEFAULT constraint:

``` text
Status = Pending
```

The database automatically supplies a sensible value.

------------------------------------------------------------------------

# 2. What is the DEFAULT Constraint?

A **DEFAULT** constraint automatically assigns a predefined value to a
column when no value is provided during an `INSERT`.

``` text
No Value Provided
        │
        ▼
DEFAULT Value Applied
```

------------------------------------------------------------------------

# 3. Why Do We Need DEFAULT?

Without DEFAULT:

-   Missing values become NULL.
-   Applications must always provide every value.
-   Repetitive data entry increases.

With DEFAULT:

-   Common values are filled automatically.
-   Data entry becomes easier.
-   Tables remain consistent.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Imagine a school form.

If you don't specify the country, the form automatically fills:

``` text
Country = India
```

You can still change it later if needed.

That is how a DEFAULT constraint works.

------------------------------------------------------------------------

# 5. SQL Implementation

## Simple DEFAULT

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Country VARCHAR(50) DEFAULT 'India'
);
```

If Country is omitted:

``` text
Country = India
```

------------------------------------------------------------------------

## Numeric DEFAULT

``` sql
Quantity INT DEFAULT 1
```

------------------------------------------------------------------------

## Boolean DEFAULT

``` sql
IsActive BOOLEAN DEFAULT TRUE
```

------------------------------------------------------------------------

# 6. DEFAULT with Date & Time Functions

Many DBMSs support built-in functions.

``` sql
OrderDate DATE DEFAULT CURRENT_DATE
```

``` sql
CreatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP
```

The database inserts the current date or time automatically.

------------------------------------------------------------------------

# 7. DEFAULT vs NOT NULL

  DEFAULT                NOT NULL
  ---------------------- -------------------------
  Supplies a value       Requires a value
  Used when omitted      Rejects missing values
  Improves convenience   Enforces mandatory data

They are often used together.

Example:

``` sql
Status VARCHAR(20)
NOT NULL
DEFAULT 'Pending'
```

------------------------------------------------------------------------

# 8. How DEFAULT Works

``` text
INSERT Statement
       │
Value Supplied?
   ┌───┴────┐
   │        │
 Yes       No
  │         │
  ▼         ▼
Store   Apply DEFAULT
```

------------------------------------------------------------------------

# 9. Real-World Examples

### Banking

``` text
AccountStatus = Active
```

### Hospital

``` text
PatientStatus = Admitted
```

### University

``` text
Country = India
Semester = 1
```

### E-commerce

``` text
OrderStatus = Pending
Quantity = 1
```

------------------------------------------------------------------------

# 10. Advantages

-   Reduces repetitive data entry
-   Prevents unnecessary NULL values
-   Ensures consistent initial values
-   Simplifies application code
-   Improves user experience

------------------------------------------------------------------------

# 11. Common Mistakes

❌ Assuming DEFAULT overrides explicitly entered values.

❌ Thinking DEFAULT prevents NULL by itself.

❌ Forgetting that DEFAULT is used only when the column is omitted (or
the DBMS behavior allows it).

------------------------------------------------------------------------

# 12. Interview Questions

### Beginner

1.  What is the DEFAULT constraint?
2.  Why is it used?
3.  Give one example.

### Intermediate

1.  DEFAULT vs NOT NULL?
2.  Can DEFAULT use functions like CURRENT_DATE?

### Advanced

1.  Why is DEFAULT useful in production databases?
2.  What happens if a value is explicitly supplied?

------------------------------------------------------------------------

# 13. Practice Problems

1.  Create a Product table with:
    -   Quantity DEFAULT 1
    -   Status DEFAULT 'Available'
2.  Create an Orders table where:
    -   OrderDate uses CURRENT_DATE
    -   Status defaults to 'Pending'
3.  Combine DEFAULT with NOT NULL.

------------------------------------------------------------------------

# Revision Notes

``` text
DEFAULT
    │
No Value Given
    │
Automatic Value
```

## Memory Trick

``` text
DEFAULT

=

Automatic Starting Value
```

## Key Points

-   DEFAULT provides a value automatically.
-   It is applied only when no value is supplied.
-   It works with text, numbers, dates, booleans, and functions.
-   DEFAULT and NOT NULL are commonly used together.
-   DEFAULT improves consistency and reduces repetitive input.

------------------------------------------------------------------------

# Final Takeaway

The **DEFAULT** constraint helps a database make sensible decisions when
information is omitted. Instead of storing unnecessary `NULL` values or
forcing every application to repeat the same values, the DBMS fills in
appropriate defaults automatically. Small automation at the database
level often prevents large amounts of repetitive work later, which is
one of the few efficiencies humans and databases both seem to
appreciate.
