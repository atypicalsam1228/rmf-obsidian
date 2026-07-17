---
type: guide
framework: fedramp
status: draft
tags:
  - bau
  - platform-ops
  - training
  - cadence-reference
  - fedramp/moderate
  - multi-tenant
created: 2026-06-15
updated: 2026-06-15
sources:
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
  - "[[Sources/FedRAMP/fedramp-continuous-monitoring-playbook]]"
  - "[[Sources/FedRAMP/operational-best-practices-for-fedramp-moderate]]"
related:
  - "[[Wiki/fedramp-moderate-platform-bau-requirements]]"
  - "[[Wiki/fedramp-continuous-monitoring]]"
  - "[[Wiki/fedramp-vulnerability-management]]"
  - "[[Wiki/fedramp-access-control]]"
  - "[[Wiki/tenant-dev-environment-account-management]]"
---

# FedRAMP Moderate Platform BAU — Team Training Reference

> [!abstract] Who This Is For
> This guide is for platform engineers, DevSecOps, and operations staff maintaining a FedRAMP Moderate authorized platform that hosts tenant organizations. It tells you **what to do**, **why it matters for your authorization**, and **what evidence you produce** — organized by *when* you do it, not by control number.
>
> For the control-by-control reference with exact quoted requirements, see [[Wiki/fedramp-moderate-platform-bau-requirements]].

> [!tip] The Stakes
> FedRAMP is a continuous authorization — you have to *maintain* it, not just pass a one-time audit. If you fall behind on ConMon deliverables, your Authorizing Official (AO) can place the system in remediation status or revoke the authorization. Every task in this guide is either a control parameter, a ConMon deliverable, or a condition your 3PAO will test at your annual assessment.

---

## Continuous / Real-Time

These are automated or always-on processes. A human needs to set them up correctly — but once running, they don't require manual scheduling.

### Log Collection & Forwarding

**What to do:** Ensure all in-scope components (servers, containers, APIs, databases, network devices, IAM services) ship logs to a centralized log aggregation system (SIEM or log archive).

**Why:** AU-12 requires audit record generation from all components. AU-11 requires retention. If a component stops sending logs, you have an unmonitored gap your 3PAO will flag.

**Evidence produced:** SIEM connectivity dashboards; log source inventory reconciled against your SSP component list.

---

### SIEM Alerting

**What to do:** Maintain and tune alert rules for: failed authentication, privilege escalation, account creation/deletion outside approved workflow, configuration changes, network anomalies, malware detections.

**Why:** AU-6 requires automated analysis of audit records. If SIEM alerting is not active, you cannot meet your incident detection obligations under IR-4.

**Evidence produced:** Alert rule inventory; alert response tickets/cases; SIEM dashboard screenshots in ConMon packages.

---

### Automated Configuration Compliance

**What to do:** Keep AWS Config conformance packs (or equivalent) active and feeding findings to Security Hub. Config rules must reflect your approved baseline (DoD STIGs → CIS Level 2 → custom, per CM-6).

**Why:** CM-6 requires continuous compliance with configuration baselines. Non-compliant resources are findings that must be tracked in the POA&M.

**Evidence produced:** AWS Config compliance dashboard; non-compliant resource list; Security Hub findings feed.

---

### Backup Jobs Running

**What to do:** Automated daily incremental and weekly full backup jobs must run and complete successfully. Alerts should fire on backup job failures.

**Why:** CP-9 requires daily incremental and weekly full backups. A missed backup is a control gap — document it in the POA&M if recurring.

**Evidence produced:** Backup job completion logs; AWS Backup reports.

---

## Daily

### Alert Triage & Response

**What to do:** Review new SIEM/Security Hub alerts. Triage by severity. For actionable alerts, open incident or change tickets. Close false positives with documented rationale.

**Why:** Unactioned alerts from AU-6 analysis can indicate an ongoing IR-4 incident. Response timelines depend on incident category per NIST SP 800-61 — High severity events may require reporting to US-CERT within hours.

**Evidence produced:** Alert triage log or ticketing system entries; incident tickets if escalated.

---

### GuardDuty High-Severity Finding Review

**What to do:** Review GuardDuty findings daily. High-severity findings (e.g., crypto mining, exposed credentials, known malicious IPs) require same-day investigation and action.

**Why:** FedRAMP conformance pack sets `GuarddutyNonArchivedFindingsParamDaysHighSev: 1` — High findings must be addressed within 1 day. These findings often map to IR-4 incidents.

**Evidence produced:** GuardDuty finding disposition record; incident ticket if confirmed.

---

### Failed Authentication Review

**What to do:** Review failed authentication patterns. Spikes in failed logins for privileged accounts warrant investigation and possible account lockout or IR escalation.

