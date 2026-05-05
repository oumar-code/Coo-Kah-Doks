# Kitchen Electronics Factory — Floor Plan & Facility Layout

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Kitchen Electronics Factory | **Location:** Agbara Industrial Estate, Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Facilities & Engineering Team

---

## 1. Site Overview

| Parameter                  | Detail                                                        |
|----------------------------|---------------------------------------------------------------|
| Total Plot Area            | ~30,000 m² (3 hectares)                                       |
| Factory Building Footprint | ~15,000 m²                                                    |
| Office / Admin Block       | ~800 m²                                                       |
| Warehouse (Finished Goods) | ~2,200 m²                                                     |
| Rooftop Solar              | ~7,800 m² usable for PV (700 kWp)                            |
| Truck Yard / Logistics     | ~4,000 m² (4 loading bays, truck queuing area)               |
| Perimeter Security         | Fenced; 4 guard posts; CCTV coverage                         |
| Special Infrastructure     | Dedicated R600a gas handling area with ventilation             |

---

## 2. Building Zone Allocations

| Zone Code | Zone Name                        | Area (m²) | Height (m) | Key Features                                      |
|-----------|----------------------------------|-----------|------------|---------------------------------------------------|
| Z1        | Raw Material & Component Store   | 1,500     | 9          | Racking; incoming QC bay; ESD-controlled sub-zone |
| Z2        | SMT PCB Production               | 1,200     | 6          | ESD flooring; positive pressure; 22–24°C, 40–60% RH |
| Z3        | Refrigerator Sheet Metal Fab     | 1,000     | 9          | Roll-form lines; press; overhead crane            |
| Z4        | Refrigerator Assembly — Main     | 2,200     | 9          | Overhead chain conveyor; PU foam station          |
| Z5        | R600a Gas Charging Zone          | 600       | 6          | ATEX-rated; negative-pressure ventilation; gas detectors |
| Z6        | Microwave Oven Assembly          | 800       | 6          | Cavity press; spot weld; hi-pot test              |
| Z7        | Electric Cooker Assembly         | 700       | 6          | Induction coil winding; glass surface bonding     |
| Z8        | SDA Assembly Lines (A, B, C)     | 1,800     | 6          | 3 parallel conveyor lines; blenders, kettles, rice cookers, toasters |
| Z9        | In-Process QC (IPQC)             | 600       | 5          | Testing bays; noise testing booths; safety test   |
| Z10       | Final QC + OBA                   | 700       | 5          | Final inspection; outbound quality audit          |
| Z11       | Packaging & Labelling            | 900       | 6          | Auto carton erector, sealer, labeller             |
| Z12       | Finished Goods Warehouse         | 2,200     | 9          | Pallet racking; dispatch bays                     |
| Z13       | Maintenance Workshop             | 400       | 5          | Tool room; spare parts store; welding bay         |
| Z14       | Compressor & Test Services       | 400       | 5          | Refrigerant recovery; nitrogen leak test          |
| Z15       | EHS & First Aid                  | 200       | 3          | First aid room; eyewash; EHS office               |
| Z16       | IT / MES Server Room             | 100       | 3          | Edge servers; network core; MES edge node         |
| Z17       | Staff Facilities                 | 400       | 3          | Canteen; locker rooms; prayer room                |

---

## 3. Floor Layout Diagram

```
┌──────────────────────────────────────────────────────────────────────┐
│                       PERIMETER FENCE                                │
│                                                                      │
│  [TRUCK YARD / LOADING BAYS]  [VISITOR PARKING]   [STAFF PARKING]   │
│         │              │                                              │
│  ┌──────┴──────────────┴────────────────────────────────────────────┐│
│  │                                                                  ││
│  │  [Z1 - RMS]  [Z2 - SMT]  [Z3 - SHEET METAL FAB]               ││
│  │                                                                  ││
│  │  [Z4 - REFRIGERATOR ASSEMBLY MAIN ─────────────────────]       ││
│  │      (Overhead Chain Conveyor runs through entire zone)         ││
│  │                                                                  ││
│  │  [Z5 - GAS CHARGING]  [Z14 - COMPRESSOR SERVICES]              ││
│  │                                                                  ││
│  │  [Z6 - MICROWAVE]   [Z7 - COOKER]   [Z8 - SDA A/B/C]         ││
│  │                                                                  ││
│  │  [Z9 - IPQC]   [Z10 - FINAL QC]   [Z11 - PACKAGING]           ││
│  │                                                                  ││
│  │  [Z12 - FINISHED GOODS WAREHOUSE]                               ││
│  │                                                                  ││
│  │  [Z13 - MAINTENANCE] [Z15 - EHS] [Z16 - IT/MES] [Z17 - STAFF] ││
│  └──────────────────────────────────────────────────────────────────┘│
│                                                                      │
│  [OFFICE / ADMIN BLOCK]     [SOLAR YARD - GROUND MOUNT POTENTIAL]   │
└──────────────────────────────────────────────────────────────────────┘
```

---

## 4. Material Flow

### 4.1 Primary Material Flow — Refrigerators

