# Smart Home & Office Electronics Factory — Machinery & Equipment Register

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Smart Home & Office Electronics Factory | **Location:** Agbara Industrial Estate, Lagos State, Nigeria | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Factory Engineering Team

---

## 1. Introduction

This document is the complete equipment register for the Coo-Cah Smart Home & Office Electronics Factory. The factory produces smart TVs (32"–65"), smart speakers, home automation hubs, smart projectors, smart displays, Wi-Fi routers, mesh systems, and laptop computers. The manufacturing process combines two SMT PCB assembly lines with dedicated product assembly lines for each product family.

**Automation Level Legend:**

| Code | Level | Description |
|------|-------|-------------|
| M | Manual | Operated entirely by human |
| SA | Semi-Automated | Machine performs primary action; human loads/monitors |
| A | Automated | Machine operates autonomously within its cycle |
| FA | Fully Automated | End-to-end autonomous; integrated with MES; self-alarming |
| AI | AI-Augmented | Data processed by Coo-Cah AI Platform for optimisation/prediction |

---

## 2. SMT PCB Assembly Lines

### 2.1 SMT Line 1 — TV Mainboards & Home Automation Hubs

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | Solder Paste Screen Printer | 1 | DEK Horizon 03iX | Deposits solder paste — large-format TV mainboards (up to 400×300mm) | FA |
| 2 | Pick-and-Place Machine (high speed) | 1 | JUKI FX-3R | Small SMT components (0402, 0201, QFN, BGA) — 75,000 cph | FA/AI |
| 3 | Pick-and-Place Machine (flexible) | 1 | JUKI RX-7 | Large/odd-form: HDMI connectors, USB ports, large ICs, shielding cans | FA |
| 4 | Reflow Oven (12-zone) | 1 | Heller 1913 MKIII | Lead-free reflow soldering — large board format | FA |
| 5 | Solder Paste Inspection (SPI) | 1 | Koh Young KY8030-3 | Pre-placement paste inspection on TV boards | FA/AI |
| 6 | Automated Optical Inspection (AOI) | 1 | Koh Young Zenith II | Post-reflow AOI for TV mainboards and hub PCBAs | FA/AI |
| 7 | X-Ray Inspection System | 1 | Saki BF-X Series | BGA and hidden solder joint inspection (SoC packages) | A/AI |
| 8 | PCB Depanelling Router | 1 | LPKF ProtoMat | Separates individual PCBs from production panel | A |

### 2.2 SMT Line 2 — Router, Smart Display & Laptop Boards

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | Solder Paste Screen Printer | 1 | Yamaha YSP | Deposits solder paste — smaller high-density router and laptop boards | FA |
| 2 | Pick-and-Place Machine | 1 | Yamaha YSM40R | High-density fine-pitch placement for Wi-Fi SoCs, DDR memory, eMMC | FA/AI |
| 3 | Pick-and-Place Machine (flexible) | 1 | Yamaha YSM20R | Connectors, large caps, shielding, antennas | FA |
| 4 | Reflow Oven (10-zone) | 1 | Heller 1809 MkIII | Lead-free reflow for medium-format boards | FA |
| 5 | AOI System | 1 | Koh Young Zenith | Post-reflow AOI for router, display, laptop boards | FA/AI |
| 6 | Wave Soldering Machine | 1 | Electrovert Vectra VS | Through-hole components on selected boards | SA |
| 7 | Selective Soldering Machine | 1 | Ersa VERSAFLOW | Selective soldering for sensitive mixed-technology boards | A |

---

## 3. Smart TV Assembly Lines

