# Coo-Cah Fine Chemicals Factory — Digital Twin Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Fine Chemicals Factory | **Location:** Asaba Industrial Estate, Delta State, Nigeria | **Phase:** Phase 2
> **Document Version:** 1.0 | **Owner:** Coo-Cah Technology Division — Digital Twin Team

---

## 1. Introduction

The Coo-Cah Fine Chemicals Factory digital twin is a **process-level simulation twin** — distinct from the discrete assembly factory twins in the Electronics vertical. Rather than tracking individual product units, the chemical factory digital twin models continuous process streams, batch reaction cycles, and mass/energy balances in real time, enabling process optimisation, safety monitoring, and regulatory reporting.

**Digital Twin Objectives:**
1. Real-time mass and energy balance across all process streams
2. Predictive quality: predict product purity from process conditions before offline lab result
3. Safety monitoring: compare DCS process state vs. DT model; flag deviations before SIS activation
4. Energy optimisation: schedule high-energy process steps around solar peak generation
5. Predictive maintenance: rotating equipment (pumps, compressors, agitators)
6. Environmental reporting: continuous emissions tracking; NESREA compliance monitoring

---

## 2. Digital Twin Architecture

```
Process Instrumentation (DCS field instruments)
    │ OPC-DA / OPC-UA → DCS Historian (OSIsoft PI or similar)
    ▼
Edge Gateway (Factory Control Room)
    │ Data aggregation; local anomaly detection; DCS integration
    ▼
Coo-Cah DT Engine (Cloud — Rwanda HQ)
    ├── Process Mass Balance Model
    ├── Energy Balance Model
    ├── Quality / Purity Prediction Model (ML)
    ├── Emissions Tracker (NESREA reporting)
    ├── Safety Delta Monitor (DCS vs. DT)
    ├── Rotating Equipment PdM (vibration + process data)
    ├── Time-Series Store (InfluxDB / OSIsoft PI)
    └── DT API → MES, AI Platform, Safety Team, EHS Team
```

---

## 3. Asset Registry

### 3.1 Primary Process Assets

| DT Asset ID     | Physical Asset                   | DT Model Type          | Sensor Count | Integration |
|-----------------|----------------------------------|------------------------|--------------|-------------|
| DT-CHM-PR-001   | Reactor / Reaction Vessel #1     | Process + Thermal      | 20–40        | OPC-UA      |
| DT-CHM-PR-002   | Reactor / Reaction Vessel #2     | Process + Thermal      | 20–40        | OPC-UA      |
| DT-CHM-HE-001   | Heat Exchanger Train (primary)   | Thermal Degradation    | 12–18        | OPC-UA      |
| DT-CHM-DC-001   | Distillation Column(s)           | Mass Transfer Model    | 18–30        | OPC-UA      |
| DT-CHM-PM-001   | Process Pumps (critical, all)    | Vibration + Process    | 4 per pump   | MQTT        |
| DT-CHM-CP-001   | Compressors (all critical)       | Vibration + Thermal    | 6 per unit   | OPC-UA      |

### 3.2 Safety + Environmental Assets

| DT Asset ID     | Physical Asset                   | DT Model Type          | Update Freq. | Integration |
|-----------------|----------------------------------|------------------------|--------------|-------------|
| DT-CHM-GS-001   | Gas Detection Array              | Concentration Map      | 10 sec       | DCS OPC-UA  |
| DT-CHM-ETP-001  | Effluent Treatment Plant         | Process + Chemistry    | 5 min        | SCADA MQTT  |
| DT-CHM-EN-001   | Solar PV + BESS System           | Power Curve            | 30 sec       | EMS MQTT    |

---

## 4. Key Simulation Use Cases

### 4.1 Predictive Quality

| Input                        | Output                                | Trigger                      |
|------------------------------|---------------------------------------|------------------------------|
| Real-time process conditions | Predicted product purity (%)          | Continuously every 5 min     |
| Batch recipe parameters      | Estimated batch completion quality    | Start of each batch          |

### 4.2 Safety Delta Monitoring

| Input                        | Output                                | Trigger                      |
|------------------------------|---------------------------------------|------------------------------|
| DCS tag readings             | Delta from DT model predictions       | Every 30 sec; alert if > 3σ  |
| Historical incident data     | Probability of approaching unsafe state| Pre-emptive operator alert  |

### 4.3 Energy Optimisation

| Input                        | Output                                | Trigger                      |
|------------------------------|---------------------------------------|------------------------------|
| Production schedule          | Optimal process scheduling vs. solar  | Daily; 15-min intervals      |
| BESS state of charge         | Process step timing recommendations   | Ongoing EMS AI               |

---

## 5. Data Retention Policy

| Data Category              | Hot Storage | Cold Storage | Policy                         |
|----------------------------|-------------|--------------|--------------------------------|
| Process DCS data (all tags)| 1 year      | 10 years     | Process safety records 10 yr   |
| Gas detection readings     | 2 years     | 15 years     | Safety incident records         |
| Quality/purity predictions | 2 years     | 7 years      | Batch record traceability       |
| Effluent monitoring        | 2 years     | 10 years     | NESREA regulatory compliance    |
| Energy / carbon data       | 1 year      | 10 years     | Carbon accounting               |

---

*Refer to [`mes-integration.md`](./mes-integration.md) for MES-DCS integration.*
*Refer to [`machinery.md`](./machinery.md) for full equipment register.*

*For standalone sensor mapping, refer to [`docs/sensor-map.md`](./docs/sensor-map.md).*
*For BIM/3D spatial stubs, refer to [`docs/bim/README.md`](./docs/bim/README.md).*
