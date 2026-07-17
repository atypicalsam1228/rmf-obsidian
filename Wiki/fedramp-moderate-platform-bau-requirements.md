---
type: guide
framework: fedramp
status: draft
tags:
  - bau
  - platform-ops
  - continuous-monitoring
  - multi-tenant
  - fedramp/moderate
created: 2026-06-15
updated: 2026-07-01
sources:
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
  - "[[Sources/FedRAMP/fedramp-continuous-monitoring-playbook]]"
  - "[[Sources/FedRAMP/operational-best-practices-for-fedramp-moderate]]"
  - "[[Sources/FedRAMP/fedramp-rev5-conmon-playbook-introduction]]"
related:
  - "[[Wiki/fedramp-moderate-platform-bau-cadence-training]]"
  - "[[Wiki/fedramp-continuous-monitoring]]"
  - "[[Wiki/fedramp-vulnerability-management]]"
  - "[[Wiki/fedramp-access-control]]"
  - "[[Wiki/tenant-dev-environment-account-management]]"
---

# FedRAMP Moderate Platform BAU Requirements (Multi-Tenant)

> [!abstract] Overview
> This article enumerates the Business As Usual (BAU) operational requirements for a cloud platform operating under a FedRAMP Moderate authorization that hosts tenant organizations. Requirements are organized by control domain. All frequencies and parameters are taken verbatim from the FedRAMP Moderate baseline or cited guidance documents.
>
> For a cadence-organized version suitable for team training, see [[Wiki/fedramp-moderate-platform-bau-cadence-training]].

---

## 1. Vulnerability Scanning & Patch Management

Controls: **RA-5, SI-2**

> [!quote] RA-5(a) — Scan Frequency
> `[monthly operating system/infrastructure; monthly web applications (including APIs) and databases]`
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, RA-5]]

> [!quote] RA-5(2) — Vulnerability Feed Currency
> Vulnerability list update requirement: `[within 24 hours prior to running scans]`
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, RA-5(2)]]

> [!quote] RA-5(d) — Remediation SLAs (from date of discovery)
> - High-risk: `[mitigated within thirty (30) days from date of discovery]`
> - Moderate-risk: `[mitigated within ninety (90) days from date of discovery]`
> - Low-risk: `[mitigated within one hundred and eighty (180) days from date of discovery]`
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, RA-5(d)]]

> [!quote] RA-5 Additional FedRAMP Requirement — Annual Independent Scan
> "An accredited independent assessor scans operating systems/infrastructure, web applications, and databases once annually."
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, RA-5 Additional Requirements]]

> [!quote] SI-2(c) — Patch Installation SLA (from date of release)
> `[within thirty (30) days of release of updates]` for security-relevant software and firmware updates.
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, SI-2(c)]]

> [!quote] SI-2(2) — Automated Patch Status Check
> Automated flaw remediation status check: `[at least monthly]`
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, SI-2(2)]]

> [!warning] RA-5 vs. SI-2 SLA Distinction
> **RA-5 SLAs** measure from *date of discovery* (when the scan finds it).
> **SI-2 SLA** measures from *date of release* (when the vendor publishes the patch).
> These are separate, additive obligations. A newly released patch with a known High CVE must be installed within 30 days of release (SI-2) regardless of when your scanner detects it.

**BAU Tasks:**
- Run OS/infrastructure vulnerability scans — **monthly**
- Run web application and database scans — **monthly**
- Update vulnerability feed — **within 24 hours before each scan run**
- Coordinate annual independent 3PAO scan — **once per year**
- Remediate High findings — **within 30 days of discovery**
- Remediate Moderate findings — **within 90 days of discovery**
- Remediate Low findings — **within 180 days of discovery**
- Deploy security-relevant patches — **within 30 days of vendor release**
- Run automated patch compliance check — **at least monthly**
- Open POA&M for any finding that cannot be remediated within SLA

> [!example] AWS Implementation
> Use Amazon Inspector for OS/container scans and OWASP ZAP or equivalent for web apps. AWS Security Hub aggregates findings. AWS Config rule `ec2-managedinstance-patch-compliance-status-check` enforces SI-2 compliance. GuardDuty High findings require action within 1 day per the AWS Config conformance pack parameters (`GuarddutyNonArchivedFindingsParamDaysHighSev: 1`).

