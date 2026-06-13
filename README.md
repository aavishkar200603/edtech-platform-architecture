# Event-Driven EdTech Learning Platform

## Live Demo

- https://edtech.aavishkar.online

![Live Application](assets/deployment/live-app.png)

Features demonstrated:

- Course browsing and enrollment
- Instructor course management
- Video learning experience
- Progress tracking
- Ratings and reviews
- Analytics generation

---

# Overview

Full-stack EdTech learning platform built using React.js, Node.js, MongoDB, Redis, BullMQ, and Nginx.

The platform enables instructors to publish courses and learners to consume educational content through course catalogs, video learning experiences, progress tracking, ratings, and analytics-driven insights.

The project demonstrates event-driven architecture patterns through both self-managed asynchronous processing using BullMQ and Redis as well as AWS-native event processing using Amazon SQS and AWS Lambda.

---

# Application Features

- Course creation and publishing
- Instructor dashboards
- Student enrollment workflows
- Video course consumption
- Progress tracking
- Course ratings and reviews
- Analytics event collection
- Background analytics processing
- Responsive React.js user interface
- JWT authentication and authorization

---

# Key Highlights

## Application Engineering

- Course management workflows
- Course catalog and content discovery
- Instructor dashboards
- Student enrollment experience
- Progress tracking
- Ratings and reviews
- Analytics event generation
- JWT authentication
- Responsive React.js interfaces

## Event-Driven Engineering

- BullMQ + Redis workers
- Retry handling
- Priority queues
- Background analytics processing
- Analytics aggregation workflows
- Asynchronous event pipelines

## Cloud & DevOps Engineering

- Jenkins CI/CD
- Dockerized services
- Ansible deployment automation
- AWS SQS + Lambda migration
- HTTPS and custom domain
- CloudWatch monitoring
- SNS alerting

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

## Application Architecture

```text
┌─────────────┐
│    User     │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ React Front │
└──────┬──────┘
       │
       ▼
┌─────────────────────┐
│ Node.js / Express   │
└──────┬──────────────┘
       │
       ▼
┌─────────────┐
│   MongoDB   │
└─────────────┘
```

---

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

The platform follows a multi-repository architecture separating application services, asynchronous processing components, cloud-native event consumers, and deployment infrastructure.

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
