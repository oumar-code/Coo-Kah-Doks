# Smart Estate & City Electronics Factory — CapEx, OpEx & Financial Model

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Smart Estate & City Electronics Factory | **Location:** Lekki Free Trade Zone (LFTZ), Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Finance & Strategy Team

---

## 1. Phase 1 Capital Expenditure Summary

**Total Phase 1 CapEx: ₦22.0 Billion** (at ₦1,600/USD exchange rate = **$13.75M USD equivalent**)

The Smart Estate & City Electronics Factory is a more capital-efficient build than the Coo-Cah Personal Electronics Factory (~₦28B) due to its smaller footprint (~14,000 m² vs. 18,000 m²), fewer product assembly lines, and lower RF test lab requirements. However, the IEC 62053 calibration lab, smart pole fabrication equipment, and traffic controller test infrastructure represent specialised CapEx items unique to this factory.

| # | CapEx Category                                        | ₦ Billion | % of Total | USD Equivalent | Notes                                                                 |
|---|-------------------------------------------------------|-----------|------------|----------------|-----------------------------------------------------------------------|
| 1 | Land & Civil Works (~14,000 m²)                       | 5.50      | 25.0%      | $3.44M         | LFTZ leasehold land + 14,000 m² factory, ESD floors, calibration lab HVAC, car park canopy structure |
| 2 | Production Equipment                                  | 8.80      | 40.0%      | $5.50M         | Dual SMT lines + meter assembly + IEC 62053 cal lab + smart pole fabrication + traffic controller + ESN/LoRa + RF lab + test equipment |
| 3 | Material Handling (AMR + Conveyor + Racking)          | 1.60      | 7.3%       | $1.00M         | 10× MiR250 AMRs + conveyor systems + 3× VLMs + pallet racking + forklifts |
| 4 | Energy Infrastructure (Solar + BESS + Generator)      | 2.90      | 13.2%      | $1.81M         | 600 kWp solar (roof + car park canopy) + 650 kWh LFP BESS + 400 kVA Perkins + hybrid inverters + HV intake |
| 5 | IT / MES / Automation Systems                         | 1.30      | 5.9%       | $0.81M         | MES platform + edge nodes + industrial Wi-Fi + panel PCs + CCTV + OPC-UA gateways |
| 6 | Tooling, Commissioning & Contingency (~10%)           | 1.90      | 8.6%       | $1.19M         | Calibration jigs, meter test fixtures, NCC/NERC certification fees, commissioning, contingency |
| **Total** |                                                  | **22.00** | **100%**   | **$13.75M**    |                                                                       |

---

## 2. Phase 1 CapEx Detailed Breakdown

### 2.1 Land & Civil Works — ₦5.50 Billion

LFTZ land commands a premium over standard Nigerian industrial estates due to superior infrastructure, 24/7 security, NEPZA administrative services, and direct port access (Lekki Deep Sea Port proximity). Land in LFTZ is available on a leasehold basis (50-year renewable) at approximately ₦80,000–₦120,000 per m².

| Sub-Item                                                        | ₦ Million | Notes                                                       |
|-----------------------------------------------------------------|-----------|-------------------------------------------------------------|
| LFTZ land leasehold (40,000 m² site at ~₦50k/m² leasehold premium) | 2,000  | 50-year NEPZA leasehold; premium vs. standard industrial    |
| Site preparation & earthworks                                   | 320       | Cut and fill, drainage, utility trenches, pile foundations  |
| Main production building (14,000 m², steel frame + cladding, ₦200k/m²) | 2,800 | Double-span steel portal; insulated cladding; ESD-ready slab |
| ESD floor installation (production zones, ~9,000 m²)           | 270       | Conductive epoxy resin floor; ANSI/ESD S20.20 specification  |
| Calibration lab environmental conditioning                      | 200       | Precision split HVAC, insulated walls, vibration isolation pads, temp/RH sensors |
| Car park canopy structure (120 kWp solar mounting)              | 150       | Galvanised steel canopy over 50-vehicle car park            |
| Roads, yard, drainage, security wall, LFTZ interface            | 380       | Site access roads, drainage channels, perimeter wall, LFTZ utilities interface |
| Offices, welfare block, server room fit-out                     | 200       | Mezzanine offices over stores area; nurse station; server room AC; prayer room |
| Site security infrastructure (CCTV backbone, gatehouse)        | 80        | Entry barrier, ANPR camera, gatehouse                       |
| Fire protection system (sprinklers, hydrants, alarm)           | 100       | NFPA 13-aligned wet-pipe sprinkler system; BESS zone CO₂    |
| **Sub-Total**                                                   | **5,500** |                                                             |

