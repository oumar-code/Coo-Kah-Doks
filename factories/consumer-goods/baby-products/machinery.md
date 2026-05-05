# Coo-Cah Baby & Infant Products Factory — Machinery & Equipment Register

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Baby & Infant Products Factory | **Location:** Sagamu Industrial Estate, Ogun State, Nigeria | **Phase:** Phase 2
> **Document Version:** 1.0 | **Owner:** Engineering & Maintenance Team

---

## 1. Overview

This document registers the principal production equipment for the Coo-Cah Baby & Infant Products Factory. Equipment selection follows international food/consumer goods standards (ISO, Codex Alimentarius, GMP) with CE-marked machinery where applicable.

---

## 2. Core Production Equipment

| # | Equipment Description                       | Capacity / Rating     | OEM / Source              | Qty | Zone |
|---|---------------------------------------------|-----------------------|---------------------------|-----|------|
| 1 | Primary production line (batch or continuous)| Process-specific     | Import (EU/China)         | 2–4 | Z2   |
| 2 | Mixing / blending vessels                   | 500–10,000 L          | Import (Italy/Germany)    | 2–4 | Z2   |
| 3 | Filling and dosing line                     | 60–600 units/min      | Import (Italy/China)      | 1–2 | Z3   |
| 4 | Capping / sealing machine                   | 60–400 units/min      | Import (Germany/China)    | 1–2 | Z3   |
| 5 | Primary packaging (labelling)               | 100–500 units/min     | Import (Germany/Italy)    | 1–2 | Z3   |
| 6 | Secondary packaging (carton + shrink wrap)  | 20–100 cartons/min    | Import (China)            | 1–2 | Z4   |
| 7 | Conveyors (product + packing)               | Various               | Local + Import            | 6–12| Z2–Z4|
| 8 | QC Laboratory equipment                     | Full analytical suite  | Shimadzu / Mettler Toledo | 1 set| Z8  |
| 9 | CIP (Clean-In-Place) system                 | Process-specific       | Import (SPX/Alfa Laval)   | 1   | Z7   |
| 10| AMR Fleet for WIP and FGW transport         | Various               | MiR Fleet                 | 6–12| All  |

---

## 3. Instrumentation & Control

| Category                      | Description                                           |
|-------------------------------|-------------------------------------------------------|
| SCADA / MES Integration       | Siemens Opcenter Execution Discrete (batch variant)  |
| Process Weighing / Dosing     | Mettler Toledo ICS checkweigher + batching controller |
| Metal Detection / X-Ray       | Mettler Safeline metal detector on all filling lines  |
| Temperature Monitoring        | Thermocouple + BLE sensors throughout cold chain      |
| Barcode + Vision Inspection   | Cognex vision; label check; fill level AI vision      |
| Traceability                  | Batch serialisation; GS1 compliant barcodes           |

---

## 4. Utilities

| Utility             | Source                                    | Backup                   |
|---------------------|-------------------------------------------|--------------------------|
| Electrical Power    | Solar PV + BESS + Grid                    | Diesel generator         |
| Process Water       | Borehole + RO treatment (food grade)      | Municipal backup         |
| Steam / Hot Water   | Gas-fired boiler (natural gas or LPG)     | Electric backup heater   |
| Chilled Water       | Industrial chiller (cold storage + CIP)   | Brine tank backup        |
| Compressed Air      | Atlas Copco oil-free compressor           | Receiver tank backup     |
| CO₂ (food grade)    | BOC / Linde Nigeria supply                | Cylinder bank            |

---

*Refer to [`energy-profile.md`](./energy-profile.md) for energy infrastructure details.*
