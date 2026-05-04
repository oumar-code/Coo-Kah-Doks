# Smart Estate & City Electronics Factory — Regulatory Compliance

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Smart Estate & City Electronics Factory | **Location:** Lekki Free Trade Zone (LFTZ), Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Regulatory Affairs & Quality Team

---

## 1. Regulatory Framework Summary

The Coo-Cah Smart Estate & City Electronics Factory operates under one of the most complex multi-layered regulatory environments in Nigerian manufacturing. Products span utility metering (NERC jurisdiction), wireless IoT devices (NCC jurisdiction), smart lighting (IEC 62386), traffic infrastructure (NTCIP/NEMA), and environmental sensing — each with distinct standards and approval pathways. NEPZA free zone status provides significant import duty and tax relief but imposes its own operating licence and compliance reporting obligations.

| Regulatory Body                          | Primary Jurisdiction                           | Key Requirement                                       | Impact Level    |
|------------------------------------------|------------------------------------------------|-------------------------------------------------------|-----------------|
| NERC (Nigerian Electricity Reg. Comm.)   | Electricity meters (CCE-SM-ELEC)               | Meter Code compliance, type test certificate, serial registry | **Critical** |
| NCC (Nigerian Communications Commission) | All wireless devices                           | Type Approval before commercial sale                  | **Critical**    |
| NEPZA (Nigerian Export Processing Zones Authority) | Free Zone Enterprise                  | FZE operating licence, annual returns                 | **Critical**    |
| SON (Standards Organisation of Nigeria)  | All manufactured products                      | NIS certification, product registration, MANCAP CoC  | High            |
| NESREA (Nat. Environmental Standards Agency) | Environmental compliance                   | EIA approval, e-waste EPR, VOC/air emissions          | High            |
| FIRS (Federal Inland Revenue Service)    | Tax compliance                                 | VAT, WHT (CIT holiday under NEPZA FZE status)         | High            |
| Ministry of Labour (FMOL)                | Workers' welfare                               | Factories Act, Labour Act, NSITF, pension             | High            |
| Lagos State Government                   | Land, construction, planning within LFTZ       | LFTZ operating permit, Lagos State environmental permit| Medium         |
| IEC / ISO (International)                | Product safety and quality                     | IEC 62053-21/22, IEC 62056, IEC 62386, ISO 9001:2015  | High            |
| NCS (Nigeria Customs Service)            | Imports (at LFTZ customs interface)            | Free zone import (duty-free); domestic sale customs duty | High          |

---

## 2. NERC Meter Code Compliance

### 2.1 What is the NERC Meter Code?

The Nigerian Electricity Regulatory Commission Meter Code 2012 (as amended) is the mandatory regulatory instrument governing the technical and commercial requirements for electricity meters deployed by Distribution Companies (DisCos) in Nigeria under the Electricity Power Sector Reform Act (EPSRA) 2005. Compliance with the Meter Code is a prerequisite for:

- Commercial sale of electricity meters to any NERC-licensed DisCo
- Participation in the Meter Asset Provider (MAP) framework
- Supply of meters under the National Mass Metering Programme (NMMP)
- Approval of meters for use in smart estate metering within DisCo licence areas

### 2.2 NERC Meter Code Key Requirements

| Requirement                         | Standard / Reference        | Specification for CCE-SM-ELEC                                      |
|-------------------------------------|-----------------------------|--------------------------------------------------------------------|
| General requirements                | IEC 62052-11                | All construction, safety, and marking requirements                 |
| Accuracy class (single-phase)       | IEC 62053-21, Class 1       | ≤±1% error at Irated; ≤±2% at 5% Irated                           |
| Accuracy class (three-phase)        | IEC 62053-22, Class 0.5S    | ≤±0.5% error at Irated; ≤±1.5% at 5% Irated                       |
| Communication protocol              | IEC 62056 (DLMS/COSEM)      | Full DLMS/COSEM HDLC + TCP/IP profile; OBIS code compliance        |
| Prepayment token compatibility      | STS (Standard Transfer Spec)| STS 60-bit token generation and acceptance                         |
| Tamper detection                    | NERC Meter Code clause 8    | Magnetic tamper, cover open, current reversal, neutral missing     |
| Event logging                       | IEC 62056 / NERC Meter Code | Power outage, tamper, cover open — all timestamped per OBIS code   |
| IP rating                           | IEC 60529                   | IP54 minimum (dust and splash protection)                          |
| Consumer display                    | NERC Meter Code clause 12   | LCD showing kWh, balance (prepaid), tamper indication              |
| Operating temperature range         | NERC / IEC 62052-11         | –25°C to +70°C                                                     |
| Factory calibration records         | NERC Meter Code clause 14   | Calibration record per serial; retained 10 years minimum           |

