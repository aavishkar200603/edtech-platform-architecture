# Event-Driven EdTech Platform with CI/CD and Cloud-Native Architecture

## Live Demo

- https://edtech.aavishkar.online

![Live Application](assets/deployment/live-app.png)

---

# Overview

Production-style event-driven EdTech platform that demonstrates architectural evolution from self-managed asynchronous worker infrastructure toward AWS-managed cloud-native event processing systems.

Version 1 implements BullMQ + Redis + dedicated workers for asynchronous processing.

Version 2 migrates asynchronous workloads to Amazon SQS and AWS Lambda to demonstrate serverless event-driven architecture patterns and reduced operational overhead.


---

# Key Highlights

- Dockerized frontend and backend services
- Jenkins-based CI/CD pipelines
- Ansible deployment orchestration
- Event-driven analytics processing
- BullMQ + Redis background workers
- AWS SQS + Lambda migration architecture
- HTTPS with custom domain
- CloudWatch + SNS operational alerting
- Serverless analytics aggregation pipeline
- Branch-aware deployments
- Multi-repository DevOps workflows

---

# Tech Stack

## Backend & Frontend
- React.js
- Node.js
- Express.js
- MongoDB

## DevOps
- Docker
- Docker Compose
- Jenkins
- Ansible
- Nginx

## AWS
- EC2
- IAM
- SQS
- Lambda
- CloudWatch
- S3
- SNS

## Async Processing
- BullMQ
- Redis

---

# System Architecture

## Self-Managed Event Architecture

![Self Managed Architecture](assets/architecture/self-managed-architecture.svg)

---

## AWS-Native Event Architecture

![AWS-Native Architecture](assets/architecture/aws-native-architecture.svg)

---

# CI/CD Workflow

![CI/CD Architecture](assets/architecture/cicd-flow.svg)

---
# Repository Ecosystem

| Repository | Purpose | Access |
|------------|----------|---------|
| [Frontend Repository](https://github.com/aavishkar200603/edtech-frontend) | React frontend, Nginx reverse proxy, HTTPS setup | Available on request |
| [Backend Repository](https://github.com/aavishkar200603/edtech-backend) | Node.js APIs, analytics processing, SQS integration | Available on request |
| [Worker Repository](https://github.com/aavishkar200603/edtech-worker) | BullMQ workers, retries, async processing | Available on request |
| [Infrastructure Repository](https://github.com/aavishkar200603/edtech-infra) | Docker Compose, Jenkins pipelines, and Ansible deployment orchestration | Available on request |
| [Lambda Repository](https://github.com/aavishkar200603/edtech-lambda) | AWS Lambda consumers for serverless event processing integrated with Amazon SQS and CloudWatch | Available on request |

---

# Repository Access

Some repositories remain private because they contain infrastructure automation and deployment configurations.

Access can be provided upon request for technical review or interview discussions.

---

# Documentation

- [Architecture Documentation](docs/ARCHITECTURE.md)
- [Deployment Documentation](docs/DEPLOYMENT.md)
- [Migration Documentation](docs/MIGRATION.md)

---

# Author

Aavishkar Pawar

- LinkedIn: https://www.linkedin.com/in/aavishkarpawar/
- GitHub: https://github.com/aavishkar200603