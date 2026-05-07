# Coo-Cah Smart Estate & City Electronics Factory — Executive Summary

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Vertical:** Electronics — Smart City & Estate Infrastructure | **Location:** Lekki Free Trade Zone (LFTZ), Lagos State, Nigeria | **Phase:** Phase 1
> **Document Version:** 1.0 | **Status:** In Development

---

## 1. Factory Overview

The Coo-Cah Smart Estate & City Electronics Factory is a purpose-built manufacturing facility for smart metering, estate automation, and urban infrastructure electronics — the foundational hardware layer of Nigeria's emerging smart city ecosystem. Located within the Lekki Free Trade Zone (LFTZ) in Lagos State, the facility benefits from duty-free importation of components and equipment, a 100% corporate tax exemption under the Nigeria Export Processing Zones Act, and access to the LFTZ's superior infrastructure compared to standard Nigerian industrial estates.

Nigeria's electricity distribution sector faces a structural reform challenge: millions of unmetered consumers, mass revenue leakage through meter bypassing and estimated billing, and a capital-constrained DisCo (Distribution Company) sector unable to self-fund the required meter rollout. The Federal Government's Meter Asset Provider (MAP) framework and the National Mass Metering Programme (NMMP) together represent a demand pipeline of over 10 million smart meters in the medium term. Coo-Cah's CCE-SM-ELEC and CCE-SM-WATER product lines are positioned to capture a significant share of this government-driven procurement cycle, while the CCE-SEH, CCE-SPS, CCE-CTC, CCE-ESN, and CCE-LORA-GW product lines address the rapidly growing smart estate development and state-level smart city investment market (Lagos Smart City Programme, Abuja Smart City, Rivers State Smart Infrastructure).

The factory is designed as a smart factory from inception: dual SMT PCB assembly lines feed dedicated product assembly lines for each of the seven product families, all tied together by the Coo-Cah MES platform, a 10-unit AMR fleet for material handling, and a 600 kWp solar + 650 kWh BESS energy system that targets ≥80% energy self-sufficiency.

| Attribute                  | Details                                                                   |
|----------------------------|---------------------------------------------------------------------------|
| Factory Name               | Coo-Cah Smart Estate & City Electronics Factory                           |
| Location                   | Lekki Free Trade Zone (LFTZ), Lagos State, Nigeria                        |
| Vertical                   | Electronics — Smart Metering, Estate IoT & Urban Infrastructure           |
| Phase                      | Phase 1                                                                   |
| Facility Area              | ~14,000 m²                                                                |
| Construction Target        | Q2 2026                                                                   |
| Production Start Target    | Q4 2026                                                                   |
| Employees (Phase 1)        | ~320 direct; ~70 indirect                                                 |
| Quality Standard           | ISO 9001:2015; IEC 62053-21/22; IEC 62056 (DLMS/COSEM); SON NIS; NCC Type Approval; IEC 62386 |
| Energy Strategy            | 600 kWp Solar (rooftop + car park canopy) + 650 kWh LFP BESS + Grid + 400 kVA Perkins backup |
| Free Zone Status           | NEPZA-licensed Free Zone Enterprise — duty-free imports, 100% tax holiday |

---

## 2. Products

### 2.1 Product Portfolio

| # | Product Name                              | SKU Code        | Target Market                                          | Phase    |
|---|-------------------------------------------|-----------------|--------------------------------------------------------|----------|
| 1 | Coo-Cah Smart Meter (Electricity)         | CCE-SM-ELEC     | DisCos (AEDC, EKEDC, IBEDC, etc.), smart estates       | Phase 1  |
| 2 | Coo-Cah Smart Meter (Water)               | CCE-SM-WATER    | State water boards, smart estate developers, councils  | Phase 1  |
| 3 | Coo-Cah Smart Estate Hub                  | CCE-SEH         | Gated estate developers, estate management companies   | Phase 1  |
| 4 | Coo-Cah Smart Pole System                 | CCE-SPS         | State govts, LGAs, smart city project contractors      | Phase 1  |
| 5 | Coo-Cah City Traffic Controller           | CCE-CTC         | State ministries of transport, LASG, FCT FCDA          | Phase 1  |
| 6 | Coo-Cah Environmental Sensor Node         | CCE-ESN         | State EPAs, smart city projects, research institutions | Phase 1  |
| 7 | Coo-Cah LoRaWAN IoT Gateway               | CCE-LORA-GW     | Smart estate developers, city IoT project integrators  | Phase 1  |

