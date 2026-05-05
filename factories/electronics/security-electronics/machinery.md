# Security Electronics Factory — Machinery & Equipment Register

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Security Electronics Factory | **Location:** Ikorodu Industrial Estate, Lagos State, Nigeria | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Factory Engineering Team

---

## 1. Introduction

This document is the complete equipment register for the Coo-Cah Security Electronics Factory. The factory produces IP security cameras (bullet, dome, PTZ, ANPR), NVRs, DVRs, access control systems, alarm panels, and video intercom systems. The manufacturing process combines one SMT PCB assembly line with multiple dedicated product assembly and test lines.

**Automation Level Legend:**

| Code | Level | Description |
|------|-------|-------------|
| M | Manual | Operated entirely by human |
| SA | Semi-Automated | Machine performs primary action; human loads/monitors |
| A | Automated | Machine operates autonomously within its cycle |
| FA | Fully Automated | End-to-end autonomous; integrated with MES; self-alarming |
| AI | AI-Augmented | Data processed by Coo-Cah AI Platform for optimisation/prediction |

---

## 2. SMT PCB Assembly Line

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | Solder Paste Screen Printer | 1 | DEK Horizon 03iX | Deposits solder paste onto PCB pads for all security product boards | FA |
| 2 | Pick-and-Place Machine (high speed) | 1 | JUKI FX-3R | Places small SMT components (0402, 0603, ICs) at up to 75,000 cph | FA/AI |
| 3 | Pick-and-Place Machine (flexible) | 1 | JUKI RX-7 | Places larger/odd-form SMT components; connectors, large ICs | FA |
| 4 | Reflow Oven (10-zone) | 1 | Heller 1913 MKIII | Lead-free reflow soldering at optimised temperature profile | FA |
| 5 | Automated Optical Inspection (AOI) | 1 | Koh Young Zenith II | Post-reflow AOI: detects solder bridges, tombstoning, missing parts | FA/AI |
| 6 | Wave Soldering Machine | 1 | Electrovert Vectra VS | Through-hole components on NVR/DVR boards | SA |
| 7 | In-Circuit Test (ICT) System | 1 | Keysight i3070 | PCB electrical connectivity and component value test | SA |
| 8 | PCB Depanelling Router | 1 | LPKF ProtoMat | Separates individual PCBs from production panel | A |
| 9 | SMT Solder Paste Inspection (SPI) | 1 | Koh Young KY8030-3 | Pre-placement solder paste volume/height inspection | FA/AI |

---

## 3. Camera Housing Assembly Lines

### 3.1 Bullet & Dome Camera Assembly (Line 1)

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | Lens Mount & Focus Station | 4 | Manual jig + motorised focus adj. | Mounts and focuses CMOS sensor + lens assembly | SA |
| 2 | IR LED Assembly Station | 4 | Manual workbench, UV cure | Positions and bonds IR LED array onto camera PCB | SA |
| 3 | Housing Assembly Press | 2 | Pneumatic press jig | Snap-fits bullet/dome housing halves | SA |
| 4 | IP Weatherproof Seal Station | 4 | Manual + torque tool | Applies O-ring seal; torques cover screws to spec | M |
| 5 | Camera Functional Test Station | 6 | Coo-Cah CCX test fixture + PC | Boots camera, tests video output, IR activation, PoE | SA |
| 6 | Optical Resolution Test Chart | 3 | ISO 12233 chart, 4K reference monitor | Validates camera resolution, focus, sharpness | SA/AI |

### 3.2 PTZ & ANPR Camera Assembly (Line 2)

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | PTZ Motor & Gear Assembly Bench | 3 | Manual + torque tools | Assembles pan/tilt/zoom motor mechanism | SA |
| 2 | Zoom Lens Calibration Station | 2 | Motorised optical bench | Calibrates 30× optical zoom; sets backfocus | SA |
| 3 | ANPR IR Array Assembly | 2 | Manual workbench + UV cure | Mounts long-range IR LED array for ANPR | M |
| 4 | Weatherproof Enclosure Assembly | 3 | Manual + air torque tool | Assembles IP66/IP67 rated PTZ housing | SA |
| 5 | PTZ Function Test Station | 3 | CCX-PTZ test fixture | Tests pan, tilt, zoom, auto-focus, IR | SA |

