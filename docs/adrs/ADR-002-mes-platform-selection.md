# ADR-002: MES Platform Selection

**Status:** ACCEPTED  
**Date:** 2025-02-10  
**Deciders:** Group CTO, CTO Rwanda, COO Nigeria, Head of Smart Factory Core  
**Technical Story:** [Issue #18 — MES Platform Selection](https://github.com/oumar-code/Coo-Kah-Doks/issues/18)

---

## Context

The Manufacturing Execution System (MES) is the operational backbone of every Coo-Cah factory. It connects the ERP (business planning layer) to the shop floor (physical execution layer), translating production orders into real-time work instructions, tracking WIP, recording performance data, and feeding the Central AI Platform.

The MES decision is consequential:
- **High switching cost:** Once a factory is running on an MES, changing platforms requires significant re-training, re-integration, and risk to production continuity
- **Data foundation:** The MES is the primary source of the production data that trains our AI models — the quality and structure of this data depends on the MES chosen
- **Cross-factory integration:** With 15+ factories planned, all running on the same MES reduces integration burden and allows group-wide benchmarking
- **Vendor dependence:** MES platforms lock in both data schemas and operational workflows

### Requirements
1. **Functional:** Work order management, materials management, quality (SPC), equipment management (OEE), traceability, labour management, document control
2. **Integration:** Native OPC-UA, REST API for integration with IoT/SCADA, ERP (SAP/Oracle/Odoo), AI platform, AMR fleet management, EMS
3. **Scalability:** Must support from 1 factory (pilot) to 15+ factories with centralised visibility
4. **Cloud/Edge hybrid:** Cloud management for group-level dashboards; edge node deployment for factory-floor real-time operations (resilient to internet outages)
5. **Localisation:** Must support multiple currencies, English language (minimum), and Unicode for future African language support
6. **Vendor stability:** Vendor must have proven presence in manufacturing MES for ≥ 10 years
7. **Total Cost:** MES licensing + implementation + 5-year support must fit within $3–5M budget for first 3 factories

---

## Decision Drivers

- Data quality and completeness is the single most important input to the AI platform
- Operational continuity during internet outages is non-negotiable for African factory environments
- Cross-factory standardisation reduces training costs and enables group-wide OEE benchmarking
- The platform must be extensible to support Phase 2 and Phase 3 automation enhancements
- Vendor must offer local (Africa-based) implementation and support partners

---

## Options Considered

### Option 1: Siemens Opcenter (formerly Camstar + SIMATIC IT)
**Description:** Enterprise MES platform from Siemens, part of the Siemens Digital Industries Software portfolio. Used by major manufacturers across automotive, electronics, food & beverage, and pharmaceuticals globally.

**Pros:**
- Market-leading MES with 30+ years of manufacturing domain expertise
- Deep integration with Siemens SCADA (SIMATIC), PLCs, and TIA Portal ecosystem
- Native OPC-UA support; strong REST API
- Cloud-managed (SaaS) with on-premise edge nodes for resilient factory operation
- Proven multi-site deployments across 50+ sites (e.g., Bosch, Henkel, BASF)
- Strong digital twin integration (Siemens Xcelerator platform)
- Siemens has a West Africa office (Lagos) and East Africa partners (Nairobi)
- Pre-built connectors for SAP, Oracle, and major ERP systems

**Cons:**
- Higher licence cost — enterprise pricing ($800K–$1.5M for first 3 factories)
- Complex implementation (typically 9–18 months per factory cluster)
- Requires certified Siemens implementation partner
- Perceived as "heavy" for smaller factories — may be over-engineered for Phase 1 pilot

**Cost estimate:** $1.2M licence + $600K implementation per 3-factory cluster; $200K/year support  
**Verdict:** ✅ Shortlisted — strong candidate for Phase 1 electronics factories

---

### Option 2: Aveva MES (formerly Wonderware MES)
**Description:** MES from AVEVA (now part of Schneider Electric), widely used in process manufacturing (chemicals, food & beverage, pharmaceuticals).

**Pros:**
- Strong in process industry verticals (chemicals, food & beverage) — directly relevant to Coo-Cah's Phase 2 factories
- Good integration with OSIsoft PI System (process historian)
- Competitive pricing

**Cons:**
- Less strong in discrete/electronics manufacturing compared to Siemens Opcenter
- AVEVA/Schneider Electric integration following acquisition has caused product uncertainty
- Limited implementation partner presence in West Africa
- Digital twin integration less mature than Siemens

**Cost estimate:** $800K licence + $500K implementation; $180K/year support  
**Verdict:** 🟡 Shortlisted as supplementary option for Phase 2 chemicals/food factories only

---

### Option 3: SAP Manufacturing Execution (SAP ME / Digital Manufacturing Cloud)
**Description:** SAP's MES offering, tightly integrated with SAP S/4HANA ERP.

**Pros:**
- Best-in-class ERP integration if SAP S/4HANA is the group ERP
- Single vendor for MES + ERP reduces integration complexity
- Strong analytics via SAP Analytics Cloud

**Cons:**
- Extremely high total cost of ownership (TCO) — SAP licensing notoriously expensive
- Heavy dependency on SAP S/4HANA; poor value if group ERP is not SAP
- Limited flexibility — customisation is difficult and expensive
- Long implementation cycles (18–24 months)
- Overkill for Phase 1 pilot factories; scales poorly for small production volumes

**Cost estimate:** $2–3M licence + $1–2M implementation  
**Verdict:** ❌ Rejected — cost/complexity ratio too high for Coo-Cah's phased approach

---

### Option 4: Open-Source / Custom-Built MES (Python + PostgreSQL + React)
**Description:** Build a custom MES using open-source components (Django/FastAPI backend, PostgreSQL time-series database, React dashboard), deeply integrated with the Central AI Platform.

**Pros:**
- Maximum customisation for Coo-Cah-specific workflows
- Zero licence cost
- Native integration with AI platform
- Full data ownership and control

**Cons:**
- Build time: 18–24 months before production-ready — unacceptable delay to first factory
- Requires dedicated engineering team (10–15 engineers) to build and maintain
- All manufacturing domain expertise must be built from scratch
- High risk: production MES systems must be extremely reliable; custom builds carry higher failure risk
- No vendor support for troubleshooting production issues
- Not bankable: DFI lenders often require proven enterprise systems in manufacturing finance

**Cost estimate:** $0 licence + $3–5M engineering team cost + 24-month delay  
**Verdict:** ❌ Rejected for Phase 1–2; re-evaluate as custom AI-native MES for Phase 3 only

---

### Option 5: Infor CloudSuite Industrial (SyteLine)
**Description:** Cloud ERP with integrated MES capabilities from Infor, targeting industrial manufacturers.

**Pros:**
- Combined ERP + MES reduces vendor count
- Good for discrete manufacturing
- Strong North American customer base in electronics and industrial

**Cons:**
- Limited presence and support in Sub-Saharan Africa
- MES capabilities less deep than dedicated MES platforms
- Not widely adopted by African manufacturers — limited local talent pool

**Cost estimate:** $700K–$1M  
**Verdict:** ❌ Rejected — insufficient African presence and support

---

## Decision

**Selected: Siemens Opcenter as the group standard MES for Phase 1 and Phase 2 factories.**

**With the following provisions:**
- **Discrete manufacturing factories** (electronics, lifestyle): Siemens Opcenter Execution Discrete
- **Process manufacturing factories** (chemicals, food & beverage, cosmetics): Siemens Opcenter Execution Process — if Opcenter Process proves inadequate during Phase 1 chemicals factory design, AVEVA MES is the fallback for process-only factories
- **Deployment model:** SaaS management (multi-factory visibility from Rwanda) + on-premise edge nodes at each factory (resilient to internet outages)
- **Phase 3 review:** A custom AI-native MES built on the Central AI Platform stack will be evaluated when the Rwanda AI team has sufficient manufacturing domain expertise (target: Year 5 evaluation)

---

## Consequences

### Positive
- Battle-tested platform reduces operational risk during Phase 1 ramp-up
- Rich, structured production data from day 1 feeds the AI platform effectively
- Group-wide OEE benchmarking possible across all factories on same platform
- Siemens ecosystem (SCADA, PLCs, digital twin) provides coherent technology stack
- Bankable for DFI lenders
- Local partner (Siemens Nigeria + regional partners) provides in-country support

### Negative / Trade-offs
- Higher upfront cost vs. open-source alternative
- Vendor lock-in to Siemens ecosystem — switching costs are high in Year 3+
- Implementation requires Siemens-certified partners — limited pool in Nigeria/Rwanda/Kenya
- Some factory-specific workflows will require configuration workarounds

### Risks

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|-----------|
| Implementation partner delays | Medium | High | Pre-qualify 2 partners; include penalty clauses in contract |
| Opcenter version upgrade disruption | Low | Medium | Test upgrades on staging environment; upgrade during planned shutdown |
| Internet outage cutting cloud MES access | Medium | High | Edge node deployment mandatory; local operation continues without cloud |
| Siemens pricing increases | Medium | Low | Multi-year licence agreement with price cap clauses |
| Process factories require AVEVA instead | Medium | Low | AVEVA fallback pre-approved; evaluate during Phase 2 chemicals factory design |

---

## Integration Architecture

```
Factory Floor (PLCs, IoT, SCADA)
         ↕ OPC-UA
Siemens Opcenter Edge Node (on-premise)
         ↕ REST API + Event streaming
Central AI Platform (Rwanda)
         ↕ REST API
ERP System (SAP/Oracle/Odoo)
         ↕ Bidirectional sync
Opcenter Cloud (multi-factory dashboard)
```

---

## Compliance Notes

- ISO 9001:2015 — Opcenter supports all QMS documentation and process control requirements
- ISO 45001:2018 — Safety incidents and near-misses can be recorded in Opcenter
- FDA 21 CFR Part 11 — Opcenter supports electronic records/signatures (relevant for food & pharma factories)
- NAFDAC compliance — Opcenter traceability module supports full batch/lot genealogy required by NAFDAC

---

## Review Date

This ADR should be reviewed:
- Before Phase 2 chemicals factory MES design (evaluate Opcenter Process vs. AVEVA)
- Before Phase 3 (evaluate custom AI-native MES as replacement for Opcenter)

Next scheduled review: **February 2027**

---

*Approved by: Group CTO | Coo-Cah Technologies Holdings*
