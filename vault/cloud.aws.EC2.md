---
id: Xnk5A8neJqINCoBLZn3Oo
title: EC2
desc: ''
updated: 1642533086926
created: 1642016207924
---

EC2 are virtual instances which can be spooled up very quickly and come in many different flavours, which have different costs and performance. 

Instances are a combination of virtual processors (vCPUs), memory, network, and, in some cases, instance storage and graphics processing units (GPUs).

Flexibility allows you to very quickly create, terminate and upgrade an instance. 

These instances can be started in an Availability Zone of choice. For high availability it is recommended to consider at least two EC2 instances in separate Availability Zones. 

## AWS Management Console
The following step can be performed to create an EC2 instance, using the management console.

**Click EC2 > launch instance**

- Step 1: choose AMI
- Step 2: choose instance type e.g. size etc
- Step 3: Configure instance details, including **User data** script
- Step 4: Add storage
- Step 5: Add tags (key/value), to categorise instance for organisation
- Step 6: Configure security group, to enable traffic required by the server (SSH, HTTP etc)

A key pair is required if accessing the instance from outside of the AWS management console.

## EBS storage
- Elastic Block Storage (EBS) is persistent storage which can attach to one or more EC2 instances. As they are separate, they persist when the EC2 instance goes down. 
- They can be backed up using _snapshots_
- use cases:
    - OS
    - Databases
    - Enterprise applications
    - Throughput-intensive applications