### 2.3 NERC Meter Code Registration Process

```
Step 1: IEC Type Test — Accredited Laboratory
│
├── Submit CCE-SM-ELEC to NMI (Nigeria), KEMA, or other NERC-accepted lab
├── Full IEC 62053-21 (single-phase) type test: accuracy, EMC, climatic, endurance
├── Full IEC 62053-22 (three-phase) type test as applicable
├── Obtain Type Test Certificate (TTC) from accredited test lab
└── Estimated timeline: 8–14 weeks per product variant
                              │
                              ▼
Step 2: NERC Technical Submission
│
├── Submit TTC + Technical Dossier to NERC Metering Unit
├── Technical dossier: product description, circuit diagrams, OBIS code list,
│   DLMS/COSEM profile, STS compatibility declaration, IP rating test certificate
├── Pay NERC meter registration fee
└── NERC review period: 4–8 weeks
                              │
                              ▼
Step 3: NERC Factory Audit (if requested)
│
├── NERC may conduct factory audit to verify:
│   — Calibration bench capability and traceability to NMI reference standards
│   — Calibration record system (MES) adequacy
│   — Production quality control procedures
│   — IEC test equipment availability and calibration status
└── Factory maintains NERC Audit Readiness file (see Section 2.5)
                              │
                              ▼
Step 4: NERC Meter Registration Certificate Issued
│
├── NERC issues Meter Registration Certificate (product-level)
├── Certificate number stored in MES NERC Module
├── All production units now eligible for DisCo deployment under MAP/NMMP
└── Periodic renewal: NERC may require re-submission if material design change occurs
                              │
                              ▼
Step 5: Ongoing — Factory Calibration & Serial Registry
│
├── 100% factory calibration of every unit (see MES calibration log)
├── Periodic submission of meter serial registries to NERC
├── MAP partner must report installation addresses to NERC
└── Annual calibration surveillance with NMI-traceable reference standards
```

### 2.4 Meter Asset Provider (MAP) Framework

The MAP framework, established by NERC, allows private entities to procure, own, and deploy electricity meters and recover the cost through a monthly meter maintenance charge collected by DisCos from end consumers.

| MAP Framework Element                | Coo-Cah Position / Action                                           |
|--------------------------------------|---------------------------------------------------------------------|
| NERC MAP Licence (required by deployer) | Coo-Cah's CCE-SM-ELEC is supplied to MAP-licensed entities (DisCos or private MAPs) |
| Meter serial registry maintenance    | Coo-Cah maintains a complete serial registry in MES; exports to MAP partners on demand |
| MAP batch documentation             | Each batch shipped to a MAP partner includes calibration certs, DLMS provisioning file, packing list |
| DisCo head-end integration support  | Coo-Cah provides DLMS/COSEM provisioning profiles (OBIS, meter password, security keys) |
| Installation verification           | Coo-Cah does not install meters; MAP partner is responsible for site installation records |

### 2.5 NERC Factory Audit Readiness Checklist

| Audit Item                                       | Status         | Location / Evidence                                      |
|--------------------------------------------------|----------------|----------------------------------------------------------|
| Calibration bench calibration certificates (NMI traceable) | Required | CAL-LAB; annual recalibration by accredited lab  |
| Reference standard calibration traceability chain | Required      | Standards lab certificates; chain to SI units via NMI   |
| MES calibration record system demonstrated       | Required       | MES live demo; sample calibration records print-out     |
| IEC 62053-21/22 type test certificate on file    | Required       | Regulatory Affairs file; copy in MES NERC Module        |
| Calibration technician training records          | Required       | HR training register; IEC 62053 calibration training    |
| ISO 9001 QMS certificate (or interim audit)      | Required       | Quality Manager; target Q2 2027                         |
| Production process flow and QC procedure        | Required       | QMS document control system; NERC-readable summary      |
| Calibration ambient condition log (temp/RH)      | Required       | CAL-LAB IoT sensor; MES environmental log               |