**Why:** AC-7 requires enforcement of consecutive failed login limits. Patterns indicating brute force are IR-4 events.

**Evidence produced:** Auth log review record; ticket if escalated.

---

## Weekly

### Patch Status Review

**What to do:** Review open vulnerability findings and patch status. Confirm High findings discovered in this month's scan are on track for 30-day remediation. Escalate any that are at risk of missing SLA.

**Why:** SI-2 requires patches within 30 days of vendor release; RA-5 requires High vulnerability remediation within 30 days of discovery. Missed SLAs open POA&M items and are scored negatively in the annual assessment.

**Evidence produced:** Patch tracking spreadsheet or ticketing system status; escalation record for at-risk items.

---

### POA&M Aging Review

**What to do:** Review all open POA&M items. Flag any approaching their scheduled completion date. If a milestone will be missed, document the deviation and update the milestone before it lapses.

**Why:** The AO reviews your POA&M monthly. Missed milestones without documented deviations signal poor risk management discipline and can trigger remediation status.

**Evidence produced:** Updated POA&M (even if no changes, note that review was performed).

---

### Backup Job Verification

**What to do:** Verify the weekly full backup completed successfully. Spot-check one or two restoration operations if feasible (even a partial restore of a single file).

**Why:** CP-9(1) requires annual backup restoration tests, but weekly verification that jobs complete is basic operational hygiene. Backup failures not caught early can leave you without recovery capability.

**Evidence produced:** Backup completion report; restoration test record.

---

### GuardDuty Medium-Severity Review

**What to do:** Review and disposition any unarchived Medium-severity GuardDuty findings.

**Why:** FedRAMP conformance pack sets `GuarddutyNonArchivedFindingsParamDaysMediumSev: 7` — Medium findings must be addressed within 7 days.

**Evidence produced:** GuardDuty finding disposition record.

---

## Monthly

Monthly is the core BAU cadence for FedRAMP. Most ConMon deliverables are monthly.

### Vulnerability Scans (OS, Web App, Database)

**What to do:** Run authenticated scans against all in-scope operating systems, infrastructure, web applications (including APIs), and databases. Use a SCAP-validated or SCAP-compatible scanner. Update vulnerability feed within 24 hours before running scans.

**Why:** RA-5(a) explicitly requires monthly scans for all three asset types. Scan frequency is one of the first things a 3PAO checks. An unscanned month = a ConMon gap.

**Evidence produced:** Scan reports (raw scanner output + summary) for OS, web app, and DB; included in monthly ConMon package.

---

### POA&M Update

**What to do:** Update the POA&M with:
- New findings from this month's scans
- Remediation progress on open items
- Closed items (with evidence of remediation)
- Any missed milestones with documented deviations
- Risk acceptances approved by the AO

**Why:** CA-5 requires POA&M maintenance. The AO uses the monthly POA&M to assess the system's risk posture. It is a primary ConMon deliverable.

**Evidence produced:** Updated POA&M file submitted to AO.

---

### ConMon Package Submission to AO

**What to do:** Compile and submit the monthly Continuous Monitoring package to your Authorizing Official. Package includes:
- Vulnerability scan reports (OS, web app, DB)
- Updated POA&M
- Asset/inventory delta (any additions, removals, or changes since last month)
- Incident summary (report zero incidents if none occurred — silence is not acceptable)
- Any significant change notifications or deviation requests

**Why:** This is the primary mechanism by which the AO tracks whether your authorization should remain active. Missing a monthly package is grounds for remediation status.

**Evidence produced:** ConMon submission confirmation; dated package archive.

---

### Asset Inventory Delta

**What to do:** Compare the current hardware/software/service inventory against last month's snapshot. Document all additions, removals, and changes. Update the SSP inventory appendix.

**Why:** CA-7 continuous monitoring requires tracking of the system boundary. Unauthorized or untracked assets are a finding. A new cloud service added without updating the inventory is a boundary violation.

**Evidence produced:** Inventory delta report included in ConMon package.

---

### Configuration Compliance Scan

**What to do:** Run configuration compliance scans (using DoD STIGs, CIS Level 2, or your approved custom baseline) against in-scope systems. Open POA&M items for non-compliant settings that cannot be immediately remediated.

**Why:** CM-6 requires compliance with configuration baselines. Monthly scanning keeps you continuously aware of drift rather than discovering it at annual assessment time.

**Evidence produced:** Configuration scan report; new POA&M items for non-compliant findings.

---

### Automated Patch Compliance Check

**What to do:** Run SI-2(2) automated flaw remediation status check. Confirm all systems show current patch status. Flag any systems behind on security patches.

**Why:** SI-2(2) explicitly requires at least monthly automated status checks for patch compliance.

