# End-to-End CI/CD Pipeline Using GitLab, Docker & Trivy

## Project Overview

This project demonstrates an automated CI/CD pipeline built using GitLab CI/CD, Docker, and Trivy.

The pipeline automates application build, testing, artifact management, caching, Docker image creation, container validation, image publishing, and security vulnerability scanning.

The objective is to understand how DevOps practices can be implemented to build, validate, publish, and scan container images through an automated pipeline.

## Technologies Used

- GitLab CI/CD
- Docker
- Docker-in-Docker (DinD)
- GitLab Container Registry
- Trivy Vulnerability Scanner
- YAML
- Linux Shell Scripting

## Pipeline Architecture

The pipeline consists of five stages:

1. **Build**
   - Creates the application build directory.
   - Generates a status file.
   - Stores the build output as a GitLab artifact.

2. **Test**
   - Validates that the build artifact exists.
   - Checks the application build output.

3. **Cache**
   - Demonstrates GitLab CI/CD cache functionality.
   - Reuses cached files
