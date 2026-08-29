# Victor Dixon — Extended Project Resume

## Summary

Automation developer and systems builder focused on practical software: Python tooling, multi-agent execution infrastructure, repository intelligence, deployment automation, APIs, and operator workflows. I work best on systems that need stronger boundaries, clearer source-of-truth rules, better verification, or automation around repetitive engineering work.

For the concise hiring version, see [RESUME.md](RESUME.md). For deeper examples, see [CASE_STUDIES.md](CASE_STUDIES.md).

## Core Capabilities

| Capability | Representative evidence |
| --- | --- |
| Python automation | CLIs, task runners, repository tools, message-bus runtime work, validation and verification helpers. |
| Multi-agent systems | Typed task messages, routing, claim/ack lifecycle, messaging, shared memory, conflict detection, agent coordination. |
| Repo intelligence | Source-tree scanning, GitHub/local inventory, branch hygiene, consolidation reports, promotion manifests. |
| Testing and verification | pytest regression gates, negative controls, real-path verification, source-of-truth checks, closeout artifacts. |
| Deployment operations | Changed-site resolution, strict dry-runs, SFTP publishing, live HTTPS verification, rollback-aware workflows. |
| Web/API systems | JavaScript/TypeScript product surfaces, static sites, backend integrations, private operator APIs and control planes. |

## Featured Work

### Dream.OS

**Status:** private operational system; sanitized architecture described in [CASE_STUDIES.md](CASE_STUDIES.md).

Dream.OS is a Python message-driven automation runtime for repository work. It coordinates task transport, relay claim/ack lifecycles, guarded execution, agent routing, and verification around git, lint, test, scan, audit, and related engineering workflows.

My work emphasizes:

- explicit task contracts instead of unbounded agent invocation;
- fail-closed enforcement for invalid or prohibited work;
- machine-readable task/closeout artifacts;
- independent verification for higher-risk runtime changes;
- salvage and promotion manifests before destructive repository cleanup.

### AgentTools / WE ARE SWARM

**Public:** [github.com/Victor-Dixon/AgentTools](https://github.com/Victor-Dixon/AgentTools)

Reusable Python multi-agent coordination and operator tooling. The repository includes messaging, shared memory, task coordination, consensus, conflict detection, capability profiling, verification helpers, CLI workflows, and MCP-oriented integrations.

What it demonstrates:

- reusable coordination primitives rather than one-off prompt scripts;
- multiple agents sharing task and memory state;
- conflict detection before overlapping work becomes a repository problem;
- verifiable-work patterns and reusable engineering utilities.

### ProjectScanner

**Public:** [github.com/Victor-Dixon/projectscanner](https://github.com/Victor-Dixon/projectscanner)

Python repository scanning and inventory intelligence tool. ProjectScanner scans local projects and selected GitHub repositories, extracts source-tree/code structure, and exports JSON/Markdown evidence used before cleanup, consolidation, or promotion decisions.

What it demonstrates:

- filesystem and source-structure analysis;
- GitHub/local repository inventory;
- machine-readable evidence exports;
- explicit separation between generated intelligence and governance authority;
- honest documentation of incomplete paths and known unknowns.

### Governed Website Fleet and Deployment Automation

**Status:** private operational repository; sanitized workflow described in [CASE_STUDIES.md](CASE_STUDIES.md).

I maintain a multi-domain website repository with explicit canonical source roots, a deployment registry, changed-site resolution, strict dry-runs, SFTP publishing, live HTTPS verification, and rollback procedures.

The deployment model is designed to prevent common operational mistakes:

- generated deploy output cannot silently become source of truth;
- legacy/unclassified paths fail closed;
- only changed domains are eligible for deployment;
- production success requires live HTTP verification, not only a successful upload command.

### Message-Bus Runtime Recovery

A recent runtime repair required restoring an authoritative missing finite-state-machine implementation rather than creating a fresh incompatible replacement. I restored the correct source and regression coverage, added a dispatch-path regression test, and separated unrelated neighboring-environment failures from the repaired claim.

**Verification:** 29 targeted tests passed and dispatch reached the intended gate.

### Network Scanner

**Public:** [github.com/Victor-Dixon/network-scanner](https://github.com/Victor-Dixon/network-scanner)

Cybersecurity utility work around local network scanning, host discovery, and security experimentation.

### HomeSchool Mastery

**Public:** [github.com/Victor-Dixon/HomeSchool_Mastery](https://github.com/Victor-Dixon/HomeSchool_Mastery)

Product-oriented education workspace for homeschool planning, learning assistance, and practical automation.

## Engineering Principles

- Make the smallest safe change that can close the immediate problem.
- Verify the real product/runtime path rather than relying only on scratch harnesses.
- Treat source, generated output, salvage, and historical evidence as different classes.
- Preserve useful work before deletion or consolidation.
- Prefer explicit JSON/YAML/Markdown artifacts that humans and automation can both inspect.
- Use targeted regression tests and negative controls to prove important enforcement behavior.
- Leave repositories commit-ready with a readable closure trail.

## Education and Career Direction

**Lone Star College System** — Business Administration coursework, 33 earned college credit hours.

Current career direction: transition from armed security into software/automation work through portfolio evidence, real engineering projects, targeted certifications, and optional continued coursework rather than waiting for a degree to begin applying.

## Target Roles

- Automation Developer
- Junior Software Developer
- Implementation Specialist / Implementation Engineer
- QA / Test Automation
- Technical Project Coordinator
- Technical Support / Application Support
- Internal Tools Developer
- AI Workflow / Agent Automation Engineer

## Current Portfolio Goal

Turn operational engineering work into a recruiter-readable public surface without overstating private implementation details. The profile repository is intended to provide three layers:

1. [README.md](README.md) — fast recruiter overview.
2. [RESUME.md](RESUME.md) — concise hiring resume.
3. [CASE_STUDIES.md](CASE_STUDIES.md) — problem, approach, verification, and outcome evidence.
