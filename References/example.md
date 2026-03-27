# MASTERING AWS & DEVOPS

## MILESTONE 1: Linux, Scripting & Containerization

### Module 1: Linux Fundamentals

### Class Topics

- Introduction to Linux
- Basic Shell Commands
- Linux Process and Job Control
- System Logging and Monitoring

### Hands-On Labs

**Linux Fundamentals**

- Linux Commands Practice
- Setting Up a Linux Environment

### AI Exam

- Linux Server Health Check

---

### Module 2: Text Processing & Regular Expressions

### Class Topics

- Advanced Text Processing with awk sed and grep
- Regular Expressions in Linux

### Hands-On Labs

**Text Processing & Log Analysis**

- Log Analysis with awk and grep
- Bulk File Editing with sed
- Pattern Matching with Regular Expressions

### AI Exam

- Server Log Analysis with awk & sed

---

### Module 3: Linux Networking & Security

### Class Topics

- Linux Networking Commands (ip netstat ss)
- Firewall Management with iptables
- Network Troubleshooting Tools
- Linux Security Fundamentals

### Hands-On Labs

**Network Configuration & Security**

- Network Interface Configuration with ip Command
- Implementing Firewall Rules with iptables
- Network Troubleshooting Scenarios

### AI Exam

- Linux Networking and Firewall Setup

---

### Module 4: Bash Scripting & Automation

### Class Topics

- Bash Scripting Fundamentals
- Advanced Bash Scripting for DevOps

### Hands-On Labs

**Bash Scripting & Automation**

- Automated System Health Check Script
- Log Rotation and Cleanup Script
- Automated Backup Solution
- Server Monitoring Script
- Docker Container Management Scripts
- Git Operations Automation
- Deployment Automation Scripts
- Service Management Automation

**System Administration & Security**

- Performance Monitoring and Tuning
- Security Hardening Scripts

### AI Exam

- Bash Automation for Server Maintenance

---

### Module 5: Linux & Container Network Namespace Fundamentals

### Class Topics

- Understanding Linux Network Namespace
- Understanding Container Network Namespace
- Creating Custom Docker Network

### Hands-On Labs

**Network Namespace Fundamentals**

- Network Namespace Inspection and Management
- Connecting Network Namespace to Host System
- Root Network Namespace Integration

**Advanced Network Configuration**

- Managing Egress Traffic Flow
- Connecting Multiple Custom Network Namespaces
- Configuring and Managing iptables Rules

### AI Exam

- Container Network Namespace Connectivity

---

### Module 6: Overlay Networking & Network Simulation

### Class Topics

- Understanding Overlay Networking
- Simulating Network Topology with Mininet

### Hands-On Labs

**Bridge Networking & Communication**

- Implementing Bridge Networking Between Namespaces
- Inter-Process Communication Across Namespaces
- Understanding and Implementing FIB Network Topology

**Overlay Networking**

- VXLAN For Overlay Networking
- VXLAN With IPAM
- FDB With VXLAN

**Network Simulation with Mininet**

- Two-Subnet Network Topology with Routing using Mininet
- Simulating a Simple Network with Mininet

### AI Exam

- VXLAN Overlay Network Setup

---

### Module 7: Docker Fundamentals & Container Lifecycle

### Class Topics

- Docker Architecture and Components
- Docker Objects

### Hands-On Labs

**Container Basics**

- Launch mysql using Docker
- The Lifecycle of a Container
- Differentiating Docker stop vs Kill
- Docker Container Restart Policies
- Automatic Restart of Docker Containers

### AI Exam

- Docker Container Lifecycle Management

---

### Module 8: Docker Image Management & Optimization

### Class Topics

- Docker Registry
- Docker image optimization

### Hands-On Labs

**Docker Image Management**

- Docker Search Command
- Filtering Docker Images
- Create Own Docker Image
- Docker Image Layer Sharing and Digest
- Building Docker Images from a Container
- Create and Commit Ubuntu Container with Git
- Reviewing Filesystem Changes
- Modifying Docker Image Attributes
- Exploring Image Layers and Size Management

### AI Exam

- Docker Image Build and Optimization

---

### Module 9: Docker Networking & Storage

### Class Topics

- Docker Networking
- Docker Volume & Storage

### Hands-On Labs

**Container Networking**

- Communication Between Containers in Bridge Network
- Exploring Bridge Networks in Docker

**Storage & Data Management**

- Docker Bind Mounts
- In-memory Storage
- Working with Docker Volumes
- Setting Up Read-Only File Systems
- Log Sharing Between Containers

### AI Exam

- Docker Networking and Volume Management

---

### Module 10: Web Applications & Multi-Container Deployments

### Class Topics

- Docker for Web Applications
- Introduction to Docker Compose
- Deploying Multi-Container Applications

### Hands-On Labs

**Web Applications Deployment**

