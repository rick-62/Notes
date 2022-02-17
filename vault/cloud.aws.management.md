---
id: WjeVqtwBm7Sr4rvMVqM0K
title: Management
desc: ''
updated: 1645086742165
created: 1645084668122
---

## Monitoring
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



