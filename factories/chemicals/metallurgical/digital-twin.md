# Coo-Cah Metallurgical & Minerals Factory — Digital Twin Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Metallurgical & Minerals Factory | **Location:** Warri / Ovwian-Aladja Steel Corridor, Delta State, Nigeria | **Phase:** Phase 2
> **Document Version:** 1.0 | **Owner:** Coo-Cah Technology Division — Digital Twin Team

---

## 1. Introduction

The Coo-Cah Metallurgical & Minerals Factory digital twin is a **process-level simulation twin** for high-temperature metallurgical operations and mineral beneficiation. Unlike the discrete assembly factory twins in the Electronics vertical, this twin models heat balances in an Electric Arc Furnace (EAF), continuous casting solidification, rolling mill speed-tension dynamics, and mineral processing yield — all in real time.

**Digital Twin Objectives:**
1. EAF heat balance: minimise electrical energy per tonne of melt; optimise tap-to-tap time
2. Continuous casting quality: predict surface and internal defects from casting speed and mould thermal data
3. Rolling mill process control: predict strip breakage risk; optimise speed and tension profiles
4. Mineral beneficiation yield: optimise reagent dosing, grind size, and flotation parameters for maximum metal recovery
5. Safety monitoring: compare DCS process state vs. DT model for high-temperature operations; pre-empt SIS activation
6. Environmental reporting: fume, dust, and effluent tracking; DPR / SON compliance monitoring

---

## 2. Digital Twin Architecture

```
Process Instrumentation (DCS + SCADA field instruments)
    │ OPC-DA / OPC-UA → DCS Historian (OSIsoft PI or similar)
    ▼
Edge Gateway (Factory Control Room)
    │ Data aggregation; local anomaly detection; DCS/SCADA gateway
    ▼
Coo-Cah DT Engine (Cloud — Rwanda HQ)
    ├── EAF Heat Balance Model
    ├── Continuous Casting Solidification Model
    ├── Rolling Mill Process Model (speed + tension)
    ├── Mineral Crushing & Grinding Model
    ├── Flotation Yield Prediction Model (ML)
    ├── Emissions Tracker (DPR / SON reporting)
    ├── Safety Delta Monitor (DCS vs. DT)
    ├── Rotating Equipment PdM (vibration + process data)
    ├── Time-Series Store (InfluxDB / OSIsoft PI)
    └── DT API → MES, AI Platform, Safety Team, EHS Team
```

---

## 3. Asset Registry

### 3.1 Primary Metallurgical Assets

| DT Asset ID     | Physical Asset                              | DT Model Type              | Sensor Count | Integration |
|-----------------|---------------------------------------------|----------------------------|--------------|-------------|
| DT-MET-EAF-001  | Electric Arc Furnace (EAF)                  | Thermal + Electrical       | 40–60        | OPC-UA      |
| DT-MET-CC-001   | Continuous Caster — Strand #1               | Solidification + Thermal   | 30–45        | OPC-UA      |
| DT-MET-CC-002   | Continuous Caster — Strand #2               | Solidification + Thermal   | 30–45        | OPC-UA      |
| DT-MET-RM-001   | Roughing Mill Stand                         | Kinematic + Force          | 20–28        | OPC-UA      |
| DT-MET-RM-002   | Finishing Mill Stands (×4)                  | Kinematic + Force + Thermal| 40–56        | OPC-UA      |
| DT-MET-HT-001   | Heat Treatment Furnace (annealing / normalising) | Thermal (multi-zone)  | 20–30        | OPC-UA      |
| DT-MET-LF-001   | Ladle Furnace (secondary metallurgy)        | Thermal + Chemistry        | 16–24        | OPC-UA      |
| DT-MET-FD-001   | Fume & Dust Extraction System               | Flow + Particulate         | 12–18        | OPC-UA      |
| DT-MET-SL-001   | Slag Handling System                        | State + Weight             | 8            | MQTT        |

### 3.2 Mineral Processing Assets

