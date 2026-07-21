# Lesson 240 - Simple Views

**Part:** Part 10 - Views

**Difficulty:** Beginner → Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 45–60 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand what a View is.
- Create, modify, and delete simple views.
- Explain how a DBMS executes views internally.
- Identify the advantages and limitations of views.
- Solve interview-oriented SQL questions involving views.

---

# 1. Introduction

A **View** is a **virtual table** created from the result of a SQL query.

Unlike a normal table, a view generally **does not store data**. It stores only the SQL query definition.

Whenever the view is queried, the DBMS executes the underlying query and returns the latest data.

---

# 2. Why Use Views?

Views provide:

- Data abstraction
- Security
- Query simplification
- Reusable SQL logic
- Controlled access to sensitive data

Instead of exposing an entire table, a view can expose only selected columns or rows.

---

# 3. Real-World Analogy

Imagine a bank database.

The Employee table contains:

- Employee ID
- Name
- Salary
- PAN Number
- Bank Account

HR managers need every column.

Department managers only need employee names and departments.

Instead of giving managers access to the entire table, create a view that exposes only the required information.

---

# 4. Syntax

### Create View

```sql
CREATE VIEW EmployeeView AS
SELECT EmployeeID,
       Name,
       DepartmentID
FROM Employee;
```

### Query View

```sql
SELECT *
FROM EmployeeView;
```

### Delete View

```sql
DROP VIEW EmployeeView;
```

---

# 5. Sample Table

```text
Employee
+----+-------+--------------+--------+
|ID  |Name   |DepartmentID  |Salary  |
+----+-------+--------------+--------+
|1   |Alice  |10            |50000   |
|2   |Bob    |20            |65000   |
|3   |Carol  |10            |55000   |
+----+-------+--------------+--------+
```

View Definition

```sql
CREATE VIEW EmployeeView AS
SELECT Name,
       DepartmentID
FROM Employee;
```

Result

```text
+-------+--------------+
|Name   |DepartmentID  |
+-------+--------------+
|Alice  |10            |
|Bob    |20            |
|Carol  |10            |
+-------+--------------+
```

---

# 6. Internal Working

```text
User Query
     │
     ▼
View Definition
     │
     ▼
Underlying SQL Query
     │
     ▼
Base Table
     │
     ▼
Return Result
```

The DBMS expands the view definition into the original SQL query before optimization and execution.

---

# 7. Updatable Views

A simple view is often **updatable** when it:

- References one table
- Does not use GROUP BY
- Does not use DISTINCT
- Does not use aggregate functions
- Does not use UNION

Example

```sql
UPDATE EmployeeView
SET DepartmentID = 30
WHERE Name = 'Alice';
```

Whether updates are allowed depends on the DBMS and the view definition.

---

# 8. Advantages

- Hides sensitive data.
- Simplifies complex queries.
- Promotes code reuse.
- Provides logical data independence.
- Improves application maintainability.

---

# 9. Limitations

- Usually does not improve performance.
- Complex views may not be updatable.
- Depends on underlying tables.
- Dropping referenced columns can invalidate a view.

---

# 10. Real Project Examples

## Banking

Customer view without confidential account details.

## Telecom

Subscriber summary view for customer support.

## E-Commerce

Product catalog view excluding supplier costs.

## Hospital

Patient view hiding confidential medical information.

---

# 11. Performance Notes

- Simple views are expanded during query optimization.
- Indexes on underlying tables are still used.
- Views themselves generally do not store data.
- Complex nested views can increase query complexity.

---

# 12. Common Mistakes

- Assuming views store data.
- Using views as a replacement for indexes.
- Creating deeply nested views.
- Expecting every view to be updatable.

---

# 13. Interview Questions

## Beginner

1. What is a view?
2. Does a view store data?
3. Why are views used?

## Intermediate

1. What makes a view updatable?
2. View vs Table?
3. Can indexes on base tables help view performance?

## Advanced

1. How does the optimizer execute a view?
2. Why don't simple views usually improve performance?
3. What happens if the underlying table changes?

---

# 14. Practice

```sql
CREATE VIEW CustomerView AS
SELECT CustomerID,
       Name,
       City
FROM Customer;

SELECT *
FROM CustomerView;

DROP VIEW CustomerView;
```

---

# Revision Notes

- A view is a virtual table.
- Stores a query, not the data.
- Executes against base tables.
- Used for abstraction, security, and simplicity.
- Simple views are often updatable.

---

# Memory Trick

**VIEW = Virtual Window**

You see the data through a window, but the data remains in the original table.

---

# Final Takeaway

Simple views provide a clean and secure way to present data without duplicating it. They simplify application development, hide unnecessary details, and enforce controlled access to underlying tables. In interviews, remember that a view is a stored query rather than stored data, and that its performance depends largely on the execution plan of the underlying SQL and the indexes on the base tables.
