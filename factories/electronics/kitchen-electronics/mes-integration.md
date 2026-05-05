# Kitchen Electronics Factory — MES Integration Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Kitchen Electronics Factory | **Location:** Agbara Industrial Estate, Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Smart Factory Core Team

---

## 1. MES Overview

The Kitchen Electronics Factory deploys **Siemens Opcenter Execution Discrete** as its MES platform, consistent with the Coo-Cah group-wide decision (ADR-002). The MES connects the ERP business layer to the factory floor — translating production orders into real-time work instructions for 5 distinct product families: refrigerators, microwaves, electric cookers, small domestic appliances, and PCB assemblies.

The kitchen electronics MES implementation has a unique requirement not shared by the personal electronics factory: **R600a gas charging traceability** — each unit of refrigerant charged into a unit must be recorded, the weight verified, the unit leak-tested, and the test result linked to the serial number and MES job card. This drives factory floor safety and NESREA regulatory compliance.

| MES Attribute               | Value                                                         |
|-----------------------------|---------------------------------------------------------------|
| Platform                    | Siemens Opcenter Execution Discrete (SaaS + Edge Node)        |
| Deployment Model            | Cloud SaaS (group visibility) + Edge Node (factory autonomous)|
| Production Zones            | 10 production zones, 42 MES-connected workstations            |
| Serial Traceability         | All refrigerators, microwaves, cookers, and SDAs serialised   |
| Gas Charging Integration    | R600a charging station OPC-UA → MES gas module                |
| ERP Integration             | REST API bidirectional sync with group ERP (SAP/Oracle/Odoo)  |
| Digital Twin Integration    | REST API + event streaming to Coo-Cah DT Engine               |

---

## 2. MES Functional Modules

| Module                         | Function                                                                   | Status     |
|--------------------------------|----------------------------------------------------------------------------|------------|
| Production Order Management    | Receives orders from ERP; creates production jobs per product type         | Phase 1    |
| Work Instruction Delivery      | Digital work instructions on HMI panels at each station                   | Phase 1    |
| WIP Tracking                   | Real-time tracking of each unit through every production zone              | Phase 1    |
| Serial Number / Traceability   | Unique serial assigned at Z3 (sheet metal) or Z8 (SDA build start)        | Phase 1    |
| OEE Data Collection            | Availability, Performance, Quality metrics for every production line       | Phase 1    |
| Quality (SPC + IPQC)           | Capture test results, apply SPC rules; auto-hold failing lots              | Phase 1    |
| R600a Gas Charging Module      | Record charge weight, lot code, leak test result; link to unit serial      | Phase 1    |
| Label & Marking Control        | Trigger rating plate printing; SON product registration label; barcode     | Phase 1    |
| Materials Management           | Backflush BOM; trigger replenishment to AMR; inventory visibility          | Phase 1    |
| Maintenance (CMMS-lite)        | Scheduled PM tasks; corrective maintenance tickets; MTBF tracking          | Phase 1    |
| Energy Sub-Metering            | Per-zone energy consumption; foam injection peak load alerts               | Phase 1    |
| Reporting & Analytics          | Shift reports, daily OEE, yield trends, gas usage, scrap analysis          | Phase 1    |
| Predictive Maintenance (AI)    | Integration with AI Platform for maintenance predictions (Phase 2)         | Phase 2    |

---

## 3. Production Zone MES Integration Map

| Zone | Zone Name                    | # Stations | MES Connection    | Key MES Events Captured                                              |
|------|------------------------------|------------|-------------------|----------------------------------------------------------------------|
| Z1   | Raw Material Store           | 3          | Barcode scanner   | Goods receipt, component QC scan, stock allocation to job            |
| Z2   | SMT PCB Line                 | 5          | OPC-UA full       | PCB print offset, P&P feeder counts, reflow zone temps, AOI results  |
| Z3   | Sheet Metal Fabrication      | 4          | MQTT IoT GW       | Cabinet serial stamp, press cycle count, roll-form speed             |
| Z4   | Refrigerator Assembly        | 8          | Panel PC HMI      | Assembly steps completed, torque results, foam injection parameters  |
| Z5   | R600a Gas Charging           | 4          | OPC-UA (gas ctrl) | Charge weight, lot code, pressure decay test, R600a leak test result |
| Z6   | Microwave Assembly           | 5          | Panel PC HMI      | Cavity assembly check, magnetron serial, hipot test result           |
| Z7   | Cooker Assembly              | 5          | Panel PC HMI      | Induction coil resistance test, glass seating torque, HV test result |
| Z8   | SDA Lines A, B, C            | 6          | Panel PC HMI      | Build steps, motor run test, heating element resistance, seal check  |
| Z9   | In-Process QC                | 4          | Panel PC HMI      | Noise test result (fridges), safety/hipot test result (all), visual  |
| Z10  | Final QC + OBA               | 3          | Barcode + HMI     | OBA sample results, warranty label printed, carton label triggered   |

---

## 4. R600a Gas Charging MES Module (Unique to Kitchen Electronics)

This is a safety-critical MES module unique to this factory. It ensures full traceability of every gram of R600a charged into every refrigerator unit.

