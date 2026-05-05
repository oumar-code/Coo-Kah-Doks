# ADR-004: AMR Fleet Platform Selection

**Status:** ACCEPTED  
**Date:** 2025-03-18  
**Deciders:** Group COO, Head of Smart Factory Core, Factory Engineering Leads  
**Technical Story:** [Issue #29 — AMR Fleet Platform](https://github.com/oumar-code/Coo-Kah-Doks/issues/29)

---

## Context

Coo-Cah's 15+ factories will collectively deploy **100+ Autonomous Mobile Robots (AMRs)** for intralogistics — component kitting, WIP transport, finished goods movement to FGW, and MRO parts delivery. A unified AMR platform decision is required to enable:

- Cross-factory fleet management from a single dashboard
- Standardised MES integration (AMR mission triggers from MES WIP tracking)
- Group-wide data collection for AI-driven fleet optimisation
- Procurement leverage through single-vendor volume

### Requirements

1. **Multi-site management:** 100+ AMRs across 15+ factories on a single management platform
2. **Payload range:** 100 kg (small components) to 500 kg (large display panels, inverter chassis, furniture)
3. **MES integration:** REST API for MES to trigger and track missions; mission result written back to MES WIP record
4. **Charging management:** Automated opportunity charging; fleet-level battery state reporting
5. **MQTT/OPC-UA support:** For DT integration and telemetry reporting
6. **Safety standard:** ISO 3691-4 compliant; CE marked; laser safety scanner
7. **African climate:** Operate reliably at 28–42°C ambient, 60–90% relative humidity
8. **After-sales support:** Regional support or maintenance-trainable programme in Nigeria/Rwanda

---

## Options Considered

### Option 1: MiR (Mobile Industrial Robots — now part of Teradyne)
**Pros:** Market leader; MiR100 (100 kg), MiR200 (200 kg), MiR250 (250 kg), MiR500 (500 kg) and MiR1000 (1,000 kg) cover full payload range; industry-standard REST API; proven in high-temperature environments (automotive foundries); MiR Fleet management system for 1,000+ AMRs; strong ecosystem of third-party top modules (shelf, conveyor, lift); proven MES integration connectors  
**Cons:** Premium pricing (~$25,000–$75,000 per robot); US-headquartered with limited Africa presence

### Option 2: Geek+ (Chinese AMR vendor)
**Pros:** Lower cost (~$15,000–$35,000); growing global presence; strong in e-commerce warehouses; good fleet management software  
**Cons:** Limited proven deployment in manufacturing environments (vs. warehousing); fewer MES integration connectors; limited Africa support; less safety standard documentation

### Option 3: Fetch Robotics (acquired by Zebra Technologies)
**Pros:** Good for lighter payloads (≤ 200 kg); strong Zebra ecosystem integration  
**Cons:** Limited to lighter payloads; US-focused support; limited Africa presence; uncertain product roadmap post-acquisition

### Option 4: In-house custom AMR (prototype)
**Pros:** Full control; lower unit cost at scale  
**Cons:** 18–24 months to first deployment; safety certification is a multi-year programme; requires robotics engineering team we don't currently have; not viable for Phase 1

---

## Decision

**Selected: Option 1 — MiR Fleet (Mobile Industrial Robots)**

Reasoning:
- Full payload coverage: MiR100 for light components; MiR250 for display panels and inverter chassis; MiR500 for furniture and heavy materials
- Industry-standard REST API already available for Siemens Opcenter MES integration
- MiR Fleet dashboard scales to 1,000+ AMRs
- Proven in electronics (Samsung, Bosch, LG factories) — directly relevant to Coo-Cah use case
- High-temperature operation proven (42°C+ in Toyota stamping plant deployments)
- Procurement volume discount: 50+ AMRs qualifies for 15–20% volume discount
- Third-party top modules (hook, conveyor, lift) enable rapid customisation per factory

**Fleet Allocation:**
- Phase 1 (Year 1): 60 AMRs across 4 Electronics factories (average 12–15 per factory)
- Phase 2 (Year 2–3): Expand to all 15+ factories; target 130+ total fleet
- Phase 3 (Year 4+): AI-optimised fleet routing; lights-out integration

---

## Consequences

**Positive:**
- Single fleet management dashboard for all factories
- Standard MES integration reduces factory-by-factory integration work
- Group-level AMR telemetry feeds into AI Platform for fleet optimisation

**Negative:**
- Premium pricing; requires CapEx planning per factory
- US vendor; requires Africa logistics for spares (plan: Lagos + Kigali spare parts hubs)

**Neutral:**
- Each factory's MES AMR module must implement MiR Fleet REST API (documented in individual factory MES integration specs)

---

## Review Trigger

Review this decision if:
- MiR Fleet pricing exceeds 25% above budget across the Phase 2 rollout
- A comparable Chinese AMR vendor achieves equivalent safety certification + MES integration at 40%+ lower cost
- Any safety incident involving MiR AMRs at any Coo-Cah factory

---

*Related ADRs: [ADR-002](./ADR-002-mes-platform-selection.md) | [ADR-003](./ADR-003-digital-twin-platform.md)*
