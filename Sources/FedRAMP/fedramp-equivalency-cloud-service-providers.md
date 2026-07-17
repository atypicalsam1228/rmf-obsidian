---
type: extracted-source
source_pdf: "[[Sources/DoD-Policy/fedramp-equivalency-cloud-service-providers.pdf]]"
pages: 3
extraction_method: vision
extracted: 2026-04-29
---

# FedRAMP Equivalency for Cloud Service Providers

**Source:** DoD CIO Memorandum  
**Date:** December 21, 2023  
**Signed by:** David W. McKeown, Deputy DoD CIO for Cybersecurity / DoD SISO

---

## Purpose

This memorandum establishes DoD policy on the use of FedRAMP-authorized Cloud Service Providers (CSPs) in the context of CMMC scoping and CUI protection requirements.

---

## Key Policy Requirement

CSPs that store, process, or transmit CUI on behalf of DoD contractors must meet **FedRAMP Moderate equivalency**. This means:

- All FedRAMP Moderate baseline security controls must be implemented and assessed.
- The assessment must be performed by a **FedRAMP-recognized Third Party Assessment Organization (3PAO)**.
- A valid FedRAMP Authority to Operate (ATO) at the Moderate baseline is the preferred mechanism for demonstrating equivalency.

---

## Equivalency Standard

For CSPs that are not FedRAMP authorized, DoD contractors may use a CSP if the CSP:

1. Meets **100% of FedRAMP Moderate security controls** (325 controls at the Moderate baseline)
2. Has been assessed by a **FedRAMP-recognized 3PAO**
3. Provides documentary evidence of compliance

---

## Required Evidence Package

When claiming FedRAMP Moderate equivalency, the following documentation is required:

| Document | Description |
|---|---|
| System Security Plan (SSP) | Full documentation of security control implementation |
| Security Assessment Plan (SAP) | Plan used by 3PAO for assessment |
| Security Assessment Report (SAR) | 3PAO findings and recommendations |
| Plan of Action & Milestones (POA&M) | Remediation tracking for any findings |

---

## CMMC Scoping Implications

- CSPs meeting FedRAMP Moderate equivalency are treated as **External Service Providers (ESPs)** in CMMC scoping.
- Contractors relying on such CSPs must verify the 3PAO assessment is current and covers all Moderate controls.
- CSPs with only a FedRAMP Low ATO do **not** satisfy this requirement for CUI storage/processing.

---

## Related References

- NIST SP 800-171 (CUI protection requirements that map to FedRAMP Moderate controls)
- 32 CFR Part 170 (CMMC Program Rule — scoping and ESP requirements)
- FedRAMP Program Management Office guidance
