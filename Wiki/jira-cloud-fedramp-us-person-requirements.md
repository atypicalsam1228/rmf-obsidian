---
type: decision-record
framework: cross-framework
status: draft
tags:
  - personnel-security/us-person
  - fedramp/moderate
  - dod-srg/impact-levels
  - atlassian/jira-cloud
  - csp/platform
  - PS-3
  - PS-7
created: 2026-05-18
updated: 2026-05-19
sources:
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
  - "[[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg]]"
related:
  - "[[Wiki/fedramp-authorization-process]]"
  - "[[Wiki/dod-srg-cloud-impact-levels]]"
---

# Jira Cloud FedRAMP — Can Non-US Persons Maintain It? (CSP Platform Perspective)

> [!abstract] Summary
> This org is the **CSP / platform provider** — Jira Cloud is procured inside our FedRAMP boundary and offered to agency customers. As the CSP, our PS-3 and PS-7 SSP implementations directly govern which of our personnel can maintain the system. FedRAMP's civilian baseline does not mandate US citizenship, but DoD SRG IL4+ does — and those requirements bind **our ops/support staff**, not tenants. Architectural segregation of non-US engineering staff from the management plane is the standard compliance model.

---

## Context — We Are the Platform

Our organization operates the FedRAMP-authorized boundary. Jira Cloud is procured as a component **within** that boundary. We are the CSP. Our customers are federal agencies (civilian and/or DoD) who use the platform as tenants.

This means:
- **PS-3 and PS-7 in our SSP** define the rules for our own personnel — who can touch the system, what screening applies, and whether US Person status is required.
- The agency AO authorizes **our** system. They review our PS implementation, not just Atlassian's.
- If we serve DoD customers, the DoD SRG's US Person requirements apply to **our** personnel with access to the boundary.

---

## FedRAMP Civilian Baseline — Screening Required, Citizenship Not Mandated

FedRAMP Moderate PS controls require us to screen our personnel and manage external provider security, but do **not** explicitly require US citizenship.

> [!quote] FedRAMP Moderate — PS-3 Personnel Screening
> "Screen individuals prior to authorizing access to the system; and rescreen individuals in accordance with [Assignment: organization-defined conditions requiring rescreening and, where rescreening is so indicated, the frequency of rescreening]."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#PS-3 — Personnel Screening|PS-3]]

> [!quote] FedRAMP Moderate — PS-7 External Personnel Security
> "Establish personnel security requirements, including security roles and responsibilities for external providers; Require external providers to comply with personnel security policies and procedures established by the organization; Document personnel security requirements; Require external providers to notify [defined personnel] of any personnel transfers or terminations of external personnel who possess organizational credentials and/or badges, or who have system privileges within [defined time period]; and Monitor provider compliance with personnel security requirements."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#PS-7 — External Personnel Security|PS-7]]

> [!warning] What You Document in the SSP, You Are Held To
> If our PS-3 implementation statement says "all personnel with boundary access are US Persons," the 3PAO will audit that. If we document a lower bar, the agency AO may impose US Person conditions anyway — especially for DoD. Write the SSP to match what we can actually enforce and verify.

**For civilian-only customers:** Non-US platform maintainers are not automatically prohibited. The AO of each agency customer can impose additional conditions via their authorization decision, but FedRAMP baseline does not require citizenship.

---

## DoD Customers — Hard US Person Requirements Apply to Our Personnel

If any DoD agency is a customer on our platform, the DoD SRG applies to **our** personnel who touch the boundary — not just to Atlassian's personnel.

> [!quote] DoD SRG V1R6 — §5.5.2 CSP Personnel Requirements
> "Access to DOD information above Impact Level 2 is limited by national affiliation. For other than U.S. Citizens or Non-Citizen U.S. Nationals as defined in 8 U.S. Code § 1408, national affiliation is defined in 22 CFR 120.15 – U.S. Person and 120.16 – Foreign Person."
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg#5.5.2 CSP Personnel Requirements|SRG §5.5.2]]

> [!quote] DoD SRG V1R6 — Impact Level Personnel Restrictions
> "Impact Level 2: CSP personnel... may be U.S. Citizens, U.S. Nationals, U.S. Persons, or Foreign Persons. There is no restriction.
> Impact Level 4/5: CSP personnel having access to the systems processing/storing DOD CUI information or to the information itself at Impact Level 4/5 must be U.S. Citizens, U.S. Nationals, or U.S. Persons. No Foreign persons may have such access.
> Impact Level 6: CSP personnel having access to systems processing/storing classified information or to the information itself must be U.S. Citizens."
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg#5.5.2 CSP Personnel Requirements|SRG §5.5.2]]

| Impact Level | Data Type | Our Non-US Staff Permitted in Boundary? |
|---|---|---|
| **IL2** | Public / non-CUI | Yes — no restrictions |
| **IL4 / IL5** | CUI / NSS | No — must be US Citizens, Nationals, or US Persons (22 CFR 120.15) |
| **IL6** | Classified | No — US Citizens only |

