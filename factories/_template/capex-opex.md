# [FACTORY_NAME] — CapEx & OpEx Financial Model

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** [FACTORY_NAME] | **Location:** [LOCATION] | **Phase:** [PHASE]
> **Document Version:** 1.0 | **Owner:** Coo-Cah Finance Division
> **Currency:** Nigerian Naira (₦) unless noted. USD equivalent at ₦[RATE]/USD exchange rate as of [DATE].

---

## 1. Executive Financial Summary

| Metric                              | Phase 1                  | Phase 2                  | Phase 3                  |
|-------------------------------------|--------------------------|--------------------------|--------------------------|
| Total CapEx                         | ₦[AMOUNT]                | ₦[AMOUNT]                | ₦[AMOUNT]                |
| Annual Revenue (at full capacity)   | ₦[AMOUNT]                | ₦[AMOUNT]                | ₦[AMOUNT]                |
| Annual OpEx                         | ₦[AMOUNT]                | ₦[AMOUNT]                | ₦[AMOUNT]                |
| EBITDA Margin (at capacity)         | [%]%                     | [%]%                     | [%]%                     |
| Simple Payback Period               | [N] years                | —                        | —                        |
| Net Present Value (10yr, [R]% disc) | ₦[AMOUNT]                | —                        | —                        |
| IRR                                 | [%]%                     | —                        | —                        |

---

## 2. Capital Expenditure (CapEx) — Phase 1

### 2.1 CapEx Breakdown

#### 2.1.1 Land & Civil Works

| Category                | Item                                    | Unit Cost (₦)  | Quantity        | Total (₦)       | Notes                          |
|-------------------------|-----------------------------------------|----------------|-----------------|-----------------|--------------------------------|
| Land                    | Factory site acquisition / lease        | [UNIT_COST]    | [AREA] m²       | [TOTAL]         | [Owned / Leased — [TERM] yr]   |
| Civil Works             | Factory building construction           | [UNIT_COST]/m² | [AREA] m²       | [TOTAL]         | Steel frame + cladding         |
| Civil Works             | Office / amenities block                | [UNIT_COST]/m² | [AREA] m²       | [TOTAL]         |                                |
| Civil Works             | Warehouse construction                  | [UNIT_COST]/m² | [AREA] m²       | [TOTAL]         |                                |
| Civil Works             | Loading dock construction ([N] bays)    | [UNIT_COST]    | [N] bays        | [TOTAL]         |                                |
| Infrastructure          | Roads, drainage, perimeter fence        | [UNIT_COST]    | Lump sum        | [TOTAL]         |                                |
| Infrastructure          | Water supply, borehole, treatment       | [UNIT_COST]    | Lump sum        | [TOTAL]         |                                |
| Infrastructure          | Fire hydrant system                     | [UNIT_COST]    | Lump sum        | [TOTAL]         |                                |
| **Land & Civil Subtotal** |                                       |                |                 | **[SUBTOTAL]**  |                                |

#### 2.1.2 Production Equipment

| Category                | Item                                    | Unit Cost (₦)  | Quantity        | Total (₦)       | Supplier / Source              |
|-------------------------|-----------------------------------------|----------------|-----------------|-----------------|--------------------------------|
| [PRODUCTION_LINE_A]     | [MACHINE_1]                             | [UNIT_COST]    | [QTY]           | [TOTAL]         | [OEM / Import / Local]         |
| [PRODUCTION_LINE_A]     | [MACHINE_2]                             | [UNIT_COST]    | [QTY]           | [TOTAL]         |                                |
| [PRODUCTION_LINE_A]     | [MACHINE_3]                             | [UNIT_COST]    | [QTY]           | [TOTAL]         |                                |
| [PRODUCTION_LINE_B]     | [MACHINE_4]                             | [UNIT_COST]    | [QTY]           | [TOTAL]         |                                |
| [PRODUCTION_LINE_B]     | [MACHINE_5]                             | [UNIT_COST]    | [QTY]           | [TOTAL]         |                                |
| QC Equipment            | [QC_MACHINE_1]                          | [UNIT_COST]    | [QTY]           | [TOTAL]         |                                |
| QC Equipment            | [QC_MACHINE_2]                          | [UNIT_COST]    | [QTY]           | [TOTAL]         |                                |
| Packaging Equipment     | Auto carton erector, sealer, wrapper    | [UNIT_COST]    | Lump sum        | [TOTAL]         |                                |
| **Production Equip. Subtotal** |                                  |                |                 | **[SUBTOTAL]**  |                                |

