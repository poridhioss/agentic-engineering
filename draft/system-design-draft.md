# Part 2: SYSTEM DESIGN

## MILESTONE 1: Core Building Blocks

### Module 1: Relational Databases

**Week 15**

### Class Topics

- Relational Model and Normalization
- B-Tree and Composite Indexes
- Query Optimization and EXPLAIN Plans
- Natural Language to SQL

### Hands-On Labs

**Schema Design with AI**

- Ride-Sharing Domain Schema from Plain English
- Normalization Violation Detection and Fix
- AI-Generated Index Recommendations from Slow Query Log

**Query Optimization with AI**

- EXPLAIN Plan Diagnostic Conversation
- N+1 Query Identification and Rewrite
- Natural Language Query Interface for PostgreSQL

**Connection Pooling**

- PgBouncer Setup and Pool Sizing
- Connection Pool Exhaustion Simulation
- pg_stat_statements Top Query Analysis

**Infrastructure**

- PostgreSQL Docker Setup with MCP Server
- DB Protection Hook with SQL Operation Whitelist
- GitHub Actions Slow Query Detection on Migration PRs

### AI Exam

- Legacy Schema Redesign


### Module 2: NoSQL & Caching

**Week 16**

### Class Topics

- NoSQL Data Models
- MongoDB Aggregation Pipelines
- Redis Data Structures and TTL
- Cache-Aside and Read-Through Patterns

### Hands-On Labs

**MongoDB with AI**

- Social Media Post Model from Plain English
- Slow Aggregation Diagnosis and Rebuild
- Natural Language to MongoDB Query via MCP

**Redis Patterns with AI**

- Cache-Aside Layer for PostgreSQL API
- Redis Sorted Set Leaderboard
- Cache-Aside Extension for Module 1 Message Broker

**Full-Text Search**

- PostgreSQL tsvector Full-Text Search on Product Catalog
- PostgreSQL FTS versus LIKE Query Benchmark
- MongoDB Atlas Search or Elasticsearch Query DSL

**Infrastructure**

- Docker Compose with PostgreSQL MongoDB and Redis
- All Three Stores Exposed as MCP Servers

### AI Exam

- Multi-Store Domain Design


### Module 3: API Design & Communication Protocols

**Week 17**

### Class Topics

- REST Design and Versioning
- GraphQL and N+1 in Resolvers
- gRPC and Protocol Buffers
- API Gateway Patterns

### Hands-On Labs

**REST & GraphQL with AI**

- OpenAPI Spec Generation and Design Review
- REST versus GraphQL Benchmark on Same Endpoints
- N+1 GraphQL Resolver Fix with DataLoader

**API Security**

- JWT Authentication Middleware
- Dual-Key API Key Rotation Strategy
- Gateway-Layer Auth Enforcement with Envoy

**gRPC & API Gateway**

- Proto File for a User Service
- Envoy Gateway with REST and gRPC Routing
- Request Transformation Lua Filter
- REST API as MCP Server with Auth Headers

**Infrastructure**

- Docker Compose with REST GraphQL gRPC and Envoy
- Nginx Path Prefix Routing for DB API and gRPC
- GitHub Actions OpenAPI Breaking-Change Detection

### AI Exam

- Notification Service API Layer


## MILESTONE 2: Scaling Strategies

### Module 4: Replication, Sharding & Consistency

**Week 18**

### Class Topics

- CAP Theorem and Trade-offs
- Leader-Follower and Leaderless Replication
- Sharding and Consistent Hashing
- Strong and Eventual Consistency

### Hands-On Labs

**Replication with AI**

- PostgreSQL Leader-Follower Replication Setup
- Replication Lag Simulation and Fix
- Failover Drill with Leader Kill and Follower Promotion

**Sharding with AI**

- Consistent Hashing Implementation
- Shard Strategy Design for Module 1 Message Broker
- Hot Shard Detection and Rebalancing Plan

**Backup & Recovery**

- Continuous WAL Archiving to S3
- Point-in-Time Recovery Drill
- Backup Verification with Checksum Comparison

**Infrastructure**

- Three-Node PostgreSQL Cluster with HAProxy on Docker Compose
- AWS RDS Multi-AZ versus Self-Managed Failover Comparison
- Prometheus Replication Lag Alert

### AI Exam

- Replication and Sharding Failover Demo


### Module 5: Load Balancing, Rate Limiting & CDN

**Week 19**

### Class Topics

- Load Balancing Algorithms
- Layer 4 versus Layer 7
- Rate Limiting Patterns
- CDN and Edge Caching

### Hands-On Labs

**Load Balancing**

- Nginx Layer 7 Load Balancer with Health Checks
- Round-Robin versus Least-Connections Under Spike Traffic
- Redis Sliding Window Rate Limiter

**CDN & Caching**

- Cache-Control Header Configuration for REST API
- TTFB Benchmark With and Without Nginx Caching Proxy
- Cache Poisoning Attack and Mitigation Headers
- CDN Invalidation Script

**Infrastructure**

- Docker Compose with Three API Replicas Nginx and Redis Rate Limiter
- Prometheus and Grafana Dashboard for RPS Error Rate and Latency

### AI Exam

- Traffic Management Layer Load Test


### Module 6: Message Queues & Event-Driven Architecture

**Week 20**

### Class Topics

- Why Async Messaging
- Message Queue Patterns
- Kafka Topics and Partitions
- Event Sourcing and CQRS

