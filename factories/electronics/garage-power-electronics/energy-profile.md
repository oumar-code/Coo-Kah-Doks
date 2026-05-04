# Garage & Power Electronics Factory — Energy Profile

> **Project Coo-Cah | Garage & Power Electronics Factory | Sagamu, Ogun State, Nigeria | Phase 1**

---

## 1. Factory Power Demand Analysis

| # | Equipment / System                         | Rated Power (kW) | Duty Cycle (%) | Avg Load (kW) | Notes                                       |
|---|--------------------------------------------|------------------|----------------|---------------|---------------------------------------------|
| 1 | SMT Reflow Oven (Heller 1964 MK5)          | 80               | 85%            | 68            | High thermal mass; dominant PCB heat load   |
| 2 | Transformer Winding Machines (×3)          | 60               | 75%            | 45            | Toroidal + EI winding; cyclic duty          |
| 3 | Inverter Assembly + Functional Test Rig    | 50               | 80%            | 40            | Bench test + load bank warm-up power        |
| 4 | Load Bank Testing (power tool + inverter)  | 100              | 35%            | 35            | Peak 100 kW; short duration per unit cycle  |
| 5 | Wave Soldering Machine                     | 30               | 60%            | 18            | Through-hole; intermittent duty             |
| 6 | Pick-and-Place (×2 JUKI)                   | 10               | 85%            | 8.5           | Low power; high-speed operation             |
| 7 | Power Strip & UPS Assembly Lines           | 25               | 75%            | 18.75         | Conveyors, pneumatic screwdrivers, testers  |
| 8 | Power Tool Motor Press + Assembly          | 20               | 70%            | 14            | Arbor press, torque tools, bench equipment  |
| 9 | Compressed Air (×2 compressors)            | 40               | 65%            | 26            | 8 bar ring-main; pneumatic tools throughout |
| 10| HVAC — Production Areas                    | 80               | 90%            | 72            | 12,000 m² — largest sustained load         |
| 11| Lighting — Production (LED, zoned)         | 30               | 100%           | 30            | LED throughout; occupancy control in stores |
| 12| Lighting — Offices / Amenities             | 8                | 80%            | 6.4           | LED, motion sensors                         |
| 13| IT / MES / Edge Servers                    | 15               | 100%           | 15            | 24/7 continuous load                        |
| 14| AMR Fleet Charging (×10 units)             | 20               | 40%            | 8             | Staggered overnight charge schedule         |
| 15| Packaging Line                             | 15               | 70%            | 10.5          | Carton erector, taper, label applicator     |
| 16| IQC Lab / Metrology Equipment              | 10               | 60%            | 6             | Oscilloscopes, hipot testers, power analysers |
| 17| General Miscellaneous                      | 20               | 55%            | 11            | Hand tools, rework stations, small loads    |

## 2. Power Summary

| Parameter                            | Value               |
|--------------------------------------|---------------------|
| Total Installed (Rated) Power        | 613 kW              |
| **Estimated Peak Simultaneous Load** | **~400 kW**         |
| Average Operational Load (16h/day)   | ~280 kW             |
| Overnight Base Load                  | ~45 kW              |
| **Daily Energy Consumption**         | **~2,800 kWh/day**  |
| **Annual Consumption**               | **~840 MWh/year**   |

> **Demand Factor:** Not all loads run simultaneously. Peak occurs during mid-morning shift overlap when inverter test rigs, load banks, and SMT oven all run together. Applied demand factor: 0.65.

---

## 3. Recommended Energy System

### 3.1 Solar PV — 600 kWp (Ground-Mount)

```
Daily demand:            2,800 kWh/day
Target solar supply:     80% = 2,240 kWh/day
Ogun State PSH (conservative, worst month):  4.5 hrs/day
System efficiency:       0.89

Required = 2,240 ÷ 4.5 ÷ 0.89 = 559 kWp → 600 kWp installed (7% design margin)
```

| Parameter              | Specification                                             |
|------------------------|-----------------------------------------------------------|
| Capacity               | 600 kWp                                                   |
| Technology             | Monocrystalline PERC, ≥ 21% efficiency                   |
| Panel (e.g.)           | Longi LR5-72HBD 580W (1,035 panels)                      |
| Mounting               | Ground-mount — open land east of main building            |
| Inverters              | 3 × Sungrow SH200HX hybrid (200 kW each)                 |
| Annual Yield           | ~720 MWh/year (4.7 avg PSH)                               |
| Land Required          | ~3,600 m² (ground-mount, 10° tilt, 3m row spacing)       |
| Note                   | Ground-mount preferred — Sagamu provides land unavailable in Lagos rooftop sites |

### 3.2 BESS — 700 kWh LFP

```
Overnight base load:       45 kW × 10 hrs        = 450 kWh
Morning ramp (pre-solar):  150 kW × 1.5 hrs       = 225 kWh
Emergency reserve (30 min peak load): 100 kW × 0.5 = 50 kWh
Gross required:            725 kWh
Adjusted for DoD (80%):   725 ÷ 0.80             = 906 kWh gross → select 700 kWh usable
                           (commercial standard rack; 80% DoD applied)
```

| Parameter              | Specification                                             |
|------------------------|-----------------------------------------------------------|
| Usable Capacity        | 700 kWh                                                   |
| Chemistry              | LFP (Lithium Iron Phosphate)                              |
| Cycle Life             | ≥ 3,500 cycles @ 80% DoD                                 |
| DC Voltage Bus         | 614V DC                                                   |
| Supplier               | CATL / BYD / Pylontech rack solution                      |
| Form Factor            | Containerised 20ft, outdoor-rated, fire-suppression built-in |
| BMS                    | Active cell balancing, thermal management, remote monitoring |
| Warranty               | ≥ 10 years / ≥ 3,500 cycles                               |

