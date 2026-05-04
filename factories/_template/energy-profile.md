# [FACTORY_NAME] — Energy Profile & Power Systems Design

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** [FACTORY_NAME] | **Location:** [LOCATION] | **Phase:** [PHASE]
> **Document Version:** 1.0 | **Owner:** Energy & Infrastructure Team

---

## 1. Introduction

This document provides a comprehensive power demand analysis and renewable energy system design for [FACTORY_NAME]. Coo-Cah's energy strategy mandates that every factory achieve a minimum of 80% solar self-sufficiency during operational hours and maintain continuous production capability through a properly sized Battery Energy Storage System (BESS). All energy data is fed into the Coo-Cah AI Platform for real-time optimisation and predictive load management.

**Key Energy Design Principles:**
- Solar PV as primary generation source
- LFP (Lithium Iron Phosphate) BESS for storage — cycle life ≥ 3,500 cycles at 80% DoD
- Grid connection retained as secondary backup and peak-shaving support
- Diesel generator as tertiary emergency backup only
- All energy assets monitored via SCADA/EMS integrated with Coo-Cah MES

---

## 2. Factory Power Demand Analysis

### 2.1 Equipment Load Schedule

The table below lists all significant electrical loads within [FACTORY_NAME], their rated power, estimated duty cycle during production, and resulting average load contribution.

| # | Equipment / System              | Rated Power (kW) | Duty Cycle (%) | Avg Load (kW) | Operating Hours/Day | Notes                           |
|---|---------------------------------|------------------|----------------|---------------|---------------------|---------------------------------|
| 1 | [MACHINE_NAME_1]                | [KW]             | [%]            | [KW]          | [HRS]               | [Notes on load profile]         |
| 2 | [MACHINE_NAME_2]                | [KW]             | [%]            | [KW]          | [HRS]               | [Notes]                         |
| 3 | [MACHINE_NAME_3]                | [KW]             | [%]            | [KW]          | [HRS]               | [Notes]                         |
| 4 | [MACHINE_NAME_4]                | [KW]             | [%]            | [KW]          | [HRS]               | [Notes]                         |
| 5 | [MACHINE_NAME_5]                | [KW]             | [%]            | [KW]          | [HRS]               | [Notes]                         |
| 6 | HVAC / Climate Control          | [KW]             | [%]            | [KW]          | [HRS]               | Continuous during production     |
| 7 | Lighting — Production Areas     | [KW]             | 100%           | [KW]          | [HRS]               | LED, zoned control              |
| 8 | Lighting — Offices/Amenities    | [KW]             | 80%            | [KW]          | [HRS]               | LED, occupancy sensors          |
| 9 | Compressed Air System           | [KW]             | [%]            | [KW]          | [HRS]               | Load varies with production      |
| 10| IT / MES / Servers              | [KW]             | 100%           | [KW]          | 24 hrs              | 24/7 load                       |
| 11| AMR Fleet Charging              | [KW]             | [%]            | [KW]          | Overnight primarily  | Scheduled overnight charge      |
| 12| Packaging Line                  | [KW]             | [%]            | [KW]          | [HRS]               | [Notes]                         |
| 13| General Miscellaneous           | [KW]             | 60%            | [KW]          | [HRS]               | Small tools, hand equipment     |

### 2.2 Total Power Summary

| Parameter                              | Value       | Notes                                              |
|----------------------------------------|-------------|----------------------------------------------------|
| Sum of Rated Powers (all equipment)    | [TOTAL] kW  | Nameplate / installed capacity                     |
| **Estimated Peak Simultaneous Load**   | **[PEAK] kW** | Demand factor applied (typically 0.65–0.80)      |
| Average Operational Load               | [AVG] kW    | Weighted average across shift                      |
| Off-Shift Base Load (IT/HVAC/security) | [BASE] kW   | Overnight continuous loads                         |
| **Daily Energy Consumption (ops)**     | **[DAILY] kWh** | [HRS] hours operational + [HRS] off-shift     |
| **Annual Energy Consumption**          | **[ANNUAL] MWh/year** | [DAYS] operating days + 365-day base   |
| Power Factor (target)                  | ≥ 0.95      | PFC capacitor banks to be installed if required   |

