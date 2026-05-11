# Personal Electronics Factory — Phase 1 Implementation Plan

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Personal Electronics Factory | **Location:** Sagamu Industrial Estate, Ogun State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Programme Management Office

---

## 1. Strategy Overview

The core strategy is **parallelise everything that has no dependency on physical equipment, compress the timeline, and be ready to connect machines the moment they land.**

All six workstreams run concurrently from Day 1 on a two-week sprint cadence. Each workstream has a designated owner and reports into the bi-weekly Programme Steering meeting.

| Workstream | Name                                  | Owner                               | Key Milestone |
|------------|---------------------------------------|-------------------------------------|---------------|
| WS1        | MES Phase 1 Deployment                | MES / Digital Manufacturing Team   | M1.4 — MES live (Q3 2025) |
| WS2        | NCC Type Approval                     | Regulatory Affairs & Quality Team  | M1.6 — NCC TA certificates (Q3–Q4 2025) |
| WS3        | Digital Twin — Descriptive Phase      | Digital Manufacturing & AI Team    | M2.9 — DT Phase 2 sync (Q2 2028) |
| WS4        | Workforce Training (Coo-Cah Academy)  | HR / Training Manager              | ~450 staff trained pre-production |
| WS5        | Supply Chain & Import Logistics       | Procurement & Trade Finance Team   | First container cleared; safety stock at reorder point |
| WS6        | Energy Management System (EMS)        | Energy & Infrastructure Team       | M1.9 — BESS + Solar commissioned (Q1 2026) |

---

## 2. Workstream 1 — MES Phase 1 Deployment (M1.4)

*Owner: MES / Digital Manufacturing Team*

### 2.1 Week 1–2 — Foundation

| Task | Detail |
|------|--------|
| Server provisioning | Procure/provision MES application server (on-site primary) and cloud-sync secondary (Lagos DC) |
| Edge node hardware | Stand up the three edge nodes (SMT Zone, Assembly, QC+RF Lab) — hardware + OS only |
| Sandbox deployment | Deploy MES application in sandbox mode; validate licence keys and connectivity to Coo-Cah Cloud Platform |

### 2.2 Week 3–6 — Module Configuration

Configure all Phase 1 modules in sequence:

1. Production Order Management
2. WIP Tracking
3. Traceability
4. Quality Management
5. NCC Test Logging
6. AMR Fleet Dispatch
7. Energy Monitoring
8. CMMS

| Task | Detail |
|------|--------|
| Serial number format | Define `CCE-SP-LITE-SAG-25-212-XXXXXX` pattern in MES; seed the full product SKU register |
| User roles | Build and test all roles: Operator, Technician, Supervisor, Engineer, Admin, Auditor |
| Network segregation | Configure IT/OT VLAN, DMZ for ERP integration |

### 2.3 Week 7–10 — Integration Plumbing (machine-free)

Implement and test all REST/OPC-UA stub endpoints for each machine interface so that integration is a cable-plug, not a design exercise, when hardware arrives.

| System | Interface | Protocol |
|--------|-----------|----------|
| DEK Screen Printer | SMEMA + SECS/GEM stub | SMEMA |
| Koh Young SPI/AOI | Inspection result stub | SECS/GEM or REST |
| JUKI P&P | Placement result stub | SECS/GEM |
| Atlas Copco Torque Station | Torque value stub | OPC-UA |
| Phone Flash Station | Serial + firmware stub | REST API |
| Chroma 17020/19053 | Battery/safety result stub | Ethernet API |
| Cognex In-Sight 9000 | Vision pass/fail stub | REST API |

Additional integrations to complete in this window:

- MES ↔ ERP (SAP or equivalent): production orders, BOM, inventory, costing
- MES ↔ AI Platform (MQTT) and MES ↔ Digital Twin MQTT stream (dummy payloads)
- MES ↔ Coo-Cah Plastics Factory MES and Garage Power Electronics MES (REST, hourly sync)
- NCC audit report generation validated using dummy RF test data

