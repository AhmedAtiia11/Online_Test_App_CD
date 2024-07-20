# Online-Test-App-CD-Continuous-Delivery

## Overview

This repository serves as the Continuous Delivery (CD) pipeline for the Online Test Application. The CD process automates the deployment of the application, ensuring a seamless and efficient release cycle using Jenkins, Docker, Kubernetes, and ArgoCD.

## Pipeline Steps

### Step 1: CI Trigger
The CD process is initiated automatically upon receiving a trigger from the associated Continuous Integration (CI) repository.

### Step 2: Application Deployment
The CD pipeline modifies the deployment configuration file, ensuring it reflects the latest version of the application image.

### Step 3: Repository Update
The CD repository on GitHub is updated with the latest changes, maintaining version control and transparency.

### Step 4: ArgoCD Deployment
ArgoCD is triggered automatically to deploy the application by running the `Application.yaml` file from this repository.

## How it Works

1. **Connection-Test-App-CD Jenkinsfile**:
   - Run `django_app_version_update` to update the `Django-deployment.yaml` file with the latest image version containing the last commit number.
   - Run `react_app_version_update` to update the `React-deployment.yaml` file with the latest image version containing the last commit number.
   - Push the updated deployment files to the GitHub repository (`Online_Test_App_CD`).

2. **ArgoCD Deployment**:
   - ArgoCD is triggered, deploying the application to the 'default' namespace.

3. **Accessing ArgoCD**:
   - To obtain the ArgoCD server IP:
     ```sh
     kubectl get pods -n argocd -o wide | grep argocd-server
     ```
   - Open the ArgoCD server in your browser using `Pod-IP:8080` (or the port specified in the pod definition file).
   - Username: `admin`
   - Password:
     ```sh
     kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath='{.data.password}' | base64 -d
     ```

4. **Application Creation**:
   - Create an application in ArgoCD using the `Application.yaml` file. This will ensure automatic deployments whenever the repository is updated.

5. **Accessing the Application**:
   - Once deployed, access the application at [http://localhost:30003/](http://localhost:30003/) to verify it is running online.

