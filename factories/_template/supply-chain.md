# [FACTORY_NAME] — Supply Chain Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** [FACTORY_NAME] | **Location:** [LOCATION] | **Phase:** [PHASE]
> **Document Version:** 1.0 | **Owner:** Coo-Cah Supply Chain Division

---

## 1. Introduction

This document defines the supply chain architecture for [FACTORY_NAME], covering inbound raw material and component flows, finished goods outbound logistics, AMR-based internal routing, cross-factory material dependencies within the Coo-Cah network, and third-party logistics requirements.

The Coo-Cah supply chain strategy prioritises:
1. **Localisation:** Maximum African content in raw materials and components
2. **Resilience:** Multi-source critical components; safety stock buffers sized for supply disruptions
3. **Visibility:** End-to-end supply chain tracking via MES and AI Platform
4. **Efficiency:** AI-driven demand planning and automated procurement signals

---

## 2. Raw Material Inputs

### 2.1 Bill of Materials — Key Raw Material Categories

| # | Material / Component     | Category       | Supplier Type       | Country of Origin (Phase 1) | Lead Time     | Safety Stock (Days) | Annual Volume   | Notes                                    |
|---|--------------------------|----------------|---------------------|----------------------------|---------------|---------------------|-----------------|------------------------------------------|
| 1 | [MATERIAL_1]             | [CAT]          | [TYPE]              | [COUNTRY]                  | [DAYS] days   | [DAYS]              | [VOLUME/year]   | [Critical / Standard / Commodity]        |
| 2 | [MATERIAL_2]             | [CAT]          | [TYPE]              | [COUNTRY]                  | [DAYS] days   | [DAYS]              | [VOLUME/year]   | [Notes]                                  |
| 3 | [MATERIAL_3]             | [CAT]          | [TYPE]              | [COUNTRY]                  | [DAYS] days   | [DAYS]              | [VOLUME/year]   | [Notes]                                  |
| 4 | [MATERIAL_4]             | [CAT]          | [TYPE]              | [COUNTRY]                  | [DAYS] days   | [DAYS]              | [VOLUME/year]   | [Notes]                                  |
| 5 | [MATERIAL_5]             | [CAT]          | [TYPE]              | [COUNTRY]                  | [DAYS] days   | [DAYS]              | [VOLUME/year]   | [Notes]                                  |
| 6 | [MATERIAL_6]             | [CAT]          | [TYPE]              | [COUNTRY]                  | [DAYS] days   | [DAYS]              | [VOLUME/year]   | [Notes]                                  |
| 7 | Packaging — Master Carton| Packaging      | Local manufacturer  | Nigeria / Local             | 14 days       | 30                  | [VOLUME/year]   | Coo-Cah branding; approved print spec    |
| 8 | Packaging — Inner Box    | Packaging      | Local manufacturer  | Nigeria / Local             | 14 days       | 30                  | [VOLUME/year]   | Full colour; insert printing included    |
| 9 | Labels (product/shipping)| Packaging      | Local printer       | Nigeria                     | 7 days        | 21                  | [VOLUME/year]   | Variable data; linked to MES label print |

### 2.2 Supplier Tiering

| Tier   | Definition                                                          | Number of Suppliers | Audit Requirement          |
|--------|---------------------------------------------------------------------|---------------------|----------------------------|
| Tier 1 | Direct suppliers — materials received by this factory               | [N]                 | Annual Coo-Cah supplier audit |
| Tier 2 | Suppliers to Tier 1 — key sub-components                            | [N]                 | Bi-annual self-assessment   |
| Tier 3 | Raw material suppliers — commodities                                | [N]                 | Annual self-declaration      |

### 2.3 Critical Materials Risk Register

| Material           | Risk Factor             | Risk Level | Mitigation Strategy                                 |
|--------------------|-------------------------|------------|-----------------------------------------------------|
| [MATERIAL_1]       | [RISK_DESCRIPTION]      | High       | Dual-source; [N] months safety stock; local develop |
| [MATERIAL_2]       | [RISK_DESCRIPTION]      | Medium     | Alternative supplier qualified; 30-day buffer       |
| [MATERIAL_3]       | FX/import duty exposure | Medium     | USD forward contracts; negotiate DDP terms          |
| [MATERIAL_4]       | Single source           | High       | Supplier qualification programme for 2nd source     |

---

## 3. Finished Goods Outputs

### 3.1 Finished Goods Catalogue

| # | Product Name         | SKU Code  | Units/Pallet | Pallet Weight (kg) | Pallet Dimensions (LxWxH mm) | Destination                          |
|---|----------------------|-----------|--------------|--------------------|-----------------------------|--------------------------------------|
| 1 | [PRODUCT_1]          | [SKU]     | [N]          | [KG]               | [LxWxH]                     | [DISTRIBUTION_HUB / RETAILER / EXPORT] |
| 2 | [PRODUCT_2]          | [SKU]     | [N]          | [KG]               | [LxWxH]                     | [DESTINATION]                        |
| 3 | [PRODUCT_3]          | [SKU]     | [N]          | [KG]               | [LxWxH]                     | [DESTINATION]                        |

