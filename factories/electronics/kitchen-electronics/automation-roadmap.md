# Kitchen Electronics Factory — Automation Roadmap

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Kitchen Electronics Factory | **Location:** Agbara Industrial Estate, Lagos State
> **Document Version:** 1.0 | **Owner:** Coo-Cah Technology & Operations Division

---

## 1. Introduction

The Kitchen Electronics Factory automation roadmap charts the progressive evolution from semi-automated appliance assembly with a live MES foundation to a lights-out-capable facility for small domestic appliances. Automation investments are staged to match growing production volumes and validated with Phase 1 production data before Phase 2 commitments are made.

**Automation Maturity Scale:**

| Level | Name            | Description                                                               |
|-------|-----------------|---------------------------------------------------------------------------|
| 1     | Manual          | All tasks performed by humans; no automation or MES                       |
| 2     | Semi-Automated  | Key machines automated; manual loading/unloading; paper-based tracking    |
| 3     | Connected       | MES live; all machines communicating; real-time OEE visible               |
| 4     | Integrated      | AMRs deployed; automated material flow; AI-generated alerts               |
| 5     | Predictive      | AI predicts failures, quality defects; scheduling optimised by AI         |
| 6     | Autonomous      | Lights-out operation for select product lines; minimal human intervention |

**Kitchen Electronics Factory Current Level:** 2 (pre-commissioning)
**Target by End of Phase 3:** Level 5

---

## 2. Phase 1 — Foundation: MES Deployment & Semi-Automation (2025–2027)

**Theme:** Connect all assembly lines and the SMT PCB line to MES; deploy 10-unit AMR fleet; achieve real-time production, quality, and energy visibility across all product lines.

| Phase | Period      | Theme                                      | Investment (₦B) | Target OEE | Headcount Change |
|-------|-------------|--------------------------------------------|-----------------|------------|------------------|
| 1     | 2025–2027   | Foundation: MES + AMR fleet + SMT live     | 1.2             | 72–75%     | +350 direct      |
| 2     | 2028–2029   | Robotics on fridge line; AI QC + DT live   | 1.8             | 80–83%     | +40 tech roles   |
| 3     | 2030–2031   | Lights-out small appliance; AI scheduling  | 1.4             | 87–90%     | +15 tech roles   |

### 2.1 Phase 1 Milestones

| # | Milestone                                          | Target Date | KPI                               | Success Criteria                                                      | Status   |
|---|----------------------------------------------------|-------------|-----------------------------------|-----------------------------------------------------------------------|----------|
| 1 | Factory civil works + service utilities complete   | Q2 2025     | Certificate of Occupancy          | Building handed over; gas handling infrastructure ready               | Planned  |
| 2 | SMT PCB line installed and producing boards        | Q3 2025     | First Article Inspection pass     | 200 boards FAI defect-free; SMT line at design throughput             | Planned  |
| 3 | Refrigerator line commissioned (2-door FF + 1D DC) | Q3 2025     | Takt time achieved                | ≤ 6 min takt; foam injection cycles passing QC                        | Planned  |
| 4 | MES Phase 1 deployed (all production zones)        | Q4 2025     | MES station coverage              | ≥ 90% production stations MES-connected and reporting                 | Planned  |
| 5 | AMR fleet (10 units) commissioned                  | Q4 2025     | AMR availability                  | ≥ 95% AMR availability; all routes mapped and operational             | Planned  |
| 6 | Solar 700 kWp + BESS 800 kWh commissioned          | Q1 2026     | Solar self-sufficiency            | ≥ 70% solar self-sufficiency within first 3 months                   | Planned  |
| 7 | R600a gas charging station certified               | Q2 2026     | NESREA permit                     | Refrigerant handling permit issued; zero-leak QC procedure active     | Planned  |
| 8 | ISO 9001 QMS implemented                           | Q3 2026     | QMS audit score                   | Internal audit pass; no major non-conformances                        | Planned  |
| 9 | Small appliance lines (blender, kettle, etc.) live | Q3 2026     | Units/day target                  | 1,200 small appliances/day across all SDA lines                       | Planned  |
| 10| Phase 1 OEE target achieved                        | Q4 2026     | Factory-wide OEE                  | OEE ≥ 72% blended; refrigerator line ≥ 68%; SDA lines ≥ 78%         | Planned  |

