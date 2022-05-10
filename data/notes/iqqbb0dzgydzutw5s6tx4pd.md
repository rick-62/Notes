
# Overview
For storing global parameters and API keys.

This can be achieved by manually entering these on the AWS console, under Systems Manager (SSM) - Parameter Store.

## Retrieving parameters
```python
# create Systems Manager object
SSM = boto3.client('ssm')

# return JSON response with details of parameter
response = SSM.get_parameter(Name='slack-api', WithDecryption=True)

# extract value of parameter
value = response['Parameters']['Value']
```