### 3.2 Outbound Logistics Channels

| Channel              | Product Types              | Frequency        | Logistics Provider        | Lead Time (factory → customer) |
|----------------------|----------------------------|------------------|---------------------------|--------------------------------|
| National Distribution| All domestic SKUs          | Daily            | [3PL_PROVIDER]            | 1–5 days within Nigeria        |
| Coo-Cah Network Transfer | Components to sister factories | Weekly       | Coo-Cah Logistics Fleet   | 1–3 days (intercity)           |
| Export (West Africa) | Select SKUs                | Weekly           | [FREIGHT_FORWARDER]        | 3–10 days (ECOWAS zone)        |
| Export (Global)      | Select SKUs                | Monthly          | [FREIGHT_FORWARDER]        | 15–45 days (sea freight)       |
| E-Commerce Fulfillment| Consumer SKUs             | Daily (as ordered)| [LAST_MILE_PROVIDER]      | 1–3 days                       |

---

## 4. Internal AMR Routing (Intra-Factory)

AMRs handle all internal material movements. The MES assigns AMR tasks automatically based on production orders and inventory signals.

### 4.1 AMR Task Types

| Task Type             | Trigger                              | From Zone         | To Zone          | AMR Type       |
|-----------------------|--------------------------------------|-------------------|------------------|----------------|
| Raw Material Delivery | MES kitting release                  | RMS (Stores)      | STG (Staging)    | Transport AMR  |
| Kit Delivery          | Production order line start          | STG (Staging)     | PL[A/B/C] Station | Transport AMR |
| WIP Transfer          | Station cycle complete               | PL Station        | Next Station     | Transport AMR  |
| QC Transfer           | IPQC trigger                         | Production Line   | IPQC Zone        | Transport AMR  |
| Finished Goods Move   | FQC PASS + pack complete             | PKG Zone          | FGW Zone         | Transport AMR  |
| Dispatch Loading      | Despatch order released              | FGW Zone          | LD-OUT Dock      | Heavy AMR      |
| Empty Pallet Return   | Pallet empty signal                  | Any zone          | Pallet Store     | Transport AMR  |
| Scrap Removal         | Scrap bin weight sensor              | Production zones  | Scrap Bay        | Transport AMR  |
| Consumable Replenishment | Line-side kanban trigger          | Consumables Store | Production lines | Small AMR      |

### 4.2 AMR Task Priority Levels

| Priority | Level      | Examples                                      | Response Time SLA |
|----------|------------|-----------------------------------------------|-------------------|
| P1       | Emergency  | E-stop response, fire evacuation assistance   | Immediate         |
| P2       | Critical   | Production line material starvation risk      | < 2 minutes       |
| P3       | Standard   | Normal WIP transfer, kit delivery             | < 5 minutes       |
| P4       | Routine    | Empty pallet return, scrap removal            | < 15 minutes      |
| P5       | Deferred   | Overnight re-stocking, batch consolidation    | Scheduled window  |

---

## 5. Cross-Factory Dependencies

[FACTORY_NAME] is an integrated node within the Coo-Cah manufacturing network. The following cross-factory material flows apply:

### 5.1 Inbound Dependencies (Materials Received FROM Sister Factories)

| Factory                          | Material / Component          | Frequency    | Volume (Phase 1)   | Backup if unavailable              |
|----------------------------------|-------------------------------|--------------|--------------------|------------------------------------|
| [SISTER_FACTORY_1]               | [COMPONENT]                   | Weekly       | [VOLUME]           | Import from [COUNTRY] (3PL)        |
| [SISTER_FACTORY_2]               | [COMPONENT]                   | Bi-weekly    | [VOLUME]           | Local supplier [NAME] (qualified)  |
| Coo-Cah Plastics Factory         | Plastic casings, housings      | Weekly       | [VOLUME]           | Import from China (4-week lead)    |
| Coo-Cah Metals Factory           | Stampings, chassis parts       | Monthly      | [VOLUME]           | Local steel fabricator             |
| Coo-Cah Packaging Hub            | Branded cartons, manuals       | Weekly       | [VOLUME]           | Local printer (approved alternate) |

### 5.2 Outbound Dependencies (Materials Supplied TO Sister Factories)

| Factory                          | Material / Component          | Frequency    | Volume (Phase 1)   | Notes                              |
|----------------------------------|-------------------------------|--------------|--------------------|------------------------------------|
| [SISTER_FACTORY_1]               | [COMPONENT]                   | Weekly       | [VOLUME]           | Just-in-time delivery              |
| Coo-Cah Distribution Hub         | Finished goods                | Daily        | [VOLUME]           | Primary outbound channel           |
| Coo-Cah Export Terminal          | Export-ready palletised goods  | Weekly       | [VOLUME]           | Pre-cleared with SON cert          |

### 5.3 Shared Services

