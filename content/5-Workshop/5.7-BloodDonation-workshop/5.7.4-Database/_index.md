---
title: "Database Setup (RDS & Seeds)"
date: ""
weight: 4
chapter: false
pre: " <b> 5.7.4. </b> "
---

This section covers provisioning an Amazon RDS instance for the project and loading the provided SQL schema and seed data.

1. Create an RDS instance (MySQL or PostgreSQL as the project requires). Choose `db.t3.micro` (Free Tier eligible) for testing.

2. Configure networking: place RDS in private subnets within a VPC. Ensure security group allows inbound traffic from the application (Lambda security group or bastion host IP for manual access).

3. Initialize the database with schema and seed data:

```bash
# From repo root
aws s3 cp BloodDonationSupportSystem.sql s3://your-bucket/ || true
# (or run locally against RDS using mysql client)
mysql -h <rds-endpoint> -u <user> -p < BloodDonationSupportSystem.sql
mysql -h <rds-endpoint> -u <user> -p < initData.sql
```

4. For Lambda connectivity: ensure DB credentials are stored securely (AWS Secrets Manager or Parameter Store). Provide the Lambda function with permissions to read those secrets.

Validation: Connect with a MySQL/Postgres client and run a few SELECTs to confirm schema and seeded data present.

Notes

- Keep RDS in private subnets and use NAT for outbound connectivity if needed.
- Consider using RDS Proxy for serverless backends to manage connections.