### 2.2 Key Product Descriptions

**Coo-Cah Smart Meter (Electricity) — CCE-SM-ELEC:** Prepaid single-phase (5–80 A, Class 1 accuracy, IEC 62053-21) and three-phase (100 A, IEC 62053-22) smart electricity meters designed for DisCo deployment under the MAP/NMMP frameworks and for private gated estate metering. Supports both AMR (Automated Meter Reading) and AMI (Advanced Metering Infrastructure) modes with GPRS and NB-IoT (Quectel BC660) backhaul. Features tamper detection (magnetic, cover, current reversal), DLMS/COSEM protocol (IEC 62056) for utility head-end system integration, and Consumer Interface Unit (CIU) compatibility via RS-485/STS prepayment token. NERC Meter Code compliant. Class 1 accuracy maintained from 5% to 120% of rated current across –25°C to +70°C operating range. PCB based on Renesas RL78 MCU with Cirrus Logic CS5480/CS5490 metrology IC. Housing: IP54-rated polycarbonate, manufactured by Coo-Cah Plastics Factory.

**Coo-Cah Smart Meter (Water) — CCE-SM-WATER:** Automated water metering unit for DN15 to DN40 pipe sizes, targeting estate water management and council distribution network monitoring. Ultrasonic flow measurement (no moving parts, no maintenance interval), NB-IoT backhaul (Quectel BC660K), IP68-rated brass body with ABS smart lid. Pulse output for legacy system compatibility. Low power design: battery life target ≥10 years (3.6 V lithium primary). MID-compliant metrology (±2% accuracy). Data logged locally at 15-minute intervals; remote tamper alerts. Compatible with CCE-LORA-GW and CCE-SEH for estate-level aggregation.

**Coo-Cah Smart Estate Hub — CCE-SEH:** The central IoT gateway and controller for gated residential estates and commercial complexes. Aggregates data from CCE-SM-ELEC/WATER meters, CCTV cameras, access control panels, intercom systems, and environmental sensors into a single estate management platform. Multi-protocol support: Zigbee 3.0, Z-Wave Plus, Wi-Fi 6 (802.11ax), RS-485 Modbus, and 10/100 Ethernet. Runs local AI edge inference on a Cortex-A55 processor module with 32 GB eMMC storage — enabling intelligent alerts and anomaly detection without cloud dependency. 8-hour battery backup (sealed lead-acid, field-replaceable). DIN-rail or wall-mount enclosure (IP40 indoor). Supports up to 2,000 end devices per hub. OTA firmware updates via encrypted HTTPS.

**Coo-Cah Smart Pole System — CCE-SPS:** An 8-metre hot-dip galvanised steel or aluminium street pole integrating multiple smart city functions in a single installation. Core specification: integrated 2 MP / 30 fps CCTV camera (IP66, IR 30m, H.265), 802.11ac dual-band Wi-Fi access point (supporting 50+ concurrent users), class 2 environmental sensor pod, and DALI-2 LED driver (IEC 62386) for adaptive LED street lighting. Optional 100 W monocrystalline solar panel and 48 V/60 Ah LiFePO₄ battery for off-grid operation. All electronics housed in a sealed IP66 junction box at 3m height. Pole assembly uses standardised base plate flanged for M24 anchor bolt foundations. Connects to city management platform via 4G (primary) or Wi-Fi mesh backhaul.

