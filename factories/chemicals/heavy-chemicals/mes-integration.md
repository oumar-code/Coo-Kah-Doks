# Coo-Cah Heavy Chemicals Factory — MES Integration Specification

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Heavy Chemicals Factory | **Location:** Warri Industrial Estate, Delta State, Nigeria | **Phase:** Phase 2 (Delta State Priority)
> **Document Version:** 1.0 | **Owner:** Smart Factory Core Team

---

## 1. MES Overview

The Coo-Cah Heavy Chemicals Factory deploys **Siemens Opcenter Execution Batch** (the batch/process variant of Opcenter, consistent with the Coo-Cah group standard) as its MES. Unlike the discrete assembly factories which use Opcenter Execution Discrete, chemical batch processing requires recipe management, batch record generation, and electronic batch records (eBR) for regulatory compliance.

| MES Attribute                  | Value                                                              |
|--------------------------------|--------------------------------------------------------------------|
| Platform                       | Siemens Opcenter Execution Batch (SaaS + Edge)                    |
| DCS Integration                | OPC-UA bidirectional: DCS → MES; MES recipes → DCS                |
| Electronic Batch Records (eBR) | Full eBR per batch; GMP-compliant format (21 CFR Part 11 equiv.) |
| ERP Integration                | Bidirectional REST API — production orders, material consumption  |
| LIMS Integration               | Lab results imported to MES batch record via REST API             |
| DT Integration                 | Real-time process data stream to Coo-Cah DT Engine                |
| Regulatory Reporting           | NESREA emissions; SON CoA generation; NAFDAC audit trail          |

---

## 2. MES Functional Modules

| Module                        | Function                                                                   | Status  |
|-------------------------------|----------------------------------------------------------------------------|---------|
| Recipe Management             | Master batch record (MBR) management; versioning; change control           | Phase 1 |
| Batch Execution               | Recipe-driven batch instruction delivery to DCS and operators              | Phase 1 |
| Electronic Batch Records      | Automatic eBR generation; parameter logging; deviations captured          | Phase 1 |
| Material Lot Traceability     | Raw material lot → batch → product lot → customer shipment traceability   | Phase 1 |
| OEE (Batch / Equipment)       | Equipment utilisation; batch cycle time; overall equipment effectiveness  | Phase 1 |
| Quality / SPC                 | In-process sampling; SPC charts; auto-hold on specification deviation     | Phase 1 |
| LIMS Integration              | Lab results pulled into eBR; CoA auto-generated from batch test results   | Phase 1 |
| DCS Integration               | OPC-UA server/client; MES-to-DCS setpoint pass (Phase 2 AI)               | Phase 1 |
| Environmental Reporting       | Auto-generate NESREA periodic reports from DCS + MES data                 | Phase 1 |
| Energy Sub-Metering           | Per-zone and per-process energy consumption tracking                       | Phase 1 |
| Predictive Maintenance (AI)   | AI Platform integration for rotating equipment PdM (Phase 2)              | Phase 2 |
| AI Process Optimisation       | AI-recommended DCS setpoints pushed via MES (Phase 3)                     | Phase 3 |

---

## 3. Electronic Batch Record (eBR) — Key Data Points

Each chemical batch produces an eBR containing:

| eBR Section               | Data Captured                                                      |
|---------------------------|--------------------------------------------------------------------|
| Batch Header              | Batch ID; product code; recipe version; scheduled + actual start/end |
| Raw Material Allocation   | Each RM lot code; quantity allocated; QC status; operator confirm  |
| Process Execution         | Each process step; DCS readings (temp, pressure, flow, level)      |
| In-Process QC             | Sampling time; lab result; pass/fail; deviations recorded          |
| Yield                     | Theoretical vs. actual yield; material loss reconciliation         |
| Operator Signatures       | Electronic sign-off per step; supervisor review + release          |
| Product Release           | QA Manager release signature; Certificate of Analysis reference    |
| Deviations + Investigations| Any out-of-spec event; investigation reference number             |

---

## 4. DCS Integration Architecture

```
MES (Siemens Opcenter Batch)
    │ OPC-UA Client
    ▼
DCS OPC-UA Server (Honeywell Experion / Siemens PCS 7)
    │ All process tags (temperature, pressure, flow, level)
    │ Recipe download: MES → DCS (Phase 2 AI setpoint pass)
    ▼
Field Instruments (Endress+Hauser / Yokogawa)
```

---

## 5. LIMS Integration

| LIMS Function              | MES Integration Point                                   |
|----------------------------|---------------------------------------------------------|
| Sample request trigger     | MES sends sample request to LIMS at defined process milestones |
| Result return              | LIMS returns pass/fail + values to MES via REST API     |
| CoA generation             | MES LIMS module auto-populates CoA template; QA Manager releases |
| SON compliance             | CoA format aligned with SON product registration requirements |

---

## 6. Key OEE and Performance Metrics

| Metric                         | Phase 1 Target | Phase 2 Target | Phase 3 Target |
|--------------------------------|----------------|----------------|----------------|
| Equipment Utilisation (batch)  | ≥ 75%          | ≥ 83%          | ≥ 88%          |
| Batch Cycle Time vs. Target    | ≤ +5%          | ≤ +2%          | ≤ +1%          |
| First-Pass Batch Quality Rate  | ≥ 90%          | ≥ 95%          | ≥ 98%          |
| eBR Completeness               | 100%           | 100%           | 100%           |
| Unplanned Process Downtime     | < 8%           | < 5%           | < 3%           |

---

*Refer to [`digital-twin.md`](./digital-twin.md) for DT integration.*
*Refer to [`regulatory.md`](./regulatory.md) for NESREA and SON reporting.*
