# NGINX Website Deployment with Kubernetes

## Project Overview

This project demonstrates how to deploy a custom static website using NGINX and Kubernetes. The project runs locally using Minikube and Docker, without requiring cloud infrastructure.

The website's HTML content is stored in a Kubernetes ConfigMap and mounted into the NGINX containers.

## Architecture

The project uses the following components:

- **Docker:** Runs the local Kubernetes environment through Minikube.
- **Minikube:** Provides a local Kubernetes cluster.
- **Kubernetes Deployment:** Manages three NGINX replicas.
- **Kubernetes Pods:** Run the NGINX containers.
- **Kubernetes Service:** Exposes the website through a NodePort service.
- **ConfigMap:** Stores the custom HTML website.
- **Readiness and Liveness Probes:** Check application health.
- **Resource Requests and Limits:** Define CPU and memory requirements for each container.

## Project Structure

```text
kubernetes-nginx-project/
├── manifests/
│   ├── deployment.yaml
│   ├── service.yaml
│   └── configmap.yaml
├── screenshots/
│   └── kubernetes-website.png
└── README.md
```

## Features Implemented

- Created a local Kubernetes cluster using Minikube.
- Deployed NGINX using a Kubernetes Deployment.
- Configured three replicas.
- Exposed the application using a NodePort Service.
- Created a ConfigMap for custom HTML content.
- Mounted the ConfigMap into the NGINX containers.
- Configured readiness and liveness probes.
- Set container CPU and memory requests and limits.
- Scaled the Deployment and verified its rollout.
- Accessed the custom website in a browser.

## Prerequisites

- Docker Desktop
- Minikube
- kubectl
- Windows PowerShell

## Deployment Instructions

### 1. Start Minikube

```powershell
minikube start --driver=docker
```

### 2. Navigate to the project directory

```powershell
cd C:\Users\ADMIN\kubernetes-nginx-project
```

### 3. Create the ConfigMap

```powershell
kubectl apply -f manifests\configmap.yaml
```

### 4. Deploy NGINX

```powershell
kubectl apply -f manifests\deployment.yaml
```

### 5. Expose the application

```powershell
kubectl apply -f manifests\service.yaml
```

### 6. Verify the Deployment

```powershell
kubectl get deployments
kubectl get pods
kubectl get services
kubectl rollout status deployment/nginx-deployment
```

### 7. Access the website

```powershell
minikube service nginx-service --url
```

Open the URL printed by Minikube in a browser. Keep the terminal running if Minikube maintains a local tunnel.

## Scaling the Application

Scale the Deployment to three replicas:

```powershell
kubectl scale deployment nginx-deployment --replicas=3
kubectl get deployments
kubectl get pods
```

## Screenshot

The `screenshots/` directory contains a screenshot of the custom website running through the local Kubernetes environment.

## Cleanup

When finished working, stop the local Minikube cluster:

```powershell
minikube stop
```

To delete this project's Kubernetes resources while retaining the Minikube cluster, run:

```powershell
kubectl delete -f manifests\deployment.yaml
kubectl delete -f manifests\service.yaml
kubectl delete -f manifests\configmap.yaml
```

**Note:** These commands delete the Kubernetes resources defined in this project. They do not delete your project files or GitHub repository.

## Learning Outcomes

This project provided hands-on experience with Kubernetes Deployments, Pods, Services, ConfigMaps, health probes, resource management, scaling, and rollout verification.

## Technologies Used

Kubernetes | Minikube | Docker | NGINX | YAML | HTML | GitHub

## Environment

This project was developed and tested locally using Minikube and Docker. No AWS resources are required.