#### 2.1.3 Material Handling Equipment

| Category                | Item                                    | Unit Cost (₦)  | Quantity        | Total (₦)       | Notes                          |
|-------------------------|-----------------------------------------|----------------|-----------------|-----------------|--------------------------------|
| AMR Fleet               | Autonomous Mobile Robots ([MODEL])      | [UNIT_COST]    | [QTY] units     | [TOTAL]         | Incl. fleet mgmt. software     |
| AMR Infrastructure      | Charging docks, Wi-Fi 6 APs             | [UNIT_COST]    | Lump sum        | [TOTAL]         |                                |
| Conveyors               | Belt and roller conveyor systems        | [UNIT_COST]    | [LM] lin. metres | [TOTAL]        |                                |
| Forklifts               | Electric counterbalance forklift        | [UNIT_COST]    | [QTY]           | [TOTAL]         |                                |
| Racking                 | Selective pallet racking system         | [UNIT_COST]    | [N] bays        | [TOTAL]         |                                |
| VLM                     | Vertical Lift Module                    | [UNIT_COST]    | [QTY]           | [TOTAL]         |                                |
| **Material Handling Subtotal** |                                  |                |                 | **[SUBTOTAL]**  |                                |

#### 2.1.4 Energy Infrastructure

| Category                | Item                                    | Unit Cost (₦)  | Quantity        | Total (₦)       | Notes                          |
|-------------------------|-----------------------------------------|----------------|-----------------|-----------------|--------------------------------|
| Solar PV                | Monocrystalline panels ([W]W each)      | [UNIT_COST]    | [QTY] panels    | [TOTAL]         | ₦[PRICE]/Wp installed          |
| Solar PV                | Mounting structure + installation       | [UNIT_COST]    | [KWP] kWp       | [TOTAL]         |                                |
| BESS                    | LFP battery system ([KWH] kWh)          | [UNIT_COST]    | [KWH] kWh       | [TOTAL]         | ₦[PRICE]/kWh                   |
| Inverter / PCS          | Hybrid string inverters                 | [UNIT_COST]    | [QTY]           | [TOTAL]         |                                |
| HV/LV Substation        | Transformer + switchgear                | [UNIT_COST]    | Lump sum        | [TOTAL]         |                                |
| Generator               | Diesel standby generator ([KVA] kVA)    | [UNIT_COST]    | [QTY]           | [TOTAL]         |                                |
| ATS                     | Automatic Transfer Switch               | [UNIT_COST]    | [QTY]           | [TOTAL]         |                                |
| EMS                     | Energy Management System software       | [UNIT_COST]    | Lump sum        | [TOTAL]         |                                |
| **Energy Infra. Subtotal** |                                     |                |                 | **[SUBTOTAL]**  |                                |

#### 2.1.5 IT / MES / Automation Infrastructure

| Category                | Item                                    | Unit Cost (₦)  | Quantity        | Total (₦)       | Notes                          |
|-------------------------|-----------------------------------------|----------------|-----------------|-----------------|--------------------------------|
| MES Software            | Coo-Cah MES Core licence + setup        | [UNIT_COST]    | Lump sum        | [TOTAL]         | Or SaaS subscription — see OpEx |
| MES Hardware            | Industrial panel PCs (shop floor)       | [UNIT_COST]    | [QTY]           | [TOTAL]         |                                |
| MES Hardware            | MES server / edge computing nodes       | [UNIT_COST]    | [QTY]           | [TOTAL]         |                                |
| IoT Gateways            | OPC-UA / MQTT gateways                  | [UNIT_COST]    | [QTY]           | [TOTAL]         |                                |
| Network                 | Industrial switches, Wi-Fi 6 APs        | [UNIT_COST]    | Lump sum        | [TOTAL]         |                                |
| CCTV / Security         | IP cameras, NVR, access control         | [UNIT_COST]    | Lump sum        | [TOTAL]         |                                |
| **IT / MES Subtotal**   |                                         |                |                 | **[SUBTOTAL]**  |                                |

#### 2.1.6 Other CapEx

| Category                | Item                                    | Unit Cost (₦)  | Quantity        | Total (₦)       | Notes                          |
|-------------------------|-----------------------------------------|----------------|-----------------|-----------------|--------------------------------|
| Tooling & Jigs          | Production tooling, test fixtures       | [UNIT_COST]    | Lump sum        | [TOTAL]         |                                |
| Moulds (if plastic)     | Injection mould tooling per product     | [UNIT_COST]    | [QTY] moulds    | [TOTAL]         |                                |
| EHS Equipment           | Fire suppression, eye wash, spill kits  | [UNIT_COST]    | Lump sum        | [TOTAL]         |                                |
| Training & Commissioning| Equipment commissioning, training costs | [UNIT_COST]    | Lump sum        | [TOTAL]         |                                |
| Contingency             | 10% contingency on above CapEx          | —              | 10%             | [TOTAL]         |                                |
| **Other CapEx Subtotal** |                                        |                |                 | **[SUBTOTAL]**  |                                |

