---
type: concept
framework: fedramp
status: draft
tags:
  - fedramp
  - section-508
  - accessibility
  - procurement
  - legal-requirements
  - ssp-appendix-l
created: 2026-05-18
updated: 2026-05-18
sources:
  - "[[Sources/FedRAMP/fedramp-high-moderate-low-li-saas-baseline-system-security-plan-ssp]]"
related:
  - "[[Wiki/fedramp-documentation-requirements]]"
  - "[[Wiki/fedramp-authorization-process]]"
  - "[[Wiki/fedramp-baseline-overview]]"
---

# Section 508 and FedRAMP Compliance

> [!abstract] Summary
> Section 508 of the Rehabilitation Act is NOT a FedRAMP security control — it does not appear in NIST 800-53 baselines, the FedRAMP control catalog, or the ATO package checklist. However, it is a hard statutory requirement enforced through federal procurement law (FAR 39.2). CSPs selling to federal agencies will effectively be required to provide a VPAT/ACR as a condition of contract award, even though FedRAMP itself does not audit or validate Section 508 compliance.

> [!danger] NEEDS SOURCE: Section 508 / FedRAMP Official Guidance
> No FedRAMP source document addressing Section 508 has been ingested. Ingest the FedRAMP Laws and Regulations document from fedramp.gov/documents-templates to add an authoritative source. Content below is derived from policy knowledge and the SSP Appendix L template.

## Is Section 508 a FedRAMP Requirement?

**No.** Section 508 is not a FedRAMP security control. A system can be fully FedRAMP Authorized and still not comply with Section 508. The FedRAMP PMO does not validate or audit Section 508 compliance as part of the ATO process.

Section 508 is a **statutory requirement** under the Rehabilitation Act (29 U.S.C. § 794d), enforced through acquisition law — not security authorization.

## Where It Appears in FedRAMP Documentation

> [!quote] FedRAMP SSP Template — Appendix L
> "If the CSO is governed by CSP or agency-specific laws and regulations, these should be listed below. If there are no CSO-specific governing laws or regulations, simply state 'N/A'."
> — [[Sources/FedRAMP/fedramp-high-moderate-low-li-saas-baseline-system-security-plan-ssp]]

Section 508 belongs in **SSP Appendix L** (CSO-Specific Required Laws and Regulations) if the agency or CSP determines it applies to their deployment. It is not pre-populated as a baseline FedRAMP requirement — the CSP or agency must assess applicability and declare it.

## Who It Applies To

| Party | Obligation | Legal Basis |
|---|---|---|
| **Federal agencies** | Must ensure all IT they develop, procure, maintain, or use is accessible to people with disabilities | Rehabilitation Act § 508 (29 U.S.C. § 794d) |
| **CSPs selling to agencies** | Must provide accessible products or document exceptions — required by agency contract, not FedRAMP | FAR 39.2 / agency procurement clauses |
| **CSP internal systems** | Only if the CSP is itself a federal contractor subject to Section 508 | Contract-specific |

## Platform vs. Customer Responsibility Split

| Layer | Responsible Party |
|---|---|
| CSP management console, APIs, user-facing interfaces used by agency staff | CSP/Platform |
| Agency-built applications deployed on top of the platform | Agency customer |
| Shared dashboards and data management portals used by agency employees | Shared — defined in CIS/CRM Workbook |

## Practical Impact for CSPs

Section 508 is effectively mandatory for federal sales even without FedRAMP enforcement, because:

1. **FAR 39.2** requires agencies to include Section 508 clauses in all IT acquisition contracts
2. **Agency contracting officers** require a **VPAT / ACR** (Accessibility Conformance Report against WCAG 2.1 AA) before contract award
3. **Agency AOs** may list Section 508 in SSP Appendix L as an applicable law for their specific deployment

> [!tip] VPAT / ACR
> The Voluntary Product Accessibility Template (VPAT), now called Accessibility Conformance Report (ACR), is the standard document CSPs use to self-declare Section 508 conformance. It maps product features against the WCAG 2.1 AA criteria and the Revised 508 Standards (36 CFR Part 1194). Agencies use it to evaluate accessibility before procurement.

## Technical Standard

The 2018 refresh of Section 508 standards (36 CFR Part 1194) aligns with **WCAG 2.1 Level AA** as the technical conformance target for web content and software.

## Relationship to FedRAMP Authorization Stack

> [!info] Cross-Framework Note
> Section 508 sits entirely outside the NIST RMF / FedRAMP security authorization stack. It is enforced through **acquisition law (FAR)**, not through NIST 800-53 controls. No NIST 800-53 Rev 5 control directly maps to Section 508 accessibility requirements. The closest controls are informational — SA-4 (Acquisition Process) may reference accessibility requirements in contract language, but Section 508 compliance itself is not assessed by a 3PAO.

## Summary

| Question | Answer |
|---|---|
| Is Section 508 a FedRAMP control? | No |
| Does FedRAMP audit Section 508? | No |
| Can you get a FedRAMP ATO without Section 508 compliance? | Yes |
| Is Section 508 required to sell to federal agencies? | Yes — through FAR 39.2 and agency contracts |
| Where does it appear in the FedRAMP package? | SSP Appendix L (if applicable to the deployment) |
| Who enforces it? | Agency contracting officers, not the FedRAMP PMO |
| Technical standard | WCAG 2.1 Level AA (36 CFR Part 1194) |
