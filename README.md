# Netfilx-Clone-APP-Continuous-Delivery

## Overview
This repository serves as the Continuous Delivery (CD) pipeline for the Nefilx Clone Application. The CD process automates the deployment of the application, ensuring a seamless and efficient release cycle.

# Pipeline Steps

### Step 1: CI Trigger
The CD process is initiated automatically upon receiving a trigger from the associated Continuous Integration (CI) repository.

### Step 2: Application Deployment
The CD pipeline modifies the deployment configuration file, ensuring it reflects the latest version of the application image.
### Step 3: Repository Update
The CD repository on GitHub is updated with the latest changes, maintaining version control and transparency.
### Step 4: ArgoCD Deployment
ArgoCD is triggered automatically to deploy the application by running the Application.yaml file from this repository.

# How it Works
## - Integration with CI:

The CD process seamlessly integrates with the CI repository, ensuring a streamlined flow from code commit to deployment.

## - Versioned Deployment:

The deployment configuration is automatically updated with the latest version of the application image, promoting version consistency.

## - GitHub Repository Update:

Changes made during the CD process are reflected in the GitHub repository, providing a clear history of deployments and changes.

## - ArgoCD Automation:

ArgoCD is leveraged for automated application deployment, allowing for declarative and GitOps-driven workflows.
           
     