### 3.3 Backup Generator

- **1 × Perkins 400 kVA diesel generator**
- Auto-start when BESS SoC < 20% and grid unavailable
- 1,500L bunded diesel tank (~60h runtime at 40% load)
- Located on external ventilated bunded pad, adjacent to north wall

---

## 4. Energy KPIs

| KPI                                    | Target            |
|----------------------------------------|-------------------|
| Solar Self-Sufficiency                 | ≥ 80%             |
| Grid Import (% of total)               | ≤ 20%             |
| Energy Intensity — Inverters           | ≤ 3.5 kWh/unit    |
| Energy Intensity — Power Strips        | ≤ 0.4 kWh/unit    |
| Energy Intensity — Power Tools         | ≤ 2.0 kWh/unit    |
| Generator Run Hours/Year               | < 100 hrs         |
| Annual CO₂ Avoidance                   | ~540 t CO₂/year   |
| Power Factor                           | ≥ 0.95            |
| BESS State of Health at Year 5         | ≥ 85%             |
| Unplanned Power Downtime               | < 4 hrs/year      |

---

## 5. Grid Dependency Analysis

| Scenario                        | Impact                                               |
|---------------------------------|------------------------------------------------------|
| Grid + Solar (Normal Day)       | Full production; BESS charges; load bank testing ok  |
| Grid Failure (daytime)          | Solar primary; full production continues             |
| Grid Failure (night)            | BESS covers overnight base load (~10h)               |
| Extended outage (> 10h)         | Generator starts; critical loads + production maintained |
| Total loss (all sources)        | Emergency shutdown procedure; safe-state all equipment |

*Ogun State grid reliability: industrial estates in Sagamu typically receive 8–12h supply/day. The 600 kWp solar + 700 kWh BESS system is designed to render the factory effectively grid-independent during all production hours.*

---

## 6. Energy Cost Analysis

### 6.1 Baseline (Grid Only) vs Solar + BESS Scenario

| Parameter                               | Grid Only          | Solar + BESS System     |
|-----------------------------------------|--------------------|-------------------------|
| Annual Energy Consumption               | ~840 MWh/year      | ~840 MWh/year           |
| Grid Import (annual)                    | 840 MWh            | ~170 MWh/year (20%)     |
| Average Grid Tariff                     | ₦100/kWh           | ₦100/kWh                |
| Annual Grid Energy Cost                 | ₦84,000,000        | ₦17,000,000             |
| Solar + BESS Capital Cost               | —                  | ~₦1,520,000,000         |
| Annual O&M (solar + BESS)               | —                  | ~₦18,000,000/year       |
| Annual Savings vs Grid Only             | Baseline           | ~₦67,000,000/year       |
| Simple Payback Period                   | —                  | ~11.5 years             |
| 25-Year NPV (at 18% discount rate)      | —                  | ~₦120,000,000           |

> *Note: Financial return improves significantly when diesel generator avoidance costs (fuel + maintenance at ~₦12M/year grid-failure scenario) are factored in. The primary driver is production continuity, not energy cost alone.*

---

## 7. Energy Infrastructure Layout

```
GARAGE & POWER ELECTRONICS FACTORY SITE (12,000 m²)
│
├── Ground-Mount Solar Array (East Yard — 3,600 m²)
│     └── 600 kWp — 1,035 × Longi 580W panels
│           3 × Sungrow SH200HX hybrid inverters (in weatherproof enclosure)
│
├── BESS Room (standalone, fire-rated, climate-controlled)
│     └── 700 kWh LFP — CATL/BYD 20ft containerised system
│           Integrated BMS, fire suppression, SCADA-connected
│
├── Hybrid Inverter / PCS Room (adjacent to BESS)
│     └── 3 × 200 kW hybrid string inverters
│           EMS software — Sungrow iSolarCloud / custom Coo-Cah EMS
│
├── HV/LV Intake Substation (north boundary)
│     └── 11kV → 415V 500 kVA transformer (EKEDC/Ogun DISCO intake)
│           Main LV switchboard with metering
│
├── Main MCC (Electrical Room, adjacent to production)
│     └── Sub-distribution boards for each production zone
│           ESD-protected circuits for SMT + electronics assembly
│
└── Backup Generator Pad (external, bunded, north wall)
      └── Perkins 400 kVA diesel generator
            1,500L bunded diesel tank
```

---

## 8. Environmental & Sustainability Notes

- LFP chemistry selected for safety (no thermal runaway phosphate cathode), long cycle life, and cobalt-free supply chain.
- Solar panel end-of-life recycling: Coo-Cah will engage SON-approved e-waste recyclers as panels approach 25-year life.
- BESS second-life: Modules with > 70% remaining capacity to be repurposed for community energy storage projects within the Coo-Cah Smart Estate network.
- Diesel generator fuel consumption and emissions reported in Coo-Cah annual sustainability disclosure.
- Target: annual CO₂ avoidance of ~540 tonnes, equating to a reduction of ~0.5 kg CO₂ per unit produced across the full product range.
- The ground-mount solar array doubles as partial shade for vehicle parking — a dual-use land efficiency measure that avoids rooftop structural loading on the production building.

---

*For machine-level power ratings, refer to [`machinery.md`](./machinery.md).*
*For digital twin energy monitoring integration, refer to [`digital-twin.md`](./digital-twin.md).*
*For energy-related CapEx and OpEx, refer to [`capex-opex.md`](./capex-opex.md).*
