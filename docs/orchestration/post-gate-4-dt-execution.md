# Post-Gate 4 DT Execution & Evidence Strategy

> **Project Coo-Cah | Orchestration**
> **Document Version:** 1.0 | **Owner:** Group CTO / Digital Twin Engineering Lead
> **Update Frequency:** Weekly (Execution), Monthly (Executive)
> **Trigger:** Activated once Gate 4 is closed.

---

## Objective

Convert Gate 4 closure into disciplined execution by delivering an **Investor-Ready Digital Twin Proof** at one pilot factory, translating DT evidence into a clear physical-factory funding demand, and releasing Tier 1 rollout only on auditable evidence.

---

## 1) Governance Lock and Operating Cadence

### Cadence

| Forum | Frequency | Required Attendees | Primary Outputs |
|---|---|---|---|
| DT/MES/OT Execution Review | Weekly | DT Lead, MES Product Owner, OT/IoT Lead, Factory CTO, PMO | Blocker log, milestone status, corrective actions |
| Executive Gate Review | Monthly | Group CTO, PMO, Factory Leadership, AI Data Lead | Go/no-go posture, risk status, evidence completeness |

### Gate 4 immutability rule

- Gate 4 decisions remain immutable after closure.
- Any change requires formal CTO-approved change control, canonical artifact update, and update of the Gate 4 evidence checklist.
- No factory-level implementation may proceed on unofficial architecture/vendor deviations.

References:
- [Gate 4 Decisions & Evidence](./gate-4-decisions.md)
- `platform/digital-twin-platform-architecture.md`

---

## 2) Pilot First: Personal Electronics (Sagamu)

The Personal Electronics factory is the single DT proving ground before wider rollout.

### Why this pilot starts first

| Factor | Justification |
|---|---|
| Phase 1 priority site | Earliest practical window to prove value before fleet replication |
| DT maturity | Most complete DT definition (asset registry, simulation use cases, maturity roadmap, governance/audit trail) |
| Instrumentation and KPI readiness | Dense telemetry and clear KPI targets (OEE, FPY, DPPM, energy intensity, MES completeness) |
| Cross-factory relevance | PCB and electronics learnings transfer directly to Kitchen, Security, and broader electronics cluster |

### Locked value hypotheses (pre-build)

| Domain | Hypothesis | Minimum Pilot Proof Threshold |
|---|---|---|
| Throughput/OEE | DT-guided scheduling and bottleneck controls improve line performance | Statistically valid OEE uplift vs. baseline/control |
| Quality/FPY | DT-driven predictive controls reduce defect escape and rework | Statistically valid FPY gain and DPPM reduction vs. baseline/control |
| Reliability | DT predictive maintenance reduces unplanned downtime | Measurable downtime reduction with significance threshold met |
| Energy | DT load and dispatch optimisation lowers kWh per unit | Statistically valid reduction in energy intensity |

All hypotheses must define locked formulas, baseline windows, confidence thresholds, and minimum effect size before intervention starts.

