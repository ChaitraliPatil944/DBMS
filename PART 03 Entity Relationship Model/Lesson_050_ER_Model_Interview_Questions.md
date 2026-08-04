# Lesson 050 --- ER Model Interview Questions

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

This lesson is designed to prepare you for:

-   Campus placements
-   Technical interviews
-   University examinations
-   Viva voce
-   DBMS coding rounds
-   System design fundamentals

------------------------------------------------------------------------

# How to Use This Lesson

Don't just memorize the answers.

For every question:

1.  Answer it yourself.
2.  Compare with the model answer.
3.  Draw a small ER diagram if applicable.
4.  Explain it aloud.

------------------------------------------------------------------------

# Section A --- Beginner Questions

### Q1. What is an ER Model?

**Answer**

An ER (Entity-Relationship) Model is a conceptual model used to design
databases by representing entities, attributes, and relationships before
creating database tables.

------------------------------------------------------------------------

### Q2. Who proposed the ER Model?

**Answer**

Peter Chen introduced the ER Model in **1976**.

------------------------------------------------------------------------

### Q3. Why is the ER Model used?

**Answer**

-   Understand business requirements
-   Reduce design mistakes
-   Visualize relationships
-   Design databases before implementation

------------------------------------------------------------------------

### Q4. What is an Entity?

An entity is a real-world object about which information is stored.

Examples:

-   Student
-   Employee
-   Product

------------------------------------------------------------------------

### Q5. What is an Attribute?

An attribute describes an entity.

Example:

Student

-   Name
-   Age
-   Roll Number

------------------------------------------------------------------------

### Q6. Difference between Entity and Attribute?

  Entity    Attribute
  --------- -----------
  Object    Property
  Student   Name
  Product   Price

------------------------------------------------------------------------

### Q7. How is an Entity represented?

Rectangle.

------------------------------------------------------------------------

### Q8. How is a Relationship represented?

Diamond.

------------------------------------------------------------------------

### Q9. How is an Attribute represented?

Oval.

------------------------------------------------------------------------

### Q10. What is a Key Attribute?

An attribute that uniquely identifies an entity.

------------------------------------------------------------------------

# Section B --- Intermediate Questions

### Q11. Strong Entity vs Weak Entity

  Strong             Weak
  ------------------ ------------------
  Independent        Depends on owner
  Own Primary Key    Partial Key
  Single Rectangle   Double Rectangle

------------------------------------------------------------------------

### Q12. What is a Partial Key?

A Partial Key uniquely identifies a weak entity **within its owner
entity**.

------------------------------------------------------------------------

### Q13. What is an Identifying Relationship?

A relationship connecting a weak entity with its owner.

Represented using a **double diamond**.

------------------------------------------------------------------------

### Q14. What is Cardinality?

Cardinality specifies how many instances of one entity can relate to
another.

Types:

-   1:1
-   1:N
-   N:1
-   M:N

------------------------------------------------------------------------

### Q15. Degree vs Cardinality

Degree = Number of participating entity types.

Cardinality = Number of participating entity instances.

------------------------------------------------------------------------

### Q16. What is Participation?

Participation specifies whether participation is mandatory or optional.

------------------------------------------------------------------------

### Q17. Difference between Total and Partial Participation?

  Total         Partial
  ------------- -------------
  Mandatory     Optional
  Double Line   Single Line

------------------------------------------------------------------------

### Q18. What is a Recursive Relationship?

A relationship where an entity relates to itself.

Example:

Employee manages Employee.

------------------------------------------------------------------------

### Q19. What is a Composite Attribute?

An attribute composed of multiple smaller attributes.

Example:

Name

-   First
-   Middle
-   Last

------------------------------------------------------------------------

### Q20. What is a Multi-Valued Attribute?

An attribute containing multiple values.

Example:

Phone Numbers.

------------------------------------------------------------------------

# Section C --- Advanced Questions

### Q21. Explain Generalization.

Generalization combines similar entities into a superclass using a
Bottom-Up approach.

------------------------------------------------------------------------

### Q22. Explain Specialization.

Specialization divides a superclass into subclasses using a Top-Down
approach.

------------------------------------------------------------------------

### Q23. Difference between Generalization and Specialization?

  Generalization   Specialization
  ---------------- ----------------
  Bottom-Up        Top-Down
  Many → One       One → Many

------------------------------------------------------------------------

### Q24. What is Aggregation?

