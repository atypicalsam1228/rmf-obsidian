---
type: guide
framework: fedramp
status: draft
tags:
  - training
  - cdse
  - dcsa
  - fedramp/moderate
  - at-family
  - ir-2
  - personnel-security
  - scrm
  - pii
  - cui
created: 2026-06-29
updated: 2026-06-29
sources:
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
related:
  - "[[Wiki/fedramp-moderate-platform-bau-cadence-training]]"
  - "[[Wiki/fedramp-moderate-platform-bau-requirements]]"
---

# FedRAMP Moderate Training — CDSE & DCSA Course Mapping

> [!abstract] Summary
> FedRAMP Moderate training obligations span AT-1 through AT-4 and IR-2. This article maps each control requirement to free government training sources — CDSE (requires free STEPP account) and the DCSA Security Awareness Hub (no account required, runs in browser). The Cyber Awareness Challenge alone satisfies AT-2, AT-2(2), and AT-2(3) for all users. Role-based AT-3 gaps remain for IR personnel and non-cyber roles not covered by any free government course.

---

## Control Requirements Summary

> [!quote] AT-2, FedRAMP Moderate Baseline
> "Provide security and privacy literacy training to system users (including managers, senior executives, and contractors): As part of initial training for new users and [at least annually] thereafter."
> — [[Sources/FedRAMP/fedramp-moderate-baseline]]

> [!quote] AT-3, FedRAMP Moderate Baseline
> "Provide role-based security and privacy training to personnel with the following roles and responsibilities: Before authorizing access to the system, information, or performing assigned duties, and [at least annually] thereafter."
> — [[Sources/FedRAMP/fedramp-moderate-baseline]]

> [!quote] IR-2, FedRAMP Moderate Baseline
> "Provide incident response training: Within [ten (10) days for privileged users, thirty (30) days for Incident Response roles] of assuming an incident response role or acquiring system access; [at least annually] thereafter."
> — [[Sources/FedRAMP/fedramp-moderate-baseline]]

---

## DCSA Security Awareness Hub — Full Catalog Mapped to AT Controls

All courses at **https://securityawareness.dcsa.mil** — no account required, certificate issued on completion. Learners must save their own certificate; DCSA does not retain completion records.

### AT-2 — Literacy Training & Awareness (All Users)

| Course | URL | AT Control | Notes |
|---|---|---|---|
| DOD Initial Orientation and Awareness Training | https://securityawareness.dcsa.mil/initialorientation/index.htm | AT-2 | New employee onboarding; 5-R Framework (Review, Recognize, React, Reference, Report); no prerequisites |
| DOD Annual Security Awareness Refresher | https://securityawareness.dcsa.mil/awarenessrefresher/index.html | AT-2 | Annual recurring requirement; covers DODM 5200.01 V3, NISPOM, Trusted Workforce 2.0; 75% passing score required |
| Cybersecurity Awareness | https://securityawareness.dcsa.mil/cybersecurity/index.htm | AT-2 | Cyber-focused awareness supplement |
| OPSEC Awareness for Military, DOD Employees and Contractors | https://securityawareness.dcsa.mil/opsec/index.htm | AT-2 | Covers protecting unclassified operational information; note: does not satisfy all DOD OPSEC requirements alone — org-specific critical information training also required |

### AT-2(2) — Insider Threat Awareness (All Users)

| Course | URL | AT Control | Notes |
|---|---|---|---|
| Insider Threat Awareness | https://securityawareness.dcsa.mil/itawareness/index.htm | AT-2(2) | Risk indicators, proactive reporting, case studies; direct match for AT-2(2) |
| Maximizing Organizational Trust | https://securityawareness.dcsa.mil/maximizing-trust/index.htm | AT-2(2) supplementary | Organizational trust and insider risk culture — complements awareness training |

> [!info] CAC Overlap
> The CDSE Cyber Awareness Challenge (DS-IA106.06) includes a dedicated insider threat module. Either the CAC or the DCSA Insider Threat Awareness course satisfies AT-2(2) — both are not required.

### AT-2 / AT-3 — CUI & Information Handling

