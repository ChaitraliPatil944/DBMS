# Lesson 6: Cloud Databases

## Learning Objectives
- Understand cloud databases and their architecture.
- Learn different cloud database deployment models.
- Explore benefits, limitations, and real-world use cases.

## Introduction
A **Cloud Database** is a database that is hosted, managed, and accessed through a cloud computing platform rather than on an organization's local servers. Cloud databases provide high availability, scalability, automatic backups, and flexible pricing models.

## Architecture

```
            +-------------------+
            |   Client Devices  |
            +---------+---------+
                      |
                  Internet
                      |
        +-------------+-------------+
        |   Cloud Database Service  |
        |  Compute + Storage + DBMS |
        +-------------+-------------+
                      |
              Cloud Storage System
```

## Types of Cloud Databases

### 1. Public Cloud
- Hosted by third-party providers.
- Accessible over the Internet.
- Cost-effective.

### 2. Private Cloud
- Dedicated infrastructure.
- Higher security.
- Suitable for sensitive data.

### 3. Hybrid Cloud
- Combination of public and private clouds.
- Balances flexibility and security.

## Characteristics
- On-demand scalability
- High availability
- Automatic backups
- Managed infrastructure
- Pay-as-you-go pricing

## Advantages
- Easy scalability
- Reduced infrastructure cost
- Automatic updates
- Disaster recovery support
- Global accessibility

## Disadvantages
- Internet dependency
- Vendor lock-in
- Data privacy concerns
- Recurring subscription costs
- Limited control over infrastructure

## Popular Cloud Database Services
- Amazon RDS
- Google Cloud SQL
- Azure SQL Database
- MongoDB Atlas
- Firebase Realtime Database

## Real-World Applications
- E-commerce platforms
- Mobile applications
- Online banking
- SaaS products
- Social media platforms

## Traditional Database vs Cloud Database

| Feature | Traditional | Cloud Database |
|---------|-------------|----------------|
| Deployment | On-Premises | Cloud |
| Scalability | Limited | High |
| Maintenance | Organization | Cloud Provider |
| Backup | Manual | Automatic |
| Cost | High Initial | Pay-as-you-go |

## Interview Questions
1. What is a cloud database?
2. What are the advantages of cloud databases?
3. Explain public, private, and hybrid cloud databases.
4. What is vendor lock-in?
5. Name four popular cloud database services.

## Key Takeaways
- Cloud databases are hosted and managed on cloud platforms.
- They provide scalability, availability, and automated management.
- They are widely used in modern web, mobile, and enterprise applications.