### 3.1 TV Assembly Line 1 & 2 (Parallel Lines)

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | LED/QLED Panel Handling Gantry | 2 | Custom vacuum lifter | Handles large display panels (up to 65") without damage | SA |
| 2 | Screen-to-Chassis Assembly Station | 6 | ESD bench + torque driver | Mounts LED/QLED panel into TV chassis | SA |
| 3 | Mainboard & T-Con Board Installation | 4 | Manual + torque tool | Inserts and cables TV mainboard, T-Con, power supply | SA |
| 4 | Cable Management Station | 4 | Manual workbench | Routes and ties all internal cables | M |
| 5 | Bezel Assembly & Snap-Fit Press | 4 | Pneumatic press | Assembles TV bezel and back cover | SA |
| 6 | TV Functional Test & Burn-In | 6 | Coo-Cah CCT test fixture, 4K test signal | Powers on TV, tests all HDMI inputs, audio, smart OS boot | SA/AI |
| 7 | Display Quality Inspection (AI Vision) | 2 | Cognex IS-8405M + 4K reference | AI-driven pixel defect, uniformity, colour accuracy check | FA/AI |
| 8 | Speaker Sound Test Station | 4 | KLIPPEL dB test | Tests TV audio output frequency response | SA |
| 9 | Smart OS & App Verification Station | 4 | Wi-Fi 6 test AP + Android TV validator | Validates Google Play certification, Chromecast, app load | SA/AI |
| 10 | Stand Assembly & Packaging Station | 6 | Manual bench + jig | Attaches TV stand, bags accessories, cartons | M |

---

## 4. Smart Speaker Assembly Line

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | Speaker Driver Press Station | 3 | Pneumatic driver press jig | Presses speaker driver cone into housing | SA |
| 2 | Amplifier PCB & Crossover Assembly | 3 | Manual + ESD bench | Installs amp board, passive crossover, power supply | SA |
| 3 | Housing Assembly Station | 3 | Manual + torque | Assembles fabric-covered housing halves with driver | M |
| 4 | Speaker Acoustic Test | 3 | KLIPPEL Audio Analyser | Tests frequency response, THD, polar pattern | SA/AI |
| 5 | Wi-Fi / BT Pairing Test | 3 | Test AP + BT analyser | Tests Wi-Fi provisioning, BT pairing, Coo-Cah AI assistant wake | SA |

---

## 5. Laptop Assembly Line

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | Motherboard & RAM Installation | 6 | Manual + ESD, anti-static bench | Installs CPU motherboard, RAM DIMMs, SSD into chassis | M |
| 2 | Display Hinge & Screen Assembly | 4 | Manual + torque driver | Attaches LCD panel, hinge, webcam, and lid bezel | SA |
| 3 | Keyboard & Trackpad Installation | 4 | Manual + clip tool | Snaps in keyboard, connects trackpad ribbon cable | M |
| 4 | Battery Connection & Sealing | 4 | Manual + ESD | Connects Li-ion battery pack, routes cables, closes chassis | SA |
| 5 | BIOS Initialisation Station | 4 | AMI flash programmer | Programs BIOS, validates boot, sets serial number | SA/AI |
| 6 | OS Imaging Station | 4 | PXE network boot server | Images Windows 11 / Ubuntu over gigabit network | FA |
| 7 | Laptop Functional Test Station | 6 | Coo-Cah CCL test script | Tests all ports (USB-C, USB-A, HDMI), Wi-Fi, BT, display, keyboard | SA/AI |
| 8 | Battery Life Test Bench | 2 | Automated discharge cycle | Runs battery life calibration and certifies minimum hours | A |

---

## 6. Router, Hub & Smart Display Assembly

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | Router PCB + Antenna Assembly | 4 | Manual + torque | Installs PCB into housing, attaches internal antennas | SA |
| 2 | Router Functional Test Station | 4 | Wi-Fi 6 tester (Ixia / Spirent) | Tests throughput, MIMO, WPA3, mesh provisioning | SA/AI |
| 3 | Home Automation Hub Assembly | 4 | Manual + ESD bench | Installs hub PCB (Zigbee + Wi-Fi + BLE) into PoE enclosure | SA |
| 4 | Hub Commissioning Test | 3 | CCX-HAH test fixture + Zigbee sniffer | Tests Zigbee pairing, BLE, Wi-Fi, edge AI boot | SA/AI |
| 5 | Smart Display Assembly Station | 4 | Manual + torque | Mounts touchscreen, hub PCB, PoE module | SA |
| 6 | Smart Display Functional Test | 3 | CCX-SD test fixture | Tests touch, display, Wi-Fi, Zigbee, app load | SA/AI |

---

## 7. Quality Control Equipment

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | 4K AI Vision System (TV QC) | 2 | Cognex In-Sight 9000 | Automated cosmetic inspection of TV housing and bezel | FA/AI |
| 2 | Display Calibration Station | 2 | Klein Instruments K-10A | Measures colour gamut, brightness, colour temperature per factory standard | SA/AI |
| 3 | Wi-Fi 6 RF Test Chamber | 2 | NTS-MIMO RF shielded box | NCC type approval — radiated emissions and RF performance | SA |
| 4 | EMC Pre-Compliance Bench | 1 | Near-field probe + spectrum analyser | Pre-compliance EMI scan for all wireless products | SA |
| 5 | Environmental Stress Screen Chamber | 1 | -10°C to +55°C cycling | ESS on TVs, routers, hubs (2-hour ramp/soak) | A |
| 6 | Drop Test Rig | 1 | Per IEC 60068-2-31 | Drop test for routers, hubs, speakers | M |
| 7 | Android CDD Compliance Station | 2 | GMS certification test suite | Validates Android TV CDD compliance for Google certification | SA/AI |
| 8 | Metrology Station | 1 | Mitutoyo CMM | Dimensional inspection of TV stands, housing tooling | A |

---

## 8. Material Handling Equipment

### 8.1 AMR Fleet

| # | Equipment | Qty | Model | Purpose | Auto Level |
|---|-----------|-----|-------|---------|------------|
| 1 | AMR — WIP Transport | 8 | MiR250 (250 kg payload) | Transports PCBAs, TV panels, sub-assemblies between stations | AI/FA |
| 2 | AMR — Stores to Line | 4 | MiR250 | Delivers component kits and TV panels from stores to lines | AI/FA |
| 3 | AMR Charging Docks | 6 | MiR Charge 48V | Autonomous charging docks for AMR fleet | FA |

**AMR Fleet Specifications:**
- Navigation: LiDAR + camera SLAM — no floor markings
- Payload: 250 kg per unit (suitable for TV panel transport)
- Battery: LFP, 10h+ operational time per charge
- Fleet Management: Coo-Cah AMR FMS (MES-integrated)
- Safety: ISO 3691-4 compliant

### 8.2 Conveyor & Storage

| # | Equipment | Qty | Spec | Purpose | Auto Level |
|---|-----------|-----|------|---------|------------|
| 1 | ESD-Safe Belt Conveyor (SMT) | 6 | 600mm wide, variable speed | PCB transport between SMT stations | A |
| 2 | Roller Conveyor (TV Assembly) | 4 | 1,200mm wide, gravity/powered | TV chassis flow between assembly stations | M/SA |
| 3 | Vertical Storage Lift (VLM) | 3 | Hänel Lean-Lift, 5m height | High-density component storage (SMT reels, accessories) | A/AI |
| 4 | Pallet Racking — Component Stores | 80 bays | Dexion, selective | Bulk component and raw material storage | M |
| 5 | Electric Reach Truck | 2 | Still FM-X 12 | High-bay racking access for pallet loads | SA |

---

## 9. Packaging Equipment

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | Automatic Carton Erector | 2 | Kliklok Eclipse | Forms cartons for TVs, laptops, speakers, routers | A |
| 2 | TV Accessory Insert Station | 4 | Manual bench | Inserts remote, stand hardware, manuals into TV carton | M |
| 3 | Automatic Carton Sealer | 2 | 3M-Matic 800af | Top/bottom taping | A |
| 4 | Pallet Wrapper | 2 | Robopac Rotoplat 50 | Stretch-wraps pallet loads | A |
| 5 | Label Printer & Applicator | 4 | Zebra ZT620 | Prints and applies product, serial number, carton labels | A/AI |
| 6 | Checkweigher | 2 | Mettler Toledo C33 | Verifies packed weight for all product lines | FA/AI |
| 7 | Barcode / QR Inline Scanner | 6 | Cognex DataMan 475 | Scans carton codes for MES serialisation and traceability | FA |

---

## 10. Energy & Utilities Equipment

| # | Equipment | Qty | Spec / Model | Purpose | Auto Level |
|---|-----------|-----|-------------|---------|------------|
| 1 | Solar PV Array | — | 750 kWp, Monocrystalline PERC | Primary renewable energy generation | AI/FA |
| 2 | LFP BESS | — | 800 kWh, containerised | Energy storage and overnight/backup power | AI/FA |
| 3 | Hybrid Inverter | 8 | Sungrow SH100T, 100 kW each | DC-AC inversion, grid and BESS management | FA |
| 4 | Automatic Transfer Switch | 3 | Schneider Electric Masterpact | Grid/solar/BESS/generator switching | FA |
| 5 | Diesel Generator | 1 | Perkins 630 kVA standby | Emergency backup | SA |
| 6 | Air Compressor | 3 | Atlas Copco GA37, 8 bar | Pneumatic tools, cleaning guns | A |
| 7 | HVAC Central Unit | 6 | Daikin VRV IV, 30 kW cooling ea. | Factory and office climate control | A/AI |
| 8 | UPS (IT / Burn-in Room) | 2 | APC Smart-UPS RT 10 kVA | Power backup for MES servers, burn-in test equipment | FA |

---

## 11. MES / IT Equipment

| # | Equipment | Qty | Spec | Purpose | Auto Level |
|---|-----------|-----|------|---------|------------|
| 1 | Industrial Panel PC (Line) | 18 | IP65, 15" touchscreen | MES operator interface at each production station | SA/AI |
| 2 | MES Workstation (QA Lab) | 6 | Desktop PC, 24" monitor | QA records, test result entry, calibration logs | M/AI |
| 3 | Shop Floor Barcode Scanners | 30 | Zebra DS2278 | WIP scanning, serial number and batch traceability | SA |
| 4 | Machine Interface Gateway | 10 | Moxa MGate MB3000 | OPC-UA/MQTT bridge — machines to MES | FA/AI |
| 5 | Industrial Wi-Fi Access Points | 12 | Cisco Catalyst IW6300, Wi-Fi 6 | AMR and mobile device wireless | FA |
| 6 | Edge Computing Node | 3 | Dell PowerEdge XR12 | Local AI inference for vision QC, TV test analytics | AI/FA |
| 7 | Android TV Certification Server | 1 | Google-spec GMS validation server | Hosts Android TV CDD certification test suite | FA |
| 8 | OS Imaging Server | 2 | Dell PowerEdge R550 | PXE image deployment for laptops and smart devices | FA |

---

## 12. Equipment Procurement Notes

- TV panel handling requires anti-static vacuum lifters and ESD-rated AMR top modules; coordinate with MiR for custom TV panel fixtures.
- Google Mobile Services (GMS) certification for Android TV requires Google-approved test environment — Google Partner liaison required before production.
- All SMT equipment sourced from Tier-1 suppliers with African service support (Juki/Yamaha, DEK/Cohu, Heller, Koh Young).
- All equipment with automation level FA or AI must integrate with Coo-Cah MES via OPC-UA or MQTT before production go-live.

---

*For energy consumption data per machine, refer to [`energy-profile.md`](./energy-profile.md).*
*For digital twin asset registration, refer to [`digital-twin.md`](./digital-twin.md).*
