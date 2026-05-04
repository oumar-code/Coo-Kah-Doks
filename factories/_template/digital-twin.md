# [FACTORY_NAME] — Digital Twin Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** [FACTORY_NAME] | **Location:** [LOCATION] | **Phase:** [PHASE]
> **Document Version:** 1.0 | **Owner:** Coo-Cah Technology Division — Digital Twin Team

---

## 1. Introduction

The Coo-Cah Digital Twin (DT) is a real-time, physics-aware virtual replica of [FACTORY_NAME]. It synchronises live operational data from machines, sensors, AMRs, energy systems, and environmental monitors to provide a continuously updated digital representation of the physical factory. The DT enables predictive simulation, scenario planning, and AI-driven optimisation that would be impossible with only physical observations.

**Digital Twin Objectives:**
1. Provide real-time visualisation of factory state (machine states, WIP, energy, AMR positions)
2. Enable predictive simulation — "what-if" production planning without physical risk
3. Detect anomalies by comparing DT prediction against actual sensor readings
4. Train and validate AI models against simulated data before live deployment
5. Support remote expert review and troubleshooting without physical site visits
6. Serve as the master asset registry for maintenance and compliance

---

## 2. Digital Twin Architecture

```
Physical Factory
    │ Sensors, OPC-UA, MQTT, REST
    ▼
Edge Computing Node (Factory)
    │ Data aggregation, buffering, local inference
    ▼
Coo-Cah Digital Twin Engine (Cloud)
    ├── Asset State Service
    │     └── Manages real-time state of every registered asset
    ├── 3D Visualisation Engine
    │     └── Photorealistic factory model (Unity/Unreal or custom)
    ├── Physics Simulation Engine
    │     └── Kinematics, thermal, fluid dynamics for scenario modelling
    ├── Time-Series Data Store
    │     └── InfluxDB / TimescaleDB — all sensor readings with timestamp
    ├── Anomaly Detection Service
    │     └── DT vs Reality delta monitoring
    ├── Scenario Planner
    │     └── What-if simulations on request
    └── Digital Twin API
          └── Serves MES, AI Platform, Operations Centre, external clients
```

---

## 3. Asset Registry

All physical assets within [FACTORY_NAME] are registered in the Digital Twin Asset Registry. Each asset has a unique DT Asset ID, physical tag (QR/RFID), and a data model defining its monitored attributes.

### 3.1 Production Equipment Assets

| DT Asset ID        | Physical Asset Name          | Asset Type       | Location (Zone) | DT Model Type   | Sensor Count | Integration Method  | DT Status     |
|--------------------|------------------------------|------------------|-----------------|-----------------|--------------|---------------------|---------------|
| DT-[FAC]-PE-001    | [MACHINE_NAME_1]             | Production       | PLA             | Kinematic + Thermal | [N]      | OPC-UA              | [ACTIVE/PLANNED] |
| DT-[FAC]-PE-002    | [MACHINE_NAME_2]             | Production       | PLA             | State Machine   | [N]          | OPC-UA              | [STATUS]      |
| DT-[FAC]-PE-003    | [MACHINE_NAME_3]             | Production       | PLB             | State Machine   | [N]          | MQTT IoT GW         | [STATUS]      |
| DT-[FAC]-PE-004    | [MACHINE_NAME_4]             | Production       | PLB             | State Machine   | [N]          | Modbus TCP          | [STATUS]      |
| DT-[FAC]-PE-005    | [MACHINE_NAME_5]             | Production       | PLC             | Thermal         | [N]          | OPC-UA              | [STATUS]      |
| DT-[FAC]-PE-006    | [MACHINE_NAME_6]             | Production       | PLC             | State Machine   | [N]          | MQTT                | [STATUS]      |

### 3.2 Quality Control Equipment Assets

| DT Asset ID        | Physical Asset Name          | Asset Type       | Zone   | DT Model Type   | Integration Method  |
|--------------------|------------------------------|------------------|--------|-----------------|---------------------|
| DT-[FAC]-QC-001    | AOI Machine ([MODEL])        | QC               | IPQC   | Vision + State  | OPC-UA + Image API  |
| DT-[FAC]-QC-002    | ICT Test System              | QC               | IPQC   | State Machine   | REST API            |
| DT-[FAC]-QC-003    | Functional Test Station A    | QC               | FQC    | State Machine   | MQTT                |
| DT-[FAC]-QC-004    | Hipot / Safety Tester        | QC               | FQC    | State Machine   | RS-232 → MQTT GW    |
| DT-[FAC]-QC-005    | CMM (if applicable)          | QC               | IQC    | Geometric       | OPC-UA              |

