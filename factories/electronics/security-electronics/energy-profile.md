# Security Electronics Factory — Energy Profile & Power Systems Design

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Security Electronics Factory | **Location:** Ikorodu Industrial Estate, Lagos State, Nigeria | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Energy & Infrastructure Team

---

## 1. Introduction

This document provides the power demand analysis and renewable energy system design for the Coo-Cah Security Electronics Factory. The factory is sized at ~11,000 m² and manufactures IP security cameras, NVRs, DVRs, access control systems, alarm panels, and video intercom systems. The facility runs one SMT PCB production line, multiple product assembly lines, an 8-unit AMR fleet, and full MES integration.

Coo-Cah's energy mandate requires a minimum of 80% solar self-sufficiency during operational hours and overnight resilience via a properly sized BESS.

---

## 2. Factory Power Demand Analysis

### 2.1 Equipment Load Schedule

| # | Equipment / System | Rated Power (kW) | Duty Cycle (%) | Avg Load (kW) | Operating Hours/Day | Notes |
|---|--------------------|-----------------|----------------|---------------|---------------------|-------|
| 1 | SMT Line (Printer + Pick-Place + Reflow + AOI) | 60 | 85% | 51 | 16 | Two-shift SMT operation |
| 2 | Camera Housing Assembly Lines (×3) | 30 | 80% | 24 | 16 | Semi-automated assembly |
| 3 | NVR / DVR Assembly Line | 20 | 80% | 16 | 16 | Board + mechanical assembly |
| 4 | Access Control / Alarm Assembly | 15 | 70% | 10.5 | 16 | Mixed product lines |
| 5 | Optical & RF Test Chambers (CCTV test) | 25 | 75% | 18.8 | 16 | Camera functional test, lens test |
| 6 | ICT / Functional Test Stations | 15 | 80% | 12 | 16 | Board-level test |
| 7 | AMR Fleet (8× MiR100) Charging | 20 | 40% | 8 | Overnight | Scheduled overnight charging |
| 8 | HVAC / Climate Control | 80 | 90% | 72 | 20 | Continuous production + office |
| 9 | Lighting — Production | 25 | 100% | 25 | 16 | LED, high-bay |
| 10 | Lighting — Offices / Welfare | 10 | 80% | 8 | 12 | LED, occupancy sensors |
| 11 | Compressed Air System | 22 | 65% | 14.3 | 16 | Pneumatic tools, cleaning |
| 12 | IT / MES / Servers / Network | 18 | 100% | 18 | 24 | 24/7 base load |
| 13 | Packaging Line | 15 | 75% | 11.3 | 16 | Carton erector, sealer, labeller |
| 14 | General / Miscellaneous | 20 | 60% | 12 | 16 | Small tools, hand equipment |

### 2.2 Total Power Summary

| Parameter | Value | Notes |
|-----------|-------|-------|
| Sum of Rated Powers | ~375 kW | Nameplate installed capacity |
| **Estimated Peak Simultaneous Load** | **~285 kW** | Demand factor 0.76 applied |
| Average Operational Load | ~220 kW | Weighted average across shift |
| Off-Shift Base Load (IT/HVAC/security) | ~35 kW | Overnight continuous loads |
| **Daily Energy Consumption** | **~3,250 kWh/day** | 16h operation + 8h base load |
| **Annual Energy Consumption** | **~910 MWh/year** | 252 operating days |
| Power Factor (target) | ≥ 0.95 | PFC capacitor banks installed |

---

## 3. Solar Site Assessment

### 3.1 Location Irradiance Data

| Parameter | Value | Source |
|-----------|-------|--------|
| Factory Location | Ikorodu Industrial Estate, Lagos State |  |
| Latitude / Longitude | 6.65° N, 3.62° E |  |
| Peak Sun Hours (PSH) — Annual Avg | 4.6 hrs/day | NASA POWER |
| Peak Sun Hours — Worst Month | 3.8 hrs/day | December |
| Peak Sun Hours — Best Month | 5.4 hrs/day | February/March |
| Avg Daily GHI | 5.2 kWh/m²/day | SolarGIS |

### 3.2 Roof / Ground Area Assessment

| Zone | Available Area (m²) | Usable for Solar (m²) | Est. Capacity |
|------|--------------------|-----------------------|--------------|
| Factory Roof — Main Production | 4,800 m² | 3,800 m² | ~570 kWp |
| Warehouse / Goods-In Roof | 1,200 m² | 900 m² | ~135 kWp |
| Ground / Car Park (optional) | 400 m² | 350 m² | ~50 kWp |
| **Total Available** | **6,400 m²** | **5,050 m²** | **~755 kWp** |

