# Engineering Case Studies

These case studies summarize representative work from public and private projects. Private-system details are intentionally limited to architecture, engineering decisions, verification, and outcomes rather than credentials or sensitive configuration.

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

A bounded automation system for git, lint, test, scan, audit, repository-maintenance and related engineering workflows where task ownership and completion can be inspected after execution.

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
- Keep canonical task/status documents bounded so the immediate queue does not become another backlog.

### Verification

The repository uses Python tests, documented source-of-truth status, package/version gates, and explicit blockers rather than presenting incomplete release work as complete.

### Outcome

Reusable coordination primitives for multi-agent engineering workflows that treat agent orchestration as software infrastructure rather than prompt choreography.

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

A repeatable website deployment workflow with stronger source authority, smaller blast radius, and live verification after publishing.

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

## 6. Dream.OS Swarm Brain — FastAPI/SQLite Planner and Live-State Service

### Problem

Task, event, project, and closeout information existed across multiple repositories and operator surfaces. Consumers needed a small service that could expose useful live-state without turning every historical artifact into current authority.

### Approach

I built and maintained a FastAPI/SQLite service that:

- initializes a local state database;
- imports allowlisted task/planner sources;
- exposes task, event, project, closeout and advisory endpoints;
- exports JSON feeds for websites and agents;
- classifies tasks into queues;
- keeps advisory/history content non-canonical;
- includes VPS/headless deployment and operator scripts.

### Engineering Decisions

- Keep DreamVault as fleet governance authority rather than duplicating policy in the API service.
- Use allowlists to prevent archive/quarantine material from becoming live planner state.
- Separate protected service operations from read/advisory access.
- Make deployment/path configuration environment-driven rather than hardcoded to one machine.

### Verification

The repository documents pytest and smoke-test gates plus feed-export checks.

### Outcome

A small service boundary between durable governance data and consumers that need queryable, machine-readable operational state.

**Skills demonstrated:** FastAPI, SQLite, API design, Python services, data import/export, Linux/VPS operations, testing.

---

## 7. TradingRobotPlug — Deterministic Backtesting and Paper-Readiness Boundaries

### Problem

Trading repositories can easily overstate readiness by mixing research code, historical experiments, live credentials, broker actions and performance claims. The project needed a safer consolidated baseline before autonomous execution could be trusted.

### Approach

I consolidated TradingRobotPlug around explicit current-state manifests and a reproducible test environment. The deterministic baseline uses synthetic OHLCV fixture data and writes reproducible paper-execution evidence without requiring network, broker, database, GUI or ML dependencies.

The project also separates:

- imported/donor research from canonical runtime code;
- paper/dry-run behavior from live order submission;
- production-readiness documentation from strategy research;
- autonomous-session work from claims of profitable or live-ready trading.

### Engineering Decisions

- Default sanitized configuration to dry-run/local-fixture behavior.
- Treat deterministic verification data as test evidence, not historical-performance evidence.
- Keep live trading behind explicit readiness gates.
- Require reproducible offline tests before expanding broker/runtime autonomy.

### Outcome

A safer trading-automation development surface where backtest/paper evidence can be reproduced without implying live-market readiness or profitability.

**Skills demonstrated:** Python, deterministic testing, backtesting architecture, paper-trading workflows, configuration safety, production-readiness governance.

---

## 8. HomeSchool Mastery — Local-First Family Learning Platform

