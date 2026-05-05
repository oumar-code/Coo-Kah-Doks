# Security Electronics Factory — Regulatory Compliance

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Security Electronics Factory | **Location:** Ikorodu Industrial Estate, Lagos State | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Regulatory Affairs & Quality Team

---

## 1. Regulatory Framework Summary

| Regulatory Body       | Jurisdiction                        | Key Requirement                                              | Criticality |
|-----------------------|-------------------------------------|--------------------------------------------------------------|-------------|
| NCC                   | Wi-Fi, BT, Zigbee cameras + NVRs    | Type Approval before sale                                    | **Critical** |
| SON                   | All manufactured products           | NIS product registration + certification                     | **Critical** |
| ONVIF (Industry Std.) | All IP cameras + NVRs + intercoms   | ONVIF Profile S / T conformance required for enterprise sales| **Critical** |
| NESREA                | Environmental                       | EIA; e-waste (electronic equipment) scheme                   | High        |
| NCS                   | Imports (CMOS sensors, SoCs)        | Form M; SON CoC; HS code                                     | High        |
| Ministry of Labour    | Worker safety                       | Factories Act; ESD safety; cleanroom protocols               | High        |
| Lagos State Govt      | Building + operations               | Building permit; Lagos EIA; operational licence               | High        |
| IEC (International)   | Product safety                      | IEC 62368-1; IEC 60839 (alarm systems); IEC 62676 (video)    | High        |
| GDPR / NDPR (privacy) | AI NVR facial recognition           | Nigeria Data Protection Regulation compliance in product design| Medium     |

---

## 2. NCC Type Approval — Scope

All wireless security electronics products require NCC Type Approval. This factory covers:

| Product                            | Radio Tech                       | NCC TA Standards                    |
|------------------------------------|----------------------------------|-------------------------------------|
| IP Security Cameras (Wi-Fi models) | Wi-Fi 802.11b/g/n                | NCC TA; Wi-Fi type approval         |
| NVR (Wi-Fi / Cloud-connected)      | Wi-Fi + cloud                    | NCC TA; Wi-Fi                       |
| Access Control (Wi-Fi / TCP/IP)    | Wi-Fi (optional)                 | NCC TA (if Wi-Fi enabled)           |
| Alarm Panel (GSM + IP)             | GSM 4G + Wi-Fi                   | NCC TA (GSM + Wi-Fi)               |
| Video Intercom (Wi-Fi + IP)        | Wi-Fi 802.11n                    | NCC TA; Wi-Fi type approval         |

---

## 3. ONVIF Conformance Requirements

ONVIF (Open Network Video Interface Forum) is the global industry standard for IP-based security products. Enterprise buyers (banks, government, corporates) require ONVIF conformance. Coo-Cah targets ONVIF Profile S (basic IP camera + NVR) and Profile T (advanced, H.265, analytics).

| ONVIF Profile | Scope                                     | Products Covered                          |
|---------------|-------------------------------------------|-------------------------------------------|
| Profile S     | Basic RTSP streaming; PTZ; events         | All IP cameras; all NVRs                  |
| Profile T     | H.265; HTTPS; TLS; video analytics        | 5MP+ IP cameras; AI NVR; 16-ch NVR       |
| Profile G     | Edge storage (on-camera SD)               | Phase 2 — evaluate for future camera SKUs|
| Profile A     | Access control management                 | Access control panels (CCX-ACS-CTRL)      |

**ONVIF Certification Process:**
1. Implement ONVIF Device Service on firmware
2. Run ONVIF Device Test Tool (DTT) internally
3. Submit to ONVIF-accredited test lab for conformance testing
4. ONVIF Certificate of Conformance issued (specific profile, firmware version)
5. MES ONVIF Module: certificate loaded; production shipment gate enforced

---

## 4. IEC 62676 — Video Surveillance Systems

IEC 62676 is the international standard series for video surveillance systems. Key parts applicable to Coo-Cah:

| Standard Part       | Scope                                   | Key Tests                                   |
|---------------------|-----------------------------------------|---------------------------------------------|
| IEC 62676-1-1       | System requirements — analog + IP       | Video compression; network performance       |
| IEC 62676-2-3       | IP cameras — video performance          | Resolution; sensitivity; dynamic range       |
| IEC 62676-4         | Application guidelines                  | Referenced in enterprise tender specs        |

---

## 5. Nigeria Data Protection Regulation (NDPR) — AI NVR

The AI NVR product (CCX-AI-NVR) includes facial recognition capabilities. Under the NDPR (2019) and the Data Protection Act 2023, Coo-Cah must:

1. Include a privacy notice in the product user manual and packaging
2. Provide configurable consent management in the NVR software
3. Enable facial data anonymisation / audit log on/off
4. Not store biometric data on the device without end-user consent (by default: local inference only; cloud sync requires explicit consent)
5. Include a GDPR-compatible privacy assessment in the product technical file

---

## 6. SON NIS Certification Schedule

| Product                 | Standard                         | Target Certification |
|-------------------------|----------------------------------|----------------------|
| IP Cameras (all models) | NIS / IEC 62368-1 + IEC 62676-2  | Q2 2026              |
| NVRs / DVRs             | NIS / IEC 62368-1 + IEC 62676-1  | Q2 2026              |
| Access Control          | NIS / IEC 60839-11-1             | Q3 2026              |
| Alarm Panels            | NIS / IEC 60839-11-1             | Q3 2026              |
| Video Intercom          | NIS / IEC 62368-1 + NCC TA       | Q3 2026              |

---

## 7. Compliance Calendar

| Obligation                    | Frequency | Deadline           | Responsible         |
|-------------------------------|-----------|--------------------|---------------------|
| NCC TA renewals               | Every 5yr | Certificate expiry | Regulatory Affairs  |
| ONVIF recertification (FW change) | Per major FW update | TBD     | Regulatory + Tech   |
| SON NIS audit                 | Annual    | Product anniversary| Regulatory Affairs  |
| NESREA EIA review             | Biennial  | Every 2 years      | EHS Officer         |
| ISO 9001 surveillance audit   | Annual    | Certification body | QA Manager          |
| NDPR annual review            | Annual    | Product data review| Legal + Tech        |
| FIRS tax filing               | Annual    | 30 June            | Finance             |
