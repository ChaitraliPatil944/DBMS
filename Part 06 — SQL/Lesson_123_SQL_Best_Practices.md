# Lesson 123 --- SQL Best Practices

> **Part 06 --- SQL Fundamentals**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   Why SQL best practices matter
-   How to write clean and readable SQL
-   Performance optimization basics
-   Security considerations
-   Common mistakes to avoid
-   Industry standards
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Why Best Practices Matter

A query can be **correct** but still be:

-   Slow
-   Difficult to understand
-   Hard to maintain
-   Unsafe

Good SQL should be:

``` text
Correct
   │
Readable
   │
Efficient
   │
Secure
```

------------------------------------------------------------------------

# 2. Use Meaningful Naming

Prefer descriptive names.

``` sql
-- Good
EmployeeID
DepartmentName
OrderDate

-- Avoid
EID
D1
OD
```

Use consistent naming throughout the database.

------------------------------------------------------------------------

# 3. Format Queries Properly

Poor formatting:

``` sql
SELECT Name,Salary FROM Employee WHERE Department='IT';
```

Better formatting:

``` sql
SELECT Name,
       Salary
FROM Employee
WHERE Department = 'IT';
```

Readable SQL is easier to debug and review.

------------------------------------------------------------------------

# 4. Avoid SELECT \*

Instead of:

``` sql
SELECT *
FROM Employee;
```

Use:

``` sql
SELECT Name,
       Salary
FROM Employee;
```

Benefits:

-   Less data transferred
-   Better performance
-   Clear intent
-   Easier maintenance

------------------------------------------------------------------------

# 5. Filter Early

Use `WHERE` to reduce rows before grouping.

``` sql
SELECT Department,
       COUNT(*)
FROM Employee
WHERE Salary > 50000
GROUP BY Department;
```

Filtering early reduces processing.

------------------------------------------------------------------------

# 6. Use Aliases Wisely

``` sql
SELECT e.Name,
       d.DepartmentName
FROM Employee AS e
JOIN Department AS d
ON e.DepartmentID = d.DepartmentID;
```

Keep aliases short but meaningful.

------------------------------------------------------------------------

# 7. Use Index-Friendly Queries

Prefer:

``` sql
WHERE EmployeeID = 101;
```

Avoid unnecessary operations on indexed columns when possible because
they may prevent efficient index usage.

------------------------------------------------------------------------

# 8. Handle NULL Properly

Wrong:

``` sql
WHERE Email = NULL;
```

Correct:

``` sql
WHERE Email IS NULL;
```

------------------------------------------------------------------------

# 9. Use Transactions

Group related operations.

``` sql
BEGIN;

UPDATE Account
SET Balance = Balance - 1000
WHERE AccountID = 1;

UPDATE Account
SET Balance = Balance + 1000
WHERE AccountID = 2;

COMMIT;
```

------------------------------------------------------------------------

# 10. Prevent SQL Injection

Never concatenate user input into SQL.

Prefer parameterized queries.

``` text
User Input
     │
Parameterized Query
     │
Database
```

------------------------------------------------------------------------

# 11. Optimize Performance

-   Retrieve only required columns.
-   Use indexes appropriately.
-   Avoid unnecessary DISTINCT.
-   Limit returned rows.
-   Review execution plans for slow queries.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Missing WHERE in UPDATE or DELETE.

❌ Using SELECT \* everywhere.

❌ Ignoring indexes.

❌ Poor naming conventions.

❌ Writing unreadable SQL.

------------------------------------------------------------------------

# 13. Industry Checklist

Before deploying a query:

``` text
✓ Readable
✓ Formatted
✓ Uses WHERE correctly
✓ Avoids SELECT *
✓ Uses indexes where appropriate
✓ Handles NULL values
✓ Uses transactions when needed
✓ Tested with sample data
```

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  Why should SELECT \* be avoided?
2.  Why is formatting important?

### Intermediate

1.  Why are indexes important?
2.  How do aliases improve readability?

### Advanced

1.  How do you optimize a slow SQL query?
2.  Explain SQL injection prevention.

------------------------------------------------------------------------

# 15. Practice Problems

1.  Rewrite an unformatted query.
2.  Replace SELECT \* with explicit columns.
3.  Improve a query using aliases.
4.  Identify bad SQL practices in a sample query.

------------------------------------------------------------------------

# Revision Notes

``` text
Readable
   │
Efficient
   │
Secure
   │
Maintainable
```

## Memory Trick

``` text
BEST SQL

B → Be Readable
E → Efficient
S → Secure
T → Test Queries
```

## Key Points

-   Write readable SQL.
-   Retrieve only necessary data.
-   Filter early.
-   Handle NULL correctly.
-   Use transactions for related operations.
-   Prefer parameterized queries for security.
-   Optimize before deploying.

------------------------------------------------------------------------

# Final Takeaway

Writing SQL is only part of becoming a good database developer.
Professional SQL is readable, efficient, secure, and easy to maintain.
Following consistent best practices reduces bugs, improves performance,
and makes collaboration easier. Future you, or the next developer
reading your query at 2 a.m., will be grateful that you chose clarity
over cleverness.
