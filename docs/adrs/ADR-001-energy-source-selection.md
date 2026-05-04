# ADR-001: Energy Source Selection for Coo-Cah Factories

**Status:** ACCEPTED  
**Date:** 2025-01-15  
**Deciders:** Group CTO, Group COO, Group CFO, Rwanda Energy Lead  
**Technical Story:** [Issue #12 — Energy Strategy Baseline](https://github.com/oumar-code/Coo-Kah-Doks/issues/12)

---

## Context

All Coo-Cah factories require a reliable, cost-effective, and sustainable energy supply. The decision on primary energy source is foundational — it determines infrastructure investment, operating cost structure, carbon footprint, and resilience to grid outages.

African manufacturing has historically struggled with grid reliability. Nigeria's grid availability for industrial users averages 8–12 hours per day in many locations. Kenya and Rwanda are more stable but still experience outages. Without a firm answer to "where does the factory's power come from?", no investment case can be made.

This ADR establishes the group-wide energy source strategy that all factories must follow.

### Constraints
- **Grid reliability:** Nigerian grid availability is < 60% in most industrial zones
- **Cost:** Grid electricity in Nigeria costs $0.10–0.18/kWh (when available); diesel generation costs $0.35–0.45/kWh — both are high compared to solar LCOE of $0.04–0.07/kWh
- **Carbon:** DFI investors (IFC, Proparco) require demonstrable ESG commitments including carbon reduction plans
- **Capital:** Energy systems must be sized to fit within the overall factory CapEx envelope
- **Operations:** Energy systems must be maintainable with locally available skills
- **Scalability:** Solution must work for factories ranging from 500kWp to 10MWp total load

---

## Decision Drivers

- Minimise energy cost as a percentage of CoGS to remain globally competitive
- Guarantee minimum production continuity regardless of grid state
- Meet DFI environmental covenants (IFC Performance Standard 3)
- Achieve carbon neutrality by Phase 3 (Year 6–10)
- Use technologies that can be maintained by locally trained teams
- Enable energy cost to decrease over time (technology roadmap alignment)

---

## Options Considered

### Option 1: Grid-Only with Diesel Backup
**Description:** Connect to national grid as primary; diesel generators as backup. No renewable generation.

**Pros:**
- Lowest upfront CapEx (~$0.5M per factory)
- Simplest system to operate
- No dependency on solar resource assessment

**Cons:**
- Energy cost $0.15–0.35/kWh (grid + diesel blend) — very high CoGS impact
- Diesel is a recurring OpEx that inflates with fuel price and FX movements
- Zero renewable credentials; fails DFI ESG requirements
- Complete dependency on Nigerian grid — significant production risk
- Diesel generators are major maintenance burden and pollution source

**Cost estimate:** $0.5M CapEx; ~$0.30/kWh blended OpEx  
**Verdict:** ❌ Rejected — economically and strategically unviable

---

### Option 2: Solar PV + Battery Energy Storage System (BESS) + Grid Backup
**Description:** Solar PV as primary generation. LFP battery storage for night operation and grid outage coverage. Grid connection maintained for top-up and emergencies. Diesel generator retained for extreme emergencies only.

**Pros:**
- Solar LCOE of $0.04–0.07/kWh is the lowest-cost electricity source in West/East Africa
- BESS provides 8–16h production continuity without grid
- Meets DFI ESG requirements — 40–65% renewable from day 1
- Technology is proven, bankable, and maintainable with trained local technicians
- Predictable OpEx — solar and BESS costs do not fluctuate with fuel prices
- Group bulk procurement of solar panels and BESS drives further cost reductions

**Cons:**
- Higher upfront CapEx ($2–5M per factory depending on size)
- Solar performance varies by weather; BESS degradation over time (~80% capacity at Year 10)
- Roof/land area required for solar arrays (potential constraint for some sites)
- BESS requires periodic cell replacement (Year 8–12 for LFP)

**Cost estimate:** $2.5–5M CapEx per factory; ~$0.09–0.13/kWh blended OpEx  
**Verdict:** ✅ Selected as primary architecture

---

### Option 3: Solar + Wind + BESS Hybrid
**Description:** As Option 2, but with wind turbines added at sites meeting minimum wind criteria (average wind speed ≥ 5.5 m/s at hub height).

**Pros:**
- Wind complements solar — generates when solar doesn't (night, cloudy days)
- Higher renewable percentage and lower grid dependency
- Reduces BESS cycling requirement → extends BESS life

**Cons:**
- Wind turbines require site-specific assessment (wind resource, land, permits)
- Turbine maintenance requires specialised skills
- Not all factory sites will have adequate wind resource

**Cost estimate:** Adds $1–8M CapEx vs. Option 2 (depending on wind array size)  
**Verdict:** ✅ Adopted as supplementary for eligible sites (see energy strategy doc for criteria)

---

### Option 4: Natural Gas / LNG
**Description:** Captive gas-to-power plant using natural gas or LNG as primary energy source.

**Pros:**
- Reliable baseload power
- Gas price in Nigeria is low for industrial users (where pipeline gas available)

**Cons:**
- Gas pipeline access limited to Delta State, Rivers State — not available in Lagos, Ogun, Abuja
- LNG logistics complex and costly
- Carbon intensity 400–500 kgCO₂/MWh — incompatible with carbon targets
- Fails DFI green financing requirements
- Long lead time and high regulatory burden

**Cost estimate:** $8–20M per factory  
**Verdict:** ❌ Rejected as primary source; may be considered as supplementary for Delta State heavy chemicals site only

---

## Decision

**Selected: Option 2 (Solar PV + BESS + Grid Backup) as the mandatory baseline for all Coo-Cah factories, with Option 3 hybrid wind deployment at eligible sites.**

All Coo-Cah factories must:
1. Install solar PV as primary energy source, sized to cover ≥ 120% of peak daily demand (kWh) per peak sun hours
2. Install LFP BESS sized for ≥ 8 hours of base load autonomy (≥ 16h for factories requiring overnight production)
3. Maintain grid connection as backup and for emergency import/export
4. Retire diesel generators to emergency-only role (< 15% of total demand, < 48h/month in Phase 1)
5. Deploy an Energy Management System (EMS) on day 1 of operation
6. Assess wind resource at each site; deploy wind turbines where criteria are met

This decision is mandatory. Exceptions require Holdings Board approval and must demonstrate an alternative path to the same energy KPIs.

---

## Consequences

### Positive
- Predictable, declining energy costs over factory life (solar LCOE will fall further)
- Production continuity regardless of grid state — competitive advantage in African market
- Meets all DFI ESG covenants from day 1 — unlocks lower-cost green financing
- Positions Coo-Cah as a sustainability leader in African manufacturing
- Builds a group energy asset base (solar arrays, BESS) with significant balance sheet value
- Enables energy arbitrage — sell excess solar to grid where PPAs allow

### Negative / Trade-offs
- Higher upfront CapEx of $2.5–5M per factory compared to grid-only
- Requires more complex commissioning and technical expertise for energy systems
- Solar performance is weather-dependent; extreme weather events may reduce output

### Risks

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|-----------|
| Solar panels damaged by extreme weather | Low | Medium | Insurance; robust mounting design to local wind/storm standards |
| BESS thermal runaway | Very Low | High | LFP chemistry (inherently safer); BMS with multiple thermal cutoffs; fire suppression |
| Solar inverter failure | Medium | Medium | Dual-string inverters; spare parts stock; local service contracts |
| Grid export agreement not available | Medium | Low | BESS can absorb excess; curtailment as last resort |
| Solar resource lower than forecast | Low | Medium | Use conservative P90 irradiance data for sizing |

---

## Compliance Notes

- **IFC Performance Standard 3 (Resource Efficiency & Pollution Prevention):** Solar + BESS strategy directly supports PS3 compliance on greenhouse gas emissions
- **ISO 50001:2018 (Energy Management):** EMS deployment satisfies the monitoring and management requirements
- **NERC (Nigeria):** Embedded generation licence required for installations > 1MW; procurement of licence to begin 6 months before commissioning
- **DFI Green Finance:** Strategy qualifies Coo-Cah for green/climate finance instruments from IFC, Proparco, EIB, and AfDB

---

## Review Date

This ADR should be reviewed if:
- Battery technology changes materially (e.g., solid-state batteries become commercially viable at lower cost)
- Grid reliability in Nigeria improves substantially (grid availability > 90%)
- A major new energy technology emerges that materially changes the economics

Next scheduled review: **January 2028**

---

*Approved by: Group CTO | Coo-Cah Technologies Holdings*
