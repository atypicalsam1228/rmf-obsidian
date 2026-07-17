---
type: decision-record
framework: cross-framework
status: final
tags:
  - personnel-security/us-person
  - personnel-security/privileged-access
  - dod-srg/impact-levels
  - fedramp/moderate
  - fedramp/equivalency
  - PS-2
  - PS-3
created: 2026-07-13
updated: 2026-07-13
sources:
  - "[[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg]]"
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
  - "[[Sources/FedRAMP/fedramp-equivalency-cloud-service-providers]]"
related:
  - "[[Wiki/jira-cloud-fedramp-us-person-requirements]]"
  - "[[Wiki/dod-srg-cloud-impact-levels]]"
---

# Do Privileged Admins (e.g., YubiKey Admins) Need to Be US-Based?

> [!abstract] Summary
> The DoD SRG requirement is about **legal citizenship/person status**, not geographic location. At IL4+, privileged administrators must be U.S. Citizens, Nationals, or U.S. Persons (LPRs) — but the SRG does not independently require them to be physically located in the United States. At IL5+ the requirement tightens to U.S. Citizens only for higher-risk admin positions.

---

## The Question

"US-based" (physically in the US) and "US Person/Citizen" (legal status) are different requirements. The DoD SRG imposes the latter — not the former — as the hard requirement for privileged access.

---

## Authoritative Answer — DoD SRG V1R6 Table 5-1

> [!quote] DoD SRG V1R6 — Table 5-1: Minimum Security Investigation Requirements for CSP Personnel
> | Impact Level | Citizenship Requirement |
> |---|---|
> | IL2 (Non-CUI) | No Restrictions |
> | IL4 (CUI) | U.S. Citizens / Nationals / Persons |
> | IL5 (CUI/NSS) — Tier 4 positions | U.S. Citizens / Nationals / Persons |
> | IL5 (CUI/NSS) — Tier 3 positions | U.S. Citizens |
> | IL6 (SECRET+NSS) | U.S. Citizens |
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg]]

> [!quote] DoD SRG V1R6 — §5.5.2.2 Considerations for Background Investigation
> "Considerations that were used to develop the minimum requirement include whether CSP personnel have access to agency information, position risk, position sensitivity, scope of impact if information is compromised, and **citizenship requirements**."
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg]]

---

## Impact Level Breakdown

| Impact Level | Data Type | Admin Citizenship Requirement |
|---|---|---|
| **IL2** | Public / non-CUI | No restriction — any nationality permitted |
| **IL4** | CUI | U.S. Citizens, Nationals, or U.S. Persons (LPRs qualify) |
| **IL5** | CUI / NSS | U.S. Citizens/Nationals/Persons (Tier 4); U.S. Citizens only (Tier 3) |
| **IL6** | Classified (SECRET+) | U.S. Citizens only |

> [!info] US Person Definition (22 CFR 120.15)
> Broader than US Citizen. Includes: U.S. Citizens, lawful permanent residents (green card holders), protected individuals under 8 U.S.C. 1324b(a)(3), and US-incorporated entities. At IL4, green card holders satisfy the requirement. At IL6, they do not.

---

## Geographic Location vs. Legal Status

The SRG does **not** impose a standalone geographic requirement that admins must be physically located in the United States. The hard requirement is citizenship/person status, which is a legal category — a US Person working remotely from abroad still satisfies the SRG requirement as to citizenship.

> [!warning] Other Controls May Impose Geographic Constraints
> While PS-3 citizenship requirements do not mandate US geography, other controls can effectively constrain location:
> - **PE-17 / Alternate Work Sites** — Telework from foreign countries may introduce risk the AO conditions against.
> - **SC / network controls** — VPN and network access policies may practically restrict where privileged access originates.
> - **Agency AO conditions** — Mission Owners may impose geographic restrictions beyond the SRG minimum as risk-based conditions on the PA.
> These are AO-imposed risk decisions, not SRG hard requirements.

---

## Minimum Background Investigation by IL

> [!quote] DoD SRG V1R6 — §5.5.2.2 Impact Level 4
> "For access to Impact Level 4 information, a Tier 2 investigation is the minimum requirement for a 'Non-Sensitive, Moderate Risk' position, per OPM policy."
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg]]

> [!quote] DoD SRG V1R6 — §5.5.2.2 Impact Level 5
> "The minimum background investigation required for CSP personnel with access to Impact Level 5 information is a Tier 2 investigation for a 'Non-Sensitive, Moderate Risk' position and a Tier 4 investigation for a 'Non-Sensitive, High Risk' position with a 'Worldwide or Government-Wide Impact.'"
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg]]

| Impact Level | Minimum Investigation |
|---|---|
| IL2 | Tier 1 |
| IL4 | Tier 2 |
| IL5 (moderate risk) | Tier 2 |
| IL5 (high risk / worldwide impact) | Tier 4 |
| IL6 | Tier 3 (Secret) / Tier 5 (Critical Sensitive) |

---

## PS-2 Position Designation Context

Citizenship requirements flow from the PS-2 position risk designation process, which drives the investigation tier required.

> [!quote] FedRAMP Moderate — PS-2 Position Risk Designation
> "Assign a risk designation to all organizational positions; establish screening criteria for individuals filling those positions; and review and update position risk designations in accordance with [at least every three years]."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#PS-2 — Position Risk Designation|PS-2]]

The position designation (Non-Sensitive / Non-Critical Sensitive / Critical Sensitive) determines the Tier investigation required, which in turn determines whether U.S. Citizenship vs. U.S. Person status is sufficient.

---

> [!info] Cross-Framework Mapping
> FedRAMP controls: [[Sources/FedRAMP/fedramp-moderate-baseline#PS-2 — Position Risk Designation|PS-2]], [[Sources/FedRAMP/fedramp-moderate-baseline#PS-3 — Personnel Screening|PS-3]]
> DoD SRG: §5.5.2, §5.5.2.2, Table 5-1
> Statutory: 8 U.S. Code § 1408 (Nationals), 22 CFR 120.15 (US Person), 22 CFR 120.16 (Foreign Person)
> FedRAMP Equivalency: [[Sources/FedRAMP/fedramp-equivalency-cloud-service-providers]]
> See also: [[Wiki/jira-cloud-fedramp-us-person-requirements]] for broader CSP US Person analysis
