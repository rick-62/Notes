---
id: tjqdepbkhzm2stivuramvnf
title: SAM Template
desc: ''
updated: 1651400400362
created: 1651391411885
---

#### Sources
* [Mastering the AWS Serverless Application Model (AWS SAM)](https://www.youtube.com/watch?v=QBBewrKR1qg)
* [AWS SAM Template Developer Guide](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-specification-resources-and-properties.html)


# Overview

Under the hood SAM templates are being converted to Cloudformation templates.

The SAM templates offer a much cleaner and readable alternative to creating Cloudformation templates directly.

# Sam Templates


## Serverless Resources
* AWS::Serverless::Function
* AWS::Serverless::Api
* AWS::Serverless::HttpApi
* AWS::Serverless::SimpleTable
* AWS::Serverless::LayerVersion
* AWS::Serverless::Application
* AWS::Serverless::StateMachine

### AWS::Serverless::Function
_Creates an AWS Lambda_

* A lot of events can trigger the lambda
* Policy can be selected here (or custom one created)

```yaml
# Example of policy for reading in a specified DynamoDB table
Policies:
    - DynamoDBReadPolicy:
        TableName: !Ref SampleTable
```

### AWS::Serverless::Api
_Creates REST API_

```yaml
# Example of creating API & using OpenAPI to define API
MyAPI:
    Type: AWS::Serverless::Api
    Properties:
        StageName: prod
        DefinitionUri: ./swagger.yml
```

### AWS::Serverless::HttpApi
_Supercharged REST API_

Allows more options and refinement, as well as being quicker etc.

```yaml
# Example of HTTP API
HttpApi:
    Type: AWS::Serverless::HttpApi
    Properties:
        CorsConfiguration:
            AllowMethods:
                - GET
                - POST
            AllowOrigins:
                - https://localhost:8080
```

### AWS::Serverless::SimpleTable
_Creates a DynamoDB table_

Can specify the Primary Key, capacity & managed encryption.

```yaml
# Example of simple DynamoDB table
MyTable:
    Type: AWS::Serverless::SimpleTable
```

```yaml
# Example of more complex DynamoDB table definition
MyTable:
    Type: AWS::Serverless::SimpleTable
    Properties:
        TableName: my-table
        PrimaryKey:
            Name: id
            Type: string
        ProvisionedThroughput:
            ReadCapacityUnits: 5
            WriteCapacityUnits: 5
        Tags:
            Department: Engineering
            AppType: Serverless
```

### AWS::Serverless::LayerVersion
_Creates Lambda Layer_

Note: can use makefile to build the layer, rather than doing so manually!

```yaml
MyLayer:
    Type: AWS::Serverless::LayerVersion
    Properties: 
        LayerName: python-resources
        Description: required third party modules for Python
        ContentUri: MyLambdaLayer/layer.zip
        CompatibleRuntimes:
            - Python3.6
        LicenseInfo: MIT
        RetentionPolicy: Retain
    Metadata:
        BuildMethod: python3.6 | makefile
```

### AWS::Serverless::Application
_Allows us to use a pre-built serverless application_

```yaml
MyApplication:
    Type: AWS::Serverless::Application
    Properties: 
        Location: https://s3.amasonaws.com/bucket/tmpl.yaml
```
            


### AWS::Serverless::StateMachine
_Creates AWS StepFunction_

```yaml
# Example of Step Function defintion
MySampleStateMachine:
    Type: AWS::Serverless::StateMachine
    Properties:
        DefinitionUri: sfn/MyStateMachine.asl.json
        Role: arn:aws:iam::role/service-role/MyRole
        DefinitionSubstitutions:
            MyFunctionArn: !GetAtt MyFunction.Arn
            MyDDBTable: !Ref TransactionTable   
```

## Globals
This is intended to add efficiency to building templates.

Define defaults across resources, by moving properties here which are repeated throughout.

## Customs functions and parameters
Can be used to create parametrised template.

### Pseudo parameters
Can be referenced from within SAM template:
- AWS::AccountId
- AWS::Region
- AWS::StackId
- AWS::StackName
- AWS::UrlSuffix
- etc...

### Intrinsic functions
- !GetAtt
- !Ref
- !Sub
- !Split
- !Join
- etc...

### Examples
```yaml
# Output endpoint for Amazon API Gateway
!Sub http://${ServerlessHttpApi}.execute-api.${AWS::Region}.amazonaws.com
```



