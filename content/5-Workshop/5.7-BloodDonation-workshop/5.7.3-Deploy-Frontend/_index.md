---
title: "Deploy Frontend (Amplify)"
date: ""
weight: 3
chapter: false
pre: " <b> 5.7.3. </b> "
---

The repository contains a frontend project that can be hosted with AWS Amplify or any static hosting (S3 + CloudFront). This section covers deploying with Amplify.

1. From the AWS Console, open AWS Amplify and choose "Get started" → "Host web app".
2. Connect the GitHub repository (`june4m/aws-blood_donation_cloud`) and choose the frontend directory (if present). Configure a build setting if Amplify cannot auto-detect the framework.
3. Alternatively, build locally and deploy to S3:

```bash
# build (example)
cd path/to/frontend
npm ci
npm run build

# sync build folder to S3
aws s3 sync build/ s3://your-frontend-bucket --delete
```

4. Configure CloudFront and custom domain as needed.

Validation: Open the Amplify URL or CloudFront distribution to verify the frontend loads and interacts with the backend API.