> **Demand Factor Basis:** Not all equipment operates simultaneously. A demand factor of [0.XX] has been applied based on production scheduling analysis. Peak load occurs during [PEAK_PERIOD, e.g., mid-morning shift overlap].

---

## 3. Solar Site Assessment

### 3.1 Location Irradiance Data

| Parameter                          | Value              | Source                    |
|------------------------------------|--------------------|---------------------------|
| Factory Location                   | [LOCATION]         |                           |
| Latitude / Longitude               | [LAT]° N, [LON]° E |                           |
| Peak Sun Hours (PSH) — Annual Avg  | [PSH] hours/day    | NASA POWER / SolarGIS data |
| Peak Sun Hours — Worst Month       | [PSH_MIN] hrs/day  | [MONTH]                   |
| Peak Sun Hours — Best Month        | [PSH_MAX] hrs/day  | [MONTH]                   |
| Average Daily Global Horizontal Irradiance | [GHI] kWh/m²/day | SolarGIS             |
| Temperature Correction Factor      | [FACTOR]           | Based on avg ambient temp  |

### 3.2 Rooftop / Ground Mount Area Assessment

| Zone                           | Available Area (m²) | Usable for Solar (m²) | Tilt Angle | Orientation | Estimated Yield     |
|--------------------------------|---------------------|-----------------------|------------|-------------|---------------------|
| Factory Roof — Main Building   | [AREA] m²           | [USABLE] m²           | [DEG]°     | South-facing | [KWH/KWP/year]     |
| Factory Roof — Warehouse       | [AREA] m²           | [USABLE] m²           | [DEG]°     | South-facing | [KWH/KWP/year]     |
| Ground Mount — Car Park / Open | [AREA] m²           | [USABLE] m²           | [DEG]°     | South-facing | [KWH/KWP/year]     |
| **Total Available**            | **[TOTAL] m²**      | **[TOTAL] m²**        |            |             |                     |

---

## 4. Recommended Energy System

### 4.1 Solar PV Sizing

The solar PV array is sized to meet the factory's daytime operational load while also charging the BESS to cover overnight base loads and early morning production ramp-up before solar generation peaks.

**Sizing Formula:**

```
Required Solar PV Capacity (kWp) =
    Daily Energy Demand (kWh) ÷ Peak Sun Hours (hrs/day) ÷ System Efficiency

System Efficiency = Panel Efficiency × Inverter Efficiency × Cable & Mismatch Losses
                  ≈ 0.95 × 0.97 × 0.97 ≈ 0.893 (target)
```

**Calculation:**

```
Daily Demand:         [DAILY] kWh/day
Target Solar Supply:  [SOLAR_%]% of daily demand = [SOLAR_KWH] kWh/day
Peak Sun Hours:       [PSH] hrs/day (worst month basis for conservative sizing)
System Efficiency:    0.89

Required PV Capacity = [SOLAR_KWH] ÷ [PSH] ÷ 0.89
                     = [RESULT] kWp

Rounded to: [SOLAR_KWP] kWp (incorporating [MARGIN]% design margin)
```

**Recommended Solar PV System:**

| Parameter               | Specification                              |
|-------------------------|-------------------------------------------|
| Installed Capacity      | [SOLAR_KWP] kWp                           |
| Panel Technology        | Monocrystalline PERC, ≥ 21% efficiency    |
| Panel Wattage           | [WATT]W per panel                         |
| Number of Panels        | [NUM_PANELS] panels                       |
| Inverter Type           | Hybrid string inverter (solar + BESS)     |
| Inverter Capacity       | [INV_KW] kW                               |
| Inverter Brand (target) | Sungrow / Huawei / Growatt                |
| Mounting System         | Aluminium rail, roof/ground ballast       |
| Estimated Annual Yield  | [ANNUAL_YIELD] MWh/year                   |

### 4.2 Battery Energy Storage System (BESS) Sizing

The BESS is sized to cover three critical use cases:
1. **Overnight base load continuity** — IT, security, HVAC maintenance
2. **Production start-up before solar peak** — covers 06:00–08:00 pre-solar ramp
3. **Grid outage resilience** — sustains critical loads during grid failure events

**Sizing Formula:**

```
Required BESS Capacity (kWh) =
    (Overnight Base Load kW × Overnight Hours)
    + (Morning Ramp Load kW × Ramp Hours)
    + (Emergency Reserve kWh)
    ÷ Depth of Discharge (DoD)
    ÷ Round-Trip Efficiency

DoD = 0.80 (LFP chemistry, preserving cycle life)
Round-Trip Efficiency = 0.95
```

