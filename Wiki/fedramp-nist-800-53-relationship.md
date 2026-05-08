---
type: mapping
framework: cross-framework
status: draft
tags:
  - fedramp
  - nist-800-53
  - cross-framework
  - baseline-mapping
created: 2026-05-08
updated: 2026-05-08
sources:
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
  - "[[Sources/FedRAMP/fedramp-high-baseline]]"
  - "[[Sources/FedRAMP/fedramp-rev5-baselines-transition-guide]]"
  - "[[Sources/NIST-800-53/nist-800-53r5-catalog]]"
  - "[[Sources/FedRAMP/operational-best-practices-for-nist-800-53-rev-5]]"
related:
  - "[[Wiki/fedramp-baseline-overview]]"
  - "[[Wiki/nist-800-53-control-families]]"
  - "[[Wiki/fedramp-access-control]]"
---

# FedRAMP and NIST 800-53: Relationship and Differences

> [!abstract] Summary
> FedRAMP is built on top of NIST SP 800-53 Rev 5 — it does not replace it. FedRAMP selects a subset of NIST controls for each impact level (Low, Moderate, High), then overlays FedRAMP-specific parameter values that are more stringent than NIST defaults. Understanding this layering is essential for CSPs navigating both a FedRAMP authorization and NIST-based agency RMF compliance.

## The Layering Model

```
NIST 800-53 Rev 5 Catalog  (1,000+ controls across 20 families)
    ↓ select by impact level
NIST Moderate/High Baseline  (~325 / ~421 controls)
    ↓ overlay FedRAMP parameters
FedRAMP Moderate/High Baseline  (same controls, specific parameter values)
    ↓ tailor for CSP system
System-Specific SSP  (inherited + customer-responsible + shared controls)
```

## Key Differences: NIST vs. FedRAMP

| Aspect | NIST 800-53 | FedRAMP |
|---|---|---|
| Authority | Guidance / FISMA requirement for agencies | Mandatory for federal cloud services |
| Parameters | Organization-defined (flexible) | Fixed FedRAMP-specific values |
| Assessment | Agency-conducted or delegated | 3PAO must be FedRAMP-recognized |
| Authorization | AO grants ATO per system | FedRAMP PMO grants P-ATO; agencies grant ATOs leveraging it |
| Reuse | Not formally reusable | FedRAMP authorization reusable by all agencies |
| ConMon | Agency-determined | FedRAMP-prescribed monthly deliverables |

## Control Count by Baseline

> [!info] NIST vs. FedRAMP Control Counts
> - NIST 800-53 Low: 156 controls
> - NIST 800-53 Moderate: 325 controls
> - NIST 800-53 High: 421 controls
> - FedRAMP Low: ~125 controls (subset — removes some NIST Low controls)
> - FedRAMP Moderate: same count as NIST Moderate, different parameter values
> - FedRAMP High: same count as NIST High, tighter parameters

## Parameter Override Examples

FedRAMP replaces `[Assignment: organization-defined]` with fixed values. Examples:

| Control | NIST Parameter | FedRAMP Moderate Value |
|---|---|---|
| AC-1(c)(1) | Organization-defined frequency | Every 3 years |
| AC-1(c)(2) | Organization-defined frequency | Annually |
| IA-5 password age | Organization-defined | 90 days |
| IA-5 password length | Organization-defined | 14 characters |
| SI-2(c) critical patches | Organization-defined | 30 days |
| SI-2(c) moderate patches | Organization-defined | 90 days |
| RA-5 OS scan frequency | Organization-defined | Monthly |
| RA-5 web app scan frequency | Organization-defined | Quarterly (Moderate), Monthly (High) |

> [!quote] FedRAMP Moderate Baseline — AC-1
> "Review and update the current access control: Policy [at least every 3 years]... Procedures [at least annually]"
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AC-1 — Policy and Procedures|AC-1]]

## Rev 4 to Rev 5 Transition

FedRAMP completed the transition from NIST 800-53 Rev 4 to Rev 5 baselines.

> [!info] Rev 5 Key Changes
> - Privacy controls integrated (formerly in 800-53A separately)
> - Supply chain risk management (SR family) added
> - Outcome-based language replacing prescriptive requirements
> - ~200 new controls/enhancements added
> See: [[Sources/FedRAMP/fedramp-rev5-baselines-transition-guide]], [[Sources/FedRAMP/fedramp-rfc-0027-rev5-controls-baseline-update]]

## Control Families in Both Frameworks

> [!quote] NIST 800-53 Rev5 Catalog — Control Families
> AC (Access Control), AT (Awareness and Training), AU (Audit and Accountability), CA (Assessment Authorization and Monitoring), CM (Configuration Management), CP (Contingency Planning), IA (Identification and Authentication), IR (Incident Response), MA (Maintenance), MP (Media Protection), PE (Physical and Environmental), PL (Planning), PM (Program Management), PS (Personnel Security), PT (PII Processing and Transparency), RA (Risk Assessment), SA (System and Services Acquisition), SC (System and Communications Protection), SI (System and Information Integrity), SR (Supply Chain Risk Management)
> — [[Sources/NIST-800-53/nist-800-53r5-catalog]]

## Cross-Framework Mapping

> [!info] Cross-Framework
> - **NIST 800-171** uses ~110 of the 800-53 controls relevant to protecting CUI — roughly equivalent to a subset of FedRAMP Moderate
> - **CMMC Level 2** = NIST 800-171 (110 practices) — maps to FedRAMP Moderate AC, IA, AU, CM, RA, SI families
> - **FedRAMP High** aligns with **DoD IL4/IL5** when combined with DISA SRG requirements
> See: [[Sources/FedRAMP/dod-srg-control-crosswalk-v1-0]], [[Sources/NIST-800-171/nist-800-171r3-security-requirements]]

## Related Notes

- [[Wiki/fedramp-baseline-overview]]
- [[Wiki/nist-800-53-control-families]]
- [[Wiki/fedramp-access-control]]
