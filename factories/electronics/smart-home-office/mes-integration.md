# Smart Home & Office Electronics Factory — MES Integration Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Smart Home & Office Electronics Factory | **Location:** Agbara Industrial Estate, Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Smart Factory Core Team

---

## 1. MES Overview

The Smart Home & Office factory deploys **Siemens Opcenter Execution Discrete** with a multi-product traceability configuration covering Smart TVs (including Android TV GMS compliance), laptops, routers, smart speakers, home automation hubs, and projectors. The NCC Type Approval tracking module (identical to Personal Electronics) is mandatory — all wireless products require TA certification before MES will permit shipment.

| MES Attribute              | Value                                                           |
|----------------------------|-----------------------------------------------------------------|
| Platform                   | Siemens Opcenter Execution Discrete (SaaS + Edge Node)          |
| Production Zones           | 10 zones; 46 MES-connected workstations                         |
| Serial Traceability        | All products serialised; battery lot traceability for laptops   |
| NCC TA Module              | All wireless products require TA certificate in MES before shipment |
| Android TV GMS Module      | Google CDD compliance test result linked to TV serial           |
| ERP Integration            | Bidirectional REST API to group ERP                             |

---

## 2. MES Functional Modules

| Module                      | Function                                                              | Status  |
|-----------------------------|-----------------------------------------------------------------------|---------|
| Production Order Management | Multi-product orders across 5+ product families                      | Phase 1 |
| Work Instruction Delivery   | Digital WI per product type; screen size routing at TV lines         | Phase 1 |
| WIP Tracking                | All units tracked from PCB sub-assy through final QC                 | Phase 1 |
| Serial / Lot Traceability   | Every unit serialised; TV display serial linked to chassis serial    | Phase 1 |
| OEE Data Collection         | Per line, per zone, factory blended                                   | Phase 1 |
| Quality (SPC + IPQC)        | Test results captured; SPC control rules applied; auto-hold          | Phase 1 |
| NCC TA Compliance Module    | TA certificate loaded per SKU; shipment blocked if TA not current    | Phase 1 |
| Android TV GMS Module       | CDD compliance test result (PASS/FAIL + GMS version) per TV serial  | Phase 1 |
| Laptop Battery Traceability | Battery cell lot code, manufacture date, charge cycle count recorded | Phase 1 |
| RF Test Data Capture        | Wi-Fi/BT/LTE test results (where applicable) per serial             | Phase 1 |
| Screen Bonding Params       | UV cure time, lamp intensity, pressure recorded per unit             | Phase 1 |
| Firmware Flash Tracking     | FW version + hash for all programmable products                      | Phase 1 |
| Label Control               | NCC TA mark, SON NIS mark, serial barcode, model, energy rating     | Phase 1 |
| Materials Management        | BOM backflush; display panel inventory visual; AMR replenishment     | Phase 1 |
| Energy Sub-Metering         | Per zone; dual SMT oven load as primary consumer                     | Phase 1 |

---

## 3. Production Zone MES Integration Map

| Zone | Name                        | # Stations | Connection     | Key MES Events                                                      |
|------|-----------------------------|------------|----------------|---------------------------------------------------------------------|
| Z1   | Raw Material Store          | 3          | Barcode        | Goods receipt; display panel batch intake; allocation to job        |
| Z2   | SMT Line 1                  | 5          | OPC-UA full    | Print offset; feeder; reflow temps; AOI results                     |
| Z3   | SMT Line 2                  | 5          | OPC-UA full    | Same as Z2 — laptop/router/hub PCBs                                 |
| Z4   | Screen Bonding              | 5          | OPC-UA+HMI     | Panel serial scan; UV cure time; pressure; cure temp; bond pass/fail|
| Z5   | Smart TV Assembly           | 8          | Panel PC HMI   | Assembly steps; backlight test; HDMI port check; remote pairing     |
| Z6   | Laptop Assembly             | 6          | Panel PC HMI   | Keyboard test; touchpad calibration; battery SN; display brightness |
| Z7   | Router + Hub Assembly       | 5          | Panel PC HMI   | RF functional test; Wi-Fi throughput; firmware version              |
| Z8   | Speaker + Projector         | 5          | Panel PC HMI   | Acoustic test (SPL, THD); projector lumen output; lens calibration  |
| Z9   | RF + NCC Test Zone          | 4          | REST API       | Full RF test report; TA certificate check; NCC mark confirmed       |
| Z10  | IPQC + Final QC             | 5          | Barcode + HMI  | Visual pass; AI cosmetic score; Android TV boot screen confirmed    |

---

## 4. Android TV GMS Compliance Module

All Coo-Cah Smart TVs ship with Android TV (Google Mobile Services). The MES Android TV module ensures every unit is tested for Google CDD compliance before shipment.

```
TV Serial Scanned at Z5 (Firmware Flash Station)
    │
    ▼
Android TV CDD Test Station (automated):
  - ADB shell test suite runs (Google-certified test tool)
  - GMS version verified
  - All required apps (Play Store, Netflix pre-auth) installed
  - Resolution + HDR metadata validated
    │
    ▼
MES Writes to TV Serial Record:
  - CDD test result: PASS / FAIL
  - GMS version deployed
  - FW hash + build ID
  - Test timestamp
    │
    ▼
PASS: TV released to IPQC (Z10)
FAIL: Unit held; engineering investigation triggered; no shipment
```

---

## 5. Key OEE Targets

| Line / Zone           | Phase 1 | Phase 2 | Phase 3 |
|-----------------------|---------|---------|---------|
| SMT Lines (blended)   | ≥ 78%   | ≥ 84%   | ≥ 89%   |
| TV Assembly Lines     | ≥ 68%   | ≥ 79%   | ≥ 86%   |
| Screen Bonding        | ≥ 75%   | ≥ 85%   | ≥ 91%   |
| Laptop Line           | ≥ 70%   | ≥ 80%   | ≥ 87%   |
| Router / Hub Lines    | ≥ 80%   | ≥ 87%   | ≥ 93%   |
| Speaker / Projector   | ≥ 78%   | ≥ 85%   | ≥ 91%   |
| **Blended Factory**   | **≥ 72%** | **≥ 82%** | **≥ 89%** |

---

*Refer to [`digital-twin.md`](./digital-twin.md) for DT integration specifics.*
*Refer to [`regulatory.md`](./regulatory.md) for NCC TA and Android CDD requirements.*
