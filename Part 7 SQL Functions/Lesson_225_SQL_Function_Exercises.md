# Lesson 225 - SQL Function Exercises

**Part:** Part 7 - SQL Functions

**Difficulty:** Beginner → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 45–60 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Apply SQL functions to solve practical problems.
- Combine aggregate, string, numeric, date, window, and analytical functions.
- Solve interview-oriented SQL questions.
- Understand which SQL function is appropriate for different scenarios.

---

# Exercise 1 – Aggregate Functions

## Q1. Find the total number of employees.

```sql
SELECT COUNT(*) FROM Employee;
```

## Q2. Find the average salary.

```sql
SELECT AVG(Salary) FROM Employee;
```

## Q3. Find the highest and lowest salary.

```sql
SELECT MAX(Salary), MIN(Salary)
FROM Employee;
```

## Q4. Find the total salary paid department-wise.

```sql
SELECT Department,
SUM(Salary)
FROM Employee
GROUP BY Department;
```

---

# Exercise 2 – String Functions

## Q1. Convert all employee names to uppercase.

```sql
SELECT UPPER(Name)
FROM Employee;
```

## Q2. Display full names.

```sql
SELECT CONCAT(FirstName,' ',LastName)
FROM Employee;
```

## Q3. Remove leading and trailing spaces.

```sql
SELECT TRIM(Name)
FROM Employee;
```

## Q4. Extract the first three characters.

```sql
SELECT SUBSTRING(Name,1,3)
FROM Employee;
```

---

# Exercise 3 – Numeric Functions

## Q1. Round salaries to two decimal places.

```sql
SELECT ROUND(Salary,2)
FROM Employee;
```

## Q2. Find the absolute profit/loss.

```sql
SELECT ABS(ProfitLoss)
FROM Sales;
```

## Q3. Calculate square root.

```sql
SELECT SQRT(144);
```

---

# Exercise 4 – Date Functions

## Q1. Display today's date.

```sql
SELECT CURDATE();
```

## Q2. Find orders placed in the last 30 days.

```sql
SELECT *
FROM Orders
WHERE OrderDate >= DATE_SUB(CURDATE(),INTERVAL 30 DAY);
```

## Q3. Calculate customer membership duration.

```sql
SELECT CustomerID,
DATEDIFF(CURDATE(),JoinDate)
AS MembershipDays
FROM Customer;
```

---

# Exercise 5 – Window Functions

## Q1. Rank employees by salary.

```sql
SELECT Name,
Salary,
RANK() OVER(ORDER BY Salary DESC)
FROM Employee;
```

## Q2. Generate a running total.

```sql
SELECT OrderID,
Amount,
SUM(Amount)
OVER(ORDER BY OrderDate)
AS RunningTotal
FROM Orders;
```

## Q3. Find the previous salary.

```sql
SELECT Name,
Salary,
LAG(Salary)
OVER(ORDER BY Salary)
FROM Employee;
```

---

# Exercise 6 – Analytical Functions

## Q1. Assign row numbers.

```sql
SELECT Name,
ROW_NUMBER()
OVER(ORDER BY Salary DESC)
FROM Employee;
```

## Q2. Divide customers into four groups.

```sql
SELECT CustomerID,
NTILE(4)
OVER(ORDER BY Revenue DESC)
FROM Customer;
```

## Q3. Find the next recharge amount.

```sql
SELECT CustomerID,
RechargeAmount,
LEAD(RechargeAmount)
OVER(ORDER BY RechargeDate)
FROM Recharge;
```

---

# Scenario-Based Questions

## Banking

Find the top 5 customers by account balance.

## Telecom

Find customers whose recharge expires within the next 7 days.

## E-Commerce

Calculate the running revenue for each day.

## Hospital

Rank doctors based on the number of appointments.

---

# Mini Project Challenge

Using the following tables:

- Employee
- Customer
- Orders
- Product

Write SQL queries to:

1. Find total revenue.
2. Find top-selling product.
3. Calculate average order value.
4. Rank customers by spending.
5. Find inactive customers for the last 90 days.
6. Display running monthly sales.
7. Show department-wise average salary.
8. Display the first and last order for every customer.

---

# Interview Practice

## Beginner

1. What is the difference between aggregate and scalar functions?
2. Why do aggregate functions ignore NULL values?
3. Difference between CURDATE() and NOW()?

## Intermediate

1. GROUP BY vs PARTITION BY?
2. RANK() vs DENSE_RANK()?
3. COUNT(*) vs COUNT(column)?

## Advanced

1. Explain the execution order of a window function.
2. How do indexes affect SQL functions?
3. Why can functions reduce query performance?

---

# Revision Checklist

- ✔ Aggregate Functions
- ✔ String Functions
- ✔ Numeric Functions
- ✔ Date Functions
- ✔ Window Functions
- ✔ Analytical Functions
- ✔ GROUP BY
- ✔ HAVING
- ✔ OVER()
- ✔ PARTITION BY
- ✔ ORDER BY

---

# Memory Map

```
SQL Functions
│
├── Aggregate
├── String
├── Numeric
├── Date
├── Window
└── Analytical
```

---

# Final Takeaway

Completing these exercises reinforces the concepts introduced throughout Part 7. In technical interviews, candidates are rarely asked to recall syntax alone. Instead, they are expected to solve realistic business problems by selecting the appropriate SQL function, writing efficient queries, and explaining why their solution works. Practicing these exercises will strengthen both conceptual understanding and practical SQL skills.
