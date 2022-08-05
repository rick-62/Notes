
# Deploy kedro to batch (simple version)
This deployment guide will outline the instructions for uploading a Kedro project to AWS Batch. This is for the main intention of allowing us to trigger running the project automatically using AWS Eventbridge, and output the results to an S3 bucket which can be accessed directly online.

Note: assumes AWS account has been setup and configured

### Future improvements
- Use CDK/CLI to automate build of the AWS stack
- Pass AWS parameters for better flexibility and separation of dependency
- Run individual nodes on separate batch jobs
- Improve public access policy for S3 bucket
- Migrate to AWS serverless (step functions & lambda)

## Create a new S3 bucket in AWS
1. Navigate to S3 Management Console in AWS
2. Click **Create bucket** 
3. Name the bucket, adhering to [bucket naming guidance](https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucketnamingrules.html)
4. Ensure the region selected is correct for the project
5. Uncheck **Block all public access** so individual files can be exposed to the internet
6. Leave the remaining settings as default and click **Create bucket**

## Create a new Kedro config folder and catalog yaml
1. Navigate to project root directory
2. Create folder called `aws_batch` in `conf`
3. Copy the `catalog.yml` from `base` and paste into `aws_batch`
4. Within the copied `catalog.yml` edit the filepaths to point to the earlier created S3 bucket, replacing the data folder prefix with `s3://<bucket-name>/`

## Ensure requirements.txt is up to date
1. Ensure `src/requirements.txt` contains all the required packages (and correct versions) to run the project locally
2. Can rebuild new virtual environment to test this is the case
3. Finally add `s3fs>=0.3.0,<0.5` to requirements for reading/saving to S3 bucket

## Create Docker container
1. Ensure Docker Daemon is running
2. Install **kedro-docker** using `pip install kedro-docker`
3. run `kedro docker init` to create required files
4. run `kedro docker build ` (note: repo name must be lowercase)

## Push Docker image to repo (in this case AWS ECR)
1. Set up the repo in AWS ECR, giving the repo a sensible name _e.g. investing-batch_
2. From command line on local machine run: `docker tag <local-repo-name>:latest <AWS-account-ID>.dkr.ecr.<region>.amazonaws.com/<aws-repo-name>:latest`
3. Login to AWS on local machine by running: `aws ecr get-login-password --region <region> | docker login --username AWS --password-stdin <AWS-account-ID>.dkr.ecr.<region>.amazonaws.com`
4. Push the docker image to ECR: `docker push <AWS-account-ID>.dkr.ecr.<region>.amazonaws.com/<aws-repo-name>:latest`

## Setup AWS Batch
1. Create IAM role so Batch can share information with ECR and S3 [similar to this](https://aws.amazon.com/blogs/compute/creating-a-simple-fetch-and-run-aws-batch-job/)
2. `Create job Definition` providing an appropriate name, assign the created IAM role, set command field to `kedro run --env aws_batch` and edit execution time etc accordingly, leaving most defaults as is
3. `Create compute environment` providing an appropriate name and choosing Fargate 
4. `Create job queue` providing an appropriate name, the compute environment and setting the priority
5. Submit a new job to test it is working as intended

## Setup scheduling
1. Navigate to AWS EventBridge
2. Click `Rules` > `Create rule` and provide an appropriate name
3. Select trigger type under `Define pattern` select either `Event` or `Schedule` driven
4. Select `Batch job queue` under `Target` and fill in ARNs for Batch components
5. Click `Create` to complete rule

## Accessing the output data
1. Navigate to S3 bucket
2. Select data or output would like to access publicly
3. Select `Actions` > `Make public using ACL`
4. Output data can now be accessed any time using S3 URL

## References
https://kedro.readthedocs.io/en/latest/10_deployment/07_aws_batch.html
https://aws.amazon.com/blogs/compute/creating-a-simple-fetch-and-run-aws-batch-job/
https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucketnamingrules.html