### 2.2 Phase 1 KPIs

| KPI                              | Baseline (Day 1) | Target (Phase 1 End) |
|----------------------------------|------------------|----------------------|
| OEE (all lines blended)          | N/A (new factory) | ≥ 72%               |
| First-Pass Yield (refrigerators) | N/A              | ≥ 95%                |
| First-Pass Yield (SDA lines)     | N/A              | ≥ 97%                |
| Production Volume — Fridges      | 0                | 330 units/day        |
| Production Volume — SDAs         | 0                | 1,200 units/day      |
| Solar Self-Sufficiency           | 0%               | ≥ 70%                |
| MES Data Completeness            | 0%               | ≥ 95%                |
| AMR Utilisation                  | 0%               | ≥ 80%                |
| Safety Incidents (LTI)           | 0                | 0                    |

### 2.3 Phase 1 Technology Stack

- **MES:** Siemens Opcenter Execution Discrete — production orders, WIP, quality, OEE, inventory
- **AMR Fleet:** 10× MiR200 heavy-load AMRs (for refrigerator sub-assemblies) + 2× MiR100 (SDA kitting)
- **Machine Connectivity:** OPC-UA on SMT equipment; MQTT IoT gateways for foam injection and PU ovens
- **EMS:** Energy Management System integrated with MES; BMS/SCADA for BESS
- **Gas Monitoring:** R600a leak detection sensors in refrigerator assembly zone; integrated with EMS alarms
- **HMI:** Industrial panel PCs at each station (IP65 rated)
- **AI Services (Phase 1):** Basic rule-based quality alerting; energy anomaly detection

---

## 3. Phase 2 — Integration: Robotics & AI Quality (2028–2029)

**Theme:** Deploy robotic arms on refrigerator foam injection and final assembly; upgrade QC to AI vision for cabinet dimensional inspection; activate digital twin; introduce AI-driven predictive maintenance for reflow oven and compressor test rigs.

**Prerequisite:** Phase 1 OEE ≥ 72% for ≥ 6 months; MES data completeness ≥ 95%.

### 3.1 Phase 2 Milestones

| # | Milestone                                               | Target Date | KPI                               | Success Criteria                                              | Status  |
|---|---------------------------------------------------------|-------------|-----------------------------------|---------------------------------------------------------------|---------|
| 1 | Robotic PU foam injection — Refrigerator Line           | Q1 2028     | Cycle time vs. manual baseline    | Foam injection cycle ≤ 4.5 min; uniform density pass ≥ 98%   | Planned |
| 2 | Robotic door hinge assembly — Fridge Line               | Q2 2028     | Assembly time reduction           | Door alignment defect rate ≤ 0.3%                             | Planned |
| 3 | AI vision QC for cabinet dimensional inspection         | Q2 2028     | Defect detection rate             | AI cabinet inspect ≥ 99% detection vs. manual baseline        | Planned |
| 4 | Digital twin live sync — all Phase 2 assets             | Q3 2028     | DT sync latency                   | All Phase 2 assets in digital twin; latency ≤ 5 sec           | Planned |
| 5 | Predictive maintenance model (reflow oven + compr. test)| Q3 2028     | Unplanned downtime reduction      | MTBF improvement ≥ 20% on monitored assets                    | Planned |
| 6 | Phase 2 capacity target — 150,000 fridges/year          | Q1 2029     | Fridge units/day                  | 500 fridges/day sustained for 3 months                        | Planned |
| 7 | ISO 14001 environmental management cert.                | Q2 2029     | Audit pass                        | No major NCs; R600a emissions < NESREA threshold              | Planned |
| 8 | Workforce reskilling (Phase 2 tech roles)               | Q4 2028     | Staff certified on Phase 2 tech   | 100% affected staff certified on new robotic systems          | Planned |

### 3.2 Phase 2 KPIs

