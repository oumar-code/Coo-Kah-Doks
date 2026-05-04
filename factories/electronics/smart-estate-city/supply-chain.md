# Smart Estate & City Electronics Factory — Supply Chain Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Smart Estate & City Electronics Factory | **Location:** Lekki Free Trade Zone, Lagos State, Nigeria
> **Document Version:** 1.0 | **Owner:** Coo-Cah Supply Chain Division

---

## 1. Introduction

This document defines the supply chain architecture for the Coo-Cah Smart Estate & City Electronics Factory, covering inbound raw material and component flows, finished goods outbound logistics, cross-factory dependencies, and third-party logistics requirements.

The Coo-Cah supply chain strategy prioritises:
1. **Localisation:** Maximum African content in raw materials and components
2. **Resilience:** Multi-source critical components; safety stock buffers sized for supply disruptions
3. **Visibility:** End-to-end supply chain tracking via MES and AI Platform
4. **Efficiency:** AI-driven demand planning and automated procurement signals

---

## 2. Raw Material Inputs

### 2.1 Bill of Materials — Key Raw Material Categories

| # | Material / Component              | Category        | Supplier Type      | Country of Origin    | Lead Time  | Safety Stock (Days) | Annual Volume      | Notes                              |
|---|-----------------------------------|-----------------|--------------------|----------------------|------------|---------------------|--------------------|------------------------------------|
| 1 | Smart Meter SoC / ASIC chips      | Electronics     | Import distributor | China / US           | 60–90 days | 90                  | 2M units/yr        | Critical; dual-source required     |
| 2 | LoRa/SX1276 RF modules            | Electronics     | Import distributor | China (Semtech OEM)  | 45–60 days | 60                  | 500K units/yr      | Single-source risk; buffer stock   |
| 3 | LCD / E-ink displays (smart meter)| Electronics     | Import distributor | China                | 45 days    | 45                  | 800K units/yr      | Standard component                 |
| 4 | PCBs (bare boards)                | Electronics     | Import (China/TW)  | China / Taiwan       | 21–30 days | 30                  | 4M boards/yr       | Multiple suppliers qualified       |
| 5 | Polycarbonate / ABS enclosures    | Plastics        | Coo-Cah Plastics   | Nigeria              | 7 days     | 14                  | 800K units/yr      | Internal supply; priority          |
| 6 | Aluminium extrusions (smart poles)| Metals          | Local + Import     | Nigeria / China      | 14–21 days | 21                  | 50K poles/yr       | Local powder coating available     |
| 7 | LED modules (street lighting)     | Electronics     | Import distributor | China                | 30 days    | 30                  | 100K units/yr      | Tier-1 LED brands (Cree/Lumileds)  |
| 8 | Li-ion battery packs (smart meter)| Energy          | Import distributor | China                | 45 days    | 45                  | 1M packs/yr        | LFP chemistry for longevity        |
| 9 | Packaging — Master Carton         | Packaging       | Local manufacturer | Nigeria              | 14 days    | 30                  | 1M cartons/yr      | Coo-Cah branding; approved spec    |
| 10| Labels (product/shipping/cert)    | Packaging       | Local printer      | Nigeria              | 7 days     | 21                  | 5M labels/yr       | Variable data; linked to MES       |

### 2.2 Supplier Tiering

| Tier   | Definition                                          | Number of Suppliers | Audit Requirement             |
|--------|-----------------------------------------------------|---------------------|-------------------------------|
| Tier 1 | Direct suppliers — materials received by this factory | 18                | Annual Coo-Cah supplier audit |
| Tier 2 | Suppliers to Tier 1 — key sub-components             | 35                | Bi-annual self-assessment     |
| Tier 3 | Raw material suppliers — commodities                 | 20                | Annual self-declaration       |

### 2.3 Critical Materials Risk Register

| Material                  | Risk Factor              | Risk Level | Mitigation Strategy                                     |
|---------------------------|--------------------------|------------|---------------------------------------------------------|
| Smart Meter SoC chips     | Single-source, long LT   | High       | Dual-source approved (Renesas + EPCOS); 90-day buffer   |
| LoRa RF modules           | Semtech IP dependency    | High       | 60-day safety stock; evaluate alternative LPWAN silicon |
| PCBs                      | FX/import duty           | Medium     | USD forward contracts; 3 approved board houses          |
| LED modules               | Price volatility         | Medium     | Annual pricing agreements with 2 suppliers              |

---

## 3. Finished Goods Outputs

### 3.1 Finished Goods Catalogue

| # | Product Name                    | SKU Code      | Units/Pallet | Pallet Weight (kg) | Destination                                |
|---|---------------------------------|---------------|--------------|--------------------|--------------------------------------------|
| 1 | Smart Electricity Meter (1-ph)  | CCE-SM-ELEC-1 | 48           | 120                | DisCo utilities, smart estate developers   |
| 2 | Smart Electricity Meter (3-ph)  | CCE-SM-ELEC-3 | 24           | 140                | Industrial/commercial customers            |
| 3 | Smart Water Meter               | CCE-SM-WATER  | 60           | 90                 | State water agencies, estates              |
| 4 | Smart Estate Hub                | CCE-SEH       | 20           | 60                 | Property developers, estate managers       |
| 5 | Smart Pole System               | CCE-SPS       | 5            | 250                | State governments, road agencies           |
| 6 | City Traffic Controller         | CCE-CTC       | 4            | 80                 | State/Federal transport ministries         |
| 7 | LoRaWAN IoT Gateway             | CCE-LORA-GW   | 20           | 50                 | Telecom/ISPs, smart city integrators       |