**Calculation:**

```
Overnight Base Load:     [BASE] kW × [HRS] hrs = [BASE_KWH] kWh
Morning Ramp Load:       [RAMP] kW × 2 hrs      = [RAMP_KWH] kWh
Emergency Reserve:       [EMERG] kWh (30 min critical load)
Total Required (gross):  [TOTAL_KWH] kWh
Adjusted for DoD:        [TOTAL_KWH] ÷ 0.80     = [ADJ_KWH] kWh
Adjusted for Efficiency: [ADJ_KWH] ÷ 0.95       = [FINAL_KWH] kWh

Recommended BESS: [BESS_KWH] kWh (rounded up to standard rack unit)
```

**Recommended BESS System:**

| Parameter               | Specification                               |
|-------------------------|---------------------------------------------|
| Usable Capacity         | [BESS_KWH] kWh                              |
| Chemistry               | LFP (Lithium Iron Phosphate)                |
| Cycle Life              | ≥ 3,500 cycles @ 80% DoD                   |
| DC Voltage Bus          | [VOLTAGE]V DC                               |
| BMS                     | Active cell balancing, thermal management   |
| Form Factor             | Rack-mount, containerised (if >500kWh)      |
| Preferred Suppliers     | CATL / BYD / Pylontech / REPT Battero       |
| Fire Suppression        | Built-in dry chemical / FM-200 in BESS room |
| Warranty                | ≥ 10 years / ≥ 3,500 cycles                 |

### 4.3 Grid Connection

| Parameter                        | Specification                          |
|----------------------------------|----------------------------------------|
| Grid Supply                      | [UTILITY] — [VOLTAGE]kV intake         |
| Grid Connection Capacity         | [GRID_KW] kW contracted demand         |
| Role                             | Secondary backup + peak shaving top-up |
| Smart Meter                      | Required for ToU tariff optimisation   |
| Import/Export Management         | Managed by hybrid inverter + EMS       |
| Grid Failure Response            | ATS switches to BESS within [MS] ms    |

### 4.4 Backup Generator

| Parameter                  | Specification                              |
|----------------------------|--------------------------------------------|
| Generator Capacity         | [GEN_KVA] kVA standby                      |
| Fuel                       | Diesel                                     |
| Auto-Start                 | Yes — triggered by BESS SoC < [%]% or grid + solar failure |
| Runtime (full tank)        | [HRS] hours at 75% load                   |
| Emission Standard          | Tier 4 Final / Stage V (if available)      |
| Tank Capacity              | [LITRES] L (≥ 72h runtime target)          |

---

## 5. Energy KPIs

| KPI                                   | Target          | Measurement Method        | Frequency   |
|---------------------------------------|-----------------|---------------------------|-------------|
| Solar Self-Sufficiency Ratio          | ≥ 80%           | EMS energy meter data     | Monthly     |
| BESS Cycle Utilisation                | ≥ 250 cycles/year | BMS cycle counter       | Annual      |
| Grid Import (as % of total energy)    | ≤ 20%           | Smart meter data          | Monthly     |
| Energy Intensity (kWh/unit produced)  | ≤ [VALUE] kWh   | MES production ÷ EMS data | Monthly     |
| Generator Run Hours                   | < 100 hrs/year  | Generator hour meter      | Annual      |
| Power Factor                          | ≥ 0.95          | Power analyser            | Monthly     |
| BESS State of Health (SoH)            | ≥ 85% at yr 5   | BMS diagnostics           | Quarterly   |
| CO₂ Emissions Avoided                 | [CO2] t/year    | Grid emission factor × solar gen | Annual |
| Unplanned Power Downtime              | < 4 hrs/year    | EMS event log             | Annual      |

---

## 6. Grid Dependency Analysis

### 6.1 Scenario Analysis

The following scenarios assess factory resilience under different energy supply conditions.

