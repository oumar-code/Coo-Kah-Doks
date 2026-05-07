# Coo-Cah Baby & Infant Products Factory — Digital Twin Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Baby & Infant Products Factory | **Location:** Sagamu Industrial Estate, Ogun State, Nigeria | **Phase:** Phase 2
> **Document Version:** 1.0 | **Owner:** Coo-Cah Technology Division — Digital Twin Team

---

## 1. Introduction

The Coo-Cah Baby & Infant Products Factory Digital Twin provides real-time production visibility, quality prediction, and predictive maintenance for the consumer goods manufacturing process. Key differentiators from the electronics vertical: focus on GMP compliance, batch traceability to raw material lot level, fill accuracy monitoring, and cold chain integrity simulation.

**Objectives:**
1. Real-time production state: filling, packaging, QC, cold chain
2. Batch yield prediction: predict yield deviations before batch closes
3. Fill accuracy prediction: detect filling machine drift before defect rate rises
4. Cold chain integrity: simulate temperature excursion risk in FGW
5. Predictive maintenance: filling valves, sealing jaws, conveyor drives
6. Energy optimisation: chiller scheduling around solar peak

---

## 2. Asset Registry

| DT Asset ID     | Physical Asset                        | DT Model Type      | Sensor Count | Integration    |
|-----------------|---------------------------------------|--------------------|--------------|-|
| DT-CGD-PR-001   | Primary Production Line               | State + Thermal    | 20–30        | OPC-UA/MQTT    |
| DT-CGD-FL-001   | Filling + Dosing Line                 | Flow + State       | 12–18        | OPC-UA         |
| DT-CGD-PK-001   | Sealing + Capping Machine             | Thermal + State    | 8–12         | OPC-UA         |
| DT-CGD-CV-001   | Conveyors (all zones)                 | State + Speed      | 8 per zone   | MQTT           |
| DT-CGD-EN-001   | Solar PV + BESS                       | Power Curve        | Standard     | EMS MQTT       |
| DT-CGD-CC-001   | Cold Storage / Chiller System         | Temperature Model  | 6–12         | BMS MQTT       |

---

## 3. Key Simulation Use Cases

| Use Case                      | Input                          | Output                                | Trigger               |
|-------------------------------|--------------------------------|---------------------------------------|-----------------------|
| Fill Accuracy Drift            | Filling valve pressure trend   | Predicted fill volume deviation       | Every 15 min          |
| Batch Yield Prediction         | Recipe inputs, process data    | Expected vs. actual yield             | Start + mid-batch     |
| Cold Chain Risk                | FGW ambient + chiller load     | Temperature excursion probability     | Hourly overnight      |
| Predictive Maintenance         | Vibration + cycle count        | Days to next maintenance event        | Weekly AI run         |
| Energy Cost Optimisation       | Chiller schedule + solar gen   | Optimal chiller on/off times          | Daily scheduling run  |

---

## 4. Data Retention

| Data Category       | Hot Storage | Cold Storage | Policy                      |
|---------------------|-------------|--------------|------------------------------|
| Production telemetry| 90 days     | 2 years      | Archive after 90 days        |
| Batch records       | 3 years     | 10 years     | NAFDAC traceability 10 yrs  |
| Cold chain logs     | 1 year      | 5 years      | HACCP / food safety records  |
| Fill accuracy logs  | 1 year      | 5 years      | Quality system records       |
| Energy data         | 1 year      | 10 years     | Carbon accounting            |

---

*Refer to [`mes-integration.md`](./mes-integration.md) for batch record MES-DT linkage.*

*For standalone sensor mapping, refer to [`docs/sensor-map.md`](./docs/sensor-map.md).*
*For BIM/3D spatial stubs, refer to [`docs/bim/README.md`](./docs/bim/README.md).*
