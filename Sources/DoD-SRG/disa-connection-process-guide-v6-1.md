---
type: source
framework: dod-srg
status: ingested
tags:
  - disa
  - disn
  - connection-approval
  - iatt
  - atc
  - snap
  - sgs
  - cap
created: 2026-07-21
updated: 2026-07-21
source_url: "https://dl.dod.cyber.mil/wp-content/uploads/connect/CPG/ConnProcGuide.html"
source_version: "6.1"
source_date: "March 2023"
authority: "DISA Risk Management Executive (RME), Risk Adjudication and Connection Division (RE4)"
classification: "Approved for public release"
---

# DISA Connection Process Guide (CPG) v6.1 — March 2023

**Authority:** DISA Risk Management Executive (RME), Risk Adjudication and Connection Division (RE4)
**Version:** 6.1 | March 2023
**Classification:** Approved for public release
**Source:** https://cyber.mil/connect/connection-approval/

---

## Core Definition

> [!quote] DISA CPG v6.1 — DISN Definition
> "The Defense Information System Network is DoD's enterprise capability of DoD-owned and -leased telecommunications and computing subsystems, networks, and capabilities, centrally managed and configured by DISA."

---

## Section 2: DISN Connection Process — 16-Step Lifecycle

### Step 2.6: Obtain Authorization Decision Document (ADD)

> [!quote] DISA CPG v6.1 — Section 2.6, A&A Mandatory Requirement
> "Customers must ensure Assessment and Authorization (A&A) of all enclaves or networks in accordance with the appropriate standard prior to connection to the DISN."

**ADD Must Include:**
- CCSD, VPN Identifier, or VRF ID assigned in TSO
- Universal System Identifier (USI) if applicable
- DITPR ID for the system

**A&A Standards by Customer Type:**

| Customer Type | Authority | Standard |
|---|---|---|
| DoD Components | DoD | DoDI 8500.01 & DoDI 8510.01 |
| Classified DoD Contractors | DCSA | DoDI 8510.01 & DoD 5220.22-M |
| Intelligence Community | IC | ICD 503 |
| Federal Mission Partners (NSS) | Federal Partner | CNSSI No. 1253 + DoD CIO agreement |
| Federal Mission Partners (non-NSS) | Federal Partner | NIST 800-37 + DoD CIO agreement |
| Other Mission Partners | Sponsor | Formal agreement (MOA, contract) |

**Accepted Authorization Decision Types for DISN Connection:**

> [!quote] DISA CPG v6.1 — Section 2.6, Authorization Decision Types
> Authorization to Operate (ATO), ATO-with-Conditions, and Interim Authorization to Test (IATT) are accepted. "Interim Authorization to Operate" is no longer permitted under DoD RMF.

---

### Step 2.7: Register Information System in DoD Repositories

**Three mandatory registrations:**
1. **DITPR** — DoD Information Technology Portfolio Repository
2. **SITR** — SIPRNet IT Registry (if classified material required)
3. **DITIP** — Defense Information Technology Investment Portal

**PPSM Tracking Identifier (2.7.3) — Non-Waivable:**

> [!quote] DISA CPG v6.1 — Section 2.7.3
> "DISN CAO will only approve a connection request that includes a valid PPSM Tracking Identifier."

**CSSP Alignment (2.7.4):**
Per DoDI 8530.01, systems must align with joint/Component operations center and a supporting Cybersecurity Service Provider (CSSP).

---

### Step 2.8: Register Connection in SNAP or SGS

**Platforms:**
- SNAP: https://snap.dod.mil (NIPRNet)
- SGS: https://giap.disa.smil.mil (SIPRNet)

**Account requirement:** DD Form 2875; annual renewal via Cyber Awareness Challenge certificate.

#### Section 2.8.3 — Required Documents for Enclave Connection

**Mandatory:**

| # | Document | Notes |
|---|---|---|
| 1 | **Authorization Decision Document (ADD)** | Signed by Authorizing Official (AO); IAW applicable A&A policies |
| 2 | **CSSP Agreement** | Per DoDI 8530.01 |
| 3 | **Topology Diagram** | Per Appendix E guidance |
| 4 | **Consent to Monitor (CTM)** | May be included in ADD; sample in Appendix I |
| 5 | DoD Component CIO Concurrence Memo | Required only if Very High/High risk non-compliant control exists |
| 6 | Mission Partner Connection Approval | Required for DoD contractors, Federal partners, Allied/Coalition |

