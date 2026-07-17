---
type: guide
framework: fedramp
status: final
tags:
  - audit-and-accountability
  - fedramp/moderate
  - assessment/questionnaire
  - logging/application
created: 2026-07-01
updated: 2026-07-01
sources:
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
  - "[[Sources/FedRAMP/ssp-appendix-a-moderate-fedramp-security-controls]]"
  - "[[Sources/FedRAMP/aws-config-fedramp-moderate-mappings]]"
related:
  - "[[fedramp-moderate-platform-bau-requirements]]"
  - "[[fedramp-continuous-monitoring]]"
  - "[[cmmc-siem-requirements]]"
---

# FedRAMP Moderate — Application Logging Assessment Questionnaire (AU Family)

> [!abstract] Purpose
> Use this questionnaire to assess application teams' compliance with FedRAMP Moderate AU (Audit and Accountability) controls. Covers AU-1 through AU-12. Each section maps to one or more controls. Collect written responses and supporting evidence before finalizing SSP control implementations or preparing for a 3PAO assessment.

> [!info] Control Coverage
> AU-1 · AU-2 · AU-3 · AU-3(1) · AU-4 · AU-5 · AU-6 · AU-6(1) · AU-6(3) · AU-7 · AU-7(1) · AU-8 · AU-9 · AU-9(4) · AU-11 · AU-12
> Source: [[Sources/FedRAMP/fedramp-moderate-baseline]]

---

## Section 1 — Policy and Procedures (AU-1)

> [!quote]- AU-1 FedRAMP Parameters
> Policy review: at least every **3 years**
> Procedure review: **annually** and after significant changes
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AU-1 — Policy and Procedures|AU-1]]

1. Do you have a documented audit and logging policy? If yes, when was it last reviewed or updated?
2. Do you have documented procedures that describe how audit logging is implemented and maintained for this application?
3. How often are the policy and procedures reviewed — and who is responsible for that review?

**Evidence to provide:** Policy document with version date; procedures document with last-reviewed date.

---

## Section 2 — What Events Are Being Logged (AU-2)

> [!quote]- AU-2 FedRAMP Moderate Required Event Types
> For **all systems**: successful and unsuccessful account logon events, account management events, object access, policy change, privilege functions, process tracking, and system events.
> For **web applications**: all administrator activity, authentication checks, authorization checks, data deletions, data access, data changes, and permission changes.
> Review/update event types: **annually** and whenever there is a change in the threat environment.
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AU-2 — Event Logging|AU-2]]

4. Is your application capable of logging all of the following event types? Mark each that applies:
   - [ ] Successful and unsuccessful login attempts
   - [ ] Account creation, modification, disabling, and deletion
   - [ ] Access to data or objects (reads, writes, queries)
   - [ ] Policy changes
   - [ ] Use of privileged or administrative functions
   - [ ] Process tracking and system events

5. For web applications specifically — does your application log all of the following?
   - [ ] All administrator activity
   - [ ] Authentication checks (pass and fail)
   - [ ] Authorization checks (pass and fail)
   - [ ] Data deletions
   - [ ] Data access
   - [ ] Data changes
   - [ ] Permission changes

6. Which of those event types are **actively being logged right now** versus only capable of being logged?
7. Do you have a documented rationale for why the selected events are sufficient to support incident investigation?
8. How often do you review and update the list of events being logged — and what triggers an out-of-cycle review?

**Evidence to provide:** Documented event type list; logging configuration export or screenshot.

---

## Section 3 — What Each Log Record Contains (AU-3 + AU-3(1))

> [!quote]- AU-3 Required Record Fields
> Each audit record must establish: what type of event occurred, when it occurred, where it occurred, the source of the event, the outcome (success/failure), and the identity of individuals or subjects associated with the event.
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AU-3 — Content of Audit Records|AU-3]]

> [!quote]- AU-3(1) Additional Required Fields (FedRAMP Moderate Enhancement)
> Records must also include: session/connection/transaction/activity duration; for client-server transactions, the number of bytes received and bytes sent; additional informational messages to diagnose or identify the event; characteristics that describe or identify the object or resource being acted upon; individual identities of group account users; full-text of privileged commands.
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AU-3 (1) — Content of Audit Records | Additional Audit Information|AU-3(1)]]

9. Does every audit log record include all of the following **required base fields**?
   - [ ] Event type (what happened)
   - [ ] Timestamp (when it happened)
   - [ ] System or component location (where it happened)
   - [ ] Source of the event (who or what initiated it)
   - [ ] Outcome (success or failure)
   - [ ] Identity of the user or subject associated with the event

