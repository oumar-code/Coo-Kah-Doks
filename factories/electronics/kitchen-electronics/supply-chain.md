# Kitchen Electronics Factory — Supply Chain Management

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Kitchen Electronics Factory | **Location:** Agbara Industrial Estate, Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Supply Chain & Procurement Team

---

## 1. Supply Chain Overview

The Kitchen Electronics Factory supply chain is characterised by a mix of high-value imported sub-assemblies (compressors, magnetrons, induction modules), imported PCB components, and domestically sourced materials (steel sheet, packaging, plastics). The strategy targets maximum Nigerian content in packaging and structural materials while importing irreplaceable technology components with 90-day safety stock to buffer the 22–28-day sea freight transit.

| Supply Category                     | Origin                | % of BOM Cost | Lead Time    | Key Risk                       |
|-------------------------------------|-----------------------|---------------|--------------|--------------------------------|
| Compressors (fridges)               | Import — Embraco/Secop (Brazil/Slovakia) | 22% | 10–14 weeks | Long lead time; single-spec    |
| Magnetrons (microwaves)             | Import — Galanz/LG (China)   | 12%   | 8–12 weeks   | Tech refresh; import duty      |
| IGBT Modules (induction cookers)    | Import — Infineon (Germany/China) | 8% | 8–10 weeks  | Supply allocation              |
| SMT Components (ICs, caps, MOSFETs) | Import — China (multi) | 10%   | 4–8 weeks    | Reel fragmentation             |
| Bare PCBs                           | Import — China/Taiwan | 6%            | 4–6 weeks    | Board quality; Forex           |
| R600a Refrigerant                   | Import — licensed distributor | 4%  | 4–6 weeks    | Controlled substance           |
| Steel Sheet Metal (fridge cabinets) | **Local — Nigerian steel service centres** | 8% | 1–2 weeks | Steel price volatility   |
| PU Foam System (polyol + isocyanate)| Import + Local        | 5%            | 2–4 weeks    | Chemical compatibility         |
| Plastic Casings (microwave, SDA)    | **Coo-Cah Plastics Factory** | 6%  | **1–2 days** | Internal capacity              |
| PCB copper-clad laminate (internal) | Import (China)        | 3%            | 4–6 weeks    | Laminate quality               |
| Packaging — Cartons, EPS foam       | **Local (Lagos printers + moulders)** | 4% | 1–2 weeks | Local quality management |
| Heating Elements (kettle/toaster)   | Import + Local       | 3%            | 3–5 weeks    | Local supplier development     |
| Motors (blenders)                   | Import — China        | 4%            | 6–8 weeks    | Motor quality spec matching    |
| Tempered Glass (induction tops)     | Import — China        | 5%            | 8–10 weeks   | Fragile; careful packaging     |

---

## 2. Import Logistics

### 2.1 Inbound Freight Routes

| Route                          | Mode      | Port of Entry       | Transit Time (CIF Lagos) | Cost (per 40ft HQ) |
|--------------------------------|-----------|---------------------|--------------------------|--------------------|
| Compressors (Brazil)           | Sea FCL   | Apapa Port, Lagos   | 18–22 days               | ~$4,200–$5,000     |
| Compressors (Slovakia)         | Sea FCL   | Apapa / Tin Can     | 22–28 days               | ~$4,500–$5,500     |
| Magnetrons (China)             | Sea FCL   | Tin Can Island      | 22–28 days               | ~$3,500–$4,500     |
| SMT Components (China)         | Sea LCL   | Tin Can Island      | 28–35 days               | ~$180–$220/CBM     |
| PCBs (China/Taiwan)            | Sea LCL   | Tin Can Island      | 24–30 days               | ~$180–$220/CBM     |
| IGBT modules (urgent)          | Air Freight | Lagos MMIA         | 3–5 days                 | ~$7.00–$10.00/kg   |
| Tempered glass                 | Sea FCL   | Tin Can Island      | 22–28 days               | ~$3,500–$4,200     |

> **Standard routing:** Sea FCL via Tin Can Island preferred over Apapa (shorter dwell time, better container handling). Air freight reserved for urgent replenishment of high-value, low-weight components.

### 2.2 Nigeria Customs Process

