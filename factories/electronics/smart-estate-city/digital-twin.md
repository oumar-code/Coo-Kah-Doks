# Smart Estate & City Electronics Factory — Digital Twin Architecture

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Smart Estate & City Electronics Factory | **Location:** Lekki Free Trade Zone (LFTZ), Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Digital Manufacturing & AI Team

---

## 1. Digital Twin Overview

The Coo-Cah Smart Estate & City Electronics Factory Digital Twin is a live, synchronised virtual model of the factory's physical production environment. It ingests real-time data from SMT machines, meter assembly and calibration stations, AMRs, energy systems, quality test stations, and environmental sensors via the Coo-Cah MES and AI Platform. The digital twin enables production simulation, root-cause analysis, calibration process optimisation, and predictive maintenance without disrupting live production.

The calibration lab digital twin is a distinctive feature of this factory: real-time error trends from the 4 IEC 62053 calibration benches are streamed to the digital twin, enabling AI-driven detection of reference standard drift and prediction of upcoming calibration failures before they impact production yield.

| Parameter                           | Value                                                               |
|-------------------------------------|---------------------------------------------------------------------|
| Digital Twin Platform               | Coo-Cah AI Platform — Digital Twin Module                          |
| Data Synchronisation Latency        | ≤ 1 second (real-time streaming via MQTT over TLS)                 |
| Asset Count (Phase 1)               | 118 registered physical assets                                      |
| Sensor Integration Points           | ~2,200 data points (energy, temperature, motion, QC, AMR, calibration) |
| Simulation Framework                | Discrete-event simulation (DES) + process physics models            |
| 3D Spatial Model                    | BIM-linked 3D model of 14,000 m² floor (all production zones)       |
| Cloud Platform                      | Coo-Cah Platform (Lagos DC) + on-site edge nodes (3×)               |
| Phase 2 Expansion                   | Cobot kinematics models; AI calibration prediction twin; meter DLMS event simulation |

> **NEPZA Data Residency:** As a NEPZA-licensed Free Zone Enterprise, primary digital twin data (including all NERC calibration records) is stored on-site at the LFTZ factory edge nodes. Only anonymised/aggregated analytics data is synced to the Coo-Cah Platform (Lagos DC) cloud. Raw meter calibration data and NERC audit logs are never transmitted to external cloud services without NEPZA compliance review. NCC audit data is retained on-site for ≥5 years; NERC calibration data for ≥10 years.

---

## 2. Asset Registry

### 2.1 SMT & PCB Processing Assets (Line 1 + Line 2)

| Asset ID          | Asset Name                          | Location    | Sensors / Data Points                                              | DT Status  |
|-------------------|-------------------------------------|-------------|--------------------------------------------------------------------|------------|
| DT-SMT-L1-01      | DEK Horizon Stencil Printer (L1)    | Z2 SMT L1   | Print recipe, paste volume (cm³), stencil life (cycles), squeegee pressure, alarm state | Phase 1 |
| DT-SMT-L1-02      | Koh Young SPI KY-3030VP (L1)        | Z2 SMT L1   | 3D paste volume per pad, volume CPK, defect count per board, board ID | Phase 1 |
| DT-SMT-L1-03      | JUKI FX-3R Pick-and-Place (L1)      | Z2 SMT L1   | CPH, feeder slot errors, nozzle state per head, placement count, recipe name | Phase 1 |
| DT-SMT-L1-04      | JUKI RS-1 Flexible Mounter (L1)     | Z2 SMT L1   | CPH, feeder errors, placement accuracy trend, active programme     | Phase 1    |
| DT-SMT-L1-05      | Heller 1964 MK5 Reflow Oven (L1)    | Z2 SMT L1   | Zone temps ×10, conveyor speed (mm/min), N₂ flow (L/min), O₂ ppm, alarms | Phase 1 |
| DT-SMT-L1-06      | Mirtec MV-3L OMNI AOI (L1)          | Z2 SMT L1   | Defect codes per board, FPY per board, image reference, alarm state | Phase 1   |
| DT-SMT-L1-07      | Viscom S6056 X-Ray (shared)         | Z2 SMT L1   | BGA void % per joint, solder joint image, pass/fail per board      | Phase 1    |
| DT-SMT-L1-08      | Ersa VERSAFLOW Selective Solder (L1)| Z2 SMT L1   | Flux level (%), solder level (mm), nozzle temp (°C), wave height, recipe | Phase 1 |
| DT-SMT-L1-09      | Keysight I3070 ICT (L1)             | Z2 SMT L1   | Net test pass/fail, shorts/opens count, fixture ID, serial, test time | Phase 1  |
| DT-SMT-L1-10      | PCB Depanelling Router (L1)         | Z2 SMT L1   | Cycle count, spindle speed (rpm), programme ID, alarm state        | Phase 1    |
| DT-SMT-L2-01 to 10| SMT Line 2 (identical set)          | Z3 SMT L2   | Same data points as L1 equivalents; separate line_id tag           | Phase 1    |

