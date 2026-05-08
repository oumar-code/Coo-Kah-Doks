# DT Value & Funding Demand Brief (Investor-Facing)

> **Project Coo-Cah | Orchestration**
> **Document Version:** 1.0 | **Owner:** Group CTO / DT Engineering Lead / PMO / Finance
> **Primary Audience:** Investors and investment committee reviewers
> **Scope:** Personal Electronics (Sagamu) pilot only

---

## Objective

Provide one auditable investor narrative that demonstrates Digital Twin value achieved so far and translates pilot simulation evidence into a clear funding demand for physical-factory execution.

---

## 1) Investor Narrative Backbone (Locked)

Every investor interaction must follow this sequence:

1. **Baseline lock:** Day 0–30 baseline KPI definitions and data-quality status
2. **Simulation scenarios:** Throughput, quality, downtime, and energy model outputs
3. **Measured outcomes:** Pilot intervention deltas and confidence posture
4. **Funding demand:** Physical capex asks linked to modeled constraints and KPI/financial impact

No alternate storyline may be used without Group CTO + PMO approval.

---

## 2) What Has Been Achieved So Far (Proof Inventory)

Minimum proof inventory to disclose:

| Domain | Evidence Type | Required Artifact |
|---|---|---|
| Data ingestion | Critical asset telemetry live and validated | Ingestion health report + schema validation log |
| Twin model coverage | Pilot-critical assets represented in DT | Asset coverage matrix + model registry snapshot |
| Simulation readiness | Priority scenarios executable with traceable inputs | Scenario runbook + output lineage report |
| Governance controls | KPI formulas and approval controls frozen | Signed KPI dictionary + governance checklist |
| Security and resilience | Required auth/TLS and edge continuity controls validated | Security baseline report + outage/recovery test record |

---

## 3) What the Twin Can Simulate Today

Investor-facing scenario pack must include at least one auditable scenario per domain:

| Domain | Example Decision Question | Required Output |
|---|---|---|
| Throughput | Which station is the next binding bottleneck at target mix? | Bottleneck ranking + projected OEE impact |
| Quality | Which upstream conditions drive defect escape and rework? | FPY/DPPM sensitivity output + control recommendations |
| Downtime | Which failure modes are highest value to pre-empt? | Downtime risk profile + preventive timing recommendation |
| Energy | What dispatch/load strategy minimizes energy intensity and cost? | kWh/unit and cost delta by scenario |

All outputs must be reproducible from recorded model version, input snapshot, and run metadata.

---

## 4) Constraints Remaining for Physical Execution

The brief must explicitly list unresolved constraints and implications:

- Physical infrastructure dependencies
- Equipment/procurement gaps
- Integration and commissioning dependencies
- Workforce and operating-readiness constraints
- Regulatory and compliance dependencies

Each constraint must state owner, target closure date, and risk if unfunded/unresolved.

---

## 5) Funding Ask Map (Capex Translation)

Each funding ask must follow the structure below:

| Ask ID | Capex Item | Modeled Bottleneck/Risk | KPI Lift Expectation | Payback Logic | Dependency Notes |
|---|---|---|---|---|---|
| FA-01 | _Define item_ | _Twin evidence reference_ | _Expected OEE/FPY/etc. lift_ | _Benefit-cost logic_ | _Prerequisites and assumptions_ |

Rules:

1. No capex ask without modeled evidence linkage
2. No KPI-lift claim without formula and baseline reference
3. No payback claim without PMO/Finance-reviewed assumptions

---

## 6) Investor Demo Cycle & Audit Controls

### Weekly internal rehearsal (mandatory)

- Rehearse approved investor script
- Validate metric consistency versus source artifacts
- Pre-clear questions on assumptions and boundary conditions

### Investor sessions

- Present only approved scenario pack and KPI set
- Capture Q&A deltas and evidence follow-up actions
- Log any proposed claim changes under change control

### Audit requirement

Any statement made during investor sessions must be traceable to source lineage in the pilot evidence pack.

---

## 7) 2–4 Week Immediate Milestone

Deliverable for the immediate window:

- **Day 0–30 baseline lock completed**
- **Investor-facing DT Value & Funding Demand brief published (v1)**
- **Initial funding ask map reviewed by PMO and Finance**

This milestone is a prerequisite for scaling external funding conversations.

---

## References

- [Post-Gate 4 DT Execution & Evidence Strategy](./post-gate-4-dt-execution.md)
- [DT Pilot Standards and Templates](./dt-pilot-standards-and-templates.md)
- [Factory Status Registry](./factory-status-registry.md#digital-twin-pilot-factory-designation-gate-4-decision)

---

## Revision History

| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | 2026-05-08 | Group CTO / DT Engineering Lead / PMO / Finance | Initial investor-facing DT value and funding-demand brief |
