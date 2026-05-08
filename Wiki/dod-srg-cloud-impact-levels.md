---
type: concept
framework: cross-framework
status: draft
tags:
  - dod-srg
  - fedramp
  - impact-levels
  - dod-pa
  - fedramp-plus
  - il2
  - il4
  - il5
  - il6
created: 2026-05-08
updated: 2026-05-08
sources:
  - "[[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg]]"
  - "[[Sources/FedRAMP/dod-srg-control-crosswalk-v1-0]]"
related:
  - "[[Wiki/fedramp-baseline-overview]]"
  - "[[Wiki/fedramp-nist-800-53-relationship]]"
  - "[[Wiki/nist-800-171-cui-protection]]"
---

# DoD Cloud Impact Levels and FedRAMP+

> [!abstract] Summary
> The DoD Cloud Computing Security Requirements Guide (CSP SRG V1R6, DISA, December 2025) defines Information Impact Levels (IL2–IL6) that determine which cloud services DoD can use for which data. FedRAMP+ extends FedRAMP authorizations with DoD-specific controls. CSPs must obtain a DoD Provisional Authorization (PA) in addition to a FedRAMP ATO to host DoD missions.

## The DoD CSP SRG

> [!quote] CSP SRG V1R6 — Purpose
> "The Cloud Service Provider SRG provides the security controls and requirements necessary for cloud service providers (CSPs) who wish to provide their cloud-based solutions to Department of Defense (DOD) Mission Owners...This Cloud Service Provider SRG, in support of DODI 8510.01, establishes the DOD security objectives to host DOD mission applications and DOD information in internal and external IT services."
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg#1. Introduction|Section 1]]

## Information Impact Levels

> [!quote] CSP SRG V1R6 — Impact Level Overview
> "The sensitivity of the DOD information may range from publicly releasable up to and including SECRET. Missions above SECRET must follow existing applicable DOD policies and are not covered by this Cloud Service Provider SRG."
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg#1.1 Executive Summary|Section 1.1]]

| Level | Data Type | FedRAMP Equivalence | Key Additional Requirements |
|---|---|---|---|
| IL2 | Publicly releasable, non-CUI | FedRAMP Moderate | DoD PA required |
| IL4 | CUI (Controlled Unclassified Information) | FedRAMP Moderate + FedRAMP+ | DISA STIG compliance, CAP connectivity |
| IL5 | CUI-sensitive / unclassified NSS | FedRAMP High + FedRAMP+ | Exclusive DoD use, DISA CAP required |
| IL6 | Classified information up to SECRET | Not covered by FedRAMP | SIPRNet connectivity, special handling |

## IL2 — Non-CUI Public Data

> [!quote] CSP SRG V1R6 — IL2
> "Impact Level 2: Noncontrolled Unclassified Information — Information that is not subject to CUI designations but is not intended for public release. May include information related to unclassified DOD programs, operations, or administrative matters."
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg#3.7.1 Impact Level 2|3.7.1]]

- Minimum: FedRAMP Moderate ATO
- Requires DoD PA
- Commercial cloud services eligible (AWS GovCloud, Azure Government, etc.)

## IL4 — CUI

> [!quote] CSP SRG V1R6 — IL4
> "Impact Level 4: Controlled Unclassified Information — Information that requires safeguarding or dissemination controls pursuant to applicable laws, regulations, and Government-wide policies."
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg#3.7.2 Impact Level 4|3.7.2]]

- Requires: FedRAMP Moderate + FedRAMP+ controls
- CSP must connect through a DISA-approved Cloud Access Point (CAP)
- DISA STIG compliance for OS, databases, web servers
- Personnel screening requirements (NACI minimum)

## IL5 — CUI-Sensitive / Unclassified NSS

> [!quote] CSP SRG V1R6 — IL5
> "Impact Level 5: Unclassified National Security System/National Security Information — Information that is particularly sensitive and requires additional protections above IL4."
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg#3.7.3 Impact Level 5|3.7.3]]

- Requires: FedRAMP High + FedRAMP+
- **Exclusive DoD use** — cannot co-mingle with commercial or other federal tenants
- Mandatory CAP (Cloud Access Point) connection
- Higher personnel security requirements

## IL6 — Classified (SECRET)

- Above FedRAMP scope entirely
- Requires SIPRNet connectivity
- Commercial cloud providers cannot host unless in dedicated Secret/Top-Secret regions (e.g., AWS C2S, Azure Government Secret)

## FedRAMP+ Concept

> [!quote] CSP SRG V1R6 — FedRAMP+
> "FedRAMP+ — A CSO that has a FedRAMP Authorization and meets additional DoD-specific security control requirements (FedRAMP+) and is listed in the DOD Cloud Service Catalog."
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg#3.5 FedRAMP+|3.5]]

FedRAMP+ adds DoD-specific control values on top of FedRAMP Moderate or High. These are specified in Appendix D of the SRG:

> [!quote] CSP SRG V1R6 — Appendix D
> "Table D-1: FedRAMP+ Additions/Adjustments to Parameter Values for FedRAMP+ Security Controls/Enhancements"
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg#Appendix D|Appendix D]]

## DoD Provisional Authorization (PA)

A DoD PA is required before any CSP can be listed in the DoD Cloud Service Catalog. It is separate from (but builds on) a FedRAMP ATO.

> [!info] PA Authorization Path
> 1. Obtain FedRAMP ATO (Moderate or High depending on IL)
> 2. Implement FedRAMP+ additional controls
> 3. DISA assesses FedRAMP+ delta controls
> 4. DISA issues DoD PA
> 5. CSP listed in DoD Cloud Service Catalog at appropriate IL
> 6. Mission Owners can then reuse the PA for their own ATO

## Continuous Monitoring (DoD)

> [!quote] CSP SRG V1R6 — Continuous Monitoring
> "DOD Continuous Monitoring for FedRAMP CSOs with a 3PAO-Assessed Non-DOD Federal Agency ATO" and "DOD Continuous Monitoring for DOD-Assessed CSOs" — separate tracks with different evidence requirements.
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg#5.3.1 Continuous Monitoring|5.3.1]]

## Cross-Framework Mapping

> [!info] Cross-Framework
> - IL2 ≈ FedRAMP Moderate
> - IL4 ≈ FedRAMP Moderate + NIST 800-171 (CUI protection)
> - IL5 ≈ FedRAMP High + exclusive tenancy
> - IL6 = Outside FedRAMP scope
> - CMMC Level 2 covers the CUI protection requirements in IL4
> See: [[Wiki/fedramp-baseline-overview]], [[Wiki/nist-800-171-cui-protection]]

## Related Notes

- [[Wiki/fedramp-baseline-overview]]
- [[Wiki/fedramp-nist-800-53-relationship]]
- [[Wiki/nist-800-171-cui-protection]]
