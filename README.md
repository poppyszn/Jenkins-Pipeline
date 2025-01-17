# Jenkins Pipeline Repository with ECS Deployment

This repository contains Jenkins pipeline files for automating CI/CD workflows, including Docker image management and ECS deployment. Each branch is tailored to specific configurations for building, testing, analyzing, and deploying applications.

## Features
- Automated code fetching, building, and testing
- SonarQube integration for code quality analysis
- Docker image building and registry upload
- Deployment to AWS ECS clusters
- Slack notifications for build and deployment updates

## How to Use
1. Clone the repository:
   ```bash
   git clone https://github.com/poppyszn/Jenkins-Pipeline.git
   ```
2. Switch to the desired branch:
   ```bash
   git checkout <branch-name>
   ```
3. Integrate the pipeline file into your Jenkins setup.
