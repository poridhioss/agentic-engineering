# Part 3: PLATFORM ENGINEERING

## MILESTONE 1: API Platform

### Module 1: Unified API Gateway

**Week 27**

### Class Topics

- API Gateway as Foundation
- API Versioning Strategies
- Gateway Auth with JWT and RBAC
- AI-Assisted Gateway Design

### Hands-On Labs

**Exposing Module 1 & Module 2 Systems**

- Module 1 Systems Mapped as Upstream Routes for Redis Broker and Serverless
- Module 2 Systems Mapped as Upstream Routes for PostgreSQL MongoDB Kafka and Microservices
- v1 Versioning with Coexisting v2 Route

**Auth & Security at the Gateway**

- JWT Validation Middleware at Gateway
- Role-Based Routing with Read Tokens to Replicas and Write Tokens to Primary
- Rate Limiting Per API Key with Nginx

**Infrastructure**

- Docker Compose with All M1 and M2 Services Envoy and Nginx as One Stack
- AI-Generated OpenAPI Spec for Every Exposed Endpoint
- GitHub Actions Gateway Config Validation and Smoke Tests

### AI Exam

- Unified API Gateway with Auth and Versioning


### Module 2: CLI Development

**Week 28**

### Class Topics

- CLI as Platform Interface
- CLI Design and Subcommands
- CLI Auth and Token Refresh
- Natural Language CLI Mode

### Hands-On Labs

**Building the Platform CLI**

- CLI Scaffold from Plain English Description
- DB Broker Function and Cache Commands Wired to API Gateway
- Login Command with JWT Storage and Auto-Refresh

**Natural Language Mode**

- Platform Ask Command to NL Gateway
- Shell Completion Script for Bash and Zsh
- Error Messages as Fix Instructions

**Infrastructure**

- CLI Binary Build with GoReleaser
- GitHub Actions Build for Linux macOS and Windows on Every Tag
- One-Line Install Script via curl

### AI Exam

- Platform CLI Build and Release


## MILESTONE 2: AI Gateway Layer

### Module 3: Natural Language to API

**Week 29**

### Class Topics

- NL-to-API Translation Pipeline
- Intent Classification and Routing
- Parameter Extraction from Unstructured Input
- Ambiguity Handling and Clarification

### Hands-On Labs

**Building the NL Gateway**

- FastAPI NL Gateway with Classify Extract Call and Summarize
- Intent Routing Table with Twenty Phrases Mapped to API Routes
- Parameter Extraction Accuracy on Twenty Test Inputs

**Ambiguity & Fallback**

- Ambiguity Detection with Multiple Route Matches Triggering Clarification
- Fallback with Top Three Interpretations Returned on Classification Failure
- Cost-Effective versus Capable Model Routing for NL Steps

**Infrastructure**

- NL Gateway Deployed Between CLI and API Gateway
- Loki Logging for Input Intent Parameters and Response
- Prometheus Metrics for Classification Accuracy Extraction Latency and Fallback Rate

### AI Exam

- Natural Language API Gateway Demo


### Module 4: Human-in-the-Loop Safety

**Week 30**

### Class Topics

- AI Safety in Production
- Sensitivity Classification
- The Approval Flow
- Immutable Audit Trail

### Hands-On Labs

**Sensitivity Classification**

- Sensitivity Classifier with Thirty Test Cases Across Edge Cases
- Permission Matrix as Code in permissions.yaml
- Least-Privilege Blocking Write Operations from Read Tokens

**Slack Approval Workflow**

- Slack Block Kit Approval Message with Operation Details
- Webhook Listener with Pending Queue Released on Approve
- Timeout Handler with Auto-Reject and Requester Notification at Ten Minutes

**Audit & Recovery**

- Immutable Audit Log in Append-Only PostgreSQL Table
- Operation Replay from Audit Log Entry
- Weekly AI-Generated Audit Summary

### AI Exam

