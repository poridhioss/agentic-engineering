# MODULE 1: SOFTWARE ENGINEERING



## MILESTONE 1: AI Foundations for Engineers


### Chapter 1: LLM Basics & Token Economics

### Class Topics
- Transformer internals: tokenization, context window, KV cache — what engineers need to know
- Token economics: input vs. output pricing, hidden overhead from retries and retransmits
- The 40% context utilization rule: why overloading context makes agents slower and less accurate
- Context window as working memory: how to keep agents focused on one task at a time

### Hands-On Labs

**Understanding the System**
- Run 10 developer tasks across 3 models — record output quality, token usage, and latency per task
- The 40% rule in practice: run the same task at 20%, 40%, 80% context fill — compare output quality
- Set up ccflare: real-time token usage dashboard per session and per task type


### AI Exam
- Audit 10 real developer tasks: identify which tasks are token-heavy, why, and how to reduce usage without losing output quality. Deliver a written report with a before/after token comparison.


### Chapter 2: Model Routing & Programmatic Tool Calling

### Class Topics
- Model routing: cost-effective models for simple tasks, capable models for reasoning, powerful models for audits
- Programmatic Tool Calling (PTC): agents write code to call tools in a sandbox — 37% token reduction vs. chaining
- Tool search: lazy-load tool definitions on demand instead of upfront — the lazy loading pattern
- When PTC beats traditional tool calling and when it doesn't

### Hands-On Labs

**Model Routing**
- Build a rule-based model router: task type → model selection logic with a fallback chain
- Test the router on 10 tasks — log which model was selected, actual token usage, and output quality


**PTC in Practice**
- Rewrite a 5-tool coding agent as a single PTC execution block — measure token reduction
- Build a 10-tool developer library with on-demand discovery — measure reduction vs. always-loaded


### AI Exam
- Build a token-aware coding agent: model router + PTC execution + token budget enforcer. Add a complexity check — if a task is high-complexity but low-budget, the agent refuses and asks for a budget increase rather than failing silently with a less capable model. Show a before/after usage report.


## MILESTONE 2: Core Software Engineering with AI


### Chapter 3: Building Real Systems with AI

### Class Topics
- AI as a pair programmer, not a code generator — the mindset shift
- Specification-driven development: write the spec first, then implement (AB Method, RIPER Workflow)
- Iterative development: small tasks with immediate verification over large one-shot prompts
- Reading AI-generated systems critically — every design decision must be understood before accepting
- When to trust AI output and when to challenge it — recognizing hallucinated architecture

### Hands-On Labs

**Project 1: Build Redis from Scratch**
- Write the full spec first (AB Method): RESP protocol, commands, data structures, persistence — no code until spec is approved
- Set up AGENTS.md: coding standards, forbidden shortcuts, and what to do when the agent hallucinates a command
- Build in verified slices: TCP server → RESP parser → data structures (strings, lists, hashes, sets, sorted sets) — tests pass before moving on
- Add TTL expiration, LRU/LFU eviction, and AOF persistence — spot the architectural mistake the agent introduces and encode it as a prevention rule

**Project 2: Build a Modern Message Broker Platform**
- Extend the spec and AGENTS.md from Project 1 with broker-specific rules: all offsets durable, consumer rebalancing tested before merge
- Build in vertical slices: partition log → producer batching → consumer group rebalancing → retention → dead-letter handling
- Add WebSocket streaming and schema validation — use subagents for each, parent agent merges and runs the full suite
- Connect to Project 1 via Redis pub/sub — validate the message flow end-to-end with a log trace

**Project 3: Build a Serverless Platform**
- Write the spec using RIPER Workflow: function registry, cold/warm start, event triggers, resource limits — agent explains every design choice
- Implement function isolation with Linux namespaces and cgroups — verify isolation by attempting a breakout and confirming it fails
- Add HTTP, cron, and message triggers (connected to Project 2) — one trigger type per subagent, parent wires them together
- Connect all three: event → Message Broker → Serverless function → reads/writes Redis, with structured JSON logs capturing the full flow

### AI Exam
- All 3 systems running together: an event enters the Message Broker, triggers a Serverless function, the function reads and writes state in Redis, execution logs are captured as structured JSON. Present the spec, architecture diagram, and a demo of the full flow.


### Chapter 4: Debugging & Refactoring with AI

