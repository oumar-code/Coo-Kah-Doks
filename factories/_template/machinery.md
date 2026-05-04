# [FACTORY_NAME] — Machinery & Equipment Register

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** [FACTORY_NAME] | **Location:** [LOCATION] | **Phase:** [PHASE]
> **Document Version:** 1.0 | **Owner:** Factory Engineering Team

---

## 1. Introduction

This document provides the complete equipment register for [FACTORY_NAME]. Each entry includes the equipment name, quantity, specification or model reference, primary purpose within the production process, and its current automation level. This register is the source of truth for asset management, MES asset tagging, digital twin onboarding, and maintenance planning.

**Automation Level Legend:**

| Code | Level              | Description                                                    |
|------|--------------------|----------------------------------------------------------------|
| M    | Manual             | Operated entirely by human; no automation                      |
| SA   | Semi-Automated     | Machine performs primary action; human loads/unloads or monitors |
| A    | Automated          | Machine operates autonomously within its cycle; minimal human supervision |
| FA   | Fully Automated    | End-to-end autonomous operation; integrated with MES; self-alarming |
| AI   | AI-Augmented       | Machine data processed by Coo-Cah AI Platform for optimization or prediction |

---

## 2. Production Line Equipment

### 2.1 Primary Assembly / Fabrication Equipment

| # | Equipment             | Qty | Spec / Model           | Purpose                                          | Auto Level |
|---|-----------------------|-----|------------------------|--------------------------------------------------|------------|
| 1 | [MACHINE_NAME_1]      | [Q] | [SPEC/MODEL]           | [Description of function in production line]     | [LEVEL]    |
| 2 | [MACHINE_NAME_2]      | [Q] | [SPEC/MODEL]           | [Description of function in production line]     | [LEVEL]    |
| 3 | [MACHINE_NAME_3]      | [Q] | [SPEC/MODEL]           | [Description of function in production line]     | [LEVEL]    |
| 4 | [MACHINE_NAME_4]      | [Q] | [SPEC/MODEL]           | [Description of function in production line]     | [LEVEL]    |
| 5 | [MACHINE_NAME_5]      | [Q] | [SPEC/MODEL]           | [Description of function in production line]     | [LEVEL]    |
| 6 | [MACHINE_NAME_6]      | [Q] | [SPEC/MODEL]           | [Description of function in production line]     | [LEVEL]    |

### 2.2 Sub-Assembly Equipment

| # | Equipment             | Qty | Spec / Model           | Purpose                                          | Auto Level |
|---|-----------------------|-----|------------------------|--------------------------------------------------|------------|
| 1 | [MACHINE_NAME_7]      | [Q] | [SPEC/MODEL]           | [Sub-assembly operation description]             | [LEVEL]    |
| 2 | [MACHINE_NAME_8]      | [Q] | [SPEC/MODEL]           | [Sub-assembly operation description]             | [LEVEL]    |
| 3 | [MACHINE_NAME_9]      | [Q] | [SPEC/MODEL]           | [Sub-assembly operation description]             | [LEVEL]    |

### 2.3 Surface Mount Technology (SMT) Line *(if applicable)*

> *Complete this section if the factory includes PCB/PCBA production or assembly.*

| # | Equipment                     | Qty | Spec / Model              | Purpose                                             | Auto Level |
|---|-------------------------------|-----|---------------------------|-----------------------------------------------------|------------|
| 1 | Solder Paste Screen Printer   | [Q] | [SPEC]                    | Deposits solder paste onto PCB pads                 | FA         |
| 2 | Pick-and-Place Machine        | [Q] | [SPEC]                    | Places SMT components on PCB                        | FA/AI      |
| 3 | Reflow Oven                   | [Q] | [SPEC] — [N]-zone         | Solders SMT components via controlled heat profile  | FA         |
| 4 | AOI — Automated Optical Insp. | [Q] | [SPEC]                    | Detects solder defects, missing/misaligned parts    | FA/AI      |
| 5 | In-Circuit Test (ICT) System  | [Q] | [SPEC]                    | Tests PCB electrical connectivity and component values | SA      |
| 6 | Wave Soldering Machine        | [Q] | [SPEC]                    | Solders through-hole components                     | SA         |
| 7 | Selective Soldering Machine   | [Q] | [SPEC]                    | Selective through-hole soldering (complex boards)   | A          |
| 8 | PCB Depanelling Router        | [Q] | [SPEC]                    | Separates individual PCBs from panel                | A          |

