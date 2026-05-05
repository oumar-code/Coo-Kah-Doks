# Coo-Cah Fine Chemicals Factory — Machinery & Equipment Register

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Fine Chemicals Factory | **Location:** Asaba Industrial Estate, Delta State, Nigeria | **Phase:** Phase 2
> **Document Version:** 1.0 | **Owner:** Engineering & Maintenance Team

---

## 1. Overview

This document registers the principal process plant and equipment for the Coo-Cah Fine Chemicals Factory. Equipment selection follows international chemical engineering standards (IEC, ISO, ASME) with preference for proven suppliers offering Nigerian service agent support.

---

## 2. Core Process Equipment

| # | Equipment Description                        | Capacity / Rating     | OEM / Source           | Quantity | Zone  |
|---|----------------------------------------------|-----------------------|------------------------|----------|-------|
| 1 | Primary reactor / reaction vessel            | Process-specific      | Import (EU/USA/China)  | 2–4      | Z2    |
| 2 | Heat exchangers (shell-and-tube)             | Process-specific      | Import (UK/India)      | 4–8      | Z2    |
| 3 | Distillation column(s)                       | Process-specific      | Import (Germany/China) | 1–3      | Z2    |
| 4 | Storage tanks (raw material + product)       | 50–500 m³             | Local fabrication      | 6–20     | Z1/Z5 |
| 5 | Process pumps (centrifugal + positive disp.) | Process-specific      | Grundfos / Flowserve   | 10–25    | Z2    |
| 6 | Compressors (process + instrument air)       | Process-specific      | Atlas Copco / Ingersoll| 2–6      | Z2    |
| 7 | Filtration / separation units                | Process-specific      | Import (EU)            | 3–8      | Z3    |
| 8 | Bagging / filling line (bulk products)       | 5–50 tonnes/hour      | Import (China/EU)      | 2–4      | Z4    |
| 9 | Cooling tower / chiller system               | Process-specific      | BAC / SPX              | 1–2      | Z6    |
| 10| Waste treatment plant                        | Full effluent load    | Local + Import         | 1 system | Z7    |

---

## 3. Instrumentation & Control

| Category                      | Description                                                  |
|-------------------------------|--------------------------------------------------------------|
| Process Control System (DCS)  | Honeywell Experion or Siemens PCS 7 — full plant DCS        |
| Safety Instrumented System    | SIL 2 rated SIS for all critical safety loops               |
| Field Instruments             | Endress+Hauser / Yokogawa — temperature, pressure, flow, level |
| Gas Detection                 | Fixed electrochemical + IR sensors at all hazard points      |
| CCTV + Access Control         | Coo-Cah Security Electronics — IP cameras throughout        |
| Emergency Shutdown (ESD)      | Hardwired ESD system; independent of DCS                    |

---

## 4. Utilities

| Utility                    | Source / Generation                              | Backup                          |
|----------------------------|--------------------------------------------------|---------------------------------|
| Electrical Power           | Solar PV + BESS + Grid (BEDC/NEDC)               | Diesel generator                |
| Process Steam              | Fire-tube boiler (gas-fired or dual-fuel)        | Backup boiler                   |
| Cooling Water              | Cooling tower + make-up from borehole            | Chiller backup for critical     |
| Instrument Air             | Atlas Copco compressed air + dryer + receiver    | N₂ purge backup (critical)      |
| Nitrogen (inert blanket)   | PSA nitrogen generator on-site                  | Cylinder bank backup            |
| Process Water              | Borehole + treatment plant (reverse osmosis)     | Municipal water backup          |

---

*Refer to [`energy-profile.md`](./energy-profile.md) for energy infrastructure details.*
*Refer to [`floor-plan.md`](./floor-plan.md) for zone layout.*
