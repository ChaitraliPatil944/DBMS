# Lesson 083 --- Constraint Comparison

> **Part 05 --- Constraints**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will be able to:

-   Compare all major DBMS constraints
-   Choose the correct constraint for different scenarios
-   Avoid common interview mistakes
-   Understand how constraints work together
-   Revise the complete Constraints chapter quickly

------------------------------------------------------------------------

# 1. Why Compare Constraints?

Every constraint solves a different problem.

``` text
Wrong Data?
     │
Choose the Right Constraint
     │
Reliable Database
```

Knowing *when* to use each constraint is more important than memorizing
definitions.

------------------------------------------------------------------------

# 2. Complete Constraint Family

``` text
Constraints
│
├── Domain Constraint
├── Key Constraint
├── Entity Integrity
├── Referential Integrity
├── NOT NULL
├── UNIQUE
├── PRIMARY KEY
├── FOREIGN KEY
├── CHECK
└── DEFAULT
```

------------------------------------------------------------------------

# 3. Domain Constraint vs Key Constraint

  Domain Constraint         Key Constraint
  ------------------------- ---------------------------
  Controls allowed values   Controls uniqueness
  Based on business rules   Based on identity
  Example: Age 18--60       Example: StudentID unique

------------------------------------------------------------------------

# 4. Entity Integrity vs Referential Integrity

  Entity Integrity         Referential Integrity
  ------------------------ ----------------------------------
  Applies to PRIMARY KEY   Applies to FOREIGN KEY
  PK cannot be NULL        FK must reference a valid parent
  Gives identity           Preserves relationships

------------------------------------------------------------------------

# 5. PRIMARY KEY vs UNIQUE

  PRIMARY KEY           UNIQUE
  --------------------- ----------------------------
  One per table         Multiple allowed
  UNIQUE + NOT NULL     Only uniqueness guaranteed
  Official identifier   Alternate identifier

------------------------------------------------------------------------

# 6. PRIMARY KEY vs FOREIGN KEY

  PRIMARY KEY       FOREIGN KEY
  ----------------- --------------------
  Identifies rows   References rows
  Parent table      Child table
  Unique            Duplicates allowed
  Never NULL        May allow NULL

------------------------------------------------------------------------

# 7. CHECK vs NOT NULL

  CHECK                NOT NULL
  -------------------- ------------------------
  Validates values     Requires a value
  Example: Age \> 18   Example: Name required

------------------------------------------------------------------------

# 8. CHECK vs DEFAULT

  CHECK                    DEFAULT
  ------------------------ -------------------------
  Rejects invalid values   Supplies missing values
  Validation               Convenience

------------------------------------------------------------------------

# 9. DEFAULT vs NOT NULL

  DEFAULT                   NOT NULL
  ------------------------- -----------------------
  Inserts automatic value   Rejects missing value
  Optional helper           Mandatory rule

Example:

``` sql
Status VARCHAR(20)
NOT NULL
DEFAULT 'Pending'
```

------------------------------------------------------------------------

# 10. Constraint Selection Guide

``` text
Need unique identity?
        │
        ▼
PRIMARY KEY

Need another unique value?
        │
        ▼
UNIQUE

Need relationship?
        │
        ▼
FOREIGN KEY

Need mandatory value?
        │
        ▼
NOT NULL

Need value validation?
        │
        ▼
CHECK

Need automatic value?
        │
        ▼
DEFAULT
```

------------------------------------------------------------------------

# 11. Real-World Mapping

  Requirement                         Constraint
  ----------------------------------- -------------
  StudentID unique                    PRIMARY KEY
  Email unique                        UNIQUE
  Student must belong to Department   FOREIGN KEY
  Name required                       NOT NULL
  Marks 0--100                        CHECK
  Country = India by default          DEFAULT

------------------------------------------------------------------------

# 12. SQL Example

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Email VARCHAR(100) UNIQUE,
    Age INT CHECK (Age BETWEEN 16 AND 60),
    Country VARCHAR(50) DEFAULT 'India',
    DepartmentID INT,
    FOREIGN KEY (DepartmentID)
        REFERENCES Department(DepartmentID)
);
```

This single table demonstrates multiple constraints working together.

------------------------------------------------------------------------

# 13. Common Interview Traps

❌ PRIMARY KEY and UNIQUE are the same.

❌ FOREIGN KEY values must be unique.

❌ DEFAULT prevents NULL.

❌ CHECK replaces FOREIGN KEY.

❌ NOT NULL validates business rules.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  Which constraint prevents duplicates?
2.  Which constraint prevents NULL?
3.  Which constraint creates relationships?

### Intermediate

1.  PRIMARY KEY vs UNIQUE?
2.  CHECK vs DEFAULT?
3.  Entity Integrity vs Referential Integrity?

### Advanced

1.  Design constraints for an online banking system.
2.  Why should business rules be enforced in the database?

------------------------------------------------------------------------

# 15. Practice Scenarios

Choose the best constraint(s):

1.  Employee email must be unique.
2.  Product quantity cannot be negative.
3.  Every order belongs to a customer.
4.  Student name is mandatory.
5.  New orders start as "Pending".

------------------------------------------------------------------------

# Revision Sheet

``` text
PRIMARY KEY
= Identity

FOREIGN KEY
= Relationship

UNIQUE
= No duplicates

NOT NULL
= Mandatory

CHECK
= Valid values

DEFAULT
= Automatic value

Entity Integrity
= PK valid

Referential Integrity
= FK valid

Domain Constraint
= Allowed values

Key Constraint
= Unique identity
```

## Memory Trick

``` text
I R U M V A

Identity
Relationship
Uniqueness
Mandatory
Validation
Automatic
```

## Final Takeaway

Constraints work best as a team rather than in isolation. A
well-designed table commonly combines a **PRIMARY KEY**, **FOREIGN
KEY**, **NOT NULL**, **UNIQUE**, **CHECK**, and **DEFAULT** constraint
to protect data from multiple angles. The goal is not merely to store
information, but to ensure that the information remains correct,
meaningful, and consistent throughout the lifetime of the database.