Aggregation treats a relationship as a higher-level entity so it can
participate in another relationship.

------------------------------------------------------------------------

### Q25. What is Abstraction?

Abstraction hides implementation details while exposing only essential
information.

------------------------------------------------------------------------

### Q26. Why is ER to Relational Mapping needed?

Because relational databases store data as tables, not ER diagrams.

------------------------------------------------------------------------

### Q27. How do you map a Many-to-Many relationship?

Using a junction (bridge) table.

------------------------------------------------------------------------

### Q28. Why shouldn't derived attributes usually be stored?

Because they can be calculated and may become inconsistent.

------------------------------------------------------------------------

### Q29. How are Multi-Valued attributes mapped?

By creating a separate table.

------------------------------------------------------------------------

### Q30. How is a Weak Entity mapped?

Using a separate table with:

-   Owner's Primary Key
-   Partial Key
-   Composite Primary Key

------------------------------------------------------------------------

# Section D --- Scenario-Based Questions

### Q31.

Design an ER model for an Online Shopping System.

Expected entities:

-   Customer
-   Product
-   Order
-   Payment
-   Seller

------------------------------------------------------------------------

### Q32.

Design a Hospital ER diagram.

Expected entities:

-   Doctor
-   Patient
-   Medicine
-   Appointment
-   Bill

------------------------------------------------------------------------

### Q33.

A customer may register without placing an order.

What participation should Customer have?

**Answer:** Partial Participation.

------------------------------------------------------------------------

### Q34.

An Order must always belong to one Customer.

Participation?

**Answer:** Total Participation.

------------------------------------------------------------------------

### Q35.

A student studies many courses and every course has many students.

Cardinality?

**Answer:** Many-to-Many.

------------------------------------------------------------------------

# Section E --- Rapid Fire

1.  Entity → Rectangle
2.  Attribute → Oval
3.  Relationship → Diamond
4.  Weak Entity → Double Rectangle
5.  Derived Attribute → Dashed Oval
6.  Multi-Valued Attribute → Double Oval
7.  Total Participation → Double Line
8.  Partial Participation → Single Line
9.  Strong Entity → Independent
10. Generalization → Bottom-Up
11. Specialization → Top-Down
12. M:N → Junction Table

------------------------------------------------------------------------

# Common Interview Mistakes

-   Confusing Degree with Cardinality.
-   Confusing Generalization with Specialization.
-   Using attributes as entities.
-   Forgetting primary keys.
-   Ignoring participation constraints.
-   Implementing Many-to-Many without a bridge table.

------------------------------------------------------------------------

# Viva Questions

1.  Why is ER modeling important?
2.  Why not create tables directly?
3.  Which relationship type is most common?
4.  Why is normalization performed after ER design?
5.  Can an entity exist without attributes?
6.  Can a weak entity become strong?
7.  Which attribute types are not stored directly?
8.  When should aggregation be used?
9.  Why are primary keys important?
10. How does ER modeling reduce redundancy?

------------------------------------------------------------------------

# Final Interview Checklist

    ✓ Entity
    ✓ Weak Entity
    ✓ Strong Entity
    ✓ Attributes
    ✓ Attribute Types
    ✓ Keys
    ✓ Relationships
    ✓ Degree
    ✓ Cardinality
    ✓ Participation
    ✓ Recursive Relationship
    ✓ Generalization
    ✓ Specialization
    ✓ Aggregation
    ✓ Abstraction
    ✓ ER Symbols
    ✓ ER Design
    ✓ ER Mapping

------------------------------------------------------------------------

# Revision Sheet

    Rectangle → Entity

    Oval → Attribute

    Diamond → Relationship

    Triangle → IS-A

    Double Rectangle → Weak Entity

    Double Diamond → Identifying Relationship

    Double Oval → Multi-Valued

    Dashed Oval → Derived

    Underline → Key

    M:N → Bridge Table

    Bottom-Up → Generalization

    Top-Down → Specialization

## Interview Tips

-   Read the requirements before drawing.
-   Identify nouns first (entities).
-   Identify verbs next (relationships).
-   Always justify your cardinality.
-   Explain assumptions clearly.
-   Think from the business perspective, not just the database
    perspective.

**Remember:**

> Interviewers are usually evaluating your reasoning more than your
> final diagram. If you can explain *why* you chose a particular entity,
> relationship, or cardinality, you're demonstrating database design
> skills rather than memorization. That distinction tends to impress
> people more than confidently drawing diamonds in random places.