```
Refrigerator Unit Serial Scanned (at Z5 Entry)
│
▼
MES R600a Module: Check Job Card Gas Spec
  (Nominal charge weight ± tolerance per model)
│
▼
Gas Charging Controller (OPC-UA) sends:
  - Actual charge weight (grams)
  - Refrigerant lot code (cylinder traceability)
  - Charging pressure (bar)
  - Cylinder ID
│
▼
MES R600a Record Written (linked to serial number):
  - Charge weight ✓
  - Lot code ✓
  - Cylinder ID ✓
│
▼
Vacuum / Leak Test Station:
  - Pressure decay test result (pass/fail)
  - Test duration (seconds)
  - Maximum pressure drop (mbar)
│
▼
MES Writes: Leak Test Result to Serial Record
│
▼
If Pass: Unit released to Compressor Performance Test (Z14)
If Fail: Unit held; rework tag printed; rework station allocated
│
▼
Compressor Performance Test (Z14) OPC-UA:
  - Power consumption (watts)
  - Cooling capacity (BTU/h)
  - Noise level (dBa)
  - All results linked to serial number in MES
│
▼
Unit Released to IPQC (Z9) — full trace chain complete
```

**Gas Usage Reporting:** MES gas module generates:
- Daily R600a consumption by model
- Running cylinder inventory (trigger reorder at < 3 cylinders)
- Monthly NESREA gas usage report (auto-generated for compliance)

---

## 5. MES API Reference

### 5.1 Inbound APIs (MES receives data FROM machines)

| Endpoint                         | Method | Source                  | Payload Description                                      |
|----------------------------------|--------|-------------------------|----------------------------------------------------------|
| `/api/v1/production/event`       | POST   | All HMI workstations    | Assembly step complete, station ID, operator ID, timestamp |
| `/api/v1/quality/result`         | POST   | All test stations       | Test type, serial number, pass/fail, test data values    |
| `/api/v1/gas/charge`             | POST   | OPC-UA Gas Charging PLC | Charge weight, lot, cylinder ID, unit serial             |
| `/api/v1/gas/leaktest`           | POST   | OPC-UA Vacuum PLC       | Pressure decay result, duration, serial                  |
| `/api/v1/oee/event`              | POST   | All production PLCs     | Downtime code, reason, zone, duration, shift             |
| `/api/v1/energy/meter`           | POST   | EMS sub-meters          | Zone, kWh reading, timestamp, 15-min interval            |
| `/api/v1/amr/event`              | POST   | MiR Fleet Manager       | AMR ID, mission ID, status, position, timestamp          |

### 5.2 Outbound APIs (MES sends data TO external systems)

| Endpoint                         | Method | Destination             | Payload Description                                      |
|----------------------------------|--------|-------------------------|----------------------------------------------------------|
| `/api/v1/erp/production-actuals` | POST   | ERP System              | Job completion, actual BoM consumption, operator hours   |
| `/api/v1/erp/inventory-update`   | POST   | ERP System              | Stock movement events, goods receipt, dispatch           |
| `/api/v1/ai/oee-stream`          | POST   | Coo-Cah AI Platform     | Real-time OEE, downtime events, production rate          |
| `/api/v1/dt/telemetry`           | POST   | Digital Twin Engine     | Machine state, sensor readings, WIP location             |
| `/api/v1/label/trigger`          | POST   | Label Printers (Zebra)  | Serial number, model, batch, SON label data              |
| `/api/v1/amr/mission`            | POST   | MiR Fleet Manager       | Mission request: from/to zones, WIP or material payload  |
| `/api/v1/safety/alert`           | POST   | EHS Dashboard + Security| Gas alarm, hipot fault, fire event, emergency stop       |

---

## 6. OEE Calculation Framework

| OEE Component  | Data Source                                | Formula Element                           |
|----------------|--------------------------------------------|-------------------------------------------|
| Availability   | MES downtime records (planned + unplanned) | (Total Time – Downtime) / Total Time      |
| Performance    | MES actual output vs. theoretical rate     | (Actual Output × Ideal Cycle Time) / Total Time |
| Quality        | IPQC + Final QC pass/fail results          | First-Pass Yield (good units/total units) |
| **OEE**        | Combined                                   | A × P × Q                                |

**OEE Targets:**

| Line / Zone              | Phase 1 Target | Phase 2 Target | Phase 3 Target |
|--------------------------|----------------|----------------|----------------|
| SMT PCB Line             | ≥ 78%          | ≥ 84%          | ≥ 88%          |
| Refrigerator Main Line   | ≥ 68%          | ≥ 78%          | ≥ 85%          |
| Gas Charging Zone        | ≥ 85%          | ≥ 90%          | ≥ 93%          |
| Microwave Line           | ≥ 72%          | ≥ 81%          | ≥ 87%          |
| Cooker Line              | ≥ 72%          | ≥ 82%          | ≥ 88%          |
| SDA Lines (blended)      | ≥ 78%          | ≥ 85%          | ≥ 92%          |
| **Factory Blended OEE**  | **≥ 72%**      | **≥ 83%**      | **≥ 90%**      |

---

## 7. Shift Reporting Structure

| Report                        | Frequency     | Recipients                           | Generated By     |
|-------------------------------|---------------|--------------------------------------|------------------|
| Shift Production Summary      | Per shift     | Factory Manager, Production Leads    | MES auto         |
| OEE Dashboard                 | Real-time     | All management; Rwanda HQ            | MES live stream  |
| Daily Quality Report          | End of day    | QA Manager, Factory Manager          | MES scheduled    |
| R600a Gas Consumption Report  | Daily         | EHS Officer, Supply Chain            | MES Gas Module   |
| Weekly OEE Trend              | Weekly        | Group Manufacturing Director         | MES + AI report  |
| Monthly NESREA Gas Report     | Monthly       | EHS Officer, Regulatory Affairs      | MES Gas Module   |

---

*For digital twin integration, refer to [`digital-twin.md`](./digital-twin.md).*
*For regulatory compliance links, refer to [`regulatory.md`](./regulatory.md).*