---

## 3. Quality Control Equipment

| # | Equipment                        | Qty | Spec / Model     | Purpose                                                   | Auto Level |
|---|----------------------------------|-----|------------------|-----------------------------------------------------------|------------|
| 1 | [QC_MACHINE_1]                   | [Q] | [SPEC]           | [QC function — e.g., dimensional inspection]              | [LEVEL]    |
| 2 | [QC_MACHINE_2]                   | [Q] | [SPEC]           | [QC function — e.g., functional test]                     | [LEVEL]    |
| 3 | [QC_MACHINE_3]                   | [Q] | [SPEC]           | [QC function — e.g., safety/hipot test]                   | [LEVEL]    |
| 4 | [QC_MACHINE_4]                   | [Q] | [SPEC]           | [QC function — e.g., visual inspection station]           | [LEVEL]    |
| 5 | [QC_MACHINE_5]                   | [Q] | [SPEC]           | [QC function — e.g., environmental stress screening]      | [LEVEL]    |
| 6 | 3D Coordinate Measuring Machine  | [Q] | [SPEC]           | Precision dimensional verification of mechanical parts    | A          |
| 7 | Digital Microscope Inspection    | [Q] | [SPEC]           | PCB solder joint visual inspection                        | SA         |
| 8 | X-Ray Inspection System          | [Q] | [SPEC]           | BGA solder joint and hidden component inspection          | A/AI       |

---

## 4. Material Handling Equipment

### 4.1 Autonomous Mobile Robots (AMRs)

| # | Equipment          | Qty | Model / Type              | Purpose                                              | Auto Level |
|---|-------------------|-----|---------------------------|------------------------------------------------------|------------|
| 1 | AMR — Transport   | [Q] | [MODEL] — [PAYLOAD_KG] kg | Transports WIP between production stations           | AI/FA      |
| 2 | AMR — Goods-to-Person | [Q] | [MODEL]               | Delivers components from stores to assembly stations | AI/FA      |
| 3 | AMR — Finished Goods | [Q] | [MODEL]                | Transports finished goods to FG warehouse            | AI/FA      |
| 4 | AMR Charging Dock | [N] | [MODEL]                   | Autonomous charging for AMR fleet                    | FA         |

**AMR Fleet Specifications:**

- **Navigation:** LiDAR + Camera SLAM — no floor modifications required
- **Fleet Management:** Coo-Cah AMR Fleet Management Software (integrated with MES)
- **Payload:** [MIN]–[MAX] kg per unit
- **Battery:** LFP, [KWH] kWh per unit, 8h+ operational time per charge
- **Communication:** Wi-Fi 6 (802.11ax), 5G-ready
- **Safety:** ISO 3691-4 compliant, emergency stop, person detection

### 4.2 Conveyor Systems

| # | Equipment               | Qty | Spec                         | Purpose                                    | Auto Level |
|---|-------------------------|-----|------------------------------|--------------------------------------------|------------|
| 1 | Belt Conveyor — Main Assembly | [Q] | Width: [W]mm, Speed: variable | Main production flow between stations      | A          |
| 2 | Roller Conveyor — Stores      | [Q] | Length: [L]m, Manual         | Raw material staging in stores area        | M          |
| 3 | Overhead Chain Conveyor  | [Q] | [SPEC]                       | Heavy sub-assembly transport               | SA         |
| 4 | ESD-Safe Conveyor        | [Q] | ESD-rated belt, [SPEC]       | PCB/electronics transport                  | A          |

