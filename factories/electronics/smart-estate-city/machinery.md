# Coo-Cah Smart Estate & City Electronics Factory — Machinery & Equipment Register

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Vertical:** Electronics — Smart City & Estate Infrastructure | **Location:** Lekki Free Trade Zone (LFTZ), Lagos State, Nigeria | **Phase:** Phase 1
> **Document Version:** 1.0 | **Status:** In Development

---

## 1. Equipment Summary

| Category                             | No. of Items | Total Units (Installed) |
|--------------------------------------|--------------|-------------------------|
| SMT PCB Assembly Line Equipment      | 14           | 22                      |
| Smart Meter Assembly & Test          | 9            | 28                      |
| Smart Meter Calibration Benches      | 4            | 8                       |
| Smart Estate Hub Assembly            | 4            | 9                       |
| Smart Pole Fabrication & Assembly    | 8            | 17                      |
| Traffic Controller / ESN / LoRa Line | 5            | 10                      |
| Surface Finishing & Protection       | 5            | 6                       |
| Material Handling (AMR & MHE)        | 6            | 18                      |
| Quality, Test & Calibration Lab      | 8            | 16                      |
| Energy & Utilities                   | 7            | 10                      |
| IT, MES & Control Infrastructure     | 5            | 12                      |

**Automation Level Codes:**

| Code  | Meaning                                        |
|-------|------------------------------------------------|
| M     | Manual                                         |
| SA    | Semi-Automated (operator-assisted)             |
| A     | Automated (programmatic, minimal intervention) |
| FA    | Fully Automated (unmanned steady-state)        |
| FA/AI | Fully Automated with AI-based adaptive control |

---

## 2. SMT PCB Assembly Lines (Dual Line)

The factory operates two parallel SMT PCB assembly lines (Line 1 and Line 2) feeding all seven product families. Both lines are configured for mixed-size PCB production (65 mm × 65 mm to 350 mm × 250 mm board range) and share a common SPI–pick-and-place–AOI–reflow–post-reflow AOI process flow.

| # | Equipment                                | Qty | Spec / Model                                                       | Purpose                                                                  | Auto Level |
|---|------------------------------------------|-----|--------------------------------------------------------------------|--------------------------------------------------------------------------|------------|
| 1 | Solder Paste Printer (Screen Printer)   | 2   | DEK Horizon 03iX or EKRA X5 (double-stage squeegee, 4-axis vision alignment, underscreen cleaning) | Applies solder paste to PCB pads before component placement | FA |
| 2 | Solder Paste Inspection (SPI) Machine   | 2   | Koh Young KY-3030VP or Saki BF-3Di (3D laser triangulation, full-board scan, 600 mm/s inspection speed) | 100% inspection of solder paste volume/height/area per pad after printing | FA/AI |
| 3 | High-Speed Pick-and-Place — Chipshooter | 2   | JUKI FX-3R (50,000 CPH rated, 20 × 20mm PCB min, 0201 to 55mm component range, 16-nozzle head) | High-speed placement of passive components (0201–0603 resistors, capacitors, LoRa/NB-IoT modules) | FA |
| 4 | Flexible Mounter (Multi-Function)        | 2   | JUKI RS-1 or Fuji NXT3 (2,000 CPH on connectors, BGA, QFP, QFN; 6-head, 24-nozzle; dual XY gantry) | Placement of ICs (CS5480, RL78 MCU, ESP32, SX1276), BGA, large connectors | FA |
| 5 | Reflow Oven — SMT                        | 2   | Heller 1964 MK5 (10-zone, forced-air convection, nitrogen-capable, 400 mm board width, peak 260°C, ±0.5°C profile accuracy) | Reflow soldering of all SMT PCBs; profile managed per product BOM in MES | FA |
| 6 | Post-Reflow Automated Optical Inspection (AOI) | 2 | Mirtec MV-3L OMNI (3D + 2D, 5-camera array, 11 µm resolution, 100% board inspection at line speed) | Detects solder bridges, missing/misaligned components, tombstoning on all PCBs | FA/AI |
| 7 | X-Ray Inspection Machine                | 1   | Viscom S6056 or Yxlon Y.Cheetah EVO (160 kV, oblique angle, BGA and QFN hidden joint inspection) | Inspect solder joint quality under BGA and large QFN ICs (ESP32, SX1302) | A |
| 8 | Selective Soldering Machine             | 1   | Ersa VERSAFLOW 3/45 (mini-wave nozzle, laser flux, 3-axis servo, N₂ blanket) | Through-hole soldering of connectors, fuse clips, power terminals on smart meter PCBs | FA |
| 9 | PCB Conveyor Transfer System            | 2   | Nutek NB-460 (single-level, 460mm max, buffer queuing, barcode scanner integration) | Automated board transfer between SPI → placement → reflow → AOI stations on each line | FA |
| 10 | Nitrogen Generator                       | 1   | Parker domnick hunter MAXIGAS NGS 50 (50 Nm³/h, 99.99% N₂ purity) | Nitrogen blanket atmosphere for lead-free reflow ovens to reduce oxidation | A |
| 11 | SMT Stencil Cleaner                      | 1   | Smart Sonic USS-700 ultrasonic cleaner (batch, 40 kHz, solvent-free) | Stencil cleaning between runs; maintains paste deposit quality | SA |
| 12 | SMT Rework Station                      | 2   | JBC TDDV or PACE TF 1700 (digital IR/convection rework, thermocouple probe, BGA reballing kit) | Manual rework of non-conforming PCBs identified by AOI or ICT | SA |
| 13 | In-Circuit Tester (ICT)                  | 2   | Keysight I3070 Series 3 or Spea 3030 (bed-of-nails, digital/analogue, boundary scan JTAG, 200+ test points) | Electrical opens/shorts, component value, functional parametric test of populated PCBs | A |
| 14 | Fixture Programming Station             | 2   | Custom JTAG ISP workstation (BDM/JTAG, ISP flash programming, 4 DUTs per cycle) | In-circuit firmware flash programming of MCUs (Renesas RL78, STM32, ESP32-S3) | SA |

