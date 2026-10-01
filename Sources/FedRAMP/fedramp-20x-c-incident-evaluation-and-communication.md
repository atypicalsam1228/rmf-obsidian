# FedRAMP 20x Class C — IEC: Incident Evaluation and Communication

**Source:** https://fedramp.gov/2026/reference/20x/c/incident-evaluation-and-communication/  
**Scraped:** 2026-08-03  
**Rules:** 8  
**Last Updated:** 2026-07-02

Legacy mapping: Replaces IR-6 1-hour major incident reporting requirement with PAIN-tiered reporting timeframes.

---

## Key Change: PAIN-Tiered Reporting Replaces Single 1-Hour SLA

Legacy FedRAMP Moderate required a single "major incident" initial report to FedRAMP PMO and US-CERT within 1 hour of detection, regardless of actual agency impact. FedRAMP 20x ties reporting timeframes to the PAIN rating — the estimated actual impact on federal agency customers.

**Default PAIN = 5 unless promptly estimated otherwise.** Providers who do not quickly estimate PAIN must treat every incident as the highest severity.

---

## Rules

### IEC-FRP-ORV: Ongoing Review (FedRAMP Responsibility)
FedRAMP must periodically review incident evaluation and communication implementation with providers. FedRAMP will request corrective action plans for unaware or non-compliant providers, allowing 3 months to remediate before possible certification revocation.

### IEC-CSO-EFR: Evaluate FedRAMP Reportability (MUST)
Providers must promptly evaluate incidents to determine if they affect confidentiality or integrity of federal customer data or "are likely to affect confidentiality or integrity of federal customer data."

### IEC-CSO-DPR: Default PAIN Rating (MUST)
"Providers MUST treat FedRAMP Reportable Incidents as if they have a Potential Agency Impact N-rating (PAIN) of 5 UNLESS they promptly estimate the PAIN rating."

### IEC-CSO-IIR: Initial Incident Report (MUST)
Providers must responsibly notify affected parties with initial reports including:
- Contact information
- Tracking identifier
- Incident description
- Timeline
- PAIN rating
- Functional impact
- Recovery plan
- Affected agencies

### IEC-CSO-OIR: Ongoing Incident Reports (MUST)
Providers must responsibly provide updates on observed activity, indicators of compromise, CVEs, root cause, and response activities.

### IEC-CSO-FIR: Final Incident Report (MUST)
Providers must responsibly notify parties once "the incident has been resolved and recovery is complete."

### IEC-CSO-EFI: Estimate Federal Impact (SHOULD)
Providers should promptly estimate adverse impact to assign PAIN ratings (N1-N5 scale) based on customer effect scope and severity.

### IEC-CSO-AIR: Automated Incident Reporting (SHOULD)
"Providers SHOULD use automation to minimize human intervention in the process of reporting FedRAMP Reportable Incidents."

---

## Incident Reporting Timeframes by PAIN Rating

| PAIN Rating | Description | Initial Report | Ongoing Report | Final Report |
|---|---|---|---|---|
| **N5** | Debilitating, multiple agencies | **1 hour** | **6 hours** | **6 hours** |
| **N4** | Debilitating 1 agency / disruptive multi | **1 hour** | **6 hours** | **6 hours** |
| **N3** | Disruptive, single agency | **1 hour** | **6 hours** | **6 hours** |
| **N2** | Narrow effect | **24 hours** | **24 hours** | **1 business day** |
| **N1** | Minimal effect | **1 business day** | **1 business day** | **1 business day** |

---

## Legacy Comparison

| Legacy FedRAMP Moderate IR-6 | FedRAMP 20x Class C IEC |
|---|---|
| Major incident: initial report within **1 hour** to FedRAMP PMO and US-CERT | PAIN-5/4/3: initial within **1 hour**; PAIN-2: 24 hours; PAIN-1: 1 business day |
| Single threshold for "major incident" | PAIN rating determines reportability and timeframe |
| US-CERT as notification endpoint | "Necessary parties" (agencies, FedRAMP) — US-CERT/CISA still applicable |
| No default severity assumption | Default PAIN = **5** unless quickly estimated otherwise |
| No automation requirement | **SHOULD** automate reporting |
