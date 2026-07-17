---
type: guide
framework: cross-framework
status: final
tags:
  - methodology
  - compliance-artifacts
  - fedramp
  - process
created: 2026-07-06
updated: 2026-07-06
sources:
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
related:
  - "[[fedramp-soc-bau-tracker-build-lessons]]"
---

# Source-Driven Enumeration Methodology

> [!abstract] Purpose
> A 4-step process for building compliance artifacts (trackers, SSP sections, control mappings) that prevents missed requirements, best-practice/requirement confusion, and partial parameter enumeration. Derived from failure analysis of the FedRAMP SOC BAU Tracker V5 build.

---

## Why This Exists

Three failure modes in the V5 tracker build produced missed hard requirements:

1. **Base-control-only evaluation** — Enhancements were not enumerated; detection functions living under "out-of-scope" base controls were missed (CM-8(3)a, CM-11c).
2. **Function-forward filtering** — The build asked "what does this role do?" instead of "what requirements apply to this role?" — causing requirements that apply *to* personnel (AT-2) to be missed while only capturing requirements assigned *to* functions (AT-3).
3. **Partial parameter enumeration** — Controls were captured at the function level without reading all assigned parameters in source (SC-7 180-day exception review).

This methodology prevents all three.

---

## The 4-Step Process

### Step 1 — Keyword Generation (from source docs only)

> [!warning] Never use recall for this step
> Keywords must be extracted from the source document verbatim. Using recalled knowledge to decide what's in scope introduces the exact bias this step is designed to eliminate.

**Action:** Read the full source document (e.g., `fedramp-moderate-baseline.md`) and extract every functional term that could describe a role-specific activity.

**Example keyword corpus for SOC scope:**
```
detection, monitoring, audit, incident, scan, vulnerability, signature,
alert, triage, malicious code, threat intelligence, advisory, directive,
training, awareness, personnel, review, backup, recovery, boundary,
unauthorized, software, component, asset, privilege, access, log,
retention, integrity, verification, reporting
```

**Output:** Keyword list with source line number references — not a mental model.

**Key principle:** The source text decides what's in scope. You do not.

---

### Step 2 — Control Match & Full Enumeration

**Action:** Search source document using Step 1 keywords. For every matched control:

1. **Read the base control AND all enhancements** — never stop at the base
2. **Record every parameter assignment** — cadence, scope, field values, personnel designations
3. **Tag each item:**
   - `Hard Requirement` — explicit parameter assignment exists in source
   - `Best Practice` — no parameter assignment; organizational addition
4. **Control family completeness check** — for each matched base control, confirm every enhancement was reviewed before moving on

> [!example] What this catches
> - CM-8(3)a and CM-11(c): keywords "detection," "unauthorized," "component," "software" match; enhancements read → detection functions found
> - AT-2: keywords "training," "awareness," "all personnel" match → AT-2 found separately from AT-3
> - SC-7 180-day: keyword "boundary" matches → all SC-7 parameter assignments read → 180-day exception review cadence found

---

### Step 3 — Cross-Reference / Production

**Action:** Build the artifact from the enumerated set only.

**Rules:**
- Every item in the artifact must have a source citation with specific parameter assignment
- Items without citations are blocked from the artifact
- Best-practice items must be visually distinct from hard requirements (separate column, color, or section)
- Never merge best practices and hard requirements into a single undifferentiated list

---

### Step 4 — Accuracy Check

**Action:** Repeat Steps 2–3 against the source. Do NOT regenerate keywords (Step 1 is run once per artifact build).

**Checklist:**
- [ ] Re-run keyword search — compare hits against artifact; flag anything in source not in artifact
- [ ] For every base control in artifact: confirm all enhancements were reviewed
- [ ] For every item tagged "Best Practice": verify no parameter assignment exists in source
- [ ] Output a gap list — artifact is not complete until gap list is empty or gaps are explicitly accepted

---

## Application to Specific Artifact Types

| Artifact | Step 1 Keyword Focus | Common Miss Pattern |
|---|---|---|
| Role-specific tracker (SOC, ISSO) | Functions the role performs AND requirements that apply to the role's personnel | Filtering only by function; missing requirements that run against the personnel |
| SSP control implementations | All parameter assignments for each control family | Partial parameter capture; missing enhancement-assigned requirements |
| Evidence matrix | Control parameter assignments + cadences | Cadence mismatches when function is captured but specific cadence parameter is not |
| Training/awareness compliance | "training," "awareness," "personnel," "annually," "within [X] days" | AT-2 vs AT-3 conflation; missing onboarding window parameters |

---

## Quick Reference — Common Missed Patterns

| Failure Mode | Prevention |
|---|---|
| Base control filed as out-of-scope → enhancements missed | Always enumerate enhancements before categorizing a control family |
| Function-forward filtering misses personnel-requirement controls | Ask both: "what does this role do?" AND "what applies to this role's staff?" |
| Partial parameter enumeration | Read full source text for matched controls; do not derive parameters from functional knowledge |
| Best practices presented as requirements | Tag before producing; block untagged items from artifact |
| Recall-based keyword generation | Step 1 always from source text; never from memory |
