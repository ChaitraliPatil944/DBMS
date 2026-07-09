# Lesson 086 --- Constraints Practice Problems

> **Part 05 --- Constraints**

------------------------------------------------------------------------

# Learning Objectives

Practice identifying, selecting, writing, and debugging DBMS constraints
using progressively challenging exercises.

------------------------------------------------------------------------

# Constraint Selection Cheat Sheet

``` text
Need unique identity?      → PRIMARY KEY

Need another unique value? → UNIQUE

Need relationship?         → FOREIGN KEY

Need mandatory data?       → NOT NULL

Need business validation?  → CHECK

Need automatic value?      → DEFAULT
```

------------------------------------------------------------------------

# Level 1 --- Basic (1--15)

### 1.

Identify the best constraint for:

``` text
StudentID must be unique.
```

------------------------------------------------------------------------

### 2.

Name must always have a value.

------------------------------------------------------------------------

### 3.

Age must be between 18 and 60.

------------------------------------------------------------------------

### 4.

Country should default to 'India'.

------------------------------------------------------------------------

### 5.

Email must never repeat.

------------------------------------------------------------------------

### 6.

Every Order must belong to a Customer.

------------------------------------------------------------------------

### 7.

Balance cannot be negative.

------------------------------------------------------------------------

### 8.

Semester must be from 1 to 8.

------------------------------------------------------------------------

### 9.

Quantity should default to 1.

------------------------------------------------------------------------

### 10.

EmployeeID identifies every employee.

------------------------------------------------------------------------

### 11--15.

Choose suitable constraints for:

-   Product
-   Library Book
-   Flight Ticket
-   Hospital Patient
-   Bank Account

------------------------------------------------------------------------

# Level 2 --- SQL Writing (16--35)

Write SQL to:

16. Create Student with PRIMARY KEY.

17. Add NOT NULL to Name.

18. Add UNIQUE to Email.

19. Add CHECK(Age \>= 18).

20. Add DEFAULT 'Pending'.

21. Create Department.

22. Create Employee with FOREIGN KEY.

23. Create Product with Price \>= 0.

24. Create Orders with CURRENT_DATE.

25. Create Enrollment with Composite PRIMARY KEY.

26. Add FOREIGN KEY using ALTER TABLE.

27. Create composite UNIQUE.

28. Restrict Gender values.

29. Restrict Marks to 0--100.

30. Create Customer table.

31. Create Invoice table.

32. Create Hospital schema.

33. Create Banking schema.

34. Create Airline schema.

35. Combine every major constraint in one table.

------------------------------------------------------------------------

# Level 3 --- Predict the Output (36--45)

Will the following succeed or fail?

36. 

``` sql
INSERT INTO Student(StudentID)
VALUES(NULL);
```

37. 

Duplicate PRIMARY KEY.

38. 

Duplicate UNIQUE Email.

39. 

Salary = -100 with CHECK(Salary \>= 0)

40. 

DepartmentID = 999 where no parent exists.

41. 

Insert without Status where DEFAULT exists.

42. 

Delete parent using CASCADE.

43. 

Delete parent using RESTRICT.

44. 

Update parent using CASCADE.

45. 

Insert NULL into NOT NULL column.

------------------------------------------------------------------------

# Level 4 --- Debugging (46--55)

Find and explain the error.

46. 

``` sql
PRIMARY KEY,
PRIMARY KEY
```

47. 

``` sql
CHECK(Age < 0)
```

48. 

``` sql
Email UNIQUE UNIQUE
```

49. 

``` sql
FOREIGN KEY(CustomerID)
REFERENCES Customer(ID)
```

(ID is not unique.)

50. 

``` sql
DEFAULT CURRENT_DATE
```

used on an integer column.

51--55.

Correct five invalid CREATE TABLE statements of your own.

------------------------------------------------------------------------

# Level 5 --- Database Design (56--65)

Design databases for:

56. University

57. Hospital

58. Banking

59. Railway Reservation

60. Food Delivery

61. Hotel Management

62. Inventory

63. Online Shopping

64. Library

65. Employee Management

For each identify:

-   Tables
-   PRIMARY KEY
-   FOREIGN KEY
-   UNIQUE
-   NOT NULL
-   CHECK
-   DEFAULT

------------------------------------------------------------------------

# Interview Challenge

Without notes, explain when you would choose:

-   PRIMARY KEY
-   UNIQUE
-   FOREIGN KEY
-   NOT NULL
-   CHECK
-   DEFAULT

Give one real-world example for each.

------------------------------------------------------------------------

# Self-Evaluation

``` text
□ I can identify the correct constraint.

□ I can write CREATE TABLE.

□ I can write ALTER TABLE.

□ I can combine multiple constraints.

□ I can debug SQL errors.

□ I understand Referential Integrity.

□ I understand Entity Integrity.

□ I can design databases using constraints.
```

------------------------------------------------------------------------

# Final Revision Map

``` text
Constraints
│
├── Domain
├── Key
├── Entity Integrity
├── Referential Integrity
├── PRIMARY KEY
├── FOREIGN KEY
├── UNIQUE
├── NOT NULL
├── CHECK
└── DEFAULT
```

# Final Takeaway

The fastest way to master constraints is to apply them repeatedly in
realistic database designs. Every well-designed table combines multiple
constraints to protect data quality, enforce business rules, and
maintain relationships. The database never gets tired of checking rules,
which is fortunate, because users have an extraordinary talent for
discovering every input you forgot to validate.
