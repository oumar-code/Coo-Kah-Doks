# DT Pilot Standards and Templates

> **Project Coo-Cah | Orchestration**
> **Document Version:** 1.0 | **Owner:** Group CTO / DT Engineering Lead / PMO
> **Purpose:** Standardized templates for proving DT value with auditable evidence and controlled Tier 1 rollout.

---

## 1) Pilot Charter Template (Required Before Intervention)

| Field | Required Content |
|---|---|
| Pilot factory | Name, location, production slice in scope |
| Pilot owner | Named accountable lead and deputies |
| Scope boundary | Included and excluded lines/assets/processes |
| Locked value hypotheses | 3–5 outcomes with measurable business claims |
| KPI formulas | Exact formulas and data sources |
| Baseline window | Dates, shifts, and control assumptions |
| Confidence threshold | Statistical confidence requirement |
| Minimum effect size | Threshold for practical business value |
| Risk controls | Safety, quality, and operational guardrails |
| Sign-off | Group CTO, Factory Leadership, PMO, Data/AI Lead |

---

## 2) Experiment Design Template (Controlled Proof)

| Field | Required Content |
|---|---|
| Design type | Pre/post + matched-control |
| Unit of analysis | Shift, line, batch, SKU, or station |
| Observation windows | Baseline and intervention windows |
| Confounder controls | Product mix, staffing, downtime classes, maintenance events |
| Data quality gates | Completeness, freshness, schema validity thresholds |
| Intervention log | Timestamped list of DT actions/rules/model versions |
| Statistical method | Test family, assumptions, and exception handling |
| Reproducibility package | Query references, scripts/notebooks, output hashes |

---

## 3) KPI Dictionary Template (Group Standard)

| KPI | Formula | Numerator | Denominator | Frequency | Owner | Target | Minimum Proof Threshold |
|---|---|---|---|---|---|---|---|
| OEE | Availability × Performance × Quality | Per formula | Per formula | Daily | MES Product Owner | Factory target | Uplift vs. control with significance |
| FPY | Good units / total units | Good units | Total units | Batch/Shift | QA Lead | Factory target | Improvement vs. control |
| DPPM | Defects per million | Defect count | Units × 1,000,000 | Weekly | QA Lead | Factory target | Reduction vs. baseline |
| Energy intensity | kWh / unit | Energy kWh | Good units | Monthly | Energy Lead | Factory target | Reduction vs. control |
| MES completeness | Complete records / expected records | Complete records | Expected records | Daily | MES Lead | Factory target | Threshold met throughout pilot |

---

## 4) Governance Checklist Template

- [ ] Pilot charter approved and frozen before intervention
- [ ] KPI formulas and thresholds versioned and change-controlled
- [ ] Asset IDs and telemetry mappings conform to platform standards
- [ ] Event logs are immutable and timestamped
- [ ] Simulation/model runs are versioned with input/output lineage
- [ ] Evidence artifacts are traceable from raw telemetry to executive claim
- [ ] Weekly review cadence completed with decisions recorded
- [ ] Independent audit reviewer assigned before Day 61

---

## 5) Go/No-Go Gate Checklist Template (Tier 1 Release)

- [ ] Data quality and completeness thresholds met
- [ ] Statistically valid KPI improvements vs. baseline and matched-control
- [ ] No hidden manual rework burden or critical operational regressions
- [ ] Financial ROI threshold met and signed by Finance
- [ ] Full evidence pack reproducible by independent reviewer
- [ ] Group CTO + PMO sign-off complete

If any item is not green, Tier 1 release remains blocked.

---

## 6) Evidence Pack Minimum Contents

1. Pilot charter and approved scope
2. Baseline report and control matching rationale
3. Intervention log and model/rule version register
4. Data quality scorecards and schema validation reports
5. Statistical analysis outputs with assumptions and caveats
6. Operational sustainability assessment
7. Financial translation and ROI validation
8. Independent reproducibility report
9. Final go/no-go decision memo

---

## Revision History

| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | 2026-05-07 | Group CTO / DT Engineering Lead / PMO | Initial standards and templates for DT pilot proof and rollout gates |

