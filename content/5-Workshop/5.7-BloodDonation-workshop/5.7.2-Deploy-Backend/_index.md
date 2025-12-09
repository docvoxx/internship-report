---
title: "Deploy Backend (Lambda + API Gateway)"
date: ""
weight: 2
chapter: false
pre: " <b> 5.7.2. </b> "
---

This section shows two ways to deploy the backend service from the repository: (A) manual packaging and updating an existing Lambda, and (B) using the provided `buildspec.yml` with CodeBuild/CodePipeline.

A. Manual packaging and deploy (quick test)

1. Change to the backend directory and install dependencies:

```bash
cd aws-blood_donation_cloud/BloodDonationSupportSystemBE
npm ci
npm run build
```

2. Create a deployment package (zip) suitable for Lambda:

```bash
cd dist
npm install --production --ignore-scripts
zip -r ../deployment-package.zip .
cd ..
```

3. Create or update a Lambda function (example):

```bash
# create (one-time)
aws lambda create-function --function-name DaiVietBloodBackend \
  --runtime nodejs18.x --role arn:aws:iam::123456789012:role/your-lambda-role \
  --handler src/lambda.handler --zip-file fileb://deployment-package.zip

# update code (subsequent deployments)
aws lambda update-function-code --function-name DaiVietBloodBackend --zip-file fileb://deployment-package.zip
```

4. Configure environment variables and API Gateway mapping as required by the project (DB connection string, Cognito settings, etc.).

Validation: invoke the Lambda or call the API endpoint to ensure the function runs and returns expected responses.

B. CI/CD using CodeBuild & CodePipeline (recommended for repeatability)

1. Review `buildspec.yml` in the repo root — it contains the build steps used by CodeBuild to install, build and package the backend.

2. Create an S3 bucket for pipeline artifacts and a CodePipeline that uses GitHub as source (or GitHub Actions). Configure CodeBuild project to use the `buildspec.yml` file.

3. Ensure the CodeBuild service role has permissions to update Lambda and upload artifacts to S3.

Notes & Troubleshooting

- If Lambda fails on cold start or dependencies, check that native modules are built for Amazon Linux (build in a compatible environment or use a CodeBuild image).
- For database access from Lambda inside a VPC, ensure subnets and security groups allow outbound access to the RDS instance.

### CloudFormation Quickstart (minimal)

The following CloudFormation snippet provides a minimal starting point you can use as a template: it provisions a VPC with public/private subnets, a security group for Lambda <-> RDS access, an IAM role for Lambda with basic execution permissions, and a Lambda function resource which expects an S3-stored deployment package. Replace placeholder values (BucketName, Key, RoleArn) before use.

```yaml
AWSTemplateFormatVersion: '2010-09-09'
Description: Minimal resources for DaiVietBlood workshop (VPC, SG, Lambda role, Lambda)

Resources:
  VPC:
    Type: AWS::EC2::VPC
    Properties:
      CidrBlock: 10.0.0.0/16
      Tags:
        - Key: Name
          Value: DaiVietBlood-VPC

  PublicSubnet1:
    Type: AWS::EC2::Subnet
    Properties:
      VpcId: !Ref VPC
      CidrBlock: 10.0.1.0/24
      AvailabilityZone: !Select [0, !GetAZs ""]

  PrivateSubnet1:
    Type: AWS::EC2::Subnet
    Properties:
      VpcId: !Ref VPC
      CidrBlock: 10.0.2.0/24
      AvailabilityZone: !Select [0, !GetAZs ""]

  LambdaSecurityGroup:
    Type: AWS::EC2::SecurityGroup
    Properties:
      GroupDescription: Allow outbound to RDS
      VpcId: !Ref VPC

  LambdaExecutionRole:
    Type: AWS::IAM::Role
    Properties:
      AssumeRolePolicyDocument:
        Version: '2012-10-17'
        Statement:
          - Effect: Allow
            Principal:
              Service: lambda.amazonaws.com
            Action: sts:AssumeRole
      Path: /
      Policies:
        - PolicyName: LambdaBasicExecution
          PolicyDocument:
            Version: '2012-10-17'
            Statement:
              - Effect: Allow
                Action:
                  - logs:CreateLogGroup
                  - logs:CreateLogStream
                  - logs:PutLogEvents
                Resource: arn:aws:logs:*:*:*

  DaiVietBloodLambda:
    Type: AWS::Lambda::Function
    Properties:
      FunctionName: DaiVietBloodBackend
      Handler: src/lambda.handler
      Runtime: nodejs18.x
      Role: !GetAtt LambdaExecutionRole.Arn
      Code:
        S3Bucket: YOUR_DEPLOYMENT_BUCKET_NAME
        S3Key: deployment-package.zip
      VpcConfig:
        SecurityGroupIds:
          - !Ref LambdaSecurityGroup
        SubnetIds:
          - !Ref PrivateSubnet1

Outputs:
  LambdaArn:
    Value: !GetAtt DaiVietBloodLambda.Arn
    Description: ARN of the backend Lambda function

```

Use this template as a starting point; production deployments should use multiple AZ subnets, NAT gateways for outbound access, and finer-grained IAM policies.
