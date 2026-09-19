# Forward-deployed engineering: delivery model and evidence

**Victor Dixon — AI automation, systems integration, and governed deployment**

This document explains how I approach engineering work inside an existing operating environment. It is a proposed delivery model informed by my own engineering portfolio, **not** a claim that these exact phases have been completed for a paying client or that Dream.OS is a packaged, production-certified product.

## The customer problem I work on

A business has repetitive technical work spread across applications, repositories, data sources, and manual handoffs. An automation prototype alone does not solve the operational problem if it lacks ownership, access control, error handling, testing, and a way to hand it over safely.

My approach is to start with the existing environment and design a **bounded implementation** with a measurable outcome.

## Delivery sequence

| Stage | Activities | Reviewable deliverable | Gate to continue |
| --- | --- | --- | --- |
| 1. Discover | Interview the process owner; map current steps, systems, data flows, access, failure modes, and constraints. | A concise problem statement, current-state workflow, source inventory, and list of unknowns. | Confirm the actual owner, requested outcome, authorized scope, and data-handling limits. |
| 2. Specify | Define an initial use case, exclusions, interfaces, success metrics, ownership, and rollback criteria. | One-page implementation brief and acceptance tests. | Obtain explicit approval of the bounded scope before making consequential changes. |
| 3. Integrate | Build the narrowest useful API, script, agent tool, or application adapter; use existing infrastructure where practical. | Reproducible implementation, configuration contract, and change record. | Preserve credentials and customer data boundaries; require review for production mutations. |
| 4. Verify | Exercise success, failure, stale-input, permissions, and recovery paths with representative permitted test data. | Tests, logs/receipts, known limitations, and a deployment decision. | Treat an agent's completion message as a claim, not verification. |
| 5. Deploy and hand off | Deploy into the approved environment, test real endpoints, document monitoring, rollback, incident routing, and ownership. | Deployment receipt, operator runbook, acceptance record, and remaining-risk register. | Mark **live-verified** only after checking the actual running surface. |

A paid pilot, if agreed, should specify an actual customer process, success criteria, budget, change permissions, data retention, support window, and handoff owner. This portfolio does not imply any particular commercial engagement has occurred.

## How my projects map to that sequence

| Portfolio component | Demonstrable role | Evidence boundary |
| --- | --- | --- |
| [ProjectScanner](https://github.com/Victor-Dixon/projectscanner) | Repository discovery and machine-readable source/inventory evidence. | The public project documents partial/unsupported analysis paths; scanner output is input to decisions, not approval to mutate a system. |
| DreamVault (private) | Durable tasks, decisions, evidence, approval manifests, and closeouts. | Repository documentation demonstrates the governance model; current cross-repository runtime activation must be verified separately. |
| [AgentTools](https://github.com/Victor-Dixon/AgentTools) | Reusable messaging, coordination, conflict-detection, and verification utilities. | Public package/core tests and CLI examples are inspectable; the legacy audit and publication status are distinct from the blocking package gate. |
| Dream.OS runtime (private consolidation) | Message-driven task execution with explicit policy, routing, and verification boundaries. | The historical Dream.os-Core repository does not, by itself, prove the authority or live status of the consolidated runtime. |
| GitHub Architect Bot (private) | Evidence-led portfolio governance and guarded GitHub operations. | Destructive actions require actual authorization, exact-head checks, executor receipts, and remote-state verification. |
| Website and operator surfaces (private source; selected public-facing sites) | Status, deployment outputs, and review interfaces for humans. | A published snapshot is not equivalent to live runtime state; verify source timestamp, freshness, and actual deployed behavior. |

**No single row establishes a complete production integration.** The end-to-end claim requires one demonstrable trace from approved input to verified outcome in a controlled environment.

## Representative engineering case study

[Branch governance across 25 operational repositories](CASE_STUDY_BRANCH_GOVERNANCE.md) shows the discovery → classification → authorization → guarded execution → verification method applied to my own repository portfolio. It includes dated counts, preservation rules, and outstanding receipt-reconciliation work.

For runnable public code and narrower technical evidence, start with [Engineering Proof](ENGINEERING_PROOF.md).

## One bounded demonstration to publish next

Build a **synthetic-data-only, read-only first** demonstration that does not access customer data or publish secrets:

1. Scan an explicitly allowlisted sample repository and export deterministic JSON inventory.
2. Produce a proposed change with its supporting evidence, risk classification, and explicit approval requirement.
3. Demonstrate that an unsafe or stale candidate is rejected, with a negative-control test.
4. Run an approved change only in a disposable test repository and record exact input/ref, test results, executor outcome, and final state.
5. Render the result in a report or dashboard carrying its own source timestamp; show that stale source data is labeled stale.

**Acceptance:** A reviewer can independently replay the safe path and the refusal path, inspect the test data and resulting artifacts, and identify which implementation acts as scanner, decision authority, executor, and reporting surface.

**Current status:** Proposed portfolio demonstration; not represented here as already implemented or deployed.

## Professional boundaries

- No credentials, access tokens, private IPs, sensitive logs, client documents, or unreviewed private-source excerpts in public evidence.
- No live customer writes, account changes, outreach, trading operations, or other consequential automation without separately established authority.
- No destructive repository action based solely on a scanner recommendation, a branch name, a stale dashboard, or a historical PR status.
- If an artifact is old, a CI gate is blocked, or a test cannot be run, report **unverified** rather than upgrading the claim to complete.
- The deliverable is a working, supportable customer outcome—not the number of agents, repositories, or generated files.