**Coo-Cah City Traffic Controller — CCE-CTC:** Adaptive traffic signal controller for urban intersection management. NEMA TS2 / ITE ATC-compatible cabinet with 316-grade stainless steel door; 4G/5G cellular connectivity for remote management and firmware updates; video detection input (RS-232/RS-485 to external camera processor); pedestrian push-button interface with accessible audible output; actuated-coordinated traffic plan library (up to 64 plans, 16 phases). Compatible with UTMC/NTCIP standards for central traffic management system integration. Cabinet rated IP55, operating –10°C to +65°C. Surge protection compliant with IEC 61643-11. PCB assembly includes dual-redundant CPU with watchdog; automatic fallback to fixed-time plan on communication loss.

**Coo-Cah Environmental Sensor Node — CCE-ESN:** A compact, solar-powered air quality and environmental monitoring node for smart city deployments. Measures: CO (0–1,000 ppm, electrochemical), NO₂ (0–20 ppm, electrochemical), PM2.5/PM10 (laser particle counter, 0–500 µg/m³), noise level (30–130 dB, calibrated), ambient temperature (–20°C to +60°C, ±0.5°C), and relative humidity (0–100% RH, ±3%). LoRaWAN Class A transmission protocol (Semtech SX1276 module), 868 MHz (deployable on 915 MHz band). 3W monocrystalline solar panel with 3-year lithium backup (LS14500 cells). IP65-rated polycarbonate enclosure (Coo-Cah Plastics Factory). Each CCE-ESN connects to CCE-LORA-GW gateways and can be integrated into Lagos State EPA monitoring networks or smart city data platforms.

**Coo-Cah LoRaWAN IoT Gateway — CCE-LORA-GW:** An 8-channel LoRa concentrator gateway built on the Semtech SX1302/SX1303 chipset, supporting simultaneous reception on 8 LoRa channels (configurable SF7–SF12, 125/250/500 kHz BW). Manages a fleet of up to 10,000 end nodes (CCE-ESN, CCE-SM-WATER, third-party LoRaWAN Class A/B/C devices). Dual backhaul: 4G LTE (primary) and 10/100 Ethernet (secondary). Outdoor-rated IP67 fibreglass enclosure; pole or wall mount. Operating temperature: –40°C to +70°C. Supports LoRaWAN 1.0.4/1.1 network server connectivity (ChirpStack or TTN compatible). Remote management via HTTPS API; automatic channel frequency plan configuration. Compliant with NCC type approval for LoRa 868 MHz operation in Nigeria.

---

## 3. Production Capacity Targets

### 3.1 Annual Volume Targets by Phase

| Product Category                  | Phase 1 (Yr 1–2)  | Phase 2 (Yr 3–4)  | Phase 3 (Yr 5+)   | Unit       |
|-----------------------------------|-------------------|-------------------|-------------------|------------|
| Smart Meters — Electricity        | 350,000           | 700,000           | 1,200,000         | units/year |
| Smart Meters — Water              | 150,000           | 300,000           | 500,000           | units/year |
| **Smart Meters (Combined Total)** | **500,000**       | **1,000,000**     | **1,700,000**     | units/year |
| Smart Estate Hubs (CCE-SEH)       | 50,000            | 120,000           | 200,000           | units/year |
| Smart Pole Systems (CCE-SPS)      | 100,000           | 200,000           | 350,000           | units/year |
| City Traffic Controllers (CCE-CTC)| 30,000            | 60,000            | 100,000           | units/year |
| Environmental Sensor Nodes (CCE-ESN)| 200,000         | 500,000           | 900,000           | units/year |
| LoRaWAN IoT Gateways (CCE-LORA-GW)| 20,000           | 50,000            | 90,000            | units/year |

### 3.2 Production Rate Assumptions

| Parameter                                   | Value                                                            |
|---------------------------------------------|------------------------------------------------------------------|
| Operating Days per Year                     | 300 days (accounting for public holidays and planned shutdowns)  |
| Shifts per Day                              | 2 shifts (Phase 1); 3 shifts (Phase 2+)                         |
| Hours per Shift                             | 8 hours                                                          |
| Overall Equipment Effectiveness (Target)    | 76% (Phase 1); 86% (Phase 2)                                    |
| First-Pass Yield — SMT PCB                  | ≥98.5% (Phase 1); ≥99.2% (Phase 2)                             |
| Smart Meter Calibration Pass Rate           | ≥99.5% on first calibration attempt                             |
| Meter Line Takt Time (single-phase)         | ~35 seconds per unit (steady state)                             |
| Smart Pole Assembly Takt Time               | ~4 minutes per pole                                             |
| Traffic Controller Assembly Cycle           | ~45 minutes per unit                                            |
| SMT Line Throughput (PCBs)                  | ~4,500–6,000 PCBs/day (dual line)                               |

