# ADR-005: ERP Platform Selection

**Status:** ACCEPTED  
**Date:** 2025-04-01  
**Deciders:** Group CFO, Group CTO, COO Nigeria, COO Rwanda  
**Technical Story:** [Issue #33 — ERP Platform Selection](https://github.com/oumar-code/Coo-Kah-Doks/issues/33)

---

## Context

Coo-Cah Technologies Holdings requires an ERP system to manage financial consolidation across 20+ subsidiaries, supply chain planning across 15+ factories, sales and distribution across 10 African markets, and HR management for 10,000+ eventual employees. The ERP must also serve as the orchestration layer above the MES — passing production orders down, receiving actuals up.

---

## Options Considered

### Option 1: SAP S/4HANA Cloud
**Pros:** World-class; deep manufacturing module (PP); native MES integration (SAP MII/ME); strong Africa implementations (MTN, Dangote, Nestlé Nigeria run SAP)  
**Cons:** Very expensive ($5–15M for initial scope); long implementation (18–36 months); requires certified SAP partners in Africa; over-engineered for Phase 1 (3 factories)

### Option 2: Oracle NetSuite
**Pros:** Cloud-native; proven for multi-entity / multi-currency; good for holding company structure; widely used by mid-market companies; reasonable price  
**Cons:** Manufacturing module less mature than SAP; MES integration requires custom API work; less known in West Africa manufacturing context

### Option 3: Odoo Community Edition (open source) → Enterprise as needed
**Pros:** Free community edition allows low-cost Phase 1 start; grows to Odoo Enterprise (manufacturing, multi-company); used by several Nigerian SMEs; strong community; native Python = Coo-Cah dev team can extend; open source means full data sovereignty  
**Cons:** Community edition requires significant customisation for manufacturing; Odoo Enterprise has per-user pricing that scales with headcount; less proven at Coo-Cah's eventual scale vs. SAP/Oracle

### Option 4: ERPNext (Frappe)
**Pros:** Open source; Nigerian community active; strong BOM + manufacturing module; free to self-host  
**Cons:** Limited enterprise support; manufacturing module not as mature as SAP/Odoo; fewer certified implementation partners; risky at holding company scale

---

## Decision

**Selected: Phased approach — Odoo Community (Phase 1) → Odoo Enterprise (Phase 2) → SAP S/4HANA evaluation at Phase 3**

**Phase 1 (Now–2027):** Odoo 17 Community with Coo-Cah customisations
- MES integration: Siemens Opcenter → Odoo via REST API (bidirectional: production orders down, actuals up)
- Modules: Accounting, Inventory, Manufacturing, Purchase, Sales, HR
- Hosting: Self-hosted on Coo-Cah cloud infrastructure (Rwanda data centre)
- Implementation: Coo-Cah IT team + Odoo partner in Lagos

**Phase 2 (2027–2030):** Migrate to Odoo Enterprise
- Add: Advanced multi-company, Quality, Subscription management, Project
- Retain: All Phase 1 customisations + MES integrations

**Phase 3 (2030+):** Evaluate SAP S/4HANA if scale demands it

---

## Consequences

**Positive:**
- Zero licence cost in Phase 1 allows CapEx to focus on factory equipment
- Odoo's Python stack matches Coo-Cah engineering team's skills
- Open source = no data lock-in; full API access for AI Platform integration

**Negative:**
- Phase 1 requires significant customisation investment for manufacturing workflows
- Odoo Enterprise licence costs will grow materially with headcount in Phase 2

**Neutral:**
- ADR-002 MES (Siemens Opcenter) has documented REST API for ERP integration — compatible

---

*Related ADRs: [ADR-002](./ADR-002-mes-platform-selection.md)*
