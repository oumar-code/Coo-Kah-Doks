# Kitchen Electronics Factory — Phase 1 Implementation Plan

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Kitchen Electronics Factory | **Location:** Agbara Industrial Estate, Lagos / Sagamu Interchange, Ogun State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Programme Management Office

---

## 1. Strategy Overview

The core strategy is **parallelise everything that has no dependency on physical equipment, compress the timeline, and be ready to connect machines the moment they land.**

All six workstreams run concurrently from Day 1 on a two-week sprint cadence. Each workstream has a designated owner and reports into the bi-weekly Programme Steering meeting.

| Workstream | Name                                  | Owner                               | Key Milestone |
|------------|---------------------------------------|-------------------------------------|---------------|
| WS1        | MES Phase 1 Deployment                | MES / Digital Manufacturing Team   | M1.4 — MES live (Q3 2025) |
| WS2        | SON / IEC Certifications & Permits    | Regulatory Affairs & Quality Team  | M1.6 — IEC 60335 + R600a permits (Q3–Q4 2025) |
| WS3        | Digital Twin — Descriptive Phase      | Digital Manufacturing & AI Team    | M2.9 — DT Phase 2 sync (Q2 2028) |
| WS4        | Workforce Training (Coo-Cah Academy)  | HR / Training Manager              | ~350 staff trained pre-production |
| WS5        | Supply Chain & Import Logistics       | Procurement & Trade Finance Team   | First container cleared; safety stock at reorder point |
| WS6        | Energy Management System (EMS)        | Energy & Infrastructure Team       | M1.9 — BESS + Solar commissioned (Q1 2026) |

---

## 2. Workstream 1 — MES Phase 1 Deployment (M1.4)

*Owner: MES / Digital Manufacturing Team*

### 2.1 Week 1–2 — Foundation

| Task | Detail |
|------|--------|
| Server provisioning | Procure/provision MES application server (on-site primary) and cloud-sync secondary (Lagos DC) |
| Edge node hardware | Stand up four edge nodes (SMT Zone, Refrigerator Line, Gas Charging / QC, SDA Lines) — hardware + OS only |
| Sandbox deployment | Deploy MES application in sandbox mode; validate licence keys and connectivity to Coo-Cah Cloud Platform |

### 2.2 Week 3–6 — Module Configuration

Configure all Phase 1 modules in sequence:

1. Production Order Management
2. WIP Tracking
3. Serial Traceability (refrigerators, microwaves, cookers, SDAs)
4. Quality Management (SPC + IPQC)
5. R600a Gas Charging Module
6. Label & Marking Control
7. AMR Fleet Dispatch
8. Energy Sub-Metering
9. CMMS

| Task | Detail |
|------|--------|
| Serial number format | Define `CCK-REF-2D-FF-AGB-25-XXXXXX` pattern in MES; seed the full product SKU register |
| User roles | Build and test all roles: Operator, Technician, Supervisor, Gas Safety Officer, QC Inspector, MES Admin, Auditor |
| Network segregation | Configure IT/OT VLAN, DMZ for ERP integration; R600a charging station isolated on dedicated OT sub-VLAN |

### 2.3 Week 7–10 — Integration Plumbing (machine-free)

Implement and test all REST/OPC-UA stub endpoints so that integration is a cable-plug, not a design exercise, when hardware arrives.

| System | Interface | Protocol |
|--------|-----------|----------|
| DEK Screen Printer | SMEMA + SECS/GEM stub | SMEMA |
| Koh Young SPI/AOI | Inspection result stub | SECS/GEM or REST |
| JUKI P&P | Placement result stub | SECS/GEM |
| R600a Charging Station | Charge weight + leak test result stub | OPC-UA |
| PU Foam Injection Machine | Injection pressure + cure time stub | OPC-UA |
| Compressor Test Rig | Cooling performance + noise level stub | OPC-UA |
| Atlas Copco Torque Station | Torque result stub (SDA assembly) | OPC-UA |

Additional integrations to complete in this window:

- MES ↔ ERP (SAP or equivalent): production orders, BOM, inventory, costing
- MES ↔ AI Platform (MQTT) and MES ↔ Digital Twin MQTT stream (dummy payloads)
- MES ↔ Garage Power Electronics MES and MES ↔ Plastics Factory MES (REST, hourly sync)
- R600a gas log report generation validated using dummy charging data (NESREA compliance readiness)

### 2.4 Week 11–12 — UAT & Go-Live Readiness

| Task | Acceptance Criterion |
|------|----------------------|
| End-to-end simulated production orders (refrigerator, microwave, SDA) | All modules pass; zero P1/P2 defects open |
| TLS 1.3 encryption validation | All MES ↔ cloud and MES ↔ machine connections verified |
| AES-256 at-rest audit | All databases and trace archives confirmed encrypted |
| Penetration test scoping | Test scope agreed with third-party firm; critical finding SLA = 30 days |

---

## 3. Workstream 2 — SON / IEC Certification & R600a Permits (M1.6)

*Owner: Regulatory Affairs & Quality Team*

> **Critical path warning:** No product may be despatched without valid SON product registration and IEC certificates. R600a handling requires a NESREA-endorsed environmental permit and licensed gas technician before any refrigerant may be stored or used on-site. Both tracks are on the critical path.

### 3.1 Week 1–2 — R600a Environmental Permit & Gas Safety Setup

| Deliverable | Content |
|-------------|---------|
| NESREA permit application | Apply for environmental permit to handle R600a (flammable hydrocarbon refrigerant) |
| Gas technician licences | Confirm NESREA-endorsed gas technician certifications for all refrigerator line gas operators |
| Gas leak detection install | Specify fixed R600a gas detectors (ATEX Zone 1) for gas charging bay |
| Emergency response plan | Gas leak emergency procedure; evacuation routes; first aid for hydrocarbon exposure |

### 3.2 Week 3–4 — IEC 60335-2-24 (Refrigerators) & SON MANCAP

| Task | Detail |
|------|--------|
| Refrigerator technical file | CCK-REF-2D-FF and CCK-REF-1D-DC — safety test per IEC 60335-1 + IEC 60335-2-24 |
| Energy label compliance | R600a charge weight label, energy consumption label per SON NIS |
| SON MANCAP application | Register CCK-REF series; pay SON fees per product category |
| Pre-compliance scan | Schedule at NTC or SONCAP-accredited lab in Lagos |

### 3.3 Week 5–6 — Microwaves (IEC 60705) & Electric Cookers (IEC 60335-2-6)

- Prepare technical files for CCK-MW-SOLO, CCK-MW-GRILL, CCK-MW-CONV (microwave radiation safety)
- Prepare technical files for CCK-EC-2IND, CCK-EC-4CONV (induction coil safety, touch interface)
- Submit all to accredited test laboratory; target certificates Q4 2025

### 3.4 Week 7–8 — Small Domestic Appliances (IEC 60335-2 sub-series)

| Product | Standard | Target Certificate |
|---------|----------|--------------------|
| CCK-BL (Blenders) | IEC 60335-2-14 | Q4 2025 |
| CCK-KT (Kettles) | IEC 60335-2-15 | Q4 2025 |
| CCK-RC (Rice Cookers) | IEC 60335-2-66 | Q4 2025 |
| CCK-TS (Toasters) | IEC 60335-2-9 | Q4 2025 |

### 3.5 Ongoing — Lab Follow-up

| Activity | Frequency | Owner |
|----------|-----------|-------|
| Lab queue position check | Weekly | Regulatory Affairs |
| SON technical clarification response | Within 5 business days of receipt | Regulatory Affairs |
| NESREA R600a compliance reporting | Quarterly (once operational) | EHS Officer |

### 3.6 Certification Schedule