---

## 4. Automation Phase Status

| Phase   | Focus                                                                         | Status       | Target Completion |
|---------|-------------------------------------------------------------------------------|--------------|-------------------|
| Phase 1 | Dual SMT lines; MES live; calibration automation; AMR fleet; energy system    | In Planning  | Q4 2026           |
| Phase 2 | Robotic conformal coating; AI vision QC for meter PCBs; digital twin; PdM     | Planned      | Q2 2028           |
| Phase 3 | Lights-out for ESN/LoRaWAN assembly lines; AI-driven smart city platform sync | Planned      | Q4 2029           |

**Current Phase:** Phase 1 — Planning & Design
**Phase 1 Automation Level:** Level 3 — Connected (MES live, semi-automated assembly, fully-automated SMT lines, automated calibration benches, AMR material handling throughout)

---

## 5. Energy Profile Summary

The Smart Estate & City Factory's energy profile is characterised by continuous 24-hour loads on calibration benches (IEC 62053 accuracy testing requires prolonged stabilisation periods), alongside standard HVAC and SMT line loads during production shifts. The LFTZ location provides more reliable grid supply than typical Lagos industrial zones, reducing dependence on diesel generation, though the solar + BESS system is designed to achieve ≥80% self-sufficiency.

| Metric                            | Value                                        |
|-----------------------------------|----------------------------------------------|
| Facility Area                     | ~14,000 m²                                   |
| Estimated Peak Load               | ~380 kW                                      |
| Daily Energy Consumption          | ~2,500 kWh/day (dual-shift, 16h operational) |
| Recommended Solar PV              | 600 kWp (rooftop + car park canopy)          |
| Recommended BESS                  | 650 kWh LFP (Lithium Iron Phosphate)         |
| Grid Backup Role                  | Peak shaving + overnight top-up              |
| LFTZ Grid Reliability             | 18–20h supply/day (better than Lagos average)|
| Lagos Irradiance                  | 4.5 Peak Sun Hours/day (conservative)        |
| Target Solar Self-Sufficiency     | ≥80% of operational energy                   |
| Backup Generator                  | 1 × Perkins 400 kVA diesel                  |
| Annual CO₂ Avoidance (est.)       | ~520 tonnes CO₂/year                         |

**Major loads:** SMT Reflow Ovens ×2 (56 kW combined), Smart Meter Calibration Benches ×4 (20 kW, 24h), HVAC (74 kW), Compressed Air ×2 (35 kW), Lighting LED (22 kW), Smart Pole Assembly & Welding (28 kW), General Production Machinery (30 kW), MES/IT Servers (11 kW, 24h).

See [`energy-profile.md`](./energy-profile.md) for full analysis.

---

## 6. Key Supply Dependencies