### 2.2 Smart Meter Assembly & Calibration Assets

| Asset ID        | Asset Name                                   | Location     | Sensors / Data Points                                                   | DT Status  |
|-----------------|----------------------------------------------|--------------|-------------------------------------------------------------------------|------------|
| DT-METER-01     | Meter Assembly Conveyor Line 1 (Bosch TS 4)  | Z4 Meter Asm | Belt speed (m/min), station queue depth, pallet ID (barcode scan), station status (idle/busy/fault) | Phase 1 |
| DT-METER-02     | Meter Assembly Conveyor Line 2 (Bosch TS 4)  | Z4 Meter Asm | Same data points as Line 1                                              | Phase 1    |
| DT-METER-03     | Atlas Copco Torque Stations ×8               | Z4 Meter Asm | Torque (Nm) per channel, angle (°), OK/NOK, screw sequence, unit serial  | Phase 1    |
| DT-METER-04     | Branson DCX-S Ultrasonic Welders ×2          | Z4 Meter Asm | Weld energy (J), amplitude (µm), weld depth (mm), alarm state, serial ref | Phase 1  |
| DT-METER-05     | Firmware Flash Stations ×8                   | Z4 Meter Asm | Unit serial, firmware version, NB-IoT IMEI (BC660), flash result, duration | Phase 1  |
| DT-METER-06     | Meter Functional Test Fixtures ×8            | Z4 Meter Asm | Supply voltage (V), injection current (A), meter reading vs. reference, DLMS OBIS snapshot, OK/NOK | Phase 1 |
| DT-METER-07     | NB-IoT Module Test Fixtures ×4               | Z4 Meter Asm | RSSI (dBm), SINR (dB), network attach time (s), band (B8), IMEI match, pass/fail | Phase 1 |
| DT-METER-08     | Nordson SelectCoat Conformal Coating Machine | Z6 Coat      | Coating weight (g), UV cure temp (°C), board ID, coating programme, alarm | Phase 1   |
| DT-METER-09     | 2-Component PU Potting Machine               | Z6 Coat      | Mix ratio (A:B), pot life timer (min), cure temp (°C), batch ID, alarm  | Phase 1    |
| DT-CAL-01       | IEC 62053 Calibration Bench 1 (8-unit)       | Z5 Cal Lab   | Error % at 5/50/100/120% Irated per unit, ambient temp (°C), RH (%), reference meter ID, certificate number, pass/fail per unit slot | Phase 1 |
| DT-CAL-02       | IEC 62053 Calibration Bench 2 (8-unit)       | Z5 Cal Lab   | Same 8-unit data set as Bench 1                                         | Phase 1    |
| DT-CAL-03       | IEC 62053 Calibration Bench 3 (8-unit, 3-ph) | Z5 Cal Lab   | Error % at 5/50/100/120% Irated (3-phase, IEC 62053-22), ambient temp, reference ID, cert, pass/fail | Phase 1 |
| DT-CAL-04       | IEC 62053 Calibration Bench 4 (8-unit, 3-ph) | Z5 Cal Lab   | Same 3-phase data set as Bench 3                                        | Phase 1    |
| DT-CAL-05       | Water Meter Gravimetric Calibration Rig 1    | Z5 Cal Lab   | Flow rate (L/min), reference mass (kg), meter reading (L), error (%), ambient temp (°C), pass/fail | Phase 1 |
| DT-CAL-06       | Water Meter Gravimetric Calibration Rig 2    | Z5 Cal Lab   | Same data set as Rig 1                                                  | Phase 1    |
| DT-CAL-07       | Calibration Lab Environmental Sensor         | Z5 Cal Lab   | Ambient temp (°C), RH (%), barometric pressure (hPa) — continuous 24/7 | Phase 1   |

