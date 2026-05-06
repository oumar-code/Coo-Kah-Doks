# Master Repository Reference

This document establishes the formal traceability link between this factory repository and the
**Coo-Cah Technologies Holdings** master orchestrating repository.

---

## Master Repository

| Attribute | Value |
|---|---|
| **Repository** | [oumar-code/Coo-Kah-Doks](https://github.com/oumar-code/Coo-Kah-Doks) |
| **Purpose** | Single source of truth for strategy, architecture, blueprints, and group-wide standards |
| **Template Version Used** | v1.0 |
| **Factory Template Path** | `factories/_template/` |
| **Factory Blueprint Path** | `factories/chemicals/metallurgical/` |
| **Group Standards Path** | `docs/` (within master repo) |

---

## Factory Registration

| Attribute | Value |
|---|---|
| **Factory ID** | CCH-MET |
| **Factory Name** | Coo-Cah Metallurgical & Minerals Factory |
| **Repository** | `coo-cah-factory-chemicals-metallurgical` |
| **Registration** | `orchestration/factory-status-registry.md` (in Coo-Kah-Doks) |
| **Vertical** | Chemicals / Metallurgical |
| **Tier** | Tier 2 — Strategic Infrastructure |
| **Phase** | Phase 2 (Planning) |
| **Status** | PLANNED |

---

## Group-Wide Standards Applied

This repository follows all group-wide standards as defined in `docs/` within the master repo
[oumar-code/Coo-Kah-Doks](https://github.com/oumar-code/Coo-Kah-Doks). The following standards
are explicitly adopted and applied in this factory repository:

| Standard Area | Master Repo Reference | Applied In This Repo |
|---|---|---|
| ISO 9001:2015 — Quality Management | `docs/standards/iso-9001.md` | [docs/regulatory.md](./docs/regulatory.md) |
| ISO 45001:2018 — Health & Safety | `docs/standards/iso-45001.md` | [docs/regulatory.md](./docs/regulatory.md) |
| ISO 14001:2015 — Environmental | `docs/standards/iso-14001.md` | [docs/regulatory.md](./docs/regulatory.md) |
| ISO 50001:2018 — Energy | `docs/standards/iso-50001.md` | [docs/energy-profile.md](./docs/energy-profile.md) |
| Automation Phases Framework | `docs/automation/phases.md` | [docs/automation-roadmap.md](./docs/automation-roadmap.md) |
| Supply Chain Doctrine | `docs/supply-chain/doctrine.md` | [docs/supply-chain.md](./docs/supply-chain.md) |
| Energy Strategy | `docs/energy/strategy.md` | [docs/energy-profile.md](./docs/energy-profile.md) |
| MES Integration Standards | `docs/mes/integration-standards.md` | [docs/mes-integration.md](./docs/mes-integration.md) |
| AI Platform Standards | `docs/ai/platform.md` | [docs/digital-twin.md](./docs/digital-twin.md) |
| Digital Twin Architecture | `docs/digital-twin/architecture.md` | [docs/digital-twin.md](./docs/digital-twin.md) |
| Factory Blueprint Template | `factories/_template/` | All `docs/` files |
| Metallurgical Factory Blueprint | `factories/chemicals/metallurgical/` | All `docs/` files |

---

## Compliance Confirmation

This repository confirms adherence to the following group-wide requirements from the master repo:

- ✅ **Document format**: All documents use the standard markdown + Mermaid diagram format as
  defined in `factories/_template/` within Coo-Kah-Doks.
- ✅ **Naming conventions**: File names, SKU codes, zone labels, and machine designations follow
  the group-wide naming standards.
- ✅ **MES integration**: This factory adopts the group MES integration standard; all production
  data, heat records, and coil/batch tracking flow to the group MES platform.
- ✅ **Automation phases**: Phase 1, 2, and 3 definitions in this repo are consistent with the
  group-wide automation phases framework.
- ✅ **Energy strategy**: The 1,000 kWp + 1,200 kWh BESS design follows the group energy
  independence strategy. Solar self-sufficiency target (≥ 70%) is aligned with the group standard.
- ✅ **Supply chain doctrine**: Delta Steel Company partnership, Warri Port import protocol, and
  intra-group supplier priority are all per the group supply chain doctrine.
- ✅ **Regulatory framework**: NESREA EIA, Ministry of Mines, SON NIS, and DPR/NUPRC obligations
  are per the group Nigerian regulatory compliance framework.

---

## Version History

| Version | Date | Description | Author |
|---|---|---|---|
| 1.0 | 2025 | Initial factory repository creation — Phase 2 Planning | Coo-Cah Engineering Team |
| 1.1 | 2026-05 | Blueprint alignment v1.0 — corrected README.md, added docs/index.md, docs/master-repo-ref.md, fixed mkdocs.yml | Blueprint Sync |

---

## Related Repositories

| Repository | Relationship |
|---|---|
| [oumar-code/Coo-Kah-Doks](https://github.com/oumar-code/Coo-Kah-Doks) | Master orchestrating repo — strategy, blueprints, group standards |
| `coo-cah-factory-electronics-power` | Key customer — copper wire rod and drawn wire for transformer winding |
| `coo-cah-factory-chemicals-plastics` | Sister factory — Chemicals vertical; shares Chemicals group standards |
| `coo-cah-factory-consumer-goods-*` | Customers — aluminium packaging and structural components |

---

*For questions about master repo standards or template updates, open an issue in
[oumar-code/Coo-Kah-Doks](https://github.com/oumar-code/Coo-Kah-Doks).*
