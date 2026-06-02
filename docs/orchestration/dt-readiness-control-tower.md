# DT Readiness Control Tower

> **Project Coo-Cah | Orchestration**
> **Document Version:** 1.0 | **Owner:** Group CTO / DT Engineering Lead / PMO
> **Update Frequency:** Weekly during active rollout waves
> **Purpose:** Central operating model for closing DT readiness gaps across the factory portfolio from the master repository.

---

## Objective

Use **Coo-Kah-Doks** as the single control tower for Digital Twin readiness while executing factory-specific detail through guided per-factory agent runs and central QA gates.

This playbook applies to the current portfolio of **17 factory blueprints plus the master template**. The master template is not counted as a factory in programme totals; it is the control-tower standard source.

---

## 1) Operating Model

| Layer | Role | Owned in Master Repo? | Factory-Specific? |
|---|---|---|---|
| Standards | Canonical DT schema, scorecard, prompt pack, acceptance rules | Yes | No |
| Validation | Gate 3 file checks, docs build, central review checklist | Yes | No |
| Dashboard | Cross-factory readiness %, blockers, next 2-week deliverables | Yes | No |
| Factory execution | Asset lists, sensor mappings, zone anchors, use cases, owners, local gaps | No | Yes |
| Replication | Proven deltas promoted back into template after review | Yes | Sometimes |

### Decision rule

- **Master repo = control tower**
- **Factory docs = execution surface**
- **Agents = acceleration mechanism, not source of policy**

Do not let factories invent their own DT structure. They may only fill in **local deltas** against the central standard.

---

## 2) DT Readiness Scorecard (Group Standard)

Use one scorecard for every factory. Scores are used for prioritisation, not as a substitute for hard release gates.

| Dimension | Weight | Minimum evidence | Score guidance |
|---|---:|---|---|
| Documentation foundation | 25 | `digital-twin.md`, `docs/sensor-map.md`, `docs/bim/README.md`, `docs/bim/zone-boundaries.md`, `docs/bim/asset-anchors.md` | 0 = missing core files; 15 = files exist but weakly linked; 25 = complete and linked |
| Asset + spatial coverage | 20 | Asset registry, zone definitions, anchor references, mounted-on asset IDs, calibration fields | 0 = placeholder only; 10 = schema established; 20 = coverage mapped for critical assets |
| Integration design readiness | 20 | `mes-integration.md`, platform-standard references, protocol map, connector ownership | 0 = absent; 10 = documented; 20 = documented with factory-specific interfaces and stub plan |
| Governance + ownership | 15 | Named owners/reviewers, gap log, due dates, review cadence | 0 = no accountable owners; 8 = owners named; 15 = owners + dated closure plan |
| Simulation readiness | 10 | At least 3 factory-relevant DT use cases with KPI linkage | 0 = absent; 5 = listed; 10 = tied to KPIs and evidence plan |
| Execution evidence | 10 | Implementation plan, gap-closure pack, AI/pentest/supporting evidence | 0 = absent; 5 = partial execution pack; 10 = pack complete |

**Total:** 100

### Hard release rule

No factory is marked **DT-ready** unless all three conditions below are green:

1. All mandatory artifacts are complete and validated
2. Live data connectivity is proven for the factory's critical assets
3. At least **3 DT simulations** have run with reproducible evidence lineage

Score alone never overrides this rule.

---

## 3) Current Seed Scoring Method

Until live telemetry evidence exists, the dashboard score is seeded only from **observable repository evidence**:

- Required Gate 3 artifact presence and linkage
- DT, MES, machinery, floor-plan, and supply-chain documentation
- Factory-level execution artifacts already committed
- Pilot or benchmark designation recorded in orchestration docs

This means current scores represent **documentation and execution readiness**, not live-operational readiness.

---

## 4) Rollout Waves

These are **DT readiness authoring waves** from the master repo. They do not override the separate production rollout gates in the pilot execution strategy.

| Wave | Scope | Goal | Entry rule |
|---|---|---|---|
| Wave 0 | Master template + Personal Electronics pilot | Freeze standards, scorecard, prompt pack, review controls | Control-tower docs approved |
| Wave 1 | All electronics factories | Reuse the strongest DT patterns first | Pilot package and prompt pack frozen |
| Wave 2 | Chemicals factories | Extend into process-industry instrumentation and spatial models | Wave 1 review lessons promoted to template |
| Wave 3 | Consumer goods + Lifestyle factories | Complete portfolio coverage using matured template | Wave 2 pattern set accepted |

### Pilot and contrast benchmark

| Role | Factory | Why |
|---|---|---|
| Primary DT pilot | Personal Electronics | Most mature DT evidence set and execution pack in the portfolio |
| Non-electronics contrast benchmark | Plastics & Polymers | Upstream strategic factory with dedicated repo path and strong cross-factory reuse value |

---

## 5) Factory DT Prompt Pack (Reusable)

Use this prompt template when handing work to an agent for a specific factory:

