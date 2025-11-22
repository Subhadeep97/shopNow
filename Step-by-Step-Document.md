## 1. Clone Project Repositories 
Access the Project:

Open VS Code and use the integrated terminal (use PowerShell or WSL/Ubuntu on Windows).

Run:

bash
git clone https://github.com/mohanDevOps-arch/shopNow.git
cd shopNow

Explore the folders to distinguish between frontend (FE) and backend (BE) codebases.

## 2.Write Kubernetes Deployment Manifests
Backend Deployment:

Create a folder: k8s inside your backend codebase.

Add backend-deployment.yaml with a Deployment resource specifying a Docker image, port, replica count, and resource limits.

Add backend-service.yaml with a Service resource (type ClusterIP or NodePort) exposing backend container.

Document any environment variables needed (MongoDB connection, etc.).


## 3.Frontend Deployment:

Repeat above steps for FE: frontend-deployment.yaml and frontend-service.yaml inside the frontend codebase.

Ensure FE service targets correct backend service URL (Cluster DNS or environment variable).

## 4.MongoDB Deployment:

Create mongo-deployment.yaml and mongo-service.yaml.

Decide whether to use a persistent volume for MongoDB (data durability).


## 5.Create HELM Chart

Helm Chart Structure:

At project root, run:

Clean up boilerplate: keep only essential templates for FE, BE, MongoDB deployments and services.

Move or rewrite your YAML manifests into mern-chart/templates/ and use Helm templating ({{ }}) for image tags, ports, replica counts, and environment variables, making them configurable via values.yaml

Helm Chart Values:

Edit mern-chart/values.yaml to provide default image names, replica counts, service ports, etc. Document configurable parameters.

## 6.Jenkins Pipeline Automation
Pipeline Script (Groovy):

Write a Jenkinsfile at the project root.

Key pipeline steps:

Checkout code 

Build frontend and backend Docker images (with tagging)

Push images to container registry (Docker Hub/AWS ECR)

Deploy/update application in Kubernetes using Helm

--This is overview of the steps which can taken in the oderly way,but the actual steps may vary--