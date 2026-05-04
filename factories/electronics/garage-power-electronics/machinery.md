# Garage & Power Electronics Factory — Machinery & Equipment Register

> **Project Coo-Cah | Garage & Power Electronics Factory | Sagamu, Ogun State | Phase 1**

---

## 1. SMT PCB Assembly Line

Produces all PCBs for inverters, solar charge controllers, UPS, battery chargers, and power strips.

| # | Equipment                         | Qty | Spec / Model                              | Purpose                                              | Auto Level |
|---|-----------------------------------|-----|-------------------------------------------|------------------------------------------------------|------------|
| 1 | Solder Paste Screen Printer       | 1   | DEK Horizon 02i or MPM Momentum II        | Solder paste deposition onto PCB pads                | FA         |
| 2 | Pick-and-Place Machine (High Speed)| 1  | JUKI FX-3R (45,000 CPH)                   | High-speed SMT component placement                   | FA/AI      |
| 3 | Pick-and-Place Machine (Flexible) | 1   | JUKI RX-7 (large/odd-form components)     | MOSFET, IGBT, large caps, through-hole prep           | FA         |
| 4 | Reflow Oven                       | 1   | Heller 1964 MK5 (8-zone, 50kW)           | Lead-free reflow; power electronics profile control  | FA/AI      |
| 5 | Wave Soldering Machine            | 1   | Seho PowerSelective 1000 (60kW)           | Through-hole soldering for power components          | SA/A       |
| 6 | AOI — 3D Automated Optical Insp.  | 1   | Koh Young Zenith or Saki AX-M2            | Post-solder defect detection on power PCBs           | FA/AI      |
| 7 | ICT — In-Circuit Test System      | 1   | Keysight I3070 Series 5i                  | Verifies PCB net continuity, component values         | SA/A       |
| 8 | PCB Depanelling Router            | 1   | LPKF Contour C                            | Separates inverter/controller PCBs from panels        | A          |
| 9 | SPI — Solder Paste Inspection     | 1   | Koh Young KY8030-3                        | 3D solder paste volume check post-print              | FA/AI      |

---

## 2. Transformer & Inductor Winding Equipment

Inverters and battery chargers require custom-wound transformers and inductors — a key in-house capability for cost control and supply chain resilience.

| # | Equipment                            | Qty | Spec / Model                              | Purpose                                              | Auto Level |
|---|--------------------------------------|-----|-------------------------------------------|------------------------------------------------------|------------|
| 1 | Toroidal Transformer Winding Machine | 2   | JOVIL Universal or Marsilli TSR-80        | Winds toroidal cores for inverter transformers (12V–48V DC input) | SA/A |
| 2 | EI/EE Core Transformer Winding Machine | 2 | Nittoku NTS-AA or Marsilli universal      | Winds EI-core transformers for battery chargers       | SA/A       |
| 3 | Bobbin Winding Machine               | 4   | Nittoku CM-25 (precision, multi-axis)     | Winds coil bobbins for inductors and EMI filters      | A          |
| 4 | Inductor Winding Machine             | 2   | Marsilli VU-I coil winder                 | Winds power inductors for inverter output filters     | A          |
| 5 | Tape Insulation Winding Station      | 2   | Semi-auto tape wrapper                    | Applies Kapton/Mylar insulation between winding layers | SA        |
| 6 | Varnish Impregnation Tank + Oven     | 1   | Vacuum impregnation unit + curing oven    | Varnishes wound transformers for vibration resistance | SA         |
| 7 | Transformer Test Station             | 2   | Voltech AT3600 transformer analyser       | Tests turns ratio, inductance, leakage, insulation    | SA/A       |

---

## 3. Inverter Assembly Line

| # | Equipment                            | Qty | Spec / Model                              | Purpose                                              | Auto Level |
|---|--------------------------------------|-----|-------------------------------------------|------------------------------------------------------|------------|
| 1 | Chassis Assembly Station             | 4   | Assembly bench, pneumatic drill + press   | Assembles metal chassis, mounts heat sink            | M          |
| 2 | PCB Mounting & Torque Station        | 4   | Torque-controlled drivers (Atlas Copco)   | Mounts power PCB to chassis; MOSFET/IGBT torque control | M/SA    |
| 3 | Transformer Integration Station      | 3   | Assembly bench, crimping tools            | Mounts transformer; connects primary/secondary leads | M          |
| 4 | Wiring Harness Assembly              | 4   | Crimping bench, wire guides, ferrule tools| Assembles DC input, AC output, battery wiring harness | M         |
| 5 | Terminal Block & Connector Assembly  | 4   | Assembly bench, torque drivers            | Fits battery terminals, AC output terminals, USB ports | M         |
| 6 | BMS Programming Station              | 2   | Custom JTAG/UART fixture + software       | Programs Battery Management System firmware           | SA/AI      |
| 7 | Inverter Firmware Flash Station      | 3   | Custom USB/UART programming fixture       | Flashes inverter firmware; sets model parameters      | SA/AI      |
| 8 | Housing / Cover Assembly Station     | 4   | Assembly bench, screwdrivers              | Fits front panel, rear panel, top cover               | M          |
| 9 | Final Assembly Conveyor              | 1   | 20m belt conveyor, variable speed         | Links inverter assembly stations                      | A          |

---

## 4. Inverter & Power Electronics Testing Equipment

