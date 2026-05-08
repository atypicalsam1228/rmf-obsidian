---
type: concept
framework: nist-800-53
status: draft
tags:
  - nist-800-53
  - control-families
  - rev5
created: 2026-05-08
updated: 2026-05-08
sources:
  - "[[Sources/NIST-800-53/nist-800-53r5-catalog]]"
  - "[[Sources/NIST-800-53/nist-sp-800-53r5-full]]"
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
related:
  - "[[Wiki/fedramp-nist-800-53-relationship]]"
  - "[[Wiki/fedramp-access-control]]"
  - "[[Wiki/nist-ai-rmf-core-functions]]"
---

# NIST 800-53 Rev 5 Control Families

> [!abstract] Summary
> NIST SP 800-53 Rev 5 organizes its controls into 20 families. Each family groups related security and privacy controls. FedRAMP selects from these families for its baselines, adding specific parameter values. This article maps each family to its purpose, control count range, and key controls relevant to FedRAMP.

## Control Family Reference

> [!quote] NIST 800-53 Rev5 — Control Families
> The catalog includes 20 control families organized by security domain.
> — [[Sources/NIST-800-53/nist-800-53r5-catalog]]

| ID | Family | Key Controls | FedRAMP Focus |
|---|---|---|---|
| AC | Access Control | AC-2, AC-3, AC-6, AC-17 | High — all levels |
| AT | Awareness and Training | AT-2, AT-3 | Required all levels |
| AU | Audit and Accountability | AU-2, AU-6, AU-9, AU-12 | High — logging |
| CA | Assessment, Authorization, Monitoring | CA-2, CA-5, CA-7, CA-8 | ConMon, 3PAO |
| CM | Configuration Management | CM-2, CM-6, CM-7, CM-8 | Hardening, inventory |
| CP | Contingency Planning | CP-2, CP-9, CP-10 | Backup, recovery |
| IA | Identification and Authentication | IA-2, IA-5, IA-8 | MFA, passwords |
| IR | Incident Response | IR-4, IR-5, IR-6 | Reporting, handling |
| MA | Maintenance | MA-2, MA-4, MA-5 | Maintenance windows |
| MP | Media Protection | MP-2, MP-6 | Storage sanitization |
| PE | Physical and Environmental | PE-3, PE-6 | Datacenter (IaaS) |
| PL | Planning | PL-2, PL-8 | SSP, security arch |
| PM | Program Management | PM-9, PM-30 | Risk mgmt program |
| PS | Personnel Security | PS-3, PS-6, PS-7 | Clearance, agreements |
| PT | PII Processing and Transparency | PT-1 through PT-8 | Privacy (Rev 5 new) |
| RA | Risk Assessment | RA-3, RA-5, RA-7 | Vuln scanning |
| SA | System and Services Acquisition | SA-4, SA-9, SA-12 | Supply chain |
| SC | System and Communications Protection | SC-7, SC-8, SC-28 | Encryption, network |
| SI | System and Information Integrity | SI-2, SI-3, SI-4, SI-7 | Patches, AV, SIEM |
| SR | Supply Chain Risk Management | SR-3, SR-5, SR-10 | Rev 5 new — SCRM |

## High-Priority Families for FedRAMP

### AC — Access Control
Most scrutinized family. FedRAMP specifies exact parameter values for all AC controls.
See: [[Wiki/fedramp-access-control]]

### AU — Audit and Accountability

> [!quote] NIST 800-53 Rev5 — AU-2
> "a. Identify the types of events that the system is capable of logging in support of the audit function; and b. Coordinate the event logging function with other organizations requiring audit-related information to guide and inform the selection criteria for events to be logged."
> — [[Sources/NIST-800-53/nist-800-53r5-catalog#AU-2|AU-2]]

> [!example] AWS Implementation — AU
> - **CloudTrail** — management and data events (AU-2, AU-12)
> - **CloudWatch Logs** — log aggregation and retention (AU-9, AU-11)
> - **Config rules:** `cloudtrail-enabled`, `cloud-trail-encryption-enabled`, `cloud-trail-log-file-validation-enabled`, `cloudwatch-log-group-encrypted`

### RA — Risk Assessment

> [!quote] NIST 800-53 Rev5 — RA-5 (excerpt)
> "Monitor and scan for vulnerabilities in the system and hosted applications [at defined frequencies]; Employ vulnerability monitoring tools and techniques; Analyze vulnerability scan reports and results; Remediate legitimate vulnerabilities within defined time periods..."
> — [[Sources/NIST-800-53/nist-800-53r5-catalog#RA-5|RA-5]]

See: [[Wiki/fedramp-vulnerability-management]]

### SC — System and Communications Protection

Key controls for encryption and network security. FedRAMP requires encryption in transit (SC-8) and at rest (SC-28) for all Moderate and High systems.

> [!example] AWS Implementation — SC
> - **EBS encryption by default** (`ec2-ebs-encryption-by-default`) — SC-28
> - **S3 KMS encryption** (`s3-default-encryption-kms`) — SC-28
> - **TLS enforcement** on ELB, API Gateway, RDS — SC-8
> - **VPC with security groups** (`ec2-instances-in-vpc`) — SC-7

### SI — System and Information Integrity

> [!quote] NIST 800-53 Rev5 — SI-2 (excerpt)
> "a. Identify, report, and correct system flaws; b. Test software and firmware updates related to flaw remediation for effectiveness and potential side effects before installation; c. Install security-relevant software updates within organization-defined time periods..."
> — [[Sources/NIST-800-53/nist-800-53r5-catalog#SI-2|SI-2]]

## Rev 5 New Additions

> [!info] What's New in Rev 5
> - **PT family** (PII Processing and Transparency) — privacy controls now integrated
> - **SR family** (Supply Chain Risk Management) — dedicated SCRM family
> - Outcome-based language — "what" not "how"
> - ~200 new controls and enhancements vs Rev 4
> - References to EO 14028 (Cybersecurity EO) guidance incorporated

## Cross-Framework Mapping

> [!info] Cross-Framework
> - **NIST 800-171:** derived from 800-53, covering 14 families protecting CUI
> - **FedRAMP:** uses all 20 families; adds FedRAMP-specific parameter overrides
> - **CMMC Level 2:** aligns to 800-171 (subset of 800-53)
> - **ISO 27001:** rough mapping — AC≈A.9, AU≈A.12.4, SC≈A.10/A.13, SI≈A.12.6

## Related Notes

- [[Wiki/fedramp-nist-800-53-relationship]]
- [[Wiki/fedramp-access-control]]
- [[Wiki/fedramp-vulnerability-management]]
- [[Wiki/nist-ai-rmf-core-functions]]