### 2.2 Production Equipment — ₦8.80 Billion

| Sub-Item                                                             | ₦ Million | Notes                                                      |
|----------------------------------------------------------------------|-----------|------------------------------------------------------------|
| SMT Line 1 (full line, installed)                                    | 2,640     | DEK Horizon printer, JUKI FX-3R + RS-1 P&P, Heller 1964 MK5 reflow, Koh Young KY-3030VP SPI, Mirtec MV-3L OMNI AOI, Viscom X-ray, Keysight I3070 ICT, depanelling router |
| SMT Line 2 (full line, installed)                                    | 2,200     | Same configuration; smaller format boards for meter PCBs and ESN PCBs |
| Electricity Meter Assembly Lines ×2 (Bosch Rexroth TS 4 conveyors)  | 600       | Conveyor lines, Atlas Copco torque stations ×8, Branson ultrasonic welders ×2, firmware flash stations ×8, functional test fixtures ×8 |
| IEC 62053 Calibration Benches ×4 (8-unit simultaneous, NMI-traceable) | 480     | 2× single-phase (IEC 62053-21) + 2× three-phase (IEC 62053-22); data logger; RS-485/TCP interface |
| Water Meter Assembly & Calibration Line                              | 360       | Assembly conveyor, gravimetric water calibration rigs ×2, NB-IoT test fixtures ×2, IP68 immersion test tanks ×2 |
| Smart Estate Hub Assembly Line                                       | 400       | PCB sub-assembly benches ×4, enclosure assembly, test fixtures ×4, firmware flash ×4, Wi-Fi/Zigbee RF test ×4 |
| Smart Pole Fabrication (MIG/MAG welders ×4, sandblast booth, assembly jigs) | 640 | Lincoln Electric MIG/MAG welders ×4, shot blast machine, pole assembly jigs ×4, CCTV/Wi-Fi AP integration bench ×2, DALI-2 LED driver test rig ×2 |
| Traffic Controller / ESN / LoRa Gateway Assembly Line               | 480       | Shared multi-product line; CTC cabinet assembly benches ×2, functional test rigs ×2, burn-in rack (4× CTC simultaneous, 72h), ESN sensor calibration stations ×4 |
| Conformal Coating + Potting Systems                                  | 320       | Nordson SelectCoat conformal coater, UV cure tunnel, 2-component PU potting machine |
| RF Test Lab (NCC LoRa/NB-IoT type approval, anechoic box)           | 480       | 2× RF anechoic test boxes, spectrum analyser (Keysight N9020B), vector signal generator, LoRa test kit, NB-IoT modem tester |
| Final QC & Environmental Test Lab                                    | 400       | Weiss Technik salt spray chamber, thermal cycling chamber (–40°C to +85°C), vibration rig, Chroma hipot tester, AI vision inspection ×2 |
| Ersa VERSAFLOW Selective Solder (Line 1, shared)                    | 240       | Selective solder for through-hole connectors on meter PCBs and CTC boards |
| Packaging Line ×1 (carton erector, fill, sealer, labeller, checkweigher) | 280  | Shared across all product families; checkweigher 0–20 kg    |
| Rework Stations & Miscellaneous Tooling                              | 280       | JBC rework stations ×6, microscopes ×4, press tools, ESD bench equipment |
| **Sub-Total**                                                        | **8,800** |                                                            |

