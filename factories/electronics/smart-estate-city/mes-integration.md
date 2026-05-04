# Smart Estate & City Electronics Factory — MES Integration Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Smart Estate & City Electronics Factory | **Location:** Lekki Free Trade Zone (LFTZ), Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** MES / Digital Manufacturing Team

---

## 1. MES Architecture Overview

The Smart Estate & City Electronics Factory MES is deployed as a Coo-Cah Platform module with an on-site primary instance and cloud-sync secondary. The system handles production order management, real-time WIP tracking, full unit-level serialisation and traceability, IEC 62053 calibration logging, NCC type approval RF test tracking, NERC meter audit report generation, MAP/NMMP batch dispatch logging, AMR fleet dispatching, and energy monitoring.

**NEPZA Free Zone Data Residency:** As a NEPZA-licensed Free Zone Enterprise, all production data — particularly NERC calibration records and NCC audit data — is stored on-site at the LFTZ factory. Cloud synchronisation to the Coo-Cah Platform (Lagos DC) is permitted for analytics and cross-factory visibility, but raw meter calibration certificates and NERC registry data are never transmitted outside the factory's local data environment without NEPZA compliance review.

```
                ┌─────────────────────────────────────────────────────┐
                │              Coo-Cah Cloud Platform                  │
                │   ERP  |  AI Platform  |  Digital Twin  | Analytics  │
                └──────────────────────┬──────────────────────────────┘
                                       │ HTTPS / MQTT (TLS 1.3)
                ┌──────────────────────▼──────────────────────────────┐
                │            MES Application Server                    │
                │   (on-site primary — LFTZ) + (cloud-sync secondary) │
                └──┬──────────┬───────────────┬──────────────────────┘
                   │          │               │                │
        ┌──────────▼──┐  ┌────▼──────┐  ┌────▼──────┐  ┌─────▼──────┐
        │  Edge Node   │  │Edge Node  │  │Edge Node  │  │Edge Node   │
        │  (SMT Zone)  │  │(Meter     │  │(Calibr.   │  │(QC + RF    │
        │  L1 + L2     │  │ Assembly) │  │  Lab)     │  │  Lab)      │
        └──┬───────────┘  └────┬──────┘  └────┬──────┘  └─────┬──────┘
           │                   │               │               │
     OPC-UA / MQTT / SECS-GEM / RS-485 / Ethernet / Wi-Fi 6 (IEEE 802.11ax)
           │                   │               │               │
   ┌───────▼───────────────────▼───────────────▼───────────────▼──────┐
   │              Shop Floor — Industrial Control Network              │
   │  SMT Lines | Meter Lines | Calibration Benches | AMRs | RF Lab   │
   └────────────────────────────────────────────────────────────────┘
```

---

## 2. MES Module Summary

| Module                            | Functionality                                                                     | Phase Available |
|-----------------------------------|-----------------------------------------------------------------------------------|-----------------|
| Production Order Management       | Work order creation, dispatch, progress tracking per product line                 | Phase 1         |
| WIP Tracking                      | Real-time unit-level WIP location by zone and station                             | Phase 1         |
| Traceability                      | Full unit serial number life history from PCB to dispatch                         | Phase 1         |
| Quality Management                | SPC, in-line hold/release gates, NCR management                                   | Phase 1         |
| Meter Calibration Traceability    | IEC 62053 calibration log per serial — error %, reference standard, certificate   | Phase 1         |
| NERC Audit Integration            | Automated NERC meter audit report generation (CSV/PDF export by batch/date/serial)| Phase 1         |
| DLMS/COSEM Event Log              | Per-serial tamper events, power outage events, demand registers per OBIS code     | Phase 1         |
| NCC LoRa / NB-IoT TA Tracking     | Type approval certificate registry, RF test logging, blocked-dispatch gate        | Phase 1         |
| MAP/NMMP Batch Dispatch Logging   | Batch-to-DisCo PO linkage, MAP licence number, NMMP batch code, location code     | Phase 1         |
| AMR Fleet Dispatch                | MiR Fleet integration; work order → transport mission creation                    | Phase 1         |
| Energy Monitoring                 | Zone-level energy sub-metering; kWh per production order                          | Phase 1         |
| Maintenance (CMMS)                | PM scheduling, work orders, spare parts inventory, calibration equipment PM       | Phase 1         |
| Predictive Maintenance            | AI vibration/temperature alert → maintenance work order                           | Phase 2         |
| AI Scheduling                     | Dynamic order sequencing based on real-time OEE and meter demand                  | Phase 2         |
| Digital Twin Sync                 | Live machine state feed to digital twin simulation model                          | Phase 2         |

