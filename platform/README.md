# Cross-Factory Infrastructure Standards (Gate 2)

> **Status:** IN REVIEW (Gate 2 closure pending approvals)  
> **Scope:** Group-wide canonical standards for federated digital twins across all Coo-Cah factories  
> **Owner:** Group CTO / Digital Twin Engineering Team  
> **Review Cadence:** Monthly (engineering), quarterly (executive architecture council)

---

## 1) Gate 2 Re-baseline

Gate 2 is treated as a **documentation standardization gate**. Existing architecture decisions in ADRs remain valid; this package provides the canonical operational standards needed for cross-factory implementation.

### Required Artifacts Status

| Requirement | Canonical Artifact | Status |
|---|---|---|
| DT platform architecture | [`/platform/digital-twin-platform-architecture.md`](./digital-twin-platform-architecture.md) | ✅ Exists |
| Asset ID naming convention | [`/platform/asset-id-naming-convention.md`](./asset-id-naming-convention.md) | ✅ Added |
| MQTT topic schema | [`/platform/mqtt-topic-schema.md`](./mqtt-topic-schema.md) | ✅ Added |
| DT data model | [`/platform/digital-twin-data-model.md`](./digital-twin-data-model.md) | ✅ Added |
| Cross-factory simulation spec | [`/platform/cross-factory-simulation-spec.md`](./cross-factory-simulation-spec.md) | ✅ Added |

### Definition of Done (Gate 2)

Gate 2 is complete only when:
1. All five required canonical artifacts exist at the required paths.
2. Cross-links are consistent and normative dependencies are explicit.
3. Owners and approvers have signed off.
4. Factory compliance obligations and rollout checkpoints are published.
5. Gate 2 checklist below is fully marked complete.

---

## 2) Document Purpose and Scope

| Document | Purpose |
|---|---|
| `digital-twin-platform-architecture.md` | Canonical federation architecture and deployment model |
| `asset-id-naming-convention.md` | Group-wide unique asset identity namespace and lifecycle rules |
| `mqtt-topic-schema.md` | Unified MQTT hierarchy, payload envelope, QoS/retain, and compatibility policy |
| `digital-twin-data-model.md` | Shared asset/telemetry/event schemas across factories |
| `cross-factory-simulation-spec.md` | Inter-factory simulation interaction contract |

---

## 3) Ownership and Approval Matrix

| Artifact | Primary Owner | Required Approvers |
|---|---|---|
| DT platform architecture | Digital Twin Engineering Lead | Group CTO, AI Platform Architect, Smart Factory Core Lead |
| Asset ID naming convention | Enterprise Data Architect | Digital Twin Engineering Lead, OT/IoT Lead |
| MQTT topic schema | OT/IoT Platform Lead | Digital Twin Engineering Lead, AI Platform Architect, Cybersecurity Lead |
| DT data model | Enterprise Data Architect | Digital Twin Engineering Lead, AI Data Lead |
| Cross-factory simulation spec | Simulation & Optimisation Lead | Group CTO, Smart Factory Core Lead, AI Platform Architect |

---

## 4) Gate 2 Traceability Matrix

