# Engineering Case Studies

These case studies summarize representative work from public and private projects. Private-system details are intentionally limited to architecture, engineering decisions, verification, and outcomes rather than proprietary configuration or credentials.

## 1. Dream.OS — Guarded Multi-Agent Repository Automation

### Problem

AI coding agents are useful, but unbounded execution creates predictable failure modes: duplicate work, unclear task ownership, weak completion claims, and risky repository mutations without independent evidence.

### Approach

I built and operated Dream.OS as a message-driven automation runtime for repository work. The system uses typed task messages, transport boundaries, claim/ack lifecycles, guarded execution, and explicit status artifacts instead of allowing agents to invoke repository operations without structure.

Representative flow:

1. A sender creates a structured task message.
2. A file- or Git-backed transport delivers the task to a node or agent.
3. The relay claims the task and records execution state.
4. The task adapter rejects invalid messages at the swarm boundary.
5. The controller routes or decomposes work across agents and tools.
6. Verification runs before the task can close.
7. Final state and evidence are written to inspectable artifacts.

### Engineering Decisions

- Treat task transport and execution as separate concerns.
- Fail closed when task contracts or enforcement rules are invalid.
- Require explicit verification instead of trusting an agent's completion statement.
- Preserve closeouts, manifests, and audit artifacts for later review.
- Keep runtime authority separate from historical or legacy documentation.

### Verification

The runtime uses targeted pytest gates plus audit/source-of-truth checks and repository Definition-of-Done scripts. Higher-risk enforcement repairs are verified with negative controls so the test suite demonstrates that removing the protection causes the expected failure.

### Outcome

The result is a bounded automation system for git, lint, test, scan, audit, and repository-maintenance workflows where task ownership and completion can be inspected after execution.

**Skills demonstrated:** Python, message-driven architecture, orchestration, schema validation, testing, Git automation, runtime governance.

---

## 2. AgentTools / WE ARE SWARM — Multi-Agent Coordination Tooling

**Public repository:** [Victor-Dixon/AgentTools](https://github.com/Victor-Dixon/AgentTools)

### Problem

Multiple AI agents working in the same engineering environment need more than parallel prompts. They need shared state, messaging, task coordination, conflict detection, and evidence that completed work actually happened.

### Approach

I developed and maintained a reusable Python coordination/tooling surface with modules for:

- asynchronous agent-to-agent messaging;
- shared memory;
- task assignment and status;
- consensus and voting;
- conflict detection for overlapping work;
- agent capability/strength tracking;
- work-proof and verification helpers;
- MCP-oriented tool integration.

### Engineering Decisions

- Make coordination primitives reusable instead of baking them into one agent implementation.
- Detect overlapping file/task intent before duplicate work becomes a merge problem.
- Separate operator tooling from product lanes in the same repository.
- Keep canonical task/status documents bounded so the "next" queue does not become another backlog.

### Verification

The repository uses Python tests, documented SSOT status, package/version gates, and explicit blockers rather than presenting incomplete release work as complete.

### Outcome

The project provides reusable coordination primitives for multi-agent engineering workflows and demonstrates how agent orchestration can be treated as software infrastructure rather than prompt choreography.

**Skills demonstrated:** Python package design, CLI tooling, MCP integration, distributed-work coordination, testing, developer tooling.

---

## 3. ProjectScanner — Evidence-First Repository Intelligence

**Public repository:** [Victor-Dixon/projectscanner](https://github.com/Victor-Dixon/projectscanner)

### Problem

Large collections of repositories become difficult to clean up safely. Manual inspection does not scale, and destructive consolidation decisions are risky when there is no structured inventory of code, documentation, git state, or generated artifacts.

### Approach

I built ProjectScanner to create repository intelligence before cleanup or promotion. The tool scans local project trees and selected GitHub repositories, extracts lightweight code structure, and exports machine-readable reports for downstream planning.

Representative outputs include:

- repository analysis;
- LLM-oriented context;
- cleanup recommendations;
- documentation-gap reports;
- scan snapshots suitable for later history/trend ingestion.

### Engineering Decisions

- Scanner output is evidence, not governance authority.
- Keep durable decisions in the control/governance layer instead of silently mutating scanner results into policy.
- Surface known unknowns instead of describing incomplete analyzers as working features.
- Use regression tests as the baseline gate for scanner changes.

### Outcome

Repository cleanup and consolidation work can begin from repeatable evidence instead of intuition. The scanner acts as a generator feeding higher-level planning and governance workflows.

**Skills demonstrated:** Python, source-code analysis, filesystem tooling, GitHub integration, JSON export, repository architecture, test-driven maintenance.

---

## 4. Governed Multi-Domain Deployment System

### Problem

A portfolio of websites spread across domains and legacy source locations creates deployment risk: wrong-source publishing, stale generated output, accidental cross-brand content movement, and deploys that report success without proving the live site changed correctly.

### Approach

I consolidated website operations around explicit source-of-truth roots, a deployable-site registry, changed-site resolution, and a unified deployment path.

The deployment contract is designed around:

1. resolve which canonical site roots changed;
2. fail closed on legacy/unclassified source paths;
3. run a strict dry-run;
4. deploy only the affected domain over SFTP;
5. verify the production HTTPS surface;
6. reject obvious hosting/default pages and validate expected markers;
7. keep rollback explicit and scoped to one site.

### Engineering Decisions

- Generated deployment output is never treated as canonical source.
- Each domain has a defined role and source root.
- Cross-role content promotion requires explicit authority instead of silent copying.
- Production verification checks the live response, not only the upload command.

### Outcome

The website fleet has a repeatable deployment workflow with stronger source authority, smaller blast radius, and live verification after publishing.

**Skills demonstrated:** Python, GitHub Actions, SFTP, deployment automation, CI/CD design, HTTPS verification, rollback planning, configuration governance.

---

## 5. Message-Bus Runtime Recovery — Regression-Driven Repair

### Problem

A dispatcher path failed because an expected finite-state-machine module was missing from the active repository line. That prevented agent-to-agent dispatch from reaching the intended gate.

### Approach

I treated the failure as a source-recovery problem rather than writing a replacement from scratch:

- located the authoritative historical implementation;
- rejected a smaller salvage candidate that did not preserve the required behavior;
- restored the implementation and its companion regression coverage;
- added a dispatch regression test that exercised the real path rather than a scratch harness;
- removed temporary live-registry probe state after verification.

### Verification

The targeted recovery suite passed **29 tests**, and a dry-run demonstrated that dispatch reached the intended gate. External failures tied to an unavailable neighboring checkout were kept separate from the repaired runtime claim.

### Outcome

The message-bus path was restored without inventing a new incompatible implementation, and the regression suite now protects the failure mode that exposed the missing module.

**Skills demonstrated:** debugging, source archaeology, regression testing, dependency isolation, Python, safe restoration.

---

## How I Work

Across these projects, the recurring pattern is:

**classify → make the smallest safe change → verify the real path → preserve evidence → close cleanly**.

That approach is useful for automation, internal tools, implementation engineering, QA/test automation, repository maintenance, and junior software-development work where correctness and recoverability matter as much as writing code.