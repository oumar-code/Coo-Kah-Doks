# Coo-Cah Smart Estate & City Electronics Factory — Energy Profile

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Vertical:** Electronics — Smart City & Estate Infrastructure | **Location:** Lekki Free Trade Zone (LFTZ), Lagos State, Nigeria | **Phase:** Phase 1
> **Document Version:** 1.0 | **Status:** In Development

---

## 1. Site Energy Context

The factory is located in the Lekki Free Trade Zone (LFTZ), Lagos State, which provides approximately 18–20 hours of grid supply per day — superior to Lagos metropolitan average (~12 h/day). Nonetheless, the energy strategy adopts a solar-first, BESS-buffered approach with grid as a secondary top-up source, ensuring the critical calibration and SMT reflow loads maintain continuous supply. The target is ≥80% operational energy from on-site renewables. A single 400 kVA Perkins diesel generator provides emergency backup when both grid and BESS are depleted.

| Metric                         | Value                                  |
|--------------------------------|----------------------------------------|
| Facility Area                  | ~14,000 m²                             |
| Operational Hours              | 16 h/day (2 shifts); 24 h/day BESS/cal |
| Estimated Peak Load            | ~380 kW                                |
| Daily Energy Consumption       | ~2,500 kWh/day                         |
| Annual Energy Consumption      | ~750,000 kWh/year                      |
| Lagos Average Daily Irradiance | 4.5 Peak Sun Hours (PSH) — conservative |
| LFTZ Grid Availability         | ~18–20 h/day                           |
| Grid Tariff (LFTZ estimate)    | ₦95/kWh (Band A equivalent)           |
| Annual Grid Energy Cost        | ~₦71.25 m/yr (if 100% grid-sourced)   |

---

## 2. Equipment Load Register

| # | Load Description                                    | Zone         | Qty | Unit kW  | Subtotal kW | Hours/Day | kWh/Day |
|---|-----------------------------------------------------|--------------|-----|----------|-------------|-----------|---------|
| 1 | SMT Reflow Oven — Heller 1964 MK5                   | PL-SMT       | 2   | 28.0     | 56.0        | 16        | 896     |
| 2 | Pick-and-Place Machines (JUKI FX-3R + RS-1)         | PL-SMT       | 4   | 4.5      | 18.0        | 16        | 288     |
| 3 | SPI / AOI / X-Ray Systems                           | PL-SMT       | 5   | 3.0      | 15.0        | 16        | 240     |
| 4 | Selective Soldering / Stencil Printer               | PL-SMT       | 3   | 3.5      | 10.5        | 16        | 168     |
| 5 | ICT & Fixture Programming Stations                  | PL-SMT       | 4   | 2.0      | 8.0         | 16        | 128     |
| 6 | Smart Meter Calibration Benches (IEC 62053)         | CAL-LAB      | 4   | 5.0      | 20.0        | 24        | 480     |
| 7 | Water Meter Calibration Rig (Gravimetric)           | CAL-LAB      | 2   | 4.0      | 8.0         | 16        | 128     |
| 8 | Ultrasonic Welders & Press-Fit Machines             | PL-METER     | 4   | 3.5      | 14.0        | 16        | 224     |
| 9 | Meter Assembly Conveyors (Lines 1 & 2)              | PL-METER     | 2   | 2.5      | 5.0         | 16        | 80      |
| 10| Smart Pole Welding Stations (MIG/MAG ×4)            | PL-POLE      | 4   | 7.0      | 28.0        | 16        | 448     |
| 11| Conformal Coating Machine + UV Tunnel               | PL-COAT      | 2   | 4.5      | 9.0         | 12        | 108     |
| 12| Potting Machine (2-component PU/epoxy)              | PL-COAT      | 1   | 2.0      | 2.0         | 12        | 24      |
| 13| Compressed Air Compressors (Atlas Copco GA30+)      | UTILITIES    | 2   | 30.0     | 60.0        | 16        | 960     |
| 14| HVAC — Production Halls (multi-split)               | ALL ZONES    | —   | 74.0     | 74.0        | 16        | 1,184   |
| 15| HVAC — Calibration Lab & QC (precision control)     | CAL-LAB/FQC  | —   | 10.0     | 10.0        | 24        | 240     |
| 16| LED Factory Lighting                                | ALL ZONES    | —   | 22.0     | 22.0        | 16        | 352     |
| 17| MES Servers, Networking, Workstations               | IT-ROOM      | —   | 11.0     | 11.0        | 24        | 264     |
| 18| AMR Fleet Charging (10 × MiR200)                    | AMR-DOCK     | 4   | 4.0      | 16.0        | 6         | 96      |
| 19| Environmental Test & Salt Spray Chambers            | QC-LAB       | 2   | 8.0      | 16.0        | 12        | 192     |
| 20| General Tools, Benches, Small Appliances            | ALL ZONES    | —   | 15.0     | 15.0        | 12        | 180     |
|   | **PEAK SIMULTANEOUS LOAD (est.)**                   |              |     |          | **~380 kW** | —         | —       |
|   | **DAILY ENERGY CONSUMPTION**                        |              |     |          | —           | —         | **~2,500 kWh** |