| DT Asset ID     | Physical Asset                              | DT Model Type              | Sensor Count | Integration |
|-----------------|---------------------------------------------|----------------------------|--------------|-------------|
| DT-MET-CR-001   | Primary Jaw Crusher                         | Vibration + Power          | 10           | MQTT        |
| DT-MET-CR-002   | Secondary Cone Crusher                      | Vibration + Power          | 10           | MQTT        |
| DT-MET-BM-001   | Ball Mill #1                                | Vibration + Process        | 14           | OPC-UA      |
| DT-MET-BM-002   | Ball Mill #2                                | Vibration + Process        | 14           | OPC-UA      |
| DT-MET-CY-001   | Hydrocyclone Cluster                        | Flow + Pressure            | 12           | MQTT        |
| DT-MET-FL-001   | Flotation Cell Bank — Rougher               | Process + Chemistry        | 18           | OPC-UA      |
| DT-MET-FL-002   | Flotation Cell Bank — Cleaner               | Process + Chemistry        | 18           | OPC-UA      |
| DT-MET-FP-001   | Filter Press (concentrate dewatering)       | Process + State            | 8            | MQTT        |
| DT-MET-TH-001   | Thickener                                   | Level + Torque + Density   | 10           | OPC-UA      |
| DT-MET-PM-001   | Process Pumps — Slurry (all critical)       | Vibration + Process        | 4 per pump   | MQTT        |

### 3.3 Safety & Environmental Assets

| DT Asset ID     | Physical Asset                              | DT Model Type              | Update Freq. | Integration |
|-----------------|---------------------------------------------|----------------------------|--------------|-------------|
| DT-MET-GS-001   | Gas & Fume Detection Array (EAF, casting areas) | Concentration Map      | 10 sec       | DCS OPC-UA  |
| DT-MET-DS-001   | Dust Monitoring System (mineral yard + mill)| Particulate Map            | 1 min        | SCADA MQTT  |
| DT-MET-ETP-001  | Effluent Treatment Plant                    | Process + Chemistry        | 5 min        | SCADA MQTT  |
| DT-MET-ST-001   | Stack Emissions Monitor — CEMS (EAF stack)  | Continuous Emissions       | 1 min        | DCS OPC-UA  |
| DT-MET-EN-001   | Solar PV + BESS System                      | Power Curve                | 30 sec       | EMS MQTT    |
| DT-MET-EN-002   | Grid Connection Meter (high-voltage intake) | State + Load               | 30 sec       | Smart Meter |

---

## 4. Key Simulation Use Cases

### 4.1 EAF Heat Balance Optimisation

**Use Case:** Model the real-time thermal state of the EAF to minimise electrical energy consumption per tonne of melt (kWh/t) while maintaining target tap temperature and chemistry, reducing energy cost and improving tap-to-tap time.

| Input                                   | Output                                          | Trigger                                  |
|-----------------------------------------|-------------------------------------------------|------------------------------------------|
| Electrode current & voltage (3-phase)   | Real-time energy input (kWh) vs. model target   | Continuously every 5 sec                |
| Scrap charge weight & composition       | Predicted tap temperature & time-to-tap         | At each scrap charge event               |
| Off-gas temperature & composition       | Foamy slag practice recommendations             | Every 30 sec during heat                 |
| Ladle furnace temperature history       | Optimal power-off point to hit tap target       | 10 min before predicted tap              |

### 4.2 Rolling Mill Speed-Tension Control Simulation

**Use Case:** Predict strip breakage risk by detecting speed and tension imbalances between mill stands, enabling proactive speed adjustments before cobble events. Optimise rolling schedules for minimum pass count and minimum temperature drop.

| Input                                   | Output                                          | Trigger                                  |
|-----------------------------------------|-------------------------------------------------|------------------------------------------|
| Inter-stand tension readings            | Breakage risk score (0–100%) per pass           | Real-time every 100 ms                   |
| Entry / exit thickness gauges           | Predicted exit gauge deviation from target      | Real-time every 100 ms                   |
| Mill stand motor current & torque       | Drive overload prediction                       | Alert if > 90% rated torque              |
| Strip temperature (pyrometers)          | Predicted mechanical properties at coiler       | After each finish mill pass              |

