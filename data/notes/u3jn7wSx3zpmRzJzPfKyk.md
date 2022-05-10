
## Overview
Typical application hosted on 3 tiers:
1. Presentation layer (HTML,CSS,JS)
2. Application layer
3. Data layer

EC2 instances could handle the presentation layer and the application layer, however this is not ideal and these tiers should be separated.

Presentation layer can be hosted on S3, with static hosting enabled. JS can handle the dynamic nature of the front end if required.

Lambda can be used for backend functions e.g. CRUD operations. Could be one or more Lambda functions.

Amazon API Gateway can be used as a front door to trigger the lambda functions, triggered by JS on the front end.

Amazon Route53 can be used for domain name management and Amazon Cloudfront for caching. 

Networking services not required for serverless applications e.g. VPC/subnets etc

![](/assets/images/2022-02-17-21-58-07.png)

*Example of application built in Serverless*

