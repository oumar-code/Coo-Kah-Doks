# Kitchen Electronics — Asset Anchors (BIM Stub)

> **Gate 3 Artifact (Digital Twin Spatial Readiness)**
> **Document Version:** 1.0 | **Owner:** BIM / Facilities Engineering
> **Integration Reviewer:** DT Integration Lead
> **Coordinate System:** LOCAL_GRID_M — matches [`docs/bim/zone-boundaries.md`](./zone-boundaries.md). Origin at SW internal corner of factory building; x = West→East; y = South→North; z = 0.00 m floor level.
> **Status:** All DT assets from `digital-twin.md` §3 are pre-registered. Anchor coordinates are **placeholder centre-of-zone estimates only**. Precise anchor positions (including IFC GUID) are **pending IFC architectural model delivery (target: 2026-Q2)**.

---

## Asset Anchor Register

| DT Asset ID | Asset Name | Zone ID | Anchor X (m) | Anchor Y (m) | Anchor Z (m) | Orientation (Yaw°/Pitch°/Roll°) | IFC GUID Status | Coordinate Source |
|-------------|------------|---------|--------------|--------------|--------------|----------------------------------|-----------------|-------------------|
| DT-KIT-PE-001 | DEK Horizon Paste Printer | Z2 | 55.0 | 92.0 | 0.0 | 0/0/0 | Pending IFC delivery | Zone centroid estimate; floor-plan.md Z2 |
| DT-KIT-PE-002 | JUKI RX-7R Pick-and-Place #1 | Z2 | 62.0 | 88.0 | 0.0 | 0/0/0 | Pending IFC delivery | Zone centroid estimate; floor-plan.md Z2 |
| DT-KIT-PE-003 | JUKI RX-7R Pick-and-Place #2 | Z2 | 72.0 | 88.0 | 0.0 | 0/0/0 | Pending IFC delivery | Zone centroid estimate; floor-plan.md Z2 |
| DT-KIT-PE-004 | Heller 1964 MK5 Reflow Oven | Z2 | 80.0 | 92.0 | 0.0 | 0/0/0 | Pending IFC delivery | Zone centroid estimate; floor-plan.md Z2 |
| DT-KIT-PE-005 | Koh Young AOI KY8030-3 | Z2 | 85.0 | 88.0 | 0.0 | 0/0/0 | Pending IFC delivery | Zone centroid estimate; floor-plan.md Z2 |
| DT-KIT-RF-001 | PU Foam Injection Machine (carousel) | Z4 | 55.0 | 67.0 | 0.0 | 0/0/0 | Pending IFC delivery | Zone centroid estimate; floor-plan.md Z4 |
| DT-KIT-RF-002 | R600a Gas Charging Station #1 | Z5 | 6.0 | 47.0 | 0.0 | 0/0/0 | Pending IFC delivery | ATEX Zone 2; floor-plan.md Z5 |
| DT-KIT-RF-003 | R600a Gas Charging Station #2 | Z5 | 14.0 | 47.0 | 0.0 | 0/0/0 | Pending IFC delivery | ATEX Zone 2; floor-plan.md Z5 |
| DT-KIT-RF-004 | Vacuum Station (leak test) | Z5 | 10.0 | 43.0 | 0.0 | 0/0/0 | Pending IFC delivery | ATEX Zone 2; floor-plan.md Z5 |
| DT-KIT-RF-005 | Compressor Performance Test Rig | Z14 | 31.0 | 47.0 | 0.0 | 0/0/0 | Pending IFC delivery | Zone centroid estimate; floor-plan.md Z14 |
| DT-KIT-RF-006 | Cabinet Roll-Form + Welding Line | Z3 | 107.0 | 94.0 | 0.0 | 90/0/0 | Pending IFC delivery | Zone centroid estimate; floor-plan.md Z3 |
| DT-KIT-AMR-001 | AMR-01 (MiR200) | Z1/Z4 | 25.0 | 95.0 | 0.0 | 0/0/0 | N/A — dynamic position | AMR REST API live position |
| DT-KIT-AMR-002 | AMR-02 (MiR200) | Z1/Z4 | 25.0 | 95.0 | 0.0 | 0/0/0 | N/A — dynamic position | AMR REST API live position |
| DT-KIT-AMR-003 | AMR-03 (MiR200) | Z1/Z8 | 25.0 | 95.0 | 0.0 | 0/0/0 | N/A — dynamic position | AMR REST API live position |
| DT-KIT-AMR-004 | AMR-04 (MiR200) | Z1/Z8/Z9 | 25.0 | 95.0 | 0.0 | 0/0/0 | N/A — dynamic position | AMR REST API live position |
| DT-KIT-AMR-005 | AMR-05 (MiR200) | Z9/Z10/Z11 | 25.0 | 95.0 | 0.0 | 0/0/0 | N/A — dynamic position | AMR REST API live position |
| DT-KIT-AMR-006 | AMR-06 (MiR200) | Z11/Z12 | 25.0 | 95.0 | 0.0 | 0/0/0 | N/A — dynamic position | AMR REST API live position |
| DT-KIT-AMR-007 | AMR-07 (MiR100) | Z2 | 55.0 | 95.0 | 0.0 | 0/0/0 | N/A — dynamic position | AMR REST API live position |
| DT-KIT-AMR-008 | AMR-08 (MiR100) | Main Floor | 25.0 | 50.0 | 0.0 | 0/0/0 | N/A — dynamic position | AMR REST API live position |
| DT-KIT-EN-001 | Solar PV Array — Main Roof | Factory Roof | 62.5 | 55.0 | 9.0 | 180/10/0 | Pending IFC delivery | Rooftop; precise coordinates pending IFC |
| DT-KIT-EN-002 | LFP BESS 800 kWh | Battery Yard | 110.0 | 0.0 | 0.0 | 0/0/0 | Pending IFC delivery | External battery yard; pending site survey |
| DT-KIT-EN-003 | Hybrid Inverter / PCS | Energy Room | 115.0 | 5.0 | 0.0 | 0/0/0 | Pending IFC delivery | Zone centroid estimate |
| DT-KIT-EN-004 | Grid Connection | HV Substation | 125.0 | 55.0 | 0.0 | 0/0/0 | Pending IFC delivery | External HV substation; pending site survey |
| DT-KIT-EN-005 | Perkins 500 kVA Generator | Generator Bay | 120.0 | 0.0 | 0.0 | 0/0/0 | Pending IFC delivery | External generator bay; pending site survey |
| DT-KIT-EN-006 | Foam Injection Load Monitor | Z4 | 55.0 | 67.0 | 0.0 | 0/0/0 | Pending IFC delivery | Co-located with DT-KIT-RF-001 |
| DT-KIT-GAS-001 | R600a Gas Detector Array (12 pts) | Z5 | 11.0 | 47.5 | 0.5 | 0/0/0 | Pending IFC delivery | ATEX Zone 2; z=0.50 m (below 0.5 m is Zone 2 floor level) |
| DT-KIT-GAS-002 | Refrigerant Storage Cylinder Bay | Z5 | 5.0 | 52.0 | 0.0 | 0/0/0 | Pending IFC delivery | ATEX Zone 2; cylinder bay |
| DT-KIT-GAS-003 | Gas Charging Zone Ventilation | Z5 | 11.0 | 55.0 | 5.5 | 0/0/0 | Pending IFC delivery | Ceiling-level ventilation unit |

---

## Governance

- Asset IDs in this file MUST match asset IDs in [`digital-twin.md`](../../digital-twin.md) §3.
- Zone IDs in this file MUST match zone IDs in [`docs/bim/zone-boundaries.md`](./zone-boundaries.md).
- AMR assets use live position from MiR Fleet Manager REST API; anchor coordinates in this file represent home/park positions only.
- **Gas zone assets (DT-KIT-GAS-*, DT-KIT-RF-002, DT-KIT-RF-003, DT-KIT-RF-004):** Any IFC coordinate update for ATEX Zone 2 assets requires EHS Officer co-sign-off.
- When IFC model is delivered, replace placeholder coordinates with IFC-extracted positions and populate IFC GUID column.
- Coordinate system change requires DT Integration Lead sign-off and updates to all downstream files.

