# Kitchen Electronics — Intra-Group Supply Coordination

> **Gate 3 Artifact (Supply Chain Readiness)**
> **Factory:** Coo-Cah Kitchen Electronics Factory | **Location:** Agbara Industrial Estate, Lagos State
> **Document Version:** 1.0 | **Owner:** Supply Chain & Procurement Team
> **Counter-parties:** Coo-Cah Plastics Factory | Coo-Cah Garage & Power Electronics Factory

---

## 1. Purpose

This document records formal intra-group supply commitments received from sister factories for Phase 1 production readiness. It supplements the supply chain risk register in [`supply-chain.md`](../supply-chain.md) with confirmed volumes, quality acceptance criteria, escalation protocols, and MES-to-MES data exchange specifications.

---

## 2. Coo-Cah Plastics Factory — Plastic Components Commitment

### 2.1 Confirmed Supply Agreement

| Parameter               | Value                                                             |
|-------------------------|-------------------------------------------------------------------|
| Supplier Factory        | Coo-Cah Plastics Factory, Ota Industrial Estate, Ogun State      |
| Buyer Factory           | Coo-Cah Kitchen Electronics Factory, Agbara Industrial Estate     |
| Agreement Reference     | INTRA-SUPPLY-PLASTIC-KIT-2025-001                                 |
| Effective Date          | 2025-Q4                                                           |
| Delivery Frequency      | 2 dedicated truck runs per day (~12 km within Agbara/Sagamu corridor) |
| Review Frequency        | Quarterly production planning meeting                             |

### 2.2 Volume Commitment by Component (Phase 1)

| Component Supplied                              | Material Spec                         | Daily Volume       | Lead Time (Intra-Group) | Quality Gate            | Status      |
|-------------------------------------------------|---------------------------------------|--------------------|--------------------------|-------------------------|-------------|
| Microwave oven plastic housing                  | ABS HH, food-grade coating            | 200 units/day      | 1–2 days                 | Dimensional + cosmetic  | ✅ Confirmed |
| Microwave door inner frame                      | ABS, microwave-transparent grade      | 200 units/day      | 1–2 days                 | Fit check + material cert | ✅ Confirmed |
| SDA housing sets (blender, kettle, rice cooker, toaster) | ABS/PP, food-grade         | 1,500 sets/day     | 1–2 days                 | Cosmetic class A        | ✅ Confirmed |
| Refrigerator interior liner                     | HIPS, food-safe, white                | 320 units/day      | 1–2 days                 | Dimensional; no warping | ✅ Confirmed |
| Cooker control panel housing                    | PC+ABS, heat-resistant                | 180 units/day      | 1–2 days                 | Heat class rating cert  | ✅ Confirmed |

> **Total committed daily plastic output (Phase 1):** ~2,400 component sets across 5 product families.

### 2.3 Capacity Buffer and Escalation

| Condition                                       | Protocol                                                                    |
|-------------------------------------------------|-----------------------------------------------------------------------------|
| Kitchen Electronics volume increase > 15%       | 10 business days advance notice required; Plastics capacity review          |
| Plastics capacity constraint flagged            | Escalate to Group Supply Chain Director within 24 hours                    |
| Quality hold on casing batch                    | MES-to-MES API notification; replacement batch dispatched within 48 hours  |
| Emergency top-up (unplanned SKU spike)          | Up to 500 sets/day emergency buffer pre-agreed across all casing types     |
| Refrigerator liner warpage rejection > 0.5%     | Automatic production hold; Plastics QA investigation within 24 hours       |

### 2.4 Quality Acceptance Criteria

| Parameter             | Requirement                                        |
|-----------------------|----------------------------------------------------|
| Dimensional tolerance | ±0.1 mm on all mating surfaces                     |
| Surface finish        | Ra ≤ 0.8 µm; no visible sink marks or flow lines   |
| Colour ΔE             | ≤ 1.5 vs. approved colour standard                 |
| Warpage (liners)      | ≤ 0.3 mm/300 mm span for HIPS refrigerator liners  |
| Food-safety compliance| EU 10/2011 or equivalent food-contact certificate required per batch |
| Incoming QC sample    | AQL 2.5 Level II per ANSI/ASQ Z1.4               |
| CoC required          | Yes — material data sheet + dimensional report per consignment |

---

## 3. Coo-Cah Garage & Power Electronics Factory — Critical Infrastructure Supply

### 3.1 Confirmed Supply Items

| Parameter               | Value                                                                       |
|-------------------------|-----------------------------------------------------------------------------|
| Supplier Factory        | Coo-Cah Garage & Power Electronics Factory, Sagamu Industrial Estate        |
| Buyer Factory           | Coo-Cah Kitchen Electronics Factory, Agbara Industrial Estate               |
| Agreement Reference     | INTRA-SUPPLY-POWER-KIT-2025-001                                             |
| Effective Date          | 2025-Q4                                                                     |
| Supply Type             | One-off commissioning supply (not recurring production volumes)             |

