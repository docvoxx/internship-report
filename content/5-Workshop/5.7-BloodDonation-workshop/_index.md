---
title: "DaiVietBlood - Workshop"
date: ""
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

#### Overview

This hands-on workshop guides you through deploying the DaiVietBlood (Blood Donation Support System) reference project available at `https://github.com/june4m/aws-blood_donation_cloud`.

The workshop is organized so you can follow a minimum-privilege, cost-aware path from cloning the repository to running a simple end-to-end demo. It covers account and environment setup, backend packaging and deployment to AWS Lambda, frontend hosting, provisioning an RDS database and loading seed data, and configuring CI/CD using CodeBuild/CodePipeline.

#### Architecture Highlights

- Backend: Node.js Lambda functions packaged and deployed using the repository's `buildspec.yml` (CodeBuild-friendly).
- Database: Relational schema provided (`BloodDonationSupportSystem.sql`, `initData.sql`) — intended for Amazon RDS (MySQL/Postgres).
- Frontend: Static app (can be hosted with AWS Amplify or S3 + CloudFront).
- CI/CD: Example `buildspec.yml` is included; CodePipeline/CodeBuild are recommended for reproducible builds and deployments.

![dai-viet-architecture](/images/5-Workshop/5.7-BloodDonation-workshop/diagram.png)

#### Workshop Content

1. [Workshop overview](./)
2. [Prerequisite](5.7.1-Prerequisite/)
3. [Deploy backend (Lambda + API Gateway)](5.7.2-Deploy-Backend/)
4. [Deploy frontend (Amplify / S3+CloudFront)](5.7.3-Deploy-Frontend/)
5. [Database setup (RDS & seeds)](5.7.4-Database/)
6. [CI/CD (CodePipeline / CodeBuild)](5.7.5-CICD/)
7. [Cleanup](5.7.6-Cleanup/)

---

Each section contains step-by-step instructions, example commands, and validation checks. If you want, I can expand any section with CloudFormation templates, IAM policy examples, or exact parameter values for your environment.