---

## 3. IEC 62053-21 & IEC 62053-22 Compliance (Electricity Meters)

### 3.1 Standard Requirements

**IEC 62053-21 (Class 1 — Single-Phase Residential Meters):**

| Test Parameter                    | Limit                                     | CCE-SM-ELEC Target    |
|-----------------------------------|-------------------------------------------|-----------------------|
| Error at Imax (100% Irated)       | ±1.0%                                     | ≤±0.3%                |
| Error at 5% Irated (light load)   | ±2.0%                                     | ≤±0.8%                |
| Error at 120% Irated (overload)   | ±1.0%                                     | ≤±0.3%                |
| Power factor influence (0.5 lag)  | ±1.5%                                     | ≤±0.5%                |
| Temperature influence (–10°C to +55°C) | ±2.5% per 10°C                       | ≤±1.0% per 10°C       |
| Frequency influence (±2% of 50 Hz)| ±1.0%                                     | ≤±0.3%                |
| Harmonic influence (3rd + 5th)    | ±1.5%                                     | ≤±0.5%                |

**IEC 62053-22 (Class 0.5S — Three-Phase Commercial/Industrial Meters):**

| Test Parameter                    | Limit                                     | CCE-SM-ELEC (3-ph) Target |
|-----------------------------------|-------------------------------------------|---------------------------|
| Error at Imax (100% Irated)       | ±0.5%                                     | ≤±0.15%                   |
| Error at 5% Irated (light load)   | ±1.5%                                     | ≤±0.5%                    |
| Error at 120% Irated              | ±0.5%                                     | ≤±0.15%                   |

**Test Conditions (IEC 62053-21 clause 5):**
- Reference temperature: 23°C ±2°C
- Relative humidity: 40–70%
- Frequency: 50 Hz ±0.5%
- Supply voltage: 100% Un ±1%

### 3.2 In-Factory Calibration Activities

| Test Type                         | Reference Standard     | Equipment                  | Frequency         | Acceptance Criteria      |
|-----------------------------------|------------------------|----------------------------|-------------------|--------------------------|
| 100% unit calibration (production)| NAFDAC/NMI-traceable ref meter | IEC 62053 Cal Bench ×4 | Every unit produced | Pass per IEC 62053-21/22|
| Reference standard recalibration  | NMI Nigeria or KEMA    | External accredited lab    | Annually          | Cert valid + traceable   |
| Environmental condition monitoring| Calibrated Temp/RH sensor | CAL-LAB IoT sensor      | Continuous (24/7) | 23°C ±2°C, 40–70% RH   |
| Calibration bench self-check      | Internal reference load| Bench internal reference   | Daily (auto)      | Reference within 0.05%   |
| Calibration bench annual audit    | NMI-traceable standard | External auditor           | Annually          | All bench results traceable |

---

## 4. IEC 62056 DLMS/COSEM Compliance

### 4.1 What is DLMS/COSEM?

DLMS/COSEM (Device Language Message Specification / Companion Specification for Energy Metering) is the internationally standardised communication framework for smart meters, defined by the DLMS User Association and adopted as IEC 62056 series. It defines:

- **OBIS codes:** Object Identification System codes that uniquely identify every data object (energy registers, status flags, event logs) within the meter
- **Application layer (COSEM):** The object model and data access methods
- **Data link layer options:** IEC 62056-21 (local optical interface), IEC 62056-46 (HDLC), IEC 62056-47 (TCP-UDP/IP)

All CCE-SM-ELEC units implement a full DLMS/COSEM profile supporting both AMR (optical) and AMI (NB-IoT TCP/IP) communication modes.

### 4.2 Key OBIS Codes Implemented in CCE-SM-ELEC

