# Garage & Power Electronics Factory — Phase 1 Implementation Plan

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Garage & Power Electronics Factory | **Location:** Sagamu Industrial Estate, Ogun State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Programme Management Office

---

## 1. Strategy Overview

The core strategy is **parallelise everything that has no dependency on physical equipment, compress the timeline, and be ready to connect machines the moment they land.**

All six workstreams run concurrently from Day 1 on a two-week sprint cadence. Each workstream has a designated owner and reports into the bi-weekly Programme Steering meeting.

| Workstream | Name                                  | Owner                               | Key Milestone |
|------------|---------------------------------------|-------------------------------------|---------------|
| WS1        | MES Phase 1 Deployment                | MES / Digital Manufacturing Team   | M1.4 — MES live (Q3 2025) |
| WS2        | SON / IEC Certifications              | Regulatory Affairs & Quality Team  | M1.6 — IEC 62040 + IEC 61683 certificates (Q3–Q4 2025) |
| WS3        | Digital Twin — Descriptive Phase      | Digital Manufacturing & AI Team    | M2.9 — DT Phase 2 sync (Q2 2028) |
| WS4        | Workforce Training (Coo-Cah Academy)  | HR / Training Manager              | ~280 staff trained pre-production |
| WS5        | Supply Chain & Import Logistics       | Procurement & Trade Finance Team   | First container cleared; safety stock at reorder point |
| WS6        | Energy Management System (EMS)        | Energy & Infrastructure Team       | M1.9 — BESS + Solar commissioned (Q1 2026) |

---

## 2. Workstream 1 — MES Phase 1 Deployment (M1.4)

*Owner: MES / Digital Manufacturing Team*

### 2.1 Week 1–2 — Foundation

| Task | Detail |
|------|--------|
| Server provisioning | Procure/provision MES application server (on-site primary) and cloud-sync secondary (Lagos DC) |
| Edge node hardware | Stand up the three edge nodes (SMT Zone, Inverter Assembly, Load Bank Test) — hardware + OS only |
| Sandbox deployment | Deploy MES application in sandbox mode; validate licence keys and connectivity to Coo-Cah Cloud Platform |

### 2.2 Week 3–6 — Module Configuration

Configure all Phase 1 modules in sequence:

1. Production Order Management (with internal supply order priority flagging)
2. WIP Tracking
3. Serial Traceability (inverter, SCC, UPS, power tools)
4. Quality Management
5. Load Bank Test Module
6. Firmware Flash Tracking
7. AMR Fleet Dispatch
8. Energy Sub-Metering
9. CMMS

| Task | Detail |
|------|--------|
| Serial number format | Define `CCG-INV-PSW-SAG-25-XXXXXX` pattern in MES; seed the full product SKU register |
| User roles | Build and test all roles: Operator, Technician, Supervisor, Test Engineer, Admin, Auditor |
| Network segregation | Configure IT/OT VLAN, DMZ for ERP integration; load bank test network isolated on OT VLAN |

### 2.3 Week 7–10 — Integration Plumbing (machine-free)

Implement and test all REST/OPC-UA stub endpoints so that integration is a cable-plug, not a design exercise, when hardware arrives.

| System | Interface | Protocol |
|--------|-----------|----------|
| DEK Screen Printer | SMEMA + SECS/GEM stub | SMEMA |
| Koh Young SPI/AOI | Inspection result stub | SECS/GEM or REST |
| JUKI P&P | Placement result stub | SECS/GEM |
| Load Bank Test Rig | Electrical test result stub (V, A, eff, THD, transfer time) | OPC-UA |
| Transformer Winding Machine | Motor torque + winding tension stub | OPC-UA |
| Firmware Programming Station | Firmware version + hash stub | REST API |
| Atlas Copco Torque Station | Torque result stub (power tool assembly) | OPC-UA |

Additional integrations to complete in this window:

- MES ↔ ERP (SAP or equivalent): production orders, BOM, inventory, costing
- MES ↔ AI Platform (MQTT) and MES ↔ Digital Twin MQTT stream (dummy payloads)
- MES ↔ Personal Electronics MES and MES ↔ Kitchen Electronics MES (REST, hourly sync — internal supply orders)
- Load bank test report generation validated using dummy electrical test data

### 2.4 Week 11–12 — UAT & Go-Live Readiness

| Task | Acceptance Criterion |
|------|----------------------|
| End-to-end simulated production orders (inverter, SCC, power tool) | All modules pass; zero P1/P2 defects open |
| TLS 1.3 encryption validation | All MES ↔ cloud and MES ↔ machine connections verified |
| AES-256 at-rest audit | All databases and trace archives confirmed encrypted |
| Penetration test scoping | Test scope agreed with third-party firm; critical finding SLA = 30 days |

