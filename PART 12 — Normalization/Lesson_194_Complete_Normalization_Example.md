# Lesson 194 --- Complete Normalization Example

> **Part 12 --- Normalization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will be able to:

-   Apply normalization from UNF to 5NF
-   Identify redundancy and anomalies
-   Detect functional, multivalued and join dependencies
-   Perform step-by-step decomposition
-   Design a normalized database
-   Answer interview questions based on complete normalization

------------------------------------------------------------------------

# 1. Problem Statement

A university stores student enrollments in one table.

  -------------------------------------------------------------------------------
  StudentID   StudentName   Department   Course   Instructor   Hobby   Language
  ----------- ------------- ------------ -------- ------------ ------- ----------
  101         Asha          CSE          DBMS     Ravi         Chess   English

  101         Asha          CSE          DBMS     Ravi         Chess   Hindi

  101         Asha          CSE          AI       Kiran        Music   English

  101         Asha          CSE          AI       Kiran        Music   Hindi
  -------------------------------------------------------------------------------

Problems:

-   Duplicate student information
-   Duplicate department information
-   Duplicate instructor information
-   Repeated hobby-language combinations
-   Difficult updates

------------------------------------------------------------------------

# 2. Step 1 --- UNF (Unnormalized Form)

Suppose hobbies and languages are stored as comma-separated values.

  StudentID   Hobbies       Languages
  ----------- ------------- ---------------
  101         Chess,Music   English,Hindi

Problems:

-   Multiple values per cell
-   Difficult searching
-   Difficult updates

------------------------------------------------------------------------

# 3. Step 2 --- First Normal Form (1NF)

Convert every cell into atomic values.

  StudentID   Hobby   Language
  ----------- ------- ----------
  101         Chess   English
  101         Chess   Hindi
  101         Music   English
  101         Music   Hindi

✔ Atomic values achieved

Still contains redundancy.

------------------------------------------------------------------------

# 4. Step 3 --- Second Normal Form (2NF)

Composite key:

``` text
(StudentID, Course)
```

Partial dependencies:

``` text
StudentID → StudentName
StudentID → Department
Course → Instructor
```

Create separate tables.

### Student

| StudentID \| StudentName \| Department \|

### Course

| Course \| Instructor \|

### Enrollment

| StudentID \| Course \|

Partial dependencies removed.

------------------------------------------------------------------------

# 5. Step 4 --- Third Normal Form (3NF)

Transitive dependency:

``` text
DepartmentID → DepartmentName
```

Split department information.

### Student

| StudentID \| StudentName \| DepartmentID \|

### Department

| DepartmentID \| DepartmentName \|

Transitive dependency removed.

------------------------------------------------------------------------

# 6. Step 5 --- BCNF

Check determinants.

If every determinant is a Super Key:

``` text
✓ BCNF satisfied
```

Otherwise, decompose further.

------------------------------------------------------------------------

# 7. Step 6 --- Fourth Normal Form (4NF)

Independent facts:

``` text
Student ↠ Hobby

Student ↠ Language
```

Split into:

### StudentHobby

| StudentID \| Hobby \|

### StudentLanguage

| StudentID \| Language \|

Redundant combinations removed.

------------------------------------------------------------------------

# 8. Step 7 --- Fifth Normal Form (5NF)

If complex join dependencies exist, decompose further.

Example:

``` text
Supplier
Product
Project
```

↓

``` text
SupplierProduct

SupplierProject

ProductProject
```

Ensure the original relation can be reconstructed through lossless
joins.

------------------------------------------------------------------------

# 9. Complete Evolution

``` text
UNF
 │
1NF
 │
2NF
 │
3NF
 │
BCNF
 │
4NF
 │
5NF
```

------------------------------------------------------------------------

# 10. Final Database Design

``` text
Student
---------
StudentID
StudentName
DepartmentID

Department
----------
DepartmentID
DepartmentName

Course
------
CourseID
CourseName
Instructor

Enrollment
----------
StudentID
CourseID

StudentHobby
------------
StudentID
Hobby

StudentLanguage
---------------
StudentID
Language
```

------------------------------------------------------------------------

# 11. Benefits

-   No redundant data
-   Easier updates
-   Better integrity
-   Reduced anomalies
-   Efficient maintenance

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Skipping normal forms.

❌ Decomposing without checking lossless joins.

❌ Ignoring functional dependencies.

❌ Over-normalizing simple databases.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  Explain normalization using one example.
2.  Why do we normalize databases?

### Intermediate

1.  Walk through 1NF to 3NF.
2.  Explain BCNF using an example.

### Advanced

1.  Difference between BCNF, 4NF and 5NF.
2.  Explain lossless decomposition and dependency preservation.

------------------------------------------------------------------------

# 14. Practice Problems

1.  Normalize a student database to 3NF.
2.  Identify partial and transitive dependencies.
3.  Detect multivalued dependencies.
4.  Design a normalized university database.

------------------------------------------------------------------------

# Revision Notes

``` text
UNF
 ↓
1NF → Atomic Values

2NF → Remove Partial Dependency

3NF → Remove Transitive Dependency

BCNF → Every Determinant is a Super Key

4NF → Remove MVD

5NF → Remove Join Dependency
```

## Memory Trick

``` text
Normalize

Atomic

Partial

Transitive

Determinant

Multivalued

Join
```

------------------------------------------------------------------------

# Final Takeaway

Normalization is a progressive process rather than a single rule. Each
normal form removes a different type of redundancy and improves database
quality. In practice, most production databases are normalized to **3NF
or BCNF**, while **4NF** and **5NF** are applied only when complex
multivalued or join dependencies exist. Understanding the complete
journey from **UNF to 5NF** gives you a strong foundation for database
design and technical interviews.
