# Part 2: SYSTEM DESIGN

## MILESTONE 1: Core Building Blocks

### Module 1: Relational Databases

### Class Topics

- Relational Model: Tables, Keys, Constraints, Normalization
- Indexing Strategies: B-Tree, Composite, Covering Indexes
- Query Optimization: EXPLAIN Plans, Slow Query Logs, N+1
- Natural Language to SQL with AI
- Schema Design with AI

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
- DB Protection Hook: Whitelist SQL Operations
- GitHub Actions Slow Query Detection on Migration PRs

### AI Exam

- Legacy Schema Redesign


### Module 2: NoSQL & Caching

### Class Topics

- NoSQL Data Models: Document, Key-Value, Wide-Column, Time-Series
- MongoDB: Collections, Aggregation Pipelines, Schema-on-Read
- Redis: Data Structures, TTL, Eviction, Cache vs. Primary Store
- Cache Strategies: Cache-Aside, Read-Through, Write-Through
- AI-Assisted Data Store Selection

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
- PostgreSQL FTS vs. LIKE Query Benchmark
- MongoDB Atlas Search or Elasticsearch Query DSL

**Infrastructure**

- Docker Compose: PostgreSQL + MongoDB + Redis Data Stack
- All Three Stores Exposed as MCP Servers

### AI Exam

- Multi-Store Domain Design


### Module 3: API Design & Communication Protocols

### Class Topics

- REST Design Principles and Versioning
- GraphQL: Schema-First Design and N+1 in Resolvers
- gRPC: Protocol Buffers, Streaming, When to Use
- API Gateway Patterns: Routing, Auth, Rate Limiting
- AI-Generated OpenAPI Spec Review

### Hands-On Labs

**REST & GraphQL with AI**

- OpenAPI Spec Generation and Design Review
- REST vs. GraphQL Benchmark on Same Endpoints
- N+1 GraphQL Resolver Fix with DataLoader

**API Security**

- JWT Authentication Middleware
- Dual-Key API Key Rotation Strategy
- Gateway-Layer Auth Enforcement with Envoy

**gRPC & API Gateway**

- .proto File for a User Service
- Envoy Gateway: REST and gRPC Routing
- Request Transformation Lua Filter
- REST API as MCP Server with Auth Headers

**Infrastructure**

- Docker Compose: REST + GraphQL + gRPC + Envoy
- Nginx Path Prefix Routing: /db, /api, /grpc
- GitHub Actions OpenAPI Breaking-Change Detection

### AI Exam

- Notification Service API Layer


## MILESTONE 2: Scaling Strategies

### Module 4: Replication, Sharding & Consistency

### Class Topics

- CAP Theorem: Consistency, Availability, Partition Tolerance
- Replication: Leader-Follower, Multi-Leader, Leaderless
- Sharding: Range, Hash, Directory, Consistent Hashing
- Consistency Models: Strong, Eventual, Read-Your-Writes
- AI-Assisted Replication and Shard Strategy Design

### Hands-On Labs

**Replication with AI**

- PostgreSQL Leader-Follower Replication Setup
- Replication Lag Simulation and Fix
- Failover Drill: Kill Leader, Promote Follower

**Sharding with AI**

- Consistent Hashing Implementation
- Shard Strategy Design for Module 1 Message Broker
- Hot Shard Detection and Rebalancing Plan

**Backup & Recovery**

- Continuous WAL Archiving to S3
- Point-in-Time Recovery Drill
- Backup Verification with Checksum Comparison

**Infrastructure**

- 3-Node PostgreSQL Cluster with HAProxy on Docker Compose
- AWS RDS Multi-AZ vs. Self-Managed Failover Comparison
- Prometheus Replication Lag Alert

### AI Exam

- Replication and Sharding Failover Demo


### Module 5: Load Balancing, Rate Limiting & CDN

### Class Topics

- Load Balancing Algorithms: Round-Robin, Least Connections, IP Hash
- Layer 4 vs. Layer 7 Load Balancing
- Rate Limiting Patterns: Token Bucket, Sliding Window, Fixed Window
- CDN: Edge Caching, Cache-Control, Origin Shield
- AI Traffic Pattern Analysis

### Hands-On Labs

**Load Balancing**

- Nginx Layer 7 Load Balancer with Health Checks
- Round-Robin vs. Least-Connections Under Spike Traffic
- Redis Sliding Window Rate Limiter

**CDN & Caching**

- Cache-Control Header Configuration for REST API
- TTFB Benchmark: With and Without Nginx Caching Proxy
- Cache Poisoning Attack and Mitigation Headers
- CDN Invalidation Script

**Infrastructure**

- Docker Compose: 3 API Replicas + Nginx + Redis Rate Limiter
- Prometheus + Grafana: RPS, Error Rate, p99 Latency Per Upstream

### AI Exam

- Traffic Management Layer Load Test


### Module 6: Message Queues & Event-Driven Architecture

