# Kitchen Electronics — Sensor Map

> **Gate 3 Artifact (Digital Twin Spatial Readiness)**
> **Document Version:** 1.1 | **Owner:** Digital Manufacturing / Sensors Team
> **Integration Reviewer:** DT Integration Lead
> **Control Total:** Pre-declared sensor data points from `digital-twin.md` §3 asset sensor counts. Full population target: 2026-Q2 (post-commissioning).

This standalone sensor map is the canonical source of truth for physical sensor placement and calibration governance for the **Kitchen Electronics** factory. All entries must be consistent with the asset registry in [`digital-twin.md`](../digital-twin.md) §3 and the anchor coordinates in [`bim/asset-anchors.md`](./bim/asset-anchors.md).

---

## 1. Sensor Registry

Rows marked `[PENDING COMMISSIONING]` are pre-declared entries awaiting population from MES sensor inventory data-load and physical commissioning (target: 2026-Q2).

| Sensor ID | Sensor Model | Sensor Type | Location (Zone) | Mounted On (Asset ID) | Anchor Ref | Protocol | Calibration Interval | Last Calibration | Data Owner | Notes |
|-----------|--------------|-------------|------------------|-----------------------|------------|----------|----------------------|------------------|------------|-------|
| SEN-SMT-PE001-PASTE-001 | DEK Horizon | Paste Print State | Z2 | DT-KIT-PE-001 | A-KIT-PE-001 | OPC-UA | 6 months | [PENDING COMMISSIONING] | SMT Engineering | Paste offset, squeegee pressure |
| SEN-SMT-PE002-PNP-001 | JUKI RX-7R #1 | Kinematic + Feeder State | Z2 | DT-KIT-PE-002 | A-KIT-PE-002 | OPC-UA | 6 months | [PENDING COMMISSIONING] | SMT Engineering | Feeder count, placement accuracy |
| SEN-SMT-PE003-PNP-001 | JUKI RX-7R #2 | Kinematic + Feeder State | Z2 | DT-KIT-PE-003 | A-KIT-PE-003 | OPC-UA | 6 months | [PENDING COMMISSIONING] | SMT Engineering | Feeder count, placement accuracy |
| SEN-SMT-PE004-REFLOW-TEMP-001 | Heller 1964 MK5 | Zone Temperature ×8 | Z2 | DT-KIT-PE-004 | A-KIT-PE-004 | OPC-UA | 3 months | [PENDING COMMISSIONING] | SMT Engineering | Zones 1–8 temp; belt speed |
| SEN-SMT-PE005-AOI-001 | Koh Young KY8030-3 | Vision + State | Z2 | DT-KIT-PE-005 | A-KIT-PE-005 | OPC-UA + REST | 6 months | [PENDING COMMISSIONING] | SMT Engineering | FPY per board type |
| SEN-RF-RF001-FOAM-001 | [Pending — foam injection OEM sensors] | Thermal + Kinematic ×24 | Z4 | DT-KIT-RF-001 | A-KIT-RF-001 | OPC-UA + MQTT | 3 months | [PENDING COMMISSIONING] | Production Engineering | Foam temp, carousel speed, mould pressure |
| SEN-GAS-RF002-CHG-001 | [Pending — gas ctrl OEM] | Pressure + Gas Concentration ×18 | Z5 | DT-KIT-RF-002 | A-KIT-RF-002 | OPC-UA | 6 months | [PENDING COMMISSIONING] | EHS Officer | Charge weight, cylinder pressure, lot code |
| SEN-GAS-RF003-CHG-001 | [Pending — gas ctrl OEM] | Pressure + Gas Concentration ×18 | Z5 | DT-KIT-RF-003 | A-KIT-RF-003 | OPC-UA | 6 months | [PENDING COMMISSIONING] | EHS Officer | Station #2; charge + leak test |
| SEN-GAS-RF004-VAC-001 | [Pending — vacuum station OEM] | Pressure State ×10 | Z5 | DT-KIT-RF-004 | A-KIT-RF-004 | MQTT | 3 months | [PENDING COMMISSIONING] | EHS Officer | Pressure decay; leak test pass/fail |
| SEN-FQC-RF005-COMP-001 | [Pending — compressor test OEM] | Thermal + Vibration ×20 | Z14 | DT-KIT-RF-005 | A-KIT-RF-005 | OPC-UA | 6 months | [PENDING COMMISSIONING] | Quality Engineering | Power (W), cooling (BTU/h), noise (dBa) |
| SEN-FAB-RF006-ROLL-001 | [Pending — roll-form OEM] | Kinematic + State ×14 | Z3 | DT-KIT-RF-006 | A-KIT-RF-006 | MQTT IoT GW | 6 months | [PENDING COMMISSIONING] | Production Engineering | Cabinet serial stamp, press cycles |
| SEN-GAS-GAS001-DET-001 | [Pending — electrochemical gas detector OEM] | R600a Concentration ×12 | Z5 | DT-KIT-GAS-001 | A-KIT-GAS-001 | Gas Ctrl Panel | 6 months | [PENDING COMMISSIONING] | EHS Officer | NESREA: calibrate 6-monthly; alarm at 10% LEL |
| SEN-GAS-GAS002-CYL-001 | [Pending — MQTT cylinder sensor] | Cylinder Inventory + Safety | Z5 | DT-KIT-GAS-002 | A-KIT-GAS-002 | MQTT | 12 months | [PENDING COMMISSIONING] | EHS Officer | Cylinder weight, lot code tracking |
| SEN-GAS-GAS003-VENT-001 | [Pending — BACnet ventilation sensor] | Airflow State | Z5 | DT-KIT-GAS-003 | A-KIT-GAS-003 | BMS BACnet | 12 months | [PENDING COMMISSIONING] | EHS Officer | 15 ACH minimum; alarm on low flow |
| SEN-EN-EN001-PV-001 | [Pending — EMS inverter OEM] | Power Curve / kW | Factory Roof | DT-KIT-EN-001 | A-KIT-EN-001 | EMS MQTT | 12 months | [PENDING COMMISSIONING] | Energy Team | 700 kWp solar array |
| SEN-EN-EN002-BESS-001 | [Pending — BMS integrated] | Electrochemical (SoC, SoH, Temp) | Battery Yard | DT-KIT-EN-002 | A-KIT-EN-002 | BMS MQTT | 6 months | [PENDING COMMISSIONING] | Energy Team | 800 kWh LFP; cell voltage + temp |
| SEN-EN-EN003-PCS-001 | [Pending — Modbus PCS] | State Machine | Energy Room | DT-KIT-EN-003 | A-KIT-EN-003 | EMS Modbus TCP | 12 months | [PENDING COMMISSIONING] | Energy Team | Hybrid inverter/PCS |
| SEN-EN-EN004-GRID-001 | [Pending — smart meter] | State + Load (kW) | HV Substation | DT-KIT-EN-004 | A-KIT-EN-004 | Smart Meter | 12 months | [PENDING COMMISSIONING] | Energy Team | Grid import; ToU period flag |
| SEN-EN-EN005-GEN-001 | [Pending — Generator SCADA] | State Machine | Generator Bay | DT-KIT-EN-005 | A-KIT-EN-005 | Generator SCADA | 12 months | [PENDING COMMISSIONING] | Energy Team | Perkins 500 kVA run-hours |
| SEN-EN-EN006-FOAM-001 | [Pending — power analyser] | Demand Spike (kW) | Z4 | DT-KIT-EN-006 | A-KIT-EN-006 | Power Analyser | 12 months | [PENDING COMMISSIONING] | Energy Team | Foam injection 5-sec demand monitor |
| SEN-AMR-AMR001-POS-001 | MiR Fleet Manager (API) | Position / Mission State | Main Floor | DT-KIT-AMR-001 | A-KIT-AMR-001 | AMR REST API | N/A | N/A | OT Engineering | AMR-01; x, y, θ, SoC, mission |
| SEN-AMR-AMR002-POS-001 | MiR Fleet Manager (API) | Position / Mission State | Main Floor | DT-KIT-AMR-002 | A-KIT-AMR-002 | AMR REST API | N/A | N/A | OT Engineering | AMR-02; x, y, θ, SoC, mission |
| SEN-AMR-AMR003-POS-001 | MiR Fleet Manager (API) | Position / Mission State | Main Floor | DT-KIT-AMR-003 | A-KIT-AMR-003 | AMR REST API | N/A | N/A | OT Engineering | AMR-03; SDA kitting routes |
| SEN-AMR-AMR004-POS-001 | MiR Fleet Manager (API) | Position / Mission State | Main Floor | DT-KIT-AMR-004 | A-KIT-AMR-004 | AMR REST API | N/A | N/A | OT Engineering | AMR-04; SDA-C + IPQC |
| SEN-AMR-AMR005-POS-001 | MiR Fleet Manager (API) | Position / Mission State | Main Floor | DT-KIT-AMR-005 | A-KIT-AMR-005 | AMR REST API | N/A | N/A | OT Engineering | AMR-05; IPQC→FQC→PKG |
| SEN-AMR-AMR006-POS-001 | MiR Fleet Manager (API) | Position / Mission State | Main Floor | DT-KIT-AMR-006 | A-KIT-AMR-006 | AMR REST API | N/A | N/A | OT Engineering | AMR-06; PKG→FGW |
| SEN-AMR-AMR007-POS-001 | MiR Fleet Manager (API) | Position / Mission State | Z2 | DT-KIT-AMR-007 | A-KIT-AMR-007 | AMR REST API | N/A | N/A | OT Engineering | AMR-07 (MiR100); SMT kitting |
| SEN-AMR-AMR008-POS-001 | MiR Fleet Manager (API) | Position / Mission State | Main Floor | DT-KIT-AMR-008 | A-KIT-AMR-008 | AMR REST API | N/A | N/A | OT Engineering | AMR-08 (MiR100); consumable replenish |
| [PENDING COMMISSIONING] | [PENDING COMMISSIONING] | [PENDING COMMISSIONING] | [PENDING COMMISSIONING] | [PENDING COMMISSIONING] | [PENDING COMMISSIONING] | [PENDING COMMISSIONING] | [PENDING COMMISSIONING] | [PENDING COMMISSIONING] | [PENDING COMMISSIONING] | Remaining sensor-level entries to be loaded from MES sensor inventory after commissioning — target 2026-Q2 |

