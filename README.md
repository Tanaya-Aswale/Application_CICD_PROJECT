
# PIPELINE DIAGRAM

<img width="1133" alt="Screenshot 2024-09-10 at 4 37 36 PM" src="https://github.com/user-attachments/assets/29bba66c-2825-48bc-baec-09c1d7926844">


# ---------Continuous Integration (CI) Pipeline------------


# Pipeline Overview

 Agent: Runs in EC2 Jenkins agent.
 
 Tools: Configures JDK 17 and Maven 3 for the build.

<img width="1440" alt="jenkins master   agent" src="https://github.com/user-attachments/assets/19fb5611-3b67-4299-9837-9b9a9ddcfc8b">


# Environment Variables

1. APP_NAME: Name of the application.
2. RELEASE: Release version.
3. DOCKER_USER: Docker Hub username.
4. DOCKER_PASS: Docker Hub password.
5. IMAGE_NAME: Docker image name.
6. IMAGE_TAG: Docker image tag.
7. JENKINS_API_TOKEN: Jenkins API token for secure operations.
   
# Pipeline Stages

1. Clean Workspace: Cleans the workspace before each build.
2. Checkout: Checks out the source code from GitHub.
3. Build Application: Builds the application with Maven.
4. Test Application: Runs tests on the application.
5. SonarQube Analysis: Performs static code analysis.
6. Quality Gate: Checks SonarQube quality gate status.
7. Build & Push Docker Image: Builds and pushes the Docker image.
8. Trivy Scan: Scans the Docker image for vulnerabilities.
9. Cleanup Artifacts: Removes Docker images from the local system.
10. Trigger CD Pipeline: Triggers a Continuous Deployment pipeline.
    
# Post Actions

1. Success: Logs a success message.
2. Failure: Logs a failure message.
3. Always: Logs a completion message.

<img width="1248" alt="continuous integration" src="https://github.com/user-attachments/assets/647ffd62-1f13-4867-8da4-634d8c128c24">



# ----------Continuous Deployment (CD) Pipeline------------

# Pipeline Stages

1. Cleanup Workspace:
    * Ensures a fresh environment by cleaning up previous workspace files and artifacts.
2. Checkout from SCM:
    * Retrieves the latest code from the GitHub repository  using the main branch and specified credentials.
3. Update the Deployment Tags:
    * Updates the deployment.yaml file with the new application version or tag. The sed command is used to replace the old tag with the new one.
4. Push the Changed Deployment File to Git:
    * Configures Git with user details, commits the updated deployment.yaml file, and pushes the changes to the GitHub repository.
 
 <img width="1440" alt="continuous deployment" src="https://github.com/user-attachments/assets/9998f794-3fa2-4cd1-a055-d2376d434177">

# ArgoCD

<img width="1440" alt="APP DETAILS TREE #ArgoCD" src="https://github.com/user-attachments/assets/34db96ab-08e9-40c4-8377-8ce93fb6ad76">


# Application 

<img width="1440" alt="registration-app" src="https://github.com/user-attachments/assets/9d8f9ff5-39e4-4601-b882-452571a4cc0e">