### Class Topics

- Why Async: Decoupling, Buffering, Retry and Replay
- Message Queue Patterns: Point-to-Point, Pub-Sub, Fan-Out, DLQ
- Kafka: Topics, Partitions, Consumer Groups, Retention
- Event-Driven Patterns: Event Sourcing, CQRS, Sagas
- Connection to Module 1 Message Broker

### Hands-On Labs

**Message Queue Patterns**

- Point-to-Point and Pub-Sub on RabbitMQ
- Dead-Letter Queue with Retry Policy
- Fan-Out: One Producer, Three Consumers

**Kafka with AI**

- Kafka Cluster Setup on Docker Compose
- Consumer Group Rebalancing Observation
- Kafka Trigger for Module 1 Serverless Platform

**Event-Driven Patterns**

- CQRS: Separate Write and Read Models
- Distributed Saga with Compensating Transactions

### AI Exam

- Message Broker Migration to Kafka


## MILESTONE 3: System Evolution

### Module 7: DB Migration & Schema Evolution

### Class Topics

- Schema Migration Strategies: Expand-Contract Pattern
- Migration Tooling: Flyway, Alembic, Liquibase
- Risk Assessment: Table Locks, Backfills, Constraint Additions
- AI Migration Planning: SQL, Risk, Rollback Script
- Rollback Planning: Down Before Up

### Hands-On Labs

**Migration Planning with AI**

- Schema Change: Migration SQL, Risk Assessment, Rollback Script
- Dangerous Migration Identification and Safe Alternative
- 10M Row Backfill Dry-Run with EXPLAIN ANALYZE

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

### Class Topics

- Monolith vs. Microservices: When the Split is Worth It
- Service Discovery: Consul, Kubernetes DNS
- Inter-Service Communication: Sync vs. Async
- Distributed Tracing Across Multiple Services
- AI for Bottleneck Identification in Traces

### Hands-On Labs

**Microservices Decomposition with AI**

- Serverless Platform Decomposed into 3 Microservices
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

- Docker Compose: 3 Microservices + Consul + Envoy + Prometheus + Tempo + Grafana
- Grafana Service Map Dashboard
- AWS CloudWatch and Alertmanager for Production Alerting
- Terraform: Isolated EC2 Per Microservice
- AWS Lambda for Event-Driven Stateless Services

### AI Exam

- Microservices Failure Diagnosis and Recovery


## MILESTONE 4: Designing Real Systems

### Module 9: Classic System Design Problems

### Class Topics

- System Design Framework: Requirements → Scale → Data → API → Components
- AI as Design Partner: Challenge Every Component
- Back-of-Envelope Scale Estimation
- Common Patterns: Write-Heavy, Hot Key, Fan-Out on Write vs. Read
- Tradeoff Vocabulary: Consistency, Latency, Throughput, Simplicity

### Hands-On Labs

**Design Sessions with AI**

- URL Shortener: Full Design, 2 Flaws Forced, Redesign
- Notification System: Queue Topology and Failure Scenarios
- News Feed: Fan-Out on Write vs. Read Decision and Defense

**Tradeoff Analysis with AI**

- Tradeoff Table: What Breaks at 10x Scale
- Rate Limiter: 3 Implementations Benchmarked
- Hot Key Mitigation: Local Cache and Jitter

**Build: URL Shortener & Notification System**

- URL Shortener: FastAPI + PostgreSQL + Redis + Nginx, 10K req/s Load Test
- Notification System: FastAPI → RabbitMQ → Workers with DLQ

### AI Exam

- Live System Design Session


## MILESTONE 5: AI-Native Operations

### Module 10: Natural Language DB Interaction & Log Analysis

### Class Topics

- Database as MCP Server: Query, Explain, Profile via Agent
- NL-to-Database Pipeline: Intent → SQL → Execute → Answer
- DB Monitoring: Query Latency, Pool Saturation, Lock Waits
- Log Analysis at Scale: Cost-Effective Classification First
- AI-Driven Incident Response

### Hands-On Labs

**Natural Language DB Interface**

- Module 1 MCP Infrastructure Reconfigured for Module 2 Databases
- Plain English Queries Across PostgreSQL, MongoDB, and Redis
- NL Failure Mode Documentation and Disambiguation Fix
- Cross-Store Query: Sessions Without DB Records

**DB Monitoring with AI**

- pg_stat_statements Query Cost Analysis via MCP
- PgBouncer Pool Exhaustion Root Cause
- Replication Lag Incident Summary from Prometheus Alert

**Log Analysis with Cost-Effective Models**

- Module 1 Tiered Log Pipeline Applied to DB Logs
- DB-Specific Escalation Rules: Deadlocks, Lock Waits
- Token Reduction Comparison vs. Module 1 Baseline

**Infrastructure**

- Dockerized MCP Servers with Health Checks
- Docker Compose: MCP Servers + Nginx Reverse Proxy
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