| Data Object                        | OBIS Code         | Description                                           |
|------------------------------------|-------------------|-------------------------------------------------------|
| Active energy import — total (kWh) | 1.0.1.8.0.255     | Cumulative import energy register                     |
| Active energy export — total (kWh) | 1.0.2.8.0.255     | Cumulative export (bi-directional meters)             |
| Instantaneous voltage L1 (V)       | 1.0.32.7.0.255    | Real-time L1 voltage                                  |
| Instantaneous voltage L2 (V)       | 1.0.52.7.0.255    | Three-phase only                                      |
| Instantaneous voltage L3 (V)       | 1.0.72.7.0.255    | Three-phase only                                      |
| Instantaneous current L1 (A)       | 1.0.31.7.0.255    | Real-time L1 current                                  |
| Instantaneous active power (W)     | 1.0.1.7.0.255     | Real-time import active power                         |
| Power factor                       | 1.0.13.7.0.255    | Instantaneous power factor                            |
| Tamper event log                   | 0.0.99.98.0.255   | Timestamped tamper event record (magnetic, cover, etc.)|
| Power outage log                   | 0.0.96.7.0.255    | Power interruption events with duration               |
| Meter serial number                | 0.0.96.1.0.255    | Factory serial number                                 |
| Firmware version                   | 0.0.96.1.4.255    | Currently installed firmware version                  |
| Load profile (15-min interval)     | 1.0.99.1.0.255    | 15-minute energy interval data for AMI                |
| Time and date                      | 0.0.1.0.0.255     | RTC value; synchronised via NTP over NB-IoT           |
| Prepayment credit balance          | 0.0.19.10.0.255   | Remaining kWh credit (prepaid mode)                   |

### 4.3 DLMS/COSEM Interoperability

CCE-SM-ELEC DLMS/COSEM implementation is tested for interoperability with the following major DisCo head-end systems:

| Head-End System Platform       | DisCo Users                      | Interoperability Status        |
|--------------------------------|----------------------------------|--------------------------------|
| Itron Riva AMI                 | EKEDC, EEDC                      | Target: pre-production interop test |
| Landis+Gyr AIM                 | IBEDC, PHED                      | Target: pre-production interop test |
| Elster/Honeywell REX2         | AEDC, BEDC                       | Target: pre-production interop test |
| Hexing GPRS Head-End           | Smaller DisCos                   | Target: Phase 2                |

### 4.4 STS Prepayment Token Compatibility

The CCE-SM-ELEC prepaid variants implement the Standard Transfer Specification (STS), the international standard (IEC 62055-41) for prepayment electricity token systems. This ensures:

- Tokens generated by any STS-compliant vending system are accepted by CCE-SM-ELEC
- Revenue protection through 60-bit encrypted token (DES-based)
- Compatible with existing DisCo vending infrastructure (kiosks, USSD, mobile app)

---

## 5. NCC Type Approval — LoRa / NB-IoT / Wi-Fi / 4G Products

### 5.1 What Products Require NCC Type Approval?

All CCE products with wireless connectivity require NCC Type Approval before commercial sale in Nigeria under the Nigerian Communications Act 2003 (as amended). Products affected: CCE-SM-ELEC (NB-IoT), CCE-SM-WATER (NB-IoT), CCE-LORA-GW (LoRa), CCE-ESN (LoRa), CCE-SEH (Wi-Fi 6 + Zigbee), CCE-SPS (4G + Wi-Fi), CCE-CTC (4G/5G).

### 5.2 NCC Type Approval Process

```
Step 1: Pre-Submission RF Engineering
│
├── Confirm device RF parameters (frequency bands, max EIRP, modulation)
├── Conduct pre-compliance EMC + RF scan in Coo-Cah RF Lab (Zone Z10 RF Lab)
├── Confirm device complies with NCC Spectrum Management Regulations
└── Prepare Technical File: User Manual, Declaration of Conformity, circuit diagrams, antenna data
                              │
                              ▼
Step 2: Formal Application to NCC (MTBS Portal)
│
├── Submit online application via NCC Mobile Terminal and Broadcasting Services portal
├── Pay non-refundable application fee (₦100,000–₦250,000 per product per standard category)
├── Upload technical file, test plans, antenna gain data, user manual
└── Designate NCC-authorised local representative (Coo-Cah Regulatory Affairs team)
                              │
                              ▼
Step 3: NCC Laboratory Testing (NITDA-accredited or NCC-designated lab)
│
├── NCC schedules device testing at an approved laboratory (Lagos or Abuja)
├── Tests: EMC (radiated/conducted), RF output power, spurious emissions, SAR (if applicable)
├── Pre-compliance data from Coo-Cah RF Lab submitted alongside formal submission
└── Timeline: 6–14 weeks depending on lab queue, product complexity, and spectrum band
                              │
                              ▼
Step 4: NCC Technical Review & Decision
│
├── NCC reviews lab test report; may request supplementary data or clarification
├── If approved: Type Approval Certificate issued (valid 5 years; renewable)
└── If rejected: Modification required; resubmission with updated design
                              │
                              ▼
Step 5: Certificate Issued — Production Authorised
│
├── NCC TA Number logged in Coo-Cah MES NCC Module
├── NCC mark applied to product label and packaging per NCC labelling guidance
├── All production units batch-linked to certificate in MES
└── Certificate monitored for expiry; renewal initiated 6 months before expiry
```