**Line 1 & Line 2 Key Metrics (Phase 1 Target):**

| Metric                              | Value                  |
|-------------------------------------|------------------------|
| SMT Line Speed (PCB throughput)     | 4,500–6,000 PCBs / day |
| First-Pass Yield (SMT)              | ≥ 98.5%                |
| Board Changeover Time               | ≤ 25 minutes           |
| Maximum PCB Size                    | 350 × 250 mm           |
| Minimum Component Size              | 0201 (0.6 × 0.3 mm)   |
| Solder Paste Standard               | SAC305 lead-free        |
| Traceability                        | PCB barcode to SMT batch in MES |

---

## 3. Smart Meter Assembly & Test Lines

### 3.1 Electricity Smart Meter Assembly (CCE-SM-ELEC)

| # | Equipment                                  | Qty | Spec / Model                                                           | Purpose                                                                      | Auto Level |
|---|--------------------------------------------|-----|------------------------------------------------------------------------|------------------------------------------------------------------------------|------------|
| 1 | Meter Assembly Conveyor Line               | 2   | Bosch Rexroth TS 4 (400 mm belt, variable speed, 12 workstations/side, barcode scanner at each station) | Paced assembly conveyor for single-phase and three-phase meter chassis assembly | SA |
| 2 | Torque-Controlled Screwdriver              | 8   | Atlas Copco QST 30-10 (20–30 Nm torque, auto-reject out-of-range, barcode scan-to-station) | Terminal block screw tightening to DIN torque spec (prevents meter tampering events) | SA |
| 3 | Ultrasonic Plastic Welder                  | 2   | Branson DCX-S (20 kHz, 3.5 kW, servo-driven, ±0.05 mm depth control, meter cover to base welding) | Seals polycarbonate meter cover to base body; critical for IP54 rating        | A |
| 4 | Meter PCB Insertion & Spring-Clip Tool     | 4   | Custom pneumatic fixture (PCB locate pins, spring-clip lock, barcode scanner confirm) | Seated PCB assembly into meter chassis; captures assembly step in MES          | SA |
| 5 | Display Module Soldering & Bonding Station | 2   | Weller WX2 (dual-channel, 150 W tip, LCD ribbon bond fixture)          | Attaches segmented LCD/e-ink display module to meter PCB, connects ribbon cable | SA |
| 6 | SIM Card / NB-IoT Module Insertion Bench   | 4   | Manual ergonomic bench (ESD-safe surface, tool-less SIM tray, module push-lock verify) | Inserts Quectel BC660 NB-IoT module and SIM into meter PCB housing          | M |
| 7 | Meter Sealing & Labelling Press            | 2   | Auto label applicator (Koenig & Bauer Kammann KBA, multi-label head) + tamper seal dispenser | Applies serial number barcode, energy class label, NERC certification mark, tamper-evident seals | A |
| 8 | Single-Phase Meter Takt Bench (Final)      | 4   | Custom ESD-safe assembly bench with pneumatic lid closer and barcode scan-in trigger | Final assembly closure and scan-in to MES; route to calibration              | SA |

