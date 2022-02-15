---
id: DR0jWndTXCBUiDu9h0IAQ
title: Databases
desc: ''
updated: 1644912297647
created: 1644910717271
---

![](/assets/images/2022-02-15-07-39-05.png)

_Database hosted on AWS managed database service (e.g. RDS/DynamoDB)_


## Available databases
- **RDS** for classic relational databases
- **DynamoDB** for non-relational, such as storing key-value pairs
- **DocumentDBS** for content management system (with MongoDB support)
- **Neptune graph** for building complex networks, such as fraud or recommendation engines
- **QLDB ledger** for immutability


## AWS RDS

### Supported database engines
- Amazon Aurora
- MySQL
- MariaDB
- PostgreSQL
- Oracle
- Microsoft SQL Server

**Amazon Aurora** is highly optimised for AWS, with greater performance and durability. It is also compatibility with MySQL and PostgreSQL. Overkill for simple database.


### Setup
- Once database engine selected, DB instance size can also be selected similar to options for EC2 instance
- Also need to create a username and password for database access
- AZ can be configured which handles auto-replication and failover all handled by AWS
- Charges per instance run-time (per hour)


## AWS DynamoDB
- Non-relational database
- Great for storing key-value pairs or documents
- Not bothered with relations between tables
- Charged per usage and amount of data









