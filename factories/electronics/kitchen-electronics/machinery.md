# Kitchen Electronics Factory — Machinery & Equipment Register

> **Project Coo-Cah | Kitchen Electronics Factory | Lagos/Ogun, Nigeria | Phase 1**

---

## 1. SMT (Surface Mount Technology) PCB Assembly Line

The SMT line produces all PCBs consumed internally by the kitchen electronics assembly lines — refrigerator control boards, microwave control PCBs, induction cooker power PCBs, and small appliance circuit boards. All SMT equipment is Tier-1 OEM sourced, integrated via OPC-UA into the Coo-Cah MES.

| # | Equipment                         | Qty | Spec / Model                           | Purpose                                                        | Auto Level |
|---|-----------------------------------|-----|----------------------------------------|----------------------------------------------------------------|------------|
| 1 | Solder Paste Screen Printer       | 1   | DEK Horizon 02i (or MPM Momentum II)   | Deposits solder paste onto PCB pads via laser-cut stencil      | FA         |
| 2 | Pick-and-Place Machine (High Speed) | 1 | JUKI FX-3R (45,000 CPH)               | High-speed placement of 0402+ SMT components onto PCBs         | FA/AI      |
| 3 | Pick-and-Place Machine (Flexible) | 1   | JUKI RX-7 (or Fuji NXT III M3)        | Flexible placer for connectors, odd-form, large components     | FA         |
| 4 | Reflow Oven                       | 1   | Heller 1964 MK5 (8-zone, forced convection) | Lead-free reflow soldering (SAC305 profile); N₂ optional  | FA/AI      |
| 5 | AOI — Automated Optical Inspection | 1  | Koh Young Zenith (3D AOI)             | Post-reflow defect detection: solder bridges, missing parts, tombstone | FA/AI |
| 6 | Wave Soldering Machine            | 1   | Seho PowerSelective 600 or Ersa POWERFLOW e | Through-hole component soldering                     | SA/A       |
| 7 | Selective Soldering Machine       | 1   | Seho SelectLine or ERSA Versaflow      | Selective through-hole solder for mixed PCBs                   | A          |
| 8 | In-Circuit Test (ICT) System      | 1   | Keysight I1000D or Genrad 228xT        | Electrical test of PCB nets, component values, shorts/opens    | SA/AI      |
| 9 | Flying Probe Tester               | 1   | Spea 4040 or Takaya APT-1400F          | Low-volume/NPI PCB testing — no dedicated fixture required     | A          |
| 10| PCB Depanelling Router            | 1   | LPKF Contour Router or Jyy JV-3E       | Separates individual PCBs from production panels               | A          |
| 11| PCB Magazine Loader/Unloader      | 2   | SMEMA-compatible auto loader           | Auto feeds PCBs into and off SMT line                          | FA         |
| 12| SPI — Solder Paste Inspection     | 1   | Koh Young KY8030-3 or CyberOptics SE300 | Post-print 3D solder paste volume inspection                  | FA/AI      |
| 13| Rework Station                    | 2   | JBC HDE-9B (BGA/SMD hot air rework)    | Manual PCB rework for SMT defects                              | M          |
| 14| ESD-Safe SMT Conveyor             | 1   | Inline conveyor, ESD belt, variable speed | Links SMT stations in production flow                       | A          |
| 15| Stencil Cleaner                   | 1   | DEK ProCleaner Plus                    | Automated SMT stencil cleaning                                 | A          |

---

## 2. Refrigerator Assembly Line

The refrigerator assembly line produces both single-door direct-cool and two-door frost-free models. Line changeover between models takes approximately 45 minutes (targeting < 30 min by Phase 2).