### 3.2 Water Smart Meter Assembly (CCE-SM-WATER)

| # | Equipment                                | Qty | Spec / Model                                                        | Purpose                                                                  | Auto Level |
|---|------------------------------------------|-----|---------------------------------------------------------------------|--------------------------------------------------------------------------|------------|
| 1 | Ultrasonic Transducer Press-Fit Machine  | 2   | Custom hydraulic press (2T, ±0.02 mm depth, ±0.1 Nm torque, Viton O-ring seat) | Precision fitting of ultrasonic transducer pairs into brass flow body — critical for metrological accuracy | A |
| 2 | Flow Body Leak Test Machine              | 2   | Ateq F620 pneumatic leak tester (test pressure 16 bar, helium tracer option, pass/fail gate to MES) | Pressure test of assembled water meter flow body pre-electronics integration | A |
| 3 | Smart Lid PCB Assembly Bench             | 4   | ESD-safe benches with fixture (NB-IoT module, display, gasket compression gauge) | Assembly of electronics smart lid (display + NB-IoT + battery) onto meter body | SA |
| 4 | Water Meter Seal & Label Station         | 2   | Auto-label applicator + lead seal wire crimper + DN designation stamp | Applies product label, DN size, accuracy class, supply direction arrow, NERC water code marks | SA |

---

## 4. Smart Meter Calibration Benches

Calibration is a critical and regulated step for both electricity and water meters. All electricity meters are calibrated to IEC 62053-21 (Class 1, single-phase) or IEC 62053-22 (Class 0.5, three-phase) accuracy standards. Water meters are calibrated to ISO 4064 Class B / MID Class C minimum (±2%). Each calibration record is issued a unique certificate ID and written to the MES via the calibration certificate API (`POST /api/v1/calibration/meter`). Records are traceable to national standards via NIS/PTF-maintained calibration chain.

| # | Equipment                                          | Qty | Spec / Model                                                            | Purpose                                                                     | Auto Level |
|---|----------------------------------------------------|-----|-------------------------------------------------------------------------|-----------------------------------------------------------------------------|------------|
| 1 | Smart Electricity Meter Calibration Bench          | 4   | Radian Research RD-33 or Zera MT3000 (Class 0.02 reference standard, 6 UUT simultaneous, 0.5A–120A range, 30V–300V, polyphase, RF/NB-IoT simulation) | IEC 62053-21/22 accuracy verification and correction factor recording; calibration certificate generation | FA |
| 2 | Water Meter Calibration Rig (Gravimetric)          | 2   | Custom gravimetric rig (Mettler Toledo ICS scale 150 kg, DN15–DN40, reference flow range 30 L/h–6,000 L/h, 5-point calibration curve, wet lab, stainless tank) | ISO 4064 multi-point flow accuracy test; generates calibration certificate    | A |
| 3 | Smart Meter Communication Protocol Tester          | 2   | Custom DLMS/COSEM protocol tester (IEC 62056 data exchange test tool, STS token generation, AMI head-end simulator, NB-IoT/GPRS signal simulator) | Tests meter communication protocol compliance; AMR/AMI interoperability       | A |
| 4 | Smart Meter Environmental Burn-In Chamber          | 2   | Weiss Technik WK3-340/70 (–25°C to +70°C, 3 cycles, 20 meters/cycle, thermal shock to IEC 60068-2-14) | Elevated temperature accelerated ageing; catch early-life failures before dispatch | A |

---

## 5. Smart Estate Hub Assembly (CCE-SEH)