---

## 3. Serial Number & Traceability Architecture

Every unit produced in the factory receives a globally unique serial number at the firmware flash station (meters) or equivalent identification point (other products). Traceability is maintained across the unit's full production life cycle, including NERC calibration certificate linkage and NCC type approval certificate linkage.

### 3.1 Serial Number Format

```
Product Prefix + Factory Code + Year + Julian Day + Sequence
Example: CCE-SM-ELEC-LFZ-25-212-006201
   CCE        = Coo-Cah Electronics
   SM-ELEC    = Product SKU abbreviation (SM-ELEC, SM-WATER, SEH, SPS, CTC, ESN, LORA-GW)
   LFZ        = LFTZ factory code (Lekki Free Zone)
   25         = Year 2025
   212        = Julian day 212 (31 July)
   006201     = Daily sequence number (zero-padded 6 digits)

Further examples:
   CCE-SM-WATER-LFZ-25-213-002400   — Water meter, LFTZ, 1 Aug 2025, unit 2400
   CCE-SEH-LFZ-26-001-000051        — Smart Estate Hub, LFTZ, 1 Jan 2026, unit 51
   CCE-LORA-GW-LFZ-26-045-000812    — LoRa Gateway, LFTZ, 14 Feb 2026, unit 812
```

### 3.2 Traceability Data Captured per Unit

| Data Point                               | Capture Stage                 | Stored In                   |
|------------------------------------------|-------------------------------|-----------------------------|
| PCB Panel ID                             | SMT line-start scan           | MES Traceability Module     |
| SMT Line Used (L1 or L2)                 | Automatic (station ID)        | MES                         |
| SPI paste volume result                  | Koh Young KY-3030VP → MES     | MES Quality Module          |
| AOI result (pass/fail/rework)            | Mirtec MV-3L OMNI → MES       | MES Quality Module          |
| X-Ray result (BGA / solder joint)        | Viscom S6056 → MES API        | MES Quality Module          |
| ICT result                               | Keysight I3070 → MES          | MES Quality Module          |
| Assembly line + station                  | Barcode scan per station      | MES Traceability            |
| Torque values (all screws)               | Atlas Copco → MES (OPC-UA)    | MES Traceability            |
| Unit Serial Number                       | Flash station → MES API       | MES + ERP                   |
| Firmware version flashed                 | Flash fixture → MES           | MES Traceability            |
| IMEI (NB-IoT module, Quectel BC660)      | IMEI read at flash station    | MES NCC Module + NERC Log   |
| Meter functional test result             | Test fixture → MES            | MES Quality Module          |
| IEC 62053 calibration: error at 5% Irated  | Calibration bench → MES    | MES Calibration Module      |
| IEC 62053 calibration: error at 50% Irated | Calibration bench → MES    | MES Calibration Module      |
| IEC 62053 calibration: error at 100% Irated| Calibration bench → MES    | MES Calibration Module      |
| IEC 62053 calibration: error at 120% Irated| Calibration bench → MES    | MES Calibration Module      |
| Calibration ambient temperature (°C)    | Calibration bench sensor      | MES Calibration Module      |
| Reference standard ID used              | Calibration bench ID          | MES Calibration Module      |
| Calibration certificate number           | MES auto-generated            | MES + NERC Audit Module     |
| NERC registration number (batch)         | MES NERC Module               | MES + NERC Audit Module     |
| NB-IoT RF test result (Quectel BC660)    | RF test fixture → MES         | MES NCC Module              |
| LoRa RF test result (SX1276 / SX1302)   | LoRa RF fixture → MES         | MES NCC Module              |
| NCC TA Certificate linked               | MES NCC Module                | MES NCC Module              |
| DLMS/COSEM OBIS snapshot on meters       | Meter functional test         | MES DLMS/COSEM Module       |
| MAP batch reference number               | Dispatch module               | MES MAP/NMMP Module         |
| DisCo purchase order number              | Dispatch module               | MES MAP/NMMP Module         |
| Packaged by operator ID                  | Operator badge scan           | MES Traceability            |
| Carton ID / Pallet ID                    | Label scan                    | MES WMS                     |
| Dispatch date / batch                    | Dispatch scan                 | MES WMS                     |

