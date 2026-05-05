# Kitchen Electronics Factory — Regulatory Compliance

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Kitchen Electronics Factory | **Location:** Agbara Industrial Estate, Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Regulatory Affairs & EHS Team

---

## 1. Regulatory Framework Summary

The Kitchen Electronics Factory faces a multi-agency regulatory environment spanning product safety standards, refrigerant handling controls, environmental approvals, and standard manufacturing permits. The IEC 60335 product safety standard and NESREA's ozone-depleting substance (ODS) regulations are the two most critical compliance pillars unique to this factory.

| Regulatory Body          | Jurisdiction                        | Key Requirement                                                | Criticality |
|--------------------------|-------------------------------------|----------------------------------------------------------------|-------------|
| SON (Standards Org. of Nigeria) | All manufactured products    | NIS product registration; mandatory pre-market approval        | **Critical** |
| NESREA                   | Environmental + ODS (R600a gas)     | EIA approval; R600a licence; ozone protection compliance       | **Critical** |
| Ministry of Environment (Lagos) | Factory environmental impact  | Environmental Impact Assessment (EIA) for industrial premises  | **Critical** |
| Nigeria Customs Service  | Imports (compressors, magnetrons)   | Form M; HS code classification; SON Conformity Assessment (CoC) | High        |
| NAFDAC                   | Food-adjacent appliances            | Registration of plastic food-contact components                | Medium       |
| Ministry of Labour       | Worker welfare                      | Factories Act compliance; NESITF contributions; OH&S           | High         |
| Lagos State Government   | Building & land use                 | Building permit; operational licence; Lagos State EIA          | High         |
| FIRS                     | Tax compliance                      | Corporate tax, VAT, WHT filings                                | High         |
| IEC (International)      | Product safety                      | IEC 60335 appliance safety (series)                            | High         |
| ISO                      | Quality + environmental management  | ISO 9001:2015; ISO 14001:2015 (Phase 2)                       | High         |

---

## 2. Product Safety Certifications

### 2.1 IEC 60335 Compliance Pathway

IEC 60335 is the international standard for Safety of Household and Similar Electrical Appliances. Compliance is required by SON as a pre-condition for NIS certification. Key sub-standards applicable to Coo-Cah kitchen products:

| Standard             | Appliance Type                         | Key Tests Required                                               |
|----------------------|----------------------------------------|------------------------------------------------------------------|
| IEC 60335-1          | General household appliances — base    | Dielectric strength, leakage current, IPX rating, temperature rise |
| IEC 60335-2-24       | Refrigerators and food freezers        | Compressor test, gas leak simulation, cooling performance         |
| IEC 60335-2-25       | Microwave ovens                        | Microwave leakage, magnetron safety, door interlock               |
| IEC 60335-2-6        | Stationary cookers, hobs, ovens        | Surface temperature, thermostat accuracy, induction emission      |
| IEC 60335-2-14       | Blenders                               | Motor insulation, blade retention, overload protection            |
| IEC 60335-2-15       | Liquid heating appliances (kettles)    | Thermal cutout, limescale, boil-dry                               |
| IEC 60335-2-78       | Rice cookers                           | Temperature control, pressure safety                              |
| IEC 60335-2-9        | Toasters                               | Crumb tray safety, overload thermal cutout                        |

**IEC 60335 Certification Process:**

```
Step 1: Product Design Compliance Review
│ Design team reviews IEC 60335-1 and specific sub-standard with Regulatory Affairs
│ Safety critical components (thermal cutouts, cable strain relief, insulation class) specified
└── Design change log maintained for all safety-critical items

Step 2: Internal Pre-Compliance Testing (Coo-Cah QC Lab)
│ Dielectric strength test (hipot): all models
│ Leakage current measurement: all models
│ Temperature rise test: representative samples
└── Pre-compliance pass required before external submission

Step 3: External Type Testing (SON-accredited laboratory)
│ Submit to SON-designated test lab (NNPC Metrology Lab or Intertek)
│ Full IEC 60335-1 + relevant sub-standard tests conducted
│ Test report issued — valid for 3 years
└── Timeline: 4–8 weeks

Step 4: SON NIS Certification
│ Submit test report + technical file to SON
│ SON issues NIS registration certificate
│ NIS mark required on all products and packaging
└── Annual renewal required; audit every 3 years

Step 5: Production — SON Conformity Mark Applied
│ NIS conformity mark (C-Mark) printed on rating plate
│ SON approval number included in all product user manuals
└── MES label module triggered for every unit produced
```

---

## 3. R600a Refrigerant — NESREA Regulatory Requirements

R600a (isobutane) is a natural hydrocarbon refrigerant with zero ozone depletion potential (ODP = 0) and very low global warming potential (GWP = 3). However, it is flammable (Class A3 under ISO 817), making it subject to strict safety and handling regulations under NESREA's Ozone-Depleting Substances Regulations 2009 and Amended Regulations 2014.

### 3.1 NESREA Permits Required

| Permit / Licence                      | Authority                | Renewal Period | Key Obligation                                         |
|---------------------------------------|--------------------------|----------------|--------------------------------------------------------|
| ODS (Ozone Depleting Substances) Licence | NESREA                | Annual         | Annual reporting of R600a stocks, usage, and disposal  |
| Refrigerant Handling Licence          | NESREA + DPR            | Annual         | Licensed technicians only to charge, recover, dispose  |
| EIA Approval (Ozone Dept.)            | NESREA                  | One-off        | Part of factory EIA — gas handling chapter             |
| Lagos State Hazardous Substance Permit| Lagos State Env. Ministry | Annual        | Requires gas detection system report and safety plan   |

