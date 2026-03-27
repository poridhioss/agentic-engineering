# Part 3: PLATFORM ENGINEERING

## MILESTONE 1: API Platform

### Module 1: Unified API Gateway

### Class Topics

- API Gateway as Platform Foundation
- Aggregating Heterogeneous Systems Behind One Entry Point
- API Versioning Strategies
- Auth at the Gateway Layer: JWT, API Keys, RBAC
- AI-Assisted Gateway Design and Routing Table

### Hands-On Labs

**Exposing Module 1 & Module 2 Systems**

- Module 1 Systems Mapped as Upstream Routes (Redis, Broker, Serverless)
- Module 2 Systems Mapped as Upstream Routes (PostgreSQL, MongoDB, Kafka, Microservices)
- v1 Versioning with Coexisting v2 Route

**Auth & Security at the Gateway**

- JWT Validation Middleware at Gateway
- Role-Based Routing: Read Tokens to Replicas, Write Tokens to Primary
- Rate Limiting Per API Key with Nginx

**Infrastructure**

- Docker Compose: All M1 + M2 Services + Envoy + Nginx as One Stack
- AI-Generated OpenAPI Spec for Every Exposed Endpoint
- GitHub Actions: Gateway Config Validation and Smoke Tests

### AI Exam

- Unified API Gateway with Auth and Versioning


### Module 2: CLI Development

### Class Topics

- CLI as the Developer Platform Interface
- CLI Design: Subcommands, Flags, Help Text, Error Messages
- Connecting CLI to APIs: Auth Flow and Token Refresh
- Natural Language CLI Mode
- CLI as Harness: AGENTS.md and Argument Parsers

### Hands-On Labs

**Building the Platform CLI**

- CLI Scaffold from Plain English Description
- db, broker, fn, cache Commands Wired to API Gateway
- Login Command with JWT Storage and Auto-Refresh

**Natural Language Mode**

- platform ask "..." Command to NL Gateway
- Shell Completion Script for Bash and Zsh
- Error Messages as Fix Instructions

**Infrastructure**

- CLI Binary Build with GoReleaser
- GitHub Actions: Build for Linux/macOS/Windows on Every Tag
- One-Line Install Script via curl

### AI Exam

- Platform CLI Build and Release


## MILESTONE 2: AI Gateway Layer

### Module 3: Natural Language to API

### Class Topics

- NL-to-API Translation Pipeline: Intent → Parameters → Call → Answer
- Intent Classification and System Routing
- Parameter Extraction from Unstructured Input
- Ambiguity Handling: Ask Before Guessing
- Cost-Effective Model for Classification, Capable Model for Execution

### Hands-On Labs

**Building the NL Gateway**

- FastAPI NL Gateway: Classify, Extract, Call, Summarize
- Intent Routing Table: 20 Phrases Mapped to API Routes
- Parameter Extraction Accuracy on 20 Test Inputs

**Ambiguity & Fallback**

- Ambiguity Detection: Multiple Route Matches Trigger Clarification
- Fallback: Top 3 Interpretations Returned on Classification Failure
- Cost-Effective vs. Capable Model Routing for NL Steps

**Infrastructure**

- NL Gateway Deployed Between CLI and API Gateway
- Loki Logging: Input, Intent, Parameters, Response
- Prometheus: Classification Accuracy, Extraction Latency, Fallback Rate

### AI Exam

- Natural Language API Gateway Demo


### Module 4: Human-in-the-Loop Safety

### Class Topics

- Why AI Should Not Autonomously Write to Production
- Sensitivity Classification: Read, Write, Destructive, Critical
- The Approval Flow: Detect → Slack Message → Wait → Execute
- Approval Message Design: What, What Data, Approve/Reject
- Immutable Audit Trail for All Operations

### Hands-On Labs

**Sensitivity Classification**

- Sensitivity Classifier: 30 Test Cases Across Edge Cases
- Permission Matrix as Code in permissions.yaml
- Least-Privilege: Write Operations Blocked from Read Tokens

**Slack Approval Workflow**

- Slack Block Kit Approval Message with Operation Details
- Webhook Listener: Pending Queue Released on Approve
- Timeout Handler: Auto-Reject and Requester Notification at 10 Minutes

**Audit & Recovery**

- Immutable Audit Log in Append-Only PostgreSQL Table
- Operation Replay from Audit Log Entry
- Weekly AI-Generated Audit Summary

### AI Exam

- Human-in-the-Loop Approval Flow