| Product SKU | Standard | Target Submission | Target Certificate | Status |
|-------------|----------|-------------------|--------------------|--------|
| CCK-REF-2D-FF | IEC 60335-2-24; NIS | Q2 2025 (overdue) | Q3 2025 | Urgent |
| CCK-REF-1D-DC | IEC 60335-2-24; NIS | Q2 2025 (overdue) | Q3 2025 | Urgent |
| CCK-MW-SOLO | IEC 60705; NIS | Q3 2025 | Q4 2025 | On track |
| CCK-EC-2IND | IEC 60335-2-6; NIS | Q3 2025 | Q4 2025 | On track |
| CCK-BL, CCK-KT, CCK-RC, CCK-TS | IEC 60335-2 series | Q3 2025 | Q1 2026 | On track |

---

## 4. Workstream 3 — Digital Twin Platform (Descriptive Phase)

*Owner: Digital Manufacturing & AI Team*

*Reference: [`digital-twin.md`](./digital-twin.md) for investor showcase requirements.*

### 4.1 Week 1–2 — Platform Provisioning

| Task | Detail |
|------|--------|
| Platform deployment | Deploy Coo-Cah AI Platform Digital Twin Module (Lagos DC + on-site edge) |
| Asset registry load | Import all Phase 1 assets from `digital-twin.md` — asset IDs, zones, sensor schemas, protocols |

### 4.2 Week 3–6 — Schema & Simulation Build

| Task | Detail |
|------|--------|
| Sensor data point schemas | Define all MQTT topics, data types, engineering units, and calibration intervals |
| DES models | Build discrete-event simulation models for all use-case families (see table below) |
| BIM 3D model | Load 15,000 m² floor model using `docs/bim/zone-boundaries.md` and `docs/bim/asset-anchors.md` |

**Simulation use-case families:**

| Family | Scenarios |
|--------|-----------|
| Production Simulation | Refrigerator line ramp, SDA throughput, foam injection carousel cycle time, SMT changeover |
| Predictive Maintenance | PU foam injection carousel wear, SMT reflow oven thermal degradation, compressor test rig |
| Energy Optimisation | BESS dispatch, foam injection peak load deferral, HVAC load shift, generator run minimisation |
| Safety & Compliance | R600a gas charging failure scenario, leak dispersion model, emergency evacuation timing |

### 4.3 Week 7–10 — Investor Showcase Pack

| Evidence Theme | Deliverable |
|----------------|-------------|
| Achieved so far | Live ingestion coverage, model coverage, simulation readiness, governance controls |
| Simulation today | Demonstrable scenarios across throughput, quality, downtime, energy, and safety |
| Physical constraints | Infrastructure, equipment, integration, workforce, and compliance gaps |
| Funding translation | Ask-by-ask mapping from modelled bottleneck/risk to KPI lift and payback |

### 4.4 Week 11–12 — MES ↔ DT Integration Validation

| Test | Acceptance Criterion |
|------|----------------------|
| End-to-end MQTT streaming pipe | Functional using WS1 UAT simulated production order data |
| Synchronisation latency | ≤ 1 second confirmed in test |

---

## 5. Workstream 4 — Workforce Training (Coo-Cah Manufacturing Academy)

*Owner: HR / Training Manager*

**Target:** ~120 staff in Wave 1 (of ~350 total Phase 1 headcount)

### 5.1 Week 1–2 — Programme Setup

| Task | Detail |
|------|--------|
| Curriculum finalisation | 6-week onboarding programme; includes R600a gas safety mandatory module |
| Venue booking | Factory building (if civil works complete) or off-site |
| Trainer roster | Internal engineers + external R600a gas safety specialist, IPC, HVAC, safety specialists |

### 5.2 Week 3–14 — Wave 1 Cohort

| Weeks | Module | Content |
|-------|--------|---------|
| 3–4 | Safety Foundation | Safety induction, ESD handling, R600a gas hazard awareness, 5S, emergency procedures |
| 5–6 | MES Operations | MES system operation using deployed sandbox; gas charging module walkthrough |
| 7–8 | Quality Awareness | IEC 60335 awareness, IPC-A-610 basics, refrigerator line IPQC procedures |
| 9–10 | AMR Operations | AMR Fleet Operator training using MiR Fleet Manager in simulation mode |
| 11–12 | Role-Specific Skills | Refrigerator Line Technicians, SDA Operators, R600a Gas Technicians, MES Data Officers |

