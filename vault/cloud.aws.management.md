---
id: WjeVqtwBm7Sr4rvMVqM0K
title: Management
desc: ''
updated: 1645133032979
created: 1645084668122
---

# Monitoring
In AWS many of the services create metrics, such as CPU usage and simultaneous connections. 

In normal use a baseline can be established to help determine whether the services are running smoothly or not. 

Can trigger automated alerts to someone or something to remediate the issue, when metric deviate too far away from the baseline.

## CloudWatch
Collates all service statistics in one place.

Most metrics are sent to CloudWatch from other AWS service automatically when the service is created.

### Create a dashboard
A dashboard is a customised page in the console which can be used to monitor different types of resources in a single view. Includes multi-region. 

1. Navigate to CloudWatch in AWS
2. Click `Dashboards` > `Create dashboard`
3. Provide a name and click `Create dashboard`
4. Select from different available widgets to add to dashboard
5. Select either `Metrics` or `Logs` for data source
6. Select various metrics from different AWS services

It's also possible to create custom metrics which can be sent from an application. Could be very specific to use case, such as API calls. 

### Create an alarm
Allows you to create threshold which can be triggered if a metric goes over for a period of time.

1. Click `Alarms` > `In alarm` > `Create alarm`
2. Select desired measure and click `Select metric`
3. Edit the statistic for the alarm and period
4. Edit the conditions and threshold for the alarm and click `Next`
5. Select an alarm state trigger: `In alarm`, `OK` or `Insufficient data`
6. Configure **SNS** for notifications
7. Click `Next` and provide the alarm a name
8. Click `Next` and preview & `Create alarm`

# Optimisation
Redundancy and autoscaling may be needed to ensure application always available, when issues with the server occur and when demand increases.

- Can use second availability zone (AZ), if hosting an application
- Automatic redirection of traffic is required
- Can chose to scale vertically (capacity) or horizontally (increase simultaneous services)

## Elastic load balancing (ELB)
- Handles traffic to different EC2 instances
- highly available and scalable
- Regional service

*Example of ELB directing traffic*

![](/assets/images/2022-02-17-20-12-12.png)

*Various load balancers*

![](/assets/images/2022-02-17-20-14-34.png)

### Application Load Balancer (ALB)
- Listener port & protocol e.g. 80 HTTP
- Target group is backend to direct traffic and ability to health check
- Rules defines how requests are directed to targets (e.g. different parts of application)

![](/assets/images/2022-02-17-20-26-02.png)

#### Creating ALB
- Can be created via EC2 service
- Type can be selected at this point, along with listeners and VPC/Subnets
- Security group can be configured to only allow certain traffic
- Finally configure routing and targets

## Auto-scaling
Using CloudWatch to monitor metrics, this can be used to trigger alert and subsequently trigger auto-scaling. This could involve increasing the number of EC2 instances.

![](/assets/images/2022-02-17-21-07-12.png)

In order for EC2 instances to be auto-scaled:
- A launch template must be created, which can be done from thh EC2 service in AWS console
- An Auto Scaling group must then be created
- ...selecting the launch template, VPC/Subnets, load balancer & target group
- Enable ELB health checks
- Select the minimum and maximum group size (number of total instances)
- Enable target tracking to configure when to scale
 
**Warning:** if auto scaling is active and EC2 instances are terminate, auto scaling will try to increase the number of EC2 instances back up to the minimum configured








