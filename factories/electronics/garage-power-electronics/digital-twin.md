# Garage & Power Electronics Factory — Digital Twin Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Garage & Power Electronics Factory | **Location:** Sagamu Industrial Estate, Ogun State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Coo-Cah Technology Division — Digital Twin Team

---

## 1. Introduction

The Garage & Power Electronics Digital Twin provides real-time virtualisation of the inverter assembly lines, SMT PCB line, transformer winding cells, and the 600 kWp ground-mount solar energy system. Given that this factory's products are themselves power conversion and energy storage systems, the digital twin provides an additional unique function: **product-level performance twin** — each inverter produced becomes a registered digital twin asset that tracks its performance throughout its commercial lifetime, supporting warranty analytics and firmware OTA updates.

**Digital Twin Objectives:**
1. Real-time production state: inverter assembly lines, SMT, winding, load bank test
2. Product-level twin: each manufactured inverter and solar charge controller has a digital record
3. Predictive maintenance: transformer winding motors, SMT oven, load bank cooling fans
4. Ground-mount solar + BESS performance modelling
5. Load bank test analytics: detect systematic test failures by SKU
6. Phase 2: extend to CNC winding cells

---

## 2. Digital Twin Architecture

```
Physical Factory (Sagamu)
    │ OPC-UA, MQTT, REST, Modbus TCP
    ▼
Edge Computing Node (Factory Server Room)
    │ Data buffering; local anomaly alerts; PLC gateway
    ▼
Coo-Cah DT Engine (Cloud — Rwanda HQ)
    ├── Asset State Service — SMT, inverter lines, winding, test
    ├── Product Twin Registry — every inverter/SCC serial number
    ├── Load Bank Analytics Engine — test result patterns
    ├── Energy Performance Model — solar + BESS twin
    ├── Time-Series Store (InfluxDB)
    ├── Predictive Maintenance AI
    └── DT API — serves MES, AI Platform, Product Support
```

---

## 3. Asset Registry

### 3.1 SMT PCB Line

| DT Asset ID      | Physical Asset                | DT Model Type     | Sensor Count | Integration |
|------------------|-------------------------------|-------------------|--------------|-------------|
| DT-GAR-PE-001    | DEK solder paste printer      | State + Thermal   | 8            | OPC-UA      |
| DT-GAR-PE-002    | JUKI FX-3R P&P #1             | Kinematic + State | 12           | OPC-UA      |
| DT-GAR-PE-003    | JUKI FX-3R P&P #2             | Kinematic + State | 12           | OPC-UA      |
| DT-GAR-PE-004    | Heller reflow oven            | Multi-Zone Thermal| 28           | OPC-UA      |
| DT-GAR-PE-005    | Koh Young AOI                 | Vision + State    | 6            | OPC-UA+REST |

### 3.2 Inverter Assembly Lines

| DT Asset ID      | Physical Asset                  | DT Model Type     | Sensor Count | Integration |
|------------------|---------------------------------|-------------------|--------------|-------------|
| DT-GAR-INV-001   | Inverter Assembly Line 1        | State + Kinematic | 18           | OPC-UA/MQTT |
| DT-GAR-INV-002   | Inverter Assembly Line 2        | State + Kinematic | 18           | OPC-UA/MQTT |
| DT-GAR-INV-003   | Inverter Assembly Line 3        | State + Kinematic | 18           | OPC-UA/MQTT |
| DT-GAR-INV-004   | Transformer Winding Cells (×6)  | Electrical+Mech   | 24           | MQTT        |
| DT-GAR-INV-005   | Load Bank Auto-Test System      | Electrical State  | 30           | OPC-UA      |

### 3.3 Product-Level Digital Twin Registry

Every inverter and solar charge controller manufactured is registered as a product twin asset in the DT engine upon serialisation in MES.