### Class Topics
- Systematic debugging: error + stack trace + logs → root cause hypothesis → verify → fix
- Debugging as a conversation — narrowing the problem space iteratively, not asking for magic fixes
- Refactoring legacy code: reading code you didn't write, understanding intent, improving without breaking
- The refactor loop: read → understand → propose → test → accept or reject
- Recognizing bad AI output: hallucinated fixes, plausible-looking bugs, wrong abstractions

### Hands-On Labs

**Debugging the Chapter 3 Projects**
- Take a real bug from the Redis implementation (error + stack trace) — document the diagnostic conversation, hypothesis by hypothesis
- Hypothesis validation: instead of asking AI to "fix it", ask "give me 3 possible causes and a command to test each" — validate before touching code
- Multi-layer bug in the Message Broker: isolate whether the issue is in the partition log, consumer group logic, or network layer using AI
- Regression hunt in the Serverless Platform: given a git bisect range, use AI to identify which commit broke function isolation

**Refactoring the Chapter 3 Projects**
- Refactor the most complex module from each project — AI extracts functions, reduces coupling, improves naming — engineer reviews every change
- Technical debt scan across all 3 codebases: AI identifies cyclomatic complexity hotspots, duplication, and god classes — produce a prioritized fix list
- Catch bad AI output: AI proposes a refactor that introduces a subtle bug — find it before merging, add it as a prevention rule in AGENTS.md

### AI Exam
- Pick the weakest module across the 3 Chapter 3 projects: debug 2 known issues, refactor the module, and produce a technical debt register. Every change covered by tests.


### Chapter 5: Testing, Code Review, Docs & Git Workflows with AI

### Class Topics
- AI-assisted TDD: write the failing test first, let AI implement to pass it
- AI code review: first pass by AI, final decision by engineer — never merge without understanding
- Documentation that stays alive: AI generates docstrings and API specs, hooks keep them in sync
- Git workflows: semantic commits, PR descriptions, and changelogs generated from diffs

### Hands-On Labs

**Testing & Code Review**
- Generate a full pytest suite for an existing module: unit tests, edge cases, 2 intentional failure cases
- TDD with AI: write 5 failing tests, let AI implement the function — verify the logic yourself
- AI-assisted PR review: feed a 200-line diff into Claude, get a structured review (bugs, style, security)
- Compare AI review vs. human review on the same PR — what did each catch that the other missed?


**Docs & Git Workflows**
- Living docs: AI generates docstrings for an undocumented module — hook flags any new function missing one
- Semantic commit hook: on every commit, AI reads the staged diff and generates a conventional commit message
- PR description agent: reads the branch diff, produces a structured PR description with summary and test plan
- Changelog agent: on every release tag, reads all commits since last tag, generates a human-readable changelog


### AI Exam
- Full engineering workflow on a real feature: TDD → implementation → AI-assisted PR review → docstring generation → semantic commit + PR description. Every step documented with before/after comparison.


## MILESTONE 3: Building with Agents


### Chapter 6: Tool Calling & MCP — Connecting Agents to Real Systems

### Class Topics
- Tool calling architecture: how agents interact with the outside world — JSON schema, parameter validation, return handling
- MCP (Model Context Protocol): the standard for exposing any system as an agent-accessible tool
- Building MCP servers: expose your database, REST API, file system, and CI pipeline as MCP tools
- Runtime tool discovery: agents find and use tools at runtime without hardcoded definitions
- MCP security: authentication, permission scopes, sandboxing — agents should only access what they need

### Hands-On Labs

**Building MCP Servers**
- Build a codebase MCP server: expose file read, grep, git log, and git diff as tools for any agent
- Build a database MCP server: expose SQL query, schema inspection, and migration status as tools
- Build a CI/CD MCP server: expose pipeline status, test results, and deployment logs as tools


**MCP Clients & Dynamic Discovery**
- Build an MCP client that connects to all 3 servers — discover tools at runtime, no hardcoded definitions
- Swap one MCP server at runtime without changing the client — verify the agent adapts automatically
- Add API key auth and read-only permission scope to the database MCP server


### AI Exam
- Build 3 MCP servers (codebase, database, CI/CD) and a client that discovers and uses them dynamically. Agent answers "Is this codebase healthy?" by querying all 3 systems in one session.


### Chapter 7: Context Engineering & AGENTS.md