**Optional Supporting Documents:**
- Security Plan (SP)
- Security Assessment Report (SAR)
- Plan of Action and Milestones (POA&M)

> [!info] Applicability Note
> Sections 2.7–2.8 (SNAP/SGS registration, PPSM, CSSP alignment, topology upload) apply only when connecting to DISN. Isolated/airgapped systems with no DISN connection are not subject to this registration process.

---

### Step 2.9: DISN CAO Quality Review

For new SIPRNet enclave connections, DISN CAO issues its own **Interim Approval To Test (IATT)** — this is distinct from the system-level ADD issued by the system's AO.

---

### Step 2.10: ATC Issuance and Duration

> [!quote] DISA CPG v6.1 — Section 2.10, ATC Duration Under IATT
> "Under IATT, [ATC expiration is] normally less than 90 days per DoDI 8510.01."

**Standard ATC duration:** Usually same as Authorization Termination Date in customer's ADD; generally within three years unless continuous monitoring program is in place.

**Significant change reissuance:** Customer must notify DISN CAO; may require new A&A before current ATC expiration.

**Events NOT requiring new A&A** (notify DISN CAO and update topology only):
- New VoIP phones with new VLAN segment
- Video Teleconference on DoD UC Approved Products List
- IP address range changes
- DISA transport re-homing
- Bandwidth changes

---

## Section 2.11: DISA Activates Connection

Upon ATC receipt, DISA Global Operations Center (DGOC) activates connection. DISA sustains for period specified in ATC per DISA Circulars 310-130-001 and 310-070-057.

---

## Appendix A: DoD CIO Approval — Commercial Alternatives to DISN

> [!quote] DISA CPG v6.1 — Appendix A, Isolation Requirement
> "DODIN commercial connections are required to be logically and physically isolated from the DISN."

**Process Duration:** 30–45 days for standard; 5 business days for expedited (GO/FO validation, <90 days urgent).

**Required Artifacts for Commercial Alternative Request:**
- DISA validation memo
- DoD Component CISO concurrence memo
- Business case including: purpose, data sensitivity, topology diagram, CSSP narrative, CONOPS (IR, recovery, vulnerability management, CM), cost analysis

---

## Appendix B: Mission Partner Connections to DISN

**Approval validity:**
- DoD SISO approval memo (contractors/allied/coalition): up to **3 years**, annual review required
- MOA (federal partners): up to **9 years**, annual review required

---

## Appendix C: Cloud IT Project (C-ITP) Registration

**By Impact Level:**

| IL | Authorization Check |
|---|---|
| IL2 | FedRAMP Marketplace → SNAP |
| IL4/IL5 | DCAS portal → SNAP |
| IL6 | DCAS portal → SGS |

---

## Key Policy Cross-References

| Policy | Relevance |
|---|---|
| DoDI 8010.01 | DODIN transport; commercial alternative approval |
| DoDI 8500.01 | Cybersecurity A&A standards |
| DoDI 8510.01 | RMF process; IATT/ATO/ATO-w-Conditions decision types; ATC <90 days under IATT |
| DoDI 8530.01 | CSSP alignment requirement |
| DoDI 8540.01 | Cross Domain Solution policy |
| DoDI 8551.01 | PPSM — ports, protocols, services (non-waivable for DISN) |
| CJCSI 6211.02D | DISN connection authority |
| DoD CC SRG | Cloud authorization, registration, connection |

---

## IATT — Authoritative Findings Summary

> [!info] Key IATT Facts from DISA CPG v6.1
> 1. IATT is an accepted authorization decision type for DISN connection (Section 2.6)
> 2. ATC issued under IATT is **normally less than 90 days** per DoDI 8510.01 (Section 2.10)
> 3. For new SIPRNet connections, DISN CAO issues its own IATT after quality review — separate from the system AO's ADD (Section 2.9)
> 4. For airgapped/isolated systems with no DISN connection: SNAP/SGS registration, PPSM, and CAO-issued ATC are not required — only the system-level AO authorization (DoDI 8510.01) applies