| Scenario                           | Grid | Solar | BESS | Generator | Production Impact       |
|------------------------------------|------|-------|------|-----------|-------------------------|
| Normal Day (Grid + Solar + BESS)   | ✅   | ✅    | ✅   | Off       | Full production          |
| Grid Failure (daytime)             | ❌   | ✅    | ✅   | Off       | Full production (solar primay) |
| Grid Failure (night / overcast)    | ❌   | ❌    | ✅   | Standby   | Base load + critical only |
| Solar + Grid Failure (long)        | ❌   | ❌    | ✅→❌| ✅        | Critical loads only      |
| Total Outage (all sources)         | ❌   | ❌    | ❌   | ❌        | Emergency shutdown proc  |

### 6.2 Critical Load Priority Tiers

When energy is constrained, loads are shed in the following priority order (controlled by EMS):

| Priority | Load Tier        | Systems Included                                          | Minimum Sustain Time |
|----------|------------------|-----------------------------------------------------------|----------------------|
| 1 — Critical | Must Never Lose Power | IT/MES servers, cleanroom HVAC (if applicable), fire alarm, security | 24 hrs (BESS) |
| 2 — Essential | Production Continuity | Assembly lines, QC equipment, AMRs | 8 hrs (BESS) |
| 3 — Important | Normal Operations | Packaging, warehousing, offices | 4 hrs (BESS)   |
| 4 — Deferrable | Comfort & Convenience | Non-production HVAC zones, electric vehicle charging | Shed first |

---

## 7. Energy Cost Analysis

### 7.1 Baseline (Grid Only) vs Solar + BESS Scenario

| Parameter                            | Grid Only          | Solar + BESS System     |
|--------------------------------------|--------------------|-------------------------|
| Annual Energy Consumption            | [ANNUAL] MWh/year  | [ANNUAL] MWh/year       |
| Grid Import (annual)                 | [ANNUAL] MWh       | [GRID_IMPORT] MWh/year  |
| Average Grid Tariff                  | ₦[TARIFF]/kWh      | ₦[TARIFF]/kWh           |
| Annual Grid Energy Cost              | ₦[COST]            | ₦[COST_REDUCED]         |
| Solar + BESS Capital Cost            | —                  | ₦[CAPEX]                |
| Annual O&M (solar + BESS)            | —                  | ₦[OM_COST]/year         |
| Annual Savings vs Grid Only          | Baseline           | ₦[SAVINGS]/year         |
| Simple Payback Period                | —                  | [YEARS] years           |
| 25-Year NPV (at [%]% discount rate)  | —                  | ₦[NPV]                  |

---

## 8. Energy Infrastructure Layout

Key infrastructure placements within the factory:

```
[FACTORY_SITE_BOUNDARY]
│
├── Rooftop Solar Arrays
│     ├── Zone A: Main Production Building Roof — [KWP] kWp
│     ├── Zone B: Warehouse Roof — [KWP] kWp
│     └── Zone C: Canopy/Carport (if applicable) — [KWP] kWp
│
├── BESS Room (standalone, fire-rated, ventilated)
│     └── LFP Battery Racks — [KWH] kWh usable
│
├── Hybrid Inverter/PCS Room (adjacent to BESS room)
│     └── [NUM] × [KW] kW inverters
│
├── HV/MV Intake Substation (boundary wall or utility easement)
│     └── [KV] kV → [LV] V step-down transformer
│
└── Backup Generator (external, bunded, ventilated pad)
      └── [KVA] kVA diesel generator
```

---

## 9. Environmental & Sustainability Notes

- LFP battery chemistry selected for safety (no thermal runaway risk with phosphate cathode), long cycle life, and absence of cobalt/nickel (supply chain ethics).
- Solar panel end-of-life: Coo-Cah will partner with certified solar panel recyclers as modules reach end of life (25–30 years). No landfill disposal.
- BESS end-of-life: Battery modules will be repurposed for second-life energy storage applications across the Coo-Cah estate network before final recycling.
- Annual CO₂ avoidance will be tracked, verified, and considered for carbon credit generation under appropriate African carbon market frameworks (e.g., Article 6 Paris Agreement mechanisms).
- Diesel generator fuel consumption and emissions will be monitored and reported as part of Coo-Cah's annual sustainability report.

---

*For machine-level power ratings, refer to [`machinery.md`](./machinery.md).*
*For digital twin energy monitoring integration, refer to [`digital-twin.md`](./digital-twin.md).*
*For energy-related CapEx and OpEx, refer to [`capex-opex.md`](./capex-opex.md).*