### 3.3 DLMS/COSEM-Specific Traceability Data (Electricity Meters)

For each CCE-SM-ELEC unit, the MES records the following DLMS/COSEM-specific data at the functional test and calibration stages:

| Data Field                     | OBIS Code            | Notes                                                     |
|--------------------------------|----------------------|-----------------------------------------------------------|
| Active energy import (kWh)     | 1.0.1.8.0.255        | Verified against calibration reference                    |
| Active energy export (kWh)     | 1.0.2.8.0.255        | Bi-directional meter only                                 |
| Instantaneous voltage (V)      | 1.0.32.7.0.255       | L1; 1.0.52.7.0.255 (L2), 1.0.72.7.0.255 (L3) for 3-phase|
| Instantaneous current (A)      | 1.0.31.7.0.255       | Per phase                                                 |
| Tamper event log count         | 0.0.99.98.0.255      | Counted during functional test                            |
| Power outage event log         | 0.0.96.7.0.255       | Tested during power interruption test                     |
| Meter serial number (DLMS)     | 0.0.96.1.0.255       | Matched to factory serial                                 |
| Metrology class                | 0.0.96.1.4.255       | Class 1 (IEC 62053-21) or Class 0.5S (IEC 62053-22)      |
| Calibration certificate number | Factory attribute     | NERC-traceable calibration cert reference                 |
| NERC registration number       | Factory attribute     | Assigned batch-level NERC reference number                |

---

## 4. NERC Meter Code & Calibration Station Integration (Nigeria-Specific)

### 4.1 What is the NERC Meter Code?

The Nigerian Electricity Regulatory Commission Meter Code 2012 (as amended) is the mandatory regulatory framework governing electricity meters deployed by Distribution Companies (DisCos) in Nigeria. The Meter Code specifies:

- Type test certificate requirements (IEC 62052-11, IEC 62053-21/22)
- Factory calibration record requirements for each meter serial number
- Tamper detection and event logging requirements
- DLMS/COSEM protocol compliance for AMI/head-end integration
- STS prepayment token compatibility for prepaid meters
- Meter serial number registration with the NERC Meter Registry

All CCE-SM-ELEC units must be calibrated and have a traceable calibration record in the MES before they may be dispatched to a DisCo or MAP partner.

### 4.2 Calibration Bench Integration

The factory operates **4× IEC 62053 calibration benches**, each capable of testing 8 units simultaneously. The calibration lab (Zone Z5) is maintained at 23°C ±2°C, 40–70% RH, per IEC 62053-21 test conditions.

| Bench ID    | Units Simultaneous | Capability                          | Protocol           |
|-------------|-------------------|-------------------------------------|--------------------|
| CAL-BENCH-1 | 8                 | Single-phase Class 1 (IEC 62053-21) | RS-485/TCP → MES   |
| CAL-BENCH-2 | 8                 | Single-phase Class 1                | RS-485/TCP → MES   |
| CAL-BENCH-3 | 8                 | Three-phase Class 0.5S (IEC 62053-22)| RS-485/TCP → MES  |
| CAL-BENCH-4 | 8                 | Three-phase Class 0.5S              | RS-485/TCP → MES   |

**Calibration data flow:** Bench controller → RS-485/TCP → Edge Node (Cal Lab) → MES Calibration Module → auto-generates calibration certificate record per serial.

### 4.3 IEC 62053 Calibration Log per Unit

For each meter serial, the MES stores the following calibration record (retained for **minimum 10 years** per NERC Meter Code requirement):

