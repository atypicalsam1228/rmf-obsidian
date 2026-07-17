---
type: mapping
framework: nist-800-171
status: draft
tags:
  - cmmc
  - scoping
  - asset-categories
  - nist-800-171
  - spa
  - crma
created: 2026-06-26
updated: 2026-06-26
sources:
  - "[[Sources/NIST-800-171/nist-800-171r3-security-requirements]]"
  - "[[Sources/NIST-800-171/aws-config-nist-800-171-mappings]]"
related:
  - "[[Wiki/cmmc-siem-requirements]]"
  - "[[Wiki/nist-800-171-cui-protection]]"
  - "[[Wiki/cmmc-remote-work-scoping]]"
---

# CMMC L2 Control-to-Asset-Category Reference

> [!abstract] How to Use This Reference
> CMMC Level 2 defines five asset categories. The table below shows which categories receive full practice assessment vs. documentation-only review. The per-domain sections then answer a more useful question: **which specific practices define WHY a given device is classified as a Security Protection Asset (SPA)?**
>
> Use the **SPA Quick-Reference Table** to start from a device type. Use the **domain sections** to start from a specific practice ID.

---

## The Three Rules

> [!quote] CMMC Scoping Guide Level 2 v2 — Asset Assessment Rules
> | Asset Category | Assessment Requirement |
> |---|---|
> | **CUI Assets** | All 110 practices assessed in full |
> | **Security Protection Assets (SPA)** | All 110 practices apply; assessors focus on practices relevant to the SPA's security function |
> | **Contractor Risk Managed Assets (CRMA)** | NOT assessed — only CA.L2-3.12.4 (SSP) reviewed to confirm CRMA status |
> | **Specialized Assets** | NOT assessed — SSP documentation reviewed only |
> | **Out-of-Scope Assets** | Nothing applies; no documentation required beyond separation validation |
> — CMMC Level 2 Scoping Guide v2.0, Table 1

---

## SPA Quick-Reference Table

Start here if you have a device type and need to know which domain practices will be the assessment focus.

| SPA Device Type | Primary Domain(s) | Key Practices | Why It Is an SPA |
|---|---|---|---|
| Firewall / NGFW | SC | 3.13.1, 3.13.4, 3.13.5, 3.13.6 | Boundary protection and information flow enforcement for the CUI environment |
| SIEM | AU | 3.3.1, 3.3.4, 3.3.5, 3.3.6 | Log aggregation, failure alerting, cross-system correlation, reduction/reporting |
| IdP / Active Directory | AC + IA | 3.1.1, 3.1.5, 3.5.1, 3.5.3 | Access enforcement and authentication for all in-scope assets |
| VPN Concentrator | AC + SC | 3.1.12, 3.1.13, 3.1.14, 3.13.8 | Remote access control and encrypted transit enforcement |
| PAM / Jump Server | AC | 3.1.5, 3.1.6, 3.1.14 | Privileged access routing and control |
| MDM System | AC + CM | 3.1.18, 3.4.2, 3.4.9 | Mobile device enrollment, configuration enforcement, software control |
| Patch Management System | CM + SI | 3.4.1, 3.4.6, 3.14.1 | Baseline configuration enforcement and flaw remediation |
| AV / EDR Platform | SI | 3.14.2, 3.14.4, 3.14.5, 3.14.6 | Malicious code detection, real-time scanning, alert generation |
| Vulnerability Scanner | RA | 3.11.2, 3.11.3 | Vulnerability identification and risk-prioritized remediation tracking |
| Physical Facility / Datacenter | PE | 3.10.1, 3.10.2, 3.10.3 | Physical access control to in-scope systems and CUI media |
| IDS / IPS | SI + SC | 3.13.1, 3.14.6, 3.14.7 | Inbound/outbound traffic monitoring and unauthorized use detection |
| PKI / Certificate Authority | SC + IA | 3.5.3, 3.13.8, 3.13.10 | Certificate-based authentication and key management |

---

## Domain Sections

---

## CA — Security Assessment (4 practices)

> [!info] Domain SPA Profile
> CA practices are primarily organizational (SSP, POA&M, continuous monitoring program). There is no typical SPA device for the CA domain — assessors use CA practices to evaluate the OSC's governance of its assessment scope. The critical exception is CA.L2-3.12.4, which is the **only** CA practice that applies to CRMAs.

| Practice ID | Practice Name | SPA Function Trigger |
|---|---|---|
| CA.L2-3.12.1 | Periodic Security Assessment | — |
| CA.L2-3.12.2 | Plan of Action | — |
| CA.L2-3.12.3 | Security Control Monitoring | Continuous monitoring tools (vulnerability management platforms) |
| CA.L2-3.12.4 | System Security Plan | **All asset categories — CRMAs documented here** |