### 3.3 AMR Fleet Assets

| DT Asset ID        | AMR Unit ID  | AMR Model        | Zone Coverage      | DT Model Type   | Update Frequency | Integration |
|--------------------|--------------|------------------|--------------------|-----------------|------------------|-------------|
| DT-[FAC]-AMR-001   | AMR-01       | [MODEL]          | RMS, STG, PLA      | Mobile Agent    | 1 second         | AMR REST API |
| DT-[FAC]-AMR-002   | AMR-02       | [MODEL]          | RMS, STG, PLB      | Mobile Agent    | 1 second         | AMR REST API |
| DT-[FAC]-AMR-003   | AMR-03       | [MODEL]          | STG, PLA, IPQC     | Mobile Agent    | 1 second         | AMR REST API |
| DT-[FAC]-AMR-004   | AMR-04       | [MODEL]          | STG, PLB, PLC      | Mobile Agent    | 1 second         | AMR REST API |
| DT-[FAC]-AMR-005   | AMR-05       | [MODEL]          | IPQC, FQC, PKG     | Mobile Agent    | 1 second         | AMR REST API |
| DT-[FAC]-AMR-006   | AMR-06       | [MODEL]          | PKG, FGW           | Mobile Agent    | 1 second         | AMR REST API |
| DT-[FAC]-AMR-007   | AMR-07       | [MODEL]          | FGW, LD-OUT        | Mobile Agent    | 1 second         | AMR REST API |

### 3.4 Energy System Assets

| DT Asset ID        | Physical Asset                 | Asset Type   | DT Model Type       | Update Frequency | Integration     |
|--------------------|--------------------------------|--------------|---------------------|------------------|-----------------|
| DT-[FAC]-EN-001    | Solar PV Array — Zone A        | Generation   | Power Curve Model   | 30 seconds       | EMS MQTT        |
| DT-[FAC]-EN-002    | Solar PV Array — Zone B        | Generation   | Power Curve Model   | 30 seconds       | EMS MQTT        |
| DT-[FAC]-EN-003    | LFP BESS System                | Storage      | Electrochemical     | 30 seconds       | BMS MQTT        |
| DT-[FAC]-EN-004    | Hybrid Inverter / PCS          | Power Conv.  | State Machine       | 30 seconds       | EMS Modbus TCP  |
| DT-[FAC]-EN-005    | Grid Connection                | Supply       | State + Load        | 30 seconds       | Smart Meter API |
| DT-[FAC]-EN-006    | Diesel Generator               | Backup       | State Machine       | 60 seconds       | Generator SCADA |
| DT-[FAC]-EN-007    | Factory Main MCC               | Distribution | Electrical Model    | 30 seconds       | Power Analyser  |

### 3.5 Environmental & Building Assets

| DT Asset ID        | Physical Asset                 | Asset Type   | DT Model Type       | Update Frequency | Integration     |
|--------------------|--------------------------------|--------------|---------------------|------------------|-----------------|
| DT-[FAC]-ENV-001   | HVAC — Production Zone         | Climate      | Thermal Fluid       | 60 seconds       | BMS BACNET      |
| DT-[FAC]-ENV-002   | HVAC — Cleanroom (if present)  | Climate      | Thermal Fluid       | 10 seconds       | BMS BACNET      |
| DT-[FAC]-ENV-003   | Air Compressor                 | Utilities    | Pressure State      | 60 seconds       | MQTT IoT Sensor |
| DT-[FAC]-ENV-004   | Fire Alarm System              | Safety       | State/Zone Map      | On event         | BACnet/IT       |
| DT-[FAC]-ENV-005   | Access Control System          | Security     | State per door      | On event         | REST API        |

---

## 4. Sensor Coverage Map

### 4.1 Sensor Types Deployed

| Sensor Type               | Quantity | Monitored Asset Type          | Measurement          | Protocol    | Calibration Freq. |
|---------------------------|----------|-------------------------------|----------------------|-------------|-------------------|
| Vibration Sensor          | [N]      | Rotating machinery (motors, pumps) | RMS velocity (mm/s) | MQTT        | Annual            |
| Thermocouple / RTD        | [N]      | Machine bearings, ovens, BESS | Temperature (°C)     | MQTT / OPC  | Annual            |
| Current Transducer (CT)   | [N]      | All major machines            | Power (kW), current  | Modbus TCP  | Annual            |
| Pressure Transducer       | [N]      | Compressed air system         | Pressure (bar)       | MQTT        | Annual            |
| Ultrasonic Level Sensor   | [N]      | Diesel tank, chemical tanks   | Level (%)            | MQTT        | Annual            |
| Environmental (Temp/RH)   | [N]      | All production zones          | Temp + Humidity      | MQTT (BLE or Wired) | Bi-annual  |
| CO₂ Sensor                | [N]      | Production and office zones   | CO₂ (ppm)            | MQTT        | Bi-annual         |
| Particulate (PM2.5/PM10)  | [N]      | Soldering/machining areas     | PM2.5, PM10 (µg/m³)  | MQTT        | Annual            |
| Photoelectric (Line Speed)| [N]      | Conveyor lines                | Part count / speed   | OPC-UA      | Per maintenance   |
| CMOS Camera (AI Vision)   | [N]      | AOI/QC stations, entry gates  | Image → AI analysis  | RTSP/REST   | Per maintenance   |
| GPS/LiDAR (AMR)           | [N]      | AMR fleet                     | Position (x,y,θ)     | AMR API     | Per maintenance   |