- Running an NGINX Web Server in Docker
- Deploying a Monitored NGINX Web Server
- Setting Up a Host-Like Environment
- Keeping Containers Running with Supervisor

**Advanced Docker Concepts**

- Containerizing a Single-Container App
- Multi-stage Builds with Node.js
- Introduction to Docker Compose
- Deploying Multi-Container Applications

### AI Exam

- Multi-Container App with Docker Compose

---

### Module 11: Makefile for Automation

### Class Topics

- Introduction to Makefile
- Makefile Syntax and Rules

### Hands-On Labs

**Makefile Fundamentals**

- Introduction to Makefile Syntax
- Building Simple Programs with Make
- Managing Dependencies in Makefile
- Using Variables and Patterns
- Conditional Statements in Makefile

**Docker Automation with Make**

- Docker Build Automation
- Multi-stage Docker Builds using Make
- Managing Multiple Dockerfiles
- Docker Compose with Make
- Container Lifecycle Management
- Image Cleanup and Maintenance

**Development Workflow Automation**

- Local Development Setup
- Test Environment Management
- Database Migration Automation
- Code Linting and Formatting
- Running Test Suites

### AI Exam

- Docker Build Automation with Makefile

---

### Module 12: Micro-service With Docker

### Class Topics

- Understanding Microservices Architecture
- Using Docker for Microservices
- CI/CD with GitHub Actions [Bonus Class]

### Hands-On Labs

**Microservices Basics**

- Building Microservices with Docker
- Deploying Microservices using Docker

**Service Implementation**

- Creating a User Service (FastAPI + PostgreSQL)
- Building a Product Service (FastAPI + MySQL)
- Implementing an Order Service (FastAPI + MongoDB)

**API Gateway & Communication**

- Setting up API Gateway using Nginx
- Order Processing with RabbitMQ
- Email Notification Service with Redis Queue
- Event Streaming with Apache Kafka

**Lab for Bonus Class**

- Basic Docker CI Pipeline
- Multi-stage Build Pipeline

### AI Exam

- Dockerized Microservices Deployment

---

## MILESTONE 2: Cloud Fundamentals with AWS

### Module 13: AWS EC2 & Storage Fundamentals

### Class Topics

- Introduction to AWS Services for DevOps
- EC2 - S3 and Lambda Overview

### Hands-On Labs

**AWS EC2 & Storage Fundamentals**

- Launch An Ec2 Instance In A Virtual Private Cloud (vpc)
- Deploying a Bastion Server in a Public Subnet
- Mount EC2 storage with EBS volume
- Copy EC2 instance using Snapshot
- Snapshot From EBS
- Mount EC2 with EBS

### AI Exam

- EC2 Instance and EBS Management

---

### Module 14: VPC Design & Network Architecture

### Class Topics

- AWS VPC - LoadBalancer Overview

### Hands-On Labs

**VPC & Network Architecture**

- Creating and Configuring a Secure AWS VPC with Public and Private Subnets
- Create a Secure SSH connection between a Bastion Server and a Private Instance
- Building a Three-Tier Network VPC from Scratch in AWS
- AWS VPC Peering Lab

### AI Exam

- AWS VPC and Subnet Design

---

### Module 15: Application Deployment on EC2 with systemd

### Class Topics

- Application Deployment Patterns on EC2 with systemd

### Hands-On Labs

**Application Deployment with Systemd**

- Deploying MySQL in a Private Subnet on AWS using Docker Compose
- Deploying MySQL in EC2 Using Systemd
- Deploy MONGODB in EC2 using Systemd
- Deploy Nginx in EC2 using systemd
- Deploy a simple Flask app in EC2 using systemd
- Deploy a FastAPI application on an EC2 instance using systemd
- Deploy Redis on EC2 Using Systemd

### AI Exam

- EC2 Application Deployment with systemd

---

### Module 16: Serverless & Lambda Fundamentals

### Class Topics

- What is Serverless Architecture?
- AWS Lambda Overview

### Hands-On Labs

**Lambda Basics**

- Introduction to AWS Lambda Function
- Creating an EC2 Instance with Lambda
- Utilizing S3 Data Using Lambda and API Gateway

### AI Exam

- AWS Lambda Function Deployment

---

### Module 17: Event-Driven Architectures with Lambda

### Class Topics

- Event-driven Patterns with Lambda, API Gateway, and S3

### Hands-On Labs

**Event-Driven Serverless Applications**

- Building a Serverless Application Using Step Functions, API Gateway, Lambda, and S3 in AWS
- AWS S3 Event Notification with Lambda and SES
- Automated EC2 Deployment & MySQL Management with Lambda & API Gateway
- Deploying a Serverless Application Using AWS Lambda, API Gateway, and DynamoDB
- Automated EC2 Deployment & MongoDB Management with Lambda & API Gateway
- Automated EC2 Deployment & PostgreSQL Management with Lambda & API Gateway

### AI Exam

- Event-Driven App with Lambda & API Gateway