---

## 4. NVR / DVR Assembly Line

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | HDD Installation Station | 4 | Manual + ESD bench | Installs and cable-connects 2TB/4TB HDDs into NVR chassis | M |
| 2 | Motherboard Assembly Station | 4 | Manual + torque driver | Mounts NVR/DVR main board, RAM, power supply | SA |
| 3 | Chassis Assembly & Screwdriving | 3 | Manual + electric torque | Assembles full NVR/DVR chassis with covers | SA |
| 4 | NVR Functional Test Station | 4 | Network test bench + PoE switch | Boots NVR, tests all PoE ports, HDD, HDMI, ONVIF | SA/AI |
| 5 | DVR Functional Test Station | 3 | Network + coax test bench | Boots DVR, tests all analogue + IP input channels | SA |

---

## 5. Access Control & Alarm Panel Assembly

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | Access Controller PCB Assembly | 3 | Manual workbench + ICT | Assembles and tests 2-door/4-door access control boards | SA |
| 2 | Card Reader Assembly Station | 4 | Manual + torque | Assembles RFID/biometric card reader units | SA |
| 3 | Alarm Panel Assembly Station | 4 | Manual workbench | Assembles 8-zone/32-zone alarm control panels | M |
| 4 | GSM Module Integration Station | 2 | Manual + SIM tool | Inserts SIM, programs APN for GSM alarm reporting | SA |
| 5 | Access Control Functional Test | 3 | CCX test fixture + RFID tester | Tests card read, relay output, network commissioning | SA |
| 6 | Alarm Panel Functional Test | 3 | CCX test fixture + zone simulator | Tests zone inputs, siren output, GSM dialler | SA |

---

## 6. Video Intercom Assembly Line

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | Display Module Bonding Station | 2 | OCA bonding jig + UV | Bonds 7" touchscreen to display frame | SA |
| 2 | Intercom PCB Assembly | 3 | Manual workbench | Assembles intercom main board into housing | SA |
| 3 | Intercom Functional Test | 3 | CCX intercom test bench | Tests video, audio, door-release, app connectivity | SA |

---

## 7. Quality Control Equipment

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | 4K AI Vision Inspection System | 2 | Cognex In-Sight 9000 | Automated cosmetic inspection of camera housings | FA/AI |
| 2 | IP Rating Test Chamber (IP66/67) | 2 | Custom dust/water chamber | Verifies IP ingress protection rating | A |
| 3 | Drop Test Rig | 1 | Per IEC 60068-2-31 | 1.5m drop test on all portable camera models | M |
| 4 | Temperature Cycling Chamber | 1 | -20°C to +70°C, 2 chambers | Environmental stress screening (ESS) | A |
| 5 | EMC Pre-Compliance Test Bench | 1 | Near-field probe + spectrum analyser | Pre-compliance EMI scan before NCC submission | SA |
| 6 | Network Performance Analyser | 2 | Ixia / Spirent | Validates NVR network throughput and latency | SA/AI |
| 7 | Metrology Station (dimensional) | 1 | Mitutoyo CMM | Dimensional verification of custom housing tooling | A |

---

## 8. Material Handling Equipment

### 8.1 AMR Fleet

| # | Equipment | Qty | Model | Purpose | Auto Level |
|---|-----------|-----|-------|---------|------------|
| 1 | AMR — WIP Transport | 6 | MiR100 (100 kg payload) | Transports PCBs, sub-assemblies, and WIP between stations | AI/FA |
| 2 | AMR — Stores to Line | 2 | MiR100 | Delivers component kits from stores to assembly stations | AI/FA |
| 3 | AMR Charging Docks | 4 | MiR Charge 48V | Autonomous charging docks for AMR fleet | FA |

**AMR Fleet Specifications:**
- Navigation: LiDAR + camera SLAM — no floor markings required
- Fleet Management: Coo-Cah AMR Fleet Management Software (MES-integrated)
- Battery: LFP, 8h+ operational time per charge
- Communication: Wi-Fi 6 (802.11ax)
- Safety: ISO 3691-4 compliant, emergency stop, pedestrian detection

### 8.2 Conveyor & Storage

