# Cross-Factory Simulation Specification

> **Status:** Canonical Standard (Gate 2)  
> **Owner:** Simulation & Optimisation Team + Digital Twin Engineering  
> **Version:** 1.0.0

---

## 1) Purpose and Scope

This specification defines the contract for simulation interactions between factory digital twins to support planning, bottleneck analysis, energy optimization, and dependency-aware scheduling.

---

## 2) Interaction Contract

Cross-factory simulation participants exchange scenario data through:

1. **Synchronous APIs** for scenario registration and result retrieval.
2. **Asynchronous MQTT streams** for simulation events and intermediate states.

### Contract Components

| Component | Requirement |
|---|---|
| Participant identity | Must use canonical `factory_id` and `asset_id` |
| Scenario identity | `scenario_id` must be globally unique UUID |
| Correlation | `correlation_id` required across all events/results for traceability |
| Versioning | `spec_version` required in all requests and responses |
| Idempotency | Duplicate submissions by same `scenario_id` must be safely handled |

---

## 3) Exchange Cadence and Timing

| Exchange Type | Cadence | SLA |
|---|---|---|
| Baseline state snapshot | Every 15 minutes | Available to federation within 2 minutes |
| Simulation trigger events | Real-time (event driven) | Delivered within 30 seconds |
| Intermediate progress events | Every 60 seconds during run | Best effort with sequence continuity |
| Final scenario outputs | At scenario completion | Published within 60 seconds |

All timestamps must be UTC and include monotonic sequence numbers for ordering.

---

## 4) Scenario Types

| Scenario Type | Description | Typical Producers | Typical Consumers |
|---|---|---|---|
| `THROUGHPUT_DEPENDENCY` | Tests impact of upstream/downstream production dependencies | MES optimizer | Neighbor factories, group planning |
| `ENERGY_BALANCING` | Models multi-factory load shifting and dispatch options | EMS/AI optimizer | Energy operations |
| `MAINTENANCE_PROPAGATION` | Simulates cross-factory effects of planned/unplanned downtime | Maintenance planner | Supply chain + planning |
| `QUALITY_FEEDBACK` | Simulates quality drift impact on downstream processes | Quality analytics | Upstream process owners |
| `LOGISTICS_CONSTRAINT` | Simulates inter-factory transport and inventory constraints | Supply chain planning | Production scheduling |

---

## 5) Inputs, Outputs, and Assumptions

### Required Inputs

- `scenario_id`, `scenario_type`, `factory_scope`
- Start/end horizon (`ts_start_utc`, `ts_end_utc`)
- Relevant asset states and constraints
- Demand, capacity, and inventory assumptions
- Model version references

### Required Outputs

- Predicted KPI deltas (throughput, OEE, energy, service level)
- Constraint violations and bottleneck locations
- Confidence score
- Recommended mitigation actions
- Full assumptions echo for auditability

### Assumptions

1. Input data quality has passed validation gates in DT and AI pipelines.
2. Factory clocks are synchronized to UTC.
3. Canonical IDs, topics, and data model standards are enforced.

---

## 6) Success Criteria and Acceptance

A simulation integration is accepted when:

1. End-to-end scenario exchange succeeds for all mandatory scenario types.
2. Contract conformance tests pass (identity, schema, timing, ordering, idempotency).
3. KPI outputs can be reconciled against known historical reference windows.
4. Operational users (planning, energy, maintenance) sign off on interpretability.

---

## 7) Error Handling and Replay

- Invalid requests return structured validation errors with field-level reasons.
- Failed asynchronous steps publish to dead-letter topics per `mqtt-topic-schema.md`.
- Replay must be supported using stored `scenario_id` + `correlation_id`.

---

## 8) Compliance and Governance

- Factories must certify simulation adapter conformance before joining federation.
- Any breaking contract change requires MAJOR version bump and approved migration plan.
- Quarterly contract compatibility review is mandatory for all active factories.