> [!info] US Person Definition (22 CFR 120.15)
> Broader than US Citizen. Includes: US Citizens, lawful permanent residents (green card holders), protected individuals under 8 U.S.C. 1324b(a)(3), and US-incorporated corporations/partnerships. Long-term resident green card holders can qualify.

> [!quote] DoD SRG V1R6 — CSP Personnel Managing Infrastructure
> "CSP personnel managing and/or monitoring the CSO infrastructure. This is primarily related to U.S. Persons constraints. Refer to Section 5.5.2, CSP Personnel Requirements."
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg#CSP Personnel|SRG §5.4]]

---

## The Architectural Segregation Model

The standard compliance approach — used by Atlassian and others — is to allow non-US engineering staff to work on the underlying product while **architecturally preventing them from accessing the FedRAMP management plane or customer data**.

This means:

- **In scope (must be US Person at IL4+):** Infrastructure ops, SRE, NOC/SOC, support staff with privileged access to the FedRAMP environment, anyone who can reach the management plane or customer tenant data
- **Potentially out of scope (may allow non-US):** Software engineers whose code changes are deployed through a controlled pipeline but who have no direct logical access to the production boundary; roles that operate only in a dev/test environment fully isolated from the FedRAMP boundary

> [!warning] "No logical access" must be technically enforced, not just policy-stated
> Claiming a role has no boundary access only holds if it is enforced through IAM, network segmentation, and audited. A 3PAO will test this. If a non-US engineer can SSH to a production server, escalate privileges, or access a customer data store — even theoretically — that is access.

> [!danger] NEEDS SOURCE: Our SSP PS-3/PS-7 Implementation Statements
> The specific role-by-role breakdown of which positions require US Person status must be documented in our SSP. This article reflects the regulatory framework; the SSP is the authoritative record for our actual implementation. Ensure PS-3 and PS-7 implementation statements explicitly address non-US personnel and boundary access scope.

---

## Shared Responsibility — Platform vs. Atlassian

We procured Jira Cloud as a component. Atlassian carries some PS responsibility for their underlying infrastructure; we carry PS responsibility for our boundary layer above it.

| Layer | Owner | US Person Obligation |
|---|---|---|
| Atlassian infrastructure (GovCloud, hypervisor, platform SaaS layer) | Atlassian | Governed by Atlassian's SSP — their problem to demonstrate |
| Our FedRAMP boundary (tenant configs, integrations, APIs, admin plane) | Us | Governed by **our** SSP PS-3/PS-7 — our problem to demonstrate |
| Agency tenant data and user accounts | Agency customer | Governed by agency PS policies |

> [!tip] Obtain Atlassian's SSP package
> For the Atlassian-managed layer, obtain their FedRAMP package from the Marketplace. Their PS-3/PS-7 responses confirm what they certify about their own personnel. We still need to document our layer independently.

---

## Decision Tree (CSP Perspective)

```
Do we serve DoD customers?
├── Yes → What Impact Level are they authorized at?
│   ├── IL2 → No citizenship restriction on our boundary staff
│   └── IL4 / IL5 → Our ops/support/SRE with boundary access must be US Persons
│       └── IL6 → US Citizens only (we would need a separate IL6 environment)
└── No (civilian only) → FedRAMP baseline applies
    ├── Check agency AO conditions on each ATO — they may impose US Person requirements
    └── Our SSP documents our actual screening criteria; 3PAO audits against what we committed
```

---

## Recommended Actions for Our SSP

> [!tip] PS Implementation Checklist (CSP)
> 1. **Map every role** with logical access to the FedRAMP boundary. Document access type (privileged, read-only, break-glass) per role.
> 2. **Classify each role** by whether it constitutes "access to the system" under PS-3 — be conservative. Ambiguous roles should be treated as in-scope.
> 3. **Document citizenship/US Person requirements per role** in PS-3 implementation. If DoD IL4+ is in scope, all in-boundary roles must be US Citizens/Nationals/Persons.
> 4. **Enforce segregation technically** for any non-US engineering staff who are excluded from scope. IAM boundaries, separate AWS accounts, network isolation — document the mechanism.
> 5. **PS-7 for Atlassian:** Document our requirements on Atlassian as an external provider. Obtain their PS-3 attestation as part of supply chain assurance.
> 6. **ConMon:** PS-3 rescreening frequencies must be tracked. FedRAMP Moderate requires reinvestigation on national security clearance schedules; our SSP must specify the frequency for non-cleared positions.

> [!info] Cross-Framework Mapping
> Controls: [[Sources/FedRAMP/fedramp-moderate-baseline#PS-3 — Personnel Screening|PS-3]], [[Sources/FedRAMP/fedramp-moderate-baseline#PS-7 — External Personnel Security|PS-7]]
> DoD SRG: §5.5.2 CSP Personnel Requirements, Table 5-1, §5.4 (infrastructure management)
> Statutory references: 8 U.S. Code § 1408 (US Nationals), 22 CFR 120.15 (US Person), 22 CFR 120.16 (Foreign Person)