## MILESTONE 3: Kubernetes & Event-Driven Platform

### Module 5: Kubernetes Fundamentals

### Class Topics

- Why Kubernetes: Orchestration, Self-Healing, Declarative Config
- Core Objects: Pods, Deployments, Services, ConfigMaps, Secrets, Ingress
- RBAC: Service Accounts, Roles, Role Bindings
- Namespace Isolation for Platform Services
- AI for Kubernetes Manifest Generation and Review

### Hands-On Labs

**Deploying M1 & M2 on Kubernetes**

- K8s Manifests for Module 1 Systems: Deployment, Service, ConfigMap
- K8s Manifests for Module 2 Systems: StatefulSets for Databases
- Nginx Ingress Controller with Path Routing

**RBAC & Namespace Isolation**

- Namespace Structure: m1-systems, m2-systems, ai-gateway, platform-tools
- AI Gateway Service Account with Scoped Permissions
- Network Policies: No Direct Cross-Namespace Traffic

**Infrastructure**

- Local K8s Cluster with k3d or Kind
- Helm Charts for All M1 and M2 Manifests
- AWS EKS Deployment and Validation

### AI Exam

- Full Platform Deployment on Kubernetes


### Module 6: Event-Driven Architecture on Kubernetes

### Class Topics

- KEDA: Kubernetes Event-Driven Autoscaler
- Event Sources: Kafka Lag, RabbitMQ Depth, HTTP Request Count
- AI as Event Processor: Pod Crash → Root Cause Agent
- Event-Driven Pipelines: Kafka → K8s Job → AI Gateway → System
- Human-in-the-Loop in Event-Driven Flows

### Hands-On Labs

**KEDA Autoscaling**

- KEDA ScaledObject: Notification Consumer Scales with RabbitMQ Depth
- Kafka-Driven Scaling: Consumer Lag Triggers Scale-Up
- HTTP Scaling for the NL Gateway

**AI-Driven Event Processing**

- Pod Failure Pipeline: CrashLoopBackOff → Logs to AI → Fix to Slack
- Metric Anomaly Pipeline: Prometheus Alert → AI Summary → Slack Approval
- Hourly CronJob: Platform Health Check with AI Summary

**Infrastructure**

- KEDA + Kafka + RabbitMQ + AI Gateway + Slack Webhook in K8s
- KEDA ScaledObjects for All Event-Driven Workloads
- Prometheus + Grafana: KEDA Scaling Events and AI Summaries

### AI Exam

- KEDA Autoscaling and Event-Driven AI


### Module 7: Observability Stack & AI Analysis

### Class Topics

- Full Observability Stack: Prometheus, Grafana, Loki, Tempo, Pyroscope
- Pyroscope: Continuous Profiling, Flame Graphs, CPU and Memory Hotspots
- Connecting All Platform Systems to the Observability Stack
- Sending Observability Data to AI Models for Analysis
- CLI-Based Natural Language Queries for Traces, Metrics, Logs, and Profiles

### Hands-On Labs

**Observability Stack Deployment**

- Prometheus + Grafana + Loki + Tempo + Pyroscope Deployed in Kubernetes
- All M1 and M2 Systems Instrumented and Reporting to the Stack
- Single Grafana Dashboard: Metrics, Logs, Traces, and Flame Graphs in One View

**Pyroscope Continuous Profiling**

- Pyroscope Setup for CPU and Memory Profiling Across Platform Services
- Flame Graph Analysis for Message Broker and Redis Hot Paths
- AI-Assisted Flame Graph Interpretation: Top Bottleneck Identification

**AI Analysis via CLI**

- CLI Commands: platform logs, platform traces, platform metrics, platform profile
- NL Query: "Why is the message broker slow?" — AI Reads Traces, Metrics, Logs, and Profile Together
- Cost-Effective Model for Routine Queries, Capable Model for Root Cause Analysis
- Correlated Incident Report: AI Links a Metric Spike to a Trace, a Log Error, and a Flame Graph Hotspot

### AI Exam

- Observability-Driven Root Cause Analysis via CLI

## MILESTONE 4: Infrastructure as Code & CI/CD

### Module 8: Infrastructure as Code

### Class Topics

- Why IaC: Infrastructure That Cannot Be Recreated Will Eventually Fail
- Terraform Fundamentals: Providers, Resources, State, Modules
- AWS Infrastructure for the Platform: VPC, EKS, RDS, ElastiCache, S3, ECR, IAM
- Remote State in S3 with DynamoDB Locking
- AI for Terraform: Review Every Resource Block Before Applying