- Human-in-the-Loop Approval Flow


## MILESTONE 3: Kubernetes & Event-Driven Platform

### Module 5: Kubernetes Fundamentals

**Weeks 31–32**

### Class Topics

- Kubernetes Orchestration and Self-Healing
- Core Kubernetes Objects
- RBAC and Service Accounts
- Namespace Isolation

### Hands-On Labs

**Deploying M1 & M2 on Kubernetes**

- Kubernetes Manifests for Module 1 Systems with Deployment Service and ConfigMap
- Kubernetes Manifests for Module 2 Systems with StatefulSets for Databases
- Nginx Ingress Controller with Path Routing

**RBAC & Namespace Isolation**

- Namespace Structure for m1-systems m2-systems ai-gateway and platform-tools
- AI Gateway Service Account with Scoped Permissions
- Network Policies Blocking Direct Cross-Namespace Traffic

**Infrastructure**

- Local Kubernetes Cluster with k3d or Kind
- Helm Charts for All M1 and M2 Manifests
- AWS EKS Deployment and Validation

### AI Exam

- Full Platform Deployment on Kubernetes


### Module 6: Event-Driven Architecture on Kubernetes

**Week 33**

### Class Topics

- KEDA Event-Driven Autoscaler
- Event Sources and Triggers
- AI as Event Processor
- Kafka to Kubernetes Job Pipelines

### Hands-On Labs

**KEDA Autoscaling**

- KEDA ScaledObject with Notification Consumer Scaling on RabbitMQ Depth
- Kafka-Driven Scaling with Consumer Lag Triggering Scale-Up
- HTTP Scaling for the NL Gateway

**AI-Driven Event Processing**

- Pod Failure Pipeline from CrashLoopBackOff to Logs to AI to Slack
- Metric Anomaly Pipeline from Prometheus Alert to AI Summary to Slack Approval
- Hourly CronJob with Platform Health Check and AI Summary

**Infrastructure**

- KEDA Kafka RabbitMQ AI Gateway and Slack Webhook in Kubernetes
- KEDA ScaledObjects for All Event-Driven Workloads
- Prometheus and Grafana Dashboard for KEDA Scaling Events and AI Summaries

### AI Exam

- KEDA Autoscaling and Event-Driven AI


### Module 7: Observability Stack & AI Analysis

**Week 34**

### Class Topics

- Full Observability Stack
- Pyroscope Continuous Profiling
- Sending Observability Data to AI
- NL Queries for Traces and Metrics

### Hands-On Labs

**Observability Stack Deployment**

- Prometheus Grafana Loki Tempo and Pyroscope Deployed in Kubernetes
- All M1 and M2 Systems Instrumented and Reporting to the Stack
- Single Grafana Dashboard with Metrics Logs Traces and Flame Graphs in One View

**Pyroscope Continuous Profiling**

- Pyroscope Setup for CPU and Memory Profiling Across Platform Services
- Flame Graph Analysis for Message Broker and Redis Hot Paths
- AI-Assisted Flame Graph Interpretation for Top Bottleneck Identification

**AI Analysis via CLI**

- CLI Commands for Logs Traces Metrics and Profile
- Natural Language Query for Why Is the Message Broker Slow Using Traces Metrics Logs and Profile Together
- Cost-Effective Model for Routine Queries and Capable Model for Root Cause Analysis
- Correlated Incident Report Linking Metric Spike to Trace Log Error and Flame Graph Hotspot

### AI Exam

- Observability-Driven Root Cause Analysis via CLI


## MILESTONE 4: Infrastructure as Code & CI/CD

### Module 8: Infrastructure as Code

**Week 35**

### Class Topics

- Why Infrastructure as Code
- Terraform Providers Resources and Modules
- AWS Infrastructure for the Platform
- Remote State and DynamoDB Locking

### Hands-On Labs

**Terraform Modules for the Platform**

