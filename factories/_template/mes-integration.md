# [FACTORY_NAME] — MES & AI Platform Integration Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** [FACTORY_NAME] | **Location:** [LOCATION] | **Phase:** [PHASE]
> **Document Version:** 1.0 | **Owner:** Coo-Cah Technology Division

---

## 1. Introduction

This document specifies the integration between [FACTORY_NAME] and the Coo-Cah Manufacturing Execution System (MES) and AI Platform. It defines:
- Data points collected from each machine and process
- API endpoints used for real-time data exchange
- Digital twin synchronisation specifications
- AI services consumed and their data schemas
- Security and connectivity requirements

The Coo-Cah MES is the operational system of record for all factory activity. The Coo-Cah AI Platform consumes MES data (and raw sensor data) to provide intelligence services back to the factory and to the central Coo-Cah Operations Centre.

---

## 2. System Architecture Overview

```
[FACTORY_NAME]
│
├── Shop Floor (OT Layer)
│   ├── Machines (OPC-UA / Modbus / Serial / Proprietary)
│   ├── IoT Sensors (MQTT over Wi-Fi/Ethernet)
│   ├── AMR Fleet (REST API / MQTT)
│   ├── EMS / SCADA (Modbus TCP / MQTT)
│   └── Vision Cameras (RTSP / REST)
│
├── Factory Edge Layer
│   ├── Industrial IoT Gateway(s) — OPC-UA aggregation, MQTT broker
│   ├── Edge Computing Node — local AI inference, data buffering
│   └── Factory Network Switch (managed, VLAN-segmented OT/IT)
│
├── Factory IT Layer
│   ├── MES Application Server (local or cloud)
│   ├── Local Database (time-series + relational)
│   └── Factory HMI / Panel PCs
│
└── Coo-Cah Platform (Cloud / Central)
    ├── Coo-Cah MES Core API
    ├── Coo-Cah AI Platform
    │   ├── Predictive Maintenance Service
    │   ├── Quality Yield Prediction Service
    │   ├── AI Scheduling Optimiser
    │   ├── Digital Twin Engine
    │   └── Energy Optimisation AI
    ├── Central Analytics & Reporting
    └── Cross-Factory Coordination Layer
```

---

## 3. MES Data Points

### 3.1 Machine Status Data

All production equipment is required to publish the following data points to the MES via the IoT Gateway. Data should update at minimum every 30 seconds (configurable per machine type).

| Data Point                  | Tag / Field Name         | Data Type | Unit       | Update Frequency | Source                     |
|-----------------------------|--------------------------|-----------|------------|------------------|----------------------------|
| Machine State               | `machine_state`          | Enum      | —          | On change        | OPC-UA: `ns=2;s=State`     |
| Alarm Active                | `alarm_active`           | Boolean   | —          | On change        | OPC-UA: `ns=2;s=Alarm`     |
| Alarm Code                  | `alarm_code`             | String    | —          | On change        | OPC-UA: `ns=2;s=AlarmCode` |
| Current Job ID              | `current_job_id`         | String    | —          | On change        | MES push / OPC-UA          |
| Cycle Time (last cycle)     | `cycle_time_last`        | Float     | seconds    | Per cycle        | OPC-UA / MES counter       |
| Parts Produced (shift)      | `parts_produced_shift`   | Integer   | units      | Per cycle        | OPC-UA counter             |
| Parts Rejected (shift)      | `parts_rejected_shift`   | Integer   | units      | Per cycle        | OPC-UA / QC system         |
| Motor Speed / RPM           | `motor_rpm`              | Float     | RPM        | 30 sec           | OPC-UA / sensor            |
| Vibration (RMS)             | `vibration_rms`          | Float     | mm/s       | 60 sec           | Vibration sensor (IoT)     |
| Temperature (bearing)       | `bearing_temp`           | Float     | °C         | 60 sec           | Thermocouple / IoT         |
| Power Consumption           | `power_kw`               | Float     | kW         | 30 sec           | Smart power meter          |
| Cumulative Run Hours        | `run_hours_total`        | Float     | hours      | 60 sec           | OPC-UA hour counter        |
| Tool Change Counter         | `tool_changes`           | Integer   | —          | On event         | OPC-UA                     |
| Maintenance Due Alert       | `maintenance_due`        | Boolean   | —          | On change        | MES PM module / OPC-UA     |

**Machine State Enum Values:**

