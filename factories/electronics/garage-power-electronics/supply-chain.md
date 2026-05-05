# Garage & Power Electronics Factory — Supply Chain Management

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Garage & Power Electronics Factory | **Location:** Sagamu Industrial Estate, Ogun State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Supply Chain & Procurement Team

---

## 1. Supply Chain Overview

The power electronics supply chain is heavily weighted toward imported semiconductor components (MOSFETs, IGBTs, gate drivers) and magnetic materials (silicon steel laminations, toroidal cores, magnet wire). Local sourcing is achievable for copper wire, plastic enclosures (from Coo-Cah Plastics), and all packaging. Phase 2 targets local transformer assembly from imported cores.

| Supply Category                 | Origin                           | % BOM Cost | Lead Time    | Key Risk                           |
|---------------------------------|----------------------------------|------------|--------------|------------------------------------|
| Power MOSFETs / IGBTs           | Import — Infineon, ON Semi       | 20%        | 8–12 weeks   | Semiconductor allocation; shortage |
| Toroidal / EI Transformer Cores | Import — silicon steel, Germany/China | 12%  | 6–10 weeks   | Steel spec; delivery              |
| Magnet Wire (copper)            | Import + Local (Nigerian copper co.) | 8%   | 2–4 weeks    | Gauge availability                 |
| Electrolytic Capacitors         | Import — Nichicon, Rubycon       | 6%         | 6–8 weeks    | Temperature grade; lead times      |
| Gate Driver ICs                 | Import — Texas Instruments       | 5%         | 8–10 weeks   | Semiconductor allocation           |
| PCB Bare Boards                 | Import — China / Taiwan          | 5%         | 4–6 weeks    | Board quality                      |
| SMT Passives (R, C, L)          | Import — Yageo, Samsung          | 6%         | 4–8 weeks    | Reel fragmentation                 |
| Plastic Enclosures (inverter)   | **Coo-Cah Plastics Factory**    | 10%        | **1–2 days** | Internal capacity                  |
| Power Tool Motors               | Import — Johnson Electric, Mabuchi | 8%      | 6–8 weeks    | Spec matching                      |
| Power Tool Gearboxes / Chucks   | Import — China                   | 6%         | 6–8 weeks    | Torque spec                        |
| Power Strip Sockets (IEC)       | Import — Schurter / Local        | 3%         | 3–5 weeks    | Contact quality                    |
| Batteries (UPS internal, VRLA)  | Import — CSB Battery, Vision     | 4%         | 6–8 weeks    | Safety cert; NESREA disposal plan  |
| Packaging                       | **Local (Lagos, Sagamu)**        | 3%         | 1–2 weeks    | Local quality management           |

---

## 2. Import Logistics

### 2.1 Inbound Freight Routes

| Route                          | Mode          | Port of Entry      | Transit (CIF Lagos) | Cost / 40ft HQ    |
|--------------------------------|---------------|--------------------|----------------------|-------------------|
| Semiconductors (Germany/US)    | Air Freight   | Lagos MMIA         | 3–5 days             | $7.00–$10.00/kg   |
| Transformer cores (China)      | Sea FCL       | Tin Can Island     | 22–28 days           | $3,500–$4,500     |
| PCBs + passives (China)        | Sea LCL       | Tin Can Island     | 24–30 days           | $180–$220/CBM     |
| Power tool motors (China)      | Sea FCL/LCL   | Tin Can Island     | 22–28 days           | $3,500–$4,200     |
| UPS batteries (China)          | Sea FCL       | Tin Can / Apapa    | 22–28 days           | Special DG class  |
| Capacitors (Japan/Taiwan)      | Air Freight   | Lagos MMIA         | 3–5 days             | $7.00–$9.00/kg    |

> **Note:** MOSFETs and critical ICs are air-freighted as their lead times are the factory's longest constraint. 90-day safety stock maintained to buffer semiconductor supply allocation risks.

### 2.2 Safety Stock Policy

| Component                    | Safety Stock Level | Reorder Point | Justification                                   |
|------------------------------|--------------------|---------------|-------------------------------------------------|
| Power MOSFETs / IGBTs        | 90 days demand     | 60 days       | Semiconductor allocation risk; critical path     |
| Toroidal / EI Transformer Cores | 60 days demand | 45 days       | Long sea freight; high-volume usage             |
| Gate Driver ICs (TI)         | 90 days demand     | 60 days       | Semiconductor allocation; sole-source risk       |
| Electrolytic Capacitors      | 45 days demand     | 30 days       | Sea freight + quality risk                       |
| UPS VRLA Batteries           | 30 days demand     | 20 days       | Controlled hazardous goods shipping; NESREA     |
| Plastic Enclosures           | 7 days demand      | 3 days        | Intra-group daily delivery                       |
| Packaging                    | 10 days demand     | 5 days        | Local supply                                     |

---

## 3. Intra-Group Supply Links

### 3.1 Coo-Cah Plastics Factory → Garage Power Electronics

| Component                       | Spec                                    | Daily Volume | Lead Time |
|---------------------------------|-----------------------------------------|--------------|-----------|
| Inverter front panel housing    | ABS/PC, tooled per model; vented        | 800 pcs      | 1–2 days  |
| Inverter rear panel housing     | ABS, cable entry knockout               | 800 pcs      | 1–2 days  |
| SCC housing (MPPT + PWM)        | ABS, DIN rail or wall-mount             | 500 pcs      | 1–2 days  |
| Power strip body (PCB channel)  | ABS, flame-retardant V-0 grade          | 2,000 pcs    | 1–2 days  |
| Power tool handle / body        | ABS+PP, ergonomic; tool-mounted         | 400 sets     | 1–2 days  |
| UPS housing                     | ABS/metal hybrid                        | 200 pcs      | 1–2 days  |

### 3.2 Garage Power Electronics → Sister Factories (Internal Supply)

| Product Supplied                  | Destination                             | Volume (Phase 1) | Priority  |
|-----------------------------------|-----------------------------------------|------------------|-----------|
| PSW Inverters (3kVA, 5kVA)        | All Coo-Cah factories — backup power    | 150 units/month  | Highest   |
| UPS (1kVA rack-mount)             | MES server rooms at all factories       | 50 units/month   | Highest   |
| MPPT Solar Charge Controllers     | Energy team — rooftop solar projects    | 100 units/month  | High      |
| Smart Surge-Protected Power Strip | All factories — IT + equipment          | 500 units/month  | High      |
| Electric Power Tools (Drill+AG)   | Maintenance workshops                   | 50 units/month   | Medium    |

---

## 4. Phase 2+ Supply Chain Targets

| Component                    | Phase 1 Source          | Phase 2 Target                                      |
|------------------------------|-------------------------|-----------------------------------------------------|
| Transformer cores            | Fully imported          | Investigate local steel lamination from Coo-Cah Metallurgical |
| Transformer winding          | Manual (in-house)       | CNC automated winding (Phase 2)                     |
| UPS batteries                | Imported (VRLA)         | Evaluate LiFePO₄ packs from Coo-Cah BESS assembly  |
| PCBs (inverter control board)| In-house SMT            | Consolidate to Coo-Cah Personal Electronics SMT line |
| Plastic enclosures           | Coo-Cah Plastics        | ✅ Already intra-group                               |

---

*Refer to [`capex-opex.md`](./capex-opex.md) for landed cost modelling.*
*Refer to [`regulatory.md`](./regulatory.md) for Form M and SON CoC compliance.*