- VPC Module with Subnets NAT Gateway and Security Groups
- EKS Module with Managed Cluster Node Groups and OIDC for IRSA
- Data Layer Module with RDS PostgreSQL ElastiCache Redis and S3 for WAL

**State & Security**

- Remote State Bootstrap with S3 and DynamoDB
- IAM Least-Privilege Per Service
- Secrets Manager and External Secrets Operator with No Plaintext Secrets

**Infrastructure**

- Full Platform Provisioned from One terraform apply
- Terraform Plan in GitHub Actions with AI Plain English Summary
- Weekly Drift Detection with Plan Posted to Slack

### AI Exam

- Platform Infrastructure from Zero with Terraform


### Module 9: CI/CD & GitOps

**Week 36**

### Class Topics

- CI/CD for Platform Engineering
- GitOps and Cluster State
- Staged Rollouts and Approval Gates
- AI for Pipeline Failure Diagnosis

### Hands-On Labs

**GitHub Actions Pipeline**

- NL Gateway Pipeline with Lint Tests Docker Build ECR Push and Helm Update
- AI Failure Analysis with Pipeline Logs to AI and Fix Posted as PR Comment
- Staging Auto-Deploy on Merge with Prod Requiring Manual Approval

**GitOps with ArgoCD**

- ArgoCD Application Watching Helm Charts Repo
- Rollback via Git Revert with ArgoCD Syncing to Previous State
- Multi-Environment Setup with envs/staging and envs/prod Using ApplicationSets

**Infrastructure**

- GitHub Actions and ArgoCD Together from Build to Helm Values Commit to Sync
- Smoke Test Kubernetes Job After Every ArgoCD Sync
- Infracost Terraform Cost Diff on Every PR with AI Summary

### AI Exam

- Full CI/CD Pipeline to Production


## MILESTONE 5: Production Platform

### Module 10: Serverless Architecture

**Week 37**

### Class Topics

- Serverless as Glue
- AWS Lambda Trigger Patterns
- Event-Driven Serverless Pipeline
- AI for Lambda Review

### Hands-On Labs

**Lambda Functions for the Platform**

- Slack Approval Processor Lambda
- Log Analysis Lambda from S3 Upload to Tiered Model Pipeline to Slack Summary
- Schema Migration Lambda with EventBridge Trigger and Human Approval Gate

**Event-Driven Serverless Pipelines**

- EventBridge Rules for Platform Events
- SQS Dead-Letter Queue with Lambda Failure Monitor
- Cold Start Optimization with Measurement and Fix

**Infrastructure**

- Terraform with Lambda Functions SQS EventBridge and IAM as Code
- GitHub Actions Lambda Deployment Pipeline
- Grafana Dashboard for Lambda Invocations Duration p99 Error Rate and Cold Start Frequency

### AI Exam

- Event-Driven Lambda Pipeline with Approval


### Module 11: Capstone — Production Platform

**Weeks 38–40**

### Class Topics

- Full Platform Architecture
- Architecture Decision Records
- The Deletion Audit
- Production Readiness Checklist

### Hands-On Labs

**Architecture & Design**

- Full Platform Dependency Graph with Mermaid Diagram
- Architecture Decision Records for Five Key Platform Decisions
- Deletion Audit with One Sentence Per Component

**Integration Testing**

- End-to-End Test Suite with Twenty Scenarios Including Five Requiring Slack Approval
- Chaos Test with One M2 Service Killed and Clean Error and NL Response Verified
- Load Test with Five Hundred Concurrent NL Requests and KEDA Response Observation

**Production Deployment**

- Full Platform from Zero via Terraform and ArgoCD Helm Sync
- Single Grafana Dashboard for NL Accuracy API Latency Kubernetes Scaling Lambda Approval Rate and Token Usage
- Security Audit with OWASP LLM Top 10 Against NL Gateway and Human Approval Flow

### AI Exam

- Production Platform Live Demo
