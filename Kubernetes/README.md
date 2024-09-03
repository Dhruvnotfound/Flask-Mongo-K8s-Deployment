# Flask Application with MongoDB on Minikube

This repository contains a Flask application that interacts with a MongoDB database. The instructions below will guide you through deploying both the Flask application and MongoDB on a Minikube Kubernetes cluster.

### Prerequisites

- [Minikube](https://minikube.sigs.k8s.io/docs/start/) installed
- [Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) installed
- Docker installed and configured to work with Minikube
- A Dockerfile for the Flask application
- Kubernetes YAML configuration files for the deployment and services

---

### Step 1: Start Minikube

   ```bash
   minikube start
   ```
### Step 2: Build Docker Images

1. Navigate to your project directory:

```bash
    cd Docker/
```
2. Build the Docker image for the Flask application:
    ```bash
    docker build -t flask-app:latest .

3. Pull the MongoDB image:

    ```bash
    docker pull mongo:latest

### Step 3: Edit the Image Field in the Kubernetes deployment file

1. Locate the `flask-deployment.yaml` file in the `kubernetes` directory
2. Edit the `spec.template.spec.image` Field as shown below

    ```bash 
    apiVersion: apps/v1
    kind: Deployment
    metadata:
        name: flask-app
    spec:
        replicas: 2
        selector:
            matchLabels:
                app: flask-app
            template:
                metadata:
                    labels:
                        app: flask-app
                spec:
                    containers:
                    - name: flask-app
                      image: dhruvnotfound/flask-app:v1  # your docker image here
                      ports:
                      - containerPort: 5000
            .....
    ```

### Step 4: Deploy the Flask Application and MongoDB on Minikube 

1. Move to the `kubernetes` directory
    ```bash
    cd kubernetes/
    ```

2. Apply the Deployment YAML Files
- Navigate to the folder containing your YAML files 
    ```bash 
    cd kubernetes
    ```
- Apply the YAML Files
    ```bash
    kubectl apply -f .
    ```
### Step 5: Verify Deployments
Check the status of your pods to ensure they are running:
```bash
    kubectl get pods
```

### Step 6: Access the Flask Application
To access your Flask application, use the following command:
```bash
minikube service flask-service --url
```
This command will open your default web browser to the URL where your Flask application is running.

### Step 6: Clean Up
To delete the entire setup, run:
```bash 
kubectl delete all --all -n default
```
When you are done, you can delete the Minikube cluster:
```bash
minikube delete
```
---
Using this you have successfully deployed a Flask application with a MongoDB backend on a Minikube Kubernetes cluster