### 5.3 NCC Type Approval Schedule

| Product SKU    | Wireless Technology           | NCC Category              | Target Submission | Target Certificate | Fee Estimate       |
|----------------|-------------------------------|---------------------------|-------------------|--------------------|------------------  |
| CCE-SM-ELEC    | NB-IoT, Quectel BC660, B8     | IoT Terminal / NB-IoT     | Q3 2026           | Q1 2027            | ₦800k–₦1.2M        |
| CCE-SM-WATER   | NB-IoT, Quectel BC660K, B8    | IoT Terminal / NB-IoT     | Q3 2026           | Q1 2027            | ₦800k–₦1.2M        |
| CCE-LORA-GW    | LoRa 868/915 MHz, SX1302      | Short Range Device / IoT GW| Q4 2026          | Q2 2027            | ₦700k–₦1.0M        |
| CCE-ESN        | LoRa 868/915 MHz, SX1276      | Short Range Device        | Q4 2026           | Q2 2027            | ₦600k–₦900k        |
| CCE-SEH        | Wi-Fi 6 + Zigbee 3.0          | ISM / Short Range Device  | Q1 2027           | Q3 2027            | ₦900k–₦1.4M        |
| CCE-SPS        | 4G LTE + Wi-Fi 4              | Mobile Terminal / SRD     | Q1 2027           | Q4 2027            | ₦900k–₦1.4M        |
| CCE-CTC        | 4G/5G (Sub-6 GHz)             | Mobile Terminal           | Q2 2027           | Q1 2028            | ₦1.2M–₦1.8M        |

### 5.4 NCC Fee Schedule

| Activity                          | Approximate Fee        | Notes                                     |
|-----------------------------------|------------------------|-------------------------------------------|
| Application fee (per product)     | ₦100,000–₦250,000     | Depends on device category                |
| Laboratory testing fee            | ₦500,000–₦1,500,000   | Per product; external accredited lab      |
| Annual Type Approval levy         | ₦50,000–₦150,000/year | During certificate validity               |
| Renewal fee (at 5-year expiry)    | ₦150,000–₦350,000     | Full re-test usually required             |

> **LoRa Spectrum Note:** 868 MHz LoRa is supported in Nigeria under the ISM/short-range device (SRD) framework. 915 MHz is also supported in firmware. Coo-Cah Regulatory Affairs must liaise with NCC Spectrum Management Division to confirm the approved LoRaWAN frequency plan and maximum EIRP before commercial deployment of CCE-LORA-GW networks.

---

## 6. NEPZA Free Zone Compliance

### 6.1 Legal Framework

The Coo-Cah Smart Estate & City Electronics Factory operates as a **Free Zone Enterprise (FZE)** under the **Nigeria Export Processing Zones Act Cap N107 LFN 2004** (as amended), administered by the **Nigeria Export Processing Zones Authority (NEPZA)** through the Lekki Free Trade Zone (LFTZ) Zone Authority.

### 6.2 Key NEPZA Benefits and Obligations

