---
type: guide
framework: fedramp
status: draft
tags:
  - fedramp
  - authorization
  - ato
  - 3pao
  - ssp
  - sar
  - sap
  - rar
created: 2026-05-08
updated: 2026-05-08
sources:
  - "[[Sources/FedRAMP/fedramp-rev5-authorization-playbook-agency]]"
  - "[[Sources/FedRAMP/fedramp-rev5-preparation-playbook-agency]]"
  - "[[Sources/FedRAMP/fedramp-rev5-ssp-playbook]]"
  - "[[Sources/FedRAMP/fedramp-rev5-sar-playbook]]"
  - "[[Sources/FedRAMP/fedramp-initial-authorization-package-checklist]]"
  - "[[Sources/FedRAMP/fedramp-high-readiness-assessment-report-rar-template]]"
  - "[[Sources/FedRAMP/fedramp-moderate-readiness-assessment-report-rar-template]]"
related:
  - "[[Wiki/fedramp-baseline-overview]]"
  - "[[Wiki/fedramp-continuous-monitoring]]"
  - "[[Wiki/fedramp-vulnerability-management]]"
  - "[[Wiki/dod-srg-cloud-impact-levels]]"
---

# FedRAMP Authorization Process

> [!abstract] Summary
> FedRAMP authorization follows a structured pathway: Preparation → Readiness Assessment (RAR) → Full Assessment (SSP + SAP + SAR) → Authorization (ATO or P-ATO) → Continuous Monitoring. Two paths exist: Agency Authorization (faster, one agency AO) and Joint Authorization Board (JAB) P-ATO (broader but slower). FedRAMP Rev5 and the emerging FedRAMP 20x process are changing how authorizations are structured.

> [!danger] NEEDS SOURCE: Playbook Content
> Most authorization playbook source files were extracted with 0 content (NotebookLM nav-only).
> See [[Sources/FedRAMP/fedramp-rev5-authorization-playbook-agency]], [[Sources/FedRAMP/fedramp-rev5-ssp-playbook]] — need re-ingestion.
> Content below is derived from baseline source files and the initial authorization package checklist.

## Authorization Paths

| Path | Sponsor | Outcome | Timeline |
|---|---|---|---|
| Agency Authorization | Federal agency AO | Agency ATO | 3–6 months (reuse) to 12–18 months (new) |
| JAB P-ATO | FedRAMP PMO (JAB) | Government-wide P-ATO | 12–24 months |
| FedRAMP 20x | TBD | Machine-readable authorization | Pilot phase |

## Phase 1: Preparation

The CSP prepares the authorization boundary, system categorization, and draft SSP before engaging a 3PAO.

**Key deliverables:**
- System boundary documentation
- Data flow diagrams
- Asset inventory
- Draft System Security Plan (SSP)
- Selection of a FedRAMP-recognized 3PAO

## Phase 2: Readiness Assessment (RAR)

The 3PAO conducts a readiness assessment before the full authorization to identify gaps. This is optional but strongly recommended for new CSPs.

> [!info] RAR Templates Available
> - [[Sources/FedRAMP/fedramp-high-readiness-assessment-report-rar-template]] — High baseline
> - [[Sources/FedRAMP/fedramp-moderate-readiness-assessment-report-rar-template]] — Moderate baseline

**RAR outcome:** FedRAMP-Ready designation listed in the FedRAMP Marketplace.

## Phase 3: Full Security Assessment

Four core documents must be completed:

### System Security Plan (SSP)
The SSP documents how each FedRAMP control is implemented. It defines control ownership (CSP-responsible, customer-responsible, or shared), implementation narratives, and system details.

> [!info] SSP Templates
> - [[Sources/FedRAMP/fedramp-high-moderate-low-li-saas-baseline-system-security-plan-ssp]] — combined template
> - Appendices: [[Sources/FedRAMP/ssp-appendix-a-moderate-fedramp-security-controls]], [[Sources/FedRAMP/ssp-appendix-a-high-fedramp-security-controls]]

### Security Assessment Plan (SAP)
The 3PAO develops the SAP to define the test methodology, scope, schedule, and test cases for the security assessment.

### Security Assessment Report (SAR)
The 3PAO documents assessment findings in the SAR. All test results, vulnerabilities, and risk ratings are recorded here.

> [!info] SAR Templates
> - [[Sources/FedRAMP/fedramp-security-assessment-report-sar-template]]
> - [[Sources/FedRAMP/fedramp-sar-appendix-b-moderate-security-requirements-traceability-matrix-template]]

### Plan of Action and Milestones (POA&M)
All open findings from the SAR are tracked in the POA&M with milestones for remediation.

> [!info] POA&M Template
> [[Sources/FedRAMP/fedramp-poam-template]]

## Phase 4: Authorization

### Agency ATO
A federal agency's Authorizing Official (AO) reviews the authorization package and issues an Authority to Operate. The CSP is listed in the FedRAMP Marketplace.

### JAB P-ATO
The Joint Authorization Board (representatives from DoD, DHS, GSA) reviews the package and issues a Provisional ATO that any agency can reuse.

> [!info] Reusing Authorizations
> Once a CSP has a FedRAMP ATO, other agencies can leverage it rather than conducting their own assessment.
> See: [[Sources/FedRAMP/reusing-authorizations-for-cloud-products-quick-guide]]

## Phase 5: Continuous Monitoring

After authorization, the CSP enters ongoing ConMon — monthly scans, POA&M updates, annual 3PAO reassessment.

See: [[Wiki/fedramp-continuous-monitoring]]

## Initial Authorization Package Checklist

> [!info] Package Contents
> The initial authorization package includes: SSP, SAP, SAR, POA&M, and supporting artifacts.
> See: [[Sources/FedRAMP/fedramp-initial-authorization-package-checklist]]

## FedRAMP 20x Authorization Changes

FedRAMP 20x is redesigning authorization to be faster and more automated:
- Machine-readable control implementations replacing narrative SSPs
- Continuous validation replacing point-in-time assessments
- CSP self-attestation with automated evidence collection
- Reduced 3PAO burden for lower-risk controls

## Cross-Framework Mapping

> [!info] Cross-Framework
> - **NIST 800-53:** CA-2 (Security Assessments), CA-6 (Authorization), CA-7 (ConMon), CA-5 (POA&M)
> - **DoD PA:** Builds on FedRAMP ATO — add FedRAMP+ controls to obtain DoD Provisional Authorization
> See: [[Wiki/dod-srg-cloud-impact-levels]]

## Related Notes

- [[Wiki/fedramp-baseline-overview]]
- [[Wiki/fedramp-continuous-monitoring]]
- [[Wiki/fedramp-vulnerability-management]]
- [[Wiki/dod-srg-cloud-impact-levels]]
