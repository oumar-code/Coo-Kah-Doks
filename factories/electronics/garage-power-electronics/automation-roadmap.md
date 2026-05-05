# Garage & Power Electronics Factory — Automation Roadmap

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Garage & Power Electronics Factory | **Location:** Sagamu Industrial Estate, Ogun State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Coo-Cah Technology & Operations Division

---

## 1. Automation Strategy Overview

The Garage & Power Electronics Factory produces Nigeria's most strategic internal products: inverters and solar charge controllers that power every other Coo-Cah facility. The automation programme is deliberately graduated — Phase 1 builds production capability and MES foundation; Phase 2 adds robotic transformer winding (the most labour-intensive and precision-demanding task); Phase 3 delivers lights-out power strip assembly and AI-driven load bank testing.

| Phase | Period      | Theme                                          | Investment (₦B) | Target OEE | Jobs Created / Transitioned |
|-------|-------------|------------------------------------------------|-----------------|------------|------------------------------|
| 1     | 2025–2026   | Foundation: SMT + MES + Load Bank Automation   | 0.9             | 70–74%     | +280 direct                  |
| 2     | 2027–2028   | Robotics: Coil Winding + AI Vision PCB QC      | 1.4             | 79–82%     | +35 tech roles; 20 redeployed |
| 3     | 2029–2031   | Autonomy: Lights-Out Power Strip + AI Testing  | 1.1             | 86–89%     | +15 tech; 20 redeployed       |

---

## 2. Phase 1 — Foundation (2025–2026)

### 2.1 Phase 1 Milestones

| # | Milestone                                            | Target Date | KPI                         | Success Criteria                                           | Status  |
|---|------------------------------------------------------|-------------|-----------------------------|------------------------------------------------------------|---------|
| 1 | Factory civil works complete; ground solar mount ready | Q2 2025   | Certificate of Occupancy    | CO issued; solar mounting frames installed                 | Planned |
| 2 | SMT PCB line installed + qualified                   | Q3 2025     | FAI pass                    | 200 boards defect-free (0-PPM); line at throughput target  | Planned |
| 3 | Inverter assembly line commissioned (3 lines)        | Q3 2025     | Units/day target            | ≥ 800 inverters/day across all 3 lines                     | Planned |
| 4 | Load bank auto-test system deployed                  | Q3 2025     | Test cycle time             | Full inverter test cycle < 8 min/unit                      | Planned |
| 5 | MES Phase 1 deployed across all zones                | Q4 2025     | MES station coverage        | ≥ 90% stations MES-connected                               | Planned |
| 6 | 12-unit AMR fleet operational                        | Q4 2025     | AMR mission success rate    | ≥ 95% mission success from week 1                          | Planned |
| 7 | 600 kWp ground-mount solar + 700 kWh BESS commissioned | Q1 2026   | Solar self-sufficiency      | ≥ 75% within 3 months of commissioning                     | Planned |
| 8 | Power tool assembly lines live (drill + grinder)     | Q2 2026     | Units/day                   | ≥ 400 power tools/day                                      | Planned |
| 9 | SON NIS + IEC 62040 (UPS) + IEC 61683 type testing complete | Q3 2026 | Certification issued     | All Phase 1 SKUs certified before sale                     | Planned |
| 10| Phase 1 OEE target achieved                          | Q4 2026     | Factory-wide OEE            | ≥ 70% blended; inverter lines ≥ 68%; power strip ≥ 78%    | Planned |

### 2.2 Phase 1 KPIs

| KPI                              | Baseline (Day 1) | Phase 1 Target |
|----------------------------------|------------------|----------------|
| OEE (blended)                    | N/A (new factory) | ≥ 70%         |
| First-Pass Yield (inverters)     | N/A              | ≥ 96%          |
| First-Pass Yield (power strips)  | N/A              | ≥ 98%          |
| Inverter Production Volume       | 0                | 800 units/day  |
| Load Bank Test Cycle Time        | N/A              | < 8 min/unit   |
| Solar Self-Sufficiency           | 0%               | ≥ 75%          |
| MES Data Completeness            | 0%               | ≥ 95%          |