---

## 3. Workstream 2 — SON / IEC Certification Programme (M1.6)

*Owner: Regulatory Affairs & Quality Team*

> **Critical path warning:** No product may be despatched without valid SON product registration and applicable IEC test certificates. Lab queue times are 4–12 weeks and are outside the team's control. Submit applications immediately.

### 3.1 Week 1–2 — Technical File Preparation (IEC 62040 — UPS)

| Deliverable | Content |
|-------------|---------|
| UPS technical file | Circuit diagrams, efficiency test data, battery compatibility matrix |
| Transfer time documentation | Measured transfer time ≤ 10 ms per IEC 62040-3 |
| EMC pre-scan report | Conducted/radiated emissions within CISPR 22 Class B limits |
| User manual draft | Per SON/IEC labelling guidance |
| Declaration of Conformity | Signed by Regulatory Affairs lead |

### 3.2 Week 3–4 — IEC 61683 (Solar Charge Controllers) & SON Registration

| Task | Detail |
|------|--------|
| SCC efficiency test | MPPT efficiency ≥ 98% at rated current; submit to accredited lab |
| PWM SCC test | Verify charge algorithm correctness per IEC 61683 §5 |
| SON MANCAP application | Register all inverter, SCC, and UPS SKUs under NIS 62040 / NIS 61683 |
| Application fees | Pay SON fees per product category |

### 3.3 Week 5–6 — Power Tools (IEC 62841)

- Prepare technical files for CCG-PT-DRILL, CCG-PT-AG, CCG-PT-CS
- IEC 62841-2 mechanical safety tests for grinder and circular saw
- Double-insulation verification for all corded tools

### 3.4 Week 7–8 — UPS Line Interactive & Solar Panel Kits

| Task | Detail |
|------|--------|
| CCG-UPS Line Interactive | IEC 62040-1 safety + IEC 62040-3 performance |
| CCG-SPK Solar Kit | Verify panel spec against IEC 61215; packaging and import marking |
| NESREA registration | Register as electronic equipment producer under Extended Producer Responsibility |

### 3.5 Ongoing — Lab Follow-up

| Activity | Frequency | Owner |
|----------|-----------|-------|
| Lab queue position check | Weekly | Regulatory Affairs |
| SON technical clarification response | Within 5 business days of receipt | Regulatory Affairs |
| MES SON Module pre-loading | Immediate — placeholder certificates loaded | MES Team |

### 3.6 Certification Schedule

| Product SKU | Standard | Target Submission | Target Certificate | Status |
|-------------|----------|-------------------|--------------------|--------|
| CCG-INV-PSW | IEC 62040-1/3; NIS 62040 | Q1 2025 (overdue) | Q3 2025 | Urgent |
| CCG-INV-MSW | IEC 62040-1/3; NIS 62040 | Q1 2025 (overdue) | Q3 2025 | Urgent |
| CCG-SCC-MPPT | IEC 61683; NIS 61683 | Q2 2025 (overdue) | Q4 2025 | Urgent |
| CCG-SCC-PWM | IEC 61683; NIS 61683 | Q2 2025 (overdue) | Q4 2025 | Urgent |
| CCG-UPS | IEC 62040-1/3 | Q3 2025 | Q1 2026 | On track |
| CCG-PT series | IEC 62841-2 | Q3 2025 | Q1 2026 | On track |

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
| BIM 3D model | Load 12,000 m² floor model using `docs/bim/zone-boundaries.md` and `docs/bim/asset-anchors.md` |

**Simulation use-case families:**

| Family | Scenarios |
|--------|-----------|
| Production Simulation | Inverter assembly ramp, SMT changeover, load bank test throughput, winding cell cycle time |
| Predictive Maintenance | Reflow oven thermal degradation, transformer winding motor vibration, BESS SoH, load bank cooling fans |
| Energy Optimisation | BESS dispatch, ground-mount solar output vs load, generator run minimisation |
| Quality & Compliance | PCB solder paste CPK drift, load bank test yield by SKU, IEC 62040 transfer time trends |

### 4.3 Week 7–10 — Investor Showcase Pack

| Evidence Theme | Deliverable |
|----------------|-------------|
| Achieved so far | Live ingestion coverage, model coverage, simulation readiness, governance controls |
| Simulation today | Demonstrable scenarios across throughput, quality, downtime, and energy |
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