| # | Equipment                               | Qty | Spec / Model                           | Purpose                                                          | Auto Level |
|---|-----------------------------------------|-----|----------------------------------------|------------------------------------------------------------------|------------|
| 1 | Cabinet Assembly Jig & Press            | 2   | Custom steel frame jig, pneumatic clamps | Assembles inner liner + outer cabinet; applies foam seal strips | SA         |
| 2 | PU Foam Injection Machine               | 1   | Hennecke TOPLINE or Cannon A-SYSTEM (45kW) | Injects polyurethane foam insulation between inner/outer cabinet | SA/A     |
| 3 | Foam Curing Conveyor / Holding Racks    | 1   | 40-position static cure rack           | Allows PU foam to cure to full hardness (20 min)                 | SA         |
| 4 | Compressor Pressing & Mounting Station  | 1   | Pneumatic compressor press + torque driver | Mounts and secures compressor to base frame                  | SA         |
| 5 | Condenser Coil Assembly Station         | 2   | Assembly bench + leak test gauge       | Fits condenser coil; visual inspection for copper damage         | M          |
| 6 | Evaporator Assembly Station             | 2   | Assembly bench + torque tools           | Fits evaporator; connects refrigerant circuit tubing            | M          |
| 7 | Refrigerant Circuit Brazing Station     | 1   | Oxy-acetylene brazing kit, nitrogen purge | Brazes refrigerant circuit joints; nitrogen leak pre-test    | M/SA       |
| 8 | Vacuum Station                          | 2   | REFCO R-32 Vacuum Pump or Robinair     | Evacuates refrigerant circuit to < 200 microns before charging  | SA         |
| 9 | Gas Charging Station (R600a)            | 2   | INFICON Charge Machine or Robinair 34700 | Precisely charges R600a refrigerant (controlled substance)  | A/FA       |
| 10| Door Assembly Station                   | 4   | Assembly bench, door hinge press        | Assembles door gasket, hinge, inner door tray; attaches to cabinet | M        |
| 11| PCB Control Board Installation          | 2   | Assembly bench, ESD protection          | Installs control PCB, thermostat, LED lighting module            | M          |
| 12| Electrical Connection & Wiring Station  | 2   | Assembly bench, wire management         | Connects compressor, fan, heaters, sensors, PCB                  | M          |
| 13| Performance Test Station                | 3   | Thermocouple logger, power meter, 24h test rack | 24-hour operational test (temp stabilisation, power draw) | SA      |
| 14| Energy Efficiency Test Bench            | 2   | Yokogawa WT333 power analyser           | Measures kWh/24h per unit — IEC 62552 standard                   | SA/AI      |
| 15| Safety Test — Hipot & Earth Bond        | 2   | Chroma 19053 Safety Analyser            | IEC 60335-1 electrical safety test (dielectric, earth bond)      | SA/A       |
| 16| Final Visual Inspection Station         | 3   | Inspection bench, UV light, mirror trolley | 360° cosmetic and functional final inspection                | M          |

---

## 3. Microwave Oven Assembly Line

| # | Equipment                               | Qty | Spec / Model                           | Purpose                                                          | Auto Level |
|---|-----------------------------------------|-----|----------------------------------------|------------------------------------------------------------------|------------|
| 1 | Magnetron Assembly & Testing Station    | 2   | Assembly bench + HV power supply test  | Mounts magnetron into cavity; tests high-voltage transformer     | M/SA       |
| 2 | Cavity Assembly Station                 | 2   | Assembly bench, pneumatic screw driver  | Assembles stainless steel cavity, waveguide cover                | M          |
| 3 | PCB Installation Station                | 2   | ESD bench, torque driver               | Installs control PCB, touch panel, display                       | M          |
| 4 | Turntable Assembly Station              | 2   | Assembly bench                         | Installs turntable motor, ring, and glass plate                  | M          |
| 5 | Door Assembly & Interlock Station       | 2   | Assembly bench, door interlock test rig | Assembles door, latches; tests door interlock safety switches    | M/SA       |
| 6 | Outer Cabinet Assembly Station          | 2   | Assembly bench, screwdriver set         | Attaches outer cabinet; installs handle and control panel trim   | M          |
| 7 | Microwave Leak Test Station             | 2   | Narda SMR-3 or Mettler Toledo MW Leakage Tester | Tests for RF leakage < 5mW/cm² (IEC 60335-2-25)       | SA/A       |
| 8 | Functional Test Station                 | 3   | Test rig: water load, power meter, timer | Tests cooking power levels, timer, grill, convection function  | SA         |
| 9 | Hipot & Safety Test                     | 2   | Chroma 19053                           | IEC 60335-1 + IEC 60335-2-25 safety compliance test             | SA/A       |

