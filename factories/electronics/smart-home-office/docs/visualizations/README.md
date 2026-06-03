# Smart Home Office — Visualizations

> **Gate 3 Artifact (Digital Twin Visual Readiness)**

This folder contains visual representations of the **Smart Home Office** factory for use in digital-twin integration, facility planning, and stakeholder communication. All diagrams are maintained as Mermaid source documents; exported SVG/PNG are generated artifacts and not committed directly.

## Asset Index

| File | Type | Description | Status |
|------|------|-------------|--------|
| [`floor-plan-diagram.md`](./floor-plan-diagram.md) | Mermaid block-diagram | Factory floor plan with zone labels and AMR routes | [PENDING / DRAFT / APPROVED] |
| [`process-flow-diagram.md`](./process-flow-diagram.md) | Mermaid flowchart | End-to-end production process flow | [PENDING / DRAFT / APPROVED] |
| [`digital-twin-renders.md`](./digital-twin-renders.md) | IFC / GLB stub registry | 3D digital-twin render file references | [PENDING / DRAFT / APPROVED] |

## Governance

- Zone IDs in all diagrams MUST match [`floor-plan.md`](../../floor-plan.md).
- Asset IDs in renders MUST match the registry in [`digital-twin.md`](../../digital-twin.md) §2.
- Anchor references MUST resolve against [`bim/asset-anchors.md`](../bim/asset-anchors.md).
- BIM render files (IFC/GLB) are stored in `assets/renders/` within the factory repository and referenced from [`digital-twin-renders.md`](./digital-twin-renders.md).
- All diagrams must render without error in MkDocs (`mkdocs build --strict`).
