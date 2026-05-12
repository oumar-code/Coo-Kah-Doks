# Kitchen Electronics Factory — Phase 1 Implementation Plan

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Kitchen Electronics Factory | **Location:** Agbara Industrial Estate, Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Programme Management Office

---

## 1. Strategy Overview

The core strategy is **parallelise everything that has no dependency on physical equipment, compress the timeline, and be ready to connect machines the moment they land.** The Kitchen Electronics Factory has a unique complexity over other Coo-Cah factories: the R600a gas handling system requires regulatory permits (NESREA) and a dedicated safety commissioning procedure before the refrigerator line can produce any unit. This is the single biggest gating item on the critical path.

All six workstreams run concurrently from Day 1 on a two-week sprint cadence. Each workstream has a designated owner and reports into the bi-weekly Programme Steering meeting.

| Workstream | Name                                      | Owner                                | Key Milestone |
|------------|-------------------------------------------|--------------------------------------|---------------|
| WS1        | MES Phase 1 Deployment                    | MES / Digital Manufacturing Team    | M1.4 — MES live (Q4 2025) |
| WS2        | SON / IEC 60335 / NESREA Regulatory       | Regulatory Affairs & EHS Team       | M1.7 — SON NIS certificates + NESREA gas permit (Q2 2026) |
| WS3        | Digital Twin — Descriptive Phase          | Digital Manufacturing & AI Team     | DT live sync (Phase 2, Q3 2028) |
| WS4        | Workforce Training (Coo-Cah Academy)      | HR / Training Manager               | ~350 staff trained pre-production |
| WS5        | Supply Chain & Import Logistics           | Procurement & Trade Finance Team    | Long-lead safety stock at reorder point |
| WS6        | Energy Management System (EMS)            | Energy & Infrastructure Team        | M1.6 — Solar + BESS commissioned (Q1 2026) |

---

## 2. Workstream 1 — MES Phase 1 Deployment

*Owner: MES / Digital Manufacturing Team*

### 2.1 Week 1–2 — Foundation

| Task | Detail |
|------|--------|
| Server provisioning | Procure/provision MES edge node for factory (on-site primary) + cloud-sync (Lagos DC) |
| Edge node hardware | Stand up edge nodes: SMT Zone, Refrigerator Line, SDA Lines, Gas Charging Zone — hardware + OS only |
| Sandbox deployment | Deploy Siemens Opcenter Execution Discrete in sandbox mode; validate licence keys and connectivity to Coo-Cah Cloud Platform |

### 2.2 Week 3–6 — Module Configuration

Configure all Phase 1 MES modules in sequence:

1. Production Order Management
2. WIP Tracking + Traceability
3. R600a Gas Charging Module *(unique to this factory)*
4. Quality Management (SPC + IPQC)
5. OEE Data Collection
6. AMR Fleet Dispatch
7. Energy Sub-Metering
8. Label & Marking Control (SON NIS marks)
9. CMMS (Maintenance)

| Task | Detail |
|------|--------|
| Serial number format | Define `CCK-REF-2D-AGB-25-XXX-XXXXXX` pattern in MES; seed full product SKU register for all 11 product lines |
| Gas charge traceability | Configure R600a charge weight, lot code, cylinder ID linkage to unit serial number |
| User roles | Build and test all roles: Operator, Gas Technician, Supervisor, Engineer, QA, Admin, EHS, Auditor |
| Network segregation | Configure IT/OT VLAN; DMZ for ERP integration; ATEX zone connectivity plan |

### 2.3 Week 7–10 — Integration Plumbing (machine-free)

Implement and test all REST/OPC-UA stub endpoints so that integration is a cable-plug, not a design exercise, when hardware arrives.

| System | Interface | Protocol |
|--------|-----------|----------|
| DEK Horizon Paste Printer | SMEMA + OPC-UA stub | OPC-UA |
| JUKI RX-7R Pick-and-Place | Placement result stub | OPC-UA |
| Heller 1964 MK5 Reflow Oven | Zone temperature stream stub | OPC-UA |
| Koh Young AOI KY8030-3 | Vision result stub | OPC-UA + REST |
| PU Foam Injection Machine | Thermal + carousel state stub | OPC-UA + MQTT |
| R600a Gas Charging Controller | Charge weight + leak test stub | OPC-UA |
| Compressor Performance Test Rig | Power + noise + cooling stub | OPC-UA |
| Cabinet Roll-Form + Welding Line | Kinematic state stub | MQTT IoT GW |
| MiR Fleet Manager | AMR position + mission stub | REST API |

