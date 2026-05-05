# Coo-Cah Plastics & Polymers Factory — Digital Twin Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Plastics & Polymers Factory | **Location:** Agbara Industrial Estate, Lagos State / Sagamu, Ogun State, Nigeria | **Phase:** Phase 1 (Priority — supplies all Coo-Cah factories)
> **Document Version:** 1.0 | **Owner:** Coo-Cah Technology Division — Digital Twin Team

---

## 1. Introduction

The Coo-Cah Plastics & Polymers Factory digital twin is a **process-level simulation twin** — distinct from the discrete assembly factory twins in the Electronics vertical. Rather than tracking individual product units, the chemical factory digital twin models continuous process streams, batch reaction cycles, and mass/energy balances in real time, enabling process optimisation, safety monitoring, and regulatory reporting.

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

### 3.1 Polymer Reaction & Compounding Assets

| DT Asset ID     | Physical Asset                       | DT Model Type          | Sensor Count | Integration |
|-----------------|--------------------------------------|------------------------|--------------|-------------|
| DT-PLS-PR-001   | Reactor / Reaction Vessel #1         | Process + Thermal      | 20–40        | OPC-UA      |
| DT-PLS-PR-002   | Reactor / Reaction Vessel #2         | Process + Thermal      | 20–40        | OPC-UA      |
| DT-PLS-PR-003   | Reactor / Reaction Vessel #3 (opt.)  | Process + Thermal      | 20–40        | OPC-UA      |
| DT-PLS-HE-001   | Heat Exchanger Train (primary)       | Thermal Degradation    | 12–18        | OPC-UA      |
| DT-PLS-HE-002   | Heat Exchanger Train (secondary)     | Thermal Degradation    | 12–18        | OPC-UA      |
| DT-PLS-DC-001   | Distillation / Devolatilisation Column #1 | Mass Transfer Model | 18–30       | OPC-UA      |
| DT-PLS-DC-002   | Distillation Column #2 (opt.)        | Mass Transfer Model    | 18–30        | OPC-UA      |
| DT-PLS-PM-001   | Process Pumps — Grundfos / Flowserve (all critical) | Vibration + Process | 4 per pump | MQTT |
| DT-PLS-CP-001   | Compressors — Atlas Copco / Ingersoll-Rand (all) | Vibration + Thermal | 6 per unit | OPC-UA |
| DT-PLS-CS-001   | Cooling Tower + Chiller System       | Thermal + Flow         | 10–14        | OPC-UA      |
| DT-PLS-NT-001   | PSA Nitrogen Generator               | Process State          | 6            | MQTT        |

### 3.2 Plastics Converting Lines

| DT Asset ID     | Physical Asset                          | DT Model Type           | Sensor Count | Integration |
|-----------------|-----------------------------------------|-------------------------|--------------|-------------|
| DT-PLS-EX-001   | Single-Screw Extrusion Line #1          | Thermal + Kinematic     | 14–20        | OPC-UA      |
| DT-PLS-EX-002   | Single-Screw Extrusion Line #2          | Thermal + Kinematic     | 14–20        | OPC-UA      |
| DT-PLS-EX-003   | Twin-Screw Compounding Extruder         | Thermal + Kinematic     | 18–24        | OPC-UA      |
| DT-PLS-IM-001   | Injection Moulding Machine #1           | Thermal + Kinematic     | 16–22        | OPC-UA      |
| DT-PLS-IM-002   | Injection Moulding Machine #2           | Thermal + Kinematic     | 16–22        | OPC-UA      |
| DT-PLS-BM-001   | Blow Moulding Machine #1               | Thermal + Pressure      | 12–16        | OPC-UA      |
| DT-PLS-BM-002   | Blow Moulding Machine #2               | Thermal + Pressure      | 12–16        | OPC-UA      |
| DT-PLS-FI-001   | Filtration / Separation Unit #1         | Process + Flow          | 8–12         | OPC-UA      |
| DT-PLS-FI-002   | Filtration / Separation Unit #2         | Process + Flow          | 8–12         | OPC-UA      |

Each converting line DT model tracks barrel zone temperatures, screw torque, melt pressure, and throughput in real time. Deviations from recipe set-points trigger operator alerts before product quality falls out of specification.

### 3.3 Bagging & Filling Lines

| DT Asset ID     | Physical Asset                    | DT Model Type       | Sensor Count | Integration |
|-----------------|-----------------------------------|---------------------|--------------|-------------|
| DT-PLS-BF-001   | Bagging / Filling Line #1 (bulk)  | Mass Flow + Weigh   | 8            | OPC-UA      |
| DT-PLS-BF-002   | Bagging / Filling Line #2         | Mass Flow + Weigh   | 8            | OPC-UA      |
| DT-PLS-BF-003   | Bagging / Filling Line #3 (opt.)  | Mass Flow + Weigh   | 8            | OPC-UA      |
| DT-PLS-BF-004   | Bagging / Filling Line #4 (opt.)  | Mass Flow + Weigh   | 8            | OPC-UA      |