### 2.3 Smart Estate Hub & LoRa / ESN Assembly Assets

| Asset ID     | Asset Name                                   | Location     | Sensors / Data Points                                                   | DT Status  |
|--------------|----------------------------------------------|--------------|-------------------------------------------------------------------------|------------|
| DT-SEH-01    | SEH Assembly Benches ×4                      | Z7 SEH/IoT   | Barcode scan per station, sub-assembly check pass/fail, stage completion flag | Phase 1 |
| DT-SEH-02    | SEH RF & Wireless Test Fixtures ×4           | Z7 SEH/IoT   | Wi-Fi 6 RSSI (dBm), Zigbee 3.0 PAN join success, BLE RSSI, RS-485 loopback, test pass/fail | Phase 1 |
| DT-SEH-03    | SEH Firmware Flash Stations ×4               | Z7 SEH/IoT   | Unit serial, firmware version, flash result, OTA test pass/fail         | Phase 1    |
| DT-SEH-04    | SEH Function Test Fixture (8-hour burn-in rack)×2 | Z7      | Power cycle count, voltage, current, comms test, alarm log, burn-in pass/fail | Phase 1 |
| DT-LORA-01   | LoRa Gateway Assembly Benches ×2             | Z7 SEH/IoT   | Barcode scan, sub-assembly stage, concentrator board alignment check    | Phase 1    |
| DT-LORA-02   | LoRa Gateway RF Test (8-ch concentrator) ×2  | Z7 SEH/IoT   | Receive sensitivity (dBm) at SF7–SF12, channel plan 868 MHz, RSSI calibration, pass/fail | Phase 1 |
| DT-LORA-03   | LoRa Gateway IP67 Immersion Test Tank        | Z7 SEH/IoT   | Immersion depth (m), soak duration (min), post-test function, pass/fail | Phase 1    |
| DT-ESN-01    | ESN Sensor Calibration Stations ×4           | Z7 SEH/IoT   | CO (ppm) vs. reference, NO₂ (ppm) vs. reference, PM2.5 (µg/m³) vs. reference, noise (dB) vs. reference, temp/RH calibration, calibration certificate per unit | Phase 1 |
| DT-ESN-02    | ESN LoRa RF Test Fixtures ×2                 | Z7 SEH/IoT   | RSSI (dBm), SNR (dB), range simulation (link budget), IMEI/DevEUI match, pass/fail | Phase 1 |
| DT-ESN-03    | ESN IP65 Spray Test Chamber                  | Z7 SEH/IoT   | Spray duration, pressure (bar), nozzle angle, post-test function, pass/fail | Phase 1 |

### 2.4 Smart Pole Fabrication & Assembly Assets

