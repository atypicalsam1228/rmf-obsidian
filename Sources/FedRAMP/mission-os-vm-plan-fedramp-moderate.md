---
title: "Mission_OS_VM_Plan_FedRAMP_Moderate"
type: reference
framework: fedramp
source_format: converted
created: 2026-05-08
tags:
  - fedramp
  - reference
---

# Mission_OS_VM_Plan_FedRAMP_Moderate

> Source: `Mission_OS_VM_Plan_FedRAMP_Moderate.docx`

Vulnerability Management Plan — FedRAMP Moderate

Mission OS Core — Platform Vulnerability Management Plan

Generated: 2026-05-08

Source: Obsidian RMF vault (Wiki/). Verbatim source citations below appear as block quotes labeled by their original Obsidian callout type. Cross-references to internal vault notes appear as plain text.

## Vulnerability Management Plan — Mission OS Core (FedRAMP Moderate)

[Executive Summary]

This plan defines vulnerability management for the Mission OS Core platform under the FedRAMP Moderate baseline. It satisfies RA-3, RA-5 (and applicable enhancements), SI-2 (and applicable enhancements), CA-5, CA-7, CM-3, CM-8, SI-4, and SI-5. SLAs are taken from FedRAMP-authoritative sources (SAR Appendix B, RAR, ConMon Guide). This plan is tool-agnostic; named tools in source citations are illustrative.

### 1. Purpose and Scope

This document is the platform-level vulnerability management plan for Mission OS Core operating to the FedRAMP Moderate impact level. It governs how the platform identifies, evaluates, prioritizes, remediates, and reports vulnerabilities affecting any component inside the authorization boundary.

In scope (see vm-asset-inventory-and-scope): all platform compute hosts, container images and runtime, platform code, OSS dependencies, exposed web/API surfaces, cloud configuration, managed databases (config-only), network perimeter, and any newly identified asset.

Out of scope: tenant mission applications (covered by separate tenant plans); CSP-inherited firmware (covered by AWS GovCloud).

### 2. Applicable Controls (FedRAMP Moderate)

### 3. Asset Inventory and Scope (CM-8, RA-5(3))

See vm-asset-inventory-and-scope for the full coverage matrix and "newly identified asset" workflow. Inventory is reconciled continuously and reviewed alongside each monthly scan cycle.

[Source Citation] FedRAMP Mod — RA-5

"a. Monitor and scan for vulnerabilities in the system and hosted applications [Assignment: organization-defined frequency and/or randomly in accordance with organization-defined process] and when new vulnerabilities potentially affecting the system are identified and reported;" — FedRAMP Mod RA-5

### 4. Scanning (RA-5)

See vm-scanning-coverage for the full coverage matrix. Summary of FedRAMP-binding requirements:

#### 4.1 Cadence

Monthly authenticated host scans, registry image re-scans, external perimeter scans, and CSPM full review.

Per build / per push for SAST, SCA, secrets, image scans.

Quarterly DAST against externally exposed endpoints.

On-demand rescans to verify closure or in response to threat intel.

#### 4.2 Breadth and Depth (RA-5(3))

Coverage spans every asset class listed in vm-asset-inventory-and-scope. Depth comes from authenticated scans plus complementary techniques (SAST, SCA, DAST, runtime).

#### 4.3 Container Scanning

Mission OS Core implements FedRAMP's Vulnerability Scanning Requirements for Containers: pipeline scans on build, registry scans on push and daily thereafter, and pre-deploy re-scans. SBOMs are produced per build and retained.

#### 4.4 Scanner Updates (RA-5(2))

Scanner signatures/plugins are refreshed within 24 hours prior to running scans, per the FedRAMP Mod parameter (SAR App B RA-05(02)).

#### 4.5 Authenticated / Privileged Scans (RA-5(5))

All host scans are authenticated using vaulted, rotated, least-privileged credentials. Credential failure is an incident, not a "skip."

[Source Citation] Mission OS Core — Authenticated Scans

"The primary method for achieving depth is through authenticated scans using Nessus/ACAS. The ISSO ensures the scanning tools are configured with the necessary privileged credentials..." — Mission OS RA SOP §4.10

### 5. Analysis and Triage (RA-5c, RA-3)

See vm-triage-and-risk-scoring. Severity precedence: CISA KEV → vendor-published → CVSS v3.1 → scanner-assigned. KEV due dates supersede the FedRAMP parameter.

#### 5.1 SLA Clock Start

The remediation clock begins at date of detection (the first scan that surfaced the finding), not date of triage.

#### 5.2 Multi-Tool Correlation (RA-5(10))

Findings from host, container, SAST, SCA, and DAST are normalized into a central aggregation platform, enabling multi-vulnerability / multi-hop attack-path analysis.

#### 5.3 Trend Analysis (RA-5(6))

The aggregation platform computes MTTR per severity, regression rate, and systemic-weakness signals; outputs feed monthly ConMon and the annual control assessment.

#### 5.4 Historical Log Review (RA-5(8))

For each new vulnerability, archived audit logs are searched for indicators that the vulnerability was previously exploited, covering at minimum the prior 365 days.

#### 5.5 Linkage to Monitoring (SI-4, SI-5)

Vulnerability advisories from CISA, vendor PSIRTs, and CSSP threat-intel feeds are ingested and trigger ad-hoc scans / targeted remediation.

### 6. Flaw Remediation (SI-2)

See vm-remediation-slas. Authoritative SLAs for FedRAMP Moderate:

[Source Citation] FedRAMP Mod SAR App B — RA-05d Parameter