| Product Category       | Twin Data Recorded                                           | Update Events                                   |
|------------------------|--------------------------------------------------------------|-------------------------------------------------|
| Pure Sine Wave Inverter| Serial, flash FW version, load bank test results (V, A, eff%) | Manufacture; FW update; warranty claim        |
| MPPT Solar Charge Ctrl | Serial, programming parameters, test results (V, I, tracking efficiency) | Manufacture; field diagnostic event   |
| UPS Line Interactive   | Serial, battery type/date, transfer time, test results      | Manufacture; battery replacement event         |
| Power Tools            | Serial, motor test results, vibration baseline              | Manufacture; warranty return                   |

### 3.4 Energy System Assets

| DT Asset ID      | Physical Asset              | DT Model Type     | Update Freq. | Integration     |
|------------------|-----------------------------|-------------------|--------------|-----------------|
| DT-GAR-EN-001    | Solar PV — 600 kWp ground   | Power Curve       | 30 sec       | EMS MQTT        |
| DT-GAR-EN-002    | LFP BESS 700 kWh            | Electrochemical   | 30 sec       | BMS MQTT        |
| DT-GAR-EN-003    | Sungrow Hybrid Inverters ×2 | State Machine     | 30 sec       | EMS Modbus TCP  |
| DT-GAR-EN-004    | Grid Connection Meter       | State + Load      | 30 sec       | Smart Meter     |

### 3.5 Power Tool Assembly Line

| DT Asset ID      | Physical Asset                       | DT Model Type         | Sensor Count | Integration |
|------------------|--------------------------------------|-----------------------|--------------|-------------|
| DT-GAR-PT-001    | Motor Assembly Station (×4)          | State + Process       | 8            | MQTT        |
| DT-GAR-PT-002    | Gearbox Assembly Station (×3)        | State + Process       | 6            | MQTT        |
| DT-GAR-PT-003    | Housing Assembly Station (×4)        | State                 | 4            | MQTT        |
| DT-GAR-PT-004    | Function Test Dynamometer (×4)       | Electrical + Mech     | 16           | OPC-UA      |
| DT-GAR-PT-005    | Hipot Safety Analyser — Chroma 19053 (×4) | Electrical State | 8            | OPC-UA      |
| DT-GAR-PT-006    | Cordless Battery Pack Assembly (×2)  | Electrical + Thermal  | 8            | MQTT        |

Each power tool function test station streams no-load RPM, stall torque, and power draw in real time. The DT engine correlates test results with upstream motor assembly torque logs to identify systematic defects by SKU.

### 3.6 AMR Fleet

Eight autonomous mobile robots handle material transport between SMT, inverter assembly, winding, test area, power tool line, and despatch.

| DT Asset ID       | Physical Asset                     | DT Model Type          | Update Freq. | Integration  |
|-------------------|------------------------------------|------------------------|--------------|--------------|
| DT-GAR-AMR-001    | AMR Unit 1 — Geek+ P40 / KEENON T8 | Position + State      | 1 sec        | AMR REST API |
| DT-GAR-AMR-002    | AMR Unit 2                         | Position + State       | 1 sec        | AMR REST API |
| DT-GAR-AMR-003    | AMR Unit 3                         | Position + State       | 1 sec        | AMR REST API |
| DT-GAR-AMR-004    | AMR Unit 4                         | Position + State       | 1 sec        | AMR REST API |
| DT-GAR-AMR-005    | AMR Unit 5                         | Position + State       | 1 sec        | AMR REST API |
| DT-GAR-AMR-006    | AMR Unit 6                         | Position + State       | 1 sec        | AMR REST API |
| DT-GAR-AMR-007    | AMR Unit 7                         | Position + State       | 1 sec        | AMR REST API |
| DT-GAR-AMR-008    | AMR Unit 8                         | Position + State       | 1 sec        | AMR REST API |

The DT engine tracks fleet-level utilisation, cycle time per route, and battery state-of-charge across all eight units. Alerts are raised when an AMR is stationary on a production route for more than 3 minutes.