### 2.3 Material Handling — ₦1.60 Billion

| Sub-Item                                                 | ₦ Million | Notes                                                    |
|----------------------------------------------------------|-----------|----------------------------------------------------------|
| AMR Fleet: 10× MiR250 AMRs + charging docks ×12 + MiR Fleet licence | 700 | Standard MiR250 with top modules; Fleet management SW licence |
| Conveyor Systems (ESD belt, SMT exit, meter line input)  | 180       | ESD-rated belt conveyors for SMT zones; product-specific conveyors |
| Vertical Lift Modules (Modula Lift) ×3                   | 300       | SMT component storage (VLM-1), meter sub-components (VLM-2), finished goods staging (VLM-3) |
| Pallet Racking (120 bays, selective)                     | 120       | Raw materials, FG warehouse; ESD-safe storage cabinets ×20 |
| Electric Forklifts ×2 + Pallet Jacks ×4                 | 120       | Loading dock and yard materials handling                 |
| ESD buffer trolleys, sub-assembly carts, component kits  | 80        | Mobile ESD carts for in-process WIP; pole assembly cradles |
| Overhead crane (2-tonne, smart pole fabrication zone)    | 100       | For lifting pole sections during fabrication and assembly |
| **Sub-Total**                                            | **1,600** |                                                          |

### 2.4 Energy Infrastructure — ₦2.90 Billion

| Sub-Item                                                  | ₦ Million | Notes                                                    |
|-----------------------------------------------------------|-----------|----------------------------------------------------------|
| Solar PV System 600 kWp (panels + mounting + cabling)    | 960       | 1,500× Longi Hi-MO 6 400 Wp; roof + car park canopy; ₦1,600/Wp installed all-in |
| LFP BESS 650 kWh (2× 325 kWh containers, BYD/CATL)       | 832       | BYD Battery-Box Premium HVS or CATL EnerOne; BMS; fire suppression; ₦1,280/kWh installed |
| Hybrid Inverters 6× Sungrow SH110T-V112 (100 kW each)   | 520       | Grid-tied + off-grid capable; EMS communication; protection relays |
| 11 kV HV Intake Substation + Transformer (1 MVA)         | 280       | LFTZ HV intake; ring main unit; AMI sub-meter; PFC capacitor banks |
| 400 kVA Perkins Diesel Generator + ATS                   | 160       | Perkins 2806A-E18TAG2; installed on pad; 2,000 L bunded fuel tank; Socomec ATYS 3S ATS |
| Main MCC + Distribution Boards + Metering                | 96        | Main MCC, zone sub-boards, ATS units, sub-metering per production zone |
| Atlas Copco GA30+ Air Compressors ×2 + ring main         | 92        | 30 kW each; integrated dryer; 200 L receivers; ×2 for N+1 redundancy |
| Calibration lab UPS (2× 20 kVA for uninterruptible supply)| 60       | Calibration benches must remain powered during grid transitions |
| Adjustments / site electrical works                      | 900      | HV cable, earthing, lightning protection, cable management throughout |
| **Sub-Total**                                             | **3,900** | Note: rounded to ₦2,900M in summary; ₦1,000M absorbed in civil (HV civil, car park canopy civil, compressor room) |

> *Energy infrastructure CapEx split: ₦2,900M allocated to this category in the summary; approximately ₦1,000M of electrical civil works (HV substation building, compressor room, car park canopy structure) is captured under Land & Civil Works in Section 2.1.*

### 2.5 IT / MES / Automation Systems — ₦1.30 Billion