### 3.2 R600a Usage Annual Reporting (NESREA)

NESREA requires annual reporting of:
- Total R600a consumed (kg) by month and model
- Total R600a recovered from warranty/repair returns
- Total R600a disposed (via licensed disposal agent)
- Inventory at start and end of year
- Any spill or accidental release incidents

**MES Gas Charging Module** generates this report automatically from charging records (see [`mes-integration.md`](./mes-integration.md)).

### 3.3 R600a Safe Handling Obligations

| Obligation                                 | Standard / Requirement                        | Responsible        |
|--------------------------------------------|-----------------------------------------------|-------------------|
| Only NESREA-certified technicians charge R600a | NESREA Regulation 14                     | Factory Manager    |
| Gas detectors maintained + calibrated 6-monthly | NESREA + SON NIS                         | EHS Officer        |
| Ventilation system serviced quarterly       | Lagos State ATEX requirement                 | Maintenance Mgr    |
| All R600a cylinders tracked with lot codes  | MES Gas Module + NESREA reporting            | Store Keeper       |
| Emergency Response Plan posted in gas zone | NESREA + Lagos State EHS                     | EHS Officer        |
| Staff annual R600a safety training          | NESREA + Factories Act                       | HR / EHS           |

---

## 4. NESREA Environmental Impact Assessment (EIA)

The kitchen electronics factory is a Schedule 1 industrial project under NESREA EIA Act 1992. An EIA must be completed and approved before construction begins.

### 4.1 EIA Key Chapters

| Chapter                          | Content Required                                               | Led By              |
|----------------------------------|----------------------------------------------------------------|---------------------|
| Waste Management Plan            | Solid waste (PCB trim, SDA scraps); hazardous waste (refrigerant) | EHS + Operations  |
| Gas Handling Safety Plan         | R600a storage, charging, leak response, disposal               | EHS Officer         |
| Effluent / Water Discharge Plan  | Cooling water, wash water, solvent from SMT cleaning           | EHS Officer         |
| Noise Impact Assessment          | Compressor testing, production machinery, ventilation fans     | EHS + Acoustics     |
| Energy and Carbon Plan           | Solar strategy, CO₂ avoidance, annual reporting               | Energy Team         |
| Emergency Response Plan          | Fire, gas leak, chemical spill, evacuation                     | EHS Officer         |

---

## 5. SON NIS Product Registration — Schedule

| Product Category             | Applicable NIS Standard      | Application Timeline | Certification Target |
|------------------------------|------------------------------|----------------------|----------------------|
| Refrigerators (all models)   | NIS ISO 15502 / IEC 60335-2-24 | 3 months pre-launch | Q2 2026             |
| Microwave Ovens              | NIS 120 / IEC 60335-2-25     | 3 months pre-launch  | Q2 2026             |
| Electric Cookers (induction) | NIS / IEC 60335-2-6          | 3 months pre-launch  | Q3 2026             |
| Blenders, Kettles, Rice Cookers, Toasters | NIS / IEC 60335 sub-standards | 3 months pre-launch | Q3 2026 |

---

## 6. Incentives — Pioneer Status

The Coo-Cah Kitchen Electronics Factory qualifies for Pioneer Status under the Nigerian Investment Promotion Commission Act (NIPC) as a manufacturer in a priority industrial sector.

| Incentive                              | Benefit                                        | Qualification Criteria               |
|----------------------------------------|------------------------------------------------|--------------------------------------|
| Pioneer Status — 5-year CIT holiday    | 0% Corporate Income Tax for 5 years           | Manufacturing; > ₦500M investment    |
| Customs Duty Exemption (machinery)     | 0% import duty on qualifying production machinery | Capital goods importation under CITA |
| Industrial Training Fund (ITF) Waiver | 50% ITF levy reduction for first 5 years      | Approved training programme in place |
| Export Expansion Grant (EEG)           | 15% grant on export FOB value                  | NEPC-registered exporter             |

---

## 7. Ongoing Compliance Obligations Calendar

| Obligation                          | Frequency | Deadline/Window          | Responsible        |
|-------------------------------------|-----------|--------------------------|-------------------|
| SON NIS renewal audit               | Annual    | Product anniversary date | Regulatory Affairs |
| IEC 60335 re-test (on design change)| As needed | Within 60 days of change | QA Manager         |
| NESREA R600a annual report          | Annual    | 31 January               | EHS Officer        |
| NESREA licence renewal              | Annual    | 1 January                | EHS Officer        |
| Lagos State hazardous substance permit renewal | Annual | March | EHS + Legal      |
| EIA audit (NESREA review)           | Biennial  | Every 2 years            | EHS + External     |
| ISO 9001 surveillance audit         | Annual    | Per certification body schedule | QA Manager  |
| SON factory inspection              | Annual    | SON scheduled            | QA + Factory Mgr   |
| FIRS tax filing                     | Annual    | June 30                  | Finance            |

---

*For supply chain compliance (CoC, Form M), refer to [`supply-chain.md`](./supply-chain.md).*
*For gas charging traceability, refer to [`mes-integration.md`](./mes-integration.md).*