| # | Equipment | Qty | Spec | Purpose | Auto Level |
|---|-----------|-----|------|---------|------------|
| 1 | ESD-Safe Belt Conveyor | 4 | 600mm wide, variable speed | PCB and PCBA transport between SMT stations | A |
| 2 | Vertical Storage Lift (VLM) | 2 | Hänel Lean-Lift, 4m height | High-density SMT component storage + retrieval | A/AI |
| 3 | Pallet Racking — Component Stores | 40 bays | Dexion, selective, 3-deep | Bulk component and raw material storage | M |
| 4 | Electric Pallet Jack | 2 | Crown WP3000 | Internal pallet movement | SA |

---

## 9. Packaging Equipment

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | Automatic Carton Erector | 1 | Kliklok Eclipse | Forms cartons for cameras, NVRs, DVRs | A |
| 2 | Product Fill Station | 4 | Manual workbench | Inserts product, accessories, warranty card into carton | M |
| 3 | Automatic Carton Sealer | 1 | 3M-Matic 800af | Top/bottom carton taping | A |
| 4 | Pallet Wrapper | 1 | Robopac Rotoplat 50 | Stretch-wraps pallet loads for dispatch | A |
| 5 | Label Printer & Applicator | 2 | Zebra ZT620 + applicator | Prints and applies product labels, serial numbers, barcodes | A/AI |
| 6 | Checkweigher | 1 | Mettler Toledo C33 | Verifies packed weight for all products | FA/AI |

---

## 10. Energy & Utilities Equipment

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | Solar PV Array | — | 500 kWp, Monocrystalline PERC | Primary renewable energy generation | AI/FA |
| 2 | LFP BESS | — | 550 kWh, LFP chemistry | Energy storage and overnight/backup power | AI/FA |
| 3 | Hybrid Inverter | 5 | Sungrow SH100T, 100 kW each | DC-AC inversion, grid and BESS management | FA |
| 4 | Automatic Transfer Switch | 2 | Schneider Electric | Grid/solar/BESS/generator switching | FA |
| 5 | Diesel Generator | 1 | Perkins 400 kVA standby | Emergency backup | SA |
| 6 | Air Compressor | 2 | Atlas Copco GA30, 8 bar | Pneumatic tools, cleaning guns | A |
| 7 | HVAC Central Unit | 4 | Daikin VRV IV, 20 kW cooling ea. | Factory and office climate control | A/AI |

---

## 11. MES / IT Equipment

| # | Equipment | Qty | Spec | Purpose | Auto Level |
|---|-----------|-----|------|---------|------------|
| 1 | Industrial Panel PC (Line) | 12 | IP65, 15" touchscreen | MES operator interface at each production station | SA/AI |
| 2 | MES Workstation (QA Lab) | 4 | Desktop PC, 24" monitor | QA inspection records, test result entry | M/AI |
| 3 | Shop Floor Barcode Scanners | 20 | Zebra DS2278 | WIP scanning, serial number traceability | SA |
| 4 | Machine Interface Gateway | 6 | Moxa MGate MB3000 | OPC-UA/MQTT bridge — machines to MES | FA/AI |
| 5 | Industrial Wi-Fi Access Points | 8 | Cisco Catalyst IW6300, Wi-Fi 6 | AMR and mobile device wireless | FA |
| 6 | Edge Computing Node | 2 | Dell PowerEdge XR12 | Local AI inference, MES edge processing | AI/FA |
| 7 | UPS (IT Room) | 1 | APC Smart-UPS 5000 kVA | Power backup for MES servers and network | FA |

---

## 12. Equipment Procurement Notes

- All SMT equipment sourced from Tier-1 suppliers with African service support (Juki, DEK/Cohu, Heller, Koh Young).
- Camera-specific test fixtures (CCX series) are designed and built by the Coo-Cah Technology Division, Rwanda OpCo.
- All equipment with automation level FA or AI must be integrated with the Coo-Cah MES via OPC-UA or MQTT before production go-live.
- AMR procurement coordinated with Coo-Cah Technology Division for fleet management software licensing.

---

*For energy consumption data per machine, refer to [`energy-profile.md`](./energy-profile.md).*
*For digital twin asset registration, refer to [`digital-twin.md`](./digital-twin.md).*