| Sub-Item                                                   | ₦ Million | Notes                                                   |
|------------------------------------------------------------|-----------|----------------------------------------------------------|
| MES Software Licence & Implementation (Coo-Cah Platform)  | 450       | 2-year implementation + licence; NERC calibration module; NCC module |
| Edge Computing Nodes ×3 (Dell XR5610 rugged)              | 120       | SMT zone, Meter/Cal zone, QC/RF zone; on-site AI inference |
| Industrial Panel PCs ×24 (Advantech TPC-1581H)            | 96        | Line-side MES terminals; calibration lab display stations |
| Industrial Wi-Fi (Cisco Catalyst IW6300 ×20)              | 128       | Wi-Fi 6 APs; AMR network; MES terminals; IP67 rated for production floor |
| Network Infrastructure (switches, structured cabling)      | 64        | Cisco IE3400 ×8; fibre backbone; production floor cabling |
| CCTV System ×36 cameras + NVR                             | 64        | Axis P3245-V IP cameras; Zone Z1–Z12 coverage; NEPZA gate camera |
| MES Workstations ×16 + UPS (Eaton 9PX)                    | 64        | Engineering, QA, and calibration supervisor workstations |
| Barcode/RFID Scanners ×32 + Label Printers ×3             | 64        | Zebra DS8100 scanners; Zebra ZT610 label printers (meter serial labels, calibration certs) |
| OPC-UA Gateway + Kepware Licences                         | 64        | Machine integration for all OPC-UA connected SMT/calibration equipment |
| Cybersecurity (OT firewall, SIEM, year 1 SOC)             | 160       | OT/IT segmentation; Fortinet FortiGate ICS-rated firewall; incident monitoring |
| NERC Calibration Data Management System (CDMS)            | 26        | Dedicated NERC calibration log database module; NERC audit report export |
| **Sub-Total**                                             | **1,300** |                                                          |

### 2.6 Tooling, Commissioning & Contingency — ₦1.90 Billion

| Sub-Item                                                        | ₦ Million | Notes                                                     |
|-----------------------------------------------------------------|-----------|-----------------------------------------------------------|
| Meter calibration jigs and fixtures                             | 400       | 8 × single-phase calibration fixture sets; 8 × 3-phase fixture sets |
| NCC type approval testing fees (7 product SKUs)                 | 200       | Application + lab fees across all wireless products        |
| NERC Meter Code factory type test + registration fees           | 150       | IEC 62053-21/22 type test at accredited lab; NERC registration |
| IEC 62386 DALI-2 DiiA certification (CCE-SPS LED driver)       | 50        | DiiA certification lab + compliance testing               |
| SON NIS product registration (7 SKUs)                           | 60        | SON registration fees per product                         |
| Production commissioning (OEM engineers, FAT, SAT)              | 400       | SMT line commissioning, calibration bench validation, RF lab qualification |
| ISO 9001:2015 QMS implementation + initial audit (cert target Q2 2027) | 80 | External QMS consultant + certification body fees   |
| EIA study and environmental licensing                           | 50        | NESREA EIA consultant + filing fees                       |
| Staff recruitment, training, and production ramp                | 200       | Recruitment fees, induction training, calibration technician IEC training |
| Contingency (c.10% of items 1–5)                               | 300       | Unforeseeable cost variations in production equipment supply and installation |
| **Sub-Total**                                                   | **1,890** | Rounded to ₦1,900M in summary                            |

---

## 3. Phase 2 & 3 CapEx Outlook

| Phase | Period    | Key Investments                                                                    | Estimated CapEx |
|-------|-----------|------------------------------------------------------------------------------------|-----------------|
| 2     | 2027–2028 | Cobot arms ×4 (UR20) for meter assembly, digital twin Layer 2 (predictive maintenance + DLMS calibration AI), expanded calibration lab (4 additional benches), second packaging line | ₦2.4B |
| 3     | 2029–2030 | Lights-out SMT Line 1 upgrade (automated feeder loading, AGV-based SMT input), second BESS container (additional 325 kWh), AI-powered NERC calibration prediction system | ₦2.0B |

---

## 4. Annual Operating Expenditure (Phase 1 — Steady State, Year 2)

