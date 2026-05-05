# Smart Home & Office Electronics Factory — Floor Plan & Facility Layout

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Smart Home & Office Electronics Factory | **Location:** Agbara Industrial Estate, Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Facilities & Engineering Team

---

## 1. Site Overview

| Parameter               | Detail                                          |
|-------------------------|-------------------------------------------------|
| Total Plot Area         | ~32,000 m² (3.2 hectares)                       |
| Factory Building        | ~16,000 m²                                      |
| Office / Admin Block    | ~900 m²                                         |
| Finished Goods Warehouse| ~2,500 m²                                       |
| Rooftop Solar           | ~8,000 m² usable (750 kWp)                      |
| Truck Yard              | ~4,500 m² (4 loading bays — 65" TV pallets)    |
| Perimeter               | Fenced; CCTV; guard posts                       |

---

## 2. Building Zone Allocations

| Zone | Zone Name                              | Area (m²) | Height (m) | Key Features                                               |
|------|----------------------------------------|-----------|------------|------------------------------------------------------------|
| Z1   | Raw Material Store                     | 1,600     | 9          | Racking; anti-static; display panel flat storage           |
| Z2   | SMT PCB Line 1                         | 1,100     | 6          | ESD floor; precision HVAC; dedicated to TV main boards     |
| Z3   | SMT PCB Line 2                         | 1,100     | 6          | ESD floor; dedicated to laptop, router, speaker PCBs       |
| Z4   | TV Panel Prep + Screen Bonding         | 1,200     | 6          | 4× screen bonding machines; UV cure ovens; clean bench     |
| Z5   | Smart TV Assembly Lines (×2)           | 1,800     | 6          | 2 parallel conveyor lines (32–43" and 55–65")              |
| Z6   | Laptop Assembly Line                   | 900       | 5          | Keyboard; display; battery; trackpad; torque stations      |
| Z7   | Router + Smart Hub Assembly            | 700       | 5          | PCB insertion; antenna; RF functional test                 |
| Z8   | Smart Speaker + Projector Assy         | 700       | 5          | Acoustic test booth; projector optical alignment station   |
| Z9   | RF + NCC Pre-Compliance Test Zone      | 500       | 5          | 3 RF shielded chambers; NCC TA preparation                 |
| Z10  | In-Process QC (IPQC)                   | 700       | 5          | Screen visual QC; AI vision station; laptop functional     |
| Z11  | Final QC + OBA                         | 500       | 5          | Final inspection; OBA sampling; NCC label application      |
| Z12  | Packaging & Labelling                  | 900       | 6          | Auto carton erector; TV poly-bag station                   |
| Z13  | Finished Goods Warehouse               | 2,500     | 9          | Pallet racking; large-format TV pallet storage             |
| Z14  | Maintenance Workshop                   | 400       | 5          | SMT spare parts; screen bonding lamp store                 |
| Z15  | IT / MES Server Room                   | 100       | 3          | Edge servers; NCC RF data storage                          |
| Z16  | EHS + First Aid                        | 200       | 3          | First aid; EHS office                                      |
| Z17  | Staff Facilities                       | 400       | 3          | Canteen; lockers; prayer room                              |

---

## 3. Floor Layout Diagram

```
┌────────────────────────────────────────────────────────────────────┐
│                       PERIMETER FENCE                              │
│                                                                    │
│  [TRUCK YARD — 4 LOADING BAYS (wide for 65" TV pallets)]         │
│                    │                                               │
│  ┌─────────────────┴──────────────────────────────────────────┐   │
│  │                                                            │   │
│  │  [Z1 - RMS]  [Z2 - SMT LINE 1]  [Z3 - SMT LINE 2]        │   │
│  │                                                            │   │
│  │  [Z4 - TV PANEL PREP + SCREEN BONDING × 4]               │   │
│  │                                                            │   │
│  │  [Z5 - SMART TV ASSEMBLY LINE 1 ─────────────────────]   │   │
│  │  [Z5 - SMART TV ASSEMBLY LINE 2 ─────────────────────]   │   │
│  │                                                            │   │
│  │  [Z6 - LAPTOP ASSEMBLY]  [Z7 - ROUTER+HUB]  [Z8 - SPEAKER]│  │
│  │                                                            │   │
│  │  [Z9 - RF/NCC TEST ZONE]  [Z10 - IPQC]  [Z11 - FINAL QC] │   │
│  │                                                            │   │
│  │  [Z12 - PACKAGING]  [Z13 - FGW]                           │   │
│  │                                                            │   │
│  │  [Z14 - MAINT]  [Z15 - IT]  [Z16 - EHS]  [Z17 - STAFF]   │   │
│  └────────────────────────────────────────────────────────────┘   │
│                                                                    │
│  [OFFICE / ADMIN BLOCK]          [ROOFTOP SOLAR — 750 kWp]       │
└────────────────────────────────────────────────────────────────────┘
```

---

## 4. Material Flow

### 4.1 Smart TV Flow

```
Z1 (RMS) → Z2 (SMT PCB) → Z4 (Screen Bonding) → Z5 (TV Assembly) → Z9 (RF QC) → Z10 (IPQC) → Z11 (Final QC) → Z12 (Pkg) → Z13 (FGW)
```

### 4.2 Laptop Flow

```
Z1 (RMS) → Z3 (SMT PCB) → Z6 (Laptop Assembly) → Z10 (IPQC — battery + display) → Z11 (Final QC) → Z12 (Pkg) → Z13 (FGW)
```

### 4.3 Router / Hub / Speaker Flow

```
Z1 (RMS) → Z3 (SMT PCB) → Z7 or Z8 (Assembly) → Z9 (RF Test) → Z11 (Final QC) → Z12 (Pkg) → Z13 (FGW)
```

---

## 5. Display Panel Storage — Special Requirements

65-inch and 55-inch TV panels require flat horizontal storage with special foam interleaving. Zone Z1 has a dedicated panel flat-rack storage area:

| Panel Size | Stack Height | Rack Spacing (mm) | AMR Compatible? | Notes                |
|------------|--------------|--------------------|-----------------|----------------------|
| 32" / 43"  | 50 panels/rack | 15 mm foam       | MiR250 (vertical carry) | Standard pallet compat |
| 55"        | 30 panels/rack | 20 mm foam       | Dedicated panel carrier | Fragile — max 3G shock |
| 65"        | 20 panels/rack | 25 mm foam       | Dedicated panel carrier | Extra-wide rack; no stacking |

---

## 6. Phase 2 Space Provisions

- Z4: Space reserved for 4× cobot screen bonding cells replacing manual bonding stations
- Z5: Conveyor aisle widening (+2 m) for 65" TV assembly Phase 2 expansion
- Z10: AI vision QC cameras pre-wired in ceiling at all IPQC stations (Phase 2 activation)

---

*Refer to [`machinery.md`](./machinery.md) for equipment list per zone.*
*Refer to [`energy-profile.md`](./energy-profile.md) for solar/BESS design.*
