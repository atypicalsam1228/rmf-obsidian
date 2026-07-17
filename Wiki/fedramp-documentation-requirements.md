---
type: guide
framework: fedramp
status: draft
tags:
  - fedramp
  - authorization
  - documentation
  - ssp
  - sar
  - sap
  - poam
  - conmon
  - package-submission
created: 2026-05-13
updated: 2026-05-13
sources:
  - "[[Sources/FedRAMP/fedramp-initial-authorization-package-checklist]]"
  - "[[Sources/FedRAMP/fedramp-continuous-monitoring-deliverables-template]]"
  - "[[Sources/FedRAMP/fedramp-security-assessment-report-sar-template]]"
related:
  - "[[Wiki/fedramp-authorization-process]]"
  - "[[Wiki/fedramp-continuous-monitoring]]"
  - "[[Wiki/fedramp-baseline-overview]]"
---

# FedRAMP Documentation Requirements

> [!abstract] Summary
> FedRAMP requires a defined set of authorization package documents (SSP, SAP, SAR, POA&M + appendices), submitted to MAX.gov for the initial package. Ongoing ConMon deliverables go to the AO via a designated repository (agency-defined). CSPs maintain their own secure repository for auxiliary evidence. High systems coordinate directly with the FedRAMP PMO.

## Initial Authorization Package

> [!quote] FedRAMP Initial Authorization Package Checklist
> "Do not submit password-protected files for Low and Moderate systems. For High systems, coordinate the package submission with the FedRAMP PMO."
> Column header: **"File Uploaded to MAX (Y/N)?"**
> — [[Sources/FedRAMP/fedramp-initial-authorization-package-checklist]]

### System Security Plan (SSP) — CSP Authored

| Document | FedRAMP Template Required? |
|---|---|
| System Security Plan (SSP) | Yes — Word (PDF only after ATO) |
| Appendix A — FedRAMP Security Controls | Yes — Word |
| Appendix B — Related Acronyms | Included within SSP |
| Appendix C — Security Policies and Procedures (all control families) | No (CSP-authored) |
| Appendix D — User Guide | No |
| Appendix E — Digital Identity Worksheet | Included within SSP |
| Appendix F — Rules of Behavior | Yes — Word |
| Appendix G — Information System Contingency Plan (ISCP) | Yes — Word |
| Appendix H — Configuration Management Plan (CMP) | No |
| Appendix I — Incident Response Plan (IRP) | No |
| Appendix J — CIS and CRM Workbook | Yes — Excel |
| Appendix K — FIPS 199 Worksheet | Included within SSP |
| Appendix L — CSO-Specific Required Laws and Regulations | Included within SSP |
| Appendix M — Integrated Inventory Workbook | Yes — Excel |
| Appendix N — Continuous Monitoring Plan (must include ConMon Strategy + Monthly Executive Summary) | No |
| Appendix O — POA&M | Yes — Excel |
| Appendix P — Supply Chain Risk Management Plan (SCRMP) | No |
| Appendix Q — Cryptographic Modules Table | Yes — Word |

### Security Assessment Plan (SAP) — 3PAO Authored

| Document | FedRAMP Template Required? |
|---|---|
| SAP | Yes — Word (PDF after ATO) |
| Appendix A — Controls Selection Worksheet (if applicable) | Yes — Excel |
| Appendix B — Sampling Methodology (if applicable) | No |
| Appendix C — Penetration Testing Plan and Methodology | No |
| Appendix D — Significant Change Request Documentation (if applicable) | No |

### Security Assessment Report (SAR) — 3PAO Authored

| Document | FedRAMP Template Required? |
|---|---|
| SAR | Yes — Word (PDF after ATO) |
| Appendix A — Risk Exposure Table | Yes — Excel |
| Appendix B — Security Requirements Traceability Matrix (SRTM) Workbook | Yes — Excel |
| Appendix C — Vulnerability Scan Results (OS, Container, DB, Web — raw + human readable, bundled zip) | No |
| Appendix F — Penetration Test Report | No |
| Appendix E — Auxiliary Documents (if applicable) | No |