### 3.2 Items and Volumes

| Item Supplied                      | Specification                                  | Volume     | Lead Time | Notes                                   | Status      |
|------------------------------------|------------------------------------------------|------------|-----------|-----------------------------------------|-------------|
| UPS for critical MES edge servers  | CCG-UPS-1kVA (rack-mount, 1U)                 | 8 units    | 4 weeks   | Factory commissioning; server room Z16  | ✅ Confirmed |
| Inverter backup for R600a gas zone | CCG-INV-PSW-3kVA (pure sine-wave)             | 4 units    | 4 weeks   | ATEX-compliant enclosure required; Z5   | ✅ Confirmed |
| Smart PDU for MES server room      | CCG-PDU-3P-24A                                | 2 units    | 3 weeks   | Remote outlet monitoring; Z16           | ✅ Confirmed |

### 3.3 ATEX Compliance Note for Gas Zone Inverters

The 4× inverter backup units destined for the R600a Gas Charging Zone (Z5) must be housed in an ATEX-rated enclosure external to the ATEX Zone 2 boundary. Supply agreement includes:

1. Coo-Cah Garage Power Electronics to confirm ATEX zone 2 suitability of inverter unit or supply in IECEx-certified enclosure.
2. EHS Officer at Kitchen Electronics to sign off placement before commissioning.
3. Electrical installation to be completed by ATEX-certified electrician.

---

## 4. Dependency Risks and Contingencies

| Risk                                              | Likelihood | Impact   | Contingency                                                    |
|---------------------------------------------------|------------|----------|----------------------------------------------------------------|
| Plastics Factory capacity shortage (SDA spike)    | Medium     | High     | Pre-agreed 500 sets/day emergency buffer; secondary local moulders identified |
| Plastics liner warpage issue (HIPS)               | Low        | High     | Refrigerator production hold; imported HIPS liner interim option (8-week lead time) |
| Garage Power supply delay (UPS/inverter)          | Low        | Medium   | Commercial UPS suppliers in Lagos available as backup (Parker/APC) |
| Daily truck run disruption (weather/traffic)      | Medium     | Medium   | 2× daily runs provide natural buffer; 7-day consignment buffer at Kitchen Electronics stores |
| MES-to-MES API downtime                           | Low        | Low      | Manual daily schedule phone call as fallback; no more than 24h disruption |

---

## 5. Monthly Coordination Cadence

| Meeting                                | Frequency   | Participants                                          | Agenda Items                                       |
|----------------------------------------|-------------|-------------------------------------------------------|----------------------------------------------------|
| Plastic Supply Review                  | Monthly     | SCM Lead (Kitchen Elec), Production Lead (Plastics)   | Volume forecast, quality scorecard, capacity flags |
| Group Supply Chain Steering            | Monthly     | Group SCM Director, SCM Leads from all factories      | Cross-factory capacity, risks, and priorities       |
| Intra-Group Quality Review             | Quarterly   | QA Managers (Kitchen Elec + Plastics)                 | Incoming quality trends, dimensional audit results |
| Annual Supply Agreement Review         | Annual      | Factory Managers + Group SCM Director                 | Volume commitments for next production year        |

---

## 6. MES-to-MES Integration for Intra-Group Supply

Both intra-group supply flows are monitored via the MES-to-MES REST API integration.

| Data Exchange                        | Direction                                    | Frequency  |
|--------------------------------------|----------------------------------------------|------------|
| Plastics production schedule         | Plastics MES → Kitchen Electronics MES       | Hourly     |
| Plastics WIP status + ETA            | Plastics MES → Kitchen Electronics MES       | Hourly     |
| Kitchen Electronics daily demand     | Kitchen Electronics MES → Plastics MES       | Daily (BOD) |
| Quality hold notification            | Bidirectional                                | Real-time  |
| Refrigerator liner warpage flags     | Kitchen Electronics IQC → Plastics QA        | Real-time  |

---

## Related Documents

| Document | Purpose |
|----------|---------|
| [`supply-chain.md`](../supply-chain.md) | Master supply chain plan, risk register, safety stock policy, and logistics |
| [`mes-integration.md`](../mes-integration.md) | MES API specifications including AMR dispatch and materials management modules |
| [`regulatory.md`](../regulatory.md) | NESREA R600a, ATEX zone compliance, and food-contact material requirements |
| [`gap-closure-report.md`](./gap-closure-report.md) | Gap closure status including intra-group supply evidence |
