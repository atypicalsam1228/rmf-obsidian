---
type: concept
framework: nist-800-171
status: draft
tags:
  - audit-accountability
  - siem
  - cmmc
  - log-management
  - nist-800-171
created: 2026-06-26
updated: 2026-06-26
sources:
  - "[[Sources/NIST-800-171/nist-800-171r3-security-requirements]]"
  - "[[Sources/NIST-800-171/aws-config-nist-800-171-mappings]]"
related:
  - "[[Wiki/nist-800-53-control-families]]"
  - "[[Wiki/cmmc-l2-asset-category-control-reference]]"
---

# CMMC SIEM Requirements

> [!abstract] Summary
> CMMC Level 2 does not mandate a SIEM product by name, but the nine Audit & Accountability (AU) practices collectively require what a SIEM delivers: centralized log collection, user-traceable records, cross-system correlation, automated alerting on failure, on-demand reduction and reporting, and immutable protected storage. A SIEM is the standard implementation vehicle — explicitly named as the expected answer in CCP exam materials.

---

## The AU Domain Drives SIEM

All nine AU practices are **CMMC Level 2** (required for any organization handling CUI under 32 CFR Part 170). They map directly to NIST SP 800-171r3 §3.3.

> [!quote] AU.L2-3.3.1 — SYSTEM AUDITING
> "Create and retain system audit logs and records to the extent needed to enable the monitoring, analysis, investigation, and reporting of unlawful or unauthorized system activity."
> — [[Sources/NIST-800-171/nist-800-171r3-security-requirements|NIST 800-171r3 §3.3.1]]

**SIEM implication:** Centralized ingestion from all in-scope systems. Audit records must include timestamps, source/destination addresses, user/process identifiers, event descriptions, success/failure indicators, and filenames involved. Privileged command full-text recording is recommended.

> [!quote] AU.L2-3.3.2 — USER ACCOUNTABILITY
> "Ensure that the actions of individual system users can be uniquely traced to those users so they can be held accountable for their actions."
> — [[Sources/NIST-800-171/nist-800-171r3-security-requirements|NIST 800-171r3 §3.3.2]]

**SIEM implication:** Log records must carry user identity, not just IP or process ID. Shared/service accounts require special handling. Account usage, remote access, VPN, wireless, mobile device connections, and configuration changes all require logging.

> [!quote] AU.L2-3.3.4 — AUDIT FAILURE ALERTING
> "Alert in the event of an audit logging process failure."
> — [[Sources/NIST-800-171/nist-800-171r3-security-requirements|NIST 800-171r3 §3.3.4]]

**SIEM implication:** Automated alerting when log sources go silent, storage capacity is reached, or the log pipeline fails. Applies per-repository and to aggregate storage. AWS implementations: Security Hub + GuardDuty satisfy this via [[Sources/NIST-800-171/aws-config-nist-800-171-mappings|AWS Config NIST 800-171 mappings]].

> [!quote] AU.L2-3.3.5 — AUDIT CORRELATION
> "Correlate audit record review, analysis, and reporting processes for investigation and response to indications of unlawful, unauthorized, suspicious, or unusual activity."
> — [[Sources/NIST-800-171/nist-800-171r3-security-requirements|NIST 800-171r3 §3.3.5]]

**This is the core SIEM function.** Cross-system event correlation for threat detection and investigation. The requirement is explicitly agnostic as to whether correlation is applied per-system or organization-wide — a single SIEM across all systems satisfies this.

> [!quote] AU.L2-3.3.6 — REDUCTION & REPORTING
> "Provide audit record reduction and report generation to support on-demand analysis and reporting."
> — [[Sources/NIST-800-171/nist-800-171r3-security-requirements|NIST 800-171r3 §3.3.6]]

> [!example] CCP Exam — Official Answer
> Q: "What is the most common solution used to perform AU.L2-3.3.6 (REDUCTION & REPORTING)?"
> **A: SIEM** — Security Information and Event Management provides automated audit record reduction and reporting capabilities.
> — CCP Course Workbook v4.0, Audit & Accountability domain

---

## Supporting Practices That Shape SIEM Architecture

