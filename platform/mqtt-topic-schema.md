# MQTT Topic Schema (Cross-Factory Digital Twin)

> **Status:** Canonical Standard (Gate 2)  
> **Owner:** OT/IoT Platform Team + Digital Twin Engineering  
> **Version:** 1.0.0

---

## 1) Purpose and Scope

This standard defines the unified MQTT topic namespace and message envelope for edge-to-cloud and cross-factory DT data exchange.

---

## 2) Canonical Topic Hierarchy

All production topics must use:

```
coocah/dt/v1/{factory_id}/{domain}/{asset_id}/{message_type}
```

### Segment Definitions

| Segment | Description | Allowed Values |
|---|---|---|
| `coocah` | Tenant root | Fixed |
| `dt` | Platform domain | Fixed |
| `v1` | Topic schema version | `v1` in this release |
| `{factory_id}` | Origin factory code | Must match canonical factory ID registry |
| `{domain}` | Functional stream | `telemetry`, `event`, `state`, `command`, `simulation` |
| `{asset_id}` | Canonical asset identity | Must match `asset-id-naming-convention.md` |
| `{message_type}` | Message subtype | Domain-specific token (e.g., `snapshot`, `alarm`, `heartbeat`) |

### Example Topics

- `coocah/dt/v1/CCG/telemetry/CCG-SMT-MCH-L1-03/snapshot`
- `coocah/dt/v1/CCH/event/CCH-EXT-LIN-A1-01/alarm`
- `coocah/dt/v1/CCW/state/CCW-BEV-AMR-WH-05/heartbeat`
- `coocah/dt/v1/CCG/simulation/CCG-SMT-LIN-L1-01/scenario-input`

---

## 3) Topic Classes

| Class | Producer | Consumer |
|---|---|---|
| `telemetry` | Edge connectors / sensors | DT engine, AI ingestion |
| `event` | MES/DT adapters, edge rules | Alerting, historian, AI |
| `state` | DT engine | Dashboards, APIs |
| `command` | Authorized orchestration services | Edge gateway / adapter |
| `simulation` | DT simulation services | Cross-factory simulation participants |

---

## 4) QoS and Retain Policy

| Domain | QoS | Retain | Notes |
|---|---|---|---|
| telemetry | 1 | false | At-least-once delivery for time-series |
| event | 1 | false | Prevent lost alarms/events |
| state | 1 | true | Latest state snapshot retained |
| command | 2 | false | Exactly-once for control intent |
| simulation | 1 | false | Deterministic replay handled at application layer |

---

## 5) Payload Envelope (Normative)

Every message payload must include:

```json
{
  "schema_version": "1.0.0",
  "factory_id": "CCG",
  "asset_id": "CCG-SMT-MCH-L1-03",
  "event_id": "uuid-v4",
  "ts_utc": "2026-05-07T18:00:00Z",
  "message_type": "snapshot",
  "payload": {}
}
```

### Envelope Rules

- `ts_utc` must be ISO 8601 UTC with `Z`.
- `event_id` must be unique for idempotency and replay protection.
- `schema_version` is payload schema version, independent of topic hierarchy version.

---

## 6) Backward Compatibility and Versioning Policy

1. Additive fields in `payload` are allowed in MINOR/PATCH updates.
2. Removing or renaming required fields requires MAJOR version bump.
3. Topic hierarchy MAJOR changes require new version segment (`v2`) and dual-publish migration window.
4. Minimum deprecation window: 6 months or 2 release cycles.

---

## 7) Error and Dead-Letter Topics

- Validation failures:
  - `coocah/dt/v1/{factory_id}/error/{asset_id}/validation`
- Processing failures after retries:
  - `coocah/dt/v1/{factory_id}/dead-letter/{asset_id}/{message_type}`

Dead-letter payload must include:
- Original topic
- Original payload
- Failure reason
- Retry count
- First failure timestamp

---

## 8) Security and Access Control

- TLS 1.3 required for broker links.
- Client certificate or JWT-based broker auth required.
- ACLs must be scoped by `factory_id`; cross-factory publish is denied unless explicitly approved for simulation channels.