> [!warning] CRMA Exception — CA.L2-3.12.4
> CA.L2-3.12.4 is the **only** practice reviewed for CRMAs. Assessors confirm the asset is documented in the SSP with sufficient risk-based justification explaining why it is prevented from processing CUI. All other 109 practices do NOT apply to CRMAs. If the SSP justification is weak, the assessor may conduct a limited spot check — but this does not constitute a full practice assessment.

> [!warning] Specialized Asset Exception
> Specialized Assets (GFE, IoT, OT, Restricted Info Systems, Test Equipment) are also only reviewed via CA.L2-3.12.4. The SSP must document these assets and explain how they are managed under the contractor's risk-based security policy.

---

## SC — System and Communications Protection (16 practices)

> [!info] Domain SPA Profile
> SC is the highest-density SPA domain. Firewalls, NGFW, routers with ACLs, IDS/IPS, VPN concentrators, encryption appliances, and any network infrastructure enforcing boundary protection or information flow control are SPAs assessed primarily on SC practices. SC.L2-3.13.11 (FIPS crypto) is uniquely important: it determines whether a storage asset is a CUI Asset or a CRMA.

| Practice ID | Practice Name | SPA Function Trigger |
|---|---|---|
| SC.L1-3.13.1 | Boundary Protection | Firewall, NGFW — canonical boundary SPA |
| SC.L1-3.13.2 | CUI in Public Networks | Firewall, encryption appliance |
| SC.L2-3.13.3 | Security Engineering Principles | — (design/architecture) |
| SC.L2-3.13.4 | Information in Shared Resources | Hypervisor, multi-tenant cloud platform |
| SC.L2-3.13.5 | Deny by Default / Allow by Exception | Firewall, router with ACLs, proxy |
| SC.L2-3.13.6 | Network Communication by Exception | Router, L3 switch with ACLs |
| SC.L2-3.13.7 | Split Tunneling | VPN concentrator (must disable split tunnel) |
| SC.L2-3.13.8 | Transmission Confidentiality | VPN concentrator, TLS terminator |
| SC.L2-3.13.9 | Network Disconnect | Firewall, session management system |
| SC.L2-3.13.10 | Key Management | PKI / Certificate Authority, HSM |
| SC.L2-3.13.11 | Cryptographic Protection (FIPS) | Encryption appliance, application layer (determines CUI Asset vs. CRMA for storage) |
| SC.L2-3.13.12 | Collaborative Computing Devices | MDM, endpoint management |
| SC.L2-3.13.13 | Mobile Code | Proxy, web filter, endpoint control |
| SC.L2-3.13.14 | VoIP | VoIP gateway, UC platform |
| SC.L2-3.13.15 | Communications Authenticity | PKI, session signing infrastructure |
| SC.L2-3.13.16 | Data at Rest | Encryption appliance, storage platform (if not CRMA) |

> [!tip] SC.L2-3.13.11 and CRMA Eligibility
> If CUI is FIPS 140-2 validated encrypted **before** being written to a storage asset (SAN, NAS, cloud storage bucket), the storage asset handles only ciphertext and qualifies as a **CRMA** rather than a CUI Asset. The FIPS practice governs the encrypting system (CUI Asset); the CRMA status of the storage system is the consequence. The contractor must hold the decryption key — if the storage provider can decrypt, the asset is a CUI Asset.

---

## AU — Audit and Accountability (9 practices)

> [!info] Domain SPA Profile
> AU is the SIEM domain. Any system that aggregates logs, performs event correlation, generates audit failure alerts, or produces on-demand audit reports is an SPA assessed on AU practices. See [[Wiki/cmmc-siem-requirements]] for the full SIEM-focused breakdown of this domain.

| Practice ID | Practice Name | SPA Function Trigger |
|---|---|---|
| AU.L2-3.3.1 | System Auditing (create/retain logs) | SIEM, log management platform |
| AU.L2-3.3.2 | User Accountability (traceability) | SIEM, UEBA platform |
| AU.L2-3.3.3 | Event Review (update logged event types) | — (organizational process) |
| AU.L2-3.3.4 | Audit Failure Alerting | SIEM, log management with alerting |
| AU.L2-3.3.5 | Audit Correlation | SIEM — this practice is the canonical SIEM SPA trigger |
| AU.L2-3.3.6 | Reduction and Reporting | SIEM — on-demand analysis and reporting |
| AU.L2-3.3.7 | Authoritative Time Source | NTP server (SPA: time integrity for audit records) |
| AU.L2-3.3.8 | Audit Protection | SIEM, immutable log storage (S3 WORM, SIEM backend) |
| AU.L2-3.3.9 | Audit Management | SIEM — privileged subset controls audit logging |

