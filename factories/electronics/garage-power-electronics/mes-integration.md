# Garage & Power Electronics Factory — MES Integration Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Garage & Power Electronics Factory | **Location:** Sagamu Industrial Estate, Ogun State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Smart Factory Core Team

---

## 1. MES Overview

The Garage & Power Electronics Factory deploys **Siemens Opcenter Execution Discrete** as its MES, operating in SaaS + Edge Node mode per the Coo-Cah group standard (ADR-002). A critical unique requirement here is **load bank test traceability** — every inverter, UPS, and solar charge controller unit must have its full electrical test result (voltage, current, efficiency, THD, transfer time) permanently linked to its serial number in the MES, forming the warranty and product liability compliance record.

Additionally, this factory produces the inverters and backup power systems used internally by sister factories, making its production schedule tightly coupled to the group supply plan.

| MES Attribute               | Value                                                         |
|-----------------------------|---------------------------------------------------------------|
| Platform                    | Siemens Opcenter Execution Discrete (SaaS + Edge)             |
| Production Zones            | 9 zones; 38 MES-connected workstations                        |
| Serial Traceability         | All inverters, SCCs, UPS, power tools fully serialised        |
| Load Bank Test Module       | Automated OPC-UA data write; pass/fail gate in MES            |
| ERP Integration             | Bidirectional REST API; internal supply orders from HQ        |
| DT Integration              | Event streaming; product twin registration on serialisation   |

---

## 2. MES Functional Modules

| Module                          | Function                                                             | Status  |
|---------------------------------|----------------------------------------------------------------------|---------|
| Production Order Management     | Receives orders from ERP; includes internal supply orders           | Phase 1 |
| Work Instruction Delivery       | Digital work instructions per product type per station              | Phase 1 |
| WIP Tracking                    | Real-time position of every chassis through all zones               | Phase 1 |
| Serial / Traceability           | Unique serial assigned at Z4 entry (inverter); Z5 (SCC); Z7 (tools) | Phase 1 |
| OEE Collection                  | Availability, Performance, Quality per line                         | Phase 1 |
| Quality / SPC                   | Capture test results; SPC rules; auto-hold on deviation             | Phase 1 |
| Load Bank Test Module           | Electrical test data: V, A, eff, THD, transfer time per serial      | Phase 1 |
| Firmware Flash Tracking         | Firmware version + hash logged per serial at programming station    | Phase 1 |
| Label Control                   | Rating plate, SON label, barcodes, serial sticker triggered by MES  | Phase 1 |
| Materials Management            | BOM backflush; AMR replenishment triggers; transformer core tracking | Phase 1 |
| Internal Supply Management      | Priority flag for sister-factory internal orders vs. commercial     | Phase 1 |
| Maintenance (CMMS-lite)         | PM schedules; corrective tickets; load bank test fixture MTBF       | Phase 1 |
| Energy Sub-Metering             | Per-zone; load bank test bays flagged as high-load consumers        | Phase 1 |
| Predictive Maintenance (AI)     | AI Platform integration — winding quality prediction (Phase 2)      | Phase 2 |

---

## 3. Production Zone MES Integration Map

| Zone | Zone Name                   | # Stations | MES Connection  | Key MES Events                                                    |
|------|-----------------------------|------------|-----------------|-------------------------------------------------------------------|
| Z1   | Raw Material Store          | 3          | Barcode scanner | Goods receipt; component QC; stock allocation; core tracking      |
| Z2   | SMT PCB Line                | 5          | OPC-UA full     | Print offset; feeder counts; reflow temps; AOI results            |
| Z3   | Transformer Winding         | 4          | Panel PC HMI    | Resistance reading; turns count; core ID; winding operator ID     |
| Z4   | Inverter Assembly           | 8          | Panel PC HMI    | Chassis serial scan; board insertion; wiring check; phase test    |
| Z5   | SCC Assembly + Programming  | 4          | Panel PC HMI    | Programming serial; param set confirmation; function test result  |
| Z6   | UPS + Battery Charger Assy  | 4          | Panel PC HMI    | Battery installation date; transfer time test result              |
| Z7   | Power Tool Assembly         | 4          | Panel PC HMI    | Motor run test; no-load current; vibration baseline               |
| Z8   | Power Strip Assembly        | 4          | Panel PC HMI    | Surge test result; continuity; socket force test                  |
| Z9   | Load Bank Test (8 bays)     | 8          | OPC-UA          | Full test cycle result: V, A, efficiency, THD, waveform          |
| Z10  | Final QC + OBA              | 3          | Barcode + HMI   | OBA result; warranty card; final label trigger                    |