| Asset ID     | Asset Name                                      | Location      | Sensors / Data Points                                                  | DT Status  |
|--------------|-------------------------------------------------|---------------|------------------------------------------------------------------------|------------|
| DT-POLE-01   | MIG/MAG Welding Stations ×4 (Lincoln Electric)  | Z8 Pole Fab   | Weld current (A), voltage (V), wire feed rate (m/min), arc time (s), shielding gas flow, QC check flag | Phase 1 |
| DT-POLE-02   | Shot-Blast / Sandblast Machine                  | Z8 Pole Fab   | Cycle time, media level (%), blast pressure (bar), throughput count    | Phase 1    |
| DT-POLE-03   | Overhead Crane (2-tonne)                        | Z8 Pole Fab   | Load weight (kg), position, travel speed, hook height, alarm           | Phase 1    |
| DT-POLE-04   | Pole Electronics Integration Benches ×3         | Z8 Pole Fab   | Assembly stage (1–6), barcode scan, harness continuity test, sub-assembly check | Phase 1 |
| DT-POLE-05   | CCTV + Wi-Fi AP Integration Test Benches ×2     | Z8 Pole Fab   | Camera image quality (bitrate, resolution, IR test), Wi-Fi AP channel (2.4/5 GHz), RSSI, IP66 seal test result | Phase 1 |
| DT-POLE-06   | DALI-2 LED Driver Test Rigs ×2 (IEC 62386)     | Z8 Pole Fab   | DALI address, dimming curve (0–100%), power factor, luminaire efficacy (lm/W), pass/fail per DiiA DALI-2 spec | Phase 1 |
| DT-POLE-07   | Pole Base Plate & Anchor Bolt Fixture          | Z8 Pole Fab   | Bolt torque (Nm) per anchor, alignment check (±1 mm), barcode scan     | Phase 1    |

### 2.5 Traffic Controller Assembly Assets

| Asset ID     | Asset Name                                    | Location       | Sensors / Data Points                                                  | DT Status  |
|--------------|-----------------------------------------------|----------------|------------------------------------------------------------------------|------------|
| DT-CTC-01    | CTC Cabinet Assembly Benches ×2               | Z9 CTC         | Assembly stage, BOM check (all components fitted), barcode scan, stage OK flag | Phase 1 |
| DT-CTC-02    | CTC Functional Test Rigs ×2                   | Z9 CTC         | Phase timing test (ms accuracy), 4G cellular attach, fallback logic test (fixed-time plan), output relay check (16 outputs), surge test pass/fail, pass/fail | Phase 1 |
| DT-CTC-03    | CTC Burn-In Rack (4-unit simultaneous, 72 h) ×1 | Z9 CTC       | Per-unit: temp (°C), power cycle count, communications log (packet loss %), alarm event count, burn-in pass/fail | Phase 1 |
| DT-CTC-04    | CTC Cabinet IP55 Seal Verification Fixture    | Z9 CTC         | Pressure test (Pa), soak time (min), post-test door seal inspection, pass/fail | Phase 1 |

### 2.6 Final QC & Environmental Test Lab Assets

| Asset ID     | Asset Name                              | Location     | Sensors / Data Points                                              | DT Status  |
|--------------|-----------------------------------------|--------------|--------------------------------------------------------------------|------------|
| DT-QC-01     | Weiss Technik Salt Spray Chamber        | Z10 QC Lab   | Salt concentration (%), chamber temp (°C), exposure time (h), part ID, pass/fail | Phase 1 |
| DT-QC-02     | Thermal Cycling Chamber (–40°C to +85°C)| Z10 QC Lab   | Temp profile, ramp rate (°C/min), cycle count, dwell time, part ID, pass/fail | Phase 1 |
| DT-QC-03     | Vibration Test Rig (IEC 60068-2-6)      | Z10 QC Lab   | Frequency (Hz), amplitude (mm), axis (X/Y/Z), duration (min), part ID, pass/fail | Phase 1 |
| DT-QC-04     | Chroma 19036 Hipot/Safety Tester ×2    | Z10 QC Lab   | Hipot voltage (V), leakage current (µA), earth bond (mΩ), serial, pass/fail | Phase 1 |
| DT-QC-05     | AI Visual Inspection Station ×2 (Cognex IS9000) | Z10 QC Lab | Defect class, confidence score, image reference, pass/fail, serial | Phase 1 |

