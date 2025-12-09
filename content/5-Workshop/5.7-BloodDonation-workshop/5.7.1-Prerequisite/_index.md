---
title: "Prerequisite"
date: ""
weight: 1
chapter: false
pre: " <b> 5.7.1. </b> "
---

### Prerequisites

Before starting, ensure you have the following prepared:

- An AWS account with permissions to create IAM roles, Lambda, API Gateway, RDS, S3, and Code* services.
- AWS CLI installed and configured (`aws configure`) with an IAM user that has sufficient privileges.
- Node.js (v16/18 recommended) and npm installed locally for building the backend.
- Git installed to clone the repository.
- A local workstation with `zip` available to package deployment artifacts.

Repository to clone:

```bash
git clone https://github.com/june4m/aws-blood_donation_cloud.git
cd aws-blood_donation_cloud
```

Key files in the repo used by this workshop:

- `BloodDonationSupportSystemBE/` - Backend Node.js project (packaging for Lambda)
- `BloodDonationSupportSystem.sql`, `initData.sql` - Database schema & seed data
- `buildspec.yml` - Reference CodeBuild pipeline used in CI/CD
- `BloodSupportSystem.md` - Project description and architecture notes

Security note: do not commit AWS credentials or DB passwords. Use Secrets Manager or environment variables for production.
