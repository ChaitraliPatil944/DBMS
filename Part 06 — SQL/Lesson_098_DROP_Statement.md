# Lesson 098 --- DROP Statement

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the `DROP` statement is
-   Why `DROP` is used
-   Dropping databases, tables, views, and indexes
-   `DROP` vs `TRUNCATE`
-   `DROP` vs `DELETE`
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a classroom that is no longer needed.

You could:

-   Remove only the desks.
-   Remove all students.
-   Demolish the entire classroom.

`DROP` performs the third action.

It removes the entire database object.

------------------------------------------------------------------------

# 2. What is the DROP Statement?

`DROP` is a **DDL (Data Definition Language)** command used to
permanently remove database objects.

It can remove:

-   Databases
-   Tables
-   Views
-   Indexes
-   Schemas

``` text
Database Object
       │
      DROP
       │
Object Removed
```

------------------------------------------------------------------------

# 3. Why Do We Need DROP?

Sometimes objects become:

-   Obsolete
-   Duplicated
-   Incorrectly designed
-   Temporary

Instead of keeping unused objects, we remove them.

------------------------------------------------------------------------

# 4. DROP DATABASE

``` sql
DROP DATABASE CollegeDB;
```

Result:

``` text
CollegeDB

❌ Removed completely
```

Everything inside the database is deleted.

------------------------------------------------------------------------

# 5. DROP TABLE

``` sql
DROP TABLE Student;
```

Before:

``` text
Student
│
├── Columns
├── Constraints
└── Rows
```

After:

``` text
Student

❌ Does not exist
```

The structure and data are both removed.

------------------------------------------------------------------------

# 6. DROP VIEW

``` sql
DROP VIEW StudentView;
```

Only the view is deleted.

The underlying tables remain unchanged.

------------------------------------------------------------------------

# 7. DROP INDEX

``` sql
DROP INDEX idx_email;
```

Only the index is removed.

The table and its data remain.

(DBMS syntax may vary.)

------------------------------------------------------------------------

# 8. DROP vs TRUNCATE

  DROP                         TRUNCATE
  ---------------------------- --------------------
  Removes the table            Removes all rows
  Deletes structure and data   Keeps structure
  Table no longer exists       Table still exists
  DDL                          DDL

Example:

``` text
DROP TABLE Student;

↓

Student table removed

TRUNCATE TABLE Student;

↓

Student table exists

0 rows
```

------------------------------------------------------------------------

# 9. DROP vs DELETE

  DROP                      DELETE
  ------------------------- ----------------------------
  Removes object            Removes rows
  Structure removed         Structure retained
  DDL                       DML
  Cannot query afterwards   Table can still be queried

------------------------------------------------------------------------

# 10. Real-World Example

A company created a temporary table.

After the migration:

``` sql
DROP TABLE TempEmployee;
```

The temporary table is permanently removed.

------------------------------------------------------------------------

# 11. Best Practices

-   Back up important databases.
-   Verify the object name.
-   Check dependencies before dropping.
-   Avoid running `DROP` directly in production without review.
-   Use transactions where supported for related operations.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Using `DROP` when only the data should be removed.

❌ Dropping the wrong table.

❌ Ignoring foreign key dependencies.

❌ Assuming dropped objects can always be recovered.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is the `DROP` statement?
2.  Is `DROP` a DDL or DML command?
3.  What objects can `DROP` remove?

### Intermediate

1.  `DROP` vs `TRUNCATE`?
2.  `DROP` vs `DELETE`?

### Advanced

1.  Why is `DROP` considered irreversible in most cases?
2.  What precautions should be taken before using `DROP` in production?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Drop a database named `LibraryDB`.
2.  Drop the `Employee` table.
3.  Drop a view named `SalesView`.
4.  Explain the difference between dropping a table and truncating it.
5.  Identify when `DELETE` is a better choice than `DROP`.

------------------------------------------------------------------------

# Revision Notes

``` text
DROP
│
├── DATABASE
├── TABLE
├── VIEW
├── INDEX
└── SCHEMA
```

## Memory Trick

``` text
DROP

=

Destroy Object Permanently
```

## Key Points

-   `DROP` permanently removes database objects.
-   Both structure and data are deleted.
-   `DROP` is a DDL command.
-   `TRUNCATE` removes rows but keeps the table.
-   `DELETE` removes rows while preserving the table structure.

------------------------------------------------------------------------

# Final Takeaway

The `DROP` statement is one of the most powerful commands in SQL because
it removes entire database objects rather than just their contents. It
should be used only when you are certain an object is no longer
required. Experienced database professionals treat `DROP` with respect,
because a few carefully typed characters can erase months of work far
faster than they can be recreated.
