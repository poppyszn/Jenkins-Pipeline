# Jenkins Pipeline Repository

This repository contains Jenkins pipeline files for automating CI/CD workflows. Each branch corresponds to a specific project or use case, enabling streamlined management and scalability.

## Features
- Automated code fetching, building, and testing
- SonarQube integration for code quality analysis
- Docker image building and deployment
- Slack notifications for build updates

## Branches
- **main**: Contains the default Jenkins pipeline files.
- **docker-pipeline**: Jenkins pipeline for Docker-based workflows.
- **project-specific branches**: Branches for specific projects (e.g., `project-x`, `project-y`).

## How to Use
1. Clone the repository:
   ```bash
   git clone https://github.com/poppyszn.git
   ```
2. Switch to the desired branch:
   ```bash
   git checkout <branch-name>
   ```
3. Integrate the pipeline file into your Jenkins setup.