**Evidence produced:** Patch compliance report; escalation tickets for non-compliant systems.

---

### Inactive Account Sweep

**What to do:** Run automated check or manual report of all accounts with no activity in 90+ days. Disable identified accounts per AC-2(3)(d). Document which accounts were disabled and why.

**Why:** AC-2(3)(d) requires disabling accounts after 90 days of inactivity. Stale accounts are frequently cited findings in FedRAMP assessments.

**Evidence produced:** Inactive account report; list of accounts disabled with timestamps.

---

### IAM Credential Audit

**What to do:** Review all IAM access keys. Disable or rotate any keys older than 90 days. Check for unused credentials (console passwords or access keys with no recent activity).

**Why:** FedRAMP conformance pack enforces 90-day key rotation (`IamUserUnusedCredentialsCheckParamMaxCredentialUsageAge: 90`). Stale credentials are an IA-5 finding.

**Evidence produced:** Access key age report; rotation or disablement records.

---

## Quarterly

### Privileged Account Recertification

**What to do:** Conduct a formal access review of all accounts with privileged access (admin, root, elevated IAM roles). For each account: confirm the individual still requires the access, confirm the access level is appropriate (least privilege), and document the review decision.

**Why:** AC-2(j) sets the FedRAMP Moderate parameter for privileged account reviews at **quarterly**. This is more frequent than the default NIST recommendation. If you don't have records showing quarterly reviews, you'll have a finding.

**Evidence produced:** Privileged account recertification report signed by the system owner or ISSO; access review tickets in ITSM.

---

### Security Control Spot Assessment

**What to do:** Select 3–5 controls from your SSP each quarter for a spot check against the current implementation. Verify the control is implemented as documented. If there's a gap (the SSP says X but the system does Y), update the SSP or open a POA&M item.

**Why:** CA-7 requires ongoing control assessments as part of your continuous monitoring strategy. Annual 3PAO assessments are the formal test, but quarterly self-assessments help you find drift before the assessor does.

**Evidence produced:** Spot assessment record with control ID, assessment method, and result.

---

### Contingency Plan Review

**What to do:** Review the Contingency Plan (CP) for accuracy. Confirm recovery time objectives (RTO) and recovery point objectives (RPO) are still achievable. Confirm contact lists and escalation paths are current.

**Why:** CP-2 requires the contingency plan to be reviewed and updated. Quarterly review keeps it fresh for the annual functional exercise.

**Evidence produced:** CP review record; updated CP if changes were made.

---

### 3PAO Check-In / Assessment Coordination

**What to do:** Quarterly touchpoint with your 3PAO (or ISSO/AO) to review assessment status, confirm readiness for annual assessment, and surface any pre-assessment remediation items.

**Why:** Annual 3PAO assessments cover a statistically significant sample of controls. Staying coordinated quarterly avoids last-minute surprises.

**Evidence produced:** Meeting notes; pre-assessment action items tracked in POA&M.

---

## Annually

### Annual Vulnerability Scan by Independent Assessor

**What to do:** Engage your accredited 3PAO or an accredited independent assessor to run authenticated scans of all OS/infrastructure, web applications, and databases.

**Why:** RA-5 (additional FedRAMP requirement) explicitly requires an independent assessor to scan all asset types once annually, in addition to your monthly internal scans. This is separate from your ongoing monthly scanning.

**Evidence produced:** Independent scan report; included in annual SAR package.

---

### Annual Security Assessment (3PAO SAR)

**What to do:** Coordinate with your 3PAO to conduct the annual security assessment covering a statistically valid sample of controls from your SSP. Assessment includes interviews, document review, and technical testing. 3PAO produces a Security Assessment Report (SAR).

**Why:** CA-2 requires an annual assessment by an independent assessor. The SAR is submitted to the FedRAMP PMO and your AO. Without it, your ATO cannot be maintained.

**Evidence produced:** Completed SAR; any new POA&M items from assessment findings.

---

### SSP Review & Update

**What to do:** Conduct a full review of your System Security Plan. Confirm all control implementations are accurately documented. Update for: new or changed system components, personnel changes, changes to interconnections, updated inherited controls from your cloud provider.

**Why:** PL-2 requires review and update at least annually or when a significant change occurs. The SSP is the authoritative record of your implementation — if it doesn't match reality, you have a documentation gap (or worse, a control gap).

**Evidence produced:** Updated SSP with revised date; change log noting what was updated.

---

### Baseline Configuration Review

**What to do:** Review all baseline configurations (OS hardening, container images, network configs, IAM baseline policies). Confirm they align with current DoD STIGs or CIS Level 2 benchmarks. Update baselines for any deprecated settings or new security guidance.

**Why:** CM-2(b)(1) requires baseline configuration review at least annually and after significant changes.