---

### Module 18: Multi-VPC & Private Connectivity

### Class Topics

- AWS Transit Gateway & Multi-VPC Architecture
- AWS PrivateLink & VPC Endpoints
- VPN Connections & Site-to-Site VPN

### Hands-On Labs

**Advanced VPC Architecture**

- Implementing AWS Transit Gateway for Multi-VPC Communication
- Configuring AWS PrivateLink for Private Service Access
- Setting Up VPC Endpoints (Gateway & Interface Endpoints)

### AI Exam

- Multi-VPC Connectivity with Transit Gateway

---

### Module 19: Edge Services, DNS & Load Balancing

### Class Topics

- AWS Route 53 - Advanced DNS Configuration
- AWS CloudFront & Global Accelerator
- Network Load Balancer vs Application Load Balancer (Advanced Features)

### Hands-On Labs

**Hybrid Cloud & DNS**

- Implementing AWS Direct Connect (Simulated Environment)
- Advanced Route 53 Configuration with Health Checks and Routing Policies

### AI Exam

- Route 53, CloudFront and Load Balancing

---

### Module 20: Network Security & Monitoring

### Class Topics

- AWS WAF, Shield & Network Security
- VPC Flow Logs & Network Monitoring
- AWS Network Firewall

### Hands-On Labs

**Security & Monitoring**

- Deploying AWS WAF with Application Load Balancer
- Implementing VPC Flow Logs and Network Monitoring Dashboard

### AI Exam

- AWS Network Security with WAF and Flow Logs

---

## MILESTONE 3: Infrastructure as Code (IaC) & Server Management

### Module 21: Pulumi As IAC

### Class Topics

- Introduction to Infrastructure as Code
- Getting Started with Pulumi

### Hands-On Labs

**Pulumi Basics**

- Setting Up a VPC with Public Subnet, Route Table, and Internet Gateway
- VPC with Public and Private Subnets, Route Tables, IGW, and NAT Gateway
- Launch EC2 Instances in Public and Private Subnets
- SSH from Public Subnet Instance to Private Subnet Instance

### AI Exam

- AWS Infrastructure with Pulumi

---

### Module 22: Terraform Core Concepts & State

### Class Topics

- Terraform Basics
- Terraform providers
- Input Variables and Variable Blocks
- Using Variables in Terraform
- Resource Attributes & Dependencies
- Output Variables
- Terraform States
- Working With Terraform
- Remote state
- Terraform Functions and Conditional Expression

### Hands-On Labs

**Terraform Setup & HCL Basics**

- Terraform Installation and CLI Setup
- Writing First HCL Configuration
- Update and Destroy Infrastructure Safely

**Core Terraform Language & Workflow**

- Using Input Variables and Variable Blocks
- Using Variables in Terraform Across Multiple Resources
- Working with Resource Attributes & Dependencies
- Defining and Consuming Output Variables
- Using Terraform Built-In Functions and Conditional Expressions

**Working with Terraform Commands & Meta-Arguments**

- Basic Terraform Commands (init, fmt, validate, plan, apply, destroy)
- Using Lifecycle Rules in Terraform
- Using Data Sources in Terraform
- Using Meta-Arguments (`count` and `for_each`) in Terraform

**Terraform Core & State**

- Understanding Terraform State and Its Purpose
- State Considerations in Team Environments
- Remote State and Remote Backends (S3, etc.)
- Remote State Commands and State Management
- Remote State & State Locking with S3 and DynamoDB

### AI Exam

- Terraform State and Core Workflow

---

### Module 23: Terraform for AWS Networking & Compute

### Class Topics

- Terraform with AWS
- Terraform Provisioners
- Terraform Import - taints and debugging

### Hands-On Labs

**Core AWS Resources with Terraform**

- Creating an S3 Bucket in AWS with Terraform
- Creating an IAM Role and Policy in AWS with Terraform
- AWS EC2 with Terraform

**Terraform Provisioners & Operations**

- Using Terraform Provisioners for EC2 Configuration
- Using `terraform import` for Existing AWS Resources
- Handling `terraform taint` and Resource Recreation
- Debugging Terraform Plans and Applies

**AWS Infrastructure with Terraform**

- Securing Private Subnet Access with a Bastion Server using Terraform
- 3-tier architecture using terraform
- VPC peering using terraform

**Advanced AWS Services**

- AWS ALB using terraform
- AWS Autoscaling using terraform
- Deploying a Simple AWS Lambda Function Using Terraform

**Practical Labs with Terraform**

- Github action AWS infra with terraform

### AI Exam

- Terraform AWS Networking and Compute

---

### Module 24: Terraform Modules & Best Practices

### Class Topics

- Terraform Modules

### Hands-On Labs

**Terraform Modules & Reuse**

- Terraform Modules with the Local Provider
- Refactoring Infrastructure into Reusable Modules (conceptual and practical exercises based on previous labs)
- Multi-Environment Infrastructure with Shared Network in Terraform
- AWS Network Infrastructure Using Terraform Registry Modules

