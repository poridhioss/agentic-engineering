# Part 1: SOFTWARE ENGINEERING

## MILESTONE 1: AI Foundations for Engineers

### Module 1: LLM Basics & Token Economics

### Class Topics

- Transformer Architecture and Tokenization
- Context Window and KV Cache Mechanics
- Token Economics and Input/Output Pricing
- The 40% Context Utilization Rule
- Context Window as Working Memory

### Hands-On Labs

**Token Usage Analysis**

- Developer Task Token Comparison Across Models
- The 40% Rule in Practice
- ccflare Token Dashboard Setup

### AI Exam

- Token Audit and Optimization Report


### Module 2: Model Routing & Programmatic Tool Calling

### Class Topics

- Model Routing: Cost-Effective vs. Capable vs. Powerful
- Programmatic Tool Calling (PTC)
- Tool Search and Lazy Loading
- When PTC Beats Traditional Tool Calling

### Hands-On Labs

**Model Routing**

- Rule-Based Model Router Build
- Router Testing Across 10 Developer Tasks

**PTC in Practice**

- 5-Tool Agent Rewrite with PTC
- On-Demand Tool Library with Discovery

### AI Exam

- Token-Aware Coding Agent


## MILESTONE 2: Core Software Engineering with AI

### Module 3: Building Real Systems with AI

### Class Topics

- AI as a Pair Programmer, Not a Code Generator
- Specification-Driven Development: AB Method and RIPER Workflow
- Iterative Development and Immediate Verification
- Reading AI-Generated Code Critically
- Recognizing Hallucinated Architecture

### Hands-On Labs

**Project 1: Build Redis from Scratch**

- Spec First: RESP Protocol, Commands, Data Structures
- AGENTS.md Setup and Forbidden Shortcuts
- Verified Slices: TCP Server to Sorted Sets
- TTL, LRU/LFU Eviction, AOF, and Mistake Prevention

**Project 2: Build a Modern Message Broker Platform**

- Spec and AGENTS.md Extension from Project 1
- Vertical Slices: Partition Log to Dead-Letter Handling
- WebSocket Streaming and Schema Validation with Subagents
- Redis Pub/Sub Integration and End-to-End Log Trace

**Project 3: Build a Serverless Platform**

- Spec with RIPER Workflow: Registry, Cold/Warm Start, Triggers
- Function Isolation with Linux Namespaces and Cgroups
- HTTP, Cron, and Message Triggers with Subagents
- Full Three-System Integration with Structured JSON Logs

### AI Exam

- Three-System Integration Demo


### Module 4: Debugging & Refactoring with AI

### Class Topics

- Systematic Debugging: Error → Hypothesis → Verify → Fix
- Debugging as a Conversation
- Refactoring Legacy Code with AI
- The Refactor Loop: Read → Propose → Test → Accept
- Recognizing Bad AI Output and Hallucinated Fixes

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

### Class Topics

- AI-Assisted TDD: Failing Test First
- AI Code Review: First Pass AI, Final Decision Engineer
- Living Documentation with Hook Enforcement
- Semantic Commits and PR Descriptions from Diffs

### Hands-On Labs

**Testing & Code Review**

- pytest Suite Generation for an Existing Module
- TDD with AI: 5 Failing Tests, AI Implements
- AI-Assisted PR Review on a 200-Line Diff
- AI Review vs. Human Review Comparison

**Docs & Git Workflows**

- Living Docstrings with Hook Enforcement
- Semantic Commit Message Hook
- PR Description Agent from Branch Diff
- Changelog Agent on Release Tag

### AI Exam

- TDD to PR Full Engineering Workflow


## MILESTONE 3: Building with Agents

### Module 6: Tool Calling & MCP

### Class Topics

- Tool Calling Architecture and JSON Schema
- Model Context Protocol (MCP)
- Building MCP Servers: Database, Codebase, CI/CD
- Runtime Tool Discovery
- MCP Security: Auth, Scopes, Sandboxing

### Hands-On Labs

**Building MCP Servers**

- Codebase MCP Server: Read, Grep, Git Log, Diff
- Database MCP Server: SQL Query, Schema, Migration Status
- CI/CD MCP Server: Pipeline Status, Test Results, Deploy Logs

**MCP Clients & Dynamic Discovery**

- Multi-Server MCP Client with Runtime Discovery
- Runtime Server Swap Without Client Changes
- API Key Auth and Read-Only Permission Scope

### AI Exam

- Codebase Health Agent Using 3 MCP Servers


### Module 7: Context Engineering & AGENTS.md

### Class Topics