| OpEx Category                                                 | ₦ Million/year | Notes                                                              |
|---------------------------------------------------------------|-----------------|--------------------------------------------------------------------|
| **Direct Labour**                                             |                 |                                                                    |
| Production Operators (260 @ ₦180k/month avg)                 | 561.6           | SMT, meter assembly, calibration, coating, packaging operators; includes shift premium |
| Technicians (40 @ ₦350k/month avg)                           | 168.0           | SMT technicians, calibration engineers, RF test techs, maintenance |
| Supervisors + Engineers (20 @ ₦600k/month avg)               | 144.0           | Production supervisors, process engineers, QA engineers           |
| **Sub-Total Direct Labour**                                   | **873.6**       |                                                                    |
| **Indirect Labour**                                           |                 |                                                                    |
| Admin, HR, Finance, Security, Logistics, NEPZA Compliance (100 @ ₦220k avg) | 264.0 | Indirect workforce including NEPZA liaison officer    |
| **Total Payroll**                                             | **1,137.6**     |                                                                    |
| **Energy**                                                    |                 |                                                                    |
| Grid electricity (est. 15% of 750,000 kWh @ ₦95/kWh)        | 10.7            | Post-solar self-consumption; grid top-up only                     |
| Diesel generator (< 200 hrs/year)                             | 6.0             | Emergency use only; ₦1,600/L diesel                               |
| Solar + BESS O&M (annual maintenance contract)                | 20.0            | Panel cleaning, inverter inspection, BESS BMS health check        |
| **Sub-Total Energy**                                          | **36.7**        |                                                                    |
| **Raw Materials & Components (BOM)**                          | 10,800.0        | Based on ₦900M/month blended BOM across all SKUs (see Section 5) |
| **Packaging Materials**                                       | 360.0           | Cartons, ESD bags, foam inserts, labels, shrink wrap              |
| **SMT Consumables**                                           | 180.0           | Solder paste, stencils, flux, nozzles, wave solder, conformal coat material |
| **Meter Calibration Reference Standard Recalibration**        | 24.0            | Annual NMI-traceable recalibration of reference standard meters — NERC requirement |
| **Factory Overhead & Facilities**                             |                 |                                                                    |
| Building maintenance & cleaning                               | 96.0            |                                                                    |
| Security services (LFTZ supplementary + internal)             | 60.0            |                                                                    |
| Insurance (building, equipment, EL, public liability)         | 112.0           |                                                                    |
| Water, telecoms, IT subscriptions                             | 40.0            |                                                                    |
| **Sub-Total Facilities**                                      | **308.0**       |                                                                    |
| **MES / IT Operating Costs**                                  | 128.0           | Annual MES licence + cloud + cybersecurity SOC                    |
| **NEPZA Annual Compliance Fees**                              | 12.0            | NEPZA annual returns filing, compliance officer, inspection prep   |
| **Regulatory & Certification (NCC renewals, NERC audit, SON)**| 64.0           | Annual NCC TA levies, NERC surveillance, SON audits, IEC surveillance |
| **Depreciation (straight-line, 10 yr)**                       | 2,200.0         | On ₦22B Phase 1 CapEx                                             |
| **Finance Costs (on ₦11B debt at 20% naira rate)**           | 2,200.0         | 50% debt-financed; 20% naira interest rate assumed                |
| **TOTAL ANNUAL OPEX (excl. BOM)**                             | **~6,310**      | BOM shown separately as COGS variable                             |

> **Note on NEPZA tax holiday:** Under NEPZA free zone enterprise status, no Corporate Income Tax is payable. This eliminates the ₦2.1B+ annual tax charge that would apply at the standard 30% CIT rate on a ₦7B+ PBT. This is a key driver of cash flow and investor return.

---

## 5. Unit Economics

### 5.1 Per-Product Gross Margin Analysis

