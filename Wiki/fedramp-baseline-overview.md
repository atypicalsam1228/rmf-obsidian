---
type: concept
framework: fedramp
status: draft
tags:
  - fedramp/baseline
  - fedramp/low
  - fedramp/moderate
  - fedramp/high
  - fedramp/li-saas
created: 2026-05-08
updated: 2026-05-08
sources:
  - "[[Sources/FedRAMP/fedramp-low-baseline]]"
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
  - "[[Sources/FedRAMP/fedramp-high-baseline]]"
  - "[[Sources/FedRAMP/fedramp-li-saas-baseline]]"
related:
  - "[[Wiki/fedramp-access-control]]"
  - "[[Wiki/fedramp-aws-config-conformance-packs]]"
  - "[[Wiki/fedramp-nist-800-53-relationship]]"
  - "[[Wiki/fedramp-vulnerability-management]]"
---

# FedRAMP Baseline Overview

> [!abstract] Summary
> FedRAMP defines four security baselines — Low, Moderate, High, and LI-SaaS — each representing a tailored subset of NIST 800-53 Rev 5 controls. The baseline determines the total control count, remediation SLAs, and continuous monitoring requirements a CSP must meet to achieve and maintain an ATO.

## Baseline Comparison

| Attribute | Low | LI-SaaS | Moderate | High |
|---|---|---|---|---|
| Controls | ~125 | ~36 | ~325 | ~421 |
| Typical use case | Public data, open data portals | Low-impact SaaS | Most federal business systems | Law enforcement, healthcare, financial |
| AWS Config rules | ~113 | — | ~129 | ~218 |
| Critical patch SLA | 30 days | 30 days | 30 days | 30 days |
| High vuln SLA | 90 days | 90 days | 90 days | 30 days |
| Moderate vuln SLA | 180 days | 180 days | 90 days | 90 days |

## Access Control Parameters (Moderate)

> [!quote] FedRAMP Moderate Baseline — AC-1
> "Review and update the current access control:
> 1. Policy [at least every 3 years] and following significant changes; and
> 2. Procedures [at least annually] and following significant changes."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AC-1 — Policy and Procedures|AC-1]]

> [!quote] FedRAMP Moderate Baseline — AC-2
> "Define and document the types of accounts allowed and specifically prohibited for use within the system; Assign account managers; Require prerequisites and criteria for group and role membership..."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AC-2 — Account Management|AC-2]]

## Key Distinctions by Level

### Low Baseline
- Targets systems where the loss of confidentiality, integrity, or availability would have **limited adverse effect**
- Minimal control enhancements; many controls satisfied by policy alone
- ConMon frequency requirements are least stringent

### LI-SaaS Baseline
- Special tailored baseline for low-impact Software-as-a-Service
- Significantly reduced control set (~36 controls) — CSP leverages agency ATO for shared responsibility
- Not available for systems processing sensitive PII or requiring high availability

### Moderate Baseline
- The **most common baseline** — applies to the majority of federal SaaS, PaaS, and IaaS authorizations
- 325+ controls with FedRAMP-specific parameter values overriding NIST defaults
- ConMon requires monthly OS/database scans, quarterly web application scans

### High Baseline
- Required for systems where compromise would have **severe or catastrophic effect**
- Includes all Moderate controls plus ~96 additional controls and enhancements
- Adds Inspector scanning, cross-region S3 replication, node-to-node encryption
- ConMon SLAs are tighter: high-severity findings must be remediated within 30 days

## FedRAMP Parameter Overrides

FedRAMP does not use NIST 800-53 defaults. All baselines define specific parameter values:

> [!info] Key Parameter Overrides (all levels)
> - Access key rotation: **90 days** (AC-2 related)
> - Password minimum length: **14 characters**
> - Password reuse prevention: **24 generations**
> - Max credential unused age: **90 days**
> - GuardDuty high-severity findings: must resolve within **1 day**
> - GuardDuty medium-severity: **7 days**
> - Backup retention minimum: **35 days**
> See: [[Wiki/fedramp-aws-config-conformance-packs]]

## Cross-Framework Mapping

> [!info] Cross-Framework
> - FedRAMP Moderate ≈ NIST 800-53 Moderate baseline with additional parameter constraints
> - FedRAMP High ≈ NIST 800-53 High baseline + FedRAMP-specific enhancements
> - NIST 800-171 maps to ~110 of the 800-53 controls used in FedRAMP Moderate
> - DoD IL2 ≈ FedRAMP Moderate; IL4/IL5 ≈ FedRAMP High + DISA SRG requirements
> See: [[Wiki/fedramp-nist-800-53-relationship]], [[Sources/FedRAMP/dod-srg-control-crosswalk-v1-0]]

## Related Notes

- [[Wiki/fedramp-access-control]]
- [[Wiki/fedramp-aws-config-conformance-packs]]
- [[Wiki/fedramp-vulnerability-management]]
- [[Wiki/fedramp-nist-800-53-relationship]]
