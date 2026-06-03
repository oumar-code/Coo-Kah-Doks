# Security Electronics — Digital Twin Renders

> **Gate 3 Artifact (Digital Twin Visual Readiness)**
> **Document Version:** 1.0 | **Owner:** BIM / Facilities Engineering | **Integration Reviewer:** DT Integration Lead

Registry of 3D model and render files for the **Security Electronics** digital twin. IFC and GLB files are generated from CAD source and stored under `assets/renders/` once the full BIM model is delivered. Asset IDs MUST match the registry in [`digital-twin.md`](../../digital-twin.md) §2.

---

## Render Status Codes

| Status Code | Meaning |
|-------------|---------|
| `PENDING` | Render not yet generated; awaiting IFC model delivery |
| `DRAFT` | Render generated but not yet validated against physical layout |
| `APPROVED` | Render validated and approved for DT spatial integration |

---

## Render Registry

| Render ID | File Path | Format | Scope | Zone(s) | BIM Source | Status | Notes |
|-----------|-----------|--------|-------|---------|------------|--------|-------|
| RND-FULL-01 | `assets/renders/factory-full.glb` | GLB | Full factory | All | IFC model | PENDING | Complete 3D factory model |
| RND-FULL-02 | `assets/renders/factory-full.ifc` | IFC | Full factory | All | CAD source | PENDING | Source IFC for DT platform import |
| RND-ZONE-01 | `assets/renders/zone-[ZONE_ID].glb` | GLB | Zone [ZONE_ID] | [ZONE_ID] | IFC model | PENDING | Zone detail view for DT navigation |

> **Note:** Add one `RND-ZONE-XX` row per production zone defined in [`floor-plan.md`](../../floor-plan.md).

---

## Acceptance Register

| Acceptance Criterion | Status | Owner | Due Date |
|----------------------|--------|-------|----------|
| Full-factory GLB generated and validated | ⏳ Pending | BIM Engineering | [DATE] |
| Full-factory IFC generated and imported to DT platform | ⏳ Pending | BIM Engineering | [DATE] |
| All zone renders generated and validated | ⏳ Pending | BIM Engineering | [DATE] |
| All renders approved by DT Integration Lead | ⏳ Pending | DT Integration Lead | [DATE] |
| Asset IDs in renders verified against `digital-twin.md` §2 | ⏳ Pending | DT Integration Lead | [DATE] |

---

## Related Documents

| Document | Purpose |
|----------|---------|
| [`bim/asset-anchors.md`](../bim/asset-anchors.md) | Asset anchor coordinates for DT placement |
| [`bim/zone-boundaries.md`](../bim/zone-boundaries.md) | Zone boundary coordinate definitions |
| [`digital-twin.md`](../../digital-twin.md) | Asset registry and sensor coverage map |
| [`floor-plan-diagram.md`](./floor-plan-diagram.md) | Factory floor plan zone layout |
