# DevOps Intern Assignment

This repository contains the necessary files and instructions to deploy a Python Flask application that interacts with MongoDB on a Minikube Kubernetes cluster. The project demonstrates knowledge of Docker, Kubernetes, and related cloud-native technologies.

## Directory Structure

```
D:.
├───Docker
│   └───Dockerfile
│   └───README.md
├───docs
│   ├───Flask application and MongoDB Deployment on Minikube
│   └───How DNS resolution works within K8s cluster
│   └───Request_and_limit.txt
│   └───Design_choices.txt
│   └───Cookie_pointer.txt
├───Kubernetes
│   └──flask-deployment.yaml
│   └──flask-HPA.yaml
│   └──flask-service.yaml
│   └──mongodb-secrets.yaml
│   └──mongodb-service.yaml
│   └──mongodb-statefulset.yaml
├───src
│   └──app.py
│   └──requirements.txt
```

### 1. Docker

This directory contains the `Dockerfile` used to create the Docker image for the Flask application. It also includes instructions on how to build and push the Docker image to a container registry.

- **Dockerfile**:  A text file that contains a set of instructions for building a Docker image

### 2. docs

The `docs` directory includes detailed documentation related to the project:


- **How DNS resolution works within K8s cluster**: An explanation of how DNS resolution works within a Kubernetes cluster, facilitating inter-pod communication.

- **Request and limit**: An explanation of resource requests and limits in Kubernetes.

- **Design choices**: An explanation of the design choices made during this project, including the selection of specific configurations and alternatives considered

- **Cookie pointer**: Answers to the cookie pointer questions

### 3. Kubernetes

This directory contains the Kubernetes YAML files used to deploy the Flask application and MongoDB on the Minikube cluster.
It also includes instructions on Detailed steps to deploy the Flask application and MongoDB on a Minikube Kubernetes cluster, including the setup of services, Statefulset, autoscaling, and resource management.


### 4. src

The `src` directory contains the source code for the Flask application.

- **app.py**: The main application file that defines the Flask application and its interaction with MongoDB.
- **requirements.txt**: A file listing the Python dependencies required for the Flask application.

## Setup and Deployment

Follow these steps to deploy the Flask application and MongoDB on a Minikube Kubernetes cluster:

1. **Start Minikube**:
   ```bash
   minikube start
   ```

2. **Build Docker Image**:
   - Navigate to the `Docker` directory and build the Docker image using the provided `Dockerfile`.
   - Push the image to a container registry (optional, depending on your Minikube setup).

3. **Deploy the YAML files**:
    - Navigate to the `Kubernetes` directory and deploy the application and other configurations using the YAML files 
    ```bash
    kubectl apply -f .

6. **Access the Application**:
   - Use `minikube service` to access the Flask application and test the endpoints.
   ```bash 
   minikube service flask-service --url

---