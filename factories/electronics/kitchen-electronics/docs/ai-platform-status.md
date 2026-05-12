# Kitchen Electronics — AI Platform Deployment Status

> **Gate 3 Artifact (AI Platform Readiness)**
> **Factory:** Coo-Cah Kitchen Electronics Factory | **Location:** Agbara Industrial Estate, Lagos State
> **Document Version:** 1.0 | **Owner:** AI Platform / Digital Manufacturing Team
> **Status:** Mock/Stub Endpoints Active — Production endpoints pending Phase 1 go-live

---

## 1. Deployment Overview

The Coo-Cah AI Platform hosts all AI inference services consumed by the Kitchen Electronics Factory MES. At Gate 3, stub/mock endpoints are deployed and reachable, allowing full integration testing without live production data. The kitchen electronics deployment has a unique safety-critical module — the **Gas Safety AI** for R600a leak detection and ventilation state monitoring — which is not present in other factory deployments.

| Parameter                  | Value                                                              |
|----------------------------|--------------------------------------------------------------------|
| Platform Host              | `ai-platform.coo-cah.internal` (on-site edge) / Lagos DC fallback |
| API Base URL (stub)        | `https://ai-stub.coo-cah.internal/api/v1`                        |
| Authentication             | OAuth 2.0 client credentials (service account per factory)        |
| Transport Security         | TLS 1.3; certificate authority: Coo-Cah Internal CA              |
| Stub Deployment Date       | 2025-Q4 (Gate 3 readiness window)                                 |
| Production Go-Live Target  | Phase 1 factory commissioning (2026-Q2)                           |

---

## 2. AI Services List

| Service ID       | Service Name                     | Description                                                             | Phase     |
|------------------|----------------------------------|-------------------------------------------------------------------------|-----------|
| AI-KIT-001       | Predictive Maintenance           | Vibration + thermal fusion on SMT reflow oven, foam injection carousel, compressor test rigs | Phase 2 |
| AI-KIT-002       | Yield Prediction                 | Predicts First-Pass Yield based on reflow profile, foam density telemetry, and IPQC scores | Phase 2 |
| AI-KIT-003       | Energy Optimisation              | BESS dispatch plan; foam injection peak demand mitigation               | Phase 1   |
| AI-KIT-004       | Gas Safety AI                    | Real-time R600a leak detection alerting; ventilation state monitoring; evacuation trigger | Phase 1 |
| AI-KIT-005       | OEE Real-time Stream             | Factory-wide OEE by line; downtime event classification                 | Phase 1   |
| AI-KIT-006       | AMR Dispatch                     | AMR fleet mission dispatch and route optimisation                       | Phase 1   |
| AI-KIT-007       | Scheduling Optimiser             | Dynamic job sequencing; foam injection idle-time minimisation           | Phase 2   |
| AI-KIT-008       | AI Vision QC — Cabinet           | CNN-based dimensional and surface inspection for refrigerator cabinets  | Phase 2   |
| AI-KIT-009       | Digital Twin Sync                | Machine state streaming and DES simulation trigger                      | Phase 2   |

---

## 3. Endpoint Status Register

| Endpoint                              | Method | Service ID   | Description                                          | Stub Status   | Prod Status    |
|---------------------------------------|--------|--------------|------------------------------------------------------|---------------|----------------|
| `/api/v1/ai/gas-safety-alert`         | POST   | AI-KIT-004   | R600a concentration alert; ventilation state input   | ✅ Active      | ⏳ Pending P1  |
| `/api/v1/ai/energy-optimisation`      | POST   | AI-KIT-003   | BESS dispatch plan; demand spike schedule            | ✅ Active      | ⏳ Pending P1  |
| `/api/v1/mes/oee/realtime`            | GET    | AI-KIT-005   | Real-time OEE summary by line                        | ✅ Active      | ⏳ Pending P1  |
| `/api/v1/amr/dispatch`                | POST   | AI-KIT-006   | AMR fleet mission creation and assignment            | ✅ Active      | ⏳ Pending P1  |
| `/api/v1/ai/predictive-maintenance`   | POST   | AI-KIT-001   | Vibration/temperature failure probability alert      | ✅ Active      | ⏳ Pending P2  |
| `/api/v1/ai/yield-predict`            | POST   | AI-KIT-002   | FPY prediction from reflow + foam + IPQC telemetry   | ✅ Active      | ⏳ Pending P2  |
| `/api/v1/ai/scheduling`               | POST   | AI-KIT-007   | Dynamic order sequencing recommendation              | ✅ Active      | ⏳ Pending P2  |
| `/api/v1/ai/cabinet-vision-qc`        | POST   | AI-KIT-008   | AI vision cabinet gap, weld, surface inspection      | ✅ Active      | ⏳ Pending P2  |
| `/api/v1/dt/machine-state`            | GET    | AI-KIT-009   | Digital twin machine state streaming feed            | ✅ Active      | ⏳ Pending P2  |
| `/api/v1/dt/simulation/run`           | POST   | AI-KIT-009   | Trigger DT simulation run (foam, gas, energy)        | ✅ Active      | ⏳ Pending P2  |

---

## 4. Data Dependencies

