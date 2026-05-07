# Asset ID Naming Convention (Cross-Factory)

> **Status:** Canonical Standard (Gate 2)  
> **Owner:** Enterprise Data Architecture + Digital Twin Engineering  
> **Version:** 1.0.0

---

## 1) Purpose and Scope

This standard defines the group-wide namespace for physical and logical assets used by digital twins, MQTT telemetry, MES integrations, and cross-factory simulation exchanges.

All factories must use this convention for new assets and for migration of existing non-canonical identifiers.

---

## 2) Canonical Asset ID Format

```
[FACTORY_ID]-[AREA]-[ASSET_CLASS]-[UNIT]-[SEQUENCE]
```

### Field Definitions

| Field | Description | Rule |
|---|---|---|
| `FACTORY_ID` | Group factory code | Uppercase, 2–6 chars, registered in factory registry |
| `AREA` | Production/utility area code | Uppercase alphanumeric, 2–10 chars |
| `ASSET_CLASS` | Canonical class code | One of `MCH`, `LIN`, `AMR`, `CBT`, `SEN`, `UTL`, `STR` |
| `UNIT` | Line/cell/unit identifier | Uppercase alphanumeric, 1–8 chars |
| `SEQUENCE` | Local unique sequence | 2-digit minimum (`01`, `02`, ...), zero padded |

### Examples

- `CCG-SMT-MCH-L1-03` (Garage & Power Electronics, SMT machine, line 1, unit 03)
- `CCH-EXT-LIN-A1-01` (Plastics, extrusion line A1)
- `CCH-ROLL-SEN-RM1-12` (Metallurgical rolling area sensor)
- `CCW-BEV-AMR-WH-05` (Consumer goods AMR in warehouse zone)

---

## 3) Allowed Values and Reserved Codes

- Factory codes must be centrally maintained; local aliases are prohibited.
- `AREA` must map to a documented floor-plan zone.
- `ASSET_CLASS` codes are fixed in this version; new classes require standards review.
- Reserved sequences: `00` and `99` are reserved for test and temporary lab mapping and must not be used in production twins.

---

## 4) Uniqueness and Lifecycle Rules

1. `asset_id` must be globally unique across all factories.
2. Asset IDs are immutable once assigned.
3. Asset IDs must never be re-used, even after decommissioning.
4. Lifecycle states:
   - `COMMISSIONING`
   - `IN_SERVICE`
   - `OUT_OF_SERVICE`
   - `DECOMMISSIONED`
5. A decommissioned asset remains queryable in historical datasets for traceability and audit.

---

## 5) Assignment and Governance

- Assignment authority: Factory OT/IoT Lead under central data architecture controls.
- Registration required before telemetry publication or simulation participation.
- Validation checks in ingestion pipelines must reject IDs violating this pattern.

Regex (normative):

```
^[A-Z0-9]{2,6}-[A-Z0-9]{2,10}-(MCH|LIN|AMR|CBT|SEN|UTL|STR)-[A-Z0-9]{1,8}-[0-9]{2,}$
```

---

## 6) Cross-Standard Dependencies

- MQTT topics must embed canonical `asset_id` (`mqtt-topic-schema.md`).
- DT payload schemas must use this `asset_id` as primary key (`digital-twin-data-model.md`).
- Simulation exchanges must reference this `asset_id` as the identity anchor (`cross-factory-simulation-spec.md`).