Additional integrations to complete:
- MES ↔ ERP (SAP/Oracle/Odoo): production orders, BOM, inventory, costing
- MES ↔ AI Platform (MQTT) and MES ↔ Digital Twin MQTT stream (dummy payloads)
- MES ↔ Coo-Cah Plastics Factory MES (REST, hourly sync)
- MES Gas Module monthly NESREA report generation validated using dummy charge data

### 2.4 Week 11–12 — UAT & Go-Live Readiness

| Task | Acceptance Criterion |
|------|----------------------|
| End-to-end simulated production orders (refrigerators + SDAs) | All modules pass; zero P1/P2 defects open |
| R600a gas module end-to-end trace | Charge weight → lot code → leak test → serial record in MES |
| TLS 1.3 encryption validation | All MES ↔ cloud and MES ↔ machine connections verified |
| Penetration test scoping | Test scope agreed with third-party firm; gas zone OT safe-harbour procedure signed off |

---

## 3. Workstream 2 — SON / IEC 60335 / NESREA Regulatory Compliance

*Owner: Regulatory Affairs & EHS Team*

> **Critical path warning:** No kitchen appliance may be despatched without valid SON NIS registration. The R600a gas charging station cannot be commissioned without a valid NESREA licence. Both require 4–12 weeks of processing outside Coo-Cah's control. All applications must start in Week 1.

### 3.1 Week 1–2 — IEC 60335 Technical File Preparation (Priority Products)

Priority: Refrigerators (IEC 60335-2-24) and Microwaves (IEC 60335-2-25) as these have the longest certification timelines.

| Deliverable | Content |
|-------------|---------|
| Dielectric strength test procedure | Hipot test spec for all 11 product lines |
| Leakage current spec | Maximum leakage current per model class |
| Temperature rise test plan | Representative sample test plan per IEC 60335-1 |
| R600a gas circuit design review | Review against IEC 60335-2-24 gas circuit safety requirements |
| Declaration of Conformity template | Signed by Regulatory Affairs Lead per product line |

### 3.2 Week 3–4 — NESREA R600a Permit Application (Critical Path)

| Task | Detail |
|------|--------|
| EIA Gas Handling Chapter | Submit factory EIA gas handling chapter to NESREA for approval |
| ODS Licence application | Apply for NESREA ODS (Ozone Depleting Substances) Licence |
| Refrigerant Handling Licence | Apply for NESREA + DPR Refrigerant Handling Licence |
| Lagos State Hazardous Substance Permit | Submit to Lagos State Environment Ministry |
| Gas detection system documentation | Submit gas detector spec sheet, layout, and alarm thresholds to NESREA |
| Staff certification roster | Identify and schedule 4 technicians for NESREA refrigerant handling certification |

### 3.3 Week 5–6 — SON NIS Pre-Compliance + Application

| Task | Detail |
|------|--------|
| Pre-compliance testing | Schedule IEC 60335 pre-compliance testing at SON-accredited lab (Intertek Lagos or NNPC Metrology Lab) for refrigerators + microwaves |
| SON MANCAP portal submission | Submit NIS registration applications for all Phase 1 SKUs |
| Application fees | Submit per-product application fees to SON |
| Small appliance files | Prepare IEC 60335-2-14/15/78/9 technical files for SDA product lines |

### 3.4 Week 7–8 — Cooker and SDA Applications + Ongoing

| Task | Detail |
|------|--------|
| Induction cooker technical file | IEC 60335-2-6; EMC assessment for induction field |
| NAFDAC food-contact registration | Register food-contact plastic components (liners, SDA containers) |
| Pioneer Status application | Submit to NIPC for 5-year CIT holiday |

### 3.5 SON NIS Certification Schedule

| Product Category               | Applicable Standard              | Target Submission | Target Certificate | Status   |
|--------------------------------|----------------------------------|-------------------|--------------------|----------|
| Refrigerators (all models)     | NIS ISO 15502 / IEC 60335-2-24   | Q4 2025           | Q2 2026            | In prep  |
| Microwave Ovens (all variants) | NIS 120 / IEC 60335-2-25         | Q4 2025           | Q2 2026            | In prep  |
| Electric Cookers               | NIS / IEC 60335-2-6              | Q1 2026           | Q3 2026            | Planned  |
| Small Domestic Appliances      | NIS / IEC 60335-2-14/15/78/9     | Q1 2026           | Q3 2026            | Planned  |

### 3.6 NESREA Permit Schedule

