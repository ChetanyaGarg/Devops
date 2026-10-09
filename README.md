# Flask DevOps Project 🚀

A hands-on DevOps project demonstrating how to containerize a Flask application, automate testing and image builds using Jenkins, publish Docker images to Docker Hub, and deploy the application to Kubernetes using Minikube.

This project helped me practice the core DevOps workflow, from source code management to containerization, CI/CD automation, application deployment, and infrastructure management.

## 🛠️ Tech Stack

- **Programming:** Python, Flask
- **Version Control:** Git, GitHub
- **CI/CD:** Jenkins
- **Containerization:** Docker
- **Container Registry:** Docker Hub
- **Container Orchestration:** Kubernetes, Minikube
- **Infrastructure as Code:** Terraform
- **Web Server / Reverse Proxy:** Nginx (previous project experience)
- **Operating System:** Debian Linux

## 📁 Project Structure

The main application repository contains the following files and configurations:

```text
Devops/
├── app.py
├── test_app.py
├── requirements.txt
├── Dockerfile
├── Jenkinsfile
├── Deployment.yaml
└── Service.yaml
```

### File Overview

| File | Purpose |
|---|---|
| `app.py` | Flask application and HTTP endpoints |
| `test_app.py` | Automated tests for the Flask application |
| `requirements.txt` | Python dependencies |
| `Dockerfile` | Instructions for building the Docker image |
| `Jenkinsfile` | Defines the CI/CD pipeline |
| `Deployment.yaml` | Kubernetes Deployment configuration |
| `Service.yaml` | Kubernetes Service configuration |

## 1. Flask Application

Created a Flask application that runs inside a container and provides HTTP endpoints.

The application includes a main route and a health-check endpoint. Additional application endpoints, such as `/info` and `/metrics`, were also explored in the project workflow.

The health-check endpoint helps verify that the application responds successfully.

## 2. Docker Containerization

Created a Dockerfile to package the Flask application and its dependencies into a Docker image.

Practiced:

- Building Docker images.
- Running containers.
- Mapping host ports to container ports.
- Inspecting and managing containers.
- Tagging images with version numbers.
- Publishing images to Docker Hub.

**Docker Hub repository:** `chetanyagarg/flask_server`

Example image references:

```text
chetanyagarg/flask_server:latest
chetanyagarg/flask_server:15
```

Versioned image tags help identify which application build is being used.

## 3. Jenkins CI/CD Pipeline

Configured Jenkins to automate the application workflow using a `Jenkinsfile`.

The pipeline was developed around these stages:

1. **Checkout:** Retrieve source code from GitHub.
2. **Install Dependencies:** Install the Python dependencies in a virtual environment.
3. **Test:** Run automated tests using `pytest`.
4. **Build Docker Image:** Build a Docker image for the Flask application.
5. **Container Test:** Practice validating the containerized application.
6. **Push Image:** Authenticate with Docker Hub using Jenkins credentials and publish versioned images.
7. **Deploy:** Practice deployment-related automation using Docker and Kubernetes.
8. **Verify:** Check application deployment and rollout status.

The pipeline was developed incrementally, with practical work on Jenkins credentials, GitHub webhook triggers, Docker access from the Jenkins container, and pipeline troubleshooting.

## 4. GitHub Integration

Connected the GitHub repository to Jenkins to automate pipeline execution when code changes are pushed.

Practiced:

- Cloning the repository in Jenkins.
- Configuring GitHub webhook notifications.
- Understanding the `checkout scm` pipeline step.
- Configuring the GitHub hook trigger for Git SCM polling.
- Understanding the difference between webhook notifications and Jenkins polling.

## 5. Docker Hub Integration

Configured Jenkins credentials for Docker Hub authentication and practiced publishing versioned Docker images.

The image repository used in this project is:

`chetanyagarg/flask_server`

This makes the application image available for deployment on environments that can access the registry.

## 6. Kubernetes Deployment with Minikube

Created Kubernetes manifests to deploy the Flask application to a local Minikube cluster.

### Deployment

The Deployment manages application Pods and helps maintain the desired number of replicas.

Practiced:

- Creating and applying a Deployment.
- Using labels and selectors.
- Inspecting Pods and Deployment status.
- Understanding replicas and self-healing.
- Exploring scaling, rolling updates, and rollbacks.

### Service

Created a Kubernetes Service to provide a stable network endpoint for the application.

Practiced:

- Connecting a Service to Pods using labels and selectors.
- Configuring ports and target ports.
- Exposing the application using NodePort.
- Accessing the application through Minikube.

The existing Kubernetes lab included a `flask-deployment` Deployment and its associated Service.

## 7. Terraform Experiments

Used Terraform separately to explore Infrastructure as Code and manage resources in Docker and Kubernetes.

### Terraform with Docker

Practiced defining Docker resources through Terraform configuration files, including:

- Docker provider configuration.
- Docker image resources.
- Docker container resources.
- Variables, outputs, locals, and dependencies.
- Terraform state and lifecycle behavior.
- `terraform init`, `terraform plan`, `terraform apply`, and state inspection.

### Terraform with Kubernetes

Configured the Kubernetes provider to connect Terraform to Minikube.

Successfully created a namespace and deployed the Flask application using Terraform.

**Verified result:** The `flask-app` Deployment reached `2/2` ready replicas in the `terraform-lab` namespace, with both Pods in the `Running` state.

This Terraform experiment was maintained separately from the original application repository.

## 🔄 DevOps Workflow

The project brings together the following workflow:

```text
        Developer
            |
            v
      GitHub Repository
            |
            v
      Jenkins Pipeline
            |
            v
     Install Dependencies
            |
            v
      Automated Testing
            |
            v
     Build Docker Image
            |
            v
       Docker Hub
            |
            v
  Kubernetes / Minikube
            |
            v
    Running Application
```

Jenkins automates the pipeline stages, Docker packages the application, Docker Hub stores the images, and Kubernetes runs and manages the application containers.

The pipeline was built and tested incrementally; not every stage was fully automated end to end in a single final pipeline.

## 📚 Key Learnings

Through this project, I gained practical exposure to:

- Linux-based development and troubleshooting.
- Git and GitHub source control.
- Docker images, containers, ports, and registries.
- Jenkins pipelines and CI/CD concepts.
- Automated Python testing with `pytest`.
- Jenkins credentials and GitHub webhooks.
- Kubernetes Deployments, Pods, Services, and namespaces.
- Terraform providers, resources, variables, outputs, and state.
- Application deployment and basic troubleshooting.

## 🚧 Future Improvements

- Complete and validate an end-to-end Jenkins pipeline.
- Improve image versioning and deployment automation.
- Integrate Terraform more cleanly into the project workflow.
- Add application monitoring using Prometheus and Grafana.
- Improve container security and configuration management.
- Add clearer documentation and screenshots of successful runs.


