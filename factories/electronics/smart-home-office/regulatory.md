# Smart Home & Office Electronics Factory — Regulatory Compliance

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Smart Home & Office Electronics Factory | **Location:** Agbara Industrial Estate, Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Regulatory Affairs & Quality Team

---

## 1. Regulatory Framework Summary

| Regulatory Body       | Jurisdiction                            | Key Requirement                                              | Criticality |
|-----------------------|-----------------------------------------|--------------------------------------------------------------|-------------|
| NCC                   | All wireless products (TVs, laptops, routers, hubs) | Type Approval before sale                     | **Critical** |
| SON                   | All manufactured products               | NIS certification; mandatory product testing                 | **Critical** |
| NESREA                | Environmental compliance                | EIA; e-waste; packaging recycling                            | High        |
| NCS                   | Imports (display panels, SoCs)          | Form M; SON CoC; correct HS code                            | High        |
| Google (Android CDD)  | Android TV products                     | Google CDD compliance required for GMS licensing             | **Critical** |
| Google (GMS)          | Android TV / laptop with Chrome OS       | GMS partner agreement; MES test compliance record           | **Critical** |
| NAFDAC                | No direct requirement                   | —                                                            | Low         |
| Ministry of Labour    | Worker safety                           | Factories Act; ESD safety; electrical safety                 | High        |
| Lagos State Government| Building + operations                   | Building permit; operational licence; Lagos EIA             | High        |
| IEC (International)   | Product safety                          | IEC 62368-1 (Audio/Video/IT); IEC 60950; EMC standards      | High        |

---

## 2. NCC Type Approval — Scope for This Factory

All products with wireless radio capability manufactured in this factory require NCC Type Approval before sale in Nigeria. This factory has the widest NCC TA scope of any Coo-Cah factory.

| Product                          | Radio Technologies              | NCC TA Standards                                    |
|----------------------------------|---------------------------------|-----------------------------------------------------|
| Smart TV (all models)            | Wi-Fi 5/6, Bluetooth 5.0        | NCC Type Approval (Wi-Fi 802.11; BT 5.0)           |
| Wi-Fi Router (Home + Mesh)       | Wi-Fi 6 (802.11ax), 2.4 + 5 GHz| NCC TA (dual-band); ETSI EN 301 893                 |
| Smart Speaker (Small + Large)    | Wi-Fi + BT 5.2                  | NCC TA; Wi-Fi + BT                                  |
| Home Automation Hub              | Zigbee 3.0 + Wi-Fi 6 + BLE 5.2 | NCC TA (multi-radio); IEEE 802.15.4 compliance      |
| Smart Display 10" / 15"          | Wi-Fi 6 + BT + Zigbee           | NCC TA (multi-radio)                               |
| Laptop (Wi-Fi + BT)              | Wi-Fi 6 (802.11ax) + BT 5.2     | NCC TA for Wi-Fi module + BT module                 |

---

## 3. Google Android TV CDD Compliance

All Coo-Cah Smart TVs ship with Android TV (Google Mobile Services). Google requires the following compliance steps:

| Step | Activity                                              | Google Requirement                            |
|------|-------------------------------------------------------|-----------------------------------------------|
| 1    | Android CDD (Compatibility Definition Document)       | Device must pass all CDD test cases           |
| 2    | CTS (Compatibility Test Suite)                        | Automated test suite; must pass 100%          |
| 3    | GTS (Google Test Suite)                               | GMS-specific tests; Google reviewed           |
| 4    | Android TV App certification (Netflix, YouTube)       | DRM compliance; Netflix pre-auth              |
| 5    | Google Play Protect                                   | Device pre-certified before shipping          |
| 6    | MES Android TV GMS Module                             | Every unit must have CDD PASS recorded in MES |

---

## 4. IEC 62368-1 — Audio/Video/IT Safety

IEC 62368-1 is the consolidated safety standard for audio/video and information technology equipment. It replaced IEC 60065 (AV) and IEC 60950 (IT) from 2021. Applies to all Coo-Cah smart home & office products.

| Safety Parameter              | Requirement                                          | Test Frequency       |
|-------------------------------|------------------------------------------------------|----------------------|
| Dielectric Strength (Hipot)   | 100% production test (1,000V AC for 1 sec)          | Every unit           |
| Leakage Current               | < 3.5 mA (Class I); < 0.25 mA (Class II)            | Type test + periodic |
| Surface Temperature           | < 70°C (accessible surfaces during operation)        | Type test            |
| Mechanical Strength (drop)    | 1m drop (portable devices); 0.5m (large TVs)        | Design verification  |
| EMC — Emissions               | EN 55032 (Class B residential)                       | Type test per SKU    |
| Power Supply Safety           | AC adapter certification (if separate)               | Type test            |

---

## 5. SON NIS Certification Schedule

| Product Category           | Applicable Standard           | Target Certification   |
|----------------------------|-------------------------------|------------------------|
| Smart TVs (all sizes)      | NIS / IEC 62368-1             | Q2 2026                |
| Wi-Fi Routers              | NIS + NCC TA                  | Q2 2026                |
| Smart Speakers             | NIS + NCC TA                  | Q3 2026                |
| Home Automation Hub        | NIS + NCC TA (multi-radio)    | Q3 2026                |
| Laptops                    | NIS / IEC 62368-1 + NCC TA    | Q3 2026                |
| Smart Displays             | NIS + NCC TA                  | Q4 2026                |
| Projectors                 | NIS / IEC 62368-1             | Q4 2026                |

---

## 6. Compliance Calendar

| Obligation                    | Frequency | Deadline              | Responsible         |
|-------------------------------|-----------|-----------------------|---------------------|
| NCC TA renewals (all SKUs)    | Every 5yr | Certificate expiry    | Regulatory Affairs  |
| SON NIS audit                 | Annual    | Product anniversary   | Regulatory Affairs  |
| Google CDD recertification    | Per major Android TV version | On Google's schedule | Tech + Regulatory |
| ISO 9001 surveillance audit   | Annual    | Certification body    | QA Manager          |
| NESREA EIA review             | Biennial  | Every 2 years         | EHS Officer         |
| FIRS tax filing               | Annual    | 30 June               | Finance             |

---

*For supply chain CoC and Form M, refer to [`supply-chain.md`](./supply-chain.md).*
*For MES NCC TA tracking, refer to [`mes-integration.md`](./mes-integration.md).*
