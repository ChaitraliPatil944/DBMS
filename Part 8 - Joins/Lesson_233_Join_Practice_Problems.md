# Lesson 233 - Join Practice Problems

**Part:** Part 8 - Joins

**Difficulty:** Beginner → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 60–90 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Apply different types of SQL joins to real-world problems.
- Decide which join is appropriate for a given scenario.
- Write efficient join queries.
- Solve interview-level SQL questions.
- Strengthen problem-solving skills using relational databases.

---

# Database Schema

Assume the following tables:

### Customer

```text
Customer(CustomerID, Name, City)
```

### Orders

```text
Orders(OrderID, CustomerID, ProductID, Amount, OrderDate)
```

### Product

```text
Product(ProductID, ProductName, CategoryID, Price)
```

### Category

```text
Category(CategoryID, CategoryName)
```

### Employee

```text
Employee(EmployeeID, Name, ManagerID, DepartmentID, Salary)
```

### Department

```text
Department(DepartmentID, DepartmentName)
```

---

# Beginner Problems

## 1. Display every customer with their orders.

```sql
SELECT c.Name,
       o.OrderID,
       o.Amount
FROM Customer c
INNER JOIN Orders o
ON c.CustomerID = o.CustomerID;
```

---

## 2. Display every customer, even if they never ordered.

```sql
SELECT c.Name,
       o.OrderID
FROM Customer c
LEFT JOIN Orders o
ON c.CustomerID = o.CustomerID;
```

---

## 3. Display all departments and employees.

```sql
SELECT d.DepartmentName,
       e.Name
FROM Employee e
RIGHT JOIN Department d
ON e.DepartmentID = d.DepartmentID;
```

---

## 4. Generate every product-size combination.

```sql
SELECT *
FROM Product
CROSS JOIN Size;
```

---

## 5. Display employees and their managers.

```sql
SELECT e.Name AS Employee,
       m.Name AS Manager
FROM Employee e
LEFT JOIN Employee m
ON e.ManagerID = m.EmployeeID;
```

---

# Intermediate Problems

## 6. Find customers who never placed an order.

```sql
SELECT c.CustomerID,
       c.Name
FROM Customer c
LEFT JOIN Orders o
ON c.CustomerID = o.CustomerID
WHERE o.CustomerID IS NULL;
```

---

## 7. Find products that have never been ordered.

```sql
SELECT p.ProductName
FROM Product p
LEFT JOIN Orders o
ON p.ProductID = o.ProductID
WHERE o.ProductID IS NULL;
```

---

## 8. Display product names with categories.

```sql
SELECT p.ProductName,
       c.CategoryName
FROM Product p
INNER JOIN Category c
ON p.CategoryID = c.CategoryID;
```

---

## 9. Find departments without employees.

```sql
SELECT d.DepartmentName
FROM Employee e
RIGHT JOIN Department d
ON e.DepartmentID = d.DepartmentID
WHERE e.EmployeeID IS NULL;
```

---

## 10. Find customers with total spending.

```sql
SELECT c.Name,
       SUM(o.Amount) AS TotalSpent
FROM Customer c
INNER JOIN Orders o
ON c.CustomerID = o.CustomerID
GROUP BY c.Name;
```

---

# Advanced Problems

## 11. Top 5 customers by spending.

```sql
SELECT c.Name,
       SUM(o.Amount) AS TotalSpent
FROM Customer c
INNER JOIN Orders o
ON c.CustomerID = o.CustomerID
GROUP BY c.Name
ORDER BY TotalSpent DESC
LIMIT 5;
```

---

## 12. Display running revenue.

```sql
SELECT OrderDate,
       Amount,
       SUM(Amount)
OVER(ORDER BY OrderDate)
AS RunningRevenue
FROM Orders;
```

---

## 13. Rank employees by salary.

```sql
SELECT Name,
       Salary,
       DENSE_RANK()
OVER(ORDER BY Salary DESC)
AS SalaryRank
FROM Employee;
```

---

## 14. Display first order for every customer.

```sql
SELECT CustomerID,
       OrderID,
       ROW_NUMBER()
OVER(PARTITION BY CustomerID
ORDER BY OrderDate)
AS OrderNumber
FROM Orders;
```

---

## 15. Display latest order for each customer.

```sql
SELECT *
FROM
(
SELECT CustomerID,
       OrderID,
       OrderDate,
       ROW_NUMBER()
OVER(PARTITION BY CustomerID
ORDER BY OrderDate DESC) AS RN
FROM Orders
) X
WHERE RN = 1;
```

---

# Scenario-Based Questions

## Banking

- Customers without accounts.
- Branches without employees.
- Highest-value transactions.

## Telecom

- Subscribers who never recharged.
- SIM cards without owners.
- Plans with no active users.

## E-Commerce

- Products without sales.
- Categories without products.
- Customers with highest revenue.

## Hospital

- Doctors without appointments.
- Patients without visits.
- Department-wise patient count.

---

# Interview Challenge

### Q1

Difference between INNER JOIN and LEFT JOIN?

---

### Q2

Why is LEFT JOIN commonly used to find missing records?

---

### Q3

Why is NATURAL JOIN discouraged in enterprise applications?

---

### Q4

How can FULL OUTER JOIN be implemented in MySQL?

---

### Q5

Explain the difference between CROSS JOIN and INNER JOIN.

---

### Q6

What is a SELF JOIN?

---

### Q7

How does an optimizer choose a join algorithm?

---

### Q8

What indexes improve join performance?

---

# Mini Project

Using the schema above, write SQL queries to:

1. Find the top-selling products.
2. Find inactive customers.
3. Display department-wise average salary.
4. Find products never purchased.
5. Rank employees by salary.
6. Generate monthly sales reports.
7. Display customer lifetime value.
8. Find the manager of every employee.
9. Display categories without products.
10. Show customers with their latest order.

---

# Revision Checklist

- ✔ INNER JOIN
- ✔ LEFT JOIN
- ✔ RIGHT JOIN
- ✔ FULL OUTER JOIN
- ✔ CROSS JOIN
- ✔ SELF JOIN
- ✔ NATURAL JOIN
- ✔ GROUP BY
- ✔ Window Functions
- ✔ Ranking Functions

---

# Memory Map

```text
JOINS
│
├── INNER
├── LEFT
├── RIGHT
├── FULL OUTER
├── CROSS
├── SELF
└── NATURAL
        │
        ▼
Real Business Problems
```

---

# Final Takeaway

Joins are the foundation of relational databases because they connect normalized data spread across multiple tables. Mastering joins means more than remembering syntax. You should know which join to choose, how it affects the result set, how the optimizer executes it, and how indexes influence performance. These concepts are among the most frequently tested topics in SQL interviews and are equally important in real-world database development.
