# Garage & Power Electronics Factory — Floor Plan & Facility Layout

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Garage & Power Electronics Factory | **Location:** Sagamu Industrial Estate, Ogun State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Facilities & Engineering Team

---

## 1. Site Overview

| Parameter                  | Detail                                                |
|----------------------------|-------------------------------------------------------|
| Total Plot Area            | ~25,000 m² (2.5 hectares)                            |
| Factory Building           | ~12,000 m²                                           |
| Office / Admin Block       | ~600 m²                                              |
| Finished Goods Warehouse   | ~1,800 m²                                            |
| Ground-Mount Solar Yard    | ~5,000 m² (dedicated solar field; 600 kWp)          |
| Truck Logistics Area       | ~3,000 m² (3 loading bays)                          |
| Perimeter                  | Fenced; guard posts; CCTV                            |

---

## 2. Building Zone Allocations

| Zone | Zone Name                         | Area (m²) | Height (m) | Key Features                                            |
|------|-----------------------------------|-----------|------------|---------------------------------------------------------|
| Z1   | Raw Material & Component Store    | 1,200     | 9          | Racking; incoming QC; ESD sub-zone for PCB components   |
| Z2   | SMT PCB Line                      | 1,000     | 6          | ESD floor; precision HVAC; 22–24°C; 40–60% RH          |
| Z3   | Transformer Winding Cells         | 600       | 5          | 6 manual winding benches; ESD; mag wire storage         |
| Z4   | Inverter Assembly Lines (×3)      | 2,200     | 6          | 3 parallel conveyor lines; chassis assembly; wiring     |
| Z5   | Solar Charge Controller Assembly  | 600       | 5          | PCB insertion; programming stations; SCC test rigs      |
| Z6   | UPS & Battery Charger Assembly    | 500       | 5          | UPS chassis; battery installation; transfer-time test   |
| Z7   | Power Tool Assembly Lines (×2)    | 700       | 6          | Motor installation; gearbox; run-test benches           |
| Z8   | Power Strip / Surge Assembly (×2) | 700       | 5          | Automated surge test; wiring; IEC socket insert         |
| Z9   | Load Bank Auto-Test (Inverters)   | 800       | 6          | 8 parallel test bays; Ametek/Cinergia; full-load 8-min  |
| Z10  | In-Process QC + Final QC          | 500       | 5          | Hipot; insulation tester; visual; OBA sampling          |
| Z11  | Packaging & Labelling             | 700       | 6          | Auto carton erector; sealer; label applicator           |
| Z12  | Finished Goods Warehouse          | 1,800     | 9          | Pallet racking; dispatch                                |
| Z13  | Maintenance Workshop              | 350       | 5          | Tool room; spare inverter modules; SMT spare parts      |
| Z14  | IT / MES Server Room              | 80        | 3          | Edge servers; network core                              |
| Z15  | EHS + First Aid                   | 150       | 3          | First aid; EHS officer office                           |
| Z16  | Staff Facilities                  | 320       | 3          | Canteen; lockers; prayer room                           |

---

## 3. Floor Layout Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                     PERIMETER FENCE                             │
│                                                                 │
│  [TRUCK YARD — 3 LOADING BAYS]   [STAFF + VISITOR PARKING]    │
│          │                                                      │
│  ┌───────┴─────────────────────────────────────────────────┐   │
│  │                                                         │   │
│  │  [Z1 - RMS]       [Z2 - SMT LINE]    [Z3 - WINDING]   │   │
│  │                                                         │   │
│  │  [Z4 - INVERTER ASSEMBLY LINE 1 ─────────────────]    │   │
│  │  [Z4 - INVERTER ASSEMBLY LINE 2 ─────────────────]    │   │
│  │  [Z4 - INVERTER ASSEMBLY LINE 3 ─────────────────]    │   │
│  │                                                         │   │
│  │  [Z5 - SCC ASSY]   [Z6 - UPS ASSY]   [Z7 - POWER TOOL]│   │
│  │                                                         │   │
│  │  [Z8 - POWER STRIP] [Z9 - LOAD BANK TEST (8 bays)]    │   │
│  │                                                         │   │
│  │  [Z10 - FINAL QC]  [Z11 - PACKAGING]  [Z12 - FGW]     │   │
│  │                                                         │   │
│  │  [Z13 - MAINT]  [Z14 - IT]  [Z15 - EHS]  [Z16 - STAFF]│   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  [OFFICE / ADMIN BLOCK]    [GROUND-MOUNT SOLAR FIELD 600kWp]  │
└─────────────────────────────────────────────────────────────────┘
```

---

## 4. Material Flow

### 4.1 Inverter Production Flow

```
Z1 (RMS) → Z2 (SMT — PCB sub-assy) → Z3 (Winding — transformer) → Z4 (Inverter Assembly)
                                                                        ↓
                                                               Z9 (Load Bank Test)
                                                                        ↓
                                                               Z10 (Final QC) → Z11 (Pkg) → Z12 (FGW)
