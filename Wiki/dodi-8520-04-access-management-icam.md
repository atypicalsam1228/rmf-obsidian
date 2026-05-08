---
type: concept
framework: cross-framework
status: draft
tags:
  - access-control/icam
  - access-control/zero-trust
  - access-control/privileged-access
  - access-control/npe
  - dod/dodi-8520-04
  - fedramp/moderate
  - fedramp/high
  - nist-800-53/ac
  - nist-800-53/au
  - nist-800-53/ia
created: 2026-05-08
updated: 2026-05-08
sources:
  - "[[Sources/DoD-SRG/dodi-8520-04-access-management]]"
  - "[[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg]]"
related:
  - "[[Wiki/fedramp-moderate-access-controls]]"
---

# DoDI 8520.04 — Access Management & ICAM for DoD IT Systems

> [!abstract] Summary
> DoDI 8520.04 (effective September 3, 2024) is the DoD's mandatory access management policy for all DoD IT systems — NIPRNET through JWICS, contractor networks, and commercial cloud services hosting DoD data. It operationalizes the **DoD Zero Trust Strategy** by mandating a migration from static explicit provisioning to attribute-driven **dynamic access** by FY2028. It covers person entities, NPEs (non-person entities), privileged users, emergency access, SOD enforcement, access reviews, logging, and the approval process for enterprise authoritative attribute services (ICAM).

---

## Why This Matters for Compliance

DoDI 8520.04 is the **DoD-specific overlay on NIST 800-53 AC and IA families** for any system that:
- Is hosted in a commercial cloud provider with DoD data
- Is pursuing a DoD Authority to Operate (ATO) under the RMF
- Is a FedRAMP-authorized CSP serving DoD mission owners
- Processes CUI, classified, or DoD-owned data

> [!info] Cross-Framework Mapping
> | DoDI 8520.04 Requirement | NIST 800-53 | FedRAMP Moderate | CMMC |
> |---|---|---|---|
> | Explicit access provisioning | AC-2 Account Management | AC-2 | AC.L2-3.1.1 |
> | Dynamic access / ABAC | AC-2(13), AC-16 | AC-2(13) | — |
> | Least privilege | AC-6 | AC-6 | AC.L1-3.1.2 |
> | SOD | AC-5 | AC-5 | AC.L2-3.1.4 |
> | Access reviews | AC-2(4), AC-2(7) | AC-2(4) | AC.L2-3.1.6 |
> | IT privileged user controls | AC-2(7), AC-2(9) | AC-2(7) | — |
> | NPE / service accounts | IA-3, IA-9 | IA-3 | — |
> | Activity logging | AU-2, AU-12 | AU-2 | AU.L2-3.3.1 |
> | Audit log protection | AU-9 | AU-9 | AU.L2-3.3.8 |
> | Emergency access | AC-2(2) | AC-2(2) | — |

---

## Three Access Models

DoDI 8520.04 defines three access models that map directly to Zero Trust architectural patterns:

### Explicit Access (Traditional IAM)
Provisioned entitlements — "by name" accounts. Required for:
- All IT privileged users (system admins, network admins, DBAs, security analysts)
- Emergency accounts
- Functional privileged users when audit of provisioning process is required
- NPEs when attribute services are unavailable

