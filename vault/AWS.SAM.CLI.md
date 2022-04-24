---
id: t4uuedygp6wzp1vafh2rcwk
title: SAM CLI
desc: ''
updated: 1650780024392
created: 1650263694473
---

# Setup and common pipeline

```bash
# Check SAM version
sam --version

# Download a sample application
sam init

# Specify runtime & name
sam init --runtime python3.7 --name sam-app

# Bootstrap a CI/CD pipeline
sam pipeline init --bootstrap

# Build your application (from application root folder)
sam build

# Deploy application (guided arg for first time)
sam deploy --guided

# Validate template.yaml configuration file
sam validate

# Delete stack ( AWS CLI)
aws cloudformation delete-stack --stack-name sam-app --region region
```

# Local testing

```bash
# Host API locally
sam local start-api

# Send API request
curl http://127.0.0.1:3000/hello

# Invoke Lambda function directly
sam local invoke "HelloWorldFunction" -e events/event.json

# Test API gateway
sam local generate-event apigateway aws-proxy --body "" --path "hello" --method GET > api-event.json

# Create an API output & copy to clipboard
sam local generate-event apigateway aws-proxy | clip
```






