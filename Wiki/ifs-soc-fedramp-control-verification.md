---
type: decision-record
framework: fedramp
status: final
tags:
  - fedramp/moderate
  - soc-operations
  - control-verification
  - audit-logging
  - vulnerability-management
  - incident-response
  - threat-intel
created: 2026-07-15
updated: 2026-07-15
sources:
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
related:
  - "[[Wiki/fedramp-vulnerability-management]]"
  - "[[Wiki/fedramp-continuous-monitoring]]"
---

# IFS SOC FedRAMP Control Verification — 2026-07-15

> [!abstract] Summary
> Source-verified control parameters for FedRAMP Moderate controls cited during the IFS SOC BAU tracker review session. Documents confirmed parameters and three discrepancies where session guidance overstated hard requirements. Discrepancies flagged and corrected below.

---

## Verified Correct

### AU-6(a) — Weekly Audit Log Review

> [!quote] FedRAMP Moderate Baseline — AU-6
> "AU-6 (a)-1 [at least weekly]"
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AU-6 — Audit Record Review, Analysis, and Reporting|AU-6]]

**Confirmed:** AU-6(a) frequency is at least weekly. Hard FedRAMP Moderate parameter. ✅

---

### SI-5(a) — US-CERT and CISA Required

> [!quote] FedRAMP Moderate Baseline — SI-5
> "SI-5 (a) [to include US-CERT and Cybersecurity and Infrastructure Security Agency (CISA) Directives]"
> "SI-5 (c) [to include system security personnel and administrators with configuration/patch-management responsibilities]"
> "SI-5 Requirement: Service Providers must address the CISA Emergency and Binding Operational Directives applicable to their cloud service offering per FedRAMP guidance. This includes listing the applicable directives and stating compliance status."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#SI-5 — Security Alerts, Advisories, and Directives|SI-5]]

**Confirmed:** SI-5(a) explicitly assigns US-CERT and CISA — not organization-discretionary. Hard requirement. ✅

---

### RA-5(d) — Vulnerability Remediation SLAs

> [!quote] FedRAMP Moderate Baseline — RA-5
> "RA-5 (d) [high-risk vulnerabilities mitigated within thirty (30) days from date of discovery; moderate-risk vulnerabilities mitigated within ninety (90) days from date of discovery; low risk vulnerabilities mitigated within one hundred and eighty (180) days from date of discovery]"
> "RA-5 (d) Requirement: If a vulnerability is listed among the CISA Known Exploited Vulnerability (KEV) Catalog the KEV remediation date supersedes the FedRAMP parameter requirement."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#RA-5 — Vulnerability Monitoring and Scanning|RA-5]]

**Confirmed:** High=30d, Moderate=90d, Low=180d. KEV supersedes. ✅

> [!warning] FedRAMP Uses Risk Tiers, Not CVSS Severity Labels
> FedRAMP RA-5(d) uses **high/moderate/low risk** — not CVSS critical/high/medium/low. "Critical" is not a separate FedRAMP tier. CVSS Critical findings are treated as high-risk (30 days) unless in KEV, in which case KEV date governs.

---

### CM-7(2) — Prevent Program Execution

> [!quote] FedRAMP Moderate Baseline — CM-7(2)
> "Prevent program execution in accordance with [Selection (one or more): [Assignment: organization-defined policies, rules of behavior, and/or access agreements regarding software program usage and restrictions]; rules authorizing the terms and conditions of software program usage]."
> "CM-7 (2) Guidance: This control refers to software deployment by CSP personnel into the production environment. The control requires a policy that states conditions for deploying software. This control shall be implemented in a technical manner on the information system to only allow programs to run that adhere to the policy (i.e. allow-listing). This control is not to be based off of strictly written policy on what is allowed or not allowed to run."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#CM-7 (2) — Least Functionality | Prevent Program Execution|CM-7(2)]]

**Confirmed:** CM-7(2) is in FedRAMP Moderate. Technical allowlisting required. ✅

> [!info] CM-7(5) is the Deny-All / Permit-by-Exception Control
> CM-7(2) guidance scopes to CSP software deployments into production. The deny-all, permit-by-exception posture for **authorized software execution** is CM-7(5):
> "Employ a deny-all, permit-by-exception policy to allow the execution of authorized software programs on the system" with quarterly review of the authorized list.
> For fapolicyd implementation on Oracle Linux 9, **CM-7(5) is the more direct control**. CM-7(2) and CM-7(5) are both required and complementary.

---

## Discrepancies — Session Guidance vs. Source

### ⚠️ DISCREPANCY 1: IR-6 Reporting Timeframe

**What was stated in session:** "Major incidents must be reported to US-CERT within 1 hour of identification."

**What the source actually says:**

> [!quote] FedRAMP Moderate Baseline — IR-6
> "IR-6 (a) [US-CERT incident reporting timelines as specified in NIST Special Publication 800-61 (as amended)]"
> "IR-6 Requirement: Reports security incident information according to the guidance in the FedRAMP Continuous Monitoring Playbook."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#IR-6 — Incident Reporting|IR-6]]