### 2.4 Week 11–12 — UAT & Go-Live Readiness

| Task | Acceptance Criterion |
|------|----------------------|
| End-to-end simulated production orders | All modules pass; zero P1/P2 defects open |
| TLS 1.3 encryption validation | All MES ↔ cloud and MES ↔ machine connections verified |
| AES-256 at-rest audit | All databases and trace archives confirmed encrypted |
| Penetration test scoping | Test scope agreed with third-party firm; critical finding SLA = 30 days |

---

## 3. Workstream 2 — NCC Type Approval (M1.6)

*Owner: Regulatory Affairs & Quality Team*

> **Critical path warning:** No wireless product may be despatched without a valid NCC Type Approval certificate. Lab queue time is 4–12 weeks and is outside the team's control. Submit applications immediately.

### 3.1 Week 1–2 — Technical File Preparation (CCE-FP-3G & CCE-SP-LITE)

Both products have Q3 2025 certificate targets and are already overdue.

| Deliverable | Content |
|-------------|---------|
| RF parameter sheet | Frequency bands, max EIRP, modulation |
| Antenna documentation | Antenna gain data, radiation patterns |
| Circuit diagrams | Final production schematics |
| User manual draft | Per NCC labelling guidance |
| Declaration of Conformity | Template signed by Regulatory Affairs lead |
| SAR compliance posture | Confirm ≤ 2.0 W/kg (head + body) for CCE-FP-3G, CCE-FP-4G, CCE-SP-LITE |

### 3.2 Week 3–4 — Pre-Compliance & Application

| Task | Detail |
|------|--------|
| Pre-compliance scan | Schedule EMC + RF scan at NCC-accredited lab (Lagos or Abuja) using engineering samples |
| MTBS portal submission | Submit online applications for CCE-FP-3G and CCE-SP-LITE |
| Application fees | Pay ₦100k–₦250k per product |
| NCC representative | Designate Coo-Cah Regulatory Affairs as local NCC representative |

### 3.3 Week 5–6 — CCE-FP-4G and CCE-TWS-01

- Repeat Technical File preparation and MTBS portal application for both SKUs
- CCE-TWS-01 is Bluetooth-only (Short Range Device category) — simpler test scope, shorter lab queue

### 3.4 Week 7–8 — CCE-SW-LITE & Parallel Registrations

| Task | Detail |
|------|--------|
| CCE-SW-LITE Technical File | Bluetooth 5.1; target certificate Q1 2026 |
| SON product registration | Initiate for all Phase 1 SKUs under NIS 62368-1:2022 |
| NESREA EPR registration | Register as electronic product producer (obligation was due Q2 2025 — urgent) |

### 3.5 Ongoing — Lab Follow-up

| Activity | Frequency | Owner |
|----------|-----------|-------|
| Lab queue position check | Weekly | Regulatory Affairs |
| NCC technical clarification response | Within 5 business days of receipt | Regulatory Affairs |
| MES NCC Module pre-loading | Immediate — placeholder certificates loaded | MES Team |

### 3.6 NCC Type Approval Schedule

| Product SKU | Category | Target Submission | Target Certificate | Status |
|-------------|----------|-------------------|--------------------|--------|
| CCE-FP-3G | Mobile Handset | Q1 2025 (overdue) | Q3 2025 | Urgent |
| CCE-SP-LITE | Smartphone | Q1 2025 (overdue) | Q3 2025 | Urgent |
| CCE-FP-4G | Mobile Handset | Q2 2025 (overdue) | Q4 2025 | Urgent |
| CCE-TWS-01 | Short Range Device | Q2 2025 (overdue) | Q4 2025 | Urgent |
| CCE-SW-LITE | Short Range Device / Watch | Q3 2025 | Q1 2026 | On track |

---

