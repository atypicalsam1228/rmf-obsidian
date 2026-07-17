---
type: guide
framework: fedramp
status: draft
tags:
  - bau
  - platform-ops
  - team-assignments
  - fedramp/moderate
  - multi-tenant
  - continuous-monitoring
created: 2026-07-02
updated: 2026-07-02
sources:
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
  - "[[Sources/FedRAMP/fedramp-continuous-monitoring-playbook]]"
related:
  - "[[Wiki/fedramp-moderate-platform-bau-requirements]]"
  - "[[Wiki/fedramp-moderate-platform-bau-cadence-training]]"
  - "[[Wiki/fedramp-continuous-monitoring]]"
---

# FedRAMP Moderate BAU — Team Assignments by Task

> [!abstract] Overview
> This article maps every BAU task from the FedRAMP Moderate Platform BAU Tracker (V5) to the responsible team. Tasks are organized by cadence. Joint tasks include a party-level breakdown showing which team owns which portion of the obligation.
>
> Owner key: **Engineering** | **ISSO** | **Sec Ops** | **Joint** (shared)
>
> For the full task definitions with control citations and evidence requirements, see [[Wiki/fedramp-moderate-platform-bau-requirements]] and [[Wiki/fedramp-moderate-platform-bau-cadence-training]].

> [!info] Joint Task Convention
> "Joint" means the task cannot be completed by one team alone. Each entry shows the split: `Team A (what they do) | Team B (what they do)`. If a task appears as a single team, that team owns it end-to-end.

---

## Continuous

| Task | Control | Responsible Team |
|---|---|---|
| Continuous Audit Event Capture — All In-Scope Components | AU-2a / AU-2c / AU-2d | Sec Ops |
| Continuous Monitoring Strategy — Platform Tool Coverage Verification | CA-7 | Sec Ops |
| Automated Asset Discovery — 5-Minute Maximum Detection Delay | CM-8(3)a | Engineering |
| Software Installation Policy Compliance Monitoring | CM-11c | Sec Ops |
| Incident Detection & Escalation Pipeline — Always Available | IR-6 | Sec Ops |
| Environmental Controls Monitoring — Temperature & Humidity | PE-14b | Engineering |
| Vulnerability Scanner Definition Currency | RA-5(2) | Sec Ops |
| External Service Provider Technical Integration Monitoring | SA-9(c) | Engineering |
| Real-Time Malicious Code Protection — Endpoints & Network Entry/Exit | SI-3 | Sec Ops |
| System Monitoring — Near Real-Time Event Analysis & Continuous Traffic Monitoring | SI-4 / SI-4(2) / SI-4(4) | Sec Ops |
| Security Alerts, Advisories & Directives — Ongoing Receipt & Action | SI-5(a) | Sec Ops |

---

## Weekly

| Task | Control | Responsible Team |
|---|---|---|
| Formal Audit Log Review | AU-6a | Sec Ops |
| Malicious Code / AV Full System Scan | SI-3c | Sec Ops |
| Patch SLA Status Review | SI-2(c) / RA-5(d) | Engineering |
| Medium-Severity Threat Alert Review | SI-4 / IR-4 | Sec Ops |
| Weekly Full Backup Verification & Spot Restore | CP-9 / CP-9(1) | Engineering |
| TLS Certificate Expiration Review | SC-17 / IA-5 | Engineering |
| Configuration Compliance Drift Review | CM-6 | Engineering |

---

## Monthly

