# Part 1: SOFTWARE ENGINEERING

## MILESTONE 1: AI Foundations for Engineers

### Module 1: LLM Basics & Token Economics

**Week 1**

### Class Topics

- Transformer Architecture and Tokenization
- Context Window and KV Cache
- Token Economics and Pricing
- The 40% Context Rule

### Hands-On Labs

**Token Usage Analysis**

- Developer Task Token Comparison Across Models
- The 40% Rule in Practice
- ccflare Token Dashboard Setup

### AI Exam

- Token Audit and Optimization Report


### Module 2: Model Routing & Programmatic Tool Calling

**Week 2**

### Class Topics

- Model Routing Strategies
- Programmatic Tool Calling
- Tool Search and Lazy Loading
- When PTC Beats Traditional Tools

### Hands-On Labs

**Model Routing**

- Rule-Based Model Router Build
- Router Testing Across Ten Developer Tasks

**Programmatic Tool Calling**

- Five-Tool Agent Rewrite with PTC
- On-Demand Tool Library with Discovery

### AI Exam

- Token-Aware Coding Agent


## MILESTONE 2: Core Software Engineering with AI

### Module 3: Building Real Systems with AI

**Weeks 3–5**

### Class Topics

- AI as Pair Programmer
- AB Method and RIPER Workflow
- Iterative Development and Verification
- Reading and Reviewing AI-Generated Code

### Hands-On Labs

**Redis from Scratch**

- Specification First with RESP Protocol and Commands
- AGENTS.md Setup and Forbidden Shortcuts
- Verified Slices from TCP Server to Sorted Sets
- TTL, LRU/LFU Eviction, AOF, and Mistake Prevention

**Message Broker Platform**

- Specification and AGENTS.md Extension from Redis Project
- Vertical Slices from Partition Log to Dead-Letter Handling
- WebSocket Streaming and Schema Validation with Subagents
- Redis Pub/Sub Integration and End-to-End Log Trace

**Serverless Platform**

- Specification with RIPER Workflow for Registry and Triggers
- Function Isolation with Linux Namespaces and Cgroups
- HTTP, Cron, and Message Triggers with Subagents
- Full Three-System Integration with Structured JSON Logs

### AI Exam

- Three-System Integration Demo


### Module 4: Debugging & Refactoring with AI

**Week 6**

### Class Topics

- Systematic Debugging Methods
- Debugging as a Conversation
- Refactoring Legacy Code and the Refactor Loop
- Recognizing Bad AI Output

### Hands-On Labs

**Debugging the Module 3 Projects**

- Redis Bug Diagnostic Conversation
- Hypothesis Validation Before Touching Code
- Multi-Layer Bug Isolation in Message Broker
- Regression Hunt with Git Bisect in Serverless Platform

**Refactoring the Module 3 Projects**

- Module Refactor with AI Across All Three Projects
- Technical Debt Scan and Prioritized Fix List
- Catching AI-Introduced Refactor Bugs

### AI Exam

- Debug, Refactor, and Technical Debt Register


### Module 5: Testing, Code Review, Docs & Git Workflows

**Week 7**

### Class Topics

- AI-Assisted TDD
- AI Code Review
- Living Documentation with Hooks
- Semantic Commits and PR Descriptions

### Hands-On Labs

**Testing & Code Review**

- pytest Suite Generation for an Existing Module
- TDD with AI and Failing Test First
- AI-Assisted PR Review on a 200-Line Diff
- AI Review versus Human Review Comparison

**Docs & Git Workflows**

- Living Docstrings with Hook Enforcement
- Semantic Commit Message Hook
- PR Description Agent from Branch Diff
- Changelog Agent on Release Tag

### AI Exam

- TDD to PR Full Engineering Workflow


## MILESTONE 3: Building with Agents

### Module 6: Tool Calling & MCP

**Week 8**

### Class Topics

- Tool Calling Architecture
- Model Context Protocol
- Building MCP Servers with Runtime Discovery
- MCP Security and Sandboxing

### Hands-On Labs

**Building MCP Servers**

- Codebase MCP Server with Read Grep and Git Log
- Database MCP Server with SQL Query and Schema Access
- CI/CD MCP Server with Pipeline Status and Deploy Logs

**MCP Clients & Dynamic Discovery**

- Multi-Server MCP Client with Runtime Discovery
- Runtime Server Swap Without Client Changes
- API Key Auth and Read-Only Permission Scope

### AI Exam

- Codebase Health Agent Using Three MCP Servers


### Module 7: Context Engineering & AGENTS.md

**Week 9**

### Class Topics