| Endpoint                          | Required Input Data                                                    | Data Source                              |
|-----------------------------------|------------------------------------------------------------------------|------------------------------------------|
| `/api/v1/ai/gas-safety-alert`     | R600a sensor concentration (ppm), ventilation airflow state, zone ID  | Gas ctrl panel → MES → AI Platform       |
| `/api/v1/ai/energy-optimisation`  | Foam injection load profile, BESS SoC, solar generation, production schedule | EMS/BMS → DT Engine → AI Platform    |
| `/api/v1/mes/oee/realtime`        | MES downtime records, production actuals, IPQC results                | MES production event stream              |
| `/api/v1/amr/dispatch`            | Zone WIP levels, AMR position + SoC, mission queue                   | MiR Fleet Manager REST API               |
| `/api/v1/ai/predictive-maintenance`| Vibration (Hz, g-RMS), temperature (°C), run hours, carousel speed   | OPC-UA machine sensors → DT telemetry    |
| `/api/v1/ai/yield-predict`        | Reflow zone temps ×8, foam injection params, IPQC pass/fail           | MES quality stream + DT telemetry        |
| `/api/v1/ai/gas-safety-alert`     | Also: emergency shutdown (ESD) state, cylinder bay inventory          | MES Gas Module + MQTT sensor             |

---

## 5. Stub Behaviour Contract

All stub endpoints conform to the API contracts documented in [`mes-integration.md`](../mes-integration.md) §5. Stub responses:

- Return well-formed JSON matching the production response schema.
- Use deterministic mock values (fixed seed) to enable repeatable integration tests.
- Include `"stub": true` in all response bodies as a discriminator flag.
- Return HTTP 200 for valid requests; HTTP 422 for schema-invalid payloads; HTTP 503 when the stub health flag is toggled off for downtime testing.

---

## 6. Service Account Credentials (Non-Production)

> **Security Note:** Stub credentials are test-only and are rotated at production go-live. Do not use in production configurations.

| Service Account            | Scope                                          | Managed By               |
|----------------------------|------------------------------------------------|--------------------------|
| `svc-mes-ai-kit-stub`      | Gas safety, energy optimisation, OEE, AMR     | AI Platform / IT Ops     |
| `svc-dt-feed-kit-stub`     | Machine state, simulation run                 | Digital Manufacturing    |
| `svc-safety-gas-stub`      | Gas safety AI, ESD integration                | EHS / OT Engineering     |

Credential rotation schedule: 90 days in stub environment; 30 days in production.

---

## 7. Environment Readiness Checklist

| Item | Description | Status |
|------|-------------|--------|
| ENV-01 | On-site edge compute node provisioned (GPU inference for AI-KIT-001/002/008) | ⏳ Pending Phase 2 |
| ENV-02 | Gas safety AI module connected to R600a gas controller panel OPC-UA | ⏳ Pending commissioning |
| ENV-03 | EMS/BMS → AI Platform MQTT bridge tested with real sensor data | ⏳ Pending commissioning |
| ENV-04 | AI stub endpoints reachable from factory LAN | ✅ Ready |
| ENV-05 | TLS 1.3 certificate chain valid (stub CA) | ✅ Ready |
| ENV-06 | Service accounts provisioned in IAM | ✅ Ready |
| ENV-07 | Production TLS certificate from Coo-Cah Internal CA issued | ⏳ Pending Phase 1 go-live |
| ENV-08 | Load test (500 req/min sustained, 1,000 req/min burst) | ⏳ Pending Phase 1 UAT |
| ENV-09 | Gas Safety AI model trained on commissioning data | ⏳ Pending commissioning |
| ENV-10 | MES failover to local stub on cloud connectivity loss | ⏳ Pending Phase 1 UAT |

---

## 8. Integration Test Coverage

| Integration Test Suite                  | Coverage                                              | Last Run   | Result       |
|-----------------------------------------|-------------------------------------------------------|------------|--------------|
| MES → Gas Safety Alert API             | Happy path, threshold breach, ESD trigger             | 2025-Q4    | ✅ Pass       |
| MES → Energy Optimisation API           | BESS dispatch plan, foam injection spike mitigation   | 2025-Q4    | ✅ Pass       |
| MES → OEE Real-time API                 | Multi-line summary, per-line drill-down               | 2025-Q4    | ✅ Pass       |
| MES → AMR Dispatch API                  | Mission creation, zone routing, AMR assignment        | 2025-Q4    | ✅ Pass       |
| DT Feed → Machine State API             | MQTT to REST bridge, 30-second poll                   | 2025-Q4    | ✅ Pass       |
| Full E2E (MES → Gas Safety → ESD)       | End-to-end gas alarm → ventilation check → alert      | 2025-Q4    | ✅ Pass       |

---

## 9. Open Items Before Production Go-Live

| Item                                         | Owner                     | Target Date   | Status      |
|----------------------------------------------|---------------------------|---------------|-------------|
| On-site GPU inference node commissioning     | AI Platform Team          | 2026-Q2       | ⏳ Pending  |
| Gas Safety AI model training (commissioning data) | EHS / AI Platform    | 2026-Q2       | ⏳ Pending  |
| Service account credential rotation          | IT Security               | 2026-Q2       | ⏳ Pending  |
| Production TLS certificate issue             | IT Ops                    | 2026-Q2       | ⏳ Pending  |
| Load test (500 req/min sustained)            | AI Platform / QA          | 2026-Q1       | ⏳ Pending  |
| Penetration test of API endpoints            | IT Security / Ext. Firm   | See [`pentest-scoping.md`](./pentest-scoping.md) | ⏳ Pending |
| MES failover to local stub on cloud loss     | MES Integration Team      | 2026-Q2       | ⏳ Pending  |
| NESREA gas module reporting integration test | EHS Officer               | 2026-Q2       | ⏳ Pending  |

---

## Related Documents

| Document | Purpose |
|----------|---------|
| [`mes-integration.md`](../mes-integration.md) | MES API endpoint specifications (§5) and R600a gas module (§4) |
| [`pentest-scoping.md`](./pentest-scoping.md) | Penetration test scope covering AI platform API surface |
| [`digital-twin.md`](../digital-twin.md) | Digital twin architecture, asset registry, and simulation use cases |
| [`gap-closure-report.md`](./gap-closure-report.md) | Gap closure status including AI Platform readiness evidence |