> [!quote] DoDI 8520.04 Section 4.2.a
> "Explicit access requires provisioning authorizations, also known as entitlements, to entities for specific access rights to IT resources. Explicit access establishes a 'by name' account with authorizations for each entity accessing the resource."
> — [[Sources/DoD-SRG/dodi-8520-04-access-management#4.2 Access Requirements|Section 4.2.a]]

### Dynamic Access (Zero Trust / ABAC)
Authorization determined at request time from digital policy rules + user/environment attributes. No pre-provisioning required. Preferred model for general users where attributes are available.

> [!quote] DoDI 8520.04 Section 4.2.b
> "For dynamic access, authorization is determined when the entity requests access to the IT resource based on the digital policy rule for the resource and user and environment attribute values. Dynamic access does not require provisioning entitlements or accounts for the user."
> — [[Sources/DoD-SRG/dodi-8520-04-access-management#4.2 Access Requirements|Section 4.2.b]]

### Hybrid Access
Combination — automated attribute verification drives the provisioning/de-provisioning of explicit entitlements. Requires:
- Subscription to Enterprise ICAM person identity distribution services
- **Daily** re-verification of critical access information (background investigation, clearance, need-to-know)
- De-provisioning within **48 hours** when person attribute changes dictate

---

## Critical Timelines (Implementation Reference)

| Event | Requirement | Source |
|---|---|---|
| Network access de-provisioning (routine) | 24 hours | Section 4.2.a.(3) |
| Physical access de-provisioning (routine) | End of business day | Section 4.2.a.(3) |
| Access de-provisioning (high-risk/involuntary) | No later than 2 business days | Section 4.2.a.(3) |
| Supervisor notification for privileged access removal | Within 1 business day | Section 4.2.a.(3) |
| Supervisor notification for non-privileged access removal | Within 2 business days | Section 4.2.a.(3) |
| Emergency account approval (when pre-approval not possible) | Within 8 hours of use | Section 4.1.d.(3).(c) |
| Access review — functional privileged users | Every 12 months | Section 4.2.a.(5) |
| Access review — IT privileged users | Every 3 months | Section 4.2.a.(5) |
| Unauthorized access review suspension | Within 2 business days of notice | Section 4.2.a.(5) |
| Hybrid access re-verification (clearance, NTK) | Daily | Section 4.2.c.(2) |
| Hybrid access de-provisioning on attribute change | Within 48 hours | Section 4.2.c.(2) |
| Audit log review | At least weekly | Section 4.4.b.(3) |
| Access review documentation retention | 12 months beyond deactivation | Section 4.2.a.(5) |
| ICAM automated provisioning tool adoption deadline | End of FY2028 | Section 4.2.a.(2) |
| Annual authorization requirement reviews | At least annually | Section 4.1.c, 4.1.d |

---

## Privileged Access Management (PAM) Requirements

DoDI 8520.04 draws a hard line between three privilege levels:

| User Type | Definition | Provisioning Method | Auth Requirement |
|---|---|---|---|
| General User | No elevated privileges | Dynamic preferred | Per DoDI 8520.02/8520.03 |
| Functional Privileged | Application-level approver (e.g., finance system approver) | Explicit or dynamic; explicit required when audit needed | Traceable to single person/NPE |
| IT Privileged | Sys/network/DB admins, security analysts who manage audit logs | Explicit only | Separate credentials + separate accounts for privileged actions |

> [!quote] DoDI 8520.04 Section 3.2.e
> "Access granted must be based on least privilege, most restrictive access. [...] IT privileged users must use separate credentials and separate accounts when accessing the system using elevated privileges to perform IT privileged actions."
> — [[Sources/DoD-SRG/dodi-8520-04-access-management#3.2 System Protocol|Section 3.2.e]]

> [!example] AWS Implementation — PAM
> - Use **AWS IAM Identity Center** with separate permission sets for privileged roles vs. general users.
> - Require **MFA hardware tokens** (hardware-bound, not TOTP) for all IT privileged role assumptions.
> - Use **AWS CloudTrail** + **CloudWatch Logs** to log all privileged API calls; protect with `cloudwatch-log-group-encrypted` and `cloud-trail-encryption-enabled` FedRAMP Config rules.
> - Implement **AWS Config rule `iam-no-inline-policy-check`** and `iam-user-no-policies-check` to enforce managed policies.
> - Enforce `access-keys-rotated` (90-day max) and `iam-user-unused-credentials-check` (90-day max) from FedRAMP Moderate conformance pack.

---

## Non-Person Entity (NPE) Access

NPEs — service accounts, monitoring tools, RPA bots, endpoint devices — must follow the same access controls as person entities with several additional requirements:

> [!quote] DoDI 8520.04 Section 4.5.c
> "NPEs acting as users must be authorized using the same access methodologies as person users [...]. NPEs must be provisioned with their own identities, credentials through the DoD public key infrastructure NPE issuance portal, and unique network or application accounts. NPEs must not be assigned an identifier that also maps to a person entity."
> — [[Sources/DoD-SRG/dodi-8520-04-access-management#4.5 NPE Access|Section 4.5.c]]

> [!example] AWS Implementation — NPE / Service Accounts
> - Use **IAM Roles** (not IAM Users) for all service accounts, Lambda functions, EC2 instance profiles, ECS task roles.
> - **Never create long-lived access keys** for service accounts; use instance profiles and role assumption.
> - FedRAMP rule `ec2-instance-profile-attached` enforces instance profile attachment on EC2.
> - Enforce `iam-policy-no-statements-with-admin-access` and `iam-policy-no-statements-with-full-access` to prevent over-permissioned service roles.
> - Log all NPE API activity to **CloudTrail** with `cloudtrail-s3-dataevents-enabled` for data plane access.
> - Tag all NPE IAM roles with `EntityType: NPE` and owning team for access review traceability.

---

## Separation of Duties (SOD)

SOD requirements under DoDI 8520.04 require both policy definition and automated enforcement across systems:

> [!quote] DoDI 8520.04 Section 4.2.a.(4)
> "System owners and IT resource owners must define and document SOD requirements for users, including the definition of incompatible activities and transactions. For example, it would be a SOD violation for a functional privileged user to have both the ability to create an invoice and to authorize payment of that invoice."
> — [[Sources/DoD-SRG/dodi-8520-04-access-management#4.2 Access Requirements|Section 4.2.a.(4)]]

> [!example] AWS Implementation — SOD
> - Use **AWS IAM permission boundaries** to cap maximum permissions, preventing privilege escalation even by account admins.
> - Use **AWS Organizations SCPs** to enforce enterprise-level SOD rules (e.g., prevent same account from deploying and approving infrastructure changes).
> - Map IAM roles to enterprise roles per 4.2.a.(4).b.1 — document mappings in SSP Appendix.
> - Use **AWS Security Hub** findings + custom AWS Config rules to detect SOD violations (e.g., combined create + approve entitlements on financial systems).

---

## Authoritative Attribute Services (Dynamic Access ICAM)

For DoD systems using dynamic access, attributes must come from approved authoritative attribute services. The attribute service must meet:

| Requirement | Standard |
|---|---|
| Accuracy | Documented verification process + freshness timestamps |
| Integrity | Controls commensurate with risk level of protected resources |
| Privacy/Confidentiality | Registered relying parties + Privacy Act SORNs |
| Availability | Documented SLA + just-in-time API query support |

> [!info] DoD Enterprise Attribute Services
> The authoritative source for person entity attributes is DMDC's **Enterprise Identity Attribute Service (EIAS)**. Approved enterprise attribute services list: https://intelshare.intelink.gov/sites/dodcioicamdocs. Published attribute service info at https://cyber.mil/icam/.

---

## Activity Logging Requirements

Logging requirements under this instruction align with **OMB M-21-31 Event Logging Tier 3** (the highest federal logging tier).

Logs must capture:
- All IT privileged user system access (including emergency access)
- All successful AND unsuccessful access requests: user identity, IT resource, date/time, access granted or denied
- For dynamic access: attributes used by the digital policy rule to determine access

Additional controls:
- Audit logs must be reviewed **at least weekly** for suspicious activity
- System privileged users **must not have access** to modify, add, or delete audit logs that track their activity

> [!example] AWS Implementation — Logging (FedRAMP alignment)
> FedRAMP rules that satisfy DoDI 8520.04 logging requirements:
> - `cloudtrail-enabled` — baseline CloudTrail coverage
> - `cloud-trail-cloud-watch-logs-enabled` — forward to CloudWatch for alerting
> - `cloud-trail-encryption-enabled` + `cloud-trail-log-file-validation-enabled` — integrity
> - `cloudwatch-log-group-encrypted` — logs encrypted at rest
> - `cloudtrail-s3-dataevents-enabled` — data plane (S3 object-level) access
> - `cw-loggroup-retention-period-check` — log retention compliance
> - `cloudtrail-security-trail-enabled` (FedRAMP High) — organizational security trail
>
> For dynamic access attribute logging: custom application logs must capture which attribute service responses drove the authorization decision. Store in CloudWatch Logs or S3 with a dedicated audit log bucket (locked, versioned, no delete permissions for service accounts).

---

## Zero Trust Alignment

DoDI 8520.04 is a direct implementation vehicle for the DoD Zero Trust Strategy. Key ZT objectives referenced:

> [!quote] DoDI 8520.04 Section 3.1
> "IT and digital resource owners must implement ICAM access capabilities in accordance with Objectives 2.1. and 2.4. in the Office of the DoD CIO's 'DoD Zero Trust Strategy' and the users and data pillars described in their 'DoD Zero Trust Reference Architecture.'"
> — [[Sources/DoD-SRG/dodi-8520-04-access-management#3.1 IT and Digital Resource Protocol|Section 3.1]]

| ZT Pillar | DoDI 8520.04 Mechanism |
|---|---|
| User | ICAM / DMDC EIAS attributes, MFA, CAC, dynamic access |
| Device | NPE endpoint authorization, device attributes (type, management state, geolocation) |
| Data | IT resource owner tagging, digital policy rules at resource level |
| Application | Functional privileged user access controls, service account management |
| Network | SOD enforcement, operationally constrained environment compensating controls |

---

## FedRAMP Cloud Service Provider Implications

Commercial CSPs hosting DoD IT resources fall under DoDI 8520.04 applicability (Section 1.1.a.(1)(c)). Key implications for FedRAMP CSPs serving DoD mission owners:

1. **ICAM integration:** CSP must support DoD enterprise ICAM services (DMDC EIAS attribute distribution) or integrate with DoD Component-level ICAM.
2. **Dynamic access support:** CSP systems should support attribute-based authorization, not just static provisioning.
3. **NPE controls:** Cloud service accounts, automation roles, and monitoring agents are NPEs — must meet 4.5 requirements.
4. **Logging to Tier 3:** FedRAMP Moderate logging controls + cloudtrail-s3-dataevents-enabled satisfy baseline; DoD mission owners may require additional attributes logged.
5. **Audit log immutability:** FedRAMP rules `backup-recovery-point-manual-deletion-disabled` and S3 Object Lock controls satisfy the audit log protection requirement in 4.4.b.(5).

> [!info] DoD Cloud SRG Relationship
> DoD mission owners using FedRAMP-authorized CSPs must also comply with the [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg|DoD Cloud Computing SRG V1R6]]. DoDI 8520.04 access management requirements layer on top of the CSP SRG requirements — they do not replace them.

---

## Key Definitions Quick Reference

| Term | Definition |
|---|---|
| **Explicit Access** | Provisioned entitlements — "by name" accounts with pre-approved access rights |
| **Dynamic Access** | Real-time attribute-based authorization against digital policy rules; no pre-provisioning |
| **Hybrid Access** | Automated attribute verification drives provisioning/de-provisioning of explicit accounts |
| **Digital Policy Rule** | A rule defining the combination of attributes under which access may take place |
| **Authoritative Attribute Service** | Approved repository that provisions and serves up authorization attributes |
| **NPE** | Physical device, VM, system, service, or process assigned an identifier and credentials |
| **Entitlement** | Authorization to access one or more IT resources within an information system |
| **SOD** | Separation of duties — prevents a single user from having incompatible access combinations |
| **ICAM** | Identity, Credential, and Access Management |
| **DMDC EIAS** | Defense Manpower Data Center Enterprise Identity Attribute Service — the authoritative person entity attribute source |