## 4. Workstream 3 — Digital Twin Platform (Descriptive Phase)

*Owner: Digital Manufacturing & AI Team*

*Reference: [`digital-twin.md`](./digital-twin.md) §5 for investor showcase requirements.*

### 4.1 Week 1–2 — Platform Provisioning

| Task | Detail |
|------|--------|
| Platform deployment | Deploy Coo-Cah AI Platform Digital Twin Module (Lagos DC + on-site edge) |
| Asset registry load | Import all 142 Phase 1 assets from `digital-twin.md` — asset IDs, zones, sensor schemas, protocols |

### 4.2 Week 3–6 — Schema & Simulation Build

| Task | Detail |
|------|--------|
| Sensor data point schemas | Define all ~2,800 MQTT topics, data types, engineering units, and calibration intervals |
| DES models | Build discrete-event simulation models for all four use-case families (see table below) |
| BIM 3D model | Load 18,000 m² floor model using `docs/bim/zone-boundaries.md` and `docs/bim/asset-anchors.md` |

**Simulation use-case families:**

| Family | Scenarios |
|--------|-----------|
| Production Simulation | Ramp, SMT changeover, WIP flow, product mix, NPI |
| Predictive Maintenance | Reflow oven thermal degradation, feeder vibration, AMR battery EOL, BESS SoH |
| Energy Optimisation | BESS dispatch, factory load shift, solar soiling loss, generator run minimisation |
| Quality & Compliance | SMT paste CPK drift, NCC RF sample yield, cosmetic defect root cause |

### 4.3 Week 7–10 — Investor Showcase Pack

Per the locked four-part investor storyline (`digital-twin.md §5.1`):

| Evidence Theme | Deliverable |
|----------------|-------------|
| Achieved so far | Live ingestion coverage, model coverage, simulation readiness, governance controls |
| Simulation today | Demonstrable scenarios across throughput, quality, downtime, and energy |
| Physical constraints | Infrastructure, equipment, integration, workforce, and compliance gaps |
| Funding translation | Ask-by-ask mapping from modelled bottleneck/risk to KPI lift and payback |

- Lock metric dictionary; all investor claims must be reproducible from evidence lineage
- Begin weekly internal rehearsal cadence

### 4.4 Week 11–12 — MES ↔ DT Integration Validation

| Test | Acceptance Criterion |
|------|----------------------|
| End-to-end MQTT streaming pipe | Functional using WS1 UAT simulated production order data |
| Synchronisation latency | ≤ 1 second confirmed in test |

---

## 5. Workstream 4 — Workforce Training (Coo-Cah Manufacturing Academy)

*Owner: HR / Training Manager*

**Target:** ~150 staff in Wave 1 (of 450 total Phase 1 headcount)

### 5.1 Week 1–2 — Programme Setup

| Task | Detail |
|------|--------|
| Curriculum finalisation | 6-week onboarding programme |
| Venue booking | Factory building (if civil works complete) or off-site |
| Trainer roster | Internal engineers + external ESD, IPC, safety specialists |

### 5.2 Week 3–14 — Wave 1 Cohort

| Weeks | Module | Content |
|-------|--------|---------|
| 3–4 | Safety Foundation | Safety induction, ESD handling, 5S methodology, emergency procedures, Factories Act rights |
| 5–6 | MES Operations | MES system operation using deployed sandbox (WS1 output) |
| 7–8 | Quality Awareness | IPC-A-610 class, SMT quality basics, NCC type approval awareness |
| 9–10 | AMR Operations | AMR Fleet Operator training using MiR Fleet Manager in simulation mode |
| 11–12 | Role-Specific Skills | Separate tracks: SMT Operators, Assembly Technicians, QC Inspectors, MES Data Officers |