**Public repository:** [Victor-Dixon/HomeSchool_Mastery](https://github.com/Victor-Dixon/HomeSchool_Mastery)

### Problem

A household learning system needed to make daily work visible and motivating while remaining locally controlled and usable from devices on the home network.

### Approach

The canonical application is a Flask/Jinja/SQLite web app that provides:

- daily lesson/checklist flows;
- TEKS/STAAR-aligned Math and Reading/ELAR practice;
- learning games and mastery gates;
- XP, levels, boss fights and gear rewards;
- student feedback;
- parent/admin account and lesson management;
- optional local Ollama coaching.

### Engineering Decisions

- Keep student data local instead of requiring cloud infrastructure.
- Separate the canonical Flask application from older Node/support prototypes.
- Preserve and back up SQLite data before destructive maintenance.
- Make current implementation status explicit where standards coverage or integrations are incomplete.

### Verification

The canonical app has pytest coverage for smoke routes, lessons, mastery, rewards, generator behavior, practice and Story Duel behavior.

### Outcome

A usable local-first education product combining web application development, data persistence, gamification, parent/admin operations and optional local AI.

**Skills demonstrated:** Flask, Jinja, SQLite, product design, web application development, tests, local AI integration.

---

## 9. Private Dream Office Gateway — Tailnet-Only API Exposure

### Problem

An operator control surface needed access to a private Dream.OS API without exposing the backend directly to the public internet.

### Approach

I built and verified a private connectivity path using:

- a Windows-hosted API bound to a Tailscale address;
- a VPS connected through the same Tailnet;
- Nginx/control-plane routing on the hosted side;
- explicit endpoint validation for state retrieval and task/claim operations;
- local artifacts for operator actions and verification.

### Engineering Decisions

- Bind the backend to the private Tailnet instead of `0.0.0.0` public exposure.
- Verify connectivity from the real remote consumer rather than only testing localhost.
- Treat firewall/routing failures separately from application failures.
- Keep public control surfaces separate from private execution authority.

### Verification

Remote VPS-to-Windows API reachability returned HTTP 200 on the validated state endpoint, and product/API validation gates were run separately from network reachability.

### Outcome

A private operator/API bridge that demonstrates practical networking, service exposure, remote verification, and security-boundary reasoning.

**Skills demonstrated:** Tailscale, Nginx, REST APIs, Windows/Linux networking, troubleshooting, private-service architecture.

---

## 10. Network Scanner — Defensive Networking and Test Hardening

**Public repository:** [Victor-Dixon/network-scanner](https://github.com/Victor-Dixon/network-scanner)

### Problem

A small security-research repository had multiple network and ML experiments but needed an honest boundary between implemented diagnostic utilities and incomplete/experimental features.

### Approach

The project contains authorized-network tooling for:

- IPv4 ARP discovery;
- TCP port scanning and banner helpers;
- local service/version vulnerability lookup;
- optional AbuseIPDB reputation checks;
- Isolation Forest and Keras anomaly-detection experiments;
- encrypted-traffic heuristic helpers.

I kept unsupported claims out of the production description and documented missing packaging/dependency/CLI paths instead of presenting them as complete.

### Verification

The documented current regression gate records **56 passing tests** while still calling out remaining placeholder tests, dependency gaps and CI behavior that need hardening.

### Outcome

A recruiter-readable defensive networking project that shows Python/networking/testing breadth without overstating enterprise security maturity.

**Skills demonstrated:** Python networking, defensive security, APIs, pytest, anomaly-detection experimentation, technical documentation.

---

## 11. MeTuber — Real-Time Webcam Effects and Creator Tooling

### Problem

Streamers and creators need a local way to transform webcam video and publish the processed feed into conferencing/streaming tools without a cloud processing dependency.

### Approach

MeTuber combines:

- PyQt desktop GUI work;
- OpenCV frame processing and artistic filters;
- camera-device detection and threaded capture;
- preview and snapshot workflows;
- virtual-camera output paths for OBS/UnityCapture;
- adaptive performance controls and heuristic parameter optimization;
- experimental captions/plugins, Twitch scaffolding and WebSocket/browser tooling.

### Engineering Decisions

- Keep the most complete legacy/refactored webcam path separate from experimental V2 capabilities.
- Document which recording/streaming/plugin features are partial rather than implying production readiness.
- Treat camera/hardware-dependent tests differently from pure unit tests.

### Outcome

A desktop computer-vision/creator-tools project that broadens the portfolio beyond automation backends into real-time media processing and GUI development.

**Skills demonstrated:** Python, OpenCV, PyQt, threading/device handling, real-time processing, creator tooling.

---

## How I Work

Across these projects, the recurring pattern is:

**classify → make the smallest safe change → verify the real path → preserve evidence → close cleanly**.

That operating model is useful for automation, internal tools, implementation engineering, QA/test automation, technical operations, repository maintenance and software-development work where correctness and recoverability matter as much as writing code.