# Coo-Cah Metallurgical & Minerals Factory — Energy Profile & Power Systems Design

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Metallurgical & Minerals Factory | **Location:** Warri / Ovwian-Aladja Steel Corridor, Delta State, Nigeria | **Phase:** Phase 2
> **Document Version:** 1.0 | **Owner:** Energy & Infrastructure Team

---

## 1. Factory Power Demand Analysis

Chemical manufacturing is energy-intensive. The dominant loads are process heating (reactors, distillation), compressed air systems, and HVAC for controlled storage areas.

| # | System / Load                          | Rated Power (kW) | Duty Cycle | Avg Load (kW) |
|---|----------------------------------------|------------------|------------|---------------|
| 1 | Primary Process Plant (reactors, heat) | Process-specific | 80–100%    | Dominant      |
| 2 | Compressed Air System                  | 150–400 kW       | 70%        | 105–280 kW    |
| 3 | Pumping Systems                        | 50–200 kW        | 80%        | 40–160 kW     |
| 4 | HVAC (controlled storage + lab)        | 80–200 kW        | 90%        | 72–180 kW     |
| 5 | Process Cooling (towers + chillers)    | 100–300 kW       | 80%        | 80–240 kW     |
| 6 | Lighting + General                     | 50–100 kW        | 100%       | 50–100 kW     |
| 7 | IT / SCADA / DCS                       | 20–40 kW         | 100%       | 20–40 kW      |
| 8 | AMR Fleet Charging                     | 20–40 kW         | 30%        | 6–12 kW       |

---

## 2. Power Summary

| Parameter                        | Value            |
|----------------------------------|------------------|
| Estimated Peak Simultaneous Load | ~2,500 kW        |
| Average Operational Load         | 70% of peak      |
| Daily Energy Consumption         | ~16h operational |
| Recommended Solar PV             | 1,000 kWp      |
| Recommended BESS                 | 1,200 kWh LFP           |
| Target Solar Self-Sufficiency    | ≥ 70%            |
| Power Factor Target              | ≥ 0.92           |

---

## 3. Solar Site Assessment

| Parameter                              | Value                    |
|----------------------------------------|--------------------------|
| Location                               | Warri / Ovwian-Aladja Steel Corridor, Delta State, Nigeria               |
| Peak Sun Hours (annual average)        | 4.6–5.0 hrs/day          |
| Recommended PV System Size             | 1,000 kWp              |
| Mounting Type                          | Ground-mount + Rooftop   |
| Estimated Annual Solar Generation      | ~1715 MWh  |

---

## 4. BESS Specification

| Parameter              | Value                       |
|------------------------|-----------------------------|
| BESS Capacity          | 1,200 kWh LFP                      |
| Chemistry              | LFP (LiFePO₄)               |
| C-Rate                 | 0.5C charge / 1C discharge  |
| Cycle Life             | ≥ 4,000 cycles at 80% DoD   |
| Management             | Sungrow EMS + MES sub-meter |
| Safety                 | BMS with SIL-rated interlock|

---

## 5. Generator / Standby Power

| Parameter              | Value                          |
|------------------------|--------------------------------|
| Standby Generator      | Perkins / Caterpillar diesel   |
| Rating                 | Sized for critical loads + 20% |
| ATS Transfer Time      | < 20 ms                        |
| Fuel Storage           | 30,000-litre on-site tank      |

---

*Refer to [`floor-plan.md`](./floor-plan.md) for power distribution routing.*
*Refer to [`machinery.md`](./machinery.md) for load breakdown by equipment.*