| Permit                                | Authority                | Target Date | Status   |
|---------------------------------------|--------------------------|-------------|----------|
| EIA Gas Handling Chapter Approval     | NESREA                   | Q1 2026     | In prep  |
| ODS Licence                           | NESREA                   | Q1 2026     | In prep  |
| Refrigerant Handling Licence          | NESREA + DPR             | Q1 2026     | In prep  |
| Lagos State Hazardous Substance Permit| Lagos State Env. Ministry | Q2 2026    | Planned  |
| R600a Gas Station Commissioning Cert  | EHS Officer sign-off     | Q2 2026     | Planned  |

---

## 4. Workstream 3 — Digital Twin Platform (Descriptive Phase)

*Owner: Digital Manufacturing & AI Team*

*Reference: [`digital-twin.md`](./digital-twin.md) for asset registry and simulation use cases.*

### 4.1 Week 1–2 — Platform Provisioning

| Task | Detail |
|------|--------|
| Platform deployment | Deploy Coo-Cah AI Platform Digital Twin Module (Lagos DC + on-site edge) |
| Asset registry load | Import all Phase 1 assets from `digital-twin.md` §3 — asset IDs, zones, sensor schemas, protocols |

### 4.2 Week 3–6 — Schema & Simulation Build

| Task | Detail |
|------|--------|
| Sensor data point schemas | Define all OPC-UA/MQTT topics, data types, engineering units, and calibration intervals for ~190 pre-declared sensor points |
| Foam injection thermal model | Build thermal physics model for PU foam injection carousel (foam density, cure time, insulation performance) |
| R600a gas dispersion model | Build gas dispersion simulation for Z5 leak scenarios (ventilation adequacy validation) |
| Energy peak demand model | Build foam injection demand spike model; BESS dispatch simulation |
| BIM spatial model | Load 15,000 m² floor model using `docs/bim/zone-boundaries.md` and `docs/bim/asset-anchors.md` |

**Simulation use-case families:**

| Family | Scenarios |
|--------|-----------|
| Thermal Process Simulation | Foam injection profile, reflow oven zone drift, compressor test correlation |
| Gas Safety Simulation | R600a leak dispersion plumes; evacuation time modelling; ventilation adequacy |
| Energy Optimisation | BESS dispatch; foam injection demand spike mitigation; solar self-sufficiency |
| Predictive Maintenance | Reflow oven thermal zone drift; foam injection carousel bearing wear; compressor test MTBF |

### 4.3 Week 7–10 — Gas Safety DT Validation

A unique requirement for this factory: validate the Gas Safety simulation module against known R600a dispersion data before commissioning.

| Task | Acceptance Criterion |
|------|----------------------|
| Dispersion model calibration | Model output within ±15% of ASHRAE/IEC reference data for equivalent ventilation rates |
| Evacuation scenario validated | Time-to-safe-concentration modelled for all 12 gas detector locations in Z5 |
| EHS Officer sign-off | EHS Officer reviews and accepts simulation as fit for emergency response planning |

### 4.4 Week 11–12 — MES ↔ DT Integration Validation

| Test | Acceptance Criterion |
|------|----------------------|
| End-to-end MQTT streaming pipe | Functional using WS1 UAT simulated production order data |
| Synchronisation latency | ≤ 30 seconds confirmed in test (real-time monitoring target ≤ 5 seconds at Phase 2 live) |

---

## 5. Workstream 4 — Workforce Training (Coo-Cah Manufacturing Academy)

*Owner: HR / Training Manager*

**Target:** ~120 staff in Wave 1 (of 350 total Phase 1 headcount)

### 5.1 Week 1–2 — Programme Setup

| Task | Detail |
|------|--------|
| Curriculum finalisation | 6-week onboarding programme; includes mandatory R600a safety module for all factory staff |
| Venue booking | Factory building (if civil works complete) or off-site Agbara area |
| Trainer roster | Internal engineers + external ESD, IPC, R600a safety, ATEX, and food-safety specialists |

### 5.2 Week 3–14 — Wave 1 Cohort

| Weeks | Module | Content |
|-------|--------|---------|
| 3–4 | Safety Foundation | Safety induction, R600a gas handling awareness, ATEX zone awareness, 5S, emergency procedures, Factories Act rights |
| 5–6 | MES Operations | MES system operation using deployed sandbox (WS1 output); R600a Gas Module for technicians |
| 7–8 | Quality Awareness | IEC 60335 compliance basics, SON NIS certification requirements, IPQC procedures, foam QC |
| 9–10 | AMR Operations | AMR Fleet Operator training using MiR Fleet Manager in simulation mode |
| 11–12 | Role-Specific Skills | Separate tracks: SMT Operators, Refrigerator Line Technicians, Gas Charging Technicians, SDA Operators, QC Inspectors |