---

## 4. Electric Cooker & Induction Hob Assembly Line

| # | Equipment                               | Qty | Spec / Model                           | Purpose                                                          | Auto Level |
|---|-----------------------------------------|-----|----------------------------------------|------------------------------------------------------------------|------------|
| 1 | Conventional Burner Assembly Station    | 3   | Assembly bench, torque driver          | Mounts cast iron burners, gas-to-electric conversion units       | M          |
| 2 | Induction Coil Assembly Station         | 2   | Assembly bench, ESD protection         | Mounts induction coil assembly, ferrite shield                   | M          |
| 3 | IGBT PCB Assembly Station               | 2   | ESD bench — received from SMT line     | Fits IGBT power board into chassis; heat sink mounting           | M          |
| 4 | Tempered Glass Hob Fitting              | 2   | Assembly bench, suction cup lifter     | Mounts tempered glass surface; applies gasket seal               | M/SA       |
| 5 | Control Panel Assembly                  | 2   | Assembly bench, torque driver          | Installs touch/knob control panel, indicator LEDs                | M          |
| 6 | Wiring Harness & Electrical Assembly    | 2   | Assembly bench, wire management        | Routes and terminates all internal wiring to IEC 60320 standard  | M          |
| 7 | Cooker Safety & Function Test           | 3   | Temperature calibrator, power analyser | Tests heating element performance, temperature accuracy, safety  | SA         |
| 8 | Induction Power & Efficiency Test       | 2   | Fluke 1760 power quality analyser      | Tests induction coil efficiency, EMC pre-screen                  | SA/A       |
| 9 | Hipot & Earth Continuity Test           | 2   | Chroma 19053                           | IEC 60335-2-6 compliance testing                                 | SA/A       |

---

## 5. Small Domestic Appliances (SDA) Lines

Three parallel lines operating on a flexible basis: Line SDA-1 (blenders), Line SDA-2 (kettles & toasters), Line SDA-3 (rice cookers).

| # | Equipment                               | Qty | Spec / Model                           | Purpose                                                          | Auto Level |
|---|-----------------------------------------|-----|----------------------------------------|------------------------------------------------------------------|------------|
| 1 | Motor Assembly Station (Blenders)       | 4   | Assembly bench, torque driver, arbor press | Presses motor into housing; connects carbon brush assembly  | M          |
| 2 | Blade & Bowl Assembly Station           | 4   | Assembly bench, blade seal press       | Assembles blade unit, applies seal, attaches bowl               | M          |
| 3 | PCB + Switch Fitting Station            | 4   | ESD bench                              | Fits control PCB and speed switch into housing                  | M          |
| 4 | SDA Housing Assembly Station           | 6   | Assembly bench, screwdrivers           | Final housing assembly, cord management                         | M          |
| 5 | Blender Function Test                   | 4   | Load test rig (water), power analyser  | Tests all speed functions, blade integrity                      | SA         |
| 6 | Kettle Heating Element Assembly         | 4   | Assembly bench, welding tool           | Mounts stainless steel element + thermostat                     | M          |
| 7 | Kettle Function Test                    | 4   | Auto-boil test rig                     | Boils to 100°C, confirms auto-shutoff function                  | SA         |
| 8 | Rice Cooker Pot & Heating Plate         | 4   | Assembly bench                         | Assembles heating plate, non-stick pot, thermostat              | M          |
| 9 | SDA Safety & Hipot Test (shared)        | 4   | Chroma 19053 (shared across SDA lines) | IEC 60335 series electrical safety test for all SDA products    | SA/A       |
| 10| SDA Final Visual & Pack Inspection      | 6   | Inspection bench                       | Cosmetic check, accessories confirm, manual insert              | M          |