### AI Exam

- Reusable Terraform Modules Design

---

### Module 25: Ansible Fundamentals

### Class Topics

- Ansible Overview

### Hands-On Labs

**Ansible Fundamentals**

- Getting Started with Ansible: Setup and Running Ad-hoc Commands

### AI Exam

- Ansible Ad-hoc Commands on Servers

---

### Module 26: Application Installation & Configuration with Ansible

### Class Topics

- Application Installation Patterns with Ansible

### Hands-On Labs

**Application Installation & Configuration**

- Installing Nginx Using Ansible
- Installing Jenkins on an EC2 Instance Using Ansible Playbook
- Installing MySQL on an EC2 Instance Using Ansible
- Installing Redis on an EC2 Instance Using Ansible Playbook
- Installing Docker on remote servers using Ansible Playbook
- Installing and Configuring PostgreSQL on Multiple EC2 Instances Using Ansible Playbook

### AI Exam

- App Installation with Ansible Playbooks

---

### Module 27: Automation, CI/CD & AWS Infrastructure with Ansible

### Class Topics

- Infrastructure Automation with Ansible
- CI/CD Integration Patterns with Ansible

### Hands-On Labs

**Automation & CI/CD Integration**

- Automating MySQL Installation on an EC2 Instance Using Ansible and GitHub Actions
- Automate Git-runner setup using Ansible
- Automating Nginx Website Deployment with Ansible

**AWS Infrastructure with Ansible**

- AWS Infrastructure Deployment with Ansible (VPC)
- AWS Infrastructure Deployment with Ansible (EC2)
- AWS Infrastructure Deployment with Ansible (Role-based)
- Launch multiple EC2 instances with different AMI IDs using Ansible and install Nginx into these instances

### AI Exam

- Ansible CI/CD and AWS Automation

---

## MILESTONE 4: Kubernetes Mastery

### Module 28: Kubernetes Setup & Configuration

### Class Topics

- Check health of the Kubernetes API endpoints
- Filtering Output with Custom Columns
- Generate Kubernetes YAMLs Easily
- List Kubernetes API Resources
- Verify Service Account Permissions

### Hands-On Labs

**Kubernetes Setup & Configuration**

- Installing Kubernetes
- Multi-node Cluster with kubeadm
- Setting up k3s Lightweight Cluster
- Configuring kubectl Contexts

### AI Exam

- Kubernetes Cluster Setup and kubectl

---

### Module 29: Core Kubernetes Concepts

### Class Topics

- Pods, ReplicaSets, and Deployments Overview
- Services, Namespaces, ConfigMaps & Secrets

### Hands-On Labs

**Core Kubernetes Concepts**

- Creating and Managing Pods
- Working with ReplicaSets
- Deployment Strategies
- Service Types and Networking
- Understanding Namespaces
- ConfigMaps and Secrets

### AI Exam

- Deploying Apps with Kubernetes Core Objects

---

### Module 30: Storage & Deployment Strategies

### Class Topics

- Persistent Volumes, PVCs, and Storage Classes
- StatefulSets and Deployment Strategies Overview

### Hands-On Labs

**Storage & Stateful Applications**

- Persistent Volumes (PV)
- Persistent Volume Claims (PVC)
- Storage Classes
- StatefulSet Applications

**Deployment Strategies**

- Blue-Green Deployments
- Canary Deployments
- Rolling Updates
- Scaling Applications

### AI Exam

- Kubernetes Storage and Stateful Deployments

---

### Module 31: Resource Management & Advanced Networking

### Class Topics

- Resource Quotas, Limits, and Networking Concepts
- Ingress, Network Policies, Load Balancing & External DNS

### Hands-On Labs

**Resource Management**

- Resource Quotas and Limits

**Advanced Networking**

- Service Mesh with Istio
- Ingress Controllers
- Network Policies
- Load Balancing
- External DNS Configuration

### AI Exam

- Resource Quotas and Ingress Configuration

---

### Module 32: Monitoring, Observability & Security

### Class Topics

- Kubernetes Monitoring Overview (Prometheus, Grafana, ELK, Dashboard)
- RBAC, Pod Security, Network Security & Secret Management

### Hands-On Labs

**Monitoring & Observability**

- Prometheus Setup
- Grafana Dashboards
- ELK Stack Integration
- Kubernetes Dashboard

**Security & Access Control**

- RBAC Configuration
- Pod Security Policies
- Network Security Policies
- Secret Management
- Container Security Scanning

### AI Exam

- Kubernetes RBAC and Security Hardening

---

### Module 33: Stateful Services, Messaging & CI/CD

### Class Topics

- Database Clusters and Message Queues on Kubernetes
- CI/CD Integration and Auto-scaling on Kubernetes

### Hands-On Labs

**Stateful Services & Messaging**