---

## 2. Continuous Monitoring & ConMon Reporting

Controls: **CA-7, CA-5 (POA&M)**

> [!quote]- CA-7 — Continuous Monitoring Program
> CA-7 requires a continuous monitoring strategy including: defined metrics, monitoring frequencies, assessment of controls, and reporting to organizational officials.
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, CA-7]]

> [!quote] FedRAMP ConMon Reporting Requirements
> CSPs must submit ConMon deliverables per the FedRAMP Continuous Monitoring Playbook. Reporting includes monthly packages to the Authorizing Official (AO) and FedRAMP PMO.
> — [[Sources/FedRAMP/fedramp-continuous-monitoring-playbook|FedRAMP ConMon Playbook]]

**BAU Tasks:**
- Submit monthly ConMon package to AO — scan results, POA&M delta, asset inventory updates
- Update POA&M with new findings, status changes, and milestone progress — **monthly**
- Conduct quarterly security control reviews and spot assessments — **quarterly**
- Coordinate annual 3PAO security assessment (SAR) — **annually**
- Review and update SSP — **annually or after any significant change**
- Submit annual assessment results to FedRAMP repository

> [!info] ConMon Package Contents (Monthly)
> Typical monthly package includes: vulnerability scan reports (OS, web app, DB), POA&M (updated), asset/inventory delta, incident summary (even if zero incidents), and any plan of action deviations.

---

## 3. Access Control & Account Management

Controls: **AC-2, IA-2, IA-5**

> [!quote] AC-2(j) — Account Review Frequency
> `[quarterly for privileged access, annually for non-privileged access]`
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, AC-2(j)]]

> [!quote] AC-2(h)(1) — Account No Longer Required
> Notify account managers within `[twenty-four (24) hours]` when accounts are no longer required.
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, AC-2(h)(1)]]

> [!quote] AC-2(h)(2) — User Termination / Transfer
> Notify account managers within `[eight (8) hours]` when users are terminated or transferred.
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, AC-2(h)(2)]]

> [!quote] AC-2(3)(d) — Inactivity-Based Account Disablement
> Disable accounts after `[ninety (90) days]` of inactivity.
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, AC-2(3)(d)]]

> [!quote] IA-2 — Phishing-Resistant MFA (All Users)
> "For all control enhancements that specify multifactor authentication, the implementation must adhere to the Digital Identity Guidelines specified in NIST Special Publication 800-63B."
> "Multi-factor authentication must be phishing-resistant."
> IA-2(1): MFA to privileged accounts — Required
> IA-2(2): MFA to non-privileged accounts — Required
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, IA-2]]

> [!quote] IA-5(1)(h) — Password Minimum Length
> Where MFA is not used, passwords must have `"a minimum length of 14 characters and must support all printable ASCII characters."`
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, IA-5(1)(h)]]

**BAU Tasks:**
- Review privileged accounts for compliance — **quarterly** (AC-2(j))
- Review non-privileged accounts for compliance — **annually** (AC-2(j))
- Disable or terminate accounts when no longer needed — **within 24 hours of notification** (AC-2(h)(1))
- Terminate/disable accounts on employee separation — **within 8 hours** (AC-2(h)(2))
- Disable accounts inactive for 90+ days — **automated check, at least monthly** (AC-2(3)(d))
- Enforce phishing-resistant MFA for ALL users (privileged and non-privileged) (IA-2(1/2))
- Enforce 14-character minimum passwords where MFA is not in use (IA-5(1)(h))
- Rotate IAM access keys — **within 90 days** (AWS Config conformance pack parameter)
- Monitor unused credentials — disable after **90 days** (AWS Config conformance pack parameter)

> [!example] Multi-Tenant Account Management
> For tenant accounts, document account provisioning and deprovisioning procedures in the SSP. See [[Wiki/tenant-dev-environment-account-management]] for tenant-specific account management procedures. Apply the same AC-2 SLAs to tenant user accounts hosted on the platform.

---

## 4. Incident Response