| Field                          | Description                                    | Example Value                |
|-------------------------------|------------------------------------------------|------------------------------|
| Unit serial number             | CCE-SM-ELEC-LFZ format                        | CCE-SM-ELEC-LFZ-26-001-000123|
| Calibration bench ID           | CAL-BENCH-1 to 4                              | CAL-BENCH-2                  |
| Reference standard ID          | NAFDAC/NMI-traceable reference meter serial    | REF-STD-2026-003             |
| Reference standard calibration date | Last recalibration of reference standard | 2026-01-15                   |
| Test date/time                 | ISO 8601 timestamp                            | 2026-04-01T09:22:11Z         |
| Ambient temperature (°C)       | Calibration lab temperature                   | 23.1°C                       |
| Error at 5% Irated (%)         | Max allowed: ±2% (Class 1), ±1.5% (0.5S)     | +0.42%                       |
| Error at 50% Irated (%)        | Max allowed: ±1% (Class 1), ±0.5% (0.5S)     | +0.18%                       |
| Error at 100% Irated (%)       | Max allowed: ±1% (Class 1), ±0.5% (0.5S)     | +0.11%                       |
| Error at 120% Irated (%)       | Max allowed: ±1% (Class 1), ±0.5% (0.5S)     | +0.09%                       |
| Calibration result             | PASS / FAIL                                    | PASS                         |
| Certificate number             | Auto-generated unique cert reference          | CERT-CCE-LFZ-2026-123456     |
| Operator ID                    | Calibration technician badge                  | OPR-0042                     |

### 4.4 NERC Audit Report Auto-Generation

The MES NERC Audit Module generates one-click CSV and PDF reports of all calibration records:

- **By serial number range:** Export calibration log for any serial or range of serials
- **By production batch:** Export all calibration records for a named production batch
- **By date range:** Export all records between two dates
- **By DisCo PO:** Export all meters linked to a specific DisCo purchase order
- **Summary statistics:** Pass rate, mean error at each test point, reference standard ID, ambient temperature distribution

NERC audit reports are digitally signed with the factory's Quality Manager certificate and are export-ready for submission to NERC on demand.

### 4.5 MAP/NMMP Batch Dispatch Logging

Each meter dispatch batch is linked to the following MAP/NMMP fields in the MES:

| Field                       | Description                                          |
|-----------------------------|------------------------------------------------------|
| DisCo purchase order number | The DisCo (e.g., EKEDC) or MAP partner PO reference |
| MAP licence number          | NERC-issued MAP licence of the deploying entity      |
| NMMP batch code             | FGN/REA NMMP batch reference (if applicable)         |
| Installation state/LGA      | Target deployment location code                      |
| Dispatch date               | ISO 8601 timestamp                                   |
| Carton count / unit count   | Quantity dispatched                                  |
| Serial number list          | CSV or PDF of all serials in the batch               |
| Calibration certificate refs| Linked certificate numbers for all units in batch    |

---

## 5. NCC Type Approval Integration for LoRa / NB-IoT

### 5.1 NCC Type Approval Certificate Register

| Product SKU    | Wireless Technology           | Frequency              | Chipset                  | NCC TA Number (placeholder) | Certificate Date | Expiry   | Status       |
|----------------|-------------------------------|------------------------|--------------------------|------------------------------|------------------|----------|--------------|
| CCE-SM-ELEC    | NB-IoT (LTE-M/NB1)            | 900 MHz Band B8        | Quectel BC660            | NCC/TA/2026/XXXX             | Q2 2027          | Q2 2032  | Pending (P1) |
| CCE-SM-WATER   | NB-IoT (LTE-M/NB1)            | 900 MHz Band B8        | Quectel BC660K           | NCC/TA/2026/XXXX             | Q2 2027          | Q2 2032  | Pending (P1) |
| CCE-LORA-GW    | LoRa 868/915 MHz              | 868 MHz (primary)      | Semtech SX1302/SX1303    | NCC/TA/2026/XXXX             | Q3 2027          | Q3 2032  | Pending (P1) |
| CCE-ESN        | LoRa 868/915 MHz              | 868 MHz (primary)      | Semtech SX1276           | NCC/TA/2026/XXXX             | Q3 2027          | Q3 2032  | Pending (P1) |
| CCE-SEH        | Wi-Fi 6 (802.11ax) + Zigbee 3.0| 2.4/5 GHz + 2.4 GHz  | Qualcomm/MediaTek + TI   | NCC/TA/2026/XXXX             | Q4 2027          | Q4 2032  | Pending (P1) |
| CCE-SPS        | 4G LTE + Wi-Fi 4 (802.11n)    | LTE B1/B3/B8 + 2.4 GHz| Sierra/Quectel + AP chip | NCC/TA/2026/XXXX             | Q4 2027          | Q4 2032  | Pending (P1) |
| CCE-CTC        | 4G/5G cellular                | LTE + Sub-6 GHz 5G     | Quectel RG500Q           | NCC/TA/2027/XXXX             | Q1 2028          | Q1 2033  | Pending (P1) |