---

## AC — Access Control (17 practices)

> [!info] Domain SPA Profile
> AC is the IdP/Active Directory, PAM, VPN, and MDM domain. Any asset whose core function is controlling who can access the CUI environment is an SPA assessed on AC practices. Note: AC.L2-3.1.3 (CUI flow control) is the scoping gatekeeper — if CUI flows through an asset, it is in scope.

| Practice ID | Practice Name | SPA Function Trigger |
|---|---|---|
| AC.L1-3.1.1 | Authorized Access Control | IdP, Active Directory |
| AC.L1-3.1.2 | Transaction and Function Control | IdP, RBAC system |
| AC.L2-3.1.3 | Control CUI Flow | Firewall, proxy, DLP — **scoping gatekeeper** |
| AC.L2-3.1.4 | Separation of Duties | — (organizational/IAM policy) |
| AC.L2-3.1.5 | Least Privilege | IdP, PAM, AD — privilege enforcement |
| AC.L2-3.1.6 | Non-Privileged Account Use | PAM, jump server |
| AC.L2-3.1.7 | Privileged Functions | PAM, jump server |
| AC.L2-3.1.8 | Unsuccessful Logon Attempts | IdP, Active Directory, RADIUS |
| AC.L2-3.1.9 | Privacy and Security Notices | — (policy/banner configuration) |
| AC.L2-3.1.10 | Session Lock | Endpoint management, MDM |
| AC.L2-3.1.11 | Session Termination | IdP, network access control |
| AC.L2-3.1.12 | Control Remote Access | VPN concentrator, ZTNA platform |
| AC.L2-3.1.13 | Remote Access Confidentiality | VPN concentrator (encryption) |
| AC.L2-3.1.14 | Remote Access Routing | VPN concentrator (full tunnel), jump server |
| AC.L2-3.1.15 | Privileged Remote Access | PAM, jump server |
| AC.L2-3.1.18 | Mobile Device Connection | MDM |
| AC.L2-3.1.20 | Use of External Systems | — (policy; governs BYOD/CRMA classification) |
| AC.L1-3.1.22 | Control Public Information | — (organizational) |

> [!info] AC.L2-3.1.3 as Scoping Gatekeeper
> AC.L2-3.1.3 (Control the flow of CUI) is the practice that determines which network paths are in scope. Any asset that enforces CUI flow control (firewall, proxy, DLP) is an SPA by definition — it is performing a security function that protects the CUI environment.

---

## IA — Identification and Authentication (11 practices)

> [!info] Domain SPA Profile
> IA practices are assessed primarily on IdP, RADIUS, MFA servers, and PKI infrastructure. These assets authenticate users and devices to the CUI environment — they are SPAs even if they never directly touch CUI.

| Practice ID | Practice Name | SPA Function Trigger |
|---|---|---|
| IA.L1-3.5.1 | Identify System Users | IdP, Active Directory |
| IA.L1-3.5.2 | Authenticate Users | IdP, RADIUS, MFA server |
| IA.L2-3.5.3 | Multifactor Authentication | MFA server, IdP with MFA, FIDO2 platform |
| IA.L2-3.5.4 | Replay-Resistant Authentication | PKI, FIDO2, smart card infrastructure |
| IA.L2-3.5.5 | Identifier Management | IdP, Active Directory (account lifecycle) |
| IA.L2-3.5.6 | Password Management | IdP, password vault, PAM |
| IA.L2-3.5.7 | Password Complexity | IdP, Active Directory GPO |
| IA.L2-3.5.8 | Password Reuse | IdP, Active Directory GPO |
| IA.L2-3.5.9 | Temporary Passwords | IdP |
| IA.L2-3.5.10 | Cryptographic Authentication | PKI, smart card CA |
| IA.L2-3.5.11 | Obscure Feedback | — (application configuration) |

---

## CM — Configuration Management (9 practices)

> [!info] Domain SPA Profile
> CM practices are assessed on patch management systems, configuration management databases (CMDB), application allowlisting tools, and any system whose core function is enforcing baseline configurations across in-scope assets.