"high-risk vulnerabilities mitigated within thirty (30) days from date of discovery; moderate-risk vulnerabilities mitigated within ninety (90) days from date of discovery; low risk vulnerabilities mitigated within one hundred and eighty (180) days from date of discovery" — FedRAMP Mod SAR App B

#### 6.1 Patch Testing (SI-2)

Patches and firmware updates are tested in lower environments before production deployment. Testing covers both effectiveness (does it close the finding) and side effects (does it regress the system).

#### 6.2 Automated Patch Status (SI-2(2))

The aggregation platform reports remediation status, MTTR, and open-finding age automatically.

#### 6.3 Replace-not-Patch (SI-2(6))

Where supported by the platform's IaC/CD model, hosts and containers are replaced rather than patched in place. New images/AMIs go through change control and the CI/CD pipeline; old versions are decommissioned.

### 7. POA&M, ConMon, and Reporting

See vm-poam-and-reporting.

#### 7.1 POA&M (CA-5)

Every legitimate finding becomes a POA&M entry, using the FedRAMP POA&M template field set. POA&Ms close only on verified remediation evidence (preferred: targeted re-scan).

#### 7.2 Continuous Monitoring (CA-7)

Monthly ConMon package — scan output, POA&M, inventory delta, summary metrics, significant-change notices — is produced per the ConMon deliverables template and submitted to the AO.

#### 7.3 Information Sharing (RA-5e)

Findings shared with all AOs, ISSO, ISSE, ISSM, ISO, CSSP/SOC, and (for inheritance-relevant findings) tenant ISSOs.

#### 7.4 Public Disclosure (RA-5(11))

Externally reported vulnerabilities are routed to the appropriate enterprise VDP (FedRAMP allows acceptance of agency-level VDP). Mission OS Core does not run an independent disclosure channel.

#### 7.5 JAB / Agency Tolerance Constraints

Per FedRAMP CSP Timeliness & Accuracy: "There are no late high vulnerabilities on the system open for longer than 30 days from the date of discovery." Late-High count is a leading indicator for ATO risk and must be 0 in monthly submissions.

### 8. Deviations and Exceptions

When SLA cannot be met:

POA&M with milestone schedule (default).

Risk-Based Decision (RBD) signed by AO with compensating controls.

False-Positive (FP) with assessor evidence.

Operational Requirement (OR) for findings whose remediation would break the mission.

Until accepted, the SLA clock continues; the finding is reported as Late.

### 9. Roles and Responsibilities

See vm-roles-and-responsibilities for the full RACI. Platform is the responsible party; tenants own their application-layer findings.

### 10. Plan Maintenance

Reviewed annually as part of CA-7 ConMon strategy review.

Revised when FedRAMP issues updated guidance (e.g., new SAR App B parameter, KEV policy change, container scanning revision).

Versioned in the SSP package; changes flow through change control (CM-3).

### Appendix A — Cross-Reference to NIST 800-53 r5

[Source Citation] NIST 800-53 r5 — RA-5 (skeleton)

"a. Monitor and scan for vulnerabilities in the system and hosted applications [Assignment: organization-defined frequency...] and when new vulnerabilities potentially affecting the system are identified and reported; b. Employ vulnerability monitoring tools and techniques that facilitate interoperability among tools and automate parts of the vulnerability management process by using standards for: 1. Enumerating platforms, software flaws, and improper configurations; 2. Formatting checklists and test procedures; and 3. Measuring vulnerability impact; c. Analyze vulnerability scan reports and results from vulnerability monitoring; d. Remediate legitimate vulnerabilities [Assignment: organization-defined response times] in accordance with an organizational assessment of risk; e. Share information obtained from the vulnerability monitoring process and control assessments with [Assignment: organization-defined personnel or roles]...; f. Employ vulnerability monitoring tools that include the capability to readily update the vulnerabilities to be scanned." — NIST 800-53r5 RA-5

[Source Citation] NIST 800-53 r5 — SI-2 (skeleton)

"a. Identify, report, and correct system flaws; b. Test software and firmware updates related to flaw remediation for effectiveness and potential side effects before installation; c. Install security-relevant software and firmware updates within [Assignment: organization-defined time period] of the release of the updates; d. Incorporate flaw remediation into the organizational configuration management process." — NIST 800-53r5 SI-2

| Control | Topic | Section |
| --- | --- | --- |
| RA-3 | Risk Assessment | §5 Triage |
| RA-5 | Vulnerability Monitoring and Scanning | §4 Scanning |
| RA-5(2) | Update by Frequency / Prior to Scan | §4.4 |
| RA-5(3) | Breadth and Depth | §4.2 |
| RA-5(5) | Privileged Access | §4.5 |
| RA-5(6) | Automated Trend Analysis | §5.4 |
| RA-5(8) | Review Historic Audit Logs | §5.5 |
| RA-5(11) | Public Disclosure Program | §7.4 |
| SI-2 | Flaw Remediation | §6 |
| SI-2(2) | Automated Status | §6.2 |
| SI-2(3) | Time to Remediate | §6.3 |
| SI-4 / SI-5 | Information System Monitoring / Security Alerts | §5.6 |
| CA-5 | POA&M | §7.1 |
| CA-7 | Continuous Monitoring | §7.2 |
| CM-3 / CM-8 | Configuration Change Control / Inventory | §3 Inventory |

| Severity | Remediation SLA from Date of Detection |
| --- | --- |
| High | 30 days |
| Moderate | 90 days |
| Low | 180 days |
| CISA KEV (any sev) | KEV due date (overrides the above) |