| Benefit / Obligation                          | Detail                                                                     |
|-----------------------------------------------|----------------------------------------------------------------------------|
| 100% corporate income tax holiday            | No CIT payable for the duration of free zone enterprise status             |
| Duty-free import of raw materials             | All components, machinery, and consumables imported duty-free into LFTZ   |
| Duty-free import of production equipment     | Capital equipment imported without customs duty or import levy             |
| No VAT on inputs (free zone)                  | Inputs to free zone production are zero-rated for VAT purposes within LFTZ|
| NEPZA operating licence                       | Annual renewal; production activity, employment level, and investment must be reported |
| Annual returns to NEPZA                       | Annual compliance filing: employment report, production volume, CapEx deployed |
| NEPZA factory inspection                      | NEPZA may conduct periodic factory inspections; compliance register maintained |
| Domestic market sales restriction             | Products sold into the Nigerian domestic market require customs clearance at LFTZ boundary |
| Form M for domestic sales                     | Products exiting the free zone for Nigerian domestic consumption require Form M and customs duty payment |
| SON CoC for domestic market products          | Products leaving the free zone for domestic sale require a SON Certificate of Conformity |
| NEPZA data residency compliance               | NEPZA-regulated production data (especially sensitive calibration data) must remain on-site |

### 6.3 NEPZA Compliance Register

The factory maintains a NEPZA Compliance Register covering:

- NEPZA FZE Licence number and renewal dates
- NEPZA annual returns filing status
- NEPZA inspection records and corrective actions
- Employment statistics (direct + indirect staff per quarter)
- Production volume by product category per year
- CapEx deployment evidence (receipts, commissioning records)
- Domestic market sales log (units exiting the free zone with associated customs documentation)

---

## 7. IEC 62386 (DALI) Compliance — Smart Pole Lighting

### 7.1 What is DALI-2?

The Digital Addressable Lighting Interface (DALI) is the international standard (IEC 62386) for digital lighting control. DALI-2 (the current certification programme managed by the DiiA — Digital Illumination Interface Alliance) ensures interoperability between DALI-2 certified control devices (switches, sensors, controllers) and control gear (LED drivers, ballasts).

The **CCE-SPS Smart Pole System** integrates a DALI-2 certified LED driver for its adaptive street lighting function, enabling:

- Individual pole dimming (0–100%) from the city management platform
- Scheduled dimming profiles (time-of-night programmes)
- Fault reporting (lamp failure, driver fault) back to the network
- Interoperability with third-party DALI-2 lighting management systems

### 7.2 DALI-2 Compliance Requirements

| DALI-2 Standard Part          | Scope                                    | Applicability to CCE-SPS               |
|-------------------------------|------------------------------------------|-----------------------------------------|
| IEC 62386 Part 101            | General requirements — control device    | CCE-SPS lighting controller PCB        |
| IEC 62386 Part 102            | General requirements — control gear      | CCE-SPS LED driver module              |
| IEC 62386 Part 207            | Control gear — LED drivers               | LED driver compliance and DiiA testing |
| DiiA DALI-2 Certification     | Interoperability testing (DiiA programme)| Factory prototype test + DiiA cert     |

### 7.3 Energy Efficiency Targets for CCE-SPS LED

| Parameter                      | Target                    | Notes                                    |
|--------------------------------|---------------------------|------------------------------------------|
| Luminaire efficacy             | ≥ 140 lm/W               | At 100% drive (full output)              |
| Minimum dimming level          | 5% (≈ 0.25 W)             | For ambient sensing night mode           |
| Dimming range                  | 0–100% (DALI-2)          | Smooth, flicker-free dimming             |
| Power factor (full load)       | ≥ 0.92                   | LED driver specification                 |
| Colour temperature             | 4,000 K (neutral white)  | Lagos State smart city project preference|
| Operating temperature (driver) | –20°C to +65°C           | Nigerian climate; pole internal temp     |

---

## 8. SON NIS Certification

### 8.1 Relevant NIS Standards by Product

| Product SKU    | Relevant NIS Standard(s)                        | SON Action Required                               | Timeline      |
|----------------|-------------------------------------------------|---------------------------------------------------|---------------|
| CCE-SM-ELEC    | NIS 62053-21:2022; NIS 62052-11                | Product registration + CoC + NERC Meter Code     | Before sale   |
| CCE-SM-WATER   | NIS 12758 (water meters) / NIS equivalent       | Product registration + CoC                       | Before sale   |
| CCE-SEH        | NIS 62368-1:2022 (A/V/IT safety)               | Product registration + CoC                       | Before sale   |
| CCE-SPS        | NIS 60598-2-3:2022 (street luminaires)         | Product registration + CoC + DiiA cert           | Before sale   |
| CCE-CTC        | NIS 62262 (IK ratings for traffic controllers) | Product registration + CoC                       | Before sale   |
| CCE-ESN        | NIS 60068 (environmental testing); NIS 62368-1 | Product registration + CoC                       | Before sale   |
| CCE-LORA-GW    | NIS 62368-1:2022                                | Product registration + CoC                       | Before sale   |