| Practice ID | Practice Name | SPA Function Trigger |
|---|---|---|
| CM.L2-3.4.1 | Baseline Configuration | Patch management system, CMDB, DSC/Ansible |
| CM.L2-3.4.2 | Configuration Settings | STIG/CIS enforcement tooling, MDM, Group Policy |
| CM.L2-3.4.3 | Configuration Change Control | Change management system, ITSM with change workflow |
| CM.L2-3.4.4 | Impact Analysis | Change management system |
| CM.L2-3.4.5 | Access Restrictions for Change | Change management system, SCM (Git with access controls) |
| CM.L2-3.4.6 | Least Functionality | Configuration enforcement tooling, MDM |
| CM.L2-3.4.7 | Nonessential Functionality | Endpoint management, application control |
| CM.L2-3.4.8 | Application Allowlisting | Application control platform (AppLocker, Defender WDAC, CrowdStrike) |
| CM.L2-3.4.9 | User-Installed Software | MDM, application control, endpoint management |

---

## SI — System and Information Integrity (7 practices)

> [!info] Domain SPA Profile
> SI practices are assessed on AV/EDR platforms, IDS/IPS, vulnerability scanners, and any system performing malicious code detection or security alert generation. These tools protect in-scope assets without directly handling CUI.

| Practice ID | Practice Name | SPA Function Trigger |
|---|---|---|
| SI.L1-3.14.1 | Flaw Remediation | Patch management system (shared with CM) |
| SI.L1-3.14.2 | Malicious Code Protection | AV/EDR platform, email security gateway |
| SI.L2-3.14.3 | Security Alerts and Advisories | SIEM, threat intel platform, SOC |
| SI.L1-3.14.4 | Update Malicious Code Protection | AV/EDR platform (auto-update function) |
| SI.L1-3.14.5 | System and File Scanning | AV/EDR platform (scheduled + real-time scanning) |
| SI.L2-3.14.6 | Monitor Communications for Attacks | IDS/IPS, NGFW with IPS, network monitoring platform |
| SI.L2-3.14.7 | Identify Unauthorized Use | IDS/IPS, UEBA, SIEM (unauthorized use detection) |

---

## RA — Risk Assessment (3 practices)

> [!info] Domain SPA Profile
> RA practices are assessed on vulnerability scanning platforms and risk management systems. The vulnerability scanner is a classic SPA — it provides security protection (identifying vulnerabilities across in-scope assets) without directly handling CUI.

| Practice ID | Practice Name | SPA Function Trigger |
|---|---|---|
| RA.L2-3.11.1 | Risk Assessments | — (organizational process; GRC platform) |
| RA.L2-3.11.2 | Vulnerability Scanning | Vulnerability scanner (Tenable, Qualys, Rapid7) |
| RA.L2-3.11.3 | Vulnerability Remediation | Vulnerability scanner + patch management integration |

---

## PE — Physical Protection (6 practices)

> [!info] Domain SPA Profile
> PE practices are assessed on physical facilities, datacenters, and server rooms that house in-scope systems. The facility itself is an SPA — it provides physical security protection for CUI Assets and other SPAs. Physical access control systems (badge readers, cameras, mantrap systems) are also SPAs assessed on PE practices.

| Practice ID | Practice Name | SPA Function Trigger |
|---|---|---|
| PE.L1-3.10.1 | Limit Physical Access | Physical facility, badge reader system, mantrap |
| PE.L2-3.10.2 | Monitor Physical Access | Physical facility (camera system, visitor log) |
| PE.L1-3.10.3 | Escort Visitors | Physical facility (operational control) |
| PE.L1-3.10.4 | Physical Access Logs | Physical access control system, visitor management |
| PE.L1-3.10.5 | Manage Physical Access Devices | Badge management system |
| PE.L2-3.10.6 | Alternative Work Site | Remote/home office (see [[Wiki/cmmc-remote-work-scoping]]) |

> [!info] Alternate Work Sites and PE
> PE.L2-3.10.6 governs alternate work sites (home offices, hotel rooms, client facilities). Assessors apply this practice to evaluate whether CUI is adequately protected at those sites — whether through physical controls, administrative controls, or technical compensating controls.

---

## AT — Awareness and Training (3 practices)

> [!info] Domain SPA Profile
> AT practices are organizational/people-focused. There is no typical SPA device for this domain. Training management systems (LMS platforms) may qualify as SPAs if they deliver mandatory security training that gates access to the CUI environment.

| Practice ID | Practice Name | SPA Function Trigger |
|---|---|---|
| AT.L2-3.2.1 | Security Awareness | LMS / training platform |
| AT.L2-3.2.2 | Role-Based Training | LMS / training platform |
| AT.L2-3.2.3 | Insider Threat Awareness | LMS / UEBA (behavioral monitoring) |

---

## IR — Incident Response (3 practices)

