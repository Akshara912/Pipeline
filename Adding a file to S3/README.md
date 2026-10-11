# GitLab CI/CD to AWS S3 Upload Pipeline

A lightweight GitLab CI/CD pipeline that automates building an HTML file and deploying it to an Amazon S3 bucket.

## 🚀 Overview

This repository uses a single GitLab CI/CD stage (`build`) running on the official `amazon/aws-cli` Docker image to:
1. Verify the AWS CLI environment and check connection permissions (`aws s3 ls`).
2. Generate a simple `index.html` file (`<h1>hello friends</h1>`).
3. Upload the file to your configured Amazon S3 bucket.

⚙️ Required CI/CD Variables
Make sure to add the following variables in your GitLab project under Settings > CI/CD > Variables:

AWS_S3_BUCKET: Target S3 bucket name.

AWS_ACCESS_KEY_ID: AWS IAM Access Key.

AWS_SECRET_ACCESS_KEY: AWS IAM Secret Key.

AWS_DEFAULT_REGION: AWS Region (e.g., us-east-1).
