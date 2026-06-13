# Architecture Documentation

# Overview

This project demonstrates the architecture and evolution of a full-stack event-driven EdTech learning platform built using React.js, Node.js, MongoDB, Redis, BullMQ, and AWS cloud services.

The platform enables instructors to publish educational content and learners to consume courses through video learning experiences, progress tracking, ratings, reviews, and analytics-driven insights.

The architecture showcases the evolution from self-managed asynchronous processing infrastructure toward AWS-native serverless event processing using Amazon SQS and AWS Lambda.

The project also demonstrates modern CI/CD automation, infrastructure orchestration, deployment workflows, observability, and cloud-native migration strategies.

---

# Application Architecture

## Core Application Flow

```text
┌─────────────┐
│    User     │
└──────┬──────┘
       │
       ▼
┌─────────────────┐
│ React Frontend  │
└──────┬──────────┘
       │
       ▼
┌─────────────────┐
│ Nginx Proxy     │
└──────┬──────────┘
       │
       ▼
┌─────────────────┐
│ Node.js Backend │
└──────┬──────────┘
       │
       ▼
┌─────────────────┐
│    MongoDB      │
└─────────────────┘
```

---

# Application Features

The platform supports:

- Course publishing workflows
- Instructor dashboards
- Student enrollment workflows
- Video course consumption
- Course ratings and reviews
- Progress tracking
- Analytics event generation
- Background analytics processing
- Responsive user experience
- JWT-based authentication and authorization

---

# Version 1 — Self-Managed Event Architecture

## Architecture Diagram

![Self Managed Architecture](../assets/architecture/self-managed-architecture.svg)

---

## Components

- React Frontend
- Node.js Backend API
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
React Frontend
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

# Self-Managed Event Processing

The first implementation uses BullMQ and Redis to process analytics and background workloads asynchronously.

Backend APIs publish events into BullMQ queues while dedicated worker services consume and process queued jobs.

This architecture demonstrates traditional event-driven backend design patterns using self-managed queue infrastructure.

---

# Key Features

Implemented:

- Retry handling
- Failure recovery
- Background processing
- Analytics aggregation
- Async workload execution
- Queue-based event processing
- Worker isolation
- Dockerized service orchestration

---

# Event Processing Workflow

The backend publishes asynchronous events into BullMQ queues.

Worker services consume queued jobs and perform:

- Analytics tracking
- Event aggregation
- Background processing
- Failure retries
- Usage metric collection

Redis acts as the queue backend for BullMQ event processing.

---

# Version 2 — AWS-Native Architecture

## Architecture Diagram

![AWS Native Architecture](../assets/architecture/aws-native-architecture.svg)

---

## Components

- React Frontend
- Node.js Backend API
- Amazon SQS
- AWS Lambda
- CloudWatch
- MongoDB

---

## Request Flow

```text
User
   ↓
React Frontend
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

CloudWatch provides centralized monitoring, execution visibility, and operational observability.

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

## Deployment Workflow

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

- Lambda invocation monitoring
- CloudWatch execution metrics
- SNS email alert integration
- Queue visibility monitoring
- Application health checks
- Event processing visibility

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