**Pre-production compliance:**
- All staff registered in NSITF (workers' compensation) and pension scheme before production commencement.
- All gas charging technicians must hold NESREA refrigerant handling certification before working in Z5.

---

## 6. Workstream 5 — Supply Chain & Import Logistics

*Owner: Procurement & Trade Finance Team*

### 6.1 Week 1–2 — Procurement Launch

Issue RFQs and initiate purchase orders for all long-lead components:

| Component | Lead Time | Safety Stock Policy |
|-----------|-----------|---------------------|
| Refrigerator Compressors (Brazil/Slovakia) | 18–28 days sea | 60 days demand |
| Magnetrons (China) | 22–28 days sea | 45 days demand |
| IGBT Modules (Germany/China) | 8–10 weeks | 60 days demand |
| Tempered Glass (China) | 22–28 days sea | 30 days demand |
| SMT Components (passive, ICs) | 28–35 days sea | 30 days demand |
| Bare PCBs (China/Taiwan) | 24–30 days sea | 30 days demand |
| R600a Refrigerant | 4–6 weeks (licensed) | 30 days demand |
| PU Foam System (polyol + isocyanate) | 2–4 weeks | 21 days demand |

### 6.2 Week 2–4 — Import Compliance Setup

> **Government processing times are long — all items below must start in Week 1.**

| Action | Body | Timeline |
|--------|------|----------|
| Form M applications (per PO) | CBN / Commercial Bank | Per PO — initiate immediately |
| SON Conformity Assessment (CoC) | SON | 4–8 weeks pre-shipment |
| NAFDAC notification (R600a, polyol/isocyanate) | NAFDAC | 4–6 weeks — start immediately |
| Licensed customs agents briefed (2 agents) | NCS-licensed agents | Week 1 |
| Tin Can Island pre-clearance protocol agreed | Tin Can / freight forwarder | Week 2 |

### 6.3 Week 3–6 — Intra-Group Coordination

| Partner | Action | SLA |
|---------|--------|-----|
| Coo-Cah Plastics Factory | Confirm daily volumes for all 5 casing/liner types; establish 2× daily shuttle SLA | As per `docs/intragroup-supply-coordination.md` |
| Coo-Cah Garage Power Electronics | Deliver UPS (8 units) + ATEX inverters (4 units) + smart PDUs (2 units) | Per commissioning schedule |
| Both partner factories | Activate hourly MES-to-MES REST sync once both MES systems are live | Hourly |

### 6.4 Week 4–8 — Warehouse & Stores Setup

| Task | Detail |
|------|--------|
| Bonded stores in MES WMS | Configure bin locations for all component categories in Z1 |
| R600a cylinder bay setup | Configure MES Gas Module cylinder tracking; serial-numbered cylinder bay slots |
| Safety stock triggers | Set reorder points per `supply-chain.md` §4 policy |
| Incoming QC workflow | Set up MES goods-receipt scan for every inbound shipment |

---

## 7. Workstream 6 — Energy Management System (EMS) Configuration

*Owner: Energy & Infrastructure Team*

### 7.1 Week 1–2 — Software Platform Deployment

| Task | Detail |
|------|--------|
| EMS software | Deploy Sungrow iSolarCloud + Coo-Cah EMS in configuration/simulation mode |
| Site parameters | Load: 700 kWp PV, 800 kWh BESS (LFP), 500 kW peak demand, 500 kVA backup generator |
| Foam injection integration | Configure 5-second demand monitoring on foam injection machine sub-meter |

### 7.2 Week 3–4 — Operating Logic Configuration

| Rule | Detail |
|------|--------|
| BESS charge/discharge | Solar-first priority; overnight BESS discharge schedule; grid top-up thresholds |
| Foam injection peak mitigation | Auto BESS discharge trigger when foam injection machine start detected; 45 kW spike absorption |
| ATS trigger | Auto-start generator when BESS SoC < 20% + grid failure |
| Critical load tiers | Configure tier 1–4 shed sequence: Tier 1 = R600a gas zone ventilation (never shed) |
| ToU tariff management | AMI smart meter integration for time-of-use optimisation |

### 7.3 Week 5–6 — KPI Dashboards & Alerts

Build all energy KPI dashboards:

| KPI | Target |
|-----|--------|
| Solar Self-Sufficiency Ratio | ≥ 80% |
| Grid Import (% of total) | ≤ 20% |
| Energy Intensity — Refrigerator | ≤ 18 kWh/unit |
| Energy Intensity — Small Appliances | ≤ 2 kWh/unit |
| Generator Run Hours | < 120 hrs/year |
| Power Factor | ≥ 0.95 |
| BESS SoH at Year 5 | ≥ 85% |
| Annual CO₂ Avoidance | ~700 t CO₂/year |
| Foam Injection Demand Spike Absorbed | ≥ 95% spikes absorbed by BESS |
| R600a Zone Ventilation Uptime | 100% (never interrupted) |

### 7.4 Week 7–8 — Simulation & Validation

| Simulation | Output |
|------------|--------|
| BESS Dispatch Optimisation | Daily solar forecast × ToU × foam injection load profile |
| R600a Zone Ventilation Resilience | Confirm ventilation BESS backup ≥ 4 hours on battery alone |
| 12-month energy cost projection | Solar+BESS vs grid-only baseline for CFO/investor reporting |

---

## 8. Cross-Cutting Governance

### 8.1 Meeting Cadence

| Cadence | Meeting | Purpose |
|---------|---------|---------|
| Weekly | Workstream stand-ups | Block removal, dependency tracking |
| Bi-weekly | Programme steering | Cross-workstream progress; milestone gating |
| Monthly | Regulatory status review | SON NIS + NESREA application status; ATEX compliance |
| Monthly | Supplier performance review | OTIF, lead time adherence, quality |
| Monthly | Gas Safety review | R600a permit progress; commissioning readiness |

### 8.2 Key Dependencies

| Dependency | Risk | Mitigation |
|------------|------|------------|
| NESREA R600a permits required before gas charging zone can operate | No refrigerators can be produced until permits in hand | File NESREA application in Week 1; designate Regulatory Affairs lead as single point of contact |
| SON lab queue (4–8 weeks per product) | Certificates delayed → zero refrigerator/appliance revenue | Submit all applications in Week 1; pre-arrange with SON-accredited lab |
| NAFDAC chemical import notification (4–6 weeks) | R600a and PU foam components blocked at customs | File in Week 1; no exceptions |
| Form M processing time at CBN/commercial bank | PO payments blocked | Initiate simultaneously with PO issue in Week 1 |
| WS1 MES UAT must complete before WS4 staff training on MES | Training on unstable system wastes resource | Gate WS4 Week 5–6 start to WS1 sandbox passing UAT |
| Coo-Cah Plastics Factory casing supply | Microwave + SDA lines cannot start without casings | Daily MES visibility from Week 3; 7-day buffer stock target |

### 8.3 Programme Milestone Gate Summary

| Gate | Trigger | Key Evidence |
|------|---------|--------------|
| G1 — MES Sandbox Live | WS1 Week 2 complete | MES accessible; edge nodes online |
| G2 — MES UAT Pass | WS1 Week 12 complete | Zero P1/P2 defects; all machine stubs passing |
| G3 — NESREA Applications Submitted | WS2 Week 4 complete | EIA chapter + ODS licence + Refrigerant Handling Licence applications lodged |
| G4 — SON NIS Applications Submitted | WS2 Week 6 complete | All product lines submitted to SON MANCAP portal |
| G5 — Gas Safety DT Validated | WS3 Week 10 complete | EHS Officer sign-off on R600a dispersion model |
| G6 — Wave 1 Training Complete | WS4 Week 14 complete | ~120 staff certified; all gas technicians NESREA-certified |
| G7 — Safety Stock at Reorder Point | WS5 Week 8 complete | All categories above reorder point in MES WMS |
| G8 — EMS Commissioned | WS6 Week 8 complete | EMS live in simulation; 12-month cost projection delivered |

---

*For automation phase details, refer to [`automation-roadmap.md`](./automation-roadmap.md).*
*For MES architecture and machine integration specifications, refer to [`mes-integration.md`](./mes-integration.md).*
*For regulatory requirements (SON NIS, NESREA, IEC 60335), refer to [`regulatory.md`](./regulatory.md).*
*For energy system design, refer to [`energy-profile.md`](./energy-profile.md).*
*For supply chain logistics and safety stock policy, refer to [`supply-chain.md`](./supply-chain.md).*
*For digital twin asset registry and simulation use cases, refer to [`digital-twin.md`](./digital-twin.md).*
*For gap closure tracking, refer to [`docs/gap-closure-report.md`](./docs/gap-closure-report.md).*