| Task | Control | Responsible Team |
|---|---|---|
| Vulnerability Scan — OS & Infrastructure | RA-5(a) / RA-5(2) | Sec Ops |
| Vulnerability Scan — Web Applications & APIs | RA-5(a) / RA-5(2) | Sec Ops |
| Vulnerability Scan — Databases | RA-5(a) / RA-5(2) | Sec Ops |
| Vulnerability Remediation SLA Tracking | RA-5(d) | Engineering (remediates) \| ISSO (tracks SLAs / POA&M entry) |
| Security Patch Deployment — All In-Scope Systems | SI-2(c) | Engineering |
| Automated Patch Compliance Check | SI-2(2) | Engineering |
| Security Function Verification | SI-6b | Engineering (runs checks) \| Sec Ops (validates findings) |
| Software & Firmware Integrity Check | SI-7(1) | Engineering |
| Authenticator / Password Rotation Enforcement (60-Day Cycle) | IA-5f | Engineering |
| Inactive Account Sweep (90-Day Check) | AC-2(3)(d) | Engineering |
| IAM Credential & API Key Audit (90-Day Rotation) | IA-5 / SC-12 | Engineering |
| Secrets Rotation Verification | IA-5 / SC-12 | Engineering |
| Audit Log Retention & Integrity Verification | AU-9 / AU-11 | Sec Ops |
| Asset Inventory Delta | CM-8 / CM-8b | Engineering |
| User-Installed Software Compliance Check | CM-11c | Engineering |
| POA&M Evidence Package — Monthly Compilation | CA-5b | ISSO |

---

## Quarterly

| Task | Control | Responsible Team |
|---|---|---|
| Privileged Account Recertification | AC-2(j) / AC-6(7) | Engineering (IAM execution) \| ISSO (sign-off / evidence) |
| Change Access Privilege Review | CM-5(5)b | Engineering (IAM execution) \| ISSO (sign-off / evidence) |
| Authorized Software List Review & Update | CM-7(5)c | Engineering |
| Publicly Accessible Content Review | AC-22d | Engineering (identifies content) \| ISSO (documents / reports) |
| Network Security Rule Review | SC-7 / CM-7 | Engineering |
| Encryption Key Rotation Review | SC-12 / SC-28 / SC-13 | Engineering |
| Container Image Vulnerability Scan | RA-5 / CM-7 | Sec Ops |
| DR Runbook & Failover Procedure Review | CP-2 / CP-10 | Engineering |
| Technical Control Spot Check (3–5 Controls) | CA-7 | ISSO |

---

## Bi-Annual

| Task | Control | Responsible Team |
|---|---|---|
| Traffic Flow Policy Exception Review | SC-7(4)e | Engineering |
| Low-Risk Vulnerability Remediation Status Review | RA-5(d) | Engineering (remediates) \| ISSO (tracks SLA / POA&M) |

---

## 18-Month

| Task | Control | Responsible Team |
|---|---|---|
| Offline Audit Record Retention Audit | AU-11 | Sec Ops (verifies archives) \| ISSO (documents compliance) |

---

## Annual

| Task | Control | Responsible Team |
|---|---|---|
| Independent Vulnerability Scan — All Asset Types | RA-5 (FedRAMP Addl Req) | Sec Ops (provides access & support) \| ISSO (coordinates 3PAO) |
| Annual Penetration Test | CA-8 | Engineering (provides access & support) \| ISSO (coordinates tester) |
| Baseline Configuration Review & Refresh | CM-2(b)(1) / CM-6 | Engineering |
| Annual Review — Unnecessary Functions, Ports, Protocols & Services | CM-7(1)a | Engineering |
| Internal System Connection Review | CA-9d | Engineering |
| Contingency Plan Functional Exercise (DR Test) | CP-4(a) | Engineering (executes recovery) \| ISSO (documents / reports to PMO) |
| Backup Restoration Test — Full Recovery | CP-9(1) | Engineering |
| Incident Response Functional Exercise | IR-3 | Sec Ops (runs scenario) \| ISSO (documents / updates IR plan) |
| Non-Privileged Account Annual Recertification | AC-2(j) | Engineering |
| Full TLS Certificate & PKI Audit | SC-17 / IA-5 | Engineering |
| FIPS Cryptographic Algorithm Compliance Audit | SC-13 / SC-28 | Engineering |
| Role-Based Security Training — Platform Team Completion Verification | AT-3a / AT-3b | ISSO |
| Incident Response Training — Platform Team Completion Verification | IR-2a / IR-2b | ISSO |
| Incident Response Plan — Platform Technical Procedure Review | IR-8a | Engineering (technical input) \| ISSO (owns / updates plan) |
| Maintenance Tools Review | MA-3b | Engineering |
| SSP Platform Control Implementations — Annual Accuracy Review | PL-2c | Engineering (technical input) \| ISSO (updates SSP / submits to AO) |
| Information Security Architecture Review | PL-8b | Engineering (updates architecture) \| ISSO (reviews / approves) |
| Audit Event Types Review & Update | AU-2e | Engineering (implements changes) \| ISSO (updates SSP AU-2) |
| Annual Security Controls Assessment | CA-2d | ISSO |
| System Interconnections — Annual Technical Accuracy Review | CA-3c | Engineering |
| Contingency Plan — Annual Technical Procedure Review | CP-2d | Engineering |
| Contingency Training — Platform Team Completion Verification | CP-3a / CP-3b | ISSO |
| Development Process, Standards & Tools Review | SA-15b | Engineering |
| Supplier & Contractor Technical Integration Review | SR-6 | Engineering (technical review) \| ISSO (risk acceptance / SA-9) |

