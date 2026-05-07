# Digital Twin Data Model (Cross-Factory)

> **Status:** Canonical Standard (Gate 2)  
> **Owner:** Enterprise Data Architecture + AI Data Platform  
> **Version:** 1.0.0

---

## 1) Purpose and Scope

This document defines the common asset, telemetry, and event model for all factory digital twins to support interoperability, analytics, and simulation federation.

---

## 2) Common Asset Classes

| Asset Class | Code | Description |
|---|---|---|
| Machine | `MCH` | Discrete process equipment |
| Line | `LIN` | Production line/system aggregate |
| Autonomous Mobile Robot | `AMR` | Intralogistics autonomous unit |
| Cobot | `CBT` | Collaborative robot |
| Sensor | `SEN` | Instrumentation endpoint |
| Utility | `UTL` | Power, air, water, steam, compressed systems |
| Storage | `STR` | Tanks, silos, bins, warehouse zones |

---

## 3) Required Asset Attributes

All assets must expose these fields:

| Field | Type | Required | Description |
|---|---|---|---|
| `asset_id` | string | Yes | Canonical ID (`asset-id-naming-convention.md`) |
| `factory_id` | string | Yes | Origin factory code |
| `asset_class` | enum | Yes | One of canonical class codes |
| `display_name` | string | Yes | Human-readable name |
| `status` | enum | Yes | `COMMISSIONING`, `IN_SERVICE`, `OUT_OF_SERVICE`, `DECOMMISSIONED` |
| `location` | object | Yes | `{site, building, area, line_or_cell}` |
| `commissioned_at` | datetime | Yes | ISO 8601 UTC |
| `tags` | array[string] | No | Search and grouping metadata |
| `metadata` | object | No | Class-specific optional attributes |

---

## 4) Telemetry Schema

Minimum telemetry payload model:

```json
{
  "schema_version": "1.0.0",
  "asset_id": "CCG-SMT-MCH-L1-03",
  "factory_id": "CCG",
  "ts_utc": "2026-05-07T18:00:00Z",
  "metrics": [
    {
      "name": "temperature",
      "value": 87.4,
      "unit": "C",
      "quality": "GOOD"
    }
  ]
}
```

Metric rules:
- `name` must be stable, lowercase snake_case.
- `value` must be numeric for time-series metrics.
- `unit` must use approved units list in section 5.
- `quality` must be `GOOD`, `UNCERTAIN`, or `BAD`.

---

## 5) Event Schema, Units, and Time

### Event Schema

```json
{
  "schema_version": "1.0.0",
  "event_id": "uuid-v4",
  "asset_id": "CCG-SMT-MCH-L1-03",
  "factory_id": "CCG",
  "event_type": "ALARM",
  "severity": "HIGH",
  "ts_utc": "2026-05-07T18:00:00Z",
  "payload": {}
}
```

### Standard Units (minimum set)

| Dimension | Unit |
|---|---|
| Temperature | `C` |
| Pressure | `bar` |
| Flow | `m3_h` |
| Electrical power | `kW` |
| Energy | `kWh` |
| Speed | `rpm` |
| Vibration | `mm_s` |
| Position | `m` |
| Time | `s` |

### Time Rules

- All system timestamps must be UTC (`ts_utc`) in ISO 8601 with `Z`.
- Edge source timestamps may be retained as optional `ts_source` for diagnostics.

---

## 6) Validation Rules

1. Reject payloads with invalid or unknown `asset_id`.
2. Reject timestamps missing timezone or non-UTC normalized format.
3. Reject telemetry metrics with missing `name`, `value`, or `unit`.
4. Reject events missing `event_id` or `event_type`.
5. Enforce schema version support at ingestion; unsupported versions route to dead-letter channels.

---

## 7) Schema Versioning and Evolution

- `MAJOR`: incompatible structural change.
- `MINOR`: backward-compatible additive fields.
- `PATCH`: clarifications/constraints with no breaking change.
- Any MAJOR transition must provide dual-read compatibility during the deprecation window.

---

## 8) Cross-Standard Dependencies

- IDs: `asset-id-naming-convention.md`
- Topics/transport: `mqtt-topic-schema.md`
- Simulation contracts: `cross-factory-simulation-spec.md`

