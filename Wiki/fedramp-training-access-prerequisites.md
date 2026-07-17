---
type: concept
framework: fedramp
status: final
tags:
  - fedramp/moderate
  - fedramp/high
  - training/access-prerequisites
  - access-control/account-management
  - personnel-security
created: 2026-07-08
updated: 2026-07-08
sources:
  - "[[Sources/NIST-800-53/nist-800-53r5-catalog]]"
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
  - "[[Sources/FedRAMP/fedramp-high-baseline]]"
  - "[[Sources/FedRAMP/ssp-appendix-f-rules-of-behavior-rob-template]]"
related:
  - "[[Wiki/fedramp-access-control]]"
  - "[[Wiki/fedramp-moderate-cdse-training-mapping]]"
  - "[[Wiki/fedramp-moderate-platform-bau-cadence-training]]"
---

# FedRAMP: Training as a Prerequisite to System Access

> [!abstract] Summary
> For role-based personnel (AT-3), training must be completed **before** access is authorized — this is fixed control language, not an organizational parameter. Rules of Behavior acknowledgment (PL-4) is a second hard gate. FedRAMP does not define an automatic "training expired → suspend access" trigger; organizations must operationalize this through AC-2 account management procedures in their SSP.

---

## AT-3: Role-Based Training Blocks Access

AT-3 is a hard prerequisite for personnel with defined security/privacy roles. Access cannot be provisioned until role-based training is complete.

> [!quote] NIST 800-53 R5 AT-3(a)(1)
> "Provide role-based security and privacy training to personnel with the following roles and responsibilities: **Before authorizing access to the system, information, or performing assigned duties**, and [at least annually] thereafter"
> — [[Sources/NIST-800-53/nist-800-53r5-catalog]]

FedRAMP Moderate and High both set the recurring frequency at **[at least annually]**, but the "before access" language is part of the base control — it is not a parameter and cannot be modified by an organization.

### Roles Subject to AT-3

AT-3 applies to personnel with security or privacy responsibilities, including:
- ISSOs / system security officers
- System owners and authorizing officials
- Database administrators
- Incident responders and contingency planners
- Personnel with access to PII
- Acquisition/procurement officials
- Senior executives with security oversight

> [!info] FedRAMP Moderate Parameter
> AT-3(a)(1): [at least annually]
> AT-3(b): [at least annually]
> — [[Sources/FedRAMP/fedramp-moderate-baseline]]

---

## PL-4: Rules of Behavior — Second Hard Gate

In addition to training, users must acknowledge Rules of Behavior (RoB) before access is granted.

> [!quote] FedRAMP SSP Appendix F — Rules of Behavior Template
> "Receive a documented acknowledgment from such individuals, indicating that they have read, understand, and agree to abide by the rules of behavior, **before authorizing access to information and the system**"
> — [[Sources/FedRAMP/ssp-appendix-f-rules-of-behavior-rob-template]]

RoB acknowledgment must be documented and retained. This applies to all users, not just role-based personnel.

---

## AT-2: General User Training — Integrated with Onboarding

For general (non-role-based) users, AT-2 requires training "as part of initial training for new users." The timing is less prescriptive than AT-3 but is expected to be concurrent with onboarding, not deferred.

> [!quote] NIST 800-53 R5 AT-2(a)(1)
> "As part of initial training for new users and [at least annually] thereafter"
> — [[Sources/NIST-800-53/nist-800-53r5-catalog]]

> [!info] FedRAMP Moderate Parameter
> AT-2(a)(1): [at least annually]
> AT-2(c): [at least annually]
> — [[Sources/FedRAMP/fedramp-moderate-baseline]]

---

## IR-2: Incident Response Training — Post-Access with Time Windows

IR-2 is the exception: it permits access first, with training required within a defined window after assuming the role.

| Role Category | Training Window |
|---|---|
| Privileged users | **10 days** after assuming role |
| Incident Response roles | **30 days** after assuming role |
| All users (recurring) | At least annually |

> [!info] FedRAMP Moderate Parameter
> IR-2(a)(1): [ten (10) days for privileged users, thirty (30) days for Incident Response roles]
> — [[Sources/FedRAMP/fedramp-moderate-baseline]]

---

## What Happens If Training Is Not Completed?

FedRAMP does not define an automatic "training not completed → suspend access" control. Enforcement relies on:

### 1. AT-3 as a Gating Requirement
If a role-based employee was granted access before AT-3 completion, that is itself a control deficiency. The correct finding is a failure of the access provisioning process.

### 2. IR-2 Window Expiration
If the 10- or 30-day IR-2 window is missed, the organization is out of compliance. Corrective action: complete training immediately or disable access until completion.

### 3. AC-2 Account Management Procedures
Organizations must define "training not completed by deadline" as a condition triggering account review or disablement in their SSP procedures. FedRAMP Moderate requires:

> [!quote] NIST 800-53 R5 AC-2(h)
> "Notify account managers and [organization-defined personnel] within [eight (8) hours] when users are terminated or transferred"
> — [[Sources/NIST-800-53/nist-800-53r5-catalog]] / [[Sources/FedRAMP/fedramp-moderate-baseline]]

AC-2(f) and AC-2(l) require that account management processes align with personnel status changes — including policy-defined conditions like missed training deadlines.

> [!tip] SSP Implementation Note
> Define "training non-completion after [N] days" as an account disablement trigger in your AC-2 procedures. This operationalizes the intent of AT-3/IR-2 within the account lifecycle framework. Common practice: 5 business days for AT-3 role-based training, 30 days for AT-2/IR-2.

---

## PS-4 / PS-7: Termination Timelines (Separation, Not Training)

These apply to employee departures and personnel transfers — not training deadlines. Included here for completeness.

| Baseline | Disable Access After Termination |
|---|---|
| FedRAMP Moderate | **4 hours** (PS-4(a)) |
| FedRAMP High | **1 hour** (PS-4(a)) |

> [!info] Cross-Framework Mapping
> AT-3 → AC-2 (access provisioning gate)
> PL-4 → AC-2 (RoB acknowledgment as access condition)
> IR-2 → AC-2 (post-access training window enforcement)
> PS-4 → AC-2(l) (termination-to-account alignment)