### 2.2 Total Phase 1 CapEx Summary

| CapEx Category                  | Total (₦)       | % of Total CapEx |
|---------------------------------|-----------------|------------------|
| Land & Civil Works              | [AMOUNT]        | [%]%             |
| Production Equipment            | [AMOUNT]        | [%]%             |
| Material Handling Equipment     | [AMOUNT]        | [%]%             |
| Energy Infrastructure           | [AMOUNT]        | [%]%             |
| IT / MES / Automation           | [AMOUNT]        | [%]%             |
| Other CapEx                     | [AMOUNT]        | [%]%             |
| **TOTAL PHASE 1 CAPEX**         | **[TOTAL]**     | **100%**         |

---

## 3. Annual Operating Expenditure (OpEx)

### 3.1 OpEx Breakdown (Annual — at Phase 1 Full Capacity)

| Category                    | Sub-Item                                | Annual Cost (₦) | Notes                                         |
|-----------------------------|-----------------------------------------|-----------------|-----------------------------------------------|
| Labour — Direct             | Production operators ([N] staff)        | [COST]          | Salary, pension, NHF, NSITF                  |
| Labour — Indirect           | Supervisors, QA, maintenance, managers  | [COST]          | Including management team                    |
| Labour — Total              |                                         | **[TOTAL]**     | Fully-burdened labour cost                   |
| Raw Materials               | Direct materials (BoM cost × volume)    | [COST]          | Variable with production volume              |
| Packaging                   | Cartons, labels, inserts                | [COST]          | Variable with production volume              |
| Energy — Grid Import        | Grid electricity (after solar)          | [COST]          | [GRID_KWH] kWh/year × ₦[TARIFF]/kWh        |
| Energy — Generator          | Diesel fuel (emergency/backup)          | [COST]          | < 100 hrs/year target                        |
| Maintenance — Planned       | Spare parts, lubricants, consumables    | [COST]          | ~2–3% of production equipment CapEx/year    |
| Maintenance — Unplanned     | Emergency repairs, call-out             | [COST]          | Contingency estimate                         |
| MES / IT Subscriptions      | Coo-Cah platform SaaS fees             | [COST]          | Per-factory annual licence                   |
| Quality & Certification     | Lab testing, SON renewals, audits       | [COST]          | Compliance cost                              |
| Logistics (Outbound)        | Third-party logistics (delivery)        | [COST]          | Variable with volume                         |
| Logistics (Inbound)         | Freight, customs clearance              | [COST]          | Variable with import volume                  |
| Occupancy                   | Rent / land lease (if leased)           | [COST]          | If land owned, this is rates/taxes only      |
| Insurance                   | Factory all-risk, product liability, etc. | [COST]        | Annual premium                               |
| EHS & Compliance            | Permits, waste disposal, monitoring     | [COST]          | NESREA, SON, NEPC fees                       |
| Training & Development      | Staff training, Coo-Cah Academy fees   | [COST]          | Annual budget                                |
| General & Administrative    | Office supplies, communications, travel | [COST]          | Overhead allocation                          |
| **TOTAL ANNUAL OPEX**       |                                         | **[TOTAL]**     | At Phase 1 full capacity                     |

---

## 4. Unit Economics

| Metric                                   | Value         | Notes                                        |
|------------------------------------------|---------------|----------------------------------------------|
| Annual Production Volume (Phase 1)       | [N] units     | Across all SKUs                              |
| Average Selling Price (ASP)              | ₦[ASP]        | Blended across SKU mix                       |
| **Annual Revenue (at capacity)**         | **₦[REV]**    |                                              |
| Total BoM Cost per Unit                  | ₦[BOM]        | Direct materials + packaging                 |
| Labour Cost per Unit                     | ₦[LAB]        | Direct labour only                           |
| Energy Cost per Unit                     | ₦[ENERGY]     |                                              |
| Other Variable Cost per Unit             | ₦[OTHER]      |                                              |
| **Total Variable Cost per Unit (COGS)**  | **₦[COGS]**   |                                              |
| Gross Margin per Unit                    | ₦[GM]         | = ASP − COGS                                 |
| **Gross Margin %**                       | **[GM%]%**    |                                              |
| Fixed OpEx (annual)                      | ₦[FIXED]      | Labour (fixed portion) + occupancy + IT + overhead |
| Fixed Cost per Unit (at volume)          | ₦[FIXED_U]    |                                              |
| **EBITDA per Unit**                      | **₦[EBITDA_U]** |                                            |
| **EBITDA Margin**                        | **[%]%**      |                                              |