### 2.7 AMR Fleet Assets

| Asset ID               | Asset Name                   | Fleet Role       | Sensors / Data Points                                                     | DT Status  |
|------------------------|------------------------------|------------------|---------------------------------------------------------------------------|------------|
| DT-AMR-MIR250-01 to 10 | MiR250 Transport AMRs ×10    | Main transport   | Position (x, y, θ), speed (m/s), payload weight (kg), battery SoC (%), mission status, error flags | Phase 1 |
| DT-AMR-DOCK-01 to 12   | AMR Charging Docks ×12       | Charging station | Dock occupied (T/F), AMR ID, charge current (A), AMR SoC (%), charge complete flag | Phase 1 |

### 2.8 Energy System Assets

| Asset ID           | Asset Name                                     | Location       | Sensors / Data Points                                                  | DT Status  |
|--------------------|------------------------------------------------|----------------|------------------------------------------------------------------------|------------|
| DT-EN-PV-01        | Solar PV Array — Roof Main (480 kWp)           | Factory Roof   | Real-time generation (kW), cumulative (kWh), panel string IV curves, irradiance (W/m²), module temp (°C) | Phase 1 |
| DT-EN-PV-02        | Solar PV Array — Car Park Canopy (120 kWp)    | Car Park       | Real-time generation (kW), cumulative (kWh), irradiance (W/m²)        | Phase 1    |
| DT-EN-BESS-01      | LFP BESS Container 1 (325 kWh, BYD/CATL)      | North Yard     | SoC (%), SoH (%), charge/discharge power (kW), cell temperatures (min/max/avg °C), pack voltage (V), alarms | Phase 1 |
| DT-EN-BESS-02      | LFP BESS Container 2 (325 kWh, BYD/CATL)      | North Yard     | Same data set as BESS-01                                               | Phase 1    |
| DT-EN-INV-01 to 06 | Sungrow SH110T-V112 Inverters ×6              | Inverter Room  | AC output (kW), DC input (kW), inverter efficiency (%), alarm state    | Phase 1    |
| DT-EN-GEN-01       | Perkins 400 kVA Diesel Generator              | SE Corner      | Running status, output (kW), fuel level (L), run hours (h), coolant temp (°C) | Phase 1 |
| DT-EN-GRID-01      | LFTZ Grid Supply AMI Meter (11 kV intake)     | HV Substation  | Import power (kW), cumulative import (kWh), ToU tariff period, PF, alarms | Phase 1  |
| DT-EN-HVAC-01      | HVAC — Production Halls (multi-split system)  | Z2–Z9          | Cooling output (kW), supply/return temp (°C), compressor status, COP, alarm | Phase 1 |
| DT-EN-HVAC-02      | HVAC — Calibration Lab (precision control)    | Z5 Cal Lab     | Supply temp (°C), return temp (°C), RH (%), setpoint deviation, COP, alarm | Phase 1  |
| DT-EN-HVAC-03      | HVAC — Server Room & Offices                  | IT Room + Mez  | Room temp (°C), cooling load (kW), alarm                               | Phase 1    |
| DT-EN-COMP-01/02   | Atlas Copco GA30+ Air Compressors ×2          | Utility Room   | Outlet pressure (bar), delivered flow (m³/min), running hours, energy (kWh), alarm | Phase 1 |

---

## 3. Sensor Coverage Map — Zone-Level Sensor Density