Critical section — every inverter, UPS, and solar controller is 100% tested before packaging.

| # | Equipment                               | Qty | Spec / Model                              | Purpose                                              | Auto Level |
|---|------------------------------------------|-----|-------------------------------------------|------------------------------------------------------|------------|
| 1 | Load Bank Tester (Resistive/Inductive)   | 4   | Avtron L-Series or Simplex 10kW load bank | Full-load test of inverter output 0–10kW range       | SA/A       |
| 2 | Power Quality / Efficiency Analyser      | 4   | Yokogawa WT310E or Fluke 435-II           | Measures output THD, efficiency, power factor        | SA/AI      |
| 3 | Waveform Analyser / Oscilloscope         | 4   | Rigol DS1054Z (100MHz) or Tektronix TBS2104 | Verifies pure sine wave output quality              | SA         |
| 4 | Battery Simulator (DC Power Supply)      | 4   | Chroma 62150H-600 (600V, 25A)            | Simulates 12V/24V/48V battery input for testing      | SA/A       |
| 5 | AC Mains Simulator                       | 2   | California Instruments 801P AC Source    | Simulates mains input; tests grid-tie switching      | SA         |
| 6 | Hipot / Safety Analyser                  | 4   | Chroma 19053                              | IEC 62040-1 safety test: dielectric, earth bond      | SA/A       |
| 7 | EMC Pre-Compliance Scanner               | 1   | Tekbox TBOH01 near-field + spectrum analyser | Pre-compliance EMC check before SON/CE submission | SA         |
| 8 | Solar Charge Controller Test Bench       | 3   | Solar array simulator + battery simulator  | Tests MPPT tracking efficiency (IEC 61683)           | SA/A       |
| 9 | UPS Test Station                         | 2   | Load bank + mains switch + battery tester | Tests UPS transfer time (< 10ms), runtime            | SA/A       |

---

## 5. Power Tool Assembly Line

| # | Equipment                            | Qty | Spec / Model                              | Purpose                                              | Auto Level |
|---|--------------------------------------|-----|-------------------------------------------|------------------------------------------------------|------------|
| 1 | Motor Assembly Station               | 4   | Assembly bench, arbor press               | Presses rotor/stator assembly for drill/grinder motors | M         |
| 2 | Gearbox Assembly Station             | 3   | Assembly bench, torque drivers, grease gun | Assembles gearbox; packs grease; tests rotation      | M          |
| 3 | Housing Assembly Station             | 4   | Assembly bench, pneumatic screwdrivers    | Fits motor + gearbox into tool housing               | M          |
| 4 | Switch & Cable Assembly              | 4   | Assembly bench, crimping tools            | Installs trigger switch, reverse switch, power cable | M          |
| 5 | Power Tool Function Test             | 4   | Load test dynamometer + power analyser    | Tests no-load RPM, stall torque, power draw          | SA         |
| 6 | Power Tool Safety Test (Hipot)       | 4   | Chroma 19053                              | IEC 60745 compliance — double insulation test        | SA/A       |
| 7 | Cordless Tool Battery Pack Assembly  | 2   | Cell sorter + spot welder + BMS station   | Assembles 18V Li-ion battery packs for cordless tools | SA/A      |

---

## 6. Cable & Wire Processing Equipment

| # | Equipment                            | Qty | Spec / Model                              | Purpose                                              | Auto Level |
|---|--------------------------------------|-----|-------------------------------------------|------------------------------------------------------|------------|
| 1 | Cable Cutting Machine                | 2   | Komax Gamma 263 or Schleuniger CrimpCenter | Cuts cables to precise length                        | A          |
| 2 | Pneumatic Crimping Tool Station      | 6   | Molex/TE Applicator on press             | Crimps terminals onto wire ends — inverter harnesses | SA         |
| 3 | Cable Marking Machine                | 1   | Brady BMP71 or Leroy Merlin thermal      | Prints cable ID sleeves for wiring harness traceability | A         |
| 4 | Cable Tester                         | 2   | Cirris Easy-Wire                          | Tests continuity and insulation of assembled harnesses | SA/A      |

---

## 7. Material Handling & Packaging

| # | Equipment                            | Qty | Spec / Model                              | Purpose                                              | Auto Level |
|---|--------------------------------------|-----|-------------------------------------------|------------------------------------------------------|------------|
| 1 | AMR Fleet                            | 8   | Geek+ P40 or KEENON T8 (250kg)           | Material transport: SMT → assembly → test → packaging | AI/FA     |
| 2 | Electric Counterbalance Forklift     | 2   | Toyota 8FBMT25 (2.5t)                    | Container offloading, heavy pallet movement           | M          |
| 3 | Selective Pallet Racking             | 1   | 60-bay, 3 levels                         | Raw materials and WIP storage                         | M          |
| 4 | Automatic Carton Erector             | 1   | Wexxar WF30                              | Erects product cartons                                | A          |
| 5 | Carton Sealer                        | 1   | Wexxar WF5                               | Tapes sealed cartons                                  | A          |
| 6 | Label Printer & Applicator           | 2   | Zebra ZT620 + applicator arm             | SON label, model label, serial number print & apply   | A/AI       |
| 7 | Pallet Wrapper                       | 1   | Robopac Rotoplat 306                     | Stretch-wraps pallets for dispatch                    | A          |

---

*Refer to [`energy-profile.md`](./energy-profile.md) for equipment power loads and energy system design.*