| Step | Activity                                      | Lead Time Before Arrival | Responsible              |
|------|-----------------------------------------------|--------------------------|--------------------------|
| 1    | Form M application (CBN-accredited bank)      | 4–6 weeks before shipment| Finance + Procurement    |
| 2    | SON Conformity Assessment (CoC) request       | 4–8 weeks before shipment| Regulatory Affairs       |
| 3    | NCS Pre-Arrival Assessment Report (PAAR)      | 5 days before arrival    | Licensed customs agent   |
| 4    | NAFDAC notification (R600a, polyol chemical)  | 4–6 weeks pre-shipment   | Regulatory Affairs       |
| 5    | Terminal gate release + NCS examination       | 2–5 days post-arrival    | Customs agent            |
| 6    | Duty payment (e-customs)                      | Same day                 | Finance                  |
| 7    | Cargo release + bonded haulage to factory     | 1–2 days                 | Logistics coordinator    |
| 8    | Incoming QC + MES goods receipt scan          | Same day as delivery     | Stores + QC team         |

**Applicable Duties:**

| Category                       | HS Code Range   | Import Duty | VAT   | Surcharge |
|--------------------------------|-----------------|-------------|-------|-----------|
| Refrigerator compressors       | 8414.30         | 5%          | 7.5%  | 1.5%      |
| Magnetrons (microwave)         | 8540.11         | 5%          | 7.5%  | 1.5%      |
| IGBT / power electronics       | 8541.29         | 5%          | 7.5%  | 1.5%      |
| SMT passive components         | 8532.xx         | 5%          | 7.5%  | 1.5%      |
| Tempered glass                 | 7007.11         | 10%         | 7.5%  | 1.5%      |
| R600a refrigerant (isobutane)  | 2901.10         | 5%          | 7.5%  | 1.5%      |
| Blender motors                 | 8501.10         | 5%          | 7.5%  | 1.5%      |

---

## 3. Intra-Group Supply Links

### 3.1 Coo-Cah Plastics Factory → Kitchen Electronics

| Component Supplied               | Specification                    | Daily Volume   | Lead Time | Quality Gate           |
|----------------------------------|----------------------------------|----------------|-----------|------------------------|
| Microwave oven plastic housing   | ABS HH, food-grade coating       | 200 units/day  | 1–2 days  | Dimensional + cosmetic |
| Microwave door inner frame       | ABS, microwave-transparent       | 200 units/day  | 1–2 days  | Fit check + material cert |
| SDA housing sets (blender, kettle, rice cooker, toaster) | ABS/PP, food-grade | 1,500 sets/day | 1–2 days | Cosmetic class A |
| Refrigerator interior liner      | HIPS, food-safe, white           | 320 units/day  | 1–2 days  | Dimensional; no warping |
| Cooker control panel housing     | PC+ABS, heat-resistant           | 180 units/day  | 1–2 days  | Heat class rating       |

> *Logistics: Dedicated truck runs between Coo-Cah Plastics Factory and Kitchen Electronics, 2× daily. Distance: ~12 km within Agbara / Sagamu corridor.*

### 3.2 Coo-Cah Personal Electronics Factory → Kitchen Electronics

| Item Supplied                    | Specification                      | Volume          | Trigger               |
|----------------------------------|------------------------------------|-----------------|-----------------------|
| PCB assemblies (fridge control)  | CCK-PCB-FRIDGE (SMT assembled)     | 350 pcs/day     | When PE PCB line capacity available |
| PCB assemblies (SDA control)     | CCK-PCB-SDA (generic platform)     | 1,200 pcs/day   | Phase 2 target        |

> *Phase 1: Kitchen Electronics operates its own in-house SMT line for PCBs. Supply from Personal Electronics factory is a Phase 2 consolidation target.*

### 3.3 Coo-Cah Garage Power Electronics → Kitchen Electronics

| Item Supplied                    | Specification                         | Volume    | Lead Time | Notes                        |
|----------------------------------|---------------------------------------|-----------|-----------|------------------------------|
| UPS for critical MES servers     | CCG-UPS-1kVA (rack-mount)             | 8 units   | One-off   | Factory commissioning        |
| Inverter backup for gas zone     | CCG-INV-PSW-3kVA                      | 4 units   | One-off   | ATEX-compliant enclosure req |

---

## 4. Safety Stock Policy