> **LoRa Spectrum Note:** 868 MHz LoRa is the primary frequency for CCE-LORA-GW and CCE-ESN in Nigeria, operated under NCC spectrum management. 915 MHz is also supported in firmware as an alternative. Coo-Cah Regulatory Affairs must confirm NCC frequency allocation for LoRaWAN deployment with NCC Spectrum Management Division before commercial shipment.

### 5.2 NCC RF Test Logging per Unit

For all wireless products, the MES NCC Module logs the following RF test data per unit serial:

| Data Field                    | Description                                         |
|-------------------------------|-----------------------------------------------------|
| Unit serial number             | CCE-SKU-LFZ format                                 |
| NCC TA certificate linked     | Active TA certificate number                        |
| RF test bench ID               | Which RF bench tested the unit                     |
| Test frequency / band          | Band(s) tested                                     |
| Tx power measured (dBm)       | Actual transmit power vs. declared max EIRP        |
| Spurious emissions pass/fail  | Regulatory limit compliance                        |
| RSSI / sensitivity (dBm)      | Receive sensitivity measured                       |
| NB-IoT IMEI confirmed          | IMEI matches IMEI recorded at flash station        |
| RF test result                 | PASS / FAIL                                        |
| Test operator ID               | RF lab technician badge                            |
| Test timestamp                 | ISO 8601                                           |

### 5.3 Production RF Sample Selection

The MES NCC Module automatically flags **every 50th unit per shift** as an NCC RF Test Sample (configurable per SKU). Flagged units are routed to the RF test bench for full NCC-compliant RF characterisation rather than the standard production RF go/no-go test.

### 5.4 Blocked-Dispatch Gate

The MES enforces a hard **Blocked-Dispatch Gate** for all wireless products:

- Any product SKU without a valid, non-expired NCC TA certificate stored in the MES NCC Module **cannot be dispatched** — the dispatch step generates a BLOCKED work order status
- NCC certificate expiry is monitored; an alert is raised 6 months before expiry and a TA renewal task is auto-created in the Regulatory Affairs workqueue

---

## 6. Machine Interface Specifications

### 6.1 SMT Equipment Integration

| Equipment                    | Protocol              | Data Points                                                        | Direction     |
|------------------------------|-----------------------|--------------------------------------------------------------------|---------------|
| DEK Horizon Stencil Printer  | SMEMA + SECS/GEM      | Print recipe, paste volume, stencil life, squeegee pressure, alarm | Bidirectional |
| Koh Young SPI KY-3030VP      | SECS/GEM or REST API  | 3D paste volume, CPK, defect count, pad-level data, board ID       | To MES        |
| JUKI FX-3R Pick-and-Place    | SECS/GEM              | CPH, feeder errors, nozzle state, placement count, recipe          | Bidirectional |
| JUKI RS-1 Flexible Mounter   | SECS/GEM              | CPH, feeder errors, placement accuracy trend, recipe               | Bidirectional |
| Heller 1964 MK5 Reflow Oven  | Modbus TCP or OPC-UA  | Zone temps ×10, conveyor speed, N₂ level, alarms, recipe          | Bidirectional |
| Mirtec MV-3L OMNI AOI        | REST API / SECS-II    | Defect codes, FPY per board, image reference, alarm state          | To MES        |
| Viscom S6056 X-Ray           | REST API              | BGA void analysis per joint, image, pass/fail per board            | To MES        |
| Ersa VERSAFLOW Selective Solder | OPC-UA             | Flux level, solder level, nozzle temp, wave height, recipe         | Bidirectional |
| Keysight I3070 ICT            | Ethernet API (AGENA3) | Net test pass/fail, short/open counts, fixture ID, serial          | To MES        |
| PCB Depanelling Router        | OPC-UA               | Cycle count, spindle speed, programme ID, alarm state              | To MES        |