| Zone | Zone Name                         | Assets Monitored | Data Points | Primary Sensor Types                                          |
|------|-----------------------------------|-----------------|-------------|---------------------------------------------------------------|
| Z2   | SMT Line 1                        | 10              | 380         | Temperature, SECS/GEM, OPC-UA, SPI 3D volume, AOI vision    |
| Z3   | SMT Line 2                        | 10              | 380         | Temperature, SECS/GEM, OPC-UA, SPI 3D volume, AOI vision    |
| Z4   | Meter Assembly (Lines 1 & 2)      | 9               | 310         | OPC-UA torque, barcode scan, flash API, functional test results |
| Z5   | Calibration Lab                   | 7               | 420         | IEC 62053 error %, ambient temp/RH, gravimetric flow, certs   |
| Z6   | Conformal Coating & Potting       | 2               | 80          | Coating weight, UV temp, potting mix ratio, pot life         |
| Z7   | SEH / LoRa / ESN Assembly & Test  | 9               | 280         | RF RSSI/SNR, sensor calibration (CO/NO₂/PM), IP spray test   |
| Z8   | Smart Pole Fabrication            | 7               | 200         | Weld current/voltage, DALI-2 dimming, CCTV image quality     |
| Z9   | Traffic Controller Assembly       | 4               | 140         | Phase timing, cellular attach, burn-in temp, relay check     |
| Z10  | Final QC & Environmental Test     | 5               | 180         | Salt spray temp, thermal cycle, vibration freq, hipot V/I    |
| Z11  | Packaging & FG Warehouse          | 3               | 80          | Checkweigher (g), barcode scan, AMR position, rack temp      |
| Z1   | Goods Inwards Stores              | 3               | 80          | VLM pick count, inventory level, barcode scan, temp/RH       |
| Site | Energy Systems                    | 14              | 470         | PV kW/kWh, BESS SoC/SoH, HVAC COP, compressor pressure      |

**Total (Phase 1):** ~118 assets monitored; ~3,000+ data points across all zones.

---

## 4. Digital Twin Simulation Use Cases

### 4.1 Production Simulation

| Use Case                                   | Description                                                                    | Business Value                              |
|--------------------------------------------|--------------------------------------------------------------------------------|---------------------------------------------|
| Meter Calibration Throughput Optimisation  | Simulate maximum daily calibration output across 4 benches; identify batching strategies | Target 192 calibrations/shift; supports 350k/year capacity |
| MAP/NMMP Batch Planning                    | Simulate production schedule vs. MAP partner delivery commitments; identify lead time risk | Maintain DisCo/NMMP delivery SLA           |
| SMT Line Changeover Optimisation           | Model optimal feeder change and recipe switch sequence for meter PCB → ESN PCB changeover | Reduce changeover time by est. 20–30%      |
| New Product Introduction (NPI) Simulation  | Simulate cycle time and yield before physical first article runs for new product variants | Reduce NPI cost and ramp time              |
| Smart Pole Assembly Takt Time Modelling    | Simulate 4-minute takt time per pole across parallel welding, integration, and test stations | Validate 100,000 poles/year Phase 1 capacity |
| Traffic Controller Burn-In Queue Modelling | Simulate 72-hour burn-in racks vs. CTC production rate; size rack capacity    | Ensure burn-in does not bottleneck CTC line |

### 4.2 Predictive Maintenance Simulation

| Use Case                                           | Description                                                                | Business Value                              |
|----------------------------------------------------|----------------------------------------------------------------------------|---------------------------------------------|
| Reflow Oven Thermal Zone Degradation Model         | Track heating element current draw vs. age; predict element failure before it causes a process excursion | Avoid unplanned SMT downtime |
| Calibration Bench Reference Standard Drift Detection | AI monitors error trends across bench slots; flags when reference standard deviation pattern suggests reference meter drift vs. NMI calibration value | Proactive NERC compliance protection |
| JUKI P&P Feeder Vibration Model                    | Monitor feeder vibration signatures; flag feeder wear before miss-picks rise | Maintain SMT FPY ≥ 98.5%                  |
| AMR Battery State-of-Health Prediction             | Monitor SoH trend per AMR; predict battery replacement window              | Maintain AMR availability ≥ 98%            |
| BESS State-of-Health Modelling                     | Compare LFP capacity fade vs. electrochemical model; project SoH at 5 years; trigger BESS cell replacement planning | Plan BESS replacement at optimal time |
| Ultrasonic Welder Transducer Wear Model            | Monitor weld amplitude vs. set-point; flag transducer fatigue              | Prevent meter housing weld failures        |
| CTC Burn-In Rack Temperature Uniformity            | Model temperature distribution inside burn-in rack; predict hot-spot failure of specific rack slots | Uniform thermal stress test across all CTC units |