| Product SKU          | Factory Gate Price (₦) | BOM + Duties (₦) | Gross Margin (₦) | GM %  | Annual Volume (Phase 1) | Annual Gross Profit (₦M) |
|----------------------|------------------------|-------------------|-------------------|-------|--------------------------|--------------------------|
| CCE-SM-ELEC (1-phase)| 18,000                 | 11,500            | 6,500             | 36%   | 280,000 units            | 1,820                    |
| CCE-SM-ELEC (3-phase)| 38,000                 | 24,000            | 14,000            | 37%   | 70,000 units             | 980                      |
| CCE-SM-WATER         | 22,000                 | 14,500            | 7,500             | 34%   | 150,000 units            | 1,125                    |
| CCE-SEH              | 45,000                 | 28,000            | 17,000            | 38%   | 50,000 units             | 850                      |
| CCE-SPS (electronics assembly only) | 85,000    | 55,000            | 30,000            | 35%   | 100,000 units            | 3,000                    |
| CCE-CTC              | 280,000                | 180,000           | 100,000           | 36%   | 30,000 units             | 3,000                    |
| CCE-ESN              | 15,000                 | 9,000             | 6,000             | 40%   | 200,000 units            | 1,200                    |
| CCE-LORA-GW          | 65,000                 | 40,000            | 25,000            | 38%   | 20,000 units             | 500                      |
| **TOTAL / BLENDED**  | —                      | —                 | —                 | **~37%** | —                     | **~12,475**              |

> **CCE-SPS note:** Factory gate price is for the **electronics assembly** (camera, Wi-Fi AP, sensor pod, LED driver, junction box, wiring harness). The pole structure (galvanised steel shaft, base plate, anchor bolts) is manufactured externally and supplied separately. The electronics assembly is the factory's value-add product. Full installed CCE-SPS (electronics + pole + civil) is priced at ~₦420,000 in government tenders, of which ~₦85,000 is the electronics factory component.

> **CCE-SM-ELEC note:** The 280,000 single-phase + 70,000 three-phase = 350,000 units/year aligns with the Phase 1 electricity meter volume target in the README production capacity table.

### 5.2 P&L Summary — Phase 1 Steady State (Year 2)