- Database Clusters (MySQL PostgreSQL)
- Message Queues (RabbitMQ Kafka)

**CI/CD & Scaling**

- CI/CD Pipeline Integration
- Auto-scaling Applications
- Deploying Applications on Kubernetes

### AI Exam

- Stateful Services and Messaging on Kubernetes

---

### Module 34: Kubernetes Networking Internals

### Class Topics

- Infrastructure Setup for Kubernetes Cluster with Terraform
- Kubernetes Cluster Setup on AWS EC2 Instances
- Network Interfaces for Kubernetes Pod Communication with Bash CNI
- Dynamic IP Assignment for Kubernetes Pods with Bash CNI
- Fixing Pod Connectivity and External Access in Kubernetes

### Hands-On Labs

**Network Configuration**

- Configuring Kubernetes Network Policies
- Networking with Services

### AI Exam

- Kubernetes Pod Networking Internals

---

### Module 35: Cilium in Kubernetes — Concepts & Installation

### Class Topics

- What is Cilium and Why It’s Used (CNI overview, comparison with iptables/kube-proxy)
- Cilium Core Components: Agent and Operator
- Where Cilium Sits in Kubernetes Networking
- Pod-to-Pod Communication and Service Handling with Cilium (ClusterIP, kube-proxy replacement)
- Basic Cilium NetworkPolicy (L3/L4), Hubble Intro & Operational Checks

### Hands-On Labs

**Cilium Installation & Configuration**

- Installing Cilium CNI in Kubernetes Cluster
- Verifying Cilium Installation and Checking Component Status
- Understanding Cilium Agent and Operator Logs

### AI Exam

- Cilium Installation and Component Verification

---

### Module 36: Cilium — Network Policy, Service Mesh & Observability

### Class Topics

- Cilium Network Policies in Practice (L3/L4, DNS-based, Pod-to-Pod)
- Cilium Service Mesh, kube-proxy Replacement & Hubble Observability

### Hands-On Labs

**Network Policy with Cilium**

- Creating Basic L3/L4 Network Policies with Cilium
- Implementing Pod-to-Pod Communication Policies
- Configuring DNS-based Network Policies

**Service Mesh & Traffic Management**

- Replacing kube-proxy with Cilium
- Configuring ClusterIP Services with Cilium
- Testing Service Discovery with Cilium

**Observability with Hubble**

- Installing and Configuring Hubble UI
- Visualizing Network Traffic with Hubble
- Analyzing Service Dependencies and Traffic Flow
- Troubleshooting Network Issues with Hubble CLI

### AI Exam

- Cilium Network Policies and Hubble Observability

---

### Module 37: Microservices With Kubernetes

### Class Topics

- Building Microservices with Kubernetes
- Deploying Microservices on Kubernetes

### Hands-On Labs

**Database Integration**

- Deploy MySQL into Kubernetes and test connectivity from a Ubuntu container
- Flask App and MySQL Deployment in Kubernetes
- Create Flask and MySQL deployments using secrets

### AI Exam

- Microservices with Database on Kubernetes

---

### Module 38: Kubernetes The Hard Way

### Class Topics

- Kubernetes Installation Methods
- The Hard Way Approach

### Hands-On Labs

**Infrastructure & Certificates**

- Kubernetes the Hard Way on AWS: Infrastructure Setup
- Provisioning CA and Generating TLS Certificates for Kubernetes
- Generating Kubernetes Configuration Files for Authentication

**Control Plane & Workers**

- Bootstrapping the etcd Cluster
- Bootstrapping the Kubernetes Control Plane
- Bootstrapping the Kubernetes Worker Nodes

**Network & Validation**

- Provisioning Pod Network Routes
- Smoke Test

### AI Exam

- Kubernetes the Hard Way Bootstrap

---

### Module 39: Helm Fundamentals

### Class Topics

- What is Helm and Helm Chart Structure
- Helm Templating Engine
- Create Helm Chart From Scratch
- Validate, Deploy, Upgrade, Rollback & Uninstall Helm Releases
- Package the Helm Chart

### Hands-On Labs

**Helm Fundamentals**

- Introduction to Helm & Installation
- Chart Structure & Creating Your First Chart
- Helm Templating Deep Dive
- Validation & Multi-Environment Configs
- Release Lifecycle (Upgrade, Rollback, Uninstall)
- Package, Version & Publish Charts

### AI Exam

- Helm Chart Creation and Release Management

---

### Module 40: Helm — Debugging, Best Practices & Application Deployment

### Class Topics

- Chart Validation, Testing & Debugging Helm Charts
- Helm Chart Possible Errors & Best Practices

### Hands-On Labs

**Application Deployment with Helm**

- Deploy Flask Application With Helm
- Deploy Nodejs Application With Helm
- Deploy mysql With Helm
- Deploy Redis With Helm
- Deploy Rabbitmq With Helm

### AI Exam

