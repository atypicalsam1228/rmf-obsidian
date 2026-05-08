---
type: concept
framework: nist-800-171
status: draft
tags:
  - nist-800-171
  - cui
  - rev3
  - cmmc
  - dfars
created: 2026-05-08
updated: 2026-05-08
sources:
  - "[[Sources/NIST-800-171/nist-800-171r3-security-requirements]]"
  - "[[Sources/NIST-800-171/aws-config-nist-800-171-mappings]]"
related:
  - "[[Wiki/fedramp-nist-800-53-relationship]]"
  - "[[Wiki/nist-800-53-control-families]]"
  - "[[Wiki/dod-srg-cloud-impact-levels]]"
---

# NIST SP 800-171 Rev 3 — CUI Protection

> [!abstract] Summary
> NIST SP 800-171 Rev 3 (May 2024) specifies security requirements for protecting Controlled Unclassified Information (CUI) in nonfederal systems. It is the technical baseline for CMMC Level 2, required by DFARS clause 252.204-7012 for defense contractors, and the foundational standard for protecting sensitive DoD information outside classified systems.

## Overview

> [!quote] NIST 800-171 Rev 3 — Purpose
> "This publication provides recommended security requirements for protecting the confidentiality of Controlled Unclassified Information (CUI) when the information is resident in nonfederal systems and organizations. The requirements apply to nonfederal system components that process, store, transmit CUI, or protect such components."
> — [[Sources/NIST-800-171/nist-800-171r3-security-requirements]]

- **Rev 3 supersedes:** SP 800-171 Rev 2 (effective May 2024)
- **Requirement count:** 17 families, ~143 requirements
- **CUI scope:** Applies anywhere CUI is processed, stored, or transmitted — contractors, sub-contractors, cloud providers

## Requirement Families

| Family | ID | Key Requirements |
|---|---|---|
| Access Control | 03.01 | Account management, least privilege, session controls |
| Awareness and Training | 03.02 | Role-based training, literacy training |
| Audit and Accountability | 03.03 | Event logging, audit record review, time stamps |
| Configuration Management | 03.04 | Baseline config, change control, impact analysis |
| Identification and Authentication | 03.05 | Multi-factor auth, password management |
| Incident Response | 03.06 | Incident handling, reporting, testing |
| Maintenance | 03.07 | Controlled maintenance, remote maintenance |
| Media Protection | 03.08 | Media access, sanitization, transport |
| Personnel Security | 03.09 | Screening, termination, transfer |
| Physical Protection | 03.10 | Physical access controls |
| Risk Assessment | 03.11 | Risk assessments, vulnerability scanning |
| Security Assessment | 03.12 | Security control assessment, POA&M |
| System and Communications Protection | 03.13 | Boundary protection, encryption |
| System and Information Integrity | 03.14 | Malicious code, security alerts, patch management |
| Planning | 03.15 | System security plan |
| System and Services Acquisition | 03.16 | Supply chain risk management |
| Supply Chain Risk Management | 03.17 | SCRM plan, provenance |

## Key Access Control Requirements

> [!quote] NIST 800-171 Rev 3 — 03.01.05 Least Privilege
> "Allow only authorized system access for users (or processes acting on behalf of users) that is necessary to accomplish assigned organizational tasks."
> — [[Sources/NIST-800-171/nist-800-171r3-security-requirements#3.1 Access Control|03.01.05]]

> [!quote] NIST 800-171 Rev 3 — 03.01.06 Privileged Accounts
> "Restrict privileged accounts on the system to [organization-defined personnel or roles]. Require that users with privileged accounts use non-privileged accounts when accessing non-security functions."
> — [[Sources/NIST-800-171/nist-800-171r3-security-requirements#03.01.06 Least Privilege — Privileged Accounts|03.01.06]]

> [!quote] NIST 800-171 Rev 3 — 03.01.12 Remote Access
> "Establish usage restrictions, configuration requirements, and connection requirements for each type of allowable remote system access. Authorize each type of remote system access prior to establishing such connections."
> — [[Sources/NIST-800-171/nist-800-171r3-security-requirements#03.01.12 Remote Access|03.01.12]]

## Audit Requirements

> [!quote] NIST 800-171 Rev 3 — 03.03.02 Audit Record Content
> "Include the following content in audit records: what type of event occurred; when the event occurred; where the event occurred; source of the event; outcome of the event; identity of individuals, subjects, objects, or entities associated with the event."
> — [[Sources/NIST-800-171/nist-800-171r3-security-requirements#03.03.02 Audit Record Content|03.03.02]]

## Relationship to NIST 800-53

800-171 is derived from NIST 800-53 but scoped to CUI protection:
- 800-171 covers ~14 of 800-53's 20 families
- 800-171 requirements map 1:1 to 800-53 controls (e.g., 03.01.01 = AC-2)
- 800-171 uses organization-defined parameters — unlike FedRAMP which fixes them

## Relationship to CMMC

CMMC Level 2 = NIST 800-171 Rev 3 (110 practices from Rev 2 mapped to ~143 Rev 3 requirements). Defense contractors handling CUI must achieve CMMC Level 2 certification via a C3PAO assessment.

> [!info] DFARS 252.204-7012 Requirement
> All DoD contractors with CUI must implement 800-171 and report cyber incidents to DIBNET within 72 hours. CMMC 2.0 adds third-party assessment verification.

## AWS Implementation

> [!example] AWS Config Rules for 800-171
> AWS provides a conformance pack mapping to NIST 800-171:
> See: [[Sources/NIST-800-171/aws-config-nist-800-171-mappings]]
> Key mappings: IAM (03.01.x), CloudTrail (03.03.x), Config (03.04.x), Inspector/SSM (03.11.x, 03.14.x)

## Cross-Framework Mapping

> [!info] Cross-Framework
> - **NIST 800-53 Moderate:** 800-171 is a subset of ~110 800-53 controls relevant to CUI
> - **FedRAMP Moderate:** Substantial overlap — systems pursuing FedRAMP likely satisfy most 800-171 requirements
> - **CMMC Level 2:** Direct 1:1 mapping to 800-171 practices
> - **DoD IL4/IL5:** Requires 800-171 compliance + additional DoD SRG controls
> See: [[Wiki/fedramp-nist-800-53-relationship]], [[Wiki/dod-srg-cloud-impact-levels]]

## Related Notes

- [[Wiki/fedramp-nist-800-53-relationship]]
- [[Wiki/nist-800-53-control-families]]
- [[Wiki/dod-srg-cloud-impact-levels]]