---

## 6. Quality Control Equipment

| # | Equipment                               | Qty | Spec / Model                           | Purpose                                                          | Auto Level |
|---|-----------------------------------------|-----|----------------------------------------|------------------------------------------------------------------|------------|
| 1 | 3D AOI (SMT line)                       | 1   | Koh Young Zenith (see SMT section)     | PCB post-solder inspection                                       | FA/AI      |
| 2 | X-Ray Inspection System                 | 1   | Nordson DAGE 4000 or Omron VT-X750     | BGA solder inspection on complex PCBs                           | A/AI       |
| 3 | Energy Consumption Tester               | 3   | Yokogawa WT333 + IEC 62552 test software | Product energy rating per IEC standard                        | SA/AI      |
| 4 | Hipot / Safety Analyser                 | 6   | Chroma 19053 + Chroma 19036            | Dielectric strength (hipot), earth bond, insulation resistance  | SA/A       |
| 5 | Microwave Leakage Meter                 | 2   | Narda SMR-3                            | IEC 60335-2-25 microwave leakage compliance                     | SA         |
| 6 | Environmental Chamber (Temperature cycling) | 1 | Weiss WK-P 1000/40 or Binder MKF 115 | Temperature + humidity endurance testing for product qualification | SA      |
| 7 | Drop Test Rig                           | 1   | Custom drop test frame, ISTA standard  | Packaging and product drop test compliance                      | M/SA       |
| 8 | Digital Calliper / Micrometer Station   | 4   | Mitutoyo IP67 calipers                 | Dimensional checks on mechanical components                     | M          |
| 9 | Pull/Torque Tester                      | 1   | Mecmesin MultiTest-dV                  | Cable pull strength, screw torque verification                  | SA         |
| 10| ESD Wrist Strap Tester (stations)       | 10  | SCS Model 724 or similar               | Daily ESD wrist strap compliance check                          | SA         |

---

## 7. Material Handling Equipment

| # | Equipment                               | Qty | Spec / Model                           | Purpose                                                          | Auto Level |
|---|-----------------------------------------|-----|----------------------------------------|------------------------------------------------------------------|------------|
| 1 | AMR — Transport Fleet                   | 10  | Geek+ P40 or KEENON T8 (250kg payload) | Intra-factory material transport (components, WIP, FG)          | AI/FA      |
| 2 | AMR Charging Docks                      | 10  | OEM matching AMR model                 | Autonomous charging between tasks                               | FA         |
| 3 | ESD-Safe Belt Conveyor (SMT line)       | 1   | 30m, ESD belt, variable speed          | PCB flow through SMT production stations                        | A          |
| 4 | Overhead Conveyor — Refrigerator Line   | 1   | Monorail, 50-hanger, motorised         | Moves refrigerator cabinets between assembly stations           | SA/A       |
| 5 | Electric Counterbalance Forklift        | 2   | Toyota 8FBMT25 (2.5t, 4.5m lift)      | Container offloading, heavy pallet movement                     | M          |
| 6 | Electric Pallet Jack                    | 4   | Crown WT 3040 (2000kg)                 | Internal pallet movement, dock to stores                        | M          |
| 7 | Selective Pallet Racking (RMS)          | 1   | 80-bay, 3 levels, 1.5t/bay capacity    | Raw material and component storage                              | M          |
| 8 | Vertical Lift Module (SMT components)   | 2   | Hänel Lean-Lift (1,000 trays)          | High-density storage for SMT reels and small components         | A          |

