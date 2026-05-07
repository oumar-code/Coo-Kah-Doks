# Gate 1 → 2 Readiness Program

> **Project Coo-Cah | Orchestration**
> **Document Version:** 1.0 | **Owner:** Group Operations & Programme Management  
> **Update Frequency:** Weekly (Ops), Monthly (Executive)

---

## Objective

Operationalize Gate 1 → 2 progression with one accountable tracker, one review cadence, and one auditable evidence model aligned with the official Phase Gate criteria in [Automation Phases](../06-automation-phases/index.md).

---

## 1) Gate Tracker — Scope, Owners, and Cadence

### Gate KPI Tracker (single source of truth)

| Criterion | Threshold | Accountable Owner | System of Record | Weekly Ops Review | Monthly Executive Review |
|---|---|---|---|---|---|
| OEE | ≥ 65% | Factory Operations Lead | MES OEE dashboards | ✅ | ✅ |
| FPY | ≥ 93% | Factory Quality Lead | QMS + MES quality records | ✅ | ✅ |
| MES data completeness | ≥ 90% | MES Product Owner | MES event/order logs | ✅ | ✅ |
| IoT sensor coverage | ≥ 85% of assets | OT/IoT Lead | IoT asset registry + telemetry | ✅ | ✅ |
| Digital twin baseline | 100% of critical assets modelled | Digital Twin Lead | Twin asset graph + model register | ✅ | ✅ |
| AI training data quality | ≥ 80% | AI Data Lead (Rwanda AI Team) | Data quality scorecards | ✅ | ✅ |
| Renewable energy share | ≥ 35% | Energy & Utilities Lead | EMS meter and dispatch reports | ✅ | ✅ |
| Safety | Zero LTI (3-month window) | EHS Lead | EHS incident system | ✅ | ✅ |
| Financial readiness | Cash-flow positive or on plan | Finance Business Partner | Factory P&L + approved plan | ✅ | ✅ |

### Review cadence

- **Weekly Ops Review (factory + PMO):** KPI movement, blockers, corrective actions, owner commitments.
- **Monthly Executive Review (Holdings):** Gate heatmap, evidence completeness, go/no-go risk posture.

---

## 2) Phase 1 Stabilization and Factory Transition Milestones

Gate readiness starts only after Phase 1 core systems are stable (MES, IoT, digital twin baseline, EMS/QMS live).

### Status transition path

`PLANNED` → `UNDER_CONSTRUCTION` → `COMMISSIONING` → `PHASE_1_ACTIVE`

### Initial transition cohort (programme priority)

| Factory | Current Baseline (from registry) | Next Target Milestone | Exit Criterion for Milestone |
|---|---|---|---|
| Kitchen Electronics | `PLANNED` | `UNDER_CONSTRUCTION` | Civil/utilities mobilized; commissioning plan approved |
| Garage/Power Electronics (single factory) | `PLANNED` | `UNDER_CONSTRUCTION` | Core process equipment procurement + site mobilization complete |
| Personal Electronics | `PLANNED` | `UNDER_CONSTRUCTION` | SMT and assembly installation readiness signed off |
| Plastics & Polymers | `PLANNED` | `UNDER_CONSTRUCTION` | Tier-1 dependency plan approved for downstream factories |

> Keep [Factory Status Registry](./factory-status-registry.md) as the authoritative status log and update monthly.

---

## 3) Gate Criterion Closure Workstreams

| Criterion | Closure Focus | Minimum Control Requirement |
|---|---|---|
| OEE | Eliminate top downtime losses | Shift-level loss tree and weekly top-3 cause closure |
| FPY | Defect prevention and containment | In-process control plan + incoming quality enforcement |
| MES completeness | Event and order record integrity | Mandatory event capture + exception reconciliation log |
| IoT coverage | Critical asset-first instrumentation | Asset criticality register and coverage audit trail |
| Digital twin baseline | Complete critical asset modeling | Twin model acceptance checklist per critical asset |
| AI data quality | Training data validity and labeling | Data quality rules + QA sign-off workflow |
| Renewable share | Energy-mix execution | Metered monthly energy mix evidence |
| Safety | LTI prevention and corrective action closure | Audit schedule + corrective action closure SLA |
| Financial | Ramp/yield/cost discipline | Monthly P&L variance and plan reconciliation |

---

## 4) 3-Month Evidence Window (Auditable by Design)

A criterion is considered met only when evidence is complete and approved for each month across a **consecutive 3-month** window.

### Evidence pack structure (per month)

| KPI | Artifact(s) | Source System | Approver |
|---|---|---|---|
| OEE / FPY | KPI extracts + downtime/defect Pareto | MES/QMS | Factory Ops Lead + Quality Lead |
| MES completeness | Completeness report + exception closure log | MES | MES Product Owner |
| IoT / Twin baseline | Coverage report + critical asset model completion log | IoT platform / Twin platform | OT/IoT Lead + Twin Lead |
| AI data quality | DQ scorecard + labeling QA report | AI data platform | AI Data Lead |
| Renewables | Energy mix report + meter reconciliation | EMS | Energy Lead |
| Safety | Incident register + audit closure summary | EHS system | EHS Lead |
| Financial | Cash-flow/P&L report vs plan | Finance system | Finance BP |

### Evidence acceptance rule

- No KPI may be marked “met” without artifact links, approver name, and approval date.
- Any red/amber KPI resets the monthly evidence cycle for that KPI.

---

## 5) Pre-Gate Readiness Reviews

Run mock gate reviews **4–6 weeks before** official submission.

### Mock review outputs

- Consolidated KPI heatmap (Green/Amber/Red)
- Open-risk log with owner and due date
- Decision to start or delay the official 3-month evidence window

### Entry rule for official window

- No unresolved red KPI
- Amber KPIs have approved, time-bound mitigation plans

---

## 6) Formal Gate Approval Execution

### Submission package

- Consolidated 3-month evidence pack
- Gate decision memo (criteria-by-criteria disposition)
- Residual risk and mitigation summary

### Approval requirement

- **Holdings Board sign-off**
- **Group CTO sign-off**

A factory is eligible for Phase 2 only after both approvals are complete and recorded.
