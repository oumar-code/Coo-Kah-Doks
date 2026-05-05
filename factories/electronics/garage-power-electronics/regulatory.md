# Garage & Power Electronics Factory — Regulatory Compliance

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Garage & Power Electronics Factory | **Location:** Sagamu Industrial Estate, Ogun State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Regulatory Affairs & Quality Team

---

## 1. Regulatory Framework Summary

| Regulatory Body          | Jurisdiction                      | Key Requirement                                                  | Criticality |
|--------------------------|-----------------------------------|------------------------------------------------------------------|-------------|
| SON (Standards Org. of Nigeria) | All manufactured products  | NIS certification before sale; mandatory type testing            | **Critical** |
| NCC                      | Wireless products (smart power strips, Wi-Fi inverters) | Type Approval for Wi-Fi/BT-enabled products | High    |
| NESREA                   | Environmental compliance          | EIA for factory; e-waste and battery disposal                    | High        |
| Nigeria Customs Service  | Imports (MOSFETs, transformers)   | Form M; HS code; SON CoC                                         | High        |
| Ministry of Labour       | Worker safety                     | Factories Act; electrical safety; lockout/tagout                 | High        |
| Ogun State Government    | Building + planning               | Building permit; operational licence                             | Medium      |
| IEC (International)      | Product safety                    | IEC 62040 (UPS), IEC 61683 (PV charge controllers), IEC 62477    | High        |
| ISO                      | Quality management                | ISO 9001:2015; ISO 45001 EHS                                     | High        |

---

## 2. SON NIS Product Certifications

### 2.1 Applicable Standards by Product

| Product                         | Applicable NIS / IEC Standard          | Key Tests                                        | Application Timeline |
|---------------------------------|----------------------------------------|--------------------------------------------------|----------------------|
| Pure / Modified Sine Inverters  | NIS 411; IEC 62477-1                   | Output voltage, frequency, safety, EMC, THD      | 3 months pre-launch  |
| UPS — Line Interactive          | NIS / IEC 62040-1 (Safety) + 62040-2 (EMC) | Transfer time, back-up time, efficiency      | 3 months pre-launch  |
| Solar MPPT / PWM Controllers    | NIS / IEC 61683                        | Tracking efficiency, temperature, protection     | 3 months pre-launch  |
| Battery Charger (smart)         | NIS / IEC 60335-2-29                   | Overcharge protection, temperature cutoff        | 3 months pre-launch  |
| Power Strip (basic)             | NIS / IEC 60884-1                      | Contact pressure, pull-out force, dielectric     | 3 months pre-launch  |
| Power Strip (Wi-Fi, smart)      | NIS + NCC Type Approval                | IEC 60884-1 + wireless type approval             | 4 months pre-launch  |
| Corded Power Tools              | NIS / IEC 60745-1                      | Motor insulation, mechanical guarding, EMC       | 3 months pre-launch  |

### 2.2 SON Certification Process

```
Step 1: Internal Pre-Compliance Testing
│ Factory QC lab (hipot, THD, transfer time, efficiency)
│ Pass criteria checked against target standard
└── Design review sign-off required

Step 2: Accredited External Type Test
│ Submit to SON-designated laboratory (Lagos or Abuja)
│ Full IEC standard + relevant sub-standard tests
│ Test report valid 3 years
└── Timeline: 4–10 weeks

Step 3: SON NIS Registration
│ Submit test report + technical file to SON
│ SON issues NIS certificate + product registration number
│ Annual renewal + audit every 3 years
└── NIS mark (C-Mark) required on product label + packaging

Step 4: MES Label Module Triggered on Every Unit
│ SON approval number printed on rating plate
└── MES confirms label applied before unit released to FGW
```

---

## 3. NCC Type Approval — Smart Power Strips & Wi-Fi Inverters

Smart power strips (CCG-PS, Wi-Fi enabled) and any inverter with Wi-Fi monitoring capability require NCC Type Approval before sale.

| NCC Requirement                  | Product                         | Timeline          |
|----------------------------------|---------------------------------|-------------------|
| Wi-Fi Type Approval (802.11b/g/n/ax) | CCG-PS smart strips        | 6 weeks minimum   |
| Wi-Fi Type Approval              | CCG-INV-PSW with Wi-Fi app      | 6 weeks minimum   |
| BLE Type Approval (if applicable)| Future smart products           | TBD               |

Process: as per Personal Electronics factory NCC TA process. Coo-Cah RF lab (at Personal Electronics factory) can perform pre-compliance RF tests before formal NCC submission.

---

## 4. IEC 62040 — UPS Safety Standard

IEC 62040 is a three-part standard covering safety, EMC, and performance of UPS systems:

| Standard Part       | Scope                             | Key Compliance Items                                    |
|---------------------|-----------------------------------|---------------------------------------------------------|
| IEC 62040-1         | Safety requirements               | Electrical safety; creepage/clearance; thermal cutoff   |
| IEC 62040-2         | EMC requirements                  | Conducted/radiated emissions; immunity                  |
| IEC 62040-3         | Performance, test methods         | Transfer time ≤ 10 ms (line-interactive); back-up time  |

---

## 5. Environmental & E-Waste Compliance

| Requirement                               | Authority        | Obligation                                               |
|-------------------------------------------|------------------|----------------------------------------------------------|
| EIA (factory construction)               | NESREA           | Pre-construction EIA approval                            |
| E-waste take-back scheme                 | NESREA           | End-of-life collection programme for inverters/batteries |
| RoHS (Restriction of Hazardous Substances) | Import markets | Lead-free solder (Phase 1 SMT); REACH compliance on BOM |
| Battery disposal (UPS internal batteries) | NESREA          | Licensed disposal agent; annual report                   |

---

## 6. Pioneer Status & Incentives

| Incentive                              | Benefit                                          | Status                           |
|----------------------------------------|--------------------------------------------------|----------------------------------|
| Pioneer Status (NIPC)                  | 5-year CIT holiday — renewables/energy sector    | Application target Q3 2025       |
| Customs duty exemption (capital goods) | 0% duty on qualifying production machinery       | CITA Schedule 2 — all main equip.|
| Export Expansion Grant                 | 15% grant on export FOB value                    | NEPC registration required       |
| NIRSAL/BOI energy manufacturing loan   | Preferential interest rate for renewable mfg.    | Application in progress          |

---

## 7. Compliance Calendar

| Obligation                     | Frequency | Deadline           | Responsible         |
|--------------------------------|-----------|--------------------|---------------------|
| SON NIS renewal audit          | Annual    | Product anniversary| Regulatory Affairs  |
| NCC TA renewal                 | Every 5 yr| Certificate expiry | Regulatory Affairs  |
| NESREA EIA review              | Biennial  | Every 2 years      | EHS Officer         |
| ISO 9001 surveillance audit    | Annual    | Certification body | QA Manager          |
| e-waste report (NESREA)        | Annual    | 31 March           | EHS Officer         |
| FIRS tax filings               | Annual    | 30 June            | Finance             |

---

*For supply chain import compliance, refer to [`supply-chain.md`](./supply-chain.md).*
*For load bank test records, refer to [`mes-integration.md`](./mes-integration.md).*
