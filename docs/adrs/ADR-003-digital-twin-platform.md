# ADR-003: Digital Twin Platform Selection

**Status:** ACCEPTED  
**Date:** 2025-03-05  
**Deciders:** Group CTO, Head of Digital Twin Team, Smart Factory Core Lead, AI Platform Architect  
**Technical Story:** [Issue #24 — Digital Twin Platform Selection](https://github.com/oumar-code/Coo-Kah-Doks/issues/24)

---

## Context

The Coo-Cah Digital Twin programme requires a platform capable of hosting **20+ factory digital twins** spanning electronics assembly, chemical processing, consumer goods manufacturing, and lifestyle production. Each twin must provide real-time process state, physics simulation (thermal, fluid, kinematic), predictive maintenance analytics, and energy optimisation — all connected to the group-wide AI Platform.

### Requirements

1. **Multi-factory scale:** Support 20+ distinct factory twins with a single management plane
2. **Real-time synchronisation:** Asset twins must update within ≤ 5 seconds of physical sensor reading
3. **Physics simulation:** Support thermal, kinematic, and (for chemicals) process flow simulation
4. **AI/ML integration:** Native connection to ML model training and inference pipelines
5. **Heterogeneous data sources:** OPC-UA, MQTT, REST API, Modbus TCP, AMR APIs — all ingested
6. **Edge + cloud hybrid:** Factory edge node for resilience; cloud for AI training and group visibility
7. **Open API:** DT twins must be consumable by MES, ERP, mobile apps via well-documented APIs
8. **African connectivity:** Must handle 50–500 ms internet latency gracefully at edge node

---

## Options Considered

### Option 1: Azure Digital Twins (Microsoft)
**Pros:** Cloud-native; strong ADT Query Language (DTQL); native Power BI integration; global support; free tier for initial pilot  
**Cons:** Azure lock-in; latency for Africa-based factories; requires Azure IoT Hub as ingestion layer (adds cost + complexity); limited physics simulation native capability (requires third-party connectors)

### Option 2: AWS IoT TwinMaker
**Pros:** AWS ecosystem native; good alarm and time-series integration with Grafana; well-documented APIs  
**Cons:** AWS lock-in; limited native physics simulation; fewer manufacturing domain connectors than Siemens; weaker in process industry simulation

### Option 3: Siemens Industrial Edge + Xcelerator (Teamcenter + MindSphere)
**Pros:** Deep integration with Siemens MES (Opcenter) — our selected MES per ADR-002; native OPC-UA; Teamcenter provides physics simulation (FEA, CFD, kinematic); proven in automotive and electronics manufacturing at scale  
**Cons:** Higher licence cost; complex implementation; MindSphere transitioning to Siemens Xcelerator (some API changes underway)

### Option 4: Coo-Cah Proprietary DT Engine (build in-house)
**Pros:** Full control; no vendor lock-in; optimised for Coo-Cah use cases; builds strategic internal capability  
**Cons:** High build cost; time to first value 18–24 months; limited physics simulation out of box; requires significant engineering team

### Option 5: Hybrid — Coo-Cah DT Engine + InfluxDB Time-Series + open-source connectors
**Pros:** Best balance of control, cost, and time-to-value; OSIsoft PI historian or InfluxDB for time-series; Grafana for dashboards; open-source physics simulation libraries (OpenFOAM for fluid); fully API-driven  
**Cons:** Requires significant integration engineering; no single vendor support contract; need to build simulation capability iteratively

---

## Decision

**Selected: Option 5 — Coo-Cah Proprietary DT Engine (Hybrid)**

The Coo-Cah DT Engine is built on:
- **InfluxDB** (time-series store for all sensor data)
- **FastAPI** (REST API layer for DT asset state and query)
- **Grafana** (real-time dashboards for factory operations teams)
- **MQTT broker (Mosquitto/EMQX)** (edge-to-cloud sensor data relay)
- **OPC-UA connectors** (factory floor DCS/PLC integration)
- **Physics simulation:** Python-based process models (thermal: SciPy; kinematic: custom); OpenFOAM for advanced fluid simulation (chemicals vertical Phase 2)
- **AI Platform integration:** DT Engine exposes REST endpoints consumed by AI Platform for PdM, yield, and energy AI services
- **Edge node:** Docker containers on factory edge server; sync to cloud every 30 seconds; local operation on internet outage

---

## Consequences

**Positive:**
- No vendor lock-in; full data sovereignty
- Builds strategic internal engineering capability
- Lower total cost than Azure/AWS/Siemens solutions at scale ($2–3M vs. $8–15M)
- Physics models can be optimised specifically for Coo-Cah processes

**Negative:**
- Longer initial build time (first twin operational Month 12; full fleet Month 30)
- Requires dedicated DT engineering team (4–6 engineers)
- Physics simulation quality dependent on in-house expertise

**Neutral:**
- ADR-002 (Siemens Opcenter MES) integrates with DT Engine via REST API + OPC-UA relay — compatible with either approach

---

## Review Trigger

This decision should be reviewed if:
- DT Engine team is unable to deliver first factory twin within 12 months of formation
- AI Platform team identifies fundamental data quality issues from DT Engine time-series
- A Siemens Xcelerator commercial offer is received that significantly undercuts the estimated build cost

---

*Related ADRs: [ADR-001](./ADR-001-energy-source-selection.md) | [ADR-002](./ADR-002-mes-platform-selection.md)*
