# Tier 1 Baseline Go/No-Go Checklist (5-Repo Lock)

> **Project Coo-Cah | Orchestration**
> **Owner:** Group CTO / PMO / DT Engineering Lead
> **Use this before:** Expanding onboarding beyond the current 5 baseline repos

---

## Purpose

This checklist is the hard readiness baseline that must be met before moving beyond the current 5 synchronized factory repositories and before claiming Tier 1 factory coverage readiness.

---

## 1) Repo Scope Lock

- [ ] Confirm active automation scope is exactly:
  - `coo-cah-factory-chemicals-plastics`
  - `coo-cah-factory-chemicals-metallurgical`
  - `coo-cah-factory-electronics-power`
  - `coo-cah-factory-electronics-personal`
  - `coo-cah-factory-electronics-kitchen`
- [ ] Confirm Tier 1 core factories are fully represented in that scope:
  - Plastics
  - Metallurgical
  - Electronics Power

---

## 2) Blueprint Structure Completeness (Per Baseline Repo)

For each of the 5 baseline repos:

- [ ] `README.md`
- [ ] `docs/index.md`
- [ ] `mkdocs.yml`
- [ ] `MASTER_REPO_REF.md`
- [ ] `docs/master-repo-ref.md`

---

## 3) Gate 3 Artifact Completeness (Per Baseline Repo)

For each of the 5 baseline repos:

- [ ] `docs/sensor-map.md`
- [ ] `docs/bim/README.md`
- [ ] `docs/bim/zone-boundaries.md`
- [ ] `docs/bim/asset-anchors.md`
- [ ] Required Gate 3 headers present in:
  - `docs/sensor-map.md`
  - `docs/bim/zone-boundaries.md`
  - `docs/bim/asset-anchors.md`

---

## 4) CI Quality Gates (Master Repo + Baseline Repos)

- [ ] Documentation build passes (`mkdocs build --strict`)
- [ ] Markdown link check passes
- [ ] Gate 3 docs validation passes

---

## 5) Sync Automation Completeness

- [ ] `.github/workflows/apply-blueprint-alignment.yml` includes all 5 baseline jobs
- [ ] `.github/workflows/notify-factories.yml` matrix includes all 5 baseline repos
- [ ] Receiver workflow is present in each baseline repo (`.github/workflows/receive-blueprint-update.yml`)
- [ ] `blueprint-sync` issue label exists in each baseline repo

---

## 6) Tier 1 Release Governance (Pilot Exit Evidence)

Before wider rollout:

- [ ] Data quality threshold met with auditable scorecard evidence
- [ ] Business value proven (statistically valid KPI uplift vs baseline/control)
- [ ] Operational sustainability confirmed (no hidden manual rework burden)
- [ ] Financial value threshold met and signed by PMO/Finance
- [ ] Audit reproducibility signed by an independent reviewer
- [x] Governance approvals complete (Group CTO + PMO go/no-go sign-off)

> **Group CTO sign-off:** ✅ Signed — 2026-07-15 | Coo-Cah Technologies Holdings
> **PMO sign-off:** ⏳ Pending

Reference: [Post-Gate 4 DT Execution Strategy](./post-gate-4-dt-execution.md)

---

## Decision Rule

- **GO:** All sections above are fully green.
- **NO-GO:** Any unresolved item blocks expansion beyond the current 5 baseline repos.