10. Do your log records also capture the following **additional required fields** (AU-3(1))?
    - [ ] Session, connection, transaction, or activity duration
    - [ ] Bytes sent and bytes received (for client-server transactions)
    - [ ] Diagnostic messages that help identify what happened
    - [ ] Description of the object or resource that was acted upon
    - [ ] Individual user identity when a shared or group account was used
    - [ ] Full text of privileged commands that were executed

11. Are there any of the above fields your application currently does not capture? If so, which ones and why?

**Evidence to provide:** Sanitized sample log record showing all fields populated.

---

## Section 4 — Log Storage Capacity (AU-4)

> [!quote]- AU-4 Requirement
> Allocate audit log storage capacity to accommodate organization-defined audit log retention requirements.
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AU-4 — Audit Log Storage Capacity|AU-4]]

12. How much storage have you allocated for audit logs?
13. How did you calculate that capacity — what assumptions did you make about log volume and growth rate?
14. What happens when log storage reaches capacity — does the system alert, overwrite, or stop logging?
15. Is log storage capacity monitored, and who is alerted if it is approaching its limit?

**Evidence to provide:** Storage configuration or capacity report; monitoring alert configuration.

---

## Section 5 — What Happens When Logging Fails (AU-5)

> [!quote]- AU-5 FedRAMP Moderate Parameter
> Alert designated personnel in the event of an audit logging process failure.
> Required action: **overwrite oldest records**.
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AU-5 — Response to Audit Logging Process Failures|AU-5]]

16. What does your application do if the audit logging system fails or becomes unavailable?
17. Who gets notified when a logging failure occurs, and how quickly are they notified?
18. What is the documented recovery action — does the system overwrite the oldest records, stop accepting new sessions, or something else?
19. Do you have a runbook or procedure for responding to logging failures?

> [!tip] Assessor Note
> FedRAMP Moderate specifies **overwrite oldest records** as the required failure action. If the team answers "stop logging" or "halt the system," flag for SSP parameter alignment.

**Evidence to provide:** Logging failure alert configuration; runbook or policy excerpt covering failure response.

---

## Section 6 — Log Review and Analysis (AU-6 + AU-6(1) + AU-6(3))

> [!quote]- AU-6 FedRAMP Moderate Parameter
> Review and analyze audit records **at least weekly**.
> In multi-tenant environments, CSPs must document and provide capability for consumers to review data pertaining to their tenant.
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AU-6 — Audit Record Review, Analysis, and Reporting|AU-6]]

20. How often are audit logs actively reviewed and analyzed?
21. Is log review done manually, automated, or both — and what tool or process supports it?
22. Are logs from different system components (application servers, databases, APIs, network devices) correlated together during review, or reviewed in isolation?
23. If this is a multi-tenant environment, can agency customers access and review log data specific to their tenant? How is that capability provided?
24. Where are review findings reported, and who receives them?

> [!tip] Assessor Note
> AU-6(1) requires automated integration; AU-6(3) requires cross-repository correlation. Verify both enhancements are implemented, not just manual review.

**Evidence to provide:** Description or screenshot of weekly review mechanism; SIEM or log aggregation tool configuration showing correlation.

---

## Section 7 — Log Reduction and Reporting (AU-7 + AU-7(1))

> [!quote]- AU-7 Requirement
> Provide an audit record reduction and report generation capability that supports on-demand analysis and reporting without altering original audit records.
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AU-7 — Audit Record Reduction and Report Generation|AU-7]]

25. Do you have a capability to reduce or filter audit logs to support investigation — for example, searching by time range, user, or event type?
26. Can your logging system automatically process and report on log data without altering the original records?
27. What tool or platform provides this capability (e.g., SIEM, CloudWatch Logs Insights, Splunk, Microsoft Sentinel)?

**Evidence to provide:** Demonstration or screenshot of query/report capability.

---

## Section 8 — Timestamps (AU-8)

> [!quote]- AU-8 FedRAMP Moderate Parameter
> Timestamp granularity: **one second**.
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AU-8 — Time Stamps|AU-8]]

28. What time source do all system components sync to for log timestamps (e.g., NTP, AWS Time Sync)?
29. Are timestamps consistent and synchronized across all components that generate logs?
30. What is the granularity of your timestamps — are they accurate to at least one second?

**Evidence to provide:** NTP or time sync configuration; sample log showing timestamp format.

---

## Section 9 — Log Protection (AU-9 + AU-9(4))

> [!quote]- AU-9 / AU-9(4) Requirements
> Protect audit information and audit logging tools from unauthorized access, modification, and deletion.
> Authorize access to management of audit logging functionality to only a defined subset of privileged users or roles.
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AU-9 — Protection of Audit Information|AU-9]]

