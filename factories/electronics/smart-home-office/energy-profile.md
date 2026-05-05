# Smart Home & Office Electronics Factory — Energy Profile & Power Systems Design

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Smart Home & Office Electronics Factory | **Location:** Agbara Industrial Estate, Lagos State, Nigeria | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Energy & Infrastructure Team

---

## 1. Introduction

This document provides the power demand analysis and renewable energy system design for the Coo-Cah Smart Home & Office Electronics Factory. The factory is sized at ~16,000 m² and manufactures smart TVs, smart speakers, home automation hubs, smart projectors, smart displays, Wi-Fi routers, mesh systems, and laptop computers. It operates dual SMT PCB assembly lines and multiple product assembly lines, a 12-unit AMR fleet, and full MES integration.

Coo-Cah's energy mandate requires a minimum of 80% solar self-sufficiency during operational hours and overnight resilience via a properly sized BESS.

---

## 2. Factory Power Demand Analysis

### 2.1 Equipment Load Schedule

| # | Equipment / System | Rated Power (kW) | Duty Cycle (%) | Avg Load (kW) | Operating Hours/Day | Notes |
|---|--------------------|-----------------|----------------|---------------|---------------------|-------|
| 1 | SMT Line 1 (TV / Hub boards) — Printer + PnP ×2 + Reflow + AOI | 80 | 85% | 68 | 16 | Primary SMT for large PCBs |
| 2 | SMT Line 2 (Router / Display boards) — Printer + PnP ×2 + Reflow + AOI | 80 | 85% | 68 | 16 | Secondary SMT line |
| 3 | Smart TV Assembly Lines (×2) | 60 | 80% | 48 | 16 | Screen bonding, chassis, QC |
| 4 | Smart Speaker Assembly Line | 25 | 75% | 18.75 | 16 | Speaker driver, housing, test |
| 5 | Laptop Assembly Line | 40 | 80% | 32 | 16 | Board-in, keyboard, screen, test |
| 6 | Router / Hub / Display Assembly | 30 | 75% | 22.5 | 16 | Mixed small-device assembly |
| 7 | Projector Assembly Line | 20 | 70% | 14 | 16 | Optical assembly, test |
| 8 | Audio & Display QC Test Stations | 30 | 80% | 24 | 16 | TV burn-in, speaker sweep, display calibration |
| 9 | RF / Wi-Fi / Bluetooth Test Chambers | 20 | 75% | 15 | 16 | NCC type approval compliance |
| 10 | AMR Fleet (12× MiR250) Charging | 35 | 40% | 14 | Overnight | Scheduled overnight charging |
| 11 | HVAC / Climate Control | 120 | 90% | 108 | 20 | Large factory footprint |
| 12 | Lighting — Production | 35 | 100% | 35 | 16 | LED high-bay, 500 lux target |
| 13 | Lighting — Offices / Welfare | 15 | 80% | 12 | 12 | LED, occupancy sensors |
| 14 | Compressed Air System | 30 | 65% | 19.5 | 16 | Pneumatic tools, cleaning |
| 15 | IT / MES / Servers / Network | 25 | 100% | 25 | 24 | 24/7 base load |
| 16 | Packaging Lines (×2) | 20 | 75% | 15 | 16 | Carton, shrink-wrap, labelling |
| 17 | General / Miscellaneous | 25 | 60% | 15 | 16 | Hand tools, small equipment |

### 2.2 Total Power Summary

| Parameter | Value | Notes |
|-----------|-------|-------|
| Sum of Rated Powers | ~690 kW | Nameplate installed capacity |
| **Estimated Peak Simultaneous Load** | **~510 kW** | Demand factor 0.74 applied |
| Average Operational Load | ~390 kW | Weighted average across shift |
| Off-Shift Base Load (IT/HVAC/security) | ~55 kW | Overnight continuous loads |
| **Daily Energy Consumption** | **~5,100 kWh/day** | 16h operation + 8h base load |
| **Annual Energy Consumption** | **~1,430 MWh/year** | 252 operating days |
| Power Factor (target) | ≥ 0.95 | PFC capacitor banks installed |

---

## 3. Solar Site Assessment

### 3.1 Location Irradiance Data

| Parameter | Value | Source |
|-----------|-------|--------|
| Factory Location | Agbara Industrial Estate, Lagos State |  |
| Latitude / Longitude | 6.50° N, 3.08° E |  |
| Peak Sun Hours (PSH) — Annual Avg | 4.7 hrs/day | NASA POWER |
| Peak Sun Hours — Worst Month | 3.9 hrs/day | December |
| Peak Sun Hours — Best Month | 5.5 hrs/day | March |
| Avg Daily GHI | 5.3 kWh/m²/day | SolarGIS |

### 3.2 Roof / Ground Area Assessment