### 8.2 SON MANCAP — Imported Component CoC

All imported components that are themselves SON-regulated products require a SON MANCAP Certificate of Conformity before clearing Nigerian Customs. Under NEPZA free zone status, this requirement is **waived for components imported directly into the LFTZ for production use**. However, if any component is re-exported as a standalone product into the Nigerian domestic market, the SON CoC applies at the free zone exit point.

The Procurement team ensures MANCAP CoC documentation is obtained for any regulated component that may be sold domestically.

---

## 9. NESREA & Environmental Compliance

### 9.1 Environmental Authorisations

| Requirement                           | Detail                                                                  | Status       |
|---------------------------------------|-------------------------------------------------------------------------|--------------|
| Environmental Impact Assessment (EIA) | Full EIA required before construction under NESREA Act 2007 and LFTZ environmental framework | Required (P1)|
| NESREA EIA Approval (Federal)         | Issued by NESREA after public review; required before commissioning      | Required (P1)|
| Lagos State Environmental Permit      | Lagos State EPA state-level environmental operating permit               | Required (P1)|
| Air Emission Permit                   | Generator exhaust (NOₓ, PM); conformal coating VOC emissions from Nordson SelectCoat | Required |
| Effluent Discharge Permit             | SMT flux cleaning water; ultrasonic welding water; ensure zero-discharge or licensed disposal | Required |
| Chemical Storage Permit               | Conformal coating materials (IPA, acrylic coating), polyurethane potting compound | Required |

### 9.2 E-Waste Management (WEEE / EPR)

Nigeria's Extended Producer Responsibility framework under the National Environmental (Electrical/Electronic Sector) Regulations 2011 places EPR obligations on manufacturers of electronic products.

| Obligation                      | Description                                                              | Implementation     |
|---------------------------------|--------------------------------------------------------------------------|--------------------|
| EPR Registration                | Register with NESREA as producer of electronic goods                     | Q2 2027            |
| Take-Back Programme             | Establish or join a NESREA-recognised take-back scheme for end-of-life meters, hubs, and poles | Q4 2027 |
| Annual E-Waste Report           | Report tonnage of products placed on Nigerian domestic market vs. waste recovered | Annual (Year 2+) |
| Factory Waste Segregation       | SMT waste (solder dross, paste, flux, PCB offcuts) segregated and disposed via licensed hazardous waste contractor | Ongoing |
| Battery Disposal (BESS)         | BESS end-of-life LFP cells sent to NESREA-certified recycler              | Per occurrence     |
| Conformal Coating Waste         | Coating solvents (IPA, acetone) collected and disposed via licensed NESREA contractor | Ongoing |

### 9.3 Conformal Coating VOC Management

The Nordson SelectCoat conformal coating line uses acrylic (AR) coating with isopropyl alcohol (IPA) solvent. VOC emissions from coating and UV cure tunnel are managed by:

- Enclosed coating chamber with extraction
- Carbon filter + catalytic oxidiser on exhaust
- Lagos State EPA air emission permit (annual monitoring)
- VOC solvent usage log submitted annually to NESREA

---

## 10. Labour & Workers' Welfare Compliance

### 10.1 Applicable Laws

| Law / Regulation                          | Key Requirement                                                     |
|-------------------------------------------|---------------------------------------------------------------------|
| Labour Act (Cap L1, LFN 2004)             | Written contracts, notice periods, termination procedures           |
| Employees' Compensation Act 2010          | Compulsory workers' compensation insurance (NSITF)                  |
| National Minimum Wage Act 2019 (amended)  | Minimum wage compliance; current ₦70,000/month (2024 revision)     |
| Factories Act (Cap F1, LFN 2004)          | Machine guarding, ventilation, sanitation, accident reporting       |
| Pension Reform Act 2014                   | Contributory pension: employer 10% + employee 8% of salary         |
| Health and Safety at Work (OSHA)          | HSE policy, PPE provision, incident register, emergency plan        |
| Nigeria Social Insurance Trust Fund (NSITF)| Monthly contribution; workers' compensation                        |
| National Industrial Court Act 2006        | Dispute resolution framework                                        |