---

## 3-Year

| Task | Control | Responsible Team |
|---|---|---|
| Risk Assessment — Platform Technical Input Package | RA-3d / RA-3f | Engineering |

---

## Team Load Summary

> [!info] Distribution Across 79 Tasks
> | Team | Task Count | Primary Responsibility Area |
> |---|---|---|
> | **Engineering** | ~38 | Patching, backups, config, IAM/keys, asset inventory, infra-level execution |
> | **Sec Ops** | ~18 | Scanning, alerting, log review, malware, threat monitoring, IR scenario execution |
> | **ISSO** | ~8 | POA&M, ConMon package, SSP, training records, assessment coordination |
> | **Joint** | ~15 | Tasks requiring both execution (Engineering/Sec Ops) and compliance oversight (ISSO) |

---

## Joint Task Split — Reference Table

> [!tip] Use this table when assigning work tickets to clarify who does what on shared tasks.

| Task | Engineering / Sec Ops Does | ISSO Does |
|---|---|---|
| Vulnerability Remediation SLA Tracking | Engineering: remediates findings within SLA | ISSO: tracks aging, enters/updates POA&M |
| Security Function Verification | Engineering: runs verification checks | Sec Ops: validates findings, escalates gaps |
| Privileged Account Recertification | Engineering: executes IAM changes | ISSO: approves, retains sign-off evidence |
| Change Access Privilege Review | Engineering: executes IAM changes | ISSO: approves, retains sign-off evidence |
| Publicly Accessible Content Review | Engineering: identifies and removes content | ISSO: documents findings, reports to AO |
| Low-Risk Vuln Remediation Status Review | Engineering: remediates open items | ISSO: tracks SLA compliance, updates POA&M |
| Offline Audit Record Retention Audit | Sec Ops: verifies archive integrity | ISSO: documents compliance, provides evidence |
| Independent Vulnerability Scan | Sec Ops: provides access and technical support | ISSO: coordinates 3PAO engagement |
| Annual Penetration Test | Engineering: provides access and technical support | ISSO: coordinates pen tester, receives report |
| Contingency Plan Functional Exercise | Engineering: executes recovery procedures | ISSO: documents results, submits to FedRAMP PMO |
| Incident Response Functional Exercise | Sec Ops: runs the incident scenario | ISSO: documents results, updates IR plan |
| IR Plan — Platform Technical Procedure Review | Engineering: provides technical corrections | ISSO: owns plan, incorporates changes, approves |
| SSP Platform Control Review | Engineering: provides updated implementation text | ISSO: updates SSP, submits to AO |
| Information Security Architecture Review | Engineering: updates architecture diagrams | ISSO: reviews for compliance, approves |
| Audit Event Types Review & Update | Engineering: implements event type changes | ISSO: updates AU-2 in SSP |
| Supplier & Contractor Technical Integration Review | Engineering: reviews technical integrations | ISSO: accepts residual risk, maintains SA-9 documentation |
