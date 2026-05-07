# Garage & Power Electronics Factory — Executive Summary

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Vertical:** Electronics — Power & Energy Solutions | **Location:** Sagamu Industrial Estate, Ogun State, Nigeria | **Phase:** Phase 1 (Priority)
> **Document Version:** 1.0 | **Status:** In Development

> 📁 **Dedicated Repository:** Full engineering blueprints, operational docs, and AI-integration specs for this factory live in the dedicated repo — **[oumar-code/coo-cah-factory-electronics-power](https://github.com/oumar-code/coo-cah-factory-electronics-power)**. This document is the master-repo executive summary; the dedicated repo is the authoritative source for all factory-level detail.

---

## 1. Factory Overview

The Coo-Cah Garage & Power Electronics Factory is a **Phase 1 priority facility** — its products directly enable the energy independence strategy of every other Coo-Cah factory and the broader Coo-Cah Smart Estate ecosystem. Inverters, solar charge controllers, and battery chargers manufactured here are consumed internally across the Coo-Cah network before being sold commercially.

Located in Sagamu Industrial Estate, Ogun State — strategically positioned between Lagos and Ibadan, with good road access, available land for ground-mount solar arrays, and proximity to the Lagos consumer market — this factory addresses Nigeria's acute energy crisis by producing high-quality, locally-manufactured power backup and solar energy solutions at competitive prices.

Nigeria's inverter and solar market is estimated at over 2 million units annually and growing at 15–20% year-on-year as grid instability persists and solar panel prices continue to fall. Coo-Cah's brand positioning: premium performance at mid-market price — underpinned by a 2-year local warranty and factory-direct aftersales support.

| Attribute                  | Details                                                                     |
|----------------------------|-----------------------------------------------------------------------------|
| Factory Name               | Coo-Cah Garage & Power Electronics Factory                                  |
| Location                   | Sagamu Industrial Estate, Ogun State, Nigeria                               |
| Vertical                   | Power Electronics — Inverters, Solar Controllers, UPS, Power Tools          |
| Phase                      | Phase 1 (Priority)                                                          |
| Facility Area              | ~12,000 m²                                                                  |
| Production Start Target    | Q[X] 20[YY]                                                                 |
| Employees (Phase 1)        | ~280 direct; ~60 indirect                                                   |
| Quality Standard           | ISO 9001:2015; SON NIS certifications; IEC 62040 (UPS); IEC 61683 (solar)  |
| Energy Strategy            | 600 kWp ground-mount solar + 700 kWh LFP BESS + grid backup                |

---

## 2. Products

| # | Product                                        | SKU Category         | Capacity Range             | Phase    |
|---|------------------------------------------------|----------------------|----------------------------|----------|
| 1 | Pure Sine Wave Inverter                        | CCG-INV-PSW          | 300VA, 500VA, 1kVA, 2kVA, 3kVA, 5kVA | Phase 1 |
| 2 | Modified Sine Wave Inverter                    | CCG-INV-MSW          | 300VA, 500VA, 1kVA, 2kVA   | Phase 1  |
| 3 | MPPT Solar Charge Controller                   | CCG-SCC-MPPT         | 20A, 40A, 60A, 100A        | Phase 1  |
| 4 | PWM Solar Charge Controller                    | CCG-SCC-PWM          | 10A, 20A, 30A              | Phase 1  |
| 5 | Solar Panel Kit (packaged)                     | CCG-SPK              | 100W, 200W, 400W           | Phase 1  |
| 6 | Battery Charger (smart, multi-stage)           | CCG-BC               | 12V/24V/48V systems        | Phase 1  |
| 7 | Surge-Protected Power Strip (individually-switched Wi-Fi) | CCG-PS  | 4-way, 6-way, 8-way        | Phase 1  |
| 8 | UPS — Line Interactive                         | CCG-UPS              | 600VA, 1kVA, 2kVA          | Phase 1  |
| 9 | Electric Drill (corded + cordless)             | CCG-PT-DRILL         | 500W, 750W; 18V cordless   | Phase 1  |
| 10| Angle Grinder                                  | CCG-PT-AG            | 115mm, 125mm (700W–1000W)  | Phase 1  |
| 11| Circular Saw                                   | CCG-PT-CS            | 165mm, 185mm (1200W–1600W) | Phase 1  |

---

## 3. Production Capacity Targets

| Product Category          | Phase 1 (Yr 1–2) | Phase 2 (Yr 3–4) | Phase 3 (Yr 5+) | Unit       |
|---------------------------|------------------|------------------|-----------------|------------|
| Inverters (all sizes)     | 200,000          | 400,000          | 700,000         | units/year |
| Solar Charge Controllers  | 150,000          | 300,000          | 500,000         | units/year |
| Battery Chargers          | 80,000           | 150,000          | 250,000         | units/year |
| Power Strips              | 500,000          | 1,000,000        | 1,500,000       | units/year |
| UPS                       | 50,000           | 120,000          | 250,000         | units/year |
| Power Tools               | 100,000          | 250,000          | 500,000         | units/year |
| **Total**                 | **1,080,000**    | **2,220,000**    | **3,700,000**   | units/year |

---

## 4. Automation Phase Status

| Phase   | Focus                                                          | Status      |
|---------|----------------------------------------------------------------|-------------|
| Phase 1 | SMT line, manual inverter assembly, load bank testing, MES, AMRs | In Planning |
| Phase 2 | Robotic winding for transformers, AI vision QC on PCBs, digital twin | Planned  |
| Phase 3 | Automated inverter final assembly, lights-out power strip line | Planned     |

---

## 5. Energy Profile Summary

| Metric                          | Value                              |
|---------------------------------|------------------------------------|
| Facility Area                   | ~12,000 m²                         |
| Estimated Peak Load             | ~400 kW                            |
| Daily Energy Consumption        | ~2,800 kWh/day                     |
| Recommended Solar PV            | 600 kWp ground-mount               |
| Recommended BESS                | 700 kWh LFP                        |
| Ogun State Irradiance           | 4.7 PSH/day (annual avg)           |
| Target Solar Self-Sufficiency   | ≥ 80%                              |
| Note                            | Ground-mount preferred — larger land available in Sagamu vs Lagos rooftop |

---

## 6. Key Supply Dependencies

| Component                    | Phase 1 Source                  | Phase 2+ Target                    |
|------------------------------|---------------------------------|------------------------------------|
| Power MOSFETs / IGBTs        | Imported (Infineon, ON Semi)    | Distributor hub + buffer stock     |
| Toroidal/EI Transformer Core | Imported (silicon steel cores)  | Local steel lamination (Phase 3)   |
| Capacitors (electrolytic)    | Imported (Nichicon, Rubycon)    | Distributor buffer                 |
| PCBs (bare boards)           | Imported (China/Taiwan)         | Coo-Cah PCB line (Phase 2)        |
| Copper Wire (magnet wire)    | Local / Import                  | Local supplier development         |
| Plastic Enclosures           | Coo-Cah Plastics / Local        | Coo-Cah Plastics Factory           |
| Power Tool Motors            | Imported (China OEM)            | Investigate local motor assembly   |
| Solar Panels (for kits)      | Imported (Tier-1 Chinese OEM)   | Coo-Cah Solar Panel Fab (Phase 3)  |

---

## 7. Team Structure

| Department                 | Phase 1 Headcount | Key Roles                                        |
|----------------------------|-------------------|--------------------------------------------------|
| Factory Management         | 5                 | Factory Manager, Deputy, Planning, EHS Manager   |
| SMT / PCB Production       | 25                | SMT Supervisor, operators, technicians           |
| Inverter Assembly          | 60                | 3 supervisors, 50 operators, 7 technicians       |
| Power Tool Assembly        | 35                | 2 supervisors, 28 operators, 5 technicians       |
| Power Strip / UPS Lines    | 40                | 2 supervisors, 32 operators, 6 technicians       |
| Test & QA                  | 30                | QA Manager, QA Engineers, QC Inspectors          |
| Maintenance                | 18                | Maintenance Manager, Electricians, Mechanics     |
| Supply Chain / Stores      | 12                | SCM Lead, Store Keepers                          |
| IT / MES                   | 5                 | MES Admin, IT Technicians                        |
| HR / Admin / Finance       | 10                | HR, Admin, Finance roles                         |
| **Total**                  | **~280 direct**   |                                                  |

---

## 8. Sub-Document Index

| Document                                         | Description                                           |
|--------------------------------------------------|-------------------------------------------------------|
| [`machinery.md`](./machinery.md)                 | SMT line, transformer winding, inverter assembly, load bank testing |
| [`energy-profile.md`](./energy-profile.md)       | 400kW demand, 600kWp ground solar, 700kWh BESS        |
| [`floor-plan.md`](./floor-plan.md)               | 12,000m² layout with ground-mount solar yard          |
| [`automation-roadmap.md`](./automation-roadmap.md) | Phase milestones                                    |
| [`supply-chain.md`](./supply-chain.md)           | Power electronics component supply chain             |
| [`regulatory.md`](./regulatory.md)               | SON, IEC 62040, IEC 61683, R&D certifications        |
| [`capex-opex.md`](./capex-opex.md)               | Financial model                                       |
| [`digital-twin.md`](./digital-twin.md)           | Asset registry, simulation use cases                  |
| [`docs/sensor-map.md`](./docs/sensor-map.md) | Standalone physical sensor registry (model, zone, protocol, calibration) |
| [`docs/bim/README.md`](./docs/bim/README.md) | BIM/3D model stub index, zone boundaries, and asset anchors |
---

*This document is part of the Coo-Cah Manufacturing Ecosystem documentation suite.*
