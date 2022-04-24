---
id: CPqidC2jdYCbcdTgTu6qq
title: Lambda
desc: ''
updated: 1650710609306
created: 1642238509411
---


Lambda is a serverless compute service for running code < 15 mins, on trigger.

## Steps
1. Package and upload code to Lambda function
2. Configure trigger for when want function to run

Charged only when Lambda function is running.

# Layers
https://www.youtube.com/watch?v=ebhcs-9FYJA_

Layers provided a shared space (or layer) where additional python modules etc can be shared across Lambdas.

A lambda can use up to five layers at a time. The total unzipped size of the function and all layers cannot exceed the unzipped **deployment** package size quota - 250 MB at time of writing, not to be confused with recent increase for **code** package to 10 GB. 

![](/assets/images/![](/assets/images/2022-04-23-10-47-39.png).png)

Layers can provide multiple use cases:
![](/assets/images/2022-04-23-11-20-44.png)


## Setting up
Must make a layers directory for module layer e.g. `lambda-layers/python/lib/python3.7/site-packages`

Can create customs packages here, or:

 `pip install <module-name> --target lambda-layers/python/lib/python3.7/site-packages`

Can also store reference data e.g. `lambda-layers/data/some-data.json`

Once installed or/and data added, need to zip folders, for reference in SAM template.yaml:

`zip -r my-lambda-layer.zip data python`

## Create lambda functions
To reference the modules, just call as normal. AWS will automatically pull these from defined path in the lambda deployment directory under the folder `opt`.

To call the reference data can use relative path `/opt/data/some-data.json`.

## Editing the template.yaml
Layers must be defined for each lambda, under properties:
```yaml
Properties:
    Other: path
    Stuff: etc
    Layers:
        - !Ref MyLambdaLayer
```
`!Ref` refers to the lambda layer definition:
```yaml
MyLambdaLayer:
    Type: AWS::Serverless::LayerVersion
    Properties:
        LayerName: MyLambdaLayer
        Description: What it contains
        ContentUri: lambda-layers/my-lambda-layer.zip
        CompatibleRuntimes:
            - python3.6
            - python3.7
        LicenceInfo: MIT
        RetentionPolicy: Retain  # can uss previous versions in lambda functions
```
Note: `ContentUri` is where path to layer zip file is specified.

To allow the layer to be used for any other lambda function in the future, can specify ARN in the template:
```yaml
Outputs:
    MyLambdaLayerARN:
        Value: !Ref MyLambdaLayer
        Description: MyLambdaLayer ARN
        Export:
            Name: my-lambda-layer-arn
```



















