# Phase 2 Scorecard — Priority 1 Remediation Runbook

> **Project Coo-Cah | Orchestration**
> **Document Version:** 1.0 | **Owner:** Programme Management Office (PMO)
> **Status:** ACTIVE
> **Update Frequency:** Weekly (until all P1 items close)

---

## Objective

Execute and close all Priority 1 blockers in the Phase 2 scorecard using one controlled sequence, explicit owners, and shared exit criteria.

---

## Scope

This runbook tracks P1 workstreams across these repositories:

1. `aku-platform-contracts`
2. `Aku-Hardware`
3. `Aku-EdgeHub`
4. `Akulearn_docs` (validated first through `AkuWorkspace`)
5. `Aku-Telhone`

---

## Required Merge Order

1. `aku-platform-contracts`
2. `Aku-Hardware`
3. `Aku-EdgeHub`
4. `Akulearn_docs` sync fix (pilot-validated in `AkuWorkspace`)
5. `Aku-Telhone`

No repository may skip ahead if it depends on an unresolved upstream P1 item.

---

## Workstream Checklists

### 1) Stabilize shared contracts (`aku-platform-contracts`)

- [ ] Repair `publish.yml` so tagged releases succeed.
- [ ] Publish `v0.1.1` (or newer) and verify installability.
- [ ] Standardize dependent repos to one contracts version pin.
- [ ] Add CI guard to fail when dev/runtime contract pins drift.

### 2) Unblock hardware population pipeline (`Aku-Hardware`)

- [ ] Create or restore `main` from current scaffold branch.
- [ ] Set default branch to `main`.
- [ ] Add minimum passing CI on `main` (lint/structure at minimum).
- [ ] Re-run upstream population workflow and confirm success.

### 3) Break EdgeHub failure loop (`Aku-EdgeHub`)

- [ ] Merge test track fix: remove Postgres coupling in CI and run SQLite-stable tests.
- [ ] Merge Docker track fix: resolve private dependency access without secret leakage.
- [ ] Merge consolidated fix only after both tracks are green together.
- [ ] Delete stale branches after merge.

### 4) Fix scaffold sync corruption at source (`Akulearn_docs`)

- [ ] Patch sync logic so workflow files cannot be overwritten by markdown/prose payloads.
- [ ] Add path/type validation and fail-fast checks in sync workflow.
- [ ] Re-run sync into `AkuWorkspace` as pilot and verify no YAML corruption.
- [ ] Roll out sync to remaining repositories after pilot verification.

### 5) Collapse stacked PRs and merge canonical recovery (`Aku-Telhone`)

- [ ] Select newest complete PR as canonical (lint + runtime bug + coverage fixes).
- [ ] Rebase once on latest `main`, run full CI, then merge.
- [ ] Close superseded PRs and delete stale branches.
- [ ] Confirm `_upsert_profile` runtime path and coverage threshold are green post-merge.

### 6) Execution governance for all P1 work

- [ ] Use one shared P1 tracking board with one owner per repository.
- [ ] Enforce per-repo done criteria (`main` green, no blocking duplicate PRs, no stale conflicting branches).
- [ ] Block P2 promotion until all P1 done criteria pass.

---

## Exit Criteria (Per Repository)

Each repo is **DONE** only when all are true:

1. `main` branch is green on required CI.
2. Canonical fix PR is merged.
3. Superseded or duplicate blocking PRs are closed.
4. Stale conflicting branches are deleted.
5. Repo-specific P1 acceptance checks pass (from checklist above).

---

## Tracking Board Template

| Repository | Owner | Status | Canonical PR | CI (main) | Duplicate PRs Closed | Stale Branches Pruned | Notes |
|-----------|-------|--------|--------------|-----------|----------------------|-----------------------|-------|
| aku-platform-contracts | TBD | NOT_STARTED | TBD | ❌/✅ | ❌/✅ | ❌/✅ | |
| Aku-Hardware | TBD | NOT_STARTED | TBD | ❌/✅ | ❌/✅ | ❌/✅ | |
| Aku-EdgeHub | TBD | NOT_STARTED | TBD | ❌/✅ | ❌/✅ | ❌/✅ | |
| Akulearn_docs | TBD | NOT_STARTED | TBD | ❌/✅ | ❌/✅ | ❌/✅ | |
| AkuWorkspace (pilot) | TBD | NOT_STARTED | TBD | ❌/✅ | N/A | N/A | Pilot validation only |
| Aku-Telhone | TBD | NOT_STARTED | TBD | ❌/✅ | ❌/✅ | ❌/✅ | |

---

## Governance Cadence

- Weekly PMO review until all P1 items close.
- Emergency review within 24 hours for any new blocker on a P1 repo.
- Change requests to this runbook require PMO + Engineering Lead approval.

---

## Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2026-05-10 | PMO | Initial Priority 1 remediation runbook |

