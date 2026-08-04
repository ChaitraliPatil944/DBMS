# Lesson 088 --- Constraints Revision Notes & Cheat Sheet

> **Part 05 --- Constraints**

------------------------------------------------------------------------

# Purpose

This lesson is a **20--30 minute revision guide** for the complete
Constraints chapter.

------------------------------------------------------------------------

# 1. Constraints Overview

``` text
Constraints
│
├── Domain Constraint
├── Key Constraint
├── Entity Integrity
├── Referential Integrity
├── PRIMARY KEY
├── FOREIGN KEY
├── UNIQUE
├── NOT NULL
├── CHECK
└── DEFAULT
```

------------------------------------------------------------------------

# 2. Why Constraints Exist

Without constraints:

-   Duplicate data
-   Missing values
-   Invalid relationships
-   Broken business rules

With constraints:

-   Accurate data
-   Reliable relationships
-   Better security
-   Higher data quality

------------------------------------------------------------------------

# 3. Constraint Cheat Sheet

  -----------------------------------------------------------------------
  Constraint              Purpose                 Example
  ----------------------- ----------------------- -----------------------
  Domain                  Restrict allowed values Age 18--60

  Key                     Enforce uniqueness      StudentID

  Entity Integrity        PK is UNIQUE + NOT NULL EmployeeID

  Referential Integrity   Valid parent-child      CustomerID in Orders
                          relation                

  PRIMARY KEY             Official identifier     OrderID

  FOREIGN KEY             Relationship            CustomerID

  UNIQUE                  No duplicates           Email

  NOT NULL                Mandatory value         Name

  CHECK                   Business rule           Salary \>= 0

  DEFAULT                 Automatic value         Status='Pending'
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 4. Constraint Decision Tree

``` text
Need row identity?
      │
PRIMARY KEY

Need relationship?
      │
FOREIGN KEY

Need another unique value?
      │
UNIQUE

Need mandatory data?
      │
NOT NULL

Need validation?
      │
CHECK

Need automatic value?
      │
DEFAULT
```

------------------------------------------------------------------------

# 5. Comparison Tables

## PRIMARY KEY vs UNIQUE

  PRIMARY KEY         UNIQUE
  ------------------- ----------------------
  One per table       Multiple allowed
  UNIQUE + NOT NULL   Unique only
  Main identifier     Alternate identifier

## PRIMARY KEY vs FOREIGN KEY

  PRIMARY KEY      FOREIGN KEY
  ---------------- --------------------
  Identifies row   References row
  Parent           Child
  Unique           Duplicates allowed

## CHECK vs NOT NULL

  CHECK             NOT NULL
  ----------------- ----------------
  Validates value   Requires value

## CHECK vs DEFAULT

  CHECK             DEFAULT
  ----------------- ----------------
  Rejects invalid   Supplies value

------------------------------------------------------------------------

# 6. Integrity Rules

``` text
Entity Integrity
      │
Primary Key
      │
UNIQUE + NOT NULL

Referential Integrity
      │
Foreign Key
      │
Valid Parent Reference
```

------------------------------------------------------------------------

# 7. SQL Syntax Summary

``` sql
PRIMARY KEY (StudentID)

FOREIGN KEY (DeptID)
REFERENCES Department(DeptID)

Email VARCHAR(100) UNIQUE

Name VARCHAR(100) NOT NULL

CHECK (Age >= 18)

Status VARCHAR(20)
DEFAULT 'Pending'
```

------------------------------------------------------------------------

# 8. 50 Rapid-Fire Questions

1.  What is a constraint?
2.  Why are constraints needed?
3.  Define Domain Constraint.
4.  Define Key Constraint.
5.  Define Entity Integrity.
6.  Define Referential Integrity.
7.  What is PRIMARY KEY?
8.  What is FOREIGN KEY?
9.  What is UNIQUE?
10. What is NOT NULL?
11. What is CHECK?
12. What is DEFAULT?
13. PRIMARY KEY vs UNIQUE?
14. PRIMARY KEY vs FOREIGN KEY?
15. CHECK vs NOT NULL?
16. CHECK vs DEFAULT?
17. DEFAULT vs NOT NULL?
18. Can PRIMARY KEY contain NULL?
19. Can FOREIGN KEY contain duplicates?
20. Can FOREIGN KEY reference UNIQUE?
21. What is CASCADE?
22. What is RESTRICT?
23. What is SET NULL?
24. What is NO ACTION?
25. What is an orphan record? 26-50. Revise all constraint rules without
    notes.

------------------------------------------------------------------------

# 9. Common Interview Traps

❌ PRIMARY KEY = UNIQUE

❌ DEFAULT prevents NULL

❌ FOREIGN KEY must be unique

❌ CHECK validates relationships

❌ NULL = 0

------------------------------------------------------------------------

# 10. Exam-Day Checklist

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

✓ Comparison Tables

✓ Real-world Examples
```

------------------------------------------------------------------------

# 11. Memory Map

``` text
Constraints
│
├── Identity
│   └── PRIMARY KEY
│
├── Relationships
│   └── FOREIGN KEY
│
├── Uniqueness
│   └── UNIQUE
│
├── Mandatory Data
│   └── NOT NULL
│
├── Validation
│   └── CHECK
│
└── Automation
    └── DEFAULT
```

------------------------------------------------------------------------

# Memory Tricks

``` text
PRIMARY KEY = Identity

FOREIGN KEY = Relationship

UNIQUE = No Duplicates

NOT NULL = Must Exist

CHECK = Must Be Valid

DEFAULT = Automatic Value
```

------------------------------------------------------------------------

# Final Chapter Summary

🎉 **Congratulations!**

You have completed **Part 05 --- Constraints**.

You now understand:

-   Domain and Key Constraints
-   Entity & Referential Integrity
-   PRIMARY KEY and FOREIGN KEY
-   UNIQUE and NOT NULL
-   CHECK and DEFAULT
-   SQL implementation of all major constraints
-   Real-world applications
-   Interview questions
-   Practice problems
-   Database design using constraints

These concepts form the foundation of reliable relational databases.
Every production database depends on constraints to protect data
integrity, enforce business rules, and maintain consistent
relationships. Well-chosen constraints reduce bugs, simplify application
logic, and keep data trustworthy long after the application is deployed.
