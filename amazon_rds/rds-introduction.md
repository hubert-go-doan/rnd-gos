# Getting Started with Amazon RDS

### Table of Contents
1. What is Amazon RDS?
2. Features of RDS
3. Amazon RDS Support Engines
4. How does Amazon RDS work?
5. Model Development
6. RDS Proxy

## What is Amazon RDS?

Amazon Relational Database Service (RDS) is a managed SQL database service provided by Amazon Web Services (AWS). Amazon RDS supports an array of database engines to store and organize data. It also helps with relational database management tasks, such as data migration, backup, recovery and patching.

Amazon RDS facilitates the deployment and maintenance of relational databases in the cloud. A cloud administrator uses Amazon RDS to set up, operate, manage and scale a relational instance of a cloud database. Amazon RDS is not itself a database; it is a service used to manage relational databases.

## Features of RDS

1. Easy to use: Amazon RDS makes it easy to create and manage a relational database, allowing users to focus on their applications and business logic, rather than on the underlying infrastructure.

2. Scalability: Amazon RDS allows users to easily scale their database up or down, depending on their needs, without having to worry about managing the underlying infrastructure.

3. Security: Amazon RDS provides a number of built-in security features, such as encryption at rest and in transit, to help protect users’ data.

4. Cost-effective: Amazon RDS allows users to pay for only the resources they use, making it a cost-effective solution for managing relational databases.

5. Automated Backups and Snapshots: Automatically backs up your database daily and retains backups.Supports manual snapshots and restores from snapshots.

6. Monitoring and Metrics:Integrates with Amazon CloudWatch to monitor the performance and health of database instances.Provides performance metrics and event notifications.

## RDS Support Engines

- Mysql
- Postgresqs
- Oracle
- SQL server
- MariaSQL
- Amazon Aurora (relational database provided by Amazon, only supports 2 engines: Aurora MySQL and Aurora PostgreSQL)

![RDS engines](./assets/01.png "RDS Support Engines")

## How does Amazon RDS work?

Amazon RDS isn’t a database itself, but a way to manage relational databases within the cloud. A relational database is a kind of database that uses tables to store and organize data with defined relationships. This enables businesses to run data queries across multiple tables, which makes it easier to organize and understand related sets of data, which is useful from both a security and a practical perspective.

Traditionally, these databases would require on-site servers that would need constant maintenance to remain up and running. Amazon RDS enables startups to instead take advantage of flexible cloud offerings to deploy their database.

## Model Development

![Model Development](./assets/02.png "Model Development")

### Single DB instance

Only creates one database instance, no backup versions. If an AZ problem occurs, the database cannot be accessed.

![Single DB instance](./assets/04.png "Single DB instance")

### Multi-AZ DB instance

An instance copy will be created in another AZ (cannot be in the same zone as the main database, because when a problem occurs at the zone level, it cannot be covered). Provides high availability. Sync data from main database. This instance cannot be accessed.

![Multi-AZ DB instance](./assets/05.png "Multi-AZ DB instance")

### RDS Multi-AZ DB Cluster

Two instances with read only mode are created, continuously replicating data from the master (main) database. This instance can only read data.  Ensure that if one zone fails, another zone can continue to operate without interruption.

Suitable for read > write applications

Endpoints of 2 separate instances: When a problem occurs, you need to edit the endpoint connection

![RDS Multi-AZ DB Cluster](./assets/03.png "RDS Multi-AZ DB Cluster")

## RDS Proxy

RDS provides proxy mechanisms that help manage connections to instances effectively. When using a proxy, the application does not connect directly to RDS but through the proxy endpoint. 

Additional costs will be incurred for proxies.

Currently supports 3 engines: MySQL, PostgreSQL, SQL Server.

![RDS Proxy](./assets/06.png "RDS Proxy")