| Dependency                                       | Phase 1 Source                              | Phase 2+ Target                              |
|--------------------------------------------------|---------------------------------------------|----------------------------------------------|
| Smart Meter Metrology IC (Cirrus Logic CS5480/90)| Imported — Cirrus Logic via HK distributors | Maintain import; dual-source with TI ADE7758  |
| Smart Meter MCU (Renesas RL78/I1D)               | Imported — Renesas Electronics              | Maintain import; dual-source with STM32       |
| NB-IoT Module (Quectel BC660/BC660K)             | Imported — Quectel via HK                   | Maintain import; qualify Fibocom MA510        |
| LoRa Module / SX1276 (Semtech)                   | Imported — Semtech via HK distributor       | Maintain import; dual-source RLXL8            |
| LoRa Concentrator SX1302/SX1303 (Semtech)        | Imported — Semtech via authorised dist.     | Maintain import                              |
| Wi-Fi/BT SoC (Espressif ESP32-S3)                | Imported — Espressif Systems HK             | Maintain import                              |
| LED Driver IC (Macroblock MBI6683 / Inventronics)| Imported — via HK/Taiwan                   | Phase 2: local LED module integration        |
| Bare PCBs (4–6 layer, smart meter / IoT)         | Imported — China/Taiwan PCB fabs            | Phase 3: Coo-Cah PCB line (if justified)    |
| Aluminium extrusions (smart pole sections)       | Local steel service centres + HK imports    | Fully local; qualify Nigerian extruder       |
| Steel pole shaft (8m hot-dip galv.)              | Local fabrication / LFTZ steel centre       | Local long-term                              |
| Plastic enclosures & weatherproof housings       | Coo-Cah Plastics Factory                    | Coo-Cah Plastics Factory (primary)           |
| IP67 gaskets & seals                             | Local rubber supplier / imported            | Local supplier development                   |
| Packaging — Master Cartons                       | Local printer (Lagos)                       | Local long-term                              |
| Packaging — Anti-static bags, trays              | Imported / Local                            | Local supplier development                   |

---

## 7. Team Structure

| Department                         | Phase 1 Headcount | Key Roles                                                   |
|------------------------------------|-------------------|-------------------------------------------------------------|
| Factory Management                 | 6                 | Factory Director, Deputy Factory Mgr, Production Planner, EHS Mgr, Quality Director, Finance Lead |
| SMT/PCB Assembly — Line 1          | 20                | SMT Supervisor, 14 operators, 5 technicians                 |
| SMT/PCB Assembly — Line 2          | 18                | SMT Supervisor, 13 operators, 4 technicians                 |
| Smart Meter Assembly & Test (Elec) | 52                | 2 × Line Supervisors, 38 operators, 12 calibration technicians |
| Smart Meter Assembly & Test (Water)| 20                | Line Supervisor, 14 operators, 5 technicians                |
| Smart Estate Hub Assembly          | 20                | Line Supervisor, 14 operators, 5 technicians                |
| Smart Pole Fabrication & Assembly  | 38                | 2 × Supervisors, 28 operators/welders, 8 technicians        |
| Traffic Controller / ESN / LoRa Line | 28              | 2 × Supervisors, 20 operators, 6 technicians                |
| Calibration Laboratory             | 14                | Cal Lab Manager, 3 Cal Engineers, 10 Cal Technicians        |
| Quality Assurance / IPQC / FQC     | 22                | QA Manager, 2 QA Engineers, 18 QC Inspectors               |
| Maintenance                        | 22                | Maintenance Mgr, 5 Electricians, 5 Mechs, 7 Instrument Techs, 5 Maintenance Tech |
| Supply Chain & Stores              | 16                | SCM Lead, 3 Store Keepers, 4 Logistics Coordinators, 4 Operators |
| IT / MES                           | 6                 | MES Administrator, 2 IT Technicians, Data Analyst, Network Technician |
| EHS                                | 4                 | EHS Officer × 2, First Aider × 2                           |
| HR / Admin                         | 4                 | HR Officer × 2, Admin Assistant × 2                        |
| **Total Direct**                   | **~320**          |                                                             |

*Indirect staff (~70): Factory Director, 8 Sales/BD (DisCo & smart city accounts), 10 Design/NPI Engineers, 5 Finance/Accounting, 6 IT/Digital/AI Engineers, 6 Procurement, 3 Legal/Compliance, 12 Security, 10 Facilities/Canteen, 5 Logistics drivers — reported separately outside direct headcount.*

---

## 8. Key Performance Indicators

