# Security Electronics Factory — MES Integration Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Security Electronics Factory | **Location:** Ikorodu Industrial Estate, Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Smart Factory Core Team

---

## 1. MES Overview

The Security Electronics factory deploys **Siemens Opcenter Execution Discrete** in SaaS + Edge Node mode. The MES has two unique capabilities:

1. **ONVIF Profile Compliance Tracking:** Every camera must pass ONVIF Profile S and T conformance tests before shipment. The MES ONVIF module records test results and blocks shipment if ONVIF compliance is not confirmed for the SKU.

2. **AI NVR Model Deployment Tracking:** The AI NVR product requires deployment of deep-learning inference models (face recognition, intrusion detection, crowd analysis) at the factory test station. The MES records the exact model version, inference benchmark score, and deployment timestamp per unit serial number.

| MES Attribute              | Value                                                             |
|----------------------------|-------------------------------------------------------------------|
| Platform                   | Siemens Opcenter Execution Discrete (SaaS + Edge)                 |
| Production Zones           | 8 zones; 32 MES-connected workstations                            |
| Serial Traceability        | All products serialised from PCB through final QC                 |
| ONVIF Module               | Profile S + T test results per camera serial                      |
| AI NVR Module              | Model version + benchmark score per NVR serial                    |
| ERP Integration            | Bidirectional REST API                                            |

---

## 2. MES Functional Modules

| Module                       | Function                                                             | Status  |
|------------------------------|----------------------------------------------------------------------|---------|
| Production Order Management  | Multi-product orders; camera + NVR + alarm + intercom families       | Phase 1 |
| Work Instruction Delivery    | Digital WI per product; camera size routing                          | Phase 1 |
| WIP Tracking                 | All units tracked from PCB through final QC                          | Phase 1 |
| Serial Traceability          | Unique serial from PCB sub-assembly; camera serial = body serial     | Phase 1 |
| OEE Data Collection          | Per line, per zone, factory blended                                  | Phase 1 |
| Quality (SPC + IPQC)         | Optical test results; IP rating results; ONVIF; cosmetic             | Phase 1 |
| ONVIF Compliance Module      | Profile S + T test pass/fail per camera serial; shipment gate        | Phase 1 |
| AI NVR Model Deploy Module   | Model version + inference score per NVR serial; blocks ship if fail  | Phase 1 |
| NCC TA Module                | Wi-Fi + BT type approval cert per SKU; shipment blocked if not current | Phase 1 |
| Firmware Flash Tracking      | FW version + hash for cameras, NVRs, access control, alarm panels   | Phase 1 |
| HDD SMART Data               | HDD serial + SMART pre-test result recorded for all NVRs             | Phase 1 |
| Label Control                | NCC mark; ONVIF logo; SON NIS; serial barcode; model label           | Phase 1 |
| Materials Management         | BOM backflush; CMOS sensor lot tracking (cold store alerts)          | Phase 1 |
| Energy Sub-Metering          | Per zone; optical test equipment as secondary energy consumer        | Phase 1 |

---

## 3. Production Zone MES Integration Map

| Zone | Name                        | # Stations | Connection  | Key MES Events                                                        |
|------|-----------------------------|------------|-------------|-----------------------------------------------------------------------|
| Z1   | Raw Material Store          | 3          | Barcode     | Goods receipt; CMOS sensor lot intake; cold store temp log            |
| Z2   | SMT PCB Line                | 5          | OPC-UA full | Print offset; feeder counts; reflow temps; AOI results                |
| Z3   | Camera Housing Prep         | 3          | Panel PC    | Lens serial scan; IR LED batch; housing cosmetic check                |
| Z4   | IP Camera Assembly          | 6          | Panel PC    | Lens mount torque; IR LED test (lux); IP seal torque; serial assigned |
| Z5   | Camera Optical + IP Test    | 5          | OPC-UA+REST | MTF score; IR illumination (lux at 30m/40m/100m); IP66 test result   |
| Z6   | NVR / AI NVR Assembly       | 5          | Panel PC    | HDD install serial + SMART; PoE port test; AI model deploy score      |
| Z7   | Access Control Assembly     | 4          | Panel PC    | RFID read test; biometric enrol test; TCP/IP comms test               |
| Z8   | Alarm + Intercom Assy       | 3          | Panel PC    | Zone detection test; GSM comms test; touchscreen test                 |
| Z9   | RF + NCC Test Zone          | 3          | REST API    | RF test report per serial; NCC TA check; ONVIF conformance link       |
| Z10  | Final QC + OBA              | 3          | Barcode+HMI | Final cosmetic; OBA sampling; NCC mark confirmation; ship release     |

---

## 4. ONVIF Compliance Module — Detailed Flow

```
Camera Serial Scanned at Z9 Entry
    │
    ▼
MES ONVIF Module: Check SKU's ONVIF Profile (S, T) certification status
    │
    ▼
ONVIF Conformance Test Tool (automated, Z9 test server):
  - Profile S: RTSP streaming; PTZ commands; event handling
  - Profile T: H.265 video; HTTPS; TLS; analytics metadata
  - Results: PASS / FAIL per profile
    │
    ▼
MES Writes to Camera Serial:
  - ONVIF Profile S result: PASS/FAIL
  - ONVIF Profile T result: PASS/FAIL
  - Test tool version + timestamp
    │
    ▼
PASS: Camera released to Final QC (Z10); ONVIF logo printed on label
FAIL: Unit held; engineering review; model re-certification triggered
```

---

## 5. AI NVR Model Deployment Module — Detailed Flow

```
AI NVR (CCX-AI-NVR) Serial Scanned at Z6 Model Deploy Station
    │
    ▼
MES AI NVR Module: Pull current approved model package from Coo-Cah AI Platform
  - Face Recognition Model: v[version], SHA256 hash
  - Intrusion Detection Model: v[version], SHA256 hash
  - Crowd Analytics Model: v[version], SHA256 hash
    │
    ▼
NVIDIA Jetson-based AI NVR Test Server:
  - Flash models to NVR via Ethernet
  - Run inference benchmark (COCO dataset subset, 100 frames)
  - Face recognition accuracy: report mAP score
  - Intrusion detection: report precision/recall
    │
    ▼
MES Writes to NVR Serial:
  - All model version codes + SHA256 hashes
  - Inference benchmark scores
  - Deployment timestamp
  - PASS if scores ≥ threshold; FAIL if below
    │
    ▼
PASS: NVR released to QC; product twin in DT updated
FAIL: Unit held; AI Platform notified; re-check model package
```

---

## 6. OEE Targets

| Line / Zone           | Phase 1 | Phase 2 | Phase 3 |
|-----------------------|---------|---------|---------|
| SMT PCB Line          | ≥ 76%   | ≥ 83%   | ≥ 89%   |
| Camera Assembly Line  | ≥ 70%   | ≥ 79%   | ≥ 86%   |
| Optical + IP Test     | ≥ 75%   | ≥ 84%   | ≥ 90%   |
| NVR / AI NVR Line     | ≥ 68%   | ≥ 78%   | ≥ 85%   |
| Access + Alarm Lines  | ≥ 78%   | ≥ 85%   | ≥ 91%   |
| **Blended Factory**   | **≥ 70%** | **≥ 80%** | **≥ 87%** |

---

*Refer to [`digital-twin.md`](./digital-twin.md) for AI NVR product twin registry.*
*Refer to [`regulatory.md`](./regulatory.md) for ONVIF, NCC, and SON compliance.*
