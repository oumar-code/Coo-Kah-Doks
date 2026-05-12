# Kitchen Electronics — Zone Boundaries (BIM Stub)

> **Gate 3 Artifact (Digital Twin Spatial Readiness)**
> **Document Version:** 1.0 | **Owner:** BIM / Facilities Engineering
> **Integration Reviewer:** DT Integration Lead
> **Coordinate System:** LOCAL_GRID_M — origin at south-west internal corner of main factory building; x-axis = West→East; y-axis = South→North; z-axis = floor level = 0.00 m.
> **Status:** Zone envelopes derived from [`floor-plan.md`](../../floor-plan.md) zone allocations and building footprint (~15,000 m²). All coordinate values are **approximate planning-level envelopes only**. Precise IFC/BIM coordinates (corner points, elevations, column grid references) are **pending delivery of the IFC architectural model**.

---

## Zone Boundary Register

| Zone ID | Zone Name | Boundary Coordinates (x,y) — m | Elevation z min..z max — m | Coordinate System | Source Reference |
|---------|-----------|----------------------------------|----------------------------|------------------|------------------|
| Z1  | Raw Material & Component Store   | (0,80);(50,80);(50,110);(0,110)     | 0.00..9.00 | LOCAL_GRID_M | floor-plan.md §2 — Z1; precise BIM coords pending IFC |
| Z2  | SMT PCB Production               | (50,80);(90,80);(90,110);(50,110)   | 0.00..6.00 | LOCAL_GRID_M | floor-plan.md §2 — Z2; precise BIM coords pending IFC |
| Z3  | Refrigerator Sheet Metal Fab     | (90,80);(125,80);(125,108);(90,108) | 0.00..9.00 | LOCAL_GRID_M | floor-plan.md §2 — Z3; precise BIM coords pending IFC |
| Z4  | Refrigerator Assembly — Main     | (0,55);(125,55);(125,80);(0,80)     | 0.00..9.00 | LOCAL_GRID_M | floor-plan.md §2 — Z4; precise BIM coords pending IFC |
| Z5  | R600a Gas Charging Zone          | (0,40);(22,40);(22,55);(0,55)       | 0.00..6.00 | LOCAL_GRID_M | floor-plan.md §2 — Z5; ATEX Zone 2 below z=0.50; precise BIM coords pending IFC |
| Z6  | Microwave Oven Assembly          | (40,40);(68,40);(68,55);(40,55)     | 0.00..6.00 | LOCAL_GRID_M | floor-plan.md §2 — Z6; precise BIM coords pending IFC |
| Z7  | Electric Cooker Assembly         | (68,40);(93,40);(93,55);(68,55)     | 0.00..6.00 | LOCAL_GRID_M | floor-plan.md §2 — Z7; precise BIM coords pending IFC |
| Z8  | SDA Assembly Lines (A, B, C)     | (93,30);(125,30);(125,55);(93,55)   | 0.00..6.00 | LOCAL_GRID_M | floor-plan.md §2 — Z8; 3 parallel lines within envelope; precise BIM coords pending IFC |
| Z9  | In-Process QC (IPQC)             | (0,20);(30,20);(30,40);(0,40)       | 0.00..5.00 | LOCAL_GRID_M | floor-plan.md §2 — Z9; precise BIM coords pending IFC |
| Z10 | Final QC + OBA                   | (30,20);(58,20);(58,40);(30,40)     | 0.00..5.00 | LOCAL_GRID_M | floor-plan.md §2 — Z10; precise BIM coords pending IFC |
| Z11 | Packaging & Labelling            | (58,20);(93,20);(93,40);(58,40)     | 0.00..6.00 | LOCAL_GRID_M | floor-plan.md §2 — Z11; precise BIM coords pending IFC |
| Z12 | Finished Goods Warehouse         | (0,5);(125,5);(125,20);(0,20)       | 0.00..9.00 | LOCAL_GRID_M | floor-plan.md §2 — Z12; ESFR sprinklers; precise BIM coords pending IFC |
| Z13 | Maintenance Workshop             | (0,0);(25,0);(25,5);(0,5)           | 0.00..5.00 | LOCAL_GRID_M | floor-plan.md §2 — Z13; precise BIM coords pending IFC |
| Z14 | Compressor & Test Services       | (22,40);(40,40);(40,55);(22,55)     | 0.00..5.00 | LOCAL_GRID_M | floor-plan.md §2 — Z14; adjacent to Z5 gas zone; precise BIM coords pending IFC |
| Z15 | EHS & First Aid                  | (25,0);(37,0);(37,5);(25,5)         | 0.00..3.00 | LOCAL_GRID_M | floor-plan.md §2 — Z15; precise BIM coords pending IFC |
| Z16 | IT / MES Server Room             | (37,0);(47,0);(47,5);(37,5)         | 0.00..3.00 | LOCAL_GRID_M | floor-plan.md §2 — Z16; FM-200 suppression zone; precise BIM coords pending IFC |
| Z17 | Staff Facilities                 | (47,0);(72,0);(72,5);(47,5)         | 0.00..3.00 | LOCAL_GRID_M | floor-plan.md §2 — Z17; precise BIM coords pending IFC |

---

## Governance

- Zone IDs in this file MUST match zone IDs in [`floor-plan.md`](../../floor-plan.md) §2.
- Zone IDs in this file MUST match zone IDs used in [`docs/sensor-map.md`](../sensor-map.md) `Location (Zone)` column.
- Zone IDs in this file MUST match zone IDs used in [`docs/bim/asset-anchors.md`](./asset-anchors.md) `Zone ID` column.
- Coordinate system change requires DT Integration Lead sign-off and update of all downstream files.
- When IFC model is delivered, replace all approximate coordinates with IFC-extracted corner points and update the document header status.

