# Coo-Cah Furniture & Home Décor Factory — MES Integration Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Furniture & Home Décor Factory | **Location:** Sagamu Industrial Estate, Ogun State, Nigeria | **Phase:** Phase 2
> **Document Version:** 1.0 | **Owner:** Smart Factory Core Team

---

## 1. MES Overview

| MES Attribute               | Value                                                              |
|-----------------------------|--------------------------------------------------------------------|
| Platform                    | Siemens Opcenter Execution (Discrete / Batch variant)              |
| Zones                       | 8–10 zones; 25–35 MES-connected workstations                       |
| Batch Traceability          | Full batch-to-raw-material traceability (NAFDAC compliance)        |
| NAFDAC eBR                  | Electronic batch records per batch; approved before shipment       |
| ERP Integration             | Bidirectional REST API                                             |
| DT Integration              | Real-time production + batch data to Coo-Cah DT Engine             |

---

## 2. MES Functional Modules

| Module                        | Function                                                             | Status  |
|-------------------------------|----------------------------------------------------------------------|---------|
| Production Order Management   | Orders from ERP; batch scheduling per recipe                        | Phase 1 |
| Recipe Management             | Master recipe versioning; change control                            | Phase 1 |
| Electronic Batch Records      | Automatic eBR; NAFDAC-grade records; operator sign-off              | Phase 1 |
| Batch / Lot Traceability      | RM lot code → batch → product lot → dispatch traceability           | Phase 1 |
| OEE                           | Per line, per zone, blended factory OEE                             | Phase 1 |
| Quality / SPC                 | In-process results; SPC; auto-hold on deviation                     | Phase 1 |
| Checkweigher Integration      | Fill weight per unit → MES; statistical distribution monitoring     | Phase 1 |
| Metal Detector Integration    | Pass/fail per unit → MES; alert on consecutive fails                | Phase 1 |
| NAFDAC CoA Module             | CoA auto-generated from batch test results; QA Manager release      | Phase 1 |
| Label Control                 | NAFDAC reg. number; SON NIS mark; batch code; expiry; MES-triggered | Phase 1 |
| Cold Chain Monitoring         | Temp sensors in FGW → MES HACCP log; alert on excursion            | Phase 1 |
| Materials Management          | BOM backflush; FIFO enforcement; AMR replenishment trigger          | Phase 1 |
| Energy Sub-Metering           | Per-zone consumption; chiller flagged as primary consumer           | Phase 1 |
| AI Vision Integration         | Fill level + label vision check results → MES per unit              | Phase 2 |
| Predictive Maintenance AI     | Valve + seal jaw PdM predictions from AI Platform                  | Phase 2 |

---

## 3. MES Zone Integration Map

| Zone | Name                      | # Stations | Integration  | Key MES Events                                              |
|------|---------------------------|------------|--------------|-------------------------------------------------------------|
| Z1   | Raw Material Store        | 3          | Barcode      | Goods receipt; lot intake; FIFO allocation; expiry tracking |
| Z2   | Primary Production        | 5–8        | OPC-UA + HMI | Process step complete; batch yield; deviations             |
| Z3   | Filling + Primary Pkg     | 4–6        | OPC-UA + HMI | Fill weight; cap torque; label check; unit count           |
| Z4   | Secondary Packaging       | 3–4        | Panel PC     | Carton weight; shrink quality; palletiser count            |
| Z5   | Finished Goods WH         | 2–3        | Barcode      | Pallet in; FIFO tracking; dispatch confirmation             |
| Z6   | Cold Storage              | 2          | BMS MQTT     | Temperature log; HACCP record; excursion alert              |
| Z8   | QC Laboratory             | 3          | LIMS REST API| Lab results to MES batch record; CoA trigger                |
| Z9   | In-Process QC             | 3          | OPC-UA + HMI | Checkweigher; metal detector; visual pass/fail              |

---

## 4. NAFDAC Compliance in MES

| NAFDAC Requirement              | MES Implementation                                                 |
|---------------------------------|--------------------------------------------------------------------|
| Batch record completeness       | All batch steps must be completed + signed in MES before batch closure |
| Raw material traceability       | RM lot code mandatory scan; batch cannot proceed without lot entry |
| QA release before dispatch      | MES shipment gate: NAFDAC CoA must be QA-approved before FGW dispatch |
| Label compliance                | MES label module checks NAFDAC reg. number is current before printing |
| Deviation management            | All out-of-spec events must have a closed investigation in MES before batch release |

---

## 5. OEE Targets

| Line                   | Phase 1 | Phase 2 | Phase 3 |
|------------------------|---------|---------|---------|
| Primary Production     | ≥ 72%   | ≥ 80%   | ≥ 86%   |
| Filling Line           | ≥ 76%   | ≥ 84%   | ≥ 90%   |
| Secondary Packaging    | ≥ 78%   | ≥ 85%   | ≥ 91%   |
| **Blended Factory**    | **≥ 72%** | **≥ 82%** | **≥ 89%** |

---

*Refer to [`digital-twin.md`](./digital-twin.md) for DT integration.*
*Refer to [`regulatory.md`](./regulatory.md) for NAFDAC eBR requirements.*
