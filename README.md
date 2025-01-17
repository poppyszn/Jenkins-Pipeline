# Jenkins Pipeline Repository with Artifact Upload

This repository contains Jenkins pipeline files for CI/CD workflows, including artifact management using Nexus. Each branch is tailored to specific needs, with configurations for building, testing, analyzing, and uploading artifacts.

## Features
- Automated code fetching, building, and testing
- SonarQube integration for code quality analysis
- Nexus artifact upload for versioned builds
- Slack notifications for build updates

## Branches
- **main**: Contains the default Jenkins pipeline files.
- **nexus-pipeline**: Jenkins pipeline configured for Nexus artifact upload.
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