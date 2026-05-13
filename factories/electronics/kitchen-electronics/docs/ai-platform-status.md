# Kitchen Electronics — AI Platform Deployment Status

> **Gate 3 Artifact (AI Platform Readiness)**
> **Factory:** Coo-Cah Kitchen Electronics Factory | **Location:** Agbara Industrial Estate, Lagos / Sagamu, Ogun State
> **Document Version:** 1.0 | **Owner:** AI Platform / Digital Manufacturing Team
> **Status:** Mock/Stub Endpoints Active — Production endpoints pending Phase 1 go-live

---

## 1. Deployment Overview

The Coo-Cah AI Platform hosts all AI inference services consumed by the Kitchen Electronics Factory MES. At Gate 3, stub/mock endpoints are deployed and reachable, allowing full integration testing without live production data.

| Parameter                  | Value                                                              |
|----------------------------|--------------------------------------------------------------------|
| Platform Host              | `ai-platform.coo-cah.internal` (on-site edge) / Lagos DC fallback |
| API Base URL (stub)        | `https://ai-stub.coo-cah.internal/api/v1`                        |
| Authentication             | OAuth 2.0 client credentials (service account per factory)        |
| Transport Security         | TLS 1.3; certificate authority: Coo-Cah Internal CA              |
| Stub Deployment Date       | 2025-Q3 (Gate 3 readiness window)                                 |
| Production Go-Live Target  | Phase 1 factory commissioning (2026-Q1)                           |

---

## 2. Endpoint Status Register

| Endpoint                                    | Method | Description                                                     | Stub Status   | Prod Status    |
|---------------------------------------------|--------|-----------------------------------------------------------------|---------------|----------------|
| `/api/v1/ai/smt-defect-predict`             | POST   | SMT solder paste defect risk prediction                          | ✅ Active      | ⏳ Pending P1  |
| `/api/v1/ai/foam-injection-process`         | POST   | PU foam injection parameter optimisation prediction              | ✅ Active      | ⏳ Pending P1  |
| `/api/v1/mes/oee/realtime`                  | GET    | Real-time OEE summary by production line                         | ✅ Active      | ⏳ Pending P1  |
| `/api/v1/amr/dispatch`                      | POST   | AMR fleet mission dispatch                                       | ✅ Active      | ⏳ Pending P1  |
| `/api/v1/ai/r600a-leak-detection`           | POST   | R600a gas leak anomaly detection from sensor readings (Phase 2) | ✅ Active      | ⏳ Pending P2  |
| `/api/v1/ai/predictive-maintenance`         | POST   | Vibration/temperature maintenance alert                          | ✅ Active      | ⏳ Pending P2  |
| `/api/v1/ai/scheduling`                     | POST   | Dynamic order sequencing recommendation                          | ✅ Active      | ⏳ Pending P2  |
| `/api/v1/dt/machine-state`                  | GET    | Digital twin machine state streaming feed                        | ✅ Active      | ⏳ Pending P1  |
| `/api/v1/dt/simulation/run`                 | POST   | Trigger DES simulation run                                       | ✅ Active      | ⏳ Pending P1  |
| `/api/v1/ai/compressor-test-predict`        | POST   | Compressor cooling performance prediction at test rig            | ✅ Active      | ⏳ Pending P1  |

---

## 3. Stub Behaviour Contract

All stub endpoints conform to the API contracts documented in [`mes-integration.md`](../mes-integration.md) §6. Stub responses:

- Return well-formed JSON matching the production response schema.
- Use deterministic mock values (fixed seed) to enable repeatable integration tests.
- Include `"stub": true` in all response bodies as a discriminator flag.
- Return HTTP 200 for valid requests; HTTP 422 for schema-invalid payloads; HTTP 503 when the stub health flag is toggled off for downtime testing.

---

## 4. Service Account Credentials (Non-Production)

> **Security Note:** Stub credentials are test-only and are rotated at production go-live. Do not use in production configurations.

| Service Account                 | Scope                                              | Managed By               |
|---------------------------------|----------------------------------------------------|--------------------------|
| `svc-mes-ai-stub-kitchen`       | SMT predict, foam injection, OEE, AMR              | AI Platform / IT Ops     |
| `svc-dt-feed-stub-kitchen`      | Machine state, simulation run                      | Digital Manufacturing    |
| `svc-safety-ai-stub-kitchen`    | R600a leak detection, compressor test, maintenance | Quality / Safety Engineering |

Credential rotation schedule: 90 days in stub environment; 30 days in production.

---

## 5. Integration Test Coverage

| Integration Test Suite                  | Coverage                                       | Last Run      | Result  |
|-----------------------------------------|------------------------------------------------|---------------|---------|
| MES → SMT Predict API                   | Happy path, schema validation, error handling  | 2025-Q3       | ✅ Pass  |
| MES → Foam Injection Process API        | Happy path, parameter bounds validation        | 2025-Q3       | ✅ Pass  |
| MES → OEE Real-time API                 | Multi-line summary, per-line drill-down        | 2025-Q3       | ✅ Pass  |
| MES → AMR Dispatch API                  | Mission creation, AMR assignment               | 2025-Q3       | ✅ Pass  |
| DT Feed → Machine State API             | MQTT to REST bridge, 1-second poll             | 2025-Q3       | ✅ Pass  |
| Full E2E (MES → AI → DT)                | End-to-end simulation trigger from MES event   | 2025-Q4       | ✅ Pass  |

---

## 6. Open Items Before Production Go-Live

| Item                                      | Owner                    | Target Date   | Status      |
|-------------------------------------------|--------------------------|---------------|-------------|
| On-site GPU inference node commissioning  | AI Platform Team         | 2026-Q1       | ⏳ Pending  |
| Service account credential rotation       | IT Security              | 2026-Q1       | ⏳ Pending  |
| Production TLS certificate issue          | IT Ops                   | 2026-Q1       | ⏳ Pending  |
| Load test (1,000 req/min sustained)       | AI Platform / QA         | 2025-Q4       | ⏳ Pending  |
| Penetration test of API endpoints         | IT Security / Ext. Firm  | See [`pentest-scoping.md`](./pentest-scoping.md) | ⏳ Pending |
| MES failover to local stub on cloud loss  | MES Integration Team     | 2026-Q1       | ⏳ Pending  |

---

## Related Documents

| Document | Purpose |
|----------|---------|
| [`mes-integration.md`](../mes-integration.md) | AI API endpoint specifications and security governance |
| [`pentest-scoping.md`](./pentest-scoping.md) | Penetration test scope covering AI platform API surface |
| [`digital-twin.md`](../digital-twin.md) | Digital twin architecture and simulation use cases |
| [`gap-closure-report.md`](./gap-closure-report.md) | Gap closure status including AI Platform readiness evidence |
