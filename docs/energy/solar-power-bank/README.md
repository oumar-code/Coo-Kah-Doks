# Solar Power Bank — Group Solar PV Programme

> **Project Coo-Cah | Energy Infrastructure**
> **Document Version:** 1.0 | **Owner:** Group Energy & Infrastructure Team

---

## Overview

The Coo-Cah Solar Power Bank is the group-wide programme governing the design, procurement, installation, and operation of solar photovoltaic (PV) systems across all Coo-Cah factories. Solar PV is the primary renewable energy source for every factory in the ecosystem and must be designed and commissioned before commercial production begins.

---

## Group Solar Portfolio

| Factory | Location | Installed Capacity (kWp) | Status | Commission Target |
|---------|----------|--------------------------|--------|------------------|
| Kitchen Electronics | Lagos, Nigeria | 600 kWp | Planned | Q2 2026 |
| Garage/Power Electronics | Ogun State, Nigeria | 750 kWp | Planned | Q2 2026 |
| Personal Electronics | Ogun State, Nigeria | 850 kWp | Planned | Q2 2026 |
| Plastics Factory | Ogun State, Nigeria | 700 kWp | Planned | Q3 2026 |
| Security Electronics | Lagos, Nigeria | 500 kWp | Planned | Q3 2026 |
| Smart Home & Office | Lagos, Nigeria | 750 kWp | Planned | Q4 2026 |
| Food & Beverages | Abuja, Nigeria | 650 kWp | Planned | Q1 2027 |
| Heavy Chemicals | Delta State, Nigeria | 900 kWp | Planned | Q2 2027 |
| Personal Care | Lagos, Nigeria | 600 kWp | Planned | Q2 2027 |
| Household Cleaning | Lagos, Nigeria | 500 kWp | Planned | Q2 2027 |
| Packaged Water | Lagos, Nigeria | 400 kWp | Planned | Q2 2027 |
| Smart Estate/City | Kigali, Rwanda | 300 kWp | Planned | Q3 2027 |
| Fashion & Apparel | Lagos, Nigeria | 450 kWp | Planned | Q3 2027 |
| **Group Total** | | **~7,750 kWp** | | |

---

## Technology Specification

### Panel Technology

| Parameter | Specification |
|-----------|--------------|
| Technology | Monocrystalline PERC (primary) |
| Efficiency | ≥ 21% module efficiency |
| Panel Wattage | 450W–600W per panel |
| Degradation | ≤ 0.5%/year linear |
| Warranty | 25-year linear power warranty; 12-year product warranty |
| Certification | IEC 61215, IEC 61730, MCS/UL/CE |
| Preferred Suppliers | Tier 1: Longi, JA Solar, Risen, Canadian Solar |

### Inverter Technology

| System Size | Inverter Type | Notes |
|-------------|--------------|-------|
| < 100 kWp | String inverter (hybrid) | BESS integration required |
| 100 kWp – 1 MWp | Central or multi-string hybrid inverter | Group-standardised models |
| > 1 MWp | Central inverter + string combiner | Grid-code compliant |
| All sizes | Hybrid with BESS integration | Mandatory — Sungrow SH/SG, Huawei SUN2000, Growatt |

### Mounting Systems

| Installation Type | Application | Specification |
|------------------|-------------|---------------|
| Rooftop (flat) | Factory roof, warehouse | Aluminium rail, ballast, 10° tilt, S/SE/SW orientation |
| Rooftop (pitched) | Any pitched roof | In-roof or on-roof rail system, orientation-optimised |
| Ground mount | Car parks, open land | Driven pile or concrete ballast, fixed tilt optimised for latitude |
| Single-axis tracker | Ground arrays > 500 kWp | East-west rotation, 15–25% yield improvement |

---

## Sizing Methodology

All solar systems are sized using the following standard methodology:

```
Step 1: Audit factory energy demand
        - Total daily demand (kWh/day)
        - Peak simultaneous load (kW)
        - Shift pattern and operational hours

Step 2: Obtain site irradiance data
        - Source: NASA POWER (https://power.larc.nasa.gov/) or SolarGIS
        - Data: Peak Sun Hours (PSH) — annual average AND worst month

Step 3: Size the solar array
        Array (kWp) = Daily Demand (kWh) × Solar Target (%) ÷ PSH ÷ System Efficiency (0.89)

Step 4: Size the BESS
        See [BESS Sizing](../hybrid-systems/README.md) in the Hybrid Systems document

Step 5: Verify roof/land area
        - Required area ≈ Array (kWp) × 6.5 m²/kWp (monocrystalline)
        - Confirm structural load capacity for rooftop installations
```

---

## Group Procurement Strategy

Coo-Cah Holdings negotiates group-level procurement contracts for solar equipment, achieving economies of scale across all factories:

| Lever | Benefit |
|-------|---------|
| Bulk panel procurement | 12–18% cost reduction vs. individual factory procurement |
| Standardised inverter models | Reduced training, spares, and service contract costs |
| Group O&M contract | Single O&M provider for all Nigerian factories |
| Group insurance | Portfolio insurance for solar assets |
| Group spare parts hub | Central inventory of panels, inverters, combiner boxes in Lagos and Kigali |

---

## Performance Monitoring

All solar systems report to the Coo-Cah Central AI Platform via the factory EMS (Energy Management System):

| KPI | Target | Measurement |
|-----|--------|-------------|
| Solar Self-Sufficiency Ratio | ≥ 80% | Monthly — EMS meter data |
| System Availability | ≥ 98% | Monthly — inverter data |
| Performance Ratio (PR) | ≥ 80% | Monthly — energy yield ÷ theoretical |
| Specific Yield (kWh/kWp) | ≥ 1,400 kWh/kWp/year (Nigeria) | Annual |
| Annual Degradation | ≤ 0.5%/year | Annual |
| CO₂ Avoided (group total) | Target: > 10,000 t/year (Phase 1) | Annual |

---

## Regulatory Compliance

### Nigeria
- **NERC Licence:** Required for embedded generation > 1 MW per site
- **NEMSA Certification:** Safety certification for all electrical installations
- **DisCo Agreement:** Net metering or feed-in arrangement with local Distribution Company

### Rwanda
- **RURA Licence:** Generation licence for systems > 50 kW
- **REG Grid Agreement:** Required for grid-connected systems

### Kenya
- **EPRA Licence:** Energy & Petroleum Regulatory Authority generation licence
- **KPLC Net Metering:** Kenya Power net metering framework

---

*See also: [Wind Power Bank](../wind-power-bank/README.md) | [Hybrid Systems](../hybrid-systems/README.md) | [Energy Strategy](../../02-energy-strategy/index.md)*
