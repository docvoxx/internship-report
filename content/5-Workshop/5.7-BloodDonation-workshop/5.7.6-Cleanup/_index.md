---
title: "Cleanup"
date: ""
weight: 6
chapter: false
pre: " <b> 5.7.6. </b> "
---

Follow these steps to remove resources created during the workshop and avoid unexpected charges.

1. Delete Lambda functions created for the workshop:

```bash
aws lambda delete-function --function-name DaiVietBloodBackend
```

2. Delete CodePipeline, CodeBuild projects and S3 artifact bucket.
3. Delete RDS instance (take a final snapshot if you need to keep data):

```bash
aws rds delete-db-instance --db-instance-identifier your-db --skip-final-snapshot
```

4. Remove Amplify app or S3 bucket hosting the frontend.
5. Revoke IAM roles created specifically for the workshop if no longer needed.

Always double-check resource names before deletion to avoid removing shared resources.
