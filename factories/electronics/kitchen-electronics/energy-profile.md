# Kitchen Electronics Factory — Energy Profile

> **Project Coo-Cah | Kitchen Electronics Factory | Lagos/Ogun, Nigeria | Phase 1**

---

## 1. Factory Power Demand Analysis

| # | Equipment / System                    | Rated Power (kW) | Duty Cycle (%) | Avg Load (kW) | Notes                              |
|---|---------------------------------------|------------------|----------------|---------------|------------------------------------|
| 1 | SMT Reflow Oven (Heller 1964 MK5)     | 80               | 80%            | 64            | High thermal mass; ramps on start  |
| 2 | Wave/Selective Soldering              | 30               | 60%            | 18            | Intermittent duty                  |
| 3 | SMT Pick-and-Place (×2)               | 10               | 85%            | 8.5           | Low power, high speed              |
| 4 | PU Foam Injection Machine             | 45               | 70%            | 31.5          | Peak at injection cycle            |
| 5 | Compressor (refrigerant circuit fab.) | 15               | 60%            | 9             |                                    |
| 6 | Gas Charging Station (R600a ×2)       | 15               | 50%            | 7.5           |                                    |
| 7 | Refrigerator Performance Test Racks   | 30               | 100%           | 30            | 24h test — continuous              |
| 8 | HVAC — Production Areas               | 120              | 90%            | 108           | Largest single load                |
| 9 | Lighting — Production (LED)           | 40               | 100%           | 40            |                                    |
| 10| Lighting — Offices/Amenities (LED)    | 10               | 80%            | 8             |                                    |
| 11| Compressed Air (×2 compressors)       | 110              | 55%            | 60.5          |                                    |
| 12| General Machinery & Assembly Lines    | 60               | 65%            | 39            | Conveyors, tools, small motors     |
| 13| MES / IT / Servers                    | 15               | 100%           | 15            | 24/7 load                          |
| 14| AMR Fleet Charging                    | 25               | 40%            | 10            | Staggered overnight charge         |
| 15| Packaging Line                        | 20               | 70%            | 14            |                                    |
| 16| Miscellaneous                         | 25               | 60%            | 15            |                                    |

## 2. Power Summary

| Parameter                          | Value              |
|------------------------------------|--------------------|
| Total Installed (Rated) Power      | 650 kW             |
| **Estimated Peak Simultaneous Load** | **~500 kW**      |
| Average Operational Load (16h/day) | ~370 kW            |
| Overnight Base Load                | ~50 kW             |
| **Daily Energy Consumption**       | **~3,500 kWh/day** |
| **Annual Consumption**             | **~1,050 MWh/year** |

---

## 3. Recommended Energy System

### 3.1 Solar PV — 700 kWp

```
Daily demand (operational):     3,500 kWh
Target solar supply:            80% = 2,800 kWh
Lagos PSH (conservative, worst month): 4.5 hrs/day
System efficiency:              0.89

Required = 2,800 ÷ 4.5 ÷ 0.89 = 699 kWp → 700 kWp installed
```

| Parameter              | Specification                                      |
|------------------------|----------------------------------------------------|
| Capacity               | 700 kWp                                            |
| Technology             | Monocrystalline PERC, ≥21% efficiency              |
| Panel (e.g.)           | Longi LR5-72HBD 580W (1,207 panels)               |
| Mounting               | Rooftop ballast + ground-mount east wing           |
| Inverters              | 4 × Sungrow SH250HX (hybrid, 250 kW each)         |
| Annual Yield           | ~840 MWh/year (4.8 avg PSH)                        |

### 3.2 BESS — 800 kWh LFP

```
Overnight base load:    50 kW × 10 hrs       = 500 kWh
Morning ramp (pre-solar): 200 kW × 1.5 hrs   = 300 kWh
Gross required:          800 kWh
Adjusted for DoD (80%): 800 ÷ 0.80           = 1,000 kWh usable → select 800 kWh usable (commercial standard)
```

| Parameter              | Specification                                      |
|------------------------|----------------------------------------------------|
| Usable Capacity        | 800 kWh                                            |
| Chemistry              | LFP (Lithium Iron Phosphate)                       |
| Cycle Life             | ≥ 3,500 cycles @ 80% DoD                          |
| Supplier               | CATL / BYD / Pylontech rack solution               |
| Form Factor            | Containerised 20ft, outdoor rated                  |

### 3.3 Backup Generator

- **1 × Perkins 500 kVA diesel generator**
- Auto-start when BESS SoC < 20% and grid unavailable
- 2,000L bunded diesel tank (~72h runtime at 40% load)

---

## 4. Energy KPIs

| KPI                                | Target          |
|------------------------------------|-----------------|
| Solar Self-Sufficiency             | ≥ 80%           |
| Grid Import (% of total)           | ≤ 20%           |
| Energy Intensity — Refrigerators   | ≤ 18 kWh/unit   |
| Energy Intensity — Small Appliances| ≤ 2 kWh/unit    |
| Generator Run Hours/Year           | < 100 hrs       |
| Annual CO₂ Avoidance               | ~700 t CO₂/year |
| Power Factor                       | ≥ 0.95          |

---

## 5. Grid Dependency Analysis

| Scenario                        | Impact                              |
|---------------------------------|-------------------------------------|
| Grid + Solar (Normal)           | Full production; BESS charges       |
| Grid Failure (day)              | Solar primary; full production      |
| Grid Failure (night)            | BESS covers overnight base load     |
| Extended outage (>10h)          | Generator starts; critical loads    |
| Total loss                      | Emergency shutdown procedure        |

*Lagos grid reliability: average 8–12h supply/day in industrial zones. Solar + BESS system effectively eliminates grid dependence during production hours.*