---

## 2. Naming and Mapping Rules

- `Location (Zone)` values MUST match zone IDs defined in [`floor-plan.md`](../floor-plan.md).
- `Mounted On (Asset ID)` values MUST match asset IDs in [`digital-twin.md`](../digital-twin.md) §3.
- `Anchor Ref` values MUST match `BIM Anchor ID` entries in [`bim/asset-anchors.md`](./bim/asset-anchors.md).
- `Sensor ID` format: `SEN-<ZONE_PREFIX>-<ASSET_PREFIX>-<TYPE_ABBREV>-<SEQ>` (zero-padded 3 digits).
- `Calibration Interval` is mandatory for all measurement sensors; enter `N/A` only for positional/status sensors with no calibration requirement (e.g., AMR position via fleet API).
- **Gas safety sensors (DT-KIT-GAS-*)**: NESREA requires calibration every 6 months. Do not extend this interval without EHS Officer approval.

---

## 3. Integration Reviewer Responsibilities

The **DT Integration Lead** is responsible for:

1. Reviewing all new entries before merge to confirm Asset ID and Anchor Ref cross-document consistency.
2. Signing off the control total at full population.
3. Approving any sensor retirement or re-categorisation that affects anchor mapping.
4. Confirming calibration interval compliance during Gate 4 readiness review.
5. **Gas safety sensor entries** additionally require EHS Officer co-sign-off.