**Pre-production compliance requirement:** All R600a gas technicians must hold NESREA-endorsed certificates before handling refrigerant. All staff registered in NSITF and pension scheme before production commencement.

---

## 6. Workstream 5 — Supply Chain & Import Logistics

*Owner: Procurement & Trade Finance Team*

### 6.1 Week 1–2 — Procurement Launch

Issue RFQs and initiate purchase orders for all long-lead components:

| Component | Lead Time | Safety Stock Policy |
|-----------|-----------|---------------------|
| Compressors (Embraco/Secop/Highly) | 10–14 weeks | 6 weeks demand |
| Magnetrons (LG/Galanz) | 8–12 weeks | 4 weeks demand |
| IGBT Modules (induction cooker) | 8–10 weeks | 4 weeks demand |
| Bare PCBs | 4–6 weeks | 4 weeks demand |
| R600a Refrigerant (licensed distributor) | 4–6 weeks | 4 weeks volume |
| PU Foam Chemicals (local supplier) | 2–4 weeks | 3 weeks volume |
| SMT Consumables | 4 weeks (sea) | 3 weeks demand |

Open LCs or initiate TT payments aligned to supplier payment terms.

### 6.2 Week 2–4 — Import Compliance Setup

> **Government processing times are long — all items below must start in Week 1.**

| Action | Body | Timeline |
|--------|------|----------|
| Form M applications | CBN / Commercial Bank | Per PO |
| NAFDAC notification (compressor lubricants, foam chemicals) | NAFDAC | 4–6 weeks — start immediately |
| SON MANCAP CoC for imported components | SON | Pre-shipment per product category |
| NESREA R600a handling permit | NESREA | 6–8 weeks — start immediately |
| Licensed customs agents briefed (2 agents) | NCS-licensed agents | Week 1 |
| Apapa/Tin Can Island pre-clearance protocol agreed | Freight forwarder | Week 2 |

### 6.3 Week 3–6 — Intra-Group Coordination

| Partner | Action | SLA |
|---------|--------|-----|
| Coo-Cah Plastics Factory | Confirm plastic casing volumes for all SDA and appliance outer body SKUs; establish truck SLA | 2 runs/day |
| Coo-Cah Garage Power Electronics | Confirm inverter backup power units for factory critical load; confirm delivery schedule | Per agreed schedule |
| All partner factories | Activate hourly MES-to-MES REST sync (built in WS1) once all MES systems are live | Hourly |

### 6.4 Week 4–8 — Warehouse & Stores Setup

| Task | Detail |
|------|--------|
| Bonded stores in MES WMS | Configure bin locations for all component categories including R600a gas store (controlled area) |
| Safety stock triggers | Set reorder points per `supply-chain.md §4` policy |
| Incoming QC workflow | MES goods-receipt scan for every inbound shipment; compressor noise test at IQC |

---

## 7. Workstream 6 — Energy Management System (EMS) Configuration (M1.9)

*Owner: Energy & Infrastructure Team*

### 7.1 Week 1–2 — Software Platform Deployment

| Task | Detail |
|------|--------|
| EMS software | Deploy Sungrow iSolarCloud + Coo-Cah EMS in configuration/simulation mode |
| Site parameters | Load: 700 kWp rooftop PV, 800 kWh BESS, 500 kW grid contract, 500 kVA backup generator |

### 7.2 Week 3–4 — Operating Logic Configuration

| Rule | Detail |
|------|--------|
| BESS charge/discharge | Solar-first priority; overnight BESS discharge schedule; grid top-up thresholds |
| ATS trigger | Auto-start generator when BESS SoC < 20% + grid failure |
| PU foam injection peak load | Flag as scheduled peak consumer; optimise start time to coincide with BESS peak availability |
| Critical load tiers | Configure tiers 1–4 shed sequence including R600a gas charging bay (safety-critical, Tier 1) |

### 7.3 Week 5–6 — KPI Dashboards & Alerts

Build all energy KPI dashboards:

