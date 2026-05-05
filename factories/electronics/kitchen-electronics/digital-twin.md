# Kitchen Electronics Factory — Digital Twin Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Kitchen Electronics Factory | **Location:** Agbara Industrial Estate, Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Coo-Cah Technology Division — Digital Twin Team

---

## 1. Introduction

The Coo-Cah Digital Twin for the Kitchen Electronics Factory provides a real-time, physics-aware virtual replica of all production assets — from the SMT PCB line through to the refrigerator foam injection carousel, compressor test rigs, and SDA assembly conveyors. The digital twin is uniquely important here because of the complex thermal processes (reflow ovens, PU foam curing, compressor performance testing) and the safety-critical R600a refrigerant charging stations, where simulation of failure scenarios is essential before live deployment.

**Digital Twin Objectives:**
1. Real-time visualisation of factory state across all product lines
2. Simulation of thermal process parameters (foam injection, reflow, compressor test)
3. Safety simulation of R600a gas charging scenarios — leak detection response models
4. Predictive maintenance targeting: foam injection carousel, SMT reflow oven, compressor test rigs
5. Energy optimisation simulation — large foam injection machine creates significant peak load events
6. Training new operators on dangerous processes (gas charging) via simulated environment

---

## 2. Digital Twin Architecture

```
Physical Factory (Agbara Industrial Estate)
    │ Sensors, OPC-UA, MQTT, REST
    ▼
Edge Computing Node (Factory)
    │ Data aggregation, buffering, local inference
    ▼
Coo-Cah Digital Twin Engine (Cloud / Rwanda HQ)
    ├── Asset State Service — SMT line, fridge line, SDA lines, energy
    ├── Thermal Physics Engine — foam curing model, reflow profile simulation
    ├── Gas Safety Simulation — R600a leak dispersion model
    ├── Time-Series Data Store — InfluxDB all sensor readings
    ├── Anomaly Detection — DT vs Reality delta monitoring
    ├── Energy Load Predictor — foam injection peak load forecasting
    └── Digital Twin API — serves MES, AI Platform, Safety team
```

---

## 3. Asset Registry

### 3.1 Production Equipment Assets — SMT Line

| DT Asset ID      | Physical Asset                 | Zone  | DT Model Type      | Sensor Count | Integration     | DT Status |
|------------------|--------------------------------|-------|--------------------|--------------|-----------------|-----------|
| DT-KIT-PE-001    | DEK Horizon Paste Printer      | SMT   | State + Thermal    | 8            | OPC-UA          | Planned   |
| DT-KIT-PE-002    | JUKI RX-7R Pick-and-Place #1   | SMT   | Kinematic + State  | 12           | OPC-UA          | Planned   |
| DT-KIT-PE-003    | JUKI RX-7R Pick-and-Place #2   | SMT   | Kinematic + State  | 12           | OPC-UA          | Planned   |
| DT-KIT-PE-004    | Heller 1964 MK5 Reflow Oven    | SMT   | Multi-Zone Thermal | 28           | OPC-UA          | Planned   |
| DT-KIT-PE-005    | Koh Young AOI KY8030-3         | SMT   | Vision + State     | 6            | OPC-UA + REST   | Planned   |

### 3.2 Production Equipment Assets — Refrigerator Line

| DT Asset ID      | Physical Asset                      | Zone  | DT Model Type          | Sensor Count | Integration     | DT Status |
|------------------|-------------------------------------|-------|------------------------|--------------|-----------------|-----------|
| DT-KIT-RF-001    | PU Foam Injection Machine (carousel) | FOAM  | Thermal + Kinematic    | 24           | OPC-UA + MQTT   | Planned   |
| DT-KIT-RF-002    | R600a Gas Charging Station #1        | GAS   | Pressure + Gas Conc.   | 18           | OPC-UA          | Planned   |
| DT-KIT-RF-003    | R600a Gas Charging Station #2        | GAS   | Pressure + Gas Conc.   | 18           | OPC-UA          | Planned   |
| DT-KIT-RF-004    | Vacuum Station (leak test)           | GAS   | Pressure State         | 10           | MQTT            | Planned   |
| DT-KIT-RF-005    | Compressor Performance Test Rig      | FQC   | Thermal + Vibration    | 20           | OPC-UA          | Planned   |
| DT-KIT-RF-006    | Cabinet Roll-Form + Welding Line     | FAB   | Kinematic + State      | 14           | MQTT IoT GW     | Planned   |

