---
id: CPqidC2jdYCbcdTgTu6qq
title: Lambda
desc: ''
updated: 1642239345683
created: 1642238509411
---


Lambda is a serverless compute service for running code < 15 mins, on trigger.

## Steps
1. Package and upload code to Lambda function
2. Configure trigger for when want function to run

Charged only when Lambda function is running.

## Management console
1. Create function
2. Author from scratch, container or AWS repo

### ... from scratch

3. Name function and runtime language
4. Set execution role, ensuring the code can call other AWS services
5. From the designer view, add a trigger
6. Add source code, either written in the browser or from zip/S3
7. Use logs and monitoring to check the function works