**Evidence produced:** Updated baseline configuration documentation; SCAP scan results against new baseline.

---

### Contingency Plan Functional Exercise

**What to do:** Execute a functional contingency plan exercise per NIST SP 800-34. This is an actual test — not just a tabletop. Simulate a failure scenario (e.g., primary region outage) and execute your documented recovery procedures. Document results including recovery time achieved vs. RTO.

**Why:** CP-4(a) requires at least annual functional exercises (not just tabletops). Results must be provided to the FedRAMP PMO and included in the SSP's contingency plan test report appendix.

**Evidence produced:** CP test report per NIST SP 800-34 format; submitted to FedRAMP PMO.

---

### Backup Restoration Test

**What to do:** Execute a full backup restoration test. Restore from a weekly full backup to a test environment. Verify data integrity, application functionality, and that the restored system meets your RPO. Document results.

**Why:** CP-9(1) requires backup restoration testing at least annually.

**Evidence produced:** Backup restoration test report with date, backup age, data integrity verification, and any issues found.

---

### Incident Response Plan Test

**What to do:** Conduct an annual IR tabletop exercise or functional test. Walk through a realistic incident scenario (e.g., ransomware detection, data exfiltration, tenant account compromise) and execute your IR plan procedures. Document gaps and update the plan accordingly.

**Why:** IR-3 requires testing of the IR plan at least annually. A tested, current IR plan is required for your annual SAR.

**Evidence produced:** IR exercise record; after-action report; updated IR plan if gaps found.

---

### Non-Privileged Account Review

**What to do:** Conduct a formal access review of all non-privileged accounts. Verify each account is associated with an active user, the access level is appropriate, and no terminated employees retain access. Remove or disable any accounts that fail review.

**Why:** AC-2(j) sets the FedRAMP Moderate parameter for non-privileged account reviews at **annually**. (Privileged accounts are reviewed quarterly — see Quarterly section.)

**Evidence produced:** Non-privileged account recertification report; list of accounts removed or modified.

---

### Third-Party Provider Review

**What to do:** Review all external service providers and cloud services used within the authorization boundary. Confirm each FedRAMP-required service still holds a current P-ATO or ATO. Review contracts and interconnection agreements for compliance.

**Why:** SA-9 requires management of external system services. If a cloud service in your boundary loses its FedRAMP authorization and you don't act, you inherit an unmitigated risk.

**Evidence produced:** Third-party review record; updated external services list in SSP; POA&M items if gaps found.

---

### Policy Review Cycle

**What to do:** Review all security policies and procedures referenced in your SSP (AC policy, CM policy, IR policy, CP policy, etc.). Confirm they are current and accurately reflect your implementation. Update any that reference outdated controls, processes, or personnel.

**Why:** Multiple control families (AC-1, AU-1, CM-1, CP-1, etc.) require policies to be reviewed and updated at defined intervals. FedRAMP Moderate sets review at every 3 years, but annual review during your SAR cycle is best practice.

**Evidence produced:** Updated policy documents with review dates; policy approval records.

---

## Quick Reference Checklist

### Monthly Checklist
- [ ] Vulnerability scans complete (OS, web app, DB)
- [ ] Vulnerability feed updated within 24h before scans
- [ ] New findings entered in POA&M
- [ ] POA&M milestones reviewed and updated
- [ ] ConMon package assembled and submitted to AO
- [ ] Asset/inventory delta reviewed and documented
- [ ] Configuration compliance scan complete
- [ ] Automated patch compliance check run
- [ ] Inactive account sweep complete (90+ day check)
- [ ] IAM credential age review complete
- [ ] Incident summary prepared (zero incidents = still required)
- [ ] GuardDuty Medium findings reviewed and actioned

### Quarterly Checklist
- [ ] Privileged account recertification complete (AC-2j)
- [ ] Security control spot assessment (3–5 controls)
- [ ] Contingency plan reviewed for currency
- [ ] 3PAO / AO check-in conducted

### Annual Checklist
- [ ] Independent assessor vulnerability scan complete (RA-5)
- [ ] 3PAO annual security assessment (SAR) complete
- [ ] SSP reviewed and updated
- [ ] Baseline configurations reviewed against current STIGs/CIS
- [ ] Contingency plan functional exercise complete (CP-4)
- [ ] Backup restoration test complete (CP-9(1))
- [ ] IR plan tabletop or functional exercise complete
- [ ] Non-privileged account recertification complete (AC-2j)
- [ ] Third-party provider review complete (SA-9)
- [ ] Security policies reviewed and updated

> [!info] Control Reference
> All frequencies in this guide are taken from the FedRAMP Moderate Baseline parameter values. For exact quoted control language and citations, see [[Wiki/fedramp-moderate-platform-bau-requirements]].