**Correction:** The FedRAMP Moderate parameter does not hardcode "1 hour." It defers to NIST SP 800-61 (as amended) timelines and the FedRAMP ConMon Playbook. The 1-hour window is from US-CERT/CISA operational guidance for major incidents — operationally accurate but not the parameter text itself. Templates and triage SLAs should reference "per NIST 800-61 / FedRAMP ConMon Playbook" rather than citing "1 hour" as a FedRAMP baseline parameter.

> [!danger] NEEDS SOURCE: FedRAMP ConMon Playbook IR Reporting Timelines
> Ingest the FedRAMP Continuous Monitoring Playbook to confirm exact IR reporting windows cited in the playbook. Run `/rmf-vault ingest`.

---

### ⚠️ DISCREPANCY 2: AU-11 Online Retention — 90 Days, Not 12 Months

**What was stated in session:** "AU-11 requires 12 months online, 18 months offline."

**What the source actually says:**

> [!quote] FedRAMP Moderate Baseline — AU-11
> "AU-11 [a time period in compliance with M-21-31]"
> "AU-11 Requirement: The service provider retains audit records on-line for at least ninety days and further preserves audit records off-line for a period that is in accordance with NARA requirements."
> "AU-11 Guidance: The service provider is encouraged to align with M-21-31 where possible."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AU-11 — Audit Record Retention|AU-11]]

**Correction:**
- **Hard FedRAMP Moderate requirement:** 90 days online minimum + offline per NARA requirements
- **M-21-31 alignment (12 months online):** Encouraged, not mandated by the FedRAMP Moderate baseline
- **18 months offline:** Not stated in the baseline; dependent on applicable NARA record schedule
- **IFS tracker V6.1** proactively adopted the M-21-31 12-month online standard — this is a self-imposed higher bar, not a FedRAMP Moderate hard requirement

> [!tip] IFS Practical Guidance
> IFS tracker V6.1 has already committed to M-21-31 proactive adoption (12-month online). This is the right approach and exceeds the FedRAMP Moderate minimum. When citing requirements, distinguish between the FedRAMP hard minimum (90 days online) and the M-21-31 standard IFS has self-adopted (12 months online).

---

### ⚠️ DISCREPANCY 3: RA-10 and PM-16 Not Confirmed in FedRAMP Moderate Baseline

**What was stated in session:** RA-10 (Threat Hunting) and PM-16/PM-16(1) (Threat Awareness Program) are FedRAMP Moderate Rev5 requirements.

**What the source shows:** Neither RA-10 nor PM-16/PM-16(1) appear in `fedramp-moderate-baseline.md`. The DoD SRG control crosswalk shows PM-16, PM-16(1), and RA-10 with blank mappings — not mapped to DoD SRG requirements either.

**Correction:** RA-10 and PM-16/PM-16(1) are **not confirmed** as FedRAMP Moderate baseline controls based on current vault sources. Threat hunting (RA-10) appears in NIST 800-53 Rev5 as a control but may not be included in FedRAMP Moderate. PM-16 threat awareness program controls may be organizational-level (PM controls are often not included in system-level baselines).

The SOC BAU tracker includes threat hunting as a quarterly task — this may reflect organizational policy or DoD overlay requirements rather than a FedRAMP Moderate hard requirement.

> [!danger] NEEDS SOURCE: FedRAMP Moderate Control Baseline for RA-10 and PM-16
> Ingest the FedRAMP Moderate Rev5 control baseline (NIST 800-53B Moderate baseline) to confirm whether RA-10 and PM-16/PM-16(1) are included. Current vault source does not contain this confirmation.

---

## Summary Table

| Claim | Source Verdict | Notes |
|---|---|---|
| AU-6(a) = at least weekly | ✅ Confirmed | Hard FedRAMP parameter |
| SI-5(a) requires US-CERT + CISA | ✅ Confirmed | Hard FedRAMP parameter |
| RA-5(d) = 30/90/180 days | ✅ Confirmed | KEV supersedes; uses risk tiers not CVSS labels |
| CM-7(2) in FedRAMP Moderate | ✅ Confirmed | CM-7(5) is the deny-all/permit-by-exception control |
| IR-6 = 1 hour reporting | ⚠️ Imprecise | Defers to NIST 800-61 / ConMon Playbook |
| AU-11 = 12 months online | ⚠️ Overstated | Hard minimum is 90 days; 12 months is M-21-31 encouraged |
| AU-11 = 18 months offline | ⚠️ Unconfirmed | Source says "per NARA requirements" — not a fixed period |
| RA-10 in FedRAMP Moderate | ⚠️ Not confirmed | Not found in vault source |
| PM-16/PM-16(1) in FedRAMP Moderate | ⚠️ Not confirmed | Not found in vault source |
