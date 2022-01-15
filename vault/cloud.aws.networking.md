---
id: TqCHfi7cFSDdTvBz1gQGG
title: Networking
desc: ''
updated: 1642252855976
created: 1642250612084
---

## Amazon VPC
The VPC is an isolated network created in the AWS cloud.

Must choose three main factors:
1. VPC name
2. Region
3. IP range (CIDR)

### Subnet
In order to isolate services from one another, each service can be given a subnet within the VPC.

The purpose of the subnet is for access control or for network optimisation. In the most typical use case it's possible to create a public and private subnet, essentially preventing direct public access to certain services. 

Must specify the following, when setting up each subnet:
1. VPC where subnet should reside
2. Availability Zone (within the region)
3. CIDR block, which must be subset of VPC CIDR

To maintain availability it is recommended to recreate the subnet within different AZs. 

#### Reserved IPs
![](/assets/images/2022-01-15-13-16-12.png)

## Gateway
Once the VPC is set up, a gateway (VIG) must be created to authenticate access. A Virtual Private Gateway (VPG) can also be created for securely connecting to another private network.