### 3.3 AMR Fleet Assets

| DT Asset ID      | AMR Unit ID | AMR Model | Zone Coverage         | Update Freq. | Integration  |
|------------------|-------------|-----------|---------------------- |--------------|--------------|
| DT-KIT-AMR-001   | AMR-01      | MiR200    | RMS, STG, FRIDGE LINE | 1 second     | AMR REST API |
| DT-KIT-AMR-002   | AMR-02      | MiR200    | RMS, STG, FRIDGE LINE | 1 second     | AMR REST API |
| DT-KIT-AMR-003   | AMR-03      | MiR200    | STG, SDA-A, SDA-B     | 1 second     | AMR REST API |
| DT-KIT-AMR-004   | AMR-04      | MiR200    | STG, SDA-C, IPQC      | 1 second     | AMR REST API |
| DT-KIT-AMR-005   | AMR-05      | MiR200    | IPQC, FQC, PKG        | 1 second     | AMR REST API |
| DT-KIT-AMR-006   | AMR-06      | MiR200    | PKG, FGW              | 1 second     | AMR REST API |
| DT-KIT-AMR-007   | AMR-07      | MiR100    | SMT zone kitting      | 1 second     | AMR REST API |
| DT-KIT-AMR-008   | AMR-08      | MiR100    | Consumable replenish  | 1 second     | AMR REST API |

### 3.4 Energy System Assets

| DT Asset ID      | Physical Asset                | DT Model Type     | Update Freq. | Integration    |
|------------------|-------------------------------|-------------------|--------------|----------------|
| DT-KIT-EN-001    | Solar PV Array — Main Roof    | Power Curve Model | 30 seconds   | EMS MQTT       |
| DT-KIT-EN-002    | LFP BESS 800 kWh              | Electrochemical   | 30 seconds   | BMS MQTT       |
| DT-KIT-EN-003    | Hybrid Inverter / PCS         | State Machine     | 30 seconds   | EMS Modbus TCP |
| DT-KIT-EN-004    | Grid Connection               | State + Load      | 30 seconds   | Smart Meter    |
| DT-KIT-EN-005    | Perkins 500 kVA Generator     | State Machine     | 60 seconds   | Generator SCADA|
| DT-KIT-EN-006    | Foam Injection Load Monitor   | Demand Spikes     | 5 seconds    | Power Analyser |

### 3.5 Gas Safety Assets (R600a)

| DT Asset ID      | Physical Asset                     | DT Model Type       | Update Freq. | Integration    |
|------------------|------------------------------------|---------------------|--------------|----------------|
| DT-KIT-GAS-001   | R600a Gas Detector Array (12 pts)  | Concentration Map   | 10 seconds   | Gas Ctrl Panel |
| DT-KIT-GAS-002   | Refrigerant Storage Cylinder Bay   | Inventory + Safety  | 60 seconds   | MQTT Sensor    |
| DT-KIT-GAS-003   | Gas Charging Zone Ventilation      | Airflow State       | 30 seconds   | BMS BACnet     |

---

## 4. Sensor Coverage Map

| Sensor Type               | Quantity | Primary Asset Type                        | Protocol    |
|---------------------------|----------|-------------------------------------------|-------------|
| Vibration Sensor          | 32       | Carousel, compressor, motors              | MQTT        |
| Thermocouple / RTD        | 58       | Reflow oven zones, foam barrel, BESS      | OPC-UA/MQTT |
| Current Transducer (CT)   | 28       | All major machines + foam injection       | Modbus TCP  |
| Pressure Transducer       | 22       | Gas charging, vacuum, compressed air      | MQTT        |
| Gas Concentration (R600a) | 12       | Gas charging zone (Zone GAS)              | RS-485/MQTT |
| Environmental (Temp/RH)   | 18       | All production zones                      | MQTT BLE    |
| Photoelectric             | 20       | Conveyor lines, overhead chain conveyor   | OPC-UA      |
| CMOS Camera (AI Vision)   | 16       | AOI, cabinet visual QC, entry points      | RTSP/REST   |
| GPS/LiDAR (AMR)           | 8        | AMR fleet                                 | AMR API     |

