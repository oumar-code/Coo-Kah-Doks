# Raspberry Pi Pilot Deployment Profile (External Factories)

> **Project Coo-Cah | Go-to-Market + Technical Delivery**
> **Document Version:** 1.0 | **Owner:** CTO / Digital Twin Engineering + CRO
> **Purpose:** Define the concrete MVP deployment profile for external-factory pilots using Raspberry Pi edge kits.

---

## 1. Scope and Boundary

This profile applies only to the **external-factory MVP offer**:

- 1 machine or 1 production line
- Basic predictive maintenance signals (vibration + temperature first)
- Local dashboard + alerts + cloud sync for analysis and reporting

This is a **pilot deployment profile**, not the full Coo-Cah factory-standard DT stack.

When scope grows to multi-line, many assets, or full-factory orchestration, transition to the heavier edge-node architecture in:
- [`platform/digital-twin-platform-architecture.md`](https://github.com/oumar-code/Coo-Kah-Doks/blob/main/platform/digital-twin-platform-architecture.md)

---

## 2. What Goes to Customer Site (Pilot Kit)

Per pilot site, deploy:

| Component | Minimum Spec | Notes |
|---|---|---|
| Edge compute | Raspberry Pi (industrial enclosure) | Installed near target machine/line |
| Sensors | 2–4 sensors (vibration + temperature first) | Mounted on failure-prone points |
| Local storage | SD + external SSD (as needed) | Buffer for offline operation |
| Power | Regulated PSU + surge protection | Sized for local grid/generator instability |
| Connectivity | Wi-Fi / Ethernet / 4G fallback | Chosen per site constraints |
| Customer access | Browser on tablet/PC/phone (optional local display) | No complex client install required |

---

## 3. How Software Gets onto Raspberry Pi

### 3.1 Pre-shipment Preparation

Prepare a standard Coo-Cah Pi image with:

- Edge runtime services
- Local data store/cache
- Local dashboard UI
- Sync agent for cloud uplink
- Device health agent (uptime, storage, connectivity, sensor status)

### 3.2 On-site Commissioning

At installation:

1. Register the Pi to `factory_id` and target `asset_id`
2. Connect and validate sensor inputs
3. Confirm dashboard access on customer browser/device
4. Verify alert path (WhatsApp/SMS) and cloud sync

### 3.3 Post-activation Model

- Remote updates are controlled by Coo-Cah
- Edge services remain usable offline
- On reconnection, buffered data is synced to cloud

---

## 4. Sensor Integration on Customer Machine/Line

### 4.1 Mounting Targets

Prioritise failure-prone assets:

- Motor housing
- Bearing block
- Gearbox
- Pump
- Conveyor drive

### 4.2 Integration Rules (MVP)

- Start with **non-invasive installation** where possible
- In Phase MVP, use **read-only telemetry** from sensors
- Do not write control commands back to customer OT assets

---

## 5. What the Customer Sees

Customer-facing screen should stay simple and operational:

- Machine status: **Healthy / Warning / Critical**
- Current readings: vibration, temperature, runtime
- Trend charts over time
- Alert history timeline
- Basic maintenance recommendation
- Weekly summary and end-of-pilot ROI report

Alert channel for MVP:
- WhatsApp/SMS notifications to Plant Manager and Maintenance Lead

---

## 6. What Coo-Cah Sees Internally

Coo-Cah internal operations view includes:

- All customer-visible machine health data
- Raw telemetry streams + timestamps
- Anomaly history and alert accuracy
- Device health: online/offline, storage, sensor connectivity, sync status
- Fleet view across active pilot sites
- Conversion metrics: downtime risk found, estimated savings, pilot success score

---

## 7. Data Visibility Split

### 7.1 Customer View (Factory-scoped)

- Their own machine/line health
- Their own alerts and trend charts
- Their own weekly and end-of-pilot reports
- Their own ROI outputs

### 7.2 Coo-Cah Internal View

- Customer view data, plus:
  - Raw sensor telemetry
  - Model diagnostics
  - Device/fleet monitoring
  - Cross-site benchmarking and analytics

Access remains **factory-scoped by default**, with group-level visibility by explicit grant, aligned with:
- [`platform/data-governance-policy.md`](https://github.com/oumar-code/Coo-Kah-Doks/blob/main/platform/data-governance-policy.md)

---

## 8. MVP Operating Model

| Layer | MVP Delivery Model |
|---|---|
| Edge at customer site | Raspberry Pi local processing + local dashboard |
| Customer notifications | WhatsApp/SMS alerts |
| Cloud | Sync telemetry/summaries for fleet analytics and reporting |
| Resilience | Local operation continues during internet outages |

Sync rule:
- Send only data required for analysis, monitoring, and reports
- Keep pilot usable even when internet is down

---

## 9. Recommended MVP Deployment Sequence

1. Pick 1 machine/line with highest downtime pain
2. Install Pi + sensors (target: 1 day)
3. Start local monitoring immediately
4. Enable cloud sync when connected
5. Send weekly reports
6. Issue end-of-pilot ROI report
7. Convert qualified sites to paid pilot

---

## 10. Standards Alignment (Pilot Profile)

Where applicable, pilot telemetry and events should align with:

- Asset IDs: [`platform/asset-id-naming-convention.md`](https://github.com/oumar-code/Coo-Kah-Doks/blob/main/platform/asset-id-naming-convention.md)
- Topics: [`platform/mqtt-topic-schema.md`](https://github.com/oumar-code/Coo-Kah-Doks/blob/main/platform/mqtt-topic-schema.md)
- Data model: [`platform/digital-twin-data-model.md`](https://github.com/oumar-code/Coo-Kah-Doks/blob/main/platform/digital-twin-data-model.md)

Pilot implementations may use reduced subsets of these standards, but should not violate canonical field conventions (`factory_id`, `asset_id`, UTC timestamps).

---

*See also: [Strategy Overview](index.md) · [Pilot Offer](pilot-offer.md) · [90-Day Tracker](90-day-tracker.md)*
