# Deployment Documentation
---

# Overview

This document describes the deployment architecture, CI/CD automation, infrastructure orchestration, runtime environment, monitoring integrations, and deployment workflows used by the Event-Driven EdTech Learning Platform.

The platform is deployed on AWS EC2 using Docker Compose multi-container orchestration, Nginx reverse proxying, HTTPS termination, Jenkins CI/CD pipelines, and Ansible deployment automation.

---

# Deployment Architecture

## Runtime Environment

The application is deployed as a multi-container Docker Compose stack running on AWS EC2.

Containers include:

- Frontend
- Backend
- Worker
- Redis
- Nginx Reverse Proxy

![Docker Runtime](../assets/deployment/docker_containers_all.png)

---

## Live Deployment

- https://edtech.aavishkar.online

![Live Deployment](../assets/deployment/live-app.png)

---

# Deployment Workflow

![CI/CD Workflow](../assets/architecture/cicd-flow.svg)

---

## Deployment Flow

```text
Developer Push
      ↓
GitHub Webhook
      ↓
Jenkins Pipeline
      ↓
Docker Image Build
      ↓
DockerHub Push
      ↓
Infrastructure Deployment Trigger
      ↓
Ansible Playbook
      ↓
AWS EC2 Deployment
```

---

# Jenkins Pipeline Ecosystem

The platform uses multiple Jenkins pipelines for frontend, backend, worker, infrastructure deployment, and AWS-native migration workflows.

These pipelines automate:

- Docker image builds
- DockerHub image pushes
- Infrastructure deployment orchestration
- Branch-aware deployments
- AWS-native migration deployments

![Jenkins Dashboard](../assets/jenkins/jenkins-dashboard.png)

---

# Frontend CI/CD Pipeline

The frontend pipeline automates:

- Docker image build
- Build-time environment variable injection
- DockerHub image push
- Deployment pipeline trigger

![Frontend Pipeline](../assets/jenkins/frontend-pipeline.png)

---

# Backend CI/CD Pipeline

The backend pipeline automates:

- Backend Docker image build
- DockerHub image push
- Infrastructure deployment trigger

![Backend Pipeline](../assets/jenkins/backend-pipeline.png)

---

# Infrastructure Deployment Pipeline

The infrastructure deployment pipeline automates:

- Runtime secret generation
- Ansible deployment execution
- Latest image pull
- Container restart orchestration

![Infra Pipeline](../assets/jenkins/infra-pipeline.png)

---

# Ansible Responsibilities

Ansible automates:

- Deployment orchestration
- Runtime secret management
- Container updates
- Docker Compose deployment
- Environment configuration

---

# Monitoring and Alerting

CloudWatch alarms and Amazon SNS notifications were integrated to monitor asynchronous Lambda traffic and operational activity.

Implemented monitoring features include:

- Lambda invocation monitoring
- CloudWatch metric alarms
- Amazon SNS email notifications
- Event-processing visibility
- Traffic threshold alerting

These integrations demonstrate operational monitoring practices for cloud-native asynchronous systems.

---

# HTTPS and Networking

Configured:

- Custom domain integration
- SSL certificate setup
- Nginx reverse proxy
- Elastic IP routing
- HTTPS enforcement

---

# Branch-Based Deployment Strategy

## Main Branch

Uses:

- BullMQ
- Redis
- Worker-based async processing

Deployment stack:

- Frontend
- Backend
- Worker
- Redis

---

## sqs-lambda-migration Branch

Uses:

- Amazon SQS
- AWS Lambda
- Serverless event processing

Deployment stack:

- Frontend
- Backend
- AWS-managed event processing

---

# Environment Variables

## Example Configuration

```env
PORT=5000
MONGODB_URL=
JWT_SECRET=
AWS_REGION=
SQS_QUEUE_URL=
```

---

# Local Setup

## Clone Repository

```bash
git clone <repo-url>
cd <repo-name>
```

---

## Run Containers

```bash
docker compose up --build
```

---

# Access Application

## Frontend

```text
http://localhost
```

---

## Backend

```text
http://localhost:5000
```
