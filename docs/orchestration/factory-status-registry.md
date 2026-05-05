# Factory Status Registry

> **Project Coo-Cah | Orchestration**
> **Document Version:** 1.0 | **Owner:** Group Operations & Programme Management
> **Update Frequency:** Monthly

---

## Overview

This registry tracks the commissioning status of every Coo-Cah factory across all verticals and locations. It is the single source of truth for programme management, investor reporting, and cross-factory dependency planning.

### Status Codes

| Code | Meaning |
|------|---------|
| `PLANNED` | Feasibility / design phase; no civil work commenced |
| `UNDER_CONSTRUCTION` | Civil works and/or equipment installation in progress |
| `COMMISSIONING` | Testing and qualification runs; production not yet commercial |
| `PHASE_1_ACTIVE` | Human-in-the-loop production; MES deployed; commercial production running |
| `PHASE_2_ACTIVE` | Collaborative automation active; robotic arms and AI QC deployed; digital twin live |
| `PHASE_3_ACTIVE` | Cognitive autonomous operation; lights-out lines certified |
| `ON_HOLD` | Delayed — awaiting capital, regulatory approval, or dependency |

---

## Electronics Vertical

| Factory | Location | Current Status | Phase 1 Start (Target) | Phase 2 Start (Target) | Phase 3 Start (Target) | Notes |
|---------|----------|---------------|----------------------|----------------------|----------------------|-------|
| Kitchen Electronics | Lagos, Nigeria | `PLANNED` | Q2 2026 | Q2 2028 | Q3 2031 | Phase 1 priority |
| [Garage/Power Electronics](https://github.com/oumar-code/coo-cah-factory-electronics-power) | Ogun State, Nigeria | `PLANNED` | Q2 2026 | Q3 2028 | Q3 2031 | Phase 1 priority; energy-critical · **Dedicated repo live** |
| Personal Electronics | Ogun State, Nigeria | `PLANNED` | Q2 2026 | Q2 2028 | Q2 2031 | Phase 1 priority; SMT lines |
| Smart Home & Office | Lagos, Nigeria | `PLANNED` | Q4 2026 | Q4 2028 | Q4 2031 | Dual SMT lines |
| Security Electronics | Lagos, Nigeria | `PLANNED` | Q3 2026 | Q1 2029 | Q1 2032 | NCC type approval required |
| Smart Estate/City | Kigali, Rwanda | `PLANNED` | Q3 2027 | Q1 2030 | Q1 2033 | Rwanda OpCo; IoT products |

---

## Chemicals Vertical

| Factory | Location | Current Status | Phase 1 Start (Target) | Phase 2 Start (Target) | Phase 3 Start (Target) | Notes |
|---------|----------|---------------|----------------------|----------------------|----------------------|-------|
| [Plastics & Polymers](https://github.com/oumar-code/coo-cah-factory-chemicals-plastics) | Ogun State, Nigeria | `PLANNED` | Q3 2026 | Q1 2029 | Q1 2032 | Tier 1 — feeds all other factories · **Dedicated repo live** |
| Heavy Chemicals | Delta State, Nigeria | `PLANNED` | Q2 2027 | Q2 2030 | Q2 2033 | Tier 3 — long-cycle |
| Fine Chemicals | Lagos, Nigeria | `PLANNED` | Q2 2027 | Q2 2030 | Q2 2033 | Tier 3; specialty chemicals |
| Fertilizer | Delta State, Nigeria | `PLANNED` | Q4 2027 | Q4 2030 | Q4 2033 | Tier 3; large capex |
| [Metallurgical & Minerals](https://github.com/oumar-code/coo-cah-factory-chemicals-metallurgical) | Delta State, Nigeria | `PLANNED` | Q4 2027 | Q4 2030 | Q4 2033 | Tier 1 for metals; Tier 3 for full ops · **Dedicated repo live** |

---

## Consumer Goods Vertical

| Factory | Location | Current Status | Phase 1 Start (Target) | Phase 2 Start (Target) | Phase 3 Start (Target) | Notes |
|---------|----------|---------------|----------------------|----------------------|----------------------|-------|
| Food & Beverages | Abuja, Nigeria | `PLANNED` | Q1 2027 | Q1 2029 | Q1 2032 | NAFDAC registration required |
| Personal Care | Lagos, Nigeria | `PLANNED` | Q2 2027 | Q2 2029 | Q2 2032 | NAFDAC registration required |
| Household Cleaning | Lagos, Nigeria | `PLANNED` | Q2 2027 | Q2 2029 | Q2 2032 | NAFDAC for some SKUs |
| Packaged Water | Lagos, Nigeria | `PLANNED` | Q1 2027 | Q1 2029 | Q1 2032 | NAFDAC water registration |
| Baby & Infant Products | Lagos, Nigeria | `PLANNED` | Q3 2027 | Q3 2030 | Q3 2033 | NAFDAC; stringent quality reqs |

---

## Lifestyle Vertical

| Factory | Location | Current Status | Phase 1 Start (Target) | Phase 2 Start (Target) | Phase 3 Start (Target) | Notes |
|---------|----------|---------------|----------------------|----------------------|----------------------|-------|
| Fashion & Apparel | Lagos, Nigeria | `PLANNED` | Q3 2027 | Q3 2030 | Q3 2033 | Phase 2 priority |
| Furniture & Home Décor | Abuja, Nigeria | `PLANNED` | Q3 2027 | Q3 2030 | Q3 2033 | Phase 2 priority |

---

## Group Summary

| Metric | Value |
|--------|-------|
| Total factories in portfolio | 17 |
| Currently `PHASE_1_ACTIVE` or above | 0 (pre-production) |
| Currently `PLANNED` | 17 |
| Currently `UNDER_CONSTRUCTION` | 0 |
| Target Phase 1 factories by end Y2 | 6 (Tier 1 Electronics + Plastics) |
| Target Phase 1 factories by end Y3 | 10 |
| Target Phase 1 factories by end Y5 | 17 |

---

## Programme Dependencies

The following cross-factory dependencies govern the sequencing of factory commissioning:

```mermaid
graph TD
    PLASTIC["Plastics Factory\n(PHASE_1_ACTIVE)"]
    METAL["Metallurgical\n(PHASE_1_ACTIVE)"]
    POWER["Garage/Power Electronics\n(PHASE_1_ACTIVE)"]

    KITCHEN["Kitchen Electronics"]
    PERSONAL["Personal Electronics"]
    SMART["Smart Home/Office"]
    SECURITY["Security Electronics"]

    PLASTIC -->|"Casings before commercial production"| KITCHEN
    PLASTIC -->|"Casings before commercial production"| PERSONAL
    METAL -->|"Frames before commercial production"| KITCHEN
    POWER -->|"Energy systems"| KITCHEN
    POWER -->|"Energy systems"| PERSONAL
```

---

## Revision History

| Date | Author | Changes |
|------|--------|---------|
| 2025-05-01 | Programme Management | Initial registry — all factories set to `PLANNED` |

---

*For factory-level detail, see the individual factory blueprint in [Factory Blueprints](../03-factories/index.md).*
*This registry is updated monthly by the Group Programme Management Office.*