### 4.3 Energy Optimisation Simulation

| Use Case                                      | Description                                                                   | Business Value                              |
|-----------------------------------------------|-------------------------------------------------------------------------------|---------------------------------------------|
| BESS Dispatch Optimisation                    | Simulate optimal BESS charge/discharge schedule vs. solar forecast + LFTZ grid ToU tariff | Minimise grid import cost; maximise solar self-consumption |
| Factory Load Shift                            | Identify deferrable loads (AMR charging, calibration bench pre-heat) to shift off-peak | Reduce grid import; flatten demand curve   |
| Calibration Lab HVAC Energy vs. Accuracy Trade-off | Model minimum HVAC energy required to maintain 23°C ±2°C for IEC 62053 test validity | Reduce calibration lab HVAC energy cost without compromising accuracy |
| Solar Soiling Loss Modelling                  | Compare actual vs. expected PV yield per string; flag underperforming strings requiring cleaning | Optimise car park canopy + rooftop cleaning schedule |
| Generator Run Minimisation                    | Simulate scenarios to keep diesel generator run hours < 200/year             | Lower OpEx; lower NOₓ emissions; NESREA compliance |

### 4.4 Quality & Compliance Simulation

| Use Case                                       | Description                                                                   | Business Value                              |
|------------------------------------------------|-------------------------------------------------------------------------------|---------------------------------------------|
| IEC 62053 Calibration Drift Prediction         | Track mean error trend per bench slot; AI models whether process drift will exceed Class 1 limits before next reference standard recalibration | Prevent NERC non-compliance |
| NB-IoT / LoRa RF Test Yield Prediction         | Model RF test first-pass yield per shift based on incoming component RSSI spread and solder joint quality from AOI | Reduce RF re-test volume by 20–30% |
| DLMS/COSEM Functional Test Defect Trending     | Correlate DLMS OBIS snapshot errors with upstream assembly parameters (torque, firmware version) | Root-cause meter functional failures |
| Meter Tamper Detection Rate Trending           | Analyse tamper event log activation rates during functional test vs. design intent; flag assembly process issues causing spurious tamper triggers | Ensure NERC Meter Code tamper detection compliance |
| ESN Sensor Calibration Drift Forecast          | Model sensor calibration certificate validity period; forecast when CO/NO₂ sensors in deployed units will require field recalibration | Support CCE-ESN field service programme |

---

## 5. Digital Twin Connectivity Architecture

Real-time data flows from physical assets to the digital twin via a layered connectivity stack:

```
Physical Assets (machines, sensors, AMRs, energy systems)
     │
     │  OPC-UA / SECS-GEM / RS-485 / REST API / BACnet
     ▼
Edge Node Layer (3× on-site nodes: SMT Zone, Meter/Cal Zone, QC/RF Zone)
     │  — MQTT publish to local broker (Eclipse Mosquitto)
     │  — Edge AI inference for real-time quality alerts
     │  — Local 90-day data buffer (SQLite time-series)
     │
     │  MQTT (TLS 1.3) — NEPZA-compliant: aggregated data only
     ▼
Coo-Cah Platform (Lagos DC) — Digital Twin Module
     │  — DES simulation engine (AnyLogic or SimPy)
     │  — AI/ML inference (calibration drift, predictive maintenance)
     │  — 3D BIM model (14,000 m² factory floor, all asset positions)
     │  — REST API for cross-factory integration and NERC/NCC exports
     ▼
Coo-Cah ERP + MES + Analytics Dashboard
```

### 5.1 Protocol Mapping per Asset Class

