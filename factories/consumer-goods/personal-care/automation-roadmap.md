# Coo-Cah Personal Care Factory — Automation Roadmap

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Personal Care Factory | **Location:** Agbara Industrial Estate, Lagos State, Nigeria | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Coo-Cah Technology & Operations Division

---

## 1. Automation Strategy

| Phase | Period    | Theme                                       | Investment (₦B) | OEE Target |
|-------|-----------|---------------------------------------------|-----------------|------------|
| 1     | 2025–2027 | Foundation: MES, AMR fleet, CIP automation  | 0.6–1.2B        | 72–76%     |
| 2     | 2027–2029 | Robotics: palletising, AI vision QC         | 0.8–1.5B        | 80–85%     |
| 3     | 2029–2031 | Autonomy: lights-out packaging; AI scheduling | 0.5–1.0B      | 86–91%     |

---

## 2. Phase 1 — Foundation (2025–2027)

### 2.1 Phase 1 Milestones

| # | Milestone                                            | Target Date | KPI                          | Status  |
|---|------------------------------------------------------|-------------|------------------------------|---------|
| 1 | Factory civil works + GMP zones certified            | Q2 2025     | NAFDAC/SON GMP inspection    | Planned |
| 2 | Production lines commissioned + qualified            | Q3 2025     | Line OEE target              | Planned |
| 3 | MES deployed (all production zones)                  | Q4 2025     | ≥ 90% MES coverage          | Planned |
| 4 | AMR fleet commissioned                               | Q4 2025     | ≥ 95% AMR success rate      | Planned |
| 5 | CIP automation fully validated                       | Q1 2026     | CIP cycle time vs. target    | Planned |
| 6 | Solar + BESS commissioned                            | Q2 2026     | Solar self-sufficiency ≥ 72% | Planned |
| 7 | NAFDAC + SON product registration complete           | Q2 2026     | All Phase 1 SKUs registered  | Planned |
| 8 | Phase 1 OEE target achieved                          | Q4 2026     | Blended OEE ≥ 72%            | Planned |

### 2.2 Phase 1 Technology Stack

- **MES:** Siemens Opcenter Execution Discrete (FMCG batch variant)
- **AMR:** 6–10× MiR100/200 AMRs for WIP and FGW transport
- **CIP:** Semi-automated CIP with MES validation step recording
- **Quality:** Mettler Safeline metal detector; checkweigher; inline vision
- **Traceability:** GS1 barcoding; batch serialisation; NAFDAC CoA linked to MES batch record

---

## 3. Phase 2 — Robotics & AI Vision (2027–2029)

| Technology                      | Application                                    | Expected Benefit               |
|---------------------------------|------------------------------------------------|--------------------------------|
| Robotic palletiser              | End-of-line layer palletising                  | 20% faster palletising; FPY ↑ |
| AI vision QC (fill level)       | 100% fill-level verification (vs. sample check)| Defect escape rate ↓ 80%      |
| AI vision label check           | 100% label correct/presence check             | Label error rate → 0           |
| Predictive maintenance AI       | Filling valves, sealing jaws                   | MTBF improvement ≥ 20%         |

---

## 4. Phase 3 — Lights-Out Packaging (2029–2031)

- Lights-out overnight packaging line (secondary packaging carton + shrink)
- AI-driven production scheduling aligned to solar output peak
- Automated FIFO inventory management in FGW via AMR + RFID

---

*Refer to [`mes-integration.md`](./mes-integration.md) for MES details.*
