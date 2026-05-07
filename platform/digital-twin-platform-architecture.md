# Coo-Cah Digital Twin Platform Architecture (Gate 2 Canonical)

> **Gate 2 Canonical Standard — Cross-Factory Infrastructure**
> **Status:** ACTIVE STANDARD — Hybrid Coo-Cah DT Engine
> **ADR Reference:** [ADR-003 — Digital Twin Platform Selection](../docs/adrs/ADR-003-digital-twin-platform.md)
> **Decision Date:** 2025-03-05
> **Approved by:** Group CTO, Head of Digital Twin Team, Smart Factory Core Lead, AI Platform Architect
> **Document Version:** 1.1 | **Owner:** Group CTO / Digital Twin Engineering Team

---

## 1. Platform Decision

### 1.1 Question Answered

> *Cloud vs. on-premises edge DT stack — Azure Digital Twins? AWS IoT TwinMaker? Custom?*

**Answer: Coo-Cah Proprietary DT Engine (Hybrid Edge + Cloud) — not Azure, not AWS, not Siemens.**

The decision was evaluated against five options. See [ADR-003](../docs/adrs/ADR-003-digital-twin-platform.md) for the full rationale. Summary:

| Option | Verdict | Reason |
|--------|---------|--------|
| Azure Digital Twins | ❌ Rejected | Azure lock-in; Africa latency issues; limited physics simulation |
| AWS IoT TwinMaker | ❌ Rejected | AWS lock-in; weak process industry simulation |
| Siemens Xcelerator / MindSphere | ❌ Rejected | High licence cost ($8–15M vs. $2–3M); MindSphere transition risk |
| Coo-Cah Proprietary DT Engine (full build) | 🟡 Partially adopted | Adopted but combined with InfluxDB + open-source stack to reduce build time |
| **Hybrid — Coo-Cah DT Engine + InfluxDB + open-source connectors** | **✅ Selected** | Best balance of control, cost, and time-to-value |

---

## 2. Technology Stack

The Coo-Cah DT Engine is built on the following components:

| Component | Technology | Role |
|-----------|-----------|------|
| Time-series store | InfluxDB | All sensor data, historian-equivalent |
| REST API layer | FastAPI (Python) | Asset state queries, DT read/write |
| Dashboard | Grafana | Real-time factory operations dashboards |
| Edge messaging | MQTT (Mosquitto / EMQX) | Edge-to-cloud sensor relay |
| Factory floor integration | OPC-UA connectors | DCS / PLC integration |
| Process simulation — thermal / kinematic | Python (SciPy + custom models) | Phase 2 predictive models |
| Process simulation — fluid (chemicals) | OpenFOAM | Phase 2 chemicals vertical CFD |
| AI integration layer | REST endpoints (FastAPI) | Consumed by Coo-Cah AI Platform for PdM, yield, energy |
| Edge runtime | Docker containers on factory edge server | Phase 1: local operation; syncs to cloud every 30 s |

---

## 3. Deployment Model

### 3.1 Architecture Overview

```
┌─────────────────────────────────────────────────────────────────────┐
│                     FACTORY EDGE NODE (per factory)                  │
│                                                                       │
│  ┌────────────────┐  ┌──────────────────┐  ┌─────────────────────┐  │
│  │  IoT Gateway   │  │  OPC-UA Connector │  │  MQTT Broker        │  │
│  │  (MQTT bridge) │  │  (PLC / DCS)      │  │  (Mosquitto / EMQX) │  │
│  └───────┬────────┘  └────────┬──────────┘  └──────────┬──────────┘  │
│          └───────────────────▼──────────────────────────┘            │
│                         Edge DT Engine                                │
│              ┌─────────────────────────────────────┐                 │
│              │  InfluxDB (local)                   │                 │
│              │  FastAPI asset state service         │                 │
│              │  Grafana (local ops dashboard)      │                 │
│              └──────────────────┬──────────────────┘                 │
│                                 │ 30-second sync (REST)               │
└─────────────────────────────────┼───────────────────────────────────┘
                                  │
                    ┌─────────────▼──────────────┐
                    │  CLOUD LAYER (Rwanda Hub)   │
                    │                             │
                    │  InfluxDB Cloud (fleet)     │
                    │  FastAPI (group DT API)     │
                    │  Grafana (group dashboard)  │
                    │  AI Platform integration    │
                    │  Group ERP sync             │
                    └─────────────────────────────┘
```

