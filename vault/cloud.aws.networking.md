---
id: TqCHfi7cFSDdTvBz1gQGG
title: Networking
desc: ''
updated: 1642451730983
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

## Routing
A route table is created automatically when the VPC is setup. The route table determines the where network traffic is directed.

The default configuration is to allow traffic between all subnets within a local network. This cannot be deleted.

It is possible to also create custom tables for routing traffic from an internet gateway to a particular subnet. 

![](/assets/images/2022-01-17-19-43-38.png)

## VPC security

### Network ACL
- Firewall at subnet level
- control over what is allowed to enter or leave the subnet
- default is to allow all traffic
- must always consider outbound and inbound traffic

### Security groups (EC2 instances)
- Firewall for EC2 instance
- default configuration is block all inbound traffic; allow all outbound traffic
- open inbound ports to accept traffic from the internet


## Example process setting up VPC for an Amazon EC2 instance
1. Create elastic IP, for NAT gateway
2. Create VPC with public & private subnets
3. Create second set of public & private subnets for second AZ
4. Set up route tables
5. Set up security groups for EC2 instances
6. launch EC2 instance with created VPC and public subnet



    
    
    






