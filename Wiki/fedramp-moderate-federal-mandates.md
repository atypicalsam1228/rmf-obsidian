---
type: guide
framework: fedramp
status: draft
tags:
  - fedramp/moderate
  - federal-mandates
  - compliance/requirements
  - csp/platform
created: 2026-05-19
updated: 2026-05-19
sources:
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
  - "[[Sources/FedRAMP/ssp-appendix-a-moderate-fedramp-security-controls]]"
related:
  - "[[Wiki/fedramp-authorization-process]]"
  - "[[Wiki/fedramp-nist-800-53-relationship]]"
  - "[[Wiki/fedramp-continuous-monitoring]]"
  - "[[Wiki/fedramp-vulnerability-management]]"
---

# FedRAMP Moderate — Federal Mandate Requirements

> [!abstract] Summary
> FedRAMP Moderate overlays NIST 800-53 with specific federal mandates — explicit requirements and parameter values that CSPs must meet regardless of organizational discretion. This article catalogs those mandates by domain, with associated controls and authoritative sources. These are not "organization-defined" — they are fixed federal requirements.

---

## Identity & Authentication

### Phishing-Resistant MFA (IA-2, IA-2(1), IA-2(2))

> [!quote] FedRAMP Moderate — IA-2 Additional Requirements
> "Multi-factor authentication must be phishing-resistant."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#IA-2 — Identification and Authentication|IA-2]]

> [!quote] FedRAMP Moderate — IA-2 Additional Requirements
> "For all control enhancements that specify multifactor authentication, the implementation must adhere to the Digital Identity Guidelines specified in NIST Special Publication 800-63B."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#IA-2 — Identification and Authentication|IA-2]]

- **Controls:** IA-2, IA-2(1), IA-2(2)
- **Standard:** NIST SP 800-63B (AAL), SP 800-63-3
- Phishing-resistant MFA is required for **all** privileged and non-privileged user authentication. TOTP/push-based MFA does not satisfy this — FIDO2/WebAuthn or PIV/CAC required.
- MFA via encrypted VPN must also be documented, assessed, and authorized.

### NIST SP 800-63-3 Digital Identity (IA-2, IA-5, IA-12)

> [!quote] FedRAMP Moderate — IA-5 Additional Requirements
> "Authenticators must be compliant with NIST SP 800-63-3 Digital Identity Guidelines IAL, AAL, FAL level 2."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#IA-5 — Authenticator Management|IA-5]]

> [!quote] FedRAMP Moderate — IA-5(1) Additional Requirements
> "Password policies must be compliant with NIST SP 800-63B for all memorized, lookup, out-of-band, or One-Time-Passwords (OTP). Password policies shall not enforce special character or minimum password rotation requirements for memorized secrets of users."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#IA-5 (1)|IA-5(1)]]

- **Controls:** IA-2, IA-5, IA-5(1), IA-12
- **Standard:** SP 800-63-3, SP 800-63A (IAL), SP 800-63B (AAL), SP 800-63C (FAL)
- No mandatory password rotation. No mandatory special character rules. Minimum 14 characters for systems where MFA is not technically possible.
- SAML assertions must be encrypted when passed through third parties (SP 800-63C §6.2.3).

### PIV / FIPS 201 (IA-2(12), SA-4(10))

> [!quote] FedRAMP Moderate — SA-4(10)
> "Employ only information technology products on the FIPS 201-approved products list for Personal Identity Verification (PIV) capability implemented within organizational systems."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#SA-4 (10)|SA-4(10)]]

- **Controls:** IA-2(12), SA-4(10)
- **Standard:** FIPS 201, HSPD-12, SP 800-79-2, SP 800-166
- PIV/CAC must be accepted for logical and physical access. DoD CAC is a PIV credential.
- Products used for PIV capability must appear on the FIPS 201-approved products list.

---

## Cryptography