| Course | URL | AT Control | Notes |
|---|---|---|---|
| DoD Mandatory CUI Training | https://securityawareness.dcsa.mil/cui/index.html | AT-2 / AT-3 | Mandatory for all DoD personnel handling CUI; covers marking, safeguarding, decontrolling, destroying, and incident reporting; satisfies industry contractor CUI requirements when mandated by GCA |
| Identifying and Safeguarding PII | https://securityawareness.dcsa.mil/piiv2/index.htm | AT-2 / AT-3 | PII and PHI definitions, legal frameworks, safeguarding responsibilities, authorized vs. unauthorized disclosure, penalties; required for all personnel with PII access |
| Unauthorized Disclosure of Classified Information and CUI | https://securityawareness.dcsa.mil/disclosure/index.html | AT-2 / AT-3 | Covers consequences and reporting obligations for unauthorized disclosure of classified info and CUI |

### AT-3 — Role-Based Training (Security & CI Roles)

| Course | URL | AT-3 Role | Notes |
|---|---|---|---|
| Counterintelligence Awareness and Reporting for DOD | https://securityawareness.dcsa.mil/cidod/index.html | CI-adjacent staff, security officers | FIE tactics, espionage indicators, terrorism warning signs, reporting obligations including Anomalous Health Incidents |
| Counterintelligence Awareness and Security Brief | https://securityawareness.dcsa.mil/ci-security-brief/index.html | Security personnel | Shorter CI briefing format; good for periodic refresher |
| Protecting Assets in the NISP | https://securityawareness.dcsa.mil/protecting/index.html | FSOs, security managers, cleared contractors | NISP-specific asset protection |
| Thwarting the Enemy: CI and Threat Awareness to the DIB | https://securityawareness.dcsa.mil/thwarting/index.htm | DIB contractors, security staff | CI and threat awareness for defense industrial base |
| Introduction to the Risk Management Framework (RMF) | https://securityawareness.dcsa.mil/rmf/index.htm | ISSOs, system owners, AOs | RMF overview; supplement with CDSE CS101–CS107 for full step coverage |
| Establishing an Insider Threat Program | https://securityawareness.dcsa.mil/insiderthreatprgm/index.htm | Insider Threat Program staff, managers | Program management focus — AT-3 for insider threat program roles |

### Information Security Specialist Roles (AT-3)

| Course | URL | AT-3 Role | Notes |
|---|---|---|---|
| Derivative Classification | https://securityawareness.dcsa.mil/derivative/index.htm | Classification managers, reviewers | Required for personnel who derivatively classify information |
| Original Classification | https://securityawareness.dcsa.mil/oca/index.htm | Original Classification Authorities | Required for OCAs |
| Marking Special Categories of Classified Information | https://securityawareness.dcsa.mil/markings/index.htm | Classification and information management staff | Covers special category markings (RD, FRD, SAP, SCI, etc.) |

---

## CDSE Courses — Mapped to AT Controls

All CDSE courses at **https://www.cdse.edu** — free STEPP account required at cdse.usalearning.gov. Certificates issued through STEPP and retained by STEPP.

### AT-2 + AT-2(2) + AT-2(3) — All Users (Single Course)

| Course | Code | URL | Length | Satisfies |
|---|---|---|---|---|
| Cyber Awareness Challenge | DS-IA106.06 | https://www.cdse.edu/Training/eLearning/DS-IA106/ | 60 min | AT-2, AT-2(2) insider threat module, AT-2(3) social engineering/phishing module |

> [!tip] Key Overlap Finding
> The CAC covers AT-2, AT-2(2), and AT-2(3) in a single annual sitting. The DCSA courses for insider threat and the CDSE DS-IA103.06 phishing course are supplementary depth — not required additions for baseline compliance.

### AT-3 — Privileged Users

| Course | Code | URL | Satisfies |
|---|---|---|---|
| Privileged User Cybersecurity Responsibilities | DS-IA112.06 | https://www.cdse.edu/Training/eLearning/DS-IA112/ | AT-3 privileged users — elevated access ethics, legal responsibilities, PKI, restricted/prohibited actions; required before access granted |

### AT-3 — RMF / Security / ISSO Roles

