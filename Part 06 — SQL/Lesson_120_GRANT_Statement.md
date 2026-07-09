# Lesson 120 --- GRANT Statement

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the `GRANT` statement is
-   Why `GRANT` is used
-   Granting privileges to users
-   Granting privileges to roles
-   Common database privileges
-   `WITH GRANT OPTION`
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a company database.

Should every employee be allowed to:

-   Read payroll? ❌
-   Delete customer records? ❌
-   View their own department data? ✅

Permissions must be assigned carefully.

The **GRANT** statement is used for this purpose.

------------------------------------------------------------------------

# 2. What is GRANT?

`GRANT` is a **DCL (Data Control Language)** command used to give
privileges to users or roles.

``` text
Administrator
      │
    GRANT
      │
User / Role
      │
Permissions
```

------------------------------------------------------------------------

# 3. Why Do We Need GRANT?

Without `GRANT`:

-   Users cannot access required resources.
-   Teams cannot perform their jobs.
-   Security becomes difficult to manage.

With `GRANT`, each user receives only the permissions they need.

------------------------------------------------------------------------

# 4. Basic Syntax

Grant a privilege:

``` sql
GRANT privilege
ON table_name
TO user_name;
```

Example:

``` sql
GRANT SELECT
ON Employee
TO Rahul;
```

Rahul can now read data from the `Employee` table.

------------------------------------------------------------------------

# 5. Grant Multiple Privileges

``` sql
GRANT SELECT,
      INSERT,
      UPDATE
ON Employee
TO Rahul;
```

------------------------------------------------------------------------

# 6. Common Privileges

``` text
SELECT   → Read data

INSERT   → Add rows

UPDATE   → Modify rows

DELETE   → Remove rows

CREATE   → Create objects

ALTER    → Modify objects

DROP     → Delete objects
```

------------------------------------------------------------------------

# 7. Granting to Roles

Instead of granting permissions individually:

``` sql
GRANT SELECT
ON Employee
TO HR_Manager;
```

Every user assigned the `HR_Manager` role inherits the privilege.

------------------------------------------------------------------------

# 8. WITH GRANT OPTION

Allows a user to pass granted privileges to others.

``` sql
GRANT SELECT
ON Employee
TO Rahul
WITH GRANT OPTION;
```

``` text
Admin
 │
Rahul
 │
Can Grant
 │
Other Users
```

Use this option carefully.

------------------------------------------------------------------------

# 9. Internal Working

``` text
User Requests Access
        │
Permission Lookup
        │
GRANT Exists?
   │          │
 Yes         No
 │            │
Allow      Access Denied
```

------------------------------------------------------------------------

# 10. Real-World Example

University database:

``` text
Professor
 │
Read Student Records

Registrar
 │
Read + Update Student Records

Student
 │
Read Own Results
```

Different users receive different privileges.

------------------------------------------------------------------------

# 11. Best Practices

-   Follow the Principle of Least Privilege.
-   Grant only required permissions.
-   Prefer roles over individual users.
-   Review permissions regularly.
-   Limit the use of `WITH GRANT OPTION`.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Granting administrator privileges unnecessarily.

❌ Using `WITH GRANT OPTION` without careful planning.

❌ Forgetting to audit user permissions.

❌ Assigning privileges directly to many users instead of roles.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is the `GRANT` statement?
2.  Is `GRANT` a DCL command?
3.  What are privileges?

### Intermediate

1.  Why are roles better than individual grants?
2.  What does `WITH GRANT OPTION` do?

### Advanced

1.  Explain the Principle of Least Privilege.
2.  Why should `WITH GRANT OPTION` be used cautiously?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Grant `SELECT` permission on the `Student` table.
2.  Grant `INSERT` and `UPDATE` to a user.
3.  Grant privileges to a role.
4.  Explain when `WITH GRANT OPTION` is appropriate.

------------------------------------------------------------------------

# Revision Notes

``` text
Administrator
      │
    GRANT
      │
User / Role
      │
Permissions
```

## Memory Trick

``` text
GRANT

=

Give

Rights

And

New

Trust
```

## Key Points

-   `GRANT` provides database privileges.
-   It is a DCL command.
-   Permissions can be assigned to users or roles.
-   Roles simplify security management.
-   Use `WITH GRANT OPTION` only when delegation is required.

------------------------------------------------------------------------

# Final Takeaway

The `GRANT` statement is the foundation of database authorization. It
ensures that users have the permissions they need while preventing
unauthorized actions. A well-designed permission model improves
security, simplifies administration, and reduces the risk of accidental
or malicious changes. In database security, giving someone exactly the
access they need is far more effective than giving them everything and
hoping for impeccable judgment.