### 2.3 Phase 1 Technology Stack

- **MES:** Siemens Opcenter Execution Discrete — production, WIP, serial traceability, IEC 62040 test records
- **AMR Fleet:** 12× MiR100/200 AMRs for kitting and WIP transport
- **Load Bank Test Automation:** Automated load banks (Cinergia / Ametek) linked via Ethernet to MES
- **EMS:** 600 kWp solar + 700 kWh BESS with full energy management system
- **HMI:** Panel PCs at all inverter and test stations
- **Transformer Winding:** Manual with digital torque/resistance readout → MES data entry in Phase 1

---

## 3. Phase 2 — Robotics: Coil Winding + AI Vision (2027–2028)

**Theme:** Automate transformer and coil winding (the highest-precision manual task); deploy AI vision PCB QC; extend digital twin to inverter assembly cells.

### 3.1 Phase 2 Milestones

| # | Milestone                                               | Target Date | KPI                          | Success Criteria                                         | Status  |
|---|---------------------------------------------------------|-------------|------------------------------|----------------------------------------------------------|---------|
| 1 | CNC transformer winding machines deployed (×2)          | Q1 2027     | Winding accuracy             | Inductance tolerance ±2%; zero shorts on first wind      | Planned |
| 2 | AI vision PCB QC on all SMT output                      | Q2 2027     | Defect detection rate        | ≥ 99% detection vs. manual baseline                      | Planned |
| 3 | Digital twin live: inverter assembly + winding cells    | Q3 2027     | DT sync latency              | All Phase 2 assets in DT; latency ≤ 5 sec               | Planned |
| 4 | Predictive maintenance: SMT oven + winding motor        | Q3 2027     | Unplanned downtime reduction | MTBF improvement ≥ 20%                                   | Planned |
| 5 | Phase 2 capacity: 400,000 inverters/year                | Q1 2028     | Inverter volume              | 1,600 inverters/day sustained for 3 months              | Planned |
| 6 | ISO 14001 environmental certification                   | Q2 2028     | Audit pass                   | No major NCs                                             | Planned |

---

## 4. Phase 3 — Autonomy: Lights-Out Power Strip (2029–2031)

**Theme:** Lights-out night-shift operation for power strip + surge protector lines; AI-driven test scheduling; automatic AI-generated failure diagnostics.

### 4.1 Phase 3 Milestones

| # | Milestone                                             | Target Date | KPI                                | Success Criteria                                      | Status  |
|---|-------------------------------------------------------|-------------|------------------------------------|-------------------------------------------------------|---------|
| 1 | Lights-out trial: Power Strip line (Night Shift)      | Q1 2029     | Unattended operation ≥ 4h          | Zero defects, zero incidents, MES data complete       | Planned |
| 2 | Full lights-out Power Strip + UPS line                | Q3 2029     | Night shift fully unattended       | 2 lines run nightly; remote NOC monitoring            | Planned |
| 3 | AI failure diagnostics (auto root cause analysis)     | Q2 2030     | Diagnosis time                     | 80% of failures auto-diagnosed within 5 min           | Planned |
| 4 | Phase 3 capacity: 700,000 inverters + 1.5M strips/yr  | Q1 2031     | Total factory output               | Sustained 3 consecutive months                        | Planned |

---

## 5. Workforce Transition Plan

| Phase   | Impact                                             | Mitigation                                                      |
|---------|----------------------------------------------------|-----------------------------------------------------------------|
| Phase 1 | Net job creation (new factory, +280)               | Coo-Cah Manufacturing Academy 6-week onboarding                |
| Phase 2 | Winding automation replaces 12 manual winding stations | Reskilling to CNC winding tech operator roles               |
| Phase 3 | Power strip night shift reduced by ~15 operators  | Redeployment to expanded inverter lines + new power tool lines  |

---

*Refer to [`mes-integration.md`](./mes-integration.md) for MES data points.*
*Refer to [`digital-twin.md`](./digital-twin.md) for DT asset registry.*