| Code | State           | Description                                           |
|------|-----------------|-------------------------------------------------------|
| 0    | OFFLINE         | Machine not powered / not connected                   |
| 1    | IDLE            | Powered on, waiting for job                           |
| 2    | RUNNING         | Producing parts                                       |
| 3    | SETUP           | Job changeover / setup in progress                    |
| 4    | PLANNED_STOP    | Scheduled maintenance, break                          |
| 5    | UNPLANNED_STOP  | Breakdown / unscheduled downtime                      |
| 6    | ALARM           | Active alarm condition                                |

### 3.2 Production Count Data

| Data Point                  | Tag / Field Name           | Data Type | Unit    | Update Frequency | Notes                              |
|-----------------------------|----------------------------|-----------|---------|------------------|------------------------------------|
| Total Parts Produced        | `production_count_total`   | Integer   | units   | Per cycle        | Cumulative since last reset        |
| Shift Parts Produced        | `production_count_shift`   | Integer   | units   | Per cycle        | Resets at shift boundary           |
| Batch / Job Parts Produced  | `production_count_job`     | Integer   | units   | Per cycle        | Resets at job completion           |
| Scrap Count (shift)         | `scrap_count_shift`        | Integer   | units   | Per event        | Triggered by QC reject             |
| Rework Count (shift)        | `rework_count_shift`       | Integer   | units   | Per event        | Triggered by rework entry          |
| Target vs Actual Rate       | `production_rate_actual`   | Float     | units/hr | 5 min           | Compared to scheduled rate in MES  |
| Serial Numbers Produced     | `serials_produced[]`       | String[]  | —       | Per unit         | Array of serial/batch codes        |

### 3.3 Quality Data

Quality data originates from QC equipment (AOI, ICT, functional testers) and is linked to individual unit serial numbers in the MES.

| Data Point                  | Tag / Field Name           | Data Type | Unit    | Update Frequency | Notes                              |
|-----------------------------|----------------------------|-----------|---------|------------------|------------------------------------|
| IQC Result (batch)          | `iqc_result`               | Enum      | —       | Per batch        | PASS / FAIL / CONDITIONAL          |
| IPQC Result (unit)          | `ipqc_result`              | Enum      | —       | Per unit         | PASS / FAIL / REWORK               |
| FQC Result (unit)           | `fqc_result`               | Enum      | —       | Per unit         | PASS / FAIL / SCRAP                |
| Defect Code                 | `defect_code`              | String    | —       | Per defect event | Maps to defect library             |
| Defect Location (PCB)       | `defect_xy`                | JSON      | mm      | Per defect event | `{x: float, y: float, layer: int}` |
| AOI Image (defect)          | `aoi_image_url`            | String    | —       | Per defect event | URL to image stored in file system |
| ICT Test Result             | `ict_result_json`          | JSON      | —       | Per unit         | Full ICT report                    |
| Functional Test Result      | `ftest_result_json`        | JSON      | —       | Per unit         | Full test report                   |
| Visual Inspection Score     | `visual_score`             | Float     | 0–100   | Per unit         | AI vision quality score            |
| First-Pass Yield (shift)    | `fpy_shift`                | Float     | %       | 15 min           | Calculated: (pass-first-time/total)×100 |

---

## 4. API Endpoints

All Coo-Cah MES API endpoints follow REST conventions over HTTPS. Authentication uses OAuth 2.0 (client credentials flow) with factory-specific API keys. All payloads are JSON. API versioning: `/api/v1/`.

### 4.1 Production Order APIs

| Method | Endpoint                                   | Description                                        |
|--------|--------------------------------------------|---------------------------------------------------|
| GET    | `/api/v1/orders?factory=[ID]&status=active`| List all active production orders for factory     |
| GET    | `/api/v1/orders/{order_id}`                | Get details of a specific production order        |
| PATCH  | `/api/v1/orders/{order_id}/status`         | Update order status (e.g., STARTED, COMPLETED)    |
| POST   | `/api/v1/orders/{order_id}/events`         | Post production event (unit complete, defect, etc.)|
| GET    | `/api/v1/orders/{order_id}/progress`       | Real-time progress: produced vs target            |

### 4.2 Inventory & Material APIs

