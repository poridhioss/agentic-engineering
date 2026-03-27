# HARNESS ENGINEERING: SKILLS, SUBAGENTS, HOOKS & PRODUCTION SYSTEMS

## PHASE I: Primitives (Weeks 1–3)

### Module 1: How LLMs Work & How to Control Them

### Class Topics

- Transformer Architecture: Tokenization, Embeddings, Self-Attention, Positional Encoding
- Inference Mechanics: Temperature, Top-p, KV Caching, Context Window
- Prompt Engineering as a Subset of Context Engineering: Zero-shot, Few-shot, Chain-of-Thought, Structured Outputs
- The 40% Context Utilization Limit: Why Overloading Context Makes Agents Worse
- Model Evaluation Methodology: How to Evaluate Models for YOUR Task, Not Benchmark Leaderboards
- Token Economics: Cost Per Task, When to Use Large vs. Small Models, Routing Strategies

### Hands-On Labs

**LLM Internals & Inference**

- Visualizing Tokenization: Compare Token Counts Across Models (Claude, GPT-4o, Gemini)
- Exploring Context Window Limits with LM Studio and Ollama
- Temperature and Top-p Experiments: Measuring Output Variability
- KV Cache Behavior: Measuring Latency Difference with Warm vs. Cold Context

**Prompt Engineering Techniques**

- Zero-shot vs. Few-shot Prompting on Structured Extraction Tasks
- Chain-of-Thought Prompting: Math Reasoning and Multi-Step Planning
- Structured Output Generation: JSON Mode with Schema Validation
- The 40% Rule in Practice: Measuring Agent Performance at 20%, 40%, 80% Context Fill

**Model Evaluation**

- Designing a Task-Specific Eval Suite (Not Benchmarks)
- Building a Cost/Quality/Latency Tradeoff Matrix Across 3 Models
- Routing Logic: Rule-Based Model Selector by Task Complexity and Cost

**Deployment & CI/CD**

- Containerize the Model Evaluation Harness with Docker: Dockerfile, Environment Variables for API Keys
- Docker Compose Setup: Eval Harness + Result Storage (PostgreSQL) as Multi-Container App
- GitHub Actions CI Pipeline: Run Eval Suite Automatically on Every Push, Publish Results as Artifacts
- Deploy Eval Harness as an AWS Lambda Function: Trigger on S3 Upload, Store Results Back to S3

### AI Exam

- Build a Model Evaluation Harness That Tests Any LLM on Your Own Task Suite and Outputs Cost/Quality/Latency Tradeoffs

### Module 2: Tool Calling — From JSON to Programmatic (PTC)

### Class Topics