### 4.2 Sensor Density by Zone

| Zone          | Vibration | Temp | Power | Environmental | Vision | AMR Location |
|---------------|-----------|------|-------|---------------|--------|--------------|
| PLA (Line A)  | [N]       | [N]  | [N]   | [N]           | [N]    | Continuous   |
| PLB (Line B)  | [N]       | [N]  | [N]   | [N]           | [N]    | Continuous   |
| PLC (Line C)  | [N]       | [N]  | [N]   | [N]           | [N]    | Continuous   |
| IPQC          | [N]       | [N]  | [N]   | [N]           | [N]    | Continuous   |
| FQC           | [N]       | [N]  | [N]   | [N]           | [N]    | Continuous   |
| RMS (Stores)  | 0         | [N]  | 0     | [N]           | [N]    | Continuous   |
| FGW (Warehouse)| 0        | [N]  | 0     | [N]           | [N]    | Continuous   |
| Energy Room   | [N]       | [N]  | [N]   | [N]           | 0      | 0            |

---

## 5. Real-Time Data Points

The following is the complete list of real-time data points maintained in the DT and available via the DT API:

| # | Data Point Category          | Example Fields                                            | Update Rate   | Retention Period |
|---|------------------------------|-----------------------------------------------------------|---------------|-----------------|
| 1 | Machine State                | `state`, `alarm_code`, `current_job`, `shift_count`       | On change     | 7 years          |
| 2 | Machine Telemetry            | `rpm`, `vibration`, `bearing_temp`, `power_kw`            | 30 sec        | 2 years (raw); 7 years (aggregated) |
| 3 | Production Counts            | `produced`, `rejected`, `rework`, `fpy`                   | Per cycle     | 7 years          |
| 4 | Quality Data                 | `iqc_result`, `fqc_result`, `defect_code`, `serial`       | Per unit      | 7 years          |
| 5 | AMR Position & Status        | `x`, `y`, `theta`, `battery_soc`, `task_id`, `speed`      | 1 second      | 30 days (raw); 1 year (events) |
| 6 | Energy Data                  | `solar_kw`, `bess_soc`, `grid_kw`, `total_factory_kw`     | 30 seconds    | 10 years         |
| 7 | Environmental Data           | `temp_zone_X`, `humidity_zone_X`, `co2_ppm`, `pm2.5`      | 60 seconds    | 5 years          |
| 8 | WIP Location                 | `serial`, `current_zone`, `station`, `timestamp`          | Per scan      | 7 years          |
| 9 | Maintenance Events           | `work_order_id`, `machine`, `type`, `duration`, `cause`   | On event      | 10 years         |
| 10| Alarm History                | `machine_id`, `alarm_code`, `start`, `end`, `resolution`  | On event      | 7 years          |

---

## 6. Simulation Use Cases

### 6.1 Production Planning Simulation

**Use Case:** Before committing to a new production schedule, simulate the plan against the DT to identify bottlenecks, machine conflicts, and material shortages.

| Input                            | Output                                    | Trigger                       |
|----------------------------------|-------------------------------------------|-------------------------------|
| Proposed production schedule     | Predicted OEE per line, bottleneck IDs    | AI Scheduler pre-validation   |
| Machine maintenance windows      | Schedule conflicts identified             | Daily scheduling run          |
| Material availability            | Risk of line starvation identified        | Daily scheduling run          |

### 6.2 Predictive Maintenance Simulation

**Use Case:** Simulate the effect of scheduling maintenance at different times to find the optimal window that minimises production loss.

| Input                            | Output                                    | Trigger                       |
|----------------------------------|-------------------------------------------|-------------------------------|
| Predicted failure probability    | Optimal maintenance window               | PdM alert (prob. ≥ 0.70)      |
| Production schedule              | Production loss per proposed window       | On demand                     |