---

## 5. Key Simulation Use Cases

### 5.1 Foam Injection Thermal Simulation

**Use Case:** Before changing PU foam formulation (e.g., blowing agent concentration), simulate the new thermal profile in the digital twin to predict foam density and insulation performance without committing a physical carousel run.

| Input                            | Output                                    | Trigger                       |
|----------------------------------|-------------------------------------------|-------------------------------|
| New foam formulation parameters  | Predicted density profile, cure time      | Engineering change request    |
| Carousel speed, mould temperature| Predicted thermal gradient in refrigerator| Pre-production qualification  |

### 5.2 R600a Leak Dispersion Simulation

**Use Case:** Model the gas dispersion pattern in the event of an R600a leak at each charging station to verify the ventilation system adequacy and evacuation plan.

| Input                            | Output                                    | Trigger                       |
|----------------------------------|-------------------------------------------|-------------------------------|
| Leak scenario (size, location)   | Dispersion plume, concentration contours  | EHS risk assessment annual    |
| Ventilation airflow rates        | Time to safe concentration level          | Prior to any HVAC changes     |

### 5.3 Energy Peak Demand Simulation

**Use Case:** The foam injection machine creates a large demand spike (~45 kW instantaneous) during mould injection. Simulate BESS dispatch to absorb the spike and avoid grid demand charges.

| Input                            | Output                                    | Trigger                       |
|----------------------------------|-------------------------------------------|-------------------------------|
| Production schedule              | Predicted demand spike timing             | Daily scheduling run          |
| BESS SoC at start of shift       | BESS dispatch recommendation              | Every 15 minutes (EMS AI)     |

### 5.4 Predictive Maintenance — Reflow Oven Zone Drift

**Use Case:** Model reflow oven thermal zone drift over time as heating elements age, predicting when zone temperature deviations will exceed ±3°C (SMT yield impact threshold).

| Input                            | Output                                    | Trigger                       |
|----------------------------------|-------------------------------------------|-------------------------------|
| Zone temperature history (trend) | Days until ±3°C deviation predicted      | Weekly PdM AI analysis        |
| Element run hours                | Recommended replacement window            | AI alert at probability ≥ 0.7 |

---

## 6. Integration with AI Platform

| AI Service               | Data FROM DT                                        | Intelligence TO DT / MES                        |
|--------------------------|-----------------------------------------------------|-------------------------------------------------|
| Predictive Maintenance   | Vibration, temp, carousel speed, reflow zone temps  | Failure probability; maintenance schedule alert |
| Yield Prediction         | Reflow profile, foam density telemetry, IQC scores  | Predicted FPY for current job                   |
| Energy Optimisation      | Foam injection load profile, BESS SoC, solar gen    | BESS dispatch plan; demand spike mitigation     |
| Gas Safety AI            | R600a sensor readings, ventilation state            | Leak detection alert; evacuation trigger        |
| Scheduling Optimiser     | Machine availability, WIP status                    | Optimised job sequence; minimise foam idle time |

---

## 7. Data Retention Policy

| Data Category           | Live Update Freq. | Hot Storage  | Cold Storage | Deletion Policy          |
|-------------------------|-------------------|--------------|--------------|--------------------------|
| Machine telemetry (raw) | 30 seconds        | 90 days      | 2 years      | Archive after 90 days    |
| Reflow zone temperature | 30 seconds        | 1 year       | 5 years      | SMT process records 5 yr |
| Gas sensor readings     | 10 seconds        | 2 years      | 10 years     | Safety record 10 years   |
| Foam injection params   | Per cycle         | 2 years      | 7 years      | QMS quality records      |
| Production records      | Per cycle         | 2 years      | 7 years      | Legal minimum 7 years    |
| Energy data             | 30 seconds        | 1 year       | 10 years     | Carbon accounting 10 yr  |
| AMR position (raw)      | 1 second          | 7 days       | 1 year       | Aggregate after 7 days   |
| DT simulation runs      | On demand         | 30 days      | 6 months     | Purge after 6 months     |

---

*For asset sensor specifications, refer to [`machinery.md`](./machinery.md).*
*For AI service API specifications, refer to [`mes-integration.md`](./mes-integration.md).*
*For energy asset details, refer to [`energy-profile.md`](./energy-profile.md).*