### Class Topics
- AGENTS.md as living infrastructure: every agent mistake becomes a prevention rule
- The table-of-contents pattern: lean entry file pointing to deeper structured docs
- Three context layers by TTL: Static (AGENTS.md, rules — lives forever), Dynamic (git diff, failing tests — refreshed each session), Ephemeral (last 3 turns — discarded after task)
- Managing TTL: knowing when to summarize vs. prune each layer is critical for long-running sessions
- Context compaction: filesystem-as-memory, summarization hooks, session handoff

### Hands-On Labs

**AGENTS.md for Real Projects**
- Write an AGENTS.md for a FastAPI project: coding standards, forbidden patterns, test requirements
- Prevention rule pattern: trigger 3 common agent mistakes, encode each as a rule — measure error rate drop
- Tiered loading: all-in-one AGENTS.md vs. tiered architecture — measure token usage on 10 agent tasks


**Dynamic Context & Session Management**
- Session start hook: auto-load git diff + failing test names + last 5 open issues into context
- Filesystem-as-memory: agent writes task state to a file, reads it back in a new session without losing progress
- Session handoff: agent writes `HANDOFF.md` on pause — next session reads it and resumes cleanly


### AI Exam
- Engineer a complete context system for a real codebase: AGENTS.md, tiered docs, dynamic session start. Measure agent task success rate before vs. after.


### Chapter 8: Subagents & Agent Delegation

### Class Topics
- Subagents: isolated workers that do one job and return a result — parent relays, subagents never talk directly
- When to delegate: tasks that are independent, context-heavy, or need a different tool set
- Parallel subagents: multiple agents scanning different parts of a codebase simultaneously
- Planning/execution separation: a planner agent designs the approach, executor agents implement it
- Flat delegation hierarchies: subagents cannot spawn subagents — design your system around this constraint

### Hands-On Labs

**Subagent Patterns for SE Workflows**
- Code review subagent: parent delegates a PR diff — subagent reviews and returns a structured report
- Test generation subagent: parent delegates a module — subagent writes a full pytest suite and returns it
- Parallel codebase scan: 4 subagents each scan a different directory simultaneously — parent merges findings


**Planner/Executor Separation**
- Planner agent reads a feature spec and produces a task breakdown with file targets and acceptance criteria
- Executor agents each implement one task — no cross-task awareness needed
- Measure: sequential single-agent vs. parallel subagent execution on a 10-file refactor


### AI Exam
- Build a multi-agent SE workflow: planner agent breaks a feature spec into tasks → 3 parallel executor subagents implement → reviewer subagent audits all changes → parent agent produces the final PR description.


### Chapter 9: Skills & Hooks — Developer Automation

### Class Topics
- Skills: on-demand context that auto-activates — code review, security audit, API design
- Skills vs. AGENTS.md: always-on vs. on-demand — the context loading decision
- Hooks: deterministic lifecycle control — PreToolUse (auto-lint), PostToolUse (audit log), Session Start (dynamic context)
- Security hooks: block dangerous commands, protect git and database from destructive agent actions
- parry: prompt injection scanner for hooks — scan every input before tool execution

### Hands-On Labs

**Skills**
- Code review skill: coding conventions, anti-patterns, PR checklist — auto-activates on PR tasks
- Security audit skill: OWASP Top 10 checklist, vulnerability patterns, severity ratings
- Measure lazy loading: token usage with both skills always-on vs. on-demand


**Hooks & Plugin**
- PreToolUse hook: auto-run Ruff before every Python file write
- Security hook: block `DROP TABLE`, `rm -rf`, `git push --force` without approval
- parry integration: add injection scanning to the PreToolUse hook — test with 3 attack attempts
- Package code review skill + security audit skill + safety hooks into one plugin with installer script


### AI Exam
- Build a developer plugin: code review skill + security audit skill + safety hooks + parry injection scanner. Install on a fresh project and run a full code audit.


## MILESTONE 4: Code Quality & Constraints


### Chapter 10: Constraints, Linters & Self-Repair

### Class Topics
- The core paradox: stricter constraints produce more reliable agent output
- Custom linter error messages as agent remediation instructions — tooling that teaches while it works
- Test coverage as agent infrastructure: without tests, agents cannot verify their own work
- Agent-to-agent review: implementation agent + reviewer agent = mutual oversight loop
- The self-repair loop: agent fails → reads linter error → fixes → retries — fully automatic

### Hands-On Labs

