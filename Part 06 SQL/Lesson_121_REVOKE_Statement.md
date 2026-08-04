# Lesson 121 --- REVOKE Statement

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the `REVOKE` statement is
-   Why `REVOKE` is needed
-   Revoking privileges from users and roles
-   Cascading revoke concepts
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Giving access is only half of database security.

Employees resign. Projects end. Contractors leave.

Their permissions should also be removed.

That is the job of **REVOKE**.

------------------------------------------------------------------------

# 2. What is REVOKE?

`REVOKE` is a **DCL (Data Control Language)** command used to remove
previously granted privileges from users or roles.

``` text
Administrator
      │
    REVOKE
      │
User / Role
      │
Permission Removed
```

------------------------------------------------------------------------

# 3. Why Do We Need REVOKE?

Without REVOKE:

-   Former employees may retain access.
-   Sensitive information remains exposed.
-   Security policies become ineffective.

Removing unnecessary permissions is just as important as granting them.

------------------------------------------------------------------------

# 4. Basic Syntax

``` sql
REVOKE privilege
ON table_name
FROM user_name;
```

Example:

``` sql
REVOKE SELECT
ON Employee
FROM Rahul;
```

Rahul can no longer read the `Employee` table.

------------------------------------------------------------------------

# 5. Revoking Multiple Privileges

``` sql
REVOKE SELECT,
       INSERT,
       UPDATE
ON Employee
FROM Rahul;
```

------------------------------------------------------------------------

# 6. Revoking from Roles

``` sql
REVOKE UPDATE
ON Employee
FROM HR_Manager;
```

Users who receive permissions only through that role lose the revoked
privilege.

------------------------------------------------------------------------

# 7. Cascading Revokes

Suppose:

``` text
Admin
 │
GRANT SELECT WITH GRANT OPTION
 │
Rahul
 │
GRANT SELECT
 │
Priya
```

If Rahul's grant is revoked with cascading behavior (DBMS dependent):

``` text
Admin
 │
REVOKE
 │
Rahul ❌
 │
Priya ❌
```

Some DBMSs support `CASCADE`; others handle dependency differently.

------------------------------------------------------------------------

# 8. Internal Working

``` text
User Requests Access
        │
Permission Exists?
   │           │
  Yes         No
   │           │
 REVOKE     Already Denied
   │
Permission Removed
```

------------------------------------------------------------------------

# 9. Real-World Example

A contractor completes a project.

``` sql
REVOKE INSERT,
       UPDATE
ON Project
FROM Contractor01;
```

The contractor can no longer modify project data.

------------------------------------------------------------------------

# 10. GRANT vs REVOKE

  GRANT               REVOKE
  ------------------- ---------------------
  Gives permissions   Removes permissions
  Expands access      Restricts access
  DCL                 DCL

------------------------------------------------------------------------

# 11. Best Practices

-   Remove unused permissions promptly.
-   Audit privileges regularly.
-   Use roles for easier management.
-   Apply the Principle of Least Privilege.
-   Document permission changes.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Forgetting to revoke contractor access.

❌ Revoking from the wrong user.

❌ Ignoring inherited role permissions.

❌ Assuming all DBMSs implement cascading revokes identically.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is the `REVOKE` statement?
2.  Is `REVOKE` a DCL command?
3.  Why is `REVOKE` important?

### Intermediate

1.  `GRANT` vs `REVOKE`?
2.  Can privileges be revoked from roles?

### Advanced

1.  What is a cascading revoke?
2.  Why should permissions be reviewed regularly?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Revoke `SELECT` from a user.
2.  Revoke multiple privileges.
3.  Remove permissions from a role.
4.  Explain a cascading revoke scenario.

------------------------------------------------------------------------

# Revision Notes

``` text
GRANT
 │
Give Access

REVOKE
 │
Remove Access
```

## Memory Trick

``` text
REVOKE

=

Remove

Existing

Verified

Operations

Keeping

Environment Secure
```

## Key Points

-   `REVOKE` removes previously granted privileges.
-   It is a DCL command.
-   Permissions can be removed from users and roles.
-   Review access regularly.
-   Least privilege improves database security.

------------------------------------------------------------------------

# Final Takeaway

`REVOKE` is the counterpart to `GRANT` and is essential for maintaining
database security over time. Access requirements change as people change
roles, projects finish, and organizations evolve. Regularly removing
unnecessary permissions reduces security risks and helps ensure that
every user has exactly the access they need, and nothing more.