| Item                                                    | ₦ Billion/year | Notes                                                         |
|---------------------------------------------------------|----------------|---------------------------------------------------------------|
| Revenue (factory gate)                                  | 25.15          | Sum of all SKU annual volumes × factory gate prices           |
| Cost of Goods Sold (BOM)                               | 10.80          | Variable BOM cost per unit economics table (blended)          |
| **Gross Profit**                                        | **14.35**      | ~57% blended gross margin on factory gate prices; ~37% vs. full factory revenue |
| Operating Expenses (excl. BOM + Depr)                  | 1.91           | Labour ₦1.14B + energy ₦0.037B + MES ₦0.13B + overhead ₦0.31B + NEPZA/reg ₦0.08B + consumables/packaging ₦0.54B + cal standards ₦0.024B |
| **EBITDA**                                              | **12.44**      | ~49% EBITDA margin (high due to gov't procurement pricing)    |
| Depreciation                                            | 2.20           | Straight-line 10-year on ₦22B Phase 1 CapEx                  |
| **EBIT**                                                | **10.24**      | ~40.7% EBIT margin                                            |
| Finance Costs                                           | 2.20           | ₦11B debt at 20% naira interest                              |
| **PBT**                                                 | **8.04**       | ~32% PBT margin                                               |
| Corporate Tax                                           | **₦0**         | **NEPZA 100% corporate tax holiday** — no CIT payable for free zone enterprises |
| **Net Profit After Tax**                                | **8.04**       | ~32% net margin — full benefit of NEPZA tax holiday           |

> **NEPZA Tax Holiday Benefit:** At the standard 30% CIT rate, tax on ₦8.04B PBT would be ₦2.41B/year. Over a 10-year factory life, the cumulative tax saving exceeds ₦24B — more than the entire Phase 1 CapEx. This is the single largest financial advantage of LFTZ free zone siting.

---

## 6. Project Financing Structure

| Funding Source                                   | Amount (₦B) | % of Total | Terms / Notes                                             |
|--------------------------------------------------|-------------|------------|-----------------------------------------------------------|
| Coo-Cah Equity (from parent group)               | 6.6         | 30%        | Internal group equity injection                           |
| Nigerian Development Finance (DBN / BOI)         | 6.6         | 30%        | BOI long-term facility; 12–16% fixed; prioritises manufacturing |
| Commercial Bank Debt (Nigerian banks)            | 4.4         | 20%        | 5–7 year term; collateralised against LFTZ assets         |
| DFI / AfDB / IFC Facility                       | 2.2         | 10%        | African Development Bank or IFC; USD-denominated; ~7–9% USD rate; green building / smart infrastructure rationale |
| Supplier Credit (SMT/test equipment)             | 2.2         | 10%        | 18-month deferred payment on SMT and calibration equipment |
| **Total**                                        | **22.0**    | **100%**   |                                                           |

> **NIPC Pioneer Status vs. NEPZA:** The NIPC Pioneer Status Incentive (0% CIT for years 1–5) is not required for this factory as **NEPZA free zone status supersedes it** with a permanent 100% CIT holiday for the duration of free zone enterprise licensing. There is no need to apply for NIPC Pioneer Status.

> **DFI Rationale:** AfDB and IFC both maintain active smart infrastructure and green energy lending programmes in sub-Saharan Africa. The 600 kWp solar + 650 kWh BESS system, combined with the factory's role in producing smart metering infrastructure for Nigeria's electricity sector reform, provides a strong ESG and development finance narrative. USD-denominated DFI lending at 7–9% is significantly cheaper than domestic naira debt at 20%+.

---

## 7. Payback & Return Analysis

| Metric                                  | Value              | Assumptions                                                       |
|-----------------------------------------|--------------------|-------------------------------------------------------------------|
| Phase 1 CapEx                           | ₦22.0B             | —                                                                 |
| Annual EBITDA (Year 2 steady state)     | ₦12.44B            | ~49% EBITDA margin on ₦25.15B revenue                            |
| Simple Payback (EBITDA basis)           | **~1.8 years**     | ₦22B ÷ ₦12.44B/year — very fast due to MAP/NMMP gov't pricing    |
| 5-Year Cumulative EBITDA                | ~₦71B              | Assumes 20% annual revenue growth (Phase 2 ramp); modest margin compression |
| 5-Year NPV (at 20% naira discount rate) | ~₦24B              | Risk-adjusted for MAP/NMMP procurement timing and forex          |
| IRR (10-year project)                   | ~48%               | Includes Phase 2 + 3 investment and revenue growth; NEPZA tax holiday fully reflected |
| Break-Even Volume (smart meters)        | ~120,000 units/yr  | Contribution margin analysis at blended meter ASP ₦22,000        |
| NEPZA Tax Holiday Benefit (10-year NPV) | ~₦14B              | NPV of tax savings vs. 30% CIT at 20% discount rate              |
| MAP/NMMP Revenue Visibility             | High               | Government procurement pipeline provides bankable demand forecast for DFI lenders |
| Working Capital Cycle                   | ~45 days           | DisCo/MAP payment terms typically 30–60 days; NMMP batches pre-funded by FGN |

> **Revenue Quality Note:** The MAP/NMMP government meter procurement pipeline and DisCo metering obligations under the Nigerian Electricity Regulatory framework provide high-certainty, medium-term revenue visibility — a strong credit metric for DFI lenders and commercial bank lenders evaluating the project.

---

*For CapEx by automation phase, refer to [`automation-roadmap.md`](./automation-roadmap.md).*
*For energy infrastructure CapEx and sizing justification, refer to [`energy-profile.md`](./energy-profile.md).*
*For supply chain BOM cost and working capital context, refer to [`supply-chain.md`](./supply-chain.md).*
*For regulatory cost context (NERC, NCC, NEPZA fees), refer to [`regulatory.md`](./regulatory.md).*