### 6.2 Meter Assembly & Calibration Equipment Integration

| Equipment                              | Protocol        | Data Points                                                         | Direction     |
|----------------------------------------|-----------------|---------------------------------------------------------------------|---------------|
| Bosch Rexroth TS 4 Conveyor (×2 lines) | OPC-UA         | Belt speed, station queue depth, pallet ID scan, station status     | Bidirectional |
| Atlas Copco Torque Station (×8 ch)     | OPC-UA         | Torque (Nm), angle (°), OK/NOK per screw, sequence number           | To MES        |
| Branson DCX-S Ultrasonic Welder (×2)   | RS-232/OPC-UA  | Weld energy (J), amplitude (µm), depth (mm), alarm state            | To MES        |
| Firmware Flash Station (×8 units)      | REST API       | Serial number, firmware version, IMEI, flash result OK/NOK          | Bidirectional |
| IEC 62053 Calibration Bench Controller | RS-485/TCP     | Error % at 5/50/100/120% Irated, temp, reference ID, cert, pass/fail| To MES        |
| Gravimetric Water Test Rig (×2)        | Ethernet API   | Flow rate (L/min), reference mass (kg), meter reading, error %, pass/fail | To MES   |
| Nordson SelectCoat Conformal Coater    | OPC-UA         | Coating weight (g), UV cure temp, board ID, programme, alarm        | To MES        |
| 2-Component Potting Machine            | RS-232/OPC-UA  | Mix ratio, pot life timer, cure temp, batch ID, alarm               | To MES        |
| Press-Fit Station (×2)                 | OPC-UA         | Press force (kN), stroke (mm), OK/NOK per unit                      | To MES        |

### 6.3 Test & QC Equipment Integration

| Equipment                              | Protocol        | Data Points                                                         | Direction     |
|----------------------------------------|-----------------|---------------------------------------------------------------------|---------------|
| NB-IoT Module Test Fixture (×4)        | REST API       | RSSI, SINR, attach time, band, IMEI match, pass/fail                | To MES        |
| LoRa RF Test Bench (anechoic box)       | REST API       | RSSI at SF7-SF12, channel plan, sensitivity dBm, pass/fail          | To MES        |
| SEH Wi-Fi 6 / Zigbee Test Fixture (×4) | REST API       | Wi-Fi RSSI, Zigbee PAN join, BLE RSSI, test pass/fail               | To MES        |
| Salt Spray Chamber (Weiss Technik)     | OPC-UA         | Chamber temp, salt concentration, exposure time, part ID            | To MES        |
| Thermal Cycling Chamber               | OPC-UA         | Temp profile, cycle count, alarm, part ID                           | To MES        |
| Vibration Test Rig (IEC 60068-2-6)    | Ethernet API   | Frequency, amplitude, axis, duration, pass/fail                     | To MES        |
| Hipot / Safety Tester (Chroma 19036)  | Ethernet API   | Hipot voltage/current, earth bond, result, serial                   | To MES        |
| IP67/IP68 Immersion Test Tank (×2)    | RS-232         | Duration, depth, pass/fail, unit serial                             | To MES        |
| Mettler Toledo Checkweigher           | Ethernet API   | Weight (g), pass/fail vs. nominal, serial ref                       | To MES        |

---

## 7. AI Service API Integration

The Coo-Cah AI Platform exposes REST API endpoints consumed by the MES for AI-driven quality, calibration, and operational decisions.

### 7.1 SMT Defect Prediction API

**Endpoint:** `POST /api/v1/ai/smt-defect-predict`

