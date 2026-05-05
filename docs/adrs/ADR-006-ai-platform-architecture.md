# ADR-006: Central AI Platform Architecture

**Status:** ACCEPTED  
**Date:** 2025-04-15  
**Deciders:** Group CTO, AI Platform Architect, Head of Smart Factory Core, Head of Digital Twin  
**Technical Story:** [Issue #38 — AI Platform Architecture](https://github.com/oumar-code/Coo-Kah-Doks/issues/38)

---

## Context

The Coo-Cah Central AI Platform is the intelligence layer above the MES, Digital Twin, and ERP. It consumes real-time production data, historical MES records, DT telemetry, and supply chain data to deliver:

1. **Predictive Maintenance (PdM):** Predict equipment failures before they occur (all 15+ factories)
2. **Yield Optimisation:** AI-recommended process parameters to maximise batch yield (chemicals + food)
3. **AI Visual QC:** Computer vision defect detection on production lines (electronics + FMCG)
4. **AI Scheduling:** Autonomous production scheduling across factory lines (Phase 3)
5. **AI NVR Models:** Deep-learning models deployed into security camera NVR products (Security Electronics factory)
6. **Energy AI:** Optimise BESS dispatch + process scheduling around solar generation

---

## Architecture Decision

**Selected: Microservices AI Platform on Coo-Cah Cloud (Rwanda HQ)**

### Components

| Service | Technology | Responsibility |
|---------|-----------|----------------|
| Data Ingestion | Apache Kafka | Real-time stream from DT Engine + MES |
| Feature Store | Feast (open source) | Pre-computed ML features per factory |
| Model Training | MLflow + Kubernetes | Versioned model training; experiment tracking |
| Model Serving | FastAPI + KServe | Real-time inference endpoint per AI service |
| PdM Service | Isolation Forest + LSTM | Anomaly detection on equipment telemetry |
| Visual QC Service | YOLOv8 + EfficientDet | Defect detection; SMT AOI; cosmetic QC |
| Yield AI Service | XGBoost + GP regression | Batch yield prediction; setpoint recommendation |
| Energy AI Service | Prophet + RL agent | BESS dispatch + process scheduling |
| NVR Model Registry | MLflow + ONNX export | AI NVR models deployed to Security Electronics factory |
| AI Dashboard | Grafana + custom React | Group-wide AI performance monitoring |

### Data Flow

```
Factory Floor (MES + DCS + Sensors)
    ↓ MQTT / OPC-UA
DT Engine (Edge Node per factory)
    ↓ REST API stream
Apache Kafka (Rwanda Cloud)
    ↓ Consumer groups
Feature Store (Feast)
    ↓ Feature vectors
Model Serving (KServe)
    ↓ Predictions / recommendations
MES API → Factory operators
ERP API → Procurement / planning
```

---

## Consequences

**Positive:**
- Each AI service independently deployable and scalable
- MLflow enables full model versioning — critical for NVR product model OTA updates
- Open-source stack minimises vendor licence costs

**Negative:**
- Requires MLOps engineering team (4–6 engineers for AI Platform)
- Kafka + Kubernetes adds operational complexity; requires DevOps capability

**Neutral:**
- Phase 1: PdM + Energy AI deployed; others follow on Phase 2 schedule

---

*Related ADRs: [ADR-003](./ADR-003-digital-twin-platform.md)*