| KPI                                           | Phase 1 Target   | Measurement Frequency |
|-----------------------------------------------|------------------|-----------------------|
| Overall Equipment Effectiveness (OEE)         | ≥ 76%            | Daily                 |
| First-Pass Yield — SMT PCB Lines              | ≥ 98.5%          | Per Batch             |
| Smart Meter Calibration Pass Rate (IEC 62053) | ≥ 99.5%          | Per Unit              |
| Defect Rate (DPPM — customer escapes)         | < 1,500 ppm      | Monthly               |
| On-Time Delivery                              | ≥ 93%            | Weekly                |
| Energy Intensity — Smart Meter (elec)         | ≤ 0.6 kWh/unit   | Monthly               |
| Energy Intensity — Smart Pole                 | ≤ 8 kWh/unit     | Monthly               |
| Solar Self-Sufficiency                        | ≥ 80%            | Monthly               |
| MES Data Completeness                         | ≥ 97%            | Daily                 |
| AMR Fleet Utilisation                         | ≥ 78%            | Daily                 |
| Warranty Claim Rate (12-month field)          | < 0.8%           | Quarterly             |
| NCC Type Approval Non-Conformance             | Zero             | Continuous            |
| Lost Time Injury Rate                         | Zero LTI         | Continuous            |

---

## 9. Cross-Factory Dependencies

| Dependency Type | Factory / Division                  | Material / Service                                   | Direction     |
|-----------------|-------------------------------------|------------------------------------------------------|---------------|
| Input           | Coo-Cah Plastics Factory            | IP-rated meter housings, weatherproof enclosures, ABS lids, polycarbonate covers | Inbound |
| Input           | Coo-Cah Personal Electronics        | SMT component supply coordination; PCB NPI expertise | Inbound (shared)    |
| Output          | Nigeria DisCo Utilities (11 DisCos) | CCE-SM-ELEC smart electricity meters                 | Outbound      |
| Output          | Smart Estate Developers             | CCE-SEH, CCE-SM-ELEC/WATER, CCE-ESN                 | Outbound      |
| Output          | LASG Smart Lagos / State Ministries | CCE-SPS, CCE-CTC, CCE-ESN, CCE-LORA-GW              | Outbound      |
| Output          | Federal Smart City Projects         | Full smart city product portfolio                    | Outbound      |
| Shared          | Coo-Cah AI Platform                 | MES, Digital Twin, Predictive Analytics, Scheduling  | Bidirectional |

---

## 10. Sub-Document Index

| Document                                             | Description                                                                       |
|------------------------------------------------------|-----------------------------------------------------------------------------------|
| [`machinery.md`](./machinery.md)                     | Full equipment register: dual SMT lines, meter calibration benches, pole assembly jigs, conformal coating, potting |
| [`energy-profile.md`](./energy-profile.md)           | 380 kW peak demand analysis, 600 kWp solar + 650 kWh BESS design calculation      |
| [`floor-plan.md`](./floor-plan.md)                   | 14,000 m² layout: SMT zones, meter assembly, estate hub, smart pole, calibration lab, FGW |
| [`automation-roadmap.md`](./automation-roadmap.md)   | Phase milestones: MES, AMR, calibration automation, AI vision QC, digital twin, lights-out ESN/LoRa lines |
| [`mes-integration.md`](./mes-integration.md)         | MES data points, API endpoints (incl. calibration cert API), AI services, data security |
| [`supply-chain.md`](./supply-chain.md)               | Component sourcing: Renesas/Cirrus Logic ICs, Semtech LoRa, Quectel NB-IoT, local pole fabrication; LFTZ import procedures |
| [`regulatory.md`](./regulatory.md)                   | IEC 62053/62056 smart meter certs, NCC Type Approval, NERC metering code, SON NIS, LFTZ tax incentives |
| [`capex-opex.md`](./capex-opex.md)                   | Phase 1 CapEx ~₦14.4 bn, annual OpEx model, unit economics, payback and sensitivity analysis |
| [`digital-twin.md`](./digital-twin.md)               | Asset registry (DT-SEC-xxx IDs), sensor coverage, simulation use cases incl. meter calibration drift prediction |
| [`docs/sensor-map.md`](./docs/sensor-map.md) | Standalone physical sensor registry (model, zone, protocol, calibration) |
| [`docs/bim/README.md`](./docs/bim/README.md) | BIM/3D model stub index, zone boundaries, and asset anchors |
---

*This document is part of the Coo-Cah Manufacturing Ecosystem documentation suite.*
