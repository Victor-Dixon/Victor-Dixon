# Victor Dixon

**Automation Developer · AI Systems Orchestrator · Multi-Agent Workflow Builder**

I build Python automation, multi-agent systems, developer tooling, repository intelligence, deployment workflows, and local-first applications.

I use AI coding agents aggressively. My role is not pretending every generated line was hand-written — it is **architecting the system, decomposing work, defining authority boundaries, directing parallel agents, designing verification gates, classifying failures, and deciding what is safe to promote**.

In plain terms: I vibe-code with a swarm, then make the swarm prove its work.

## Engineering Proof First

If you are reviewing this profile for engineering ability, start here:

**[ENGINEERING_PROOF.md](ENGINEERING_PROOF.md)** — a 10-minute review path through runnable public code, CI/test gates, known limitations, and representative architecture decisions.

| Public project | What to inspect | Verification signal |
| --- | --- | --- |
| **[AgentTools / WE ARE SWARM](https://github.com/Victor-Dixon/AgentTools)** | Python package structure, multi-agent coordination, MCP/CLI entry points, conflict/work-proof systems | GitHub Actions runs pytest, coverage/import checks, security scan, and import audit |
| **[ProjectScanner](https://github.com/Victor-Dixon/projectscanner)** | Repository scanning, source-structure extraction, JSON/Markdown evidence exports, explicit known unknowns | `pytest -q` regression gate and reproducible local scan path |
| **[Network Scanner](https://github.com/Victor-Dixon/network-scanner)** | ARP discovery, TCP/banner helpers, vulnerability/reputation tooling, experimental anomaly detection | Documented regression testing plus explicit non-production boundaries |
| **[HomeSchool Mastery](https://github.com/Victor-Dixon/HomeSchool_Mastery)** | Flask/Jinja/SQLite app, student/admin workflows, local persistence, mastery/game systems | Canonical pytest suite plus explicit learner-data safety guidance |

## What I Actually Do With AI

My workflow is orchestration-first:

```text
problem
→ establish authority
→ split into bounded lanes
→ dispatch agents in parallel
→ require tests / diffs / runtime evidence
→ classify failures
→ salvage good work
→ reject unsafe or stale work
→ promote only verified changes
→ reconcile planner/runtime state
```

I optimize for:

- **Fast TDD:** small change → targeted test → verification → commit-ready closure.
- **Mechanical proof:** tests, CI, mutation checks, diffs, runtime receipts, live HTTP/API checks, and negative controls.
- **Fail-closed automation:** stale or contradictory state produces no executable assignment rather than agent guesswork.
- **Explicit authority:** planner chooses what, dispatcher assigns who, worker decides how.
- **Safe parallelism:** isolated worktrees, ownership boundaries, promotion manifests, and no blind branch merges.
- **Salvage before deletion:** historical branches are classified and mined for bounded capabilities before destructive cleanup.
- **Honest status:** implemented, locally verified, merged, deployed, live-verified, and complete are different states.

## Recent Dream.OS / DreamVault Engineering

Recent private-system work includes:

- Built **machine-enforceable planning governance** that rejects duplicate task IDs, stale `NEXT_UP` projections, unsupported completion claims, and unsynchronized execution changes.
- Designed **evidence-gated lifecycle contracts** separating patched, CI-verified, merged, deployed, live-verified, reconciled, and complete states.
- Built **portfolio-wide task scoring and deterministic dispatch**, with explicit separation between planner, dispatcher, and worker authority.
- Added **role-aware secondary assignment** without task-title inference, worker reranking, or primary-task overlap.
- Added **local planning preflight and repo-local pre-push verification** so planner defects are caught before CI.
- Diagnosed and fixed a planning validator that could accidentally shallow a full Git clone; regression verification preserved a **173-commit full history** and completed a **273-test run with zero new failures**.
- Recovered a quarantined **SHIP_EVENT / closeout automation pipeline** using path-scoped salvage instead of wholesale cherry-picks; integrated verification reached **9/9 passing tests**.
- Moved DreamVault required checks to a **self-hosted VPS runner** when hosted CI became unavailable instead of bypassing verification.
- Built append-only **execution-ledger hooks and MCP tooling** for claims, closeouts, scanner attestations, and tool events; focused verification reached **47 tests** for the hook layer and **16 tests** for the MCP bridge.
- Performed multi-branch authority reconciliation that explicitly blocked promotion when a candidate introduced package-shadowing and disabled a closeout enforcement gate.

The pattern matters more than any single feature: **AI output is a candidate, not completion.**

## Core Engineering Areas

- **Automation & multi-agent systems:** typed task messages, routing, claim/ack lifecycles, shared state, conflict controls, verification gates, operator closeouts, and agent orchestration.
- **Backend & data:** FastAPI, Flask/Jinja, REST APIs, SQLite, JSON/YAML contracts, feed/export pipelines, and retrieval/RAG workflows.
- **Developer tooling:** Python CLIs, repository scanners, GitHub governance, cleanup/consolidation automation, manifests, evidence reports, and MCP tooling.
- **Testing & reliability:** pytest, regression tests, TDD, mutation/negative controls, smoke tests, real-path verification, and fail-closed validation.
- **Infrastructure & deployment:** GitHub Actions, self-hosted runners, Linux/Ubuntu, Nginx, Tailscale, systemd, Docker/Compose, SFTP, HTTPS verification, and rollback-aware delivery.
- **Applied systems:** education software, defensive networking, deterministic backtesting/paper-trading systems, OpenCV/PyQt creator tooling, local LLM operations, and Roblox/Rojo systems.

## Larger Systems

Several larger systems are private because they contain operational infrastructure, governance state, deployment configuration, or other non-public working material. I represent those through sanitized engineering evidence rather than asking reviewers to trust private repository claims.

Representative systems:

- **Dream.OS** — multi-agent automation architecture for repository work, planning, verification, and bounded autonomous execution.
- **DreamVault** — governance, evidence, planning, provenance, task routing, execution ledger, and operator-control layer.
- **Dream.OS Swarm Brain** — FastAPI/SQLite live-state and planner service.
- **Governed website fleet** — changed-site resolution, strict dry-run, SFTP deployment, live HTTPS verification, and rollback controls.
- **TradingRobotPlug** — deterministic backtesting, paper-execution evidence, and explicit live-readiness boundaries.
- **GitHub Architect Bot** — evidence-first portfolio audits, task/planner synthesis, branch governance, and guarded repository operations.

See **[Engineering Case Studies](CASE_STUDIES.md)** for problem → approach → verification → outcome breakdowns.

## Technical Profile

**Languages:** Python, JavaScript/TypeScript, HTML/CSS, PowerShell, Bash; project experience with Java and Luau  
**Backend/Data:** FastAPI, Flask/Jinja, REST APIs, SQLite, JSON/YAML, feed/export pipelines, retrieval/RAG  
**AI / Automation:** multi-agent orchestration, prompt/task pipelines, MCP, local LLMs, tool-driven agents, structured verification workflows  
**Engineering:** Git/GitHub, pytest, regression/mutation/negative-control testing, CLI tooling, debugging, repository governance  
**Infrastructure:** Linux/Ubuntu, Nginx, Tailscale, systemd, Docker/Compose, SFTP, GitHub Actions, self-hosted runners  
**Additional:** PyQt/OpenCV, defensive networking, deterministic backtesting, Ollama/local AI operations, Roblox/Rojo

## Resume & Application Material

- **[ATS One-Page Resume](RESUME_ATS_ONE_PAGE.md)** — concise application version.
- **[Automation / Software Resume](RESUME_AUTOMATION_SOFTWARE.md)** — automation, internal tools, QA, AI workflow, junior software.
- **[Technical Implementation / Operations Resume](RESUME_TECHNICAL_IMPLEMENTATION.md)** — implementation, technical operations, application support.
- **[Capability Matrix](CAPABILITY_MATRIX.md)** — evidence-backed capability inventory with maturity labels.
- **[Project Index](PROJECT_INDEX.md)** — portfolio inventory and project-maturity boundaries.
- **[Application Pack Guide](APPLICATION_PACK.md)** — role-family selection and tailoring workflow.

## Primary Role Direction

**Automation / AI workflow / internal tools engineering**, with adjacent fit for implementation engineering, QA/test automation, backend development, developer tooling, and technical operations.

## Engineering Principle

> Orchestrate fast. Verify hard. Promote only what survives proof.
