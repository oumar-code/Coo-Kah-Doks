# Security Electronics Factory — Automation Roadmap

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Security Electronics Factory | **Location:** Ikorodu Industrial Estate, Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Coo-Cah Technology & Operations Division

---

## 1. Automation Strategy Overview

The Security Electronics Factory is the smallest and most precision-intensive factory in the electronics vertical, producing IP cameras, NVRs, access control systems, and AI surveillance platforms. The automation roadmap prioritises optical calibration of camera lens assemblies (Phase 2 robotics) and lights-out PCB sub-assembly for the high-volume IP camera line (Phase 3). The AI-native NVR product (CCX-AI-NVR) requires specialised deep-learning model deployment testing — a unique Phase 1 capability.

| Phase | Period      | Theme                                           | Investment (₦B) | Target OEE | Headcount Change |
|-------|-------------|-------------------------------------------------|-----------------|------------|------------------|
| 1     | 2025–2026   | Foundation: SMT, MES, AMR fleet, AI NVR test   | 0.75            | 70–74%     | +260 direct      |
| 2     | 2027–2028   | Robotics: Camera lens auto-align; AI QC vision | 1.0             | 78–82%     | +30 tech roles   |
| 3     | 2029–2031   | Autonomy: Lights-out IP camera PCB; AI test    | 0.85            | 85–89%     | +15 tech; 18 redeploy |

---

## 2. Phase 1 — Foundation (2025–2026)

### 2.1 Phase 1 Milestones

| # | Milestone                                               | Target Date | KPI                          | Success Criteria                                              | Status  |
|---|---------------------------------------------------------|-------------|------------------------------|---------------------------------------------------------------|---------|
| 1 | Factory civil works complete                            | Q2 2025     | Certificate of Occupancy     | CO issued; cleanroom-grade camera assembly zone ready         | Planned |
| 2 | SMT PCB line installed + qualified                      | Q3 2025     | FAI pass                     | 200 boards defect-free at design throughput                   | Planned |
| 3 | IP Camera assembly line commissioned                    | Q3 2025     | Units/day                    | ≥ 800 IP cameras/day (2MP + 5MP combined)                     | Planned |
| 4 | NVR + DVR assembly line + AI NVR test station           | Q4 2025     | Units/day                    | ≥ 150 NVR/DVR/day; AI NVR deep-learning deploy test < 8 min  | Planned |
| 5 | MES deployed across all zones                           | Q4 2025     | MES coverage                 | ≥ 90% production stations connected                           | Planned |
| 6 | 8-unit AMR fleet operational                            | Q4 2025     | AMR success rate             | ≥ 95% success rate from week 1                                | Planned |
| 7 | NCC Type Approval: 2MP IP camera + Wi-Fi NVR            | Q2 2026     | NCC TA certificates          | Type approval before first commercial shipment                | Planned |
| 8 | Solar 500 kWp + BESS 550 kWh commissioned               | Q2 2026     | Solar self-sufficiency       | ≥ 70% in first 3 months                                       | Planned |
| 9 | ONVIF Profile S + T compliance verified for all cameras | Q3 2026     | ONVIF certification          | ONVIF conformance test pass for all Phase 1 camera SKUs       | Planned |
| 10| Phase 1 OEE target achieved                             | Q4 2026     | Factory OEE                  | Blended ≥ 70%; camera line ≥ 72%; NVR line ≥ 68%            | Planned |

### 2.2 Phase 1 Technology Stack

- **MES:** Siemens Opcenter Execution Discrete — ONVIF compliance tracking module; AI NVR model deployment logging
- **AMR:** 8× MiR100 AMRs (factory is compact — MiR100 appropriate for aisle widths)
- **AI NVR Test Station:** NVIDIA Jetson-powered test server runs inference tests on AI NVR units; results logged to MES
- **Camera Optical Test:** Integrating sphere + collimator for IR illumination characterisation
- **Lens Calibration:** Manual 5-axis alignment stage (Phase 1); robotic in Phase 2

---

## 3. Phase 2 — Robotics & AI Vision (2027–2028)

### 3.1 Phase 2 Milestones

| # | Milestone                                              | Target Date | KPI                          | Success Criteria                                           | Status  |
|---|--------------------------------------------------------|-------------|------------------------------|------------------------------------------------------------|---------|
| 1 | Robotic camera lens auto-alignment station (×2)        | Q1 2027     | Optical alignment accuracy   | MTF (modulation transfer function) pass rate ≥ 99.5%       | Planned |
| 2 | AI vision QC: 100% cosmetic inspection on camera housings | Q2 2027  | Defect detection rate        | ≥ 99% cosmetic detection vs. manual baseline               | Planned |
| 3 | Digital twin live: camera line + NVR line              | Q3 2027     | DT data latency              | All Phase 2 assets; latency ≤ 5 sec                        | Planned |
| 4 | AI NVR face recognition model OTA update workflow      | Q3 2027     | OTA update cycle time        | Model OTA < 15 min; zero failed deployments                | Planned |
| 5 | Phase 2 capacity: 300,000 cameras/year                 | Q1 2028     | Camera units/day             | 1,200 cameras/day sustained 3 months                       | Planned |

---

## 4. Phase 3 — Autonomy (2029–2031)

### 4.1 Phase 3 Milestones

| # | Milestone                                              | Target Date | KPI                          | Success Criteria                                          | Status  |
|---|--------------------------------------------------------|-------------|------------------------------|-----------------------------------------------------------|---------|
| 1 | Lights-out trial: IP Camera PCB SMT (Night Shift)      | Q1 2029     | Unattended ≥ 4h              | Zero defects, zero incidents, MES data complete           | Planned |
| 2 | Full lights-out Camera SMT (nightly)                   | Q3 2029     | Night shift unattended       | SMT runs nightly; remote NOC monitoring                   | Planned |
| 3 | AI-driven test sequencing (NVR deep-learning tests)    | Q2 2030     | Test queue efficiency        | AI schedules 90% of NVR test queue; 15% throughput gain   | Planned |
| 4 | Phase 3 capacity: 500,000+ cameras/year                | Q1 2031     | Annual output                | Sustained 3 months                                        | Planned |

---

## 5. Workforce Transition Plan

| Phase   | Impact                                           | Mitigation                                                     |
|---------|--------------------------------------------------|----------------------------------------------------------------|
| Phase 1 | New factory; net +260 jobs                       | Manufacturing Academy 6-week onboarding; optical skills focus  |
| Phase 2 | Lens alignment robots replace 6 manual stations  | Reskilling to optical robot technician roles                   |
| Phase 3 | Night SMT unattended (reduces 8 operators)       | Redeployment to expanded Phase 3 AI NVR test and QC teams      |