### 4.3 Lifting & Storage Equipment

| # | Equipment               | Qty | Spec           | Purpose                                    | Auto Level |
|---|-------------------------|-----|----------------|--------------------------------------------|------------|
| 1 | Electric Forklift       | [Q] | [CAPACITY] t   | Loading/unloading containers at dock       | M/SA       |
| 2 | Pallet Jack (Electric)  | [Q] | [CAPACITY] kg  | Internal pallet movement                   | M          |
| 3 | Vertical Storage Lift   | [Q] | [SPEC]         | High-density small parts storage           | A          |
| 4 | Racking System (Selective) | [N] bays | [SPEC]  | Bulk material and FG storage               | M          |

---

## 5. Packaging Equipment

| # | Equipment                    | Qty | Spec / Model     | Purpose                                                | Auto Level |
|---|------------------------------|-----|------------------|--------------------------------------------------------|------------|
| 1 | Automatic Carton Erector     | [Q] | [SPEC]           | Forms and folds cartons at high speed                  | A          |
| 2 | Product Insert / Fill Station| [Q] | [SPEC]           | Places product, accessories, manuals into carton       | SA         |
| 3 | Automatic Carton Sealer      | [Q] | [SPEC]           | Top and bottom carton taping/gluing                    | A          |
| 4 | Shrink Wrap Machine          | [Q] | [SPEC]           | Overwraps grouped cartons for pallet protection        | SA         |
| 5 | Pallet Wrapper (Stretch Film)| [Q] | [SPEC]           | Wraps finished pallet loads for shipping               | A          |
| 6 | Label Printer & Applicator   | [Q] | [SPEC]           | Prints and applies product, shipping, batch labels     | A/AI       |
| 7 | Checkweigher                 | [Q] | [SPEC]           | Verifies packed weight; rejects under/over-weight      | FA/AI      |
| 8 | Barcode / QR Scanner (inline)| [Q] | [SPEC]           | Scans serial/batch codes for MES traceability          | FA         |

---

## 6. Energy & Utilities Equipment

| # | Equipment                         | Qty | Spec / Model                    | Purpose                                         | Auto Level |
|---|-----------------------------------|-----|---------------------------------|-------------------------------------------------|------------|
| 1 | Solar PV Array                    | —   | [KWP] kWp, Monocrystalline      | Primary renewable energy generation             | AI/FA      |
| 2 | LFP Battery Energy Storage (BESS) | —   | [KWH] kWh, [VOLTAGE]V DC Bus    | Energy storage and overnight/backup power       | AI/FA      |
| 3 | Grid-Tied Inverter / Hybrid       | [Q] | [SPEC], [KVA] kVA               | DC-AC inversion, grid management                | FA         |
| 4 | Automatic Transfer Switch (ATS)   | [Q] | [SPEC]                          | Seamless grid/solar/BESS switching              | FA         |
| 5 | Diesel Generator (Backup)         | [Q] | [KVA] kVA standby               | Emergency backup — grid and solar failure       | SA         |
| 6 | Air Compressor                    | [Q] | [BAR] bar, [CFM] CFM            | Pneumatic tool supply, spray equipment          | A          |
| 7 | Chiller / HVAC Central Unit       | [Q] | [KW] kW cooling                 | Factory climate control                         | A/AI       |
| 8 | Water Treatment System            | [Q] | [SPEC]                          | Process water treatment (if applicable)         | SA         |

---

## 7. MES / IT Equipment

