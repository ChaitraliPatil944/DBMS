# Lesson 085 --- Constraints Interview Questions

> **Part 05 --- Constraints**

------------------------------------------------------------------------

# Purpose

This lesson is a complete interview revision guide for DBMS Constraints.
It covers conceptual, SQL, scenario-based, and tricky interview
questions with concise model answers.

------------------------------------------------------------------------

# Section 1 --- Beginner Questions

### 1. What is a database constraint?

**Answer:** A constraint is a rule enforced by the DBMS to ensure valid,
consistent, and reliable data.

### 2. Why are constraints needed?

To enforce business rules, improve data integrity, and prevent invalid
data.

### 3. Name the major constraints.

-   Domain Constraint
-   Key Constraint
-   Entity Integrity
-   Referential Integrity
-   PRIMARY KEY
-   FOREIGN KEY
-   UNIQUE
-   NOT NULL
-   CHECK
-   DEFAULT

### 4. What is a Domain Constraint?

Restricts values to a predefined domain.

### 5. What is a Key Constraint?

Ensures rows can be uniquely identified.

### 6. What is Entity Integrity?

Every PRIMARY KEY must be UNIQUE and NOT NULL.

### 7. What is Referential Integrity?

Every FOREIGN KEY must reference an existing PRIMARY KEY (or UNIQUE
Candidate Key), or be NULL if allowed.

### 8. What is a CHECK constraint?

Validates values using a logical condition.

### 9. What is a DEFAULT constraint?

Supplies a predefined value when none is provided.

### 10. What is a UNIQUE constraint?

Prevents duplicate values.

------------------------------------------------------------------------

# Section 2 --- Comparison Questions

  -----------------------------------------------------------------------
  Question                            Key Difference
  ----------------------------------- -----------------------------------
  PRIMARY KEY vs UNIQUE               Official identifier vs alternate
                                      unique value

  PRIMARY KEY vs FOREIGN KEY          Identifies vs references

  CHECK vs NOT NULL                   Validates values vs requires a
                                      value

  CHECK vs DEFAULT                    Validation vs automatic value

  DEFAULT vs NOT NULL                 Auto-fill vs mandatory

  Entity Integrity vs Referential     Identity vs relationships
  Integrity                           

  Domain Constraint vs CHECK          Allowed domain vs SQL condition
                                      implementation
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# Section 3 --- SQL Questions

### 11. Write a PRIMARY KEY.

``` sql
StudentID INT PRIMARY KEY
```

### 12. Write a UNIQUE constraint.

``` sql
Email VARCHAR(100) UNIQUE
```

### 13. Write a CHECK constraint.

``` sql
CHECK (Age >= 18)
```

### 14. Write a DEFAULT constraint.

``` sql
Status VARCHAR(20) DEFAULT 'Pending'
```

### 15. Write a FOREIGN KEY.

``` sql
FOREIGN KEY (DepartmentID)
REFERENCES Department(DepartmentID)
```

------------------------------------------------------------------------

# Section 4 --- Scenario Questions

### 16. Employee email must be unique.

**Answer:** `UNIQUE`

### 17. Every order must belong to a customer.

**Answer:** `FOREIGN KEY`

### 18. Salary cannot be negative.

**Answer:** `CHECK`

### 19. Student name is compulsory.

**Answer:** `NOT NULL`

### 20. New accounts should start as Active.

**Answer:** `DEFAULT 'Active'`

------------------------------------------------------------------------

# Section 5 --- Tricky Questions

### Can a table have multiple UNIQUE constraints?

✔ Yes.

### Can a table have multiple PRIMARY KEY constraints?

✘ No.

### Can a FOREIGN KEY contain duplicates?

✔ Yes.

### Can a FOREIGN KEY reference a UNIQUE Candidate Key?

✔ Yes.

### Does DEFAULT prevent NULL?

✘ No.

### Does CHECK prevent NULL?

Not necessarily. It depends on the column definition and DBMS.

### Is PRIMARY KEY automatically UNIQUE?

✔ Yes.

### Is PRIMARY KEY automatically NOT NULL?

✔ Yes.

------------------------------------------------------------------------

# Section 6 --- Advanced Questions

1.  Why should business rules be enforced in the database?
2.  Why are CHECK constraints preferred over application-only
    validation?
3.  When should you use a surrogate PRIMARY KEY?
4.  Explain ON DELETE CASCADE.
5.  Explain ON DELETE RESTRICT.
6.  Explain SET NULL.
7.  Why do orphan records occur?
8.  Why is Referential Integrity important?

------------------------------------------------------------------------

# Section 7 --- Coding Interview Questions

Write SQL to:

-   Create Student with PRIMARY KEY and UNIQUE Email.
-   Create Product with CHECK (Price \>= 0).
-   Create Orders with DEFAULT Status.
-   Create Customer and Orders using FOREIGN KEY.
-   Create Enrollment with Composite PRIMARY KEY.

------------------------------------------------------------------------

# Section 8 --- Common Interview Mistakes

❌ PRIMARY KEY and UNIQUE are identical.

❌ FOREIGN KEY values must be unique.

❌ DEFAULT replaces NOT NULL.

❌ CHECK validates relationships.

❌ NULL equals zero.

------------------------------------------------------------------------

# Rapid-Fire Revision

``` text
PRIMARY KEY → Identity

FOREIGN KEY → Relationship

UNIQUE → No duplicates

NOT NULL → Mandatory

CHECK → Validation

DEFAULT → Automatic value

Entity Integrity → PK

Referential Integrity → FK
```

------------------------------------------------------------------------

# Final Interview Checklist

``` text
✓ Domain Constraint

✓ Key Constraint

✓ Entity Integrity

✓ Referential Integrity

✓ PRIMARY KEY

✓ FOREIGN KEY

✓ UNIQUE

✓ NOT NULL

✓ CHECK

✓ DEFAULT

✓ SQL Syntax

✓ Comparison Questions

✓ Scenario Questions
```

# Final Takeaway

Interviewers rarely ask you to recite definitions. They want to know
whether you can choose the correct constraint for a real-world problem
and explain *why*. If you can confidently answer the questions in this
lesson and write the corresponding SQL without looking at notes, you are
well prepared for most DBMS interviews on constraints.