Controls: **IR-6, IR-4, IR-8**

> [!quote] IR-6(a) — Reporting Timeline
> Report security incidents per `[US-CERT incident reporting timelines as specified in NIST Special Publication 800-61 (as amended)]`
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, IR-6(a)]]

> [!quote] IR-6 Additional FedRAMP Requirement
> "Reports security incident information according to the guidance in the FedRAMP Continuous Monitoring Playbook."
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, IR-6 Additional Requirements]]

> [!info] NIST SP 800-61 Reporting Categories
> Reporting timelines depend on incident category and severity. NIST SP 800-61 defines categories including Root Level Intrusion, Unauthorized Access, DoS, Malicious Code, Improper Usage, and Scans/Probes. Major incidents (significant harm, large data breach) typically require reporting within 1 hour. Consult the FedRAMP ConMon Playbook and your system's IR plan for the exact matrix.

**BAU Tasks:**
- Detect, triage, and classify incidents per NIST SP 800-61 category definitions
- Report incidents to US-CERT/CISA per 800-61 timelines and FedRAMP ConMon Playbook guidance
- Report major incidents to AO per your IR plan (typically within 1 hour)
- Include incident summary in monthly ConMon package (zero-incident reports still required)
- Test incident response plan — **annually** (IR-3)
- Update IR plan after significant incidents or annually — **whichever is sooner**

---

## 5. Configuration & Change Management

Controls: **CM-2, CM-3, CM-6**

> [!quote] CM-2(b)(1) — Baseline Configuration Review
> Review and update baseline configuration: `[at least annually and when a significant change occurs]`
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, CM-2(b)(1)]]

> [!quote] CM-6 — Configuration Standards Priority Order
> "The service provider shall use the DoD STIGs to establish configuration settings; Center for Internet Security up to Level 2 (CIS Level 2) guidelines shall be used if STIGs are not available; Custom baselines shall be used if CIS is not available."
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, CM-6 Additional Requirements]]

> [!quote] CM-6 — SCAP Requirement
> "The service provider shall ensure that checklists for configuration settings are Security Content Automation Protocol (SCAP) validated or SCAP compatible (if validated checklists are not available)."
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, CM-6 Additional Requirements]]

**BAU Tasks:**
- Review and update baseline configuration — **at least annually and after any significant change** (CM-2)
- Run configuration compliance scans against DoD STIGs or CIS Level 2 baselines — **monthly**
- Process all configuration changes through the CCB (Change Control Board) (CM-3)
- Notify FedRAMP PMO and AO of significant changes before implementation
- Maintain SCAP-validated or SCAP-compatible configuration checklists (CM-6)
- Update SSP Component Inventory when new components are added or removed

---

## 6. Audit Log Management

Controls: **AU-2, AU-3, AU-6, AU-11, AU-12**

> [!quote] AU-11 — Online Log Retention
> "The service provider retains audit records on-line for at least ninety days and further preserves audit records off-line for a period that is in accordance with NARA requirements."
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, AU-11 Additional Requirements]]

> [!quote] AU-11 — Tenant Export Capability
> "The service provider must either provide a capability for agency customers to export event log files so the agency can comply with federal log storage requirements from M-21-31; or store event log data on behalf of agency customers and make them available to agency customers in compliance with M-21-31."
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, AU-11 Additional Requirements]]

> [!quote] AU-11 — Offline Retention Parameter
> Offline retention: `[a time period in compliance with M-21-31]`
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, AU-11]]

**BAU Tasks:**
- Collect logs from all in-scope system components — **continuous** (AU-12)
- Review and analyze audit logs — **ongoing via automated SIEM alerting** (AU-6)
- Retain audit logs online — **minimum 90 days** (AU-11 additional req)
- Archive audit logs offline — **per NARA retention schedule and M-21-31** (AU-11 parameter)
- Provide tenant log export capability or store on their behalf per M-21-31 (AU-11 additional req)
- Protect audit logs against unauthorized modification or deletion (AU-9)