### FIPS-Validated Cryptography (SC-13, SC-8(1), IA-2(6), CP-9(8), MP-5, IA-5(1))

> [!quote] FedRAMP Moderate — SC-13 Parameters
> "SC-13 (b) [FIPS-validated or NSA-approved cryptography]"
> — [[Sources/FedRAMP/fedramp-moderate-baseline#SC-13 — Cryptographic Protection|SC-13]]

> [!quote] FedRAMP Moderate — SC-13 Discussion
> "The requirement for FIPS 140 validation, as well as timelines for acceptance of FIPS 140-2, and 140-3 can be found at the NIST Cryptographic Module Validation Program (CMVP). Moving to non-FIPS CM or product is acceptable when: FIPS validated version has a known vulnerability; Non-FIPS version fixes the vulnerability; Non-FIPS version is submitted to NIST for FIPS validation."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#SC-13 — Cryptographic Protection|SC-13]]

- **Controls:** SC-13, SC-8(1), IA-2(6), CP-9(8), MP-5(a), IA-5(1)(c)(d)
- **Standard:** FIPS 140-2 / 140-3 (CMVP)
- All cryptography must use FIPS-validated modules or NSA-approved cryptography. Applies to: data in transit, data at rest, backups, media transport, authenticator storage, VPN.
- SSP Section 10.3 must be fully populated with cryptographic module details (DAR and DIT).

### Encrypted DNS and HTTP Traffic (SC-8, M-22-09)

> [!quote] FedRAMP Moderate — SC-8 Guidance
> "See M-22-09, including 'Agencies encrypt all DNS requests and HTTP traffic within their environment.'"
> — [[Sources/FedRAMP/fedramp-moderate-baseline#SC-8 — Transmission Confidentiality and Integrity|SC-8]]

- **Controls:** SC-8, SC-8(1)
- **Authority:** OMB M-22-09 (Zero Trust Strategy)
- All DNS requests and HTTP traffic within the environment must be encrypted. Aligns with Zero Trust architecture requirements.

---

## DNS Security

### DNSSEC on Authoritative DNS (SC-20)

> [!quote] FedRAMP Moderate — SC-20 Requirement
> "Control Description should include how DNSSEC is implemented on authoritative DNS servers to supply valid responses to external DNSSEC requests. SC-20 applies to use of external authoritative DNS to access a CSO from outside the boundary."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#SC-20 — Secure Name/address Resolution Service (Authoritative Source)|SC-20]]

- **Controls:** SC-20
- External authoritative DNS servers serving the CSO must implement DNSSEC. Positioning authoritative DNS servers inside the authorized boundary is encouraged.
- CSPs should validate configuration via DNSSEC analyzers (e.g., dnsviz.net).

### DNSSEC on Recursive DNS (SC-21)

> [!quote] FedRAMP Moderate — SC-21 Requirement
> "Control description should include how DNSSEC is implemented on recursive DNS servers to make DNSSEC requests when resolving DNS requests from internal components to domains external to the CSO boundary. If the reply is signed, and fails DNSSEC, do not use the reply."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#SC-21 — Secure Name/address Resolution Service (Recursive or Caching Resolver)|SC-21]]

- **Controls:** SC-21
- Internal recursive DNS **must be located inside an authorized environment** (within boundary or from underlying IaaS/PaaS). Signed replies that fail DNSSEC validation must be rejected.

---

## Email Security

### DMARC (SI-8 / SI-4 area, BOD 18-01)

> [!quote] FedRAMP Moderate — SI Guidance
> "When CSO sends email on behalf of the government as part of the business offering, Control Description should include implementation of Domain-based Message Authentication, Reporting & Conformance (DMARC) on the sending domain for outgoing messages as described in DHS Binding Operational Directive (BOD) 18-01."
> — [[Sources/FedRAMP/fedramp-moderate-baseline]]

- **Authority:** DHS BOD 18-01
- If the CSO sends email on behalf of government (e.g., notifications, workflow emails), DMARC must be implemented on the sending domain.

---

## Vulnerability Management

### CISA KEV Remediation Supersedes FedRAMP SLAs (RA-5)

> [!quote] FedRAMP Moderate — RA-5(d) Requirement
> "If a vulnerability is listed among the CISA Known Exploited Vulnerability (KEV) Catalog the KEV remediation date supersedes the FedRAMP parameter requirement."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#RA-5 — Vulnerability Monitoring and Scanning|RA-5]]

- **Controls:** RA-5
- **Authority:** CISA KEV Catalog
- Standard FedRAMP remediation SLAs (Critical: 30 days, High: 90 days) are overridden by KEV deadlines. CSPs must monitor the KEV catalog continuously.

### Annual Independent Vulnerability Scanning (RA-5, CA-2)

> [!quote] FedRAMP Moderate — RA-5(a) Requirement
> "An accredited independent assessor scans operating systems/infrastructure, web applications, and databases once annually."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#RA-5 — Vulnerability Monitoring and Scanning|RA-5]]

- **Controls:** RA-5, CA-2
- Scans must cover: OS/infrastructure, web applications, databases, containers, service configurations.
- ConMon frequency: OS/DB/Web App/Container/Service Config scans at **least monthly**. Independent assessor scans **at least annually**.

### Annual Penetration Testing by Independent Team (CA-8, CA-8(1))

> [!quote] FedRAMP Moderate — CA-8 Parameters
> "CA-8-1 [at least annually]"
> — [[Sources/FedRAMP/fedramp-moderate-baseline#CA-8 — Penetration Testing|CA-8]]

- **Controls:** CA-8, CA-8(1)
- Penetration testing required **at least annually** by an **independent** team. Functional testing must occur prior to initial authorization. Annual functional testing may be concurrent with pen testing.
- Reference: FedRAMP Penetration Test Guidance.

---

## Continuous Monitoring & Assessment

### POA&M Monthly Reporting (CA-5)

> [!quote] FedRAMP Moderate — CA-5 Requirement
> "POA&Ms must be provided at least monthly."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#CA-5 — Plan of Action and Milestones|CA-5]]

- **Controls:** CA-5
- POA&M updates submitted to agency AOs **at least monthly**. Required in authorization packages and subject to OMB federal reporting requirements.

### Annual Security Assessment (CA-2)

> [!quote] FedRAMP Moderate — CA-2 Parameters
> "CA-2 (d) [at least annually]"
> — [[Sources/FedRAMP/fedramp-moderate-baseline#CA-2 — Control Assessments|CA-2]]

- **Controls:** CA-2
- Full control assessment at **least annually**. Reference: FedRAMP Continuous Monitoring Playbook.

### Multi-Agency ConMon Collaboration (CA-7)

> [!quote] FedRAMP Moderate — CA-7 Requirement
> "CSOs with more than one agency ATO must implement a collaborative Continuous Monitoring (ConMon) approach described in the FedRAMP Continuous Monitoring Playbook. This requirement applies to CSOs authorized via the Agency path as each agency customer is responsible for performing ConMon oversight."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#CA-7 — Continuous Monitoring|CA-7]]

- **Controls:** CA-7
- CSOs with multiple agency ATOs must use FedRAMP's collaborative ConMon model — not siloed per-agency monitoring.

### CISA Emergency and Binding Operational Directives (SI-5)

> [!quote] FedRAMP Moderate — SI-5 Requirement
> "Service Providers must address the CISA Emergency and Binding Operational Directives applicable to their cloud service offering per FedRAMP guidance. This includes listing the applicable directives and stating compliance status."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#SI-5 — Security Alerts, Advisories, and Directives|SI-5]]

- **Controls:** SI-5
- **Authority:** CISA BODs and Emergency Directives
- CSPs must enumerate which BODs apply to their CSO and document compliance status. This is an auditable SSP artifact.

---

## Audit Logging

### Log Retention — M-21-31 Alignment (AU-11)

> [!quote] FedRAMP Moderate — AU-11 Parameters
> "AU-11 [a time period in compliance with M-21-31]"
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AU-11 — Audit Record Retention|AU-11]]

> [!quote] FedRAMP Moderate — AU-11 Requirement
> "The service provider retains audit records on-line for at least ninety days and further preserves audit records off-line for a period that is in accordance with NARA requirements. The service provider must either provide a capability for agency customers to export event log files so the agency can comply with federal log storage requirements from M-21-31; or store event log data on behalf of agency customers and make them available to agency customers in compliance with M-21-31."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AU-11 — Audit Record Retention|AU-11]]

- **Controls:** AU-11
- **Authority:** OMB M-21-31, NARA General Records Schedules
- Online retention: **minimum 90 days**. Offline: per NARA/M-21-31 requirements.
- CSPs must either provide log export capability or store on behalf of customers — M-21-31 compliance is the customer's obligation; the CSP enables it.

### Multi-Tenant Audit Reporting (AU-6)

> [!quote] FedRAMP Moderate — AU-6 Requirement
> "In multi-tenant environments, capability and means for providing review, analysis, and reporting to consumer for data pertaining to consumer shall be documented."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AU-6 — Audit Record Review, Analysis, and Reporting|AU-6]]

- **Controls:** AU-6
- Per-tenant audit data isolation and reporting capability must be documented and available.

---

## Supply Chain

### FAR Subpart 7.103 and Section 889 NDAA Prohibition (SA-4)

> [!quote] FedRAMP Moderate — SA-4 Requirement
> "The service provider must comply with Federal Acquisition Regulation (FAR) Subpart 7.103, and Section 889 of the John S. McCain National Defense Authorization Act (NDAA) for Fiscal Year 2019 (Pub. L. 115-232), and FAR Subpart 4.21, which implements Section 889."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#SA-4 — Acquisition Process|SA-4]]

- **Controls:** SA-4
- **Authority:** FAR 7.103, FAR 4.21, NDAA FY2019 §889
- Prohibits use of telecommunications equipment and services from Huawei, ZTE, Hytera, Hikvision, Dahua, and their subsidiaries/affiliates in any federal system.

### Supply Chain Vendor Security Standards (SR-6)

> [!quote] FedRAMP Moderate — SR-6 Requirement
> "CSOs must ensure that their supply chain vendors build and test their systems in alignment with NIST SP 800-171 or a commensurate security and compliance framework. CSOs must ensure that vendors are compliant with physical facility access and logical access controls to supplied products."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#SR-6 — Supplier Assessments and Reviews|SR-6]]

- **Controls:** SR-6, SR-3, SR-8, SR-11
- Supply chain vendors must align to NIST SP 800-171 or equivalent.
- CSPs must document custody chain for replacement devices (SR-3).
- CSPs must receive zero-day/vuln notifications from supply chain vendors (SR-8).
- Software and patches must have vendor-attested authenticity; vendor must protect development pipeline (SR-11).

---

## Contingency Planning

### ISCP Template Required (CP-2)

> [!quote] FedRAMP Moderate — CP-2 Requirement
> "CSPs must use the FedRAMP Information System Contingency Plan (ISCP) Template."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#CP-2 — Contingency Plan|CP-2]]

- **Controls:** CP-2
- The FedRAMP-specific ISCP template is mandatory — not an organizational discretion item.

### Backup Minimums (CP-9)

> [!quote] FedRAMP Moderate — CP-9 Requirements
> "The service provider maintains at least three backup copies of user-level information (at least one of which is available online)... system-level information... information system documentation including security information."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#CP-9 — System Backup|CP-9]]

- **Controls:** CP-9
- Minimum **3 copies** of user data, system data, and security documentation. At least 1 copy must be online (immediately accessible).

### Contingency Test Plan per NIST 800-34 (CP-4)

> [!quote] FedRAMP Moderate — CP-4(a) Requirement
> "The service provider develops test plans in accordance with NIST Special Publication 800-34 (as amended)."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#CP-4 — Contingency Plan Testing|CP-4]]

- **Controls:** CP-4
- **Standard:** NIST SP 800-34
- Test results must be included in the security package as Appendix G.

---

## Incident Response

### FISMA Incident Definition (IR-4)

> [!quote] FedRAMP Moderate — IR-4 Requirement
> "The FISMA definition of 'incident' shall be used: 'An occurrence that actually or imminently jeopardizes, without lawful authority, the confidentiality, integrity, or availability of information or an information system; or constitutes a violation or imminent threat of violation of law, security policies, security procedures, or acceptable use policies.'"
> — [[Sources/FedRAMP/fedramp-moderate-baseline#IR-4 — Incident Handling|IR-4]]

- **Controls:** IR-4
- **Authority:** FISMA (44 U.S.C. § 3552)
- Organizational incident definitions cannot be narrower than FISMA's definition.

### US-CERT Reporting Timelines (IR-6)

> [!quote] FedRAMP Moderate — IR-6 Parameters
> "IR-6 (a) [US-CERT incident reporting timelines as specified in NIST Special Publication 800-61 (as amended)]"
> — [[Sources/FedRAMP/fedramp-moderate-baseline#IR-6 — Incident Reporting|IR-6]]

> [!quote] FedRAMP Moderate — IR-6 Requirement
> "Reports security incident information according to the guidance in the FedRAMP Continuous Monitoring Playbook."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#IR-6 — Incident Reporting|IR-6]]

- **Controls:** IR-6
- **Standard:** NIST SP 800-61, US-CERT reporting timelines
- Incident response plan must name designated FedRAMP personnel (IR-8).

---

## Account Management

### Account Disable Timeframes (AC-2, AC-2(2), AC-2(3))

> [!quote] FedRAMP Moderate — AC-2 Parameters
> "AC-2 (h) (1) [twenty-four (24) hours] — AC-2 (h) (2) [eight (8) hours] — AC-2 (h) (3) [eight (8) hours] — AC-2 (j) [quarterly for privileged access, annually for non-privileged access]"
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AC-2 — Account Management|AC-2]]

> [!quote] FedRAMP Moderate — AC-2(2) Parameters
> "AC-2 (2) [Selection: disables] [Assignment: no more than 96 hours from last use]"
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AC-2 (2)|AC-2(2)]]

> [!quote] FedRAMP Moderate — AC-2(3) Parameters
> "AC-2 (3) [24 hours for user accounts] — AC-2 (3) (d) [ninety (90) days]"
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AC-2 (3)|AC-2(3)]]