| # | Equipment                                  | Qty | Spec / Model                                                        | Purpose                                                                    | Auto Level |
|---|--------------------------------------------|-----|---------------------------------------------------------------------|----------------------------------------------------------------------------|------------|
| 1 | Hub Chassis Assembly Jig                   | 2   | Custom aluminium jig (DIN-rail alignment, PCB stack locating pins, thermal compound application fixture) | Mechanical assembly of Cortex-A55 module board stack into DIN-rail enclosure | SA |
| 2 | Hub Software Flash & Configuration Station | 2   | Custom NUC-based flashing PC (USB 3.0 OTG, JTAG, factory image per SKU, serial activation key provisioning) | Flashes firmware, device certificate, product SKU configuration; generates device serial record in MES | A |
| 3 | Hub Wi-Fi / Zigbee / Z-Wave RF Test Bench  | 3   | Spirent Vertex RF test system or custom CMW100-based fixture (Wi-Fi 802.11ax, Zigbee 3.0, Z-Wave Plus, 2.4 GHz / 5 GHz, RSSI/EVM measurement, shielded box) | RF performance verification; NCC type approval validation tests          | A |
| 4 | Hub Battery Backup Test & Charge Station   | 2   | Custom 48V SLA charge/discharge tester (4 ports, 0–30 A programmable, data logger, >8h capacity verification) | Verifies 8-hour battery backup capacity to product specification; generates test record | A |

---

## 6. Smart Pole Fabrication & Assembly (CCE-SPS)

| # | Equipment                                       | Qty | Spec / Model                                                            | Purpose                                                                     | Auto Level |
|---|-------------------------------------------------|-----|-------------------------------------------------------------------------|-----------------------------------------------------------------------------|------------|
| 1 | CNC Plasma Cutter                               | 1   | Hypertherm Powermax 105 on Messer CNC gantry (3 m × 6 m table, ±0.5 mm accuracy, 20 mm mild steel rated) | Profile cutting of steel pole base plates, arm brackets, junction box panels | A |
| 2 | MIG/MAG Welding Stations                        | 4   | Lincoln Electric Aspect 375 (350A, synergic MIG, GMAW, 3-roll feeder, positioner fixture) | Welding of pole sections, bracket attachments, base flanges to DIN ISO 3834 Class C | SA |
| 3 | Hot-Dip Galvanising Pre-Treatment Line          | 1   | Alkaline degreasing tank (200L), HCl acid pickling tank (500L), flux tank, rinse tanks — 5-station sequential | Chemical pre-treatment of steel pole sections prior to external HDG galvanising (outsourced) | SA |
| 4 | Smart Pole Electronics Integration Assembly Jig | 4   | Custom height-adjustable jig (0.5–4.5 m reach, pole clamp, rotating cradle, tool tray, ESD mat) | Mounts CCTV housing, Wi-Fi AP bracket, sensor pod, LED driver, junction box inside pole arm | SA |
| 5 | DALI-2 LED Driver Test Bench                    | 2   | Custom DALI-2 tester (IEC 62386, DALI controller board, programmable address, dimming ramp test, group test, broadcast test) | Functional test and commissioning configuration of LED driver module per CCE-SPS BOM | A |
| 6 | IP66 Seal & Gasket Press Station                | 2   | Custom pneumatic gasket press (60 bar line, foam-in-place or EPDM strip, dimensional check gauge) | Seals all pole electronics housing enclosures to IP66; compression test after press | SA |
| 7 | Smart Pole End-of-Line Functional Test Bench    | 2   | Custom multi-function test controller (24V / 48V supply, CCTV image streaming, Wi-Fi AP ping, sensor data readout, DALI dimming command) | Final integrated function test of fully assembled smart pole before packaging | SA |
| 8 | Pole Painting / Powder Coat Prep Bench          | 2   | Surface preparation bench (angle grinder, pneumatic scaler, hot-air gun, priming station) | Prepares aluminium pole sections for electrostatic powder coat (outsourced or in-house Phase 2) | M |

---

## 7. Traffic Controller / ESN / LoRaWAN Gateway Assembly Line (CCE-CTC, CCE-ESN, CCE-LORA-GW)