> [!example] AWS Implementation
> Enable AWS CloudTrail across all accounts and regions. Enable CloudTrail log file validation. Send CloudTrail, VPC Flow Logs, and GuardDuty findings to a centralized S3 bucket with immutable object lock. Forward to SIEM (e.g., Splunk, CloudWatch Logs Insights) for alerting. AWS Config conformance pack rules: `cloud-trail-enabled`, `cloud-trail-encryption-enabled`, `cloud-trail-log-file-validation-enabled`.

---

## 7. Tenant Onboarding & Offboarding (Multi-Tenant Platform)

Controls: **AC-2, PS-4, SA-9**

> [!info] Multi-Tenant Platform Obligation
> As a platform CSP hosting agency tenants, the platform must apply AC-2 account management obligations to all tenant accounts. Tenant onboarding and offboarding procedures must be documented in the SSP and tracked via the POA&M and asset inventory.

**BAU Tasks:**
- Execute tenant provisioning checklist: account creation, boundary documentation, CRM/shared responsibility matrix delivery
- Collect and maintain tenant security contact information
- Issue Customer Responsibility Matrix (CRM) to each tenant at onboarding
- Update CRM if platform controls or shared responsibilities change
- Tenant offboarding: confirm data deletion, revoke all tenant accounts within 8 hours of termination notice (AC-2(h)(2))
- Remove or archive tenant-specific entries from asset inventory after offboarding
- Track active tenant count in SSP system boundary documentation

> [!tip] See Also
> [[Wiki/tenant-dev-environment-account-management]] — Detailed account request fields, approval workflow, and JIRA tracking for tenant environments.

---

## 8. Supply Chain & Third-Party Management

Controls: **SA-9, SR-2, SR-3**

**BAU Tasks:**
- Annual review of all external service providers used within the authorization boundary (SA-9)
- Verify that any cloud services in the boundary maintain current FedRAMP P-ATO or ATO — **annually**
- Review supply chain risk management plan — **annually** (SR-2)
- Notify AO if a third-party provider loses its FedRAMP authorization or has a significant incident
- Update SSP when external services are added or removed from the boundary

---

## 9. Contingency Planning & Backup

Controls: **CP-4, CP-9, CP-2**

> [!quote] CP-4(a) — Contingency Plan Test Frequency and Type
> Test the contingency plan: `[at least annually]` using `[functional exercises]`
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, CP-4(a)]]

> [!quote] CP-4 Additional FedRAMP Requirement
> "The service provider develops test plans in accordance with NIST Special Publication 800-34 (as amended). Results of the contingency plan test are provided to the FedRAMP PMO."
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, CP-4 Additional Requirements]]

> [!quote] CP-9 — Backup Frequency
> - CP-9(a): User-level information: `[daily incremental; weekly full]`
> - CP-9(b): System-level information: `[daily incremental; weekly full]`
> - CP-9(c): System documentation: `[daily incremental; weekly full]`
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, CP-9]]

> [!quote] CP-9 — Minimum Backup Copies
> "The service provider maintains at least three backup copies of user-level information (at least one of which is available online) or provides an equivalent alternative."
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, CP-9 Additional Requirements]]

> [!quote] CP-9(8) — Cryptographic Protection
> Cryptographic protection: `[all backup files]`
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, CP-9(8)]]

> [!quote] CP-9(1) — Backup Test Frequency
> Test backup restoration: `[at least annually]`
> — [[Sources/FedRAMP/fedramp-moderate-baseline|FedRAMP Moderate Baseline, CP-9(1)]]

**BAU Tasks:**
- Run daily incremental backups — **daily** (CP-9)
- Run full backups — **weekly** (CP-9)
- Maintain minimum 3 backup copies, at least 1 online (CP-9 additional req)
- Encrypt all backup files with FIPS-validated cryptography (CP-9(8))
- Verify backup completion and integrity — **weekly at minimum**
- Test backup restoration — **at least annually** (CP-9(1))
- Conduct contingency plan functional exercise — **at least annually** (CP-4(a))
- Develop test plans per NIST SP 800-34; submit results to FedRAMP PMO (CP-4 additional req)

> [!example] AWS Implementation
> AWS Backup with daily + weekly schedule, encrypted with CMK (KMS FIPS endpoint), cross-region replication for 3-copy minimum. Annual disaster recovery exercise using AWS Elastic Disaster Recovery or GameDay format.