| Service                          | Provider                      | Consumers at This Factory         |
|----------------------------------|-------------------------------|-----------------------------------|
| Coo-Cah MES Platform             | Coo-Cah Technology Division   | All factory operations            |
| Coo-Cah AI Platform              | Coo-Cah Technology Division   | Quality, maintenance, scheduling  |
| Coo-Cah HR/Payroll System        | Coo-Cah HR Division           | All employees                     |
| Coo-Cah ERP (Finance/Procurement)| Coo-Cah Finance Division      | Procurement, invoicing, inventory |
| Coo-Cah Quality Lab (Central)    | Coo-Cah Quality Division      | Type testing, certification samples |

---

## 6. Demand Planning & Replenishment

### 6.1 Demand Planning Process

| Step | Activity                            | Frequency  | System                          | Owner                  |
|------|-------------------------------------|------------|---------------------------------|------------------------|
| 1    | Sales demand signal received        | Daily      | ERP → MES                       | Sales / Planning       |
| 2    | AI demand forecast generated        | Weekly     | Coo-Cah AI Platform (time-series forecasting) | Planning  |
| 3    | Production schedule optimised       | Daily      | MES Scheduler + AI Optimiser    | Production Planning    |
| 4    | MRP (Material Requirements Planning) run | Daily | MES MRP module                  | Supply Chain           |
| 5    | Purchase requisitions auto-generated | As needed | MES → ERP trigger               | Procurement            |
| 6    | Purchase orders issued to suppliers  | Per run    | ERP                             | Procurement            |
| 7    | Supplier acknowledgements confirmed  | Per PO     | ERP supplier portal             | Procurement            |
| 8    | Inbound monitoring vs schedule       | Daily      | ERP + MES GRN tracking          | Supply Chain           |

### 6.2 Safety Stock Policy

| Component Category           | Safety Stock Method              | Target (Days of Supply) |
|------------------------------|----------------------------------|-------------------------|
| Critical imported components | Demand × lead time × variability | 60 days                 |
| Standard imported components | Reorder point formula            | 30 days                 |
| Locally sourced components   | Kanban / min-max                 | 14 days                 |
| Packaging materials          | Kanban                           | 30 days                 |
| Consumables (MRO)            | Min-max                          | 21 days                 |

---

## 7. Logistics Provider Requirements

All third-party logistics providers used by [FACTORY_NAME] must meet the following minimum requirements:

| Requirement                          | Standard                                              |
|--------------------------------------|-------------------------------------------------------|
| Operating Licence                    | Valid Nigerian Road Transport operating licence       |
| Vehicle Condition                    | ≤ [N] years old; roadworthy certificate current       |
| Insurance                            | Comprehensive goods-in-transit insurance (minimum ₦[VALUE]) |
| GPS Tracking                         | Real-time vehicle GPS with API for MES integration    |
| Cold Chain (if applicable)           | Temperature monitoring and cold store at depot        |
| EHS Compliance                       | Driver HSE induction by Coo-Cah before first delivery |
| Performance SLA                      | On-time delivery ≥ 95%; damage rate ≤ 0.1%          |
| Security                             | Tamper-evident seals; chain of custody documentation  |
| Annual Review                        | Coo-Cah Supply Chain annual logistics provider review |

---

## 8. Import / Export Procedures

### 8.1 Inbound Imports

| Step | Activity                            | Responsible            | Key Documents                        |
|------|-------------------------------------|------------------------|--------------------------------------|
| 1    | PO placed with overseas supplier    | Procurement            | Purchase Order                       |
| 2    | Supplier ships goods (Sea / Air)    | Supplier               | Bill of Lading / AWB, Packing List   |
| 3    | Pre-arrival declaration             | Customs Agent          | NCS Form M, Import Declaration       |
| 4    | Port clearance                      | Customs Agent          | Customs duty payment, SON pre-clearance |
| 5    | Delivery to factory                 | Freight Company        | Delivery Note, GRN                   |
| 6    | IQC inspection                      | Quality Team           | IQC Report                           |

### 8.2 Outbound Exports

| Step | Activity                            | Responsible            | Key Documents                        |
|------|-------------------------------------|------------------------|--------------------------------------|
| 1    | Export order confirmed              | Sales / Planning       | Sales Order, Export Proforma Invoice |
| 2    | SON Export Certificate obtained     | Quality/Compliance     | SON Product Certificate              |
| 3    | NXP (Nigerian Export Proceeds) form | Finance / Bank         | NXP Form                             |
| 4    | Cargo booked (sea/air)              | Logistics              | Booking Confirmation                 |
| 5    | Customs export clearance            | Customs Agent          | Form NCD 4, Export Declaration       |
| 6    | Goods shipped                       | Logistics              | Bill of Lading / AWB                 |

---

*For CapEx implications of safety stock financing, refer to [`capex-opex.md`](./capex-opex.md).*
*For regulatory compliance in imports/exports, refer to [`regulatory.md`](./regulatory.md).*