### 10.2 Factory Act Compliance Checklist

| Requirement                       | Status       | Details                                                     |
|-----------------------------------|--------------|-------------------------------------------------------------|
| Factory Registration with FMOL    | Required     | Register under Factories Act before production commencement |
| Machinery Guarding                | In design    | Conveyors, welders, calibration rigs comply with ISO 13857 / ISO 14119 |
| ESD Protection System             | In design    | ESD wrist straps, ESD flooring, ionisers in SMT zones; grounding log |
| First Aid Facilities              | Planned      | Staffed first aid room; 4 trained first aiders per shift    |
| Fire Safety Equipment             | Planned      | Sprinklers, extinguishers, smoke detection; BESS zone fire suppression |
| Incident Reporting System         | Planned      | OSHA-style incident register; report to FMOL within 24h for LTI |
| PPE Provision                     | Planned      | ESD wrist straps, safety shoes, lab coats, face shields (welding zone) |
| Canteen & Welfare Facilities      | Planned      | Subsidised canteen, prayer room, changing rooms, nurse station |
| Chemical Handling Training        | Planned      | Conformal coating, solder paste, flux — COSHH-style training for operators |

---

## 11. Import Regulatory Compliance — Free Zone Special Provisions

### 11.1 Free Zone Import Regime (NEPZA)

Under NEPZA free zone status, the following regulatory exemptions apply to **all inputs imported directly into the LFTZ factory**:

| Exemption                                | Applicable To                                          |
|------------------------------------------|--------------------------------------------------------|
| No Form M required                       | All components, raw materials, machinery imported into LFTZ |
| No import duty                           | Capital equipment, production materials                |
| No SON CoC required for imported inputs | Components for production (not end products for domestic market) |
| No NAFDAC import permit (electronics)   | Electronic components (non-food, non-pharma)           |
| Expedited NCS clearance within LFTZ     | LFTZ has dedicated NCS customs presence for fast processing |

### 11.2 Domestic Market Sales — Free Zone Exit Requirements

Products manufactured in the LFTZ that are sold into the **Nigerian domestic market** must comply with the following at the free zone exit boundary:

| Requirement                       | Body              | Documentation                                     |
|-----------------------------------|-------------------|---------------------------------------------------|
| Customs duty payment              | NCS               | Customs assessment; duty paid at LFTZ exit         |
| Form M (import/sales declaration) | CBN / Commercial Bank | Form M for value of goods entering domestic market |
| SON CoC for regulated products    | SON via MANCAP    | Per product category per shipment                  |
| VAT on domestic sales             | FIRS              | Standard VAT applies; no free zone exemption for buyer |

### 11.3 Export Sales — Free Zone Advantage

Products exported from LFTZ to international markets benefit from:

- **No export duty** (NEPZA free zone export incentive)
- **No Form NXP required** for NEPZA free zone exports (simplified export documentation)
- Access to ECOWAS Trade Liberalisation Scheme (ETLS) for duty-free access to ECOWAS member states (subject to ETLS rules of origin — Nigerian content ≥40%)

---

## 12. Phase 2 Export Compliance (Outlook)

| Market               | Standard / Certification      | Description                                              | Target Phase |
|----------------------|-------------------------------|----------------------------------------------------------|--------------|
| ECOWAS Region        | ECOWAS Smart Metering Directive| Harmonised metering standards for ECOWAS (under development) | Phase 2 |
| ECOWAS Region        | NCC Mutual Recognition        | ECOWAS NCC MRA for wireless type approval                | Phase 2      |
| UK                   | UKCA Marking                  | Smart metering and IoT radio equipment                   | Phase 3      |
| EU                   | CE Marking (RED + MID)        | Radio Equipment Directive + Measuring Instruments Directive | Phase 3   |
| Global               | RoHS 2 compliance             | Hazardous substances restriction for EU/UK market        | Phase 2      |

---

*For MES regulatory data tracking (NERC calibration log, NCC test result logging), refer to [`mes-integration.md`](./mes-integration.md).*
*For supply chain import process documentation, refer to [`supply-chain.md`](./supply-chain.md).*
*For energy-related environmental permits (generator emissions), refer to [`energy-profile.md`](./energy-profile.md).*
