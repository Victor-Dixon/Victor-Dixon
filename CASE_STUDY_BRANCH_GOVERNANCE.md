# Case study: Evidence-first branch governance across a multi-repository portfolio

**Engineer:** Victor Dixon  
**Focus:** Technical discovery, developer tooling, change control, verification, and recovery  
**Scope:** 25 operational repositories in the Dream.OS portfolio  
**Status:** Dated engineering evidence; final branch-retirement reconciliation is ongoing.

## The problem

A collection of related repositories accumulated active feature branches, historical implementations, duplicate work, and branches containing work not yet integrated into the canonical code line. Branch names, age, and a superficial "merged" label were not reliable reasons to delete a ref. In some histories, rewritten ancestry also made ordinary ahead/behind comparisons insufficient to establish whether unique content remained.

The engineering problem was not "delete as many branches as possible." It was to separate **safe retirement** from **work that must be preserved**, without interrupting current contributors or removing the last copy of a useful implementation.

## My approach

I organized the cleanup around an explicit evidence and authority boundary:

```text
Repository inventory and scanner outputs
    -> inspect PR ownership, exact branch SHA, history, and unique content
    -> classify: active / salvage / hold / retained / retirement candidate
    -> record a governed decision and its required proofs
    -> guarded, SHA-locked execution where authorized
    -> verify the remote ref is absent and record a receipt
    -> recensus the portfolio and reconcile changes
```

**Technical discovery:** Inventory branches across the portfolio and distinguish the default branch from temporary work. Where ProjectScanner evidence is unavailable or stale, identify that gap rather than treating an old scan as current proof; an authorized bounded live GitHub inspection can provide a separately labeled snapshot.

**Separation of concerns:** The scanner produces observations. The governance store records classifications, decisions, and approvals. The execution tool is responsible for enforcing deletion preconditions. A dashboard or report is a consumer of the resulting state, not independent authority to mutate a repository.

**Safeguards:** Require the exact expected branch SHA, default/protected-branch checks, PR-ownership checks, and appropriate ancestry/content evidence. For zero-ahead retirement candidates, worktree and live-dependency checks must be established rather than assumed. If evidence is insufficient, preserve the branch for a salvage or retention review.

**Verification:** Treat a queued request as different from successful execution. A retirement is closed only after the executor's outcome and remote absence are verified, followed by a new portfolio census.

## Decisions and trade-offs

| Decision | Why it matters |
| --- | --- |
| Retain branches with unresolved unique work | An apparently stale ref may be the last recoverable copy of a feature, fix, or decision record. |
| Use exact-SHA checks before mutation | Prevents a decision about an old commit from being applied after a branch has moved. |
| Keep inspection separate from deletion authority | Producing a cleanup recommendation does not grant permission to execute it. |
| Recheck live PR ownership and dependencies | Avoids deleting a ref currently being used by a contributor or an automated process. |
| Reconcile counts after each wave | A net count can hide concurrent branch creation, retention, and retirement. |

## Dated evidence and current limitation

- **September 18, 2026:** A recorded portfolio snapshot showed **71 total branches / 46 non-default branches across 25 operational repositories**.
- **September 19, 2026:** A separate read-only GitHub branch-list census showed **70 total / 45 non-default**.
- Three previously identified zero-ahead retirement candidates were not present in the later remote-branch lookup. Their absence alone does **not** establish which execution path removed them: authorization and deletion receipts require reconciliation.
- The September 19 count is a point-in-time inventory, **not** proof that cleanup is finished or that every remaining non-default branch should be deleted.

The detailed decision ledger and executor records remain in private operational repositories. This public case study describes the method and dated, aggregate observations; it does not publish internal credentials, client data, infrastructure addresses, or unreviewed private implementation details.

## What this demonstrates

This project applies the same method needed for forward-deployed engineering in an existing customer environment: inspect the system before proposing a change; make ownership and blast radius explicit; retain recovery options; require appropriate human authority for consequential actions; and distinguish implementation from verified operational outcomes.

**Public supporting code:** [ProjectScanner](https://github.com/Victor-Dixon/projectscanner) (repository inspection and evidence export) and [AgentTools](https://github.com/Victor-Dixon/AgentTools) (reusable coordination and verification primitives). Their public READMEs document the supported and incomplete surfaces; this case study does not claim that every proposed end-to-end integration is deployed.

## Evidence needed for final closeout

- Reconcile dated branch inventories by repository, ref, and commit SHA, including intervening additions and retirements.
- Correlate candidate retirements with the executor's approval, request, and receipt records.
- Publish a sanitized, reproducible demonstration of one successful gated retirement **and** one refusal of an unsafe deletion.
- Verify the current public status projection against its actual source timestamp before using it as a live operating-system demonstration.

**Review note:** This is an engineering case study, not a claim of a completed client engagement, a production security certification, or an independently audited system.