**Request Payload:**
```json
{
  "factory_id": "CCE-LFZ-SMART-ESTATE",
  "line_id": "SMT_L1",
  "board_id": "PANEL-LFZ-2026-001-00321",
  "paste_volume_3d": {
    "mean_volume_percent": 97.8,
    "cpk": 1.38,
    "pads_inspected": 960,
    "pads_failed": 1
  },
  "reflow_profile": {
    "peak_temp_c": 246,
    "tac_time_s": 58,
    "zone_10_temp_c": 238,
    "conveyor_speed_mm_min": 880
  },
  "placement_data": {
    "total_components": 218,
    "placement_misses": 0,
    "feeder_errors": 1
  }
}
```

**Response:**
```json
{
  "prediction_id": "SMT-PRED-LFZ-20260101-00321",
  "defect_risk_score": 0.09,
  "risk_level": "LOW",
  "flagged_concerns": [
    {
      "concern": "FEEDER_ERROR_DETECTED",
      "severity": "LOW",
      "component_ref": "U4",
      "recommended_action": "VERIFY_PLACEMENT_VISION"
    }
  ],
  "recommended_action": "PROCEED_WITH_AOI_FOCUS",
  "model_version": "smt-predict-v2.3",
  "timestamp": "2026-01-01T08:14:22Z"
}
```

---

### 7.2 Meter Calibration AI API

**Endpoint:** `POST /api/v1/ai/meter-calibration`

**Request Payload:**
```json
{
  "unit_serial": "CCE-SM-ELEC-LFZ-26-001-000123",
  "sku": "CCE-SM-ELEC",
  "meter_class": "IEC62053-21-CLASS1",
  "calibration_results": {
    "error_5pct_irated": 0.42,
    "error_50pct_irated": 0.18,
    "error_100pct_irated": 0.11,
    "error_120pct_irated": 0.09,
    "temperature_c": 23.1,
    "reference_meter_id": "REF-STD-2026-003",
    "bench_id": "CAL-BENCH-2"
  },
  "imei": "860123456789012"
}
```

**Response:**
```json
{
  "unit_serial": "CCE-SM-ELEC-LFZ-26-001-000123",
  "calibration_status": "PASS",
  "nerc_compliance": "COMPLIANT",
  "iec62053_class": "CLASS_1",
  "max_error_observed_pct": 0.42,
  "certificate_number": "CERT-CCE-LFZ-2026-123456",
  "certificate_issued": "2026-01-01T09:01:05Z",
  "dispatch_cleared": true,
  "result_stored": true,
  "model_version": "meter-cal-v1.4",
  "timestamp": "2026-01-01T09:01:07Z"
}
```

---

### 7.3 Production OEE & Scheduling API

**Endpoint:** `GET /api/v1/mes/oee/realtime`

**Response:**
```json
{
  "factory_id": "CCE-LFZ-SMART-ESTATE",
  "timestamp": "2026-04-01T09:30:00Z",
  "oee_summary": {
    "factory_blended_oee": 0.762,
    "availability": 0.894,
    "performance": 0.881,
    "quality": 0.967
  },
  "lines": [
    {
      "line_id": "SMT_L1",
      "oee": 0.791,
      "status": "RUNNING",
      "current_product": "CCE-SM-ELEC-MAINBOARD",
      "units_completed_shift": 1840
    },
    {
      "line_id": "SMT_L2",
      "oee": 0.774,
      "status": "RUNNING",
      "current_product": "CCE-SM-WATER-PCB",
      "units_completed_shift": 1620
    },
    {
      "line_id": "METER-LINE-1",
      "oee": 0.748,
      "status": "RUNNING",
      "current_product": "CCE-SM-ELEC",
      "units_completed_shift": 612
    },
    {
      "line_id": "METER-LINE-2",
      "oee": 0.721,
      "status": "RUNNING",
      "current_product": "CCE-SM-ELEC",
      "units_completed_shift": 594
    },
    {
      "line_id": "CAL-BENCH-ARRAY",
      "oee": 0.883,
      "status": "RUNNING",
      "current_product": "CCE-SM-ELEC-CALIBRATION",
      "units_completed_shift": 192
    }
  ]
}
```

---

### 7.4 AMR Fleet Mission Dispatch API

**Endpoint:** `POST /api/v1/amr/dispatch`