---

## 4. Key Simulation Use Cases

### 4.1 Load Bank Test Result Analytics

**Use Case:** Detect systematic failures in load bank testing by SKU and correlate with upstream production parameters (e.g., transformer winding tolerance deviations causing output voltage variance).

| Input                          | Output                                       | Trigger                        |
|--------------------------------|----------------------------------------------|--------------------------------|
| Load bank test results (V, A)  | Failure pattern by SKU, by assembly station  | After every 100 units tested   |
| Winding resistance readings    | Correlation: winding tolerance vs. test fail | Weekly AI analysis             |

### 4.2 Transformer Winding Quality Prediction

**Use Case:** Predict winding defects (shorts, open circuits) before the transformer is inserted into the inverter chassis, based on resistance and inductance readings from winding stations.

| Input                          | Output                                       | Trigger                        |
|--------------------------------|----------------------------------------------|--------------------------------|
| Winding resistance (Ω)         | Probability of short circuit                 | Real-time at winding station   |
| Turns count vs. nominal        | Risk of inductance out of spec               | Real-time at winding station   |

### 4.3 Ground-Mount Solar Performance Monitoring

**Use Case:** Detect individual panel string degradation or soiling by comparing DT model's expected power curve to actual measured output, triggering maintenance inspection.

| Input                          | Output                                       | Trigger                        |
|--------------------------------|----------------------------------------------|--------------------------------|
| String current readings        | Underperforming strings flagged              | Daily AI analysis              |
| Irradiance sensor              | Soiling ratio estimate per string            | Alert if > 5% deviation        |

### 4.4 Power Tool End-of-Line Test Analytics

**Use Case:** Correlate power tool function test results (no-load RPM, stall torque, power draw) with upstream motor and gearbox assembly parameters to detect systematic defects by SKU before product reaches packaging.

| Input                              | Output                                            | Trigger                         |
|------------------------------------|---------------------------------------------------|---------------------------------|
| Function test: RPM, stall torque   | Failure pattern by SKU, by assembly station       | After every 50 units tested     |
| Motor assembly torque log          | Correlation: assembly torque vs. RPM deviation    | Weekly AI analysis              |
| Hipot test results                 | Insulation failure rate by model and batch        | After every 100 units tested    |
| Battery pack voltage / IR readings | Out-of-spec pack rate vs. cell batch supplier     | Per batch incoming QC event     |

---

## 5. Data Retention Policy

| Data Category         | Live Update | Hot Storage | Cold Storage | Policy                  |
|-----------------------|-------------|-------------|--------------|-------------------------|
| Machine telemetry     | 30 sec      | 90 days     | 2 years      | Archive after 90 days   |
| Reflow zone temps     | 30 sec      | 1 year      | 5 years      | SMT quality records     |
| Load bank test data   | Per test    | 3 years     | 10 years     | Warranty records 10 yrs |
| Product twin registry | Per event   | Lifetime    | 15 years     | Product support records |
| Solar performance     | 30 sec      | 1 year      | 10 years     | Carbon accounting       |

---

## 6. Sensor Coverage Map

Sensor density and high-level coverage are tracked here for operational context. The canonical sensor-level registry for Gate 3 is maintained in [`docs/sensor-map.md`](./docs/sensor-map.md), while spatial references are maintained in [`docs/bim/zone-boundaries.md`](./docs/bim/zone-boundaries.md) and [`docs/bim/asset-anchors.md`](./docs/bim/asset-anchors.md).

- Use `docs/sensor-map.md` for model, protocol, calibration interval, and location by sensor.
- Use `docs/bim/*` files for zone boundary coordinates and asset anchor points used by 3D rendering.

---

*Refer to [`machinery.md`](./machinery.md) for full equipment register.*
*Refer to [`mes-integration.md`](./mes-integration.md) for MES API integration.*
