# Security Electronics Factory — Supply Chain Management

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Security Electronics Factory | **Location:** Ikorodu Industrial Estate, Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Supply Chain & Procurement Team

---

## 1. Supply Chain Overview

The security electronics supply chain is characterised by optical components (CMOS image sensors, lenses, IR LEDs) as the most lead-time-constrained and value-intensive items. Hard disk drives (for NVRs) are the second critical category. All optical components require careful packaging and temperature-controlled storage to prevent contamination.

| Supply Category                 | Origin                           | % BOM Cost | Lead Time    | Key Risk                            |
|---------------------------------|----------------------------------|------------|--------------|-------------------------------------|
| CMOS Image Sensors              | Import — Sony, OmniVision (Japan/Taiwan) | 18% | 8–12 weeks | Allocation; sensor quality grade |
| Camera Lenses (varifocal, fixed)| Import — China OEM (Computar, Tamron-spec) | 10% | 6–10 weeks | Optical quality; cert variance |
| IR LEDs (940nm, 850nm)          | Import — Epistar, OSRAM (Taiwan/Germany) | 5% | 6–8 weeks  | Bin spec matching for IR uniformity|
| H.265 Video SoC (NVR/camera)    | Import — HiSilicon, Ambarella    | 12%        | 8–12 weeks   | Semiconductor allocation; export ctrl|
| Hard Disk Drives (NVR, 2–4TB)   | Import — Seagate Surveillance, WD Purple | 8% | 6–8 weeks | HDD price cycles; model availability|
| Biometric Sensor (RFID/fingerprint) | Import — IDEMIA, ZKTeco       | 5%         | 6–8 weeks    | Biometric spec certification        |
| SMT Passives, PCBs              | Import — China                   | 8%         | 4–8 weeks    | Standard                            |
| Wi-Fi / BT Modules              | Import — Realtek (China/Taiwan)  | 4%         | 6–8 weeks    | NCC TA qualification                |
| GSM Modules (alarm panels)      | Import — SIM7600 series          | 3%         | 6–8 weeks    | NCC TA; GSM certification           |
| Camera Housing (plastic)        | **Coo-Cah Plastics Factory**    | 8%         | **1–2 days** | Internal capacity                   |
| NVR / Access Control Housing    | **Coo-Cah Plastics Factory**    | 4%         | **1–2 days** | Internal capacity                   |
| Packaging                       | **Local (Lagos printers)**      | 3%         | 1–2 weeks    | Local quality management            |
| EPS foam, cable accessories     | Local / Import                   | 2%         | 1–3 weeks    |                                     |

---

## 2. Import Logistics

### 2.1 CMOS Sensor Special Handling

CMOS image sensors require:
- **Cold storage during transit:** 15–25°C; humidity < 60% RH; anti-ESD packaging
- **Port-to-factory transit:** Air-conditioned bonded haulage
- **Factory storage:** Sealed ESD containers in Z1 cold-store sub-zone (20°C ±2°C)
- **NCS clearance:** Electronics category; Form M; SON CoC

### 2.2 Inbound Freight Routes

| Route                         | Mode       | Port of Entry    | Transit (CIF Lagos) | Notes                              |
|-------------------------------|------------|------------------|----------------------|------------------------------------|
| CMOS sensors (Japan/Taiwan)   | Air Freight| Lagos MMIA       | 3–5 days             | Cold-chain; priority freight       |
| Lenses + IR LEDs (China/TW)   | Sea LCL    | Tin Can Island   | 22–28 days           | Standard ESD packaging             |
| H.265 SoCs (China)            | Air Freight| Lagos MMIA       | 3–5 days             | High-value; semiconductor          |
| HDDs (Thailand/China factory) | Sea FCL    | Tin Can Island   | 22–28 days           | Standard                           |
| Biometric sensors (China/TW)  | Air Freight| Lagos MMIA       | 3–5 days             | High-value; security import docs   |
| SMT components + PCBs (China) | Sea LCL    | Tin Can Island   | 24–30 days           | Standard                           |

### 2.3 Safety Stock Policy

| Component                    | Safety Stock | Reorder Point | Justification                               |
|------------------------------|--------------|---------------|---------------------------------------------|
| CMOS Image Sensors           | 90 days      | 60 days       | Allocation risk; cold chain constraint       |
| Camera Lenses                | 45 days      | 30 days       | Optical quality matching; sea freight        |
| H.265 Video SoCs             | 90 days      | 60 days       | Semiconductor allocation risk                |
| Hard Disk Drives             | 30 days      | 20 days       | HDD price cycle management                  |
| IR LEDs                      | 45 days      | 30 days       | Bin matching for uniformity                  |
| Wi-Fi / GSM Modules          | 45 days      | 30 days       | NCC TA dependency                           |
| Camera Housings (Coo-Cah)   | 7 days       | 3 days        | Intra-group daily delivery                   |
| HDDs — AI NVR (4TB+)         | 45 days      | 30 days       | AI NVR uses premium surveillance HDDs       |

---

## 3. Intra-Group Supply Links

### 3.1 Coo-Cah Plastics Factory → Security Electronics

| Component                        | Spec                                 | Daily Volume | Notes                      |
|----------------------------------|--------------------------------------|--------------|----------------------------|
| IP camera housing (bullet)       | ABS, IP66-rated sealing grooves      | 500 units    | Size-specific per SKU      |
| IP camera housing (dome)         | PC/ABS, clear dome with IR window    | 400 units    | IR-transparent dome spec   |
| PTZ camera housing               | Die-cast Al + ABS (IP66)             | 30 units     | Heavy; Al from external    |
| NVR / DVR housing (rackmount)    | ABS, steel base                      | 80 units     |                            |
| Access control panel housing     | ABS, flush-mount + surface-mount     | 60 units     |                            |
| Alarm panel housing              | ABS, wall-mount                      | 100 units    |                            |
| Video intercom housing           | ABS, outdoor + indoor units          | 80 sets      |                            |

---

## 4. Phase 2+ Supply Chain Targets

| Component              | Phase 1 Source      | Phase 2 Target                                       |
|------------------------|---------------------|------------------------------------------------------|
| CMOS Sensors           | Fully imported      | Regional distributor bonded stock (Lagos free zone)  |
| Camera Lenses          | Imported            | Evaluate lens assembly at Coo-Cah precision machining|
| H.265 SoCs             | Imported            | Maintain 90-day buffer; dual-source where possible   |
| PCBs                   | In-house SMT        | Consolidate to Coo-Cah Personal Electronics SMT line |
| Camera Housings        | Coo-Cah Plastics    | ✅ Already intra-group                                |

---

*Refer to [`capex-opex.md`](./capex-opex.md) for landed cost modelling.*
*Refer to [`regulatory.md`](./regulatory.md) for NCC TA, ONVIF, and SON CoC requirements.*