- Helm Chart Debugging and App Deployment

---

### Module 41: Kustomize For Deployment

### Class Topics

- What is Kustomize, Why Use It & Use Cases
- Multi-Environment Deployments and Feature Flags
- Configuration Management and Resource Customization

### Hands-On Labs

**Multi-Environment Configuration**

- Kustomize: Simplifying Kubernetes Configurations for Multiple Environments
- Kustomize in Practice: Managing Kubernetes Configurations Across Environments
- Deploying NGINX Web Server in Multiple Environments with Kustomize

**Configuration Management**

- Generating ConfigMaps Using Kustomize

### AI Exam

- Kustomize Multi-Environment Configuration

---

## MILESTONE 5: Observability Stack (Monitoring, Logging, Tracing)

### Module 42: Prometheus For Monitoring (Basic)

### Class Topics

- Understanding Monitoring Concepts
- Introduction to Prometheus

### Hands-On Labs

**Prometheus Basics**

- Setting Up Prometheus
- Monitoring Applications with Prometheus

### AI Exam

- Prometheus Setup and App Monitoring

---

### Module 43: Prometheus Advanced — Architecture, Metrics & PromQL

### Class Topics

- Introduction to Prometheus Architecture
- Understanding Metrics Types
- PromQL Query Language Basics

### Hands-On Labs

**Kubernetes Monitoring Setup**

- Deploying Prometheus in Kubernetes
- Installing Prometheus Operator
- Configuring ServiceMonitors

**Query Language & Dashboards**

- Basic PromQL Queries
- First Grafana Dashboard
- Creating Dashboards for Kubernetes Monitoring

### AI Exam

- PromQL Queries for Kubernetes Monitoring

---

### Module 44: Prometheus Advanced — Alert Management

### Class Topics

- Alert Manager Overview
- Grafana Integration
- SLI/SLO Implementation

### Hands-On Labs

**Alert Management**

- Setting up Alert Manager
- Basic Alert Rules
- Alert Manager Setup
- Notification Channels
- Alert Routing
- Silencing and Inhibition

### AI Exam

- Alertmanager Rules and Notification Routing

---

### Module 45: Prometheus Advanced — Container & Docker Monitoring

### Class Topics

- Container Metrics and Exporters
- cAdvisor Integration
- Docker Container Monitoring Best Practices
- Resource Usage Metrics

### Hands-On Labs

**Container & Docker Monitoring**

- Container Metrics Collection
- Setting up cAdvisor
- Docker Container Labels
- Resource Usage Monitoring
- Container Health Checks

### AI Exam

- Container Metrics with cAdvisor

---

### Module 46: Prometheus Advanced — Node & Cluster Monitoring

### Class Topics

- Node Exporter
- Service Discovery in Kubernetes
- Custom Metrics API
- High Availability Prometheus Setup & Federation

### Hands-On Labs

**Node & Cluster Monitoring**

- Node Exporter Configuration
- kube-state-metrics Setup
- Custom ServiceMonitors
- Namespace Monitoring
- Cluster Overview Dashboard
- Node Performance Metrics
- Pod Resource Usage
- Network Traffic Visualization
- Custom Metrics Dashboards

### AI Exam

- Node and Cluster Health Monitoring

---

### Module 47: Prometheus Advanced — Application Monitoring & Custom Exporters

### Class Topics

- Custom Exporters Development
- Federation and Remote Storage
- Monitoring Security Aspects

### Hands-On Labs

**Application & Service Monitoring**

- Monitoring Microservices
- Database Monitoring
- Application Performance
- SLO Implementation

### AI Exam

- Custom Exporter and SLO Definition

---

### Module 48: Grafana — Setup & Dashboards

### Class Topics

- Introduction to Grafana
- Integrating Grafana with Kubernetes
- Building Grafana Dashboards

### Hands-On Labs

**Grafana Setup**

- Setting Up Grafana in Kubernetes
- Creating Visualizations

**Dashboard Creation**

- Creating Your First Dashboard
- Integrating Grafana with Data Sources

### AI Exam

- Grafana Dashboards for Kubernetes Metrics

---

### Module 49: Loki — Deployment & Logging

### Class Topics

- What is Loki and Why Use It for Log Management
- Deploying Loki on Kubernetes

### Hands-On Labs

**Loki Deployment**

- Deploying Loki in Kubernetes
- Collecting Logs from Applications

**Application Logging**

- Logging For Flask API
- Logging For Fast API
- Logging For Express API

### AI Exam

- Application Log Aggregation with Loki

---

### Module 50: Tempo & OpenTelemetry — Distributed Tracing

### Class Topics

- Understanding Observability and Distributed Tracing
- Deploying Tempo in Kubernetes
- Introduction to OpenTelemetry

### Hands-On Labs

**Distributed Tracing**

- Tracing Requests with Tempo
- Using Tempo with Grafana

**OpenTelemetry Integration**