| Component                    | Safety Stock Level          | Reorder Point               | Justification                                |
|------------------------------|-----------------------------|-----------------------------|----------------------------------------------|
| Compressors (all models)     | 60 days demand              | 45 days on-hand             | Long lead time (Brazil/Slovakia 22–28 days); port delays |
| Magnetrons                   | 45 days demand              | 30 days on-hand             | Single-source risk; Galanz lead times        |
| IGBT modules                 | 60 days demand              | 45 days on-hand             | Semiconductor allocation risk                |
| R600a refrigerant            | 30 days demand              | 15 days on-hand             | Controlled substance; licensed supplier; NESREA tracking |
| Tempered glass               | 30 days demand              | 20 days on-hand             | Fragile; high reject risk in transit         |
| SMT components (generic)     | 30 days demand              | 21 days on-hand             | Standard lead time manageable               |
| Plastics (from Coo-Cah)      | 7 days demand               | 3 days on-hand              | Intra-group; daily delivery                  |
| Steel sheet metal            | 10 days demand              | 5 days on-hand              | Local supply; high confidence                |
| Packaging (cartons, EPS)     | 10 days demand              | 5 days on-hand              | Local supply                                 |

---

## 5. Supplier Qualification

### 5.1 Approved Supplier List (ASL) — Phase 1

| Component Category           | Approved Supplier(s)                       | Country      | Qualification Status |
|------------------------------|--------------------------------------------|--------------|----------------------|
| Refrigerator Compressors     | Embraco (Nidec) + Secop                    | Brazil/Slovakia | Approved          |
| Magnetrons                   | Galanz; LG Components                      | China/Korea  | Approved             |
| IGBT Modules                 | Infineon Technologies; ON Semiconductor    | Germany/USA  | Approved             |
| SMT Passive Components       | Yageo; Samsung Electro-Mechanics           | Taiwan/Korea | Approved             |
| Bare PCBs                    | TTM Technologies; Tripod Technology        | USA/Taiwan   | Approved             |
| R600a Refrigerant            | Praxair / Linde Nigeria                    | Nigeria      | Approved             |
| Steel Sheet Metal            | Nippon Steel (via Lagos distributor)       | Japan/Local  | Approved             |
| PU Foam System               | BASF (polyol/isocyanate Nigeria distributor)| Germany/Local | Approved            |
| Blender Motors               | Johnson Electric; Mabuchi                  | China        | Approved             |
| Tempered Glass               | AGC Flat Glass; Schott                     | China/Germany| Approved             |
| Packaging — Cartons          | Lafarge Paper + local Lagos printers       | Nigeria      | Approved             |
| Packaging — EPS foam         | Local EPS moulders (Agbara corridor)       | Nigeria      | Approved             |

### 5.2 Supplier Scorecard

| Metric                      | Measurement Freq. | Minimum Score | Corrective Action Trigger |
|-----------------------------|-------------------|---------------|---------------------------|
| On-Time Delivery Rate       | Monthly           | ≥ 92%         | < 85% for 2 months        |
| Incoming Quality Pass Rate  | Per shipment      | ≥ 98%         | < 95% in any shipment     |
| Documentation Completeness  | Per shipment      | 100%          | Any missing cert/CoC      |
| Lead Time Adherence         | Monthly           | ± 5 days      | > 10-day variance         |

---

## 6. Phase 2+ Supply Chain Targets

| Component                    | Phase 1 Source       | Phase 2 Target                               |
|------------------------------|----------------------|----------------------------------------------|
| Refrigerator Compressors     | Fully imported       | Investigate local assembly of Embraco OEM kits |
| PCBs (kitchen appliance)     | In-house SMT         | Consolidate to Coo-Cah Personal Electronics SMT line |
| Steel inner liner            | Imported / Local     | Coo-Cah Steel/Plastics vertical (Phase 3)    |
| PU Foam chemicals            | Imported (BASF)      | Coo-Cah Chemicals Division (Phase 3)         |
| Packaging                    | Local — 100%         | ✅ Already achieved from Phase 1              |

---

*For CapEx / landed cost modelling, refer to [`capex-opex.md`](./capex-opex.md).*
*For regulatory compliance (Form M, SON CoC), refer to [`regulatory.md`](./regulatory.md).*
*For intra-group supply volumes and coordination procedures, refer to [`docs/intragroup-supply-coordination.md`](./docs/intragroup-supply-coordination.md).*