> *Peak simultaneous load is calculated with a diversity factor of 0.88 applied across production equipment loads and 1.0 for HVAC, servers, and calibration benches.*

---

## 3. Solar PV System Sizing

```
TARGET: Offset ≥ 85% of daily site energy from solar PV.
         (Remaining 15% = grid top-up + BESS discharge from previous day excess)

Daily solar generation target:
  2,500 kWh/day × 0.85 = 2,125 kWh/day

Required installed capacity:
  Formula: P_installed (kWp) = E_target (kWh) ÷ PSH ÷ η_system
  Where:
    E_target = 2,125 kWh/day
    PSH      = 4.5 h/day  (Lagos conservative)
    η_system = 0.89        (cable losses 0.02 + inverter 0.05 + soiling 0.03 + mismatch 0.01 = 0.11 total losses)

  P_installed = 2,125 ÷ 4.5 ÷ 0.89 = 530.4 kWp (minimum)

DESIGN DECISION: Install 600 kWp (600 ÷ 530 = +13% margin)
  Rationale:
    + Phase 2 load growth headroom
    + Seasonal irradiance variation buffer (harmattan: -8% Dec–Jan)
    + Soiling degradation buffer (Lekki coastal dust)
    + ≤ 1% first-year module degradation absorbed
    + Car park canopy portion (north face) is ~5% less efficient

LAYOUT:
  Rooftop (flat + slight south pitch):      480 kWp  (1,200 × 400 Wp modules)
  Car Park Canopy (east-west sawtooth):     120 kWp  (300 × 400 Wp modules)
  Total Installed:                          600 kWp  (1,500 modules)

INVERTER CONFIGURATION:
  6 × Sungrow SH110T-V112 (100 kW each) = 600 kW AC rated
  Each inverter fed by 200 modules (2 × 100-module strings, Vmpp ~3,420 V)

ESTIMATED ANNUAL GENERATION:
  600 kWp × 4.5 PSH × 365 × 0.89 = ~878,000 kWh/year
  (vs annual consumption ~750,000 kWh → ~117% coverage ratio,
   allowing for ~128,000 kWh annual grid export or BESS cycling surplus)
```

---

## 4. Battery Energy Storage System (BESS) Sizing