> [!info] Domain SPA Profile
> IR practices are primarily organizational. Ticketing/case management systems used for incident tracking may qualify as SPAs. The SIEM (an AU-domain SPA) often serves as the detection trigger for IR practices.

| Practice ID | Practice Name | SPA Function Trigger |
|---|---|---|
| IR.L2-3.6.1 | Incident Response Plan | — (organizational; ticketing/ITSM as SPA) |
| IR.L2-3.6.2 | Incident Response Training | LMS / tabletop exercise management |
| IR.L2-3.6.3 | Incident Response Testing | — (organizational exercise) |

---

## MA — Maintenance (6 practices)

> [!info] Domain SPA Profile
> MA practices govern how maintenance is performed on CUI Assets and SPAs. Remote maintenance tools (RMM platforms, remote support software) are SPAs when they provide privileged access to in-scope assets.

| Practice ID | Practice Name | SPA Function Trigger |
|---|---|---|
| MA.L2-3.7.1 | Controlled Maintenance | — (organizational process) |
| MA.L2-3.7.2 | Maintenance Tools | RMM platform, privileged remote support tool |
| MA.L2-3.7.3 | Remote Maintenance | RMM platform (encrypted remote access for maintenance) |
| MA.L2-3.7.4 | Maintenance Personnel | — (personnel vetting; PAM for access control) |
| MA.L2-3.7.5 | Multifactor Authentication for Maintenance | MFA for RMM / maintenance sessions |
| MA.L2-3.7.6 | Remove Maintenance Equipment | — (physical/procedural) |

---

## MP — Media Protection (9 practices)

> [!info] Domain SPA Profile
> MP practices govern physical and logical media containing CUI. Media sanitization equipment (degaussers, shredders) are SPAs when used to destroy CUI media. DLP tools and encrypted USB management systems are also SPAs.

| Practice ID | Practice Name | SPA Function Trigger |
|---|---|---|
| MP.L2-3.8.1 | Media Access | — (physical access control; overlaps PE) |
| MP.L2-3.8.2 | Media Marking | — (labeling process) |
| MP.L2-3.8.3 | Media Storage | Secure media storage cabinet (physical SPA) |
| MP.L2-3.8.4 | Media Transport | Encrypted transport container, courier controls |
| MP.L2-3.8.5 | Media Sanitization | Degausser, shredder (physical SPA for destruction) |
| MP.L2-3.8.6 | Media Accountability | Media tracking/inventory system |
| MP.L2-3.8.7 | Removable Media Use | Endpoint DLP, USB control software |
| MP.L1-3.8.3 | Media Disposal | Physical destruction equipment |
| MP.L2-3.8.9 | Protect CUI During Processing | DLP platform |

---

## PS — Personnel Security (2 practices)

> [!info] Domain SPA Profile
> PS practices are people-focused and organizational. No typical SPA device. HR systems and background check platforms may be in scope as SPAs if they govern access decisions for the CUI environment.

| Practice ID | Practice Name | SPA Function Trigger |
|---|---|---|
| PS.L2-3.9.1 | Screen Individuals | Background check system (HR SPA) |
| PS.L2-3.9.2 | Terminate and Transfer | IdP / AD (offboarding automation) |

---

## Cross-Cutting Notes

> [!info] CMMC SPA Definition vs. NIST 800-171
> CMMC expands the SPA definition beyond NIST SP 800-171:
> - **NIST 800-171 SPA:** Assets protecting CUI Assets only
> - **CMMC SPA:** Assets providing security protection for ANY in-scope asset — including other SPAs, CRMAs, and Specialized Assets
>
> A firewall protecting only the SIEM (an SPA) — but not directly protecting a CUI Asset — is still an SPA under CMMC.

> [!info] SPA Assessment Scope in Practice
> While technically all 110 practices apply to SPAs, assessors focus on the practices relevant to the SPA's security function. A SIEM is not assessed against PE.L1-3.10.1 (physical access) in isolation — it is assessed on AU practices. The physical facility housing the SIEM is a separate SPA assessed on PE practices.

> [!danger] NEEDS SOURCE
> The CMMC Assessment Guide Level 2 v2.0 and CMMC Level 2 Scoping Guide v2.0 are authoritative sources for these rules but are not yet ingested into this vault's Sources/. Cross-referencing CMMC Vault at `CMMC_Vault/Sources/Assessment-Guides/cmmc-scoping-guide-level-2-v2.md` and Kieri Solutions scenario analysis at `CMMC_Vault/CCP-Exam/Sources/cmmc-scoping-scenarios-analysis-1.md`. Run `/rmf-vault ingest` to add these as authoritative RMF vault sources.