**Pre-production compliance requirement:** All staff registered in NSITF (workers' compensation) and pension scheme before production commencement.

---

## 6. Workstream 5 — Supply Chain & Import Logistics

*Owner: Procurement & Trade Finance Team*

### 6.1 Week 1–2 — Procurement Launch

Issue RFQs and initiate purchase orders for all long-lead components:

| Component | Lead Time | Safety Stock Policy |
|-----------|-----------|---------------------|
| SoC Processors | 8–12 weeks | 6 weeks demand |
| Display Modules | 8–10 weeks | 4 weeks demand |
| Camera Modules | 8–10 weeks | 4 weeks demand |
| Battery Cells | 6–8 weeks | 4 weeks demand |
| Memory (LPDDR/eMMC) | 6–8 weeks | 4 weeks demand |
| Bare PCBs | 4–6 weeks | 4 weeks demand |
| SMT Consumables (paste, flux, stencils) | 4 weeks (sea) | 3 weeks demand |

Open LCs or initiate TT payments aligned to supplier payment terms.

### 6.2 Week 2–4 — Import Compliance Setup

> **Government processing times are long — all items below must start in Week 1.**

| Action | Body | Timeline |
|--------|------|----------|
| Form M applications | CBN / Commercial Bank | Per PO |
| SON MANCAP CoC for battery cells + chargers | SON | Pre-shipment |
| NAFDAC import notification (battery cells, chargers) | NAFDAC | 4–6 weeks — start immediately |
| Licensed customs agents briefed (2 agents) | NCS-licensed agents | Week 1 |
| Tin Can Island pre-clearance protocol agreed | Tin Can / freight forwarder | Week 2 |

### 6.3 Week 3–6 — Intra-Group Coordination

| Partner | Action | SLA |
|---------|--------|-----|
| Coo-Cah Plastics Factory | Confirm daily volumes for all 6 casing types; establish daily shuttle truck SLA | 2 runs/day, < 5 km |
| Coo-Cah Garage Power Electronics | Confirm charger + USB-C cable schedule; sign off Power Bank BMS PCB design | Per agreed production schedule |
| Both partner factories | Activate hourly MES-to-MES REST sync (built in WS1) once both MES systems are live | Hourly |

### 6.4 Week 4–8 — Warehouse & Stores Setup

| Task | Detail |
|------|--------|
| Bonded stores in MES WMS | Configure bin locations for all 12 component categories |
| Safety stock triggers | Set reorder points per `supply-chain.md §4` policy |
| Incoming QC workflow | Set up MES goods-receipt scan for every inbound shipment |

---

## 7. Workstream 6 — Energy Management System (EMS) Configuration (M1.9)

*Owner: Energy & Infrastructure Team*

### 7.1 Week 1–2 — Software Platform Deployment

| Task | Detail |
|------|--------|
| EMS software | Deploy Sungrow iSolarCloud + Coo-Cah EMS in configuration/simulation mode |
| Site parameters | Load: 850 kWp PV, 900 kWh BESS (2 × 450 kWh), 600 kW grid contract, 500 kVA backup generator |

### 7.2 Week 3–4 — Operating Logic Configuration

| Rule | Detail |
|------|--------|
| BESS charge/discharge | Solar-first priority; overnight BESS discharge schedule; grid top-up thresholds |
| ATS trigger | Auto-start generator when BESS SoC < 20% + grid failure |
| Critical load tiers | Configure tiers 1–4 shed sequence in ATS logic (per `energy-profile.md §6.2`) |
| ToU tariff management | AMI smart meter integration for time-of-use optimisation |

### 7.3 Week 5–6 — KPI Dashboards & Alerts

Build all 11 energy KPI dashboards:

| KPI | Target |
|-----|--------|
| Solar Self-Sufficiency Ratio | ≥ 80% |
| Grid Import (% of total) | ≤ 20% |
| Energy Intensity — Phone | ≤ 4.8 kWh/unit |
| Energy Intensity — Earbud pair | ≤ 0.35 kWh/pair |
| Energy Intensity — Smartwatch | ≤ 1.8 kWh/unit |
| Energy Intensity — Power Bank | ≤ 0.5 kWh/unit |
| Generator Run Hours | < 100 hrs/year |
| Power Factor | ≥ 0.95 |
| BESS SoH at Year 5 | ≥ 85% |
| Annual CO₂ Avoidance | ~720 t CO₂/year |
| Unplanned Power Downtime | < 4 hrs/year |

Configure alert thresholds and escalation paths for all energy events. Validate MES ↔ EMS data exchange (zone-level sub-metering, kWh per production order).

### 7.4 Week 7–8 — Simulation & Validation

| Simulation | Output |
|------------|--------|
| BESS Dispatch Optimisation | Daily solar forecast × ToU × factory load profile |
| Factory Load Shift | AMR opportunity charging deferral off-peak |
| 12-month energy cost projection | Solar+BESS vs grid-only baseline for CFO/investor reporting |

---

## 8. Cross-Cutting Governance

### 8.1 Meeting Cadence

| Cadence | Meeting | Purpose |
|---------|---------|---------|
| Weekly | Workstream stand-ups | Block removal, dependency tracking |
| Bi-weekly | Programme steering | Cross-workstream progress; milestone gating |
| Monthly | Regulatory status review | NCC application status; SON/NESREA updates |
| Monthly | Supplier performance review | OTIF, lead time adherence, quality |

### 8.2 Key Dependencies

| Dependency | Risk | Mitigation |
|------------|------|------------|
| WS1 MES UAT must complete before WS4 staff training on MES | Training on unstable system wastes resource | Gate WS4 Week 5–6 start to WS1 sandbox passing UAT |
| NCC lab queue (4–12 weeks) is not in our control | Certificates delayed → zero revenue from wireless products | Submit all applications in Week 1; maintain weekly lab contact |
| NAFDAC battery import notification (4–6 weeks) | Components blocked at customs → delayed production start | File in Week 1; no exceptions |
| Form M applications at CBN/commercial bank | Long processing time; PO payment blocked | Initiate simultaneously with PO issue in Week 1 |
| Coo-Cah Plastics Factory capacity | Casing supply shortfall delays assembly start | Daily MES visibility; shared production planning from Week 3 |

### 8.3 Programme Milestone Gate Summary

| Gate | Trigger | Key Evidence |
|------|---------|--------------|
| G1 — MES Sandbox Live | WS1 Week 2 complete | MES accessible; edge nodes online |
| G2 — MES UAT Pass | WS1 Week 12 complete | Zero P1/P2 defects; all integrations stubbed |
| G3 — NCC Applications Submitted | WS2 Week 4 complete | MTBS portal receipt for CCE-FP-3G, CCE-SP-LITE, CCE-FP-4G, CCE-TWS-01 |
| G4 — DT Investor Pack Ready | WS3 Week 10 complete | Four scenarios demonstrable; metric dictionary locked |
| G5 — Wave 1 Training Complete | WS4 Week 14 complete | ~150 staff certified; NSITF + pension registrations done |
| G6 — Safety Stock at Reorder Point | WS5 Week 8 complete | All 12 categories above reorder point in MES WMS |
| G7 — EMS Commissioned | WS6 Week 8 complete | EMS live in simulation; 12-month cost projection delivered |

---

*For automation phase details, refer to [`automation-roadmap.md`](./automation-roadmap.md).*
*For MES architecture and machine integration specifications, refer to [`mes-integration.md`](./mes-integration.md).*
*For regulatory requirements and NCC process detail, refer to [`regulatory.md`](./regulatory.md).*
*For energy system design, refer to [`energy-profile.md`](./energy-profile.md).*
*For supply chain logistics and safety stock policy, refer to [`supply-chain.md`](./supply-chain.md).*
*For digital twin asset registry and investor showcase requirements, refer to [`digital-twin.md`](./digital-twin.md).*