| KPI                              | Phase 1 End | Target (Phase 2 End) |
|----------------------------------|-------------|----------------------|
| OEE (blended)                    | ≥ 72%       | ≥ 83%                |
| First-Pass Yield (fridges)       | ≥ 95%       | ≥ 97.5%              |
| Fridge Production Volume         | 330/day     | 500/day              |
| Unplanned Downtime               | Baseline    | ≤ 3% of total time   |
| Solar Self-Sufficiency           | ≥ 70%       | ≥ 80%                |
| Digital Twin Coverage            | 0%          | ≥ 90%                |

### 3.3 Phase 2 Technology Stack

- **Robotics:** FANUC CRX-20iA collaborative robots (2× foam injection, 2× door hinge/seal)
- **AI Vision QC:** Coo-Cah AI Vision Platform — CNN model for cabinet gap, weld, and surface inspection
- **Digital Twin:** Coo-Cah Digital Twin Engine — full refrigerator line, foam injection station
- **Predictive Maintenance AI:** Vibration + thermal sensor fusion on all rotating machinery
- **Induction Coil Winding:** Semi-automated winding machine for induction cooker coil assembly

---

## 4. Phase 3 — Autonomy: Lights-Out Small Appliances & AI Scheduling (2030–2031)

**Theme:** Achieve lights-out manufacturing on the highest-volume small domestic appliance lines (blenders, kettles, rice cookers); implement AI-driven full-factory scheduling; integrate supply chain AI.

**Prerequisite:** Phase 2 OEE ≥ 83%; digital twin ≥ 90% coverage; AI models production-validated.

### 4.1 Phase 3 Milestones

| # | Milestone                                            | Target Date | KPI                                   | Success Criteria                                              | Status  |
|---|------------------------------------------------------|-------------|---------------------------------------|---------------------------------------------------------------|---------|
| 1 | Lights-out trial — Blender/Kettle line, Night Shift   | Q1 2030     | Unattended operation ≥ 4 hours        | Zero defects, zero incidents; MES data complete               | Planned |
| 2 | Full lights-out — Blender + Kettle + Rice Cooker line | Q3 2030     | Night shift fully unattended          | 3 SDA lines run every night; remote NOC monitoring            | Planned |
| 3 | AI-driven MRP and supply ordering (auto PO)          | Q2 2030     | PO generation accuracy                | AI generates 90% of POs within agreed parameters              | Planned |
| 4 | Phase 3 capacity: 1,680,000 units/year               | Q2 2031     | Total factory output                  | Sustained for 3 consecutive months                            | Planned |
| 5 | Net-Zero Energy certification                        | Q4 2031     | Annual CO₂ report                     | Verified net-zero for factory operations (Scope 1 + 2)        | Planned |

### 4.2 Phase 3 KPIs

| KPI                              | Phase 2 End | Target (Phase 3 End) |
|----------------------------------|-------------|----------------------|
| OEE (blended)                    | ≥ 83%       | ≥ 90%                |
| First-Pass Yield (SDA lines)     | ≥ 97%       | ≥ 99%                |
| Total Production Volume          | 980K/yr     | 1,680K/yr            |
| Lights-Out Hours (SDA lines)     | 0%          | ≥ 50% (night shifts) |
| Solar Self-Sufficiency           | ≥ 80%       | ≥ 90%                |

---

## 5. Workforce Transition Plan

| Phase   | Workforce Impact                                  | Mitigation                                                        |
|---------|---------------------------------------------------|-------------------------------------------------------------------|
| Phase 1 | Net job creation (new factory)                    | N/A — all new hires; Coo-Cah Manufacturing Academy onboarding     |
| Phase 2 | Foam injection robots replace 8 manual stations  | Reskilling programme → robotics technician roles                  |
| Phase 3 | Night-shift reduction on SDA lights-out lines    | Redeployment to expanding Phase 3 refrigerator/cooker lines       |

---

*For MES integration details, refer to [`mes-integration.md`](./mes-integration.md).*
*For digital twin capabilities, refer to [`digital-twin.md`](./digital-twin.md).*
