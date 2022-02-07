---
id: QNVf8BHSlHCZ9m39lur96
title: Batch
desc: ''
updated: 1644221526769
created: 1644049006818
---

## Deploy kedro to batch (simple version)
This deployment guide will outline the instructions for uploading a Kedro project to AWS Batch. This is for the main intention of allowing us to trigger running the project automatically using AWS Eventbridge, and output the results to an S3 bucket which can be accessed directly online.

Note: assumes AWS account has been setup and configured

#### Future improvements
- Use CDK/CLI to automate build of the AWS stack
- Run individual nodes on separate batch jobs
- Improve public access policy for S3 bucket
- Migrate to AWS serverless (step functions & lambda)



### Create a new S3 bucket in AWS
1. Navigate to S3 Management Console in AWS
2. Click **Create bucket** 
3. Name the bucket, adhering to [bucket naming guidance](https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucketnamingrules.html)
4. Ensure the region selected is correct for the project
5. Uncheck **Block all public access** so individual files can be exposed to the internet
6. Leave the remaining settings as default and click **Create bucket**

### Create a new Kedro config folder and catalog yaml
1. Navigate to project root directory
2. Create folder called `aws_batch` in `conf`
3. Copy the `catalog.yml` from `base` and paste into `aws_batch`
4. Within the copied `catalog.yml` edit the filepaths to point to the earlier created S3 bucket, replacing the data folder prefix with `s3://<bucket-name>/`





## References
https://kedro.readthedocs.io/en/latest/10_deployment/07_aws_batch.html