```
Z1 (RMS) → Z2 (SMT — PCB sub-assy) → Z3 (Sheet Metal Fab) → Z4 (Main Assy Line)
                                                                ↓
                                                         Z5 (Gas Charging)
                                                                ↓
                                                         Z14 (Compressor Test)
                                                                ↓
                                                         Z9 (IPQC) → Z11 (Packaging) → Z12 (FGW)
```

### 4.2 Primary Material Flow — SDAs (Blenders, Kettles, Rice Cookers, Toasters)

```
Z1 (RMS) → Z2 (SMT — PCB sub-assy) → Z8 (SDA Lines A/B/C) → Z9 (IPQC) → Z10 (Final QC) → Z11 (Packaging) → Z12 (FGW)
```

### 4.3 AMR Routing

| AMR ID       | Primary Route                                      | Mission Type        |
|--------------|----------------------------------------------------|---------------------|
| AMR-01/02    | Z1 → Z4 (component kits for fridge line)           | Inbound replenishment |
| AMR-03/04    | Z1 → Z8 (SDA kitting) + Z8 → Z9 (WIP)             | Production kitting  |
| AMR-05/06    | Z9 → Z11 (IPQC pass → packaging)                   | WIP to pack         |
| AMR-07/08    | Z1 → Z2 (SMT reels + stencils); Z2 → store        | SMT replenishment   |

---

## 5. Key Infrastructure Features

### 5.1 R600a Gas Handling Zone (Z5) — Safety Design

The R600a gas charging zone is the highest-safety-risk zone in the factory. Design features:

| Feature                         | Detail                                                                  |
|---------------------------------|-------------------------------------------------------------------------|
| Zone Classification             | ATEX Zone 2 (below 0.5m from floor — R600a is heavier than air)        |
| Ventilation                     | Forced negative pressure; 15 air changes/hour minimum                  |
| Gas Detectors                   | 12× fixed electrochemical sensors; alarm at 10% LEL; shutdown at 25% LEL |
| Electrical Equipment            | ATEX-certified all equipment in zone; explosion-proof lighting          |
| Emergency Shutdown              | Big red manual ESD button; auto shutdown of gas charging pump on high alarm |
| Drainage                        | Sealed floor — no floor drains in zone (gas pooling prevention)         |
| Isolation                       | Positive-pressure air curtain at zone entry; interlocked with ventilation |
| Fire Suppression                | CO₂ suppression system in gas cylinder bay                              |
| PPE Requirements                | Anti-static garments; no phones; gas monitor badge mandatory            |

### 5.2 SMT Zone ESD Controls (Z2)

| Feature                         | Detail                                                          |
|---------------------------------|-----------------------------------------------------------------|
| Flooring                        | Conductive ESD tiles (< 1 MΩ to ground)                        |
| HVAC                            | Dedicated precision HVAC; 22–24°C ±1°C; 40–60% RH             |
| Humidity Control                | ESD ioniser bars over solder paste printer and P&P machines     |
| Personnel PPE                   | ESD wrist straps at all workstations; ESD footwear required     |
| Packaging                       | ESD bags and pink anti-static foam for all PCB movements        |

### 5.3 Overhead Chain Conveyor (Z3–Z4)

| Feature                         | Detail                                                          |
|---------------------------------|-----------------------------------------------------------------|
| Type                            | Overhead powered chain conveyor (Power & Free)                  |
| Length                          | ~60 m total loop                                                |
| Load Capacity                   | 200 kg per carrier (for fridge cabinet bodies)                  |
| Speed                           | Variable 1–5 m/min (PLC-controlled, MES takt-linked)           |
| Workstations                    | 12 stop-stations; doors, seals, compressor, gas charge, test    |

---

## 6. Phase 2 Space Provisions

Space has been pre-planned in the Refrigerator Assembly zone (Z4) for:
- 2× FANUC collaborative robot cells (foam injection and door assembly)
- Expanded conveyor loop extension (+12m for robot cells)

Space has been reserved in SDA zone (Z8) for:
- Lights-out capable conveyor conversion (automated loading/unloading in Phase 3)

---

## 7. Fire & Life Safety

| System                           | Zones Covered         | Type                                            |
|----------------------------------|-----------------------|-------------------------------------------------|
| Sprinkler System                 | Z1, Z3, Z11, Z12      | Wet pipe, ESFR for high-piled storage (FGW)     |
| FM-200 Gas Suppression           | Z2 (SMT), Z16 (IT)    | Gaseous — PCB and server protection             |
| CO₂ Suppression                  | Z5 (Gas Zone cyl. bay)| Fixed CO₂ system                               |
| Heat / Smoke Detectors           | All zones             | Addressable fire alarm panel (Notifier)         |
| Manual Call Points               | Every 20m             | Break-glass call points on all escape routes    |
| Emergency Lighting               | All zones             | 3-hour battery backup                           |
| Muster Points                    | 3 external points     | Assembly areas marked on all evacuation maps    |

---

*For machinery details in each zone, refer to [`machinery.md`](./machinery.md).*
*For energy infrastructure, refer to [`energy-profile.md`](./energy-profile.md).*
