# FedRAMP 20x Class C — CCM: Collaborative Continuous Monitoring

**Source:** https://fedramp.gov/2026/reference/20x/c/collaborative-continuous-monitoring/  
**Scraped:** 2026-08-03  
**Rules:** 19  
**Last Updated:** 2026-06-24

Legacy mapping: Replaces monthly ConMon deliverables to FedRAMP PMO and the traditional annual 3PAO continuous monitoring assessment. Shifts from PMO-centric reporting to CSP-to-agency direct transparency.

---

## Core Model Change

Legacy FedRAMP ConMon: CSP submits monthly deliverables (vulnerability scan results, POA&M updates) to FedRAMP PMO. FedRAMP PMO reviews and distributes to agencies.

FedRAMP 20x CCM: CSP delivers **quarterly Ongoing Certification Reports** and hosts **quarterly review meetings** directly to all necessary parties (agencies, FedRAMP, assessors). No monthly PMO submission.

---

## Agency Guidance Rules

### CCM-AGM-ROR: Review Ongoing Reports (MUST — ongoing)
Agencies must examine each Ongoing Certification Report to assess how service changes affect previously authorized risk tolerance.

### CCM-AGM-CSC: Consider Security Category (SHOULD — ongoing)
Agencies should allocate appropriate resources based on their system's Security Category for reviewing reports and attending meetings.

---

## Ongoing Certification Reports

### CCM-OCR-AVL: Report Availability (MUST — quarterly)
Providers must deliver comprehensive reports to all necessary parties **every 3 months** covering:
- Certification data changes
- Planned modifications
- Accepted vulnerabilities
- Transformative changes
- Recommendations
- Agency user lists
- Incidents
- Lessons learned

### CCM-OCR-NRD: Next Report Date (MUST — with each report)
Providers must publicly disclose their next report target date alongside certification data.

### CCM-OCR-FBM: Feedback Mechanism (MUST — continuous)
Providers must enable asynchronous feedback channels for stakeholders.

### CCM-OCR-AFS: Anonymized Feedback Summary (MUST — quarterly)
Providers must compile anonymized feedback as a report addendum or in the subsequent reporting period.

### CCM-OCR-LSI: Limit Sensitive Information (MUST — per report)
Providers must avoid irresponsible disclosure of sensitive competitive information in reports.

### CCM-OCR-SOR: Spread Out Reports (SHOULD — quarterly)
Providers should stagger report releases across the beginning, middle, or end of each quarter.

### CCM-OCR-RPS: Responsible Public Sharing (MAY — follows report release)
Providers may publicly share report content if no adverse effects are likely.

---

## Quarterly Review Meetings

### CCM-QTR-MTG: Quarterly Review Meeting (MUST — Class C — every 3 months)
Class C providers must host **synchronous quarterly meetings** open to all stakeholders.

### CCM-QTR-REG: Meeting Registration Info (MUST — prior to each meeting)
Providers must supply registration links or calendar files to all necessary parties.

### CCM-QTR-NRD: Next Review Date (MUST — continuous)
Providers must publicly post upcoming meeting dates with certification data.

### CCM-QTR-NID: No Irresponsible Disclosure (MUST — per meeting)
Providers must avoid sensitive disclosures during meetings that could harm operations.

### CCM-QTR-SAR: Schedule Around Reports (SHOULD — quarterly)
Providers should schedule meetings **3–10 business days after** report release.

### CCM-QTR-ACT: Additional Content (MAY — quarterly meetings)
Providers may include supplementary relevant information during meetings.

### CCM-QTR-RTR: Record/Transcribe Reviews (SHOULD — following each meeting)
Providers should record or transcribe meetings for distribution.

### CCM-QTR-RTP: Restrict Third Parties (SHOULD — per meeting)
Providers should limit third-party attendance unless directly relevant.

### CCM-QTR-SCR: Share Content Responsibly (MAY — post meeting)
Providers may publicly distribute meeting materials if no operational harm is anticipated.

---

## Legacy Comparison

| Legacy FedRAMP Moderate ConMon | FedRAMP 20x Class C CCM |
|---|---|
| Monthly deliverables to FedRAMP PMO | **Quarterly** Ongoing Certification Reports to all stakeholders |
| Vulnerability scan results monthly | Vulnerability data in reports quarterly + JSON every 14 days (recommended) |
| POA&M submitted monthly to PMO | Agencies maintain their own POA&M using provider data |
| Annual 3PAO assessment | Annual independent assessment (see IVV ruleset) |
| No formal stakeholder meeting required | **Mandatory quarterly review meeting** open to all stakeholders (Class C) |
| FedRAMP PMO as intermediary | Direct CSP-to-agency transparency |
