# Lesson 124 --- SQL Interview Questions

> **Part 06 --- SQL Fundamentals**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will be able to:

-   Revise all SQL concepts learned so far
-   Answer common SQL interview questions
-   Explain concepts with confidence
-   Solve scenario-based interview problems
-   Prepare for technical screening rounds

------------------------------------------------------------------------

# 1. Beginner Level Questions

## Q1. What is SQL?

**Answer:** SQL (Structured Query Language) is the standard language
used to create, retrieve, update, delete, and manage data stored in
relational databases.

------------------------------------------------------------------------

## Q2. What are the categories of SQL commands?

-   DDL (CREATE, ALTER, DROP, TRUNCATE, RENAME)
-   DML (INSERT, UPDATE, DELETE, MERGE)
-   DQL (SELECT)
-   TCL (COMMIT, ROLLBACK, SAVEPOINT)
-   DCL (GRANT, REVOKE)

------------------------------------------------------------------------

## Q3. Difference between DELETE, TRUNCATE and DROP?

  ------------------------------------------------------------------------
  DELETE                    TRUNCATE                     DROP
  ------------------------- ---------------------------- -----------------
  Removes selected/all rows Removes all rows             Removes the
                                                         entire table

  Can use WHERE             No WHERE                     Deletes structure
                                                         and data

  Can usually be rolled     DBMS dependent               Removes object
  back before commit                                     
  ------------------------------------------------------------------------

------------------------------------------------------------------------

## Q4. What is a PRIMARY KEY?

A PRIMARY KEY uniquely identifies every row in a table. It cannot
contain NULL values or duplicates.

------------------------------------------------------------------------

## Q5. What is a FOREIGN KEY?

A FOREIGN KEY creates a relationship between two tables and enforces
referential integrity.

------------------------------------------------------------------------

# 2. Intermediate Level Questions

## Q6. WHERE vs HAVING

  WHERE                       HAVING
  --------------------------- ----------------------
  Filters rows                Filters groups
  Before GROUP BY             After GROUP BY
  No aggregates (generally)   Used with aggregates

------------------------------------------------------------------------

## Q7. GROUP BY vs DISTINCT

  GROUP BY               DISTINCT
  ---------------------- ---------------------------------
  Creates groups         Removes duplicates
  Used with aggregates   Usually used without aggregates

------------------------------------------------------------------------

## Q8. ORDER BY vs GROUP BY

-   ORDER BY sorts rows.
-   GROUP BY groups rows.

------------------------------------------------------------------------

## Q9. Why should SELECT \* be avoided?

-   Reads unnecessary columns
-   Reduces performance
-   Increases network traffic
-   Makes maintenance harder

------------------------------------------------------------------------

## Q10. What is a transaction?

A transaction is a logical unit of work that follows the all-or-nothing
principle.

------------------------------------------------------------------------

# 3. Advanced Questions

## Q11. Explain SQL Execution Order.

``` text
FROM
 ↓
JOIN
 ↓
WHERE
 ↓
GROUP BY
 ↓
HAVING
 ↓
SELECT
 ↓
DISTINCT
 ↓
ORDER BY
 ↓
LIMIT / OFFSET
```

------------------------------------------------------------------------

## Q12. Explain COMMIT and ROLLBACK.

-   COMMIT permanently saves changes.
-   ROLLBACK undoes uncommitted changes.

------------------------------------------------------------------------

## Q13. What is SAVEPOINT?

SAVEPOINT creates a checkpoint inside a transaction, allowing partial
rollback.

------------------------------------------------------------------------

## Q14. Difference between PRIMARY KEY and UNIQUE?

  PRIMARY KEY       UNIQUE
  ----------------- -------------------------------
  One per table     Multiple allowed
  No NULL           NULL handling depends on DBMS
  Identifies rows   Ensures uniqueness

------------------------------------------------------------------------

## Q15. Explain SQL Injection.

SQL Injection is an attack where malicious input changes the intended
SQL query. Prevent it by using parameterized queries and validating
input.

------------------------------------------------------------------------

# 4. Scenario-Based Questions

### Scenario 1

Find the top 5 highest-paid employees.

Expected concepts:

-   ORDER BY
-   DESC
-   LIMIT / TOP

------------------------------------------------------------------------

### Scenario 2

Find departments having more than 10 employees.

Expected concepts:

-   GROUP BY
-   COUNT()
-   HAVING

------------------------------------------------------------------------

### Scenario 3

Transfer money between two accounts safely.

Expected concepts:

-   UPDATE
-   COMMIT
-   ROLLBACK

------------------------------------------------------------------------

### Scenario 4

Allow HR to view employee data but not delete it.

Expected concepts:

-   GRANT
-   SELECT privilege

------------------------------------------------------------------------

# 5. Rapid Fire Questions

1.  What does SQL stand for?
2.  Which clause filters rows?
3.  Which clause filters groups?
4.  Can a PRIMARY KEY contain NULL?
5.  What is DDL?
6.  What is DML?
7.  What is DQL?
8.  What is TCL?
9.  What is DCL?
10. Which command permanently saves a transaction?
11. Which command undoes a transaction?
12. What is a foreign key?
13. What is DISTINCT?
14. Why use aliases?
15. Why use LIMIT?

------------------------------------------------------------------------

# 6. Tips for SQL Interviews

-   Explain your thought process.
-   Write clean and formatted SQL.
-   Clarify assumptions.
-   Optimize after getting a correct solution.
-   Discuss edge cases if time permits.

------------------------------------------------------------------------

# Practice Activity

Answer these without notes:

1.  Explain SQL execution order.
2.  Compare WHERE and HAVING.
3.  Compare DELETE, TRUNCATE, and DROP.
4.  Explain COMMIT vs ROLLBACK.
5.  Write a query using GROUP BY and HAVING.

------------------------------------------------------------------------

# Revision Notes

``` text
DDL → Structure
DML → Data
DQL → Query
TCL → Transactions
DCL → Permissions

WHERE → Rows
HAVING → Groups

PRIMARY KEY → Identity
FOREIGN KEY → Relationship
```

## Memory Trick

``` text
Interview Formula

Understand
↓

Explain
↓

Example
↓

SQL Query
↓

Optimization
```

------------------------------------------------------------------------

# Final Takeaway

SQL interviews assess more than syntax. Interviewers look for
understanding of database concepts, query logic, performance awareness,
and the ability to explain your reasoning clearly. Mastering the
fundamentals and practicing real scenarios will prepare you for both
coding rounds and technical discussions.