| Course | Code | URL | Satisfies |
|---|---|---|---|
| RMF Prepare Step | CS101.16 | https://www.cdse.edu/Training/eLearning/CS101/ | AT-3 RMF roles |
| RMF Categorize Step | CS102.16 | https://www.cdse.edu/Training/eLearning/CS102/ | AT-3 RMF roles |
| RMF Select Step | CS103.16 | https://www.cdse.edu/Training/eLearning/CS103/ | AT-3 RMF roles |
| RMF Implement Step | CS104.16 | https://www.cdse.edu/Training/eLearning/CS104/ | AT-3 RMF roles |
| RMF Assess Step | CS105.16 | https://www.cdse.edu/Training/eLearning/CS105/ | AT-3 RMF roles |
| RMF Authorize Step | CS106.16 | https://www.cdse.edu/Training/eLearning/CS106/ | AT-3 RMF roles |
| RMF Monitor Step | CS107.16 | https://www.cdse.edu/Training/eLearning/CS107/ | AT-3 RMF roles |

### AT-3 — SCRM Roles

| Course | Code | URL | Length | Satisfies |
|---|---|---|---|---|
| Supply Chain Threat Awareness | CI102.16 | https://www.cdse.edu/Training/eLearning/CI102/ | 30 min | AT-3 SCRM team, acquisition, contracting — FIE threats, counterfeit hardware, mitigation strategies; 75% passing exam |
| Supply Chain Risk Management for ICT | CLE080 | https://www.cdse.edu/Training/eLearning/CLE080/ | 3 hrs | AT-3 dedicated SCRM team — deep ICT SCRM coverage; DAU-hosted via CDSE |

---

## Consolidated Minimum Training Stack by Role

| Role | Required Courses | Timing |
|---|---|---|
| **All users** | CAC (DS-IA106) + CUI Training (DCSA) + PII (DCSA) | Onboarding; annually |
| **Privileged users** | Above + DS-IA112.06 (CDSE) | Before access granted; annually |
| **ISSOs / System Owners / AOs** | Above + RMF series CS101–CS107 (relevant steps) + CI Awareness (DCSA) | Before duties begin; annually |
| **SCRM team / Acquisition / Contracting** | All-user stack + CI102.16 (CDSE) or CLE080 for depth | Before duties begin; annually |
| **Insider Threat Program staff** | All-user stack + Establishing ITP (DCSA) | Before duties begin; annually |
| **IR personnel** | All-user stack + org IR plan walkthrough | Within 30 days of role assumption; annually |
| **Privileged users (IR-2)** | All-user stack + org IR plan walkthrough | Within **10 days** of access grant |
| **PII-heavy roles** | All-user stack — PII course already in all-user stack | Before access to PII systems |
| **Classification staff** | All-user stack + Derivative/OCA/Markings courses (DCSA) | Before performing classification duties |

---

## Gaps — No Free Government Course Available

> [!danger] IR-2 — No Full Course on CDSE or DCSA
> Neither CDSE nor DCSA offers a full incident response training course. FedRAMP Moderate requires IR personnel trained within 10–30 days of access/role assumption and annually thereafter. Supplement with organization's own IR plan walkthrough (documented tabletop), CISA free IR training, or SANS FOR508 for technical IR staff.

> [!danger] Privacy Officer / PT-Role Training
> No CDSE or DCSA course covers privacy officer responsibilities at the AT-3 depth required for personnel implementing PT-family controls. Use IAPP CIPP/G or agency-developed privacy officer training.

---

## Records Requirements (AT-4)

> [!warning] AT-4 — Retain All Certificates 1 Year Minimum
> - **CDSE (STEPP):** Certificates retained in STEPP; learner should also download personal copy
> - **DCSA Hub:** No retention — learner must save certificate immediately on completion
> - **Org-delivered training (IR-2, internal AT-3):** Dated attendance records with ISSO signature
> - Retention period: **at least 1 year** per AT-4(b) FedRAMP Moderate parameter

---

## AT-1 Policy Cadence

| Policy Element | Frequency |
|---|---|
| Awareness & Training policy review | Every 3 years |
| Procedures review | Annually + after significant changes |

---

> [!info] Cross-Framework Mapping
> - **CMMC Level 2:** AT domain maps directly — same course stack applies for CUI environments
> - **NIST 800-53:** AT-2, AT-3, AT-4 are parent controls; FedRAMP Moderate parameters set frequencies
> - **SCRM training** derives from AT-3 discussion and SR-5 discussion — not a standalone AT control
> - **PII/CUI training** derives from AT-2 discussion requirement to cover PII handling and CUI obligations