Reference:
- [Factory Status Registry — DT Pilot Designation](./factory-status-registry.md#digital-twin-pilot-factory-designation-gate-4-decision)

---

## 3) Investor-Ready DT Proof Track (Pre-Factory Funding)

The first external narrative is investor-facing and must be anchored to one pilot only: **Personal Electronics (Sagamu)**.

### Required investor narrative

All investor sessions must follow one auditable sequence:

1. **Baseline:** Current state and locked KPI baseline window.
2. **Simulation scenarios:** Throughput, quality, downtime, and energy simulations tied to pilot assets.
3. **Measured outcomes:** Quantified deltas and confidence statements from controlled pilot evidence.

### Required evidence pack (investor-facing)

The investor package must include:

- What has already been achieved (ingestion, model coverage, validated simulations, controls in place)
- What can be simulated today (production, quality, reliability, energy)
- What constraints remain before full physical execution (infrastructure, equipment, integration, commissioning dependencies)

### Funding ask map (mandatory)

Every capex demand must map to:

1. A modeled bottleneck/risk in the pilot twin
2. The KPI lift expected when the physical intervention is funded
3. The payback logic and dependency assumptions

### Investor demo cycle

- **Weekly internal rehearsal:** Dry-run the investor script and evidence lineage checks.
- **Investor sessions:** Use one approved script and metric pack, without ad hoc KPI redefinition.
- **Audit control:** Any investor claim must be reproducible from source evidence artifacts.

Reference:
- [DT Value & Funding Demand Brief](./dt-value-funding-demand-brief.md)

---

## 4) Phase 1 “Minimum Viable Twin” Outcomes

Phase 1 delivery is complete only when all three baseline outcomes are met:

1. **Reliable ingestion:** OPC-UA/MQTT ingestion stable for critical assets with validated event/telemetry integrity.
2. **Standards compliance:** Canonical asset IDs, MQTT schema, and DT data model implemented without unresolved schema violations.
3. **Operational resilience + security:** Edge operation continues during internet outage, secure cloud sync restored on reconnection, and required auth/TLS controls enforced.

Normative standards:
- `platform/asset-id-naming-convention.md`
- `platform/mqtt-topic-schema.md`
- `platform/digital-twin-data-model.md`
- `platform/digital-twin-platform-architecture.md`

---

## 5) Hard Pilot Exit Criteria (Go/No-Go)

Tier 1 rollout approval requires all criteria below to be met with auditable evidence:

| Criterion | Minimum Threshold | Evidence Artifact |
|---|---|---|
| Data quality | Data quality and completeness threshold met on pilot-critical streams | Data quality scorecard + defect closure log |
| Business value | Statistically valid KPI improvement vs. baseline and matched-control | Baseline/control vs. intervention impact report |
| Operational sustainability | No hidden manual rework burden and no critical operational regressions | Operations sustainability assessment + exception log |
| Financial value | ROI threshold approved by PMO and Finance met | Benefit/cost model + signed finance validation |
| Audit reproducibility | Independent reviewer can reproduce claims from source lineage | Signed evidence-pack reproducibility report |
| Governance compliance | Required approvals and control records complete | Go/no-go memo signed by Group CTO + PMO |

No partial approval: unresolved red criteria block Tier 1 release.

---

## 6) Tier 1 Replication Package (Built During Pilot)

To reduce rollout risk, produce a replication package during pilot execution:

- Standard deployment playbook (edge setup, connectors, sync, rollback)
- Connector templates (OPC-UA and MQTT mapping patterns)
- Security baseline (network segmentation, auth, key/cert rotation controls)
- Factory onboarding checklist (dependencies, acceptance sequence, evidence requirements)
- Operations runbook (incident response, support model, escalation path)
- Pilot charter template
- Experiment design template
- KPI dictionary template
- Governance checklist template
- Go/no-go gate checklist template

Tier 1 sequence:
- **Wave 1:** Security Electronics, Kitchen Electronics
- **Wave 2:** Remaining electronics factories and selected consumer-goods factories

Rollout rule: **inherit standards + local delta only**.

Reference:
- [DT Pilot Standards and Templates](./dt-pilot-standards-and-templates.md)

---

## 7) DT + MES as One Integrated Transformation

DT and MES execution must be jointly governed from day one.

### Integration priorities

- Shared event interoperability contract across MES, DT, and OT integrations.
- Shared KPI definitions for OEE, quality, energy, and downtime attribution.
- AI-readiness by design: DT outputs exposed in stable API/event forms usable by the central AI platform early in pilot lifecycle.

### Minimum control

- Any integration interface change must update both DT and MES interface/control documentation.
- KPI logic changes must be jointly approved by DT Lead and MES Product Owner before executive reporting.

---

## 8) 90-Day Execution Shape

| Window | Primary Focus | Required Outputs |
|---|---|---|
| Days 0–30 | Baseline capture and KPI contract lock | Baseline pack, locked KPI formulas/thresholds, data quality hardening plan, signed pilot charter, investor-facing DT Value & Funding Demand brief v1 |
| Days 31–60 | Controlled DT interventions | Intervention logs, weekly evidence reviews, standards draft v1 |
| Days 61–90 | Independent audit and release decision | Reproducible audit pack, formal gate decision, Tier 1 playbook freeze |

---

## Decision Rule

Progression from pilot to Tier 1 is evidence-based:

1. Pilot milestones complete.
2. Exit criteria all green.
3. Replication package complete and accepted by Wave 1 receiving factories.
4. Group CTO and PMO approve formal rollout memo.

Until all four conditions are met, Tier 1 rollout remains blocked.
No broader Tier 1 expansion claim is permitted before all hard exit criteria are green.

---

## Revision History

| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | 2026-05-07 | Group CTO / DT Engineering Lead | Initial post-Gate 4 execution and evidence strategy |
| 1.1 | 2026-05-07 | Group CTO / DT Engineering Lead | Updated pilot designation to Personal Electronics and added auditable evidence-based rollout gates |
| 1.2 | 2026-05-08 | Group CTO / DT Engineering Lead | Added investor-ready DT proof track, funding ask mapping, and investor demo cycle requirements |
