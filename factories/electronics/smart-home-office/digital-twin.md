# Smart Home & Office Electronics Factory — Digital Twin Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Smart Home & Office Electronics Factory | **Location:** Agbara Industrial Estate, Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Coo-Cah Technology Division — Digital Twin Team

---

## 1. Introduction

The Smart Home & Office Electronics Digital Twin provides real-time virtualisation of the dual SMT lines, Smart TV assembly lines, laptop assembly, router/hub assembly, and RF test chambers. A notable feature is the **Android TV performance simulation** — new display panel batches can be simulated through the assembly and test flow to predict NCC compliance pass rates before committing a full production run.

**Digital Twin Objectives:**
1. Real-time factory state: both SMT lines; TV, laptop, router, speaker lines
2. RF test chamber utilisation simulation — prevent NCC TA test bottlenecks
3. Screen bonding quality prediction: UV cure parameters → bonding defect probability
4. Predictive maintenance: SMT reflow ovens, screen bonding machines, acoustic test rigs
5. Energy optimisation: dual SMT reflow ovens create dominant peak load
6. Phase 2: cobot integration and AI vision QC integration

---

## 2. Asset Registry

### 2.1 SMT Lines

| DT Asset ID    | Physical Asset                 | DT Model Type      | Sensor Count | Integration |
|----------------|--------------------------------|--------------------|--------------|-------------|
| DT-SHO-PE-001  | DEK Horizon Printer — Line 1   | State + Thermal    | 8            | OPC-UA      |
| DT-SHO-PE-002  | JUKI RX-7R P&P #1 (Line 1)     | Kinematic + State  | 12           | OPC-UA      |
| DT-SHO-PE-003  | JUKI RX-7R P&P #2 (Line 1)     | Kinematic + State  | 12           | OPC-UA      |
| DT-SHO-PE-004  | Heller 1964 Reflow (Line 1)    | Multi-Zone Thermal | 28           | OPC-UA      |
| DT-SHO-PE-005  | Koh Young AOI (Line 1)         | Vision + State     | 6            | OPC-UA+REST |
| DT-SHO-PE-006-010 | SMT Line 2 (identical set) | (as above)         | Same          | OPC-UA     |

### 2.2 Product Assembly Lines

| DT Asset ID    | Physical Asset                        | DT Model Type     | Sensor Count | Integration |
|----------------|---------------------------------------|-------------------|--------------|-------------|
| DT-SHO-TV-001  | TV Assembly Line — 32"/43"            | State + Kinematic | 20           | MQTT/OPC-UA |
| DT-SHO-TV-002  | TV Assembly Line — 55"/65"            | State + Kinematic | 20           | MQTT/OPC-UA |
| DT-SHO-TV-003  | Screen Bonding Machine ×4             | Thermal + Kinematic| 16          | OPC-UA      |
| DT-SHO-LP-001  | Laptop Assembly Line                  | State + Kinematic | 18           | MQTT/Panel PC|
| DT-SHO-RT-001  | Router Assembly + RF Test             | State + RF        | 12           | OPC-UA+REST |
| DT-SHO-SP-001  | Smart Speaker + Hub Assembly          | State + Acoustic  | 10           | MQTT        |
| DT-SHO-PJ-001  | Projector Assembly + Optical Test     | State + Optical   | 14           | OPC-UA      |

### 2.3 RF Test Assets

| DT Asset ID    | Physical Asset                    | DT Model Type     | Update Freq. | Integration |
|----------------|-----------------------------------|-------------------|--------------|-------------|
| DT-SHO-RF-001  | RF Shielded Test Chamber #1       | State + RF        | Per test     | REST API    |
| DT-SHO-RF-002  | RF Shielded Test Chamber #2       | State + RF        | Per test     | REST API    |
| DT-SHO-RF-003  | RF Shielded Test Chamber #3       | State + RF        | Per test     | REST API    |

### 2.4 Energy System Assets

| DT Asset ID    | Physical Asset                | DT Model Type    | Update Freq. | Integration    |
|----------------|-------------------------------|------------------|--------------|----------------|
| DT-SHO-EN-001  | Solar PV Array 750 kWp        | Power Curve      | 30 sec       | EMS MQTT       |
| DT-SHO-EN-002  | LFP BESS 800 kWh              | Electrochemical  | 30 sec       | BMS MQTT       |
| DT-SHO-EN-003  | Hybrid Inverters              | State Machine    | 30 sec       | Modbus TCP     |
| DT-SHO-EN-004  | SMT Line 1 + 2 Load Monitor   | Demand Spikes    | 5 sec        | Power analyser |

---

## 3. Key Simulation Use Cases

### 3.1 Screen Bonding Quality Simulation

**Use Case:** New display panel batch received with different glass thickness. Simulate UV cure energy and pressure parameters to predict bonding delamination risk before committing production run.

| Input                      | Output                            | Trigger                    |
|----------------------------|-----------------------------------|----------------------------|
| New panel batch parameters | Bond quality probability score    | New display batch received |
| UV lamp intensity (mW/cm²) | Optimal cure time recommendation  | Pre-production validation  |

### 3.2 NCC RF Test Chamber Bottleneck Simulation

**Use Case:** Schedule all NCC pre-compliance tests across 3 RF chambers to avoid bottlenecks when launching multiple SKUs simultaneously.

| Input                      | Output                            | Trigger                    |
|----------------------------|-----------------------------------|----------------------------|
| Launch schedule (new SKUs) | Optimal RF chamber booking plan   | Monthly NCC TA planning    |
| Test time per SKU type     | Expected NCC submission dates     | New product launch brief   |

### 3.3 Dual SMT Energy Peak Simulation

**Use Case:** Both reflow ovens peak simultaneously (2× 80 kW = 160 kW). Schedule BESS discharge to absorb peak and avoid grid demand charges.

| Input                      | Output                            | Trigger                    |
|----------------------------|-----------------------------------|----------------------------|
| Production schedule        | Predicted peak demand timing      | Daily scheduling run       |
| BESS SoC                   | BESS dispatch recommendation      | Every 15 min (EMS AI)      |

---

## 4. Data Retention Policy

| Data Category          | Hot Storage | Cold Storage | Policy                   |
|------------------------|-------------|--------------|--------------------------|
| Machine telemetry      | 90 days     | 2 years      | Archive after 90 days    |
| RF test results        | 3 years     | 10 years     | NCC compliance records   |
| Screen bonding params  | 2 years     | 7 years      | QMS + warranty records   |
| Laptop battery records | 2 years     | 10 years     | Consumer safety records  |
| Energy data            | 1 year      | 10 years     | Carbon accounting        |

---

*Refer to [`machinery.md`](./machinery.md) and [`mes-integration.md`](./mes-integration.md).*