- AGENTS.md as Living Infrastructure
- Three Context Layers by TTL
- TTL Management and Compaction
- Context Compaction and Session Handoff

### Hands-On Labs

**AGENTS.md for Real Projects**

- AGENTS.md for a FastAPI Project
- Prevention Rule Pattern with Trigger and Measurement
- Tiered Context Loading Token Comparison

**Dynamic Context & Session Management**

- Session Start Hook with Git Diff and Open Issues
- Filesystem-as-Memory State Across Sessions
- Session Handoff with HANDOFF.md

### AI Exam

- Context System Performance Measurement


### Module 8: Subagents & Agent Delegation

**Week 10**

### Class Topics

- Subagent Architecture and Delegation
- When to Delegate
- Parallel Subagent Execution
- Planning and Execution Separation

### Hands-On Labs

**Subagent Patterns for SE Workflows**

- Code Review Subagent
- Test Generation Subagent
- Parallel Codebase Scanner with Four Subagents

**Planner/Executor Separation**

- Planner Agent from Feature Spec
- Executor Agents Per Task
- Sequential versus Parallel Execution Comparison

### AI Exam

- Multi-Agent Software Engineering Workflow


### Module 9: Skills & Hooks

**Week 11**

### Class Topics

- Skills as On-Demand Context
- Skills versus AGENTS.md
- Hook Lifecycle and Events
- parry Injection Scanner

### Hands-On Labs

**Skills**

- Code Review Skill with Auto-Activation
- Security Audit Skill with OWASP Top 10
- Lazy Loading Token Cost Comparison

**Hooks & Plugin**

- PreToolUse Auto-Lint Hook
- Security Hook Blocking Dangerous Commands
- parry Injection Scanning on PreToolUse
- Developer Plugin with Installer Script

### AI Exam

- Developer Plugin Code Audit


## MILESTONE 4: Code Quality & Constraints

### Module 10: Constraints, Linters & Self-Repair

**Week 12**

### Class Topics

- Constraints and Reliable Output
- Custom Linter Remediation Messages
- Test Coverage as Infrastructure
- The Self-Repair Loop

### Hands-On Labs

**Constraints & Test Harness**

- Custom Ruff Rule with Remediation Message
- ArchUnit Structural Test for Layer Dependencies
- Agent-Verified pytest Suite
- Agent-to-Agent Review Pipeline

**Self-Repair & CI**

- Self-Repair Loop with Failure Parsing and Retry
- GC Agent for Doc Drift and Dead Code
- GitHub Actions with Linter Tests and Coverage Gate

### AI Exam

- Constraint and Feedback System Over Fifty Agent Commits


## MILESTONE 5: Monitoring, Log Analysis & Security

### Module 11: Structured Logging & AI Log Analysis

**Week 13**

### Class Topics

- Logs as Ground Truth
- Structured JSON Logging
- Log Collection with Loki
- The Volume Problem

### Hands-On Labs

**Log Collection**

- Structured JSON Logging for FastAPI and Agent Sessions
- Promtail and Loki Setup

**Sending Logs to Models**

- Naive versus Filtered Log Analysis Token Comparison
- Log Pre-Processor with Filter and Deduplication
- Tiered Model Pipeline with Classification and Escalation

**AI Log Analysis**

- Plain English Log Query Agent
- Usage Anomaly Detection with Cost-Effective Model

### AI Exam

- AI Log Analysis Pipeline


### Module 12: Evaluation & Security Hardening

**Week 14**

### Class Topics

- Agent Evaluation Methods
- LLM-as-Judge with Rubrics
- Security Surface and Attack Vectors
- Input Sanitization and Output Filtering

### Hands-On Labs

**Evaluation & System Analysis**

- LLM-as-Judge Evaluation Suite
- Scenario Test Suite
- Bug Archaeology Agent on Three Months of Git History
- Architecture Drift Detection Agent

**Security Hardening**

- Prompt Injection Red-Team with Direct and Indirect Attacks
- Input Sanitization PreToolUse Hook
- Output Filtering for Secrets and PII
- OWASP LLM Top 10 Walkthrough with Mitigations

### AI Exam

- Evaluation and Security Pipeline


## PROGRAM OVERVIEW

| Module | Status | Focus |
|---|---|---|
| Module 1: Software Engineering | ✅ Complete | AI-assisted coding, debugging, testing, MCP, subagents, context, log analysis |
| Module 2: System Design | 🔲 Remaining | Databases, distributed systems, APIs, scalable architecture with AI |
| Module 3: Platform Engineering | 🔲 Remaining | API gateway, CLI, NL-to-API, Kubernetes, IaC, CI/CD, human-in-the-loop |
