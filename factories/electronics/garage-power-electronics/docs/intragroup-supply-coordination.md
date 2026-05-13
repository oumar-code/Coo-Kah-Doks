# Garage & Power Electronics — Intra-Group Supply Coordination

> **Gate 3 Artifact (Supply Chain Readiness)**
> **Factory:** Coo-Cah Garage & Power Electronics Factory | **Location:** Sagamu Industrial Estate, Ogun State
> **Document Version:** 1.0 | **Owner:** Supply Chain & Procurement Team
> **Counter-parties:** Coo-Cah Plastics Factory | Coo-Cah Personal Electronics Factory | Sister Factory Energy Consumers

---

## 1. Purpose

This document records formal intra-group supply commitments flowing to and from the Garage & Power Electronics Factory for Phase 1 production readiness. It supplements the supply chain risk register in [`supply-chain.md`](../supply-chain.md) with confirmed volumes, design sign-offs, and priority rules for internal supply orders.

---

## 2. Coo-Cah Plastics Factory — Enclosure Volume Confirmation

### 2.1 Confirmed Supply Agreement

| Parameter               | Value                                                          |
|-------------------------|----------------------------------------------------------------|
| Supplier Factory        | Coo-Cah Plastics Factory, Ota Industrial Estate, Ogun State   |
| Buyer Factory           | Coo-Cah Garage & Power Electronics Factory, Sagamu            |
| Agreement Reference     | INTRA-SUPPLY-PLASTIC-POWER-2025-001                            |
| Effective Date          | 2025-Q3                                                        |
| Review Frequency        | Quarterly production planning meeting                         |

### 2.2 Volume Commitment by SKU (Phase 1)

| Product SKU        | Product Name                        | Enclosure Description                   | Committed Volume/Month | Lead Time (Intra-Group) | Status      |
|--------------------|-------------------------------------|-----------------------------------------|------------------------|--------------------------|-------------|
| CCG-INV-PSW (all)  | Pure Sine Wave Inverter             | ABS enclosure (2-part top/base)         | 12,000 sets            | 5 business days          | ✅ Confirmed|
| CCG-INV-MSW (all)  | Modified Sine Wave Inverter         | ABS enclosure (2-part top/base)         | 8,000 sets             | 5 business days          | ✅ Confirmed|
| CCG-SCC-MPPT (all) | MPPT Solar Charge Controller        | ABS wall-mount enclosure (single-part)  | 10,000 sets            | 5 business days          | ✅ Confirmed|
| CCG-SCC-PWM (all)  | PWM Solar Charge Controller         | ABS wall-mount enclosure (single-part)  | 6,000 sets             | 5 business days          | ✅ Confirmed|
| CCG-UPS (all)      | UPS Line Interactive                | ABS tower enclosure (3-part)            | 3,500 sets             | 5 business days          | ✅ Confirmed|
| CCG-PT-DRILL       | Electric Drill                      | ABS handle + motor housing (4-part)     | 5,000 sets             | 7 business days          | ✅ Confirmed|
| CCG-PT-AG          | Angle Grinder                       | ABS body housing (3-part)               | 4,000 sets             | 7 business days          | ✅ Confirmed|
| CCG-PT-CS          | Circular Saw                        | ABS body + guard housing (4-part)       | 3,000 sets             | 7 business days          | ✅ Confirmed|

> **Total committed monthly enclosure output (Phase 1):** ~51,500 product sets across 8 SKU families.

### 2.3 Capacity Buffer and Escalation

| Condition                                     | Protocol                                                           |
|-----------------------------------------------|--------------------------------------------------------------------|
| Garage volume increase >15%                   | 10 business days advance notice required; Plastics capacity review |
| Plastics capacity constraint flagged          | Escalate to Group Supply Chain Director within 24 hours           |
| Quality hold on enclosure batch               | MES-to-MES API notification; replacement batch dispatched <48 hrs |
| Emergency top-up (unplanned SKU spike)        | Up to 5,000 sets/week emergency buffer pre-agreed                 |

### 2.4 Quality Acceptance Criteria

| Parameter             | Requirement                                      |
|-----------------------|--------------------------------------------------|
| Dimensional tolerance | ±0.15 mm on all mating surfaces                  |
| Wall thickness        | ≥ 2.5 mm for high-voltage (inverter/UPS) housings|
| Surface finish        | Ra ≤ 1.0 µm; no visible sink marks               |
| Colour ΔE             | ≤ 1.5 vs. approved colour standard               |
| Incoming QC sample    | AQL 2.5 Level II per ANSI/ASQ Z1.4              |
| COC required          | Yes — material data sheet + dimensional report  |
| Flammability rating   | UL 94 V-0 required for inverter and UPS housings |

---

## 3. Coo-Cah Personal Electronics Factory — PCB Design Coordination

### 3.1 Coordination Record

| Parameter               | Value                                                                       |
|-------------------------|-----------------------------------------------------------------------------|
| Buyer Factory           | Coo-Cah Personal Electronics Factory, Sagamu Industrial Estate              |
| Supplier Factory        | Coo-Cah Garage & Power Electronics Factory, Sagamu Industrial Estate        |
| Document Reference      | INTRA-DESIGN-BMS-2025-001                                                   |
| Design Review Date      | 2025-Q3                                                                     |
| Sign-Off Status         | ✅ **Signed Off**                                                            |