```

### 4.2 Power Strip / SCC Flow

```
Z1 (RMS) → Z2 (SMT) → Z5 / Z8 (SCC or Strip Assy) → Z10 (QC) → Z11 (Pkg) → Z12 (FGW)
```

### 4.3 AMR Routing

| AMR ID    | Primary Route                              | Mission Type         |
|-----------|--------------------------------------------|----------------------|
| AMR-01/04 | Z1 → Z4 (inverter chassis kitting)         | Inbound replenishment|
| AMR-05/08 | Z9 → Z11 (tested units to packaging)       | WIP to pack          |
| AMR-09/10 | Z1 → Z2 (SMT reel replenishment)           | SMT kitting          |
| AMR-11/12 | Z11 → Z12 (packaged goods to FGW)         | Finished goods       |

---

## 5. Load Bank Test Zone (Z9) — Design Details

The load bank test zone is a specialised area unique to power electronics manufacture. Each inverter must be tested at full-rated output for ≥ 5 minutes to confirm:

| Test Parameter             | Method                           | Pass Criterion                    |
|----------------------------|----------------------------------|-----------------------------------|
| Output Voltage (AC)        | Precision voltmeter              | ±2% of rated voltage              |
| Output Frequency           | Frequency counter                | 50 Hz ± 0.2 Hz                    |
| Output Power               | Power analyser                   | ≥ 98% of rated VA                 |
| Efficiency (η)             | Input/Output power ratio         | ≥ 88% at 75% load (per IEC 62040) |
| Waveform THD               | Oscilloscope / analyser          | < 3% THD at full load             |
| Transfer Time (UPS models) | Automated relay switching        | < 10 ms (line-interactive class)  |
| Thermal Performance        | Thermal camera + thermocouple    | Hotspot < 85°C at full load       |

**Test Bay Layout (8 bays):**
- Each bay: 1 load bank (Ametek RS Series or Cinergia GE series), 1 power analyser, 1 DUT fixture
- Test bays connected via OPC-UA to MES load bank module
- Test cycle automated: result auto-written to MES serial number record
- Reject conveyor: failed units automatically diverted to Z13 (maintenance/rework)

---

## 6. ESD Zone Design (Z2 — SMT)

| Feature                  | Specification                          |
|--------------------------|----------------------------------------|
| Flooring                 | Conductive ESD tile (< 1 MΩ to ground) |
| HVAC                     | Precision unit; 22–24°C ±1°C; 40–60% RH |
| Personnel Protection     | ESD wrist straps; ESD footwear          |
| Component Storage        | ESD bags; anti-static foam; controlled humidity cabinet |
| Ionisers                 | Over P&P machines and paste printer    |

---

## 7. Phase 2 Space Provisions

- Z3 (Winding): space reserved for 2× CNC transformer winding machines to replace manual stations
- Z4 (Inverter Lines): 3 m aisle widening provision for Phase 2 cobot deployment alongside Line 3

---

*Refer to [`machinery.md`](./machinery.md) for full equipment list.*
*Refer to [`energy-profile.md`](./energy-profile.md) for solar yard specifications.*
