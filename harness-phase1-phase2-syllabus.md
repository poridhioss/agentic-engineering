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

---

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
