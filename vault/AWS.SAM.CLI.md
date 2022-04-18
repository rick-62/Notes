---
id: t4uuedygp6wzp1vafh2rcwk
title: SAM CLI
desc: ''
updated: 1650275540058
created: 1650263694473
---

# Setup and common pipeline

```bash
# Check SAM version
sam --version

# Download a sample application
sam init

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
```