- AGENTS.md as Living Infrastructure
- The Table-of-Contents Pattern
- Three Context Layers by TTL: Static, Dynamic, Ephemeral
- TTL Management: Summarize vs. Prune
- Context Compaction and Session Handoff

### Hands-On Labs

**AGENTS.md for Real Projects**

- AGENTS.md for a FastAPI Project
- Prevention Rule Pattern: Trigger, Encode, Measure
- Tiered Context Loading Token Comparison

**Dynamic Context & Session Management**

- Session Start Hook with Git Diff and Open Issues
- Filesystem-as-Memory State Across Sessions
- Session Handoff with HANDOFF.md

### AI Exam

- Context System Performance Measurement


### Module 8: Subagents & Agent Delegation

### Class Topics

- Subagent Architecture: Isolated Workers, Parent Relays
- When to Delegate: Independent, Context-Heavy, Different Tools
- Parallel Subagent Execution
- Planning/Execution Separation
- Flat Delegation Hierarchies

### Hands-On Labs

**Subagent Patterns for SE Workflows**

- Code Review Subagent
- Test Generation Subagent
- Parallel Codebase Scanner: 4 Subagents, 4 Directories

**Planner/Executor Separation**

- Planner Agent from Feature Spec
- Executor Agents Per Task
- Sequential vs. Parallel Execution Comparison

### AI Exam

- Multi-Agent Software Engineering Workflow


### Module 9: Skills & Hooks

### Class Topics

- Skills: On-Demand Context by Description Matching
- Skills vs. AGENTS.md: Always-On vs. On-Demand
- Hook Lifecycle: PreToolUse, PostToolUse, Session Start
- Security Hooks: Block Dangerous Commands
- parry: Prompt Injection Scanner for Hooks

### Hands-On Labs

**Skills**

- Code Review Skill with Auto-Activation
- Security Audit Skill: OWASP Top 10 Checklist
- Lazy Loading Token Cost Comparison

**Hooks & Plugin**

- PreToolUse Auto-Lint Hook
- Security Hook: Block DROP TABLE, rm -rf, Force Push
- parry Injection Scanning on PreToolUse
- Developer Plugin with Installer Script

### AI Exam

- Developer Plugin Code Audit


## MILESTONE 4: Code Quality & Constraints

### Module 10: Constraints, Linters & Self-Repair

### Class Topics

- Stricter Constraints Produce More Reliable Output
- Custom Linter Error as Agent Remediation Message
- Test Coverage as Agent Infrastructure
- Agent-to-Agent Review Loop
- The Self-Repair Loop

### Hands-On Labs

**Constraints & Test Harness**

- Custom Ruff Rule with Remediation Message
- ArchUnit Structural Test: Layer Dependency Enforcement
- Agent-Verified pytest Suite
- Agent-to-Agent Review Pipeline

**Self-Repair & CI**

- Self-Repair Loop: Fail → Parse → Fix → Retry
- GC Agent for Doc Drift and Dead Code
- GitHub Actions: Linter, Tests, Coverage Gate, Architecture Check

### AI Exam

- Constraint and Feedback System Over 50 Agent Commits


## MILESTONE 5: Monitoring, Log Analysis & Security

### Module 11: Structured Logging & AI Log Analysis

### Class Topics

- Why Logs Are Ground Truth
- Structured JSON Logging vs. Plain Text
- Log Collection: Promtail and Loki
- The Volume Problem: Filter Before Model
- Cost-Effective Model Routing for Log Analysis

### Hands-On Labs

**Log Collection**

- Structured JSON Logging for FastAPI and Agent Sessions
- Promtail and Loki Setup

**Sending Logs to Models**

- Naive vs. Filtered Log Analysis Token Comparison
- Log Pre-Processor: Filter, Deduplicate, Summarize
- Tiered Model Pipeline: Classification then Escalation

**AI Log Analysis**

- Plain English Log Query Agent
- Usage Anomaly Detection with Cost-Effective Model

### AI Exam

- AI Log Analysis Pipeline


### Module 12: Evaluation & Security Hardening

### Class Topics

- Agent Evaluation: Non-Deterministic Systems, Non-Traditional Testing
- LLM-as-Judge with Calibrated Rubrics
- System Analysis: Bug Archaeology and Architecture Drift
- Security Surface: Prompt Injection, Exfiltration, Escalation
- Defense: Input Sanitization, Output Filtering, OWASP LLM Top 10

### Hands-On Labs

**Evaluation & System Analysis**

- LLM-as-Judge Eval Suite: 10 Rubrics
- Scenario Test Suite: 30 Cases
- Bug Archaeology Agent on 3 Months of Git History
- Architecture Drift Detection Agent

**Security Hardening**

- Prompt Injection Red-Team: 5 Direct + 5 Indirect Attacks
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