### Hands-On Labs

**Message Queue Patterns**

- Point-to-Point and Pub-Sub on RabbitMQ
- Dead-Letter Queue with Retry Policy
- Fan-Out with One Producer and Three Consumers

**Kafka with AI**

- Kafka Cluster Setup on Docker Compose
- Consumer Group Rebalancing Observation
- Kafka Trigger for Module 1 Serverless Platform

**Event-Driven Patterns**

- CQRS with Separate Write and Read Models
- Distributed Saga with Compensating Transactions

### AI Exam

- Message Broker Migration to Kafka


## MILESTONE 3: System Evolution

### Module 7: DB Migration & Schema Evolution

**Week 21**

### Class Topics

- Schema Migration Strategies
- Flyway Alembic and Liquibase
- Migration Risk Assessment
- Down Before Up Rollbacks

### Hands-On Labs

**Migration Planning with AI**

- Schema Change with Migration SQL Risk Assessment and Rollback Script
- Dangerous Migration Identification and Safe Alternative
- Ten Million Row Backfill Dry-Run with EXPLAIN ANALYZE

**Zero-Downtime Migration**

- Expand-Contract Pattern Implementation
- Blue-Green Schema Migration with Feature Flag
- Automated Rollback on Migration Timeout

**Infrastructure**

- Alembic Migration Pipeline in GitHub Actions
- Module 1 Log Pipeline Applied to Migration Logs

### AI Exam

- Zero-Downtime Schema Migration


### Module 8: Microservices & Observability

**Weeks 22–23**

### Class Topics

- Monolith versus Microservices
- Service Discovery with Consul
- Distributed Tracing Across Services
- AI Bottleneck Identification

### Hands-On Labs

**Microservices Decomposition with AI**

- Serverless Platform Decomposed into Three Microservices
- Service Discovery with Consul
- Circuit Breaker Between Services

**Service Mesh & Security**

- Istio mTLS Between Microservices
- Traffic Shifting with Istio VirtualService
- Retry and Timeout Policies at the Mesh Layer

**Distributed Tracing**

- OpenTelemetry Instrumentation
- Latency Fault Injection and Trace Diagnosis
- Missing Instrumentation Detection via AI

**Infrastructure**

- Docker Compose with Three Microservices Consul Envoy Prometheus Tempo and Grafana
- Grafana Service Map Dashboard
- AWS CloudWatch and Alertmanager for Production Alerting
- Terraform with Isolated EC2 Per Microservice
- AWS Lambda for Event-Driven Stateless Services

### AI Exam

- Microservices Failure Diagnosis and Recovery


## MILESTONE 4: Designing Real Systems

### Module 9: Classic System Design Problems

**Week 24**

### Class Topics

- System Design Framework
- AI as Design Partner
- Back-of-Envelope Estimation
- Write-Heavy and Fan-Out Patterns

### Hands-On Labs

**Design Sessions with AI**

- URL Shortener Full Design with Two Forced Flaws and Redesign
- Notification System Queue Topology and Failure Scenarios
- News Feed Fan-Out on Write versus Read Decision and Defense

**Tradeoff Analysis with AI**

- Tradeoff Table for What Breaks at Ten Times Scale
- Rate Limiter with Three Implementations Benchmarked
- Hot Key Mitigation with Local Cache and Jitter

**URL Shortener & Notification System**

- URL Shortener with FastAPI PostgreSQL Redis and Nginx at Ten Thousand Requests per Second
- Notification System with FastAPI RabbitMQ Workers and DLQ

### AI Exam

- Live System Design Session


## MILESTONE 5: AI-Native Operations

### Module 10: Natural Language DB Interaction & Log Analysis

**Weeks 25–26**

### Class Topics

- Database as MCP Server
- NL-to-Database Pipeline
- DB Monitoring and Lock Waits
- AI-Driven Incident Response

### Hands-On Labs

**Natural Language DB Interface**

- Module 1 MCP Infrastructure Reconfigured for Module 2 Databases
- Plain English Queries Across PostgreSQL MongoDB and Redis
- NL Failure Mode Documentation and Disambiguation Fix
- Cross-Store Query for Sessions Without DB Records

**DB Monitoring with AI**

- pg_stat_statements Query Cost Analysis via MCP
- PgBouncer Pool Exhaustion Root Cause
- Replication Lag Incident Summary from Prometheus Alert

**Log Analysis with Cost-Effective Models**

- Module 1 Tiered Log Pipeline Applied to DB Logs
- DB-Specific Escalation Rules for Deadlocks and Lock Waits
- Token Reduction Comparison versus Module 1 Baseline

**Infrastructure**

- Dockerized MCP Servers with Health Checks
- Docker Compose with MCP Servers and Nginx Reverse Proxy
- MCP Servers on AWS EC2 Private VPC
- MCP Servers as systemd Services on EC2

### AI Exam

- AI-Driven Database Performance Diagnosis


## PROGRAM OVERVIEW

| Module | Status | Focus |
|---|---|---|
| Module 1: Software Engineering | ✅ Complete | AI-assisted coding, debugging, testing, MCP, subagents, context, log analysis |
| **Module 2: System Design** | **✅ Complete** | **Databases, distributed systems, APIs, scalable architecture with AI** |
| Module 3: Platform Engineering | 🔲 Remaining | API gateway, CLI, NL-to-API, Kubernetes, IaC, CI/CD, human-in-the-loop |
