# Personal Electronics — Intra-Group Supply Coordination

> **Gate 3 Artifact (Supply Chain Readiness)**
> **Factory:** Coo-Cah Personal Electronics Factory | **Location:** Sagamu Industrial Estate, Ogun State
> **Document Version:** 1.0 | **Owner:** Supply Chain & Procurement Team
> **Counter-parties:** Coo-Cah Plastics Factory | Coo-Cah Garage & Power Electronics Factory

---

## 1. Purpose

This document records formal intra-group supply commitments received from sister factories for Phase 1 production readiness. It supplements the supply chain risk register in [`supply-chain.md`](../supply-chain.md) with confirmed volumes and signed-off design artefacts.

---

## 2. Coo-Cah Plastics Factory — Casing Volume Confirmation

### 2.1 Confirmed Supply Agreement

| Parameter               | Value                                                          |
|-------------------------|----------------------------------------------------------------|
| Supplier Factory        | Coo-Cah Plastics Factory, Ota Industrial Estate, Ogun State   |
| Buyer Factory           | Coo-Cah Personal Electronics Factory, Sagamu                  |
| Agreement Reference     | INTRA-SUPPLY-PLASTIC-2025-001                                  |
| Effective Date          | 2025-Q3                                                        |
| Review Frequency        | Quarterly production planning meeting                         |

### 2.2 Volume Commitment by SKU (Phase 1)

| Product SKU       | Product Name           | Casing Description                 | Committed Volume/Month | Lead Time (Intra-Group) | Status     |
|-------------------|------------------------|------------------------------------|------------------------|--------------------------|------------|
| CCE-FP-3G         | Feature Phone 3G       | PP housing (2 parts) + keypad mat  | 30,000 sets            | 5 business days          | ✅ Confirmed|
| CCE-FP-4G         | Feature Phone 4G       | PP housing (2 parts) + keypad mat  | 25,000 sets            | 5 business days          | ✅ Confirmed|
| CCE-SP-LITE       | Smartphone Lite        | PC/ABS housing (3 parts)           | 60,000 sets            | 5 business days          | ✅ Confirmed|
| CCE-TWS-01        | TWS Earbuds (Basic)    | ABS earbud shell + case (5 parts)  | 40,000 sets            | 5 business days          | ✅ Confirmed|
| CCE-SW-LITE       | Smartwatch Lite        | PC watch case + band (4 parts)     | 20,000 sets            | 5 business days          | ✅ Confirmed|
| CCE-PB-10K        | Power Bank 10,000 mAh  | ABS housing (2 parts)              | 20,000 sets            | 5 business days          | ✅ Confirmed|

> **Total committed monthly casing output (Phase 1):** ~195,000 product sets across 6 SKUs.

### 2.3 Capacity Buffer and Escalation

| Condition                                | Protocol                                                           |
|------------------------------------------|--------------------------------------------------------------------|
| Personal Electronics volume increase >15%| 10 business days advance notice required; Plastics capacity review |
| Plastics capacity constraint flagged     | Escalate to Group Supply Chain Director within 24 hours           |
| Quality hold on casing batch             | MES-to-MES API notification; replacement batch dispatched <48 hrs |
| Emergency top-up (unplanned SKU spike)   | Up to 10,000 sets/week emergency buffer pre-agreed                |

### 2.4 Quality Acceptance Criteria

| Parameter             | Requirement                                      |
|-----------------------|--------------------------------------------------|
| Dimensional tolerance | ±0.1 mm on all mating surfaces                   |
| Surface finish        | Ra ≤ 0.8 µm; no visible sink marks               |
| Colour ΔE             | ≤ 1.5 vs. approved colour standard               |
| Incoming QC sample    | AQL 2.5 Level II per ANSI/ASQ Z1.4              |
| COC required          | Yes — material data sheet + dimensional report  |

---

## 3. Coo-Cah Garage & Power Electronics Factory — BMS PCB Design Sign-Off

### 3.1 Sign-Off Record

| Parameter               | Value                                                                       |
|-------------------------|-----------------------------------------------------------------------------|
| Supplier Factory        | Coo-Cah Garage & Power Electronics Factory, Sagamu Industrial Estate        |
| Buyer Factory           | Coo-Cah Personal Electronics Factory, Sagamu                                |
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
| Applicable SKUs             | CCE-SP-LITE, CCE-SP-MID, CCE-TWS-PRO, CCE-SW-PRO, CCE-PB-10K, CCE-PB-20K |
| Safety Standards            | IEC 62133-2:2017; MSDS for cells sourced from CATL/EVE    |
| PCB Layers                  | 4-layer FR-4; ENIG surface finish                          |
| Test Coverage               | 100% in-circuit test + thermal soak 45 °C/4 h per batch   |

### 3.3 Monthly PCB Supply Commitment (Phase 1)

| PCB Type     | Committed Volume/Month | Lead Time (Intra-Group) | Status      |
|--------------|------------------------|--------------------------|-------------|
| BMS-1S       | 80,000 units           | 7 business days          | ✅ Confirmed|
| BMS-2S       | 40,000 units           | 7 business days          | ✅ Confirmed|
| Main PCB (assembled, phone) | 60,000 boards | 10 business days       | ✅ Confirmed|
| Main PCB (assembled, TWS)   | 40,000 boards | 10 business days       | ✅ Confirmed|

### 3.4 Design Change Control

Any BMS PCB design change requires:

1. Engineering Change Request (ECR) raised in the shared PLM system.
2. 10-business-day advance notification to Personal Electronics factory Quality and Manufacturing teams.
3. Updated design documentation (BOM, schematics, test spec) shared at ECR initiation.
4. New batch acceptance test at Personal Electronics IQC before production use.

---

## 4. MES-to-MES Integration for Intra-Group Supply

Both intra-group supply flows are monitored via the MES-to-MES REST API integration described in [`mes-integration.md`](../mes-integration.md) §8.

| Data Exchange                 | Direction                            | Frequency  |
|-------------------------------|--------------------------------------|------------|
| Casing production schedule    | Plastics MES → Personal Electronics | Hourly     |
| Casing WIP status + ETA       | Plastics MES → Personal Electronics | Hourly     |
| PCB delivery schedule         | Garage MES → Personal Electronics   | Hourly     |
| Internal PCB order status     | Garage MES → Personal Electronics   | Hourly     |
| Quality hold notification     | Bidirectional                        | Real-time  |

---

## Related Documents

| Document | Purpose |
|----------|---------|
| [`supply-chain.md`](../supply-chain.md) | Master supply chain plan, risk register, and logistics |
| [`mes-integration.md`](../mes-integration.md) | MES-to-MES API integration specification (§8) |
| [`regulatory.md`](../regulatory.md) | IEC 62133, SON NIS, and RoHS requirements for PCBs and cells |
| [`gap-closure-report.md`](./gap-closure-report.md) | Gap closure status including intra-group supply evidence |