### 4.3 Continuous Casting Quality Prediction

**Use Case:** Predict surface and internal defects (longitudinal cracks, centreline segregation) from real-time mould thermal and casting speed data, enabling operators to adjust secondary cooling and casting speed before defective material is produced.

| Input                                   | Output                                          | Trigger                                  |
|-----------------------------------------|-------------------------------------------------|------------------------------------------|
| Mould thermocouple readings (all rows)  | Mould hot-spot score; breakout risk index       | Every 10 sec                             |
| Casting speed                           | Predicted shell thickness at mould exit         | Every 10 sec                             |
| Secondary cooling water flows           | Predicted surface crack probability             | Every 30 sec                             |
| Tundish temperature & superheat         | Centreline segregation risk estimate            | Each ladle change event                  |

### 4.4 Mineral Beneficiation Yield Simulation

**Use Case:** Optimise flotation reagent dosing (collector, frother, pH modifier) and ball mill grind size to maximise metal recovery grade and minimise reagent cost. The DT engine runs what-if scenarios against a trained ML yield model.

| Input                                   | Output                                          | Trigger                                  |
|-----------------------------------------|-------------------------------------------------|------------------------------------------|
| Feed grade (ore assay)                  | Predicted concentrate grade and recovery (%)    | Each new ore batch; every 15 min ongoing |
| Ball mill P80 grind size                | Recommended grind target for current ore type   | Daily; updated on ore type change        |
| Flotation reagent dosing rates          | Optimal dosing recommendation vs. current feed  | Every 15 min; AI reagent optimiser       |
| Thickener underflow density             | Predicted filter press throughput and moisture  | Every 10 min                             |

---

## 5. Data Retention Policy

| Data Category                    | Hot Storage | Cold Storage | Policy                                        |
|----------------------------------|-------------|--------------|-----------------------------------------------|
| EAF process data (all DCS tags)  | 1 year      | 10 years     | Process safety & metallurgical records        |
| Continuous caster thermal data   | 2 years     | 15 years     | Quality traceability per cast heat number     |
| Rolling mill process data        | 2 years     | 10 years     | Product quality records per coil / bar ID     |
| Mineral process (crusher, mill)  | 1 year      | 7 years      | Yield optimisation records                    |
| Fume / dust & stack emissions    | 2 years     | 15 years     | DPR / SON regulatory compliance               |
| Effluent monitoring (ETP)        | 2 years     | 10 years     | NESREA / DPR effluent consent records         |
| Energy / carbon data             | 1 year      | 10 years     | Carbon accounting; DPR emissions inventory    |

---

## 6. Sensor Coverage Map

| Zone                              | Temp / Thermal | Force / Vibration | Flow / Level | Gas / Dust / Emissions | Electrical | Total (approx.) |
|-----------------------------------|----------------|-------------------|--------------|------------------------|------------|-----------------|
| Mineral Yard & Primary Crushing   | 4              | 20                | 8            | 10                     | 10         | ~52             |
| Grinding & Classification (mills) | 10             | 28                | 24           | 4                      | 16         | ~82             |
| Flotation & Thickening            | 8              | 10                | 36           | 6                      | 10         | ~70             |
| EAF & Ladle Furnace               | 40             | 8                 | 10           | 20                     | 30         | ~108            |
| Continuous Caster                 | 60             | 6                 | 20           | 4                      | 10         | ~100            |
| Rolling Mill (roughing + finishing)| 30            | 30                | 10           | 4                      | 60         | ~134            |
| Heat Treatment Furnace            | 24             | 4                 | 6            | 4                      | 8          | ~46             |
| ETP + Stack (environmental)       | 10             | 4                 | 14           | 20                     | 4          | ~52             |
| **Total (approx.)**               | **186**        | **110**           | **128**      | **72**                 | **148**    | **~644**        |

*Sensor counts are indicative. Final counts confirmed at FEED / detail engineering stage.*

---

*Refer to [`mes-integration.md`](./mes-integration.md) for MES-DCS integration.*
*Refer to [`machinery.md`](./machinery.md) for full equipment register.*