---

## 4. Load Bank Test MES Module — Detailed Flow

```
Inverter Serial Scanned at Z9 Entry
    │
    ▼
MES: Look up job spec — rated voltage, VA, efficiency threshold, THD limit
    │
    ▼
Load Bank Controller (OPC-UA) sends test data:
  - Output Voltage (V AC)           → MES writes to serial record
  - Output Current (A)              → MES writes
  - Output Power (VA and W)         → MES writes
  - Input Power (W)                 → MES writes
  - Efficiency η (%)                → MES writes; check ≥ threshold
  - Total Harmonic Distortion (%)   → MES writes; check ≤ limit
  - Transfer Time (UPS only, ms)    → MES writes; check ≤ 10ms
  - Thermal Hot-Spot (°C)          → MES writes; check ≤ 85°C
  - Test Duration (seconds)         → MES confirms ≥ 5 min full-load
    │
    ▼
MES Pass/Fail Gate:
  PASS → Release to Z10 Final QC; DT product twin updated with test results
  FAIL → Unit held; failure code logged; rework ticket created
    │
    ▼
Warranty Record:
  Test results + serial + firmware version + assembly date locked in MES
  Available for warranty claim investigation for 10 years
```

---

## 5. Firmware Flash & Programming Module

Every inverter, SCC, UPS, and smart power strip that contains programmable firmware must have its firmware version and flash timestamp recorded in MES.

| Product             | Programming Method         | MES Record                                | Trigger              |
|---------------------|----------------------------|-------------------------------------------|----------------------|
| Inverter            | JTAG/UART flash fixture    | FW version, flash date/time, operator ID  | At Z4 final stage    |
| Solar Charge Ctrl   | RS-485 / USB programming   | Parameter set code, FW version, serial    | Z5 programming stn   |
| UPS                 | USB firmware update        | FW version, battery data, flash timestamp | Z6 UPS station       |
| Smart Power Strip   | Wi-Fi OTA + factory config | FW version, Wi-Fi provisioning test       | Z8 power strip       |

---

## 6. Internal Supply Management

The Garage Power Electronics factory is an internal supplier to other Coo-Cah factories. MES handles this via a dedicated production order flag.

| Order Type             | Priority | MES Flag          | Routing                                       |
|------------------------|----------|-------------------|-----------------------------------------------|
| Internal — Sister Factories | 1   | `INTERNAL-PRIORITY` | Direct dispatch route to group logistics hub |
| Internal — Coo-Cah Energy (BESS) | 1 | `INTERNAL-PRIORITY` | Pre-commissioning supply for factory builds |
| Commercial — Retail    | 2        | `COMMERCIAL`      | FGW → distribution channel                   |
| Commercial — OEM/B2B   | 2        | `COMMERCIAL-OEM`  | Special packaging; OEM labels                 |

---

## 7. OEE Targets

| Line / Zone           | Phase 1 | Phase 2 | Phase 3 |
|-----------------------|---------|---------|---------|
| SMT PCB Line          | ≥ 76%   | ≥ 83%   | ≥ 88%   |
| Inverter Lines (blnd) | ≥ 68%   | ≥ 79%   | ≥ 86%   |
| Load Bank Test Bays   | ≥ 80%   | ≥ 88%   | ≥ 92%   |
| Power Tool Lines      | ≥ 72%   | ≥ 82%   | ≥ 88%   |
| Power Strip Lines     | ≥ 78%   | ≥ 85%   | ≥ 92%   |
| **Blended Factory**   | **≥ 70%** | **≥ 79%** | **≥ 87%** |

---

*Refer to [`digital-twin.md`](./digital-twin.md) for DT integration.*
*Refer to [`regulatory.md`](./regulatory.md) for IEC 62040 / IEC 61683 compliance records.*