| Practice | Statement | SIEM Implication |
|---|---|---|
| **3.3.3** EVENT REVIEW | Review and update logged event types | Periodic review of ingestion scope; documented event taxonomy; not about reviewing log content |
| **3.3.7** AUTHORITATIVE TIME | Sync internal clocks to authoritative source for timestamps | All log sources must NTP-sync before forwarding; clock drift breaks correlation |
| **3.3.8** AUDIT PROTECTION | Protect audit info from unauthorized access, modification, deletion | Immutable log storage (S3 Object Lock / WORM); restrict delete/modify permissions |
| **3.3.9** AUDIT MANAGEMENT | Limit management of audit logging to a subset of privileged users | Separate SIEM-admin role from general IT admin; audit-admin is a distinct privilege |

> [!tip] 3.3.3 Gotcha
> AU.L2-3.3.3 (EVENT REVIEW) is about reviewing and updating **which event types are logged** — not reviewing log content. Reviewing log content for threats is covered by 3.3.5. A weekly log review by a security admin does **not** satisfy 3.3.3.

---

## Log Retention

> [!quote] DFARS 252.204-7012 — Incident Data Preservation
> Organizations must preserve images of all known or reasonably suspected compromised systems and all relevant monitoring/packet capture data for **at least 90 days**, and support DoD damage assessment activities for **at least 90 days**. Effective retention for incident data: **180 days total**.

For non-incident log retention, NIST 800-171r3 defers to organizational policy. Assessors expect a documented retention period with logs actually retained to match. A common defensible baseline is **1 year** for general audit logs.

---

## Required Log Sources (In-Scope CUI Environment)

Based on 3.3.2 (user traceability) and 3.3.5 (correlation), a SIEM covering a CUI environment must ingest:

- Authentication events — login, logout, failure — from identity systems, VPN, remote access
- Privileged command execution (full-text recording recommended)
- Account lifecycle events (create / modify / disable / delete)
- Network flows — firewall, VPC flow logs, proxy
- File access on CUI repositories
- Configuration changes on in-scope systems
- Endpoint security events (EDR/AV detections)
- Cloud API calls (CloudTrail or equivalent)
- Wireless and mobile device connections (per 3.3.2 discussion)

---

## AWS Implementation Mapping

From [[Sources/NIST-800-171/aws-config-nist-800-171-mappings|AWS Config NIST 800-171 mappings]]:

| 800-171 Practice | AWS Config Rules |
|---|---|
| 3.3.1 (log creation/retention) | `cloudtrail-enabled`, `multi-region-cloudtrail-enabled`, `cloud-trail-cloud-watch-logs-enabled`, `vpc-flow-logs-enabled`, `s3-bucket-logging-enabled`, `elb-logging-enabled`, `rds-logging-enabled`, `guardduty-enabled-centralized` |
| 3.3.2 (user traceability) | `cloudtrail-enabled`, `cloud-trail-cloud-watch-logs-enabled`, `api-gw-execution-logging-enabled` |
| 3.3.4 (failure alerting) | `securityhub-enabled`, `guardduty-enabled-centralized` |
| 3.3.5 (correlation) | `securityhub-enabled`, `guardduty-enabled-centralized` |
| 3.3.8 (log protection) | `cloud-trail-log-file-validation-enabled`, `s3-bucket-default-lock-enabled`, `s3-bucket-versioning-enabled`, `s3-bucket-public-read-prohibited` |

> [!danger] NEEDS SOURCE
> CMMC Assessment Guide Level 2 (v2.0) and 32 CFR Part 170 are not yet ingested into Sources/. Practice text above is sourced from NIST 800-171r3 and CCP exam workbook. Run `/rmf-vault ingest` to add the CMMC Assessment Guide as an authoritative source.

---

> [!info] Cross-Framework Mapping
> - **NIST 800-53:** AU-2, AU-3, AU-6, AU-9, AU-12 (direct parents of these practices)
> - **FedRAMP Moderate:** AU family required; AU-6 (review/analysis) is the FedRAMP analogue to 3.3.5
> - **CMMC Level 2:** All 9 AU practices required (no optional practices in AU domain)
