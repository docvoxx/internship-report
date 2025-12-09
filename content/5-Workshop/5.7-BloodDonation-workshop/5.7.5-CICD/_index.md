---
title: "CI/CD (CodePipeline & CodeBuild)"
date: ""
weight: 5
chapter: false
pre: " <b> 5.7.5. </b> "
---

This section outlines how to set up CI/CD for the repo using AWS CodePipeline and CodeBuild. The repo includes a `buildspec.yml` that demonstrates install/build/package steps for the backend.

1. Create an S3 bucket for pipeline artifacts.
2. Create or connect a CodePipeline that uses GitHub (or CodeCommit) as the source.
3. Create a CodeBuild project and point it to the repo root (it will pick `buildspec.yml`). Use an image with Node.js 18.
4. Grant the CodeBuild role permissions to update Lambda (`lambda:UpdateFunctionCode`), upload artifacts to S3, and to other services used by the build steps.

Tip: Reuse the `buildspec.yml` found in the repository. Test the build locally by running the same commands in the `phases` section.

Validation: Push a test commit and verify the pipeline runs, builds artifacts and updates Lambda or uploads the deployment package to S3.

### IAM Policy Examples

Below are example IAM policy snippets to help you scope permissions for CodeBuild (CI role) and for Lambda (execution role). These are conservative examples — adjust resource ARNs and limits to fit your account.

CodeBuild service role example (minimal permissions to build, upload artifacts, and update Lambda):

```json
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Effect": "Allow",
			"Action": [
				"s3:GetObject",
				"s3:PutObject",
				"s3:GetObjectVersion",
				"s3:ListBucket"
			],
			"Resource": [
				"arn:aws:s3:::YOUR_ARTIFACT_BUCKET",
				"arn:aws:s3:::YOUR_ARTIFACT_BUCKET/*"
			]
		},
		{
			"Effect": "Allow",
			"Action": [
				"lambda:UpdateFunctionCode",
				"lambda:UpdateFunctionConfiguration",
				"lambda:PublishVersion"
			],
			"Resource": "arn:aws:lambda:REGION:ACCOUNT_ID:function:DaiVietBloodBackend"
		},
		{
			"Effect": "Allow",
			"Action": [
				"logs:CreateLogGroup",
				"logs:CreateLogStream",
				"logs:PutLogEvents"
			],
			"Resource": "arn:aws:logs:*:*:*"
		}
	]
}
```

Lambda execution role example (allowing access to Secrets Manager and RDS connectivity):

```json
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Effect": "Allow",
			"Action": [
				"secretsmanager:GetSecretValue",
				"ssm:GetParameter",
				"ssm:GetParameters"
			],
			"Resource": "arn:aws:secretsmanager:REGION:ACCOUNT_ID:secret:YOUR_SECRET_NAME*"
		},
		{
			"Effect": "Allow",
			"Action": [
				"rds-db:connect"
			],
			"Resource": "arn:aws:rds-db:REGION:ACCOUNT_ID:dbuser:DBRESOURCE/YOUR_DB_USER"
		},
		{
			"Effect": "Allow",
			"Action": [
				"logs:CreateLogGroup",
				"logs:CreateLogStream",
				"logs:PutLogEvents"
			],
			"Resource": "arn:aws:logs:*:*:*"
		}
	]
}
```

Replace `REGION`, `ACCOUNT_ID`, `YOUR_ARTIFACT_BUCKET`, and other placeholders with your actual values. Prefer least privilege (narrow resource ARNs) in production.