### Agency ATO Letter
- FedRAMP template in Word; submitted as **PDF**
- Required for agency packages only

### Format Rules
- **Word format required** for initial SSP, SAP, SAR submissions where FedRAMP template is mandated
- **PDF allowed only after** FedRAMP Authorized designation is achieved
- **High systems**: coordinate directly with FedRAMP PMO — no self-submission to MAX

---

## Where Documentation Must Be Kept

### Initial Authorization Package → MAX.gov

> [!quote] FedRAMP Initial Authorization Package Checklist
> "File Uploaded to MAX (Y/N)?"
> — [[Sources/FedRAMP/fedramp-initial-authorization-package-checklist]]

The initial authorization package is submitted to **MAX.gov** (OMB MAX Collect) — the federal government's secure package portal managed by the FedRAMP PMO.

- Low/Moderate: Upload directly to MAX
- High: Coordinate submission with FedRAMP PMO

### Continuous Monitoring Deliverables → AO-Designated Repository

> [!quote] FedRAMP ConMon Deliverables Template
> "Submitted to the AO via the designated repository."
> Applies to: Monthly Executive Summary, vulnerability scans, POA&M, inventory, SAP, SAR, pen test reports, contingency plan tests, incident response test results.
> — [[Sources/FedRAMP/fedramp-continuous-monitoring-deliverables-template]]

FedRAMP does **not** prescribe a specific product. The AO designates the repository. Common implementations:

| Implementation | Context |
|---|---|
| MAX.gov | Legacy / JAB P-ATO systems |
| Agency SharePoint / GovCloud | Agency ATOs |
| FedRAMP Secure Repository | Post-Rev5 newer authorizations |

### Auxiliary Evidence → CSP Secure Repository

> [!quote] FedRAMP SAR Template
> "Auxiliary documents must be readily available to reviewers via a CSP's secure repository."
> — [[Sources/FedRAMP/fedramp-security-assessment-report-sar-template]]

The CSP maintains its own internal secure repository for evidence artifacts — raw scan files, auxiliary docs — accessible to AO reviewers and the 3PAO on demand.

### Summary Table

| Document Type | Location |
|---|---|
| Initial authorization package | MAX.gov (FedRAMP PMO portal) |
| High system packages | Coordinated directly with FedRAMP PMO |
| Monthly ConMon deliverables | AO's designated repository (agency-defined) |
| SSP + supporting docs (annual update) | Submitted to 3PAO ≥30 days before annual assessment |
| Auxiliary evidence artifacts | CSP's own secure repository |

> [!danger] NEEDS SOURCE: Designated Repository Definition
> FedRAMP does not formally define "designated repository" in ingested sources — the term is intentionally flexible. Re-ingest the FedRAMP Rev5 Authorization Playbook (agency) once a full-text version is available for authoritative guidance.

---

## Continuous Monitoring Deliverable Frequency

| Deliverable | Frequency |
|---|---|
| ConMon Monthly Executive Summary | Monthly |
| Vulnerability & Configuration Scans | Monthly |
| POA&M update | Monthly |
| Inventory update | Monthly |
| Contingency Plan Test (Moderate/High) | Annually (functional) |
| Contingency Plan Test (Low) | Every 3 years (tabletop) |
| Incident Response Test (Moderate) | Annually |
| Incident Response Test (High) | Every 6 months (functional annually) |
| SAP | Annually |
| SAR + Pen Test | Annually |
| SSP update to 3PAO | 30 days before annual assessment |

> [!info] Cross-Framework Mapping
> - **NIST 800-53:** CA-2 (Security Assessments), CA-5 (POA&M), CA-6 (Authorization), CA-7 (ConMon), PL-2 (SSP), SA-5 (System Documentation)
> - **DoD SRG:** FedRAMP package is the foundation for DoD PA; same repository submission applies
> See: [[Wiki/fedramp-authorization-process]], [[Wiki/fedramp-continuous-monitoring]]
