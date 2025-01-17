# Jenkins Pipeline Repository with ECS Deployment

This repository contains Jenkins pipeline files for automating CI/CD workflows, including Docker image management and ECS deployment. Each branch is tailored to specific configurations for building, testing, analyzing, and deploying applications.

## Features
- Automated code fetching, building, and testing
- SonarQube integration for code quality analysis
- Docker image building and registry upload
- Deployment to AWS ECS clusters
- Slack notifications for build and deployment updates

## Branches
- **main**: Contains the default Jenkins pipeline files.
- **ecs-deploy-pipeline**: Jenkins pipeline configured for AWS ECS deployments.
- **project-specific branches**: Branches for specific projects (e.g., `project-x`, `project-y`).

## How to Use
1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo-name.git
   ```
2. Switch to the desired branch:
   ```bash
   git checkout <branch-name>
   ```
3. Integrate the pipeline file into your Jenkins setup.