# Smart Estate & City Electronics Factory — Automation Roadmap

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Smart Estate & City Electronics Factory | **Location:** Lekki Free Trade Zone, Lagos State, Nigeria
> **Document Version:** 1.0 | **Owner:** Coo-Cah Technology & Operations Division

---

## 1. Introduction

The Coo-Cah automation roadmap defines the progressive journey from initial semi-manual operations to a fully AI-integrated, lights-out-capable manufacturing facility. For the Smart Estate & City Electronics Factory, which manufactures smart meters, IoT gateways, smart poles, and traffic controllers, the automation focus centres on PCB assembly precision, calibration automation, and traceability — critical for products deployed in utility and public safety infrastructure.

**Automation Maturity Scale:**

| Level | Name          | Description                                                               |
|-------|---------------|---------------------------------------------------------------------------|
| 1     | Manual        | All tasks performed by humans; no automation or MES                       |
| 2     | Semi-Automated| Key machines automated; manual loading/unloading; paper-based tracking    |
| 3     | Connected     | MES live; all machines communicating; real-time OEE visible               |
| 4     | Integrated    | AMRs deployed; automated material flow; AI-generated alerts               |
| 5     | Predictive    | AI predicts failures, quality defects; scheduling optimised by AI         |
| 6     | Autonomous    | Lights-out operation for select product lines; minimal human intervention |

**Smart Estate & City Factory Current Level:** 1 (Pre-production)
**Target by End of Phase 3:** Level 5

---

## 2. Phase 1 — Foundation: MES Deployment & Semi-Automation

**Theme:** Establish operational foundation — SMT line connected to MES, AMR fleet deployed, calibration traceability live, energy system commissioned.

**Phase Duration:** Q3 2026 → Q2 2027 (12 months)

### 2.1 Phase 1 Milestones

| # | Milestone                                     | Target Date | KPI                                | Success Criteria                                                   | Status    |
|---|-----------------------------------------------|-------------|------------------------------------|--------------------------------------------------------------------|-----------|
| 1 | Factory construction completed                | Q3 2026     | Certificate of Occupancy           | Building handed over; utilities connected                          | Planned   |
| 2 | Production equipment installed & commissioned | Q4 2026     | All machines powered on, tested    | OEM sign-off; all machines in MES asset register                   | Planned   |
| 3 | MES platform deployed (core modules)          | Q4 2026     | MES live for all production zones  | Production orders, WIP tracking, QC results in MES                 | Planned   |
| 4 | Smart meter calibration traceability live      | Q1 2027     | 100% calibration data in MES       | Every meter serial linked to calibration certificate in MES         | Planned   |
| 5 | AMR fleet (8 units) commissioned              | Q1 2027     | AMR availability ≥ 95%             | All 8 AMRs navigating all defined routes autonomously              | Planned   |
| 6 | Energy system (Solar + BESS) commissioned     | Q4 2026     | Solar contributing ≥ 70% of energy | EMS online; solar/BESS data feeding MES energy dashboard           | Planned   |
| 7 | First production run — Smart Meters           | Q1 2027     | 5,000 units pilot batch            | Pilot batch passes IQC, IPQC, FQC; IEC 62053 test pass            | Planned   |
| 8 | ISO 9001 QMS implemented                      | Q2 2027     | Quality manual approved            | All QMS procedures written, trained, and followed                   | Planned   |
| 9 | Phase 1 capacity target achieved              | Q2 2027     | 40,000 units/month                 | Sustained for 3 consecutive months                                  | Planned   |
| 10| NCC type approval received (LoRa gateway)     | Q2 2027     | Type approval certificate          | NCC certificate in hand; products cleared for commercial sale       | Planned   |

### 2.2 Phase 1 KPIs

| KPI                              | Baseline (Day 1) | Target (Phase 1 End) |
|----------------------------------|------------------|----------------------|
| OEE                              | N/A              | ≥ 75%                |
| First-Pass Yield                 | N/A              | ≥ 95%                |
| Production Volume                | 0                | 40,000 units/month   |
| Energy — Solar Self-Sufficiency  | 0%               | ≥ 70%                |
| MES Data Completeness            | 0%               | ≥ 95%                |
| Calibration Traceability         | 0%               | 100%                 |
| AMR Utilisation                  | 0%               | ≥ 80%                |
| Safety Incidents (LTI)           | 0                | 0                    |

### 2.3 Phase 1 Technology Stack

- **MES:** Coo-Cah MES Core (Production Planning, WIP, QC, Calibration Registry, Inventory, OEE, Energy)
- **AMR Software:** Coo-Cah AMR Fleet Manager v2.0
- **Machine Connectivity:** OPC-UA for SMT equipment; MQTT IoT gateways for test/calibration rigs
- **Calibration Management:** Integrated calibration module in MES; certificates auto-generated and linked to serial numbers
- **Energy Management:** EMS integrated with MES; BMS/SCADA for BESS

---

## 3. Phase 2 — Integration: Robotics & AI Quality

**Theme:** Deploy robotic handling for fragile electronic subassemblies; AI vision for PCB and smart meter inspection; digital twin live; predictive maintenance.

**Phase Duration:** Q3 2027 → Q2 2028 (12 months)
**Prerequisite:** Phase 1 KPIs met; MES data quality ≥ 95% for ≥ 6 months.

