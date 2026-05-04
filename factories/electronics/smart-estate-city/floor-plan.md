# Coo-Cah Smart Estate & City Electronics Factory — Floor Plan

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Vertical:** Electronics — Smart City & Estate Infrastructure | **Location:** Lekki Free Trade Zone (LFTZ), Lagos State, Nigeria | **Phase:** Phase 1
> **Document Version:** 1.0 | **Status:** In Development

---

## 1. Facility Overview

| Attribute                  | Details                                                     |
|----------------------------|-------------------------------------------------------------|
| Total Site Area (LFTZ Lease)| ~22,000 m² (including external yard, car park, future expansion) |
| Built-Up Factory Area       | ~14,000 m²                                                  |
| Building Footprint          | ~10,800 m² (production + warehouse + QC + services)         |
| Mezzanine / Office Level    | ~1,200 m² (above RMS and services)                          |
| External Hardstand / Yard   | ~3,000 m² (container staging, smart pole hardstand, generator enclosure) |
| Car Park (doubles as solar canopy) | ~2,000 m² (120 kWp canopy solar)                    |
| Ceiling Height — Production | 9 m clear (structural steel portal frame)                   |
| Ceiling Height — Warehouse  | 9 m (racking to 6 m, top beam at 8.5 m)                    |
| Column Grid                 | 12 m × 12 m (column-free production spans possible)         |
| Floor Loading               | 10 kN/m² (production), 20 kN/m² (warehouse/AMR aisles)     |
| ESD Flooring                | Conductive epoxy flooring (ANSI/ESD S20.20) in all PCB/assembly zones |
| HVAC                        | Daikin VRV multi-split throughout; precision ±1°C in Calibration Lab |

---

## 2. Zone Summary

| Zone Code | Zone Name                             | Area (m²) | Level     | Key Contents                                        |
|-----------|---------------------------------------|-----------|-----------|-----------------------------------------------------|
| LD-IN     | Inbound Loading Dock                  | 480       | Ground    | 4 dock levellers, container staging, barcode scan-in |
| RMS       | Raw Material Store                    | 1,200     | Ground    | Pallet racking (ESD), SMT reel tower, bonded cage for ICs |
| IQC       | Incoming Quality Control              | 320       | Ground    | Inspection benches, dimensional check, IEC 62053 ref samples |
| STG       | Component Staging (Kitting)           | 280       | Ground    | AMR kitting bays, SMT feeder trolleys, pick-to-light |
| PL-SMT    | SMT PCB Assembly Lines (×2)           | 1,600     | Ground    | Dual line: printer→SPI→P&P→reflow→AOI→ICT→programming |
| PL-METER  | Smart Meter Assembly (Electricity)    | 1,100     | Ground    | 2 conveyor lines, ultrasonic weld, calibration handoff |
| PL-WATER  | Smart Water Meter Assembly            | 520       | Ground    | Transducer press-fit, flow body test, smart lid bench |
| PL-HUB    | Smart Estate Hub Assembly             | 420       | Ground    | Hub chassis jigs, flash station, RF test enclosures  |
| PL-POLE   | Smart Pole Fabrication & Assembly     | 1,400     | Ground    | CNC plasma, welding bays, galv pre-treat, jigs       |
| PL-TRAFFIC| Traffic Controller / ESN / LoRa Line  | 540       | Ground    | Cabinet assembly benches, sensor calibration rig     |
| PL-COAT   | Conformal Coating & Potting           | 280       | Ground    | Nordson ASYMTEK, UV tunnel, potting machine          |
| IPQC      | In-Process Quality Control            | 240       | Ground    | Inspection benches embedded in each line corridor    |
| RWK       | Rework & Repair Cell                  | 180       | Ground    | BGA rework station, ICT re-test, failure analysis bench |
| CAL-LAB   | Calibration Laboratory                | 480       | Ground    | 4× IEC 62053 calibration benches, 2× gravimetric rigs, precision HVAC ±1°C |
| FQC       | Final Quality Control                 | 320       | Ground    | FQC inspection, RF/protocol check, spot re-calibration |
| PKG       | Packaging Line                        | 480       | Ground    | Auto label, carton erect, foam insert, tape & seal, carton print |
| FGW       | Finished Goods Warehouse              | 1,400     | Ground    | 4,000 pallet positions, racking, FIFO pick lanes     |
| LD-OUT    | Outbound Dispatch Dock                | 320       | Ground    | 3 dock levellers, manifest scan, staging              |
| SVC       | Services (Compressor, EMS, E-room)    | 360       | Ground    | Compressed air, MV substation, ATS, BESS enclosure   |
| IT-ROOM   | IT / MES Server Room                  | 60        | Ground    | MES servers, network core, CCTV NVR, UPS             |
| MZOFFICE  | Mezzanine Office & Training           | 1,200     | Mezzanine | Management offices, meeting rooms, training lab, canteen |
| EXT-YARD  | External Hard-Stand Yard              | 3,000     | External  | Smart pole staging (assembled, pre-dispatch), container bay, generator enclosure, EHS yard |

---

## 3. Detailed Zone Descriptions

