# Coo-Cah Metallurgical & Minerals Factory — Automation Roadmap

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Metallurgical & Minerals Factory | **Location:** Warri / Ovwian-Aladja Steel Corridor, Delta State, Nigeria | **Phase:** Phase 2
> **Document Version:** 1.0 | **Owner:** Coo-Cah Technology & Operations Division

---

## 1. Automation Strategy Overview

Chemical manufacturing automation follows a different paradigm from discrete electronics assembly. The primary automation layer is the **Distributed Control System (DCS)** and **Safety Instrumented System (SIS)**, which are present from Day 1. Subsequent phases extend to AI-driven process optimisation, predictive maintenance, and digital twin integration.

| Phase | Period      | Theme                                               | Investment (₦B) | Focus                             |
|-------|-------------|-----------------------------------------------------|-----------------|-----------------------------------|
| 1     | Phase 1–2   | Foundation: DCS, SIS, MES, energy management        | Included in CapEx| DCS commissioning; MES batch mgmt |
| 2     | Phase 2–3   | AI Optimisation: yield AI; predictive maintenance   | 0.5–1.5B        | AI process control; DT live       |
| 3     | Phase 3+    | Autonomous: self-optimising process control         | 0.5–1.0B        | AI DCS integration; lights-out ops|

---

## 2. Phase 1 — Foundation: DCS + SIS + MES

### 2.1 Control System Foundation

| System                        | Description                                                     | Status  |
|-------------------------------|-----------------------------------------------------------------|---------|
| DCS — Honeywell Experion/Siemens PCS 7 | Full plant distributed control: PID loops, sequence, alarm | Phase 1 |
| SIS — SIL 2                  | Independent safety shutdown system; HAZOP-validated loops       | Phase 1 |
| SCADA / Historian             | OSIsoft PI or Coo-Cah Digital Twin — all process tags recorded  | Phase 1 |
| Batch Management (MES)        | Recipe-driven batch production; batch records for QA/QC         | Phase 1 |
| Energy Management System      | Solar + BESS + grid optimisation integrated with DCS            | Phase 1 |
| Laboratory LIMS               | Lab Information Management System; CoA auto-generation          | Phase 1 |
| Gas Detection Network         | Fixed detection; DCS-integrated alarm + ESD trigger             | Phase 1 |

### 2.2 Phase 1 Key Milestones

| # | Milestone                                    | Target        | Status  |
|---|----------------------------------------------|---------------|---------|
| 1 | Civil works + site services complete         | See project schedule | Planned |
| 2 | DCS hardware and software commissioned       | +6 months     | Planned |
| 3 | SIS loop testing + proof test complete       | +8 months     | Planned |
| 4 | Process plant start-up + steady-state ops    | +10–14 months | Planned |
| 5 | MES batch management live                    | +12 months    | Planned |
| 6 | Solar + BESS commissioned                    | +14 months    | Planned |
| 7 | NESREA operational permits issued            | +14 months    | Planned |
| 8 | ISO 9001 + ISO 14001 certified               | +18 months    | Planned |

---

## 3. Phase 2 — AI Process Optimisation

### 3.1 AI Use Cases (Chemical Process)

| AI Use Case                         | Description                                                   | Expected Benefit              |
|-------------------------------------|---------------------------------------------------------------|-------------------------------|
| Yield Optimisation AI               | ML model optimises reaction conditions (temperature, pressure, feed ratio) | 2–5% yield improvement |
| Predictive Maintenance              | Vibration + process data fusion for pump, compressor, heat exchanger | MTBF improvement ≥ 25% |
| Energy Cost Optimisation            | AI schedules high-energy processes around solar availability  | 8–15% energy cost reduction   |
| Quality Prediction                  | Real-time purity prediction before offline lab analysis       | QC lab turnaround -60%        |
| Anomaly Detection                   | DT vs. DCS delta monitoring; early fault detection            | Unplanned downtime -30%       |

---

## 4. Phase 3 — Autonomous Process Control

**Phase 3 Target:** AI-driven DCS setpoint adjustment approved for selected non-critical loops; operator oversight retained for SIS-adjacent loops. Net effect: 24/7 process optimisation without continuous operator manual input.

**Prerequisite:** Phase 2 AI models validated for ≥ 12 months; regulatory review by NESREA for AI process control.

---

## 5. Workforce Technology Plan

| Phase   | Technology Added                  | Workforce Impact                                    |
|---------|-----------------------------------|-----------------------------------------------------|
| Phase 1 | DCS + SIS + MES                   | All operators trained on DCS; no job displacement   |
| Phase 2 | AI yield + PdM                    | Data Scientist role added; existing operators upskilled |
| Phase 3 | Autonomous setpoint control       | Shift supervisor role evolves to AI system oversight |
