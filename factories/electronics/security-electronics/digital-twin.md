# Security Electronics Factory — Digital Twin Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Security Electronics Factory | **Location:** Ikorodu Industrial Estate, Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Coo-Cah Technology Division — Digital Twin Team

---

## 1. Introduction

The Security Electronics Digital Twin has a unique feature not present in other Coo-Cah factory twins: **product-embedded AI model version tracking**. The AI NVR product (CCX-AI-NVR) ships with deep-learning models for face recognition, intrusion detection, and crowd analytics. The digital twin tracks the model version deployed in every unit and supports OTA model update simulations before fleet-wide push.

**Digital Twin Objectives:**
1. Real-time production state: SMT, camera assembly, optical test, NVR/DVR assembly
2. Optical quality simulation: MTF (modulation transfer function) prediction by lens batch
3. AI NVR model version registry: every unit → deployed model version tracked
4. Predictive maintenance: SMT oven, camera lens alignment jigs, optical test rigs
5. Energy optimisation: compact factory, smaller loads — fine-grained peak management

---

## 2. Asset Registry

### 2.1 SMT Line Assets

| DT Asset ID    | Physical Asset              | DT Model Type      | Sensor Count | Integration |
|----------------|-----------------------------|--------------------|--------------|-------------|
| DT-SEC-PE-001  | DEK Horizon Printer         | State + Thermal    | 8            | OPC-UA      |
| DT-SEC-PE-002  | JUKI RX-7R P&P #1           | Kinematic + State  | 12           | OPC-UA      |
| DT-SEC-PE-003  | JUKI RX-7R P&P #2           | Kinematic + State  | 12           | OPC-UA      |
| DT-SEC-PE-004  | Heller Reflow Oven          | Multi-Zone Thermal | 28           | OPC-UA      |
| DT-SEC-PE-005  | Koh Young AOI               | Vision + State     | 6            | OPC-UA+REST |

### 2.2 Camera Assembly + Optical Test Assets

| DT Asset ID    | Physical Asset                    | DT Model Type     | Sensor Count | Integration |
|----------------|-----------------------------------|-------------------|--------------|-------------|
| DT-SEC-CAM-001 | IP Camera Assembly Line           | State + Kinematic | 16           | MQTT/HMI    |
| DT-SEC-CAM-002 | Lens Mount + Alignment Jig (×6)   | Kinematic+Optical | 12           | MQTT        |
| DT-SEC-CAM-003 | IR Illuminator Test (integrating sphere) | Optical State | 8            | OPC-UA      |
| DT-SEC-CAM-004 | MTF + Optical Resolution Test     | Optical + State   | 10           | REST API    |
| DT-SEC-CAM-005 | PTZ Camera Pan/Tilt Test Rig      | Kinematic + State | 8            | OPC-UA      |

### 2.3 NVR / DVR + AI NVR Assets

| DT Asset ID    | Physical Asset               | DT Model Type        | Sensor Count | Integration  |
|----------------|------------------------------|----------------------|--------------|--------------|
| DT-SEC-NVR-001 | NVR Assembly Line            | State + Kinematic    | 12           | Panel PC HMI |
| DT-SEC-NVR-002 | AI NVR Deep-Learning Test Server | AI Model Registry  | 4            | REST API     |
| DT-SEC-NVR-003 | HDD Pre-Format + Load Station | State + HDD SMART   | 6            | MQTT         |

### 2.4 Product-Level AI NVR Twin Registry

| Product                | DT Data Tracked                                              | Update Events                       |
|------------------------|--------------------------------------------------------------|-------------------------------------|
| AI NVR (CCX-AI-NVR)   | Serial; face-detect model version; intrusion-detect version; crowd-detect version | Manufacture; OTA model update; warranty return |
| Standard NVR (×4, ×16)| Serial; FW version; HDD S/N + health; PoE port test results | Manufacture; FW update              |

---

## 3. Key Simulation Use Cases

### 3.1 MTF (Optical Resolution) Batch Prediction

**Use Case:** New CMOS image sensor batch received with slight QE variation. Simulate expected MTF distribution across lenses from this batch to predict yield before full production run.

| Input                       | Output                               | Trigger                     |
|-----------------------------|--------------------------------------|-----------------------------|
| Batch CMOS QE measurements  | Predicted MTF distribution and yield | New sensor batch received   |
| Lens nominal specs          | Recommended tolerance window         | Pre-production review       |

### 3.2 AI NVR Model OTA Simulation

**Use Case:** New deep-learning model version ready for deployment. Simulate OTA push to 10 test units to verify deployment success rate before fleet-wide push.

| Input                       | Output                               | Trigger                     |
|-----------------------------|--------------------------------------|-----------------------------|
| New model version + weights | Predicted deployment success rate    | Before new model production run |
| Unit hardware config        | Risk of incompatibility              | AI Platform release pipeline |

---

## 4. Data Retention Policy

| Data Category          | Hot Storage | Cold Storage | Policy                     |
|------------------------|-------------|--------------|----------------------------|
| Machine telemetry      | 90 days     | 2 years      | Archive after 90 days      |
| Camera optical test    | 2 years     | 7 years      | QMS + warranty records     |
| AI NVR model registry  | Lifetime    | 15 years     | Product support + liability|
| NVR test results       | 3 years     | 10 years     | Warranty records           |
| Energy data            | 1 year      | 10 years     | Carbon accounting          |

---

*Refer to [`machinery.md`](./machinery.md) and [`mes-integration.md`](./mes-integration.md).*
