# Architecture Documentation

---

# Overview

This project demonstrates the evolution of an event-driven EdTech platform from a self-managed asynchronous processing architecture toward an AWS-native serverless architecture.

The system was designed to showcase modern DevOps workflows, event-driven backend engineering, CI/CD automation, infrastructure orchestration, and cloud-native migration strategies.

---

# Version 1 — Self-Managed Event Architecture

## Architecture Diagram

![Self Managed Architecture](../assets/architecture/self-managed-architecture.svg)

---

## Components

- Frontend Container
- Backend API Container
- BullMQ Queue
- Redis Queue Backend
- Worker Service
- MongoDB
- Nginx Reverse Proxy

---

## Request Flow

```text
User
   ↓
Frontend
   ↓
Nginx Reverse Proxy
   ↓
Backend API
   ↓
BullMQ Queue
   ↓
Redis
   ↓
Worker Service
   ↓
MongoDB Analytics
```

---

# Key Features

Implemented:

- Retry handling
- Failure recovery
- Background processing
- Analytics aggregation
- Async workload execution
- Queue-based event processing
- Dockerized service orchestration

---

# Event Processing Workflow

The backend publishes asynchronous events into BullMQ queues.

Worker services consume queued jobs and perform:

- Analytics tracking
- Event aggregation
- Background processing
- Failure retries

Redis acts as the queue backend for BullMQ event processing.

---

# Version 2 — AWS-Native Architecture

## Architecture Diagram

![AWS Native Architecture](../assets/architecture/aws-native-architecture.svg)

---

## Components

- Frontend Container
- Backend API
- Amazon SQS
- AWS Lambda
- CloudWatch
- MongoDB

---

## Request Flow

```text
User
   ↓
Frontend
   ↓
Nginx Reverse Proxy
   ↓
Backend API
   ↓
Amazon SQS
   ↓
AWS Lambda
   ↓
MongoDB Analytics
```

---

# AWS-Native Event Processing

The migrated architecture replaces self-managed queue infrastructure with AWS-managed cloud-native services.

Backend APIs publish events to Amazon SQS queues.

AWS Lambda functions automatically consume queue messages and process analytics events asynchronously.

CloudWatch provides centralized monitoring and execution logging.

---

# Why Migrate to AWS-Native Architecture

The migration demonstrates the transition from self-managed infrastructure toward managed cloud-native event processing systems.

Benefits include:

- Reduced operational overhead
- Auto-scaling event processing
- Improved reliability
- Fully managed queue infrastructure
- Serverless execution model
- Native AWS observability integration
- Simplified operational management

---

# Branch-Aware Deployment Strategy

## Main Branch

Implements:

- BullMQ
- Redis
- Worker-based event processing
- Self-managed asynchronous infrastructure

---

## sqs-lambda-migration Branch

Implements:

- Amazon SQS
- AWS Lambda
- Cloud-native event processing
- Serverless execution workflows

---

# Infrastructure Separation

## Application EC2

Runs:

- Frontend container
- Backend container
- Worker container
- Redis container
- Nginx reverse proxy

---

## Jenkins EC2

Runs:

- Jenkins
- Docker CLI
- CI/CD pipelines
- Deployment orchestration
- Ansible execution

---

# CI/CD Architecture

## CI/CD Flow Diagram

![CI/CD Workflow](../assets/architecture/cicd-flow.svg)

---

# Deployment Workflow

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
Infra Deployment Trigger
      ↓
Ansible Playbook
      ↓
AWS EC2 Deployment
```

---

# Monitoring and Reliability

Implemented:

- Docker health checks
- CloudWatch logging
- Retry mechanisms
- Failure simulation
- Event aggregation logging
- Queue retry handling
- Container restart policies

---

# Cloud-Native Observability

The AWS-native event-driven architecture integrates CloudWatch and SNS-based operational monitoring for serverless workloads.

Implemented monitoring capabilities include:

* Lambda invocation monitoring
* CloudWatch execution metrics
* SNS email alert integration
* Queue visibility monitoring
* Application health checks
* Event processing visibility

A CloudWatch alarm monitors Lambda invocation traffic volume and automatically triggers SNS email notifications when invocation thresholds exceed configured limits.

This demonstrates operational observability practices commonly used in production-grade distributed systems.

---

# Security and Networking

Configured:

- HTTPS deployment
- SSL certificates
- Custom domain integration
- Elastic IP routing
- Nginx reverse proxy
- IAM-based AWS access control

---

# Future Improvements

Potential future enhancements:

- Dead Letter Queue (DLQ) integration
- Blue-green deployments
- Canary deployments
- ECS/Fargate migration
- Kubernetes orchestration
- Centralized observability stack
- Distributed tracing