| Zone | Available Area (m²) | Usable for Solar (m²) | Est. Capacity |
|------|--------------------|-----------------------|--------------|
| Factory Roof — Main Production | 7,200 m² | 5,800 m² | ~870 kWp |
| Warehouse / Goods-In Roof | 2,000 m² | 1,600 m² | ~240 kWp |
| Ground / Car Park | 600 m² | 500 m² | ~75 kWp |
| **Total Available** | **9,800 m²** | **7,900 m²** | **~1,185 kWp** |

---

## 4. Recommended Energy System

### 4.1 Solar PV Sizing

```
Daily Demand:          5,100 kWh/day
Target Solar Supply:   80% = 4,080 kWh/day
Peak Sun Hours:        3.9 hrs/day (worst month basis)
System Efficiency:     0.89

Required PV Capacity = 4,080 ÷ 3.9 ÷ 0.89 = 1,177 kWp
Phase 1 Installation:  750 kWp (phased — full capacity by Phase 2)
                       Note: 750 kWp covers >80% on average-to-good days;
                       worst-month and peak demand deficit covered by grid + BESS
```

| Parameter | Specification |
|-----------|--------------|
| Installed Capacity (Phase 1) | 750 kWp |
| Panel Technology | Monocrystalline PERC, ≥ 21% efficiency |
| Panel Wattage | 580 W per panel |
| Number of Panels | ~1,293 panels |
| Inverter Type | Hybrid string inverter (solar + BESS integrated) |
| Inverter Capacity | 8× 100 kW hybrid inverters |
| Inverter Brand (target) | Sungrow SH100T / Huawei SUN2000-100K-MGT |
| Estimated Annual Yield | ~1,070 MWh/year |

### 4.2 Battery Energy Storage System (BESS)

```
Overnight Base Load:    55 kW × 10 hrs = 550 kWh
Morning Ramp Load:      120 kW × 2 hrs  = 240 kWh
Emergency Reserve:      80 kWh (30 min critical load)
Total Gross Required:   870 kWh
Adjusted for DoD:       870 ÷ 0.80      = 1,087 kWh
Adjusted for Efficiency: 1,087 ÷ 0.95  = 1,145 kWh

Recommended BESS: 800 kWh usable (Phase 1; expand to 1,200 kWh in Phase 2)
```

| Parameter | Specification |
|-----------|--------------|
| Usable Capacity | 800 kWh |
| Chemistry | LFP (Lithium Iron Phosphate) |
| Cycle Life | ≥ 3,500 cycles @ 80% DoD |
| Form Factor | Containerised BESS unit (20ft equivalent, outdoor-rated) |
| Preferred Suppliers | CATL EnerOne / BYD MC Cube |
| Fire Suppression | Built-in inert gas system in containerised unit |
| Warranty | ≥ 10 years / ≥ 3,500 cycles |

### 4.3 Grid Connection

| Parameter | Specification |
|-----------|--------------|
| Grid Supply | Ikeja Electric (IE) DisCo — 11 kV intake |
| Contracted Demand | 500 kW |
| Role | Secondary backup + peak shaving for SMT line surge loads |
| Smart Meter | Bidirectional, ToU-capable |
| ATS Response | < 100 ms switchover |

### 4.4 Backup Generator

| Parameter | Specification |
|-----------|--------------|
| Generator Capacity | 630 kVA standby (Perkins / Cummins) |
| Fuel | Diesel |
| Auto-Start | BESS SoC < 15% or grid + solar failure |
| Runtime (full tank) | ≥ 72 hrs at 75% load |
| Tank Capacity | 3,000 L |

---

## 5. Energy KPIs

| KPI | Target | Frequency |
|-----|--------|-----------|
| Solar Self-Sufficiency Ratio | ≥ 80% | Monthly |
| Grid Import (% of total energy) | ≤ 20% | Monthly |
| BESS Utilisation | ≥ 250 cycles/year | Annual |
| Energy Intensity (kWh/TV, 43") | ≤ 12 kWh/unit | Monthly |
| Energy Intensity (kWh/router) | ≤ 1.2 kWh/unit | Monthly |
| Energy Intensity (kWh/laptop) | ≤ 5.5 kWh/unit | Monthly |
| Generator Run Hours | < 100 hrs/year | Annual |
| Solar System Availability | ≥ 98% | Monthly |
| CO₂ Avoided | ~960 t/year | Annual |
| Power Factor | ≥ 0.95 | Monthly |

---

## 6. Annual CO₂ Avoidance

| Parameter | Value |
|-----------|-------|
| Solar Annual Yield | ~1,070 MWh/year |
| Nigerian Grid Emission Factor | ~0.90 kgCO₂/kWh (NERC data) |
| **Estimated Annual CO₂ Avoided** | **~963 tonnes CO₂/year** |

---

*For machine-level power ratings, refer to [`machinery.md`](./machinery.md).*
*For digital twin energy monitoring integration, refer to [`digital-twin.md`](./digital-twin.md).*
*For energy-related CapEx and OpEx, refer to [`capex-opex.md`](./capex-opex.md).*