**Target:** ~100 staff in Wave 1 (of ~280 total Phase 1 headcount)

### 5.1 Week 1–2 — Programme Setup

| Task | Detail |
|------|--------|
| Curriculum finalisation | 6-week onboarding programme; includes high-voltage safety and IEC standard awareness |
| Venue booking | Factory building (if civil works complete) or off-site |
| Trainer roster | Internal engineers + external high-voltage safety, IPC, ESD, power electronics specialists |

### 5.2 Week 3–14 — Wave 1 Cohort

| Weeks | Module | Content |
|-------|--------|---------|
| 3–4 | Safety Foundation | Safety induction, ESD handling, high-voltage HV work permit process, 5S, emergency procedures |
| 5–6 | MES Operations | MES system operation using deployed sandbox (WS1 output); load bank test module walkthrough |
| 7–8 | Quality Awareness | IEC 62040, IEC 61683, IPC-A-610 basics; load bank test pass/fail criteria |
| 9–10 | AMR Operations | AMR Fleet Operator training using MiR Fleet Manager in simulation mode |
| 11–12 | Role-Specific Skills | SMT Operators, Inverter Assembly Technicians, Test Engineers, MES Data Officers |

**Pre-production compliance requirement:** All staff registered in NSITF (workers' compensation) and pension scheme before production commencement.

---

## 6. Workstream 5 — Supply Chain & Import Logistics

*Owner: Procurement & Trade Finance Team*

### 6.1 Week 1–2 — Procurement Launch

Issue RFQs and initiate purchase orders for all long-lead components:

| Component | Lead Time | Safety Stock Policy |
|-----------|-----------|---------------------|
| Power MOSFETs / IGBTs | 8–12 weeks | 6 weeks demand |
| Toroidal Core (silicon steel) | 10–14 weeks | 6 weeks demand |
| Electrolytic Capacitors | 6–8 weeks | 4 weeks demand |
| Bare PCBs | 4–6 weeks | 4 weeks demand |
| Copper Magnet Wire | 4–6 weeks | 4 weeks demand |
| Power Tool Motors (OEM) | 10–12 weeks | 8 weeks demand |
| SMT Consumables | 4 weeks (sea) | 3 weeks demand |

Open LCs or initiate TT payments aligned to supplier payment terms.

### 6.2 Week 2–4 — Import Compliance Setup

> **Government processing times are long — all items below must start in Week 1.**

| Action | Body | Timeline |
|--------|------|----------|
| Form M applications | CBN / Commercial Bank | Per PO |
| SON MANCAP pre-shipment CoC | SON | Per container |
| NESREA EPR registration | NESREA | 4–6 weeks — start immediately |
| Licensed customs agents briefed (2 agents) | NCS-licensed agents | Week 1 |
| Tin Can Island pre-clearance protocol agreed | Freight forwarder | Week 2 |

### 6.3 Week 3–6 — Intra-Group Coordination

| Partner | Action | SLA |
|---------|--------|-----|
| Coo-Cah Plastics Factory | Confirm plastic enclosure volumes for all inverter, SCC, UPS, and power tool SKUs; establish truck SLA | 2 runs/day, < 5 km |
| Coo-Cah Personal Electronics | Confirm PCB supply schedule for BMS boards; sign off BMS-1S and BMS-2S PCB design | Per agreed production schedule |
| All sister factories | Activate hourly MES-to-MES REST sync (built in WS1) once all MES systems are live | Hourly |

### 6.4 Week 4–8 — Warehouse & Stores Setup

| Task | Detail |
|------|--------|
| Bonded stores in MES WMS | Configure bin locations for all component categories |
| Safety stock triggers | Set reorder points per `supply-chain.md §4` policy |
| Incoming QC workflow | MES goods-receipt scan for every inbound shipment; transformer core dimensional inspection |

---

## 7. Workstream 6 — Energy Management System (EMS) Configuration (M1.9)

*Owner: Energy & Infrastructure Team*

### 7.1 Week 1–2 — Software Platform Deployment

| Task | Detail |
|------|--------|
| EMS software | Deploy Sungrow iSolarCloud + Coo-Cah EMS in configuration/simulation mode |
| Site parameters | Load: 600 kWp ground-mount PV, 700 kWh BESS, grid contract, 350 kVA backup generator |

### 7.2 Week 3–4 — Operating Logic Configuration

| Rule | Detail |
|------|--------|
| BESS charge/discharge | Solar-first priority; overnight BESS discharge schedule; grid top-up thresholds |
| ATS trigger | Auto-start generator when BESS SoC < 20% + grid failure |
| Load bank test bay | Configure as scheduled high-load consumer; defer during BESS low SoC |
| Critical load tiers | Configure tiers 1–4 shed sequence in ATS logic (per `energy-profile.md §6.2`) |

### 7.3 Week 5–6 — KPI Dashboards & Alerts

Build all energy KPI dashboards:

| KPI | Target |
|-----|--------|
| Solar Self-Sufficiency Ratio | ≥ 80% |
| Grid Import (% of total) | ≤ 20% |
| Energy Intensity — Inverter (PSW 1kVA) | ≤ 3.5 kWh/unit |
| Energy Intensity — SCC (MPPT 40A) | ≤ 0.8 kWh/unit |
| Energy Intensity — Power Tool | ≤ 1.2 kWh/unit |
| Generator Run Hours | < 100 hrs/year |
| Power Factor | ≥ 0.95 |
| BESS SoH at Year 5 | ≥ 85% |
| Annual CO₂ Avoidance | ~600 t CO₂/year |
| Unplanned Power Downtime | < 4 hrs/year |

Configure alert thresholds and escalation paths for all energy events. Validate MES ↔ EMS data exchange.

### 7.4 Week 7–8 — Simulation & Validation

| Simulation | Output |
|------------|--------|
| BESS Dispatch Optimisation | Daily solar forecast × factory load profile × load bank test schedule |
| Ground-Mount Solar Soiling Loss | Monthly output degradation model for cleaning schedule optimisation |
| 12-month energy cost projection | Solar+BESS vs grid-only baseline for CFO/investor reporting |

---

## 8. Cross-Cutting Governance

### 8.1 Meeting Cadence

| Cadence | Meeting | Purpose |
|---------|---------|---------|
| Weekly | Workstream stand-ups | Block removal, dependency tracking |
| Bi-weekly | Programme steering | Cross-workstream progress; milestone gating |
| Monthly | Regulatory status review | IEC/SON application status; NESREA updates |
| Monthly | Supplier performance review | OTIF, lead time adherence, quality |

### 8.2 Key Dependencies

| Dependency | Risk | Mitigation |
|------------|------|------------|
| WS1 MES UAT must complete before WS4 staff training on MES | Training on unstable system wastes resource | Gate WS4 Week 5–6 start to WS1 sandbox passing UAT |
| IEC lab queue (4–12 weeks) is not in our control | Certificates delayed → zero revenue from certified products | Submit all applications in Week 1; maintain weekly lab contact |
| NESREA EPR registration (4–6 weeks) | Non-compliance at market launch | File in Week 1; no exceptions |
| Form M applications at CBN/commercial bank | Long processing time; PO payment blocked | Initiate simultaneously with PO issue in Week 1 |
| Coo-Cah Plastics Factory enclosure capacity | Enclosure supply shortfall delays assembly start | Daily MES visibility; shared production planning from Week 3 |

### 8.3 Programme Milestone Gate Summary

| Gate | Trigger | Key Evidence |
|------|---------|--------------|
| G1 — MES Sandbox Live | WS1 Week 2 complete | MES accessible; edge nodes online |
| G2 — MES UAT Pass | WS1 Week 12 complete | Zero P1/P2 defects; all integrations stubbed |
| G3 — IEC Applications Submitted | WS2 Week 4 complete | Lab receipt for CCG-INV-PSW, CCG-INV-MSW, CCG-SCC-MPPT |
| G4 — DT Investor Pack Ready | WS3 Week 10 complete | Four scenarios demonstrable; metric dictionary locked |
| G5 — Wave 1 Training Complete | WS4 Week 14 complete | ~100 staff certified; NSITF + pension registrations done |
| G6 — Safety Stock at Reorder Point | WS5 Week 8 complete | All component categories above reorder point in MES WMS |
| G7 — EMS Commissioned | WS6 Week 8 complete | EMS live in simulation; 12-month cost projection delivered |

---

*For automation phase details, refer to [`automation-roadmap.md`](./automation-roadmap.md).*
*For MES architecture and machine integration specifications, refer to [`mes-integration.md`](./mes-integration.md).*
*For regulatory requirements and IEC process detail, refer to [`regulatory.md`](./regulatory.md).*
*For energy system design, refer to [`energy-profile.md`](./energy-profile.md).*
*For supply chain logistics and safety stock policy, refer to [`supply-chain.md`](./supply-chain.md).*
*For digital twin asset registry and investor showcase requirements, refer to [`digital-twin.md`](./digital-twin.md).*