```
OBJECTIVE: Store sufficient solar energy to:
  (a) Supply overnight base load (servers, calibration benches, HVAC cal lab)
  (b) Support morning production ramp before solar output rises
  (c) Provide ≥ 2 h grid outage buffer at full production load

OVERNIGHT BASE LOAD (22:00–06:00 = 8 hours):
  Servers + MES:           11 kW
  Calibration benches:     20 kW
  Precision HVAC:          10 kW (cal lab only)
  Security + Emergency:     4 kW
  Overnight base total:  = 35 kW × 8 h = 280 kWh

MORNING RAMP SUPPORT (06:00–07:30 = 1.5 hours):
  (Solar output ramping, production starting — partial load ~200 kW)
  200 kW × 1.5 h = 300 kWh
  (Solar covers ~half this by 07:00; BESS covers balance: ~150 kWh)
  Conservative allocation: 300 kWh assigned to morning ramp

TOTAL ENERGY REQUIRED FROM BESS:
  280 kWh (overnight) + 300 kWh (morning ramp) = 580 kWh usable

ACCOUNTING FOR DEPTH OF DISCHARGE (DoD):
  LFP chemistry: max 90% DoD for 3,000+ cycle life target
  Required nominal capacity: 580 ÷ 0.90 = 644 kWh

DESIGN DECISION: Install 650 kWh LFP BESS
  Supplier options: BYD Battery-Box Premium HVS or CATL EnerOne
  Rounding margin: 650 ÷ 644 = +0.9% (minimal; justified by BESS module sizing steps)
  At 90% DoD: 585 kWh usable (vs 580 kWh required — adequate)

BMS SETTINGS:
  Charge cut-off:   100% SoC (bulk) / 95% SoC (float)
  Discharge cut-off: 10% SoC (10% reserve for emergency loads)
  Charge rate:       0.5C max (325 kW charge from solar surplus)
  Discharge rate:    1C max (650 kW; limited by inverter to 600 kW AC)
```

---

## 5. Grid & Generator Integration

| Source         | Role                                  | Capacity      | Priority |
|----------------|---------------------------------------|---------------|----------|
| Solar PV       | Primary generation (daytime)          | 600 kWp       | 1        |
| LFP BESS       | Night + morning ramp buffer           | 650 kWh       | 2        |
| LFTZ Grid      | Peak shaving top-up; BESS recharge    | 400 kVA supply| 3        |
| Perkins Diesel | Emergency / extended grid outage only | 400 kVA       | 4        |

**Automatic Transfer Switch Logic (ATS — Socomec ATYS 3S):**
- Normal: Solar + BESS + Grid (hybrid, grid as buffer)
- Grid drop: Solar + BESS island mode — seamless < 30 ms transfer
- BESS < 15% SoC + grid absent: Generator auto-start, ATS transfers, load protection

---

## 6. Energy Intensity Targets by Product

| Product                      | Phase 1 Target       | Basis                                                         |
|------------------------------|----------------------|---------------------------------------------------------------|
| Smart Meter (Electricity)    | ≤ 0.6 kWh / unit     | SMT + meter assembly + calibration bench (24h) ÷ daily yield |
| Smart Meter (Water)          | ≤ 0.5 kWh / unit     | SMT + water line assembly + gravimetric calibration           |
| Smart Estate Hub             | ≤ 1.2 kWh / unit     | SMT + hub assembly + RF test bench + firmware flash           |
| Smart Pole System            | ≤ 8.0 kWh / unit     | Welding + electronics integration + powder coat prep          |
| City Traffic Controller      | ≤ 12.0 kWh / unit    | Cabinet assembly + integrated test + burn-in                  |
| Environmental Sensor Node    | ≤ 0.4 kWh / unit     | PCB SMT + sensor calibration + potting                        |
| LoRaWAN Gateway              | ≤ 1.0 kWh / unit     | SMT + concentrator integration + IP67 test + provisioning     |

---

## 7. Sustainability Metrics

| Metric                           | Value / Target                                                |
|----------------------------------|---------------------------------------------------------------|
| Solar Self-Sufficiency           | ≥ 80% of annual operational energy                           |
| Estimated Annual CO₂ Avoidance   | ~520 tonnes CO₂/year (vs 100% diesel baseline)               |
| CO₂ Intensity (grid baseline)    | 0.431 kg CO₂/kWh (Nigeria grid average — EPA 2022)           |
| Generator Diesel Usage Target    | < 2,000 litres/year (emergency use only)                     |
| BESS LFP Cycle Life Target       | ≥ 3,000 cycles @ 90% DoD → ~8-year BESS life                |
| Waste Heat Recovery (future)     | Phase 2: reflow oven exhaust heat for hot-water pre-heat      |
| EMS Reporting                    | Real-time energy per zone; monthly sustainability report to NEPZA |

---

*See [`machinery.md`](./machinery.md) for equipment load specifications. See [`capex-opex.md`](./capex-opex.md) for energy system CapEx. See [`digital-twin.md`](./digital-twin.md) for DT energy sensor asset registry.*
