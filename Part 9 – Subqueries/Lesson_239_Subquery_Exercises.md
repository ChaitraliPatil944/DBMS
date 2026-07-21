# Lesson 239 - Subquery Exercises

**Part:** Part 9 - Subqueries

**Difficulty:** Beginner → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 60–90 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Apply scalar, correlated, and multi-row subqueries.
- Use EXISTS, ANY, ALL, IN, and NOT IN effectively.
- Solve interview-level SQL problems.
- Choose between subqueries, joins, and window functions.

---

# Database Schema

Assume the following tables:

```text
Customer(CustomerID, Name, City)

Orders(OrderID, CustomerID, ProductID, Amount, OrderDate)

Product(ProductID, ProductName, CategoryID, Price)

Employee(EmployeeID, Name, DepartmentID, Salary)

Department(DepartmentID, DepartmentName)
```

---

# Beginner Exercises

## 1. Employees earning above average salary

```sql
SELECT Name, Salary
FROM Employee
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employee
);
```

---

## 2. Products priced above average

```sql
SELECT ProductName, Price
FROM Product
WHERE Price >
(
    SELECT AVG(Price)
    FROM Product
);
```

---

## 3. Customers who placed orders

```sql
SELECT Name
FROM Customer
WHERE CustomerID IN
(
    SELECT CustomerID
    FROM Orders
);
```

---

## 4. Customers who never placed orders

```sql
SELECT Name
FROM Customer
WHERE CustomerID NOT IN
(
    SELECT CustomerID
    FROM Orders
);
```

---

## 5. Customers using EXISTS

```sql
SELECT Name
FROM Customer c
WHERE EXISTS
(
    SELECT 1
    FROM Orders o
    WHERE o.CustomerID = c.CustomerID
);
```

---

# Intermediate Exercises

## 6. Employees earning above their department average

```sql
SELECT e1.Name,
       e1.Salary
FROM Employee e1
WHERE e1.Salary >
(
    SELECT AVG(e2.Salary)
    FROM Employee e2
    WHERE e2.DepartmentID = e1.DepartmentID
);
```

---

## 7. Products priced above all products in Category 1

```sql
SELECT ProductName
FROM Product
WHERE Price > ALL
(
    SELECT Price
    FROM Product
    WHERE CategoryID = 1
);
```

---

## 8. Products priced above any product in Category 2

```sql
SELECT ProductName
FROM Product
WHERE Price > ANY
(
    SELECT Price
    FROM Product
    WHERE CategoryID = 2
);
```

---

## 9. Departments having employees

```sql
SELECT DepartmentName
FROM Department d
WHERE EXISTS
(
    SELECT 1
    FROM Employee e
    WHERE e.DepartmentID = d.DepartmentID
);
```

---

## 10. Departments without employees

```sql
SELECT DepartmentName
FROM Department d
WHERE NOT EXISTS
(
    SELECT 1
    FROM Employee e
    WHERE e.DepartmentID = d.DepartmentID
);
```

---

# Advanced Exercises

## 11. Latest order for every customer

```sql
SELECT *
FROM Orders o
WHERE OrderDate =
(
    SELECT MAX(o2.OrderDate)
    FROM Orders o2
    WHERE o2.CustomerID = o.CustomerID
);
```

---

## 12. Highest-paid employee in every department

```sql
SELECT e1.*
FROM Employee e1
WHERE Salary =
(
    SELECT MAX(e2.Salary)
    FROM Employee e2
    WHERE e2.DepartmentID = e1.DepartmentID
);
```

---

## 13. Customers spending more than average order amount

```sql
SELECT DISTINCT c.Name
FROM Customer c
JOIN Orders o
ON c.CustomerID = o.CustomerID
WHERE o.Amount >
(
    SELECT AVG(Amount)
    FROM Orders
);
```

---

## 14. Products never ordered

```sql
SELECT ProductName
FROM Product p
WHERE NOT EXISTS
(
    SELECT 1
    FROM Orders o
    WHERE o.ProductID = p.ProductID
);
```

---

## 15. Employees earning more than all employees in Department 10

```sql
SELECT Name
FROM Employee
WHERE Salary > ALL
(
    SELECT Salary
    FROM Employee
    WHERE DepartmentID = 10
);
```

---

# Scenario-Based Questions

## Banking

- Customers without loans.
- Accounts above branch average balance.
- Branches without active accounts.

## Telecom

- Subscribers who never recharged.
- Users with usage above plan average.
- Plans with no subscribers.

## E-Commerce

- Products never sold.
- Customers with latest orders.
- Products above category average price.

## Hospital

- Doctors without appointments.
- Doctors above department average salary.
- Departments with no doctors.

---

# Interview Challenge

1. Scalar vs Correlated Subquery?
2. EXISTS vs IN?
3. ANY vs ALL?
4. Why can NOT IN fail with NULL values?
5. When should JOIN replace a subquery?
6. Can correlated subqueries be optimized?
7. How does the optimizer execute EXISTS?
8. Which subqueries execute only once?

---

# Mini Project

Write SQL queries to:

1. Find inactive customers.
2. Find top-selling products.
3. Find employees above department average salary.
4. Display latest order for each customer.
5. Find products never purchased.
6. Find departments without employees.
7. Find customers with orders above average.
8. Compare EXISTS and JOIN solutions for the same problem.

---

# Revision Checklist

- ✔ Scalar Subqueries
- ✔ Correlated Subqueries
- ✔ EXISTS / NOT EXISTS
- ✔ ANY
- ✔ ALL
- ✔ IN
- ✔ NOT IN
- ✔ Aggregate Subqueries
- ✔ Multi-row Subqueries

---

# Memory Map

```text
SUBQUERIES
│
├── Scalar
├── Correlated
├── EXISTS
├── ANY / ALL
├── IN / NOT IN
└── Real Business Problems
```

---

# Final Takeaway

Subqueries allow SQL queries to solve complex business problems by nesting one query inside another. Mastering scalar, correlated, and multi-row subqueries, along with operators such as EXISTS, ANY, ALL, IN, and NOT IN, equips you to write expressive, efficient SQL. In technical interviews, the focus is not only on correct syntax but also on understanding execution behavior, performance trade-offs, and choosing the right approach for each scenario.