**Constraints & Test Harness**
- Write a custom Ruff rule: detect a project-specific anti-pattern, return a remediation message as the error text
- ArchUnit structural test: service layer cannot import controller layer — enforced on every commit
- Build a pytest suite that agents run to verify their own changes before committing
- Agent-to-agent review: implementation agent writes code, reviewer agent runs tests and returns structured feedback


**Self-Repair & CI**
- Self-repair loop: agent task fails → parses linter error → fixes automatically → retries — end-to-end demo
- GC agent: scans weekly for doc drift, dead code, and architectural violations — posts a report
- GitHub Actions pipeline: linter + tests + coverage gate + architecture check as separate jobs on every push


### AI Exam
- Build a constraint + feedback system: custom linter with remediation messages, pytest harness, agent-to-agent review, GC agent. Measure code quality improvement over 50 agent commits.


## MILESTONE 5: Monitoring, Log Analysis & Security


### Chapter 11: Structured Logging & AI Log Analysis

### Class Topics
- Why logs are ground truth: metrics tell you something is wrong, logs tell you why
- Structured logging: JSON logs vs. plain text — why structure makes AI analysis possible
- Log collection: stdout → Promtail → Loki — the lightweight stack for developer teams
- The volume problem: logs are huge — filter, deduplicate, and summarize before sending to any model
- Model selection for log analysis: cost-effective models for scanning and classification, capable models for root cause only

### Hands-On Labs

**Log Collection**
- Add structured JSON logging to a FastAPI app and agent sessions (tool calls, model used, duration)
- Set up Promtail + Loki: collect app logs and agent session logs into one place


**Sending Logs to Models — The Right Way**
- Naive vs. smart: raw 10,000 lines → expensive model vs. filtered ERROR/WARN only — measure token reduction
- Build a log pre-processor: filter by severity → deduplicate → summarize repeated patterns before any model call
- Tiered model pipeline: cost-effective model classifies log batches (critical / noise / anomaly), capable model handles critical only


**AI Log Analysis**
- Log query agent: plain English question → Loki query → pre-process → model answers "What broke and why?"
- Usage anomaly detection: cost-effective model scans daily session logs, escalates significant anomalies for deeper investigation


### AI Exam
- Build a production-grade AI log analysis pipeline: structured logging → Loki collection → pre-processor (filter + deduplicate + summarize) → cost-effective model for classification → capable model for root cause on critical only. Show token usage comparison between naive and the smart tiered pipeline.


### Chapter 12: Evaluation & Security Hardening

### Class Topics
- Agent evaluation: non-deterministic code generation needs non-traditional testing
- LLM-as-judge: calibrated rubrics for code correctness, security posture, and style
- System analysis with AI: bug archaeology, dependency risk, architecture drift detection
- Security surface: prompt injection, data exfiltration, privilege escalation
- Defense: input sanitization, output filtering, OWASP LLM Top 10

### Hands-On Labs

**Evaluation & System Analysis**
- LLM-as-judge: write 10 eval prompts with rubrics for a code generation agent — score correctness, security, style
- Scenario test suite: 30 scenarios — normal tasks, edge cases, adversarial inputs, regression cases
- Bug archaeology: feed 3 months of git log + issue tracker into an agent — find the 5 highest-risk code patterns
- Architecture drift: agent compares codebase against original architecture decision records — reports violations


**Security Hardening**
- Prompt injection red-team: craft 5 direct + 5 indirect attacks against a code agent — document which succeed
- Input sanitization hook: PreToolUse hook strips injection patterns before any tool receives user input
- Output filtering hook: scans agent output for hardcoded secrets and PII before returning to the user
- OWASP LLM Top 10: work through all 10 vulnerability classes, document a mitigation for each


### AI Exam
- Build an evaluation + security pipeline: 30-scenario test suite + LLM-as-judge scoring + full security red-team + system analysis report. Present before/after harness metrics.


## PROGRAM OVERVIEW

| Module | Status | Focus |
|---|---|---|
| Module 1: Software Engineering | ✅ Complete | AI-assisted coding, debugging, refactoring, testing, MCP, subagents, context, monitoring |
| Module 2: System Design | 🔲 Remaining | Multi-agent architecture, orchestration patterns, system scalability, agent topology design |
| Module 3: Platform Engineering | 🔲 Remaining | Infrastructure, Docker, Kubernetes, CI/CD, observability stack, production deployment |