### Hands-On Labs

**Terraform Modules for the Platform**

- VPC Module: Subnets, NAT Gateway, Security Groups
- EKS Module: Managed Cluster, Node Groups, OIDC for IRSA
- Data Layer Module: RDS PostgreSQL, ElastiCache Redis, S3 for WAL

**State & Security**

- Remote State Bootstrap: S3 + DynamoDB
- IAM Least-Privilege Per Service
- Secrets Manager + External Secrets Operator: No Plaintext Secrets

**Infrastructure**

- Full Platform Provisioned from One terraform apply
- terraform plan in GitHub Actions with AI Plain English Summary
- Weekly Drift Detection: Plan Posted to Slack

### AI Exam

- Platform Infrastructure from Zero with Terraform


### Module 9: CI/CD & GitOps

### Class Topics

- CI/CD for Platform Engineering: No Manual Steps in Production
- GitOps: Git as Single Source of Truth for Cluster State
- Pipeline Stages: Lint → Test → Build → Push → Update Helm → Sync
- Staged Rollouts: Dev → Staging → Prod with Manual Approval Gate
- AI for Pipeline Failure Diagnosis

### Hands-On Labs

**GitHub Actions Pipeline**

- NL Gateway Pipeline: Lint, Tests, Docker Build, ECR Push, Helm Update
- AI Failure Analysis: Pipeline Logs to AI, Fix Posted as PR Comment
- Staging Auto-Deploy on Merge, Prod Requires Manual Approval

**GitOps with ArgoCD**

- ArgoCD Application Watching Helm Charts Repo
- Rollback via Git Revert: ArgoCD Syncs to Previous State
- Multi-Environment: envs/staging and envs/prod with ApplicationSets

**Infrastructure**

- Actions + ArgoCD Together: Build → Commit Helm Values → ArgoCD Syncs
- Smoke Test K8s Job After Every ArgoCD Sync
- Infracost Terraform Cost Diff on Every PR with AI Summary

### AI Exam

- Full CI/CD Pipeline to Production


## MILESTONE 5: Production Platform

### Module 10: Serverless Architecture

### Class Topics

- Serverless as Glue: Event Handler, Transformer, Notifier
- AWS Lambda Patterns: S3, SQS, EventBridge, API Gateway Triggers
- Connecting Lambda to the Platform via API Gateway
- Event-Driven Serverless Pipeline
- AI for Lambda: Describe Handler, Review Before Deploy

### Hands-On Labs

**Lambda Functions for the Platform**

- Slack Approval Processor Lambda
- Log Analysis Lambda: S3 Upload → Tiered Model Pipeline → Slack Summary
- Schema Migration Lambda with EventBridge Trigger and Human Approval Gate

**Event-Driven Serverless Pipelines**

- EventBridge Rules for Platform Events
- SQS Dead-Letter Queue with Lambda Failure Monitor
- Cold Start Optimization: Measure, Identify, Fix

**Infrastructure**

- Terraform: Lambda Functions, SQS, EventBridge, IAM as Code
- GitHub Actions Lambda Deployment Pipeline
- Grafana: Lambda Invocations, Duration p99, Error Rate, Cold Start Frequency

### AI Exam

- Event-Driven Lambda Pipeline with Approval


### Module 11: Capstone — Production Platform

### Class Topics

- Full Platform Architecture: CLI → NL Gateway → API Gateway → K8s → Human Approval → Lambda
- Architecture Decision Records
- The Deletion Audit: Which Model Improvement Makes This Obsolete?
- Production Readiness Checklist
- Final Presentation: Demo + Architecture Diagram + Metrics

### Hands-On Labs

**Architecture & Design**

- Full Platform Dependency Graph with Mermaid Diagram
- Architecture Decision Records for 5 Key Platform Decisions
- Deletion Audit: One Sentence Per Component

**Integration Testing**

- End-to-End Test Suite: 20 Scenarios Including 5 Requiring Slack Approval
- Chaos Test: Kill One M2 Service, Verify Clean Error and NL Response
- Load Test: 500 Concurrent NL Requests with KEDA Response Observation

**Production Deployment**

- Full Platform from Zero via Terraform + ArgoCD Helm Sync
- Single Grafana Dashboard: NL Accuracy, API Latency, K8s Scaling, Lambda, Approval Rate, Token Usage
- Security Audit: OWASP LLM Top 10 Against NL Gateway and Human Approval Flow

### AI Exam

- Production Platform Live Demo