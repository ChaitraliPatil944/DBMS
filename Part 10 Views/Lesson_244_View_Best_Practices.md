# Lesson 244 - View Best Practices

**Part:** Part 10 - Views

**Difficulty:** Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 40–55 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Design efficient and maintainable views.
- Follow industry best practices for creating views.
- Avoid common performance and security pitfalls.
- Understand when to use and when to avoid views.
- Answer interview questions related to view design.

---

# 1. Introduction

Views simplify SQL queries and improve security, but poor view design can lead to slow queries, maintenance issues, and confusing database structures.

Following best practices helps keep applications scalable, readable, and efficient.

---

# 2. Use Views for the Right Purpose

Views are ideal for:

- Hiding sensitive columns.
- Simplifying complex joins.
- Providing a consistent interface to applications.
- Reporting and analytics.

Avoid creating views simply to rename tables or duplicate existing queries without a clear purpose.

---

# 3. Select Only Required Columns

❌ Avoid

```sql
CREATE VIEW EmployeeView AS
SELECT *
FROM Employee;
```

✅ Prefer

```sql
CREATE VIEW EmployeeView AS
SELECT EmployeeID,
       Name,
       DepartmentID
FROM Employee;
```

Selecting only necessary columns improves readability, security, and can reduce data transfer.

---

# 4. Avoid Deeply Nested Views

Poor Design

```text
View A
   │
View B
   │
View C
   │
View D
```

Every additional layer increases complexity for both developers and the query optimizer.

Prefer flatter view hierarchies whenever possible.

---

# 5. Keep Views Focused

A good view should have a single responsibility.

Examples:

- Customer summary
- Product catalog
- Active subscriptions
- Monthly sales report

Avoid creating one view that tries to solve unrelated business problems.

---

# 6. Be Careful with Complex Logic

Views containing many joins, aggregations, and subqueries can become expensive.

If the same heavy query is executed repeatedly, consider:

- Materialized Views (where supported)
- Indexed Views (where supported)
- Summary tables
- Caching strategies

---

# 7. Secure Sensitive Data

Views are commonly used to hide:

- Salaries
- Credit card details
- PAN numbers
- Medical records
- Personal identifiers

Grant users access to the view instead of the base table whenever appropriate.

---

# 8. Index the Base Tables

Normal views do not store data.

Performance depends on:

- Base table indexes
- Query optimizer
- Execution plan

Creating a view alone does not make queries faster.

---

# 9. Document View Purpose

Use meaningful names.

Good examples:

```text
CustomerSummary
MonthlySales
ActiveEmployees
DepartmentStatistics
```

Avoid generic names like:

```text
View1
TempView
DataView
```

---

# 10. Internal Execution Flow

```text
Application
      │
      ▼
View
      │
Expand SQL
      │
Optimizer
      │
Indexes
      │
Base Tables
      │
Return Result
```

The optimizer evaluates the expanded SQL, not the view as a separate physical object (except for materialized/indexed views).

---

# 11. Common Mistakes

- Using SELECT * inside views.
- Creating unnecessary nested views.
- Assuming views improve performance automatically.
- Forgetting permissions on base tables.
- Ignoring changes to underlying schemas.

---

# 12. Real Project Examples

## Banking

Expose customer details without account balances.

## Telecom

Provide customer support with subscriber information while hiding billing data.

## E-Commerce

Display product information without supplier costs.

## Hospital

Allow reception staff to view patient appointments without exposing medical history.

---

# 13. Interview Questions

## Beginner

1. Why are views used?
2. Do views improve performance?
3. Why avoid `SELECT *` in a view?

## Intermediate

1. What are best practices for designing views?
2. Why avoid nested views?
3. How do views improve security?

## Advanced

1. How does the optimizer execute a view?
2. When should a materialized or indexed view be preferred?
3. How do base table indexes affect view performance?

---

# 14. Best Practices Checklist

- ✔ Use meaningful names.
- ✔ Select only required columns.
- ✔ Keep views focused.
- ✔ Avoid unnecessary nesting.
- ✔ Protect sensitive data.
- ✔ Index base tables.
- ✔ Review execution plans.
- ✔ Document business purpose.
- ✔ Prefer materialized or indexed views for heavy reporting where appropriate.

---

# Revision Notes

- Views improve abstraction, not necessarily speed.
- Simple views are often updatable.
- Complex views are usually read-only.
- Performance depends on base tables and indexes.
- Good design improves maintainability and security.

---

# Memory Trick

**VIEW**

- **V**irtual table
- **I**solate sensitive data
- **E**asier queries
- **W**ell-designed for reuse

---

# Final Takeaway

Views are a powerful abstraction mechanism that simplify SQL, improve security, and promote code reuse when designed thoughtfully. The best-performing systems use views with clear business purposes, minimal complexity, and strong indexing on the underlying tables. In interviews, emphasize that views are primarily a logical design tool, while performance gains come from good indexing, optimized queries, or specialized technologies such as materialized and indexed views.