---

## 10. Documentation & SSP Maintenance

Controls: **PL-2, CA-5, SA-5**

**BAU Tasks:**
- Review and update SSP — **annually or after any significant change** (PL-2)
- Update POA&M with new findings and milestone changes — **monthly** (CA-5)
- Keep hardware/software/service inventory current — **update with each configuration change**
- Update Customer Responsibility Matrix (CRM) when tenant-facing controls change
- Review and update all required SSP appendices (IR plan, CP, CMP, etc.) per their own review cycles
- Maintain authorization package in FedRAMP repository (current authorized versions)

---

## Quick Reference: Frequency Matrix

| Task | Frequency | Control | Responsible Team |
|---|---|---|---|
| Vulnerability scans (OS, web app, DB) | Monthly | RA-5(a) | DevSecOps / Platform Ops |
| Vulnerability feed update | Within 24h before scan | RA-5(2) | DevSecOps / Platform Ops |
| Patch automated compliance check | Monthly | SI-2(2) | DevSecOps / Platform Ops |
| Security-relevant patch deployment | Within 30 days of release | SI-2(c) | Platform Engineering |
| High vuln remediation | Within 30 days of discovery | RA-5(d) | Platform Engineering + DevSecOps |
| Moderate vuln remediation | Within 90 days of discovery | RA-5(d) | Platform Engineering + DevSecOps |
| Low vuln remediation | Within 180 days of discovery | RA-5(d) | Platform Engineering + DevSecOps |
| Independent assessor scan | Annually | RA-5 (addl req) | GRC / ISSO (coordinates 3PAO) |
| ConMon package to AO | Monthly | CA-7 | GRC / ISSO |
| POA&M update | Monthly | CA-5 | GRC / ISSO |
| Log collection | Continuous | AU-12 | DevSecOps / Platform Ops |
| Audit log online retention minimum | 90 days | AU-11 (addl req) | DevSecOps / Platform Ops |
| Config compliance scan | Monthly | CM-6 | DevSecOps / Platform Ops |
| Baseline config review | Annually + significant changes | CM-2(b)(1) | Platform Engineering + GRC |
| Privileged account review | Quarterly | AC-2(j) | IAM Team + System Owners |
| Non-privileged account review | Annually | AC-2(j) | IAM Team + System Owners |
| Account termination (no longer needed) | Within 24 hours | AC-2(h)(1) | IAM Team / Help Desk |
| Account termination (employee separated) | Within 8 hours | AC-2(h)(2) | HR + IAM Team |
| Inactive account disablement | After 90 days inactivity | AC-2(3)(d) | IAM Team / DevSecOps (automated) |
| IAM access key rotation | Within 90 days | AWS Config (IA-5) | DevSecOps / Platform Ops |
| Daily incremental backup | Daily | CP-9 | Platform Ops (automated) |
| Weekly full backup | Weekly | CP-9 | Platform Ops (automated) |
| Backup restoration test | Annually | CP-9(1) | Platform Ops + GRC |
| Contingency plan test | Annually (functional exercise) | CP-4(a) | GRC / Business Continuity + Platform Ops |
| IR plan test | Annually | IR-3 | Security / IR Team + GRC |
| SSP review/update | Annually + significant changes | PL-2 | GRC / ISSO |
| Supply chain / 3rd party review | Annually | SA-9 | GRC + Procurement |
| Annual security assessment (3PAO) | Annually | CA-2 | GRC / ISSO (coordinates 3PAO) |

> [!info] Cross-Framework Mapping
> These BAU requirements map primarily to NIST 800-53 Rev5 control families: AC (Access Control), AU (Audit & Accountability), CA (Assessment & Authorization), CM (Configuration Management), CP (Contingency Planning), IA (Identification & Authentication), IR (Incident Response), PL (Planning), RA (Risk Assessment), SA (System & Services Acquisition), SI (System & Information Integrity), SR (Supply Chain).
> See [[Wiki/fedramp-nist-800-53-relationship]] for how FedRAMP parameters overlay the base NIST controls.