---

## 4. Documentation QA Checklist

| Check | Description | Status |
|-------|-------------|--------|
| QA-01 | All sensor rows are fully populated (no `[PENDING COMMISSIONING]` data rows remaining) | ⏳ Open — target 2026-Q2 |
| QA-02 | Every `Mounted On (Asset ID)` exists in `digital-twin.md` §3 asset registry | ⏳ Open — blocked on full population |
| QA-03 | Every `Anchor Ref` exists in `bim/asset-anchors.md` register | ⏳ Open — blocked on full population |
| QA-04 | Every `Location (Zone)` matches a zone ID in `floor-plan.md` | ⏳ Open — blocked on full population |
| QA-05 | Calibration intervals set for all measurement sensors | ⏳ Open — blocked on full population |
| QA-06 | Gas safety sensors (DT-KIT-GAS-*) have EHS Officer co-sign-off | ⏳ Open — pending commissioning |
| QA-07 | Integration Reviewer sign-off on control total | ⏳ Open — pending QA-01 completion |
| QA-08 | `mkdocs build --strict` passes with no broken links | ✅ Closed |

---

## Related Documents

| Document | Purpose |
|----------|---------|
| [`digital-twin.md`](../digital-twin.md) | Asset registry (§3) and sensor coverage map overview (§4) |
| [`bim/asset-anchors.md`](./bim/asset-anchors.md) | BIM anchor coordinates referenced by `Anchor Ref` column |
| [`floor-plan.md`](../floor-plan.md) | Zone IDs and spatial layout |
| [`gap-closure-report.md`](./gap-closure-report.md) | Gap closure status for sensor registry completeness |

