# Engineering Proof — Victor Dixon

This page is for reviewers who want to distinguish implemented engineering work from portfolio claims quickly.

## What to look for

My strongest signal is not the number of projects. It is the operating pattern repeated across them:

**define a boundary → implement a small change → test the real path → inspect evidence → preserve recovery options → close cleanly**

I intentionally document incomplete, experimental, blocked, and legacy paths instead of presenting every repository as production-ready.

## Public repositories you can inspect now

### 1. AgentTools / WE ARE SWARM

**Repository:** https://github.com/Victor-Dixon/AgentTools

What to verify:

- installable Python package metadata for `swarm-mcp`;
- multi-agent messaging, memory, task coordination, consensus, conflict detection, work-proof and verification components;
- CLI and MCP server entry points;
- GitHub Actions CI that installs the development package, runs pytest, checks import-healer coverage, runs a security scan, and audits imports;
- current blockers and release limitations documented instead of hidden.

Representative verification path:

```bash
git clone https://github.com/Victor-Dixon/AgentTools.git
cd AgentTools
python -m pip install -e ".[dev]"
pytest tests/ -v
```

Engineering signal: reusable coordination infrastructure rather than a single generated demo.

---

### 2. ProjectScanner

**Repository:** https://github.com/Victor-Dixon/projectscanner

What to verify:

- a real Python repository-scanning implementation;
- local and GitHub project inventory paths;
- source/file structure extraction;
- JSON and Markdown evidence exports;
- explicit separation between scanner evidence and governance authority;
- a documented list of known incomplete paths instead of unsupported feature claims;
- pytest regression gate.

Representative verification path:

```bash
git clone https://github.com/Victor-Dixon/projectscanner.git
cd projectscanner
python -m pip install -e .
pytest -q
python main.py --scan . --export-context
```

Engineering signal: evidence generation, domain boundaries, and honest failure/unknown documentation.

---

### 3. Network Scanner

**Repository:** https://github.com/Victor-Dixon/network-scanner

What to verify:

- Python IPv4/ARP discovery;
- TCP port and banner helpers;
- local service/version vulnerability lookup;
- optional AbuseIPDB reputation integration;
- anomaly-detection research modules;
- explicit documentation of non-implemented and experimental paths;
- documented regression result of 56 passing tests from the current repository audit.

Representative verification path:

```bash
git clone https://github.com/Victor-Dixon/network-scanner.git
cd network-scanner
python3 -m pip install -r requirements.txt
python3 -m pytest -q
```

Engineering signal: security/networking code with tests and maturity boundaries, not a claim of enterprise-scanner readiness.

---

### 4. HomeSchool Mastery

**Repository:** https://github.com/Victor-Dixon/HomeSchool_Mastery

What to verify:

- canonical Flask/Jinja/SQLite application under `lessons_lan/`;
- student and parent/admin workflows;
- lesson completion, practice, games, XP/mastery, feedback, and local persistence;
- optional local Ollama coaching;
- test coverage for routes, lessons, mastery, rewards, generators, practice, and Story Duel behavior;
- explicit data-safety guidance around the SQLite learner database.

Representative verification path:

```bash
git clone https://github.com/Victor-Dixon/HomeSchool_Mastery.git
cd HomeSchool_Mastery/lessons_lan
python -m pip install -r requirements.txt
pytest -q
```

Engineering signal: an end-to-end local application with persistence, roles, tests, and operator/data-safety concerns.

## Private systems represented through sanitized evidence

Several of my larger systems are private because they contain operational infrastructure, portfolio governance, deployment configuration, or other non-public working material. I do not ask reviewers to accept those systems on trust. The profile contains sanitized case studies that describe architecture, decisions, verification, and outcomes without exposing credentials or private configuration.

Representative private systems include:

- Dream.OS — message-driven multi-agent repository automation runtime;
- DreamVault — governance, evidence, planning, provenance, and retrieval layer;
- Dream.OS Swarm Brain — FastAPI/SQLite live-state and planner service;
- governed multi-domain deployment infrastructure;
- TradingRobotPlug — deterministic backtesting and paper-readiness work;
- GitHub Architect Bot — portfolio intelligence and governed repository operations.

See [CASE_STUDIES.md](CASE_STUDIES.md) and [CAPABILITY_MATRIX.md](CAPABILITY_MATRIX.md).

## Evidence standards I use

A completion claim should be backed by one or more of:

- passing targeted tests;
- a reproducible command;
- a diff or commit;
- a live HTTP/API response;
- a CI result;
- an exact branch/commit comparison;
- a machine-readable report or manifest;
- a negative control showing the protection/test actually detects the failure;
- a rollback or recovery path when the change affects production or shared state.

## Signals I intentionally avoid

I do not use these as substitutes for engineering evidence:

- repository count by itself;
- screenshots of generated code;
- unsupported "production-ready" labels;
- vague AI-agent completion statements;
- fake performance or profitability claims;
- pretending a prototype, research lane, or historical branch is current production software.

## Ten-minute review path

If you only have ten minutes:

1. Read the top of the profile README.
2. Open AgentTools and inspect `pyproject.toml` plus `.github/workflows/swarm_ci.yml`.
3. Open ProjectScanner and inspect its known-unknown section plus test command.
4. Open Network Scanner and inspect its implemented/not-implemented split and tests.
5. Open one case study and look for problem → implementation decision → verification → outcome.

That sequence gives a better picture of my engineering ability than repository count or generated screenshots.