### 3.4 Material Handling & Logistics Assets

| DT Asset ID     | Physical Asset                          | DT Model Type       | Update Freq. | Integration  |
|-----------------|-----------------------------------------|---------------------|--------------|--------------|
| DT-PLS-AMR-001  | Electric Counterbalance Forklift #1     | Position + State    | 5 sec        | RFID + MQTT  |
| DT-PLS-AMR-002  | Electric Counterbalance Forklift #2     | Position + State    | 5 sec        | RFID + MQTT  |
| DT-PLS-CV-001   | Belt Conveyor — Z2 to Z4 transfer       | State + Speed       | 10 sec       | MQTT         |
| DT-PLS-CV-002   | Belt Conveyor — Z4 bagging line feed    | State + Speed       | 10 sec       | MQTT         |
| DT-PLS-TK-001   | Raw Material Storage Tanks (Z1/Z5, all) | Level + Temp        | 1 min        | OPC-UA       |

### 3.5 Environmental & Safety Assets

| DT Asset ID     | Physical Asset                        | DT Model Type          | Update Freq. | Integration |
|-----------------|---------------------------------------|------------------------|--------------|-------------|
| DT-PLS-GS-001   | Gas Detection Array (all hazard zones)| Concentration Map      | 10 sec       | DCS OPC-UA  |
| DT-PLS-ETP-001  | Effluent Treatment Plant              | Process + Chemistry    | 5 min        | SCADA MQTT  |
| DT-PLS-ST-001   | Stack Emissions Monitor (CEMS)        | Continuous Emissions   | 1 min        | DCS OPC-UA  |
| DT-PLS-CT-001   | Cooling Tower (Z6)                    | Thermal + Water Chem   | 5 min        | MQTT        |
| DT-PLS-EN-001   | Solar PV + BESS System                | Power Curve            | 30 sec       | EMS MQTT    |

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

### 4.4 Emissions Compliance Simulation

**Use Case:** Continuously compare CEMS (Continuous Emissions Monitoring System) stack readings and ETP effluent discharge values against NESREA permit limits, generating pre-emptive alerts before a consent breach occurs and producing regulatory reports automatically.

| Input                                 | Output                                        | Trigger                                  |
|---------------------------------------|-----------------------------------------------|------------------------------------------|
| CEMS SO₂, NOₓ, VOC, PM readings       | % of permit limit consumed (real-time)        | Every 1 min; alert if > 80% of limit     |
| ETP effluent COD, BOD, pH, TSS        | Predicted consent breach within 4 hours       | Every 5 min; alert if trend to limit     |
| Production schedule + recipe          | Forecasted emission load for next 24 hours    | Daily; updated on recipe change          |
| Incident history                      | Exceedance probability score by process step  | Weekly AI analysis; NESREA reporting     |

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

## 6. Sensor Coverage Map

| Zone                          | Temp / Pressure | Flow / Level | Vibration | Gas / Emissions | Position / State | Total (approx.) |
|-------------------------------|-----------------|--------------|-----------|-----------------|------------------|-----------------|
| Z1 — Raw Material Storage     | 10              | 20           | —         | 6               | 4                | ~40             |
| Z2 — Reaction & Compounding   | 60              | 30           | 20        | 12              | 8                | ~130            |
| Z3 — Separation & Filtration  | 20              | 20           | 8         | 4               | 4                | ~56             |
| Z4 — Converting Lines (extrusion / moulding) | 60 | 16    | 12        | 4               | 8                | ~100            |
| Z4 — Bagging & Filling Lines  | 4               | 16           | 4         | 2               | 4                | ~30             |
| Z5 — Product Tank Farm        | 10              | 20           | —         | 8               | 4                | ~42             |
| Z6 — Utilities (cooling, N₂, steam) | 20        | 16           | 8         | 2               | 4                | ~50             |
| Z7 — ETP + Stack              | 12              | 14           | 4         | 16              | 2                | ~48             |
| **Total (approx.)**           | **196**         | **152**      | **56**    | **54**          | **38**           | **~496**        |

*Sensor counts are indicative. Final counts confirmed at FEED / detail engineering stage.*

---

*Refer to [`mes-integration.md`](./mes-integration.md) for MES-DCS integration.*
*Refer to [`machinery.md`](./machinery.md) for full equipment register.*