- Traditional Tool Calling: JSON Schema Definition, Parameter Validation, Return Handling
- Why Traditional Tool Calling Is Becoming Obsolete: Each Invocation = Full Inference Pass
- Programmatic Tool Calling (PTC): Agents Write Code That Calls Tools in a Sandbox
- PTC Results: 37% Token Reduction, Improved Accuracy on Knowledge Retrieval and GIA Benchmarks
- The Core Insight: LLMs Are Trained on Billions of Lines of Code — Code Is Their Natural Action Primitive
- Tool Search Tool: Agents Search a Tool Library on Demand Instead of Loading All Definitions Upfront
- Building Tools for PTC: Designing Functions That Work in Sandboxed Code Execution Environments
- The Tool Selection Problem: Why Less Tools = Better Results (Vercel's 80% Reduction Case Study)
- PTC + MCP Together: Code Execution Calling MCP Tools, Keeping Intermediate Results Out of Context

### Hands-On Labs

**Traditional Tool Calling**

- Define a JSON Schema Tool for Web Search
- Build a Tool With Parameter Validation and Structured Return Handling
- Measure Token Usage of a 5-Tool Traditional Agent on a Research Task

**Programmatic Tool Calling (PTC)**

- Set Up Anthropic PTC with the `code_execution` Tool
- Rewrite the Traditional 5-Tool Agent as a Single PTC Execution Block
- Compare Token Usage and Accuracy Between Traditional vs. PTC on the Same Task
- Handling Tool Errors and Retries Inside a PTC Code Block

**Tool Search & Dynamic Discovery**

- Build a Tool Library with 10 Custom Python Tools
- Implement the Tool Search Tool: Agents Query the Library at Runtime
- Measure Token Reduction: All Tools Loaded Upfront vs. Tool Search on Demand
- PTC + MCP Integration: Write a Code Block That Calls 3 MCP Server Tools in One Pass

**Infrastructure & Automation**

- Bash Script: Automate Tool Library Setup, Dependency Install, and Sandbox Environment Bootstrap
- Docker Compose: Multi-Container Setup — PTC Agent + Tool Servers + S3-Compatible Result Storage (MinIO)
- AWS S3 Integration: Store Tool Execution Results, Logs, and Comparison Reports in S3 Buckets
- GitHub Actions Pipeline: On Every Push, Run Traditional vs. PTC Comparison and Post Token/Accuracy Report as PR Comment

### AI Exam

- Build a PTC-Powered Research Agent: Write Code That Orchestrates 5+ MCP Tools in a Single Execution Block. Compare Token Usage and Accuracy Against Traditional Tool Calling on the Same Task.

### Module 3: MCP — The Settled Protocol Standard

### Class Topics

- Why MCP Won: 97M+ Monthly SDK Downloads, Adopted by Every Major Provider, Governed by Linux Foundation
- Architecture: Client-Server Model, JSON-RPC 2.0, Transports (stdio, SSE, HTTP Streaming)
- Building MCP Servers: Exposing Tools, Resources, and Prompts to Any AI Client
- Building MCP Clients: Connecting Any Agent to Any MCP-Compatible Tool
- Runtime Tool Discovery vs. Hardcoded Connections — Why This Changes Everything
- MCP Security: Authentication, Authorization, Sandboxing, Permission Scopes
- The Protocol Landscape: A2A for Agent-to-Agent (Early but Important), WebMCP for Browsers (Emerging)

### Hands-On Labs

**MCP Server Fundamentals**

- Install and Configure the MCP Python SDK
- Build a Database MCP Server: Expose SQL Query Tool, Schema Resource, and a Query Prompt
- Build a Web API MCP Server: Wrap a REST API as MCP Tools with Auth Headers
- Build a File System MCP Server: Expose Read, Write, and Search as MCP Tools

**MCP Client & Dynamic Discovery**

- Build an MCP Client That Connects to All 3 Servers Above
- Implement Runtime Tool Discovery: Client Lists Available Tools Without Hardcoded Definitions
- Swap One MCP Server at Runtime Without Changing the Client Code
- Test Cross-Client Compatibility: Same Server with Claude Desktop and a Custom Python Client

**MCP Security**

- Add API Key Authentication to the Web API MCP Server
- Implement Permission Scopes: Read-Only vs. Read-Write Tool Access
- Sandbox the File System Server: Restrict Access to a Specific Directory

**Production Deployment**

- Dockerize All 3 MCP Servers: Each in Its Own Container with Health Checks and Restart Policies
- Docker Compose Orchestration: All 3 MCP Servers + Nginx Reverse Proxy Routing by Path Prefix
- Nginx Config: Route `/db`, `/api`, `/fs` Prefixes to the Correct MCP Server Container
- Deploy MCP Servers on AWS EC2 Inside a Private VPC: Public Subnet for Nginx, Private Subnet for Servers
- Run MCP Servers as systemd Services on EC2: Auto-Restart on Failure, Logs via journald

### AI Exam

- Build 3 MCP Servers (Database, Web API, File System) and a Client That Discovers and Uses Them Dynamically

## PHASE II: The Extension System (Weeks 4–7)

### Module 4: Context Engineering & AGENTS.md

### Class Topics

- The Hierarchy: Prompt Engineering ⊂ Context Engineering ⊂ Harness Engineering
- "From the Agent's Point of View, Anything It Can't Access In-Context Doesn't Exist" (OpenAI)
- AGENTS.md / CLAUDE.md as Living Infrastructure: Every Agent Mistake Becomes a Prevention Rule
- The "Table of Contents, Not Encyclopedia" Pattern: Small Entry File Pointing to Deeper Structured Docs
- Three-Tier Context Architecture: Tier 1 (Always Loaded), Tier 2 (Skill-Specific, On Demand), Tier 3 (Persistent Knowledge Base)
- Context Compaction: Summarization, Filesystem-as-Memory, State Offloading, Sub-Agent Isolation
- Dynamic Context: Giving Agents Access to Logs, Metrics, Browser State, Runtime Signals
- Why Context Engineering Is the Highest-Leverage Skill: LangChain Went from Rank 30 to Rank 5 by Changing Only Context, Not the Model

### Hands-On Labs

**AGENTS.md Fundamentals**

- Write Your First AGENTS.md for a Real Project: Define Agent Role, Tools, Constraints, and Coding Standards
- The Prevention Rule Pattern: Trigger 3 Common Agent Mistakes, Then Encode Each as a CLAUDE.md Rule
- Compare Agent Task Success Rate Before and After Adding AGENTS.md (Same Task, Same Model)

**Three-Tier Context Architecture**

- Tier 1 Setup: Write a Lean, Always-Loaded AGENTS.md (Under 200 Lines)
- Tier 2 Setup: Create 3 Skill-Specific Context Files Loaded Only When Relevant
- Tier 3 Setup: Build a Persistent Knowledge Base Directory with Structured Markdown Docs
- Test Tiered Loading: Measure Token Usage with All-in-One vs. Tiered Architecture

**Context Compaction & Dynamic Context**

- Implement Filesystem-as-Memory: Agent Writes State to Files, Reads Back in New Sessions
- Build a Context Summarization Hook: Auto-Summarize Session State Before Context Limit
- Inject Dynamic Context: Feed Live Log Output and System Metrics Into Agent Context at Runtime
- Sub-Agent Isolation: Run Heavy Research in a Subagent, Return Only the Summary to Main Context

**Infrastructure Integration**

- Bash Script: Auto-Build AGENTS.md by Pulling Git Log, Open Issues, and Last Deployment Info at Session Start
- AWS S3: Store and Version the Tier 3 Knowledge Base in S3, Fetch the Relevant Files Dynamically at Runtime
- systemd Service: Run the Context Delivery API as a Persistent Background Service on EC2 with Auto-Restart
- Docker: Containerize the Context Delivery Service, Mount the Knowledge Base Directory as a Docker Volume

### AI Exam

- Engineer a Complete Context System for a Real Project: AGENTS.md, Structured Docs, Tiered Loading. Measure Agent Task Success Before vs. After.

### Module 5: Skills — Packaging Expert Knowledge for Agents

### Class Topics

- What Skills Are: On-Demand Context Providers That Auto-Activate Based on Description Matching
- SKILL.md Anatomy: Name, Description, Trigger Conditions, the Knowledge Payload
- Skills vs. AGENTS.md: Always-On Context (AGENTS.md) vs. On-Demand Expertise (Skills) — Context Budget Management
- The Universal SKILL.md Format: Works Across Claude Code, Codex, Gemini CLI, Cursor — Write Once, Use Everywhere
- Building Domain Skills: Frontend Design, Code Review, Security Auditing, Document Generation, Data Analysis
- Skills for Research: Scanning Reddit/X/Web for Topics, Competitive Analysis, Market Intelligence
- Skills as Harness Components: The Frontend-Design Skill Is Just a Harness for UI Generation
- The Smithery Catalog and awesome-claude-code: 713+ Community Skills, What Makes a Good Skill
- Lazy Loading and the Context Budget: "Smaller System Prompt + Load Skill X When Needed" (Harrison Chase)

### Hands-On Labs

**SKILL.md Fundamentals**

- Anatomy Deep Dive: Dissect 3 Community Skills from the Smithery Catalog
- Write a Skill from Scratch: Bangla Document Processor Skill with Clear Trigger Conditions
- Test Auto-Activation: Verify Your Skill Loads When Expected and Stays Unloaded Otherwise
- Measure Context Budget: Token Cost with Skill Always-On vs. On-Demand Lazy Loading

**Building Domain Skills**

- Code Review Skill: Conventions, Anti-Patterns, PR Checklist for a Python/FastAPI Project
- Security Audit Skill: OWASP Top 10 Checklist, Common Vulnerability Patterns, Remediation Prompts
- Financial Analysis Skill: Ratio Calculations, Report Interpretation, Structured Output Templates
- Research Skill: Web Search Strategy, Source Evaluation, Structured Summary Format

**Skills as Harness Components**

- Chain 2 Skills: Research Skill Feeds Output Directly into Financial Analysis Skill
- Publish a Skill to awesome-skills.com or Smithery Catalog
- Cross-Tool Verification: Test the Same SKILL.md in Claude Code and Gemini CLI

**Distribution Infrastructure**

- GitHub Actions CI: Validate SKILL.md Schema and Trigger Conditions on Every Push, Block Merge if Malformed
- Docker: Containerize a Skills Registry Server — Versioned, Queryable API for SKILL.md Files
- AWS S3: Host and Version the Skills Catalog as Static Files, Serve via S3 Presigned URLs
- Bash Script: One-Command Skill Installer — Pull from S3, Place in Correct `.claude/` Directory, Verify Load

### AI Exam

- Build 5 Production Skills: A Bangla Document Processor, a Code Review Skill, a Security Audit Skill, a Financial Analysis Skill, and a Research Skill. Publish to a Marketplace.

### Module 6: Subagents & Agent Teams — Delegation as Architecture

### Class Topics

- Subagents: Isolated Workers That Do a Job, Return a Result, Never Talk to Each Other. Parent Relays Information.
- Agent Teams: Collaborative Squads That Share a Task List and Message Each Other Directly
- When to Use Subagents (Independent Tasks) vs. Agent Teams (Coordinated Work)
- The Context Isolation Principle: Heavy Lifting in Separate Context Windows Keeps the Main Session Clean
- Subagent Configuration: System Prompts, Tool Permissions, Model Selection Per Agent
- Parallel Execution Patterns: 10 Subagents Scanning a Codebase Simultaneously
- Planning/Execution Separation: Dedicated Planning Agent → Execution Agents (the OPENDEV Dual-Agent Pattern)
- Practical Patterns: Bootstrap-Repo (Parallel Scanners), Design Review Workflows, Competitive Analysis Teams
- Constraint: Subagents Cannot Spawn Subagents — Designing Flat Delegation Hierarchies

### Hands-On Labs

**Subagent Fundamentals**

- Build Your First Subagent: A Researcher That Takes a Query, Returns a Structured Summary, No Tool Access Except Web Search
- Configure Subagent System Prompts and Tool Permissions Independently from the Parent
- Model Routing Per Agent: Use a Large Model for Planning, Small Model for Formatting Subagents
- Context Isolation Test: Verify Subagent Work Does Not Pollute Main Session Context

**Parallel Execution & Planning/Execution Separation**

- Parallel Codebase Scanners: 4 Subagents Each Scanning a Different Directory Simultaneously
- OPENDEV Pattern: Build a Dedicated Planning Agent → 2 Execution Agents → 1 Reviewer Agent
- Bootstrap-Repo Workflow: Lead Agent Delegates File Generation to Parallel Subagents
- Measure Speedup: Sequential vs. Parallel Subagent Execution on a 20-File Codebase Scan

**Agent Teams**

- Build an Agent Team: Shared Task List, Researcher and Analyst Message Each Other Directly
- Design Review Team: Design Agent Proposes, Critic Agent Reviews, Arbitrator Agent Decides
- Competitive Analysis Team: 3 Agents Each Researching a Competitor, Synthesizer Agent Merges Output
- Flat Hierarchy Enforcement: Attempt to Spawn a Sub-Subagent, Observe and Handle the Constraint

**Agent Infrastructure**

- Docker Compose: Each Subagent Isolated in Its Own Container with Scoped Tool Access and Resource Limits
- RabbitMQ Task Queue: Lead Agent Publishes Jobs to a Queue, Subagents Consume and Process Independently
- Kafka Event Streaming: Agent Results Published as Events, Downstream Agents Subscribe and React
- AWS Lambda: Deploy Lightweight Formatting and Summarization Subagents as Serverless Lambda Functions
- Terraform: Provision the Full Multi-Agent Infrastructure on AWS (VPC, EC2, Lambda, SQS) as Code

### AI Exam

- Build a Multi-Agent System: A Lead Agent That Delegates to 4 Specialized Subagents (Researcher, Analyst, Coder, Reviewer), with an Agent Team Variant That Coordinates Directly

### Module 7: Hooks, Plugins & the Distribution Layer

### Class Topics

- Hooks: Deterministic Lifecycle Control — PreToolUse, PostToolUse, PermissionRequest, Session Start/End
- Hook Patterns: Auto-Lint on Every File Write, Block Dangerous Commands, Push Notifications, Aggregate Context on Session Start
- Security Hooks: 49+ Packs Protecting Git, Databases, Cloud Providers from Destructive Commands
- Plugins: The Packaging Format That Bundles Skills + Subagents + Hooks + MCP Servers into Distributable Units
- Plugin Anatomy: Manifest (plugin.json), Namespaced Skills (/plugin-name:skill), Installer Scripts
- Standalone (.claude/) vs. Plugin: Personal Iteration First, Package for Sharing When Stable
- Marketplace Ecosystem: Anthropic Official, Community Marketplaces (ComposioHQ, buildwithclaude.com), 9,000+ Plugins
- Plugin Hygiene: Context Budget Impact, Lazy Loading for MCP but Not Yet for Skills, "5 Well-Chosen > 20 Mediocre" Rule
- Building Your Own Marketplace: Structuring a GitHub Repo as a Plugin Source

### Hands-On Labs

**Hook Fundamentals**

- Write a PreToolUse Hook: Auto-Run Black Formatter Before Every Python File Write
- Write a PostToolUse Hook: Log Every Tool Call with Timestamp and Token Cost to a File
- Session Start Hook: Load Dynamic Context (Git Status, Last 10 Log Lines) at Session Begin
- PermissionRequest Hook: Require Human Confirmation Before Any `git push` or `rm` Command

**Security Hooks**

- Block Dangerous Commands: Hook That Rejects `DROP TABLE`, `rm -rf`, `git push --force`
- Database Protection Hook: Whitelist-Only SQL Operations (SELECT Allowed, DELETE Requires Confirmation)
- Git Safety Hook: Block Force Push to Main/Master Branch
- Audit Trail Hook: Write Every Tool Call and Result to an Append-Only Log File

**Plugin Development & Distribution**

- Build a Plugin Manifest (plugin.json): Name, Version, Skills, Subagents, Hooks, MCP Servers
- Package 3 Skills + 2 Subagents + Security Hooks + an MCP Server into a Single Plugin
- Write an Installer Script: One-Command Plugin Install for a New Team Member
- Publish to a Marketplace: Deploy Plugin to buildwithclaude.com or a GitHub Repo Source
- Namespace Verification: Confirm Skills Load as `/plugin-name:skill-name` Without Conflicts

**CI/CD & Distribution Infrastructure**

- GitHub Actions Pipeline: On Every Push, Validate Hook Scripts, Run Plugin Integration Tests, Block Merge on Failure
- Docker: Package the Entire Plugin as a Docker Image — All Skills, Subagents, Hooks, and MCP Server Bundled
- Bash Installer Script: Pull Plugin Image from Registry, Extract Artifacts, Place in `.claude/` with One Command
- AWS ECR: Push Plugin Docker Image to Elastic Container Registry for Versioned, Private Distribution
- AWS S3: Host Plugin Release Artifacts (zip + manifest) on S3 with Public Download URL for Marketplace Listing

### AI Exam

- Build and Publish a Complete Plugin: 3 Skills + 2 Subagents + Security Hooks + an MCP Server, Packaged with Manifest and Installer. Deploy to a Marketplace.

## PHASE III: Harness Discipline (Weeks 8–10)

### Module 8: Constraints & Feedback Loops

### Class Topics

- The Core Paradox: Stricter Constraints Produce More Reliable Output — Constraining the Solution Space Is a Feature
- Architectural Boundaries Enforced Mechanically: Dependency Layers, Custom Linters, Structural Tests
- Custom Linter Error Messages as Agent Remediation Instructions: Tooling That Teaches While It Works
- Test Coverage as Agent Infrastructure: Without Tests, Agents Cannot Verify Their Own Work
- Agent-to-Agent Review: Implementation Agent + Reviewer Agent = Mutual Oversight Loop
- CI/CD as Harness: Pre-Commit Hooks for Instant Feedback (Not Just CI Gates in the Cloud)
- Garbage Collection Agents: Periodic Sweeps for Doc Drift, Architectural Violations, Dead Patterns
- The Self-Repair Loop: Agent Fails → Identify Missing Capability → Encode Fix into Repo → Agent Improves Permanently
- "Golden Principles": Opinionated Mechanical Rules That Keep Systems Legible for Future Agent Runs

### Hands-On Labs

**Custom Linters & Architectural Constraints**

- Write a Custom Ruff Rule: Detect a Project-Specific Anti-Pattern and Return a Remediation Message as the Error
- Write a Custom ESLint Rule: Block a Forbidden Import Pattern with an Actionable Fix Message
- ArchUnit Structural Test: Enforce Dependency Layer Rules — Service Layer Cannot Import Controller Layer
- Constraint Density Test: Add 5 Linter Rules, Run 10 Agent Tasks, Measure Error Rate vs. Unconstrained Baseline

**Test Harness as Agent Infrastructure**

- Build a pytest Test Suite That Agents Use to Verify Their Own Code Changes Before Committing
- Agent-to-Agent Review Pipeline: Implementation Agent Writes Code, Reviewer Agent Runs Tests and Returns Structured Feedback
- Mutation Testing: Use mutmut to Verify the Test Suite Actually Catches Real Bugs
- Test Coverage Gate: Block Agent Commits If Coverage Drops Below 80% — Pre-Commit Hook + CI Check

**Feedback Loops & Self-Repair**

- Pre-Commit Hook Pipeline: Linter → Formatter → Tests — All Must Pass Before Any Agent Commit
- Self-Repair Loop: Agent Task Fails → Parse Error → Agent Reads Linter Message → Fixes and Retries Automatically
- Garbage Collection Agent: Scheduled Script That Scans for Doc Drift, Dead Code, and Architectural Violations
- Golden Principles File: Write a `CONSTRAINTS.md` with 10 Mechanical Rules, Verify Each Is Enforced by a Linter or Test

**CI/CD & Observability for Constraints**

- GitHub Actions Pipeline: On Every Push — Linter, Tests, Coverage Gate, Architecture Check All as Separate Jobs
- Docker: Containerize the Linter + Test Harness So Any Agent Can Run Constraints Identically Anywhere
- Bash Script: GC Agent Script That Runs on Cron, Scans Repo, Posts Violation Report to Slack/File
- AWS S3 + Prometheus: Store Drift Metrics (Violations per Commit) in S3, Visualize Trend on Grafana Dashboard Over 50 Agent Commits

### AI Exam

- Build a Constraint + Feedback System from Scratch: Architectural Linters with Remediation Messages, Test Harness, Agent-Review Pipeline, and a Garbage Collection Agent. Measure Drift Over 50 Agent Commits.

### Module 9: Workflow Design & The Bitter Lesson

### Class Topics

- The Subtraction Principle: Vercel Removed 80% of Tools and Agents Got Better. Manus Rewrote 5 Times, Each Time Simpler.
- The Bitter Lesson Applied to Harnesses: Every Model Upgrade Makes Some Harness Logic Obsolete. Design for Deletion.
- Permission Systems: Least-Privilege, Scoped Tools, Human-in-the-Loop Gates for Sensitive Operations
- Task Isolation: Git Worktrees, Sandboxed VMs, Filesystem Scoping to Prevent Cross-Contamination
- Session Management: Running 3–4 Concurrent Agents, Dead-Time Utilization, Notifications for When Agents Need Input
- Harness Types as Deployment Contexts: Coding CLI, IDE, Browser, Desktop, Runtime, Domain
- The Harness-as-Operating-System Analogy: Model = CPU, Context = RAM, Harness = OS. Build the OS, Swap the CPU Freely.
- Re-Architecture Readiness: LangChain Rebuilt 4 Times in One Year. Manus 5 Times in 6 Months. This Is Normal, Not Failure.
- Instruction Fade-Out: Why Agents Drift After 100+ Steps and How Context Durability Engineering Solves It

### Hands-On Labs

**Permission Systems & Least-Privilege**

- Design a Scoped Tool Permission Matrix: Each Agent Role Gets Only the Tools It Needs (Read-Only, Write, Deploy)
- Human-in-the-Loop Gate: Any Agent Action Tagged `destructive=true` Pauses and Waits for Explicit Approval
- Least-Privilege Enforcement Test: Attempt a Disallowed Action from a Scoped Agent, Verify It Is Blocked
- Permission Config as Code: Define All Agent Permissions in a `permissions.yaml`, Load at Session Start

**Task Isolation**

- Git Worktrees: Each Agent Task Gets Its Own Worktree — No Cross-Task File Contamination
- Filesystem Scoping: Restrict Agent Write Access to a `/workspace/task-id/` Directory Only
- Docker Sandboxed VM: Run Each Agent Task Inside an Ephemeral Docker Container, Destroyed After Completion
- Cross-Contamination Test: Run 2 Concurrent Agent Tasks in Shared vs. Isolated Environments, Compare Results

**Session Management & Concurrent Agents**

- tmux Session Manager: Script That Launches 3 Concurrent Agent Sessions, Each on a Separate Task
- Dead-Time Utilization: While Agent A Waits for Human Input, Agent B and C Continue Running in Parallel
- Session Handoff Protocol: Agent Writes a `HANDOFF.md` on Pause — Next Session Reads It to Resume Without Context Loss
- Instruction Fade-Out Test: Run an Agent for 100+ Steps, Measure When It Starts Ignoring AGENTS.md Rules

**Infrastructure for Workflow Isolation**

- Terraform: Provision Isolated AWS EC2 Instances Per Agent Task — Spin Up, Run, Tear Down as Code
- AWS VPC + Private Subnets: Each Agent Task Runs in a Network-Isolated Environment, No Cross-Task Traffic
- Docker Compose: Multi-Agent Workflow — Lead Agent Container Spawns Worker Containers via Docker Socket
- Bash Script: Session Handoff Automation — On Agent Pause, Auto-Write State to File and Notify Engineer via Slack Webhook

### AI Exam

- Design a Workflow System for a Team of 3 Engineers: Permission Gates, Task Isolation, Parallel Agents, Session Handoff Protocol. Test It Over a 1-Week Sprint.

### Module 10: Evaluation, Observability & Security

### Class Topics

- Agent Evaluation as Its Own Discipline: Non-Deterministic Systems Need Non-Traditional Testing
- LLM-as-Judge: Designing Eval Prompts, Calibrating Scores, Component-Level Evals (Retrieval, Planning, Execution)
- Scenario-Based Testing: Simulated Environments, Adversarial Inputs, Edge Cases, Regression Suites
- Observability as Table Stakes: 89% of Production Teams Trace Agent Execution Step-by-Step
- Tracing: Step-by-Step Visibility into Reasoning Chains, Tool Calls, Token Usage, Cost Per Task
- Dogfooding as Evaluation: Real-World Failure Capture Beats Synthetic Benchmarks
- Testing Harnesses Across Models: What Works for Claude May Need Harness Iteration for Codex
- Security Surface: Prompt Injection (Direct + Indirect), Data Exfiltration, Permission Escalation
- Defense: Input Sanitization, Output Filtering, Privilege Separation, OWASP LLM Top 10

### Hands-On Labs

**Evaluation Framework**

- LLM-as-Judge Setup: Write 10 Eval Prompts with Calibrated Rubrics for a Code Generation Agent
- Component-Level Evals: Separate Evals for Retrieval Quality, Planning Correctness, and Execution Accuracy
- Scenario-Based Test Suite: 50 Scenarios — Normal Cases, Edge Cases, Adversarial Inputs, Regression Cases
- Regression Suite: Every Production Bug Becomes a Permanent Test Scenario — Run on Every Harness Change
- Cross-Model Harness Test: Run the Same Eval Suite Against Claude and GPT-4o, Document Where Harness Needs Iteration

**Observability Stack**

- OpenTelemetry Integration: Instrument Agent Code to Emit Traces for Every Reasoning Step and Tool Call
- Tempo Deployment: Deploy Grafana Tempo on Docker Compose, Ingest Agent Traces, Visualize Reasoning Chains
- Loki Log Aggregation: Collect All Agent Execution Logs (Tool Calls, Errors, Token Counts) into Loki
- Prometheus Metrics: Track Agent-Level KPIs — Token Usage Per Task, Error Rate, Latency, Cost Per Run
- Grafana Dashboard: Build a Single-Pane Dashboard — Traces (Tempo) + Logs (Loki) + Metrics (Prometheus) for Every Agent Run

**Security**

- Prompt Injection Test: Craft 5 Direct and 5 Indirect Injection Attacks Against Your Agent, Document Which Succeed
- Input Sanitization Hook: PreToolUse Hook That Strips Injection Patterns Before Any Tool Receives User Input
- Output Filtering: PostToolUse Hook That Scans Agent Responses for Sensitive Data (Keys, PII) Before Returning
- Privilege Escalation Test: Attempt to Get a Read-Only Agent to Perform a Write Operation via Prompt Manipulation
- OWASP LLM Top 10 Red-Team: Work Through All 10 Vulnerability Classes Against Your Harness, Document Mitigations

**Production Observability Infrastructure**

- Docker Compose: Full Observability Stack — Prometheus + Grafana + Loki + Tempo Running as Containers
- GitHub Actions: Run Eval Suite in CI on Every Push, Fail Pipeline if Regression Score Drops Below Threshold
- AWS CloudWatch: Push Agent Metrics (Token Usage, Error Rate, Cost) to CloudWatch for Production Alerting
- Alertmanager: Configure Alerts for High Error Rate, Cost Spike, or Security Violation — Notify via Email/Slack

### AI Exam

- Build an Evaluation + Observability Pipeline: 50+ Test Scenarios, Full Tracing Dashboard, Security Red-Team Exercise with Documented Mitigations

## PHASE IV: Production (Weeks 11–12)

### Module 11: Domain Harnesses & Agentic Commerce

### Class Topics

- Harnesses as the New Service Templates: Shared Golden Paths Per Domain, Team-Contributed and Maintained
- Agentic Commerce: Stripe's Agentic Commerce Suite — the Economic Infrastructure Layer for Agents That Transact
- Shared Payment Tokens (SPTs): The New Payment Primitive — Scoped by Seller/Time/Amount, Agents Pay Without Exposing Credentials
- Agentic Commerce Protocol (ACP): Open-Source Spec for Agent-to-Business Commerce, Implementable as REST or MCP Server
- Stripe's Agent Toolkit and MCP Server: Adding Payments to Any Agent via MCP
- Building Commerce-Capable Agents: Product Discovery, Checkout Flows, Fraud Detection (Radar), Order Management
- Domain Skills and Plugins for Bangladesh: Fintech (bKash/Nagad SPT Integration), RMG Supply Chain, Bangla Document Processing, E-Governance
- Browser Harness Patterns: Automating Government Portals, Form-Filling Agents with Session Persistence
- Deployment: Docker, CI/CD, Staged Rollouts, Cost Optimization (Model Routing, Caching, Context Budgets)
- The Brownfield Problem: Incremental Harness Adoption — AGENTS.md First → Hooks → Linters → Full Harness

### Hands-On Labs

**Agentic Commerce Fundamentals**

- Stripe Agent Toolkit Setup: Connect an Agent to the Stripe MCP Server, List Products and Retrieve Prices via MCP Tools
- Shared Payment Token (SPT): Generate a Scoped SPT for a Test Merchant, Use It in an Agent Checkout Without Exposing Full Credentials
- ACP Integration: Implement the Agentic Commerce Protocol as a Lightweight REST Endpoint on a FastAPI Server
- Commerce Agent Flow: Product Discovery → Cart → SPT Checkout → Order Confirmation — Full End-to-End in One Agent Run

**Domain Harnesses for Bangladesh**

- bKash/Nagad SPT Integration: Build a Fintech Skill That Triggers When an Agent Needs to Process a Bangladesh Mobile Payment
- RMG Supply Chain Agent: Subagent That Queries Supplier Inventory via MCP, Places Orders, Tracks Shipment Status
- Bangla Document Processing Agent: Skill That Extracts Structured Data from Bangla PDFs (Government Forms, Invoices)
- E-Governance Browser Harness: Form-Filling Agent That Navigates a Government Portal, Fills Fields, and Submits with Session Persistence

**Brownfield Harness Adoption**

- Brownfield Step 1: Add AGENTS.md to an Existing Project with No Harness — Measure Agent Task Success Improvement
- Brownfield Step 2: Add Pre-Commit Hooks to the Same Project — Measure Error Rate Drop
- Brownfield Step 3: Add Custom Linters — Measure Architectural Drift Reduction
- Brownfield Step 4: Package Everything as a Plugin — One-Command Install for the Full Harness on Any New Clone

**Production Deployment**

- Docker Compose: Commerce Agent + Stripe MCP Server + Domain Skill Registry + Nginx All Running as One Stack
- AWS EC2 + VPC: Deploy Commerce Agent in a Private Subnet, Nginx in Public Subnet, RDS for Order Storage
- Terraform: Provision the Full Commerce Agent Infrastructure on AWS — VPC, EC2, RDS, S3, Lambda as Code
- AWS Lambda: Event-Driven Order Processing — On Checkout Completion, Lambda Triggers Fulfillment Subagent
- GitHub Actions CI/CD: Staged Rollout Pipeline — Dev → Staging → Prod with Manual Approval Gate Before Prod Deploy
- Prometheus + Grafana: Cost Monitoring Dashboard — Token Usage Per Commerce Transaction, Model Routing Savings

### AI Exam

- Build an Agentic Commerce Agent: Product Discovery via MCP, Checkout via Stripe ACP/SPTs, with a Domain Skill for a Bangladesh Vertical. Deploy with CI/CD and Cost Monitoring.

### Module 12: Capstone — Ship a Production Harness

### Class Topics

- Choosing a Domain: Fintech, Agri-Tech, E-Governance, Supply Chain, Edtech, Healthcare
- Architecture Review: AGENTS.md, Skills (3+), Subagents (2+), Hooks, at Least 1 MCP Server, Architectural Constraints
- Packaging as a Plugin: Manifest, Namespaced Skills, Installer Script, Marketplace Listing
- Evaluation Pipeline Design: Scenario Tests, Component Evals, Before/After Harness Performance Data
- Production Deployment Checklist: Containerized, Observable, Monitored, CI/CD, Security Audited
- The "What Would You Delete" Exercise: Every Harness Element Justified or Marked for Deletion on Next Model Upgrade
- Final Presentation Structure: Live Demo + Harness Architecture Diagram + Measurable Impact Metrics

### Hands-On Labs

**Harness Architecture & Design**

- Architecture Decision Record (ADR): Document Every Major Harness Decision — What Was Chosen, What Was Rejected, Why
- Dependency Map: Draw the Full Graph — AGENTS.md → Skills → Subagents → Hooks → MCP Servers → Constraints
- Deletion Audit: For Every Harness Component, Write One Sentence on Which Model Improvement Would Make It Obsolete
- Peer Architecture Review: Present Harness Design to 2 Peers, Incorporate Structured Feedback Before Building

**Building the Production Harness**

- AGENTS.md: Final Version with All Prevention Rules Accumulated from Modules 1–11
- Skills (3+): Domain-Specific Skills for Your Chosen Vertical, All Tested for Auto-Activation Accuracy
- Subagents (2+): Configured with Scoped Permissions, Model Selection, and Context Isolation
- Hooks: Pre-Commit Linter, Security Guard, Audit Trail, Session Handoff — All Wired and Tested
- MCP Server: Domain-Specific Tool Exposure (e.g., bKash API, Government Portal, Supply Chain DB)
- Architectural Constraints: Custom Linter Rules + Test Suite That Enforces Domain-Specific Golden Principles

**Evaluation & Observability**

- Before/After Benchmark: Run 20 Agent Tasks Without Harness, Then Same 20 With Harness — Document Success Rate, Token Cost, Error Rate
- Component Eval Suite: Separate Evals for Each Skill, Each Subagent, and Each MCP Tool
- Full Observability Stack: Prometheus + Grafana + Loki + Tempo — Every Agent Run Traced, Logged, and Metered
- Security Audit Report: Run OWASP LLM Top 10 Checklist Against the Production Harness, Document All Findings and Mitigations

**Production Deployment & CI/CD**

- Docker + Docker Compose: Full Harness Stack Containerized — Agent, MCP Server, Observability, Skill Registry
- Terraform: Entire Production Infrastructure on AWS Defined as Code — VPC, EC2, RDS, S3, Lambda, ECR
- GitHub Actions Full Pipeline: Lint → Test → Eval Suite → Security Scan → Docker Build → Push to ECR → Deploy to AWS → Smoke Test
- Plugin Packaging: Final Plugin with Manifest, Installer Script, and Marketplace Listing — Installable in One Command
- Cost Monitoring: Grafana Dashboard Showing Token Cost Per Task, Total Daily Spend, Model Routing Savings vs. Baseline

### AI Exam

- A Production-Grade Harness Solving a Real Bangladesh Problem: Packaged as a Plugin, Deployed on AWS, Fully Observable, with Measurable Before/After Data Proving the Harness Effect. Live Demo + Architecture Presentation.