- **Controls:** AC-2, AC-2(2), AC-2(3)

| Condition | Timeframe |
|---|---|
| Disable inactive temporary accounts | 24 hours |
| Disable inactive non-temp accounts | 96 hours from last use |
| User account disable (general) | 24 hours |
| Account inactivity threshold | 90 days |
| Privileged account access review | Quarterly |
| Non-privileged account access review | Annually |

---

## System Inventory

### Inventory Refresh Frequency (CM-8)

> [!quote] FedRAMP Moderate — CM-8 Requirement
> "Must be provided at least monthly or when there is a change."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#CM-8 — System Component Inventory|CM-8]]

- **Controls:** CM-8
- Component inventory must be updated **at least monthly** or upon any change.

### Authorization Boundary Alignment (CM-12, CM-12(1))

> [!quote] FedRAMP Moderate — CM-12 Requirement
> "According to FedRAMP Authorization Boundary Guidance."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#CM-12 — Information Location|CM-12]]

- **Controls:** CM-12, CM-12(1)
- **Authority:** FedRAMP Authorization Boundary Guidance document
- Information location documentation must align with the boundary definition — not a free-form narrative.

---

## Personnel Security

### Background Investigation Rescreening (PS-3)

> [!quote] FedRAMP Moderate — PS-3 Parameters
> "PS-3 (b) [for national security clearances; a reinvestigation is required during the fifth (5th) year for top secret security clearance, the tenth (10th) year for secret security clearance, and fifteenth (15th) year for confidential security clearance. For moderate risk law enforcement and high impact public trust level, a reinvestigation is required during the fifth (5th) year. There is no reinvestigation for other moderate risk positions or any low risk positions]"
> — [[Sources/FedRAMP/fedramp-moderate-baseline#PS-3 — Personnel Screening|PS-3]]

- **Controls:** PS-3, PS-3(3)
- Rescreening frequency is federally mandated, not organization-defined.
- Personnel with access to CUI must satisfy PS-3(3) additional criteria.

> [!info] Cross-Reference
> For CSP personnel US Person requirements (DoD IL4+), see [[Wiki/jira-cloud-fedramp-us-person-requirements]].

---

## System Communications

### Change Communication (CM-3)

> [!quote] FedRAMP Moderate — CM-3 Requirement
> "The service provider establishes a central means of communicating major changes to or developments in the information system or environment of operations that may affect its services to the federal government and associated service consumers (e.g., electronic bulletin board, web status page)."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#CM-3 — Configuration Change Control|CM-3]]

- **Controls:** CM-3
- A public-facing or agency-accessible change communication channel is required — this is not just internal change management.

### Ports, Protocols, Services via STIGs or CIS (CM-7)

> [!quote] FedRAMP Moderate — CM-7(b) Requirement
> "The service provider shall use Security guidelines (See CM-6) to establish list of prohibited or restricted functions, ports, protocols, and/or services or establishes its own list of prohibited or restricted functions, ports, protocols, and/or services if STIGs or CIS is not available."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#CM-7 — Least Functionality|CM-7]]

- **Controls:** CM-7
- **Authority:** DISA STIGs or CIS Benchmarks (mandatory baseline; custom list only if neither exists)

### Time Server Requirements (SC-45(1))

> [!quote] FedRAMP Moderate — SC-45(1) Requirements
> "The service provider selects primary and secondary time servers used by the NIST Internet time service. The secondary server is selected from a different geographic region than the primary server. The service provider synchronizes the system clocks of network computers that run operating systems other than Windows to the Windows Server Domain Controller emulator or to the same time source for that server."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#SC-45 (1)|SC-45(1)]]

- **Controls:** SC-45(1)
- **Authority:** NIST Internet Time Service
- Primary and secondary NTP servers must be from NIST; secondary from different geographic region. Non-Windows systems must sync to DC emulator or same source.

---

## Acquisition & Compliance

### OMB A-130 Authorization Frequency (CA-6)

> [!quote] FedRAMP Moderate — CA-6 Parameters
> "CA-6 (e) [in accordance with OMB A-130 requirements or when a significant change occurs]"
> — [[Sources/FedRAMP/fedramp-moderate-baseline#CA-6 — Authorization|CA-6]]

- **Controls:** CA-6
- **Authority:** OMB Circular A-130
- Authorization must be renewed per OMB A-130 cadence or upon significant change — not purely on a fixed 3-year cycle.

### Incident Response Testing per NIST 800-61 (IR-3)

> [!quote] FedRAMP Moderate — IR-3-2 Requirement
> "The service provider defines tests and/or exercises in accordance with NIST Special Publication 800-61 (as amended). Functional testing must occur prior to testing for initial authorization. Annual functional testing may be concurrent with required penetration tests (see CA-8)."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#IR-3 — Incident Response Testing|IR-3]]

- **Controls:** IR-3
- **Standard:** NIST SP 800-61
- IR functional test required **before initial authorization**. Annual thereafter (can be combined with CA-8 pen test).

---

## Summary Table

| Requirement Area | What is Needed | Rationale |
|---|---|---|
| **FedRAMP Documentation Package** | Use the FedRAMP ISCP template (not a custom format) for the contingency plan (CP-2). Include contingency test results as SSP Appendix G (CP-4). Submit POA&Ms at least monthly (CA-5). Document CISA BOD compliance status and list applicable directives in the SSP (SI-5). Establish a public/agency-accessible channel for communicating major system changes (CM-3). | FedRAMP standardizes package artifacts so agency AOs can review consistently across CSPs. Monthly POA&Ms and BOD status ensure ongoing federal oversight visibility. |
| **Authentication & Identity** | All MFA must be phishing-resistant — FIDO2/WebAuthn or PIV/CAC (IA-2, IA-2(1), IA-2(2)). Authenticators must comply with NIST SP 800-63-3 IAL/AAL/FAL Level 2 (IA-5). Accept PIV/CAC for logical access; use only FIPS 201-approved products for PIV capability (IA-2(12), SA-4(10)). Do not enforce password rotation or special character rules; minimum 14 chars where MFA is unavailable (IA-5(1)). | NIST 800-63B supersedes legacy password complexity rules based on evidence they reduce security. Phishing-resistant MFA addresses credential theft as the leading federal breach vector. PIV/HSPD-12 is a federal identity standard since 2004. |
| **Cryptography** | All cryptography must use FIPS 140-2 or 140-3 validated modules (SC-13). Applies to data in transit, at rest, backups, media transport, and VPN. SSP Section 10.3 must fully document all cryptographic modules for DAR and DIT (SC-8(1)). All DNS requests and HTTP traffic within the environment must be encrypted per OMB M-22-09 (SC-8). | FIPS 140 validation ensures cryptographic modules meet federal security standards. M-22-09 (Zero Trust Strategy) mandates encrypted internal traffic to eliminate implicit trust on federal networks. |
| **DNS Security** | Implement DNSSEC on all authoritative DNS servers serving the CSO (SC-20). Implement DNSSEC on all internal recursive DNS servers; reject signed replies that fail validation (SC-21). Internal recursive DNS must reside inside the authorized boundary. | DNSSEC prevents DNS spoofing and cache poisoning attacks. A compromised DNS can redirect users to malicious infrastructure silently — critical for federal data integrity. |
| **Email Security** | If the CSO sends email on behalf of government (notifications, workflow), implement DMARC on the sending domain per DHS BOD 18-01. | BOD 18-01 (2017) mandates DMARC to prevent domain spoofing of federal email, protecting agency recipients from phishing using the CSO's domain. |
| **Vulnerability & Patch Management** | CISA KEV catalog deadlines supersede FedRAMP remediation SLAs — KEV items must be remediated by the CISA-specified date (RA-5(d)). Conduct monthly OS, database, web application, container, and service configuration scans (CA-7). An accredited independent assessor must scan OS/infrastructure/web apps/databases at least annually (RA-5(a)). Conduct annual penetration testing by an independent team (CA-8, CA-8(1)). | KEV items are actively exploited in the wild — CISA deadlines reflect operational threat intelligence, not just theoretical risk windows. Independent scanning prevents self-attestation bias. |
| **Audit Logging & Retention** | Retain audit logs online for at least 90 days (AU-11). Retain offline per NARA and M-21-31 requirements. In multi-tenant environments, provide per-tenant log export capability or store and make logs available in compliance with M-21-31 (AU-11, AU-6). | M-21-31 (2021) mandates federal log retention to enable incident investigation. Per-tenant access ensures agencies can perform their own FISMA oversight without depending solely on the CSP. |
| **Incident Response** | Use the FISMA statutory definition of "incident" — not a narrower organizational definition (IR-4). Report incidents per US-CERT timelines in NIST SP 800-61 and the FedRAMP ConMon Playbook (IR-6). Name designated FedRAMP personnel in the IR plan (IR-8). Conduct IR functional testing before initial authorization and annually thereafter — may be concurrent with pen test (IR-3). | FISMA's definition is intentionally broad to ensure federal agencies are notified of all potential compromises. Narrow definitions are a common way CSPs inadvertently underreport. |
| **Continuous Monitoring** | Conduct a full security control assessment at least annually (CA-2). CSOs with multiple agency ATOs must implement collaborative ConMon per the FedRAMP ConMon Playbook (CA-7). | Annual assessments ensure controls remain effective as systems evolve. Collaborative ConMon prevents duplicative agency audits while maintaining oversight breadth for multi-tenant CSOs. |
| **Supply Chain & Acquisition** | Prohibit use of telecommunications products from NDAA §889-listed entities (Huawei, ZTE, Hytera, Hikvision, Dahua) (SA-4 / FAR 4.21). Supply chain vendors must align to NIST SP 800-171 or equivalent (SR-6). Document custody chain for replacement devices (SR-3). Establish zero-day/vuln notification process with vendors (SR-8). Require vendor attestation of software/patch authenticity and secure development pipeline (SR-11). | §889 bans specific vendors due to national security concerns (foreign adversary-controlled equipment). SP 800-171 extends CUI protection requirements into the supply chain, closing a common attack vector. |
| **3rd Party & Independent Assessment** | All annual security assessments must be performed by an independent assessor (CA-2). Vulnerability scans must be performed by an accredited independent assessor annually (RA-5(a)). Penetration testing must be conducted by an independent team — no conflicts of interest with system development or operations (CA-8(1)). | Independence prevents self-attestation and conflict of interest. 3PAOs are accredited by the FedRAMP PMO specifically to ensure assessor quality and consistency across authorizations. |
| **Personnel Security** | Rescreen personnel per OPM/federal schedule: TS reinvestigation at year 5, Secret at year 10, Confidential at year 15; moderate-risk law enforcement/high public trust at year 5 (PS-3). Personnel accessing CUI must satisfy additional screening criteria (PS-3(3)). | OPM rescreening schedules reflect evolving insider threat risk over time. Personnel in CUI-access positions can affect multiple agencies if compromised. |
| **Account Management** | Disable inactive temporary accounts within 24 hours (AC-2(3)). Disable inactive non-temporary accounts within 96 hours of last use (AC-2(2)). Disable accounts after 90 days of inactivity (AC-2(3)(d)). Review privileged account access quarterly; non-privileged annually (AC-2(j)). | Stale accounts are a primary lateral movement vector. FedRAMP fixes specific timeframes because "organization-defined" produced inconsistent results across CSPs. |
| **Infrastructure Operations** | Refresh system component inventory at least monthly or on any change (CM-8). Restrict ports/protocols/services using DISA STIGs or CIS Benchmarks; custom list only if neither applies (CM-7). Sync clocks to NIST Internet Time Service with primary and secondary from different geographic regions (SC-45(1)). Align information location documentation to FedRAMP Authorization Boundary Guidance (CM-12). | Accurate inventories are prerequisite to vulnerability management. STIGs/CIS provide vetted federal hardening baselines. Time synchronization is required for log correlation and forensic integrity. |
| **Contingency Planning** | Maintain at least 3 copies of user data, system data, and security documentation — at least 1 online (CP-9). Develop contingency test plans per NIST SP 800-34; include results in SSP Appendix G (CP-4). Define RTO-consistent timeframes for alternate processing and telecom sites (CP-7, CP-8). | The 3-copy minimum guards against simultaneous failure of primary and one backup. NIST 800-34 ensures plans are actionable and tested, not just documented. |
| **Authorization Lifecycle** | Renew authorization per OMB Circular A-130 or upon significant change — not on a fixed calendar cycle (CA-6). Notify all Authorizing Officials of risk assessment findings (RA-3(e)). | OMB A-130 ties reauthorization to meaningful risk changes. Multi-AO notification ensures all relying agencies are informed of updated risk posture. |
