# Kitchen Electronics — Intra-Group Supply Coordination

> **Gate 3 Artifact (Supply Chain Readiness)**
> **Factory:** Coo-Cah Kitchen Electronics Factory | **Location:** Agbara Industrial Estate, Lagos / Sagamu, Ogun State
> **Document Version:** 1.0 | **Owner:** Supply Chain & Procurement Team
> **Counter-parties:** Coo-Cah Plastics Factory | Coo-Cah Garage & Power Electronics Factory

---

## 1. Purpose

This document records formal intra-group supply commitments received from sister factories for Phase 1 production readiness of the Kitchen Electronics Factory. It supplements the supply chain risk register in [`supply-chain.md`](../supply-chain.md) with confirmed volumes and service level agreements.

---

## 2. Coo-Cah Plastics Factory — Casing Volume Confirmation

### 2.1 Confirmed Supply Agreement

| Parameter               | Value                                                          |
|-------------------------|----------------------------------------------------------------|
| Supplier Factory        | Coo-Cah Plastics Factory, Ota Industrial Estate, Ogun State   |
| Buyer Factory           | Coo-Cah Kitchen Electronics Factory, Agbara / Sagamu          |
| Agreement Reference     | INTRA-SUPPLY-PLASTIC-KITCHEN-2025-001                          |
| Effective Date          | 2025-Q3                                                        |
| Review Frequency        | Quarterly production planning meeting                         |

### 2.2 Volume Commitment by Product Category (Phase 1)

| Product SKU              | Product Name                    | Casing Description                             | Committed Volume/Month | Lead Time (Intra-Group) | Status      |
|--------------------------|---------------------------------|------------------------------------------------|------------------------|--------------------------|-------------|
| CCK-REF-2D-FF (220L/280L)| Frost-Free Refrigerator         | ABS inner liner + HIPS decorative inner door   | 5,000 sets             | 7 business days          | ✅ Confirmed|
| CCK-REF-1D-DC            | Single Door Direct Cool Fridge  | ABS inner liner                                | 4,000 sets             | 7 business days          | ✅ Confirmed|
| CCK-MW-SOLO/GRILL/CONV   | Microwave Oven (all variants)   | ABS outer shell + door bezel (2-part)          | 4,500 sets             | 5 business days          | ✅ Confirmed|
| CCK-EC-2IND / CCK-EC-4CONV| Electric Cooker (all variants) | ABS control panel housing (2-part)             | 3,500 sets             | 5 business days          | ✅ Confirmed|
| CCK-BL-500/1000          | Blender                         | ABS base + jar housing (3-part)                | 7,000 sets             | 5 business days          | ✅ Confirmed|
| CCK-KT-1.5/1.7           | Electric Kettle                 | PP/ABS body (2-part)                           | 6,000 sets             | 5 business days          | ✅ Confirmed|
| CCK-RC-1.8/3.0           | Rice Cooker                     | ABS outer body + inner lid ring (3-part)       | 4,500 sets             | 5 business days          | ✅ Confirmed|
| CCK-TS-2/4               | Pop-Up Toaster                  | ABS chassis body (2-part)                      | 5,500 sets             | 5 business days          | ✅ Confirmed|

> **Total committed monthly casing output (Phase 1):** ~40,000 product sets across 8 product families.

### 2.3 Capacity Buffer and Escalation

| Condition                                | Protocol                                                           |
|------------------------------------------|--------------------------------------------------------------------|
| Kitchen volume increase >15%             | 10 business days advance notice required; Plastics capacity review |
| Plastics capacity constraint flagged     | Escalate to Group Supply Chain Director within 24 hours           |
| Quality hold on casing batch             | MES-to-MES API notification; replacement batch dispatched <48 hrs |
| Emergency top-up (unplanned SKU spike)   | Up to 6,000 sets/week emergency buffer pre-agreed                 |

### 2.4 Quality Acceptance Criteria

| Parameter             | Requirement                                      |
|-----------------------|--------------------------------------------------|
| Dimensional tolerance | ±0.2 mm on all mating surfaces (appliance bodies)|
| Wall thickness        | ≥ 2.0 mm for appliance outer casings             |
| Surface finish        | Ra ≤ 1.2 µm; no visible sink marks               |
| Colour ΔE             | ≤ 1.5 vs. approved colour standard               |
| Incoming QC sample    | AQL 2.5 Level II per ANSI/ASQ Z1.4              |
| COC required          | Yes — material data sheet + dimensional report  |
| Temperature resistance| PP/ABS casings: minimum 120 °C short-term (kettle/toaster adjacency) |

