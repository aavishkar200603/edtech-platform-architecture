# AWS-Native Migration Documentation

---

# Overview

This project evolved from a self-managed asynchronous worker architecture toward an AWS-native serverless event-driven architecture.

The migration demonstrates the transition from self-managed infrastructure toward managed cloud-native event processing systems.

---

# Initial Architecture

## Self-Managed Queue System

```text
Backend API
    ↓
BullMQ Queue
    ↓
Redis
    ↓
Worker Service
```

---

# Self-Managed Architecture Diagram

![Self Managed Architecture](../assets/architecture/self-managed-architecture.svg)

---

# Migrated Architecture

## AWS-Native Event Architecture

```text
Backend API
    ↓
Amazon SQS
    ↓
AWS Lambda
    ↓
CloudWatch Logs
```

---

# AWS-Native Architecture Diagram

![AWS Native Architecture](../assets/architecture/aws-native-architecture.svg)

---

# Amazon SQS Integration

The migrated architecture uses Amazon SQS for reliable asynchronous event delivery and decoupled backend processing.

Features implemented:

- Queue-based event delivery
- Lambda trigger integration
- Managed asynchronous processing
- Cloud-native event orchestration

![SQS Lambda Integration](../assets/aws/sqs-trigger.png)

---

# S3 Analytics Storage

Processed analytics reports are uploaded into Amazon S3 for durable cloud storage and future reporting workflows.

The uploaded JSON reports demonstrate asynchronous analytics aggregation handled through AWS Lambda event processing.

![S3 Analytics Storage](../assets/aws/s3-analytics-storage.png)

---

# Motivation for Migration

The migration was implemented to demonstrate:

- Cloud-native event processing
- Managed queue infrastructure
- Serverless execution
- Reduced operational complexity
- Event-driven scalability

---

# Key Architectural Changes

## Removed

- Redis container
- Worker container
- Self-managed polling mechanisms

---

## Added

- Amazon SQS
- AWS Lambda
- CloudWatch logging
- IAM-based access control

---

# Benefits of AWS-Native Architecture

- Fully managed queue service
- Auto-scaling event consumers
- Lower operational overhead
- Event-triggered execution model
- Integrated AWS monitoring capabilities

---

# Monitoring

Implemented:

- CloudWatch Logs
- Lambda execution logging
- SQS event visibility monitoring
- Application health checks

---

# CloudWatch Alarm Monitoring

CloudWatch alarms were configured to monitor Lambda invocation traffic thresholds.

When Lambda invocations exceed configured thresholds, Amazon SNS automatically sends operational alert notifications.

Implemented monitoring capabilities include:

- Lambda invocation monitoring
- CloudWatch metric alarms
- SNS email notifications
- Traffic threshold alerting
- Serverless operational visibility

![CloudWatch Alarm](../assets/aws/cloudwatch-alarm.png)

---

# Lambda Event Processing Logs

CloudWatch Logs provide centralized visibility into asynchronous event-processing workflows.

The logs below demonstrate:

- SQS event consumption
- Lambda execution
- MongoDB analytics updates
- S3 analytics uploads

![Lambda Logs](../assets/aws/lambda-event-processing.png)

---

# Future Improvements

Potential future enhancements:

- Dead Letter Queue (DLQ) integration
- Blue-green deployments
- Canary deployments
- Centralized log aggregation
- ECS/Fargate migration