---

## 4. Recommended Energy System

### 4.1 Solar PV Sizing

```
Daily Demand:          3,250 kWh/day
Target Solar Supply:   80% = 2,600 kWh/day
Peak Sun Hours:        3.8 hrs/day (worst month basis)
System Efficiency:     0.89

Required PV Capacity = 2,600 ÷ 3.8 ÷ 0.89 = 769 kWp
Rounded to:           500 kWp (Phase 1 — rooftop only)
                      Note: 500 kWp covers >80% on average days;
                      worst-month deficit covered by grid + BESS
```

| Parameter | Specification |
|-----------|--------------|
| Installed Capacity (Phase 1) | 500 kWp |
| Panel Technology | Monocrystalline PERC, ≥ 21% efficiency |
| Panel Wattage | 580 W per panel |
| Number of Panels | ~862 panels |
| Inverter Type | Hybrid string inverter (solar + BESS integrated) |
| Inverter Capacity | 5× 100 kW hybrid inverters |
| Inverter Brand (target) | Sungrow SH100T / Huawei SUN2000 |
| Estimated Annual Yield | ~720 MWh/year |

### 4.2 Battery Energy Storage System (BESS)

```
Overnight Base Load:    35 kW × 10 hrs = 350 kWh
Morning Ramp Load:      80 kW × 2 hrs  = 160 kWh
Emergency Reserve:      50 kWh (30 min critical load)
Total Gross Required:   560 kWh
Adjusted for DoD:       560 ÷ 0.80      = 700 kWh
Adjusted for Efficiency: 700 ÷ 0.95    = 737 kWh

Recommended BESS: 550 kWh usable (conservative Phase 1; expand to 750 kWh in Phase 2)
```

| Parameter | Specification |
|-----------|--------------|
| Usable Capacity | 550 kWh |
| Chemistry | LFP (Lithium Iron Phosphate) |
| Cycle Life | ≥ 3,500 cycles @ 80% DoD |
| Form Factor | 19" rack-mount, dedicated fire-rated BESS room |
| Preferred Suppliers | CATL EnerOne / BYD Battery-Box |
| Fire Suppression | FM-200 in BESS room |
| Warranty | ≥ 10 years / ≥ 3,500 cycles |

### 4.3 Grid Connection

| Parameter | Specification |
|-----------|--------------|
| Grid Supply | Ikeja Electric (IE) DisCo — 11 kV intake |
| Contracted Demand | 300 kW |
| Role | Secondary backup + peak shaving top-up |
| Smart Meter | Bidirectional, ToU-capable |
| ATS Response | < 100 ms switchover |

### 4.4 Backup Generator

| Parameter | Specification |
|-----------|--------------|
| Generator Capacity | 400 kVA standby (Perkins / Cummins) |
| Fuel | Diesel |
| Auto-Start | BESS SoC < 15% or grid + solar failure |
| Runtime (full tank) | ≥ 72 hrs at 75% load |
| Tank Capacity | 2,000 L |

---

## 5. Energy KPIs

| KPI | Target | Frequency |
|-----|--------|-----------|
| Solar Self-Sufficiency Ratio | ≥ 80% | Monthly |
| Grid Import (% of total energy) | ≤ 20% | Monthly |
| BESS Utilisation | ≥ 250 cycles/year | Annual |
| Energy Intensity (kWh/unit — camera) | ≤ 2.5 kWh/unit | Monthly |
| Generator Run Hours | < 100 hrs/year | Annual |
| Solar System Availability | ≥ 98% | Monthly |
| CO₂ Avoided | ~650 t/year | Annual |
| Power Factor | ≥ 0.95 | Monthly |

---

## 6. Annual CO₂ Avoidance

| Parameter | Value |
|-----------|-------|
| Solar Annual Yield | ~720 MWh/year |
| Nigerian Grid Emission Factor | ~0.90 kgCO₂/kWh (NERC data) |
| **Estimated Annual CO₂ Avoided** | **~648 tonnes CO₂/year** |

---

*For machine-level power ratings, refer to [`machinery.md`](./machinery.md).*
*For digital twin energy monitoring integration, refer to [`digital-twin.md`](./digital-twin.md).*
*For energy-related CapEx and OpEx, refer to [`capex-opex.md`](./capex-opex.md).*
