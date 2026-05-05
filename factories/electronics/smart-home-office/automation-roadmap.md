# Smart Home & Office Electronics Factory — Automation Roadmap

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Smart Home & Office Electronics Factory | **Location:** Agbara Industrial Estate, Lagos State
> **Document Version:** 1.0 | **Owner:** Coo-Cah Technology & Operations Division

---

## 1. Automation Strategy Overview

The Smart Home & Office Electronics Factory operates 2 SMT lines and dedicated product assembly lines for Smart TVs, laptops, routers, smart speakers, home automation hubs, and projectors. The automation programme prioritises the display bonding process (screen-to-chassis) and laptop assembly — the two highest-value, highest-precision tasks — for Phase 2 robotic enhancement.

| Phase | Period      | Theme                                           | Investment (₦B) | Target OEE | Headcount Change |
|-------|-------------|-------------------------------------------------|-----------------|------------|------------------|
| 1     | 2025–2027   | Foundation: 2× SMT, MES, AMR fleet             | 1.4             | 72–75%     | +380 direct      |
| 2     | 2028–2029   | Robotics: Screen bonding cobots; AI vision QC  | 2.0             | 80–84%     | +50 tech roles   |
| 3     | 2030–2031   | Autonomy: Lights-out router/speaker lines; AI scheduling | 1.6    | 87–91%     | +20 tech roles   |

---

## 2. Phase 1 — Foundation (2025–2027)

### 2.1 Phase 1 Milestones

| # | Milestone                                                | Target Date | KPI                          | Success Criteria                                             | Status  |
|---|----------------------------------------------------------|-------------|------------------------------|--------------------------------------------------------------|---------|
| 1 | Factory civil works complete                             | Q2 2025     | Certificate of Occupancy     | CO issued; SMT ESD zones certified                           | Planned |
| 2 | SMT Lines 1 & 2 installed + qualified                    | Q3 2025     | FAI pass (both lines)        | 200 boards each line defect-free at design throughput        | Planned |
| 3 | Smart TV assembly lines 32"/43"/55" commissioned         | Q3 2025     | Units/day target             | ≥ 600 TVs/day across all 3 size lines                        | Planned |
| 4 | Laptop assembly line qualified (14" + 15.6")             | Q4 2025     | Units/day                    | ≥ 300 laptops/day; battery cycle test < 30 min/unit          | Planned |
| 5 | MES deployed across all zones                            | Q4 2025     | MES coverage                 | ≥ 90% stations connected                                     | Planned |
| 6 | AMR fleet (12 units) operational                         | Q4 2025     | AMR mission success          | ≥ 95% success from week 1                                    | Planned |
| 7 | NCC Type Approval: Smart TVs (Android TV) + Wi-Fi routers| Q2 2026     | NCC TA certificates          | All Phase 1 wireless products type-approved                  | Planned |
| 8 | Solar 750 kWp + BESS 800 kWh commissioned                | Q2 2026     | Solar self-sufficiency       | ≥ 72% in first 3 months                                      | Planned |
| 9 | Router + Smart Speaker lines at capacity                 | Q3 2026     | Units/day                    | ≥ 2,000 routers/day; ≥ 1,000 smart speakers/day             | Planned |
| 10| Phase 1 OEE target achieved                              | Q4 2026     | Factory OEE                  | Blended ≥ 72%; TV lines ≥ 68%; router line ≥ 80%            | Planned |

### 2.2 Phase 1 Technology Stack

- **MES:** Siemens Opcenter Execution Discrete — NCC TA tracking module for all wireless products
- **AMR:** 12× MiR250 AMRs — heavy enough for 65" TV panel transport  
- **Android TV CDD Compliance:** ROM validation station linked to MES at laptop/TV lines
- **NCC Pre-Compliance RF Lab:** Access to Personal Electronics RF lab at Sagamu for pre-type-approval testing

---

## 3. Phase 2 — Robotics & AI Vision (2028–2029)

### 3.1 Phase 2 Milestones

| # | Milestone                                              | Target Date | KPI                          | Success Criteria                                           | Status  |
|---|--------------------------------------------------------|-------------|------------------------------|------------------------------------------------------------|---------|
| 1 | Cobot deployment at TV screen bonding stations (×4)    | Q1 2028     | Bonding cycle time           | Bond cycle ≤ 90 sec/TV; cosmetic defect ≤ 0.5%            | Planned |
| 2 | AI vision QC: 100% final inspection on TV panels       | Q2 2028     | Defect detection rate        | ≥ 99.2% cosmetic defect detection                         | Planned |
| 3 | Laptop auto-screw torque (Z5 laptop line)              | Q2 2028     | Torque cycle time            | Torque step < 12 sec/unit; 100% MES-logged                | Planned |
| 4 | Digital twin live: TV lines + laptop line              | Q3 2028     | DT data latency              | ≤ 5 sec lag for all Phase 2 assets                        | Planned |
| 5 | Phase 2 capacity: 120,000 TVs/year                     | Q1 2029     | TV units/day                 | 400 TVs/day sustained for 3 months                        | Planned |

---

## 4. Phase 3 — Autonomy (2030–2031)

### 4.1 Phase 3 Milestones

| # | Milestone                                               | Target Date | KPI                          | Success Criteria                                          | Status  |
|---|---------------------------------------------------------|-------------|------------------------------|-----------------------------------------------------------|---------|
| 1 | Lights-out trial: Router + Smart Speaker lines          | Q1 2030     | Unattended ≥ 4h              | Zero defects, zero incidents                              | Planned |
| 2 | Full lights-out Router + Speaker (nightly)              | Q3 2030     | Night shift unattended       | Both lines nightly; NOC remote monitoring                 | Planned |
| 3 | AI scheduling factory-wide                              | Q2 2030     | Schedule adherence           | AI generates 90% of job sequences; OTD ≥ 95%             | Planned |
| 4 | Phase 3 capacity: 1.8M smart devices/year               | Q1 2031     | Total factory output         | Sustained 3 months                                        | Planned |

---

## 5. Workforce Transition Plan

| Phase   | Impact                                                    | Mitigation                                               |
|---------|-----------------------------------------------------------|----------------------------------------------------------|
| Phase 1 | New factory; net +380 jobs                                | Coo-Cah Manufacturing Academy 6-week onboarding          |
| Phase 2 | Cobots replace 8 screen bonding operators                 | Reskilling to cobot technician / vision system operator  |
| Phase 3 | Router/speaker night shift automated (12 operators)       | Redeployment to Phase 3 new product lines                |

---

*Refer to [`mes-integration.md`](./mes-integration.md) and [`digital-twin.md`](./digital-twin.md) for details.*