| Asset Class                      | Protocol(s) Used                    | Edge Node          | Update Rate   |
|----------------------------------|-------------------------------------|--------------------|---------------|
| SMT Equipment (DEK, JUKI, Heller)| SECS/GEM (SEMI standards) + OPC-UA  | SMT Zone Node      | 1–5 seconds   |
| SPI / AOI / X-Ray                | REST API or SECS-II                  | SMT Zone Node      | Per board      |
| Calibration Benches              | RS-485/TCP                          | Meter/Cal Node     | Per test result|
| Meter Assembly Conveyors         | OPC-UA                              | Meter/Cal Node     | 1 second       |
| Torque / Weld / Flash Stations   | OPC-UA / REST API                   | Meter/Cal Node     | Per cycle      |
| AMR Fleet (MiR250)               | MiR REST API via MiR Fleet          | SMT Zone Node      | 500 ms         |
| Energy Systems (BESS, Solar)     | SunSpec Modbus TCP / MQTT           | SMT Zone Node      | 5 seconds      |
| HVAC Systems                     | BACnet/IP                           | Meter/Cal Node     | 30 seconds     |
| RF Test Benches                  | REST API                            | QC/RF Node         | Per test       |
| Environmental Sensors (Cal Lab)  | MQTT (IoT sensor module)            | Meter/Cal Node     | 60 seconds     |

---

## 7. Digital Twin Maturity Roadmap

| Phase | Period    | Maturity Level          | Capabilities Added                                                                          |
|-------|-----------|-------------------------|---------------------------------------------------------------------------------------------|
| 1     | 2025–2026 | Descriptive Twin        | Real-time machine state, WIP tracking, calibration bench live data, energy monitoring, NCC and NERC log integration, AMR fleet position |
| 2     | 2027–2028 | Diagnostic + Predictive | Cobot kinematics model (UR20 arms), AI calibration drift prediction, BESS SoH model, NB-IoT/LoRa RF yield prediction, meter DLMS event simulation |
| 3     | 2029–2030 | Prescriptive Twin       | Fully autonomous schedule recommendation; lights-out SMT simulation; AI-driven NERC calibration pass-rate optimisation; predictive MAP/NMMP batch fulfillment |

---

## 8. Data Governance for Digital Twin

| Requirement                      | Implementation                                                                         |
|----------------------------------|----------------------------------------------------------------------------------------|
| Data Ownership                   | All digital twin data owned by Coo-Cah Group; not shared with third parties without written consent |
| NEPZA Data Residency             | Primary data stored on-site at LFTZ edge nodes; cloud sync to Coo-Cah Platform (Lagos DC) for aggregated analytics only |
| NERC Calibration Data Retention  | Raw calibration records retained on-site for ≥ 10 years per NERC Meter Code requirement|
| NCC Audit Data Retention         | RF test records retained on-site for ≥ 5 years per NCC audit requirement              |
| Intellectual Property            | Machine learning models and simulation outputs are Coo-Cah proprietary IP              |
| Real-Time Data Retention         | Real-time streaming data: 90 days on edge cache; then aggregated to daily summaries for cloud archive |
| Access Control                   | Role-based: Operator (read only), Engineer (simulate + configure), NERC Auditor (calibration export), Admin (full) |
| Export / API Access              | REST API available for approved Coo-Cah cross-factory integrations and NERC audit exports only |
| Audit Trail                      | All simulation runs, configuration changes, and NERC/NCC report exports logged with user ID, timestamp, and input/output summary |
| Cybersecurity                    | OT network isolation; TLS 1.3 for all MQTT and HTTPS streams; annual penetration test  |

---

*For MES data architecture and machine integration protocols, refer to [`mes-integration.md`](./mes-integration.md).*
*For automation milestones that expand the digital twin scope, refer to [`automation-roadmap.md`](./automation-roadmap.md).*
*For energy system monitoring and BESS data details, refer to [`energy-profile.md`](./energy-profile.md).*
*For regulatory data retention requirements (NERC, NCC, NEPZA), refer to [`regulatory.md`](./regulatory.md).*
