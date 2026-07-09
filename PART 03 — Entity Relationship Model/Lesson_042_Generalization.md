# Lesson 042 --- Generalization

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Generalization is
-   Why Generalization was introduced
-   Superclass and Subclass
-   IS-A Relationship
-   Bottom-Up Approach
-   Characteristics of Generalization
-   ER Diagram notation
-   SQL implementation
-   Real-world examples
-   Generalization vs Specialization
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

As databases become larger, many entities begin sharing common
attributes.

Example:

    Car
    Bike
    Truck

All have:

-   Registration Number
-   Brand
-   Color

Instead of repeating these attributes in every entity, we create a
**general entity** that stores the common information.

This process is called **Generalization**.

------------------------------------------------------------------------

# 2. What is Generalization?

**Generalization** is the process of combining two or more similar
lower-level entities into a single higher-level entity called a
**Superclass**.

It follows a **Bottom-Up** approach.

    Car
    Bike
    Truck
       │
       ▼
    Vehicle

------------------------------------------------------------------------

# 3. Why Do We Need Generalization?

Without Generalization:

    Car
     ├── Brand
     ├── Color
     └── RegistrationNo

    Bike
     ├── Brand
     ├── Color
     └── RegistrationNo

    Truck
     ├── Brand
     ├── Color
     └── RegistrationNo

The same attributes are repeated.

With Generalization:

              Vehicle
         ├── RegistrationNo
         ├── Brand
         └── Color
             ▲
       ┌─────┼─────┐
       │     │     │
     Car   Bike  Truck

Redundancy is reduced.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Imagine a toy box.

    Toy

    ├── Car Toy
    ├── Robot Toy
    └── Doll

Every toy has:

-   Name
-   Price
-   Manufacturer

Instead of writing these for every toy, create one parent called
**Toy**.

------------------------------------------------------------------------

# 5. Superclass and Subclass

Superclass:

A generalized entity containing common attributes.

Subclass:

A specialized entity containing unique attributes.

Example:

    Superclass

    Vehicle

    ↓

    Subclasses

    Car
    Bike
    Truck

------------------------------------------------------------------------

# 6. IS-A Relationship

Generalization uses an **IS-A** relationship.

    Car

    IS A

    Vehicle

    Bike

    IS A

    Vehicle

Meaning:

Every Car **is a** Vehicle.

Every Bike **is a** Vehicle.

------------------------------------------------------------------------

# 7. ER Diagram Representation

                Vehicle
              /    |    \
             /     |     \
          Car    Bike   Truck

Another representation:

                 Vehicle
                    ▲
          ┌─────────┼─────────┐
          │         │         │
        Car       Bike      Truck

------------------------------------------------------------------------

# 8. Characteristics

Generalization:

-   Combines similar entities
-   Removes redundancy
-   Creates a Superclass
-   Uses Bottom-Up design
-   Represents "IS-A" relationships

------------------------------------------------------------------------

# 9. SQL Implementation

Superclass

``` sql
CREATE TABLE Vehicle(
    VehicleID INT PRIMARY KEY,
    Brand VARCHAR(50),
    Color VARCHAR(30),
    RegistrationNo VARCHAR(20)
);
```

Subclass

``` sql
CREATE TABLE Car(
    VehicleID INT PRIMARY KEY,
    NumberOfDoors INT,
    FOREIGN KEY (VehicleID)
        REFERENCES Vehicle(VehicleID)
);
```

``` sql
CREATE TABLE Bike(
    VehicleID INT PRIMARY KEY,
    HasCarrier BOOLEAN,
    FOREIGN KEY (VehicleID)
        REFERENCES Vehicle(VehicleID)
);
```

------------------------------------------------------------------------

# 10. Real-World Examples

## University

    Person

    ├── Student
    ├── Teacher
    └── Staff

------------------------------------------------------------------------

## Banking

    Account

    ├── Savings Account
    ├── Current Account
    └── Loan Account

------------------------------------------------------------------------

## Hospital

    Employee

    ├── Doctor
    ├── Nurse
    └── Receptionist

------------------------------------------------------------------------

## Online Shopping

    Product

    ├── Electronics
    ├── Clothing
    └── Grocery

------------------------------------------------------------------------

# 11. Generalization vs Specialization

  Generalization          Specialization
  ----------------------- ----------------------
  Bottom-Up               Top-Down
  Combine entities        Divide entities
  Creates Superclass      Creates Subclasses
  Finds common features   Adds unique features

Memory Trick:

    Generalization

    Many

    ↓

    One

    Specialization

    One

    ↓

    Many

------------------------------------------------------------------------

# 12. Advantages

-   Reduces duplicate attributes
-   Easier maintenance
-   Better database design
-   Improves scalability
-   Simplifies future changes

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Thinking Generalization copies data.

It reorganizes the design.

❌ Confusing Generalization with Normalization.

Generalization models inheritance.

Normalization removes redundancy in relational tables.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is Generalization?
2.  What is a Superclass?
3.  What is an IS-A relationship?

### Intermediate

1.  Why is Generalization Bottom-Up?
2.  Explain Superclass and Subclass.

### Advanced

Design a Generalization hierarchy for:

-   Hospital
-   Banking
-   University
-   E-commerce

------------------------------------------------------------------------

# 15. Practice Problems

Create a Generalization model for:

1.  Animals
2.  Employees
3.  Vehicles
4.  Accounts
5.  Products

Identify:

-   Superclass
-   Subclasses
-   Common attributes
-   Unique attributes

------------------------------------------------------------------------

# Revision Notes

    Generalization

    Many Entities

    ↓

    Combine

    ↓

    Superclass

    Car
    Bike
    Truck

    ↓

    Vehicle

Key Points

-   Bottom-Up Approach
-   IS-A Relationship
-   Removes redundancy
-   Creates Superclass
-   Improves maintainability

**Remember:**

> Generalization combines multiple similar entities into a single parent
> entity by extracting their common characteristics. It models
> inheritance in databases and makes ER designs cleaner, reusable, and
> easier to maintain.