### 3.2 Edge Node Specification (minimum per factory)

| Resource | Specification |
|----------|--------------|
| CPU | Intel Core i7 / Xeon E-series (8 cores) or equivalent ARM |
| RAM | 32 GB |
| Storage | 2 TB NVMe SSD (RAID-1) |
| OS | Ubuntu 22.04 LTS |
| Runtime | Docker + Docker Compose |
| Network | Dual NIC: OT-side (DCS/IoT VLAN) + IT-side (factory LAN / internet uplink) |
| UPS | Minimum 4-hour battery backup (factory's own CCG-UPS product where applicable) |

### 3.3 Internet Resilience

The edge node operates **fully independently during internet outages**:
- InfluxDB stores 90 days of local time-series data
- Grafana dashboards run locally from edge InfluxDB
- FastAPI asset state service continues accepting writes
- On reconnection, edge node syncs delta to cloud automatically

---

## 4. Factory Integration Standards

Every factory repo's `docs/digital-twin.md` must conform to these group standards.

### 4.0 Gate 2 Normative Dependencies

This architecture is normative only when implemented with the following companion standards:

1. [`/platform/asset-id-naming-convention.md`](./asset-id-naming-convention.md)
2. [`/platform/mqtt-topic-schema.md`](./mqtt-topic-schema.md)
3. [`/platform/digital-twin-data-model.md`](./digital-twin-data-model.md)
4. [`/platform/cross-factory-simulation-spec.md`](./cross-factory-simulation-spec.md)

Canonical package entrypoint:
- [`/platform/README.md`](./README.md)

### 4.1 Required Sensor Integration Points

| Integration | Protocol | Minimum Frequency |
|-------------|----------|-------------------|
| Machine state (run / idle / fault) | OPC-UA or MQTT | On-change + 30 s heartbeat |
| Critical process parameters | OPC-UA | 1–5 seconds |
| Energy sub-meters | Modbus TCP → MQTT | 30 seconds |
| AMR fleet positions | REST API | 10 seconds |
| MES production events | REST API (push) | Per event (real-time) |
| Quality inspection results | REST API (push) | Per event (real-time) |

### 4.2 Asset Naming Convention

All assets must use the Coo-Cah tag format:

```
[FACTORY_ID]-[AREA]-[UNIT]-[SEQUENCE]

Examples:
  CCG-PE-SMT-03      (Power Electronics factory, SMT area, unit 03)
  CCH-PLS-EXT-A1-01  (Plastics factory, Extrusion area, unit A1, asset 01)
  CCH-MET-ROLL-01    (Metallurgical factory, Rolling mill, asset 01)
```

### 4.3 Data Retention Policy (Group Standard)

| Tier | Storage | Retention | Scope |
|------|---------|-----------|-------|
| Hot (real-time) | InfluxDB (edge + cloud) | 90 days | All sensor streams |
| Warm (operational) | PostgreSQL + object storage | 3 years | Aggregated time-series, events |
| Cold (archive) | Object storage (S3-compatible) | 10 years | ISO 50001, audit evidence, warranty records |

> Data governance policy — ownership, access control, and cross-factory visibility rights —
> is defined in [`/platform/data-governance-policy.md`](./data-governance-policy.md).

### 4.4 AI Platform Integration

The DT Engine exposes REST endpoints consumed by the Coo-Cah Central AI Platform:

| Endpoint | Data | Consumer |
|----------|------|----------|
| `GET /dt/assets/{id}/state` | Real-time asset state | AI Platform — PdM inference |
| `GET /dt/assets/{id}/history` | Time-series (last N days) | AI Platform — model training |
| `POST /dt/events` | Event stream (alarms, state changes) | AI Platform — anomaly detection |
| `GET /dt/factory/oee` | OEE by line and shift | Group operations dashboard |
| `GET /dt/factory/energy` | Energy summary | Group sustainability reporting |

---

## 5. Security and Network Segmentation

### 5.1 OT/IT Network Isolation

```
OT Network (DCS / PLC / IoT)
    ↕ OPC-UA / MQTT (read-only from OT → edge DT)
Factory Edge Node (IT/OT DMZ)
    ↕ REST / MQTT over TLS (encrypted, authenticated)
Factory IT Network (MES / ERP servers)
    ↕ REST over HTTPS (TLS 1.3; JWT auth)
Cloud DT Layer (Rwanda)
    ↕ REST over HTTPS (TLS 1.3; JWT auth)
Coo-Cah AI Platform
```

**Key rules:**
- The edge DT node **never writes back to the OT network** in Phase 1 or Phase 2
- All cloud connections use TLS 1.3 minimum; certificates rotated annually
- Factory API keys are factory-scoped; no cross-factory read without explicit group-level API key
- Phase 3 autonomous setpoint write-back requires explicit DCS engineering change and separate safety review

### 5.2 Authentication

| Interface | Authentication |
|-----------|---------------|
| Factory edge → cloud DT | JWT (factory-scoped service account; 24 h token rotation) |
| MES → DT edge | OAuth 2.0 client credentials flow |
| AI Platform → DT cloud | JWT (service account; read-only scope) |
| Grafana dashboard access | LDAP/SSO (group Active Directory) |
| Factory manager mobile app | OAuth 2.0 + MFA |

---

## 6. Phase Rollout Plan

| Phase | Scope | Target |
|-------|-------|--------|
| **Phase 1 — Pilot Twin** | Personal Electronics (Sagamu) with auditable evidence gates | 90-day pilot window (Days 0–90) |
| **Phase 2 — Tier 1 Wave 1** | Security Electronics + Kitchen Electronics | Starts only after pilot go/no-go is fully green |
| **Phase 3 — Tier 1 Wave 2 and beyond** | Remaining electronics + selected consumer-goods factories, then full fleet | Sequenced by standards inheritance and evidence readiness |

The pilot factory is designated in [`docs/orchestration/factory-status-registry.md`](../docs/orchestration/factory-status-registry.md).

---

## 7. Review Triggers

This architecture should be reviewed if:
- DT Engineering team cannot deliver pilot twin within 12 months of formation
- AI Platform team identifies fundamental data quality issues from DT Engine time-series
- A Siemens Xcelerator commercial offer significantly undercuts the estimated build cost ($2–3M)
- Edge node connectivity requirements change materially (e.g., satellite uplink mandate)

---

## 8. Related Documents

| Document | Location |
|----------|----------|
| Platform Standards Index (Gate 2) | [`platform/README.md`](./README.md) |
| ADR-003 — Digital Twin Platform Selection | [`docs/adrs/ADR-003-digital-twin-platform.md`](../docs/adrs/ADR-003-digital-twin-platform.md) |
| ADR-002 — MES Platform Selection | [`docs/adrs/ADR-002-mes-platform-selection.md`](../docs/adrs/ADR-002-mes-platform-selection.md) |
| ADR-006 — AI Platform Architecture | [`docs/adrs/ADR-006-ai-platform-architecture.md`](../docs/adrs/ADR-006-ai-platform-architecture.md) |
| Asset ID Naming Convention | [`platform/asset-id-naming-convention.md`](./asset-id-naming-convention.md) |
| MQTT Topic Schema | [`platform/mqtt-topic-schema.md`](./mqtt-topic-schema.md) |
| DT Data Model | [`platform/digital-twin-data-model.md`](./digital-twin-data-model.md) |
| Cross-Factory Simulation Spec | [`platform/cross-factory-simulation-spec.md`](./cross-factory-simulation-spec.md) |
| Data Governance Policy | [`platform/data-governance-policy.md`](./data-governance-policy.md) |
| Factory Status Registry (incl. DT Pilot Designation) | [`docs/orchestration/factory-status-registry.md`](../docs/orchestration/factory-status-registry.md) |
| Gate 4 Decisions & Evidence Checklist | [`docs/orchestration/gate-4-decisions.md`](../docs/orchestration/gate-4-decisions.md) |

---

*This document is the authoritative group-level reference for DT platform architecture in Gate 2.
All factory-level `docs/digital-twin.md` files must align with this architecture and its Gate 2 normative dependencies.*
