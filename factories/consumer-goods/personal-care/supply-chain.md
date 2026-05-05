# Coo-Cah Personal Care Factory — Supply Chain Management

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Personal Care Factory | **Location:** Agbara Industrial Estate, Lagos State, Nigeria | **Phase:** Phase 1
> **Document Version:** 1.0 | **Owner:** Supply Chain & Procurement Team

---

## 1. Supply Chain Overview

| Supply Category                 | Origin                       | % of COGS | Lead Time    | Key Risk                         |
|---------------------------------|------------------------------|-----------|--------------|----------------------------------|
| Primary raw ingredients         | Local / Regional Africa      | 35–50%    | 1–4 weeks    | Crop / seasonal availability     |
| Active / functional ingredients | Import — EU / Asia           | 15–25%    | 6–10 weeks   | Forex; import permit              |
| Packaging — primary (bottles, pouches) | Import + Local       | 10–15%    | 2–6 weeks    | Primary packaging spec matching  |
| Packaging — secondary (cartons) | Local (Lagos suppliers)      | 5–8%      | 1–2 weeks    | Local print quality              |
| Fragrances + flavours           | Import — Givaudan/IFF        | 5–10%     | 4–8 weeks    | IP; sensory specs                |
| Preservatives + additives       | Import                       | 3–6%      | 4–8 weeks    | NAFDAC registration required     |
| Intra-group (Coo-Cah Plastics)  | Coo-Cah Plastics Factory     | 8–12%     | 1–2 days     | Internal capacity                |
| Labels, closures                | Import + Local               | 3–5%      | 2–4 weeks    |                                  |

---

## 2. Import Logistics

| Route                       | Mode        | Port of Entry    | Transit     | Notes                        |
|-----------------------------|-------------|------------------|-------------|------------------------------|
| Functional ingredients (EU) | Air Freight | Lagos MMIA       | 3–5 days    | High-value; NAFDAC pre-import |
| Ingredients (China/Asia)    | Sea LCL/FCL | Tin Can Island   | 22–28 days  | NAFDAC + NESREA notification |
| Fragrances (UK/France)      | Air Freight | Lagos MMIA       | 2–4 days    | Controlled substance docs     |
| Packaging materials         | Sea LCL     | Tin Can Island   | 22–28 days  | MOQ / batch matching         |

---

## 3. Intra-Group Supply Links

| Supplier                     | Component                        | Daily Volume    | Lead Time  |
|------------------------------|----------------------------------|-----------------|------------|
| Coo-Cah Plastics Factory     | Primary plastic packaging        | Per production  | 1–2 days   |
| Coo-Cah Chemicals — Plastics | PET preforms, closures           | Per production  | 1–2 days   |
| Coo-Cah Garage Power Elec.   | Inverter backup for cold chain   | On-request      | 1–2 days   |

---

## 4. Safety Stock Policy

| Item                         | Safety Stock  | Reorder Point | Rationale                      |
|------------------------------|---------------|---------------|--------------------------------|
| Primary raw ingredients      | 21 days       | 14 days       | Seasonal; local sourcing       |
| Active functional ingredients| 60 days       | 45 days       | Import lead time               |
| NAFDAC-registered additives  | 45 days       | 30 days       | Import permit lead time        |
| Packaging — primary          | 21 days       | 14 days       | Seasonal import batches        |
| Packaging — secondary (local)| 7 days        | 4 days        | Local; reliable                |

---

*Refer to [`regulatory.md`](./regulatory.md) for NAFDAC import documentation.*
*Refer to [`capex-opex.md`](./capex-opex.md) for feedstock cost modelling.*