### 3.1 LD-IN — Inbound Loading Dock
Four dock-leveller bays (mechanical, 6-tonne rated) with container-height alignment ramps. All inbound materials — imported SMT components, Coo-Cah Plastics Factory enclosures, raw aluminium/steel — are received here. Each pallet receives a GRN barcode scan on arrival; the MES raises an IQC inspection order automatically for new part numbers or incoming inspection-required items. Forklift charging bay is co-located. The dock overhead doors are insulated roller shutters (3.5 m × 3.5 m).

### 3.2 RMS — Raw Material Store
1,200 m² adjustable pallet racking (Mecalux VNA), 4,000 pallet positions across 6 m height. An ESD-rated bonded cage within RMS stores high-value imported ICs (Renesas RL78, Cirrus Logic CS5480/90, Semtech SX1302, Quectel BC660) under restricted access. Moisture Sensitive Level (MSL) cabinets hold ICs requiring dry-nitrogen storage. SMT tape reels are stored in a separate automated SMT reel tower (humidity-controlled, 5,000-reel capacity). AMR fleet has dedicated pick lanes through RMS.

### 3.3 PL-SMT — Dual SMT PCB Assembly Lines
The factory's PCB manufacturing hub: two fully parallel SMT lines, each 80 m long, laid out east–west with a 2.4 m operator aisle between lines. Board flow: screen printer → SPI → high-speed chipshooter → flexible mounter → reflow oven → post-reflow AOI → selective soldering (for THT connectors) → ICT → firmware flash station → conveyor buffer to product lines. SMT feeder trolleys are kitted in STG and wheeled to P&P machines. All PCBs carry a DMC barcode linked to the production order in MES throughout. SMT PCB scrap is sorted into Pb-free solder waste stream (NESREA compliance).

### 3.4 CAL-LAB — Calibration Laboratory
Environmentally controlled zone (±1°C, 45–55% RH precision) housing four IEC 62053-21/22 meter calibration benches and two gravimetric water meter calibration rigs. Access controlled — only calibration technicians and QA engineers. All calibration standards traceable to the Nigerian Institute of Standards (NIS) national reference, with NAFDAC-equivalent PTF chain for electricity metrology. Each calibrated unit receives a printed calibration certificate with a unique certificate ID recorded in the MES calibration database via the `POST /api/v1/calibration/meter` endpoint. Calibration records are immutable once written.

### 3.5 PL-POLE — Smart Pole Fabrication & Assembly
Largest production zone at 1,400 m², with 9 m clear height to accommodate 8 m pole sections during horizontal assembly on rotating cradle jigs. Dedicated extraction ventilation for welding fume (LEV system, 4,000 m³/h per welding bay). CNC plasma cutter at north end, welding bays running south, galvanising pre-treatment tanks at east wall (with ventilation extraction and acid-resistant floor coating), electronics integration jigs at south end. Finished poles are transferred to EXT-YARD via a side roller door (4 m × 4.5 m) on a custom pole trolley.

---

## 4. AMR Routing Map

```
[LD-IN] ──► [IQC] ──► [RMS]
                          │
              ┌───────────┼───────────┐
              ▼           ▼           ▼
           [STG]       [STG]       [STG]
             │           │           │
             ▼           ▼           ▼
         [PL-SMT]  [PL-POLE]  [PL-TRAFFIC]
             │           │           │
             └─────┬─────┘           │
                   ▼                 ▼
               [PL-METER]       [PL-COAT]
               [PL-WATER]           │
               [PL-HUB]             ▼
                   │            [IPQC/RWK]
                   ▼                 │
               [PL-COAT] ◄───────────┘
                   │
                   ▼
               [CAL-LAB]
                   │
                   ▼
                [FQC]
                   │
                   ▼
                [PKG]
                   │
                   ▼
                [FGW]
                   │
                   ▼
               [LD-OUT]
```

**AMR Mission Types:**

| Mission Code | Description                                          | Trigger                                     |
|--------------|------------------------------------------------------|---------------------------------------------|
| AMR-KIT-SMT  | Kit SMT reels from RMS to PL-SMT feeder trolley     | MES production order release                |
| AMR-KIT-PROD | Kit component trays from RMS/STG to product lines   | MES production order release                |
| AMR-WIP-MOVE | Transfer WIP bins between assembly zones            | MES station complete scan                   |
| AMR-CAL      | Transfer metered units to CAL-LAB queue             | Meter assembly FQC scan (pre-calibration)   |
| AMR-FGW      | Move packaged cartons from PKG to FGW pallet        | Packaging complete scan                     |
| AMR-RETN     | Return empty containers / rejected WIP to RWK/RMS   | MES rejection scan                          |

---

## 5. Future Expansion Zones

| Zone         | Phase | Planned Use                                                          | Estimated Area |
|--------------|-------|----------------------------------------------------------------------|----------------|
| EXP-SMT3     | 2     | Third SMT line for volume ramp to 1M+ smart meters/year             | 800 m²         |
| EXP-SOLAR    | 2     | Additional rooftop solar (200 kWp) + canopy expansion               | Rooftop        |
| EXP-ROBOTICS | 2     | Robotic conformal coating + AI vision inspection cells              | 400 m²         |
| EXP-PCBFAB   | 3     | Potential PCB bare-board fabrication line (subject to demand)        | 2,000 m²       |
| EXP-TRAINING | 2     | Expanded technical training centre; NCC-accredited testing lab       | 400 m²         |

---

*See [`machinery.md`](./machinery.md) for equipment specifications. See [`automation-roadmap.md`](./automation-roadmap.md) for expansion timelines.*