| # | Equipment                                       | Qty | Spec / Model                                                               | Purpose                                                                        | Auto Level |
|---|-------------------------------------------------|-----|----------------------------------------------------------------------------|--------------------------------------------------------------------------------|------------|
| 1 | Traffic Controller Cabinet Assembly Bench       | 2   | ESD-rated stainless steel bench (100 kg capacity, DIN-rail kit, 316 SS panel, cable tray, looming jig) | Assembles traffic controller cabinet: PSU, dual-CPU boards, signal head drivers, 4G/5G modem, terminal blocks | SA |
| 2 | Traffic Controller Integrated Test System       | 1   | Custom signal head simulator (12 V / 230 V signal outputs, pedestrian push button emulator, 4G comms test, NTCIP data exchange tester) | Full system test of CCE-CTC against NEMA TS2 / ITE ATC interface requirements | A |
| 3 | ESN Module Assembly & Calibration Bench         | 4   | Custom multi-sensor calibration rig (CO: certified calibration gas 100 ppm, NO₂: 2 ppm, PM2.5: salt spray reference, noise: 94 dB pistophone calibrator, LoRa TX power tester) | Sensor calibration and zeroing; RF link margin test; LoRaWAN uplink confirmation | A |
| 4 | LoRaWAN Gateway Configuration Station           | 2   | Custom flashing station (USB + Ethernet, factory firmware + LoRaWAN channel plan per region, 4G modem provisioning, ChirpStack NS registration) | Programs 8-channel concentrator, sets LoRaWAN 1.0.4/1.1 settings, provisions 4G SIM, registers gateway on NS | A |
| 5 | IP65/IP67 Enclosure Sealing Test Machine        | 1   | Ateq F620 IP test station (IP65: dust test, 12.5 kPa water jet; IP67: 1m submersion 30 min; pressure differential leak method for production testing) | Post-assembly ingress protection test for CCE-ESN (IP65), CCE-LORA-GW (IP67) | A |

---

## 8. Surface Finishing & Protection

| # | Equipment                                   | Qty | Spec / Model                                                              | Purpose                                                                       | Auto Level |
|---|---------------------------------------------|-----|---------------------------------------------------------------------------|-------------------------------------------------------------------------------|------------|
| 1 | Conformal Coating Machine                   | 1   | Nordson ASYMTEK S-920i (XY programmable spray/needle dispensing, 600 × 500 mm working area, 3 heads, solvent-based and UV-cure acrylic) | Applies conformal coating (IPC-CC-830) to all outdoor/weatherproof PCBs (smart pole, ESN, traffic controller, water meter) | A |
| 2 | UV Curing Tunnel                            | 1   | Dymax BlueWave LED XL curing conveyor (365/405 nm LEDs, variable speed, 300 mm belt width) | UV cures conformal coating and adhesives; inline after conformal coating machine | FA |
| 3 | Potting Machine (Encapsulation)             | 1   | Scheugenpflug A025 Dos (2-component PU / epoxy, 1:1 to 4:1 ratio, ±1% volume accuracy, 200 mL/min throughput) | Encapsulates IP-critical sensor circuits and junction box connections for CCE-ESN and water meter electronics | A |
| 4 | Desiccant Packing Station                   | 2   | Desiccant dispenser and heat-seal bag station (molecular sieve 4A, 1–2 g sachets, heat sealer for inner pack) | Places desiccant sachets inside sealed product packaging (smart meters, ESN, LoRa gateway) | SA |
| 5 | Anti-Static ESD Workstation Surfaces        | 40  | Desco 37085 series table mat + wriststrap monitor + ioniser bar (ANSI/ESD S20.20 compliant) | ESD control across all PCB handling, assembly, and test workstations           | M |

---

## 9. Material Handling — AMR Fleet & MHE