| KPI | Target |
|-----|--------|
| Solar Self-Sufficiency Ratio | ≥ 80% |
| Grid Import (% of total) | ≤ 20% |
| Energy Intensity — Refrigerators | ≤ 18 kWh/unit |
| Energy Intensity — Small Appliances | ≤ 2 kWh/unit |
| Energy Intensity — Microwaves | ≤ 5 kWh/unit |
| Generator Run Hours | < 100 hrs/year |
| Power Factor | ≥ 0.95 |
| BESS SoH at Year 5 | ≥ 85% |
| Annual CO₂ Avoidance | ~700 t CO₂/year |
| Unplanned Power Downtime | < 4 hrs/year |

Configure alert thresholds and escalation paths for all energy events. Validate MES ↔ EMS data exchange.

### 7.4 Week 7–8 — Simulation & Validation

| Simulation | Output |
|------------|--------|
| BESS Dispatch Optimisation | Daily solar forecast × ToU × foam injection peak load schedule |
| Factory Load Shift | AMR opportunity charging deferral; HVAC pre-cooling off-peak |
| 12-month energy cost projection | Solar+BESS vs grid-only baseline for CFO/investor reporting |

---

## 8. Cross-Cutting Governance

### 8.1 Meeting Cadence

| Cadence | Meeting | Purpose |
|---------|---------|---------|
| Weekly | Workstream stand-ups | Block removal, dependency tracking |
| Bi-weekly | Programme steering | Cross-workstream progress; milestone gating |
| Monthly | Regulatory status review | IEC/SON application status; NESREA R600a permit updates |
| Monthly | Supplier performance review | OTIF, lead time adherence, quality |

### 8.2 Key Dependencies

| Dependency | Risk | Mitigation |
|------------|------|------------|
| WS1 MES UAT must complete before WS4 staff training on MES | Training on unstable system wastes resource | Gate WS4 Week 5–6 start to WS1 sandbox passing UAT |
| NESREA R600a permit (6–8 weeks) is not in our control | Cannot charge refrigerant → zero refrigerator production | File in Week 1; no exceptions |
| NAFDAC notification (4–6 weeks) | Components blocked at customs | File in Week 1 |
| Form M applications at CBN/commercial bank | Long processing time; PO payment blocked | Initiate simultaneously with PO issue in Week 1 |
| R600a gas technician certification | Cannot operate gas charging station without certified technicians | Identify and enrol candidates in Week 1; target certification by Week 10 |

### 8.3 Programme Milestone Gate Summary

| Gate | Trigger | Key Evidence |
|------|---------|--------------|
| G1 — MES Sandbox Live | WS1 Week 2 complete | MES accessible; edge nodes online |
| G2 — MES UAT Pass | WS1 Week 12 complete | Zero P1/P2 defects; R600a gas module validated |
| G3 — IEC Applications Submitted | WS2 Week 4 complete | Lab receipts for CCK-REF-2D-FF, CCK-REF-1D-DC |
| G4 — DT Investor Pack Ready | WS3 Week 10 complete | Four scenarios demonstrable; metric dictionary locked |
| G5 — Wave 1 Training Complete | WS4 Week 14 complete | ~120 staff certified; R600a technicians certified; NSITF + pension registrations done |
| G6 — Safety Stock at Reorder Point | WS5 Week 8 complete | All categories above reorder point in MES WMS; R600a stock in controlled store |
| G7 — EMS Commissioned | WS6 Week 8 complete | EMS live in simulation; 12-month cost projection delivered |

---

*For automation phase details, refer to [`automation-roadmap.md`](./automation-roadmap.md).*
*For MES architecture and machine integration specifications, refer to [`mes-integration.md`](./mes-integration.md).*
*For regulatory requirements and IEC/R600a process detail, refer to [`regulatory.md`](./regulatory.md).*
*For energy system design, refer to [`energy-profile.md`](./energy-profile.md).*
*For supply chain logistics and safety stock policy, refer to [`supply-chain.md`](./supply-chain.md).*
*For digital twin asset registry and investor showcase requirements, refer to [`digital-twin.md`](./digital-twin.md).*