```text
You are preparing Digital Twin readiness content for [FACTORY NAME] in the Coo-Kah-Doks master blueprint.

Use the master standards from:
- /tmp/workspace/oumar-code/Coo-Kah-Doks/docs/orchestration/dt-readiness-control-tower.md
- /tmp/workspace/oumar-code/Coo-Kah-Doks/docs/orchestration/post-gate-4-dt-execution.md
- /tmp/workspace/oumar-code/Coo-Kah-Doks/docs/orchestration/dt-pilot-standards-and-templates.md
- /tmp/workspace/oumar-code/Coo-Kah-Doks/platform/digital-twin-platform-architecture.md
- /tmp/workspace/oumar-code/Coo-Kah-Doks/factories/_template/digital-twin.md

Factory source files:
- /tmp/workspace/oumar-code/Coo-Kah-Doks/factories/[VERTICAL]/[FACTORY]/README.md
- /tmp/workspace/oumar-code/Coo-Kah-Doks/factories/[VERTICAL]/[FACTORY]/machinery.md
- /tmp/workspace/oumar-code/Coo-Kah-Doks/factories/[VERTICAL]/[FACTORY]/floor-plan.md
- /tmp/workspace/oumar-code/Coo-Kah-Doks/factories/[VERTICAL]/[FACTORY]/mes-integration.md
- /tmp/workspace/oumar-code/Coo-Kah-Doks/factories/[VERTICAL]/[FACTORY]/digital-twin.md
- /tmp/workspace/oumar-code/Coo-Kah-Doks/factories/[VERTICAL]/[FACTORY]/docs/sensor-map.md
- /tmp/workspace/oumar-code/Coo-Kah-Doks/factories/[VERTICAL]/[FACTORY]/docs/bim/zone-boundaries.md
- /tmp/workspace/oumar-code/Coo-Kah-Doks/factories/[VERTICAL]/[FACTORY]/docs/bim/asset-anchors.md

Do not invent new standards. Fill only factory-specific deltas.

Required outputs:
1. DT readiness score using the group scorecard
2. Gap list grouped into:
   - Documentation
   - Data integration
   - Instrumentation
   - Simulation use-cases
   - Ownership/governance
3. Named owner per gap
4. Due date per gap
5. Next 2-week deliverables
6. Template improvements that should be promoted back to master

Completion rule:
- Do not mark the factory DT-ready unless mandatory artifacts are complete, live data connectivity is proven, and 3 simulations have reproducible evidence.
```

### Mandatory agent output shape

| Output | Requirement |
|---|---|
| Readiness score | Must use the group weights exactly |
| Gap list | Must be grouped into the 5 triage buckets |
| Evidence references | Must link back to factory files |
| Next actions | Must be limited to the next 2 weeks |
| Template deltas | Must distinguish reusable improvements from local-only details |

---

## 6) Central Review Before Merge

Every factory submission must pass central review in the master repo before it is accepted.

| Review gate | Requirement |
|---|---|
| Standards conformance | No schema drift from platform or template standards |
| Gate 3 docs validation | Required sensor-map and BIM files pass CI checks |
| Docs build | `mkdocs build --strict` passes |
| Scorecard review | Score justified by linked evidence |
| Triage completeness | All open gaps classified with owner and due date |
| Promotion review | Any reusable pattern either promoted to template or explicitly rejected |

---

## 7) Triage Model for Gap Closure

Use one triage board across the portfolio.

| Bucket | Typical issues | Default owner |
|---|---|---|
| Documentation | Missing or weak DT docs, broken cross-links, missing evidence refs | DT Programme Office |
| Data integration | Missing protocol map, connector ownership, API/event schema gaps | MES Product Owner / OT-IT Integration Lead |
| Instrumentation | Missing sensors, weak asset anchors, unassigned mounted-on asset IDs, calibration gaps | Factory Engineering / OT Instrumentation Lead |
| Simulation use-cases | No KPI-linked scenarios, no evidence plan, no experiment design | DT Engineering Lead |
| Ownership/governance | No named owners, no due dates, no review cadence, no sign-off path | PMO / Factory Leadership |

### Triage SLA

- Red gaps: owner assigned within **2 business days**
- Amber gaps: closure plan within **5 business days**
- Green gaps: monitor only, no special escalation

---

## 8) Dashboard Operating Rules

The cross-factory dashboard lives in the master repo and is updated centrally.

### Dashboard minimum columns

1. Factory
2. Wave
3. DT readiness %
4. Current blocker
5. Next 2-week deliverable
6. Review owner

### Update cadence

- Weekly during active waves
- Monthly for executive reporting

---

## 9) Immediate Execution Sequence

| Order | Action |
|---|---|
| 1 | Freeze this control-tower standard in master |
| 2 | Keep Personal Electronics as the proving ground |
| 3 | Run Wave 1 prompts across electronics factories |
| 4 | Review centrally and promote reusable deltas back to template |
| 5 | Launch Plastics as the non-electronics contrast benchmark |
| 6 | Move to Chemicals wave after Wave 1 patterns are stable |
| 7 | Finish Consumer Goods and Lifestyle only after the template has matured |

---

## Revision History

| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | 2026-06-02 | Group CTO / DT Engineering Lead / PMO | Introduced central DT readiness control-tower model, scorecard, prompt pack, wave strategy, triage model, and hard completion rule |