---

## 3. Coo-Cah Garage & Power Electronics Factory — Energy Supply Agreement

### 3.1 Confirmed Internal Supply Agreement

| Parameter               | Value                                                                        |
|-------------------------|------------------------------------------------------------------------------|
| Supplier Factory        | Coo-Cah Garage & Power Electronics Factory, Sagamu Industrial Estate         |
| Buyer Factory           | Coo-Cah Kitchen Electronics Factory, Agbara / Sagamu                         |
| Agreement Reference     | INTRA-ENERGY-KITCHEN-2025-001                                                |
| Effective Date          | 2025-Q3                                                                      |
| Review Frequency        | Quarterly                                                                    |

### 3.2 Internal Energy Hardware Commitment (Phase 1)

| Product | Specification | Committed Allocation | Purpose | Status |
|---------|---------------|----------------------|---------|--------|
| CCG-INV-PSW-3kVA | Pure Sine Wave Inverter, 3kVA | 4 units/quarter | Critical load backup — MES servers, R600a gas monitoring, IT infra | ✅ Confirmed |
| CCG-UPS-1kVA | UPS Line Interactive, 1kVA | 8 units/quarter | Individual UPS for MES edge nodes and operator terminals | ✅ Confirmed |
| CCG-SCC-MPPT-40A | MPPT Solar Charge Controller | 2 units/quarter | Supplementary battery charging for off-grid emergency power | ✅ Confirmed |
| CCG-PS-6way | Surge-Protected Power Strip | 100 units/quarter | IT infrastructure and office equipment protection | ✅ Confirmed |

### 3.3 Priority and Delivery Terms

| Term | Detail |
|------|--------|
| Production priority | `INTERNAL-PRIORITY` flag in Garage Power MES; scheduled before commercial orders |
| Delivery SLA | Within 3 business days of production completion |
| Packaging | Transit packaging suitable for intra-estate truck delivery |
| Warranty (internal) | Full 2-year product warranty applies to internal supply |
| Technical support | Garage Power Electronics Engineering on-call for installation commissioning |

### 3.4 Critical Load Protection Scope

The inverters and UPS units supplied by Garage Power Electronics protect the following Kitchen Electronics systems:

| Protected System | Load (kW) | Inverter/UPS Unit | Priority Tier |
|------------------|-----------|-------------------|---------------|
| MES Application Servers | 3.5 kW | CCG-INV-PSW-3kVA | Tier 1 |
| R600a Gas Monitoring Sensors + Alarms | 0.5 kW | CCG-UPS-1kVA | Tier 1 (safety-critical) |
| MES Edge Node — Refrigerator Line | 1.2 kW | CCG-UPS-1kVA | Tier 2 |
| MES Edge Node — SDA Lines | 0.8 kW | CCG-UPS-1kVA | Tier 2 |
| IT Switch Room (LAN/WAN) | 2.0 kW | CCG-INV-PSW-3kVA | Tier 2 |
| Quality Lab Instruments | 1.0 kW | CCG-UPS-1kVA | Tier 3 |

---

## 4. MES-to-MES Integration for Intra-Group Supply

All intra-group supply flows are monitored via the MES-to-MES REST API integration described in [`mes-integration.md`](../mes-integration.md) §8.

| Data Exchange                 | Direction                                  | Frequency  |
|-------------------------------|---------------------------------------------|------------|
| Casing production schedule    | Plastics MES → Kitchen Electronics MES     | Hourly     |
| Casing WIP status + ETA       | Plastics MES → Kitchen Electronics MES     | Hourly     |
| Inverter/UPS delivery schedule| Garage Power MES → Kitchen Electronics MES | Hourly     |
| Internal energy order status  | Garage Power MES → Kitchen Electronics MES | Hourly     |
| Quality hold notification     | Bidirectional                               | Real-time  |

---

## Related Documents

| Document | Purpose |
|----------|---------|
| [`supply-chain.md`](../supply-chain.md) | Master supply chain plan, risk register, and logistics |
| [`mes-integration.md`](../mes-integration.md) | MES-to-MES API integration specification |
| [`regulatory.md`](../regulatory.md) | IEC 60335, SON NIS, NESREA R600a requirements |
| [`energy-profile.md`](../energy-profile.md) | Energy demand analysis; critical load tiers |
| [`gap-closure-report.md`](./gap-closure-report.md) | Gap closure status including intra-group supply evidence |