**Request Payload:**
```json
{
  "mission_type": "WIP_TRANSFER",
  "source_zone": "SMT_L1_OUTPUT",
  "destination_zone": "METER_LINE_1_INPUT",
  "payload_description": "CCE-SM-ELEC Mainboards, Qty: 160, Tray-ID: TR-LFZ-2026-001-0089",
  "priority": "HIGH",
  "requested_by": "MES_AUTO",
  "work_order_id": "WO-LFZ-2026-001-0412"
}
```

**Response:**
```json
{
  "mission_id": "AMR-MISS-LFZ-20260101-0412",
  "assigned_amr_id": "MIR250-04",
  "estimated_completion_time": "2026-01-01T09:47:33Z",
  "status": "DISPATCHED",
  "timestamp": "2026-01-01T09:44:00Z"
}
```

---

## 8. MES Data Governance & Security

| Requirement                      | Implementation                                                                       |
|----------------------------------|--------------------------------------------------------------------------------------|
| Data Residency (NEPZA)           | All production, calibration, and NERC data stored on-site at LFTZ; cloud sync to Coo-Cah Platform (Lagos DC) for analytics only |
| NERC Calibration Data Retention  | Calibration records retained for **minimum 10 years** per NERC Meter Code requirement|
| NCC Audit Data Retention         | NCC RF test records retained for **minimum 5 years** per NCC requirement             |
| Encryption in Transit            | TLS 1.3 for all MES ↔ cloud, MES ↔ machine API, and MES ↔ external portal connections|
| Encryption at Rest               | AES-256 for all MES databases, calibration data archives, and NERC audit logs        |
| Role-Based Access Control        | Roles: Operator, Technician, Calibration Engineer, Supervisor, QA Auditor, Admin     |
| NERC Audit Report Access         | Only authorised NERC Auditor role can export full NERC audit reports                 |
| Backup                           | Daily incremental + weekly full backup; offsite copy to Coo-Cah Lagos DC             |
| IT/OT Network Segregation        | MES on OT VLAN; isolated from corporate IT; DMZ for ERP and portal integration       |
| Penetration Testing              | Annual third-party pen test; critical finding resolution within 30 days              |
| NEPZA Inspection Readiness       | MES can generate NEPZA production and employment reports on demand                   |

---

## 9. MES Integration with Cross-Factory Systems

| System                               | Integration Type           | Data Exchanged                                                       | Frequency      |
|--------------------------------------|----------------------------|----------------------------------------------------------------------|----------------|
| Coo-Cah ERP (SAP or equivalent)      | REST API / SAP RFC         | Production orders, BOM, inventory, costing, despatch notes           | Real-time      |
| Coo-Cah AI Platform                  | MQTT + REST API            | OEE, quality events, calibration alerts, energy, AI predictions      | Real-time      |
| Coo-Cah Plastics Factory MES         | REST API (factory link)    | Meter housing delivery schedule, WIP status, colour batch, ETA       | Hourly         |
| DisCo Head-End Systems (AMI)         | DLMS/COSEM interface       | Meter serial list, OBIS provisioning data, firmware version per batch| Per despatch   |
| NERC Meter Registry                  | CSV / portal submission    | Batch serial numbers, calibration cert refs, factory details         | Per batch      |
| NCC Type Approval Portal             | Manual + CSV export        | RF test summary reports for TA submission and renewal                | Per submission |
| MAP/NMMP Government Portal           | REST API (planned Phase 2) | Batch dispatch records, serial lists, DisCo PO linkage               | Per despatch   |
| Coo-Cah Distribution / WMS           | REST API                   | Finished goods despatch notes, serial lists, ASN                     | Per despatch   |
| Coo-Cah Digital Twin                 | MQTT (streaming)           | Real-time machine states, calibration bench status, WIP, energy flow | 1-second poll  |

---

*For digital twin architecture, refer to [`digital-twin.md`](./digital-twin.md).*
*For regulatory data requirements (NERC, NCC, NEPZA), refer to [`regulatory.md`](./regulatory.md).*
*For supply chain ERP integration, refer to [`supply-chain.md`](./supply-chain.md).*
