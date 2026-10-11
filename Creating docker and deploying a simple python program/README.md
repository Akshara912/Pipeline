# AWS Project - CI/CD Pipeline

This project features a multi-stage GitLab CI/CD pipeline that automates container building, execution of a Python script using a custom container environment, and deployment of the resulting output to an AWS S3 bucket.

## 🚀 Pipeline Architecture

The pipeline consists of three sequential stages:

📋 Pipeline Stages Breakdown
## 1. docker_stage (.pre)
Purpose: Builds a custom Docker image and pushes it to the GitLab Container Registry.

Environment: Uses Docker-in-Docker (docker:dind).

Actions:

Logs into the GitLab Container Registry using CI variables ($CI_REGISTRY_USER, $CI_REGISTRY_PASSWORD).

Builds the Docker image from the local dockerfile.

Pushes the image to $CI_REGISTRY_IMAGE/dockerfile.

## 2. python_stage (build)
Purpose: Runs a Python script inside the newly built and published custom container environment.

Environment: Uses registry.gitlab.com/akshara912/aws_project/dockerfile.

Actions:

Creates a local python/ directory.

Executes add.py and pipes the output into python/output.txt.

Artifacts: Saves python/output.txt so it can be passed along to subsequent deployment stages.

## 3. aws_stage (deploy)
Purpose: Deploys the generated output file to an Amazon S3 bucket.

Environment: Uses the official amazon/aws-cli image.

Actions:

Verifies the AWS CLI version.

Copies python/output.txt to the target S3 bucket specified by $AWS_S3_BUCKET.

## ⚙️ Required CI/CD Variables

To make this pipeline run successfully, configure the following variables under your GitLab project settings (Settings > CI/CD > Variables):

## Variable Name	Description	Type

AWS_ACCESS_KEY_ID	Your AWS IAM access key with permissions to write to the S3 bucket.	

AWS_SECRET_ACCESS_KEY	Your AWS IAM secret access key.

AWS_DEFAULT_REGION	The AWS region where your S3 bucket resides (e.g., us-east-1).	

AWS_S3_BUCKET	The name of your target S3 bucket (e.g., my-project-output-bucket).	

(Note: GitLab automatically provides $CI_REGISTRY, $CI_REGISTRY_USER, $CI_REGISTRY_PASSWORD, and $CI_REGISTRY_IMAGE for the container registry stage.)