| Gate 2 Requirement | Canonical Section(s) |
|---|---|
| DT platform architecture | [`digital-twin-platform-architecture.md#1-platform-decision`](./digital-twin-platform-architecture.md#1-platform-decision), [`#4-gate-2-normative-dependencies`](./digital-twin-platform-architecture.md#4-gate-2-normative-dependencies) |
| Asset ID naming convention | [`asset-id-naming-convention.md#2-canonical-asset-id-format`](./asset-id-naming-convention.md#2-canonical-asset-id-format), [`#4-uniqueness-and-lifecycle-rules`](./asset-id-naming-convention.md#4-uniqueness-and-lifecycle-rules) |
| MQTT topic schema | [`mqtt-topic-schema.md#2-canonical-topic-hierarchy`](./mqtt-topic-schema.md#2-canonical-topic-hierarchy), [`#4-qos-and-retain-policy`](./mqtt-topic-schema.md#4-qos-and-retain-policy), [`#6-backward-compatibility-and-versioning-policy`](./mqtt-topic-schema.md#6-backward-compatibility-and-versioning-policy) |
| DT data model | [`digital-twin-data-model.md#2-common-asset-classes`](./digital-twin-data-model.md#2-common-asset-classes), [`#4-telemetry-schema`](./digital-twin-data-model.md#4-telemetry-schema), [`#6-validation-rules`](./digital-twin-data-model.md#6-validation-rules) |
| Cross-factory simulation spec | [`cross-factory-simulation-spec.md#2-interaction-contract`](./cross-factory-simulation-spec.md#2-interaction-contract), [`#3-exchange-cadence-and-timing`](./cross-factory-simulation-spec.md#3-exchange-cadence-and-timing), [`#6-success-criteria-and-acceptance`](./cross-factory-simulation-spec.md#6-success-criteria-and-acceptance) |

---

## 5) Factory Compliance Obligations

Each factory repository must align its local implementation (`docs/digital-twin.md`, telemetry integrations, event contracts, and simulation assumptions) to these platform standards.

### Mandatory Alignment Items

1. Use only the canonical asset IDs from `asset-id-naming-convention.md`.
2. Publish MQTT telemetry and events using `mqtt-topic-schema.md`.
3. Emit DT payloads conforming to `digital-twin-data-model.md`.
4. Follow `cross-factory-simulation-spec.md` for shared simulation exchanges.
5. Keep factory-specific extensions additive and backward-compatible.

---

## 6) Rollout Checkpoints

| Milestone | Coverage Requirement |
|---|---|
| Pilot factory checkpoint | 100% of critical assets in pilot use canonical asset IDs and topic/schema contracts |
| Tier-1 fleet checkpoint | Power Electronics, Plastics, and Metallurgical factories publish conformant telemetry/events |
| Full fleet checkpoint | All factories conform; no legacy non-canonical identifiers/topics in production |

---

## 7) Change Control Policy

- **Versioning:** Semantic versioning for each standard (`MAJOR.MINOR.PATCH`).
- **Breaking change rule:** MAJOR bump required for incompatible schema/topic/ID changes.
- **Deprecation window:** Minimum 2 release cycles (or 6 months, whichever is longer) before removing deprecated fields/topics.
- **Compatibility commitment:** Existing factory integrations must continue functioning throughout deprecation periods.
- **Approval gate:** No MAJOR release without Group CTO + designated domain approvers.

---

## 8) Gate 2 Closure Evidence Checklist

- [x] `platform/digital-twin-platform-architecture.md` exists and is canonical.
- [x] `platform/asset-id-naming-convention.md` exists.
- [x] `platform/mqtt-topic-schema.md` exists.
- [x] `platform/digital-twin-data-model.md` exists.
- [x] `platform/cross-factory-simulation-spec.md` exists.
- [x] Canonical entrypoint `platform/README.md` exists.
- [x] Requirement-to-section traceability matrix completed.
- [x] Ownership and approval matrix defined.
- [x] Factory compliance obligations and rollout checkpoints documented.
- [x] Change control policy documented.
- [ ] Reviewer sign-off complete.
- [ ] Group CTO final approval recorded.

> Gate 2 should be marked complete only when all checklist items are checked.

---

## 9) Gate 4 Artifacts in This Directory

The following `platform/` files are required Gate 4 canonical artifacts:

| Gate 4 Decision | Canonical Artifact |
|----------------|--------------------|
| Cloud vs. on-prem / DT stack decision | [`platform/digital-twin-platform-architecture.md`](./digital-twin-platform-architecture.md) |
| Group data governance policy (ownership / retention / access) | [`platform/data-governance-policy.md`](./data-governance-policy.md) |

Gate 4 evidence checklist and closure record: [`docs/orchestration/gate-4-decisions.md`](../docs/orchestration/gate-4-decisions.md)