| # | Equipment                        | Qty | Spec / Model         | Purpose                                                  | Auto Level |
|---|----------------------------------|-----|----------------------|----------------------------------------------------------|------------|
| 1 | MES Workstation (Floor)          | [Q] | [SPEC]               | Operator production entry, job tracking                  | M/AI       |
| 2 | Industrial Panel PC (Line)       | [Q] | [SPEC] — IP65 rated  | Mounted at each station for real-time MES display        | SA/AI      |
| 3 | Shop Floor Barcode Scanners      | [Q] | [SPEC]               | WIP scanning, component traceability                     | SA         |
| 4 | Machine Interface Gateway (MIG)  | [Q] | [SPEC]               | OPC-UA/MQTT bridge between machines and MES              | FA/AI      |
| 5 | Industrial Wi-Fi Access Points   | [Q] | Wi-Fi 6, IP67        | Wireless connectivity for AMRs and mobile devices        | FA         |
| 6 | Network Switch — Industrial      | [Q] | [SPEC] — managed     | Factory LAN backbone                                     | FA         |
| 7 | Edge Computing Node              | [Q] | [SPEC]               | Local AI inference, MES edge processing                  | AI/FA      |
| 8 | CCTV System (Factory Floor)      | [Q] | 4MP IP cameras       | Safety monitoring, quality audit footage                 | AI         |
| 9 | UPS (IT Room)                    | [Q] | [KVA] kVA            | Power backup for MES servers and network equipment       | FA         |

---

## 8. Equipment Maintenance Schedule Summary

| Maintenance Type       | Frequency        | Responsible Team              | MES Trigger        |
|------------------------|------------------|-------------------------------|--------------------|
| Preventive Maintenance | Per OEM schedule | Maintenance Team + MES PM     | Automated work order |
| Predictive Maintenance | Continuous       | AI Platform alert             | AI vibration/temp alert |
| Lubrication            | Weekly           | Maintenance Technician        | PM schedule        |
| Calibration (QC Tools) | Monthly / Annual | QA Lab + Certified 3rd party  | Calibration register |
| Deep Clean             | Monthly          | Production + EHS              | Planned shutdown   |
| Annual Overhaul        | Yearly           | OEM-authorised service team   | Annual shutdown    |

---

## 9. Spare Parts & Consumables Register

| # | Item                         | Equipment                  | Min Stock | Reorder Point | Supplier Type  |
|---|------------------------------|----------------------------|-----------|---------------|----------------|
| 1 | [SPARE_PART_1]               | [MACHINE]                  | [QTY]     | [QTY]         | OEM / Local    |
| 2 | [SPARE_PART_2]               | [MACHINE]                  | [QTY]     | [QTY]         | OEM / Import   |
| 3 | Solder Paste (500g jar)      | SMT Screen Printer         | 20 jars   | 10 jars       | Import         |
| 4 | Soldering Iron Tips          | Rework / Manual Solder     | 50 pcs    | 20 pcs        | Local / Import |
| 5 | ESD Wrist Straps             | All Assembly Stations      | 100 pcs   | 40 pcs        | Local          |
| 6 | Conveyor Belt (per m)        | Belt Conveyors             | 20 m      | 10 m          | Local / Import |
| 7 | AMR Battery Module           | AMR Fleet                  | 2 units   | 1 unit        | OEM            |
| 8 | HEPA Filters (if cleanroom)  | HVAC/Cleanroom             | 6 units   | 3 units       | Import         |

---

## 10. Equipment Procurement Notes

- All SMT equipment should be sourced from Tier-1 suppliers with established African service support (preferred: Juki, DEK/Cohu, Heller, Koh Young).
- Localisation target: by Phase 2, minimum 30% of MRO (maintenance, repair, operations) supplies should be sourced within Nigeria/Africa.
- All equipment with automation level FA or AI must be integrated with the Coo-Cah MES via OPC-UA or MQTT protocol before production go-live.
- AMR procurement to be coordinated with Coo-Cah Technology Division for fleet management software licensing.

---

*For energy consumption data per machine, refer to [`energy-profile.md`](./energy-profile.md).*
*For digital twin asset registration, refer to [`digital-twin.md`](./digital-twin.md).*