---

## 5. Payback Period Analysis

| Year | CapEx Deployed (₦) | Annual EBITDA (₦) | Cumulative Net Position (₦) | Notes                          |
|------|--------------------|--------------------|------------------------------|--------------------------------|
| 0    | ([CAPEX])          | 0                  | ([CAPEX])                    | Construction/pre-production    |
| 1    | 0                  | [EBITDA_Y1]        | ([Y1_NET])                   | Ramp-up year (~60% capacity)   |
| 2    | 0                  | [EBITDA_Y2]        | ([Y2_NET])                   | Full Phase 1 capacity          |
| 3    | 0                  | [EBITDA_Y3]        | ([Y3_NET])                   | Optimisation gains kick in     |
| 4    | ([P2_CAPEX])       | [EBITDA_Y4]        | ([Y4_NET])                   | Phase 2 CapEx deployed         |
| 5    | 0                  | [EBITDA_Y5]        | ([Y5_NET])                   | Phase 2 capacity achieved      |
| 6    | 0                  | [EBITDA_Y6]        | [Y6_NET]                     | **Payback achieved**           |
| 7    | 0                  | [EBITDA_Y7]        | [Y7_NET]                     | Net positive cash              |
| 8    | 0                  | [EBITDA_Y8]        | [Y8_NET]                     |                                |
| 9    | 0                  | [EBITDA_Y9]        | [Y9_NET]                     |                                |
| 10   | 0                  | [EBITDA_Y10]       | [Y10_NET]                    |                                |

**Simple Payback Period:** [N] years
**Discounted Payback Period:** [N] years (at [RATE]% discount rate)
**10-Year NPV:** ₦[NPV]
**IRR:** [IRR]%

---

## 6. Sensitivity Analysis

| Variable                    | Base Case    | Bear Case (−20%)  | Bull Case (+20%) | NPV Impact (Bear/Bull)  |
|-----------------------------|--------------|-------------------|------------------|-------------------------|
| Average Selling Price       | ₦[ASP]       | ₦[ASP_BEAR]       | ₦[ASP_BULL]      | (₦[BEAR_NPV]) / ₦[BULL_NPV] |
| Production Volume           | [N] units    | [N_BEAR] units    | [N_BULL] units   | (₦[BEAR_NPV]) / ₦[BULL_NPV] |
| Raw Material Cost           | ₦[BOM]       | ₦[BOM_BEAR]       | ₦[BOM_BULL]      | (₦[BEAR_NPV]) / ₦[BULL_NPV] |
| USD/NGN Exchange Rate       | ₦[RATE]      | ₦[RATE_BEAR]      | ₦[RATE_BULL]     | (₦[BEAR_NPV]) / ₦[BULL_NPV] |
| Energy Cost                 | ₦[TARIFF]/kWh| ₦[TARIFF_BEAR]    | ₦[TARIFF_BULL]   | (₦[BEAR_NPV]) / ₦[BULL_NPV] |

---

## 7. Funding Strategy

| Funding Source                    | Amount (₦)   | % of Total CapEx | Terms / Notes                               |
|-----------------------------------|--------------|------------------|---------------------------------------------|
| Coo-Cah Equity (founders/investors)| [AMOUNT]    | [%]%             | Equity injection                            |
| Development Bank Loan (DFI)        | [AMOUNT]    | [%]%             | e.g., DBN, BOI — [TERM] yr, [RATE]%        |
| Equipment Leasing                  | [AMOUNT]    | [%]%             | For key production equipment                |
| Export Credit Financing            | [AMOUNT]    | [%]%             | For imported equipment (ECA-backed)         |
| Pioneer Status Tax Savings         | [AMOUNT]    | [%]%             | NIPC Pioneer Status — [N]-year tax holiday  |
| **Total Funding**                  | **[TOTAL]** | **100%**         |                                             |

---

*For energy infrastructure CapEx detail, refer to [`energy-profile.md`](./energy-profile.md).*
*For machinery procurement, refer to [`machinery.md`](./machinery.md).*
*For incentives detail, refer to [`regulatory.md`](./regulatory.md).*