31. How are audit logs protected from being modified, deleted, or accessed by unauthorized users?
32. Are logs stored separately from the application environment they are monitoring?
33. Are logs write-protected or made immutable after generation (e.g., S3 Object Lock, WORM storage)?
34. Who has administrative access to the logging system — can they modify or delete log records?
35. Is access to log management functions restricted to a small, defined set of privileged users or roles? Who are they?

**Evidence to provide:** IAM role or permission list for log management access; immutable storage configuration (e.g., S3 Object Lock policy).

---

## Section 10 — Retention (AU-11)

> [!quote]- AU-11 FedRAMP Moderate Requirements
> Retain audit records **online for at least 90 days**.
> Preserve offline for a period in accordance with **NARA requirements**.
> CSP must either: (a) provide export capability so the agency can self-manage retention per M-21-31, or (b) store and manage logs on the agency's behalf and make them available in compliance with M-21-31.
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AU-11 — Audit Record Retention|AU-11]]

> [!danger] NEEDS SOURCE: M-21-31
> OMB Memorandum M-21-31 defines Event Logging (EL) maturity tiers but has not been ingested as a vault source. The tier summary below is from training knowledge. Run `/rmf-vault ingest` with the M-21-31 PDF to add authoritative source text.

**M-21-31 Event Logging Maturity Tiers** (from training knowledge pending source ingestion):

| Tier | Hot Storage (Online) | Total Retention | Scope |
|---|---|---|---|
| **EL0** | None | None | Non-compliant baseline |
| **EL1** | 30 days | 12 months | Auth, account mgmt, privileged access |
| **EL2** | 90 days | 12 months | + Network flows, DNS, endpoint events |
| **EL3** | 12 months | 18 months | Full environment; centralized SIEM; immediately queryable |

> [!tip] FedRAMP Moderate floor = EL2 (90 days hot). NARA GRS 3.2 typically requires 3 years total for federal IT records. Agencies may require EL3 or beyond — confirm with your AO.

36. How long are logs kept in **hot storage** — immediately accessible for query and investigation?
37. How long are logs retained in total, including archived or cold storage?
38. Which M-21-31 Event Logging maturity tier do you currently meet?
    - [ ] EL1 — 30 days hot, 12 months total
    - [ ] EL2 — 90 days hot, 12 months total
    - [ ] EL3 — 12 months hot, 18 months total
39. Can the agency **export log data** so they can manage their own retention obligations — or do you retain and manage logs on their behalf and make them available on request?
40. What is your process for producing logs in response to an incident investigation or legal/FOIA request, and what is your response time SLA?

**Evidence to provide:** Retention configuration (screenshot or policy); written statement of M-21-31 tier met; export capability demonstration or data-sharing agreement.

---

## Section 11 — Log Generation Coverage (AU-12)

> [!quote]- AU-12 FedRAMP Moderate Parameter
> Generate audit records on **all information system and network components where audit capability is deployed or available**.
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AU-12 — Audit Record Generation|AU-12]]

41. Which system components generate audit logs? Provide a list — application servers, databases, APIs, network devices, load balancers, WAF, etc.
42. Are there any components **within the system boundary** that do not currently generate audit logs? If so, which ones and why?
43. Do the log records generated match the event types defined in your AU-2 list and contain all fields required by AU-3?

**Evidence to provide:** Component inventory with logging status per component; architecture diagram showing log flow from each component to central storage.

---

## Evidence Summary Checklist

| # | Evidence Item | Control(s) |
|---|---|---|
| 1 | Audit policy with version/review date | AU-1 |
| 2 | Audit procedures with last-reviewed date | AU-1 |
| 3 | Documented event type list currently active | AU-2 |
| 4 | Logging configuration export or screenshot | AU-2 |
| 5 | Sanitized sample log record showing all AU-3 fields | AU-3, AU-3(1) |
| 6 | Storage configuration or capacity report | AU-4 |
| 7 | Logging failure alert configuration | AU-5 |
| 8 | Runbook or policy for logging failure response | AU-5 |
| 9 | Weekly review mechanism (screenshot or description) | AU-6 |
| 10 | SIEM/aggregation config showing cross-component correlation | AU-6(3) |
| 11 | Log query/report capability demonstration | AU-7 |
| 12 | NTP or time sync configuration | AU-8 |
| 13 | IAM role/permission list for log management access | AU-9(4) |
| 14 | Immutable storage configuration (e.g., S3 Object Lock) | AU-9 |
| 15 | Retention configuration screenshot or policy | AU-11 |
| 16 | Written M-21-31 tier statement with supporting config | AU-11 |
| 17 | Log export capability demonstration or agency agreement | AU-11 |
| 18 | Component inventory with logging status per component | AU-12 |
| 19 | Architecture diagram showing log flow | AU-12 |
