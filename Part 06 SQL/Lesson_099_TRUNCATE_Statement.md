# Lesson 099 --- TRUNCATE Statement

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the `TRUNCATE` statement is
-   Why `TRUNCATE` is used
-   How `TRUNCATE` works internally
-   `TRUNCATE` vs `DELETE`
-   `TRUNCATE` vs `DROP`
-   Identity (Auto Increment) behavior
-   Why `TRUNCATE` is faster
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a classroom.

You have three choices:

``` text
DELETE
↓

Remove students

TRUNCATE
↓

Remove all students instantly

DROP
↓

Demolish the classroom
```

`TRUNCATE` empties the table but keeps the classroom (table) itself.

------------------------------------------------------------------------

# 2. What is TRUNCATE?

`TRUNCATE` is a **DDL (Data Definition Language)** command that removes
**all rows** from a table while keeping its structure.

``` text
Table
 │
TRUNCATE
 │
0 Rows
 │
Table Still Exists
```

------------------------------------------------------------------------

# 3. Why Do We Need TRUNCATE?

Sometimes we want to:

-   Empty a table quickly
-   Keep the table structure
-   Reset test data
-   Improve performance over DELETE

Instead of deleting rows one by one, `TRUNCATE` clears the table
efficiently.

------------------------------------------------------------------------

# 4. Syntax

``` sql
TRUNCATE TABLE Student;
```

------------------------------------------------------------------------

# 5. Before and After

Before:

``` text
Student

ID   Name
------------
1    Alice
2    Bob
3    Charlie
```

SQL:

``` sql
TRUNCATE TABLE Student;
```

After:

``` text
Student

(No Rows)

Table Exists
```

------------------------------------------------------------------------

# 6. How TRUNCATE Works Internally

Unlike `DELETE`, which removes rows individually, `TRUNCATE` deallocates
the data pages used by the table.

``` text
DELETE
 │
Row
Row
Row
Row
 │
Done

TRUNCATE
 │
Release Data Pages
 │
Done
```

Because fewer operations are required, `TRUNCATE` is usually much
faster.

------------------------------------------------------------------------

# 7. TRUNCATE vs DELETE

  TRUNCATE                  DELETE
  ------------------------- ------------------------------
  Removes all rows          Removes selected or all rows
  Cannot use WHERE          WHERE supported
  Faster                    Slower for large tables
  DDL                       DML
  Usually minimal logging   Logs row deletions

Example:

``` sql
DELETE FROM Student
WHERE Age > 18;
```

Possible with DELETE.

``` sql
TRUNCATE TABLE Student;
```

Removes every row.

------------------------------------------------------------------------

# 8. TRUNCATE vs DROP

  TRUNCATE              DROP
  --------------------- ----------------------------
  Keeps table           Removes table
  Removes data only     Removes structure and data
  Table can be reused   Table no longer exists
  DDL                   DDL

------------------------------------------------------------------------

# 9. Identity (Auto Increment) Behavior

Many DBMSs reset identity values after a `TRUNCATE`.

Example:

Before:

``` text
ID
1
2
3
```

After `TRUNCATE`:

``` text
Next Insert

ID = 1
```

**Note:** This behavior depends on the DBMS. Some systems require
additional commands to reset identity values.

------------------------------------------------------------------------

# 10. Real-World Example

A company imports sales data every night.

Before importing new data:

``` sql
TRUNCATE TABLE DailySales;
```

Then:

``` sql
INSERT INTO DailySales ...
```

This is much faster than deleting millions of rows individually.

------------------------------------------------------------------------

# 11. Best Practices

-   Use `TRUNCATE` only when every row should be removed.
-   Verify that no important data will be lost.
-   Check for foreign key restrictions.
-   Back up production data before truncating.
-   Use `DELETE` if only specific rows should be removed.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Expecting `WHERE` to work with `TRUNCATE`.

Wrong:

``` sql
TRUNCATE TABLE Student
WHERE Age > 18;
```

✔ Correct:

``` sql
DELETE FROM Student
WHERE Age > 18;
```

------------------------------------------------------------------------

❌ Confusing `TRUNCATE` with `DROP`.

`TRUNCATE` keeps the table.

`DROP` removes the table itself.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is the `TRUNCATE` statement?
2.  Is `TRUNCATE` DDL or DML?
3.  Does `TRUNCATE` remove the table?

### Intermediate

1.  `TRUNCATE` vs `DELETE`?
2.  Why is `TRUNCATE` faster?
3.  Can `TRUNCATE` use a `WHERE` clause?

### Advanced

1.  Explain how `TRUNCATE` works internally.
2.  What happens to identity values after `TRUNCATE`?
3.  Why might `TRUNCATE` be restricted by foreign keys?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Empty the `Employee` table while keeping its structure.
2.  Explain when `DELETE` should be preferred over `TRUNCATE`.
3.  Compare `DROP`, `DELETE`, and `TRUNCATE`.
4.  Predict the next identity value after truncating a table.

------------------------------------------------------------------------

# Revision Notes

``` text
DELETE
 │
Remove Rows

TRUNCATE
 │
Remove All Rows
Keep Table

DROP
 │
Remove Entire Table
```

## Memory Trick

``` text
DELETE

= Selective

TRUNCATE

= Total Cleanup

DROP

= Destroy Structure
```

## Key Points

-   `TRUNCATE` removes every row but preserves the table.
-   It is generally faster than `DELETE`.
-   `TRUNCATE` cannot use a `WHERE` clause.
-   Many DBMSs reset identity values after truncation.
-   `DROP` removes both the structure and the data.

------------------------------------------------------------------------

# Final Takeaway

The `TRUNCATE` statement is the fastest way to empty a table when you no
longer need its current data but still want to keep its structure. It is
commonly used for staging tables, testing environments, and bulk data
reloads. Understanding when to use `DELETE`, `TRUNCATE`, or `DROP` is a
fundamental SQL skill because each command serves a different purpose,
and the database is remarkably literal about carrying out whichever one
you choose.
