# Security Electronics Factory — Floor Plan & Facility Layout

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Security Electronics Factory | **Location:** Ikorodu Industrial Estate, Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Facilities & Engineering Team

---

## 1. Site Overview

| Parameter               | Detail                                       |
|-------------------------|----------------------------------------------|
| Total Plot Area         | ~20,000 m² (2.0 hectares)                    |
| Factory Building        | ~11,000 m²                                   |
| Office / Admin Block    | ~600 m²                                      |
| Finished Goods Warehouse| ~1,500 m²                                    |
| Rooftop Solar           | ~5,500 m² usable (500 kWp)                   |
| Truck / Loading Area    | ~2,500 m² (3 loading bays)                   |
| Perimeter               | Fenced; CCTV; guard posts                    |

---

## 2. Building Zone Allocations

| Zone | Zone Name                           | Area (m²) | Height (m) | Key Features                                             |
|------|-------------------------------------|-----------|------------|----------------------------------------------------------|
| Z1   | Raw Material Store                  | 1,000     | 9          | Racking; ESD-controlled sub-zone; CMOS sensor cold store |
| Z2   | SMT PCB Line                        | 900       | 6          | ESD floor; precision HVAC; 22–24°C; 40–60% RH           |
| Z3   | Camera Housing + Lens Prep          | 600       | 5          | ISO Class 7 cleanroom bay for optical sub-assembly       |
| Z4   | IP Camera Assembly Line             | 1,100     | 5          | Lens mount; IR LED; housing; potting; sealing            |
| Z5   | Camera Optical + IP Test            | 500       | 5          | MTF test; IR illumination test; IP66 water spray test    |
| Z6   | NVR / DVR + AI NVR Assembly         | 800       | 5          | HDD installation; PoE port test; AI model deploy station |
| Z7   | Access Control Assembly             | 400       | 5          | PCB insertion; RFID/biometric test; IP enclosure seal    |
| Z8   | Alarm + Video Intercom Assembly     | 400       | 5          | Panel board; GSM module; touchscreen test                |
| Z9   | RF + NCC Pre-Compliance Test        | 300       | 5          | 2 RF shielded chambers; Wi-Fi/BT NCC pre-compliance      |
| Z10  | In-Process QC + Final QC            | 500       | 5          | AI vision cosmetic check; functional test; ANPR test     |
| Z11  | Packaging & Labelling               | 500       | 6          | Auto carton erector; camera foam insert; seal and label  |
| Z12  | Finished Goods Warehouse            | 1,500     | 9          | Racking; dispatch                                        |
| Z13  | Maintenance Workshop                | 300       | 5          | Tool room; SMT spare parts; optical fixture store        |
| Z14  | IT / MES + AI Server Room           | 100       | 3          | Edge servers; AI NVR test server (NVIDIA Jetson cluster) |
| Z15  | EHS + First Aid                     | 150       | 3          | First aid room; EHS office                               |
| Z16  | Staff Facilities                    | 300       | 3          | Canteen; lockers; prayer room                            |

---

## 3. Floor Layout Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                     PERIMETER FENCE                             │
│                                                                 │
│  [TRUCK YARD — 3 LOADING BAYS]   [STAFF + VISITOR PARKING]    │
│           │                                                     │
│  ┌────────┴────────────────────────────────────────────────┐   │
│  │                                                         │   │
│  │  [Z1 - RMS]        [Z2 - SMT LINE]                     │   │
│  │                                                         │   │
│  │  [Z3 - CAMERA HOUSING PREP (Cleanroom)]                │   │
│  │                                                         │   │
│  │  [Z4 - IP CAMERA ASSEMBLY ─────────────────────────]  │   │
│  │                                                         │   │
│  │  [Z5 - OPTICAL + IP TEST]   [Z6 - NVR/DVR + AI NVR]  │   │
│  │                                                         │   │
│  │  [Z7 - ACCESS CTRL]   [Z8 - ALARM + INTERCOM]         │   │
│  │                                                         │   │
│  │  [Z9 - RF/NCC TEST]   [Z10 - QC]   [Z11 - PACKAGING]  │   │
│  │                                                         │   │
│  │  [Z12 - FGW]                                           │   │
│  │                                                         │   │
│  │  [Z13 - MAINT] [Z14 - IT/AI] [Z15 - EHS] [Z16 - STAFF]│   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  [OFFICE / ADMIN]              [ROOFTOP SOLAR — 500 kWp]       │
└─────────────────────────────────────────────────────────────────┘
```

---

## 4. Material Flow

### 4.1 IP Camera Flow

```
Z1 (RMS) → Z2 (SMT PCB) → Z3 (Camera Housing Prep) → Z4 (Camera Assembly) → Z5 (Optical + IP Test) → Z10 (QC) → Z11 (Pkg) → Z12 (FGW)
```

### 4.2 NVR / DVR Flow

```
Z1 (RMS) → Z2 (SMT PCB) → Z6 (NVR Assembly + AI Test) → Z10 (QC) → Z11 (Pkg) → Z12 (FGW)
```

---

## 5. Camera Optical Zone (Z3 + Z5) — Special Requirements

The IP camera optical sub-assembly and test zone requires controlled particulate levels to prevent sensor contamination:

| Feature                   | Specification                                        |
|---------------------------|------------------------------------------------------|
| Cleanroom Class           | ISO Class 7 (Class 10,000) in lens mount bay (Z3)   |
| HEPA Filtration           | Overhead HEPA air supply; positive pressure maintained |
| ESD Control               | ESD mats; ionising blowers over lens mount stations  |
| Personnel PPE             | Cleanroom smocks; gloves; no loose accessories       |
| Lens Handling             | Vacuum pen only; no direct finger contact            |
| CMOS Sensor Storage       | Sealed ESD + anti-static containers; 20°C ±2°C cold store |

---

## 6. Phase 2 Space Provisions

- Z4 (Camera Assembly): 2 m aisle extension reserved for 2× robotic lens alignment cells
- Z10 (QC): AI vision camera mounts pre-wired in ceiling (Phase 2 activation)
- Z14 (IT/AI Server Room): Rack space reserved for expanded AI inference cluster (Phase 3)

---

*Refer to [`machinery.md`](./machinery.md) for equipment details.*
*Refer to [`energy-profile.md`](./energy-profile.md) for solar/BESS.*