| # | Equipment                                   | Qty | Spec / Model                                                            | Purpose                                                                    | Auto Level |
|---|---------------------------------------------|-----|-------------------------------------------------------------------------|----------------------------------------------------------------------------|------------|
| 1 | Autonomous Mobile Robot (AMR) — Transport    | 10  | MiR200 or Quicktron E100 (200 kg payload, LiDAR + camera navigation, fleet managed via MES interface, 8h battery, inductive charging, 6 km/h max) | Material transport: raw material kitting from RMS to SMT feeders; WIP movement between assembly zones; FG to packaging | FA/AI |
| 2 | AMR Charging Stations                        | 4   | Inductive charging dock (auto-docking, 48 V/20 A, ≤90 min full charge) | Automated overnight and opportunistic charging of AMR fleet              | FA |
| 3 | Adjustable Pallet Racking System             | 1   | Mecalux structural pallet racking (6m height, 4,000 pallet positions, seismically braced, VNA layout for AMR aisle compatibility) | Raw materials and finished goods warehouse storage (RMS and FGW zones)     | M |
| 4 | Reach Forklift                               | 2   | Toyota 7FBMF30 electric reach truck (3.0T, 8m lift height, AC motor, Li-ion battery) | Loading/unloading of inbound containers at LD-IN; high-rack FGW pallet placement | SA |
| 5 | Manual Pallet Jack (electric)                | 4   | Crown WP3040 (1.5T, 1.5 kW motor, 2h charge, 10 km/h travel) | Short-distance pallet movement in packaging and dispatch zones             | SA |
| 6 | Gravity Roller Conveyor (fixed sections)     | 6   | Hytrol Model TS (100 mm dia rollers, 1.2m × 0.6m section, bolted frames) | Carton conveyor between packaging line and FGW dispatch area               | M |

---

## 10. Quality, Test & Calibration Laboratory Equipment

| # | Equipment                                            | Qty | Spec / Model                                                        | Purpose                                                                     | Auto Level |
|---|------------------------------------------------------|-----|---------------------------------------------------------------------|-----------------------------------------------------------------------------|------------|
| 1 | Digital Multimeter (Benchtop — Reference Grade)      | 4   | Keysight 34465A (6.5 digit, TRMS, LF extension, data logging) | Reference measurement for product test and calibration traceable to NIS national standards | M |
| 2 | Power Analyser                                       | 2   | Yokogawa WT500 (200 kHz bandwidth, 3-phase, 0.05% accuracy, IEC 62053 test) | Accuracy measurement of smart meter PCB against reference power standard     | A |
| 3 | Oscilloscope                                         | 4   | Keysight DSOX1204G (70 MHz, 4-channel, waveform generator, USB) | Signal trace and debugging for SMT rework and product NPI                   | M |
| 4 | RF Signal Generator & Analyser                       | 2   | Rohde & Schwarz CMW100 (2G/3G/4G/NB-IoT/LoRa modes, 100 kHz–3 GHz, 0.1 dB output accuracy) | Type approval RF test support for NB-IoT, LoRa, Wi-Fi, 4G/5G devices      | A |
| 5 | Spectrophotometer (LED colour/flux)                  | 1   | Konica Minolta CL-200A illuminance colorimeter + integrating sphere (LED driver / street light QC) | Verification of LED flux (lm), colour temperature (CCT), CRI for CCE-SPS pole LED modules | SA |
| 6 | Environmental Test Chamber (Temperature & Humidity)  | 1   | Binder MKF 240 (–40°C to +180°C, 10–98% RH, 240 L, IEC 60068-2-78 humidity cycle, temperature ramp 5°C/min) | Accelerated reliability test for finished products; qualification testing of new designs | A |
| 7 | Salt Spray Chamber                                   | 1   | Ascott S450ip (450L, ASTM B117 / IEC 60068-2-52, NaCl 5% neutral, 35°C ±1°C) | Corrosion test for smart pole hardware and CCE-ESN enclosures              | A |
| 8 | Microscope (Inspection — PCB/Solder)                 | 2   | Leica EZ4W stereo microscope (8× – 35×, 5 MP digital camera output, ring illuminator, USB export) | Manual solder joint inspection, failure analysis of returned defective PCBs | M |

---

## 11. Energy & Utilities Infrastructure

