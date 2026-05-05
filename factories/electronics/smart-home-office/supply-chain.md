# Smart Home & Office Electronics Factory — Supply Chain Management

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Smart Home & Office Electronics Factory | **Location:** Agbara Industrial Estate, Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Supply Chain & Procurement Team

---

## 1. Supply Chain Overview

This factory has the most complex BOM structure in the Coo-Cah Electronics vertical, sourcing display panels, SoCs, Wi-Fi/BT modules, optical engines (projectors), and laptop chassis from China, Taiwan, and South Korea, while relying on intra-group supply from Coo-Cah Plastics for housings. Display panels (32" to 65") are the highest-value, most logistics-intensive component.

| Supply Category                  | Origin                         | % BOM Cost | Lead Time    | Key Risk                           |
|----------------------------------|--------------------------------|------------|--------------|------------------------------------|
| LCD / QLED Display Panels (TVs)  | Import — BOE, Tianma (China)   | 30%        | 8–12 weeks   | Panel demand seasonality; price    |
| TV System-on-Chip (MediaTek)     | Import — China                 | 6%         | 8–10 weeks   | SoC allocation risk                |
| OLED / IPS Laptop Display        | Import — BOE, LG Display       | 12%        | 8–10 weeks   | Laptop display spec match          |
| Laptop SoC (Intel/AMD)           | Import — Intel/AMD distributors| 18%        | 6–10 weeks   | Semiconductor allocation           |
| Wi-Fi 6 + BT Modules (Realtek)   | Import — China / Taiwan        | 4%         | 6–8 weeks    | NCC TA qualification               |
| Zigbee + BLE SoC (Hub)           | Import — Silicon Labs, NXP     | 3%         | 6–8 weeks    | NCC multi-radio TA                 |
| DLP Optical Engine (Projectors)  | Import — Texas Instruments     | 8%         | 10–14 weeks  | TI DLP supply programme            |
| Acoustic Drivers (Speakers)      | Import — Tymphany / local OEM  | 4%         | 6–8 weeks    | Acoustic tuning per model          |
| Bare PCBs                        | Import — China / Taiwan        | 3%         | 4–6 weeks    | Board quality                      |
| SMT Passives                     | Import — Yageo, Samsung        | 4%         | 4–8 weeks    | Standard lead time                 |
| TV / Speaker Plastic Housings    | **Coo-Cah Plastics Factory**  | 6%         | **1–2 days** | Internal capacity constraint       |
| Laptop Chassis (Aluminium)       | Import — ODM/OEM China         | 4%         | 8–10 weeks   | ODM tooling lead time              |
| Packaging — Cartons + EPS foam   | **Local (Lagos printers)**    | 2%         | 1–2 weeks    | Local quality management           |

---

## 2. Import Logistics

### 2.1 Inbound Freight Routes

| Route                         | Mode       | Port of Entry    | Transit (CIF Lagos) | Notes                             |
|-------------------------------|------------|------------------|----------------------|-----------------------------------|
| TV panels (China — BOE)       | Sea FCL    | Tin Can Island   | 22–28 days           | Flat-pack; special foam packaging |
| SoCs, Wi-Fi modules (China)   | Air Freight| Lagos MMIA       | 3–5 days             | High-value; air only              |
| Laptop displays (China/Korea) | Sea LCL    | Tin Can Island   | 22–28 days           | Fragile; foam interleaved         |
| Intel/AMD CPUs                | Air Freight| Lagos MMIA       | 3–5 days             | High-value                        |
| DLP optical engines (USA/TW)  | Air Freight| Lagos MMIA       | 3–5 days             | High-value; lead time critical    |
| Laptop chassis (China ODM)    | Sea FCL    | Tin Can Island   | 22–28 days           | Full containers per model         |
| PCBs + SMT components         | Sea LCL    | Tin Can Island   | 24–30 days           | Standard                          |

### 2.2 Safety Stock Policy

| Component                    | Safety Stock | Reorder Point | Justification                         |
|------------------------------|--------------|---------------|---------------------------------------|
| TV Display Panels (all sizes)| 45 days      | 30 days       | Sea freight; panel demand seasonality |
| TV / Laptop SoCs             | 90 days      | 60 days       | Semiconductor allocation risk         |
| Laptop CPUs (Intel/AMD)      | 90 days      | 60 days       | High allocation risk; air freight only|
| DLP Optical Engines          | 60 days      | 45 days       | TI DLP supply programme access        |
| Wi-Fi / BT Modules           | 45 days      | 30 days       | NCC TA qualification dependency       |
| Laptop Chassis               | 30 days      | 20 days       | ODM tooling schedule dependency       |
| Plastic Housings (Coo-Cah)  | 7 days       | 3 days        | Intra-group daily delivery            |

---

## 3. Intra-Group Supply Links

### 3.1 Coo-Cah Plastics Factory → Smart Home & Office

| Component                      | Spec                              | Daily Volume   | Notes                      |
|--------------------------------|-----------------------------------|----------------|----------------------------|
| Smart TV rear housing + stand  | ABS/HIPS, black matte             | 150 units      | Size-specific tooling sets |
| Smart Speaker housing (S + L)  | PC/ABS, fabric insert compatible  | 300 units      |                            |
| Router housing                 | ABS, ventilated, white            | 600 units      |                            |
| Home Automation Hub housing    | ABS, LED diffuser panel           | 200 units      |                            |
| Smart Display bezel            | ABS, touch-clean surface coating  | 80 units       |                            |
| Projector housing              | ABS, heat-resistant vented design | 50 units       |                            |

---

## 4. Phase 2+ Targets

| Component              | Phase 1 Source   | Phase 2 Target                                    |
|------------------------|------------------|---------------------------------------------------|
| TV Display Panels      | Fully imported   | Regional display distributor hub (Lagos bonded)   |
| Laptop Chassis         | China ODM        | Investigate local Al-alloy machining by Phase 3   |
| Wi-Fi/BT Modules       | Imported         | Evaluate Coo-Cah module assembly (Phase 3)        |
| TV/Speaker housings    | Coo-Cah Plastics | ✅ Already intra-group                             |
| Packaging              | Local            | ✅ Already 100% local                              |

---

*Refer to [`capex-opex.md`](./capex-opex.md) for BOM cost modelling.*
*Refer to [`regulatory.md`](./regulatory.md) for NCC TA and SON CoC requirements.*