- Setting Up OpenTelemetry
- Tracing with Tempo

### AI Exam

- Distributed Tracing with Tempo and OpenTelemetry

---

## MILESTONE 6: Production-Grade CI/CD & GitOps

### Module 51: CI/CD For Docker

### Class Topics

- CI/CD Fundamentals for Containerized Applications
- Docker Build Optimization & Image Scanning
- Automated Testing for Docker
- Container Registry Management

### Hands-On Labs

- Basic Docker CI Pipeline
- Multi-stage Build Pipeline
- Image Scanning and Security Checks
- Automated Testing in Docker
- Docker Registry Integration
- Docker Compose CI/CD

### AI Exam

- Docker CI Pipeline with Image Scanning

---

### Module 52: Deployment of Microservices With AWS

### Class Topics

- Building Microservices on AWS
- AWS ECS Overview

### Hands-On Labs

**AWS ECS & Fargate**

- Deploying Microservices to AWS
- Using AWS Fargate

### AI Exam

- Microservices Deployment on AWS ECS

---

### Module 53: GitOps Fundamentals — Principles & Workflows

### Class Topics

- Introduction to GitOps Principles and GitOps vs Traditional CI/CD
- Benefits, Challenges & GitOps Workflows and Patterns
- Git as Single Source of Truth and Pull-based vs Push-based Deployment

### Hands-On Labs

**GitOps Fundamentals**

- Setting Up a GitOps Repository Structure
- Implementing Pull-based Deployment with Git Webhooks
- Creating Multi-Environment GitOps Workflows (Dev, Staging, Prod)

### AI Exam

- GitOps Repository and Pull-based Deployment

---

### Module 54: GitOps — Kubernetes, Security & Implementation

### Class Topics

- GitOps for Kubernetes and Multi-Environment GitOps Strategies
- GitOps Tooling Landscape (ArgoCD, Flux, Jenkins X)
- GitOps Security Best Practices, Secrets Management & Monitoring

### Hands-On Labs

**GitOps Implementation**

- Implementing GitOps with Kubernetes Manifests
- Integrating Secrets Management in GitOps (Sealed Secrets, External Secrets)
- Building a Complete GitOps Pipeline with Multiple Environments
- Implementing GitOps Monitoring and Drift Detection

### AI Exam

- GitOps on Kubernetes with Secrets Management

---

### Module 55: ArgoCD — Fundamentals & Multi-Environment Management

### Class Topics

- Introduction to GitOps and Getting Started with ArgoCD
- ArgoCD Multi-Environment Management, Helm Integration & Security

### Hands-On Labs

**ArgoCD Fundamentals**

- Basic ArgoCD Setup and Configuration
- Simple Application Deployment

**Multi-Environment & Integration**

- Multi-Environment Management
- GitOps Pipeline
- Helm Integration
- Private Repository Integration

**Security & Access Control**

- RBAC and Security

### AI Exam

- ArgoCD Setup and Multi-Environment Management

---

### Module 56: ArgoCD — Advanced Features & Deployment Strategies

### Class Topics

- ArgoCD Advanced Features: ApplicationSet, Sync Strategy, Health Check & Disaster Recovery
- ArgoCD Notifications, Custom Plugins & Deployment Strategies

### Hands-On Labs

**Advanced ArgoCD Features**

- ApplicationSet
- Sync Strategy
- Health Check
- Disaster Recovery
- Notification and Monitoring
- Custom Plugin

**Deployment Strategies**

- Blue-Green Deployment
- Canary Deployment

### AI Exam

- ArgoCD ApplicationSets and Sync Strategies

---

### Module 57: GitHub Actions — Fundamentals & Runners

### Class Topics

- What are GitHub Actions and Using Actions for CI/CD
- GitHub Actions Workflows and Self-Hosted Runners
- Secrets Management, Matrix Builds & Best Practices

### Hands-On Labs

**GitHub Actions Fundamentals**

- Introduction to GitHub Actions
- GitHub Actions Multiple Jobs with Dependencies
- GitHub Actions with Docker and Nginx
- Self-Hosted GitHub Actions Runner Setup
- Self Hosted Runner in Kubernetes
- Self Hosted Runner in k3s Cluster Running on AWS

### AI Exam

- GitHub Actions with Self-Hosted Runners

---

### Module 58: GitHub Actions — Infrastructure Automation

### Class Topics

- Automating AWS Infrastructure with GitHub Actions
- Using Pulumi and Terraform with GitHub Actions

### Hands-On Labs

**Infrastructure Automation**

- Creating AWS Infrastructure with GitHub Actions and SSH Access
- Automating K3s cluster Deployment in AWS Using Pulumi and GitHub Actions
- Automating Lambda Function Deployment with Pulumi and GitHub Actions
- Github action AWS infra with terraform

### AI Exam

- AWS Infrastructure Automation with GitHub Actions

---

### Module 59: GitHub Actions — Application CI/CD Pipelines