### 3.2 BMS PCB Specification (Confirmed)

| Parameter                   | Specification                                              |
|-----------------------------|------------------------------------------------------------|
| PCB Product Designation     | Coo-Cah BMS-1S (single-cell Li-Po) and BMS-2S (dual-cell) |
| Form Factor                 | BMS-1S: 32 × 16 mm; BMS-2S: 45 × 20 mm                   |
| Cell Chemistry Support      | Li-Po 3.7 V nominal; Li-ion 3.6 V nominal                 |
| Protection Features         | Overcharge, over-discharge, short circuit, over-temperature|
| Communication Interface     | I²C (battery gauge) + 1-wire fuel gauge option             |
| Applicable SKUs (Personal)  | CCE-SP-LITE, CCE-SP-MID, CCE-TWS-PRO, CCE-SW-PRO, CCE-PB-10K, CCE-PB-20K |
| Safety Standards            | IEC 62133-2:2017; MSDS for cells sourced from CATL/EVE    |
| PCB Layers                  | 4-layer FR-4; ENIG surface finish                          |
| Test Coverage               | 100% in-circuit test + thermal soak 45 °C/4 h per batch   |

### 3.3 Monthly PCB Supply Commitment (Phase 1)

| PCB Type                    | Committed Volume/Month | Lead Time (Intra-Group) | Status      |
|-----------------------------|------------------------|--------------------------|-------------|
| BMS-1S                      | 80,000 units           | 7 business days          | ✅ Confirmed|
| BMS-2S                      | 40,000 units           | 7 business days          | ✅ Confirmed|
| Main PCB (assembled, phone) | 60,000 boards          | 10 business days         | ✅ Confirmed|
| Main PCB (assembled, TWS)   | 40,000 boards          | 10 business days         | ✅ Confirmed|

### 3.4 Design Change Control

Any BMS PCB design change requires:

1. Engineering Change Request (ECR) raised in the shared PLM system.
2. 10-business-day advance notification to Personal Electronics factory Quality and Manufacturing teams.
3. Updated design documentation (BOM, schematics, test spec) shared at ECR initiation.
4. New batch acceptance test at Personal Electronics IQC before production use.

---

## 4. Internal Energy Supply to Sister Factories

The Garage & Power Electronics Factory manufactures inverters and UPS systems that are **consumed internally** by other Coo-Cah factories before commercial sale. This internal energy supply is treated as a priority production category.

### 4.1 Internal Supply Priority Policy

| Rule | Detail |
|------|--------|
| Priority flag | MES Production Order Management assigns `INTERNAL-PRIORITY` flag to all sister-factory orders |
| Scheduling | Internal orders are scheduled before commercial orders in the same production week |
| Delivery SLA | Internal orders delivered within 3 business days of production completion |
| ERP integration | Internal orders raised directly by group ERP; no manual intervention required |

### 4.2 Committed Internal Allocations (Phase 1)

| Recipient Factory | Product | Committed Allocation/Month | Purpose |
|-------------------|---------|-----------------------------|---------|
| Coo-Cah Personal Electronics (Sagamu) | CCG-INV-PSW-1kVA | 8 units/quarter | Factory energy backup |
| Coo-Cah Kitchen Electronics (Agbara) | CCG-INV-PSW-3kVA + CCG-UPS-1kVA | 12 units/quarter | Factory critical load backup |
| Coo-Cah Plastics Factory (Ota) | CCG-INV-PSW-2kVA + CCG-SCC-MPPT-40A | 10 units/quarter | Factory energy independence |
| All factories | CCG-PS (surge-protected power strips) | 200 units/quarter | IT infrastructure protection |

---

## 5. MES-to-MES Integration for Intra-Group Supply

All intra-group supply flows are monitored via the MES-to-MES REST API integration described in [`mes-integration.md`](../mes-integration.md) §8.

| Data Exchange                 | Direction                                  | Frequency  |
|-------------------------------|---------------------------------------------|------------|
| Enclosure production schedule | Plastics MES → Garage Power MES            | Hourly     |
| Enclosure WIP status + ETA    | Plastics MES → Garage Power MES            | Hourly     |
| PCB delivery schedule         | Garage Power MES → Personal Electronics    | Hourly     |
| Internal PCB order status     | Garage Power MES → Personal Electronics    | Hourly     |
| Internal inverter order status| Garage Power MES → Kitchen/Plastics MES    | Hourly     |
| Quality hold notification     | Bidirectional                               | Real-time  |

---

## Related Documents

| Document | Purpose |
|----------|---------|
| [`supply-chain.md`](../supply-chain.md) | Master supply chain plan, risk register, and logistics |
| [`mes-integration.md`](../mes-integration.md) | MES-to-MES API integration specification |
| [`regulatory.md`](../regulatory.md) | IEC 62133, IEC 62040, SON NIS requirements for PCBs and inverters |
| [`gap-closure-report.md`](./gap-closure-report.md) | Gap closure status including intra-group supply evidence |
