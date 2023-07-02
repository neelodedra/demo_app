# React CI/CD Pipeline with Git Actions

Welcome to the Git repository for our React application's CI/CD pipeline! This pipeline is designed to automate the build and deployment process, allowing for quick and efficient deployments of our React application using Git Actions and an EC2 server hosting the application via Nginx.

## Overview

The CI/CD pipeline consists of two main stages: **build** and **deployment**. Here's how the pipeline works:

1. **Build Stage**: This stage is triggered whenever changes are pushed to the `main` branch of the repository. It performs the following steps:
   - Checks out the repository code.
   - Sets up Node.js and installs the required dependencies.
   - Builds the React app using the `npm run build` command.
   - Uploads the built artifacts to the Git Action pipeline using the `actions/upload-artifact` action.

2. **Deployment Stage**: This stage is triggered after the successful completion of the build stage. It performs the following steps:
   - Downloads the build artifacts from the previous stage using the `actions/download-artifact` action.
   - Lists the directories in the downloaded artifacts for debugging purposes.
   - Transfers the downloaded artifacts to the EC2 server using the `appleboy/scp-action`.
   - The transferred files are then deployed to the specified target location on the EC2 server.

## Prerequisites

Before running the CI/CD pipeline, ensure you have the following prerequisites in place:
- A Git repository containing the React source code.
- An EC2 server running Unix with Nginx installed.
- Access to the EC2 server via SSH using an SSH private key.

## Getting Started

To get started with the CI/CD pipeline, follow these steps:
1. Clone this repository to your local development environment.
2. Make any necessary modifications or customizations to the Git Action workflow file located at `.github/workflows/main.yml`.
3. Set up the required secrets and environment variables in your Git repository settings.
4. Push your changes to the `main` branch, and the CI/CD pipeline will automatically trigger.

## Continuous Integration and Deployment Benefits

By implementing this CI/CD pipeline, we gain several benefits:
- **Automated Builds**: The pipeline automatically builds the React application whenever changes are pushed to the `main` branch, ensuring that the latest code is always deployed.
- **Quick Deployments**: The pipeline allows for fast and efficient deployments, saving time and effort.
- **Consistent Deployments**: With the automated deployment process, we ensure that each deployment follows the same steps and configurations, reducing the chances of human error.
- **Easy Rollbacks**: In case of issues or bugs in a deployed version, the pipeline makes it easier to roll back to a previous version by simply specifying the desired version.

We hope you find this CI/CD pipeline useful and efficient for managing your React application deployments. Happy coding!