### 3.2 Outbound Logistics Channels

| Channel                      | Product Types           | Frequency  | Logistics Provider       | Lead Time (factory → customer) |
|------------------------------|-------------------------|------------|--------------------------|--------------------------------|
| Utility/Government Direct    | Smart meters, poles     | Weekly     | Coo-Cah Logistics Fleet  | 1–5 days within Nigeria        |
| Coo-Cah Distribution Hub     | All consumer SKUs       | Daily      | Coo-Cah Logistics Fleet  | 1–3 days                       |
| Export (West Africa)         | Smart meters, gateways  | Bi-weekly  | Scan Global Logistics    | 5–14 days (ECOWAS)             |
| Project-Based Delivery       | Smart poles, traffic ctrl| Per project| Project logistics contractor | Per project plan            |

---

## 4. Internal AMR Routing (Intra-Factory)

### 4.1 AMR Task Types

| Task Type             | Trigger                     | From Zone    | To Zone       | AMR Type      |
|-----------------------|-----------------------------|--------------|---------------|---------------|
| Raw Material Delivery | MES kitting release         | RMS          | STG           | Transport AMR |
| Kit Delivery          | Production order start      | STG          | PL Station    | Transport AMR |
| WIP Transfer          | Station cycle complete      | PL Station   | Next station  | Transport AMR |
| Calibration Transfer  | IPQC trigger                | Assembly     | CAL Zone      | Transport AMR |
| FG Move               | FQC PASS + pack complete    | PKG          | FGW           | Transport AMR |
| Scrap Removal         | Scrap bin weight sensor     | Any zone     | Scrap Bay     | Transport AMR |

### 4.2 AMR Fleet: 8 Units

| AMR Unit | Primary Route         | Payload (kg) | Charging Bay |
|----------|-----------------------|--------------|--------------|
| AMR-01   | RMS → STG → SMT Line  | 250          | Bay-01       |
| AMR-02   | RMS → STG → Assembly  | 250          | Bay-02       |
| AMR-03   | STG → Meter Assembly  | 200          | Bay-03       |
| AMR-04   | Assembly → Calibration| 150          | Bay-04       |
| AMR-05   | Calibration → FQC     | 150          | Bay-05       |
| AMR-06   | FQC → PKG → FGW       | 250          | Bay-06       |
| AMR-07   | FGW → LD-OUT          | 300          | Bay-07       |
| AMR-08   | Spare / overflow      | 250          | Bay-08       |

---

## 5. Cross-Factory Dependencies

### 5.1 Inbound Dependencies

| Factory                       | Material / Component         | Frequency | Volume (Phase 1)       | Backup if unavailable           |
|-------------------------------|------------------------------|-----------|------------------------|---------------------------------|
| Coo-Cah Plastics Factory      | PC/ABS enclosures, housings  | Weekly    | 100K units/week        | Import from China (4-week LT)   |
| Coo-Cah Personal Electronics  | PCB assembly expertise       | Ongoing   | Knowledge sharing      | In-house capability             |
| Coo-Cah Garage Power Elec.    | Inverters for test equipment | As needed | 10 units/yr            | External UPS supplier           |

### 5.2 Outbound Dependencies

| Factory / Customer              | Material / Service       | Frequency | Volume (Phase 1)     |
|---------------------------------|--------------------------|-----------|----------------------|
| Coo-Cah Distribution Hub        | All finished goods       | Daily     | 2,000+ units/day     |
| DisCo Utilities (direct B2B)    | Smart meters             | Weekly    | 20,000 meters/week   |
| Smart city/estate developers    | Smart poles, hubs        | Per project | Per contract       |

---

## 6. Demand Planning & Replenishment

### 6.1 Safety Stock Policy

| Component Category           | Safety Stock Method       | Target (Days of Supply) |
|------------------------------|---------------------------|-------------------------|
| Critical SoC chips           | Demand × lead time × var. | 90 days                 |
| RF modules                   | Reorder point formula     | 60 days                 |
| Standard imported components | Reorder point formula     | 30 days                 |
| Plastics (Coo-Cah supplied)  | Kanban                    | 14 days                 |
| Packaging                    | Kanban                    | 30 days                 |

---

## 7. Import / Export Procedures

### 7.1 Inbound Imports (Key)

- All imported electronic components cleared via Lekki Free Trade Zone bonded warehouse (duty-free import within LFTZ)
- SONCAP pre-clearance required for regulated electronic products before import
- IQC inspection mandatory for all PCBs, SoCs, and RF modules before release to production

### 7.2 Outbound Exports

- SON product certificate required for smart meters before commercial sale
- NCC type approval required for all wireless-enabled products (LoRa, Wi-Fi, cellular)
- ECOWAS TLS documentation for regional exports

---

*For CapEx implications, refer to [`capex-opex.md`](./capex-opex.md).*
*For regulatory compliance, refer to [`regulatory.md`](./regulatory.md).*
