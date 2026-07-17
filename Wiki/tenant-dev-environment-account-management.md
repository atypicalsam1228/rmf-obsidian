---
type: guide
framework: fedramp
status: draft
tags:
  - access-control/account-management
  - dev-environments
  - tenant-access
  - fedramp/moderate
  - AC-2
  - PS-3
created: 2026-06-05
updated: 2026-06-05
sources:
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
related:
  - "[[Wiki/fedramp-access-control]]"
  - "[[Wiki/jira-cloud-fedramp-us-person-requirements]]"
---

# Tenant Dev Environment Account Management (FedRAMP)

> [!abstract] Summary
> Covers account request requirements, batch requests, request tracking tools, who can request accounts, and what happens to dev accounts when federal data arrives in the boundary. Applies to CSPs going through FedRAMP ATO with dev tenants that may persist into production.

---

## Required Fields on an Account Request

Beyond name, duration, and permissions:

| Field | Control |
|---|---|
| Full legal name + unique identifier | AC-2(d), IA-4 |
| Role/title and organizational affiliation | AC-2(d) |
| Business justification / specific mission need | AC-2(d), AC-6 |
| Specific permissions (not broad roles like "Admin") | AC-6 |
| Account type (individual, temporary, service) | AC-2(a) |
| Account expiration date | AC-2(2) |
| Approver name and role | AC-2(e) |
| Nationality / US Person status | PS-3 |
| Point of contact for removal notification | AC-2(h) |
| Work location (city/state/country) | AC-2(12) |

> [!quote] FedRAMP Moderate — AC-2 Supplemental Guidance
> "Users requiring administrative privileges on system accounts receive additional scrutiny by organizational personnel responsible for approving such accounts and privileged access, including system owner, mission or business owner, senior agency information security officer..."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AC-2 — Account Management|AC-2]]

> [!info] On Nationality
> FedRAMP Moderate does not mandate US citizenship for tenant users. However, if DoD customers at IL4+ are ever in scope, all boundary personnel must be US Persons (22 CFR 120.15). Capture nationality on the request form now to avoid retrofitting records.

---

## Batch Requests (One Ticket for a Group)

Permitted with conditions:

- Each individual must be **named** — anonymous or group accounts are flagged as high-risk
- Permissions assigned **per-person or per-role**, not to the group collectively
- Expiration listed per user or uniformly applied and stated
- Approver explicitly reviewed and signed off on the full list

> [!quote] FedRAMP Moderate — AC-2(9)
> "Shared and group accounts are authorized only for [organization-defined need with justification statement that explains why such accounts are necessary]"
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AC-2 (9) — Restrictions on Use of Shared and Group Accounts|AC-2(9)]]

A batch ticket requesting individual accounts (each person gets their own) is fine. One shared credential for multiple people is a compliance violation.

---

## Tracking Location

Location is not a required account record field in FedRAMP, but AC-2(12) uses location-inconsistent logins as an atypical usage signal. Best practice: capture work location (city/state/country, on-site vs. remote) on the request form and enforce via conditional access or IP allowlisting.

> [!quote] FedRAMP Moderate — AC-2(12)
> "Atypical usage includes accessing systems at certain times of the day or from locations that are not consistent with the normal usage patterns of individuals."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AC-2 (12) — Account Monitoring for Atypical Usage|AC-2(12)]]

---

## Recording Requests — Can You Use JIRA?

> [!warning] JIRA Location Matters
> If JIRA lives **inside** your FedRAMP boundary, it is a boundary component and must appear in the SSP. If it lives outside (standard Atlassian Cloud), it is an external system under AC-20 — acceptable for the request workflow, not for storing sensitive federal data in tickets.

**Split model:**
- JIRA outside boundary = acceptable for request/approval workflow
- Authoritative access record (who has an account, what permissions, expiration) = must live inside the boundary in your IAM system
- Audit logs of account creation/modification = inside boundary per AU-2 and AC-2(4)

---

## Who Can Request Accounts

Your SSP defines this; AC-2(e) requires a named approver role.

| Requestor | Approver |
|---|---|
| Project/team lead on behalf of team | System Owner or ISSO |
| Individual self-request | Manager + System Owner |
| Contractor | COR + ISSO |

Approver must be a named role documented in the SSP — not just "a manager."

---

## When Federal Data Arrives — Dev Account Handling

> [!warning] Dev + Real Federal Data = Production Boundary
> The moment federal agency data lands in an environment, that environment falls under full authorization boundary controls. Dev accounts provisioned under a "no live data" assumption may no longer meet the access control requirements in your SSP.

> [!quote] FedRAMP Moderate — AC-2(2)
> "Automatically [disable] temporary and emergency accounts after [organization-defined time period]"
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AC-2 (2) — Automated Temporary and Emergency Account Management|AC-2(2)]]

> [!quote] FedRAMP Moderate — AC-2(3)
> "Disable accounts within [24 hours for user accounts] when accounts are no longer required..."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AC-2 (3) — Disable Accounts|AC-2(3)]]

**Required actions at data arrival:**
1. Disable or remove all accounts scoped as "dev only" before federal data is introduced
2. Accounts that must persist must be re-scoped, re-approved, and re-documented as production accounts
3. If dev and production environments coexist, enforce technical segregation (separate AWS accounts/VPCs, separate identity stores) — the 3PAO will test this

**Cleanest compliance model:** Dev = entirely separate boundary, no dev account ever touches production, data transfer is a formal logged approved process.

---

## SSP Documentation Checklist (AC-2)

> [!tip] Document in your AC-2 implementation statement
> - [ ] Required fields for account requests
> - [ ] Batch request policy (allowed with named individuals)
> - [ ] Where the request system lives (JIRA external, IAM records internal)
> - [ ] Named approver roles
> - [ ] Data-arrival trigger for dev account review/termination
> - [ ] Location capture tied to AC-2(12) atypical usage monitoring
> - [ ] Account review frequencies: quarterly (privileged), annually (non-privileged)

> [!info] Cross-Framework Mapping
> - NIST 800-53: [[Sources/FedRAMP/fedramp-moderate-baseline#AC-2 — Account Management|AC-2]], AC-6, AC-2(2), AC-2(3), AC-2(12), PS-3
> - NIST 800-171: 3.1.1, 3.1.2 (access control), 3.9.1 (personnel screening)
> - CMMC Level 2: AC.L2-3.1.1, AC.L2-3.1.5

## Related Notes

- [[Wiki/fedramp-access-control]]
- [[Wiki/jira-cloud-fedramp-us-person-requirements]]
