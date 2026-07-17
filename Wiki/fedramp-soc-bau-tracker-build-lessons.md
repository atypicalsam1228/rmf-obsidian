---
type: session-log
framework: fedramp
status: final
tags:
  - fedramp/moderate
  - soc/operations
  - compliance-artifacts
  - lessons-learned
created: 2026-07-06
updated: 2026-07-06
sources:
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
related:
  - "[[source-driven-enumeration-methodology]]"
---

# FedRAMP SOC BAU Tracker — Build Lessons & V5→V6 Gap Analysis

> [!abstract] Summary
> Post-build analysis of the FedRAMP Moderate SOC BAU Tracker V5. Documents missed hard requirements, best-practice/requirement confusion instances, stale citations, and the methodology gaps that caused them. V6 corrects all items.

---

## Stale Citations

### M-21-31 Rescinded

The V5 tracker cited **M-21-31** as the authority for the 18-month offline audit log retention requirement. M-21-31 has been rescinded and replaced by **M-26-14**, which carries slightly less rigid retention timelines.

> [!warning] Stale Citation
> AU-11 (18-Month tab) referenced M-21-31 as justification for offline retention duration. M-21-31 is no longer in effect. M-26-14 is the current federal guidance.

**Corrective action (V6):** The NIST/FedRAMP floor remains AU-11 (online ≥90 days / offline ≥18 months). M-26-14 is cited as the current federal layer above that floor. The specific retention timelines at the end of M-26-14 govern operational compliance.

---

## Missed Hard Requirements (V5 → V6 Additions)

These controls were present in the FedRAMP Moderate baseline with explicit parameter assignments but were omitted from V5.

### Continuous

| Control | Requirement | Why Missed |
|---|---|---|
| CM-8(3)a | Automated detection of unauthorized/new network components | CM-8 categorized as "platform/CM team" at base control level; enhancements not enumerated |
| CM-11(c) | Detection of user-installed unauthorized software (EDR) | Same — CM-11 base control treated as out-of-SOC-scope without checking enhancements |

### Daily / Weekly

| Control | Requirement | Why Missed |
|---|---|---|
| CP-9 | Incremental backup (daily) and full backup (weekly) confirmation | CP family categorized as infrastructure scope; SOC alert-monitoring role not considered |

### Quarterly

| Control | Requirement | Why Missed |
|---|---|---|
| CM-5(5)b | Reevaluate privileges of roles with production change permissions (quarterly) | CM-5 treated as CM team scope; conditional SOC relevance not evaluated |

### Annual

| Control | Requirement | Why Missed |
|---|---|---|
| AT-2a | Security awareness and literacy training — all personnel including SOC | Filtered by "SOC function" axis; missed requirements that apply TO SOC staff regardless of who administers |
| AT-2c | Annual review of training content sufficiency | Same |
| CP-3 | Contingency plan training annually | CP family categorized as infrastructure/COOP without checking SOC participation requirement |
| CP-4a | Contingency plan functional test annually | Same |

### Bi-Annual

| Control | Requirement | Why Missed |
|---|---|---|
| SC-7 | Boundary exception review — at least every 180 days or when threat environment changes | SC-7 task built from function angle (sensor health); parameter-assigned cadence for exception review not enumerated from source |

---

## Root Cause Analysis

Three distinct failure modes produced all gaps:

**1. Base-control-only evaluation** — CM-8 and CM-11 were categorized at the base control level (out-of-scope) without enumerating enhancements. CM-8(3)a and CM-11(c) are detection functions — SOC-relevant — but live under controls mentally filed as platform-team scope.

**2. Function-forward vs. source-forward filtering** — AT-2 was missed because the build filtered by "what functions does SOC perform?" rather than "what requirements apply to SOC personnel?" AT-3 is a function SOC runs. AT-2 is a requirement that runs against SOC staff. Different axis.

**3. Partial parameter enumeration** — SC-7 was captured via the monitoring function but the source document was not read exhaustively for all parameter assignments. The 180-day exception review cadence is a distinct parameter assignment, not derivable from the general monitoring function.

> [!tip] Prevention
> See [[source-driven-enumeration-methodology]] for the corrected 4-step process that prevents all three failure modes.

---

## Best-Practice Instances in V5 Tracker

The following 9 tasks in V5 are **SOC best practice, not hard FedRAMP requirements**. They are retained in V6 but visually distinguished via a "Requirement Type" column.

| Task | Cadence | Why Not a Hard Requirement |
|---|---|---|
| Alert Triage — All Priority Queues | Daily | FedRAMP does not assign a daily triage cadence; supports SI-4/IR-4 but cadence is organizational |
| Threat Intelligence Feed Review | Daily | SI-5 requires maintained subscriptions; daily review cadence is organizational |
| Medium-Severity Alert Pattern Analysis | Weekly | No explicit FedRAMP weekly cadence for medium-severity review |
| High-Use Playbook Review — Top 5 | Monthly | Monthly cadence is organizational; annual full review = IR-4 requirement |
| DLP Alert Review | Monthly | FedRAMP Moderate does not mandate DLP technology |
| IR Tabletop Exercise | Quarterly | IR-3 annual minimum; quarterly frequency exceeds minimum |
| SOC Playbook Full Review | Quarterly | IR-4 requires procedures; quarterly full review is organizational |
| UEBA Baseline Review | Quarterly | FedRAMP Moderate does not mandate UEBA technology |
| CISA KEV Cross-Referencing | Continuous | SI-5 does not name KEV; KEV is CISA guidance, not a FedRAMP Moderate parameter assignment |

> [!danger] NEEDS SOURCE: Quarterly Threat Hunt
> The quarterly threat hunt was cited to CA-7 in V5. CA-7 requires an ongoing monitoring program but does not assign a threat hunting cadence. This task is SOC best practice. Annual pen test detection monitoring (CA-8) remains a hard requirement.

---

## Corrective Action Summary (V6)

- Added 9 new hard-requirement tasks across Continuous, Daily, Weekly, Quarterly, Annual, and Bi-Annual tabs
- Added "Requirement Type" column to all cadence tabs: `Hard Requirement` | `SOC Best Practice`
- Replaced M-21-31 citation with M-26-14 in 18-Month tab
- Relabeled quarterly threat hunt as SOC best practice
- Updated Log Templates to absorb new controls into existing tabs