### 6.3 Energy Optimisation Simulation

**Use Case:** Simulate load scheduling and BESS dispatch for the next 24 hours, optimising for minimum grid import and maximum solar utilisation.

| Input                            | Output                                    | Trigger                       |
|----------------------------------|-------------------------------------------|-------------------------------|
| Weather forecast (solar irradiance) | Optimal BESS charge/discharge plan     | Every 15 minutes              |
| Production load forecast         | Load shedding recommendations            | Every 15 minutes              |
| BESS SoC                         | Predicted grid import (kWh, cost)         | Every 15 minutes              |

### 6.4 Throughput Improvement Simulation

**Use Case:** Evaluate the impact of adding a new machine, changing shift patterns, or rebalancing workstations on throughput and OEE.

| Input                            | Output                                    | Trigger                       |
|----------------------------------|-------------------------------------------|-------------------------------|
| Proposed layout / equipment change | Predicted new throughput, OEE           | On demand (Engineering)       |
| New shift pattern                | Labour vs output trade-off analysis       | On demand (Planning)          |

### 6.5 Incident Response Simulation

**Use Case:** Following a production incident, replay the DT state to reconstruct the sequence of events, supporting root cause analysis without relying on memory.

| Input                            | Output                                    | Trigger                       |
|----------------------------------|-------------------------------------------|-------------------------------|
| Incident time window             | Full state replay: machines, AMRs, energy | Post-incident (QA/Maintenance)|
| Sensor data from incident period | Timeline of events; anomaly identified    | RCA investigation             |

---

## 7. Integration with AI Platform

The DT feeds data to and receives intelligence from the Coo-Cah AI Platform as follows:

| AI Service                   | Data FROM DT                                      | Intelligence TO DT / MES                         |
|------------------------------|---------------------------------------------------|--------------------------------------------------|
| Predictive Maintenance       | Vibration, temp, run hours (all assets)           | Failure probability per asset; maintenance alert |
| Yield Prediction             | Process parameters, machine states, env. data     | Predicted FPY for current job                    |
| Scheduling Optimiser         | Machine availability, WIP, material stock         | Optimised schedule; bottleneck flags             |
| Energy Optimisation AI       | Solar gen, BESS SoC, load data, weather forecast  | Load dispatch plan; BESS charge schedule         |
| Anomaly Detection            | All sensor streams                                | Anomaly alerts (deviation from DT prediction)    |
| Computer Vision QC           | Camera feeds from AOI and inline cameras          | Defect classification, coordinates, severity     |

---

## 8. Update Frequency and Data Retention Policy

| Data Category              | Live Update Frequency | Hot Storage (Fast Query) | Cold Storage (Archive) | Deletion Policy                 |
|----------------------------|-----------------------|--------------------------|------------------------|---------------------------------|
| Machine telemetry (raw)    | 30 seconds            | 90 days                  | 2 years                | Archive to cold after 90 days   |
| Machine state events       | On change             | 1 year                   | 7 years                | Retain for compliance 7 years   |
| Production records         | Per cycle / per unit  | 2 years                  | 7 years                | Legal minimum 7 years           |
| Quality records (serial)   | Per unit              | 2 years                  | 10 years               | Product liability minimum 10 yr |
| Energy data                | 30 seconds            | 1 year                   | 10 years               | Carbon accounting 10 years      |
| AMR position (raw)         | 1 second              | 7 days                   | 1 year                 | Aggregate after 7 days          |
| Environmental data         | 60 seconds            | 1 year                   | 5 years                | NESREA monitoring 5 years       |
| Maintenance records        | On event              | 3 years                  | 10 years               | Asset lifecycle records 10 yr   |
| DT simulation runs         | On demand             | 30 days                  | 6 months               | Purge after 6 months            |

---

## 9. Digital Twin Governance

| Role                        | Responsibility                                                         |
|-----------------------------|------------------------------------------------------------------------|
| DT Asset Owner (per asset)  | Ensures asset data is accurate, sensors calibrated, integration active |
| Factory IT / MES Admin      | Manages factory-side connectivity, gateway health                      |
| Coo-Cah DT Platform Team    | DT engine maintenance, model updates, simulation quality               |
| QA Manager                  | Validates DT quality data accuracy vs physical QC records              |
| AI Platform Team            | Trains and deploys AI models consuming DT data                         |
| CISO / Security Team        | Governs data access, encryption, API security                          |

---

*For asset sensor specifications, refer to [`machinery.md`](./machinery.md).*
*For AI service API specifications, refer to [`mes-integration.md`](./mes-integration.md).*
*For energy asset details, refer to [`energy-profile.md`](./energy-profile.md).*