### 3.1 Phase 2 Milestones

| # | Milestone                                        | Target Date | KPI                                  | Success Criteria                                                  | Status  |
|---|--------------------------------------------------|-------------|--------------------------------------|-------------------------------------------------------------------|---------|
| 1 | Robotic PCB handling — SMT unload station        | Q3 2027     | Cycle time reduction ≥ 20%           | Robot operational; board damage rate < 0.1%                       | Planned |
| 2 | Automated smart meter sealing & potting station  | Q4 2027     | Cycle time reduction ≥ 15%           | Automated dispensing; seal pass rate ≥ 99.5%                      | Planned |
| 3 | AI Vision QC on PCBs deployed                   | Q4 2027     | Defect detection rate ≥ 99.5%        | AI model validated; false positive rate < 0.5%                    | Planned |
| 4 | Digital twin — live sync established             | Q1 2028     | DT sync latency ≤ 5 seconds          | All Phase 2 assets in digital twin; real-time state visible       | Planned |
| 5 | Predictive maintenance model trained & deployed  | Q1 2028     | MTBF improvement ≥ 20%               | Model predicting failures ≥ 48h in advance for top 5 machines    | Planned |
| 6 | Phase 2 capacity target achieved                 | Q2 2028     | 80,000 units/month                   | Sustained for 3 consecutive months                                | Planned |
| 7 | Energy — solar self-sufficiency ≥ 80%            | Q2 2028     | EMS monthly report                   | Monthly average solar supply ≥ 80% of total consumption           | Planned |
| 8 | IEC 62053 recertification (Phase 2 scope)        | Q2 2028     | Audit pass                           | Expanded scope certification confirmed                             | Planned |

### 3.2 Phase 2 KPIs

| KPI                              | Phase 1 End  | Target (Phase 2 End) |
|----------------------------------|--------------|----------------------|
| OEE                              | ≥ 75%        | ≥ 85%                |
| First-Pass Yield                 | ≥ 95%        | ≥ 98%                |
| Production Volume                | 40,000/month | 80,000/month         |
| Defect Escape Rate               | < 500 ppm    | ≤ 100 ppm            |
| Energy — Solar Self-Sufficiency  | ≥ 70%        | ≥ 80%                |
| Digital Twin Coverage            | 0%           | ≥ 90%                |

---

## 4. Phase 3 — Autonomy: Lights-Out & Full AI Integration

**Theme:** Achieve lights-out operation for smart meter and LoRa gateway lines; fully autonomous calibration and test; AI-driven cross-factory scheduling.

**Phase Duration:** Q3 2028 → Q4 2029 (18 months)

### 4.1 Phase 3 Milestones

| # | Milestone                                           | Target Date | KPI                                      | Success Criteria                                               | Status  |
|---|-----------------------------------------------------|-------------|------------------------------------------|----------------------------------------------------------------|---------|
| 1 | Lights-out trial — Smart Meter Line, Night Shift    | Q3 2028     | Unattended operation ≥ 6 hours           | Line runs 6h with 0 human intervention; quality maintained     | Planned |
| 2 | Full lights-out — Smart Meter Line                  | Q4 2028     | Night shift fully unattended             | Line runs unattended every night; remote NOC monitoring        | Planned |
| 3 | Autonomous calibration & test deployment            | Q1 2029     | 100% automated calibration               | Zero manual calibration steps; all certs auto-generated        | Planned |
| 4 | AI-to-AI cross-factory scheduling                   | Q2 2029     | Cross-factory plan in < 10 min           | Coo-Cah AI Platform optimises across all 8 electronics factories | Planned |
| 5 | Phase 3 capacity target achieved                    | Q3 2029     | 150,000 units/month                      | Sustained for 3 consecutive months                              | Planned |
| 6 | Net-Zero Energy certification                       | Q4 2029     | Annual CO₂ report                        | Verified net-zero carbon (Scope 1+2)                           | Planned |

### 4.2 Phase 3 KPIs

| KPI                              | Phase 2 End   | Target (Phase 3 End) |
|----------------------------------|---------------|----------------------|
| OEE                              | ≥ 85%         | ≥ 92%                |
| First-Pass Yield                 | ≥ 98%         | ≥ 99.5%              |
| Lights-Out Hours (% of total)    | 0%            | ≥ 40% (night shifts) |
| Defect Escape Rate               | ≤ 100 ppm     | ≤ 30 ppm             |
| Energy — Solar Self-Sufficiency  | ≥ 80%         | ≥ 90%                |

---

## 5. Workforce Transition Plan

| Phase   | Workforce Impact                                  | Mitigation                                                        |
|---------|---------------------------------------------------|-------------------------------------------------------------------|
| Phase 1 | Net job creation (new factory)                    | N/A — all new hires                                               |
| Phase 2 | Robotic handling replaces 12 manual stations      | Reskilling: operators → calibration technician / AI vision roles  |
| Phase 3 | Night-shift reduction on meter line               | Redeployment to smart pole and traffic controller expansion lines |

---

*For MES integration details, refer to [`mes-integration.md`](./mes-integration.md).*
*For digital twin capabilities, refer to [`digital-twin.md`](./digital-twin.md).*