| # | Equipment                                    | Qty | Spec / Model                                                          | Purpose                                                                     | Auto Level |
|---|----------------------------------------------|-----|-----------------------------------------------------------------------|-----------------------------------------------------------------------------|------------|
| 1 | Solar PV Array (Rooftop + Car Park Canopy)   | 600 kWp | 1,500 × Risen Energy 400 Wp monocrystalline half-cut PERC modules (bifacial-ready, 144 cells, Vmpp 34.2 V, IP68 J-box) | Primary renewable energy generation; 85% of daytime facility energy demand | FA |
| 2 | LFP Battery Energy Storage System (BESS)     | 1   | BYD Battery-Box Premium HVS 650 kWh or CATL EnerOne 650 kWh (rack-mount LFP, BMS, IP55, ≤ 0.5°C cell temp variation, 10-year cycle warranty) | Night and early-morning load supply; peak shaving; LFTZ grid outage backup | FA/AI |
| 3 | Grid-Tied Solar Inverter / Hybrid Inverter   | 6   | Sungrow SH110T-V112 110 kW hybrid (per 100 kWp string, MPPT 2-channel, 3-phase, IEC 62109, grid-forming mode for BESS) | DC/AC conversion for solar; controls BESS charge/discharge vs grid tariff | FA/AI |
| 4 | Diesel Generator — Standby                   | 1   | Perkins 2806A-E18TTAG4 400 kVA (3-phase, 0.8 pf, 50 Hz, 12V Delco electric start, 750L base tank, 48h autonomy) | Backup power when BESS depleted and LFTZ grid unavailable; peak emergency load | A |
| 5 | Automatic Transfer Switch (ATS)              | 1   | Socomec ATYS 3S 400 A (3-pole, 3-phase, auto source transfer: Grid → BESS Inverter → Generator; < 30 ms) | Seamless source switching; prevents SMT reflow oven voltage sag damage      | FA |
| 6 | Compressed Air Compressor                    | 2   | Atlas Copco GA30+ FF (30 kW, 5.6 m³/min, 8 bar, integrated dryer and filter, IE4 motor, Smartlink monitoring) | Pneumatic tools (screwdrivers, press-fit, pick-and-place), PCB cleaning, potting machine air | FA |
| 7 | Energy Management System (EMS) — Building    | 1   | Schneider Electric EcoStruxure PME (real-time load monitoring per zone, solar/BESS/grid metering, demand forecasting, MES integration) | Building energy monitoring, load priority management, MES energy data sync  | FA/AI |

---

## 12. IT, MES & Control Infrastructure

| # | Equipment                                    | Qty | Spec / Model                                                               | Purpose                                                                     | Auto Level |
|---|----------------------------------------------|-----|----------------------------------------------------------------------------|-----------------------------------------------------------------------------|------------|
| 1 | MES Server Cluster                            | 2   | Dell PowerEdge R750xs (Xeon Silver 4310, 128 GB RAM, 4× 2TB SSD RAID10, Redundant PSU, iDRAC9) | Primary + secondary MES application servers (Coo-Cah MES); active–passive HA failover | FA |
| 2 | Industrial Network Switch (Core)              | 2   | Cisco IE-3400H-24T-E (24-port GbE, TSN-capable, IEC 61850, L3 managed, IEC 61850 ring protection) | Core production network; EtherNet/IP, Modbus TCP, PROFINET to all PLCs and equipment | FA |
| 3 | Industrial Workstation (MES Operator)         | 6   | Dell OptiPlex 7000 MT (i7-12700, 32 GB RAM, 22" industrial touchscreen, CE-marked, fanless option for solder environment) | MES operator terminals at each production zone supervisor station            | A |
| 4 | CCTV Safety & Production Monitoring System   | 1   | 32-channel Hikvision NVR DS-9632NI-I16 + 24× 2MP dome cameras (PoE, H.265, 60-day storage, AI intrusion detection, production line coverage) | 24/7 safety surveillance; production incident review; AI anomaly motion alerts | FA/AI |
| 5 | Factory Wi-Fi Network (Production Floor)     | 1   | Cisco Catalyst Wi-Fi 6E Access Points × 12 (C9136AXI, 802.11ax, PoE, roaming, WPA3-Enterprise, VLAN segregation) | AMR fleet Wi-Fi backbone; barcode scanner and tablet connectivity throughout plant | FA |

---

*See [`energy-profile.md`](./energy-profile.md) for energy load calculations. See [`floor-plan.md`](./floor-plan.md) for equipment zone placement. See [`automation-roadmap.md`](./automation-roadmap.md) for Phase 2/3 upgrades.*
