---
type: concept
framework: nist-800-53
status: final
tags:
  - policy-and-procedures
  - documentation
  - ssp
  - assessment
created: 2026-06-25
updated: 2026-06-25
sources:
  - "[[Sources/NIST-800-53/nist-800-53r5-catalog]]"
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
related:
  - "[[Wiki/fedramp-documentation-requirements]]"
  - "[[Wiki/fedramp-authorization-process]]"
  - "[[Wiki/nist-800-53-control-families]]"
---

# Policy and Procedures — Requirements and SSP Satisfaction

> [!abstract] Summary
> Procedures are independently required by every XX-1 control across all 20 NIST 800-53 control families. The SSP can satisfy the procedures requirement — but only if it contains actual role-specific, step-by-step implementation content. Simply restating control text fails.

## Are Procedures Required?

Yes. Every control family has an XX-1 control (AC-1, AT-1, AU-1, CA-1, CM-1, etc.) that requires both a **policy** and **procedures** document. A policy alone does not satisfy the control.

> [!quote] NIST 800-53r5 — AC-1 Discussion (identical across all XX-1 controls)
> "Procedures describe how the policies or controls are implemented and can be directed at the individual or role that is the object of the procedure."
> — [[Sources/NIST-800-53/nist-800-53r5-catalog#AC-1 — Policy and Procedures|AC-1]]

> [!warning] Critical Disqualifier
> "**Simply restating controls does not constitute an organizational policy or procedure.**"
> — [[Sources/NIST-800-53/nist-800-53r5-catalog#AC-1 — Policy and Procedures|AC-1 Discussion]]
>
> An SSP section that copies NIST control text verbatim does not satisfy this requirement. Assessors will mark it as a finding.

## Does the SSP Satisfy the Procedures Requirement?

Yes — NIST explicitly permits it, subject to a content quality condition.

> [!quote] NIST 800-53r5 — AC-1 Discussion (identical across all XX-1 controls)
> "Procedures can be documented in **system security and privacy plans** or in **one or more separate documents**."
> — [[Sources/NIST-800-53/nist-800-53r5-catalog#AC-1 — Policy and Procedures|AC-1]]

The SSP and standalone procedures documents are both acceptable. The format is the organization's choice. What matters is content quality.

## Review Cadences

> [!quote] FedRAMP Moderate Baseline — AC-1(c)
> `AC-1 (c) (1) [at least every 3 years]`  — Policy document
> `AC-1 (c) (2) [at least annually] [significant changes]` — Procedures
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AC-1|AC-1(c)]]

| Document | Review Frequency |
|---|---|
| Policy | At least every 3 years |
| Procedures | At least annually + after significant changes |

Event-driven triggers (audit findings, incidents, regulatory changes) require immediate review regardless of the calendar.

## Acceptable vs. Failing Approaches

| Approach | Acceptable? | Notes |
|---|---|---|
| Standalone procedures doc (separate from SSP) | Yes | Always acceptable |
| SSP contains role-specific, step-by-step procedures | Yes | Satisfies XX-1 if content is substantive |
| SSP restates control text only | **No** | Explicitly disqualified by NIST |
| Policy document with no procedures anywhere | **No** | Procedures are independently required |

## What Assessors Look For

Procedures must be **testable** — an assessor should be able to compare the written procedure against observed practice. Vague language fails; specificity passes.

> [!example] Failing vs. Passing Procedure Language
>
> **Fails:** "The organization reviews accounts periodically."
>
> **Passes:** "Managers review and certify privileged accounts quarterly (every 90 days) in the access management tool. Uncertified accounts are disabled after 5 business days with no response." (AC-2j)

Minimum elements for a testable procedure:
- **Who** — specific role or position responsible
- **What** — the discrete action taken
- **When** — concrete timeframe or trigger condition
- **How** — tool, system, or method used
- **Evidence** — what artifact proves it happened

## Cross-Framework Note

> [!info] Cross-Framework Mapping
> The SSP-as-procedures flexibility is a NIST 800-53 construct. Related frameworks handle this differently:
> - **NIST 800-171**: Requires a System Security Plan (SSP) and a Plan of Action (POA&M); procedures embedded in the SSP are acceptable
> - **FedRAMP**: SSP is the primary artifact; procedures are expected in SSP control implementation descriptions or as attachments
> - **CMMC**: Requires documented policies AND procedures as separate evidence; embedded SSP procedures may not satisfy the auditor depending on the C3PAO
>
> See [[Wiki/fedramp-documentation-requirements]] for FedRAMP-specific document requirements.