---

## 8. Packaging Line

| # | Equipment                               | Qty | Spec / Model                           | Purpose                                                          | Auto Level |
|---|-----------------------------------------|-----|----------------------------------------|------------------------------------------------------------------|------------|
| 1 | Automatic Carton Erector (Large — fridge) | 1 | Wexxar WF30 or Endoline 101            | Erects outer shipping cartons for refrigerators/microwaves      | A          |
| 2 | Automatic Carton Erector (Small — SDA)  | 1   | Lantech CST or Endoline 101 (smaller)  | Erects smaller product cartons for SDA products                 | A          |
| 3 | Polystyrene Insert Dispenser            | 2   | Custom frame feed                      | Places EPS foam end-caps into cartons before product insert     | SA         |
| 4 | Product Insert / Fill Station           | 4   | Ergonomic assembly station             | Places product, accessories, manual into carton                 | SA         |
| 5 | Carton Sealer — Top/Bottom              | 2   | Wexxar WF5 or Signode                  | Tapes top and bottom of carton at production rate               | A          |
| 6 | Pallet Wrapper (Stretch Film)           | 2   | Robopac Rotoplat 306 (auto)            | Stretch-wraps finished pallet loads                             | A          |
| 7 | Label Printer & Applicator (inline)     | 2   | Zebra ZT620 + applicator arm           | Prints and applies product label (SON, energy rating, serial)   | A/AI       |
| 8 | Checkweigher                            | 2   | Mettler Toledo C35 or Ishida           | Verifies packed weight; rejects under/over spec cartons         | FA/AI      |
| 9 | Barcode/QR Verifier (inline)           | 2   | Cognex DataMan 262                     | Verifies label print quality before dispatch                    | FA         |
| 10| Shrink Wrap Tunnel (SDA products)       | 1   | Conflex or Wulfsberg 400T              | Applies shrink overwrap for small appliance retail packs        | A          |

---

## 9. Energy & Utilities Equipment

| # | Equipment                               | Qty | Spec / Model                           | Purpose                                                          | Auto Level |
|---|-----------------------------------------|-----|----------------------------------------|------------------------------------------------------------------|------------|
| 1 | Solar PV Array                          | —   | 700 kWp monocrystalline PERC (Longi/Risen) | Rooftop primary power generation                           | AI/FA      |
| 2 | LFP BESS                                | —   | 800 kWh, LFP, 400V DC bus (CATL/BYD)  | Energy storage + overnight critical load                        | AI/FA      |
| 3 | Hybrid Grid-Tied Inverter               | 4   | Sungrow SH250HX (250kW each)           | Solar/BESS/grid management                                      | FA         |
| 4 | Automatic Transfer Switch               | 2   | Socomec SIRCO AC                       | Seamless solar/BESS/grid/generator switching                    | FA         |
| 5 | Diesel Standby Generator                | 1   | Perkins 500kVA (400kW output)          | Emergency backup power                                          | SA         |
| 6 | Compressed Air System                   | 2   | Atlas Copco GA55+ (55kW, 7 bar, 290 l/s) | Factory-wide pneumatic supply                               | A          |
| 7 | Central HVAC System                     | 1   | Daikin VRV / Carrier AHU, 120kW cooling | Factory climate control                                       | A/AI       |
| 8 | Refrigerant Gas Recovery Unit           | 1   | Refco Cora-L R600a Recovery            | R600a refrigerant recovery — regulatory requirement            | SA         |
| 9 | Nitrogen Generator                      | 1   | Parker domnick hunter NGP 30           | Nitrogen supply for refrigerant circuit purging                 | A          |

---

*For energy system sizing calculations, refer to [`energy-profile.md`](./energy-profile.md).*
*For MES integration of each machine, refer to [`mes-integration.md`](./mes-integration.md).*