| Method | Endpoint                                   | Description                                        |
|--------|--------------------------------------------|---------------------------------------------------|
| POST   | `/api/v1/inventory/grn`                    | Create Goods Receipt Note (inbound materials)     |
| GET    | `/api/v1/inventory/stock?location=[LOC]`   | Check stock level at a location/bin               |
| POST   | `/api/v1/inventory/transfer`               | Record stock transfer (stores → line)             |
| POST   | `/api/v1/inventory/consume`                | Record component consumption against job          |
| GET    | `/api/v1/inventory/reorder-alerts`         | List materials at or below reorder point          |

### 4.3 Quality APIs

| Method | Endpoint                                   | Description                                        |
|--------|--------------------------------------------|---------------------------------------------------|
| POST   | `/api/v1/quality/iqc`                      | Submit IQC inspection result                      |
| POST   | `/api/v1/quality/ipqc`                     | Submit IPQC result for a unit                     |
| POST   | `/api/v1/quality/fqc`                      | Submit FQC final test result for a unit           |
| POST   | `/api/v1/quality/defect`                   | Log defect event (code, location, image)          |
| GET    | `/api/v1/quality/serial/{serial}/history`  | Full quality history for a unit serial number     |
| GET    | `/api/v1/quality/spc/{process_id}`         | SPC control chart data for a process              |

### 4.4 Machine & OEE APIs

| Method | Endpoint                                   | Description                                        |
|--------|--------------------------------------------|---------------------------------------------------|
| POST   | `/api/v1/machines/{machine_id}/state`      | Push machine state change event                   |
| POST   | `/api/v1/machines/{machine_id}/telemetry`  | Push telemetry data payload                       |
| GET    | `/api/v1/machines/{machine_id}/oee`        | Get current OEE breakdown (A, P, Q)               |
| POST   | `/api/v1/machines/{machine_id}/alarm`      | Log alarm event                                   |
| GET    | `/api/v1/maintenance/workorders?machine=[ID]` | List open maintenance work orders               |
| POST   | `/api/v1/maintenance/workorders`           | Create maintenance work order                     |

### 4.5 Energy APIs

| Method | Endpoint                                   | Description                                        |
|--------|--------------------------------------------|---------------------------------------------------|
| POST   | `/api/v1/energy/meter`                     | Push energy meter reading                         |
| GET    | `/api/v1/energy/summary?date=[DATE]`       | Daily energy summary (solar, BESS, grid, diesel)  |
| GET    | `/api/v1/energy/forecast?hours=24`         | AI-generated 24h energy demand forecast           |
| PATCH  | `/api/v1/energy/load-shedding`             | Trigger/clear load shedding tier                  |

### 4.6 AMR Fleet APIs

| Method | Endpoint                                   | Description                                        |
|--------|--------------------------------------------|---------------------------------------------------|
| POST   | `/api/v1/amr/{amr_id}/task`               | Assign transport task to AMR                      |
| GET    | `/api/v1/amr/{amr_id}/status`             | Get AMR status, location, battery SoC             |
| GET    | `/api/v1/amr/fleet/status`                | Fleet-wide status summary                         |
| POST   | `/api/v1/amr/fleet/e-stop`                | Emergency stop all AMRs                           |
| GET    | `/api/v1/amr/{amr_id}/route-history`      | AMR route history (last 8 hours)                  |

---

## 5. Digital Twin Synchronisation

### 5.1 Sync Architecture

```
Factory Edge Node
  │ (MQTT / OPC-UA aggregation)
  ▼
Coo-Cah Digital Twin Engine
  ├── Asset State Service  — receives real-time telemetry, updates asset state
  ├── 3D Model Renderer    — maps state to 3D factory visualisation
  ├── Physics Simulator    — runs what-if scenarios
  └── Anomaly Detector     — flags DT vs Reality divergence
```

### 5.2 Digital Twin Sync Parameters

| Parameter                      | Value                                               |
|--------------------------------|-----------------------------------------------------|
| Sync Protocol                  | MQTT (telemetry) + REST (batch updates)             |
| Telemetry Sync Frequency       | 5 seconds (critical assets), 30 seconds (others)   |
| Asset State Sync Frequency     | On change + 30-second heartbeat                     |
| Production Count Sync          | Per unit / per batch                                |
| Energy Data Sync               | 30 seconds                                          |
| AMR Position Sync              | 1 second                                            |
| QC Results Sync                | On event (immediate)                                |
| DT vs Reality Divergence Alert | When DT state differs from reported state > 60 sec  |
| Historical Data Retention      | 90 days in DT engine; 7 years in MES database       |
| Simulation Runs (on demand)    | Ad hoc — 10-minute simulation completes in < 2 min  |

---