### Class Topics

- Building Application CI/CD Pipelines with GitHub Actions
- Multi-Language and Microservice Pipeline Patterns

### Hands-On Labs

**Application CI/CD Pipelines**

- Automated CI/CD Pipeline for Express.js Deployment Using GitHub Actions and Self-Hosted Runners
- Deploy React app on EC2 instance using github actions
- Auto-Deploy Go App on AWS EC2 by Building a Docker Image and Publish it to Dockerhub with CI/CD Pipeline using GitHub Actions
- Setting Up CI/CD Pipeline for Flask Application on AWS EC2 with GitHub Actions
- Building a CI/CD Pipeline for E-commerce Microservices with GitHub Actions
- Building a CI/CD Pipeline for CRUD Application with GitHub Actions

### AI Exam

- End-to-End App CI/CD with GitHub Actions

---

### Module 60: Jenkins

### Class Topics

- Understanding Jenkins and CI/CD
- Setting Up Jenkins

### Hands-On Labs

**Jenkins Setup & Configuration**

- Jenkins Installation on Ubuntu: A Step-by-Step Guide
- Creating and Managing Your First Jenkins Job
- Running Jenkins on Port 80: Two Different Methods

**Jenkins Agents & Scaling**

- Setting Up a Jenkins Agent Using SSH Keys
- Configuring Docker Containers as Build Agents in Jenkins

**Build & Deploy Pipelines**

- Building a Java Application with Maven Using Jenkins
- Automating Docker Image Builds and Pushes to Docker Hub using Jenkins
- Deploy Application On Kubernetes Using Jenkins

### AI Exam

- Jenkins Pipelines and Kubernetes Deployment

---

### Module 61: Production Deployment & Common Practices

### Class Topics

- Integrating All Components
- Best Practices for Production Deployment

### Hands-On Labs

**Full Stack Deployment**

- Building a Full Deployment Pipeline
- Deploying a Complete Application

### AI Exam

- Full Production Deployment Pipeline

**Realistic timeline: 1.5 – 2 years (18–24 months) part-time at your pace.**

### Why this number?

- **Total modules**: Exactly **60** (Module 1 to Module 60).
- **Your constraint**: Maximum **2 classes per week**, each **2 hours** → **4 hours of class time per week**.
- Each module has **multiple topics + many hands-on labs + AI exam**, so it cannot be rushed.

**My calculation** (conservative but realistic):

| Item | Estimate | Time at 2 classes/week |
| --- | --- | --- |
| Classes (lectures) | 2 classes per module | 120 classes → **60 weeks** (~14 months) |
| Hands-on labs + AI exams | 6–12 hours extra per module | Equivalent to another **40–60 weeks** of effort |
| **Total** | — | **18–24 months** (1.5–2 years) |

### Milestone-by-milestone breakdown (at your pace)

| Milestone | Modules | Estimated Time |
| --- | --- | --- |
| 1: Linux + Scripting + Docker basics | 12 | 3–4 months |
| 2: AWS Cloud Fundamentals | 8 | 2–3 months |
| 3: IaC (Pulumi + Terraform + Ansible) | 7 | 2–2.5 months |
| 4: Kubernetes Mastery (heaviest part) | 14 | 5–6 months |
| 5: Observability (Prometheus + Grafana + Loki + Tempo) | 9 | 3 months |
| 6: Production CI/CD & GitOps | 10 | 3–4 months |
| **Total** | **60** | **18–24 months** |

### Why it takes this long (not 6–9 months)

- Many labs are **complex real-world setups**:
    - Kubernetes the Hard Way on AWS
    - Cilium + Hubble full setup
    - Full microservices with 4–5 services + RabbitMQ/Kafka + databases
    - Complete GitOps with ArgoCD + secrets + multi-env
    - Observability stack from scratch
- These take **days** each if you want to actually understand and troubleshoot (which is the point of the course).
- You will need time to **break things and fix them** — that's where real learning happens.

### How to finish closer to 1.5 years (18 months)

- Strictly 2 classes every week (no skipping).
- Do labs the same week or weekend (aim for 8–10 total hours/week).
- Group modules that are related (e.g., all Terraform together, all Prometheus modules together).
- Build 1 mini-project after every milestone (this replaces many small labs and saves time).

### If you go slower (more realistic for most people with job/family)

→ 2 years is very comfortable and you will actually master it.

This syllabus is **extremely comprehensive** — it's basically a full professional DevOps engineer training program (most bootcamps that cover even half of this charge $5k–15k and run 6–9 months full-time).

**Bottom line**:

**Plan for 1.5–2 years** if you want to finish with real, job-ready skills.

Anything faster and you will only complete the theory, not the deep hands-on mastery this course is designed for.

Would you like me to create a **ready-to-follow 24-month week-by-week plan** (with exact modules per week + lab time estimates)? Just say yes and I’ll make it for you. You’ve got this! 🚀