## 6. AI Services Consumed

### 6.1 Predictive Maintenance Service

| Attribute           | Detail                                                      |
|---------------------|-------------------------------------------------------------|
| Service Name        | `coo-cah-ai.predictive-maintenance`                         |
| Input Data          | Vibration RMS, bearing temperature, run hours, alarm history|
| Model Type          | Gradient boosted tree (time-series feature extraction)      |
| Output              | Failure probability (0–1.0) per asset, per 24h window       |
| Alert Threshold     | Failure probability ≥ 0.70 → MES maintenance work order     |
| Retraining Freq.    | Weekly on rolling 90-day data window                        |
| Monitored Assets    | [LIST_OF_CRITICAL_MACHINES]                                 |
| API Endpoint        | `POST /ai/v1/pred-maintenance/infer`                        |

**Input Schema:**

```json
{
  "asset_id": "string",
  "factory_id": "string",
  "timestamp": "ISO8601",
  "vibration_rms": 2.34,
  "bearing_temp": 68.2,
  "run_hours_total": 4521.5,
  "alarm_count_30d": 3,
  "last_maintenance_hrs": 450.0
}
```

**Output Schema:**

```json
{
  "asset_id": "string",
  "failure_probability_24h": 0.83,
  "failure_probability_72h": 0.91,
  "recommended_action": "Schedule maintenance within 24 hours",
  "top_contributing_factors": ["bearing_temp_trend", "vibration_rms_spike"],
  "model_version": "2.1.4",
  "inference_timestamp": "ISO8601"
}
```

### 6.2 Yield Prediction Service

| Attribute           | Detail                                                           |
|---------------------|------------------------------------------------------------------|
| Service Name        | `coo-cah-ai.yield-prediction`                                    |
| Input Data          | Process parameters, input material IQC scores, environmental    |
| Model Type          | Neural network regression                                        |
| Output              | Predicted first-pass yield (%) for next [N] units / current job |
| Alert Threshold     | Predicted yield ≤ 90% → alert production supervisor              |
| Retraining Freq.    | Monthly on rolling 6-month data window                           |
| API Endpoint        | `POST /ai/v1/yield-prediction/infer`                            |

### 6.3 AI Scheduling Optimiser

| Attribute           | Detail                                                           |
|---------------------|------------------------------------------------------------------|
| Service Name        | `coo-cah-ai.scheduling`                                          |
| Input Data          | Demand plan, machine availability, raw material stock levels     |
| Model Type          | Genetic algorithm + constraint programming                       |
| Output              | Optimised production schedule (job-machine-time assignments)     |
| Optimisation Goals  | Minimise changeover time, maximise OEE, meet delivery dates      |
| Run Frequency       | Daily (06:00) + on-demand re-plan                                |
| API Endpoint        | `POST /ai/v1/scheduling/optimise`                                |

### 6.4 Energy Optimisation AI

| Attribute           | Detail                                                           |
|---------------------|------------------------------------------------------------------|
| Service Name        | `coo-cah-ai.energy-optimisation`                                 |
| Input Data          | Production schedule, weather forecast, current BESS SoC, tariffs|
| Output              | Optimal load scheduling, BESS charge/discharge plan              |
| Update Frequency    | Every 15 minutes (rolling 24h horizon)                           |
| API Endpoint        | `GET /ai/v1/energy/dispatch-plan`                                |

---

## 7. Data Security & Connectivity

| Requirement                    | Specification                                              |
|--------------------------------|------------------------------------------------------------|
| Network Segmentation           | OT network (machines) isolated from IT via firewall/VLAN  |
| Data in Transit                | TLS 1.3 for all API calls and MQTT connections             |
| Data at Rest                   | AES-256 encryption for stored production and quality data  |
| Authentication                 | OAuth 2.0 client credentials; API keys rotated quarterly   |
| Access Control                 | Role-based (Operator, Supervisor, Engineer, Admin)         |
| Audit Logging                  | All API calls and data modifications logged; 12-month retention |
| OT/IT Connectivity             | Industrial DMZ with application-layer firewall for OPC-UA  |
| Disaster Recovery              | MES data backed up to off-site cloud every 4 hours         |
| Incident Response              | ISO/IEC 27001-aligned procedures; CISO notified within 1h  |

---

*For digital twin asset registry, refer to [`digital-twin.md`](./digital-twin.md).*
*For automation phasing of MES features, refer to [`automation-roadmap.md`](./automation-roadmap.md).*
