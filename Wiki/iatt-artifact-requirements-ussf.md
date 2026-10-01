---
type: guide
framework: cross-framework
status: final
tags:
  - dod-rmf
  - iatt
  - ussf
  - emass
  - authorization
  - artifact-requirements
created: 2026-09-01
updated: 2026-09-01
sources:
  - "[[Sources/DoD-SRG/ussf-osb-ao-iatt-artifact-requirements-2026]]"
  - "[[Sources/DoD-SRG/dodi-8510-01-rmf-dod-it]]"
  - "[[Sources/DoD-SRG/disa-connection-process-guide-v6-1]]"
related:
  - "[[Wiki/dod-ato-with-conditions]]"
  - "[[Wiki/dod-srg-cloud-impact-levels]]"
---

# IATT Artifact Requirements — USSF OSB AO

> [!abstract]
> This article covers the minimum artifacts required for an Interim Authority to Test (IATT) submission to the USSF Operations Subordinate Boundary Authorizing Official (USSF OSB AO). Source: HQ CFC memorandum, 3 June 2026, signed by Col Shane M. Warren, USSF. Supersedes HQ SpOC S66 memo of 10 July 2024.

See also: [[Wiki/dod-ato-with-conditions]] for authorization decision types, ATC duration under IATT, and the IL5/IL6 authorization path.

---

## Governing Authority

The **USSF Operations Subordinate Boundary (OSB) AO** is the Authorizing Official for USSF FLDCOM systems. Submissions go to the OSB AO via **eMASS**. The Space Security Control Assessor (SCA) performs the technical assessment; the AO makes the authorization decision.

> [!quote] USSF OSB AO Memo — 3 June 2026
> "To support an accurate and timely risk determination from the Space Security Control Assessor (SCA), all authorization requests to the USSF Operations Subordinate Boundary Authorizing Official (USSF OSB AO) review shall include the following artifacts uploaded to the Enterprise Mission Assurance Support System (eMASS)."
> — [[Sources/DoD-SRG/ussf-osb-ao-iatt-artifact-requirements-2026]]

---

## Required Artifacts (Minimum Set)

> [!quote] USSF OSB AO Memo — Section 2
> "Paragraph (2) is not a comprehensive list of all system documentation to support implementation of cybersecurity requirements, but rather the minimum requirements necessary for the USSF OSB AO to make an authorization decision."
> — [[Sources/DoD-SRG/ussf-osb-ao-iatt-artifact-requirements-2026]]

| # | Artifact | Signer / Requirement |
|---|---|---|
| 2a | IT Categorization and Selection Checklist (ITCSC) | Signed by AODR |
| 2b | Security Plan | Assessed by USSF OSB AO; signed by SCA |
| 2c | Topology Diagram(s) | IAW DoD Architecture Framework; saved as PDF; see Attachment 1 |
| 2d | Hardware and Software List(s) | Imported via eMASS Assets > Import/Export |
| 2e | Boundary Network Device Config Files | As requested |
| 2f | Cybersecurity Strategy | ACAT-designated systems only |
| 2g | RMF Plans and Policies | Signed (digital/electronic/wet) and dated |
| 2h | STIG Applicability List | Selected in eMASS at System > Categorization > STIGs |
| 2i | STIG Compliance and Vulnerability Scans | Within 60 days of submission — **initial IATTs exempt** |
| 2j | PPS Matrix | Imported into eMASS; PPSM tracking number required for DISN connections |
| 2k | Approved Test Plan | Signed by ISSM, PM, or ISO |

---

## Initial vs. Subsequent IATTs

> [!quote] USSF OSB AO Memo — Sections 4 and 5
> "The USSF OSB AO staff do not expect all security controls to be addressed prior to an initial IATT request... Initial IATT's do not require STIG compliance and vulnerability scans. Subsequent IATT's will require an updated test plan and a full control assessment."
> — [[Sources/DoD-SRG/ussf-osb-ao-iatt-artifact-requirements-2026]]

| Requirement | Initial IATT | Subsequent IATT |
|---|---|---|
| STIG compliance/vulnerability scans | **Not required** | Required (within 60 days) |
| Test plan | Required (signed) | Updated test plan required |
| Control assessment | Partial (SA/SR + tested controls) | **Full control assessment** |

---

## eMASS Workflow

> [!quote] USSF OSB AO Memo — Section 6
> "Due to persistent functionality challenges, the separate eMASS IATT workflow is discontinued. Programs should now utilize the standard eMASS workflow for Steps 4 and 5, labeling all IATT Systems with 'IATT' in the package name for tracking and management purposes."
> — [[Sources/DoD-SRG/ussf-osb-ao-iatt-artifact-requirements-2026]]

- Use **standard eMASS workflow** (Steps 4 and 5)
- Label all IATT packages: **"IATT" in the package name**
- Separate IATT workflow is discontinued as of the June 2026 memo

---

## IATT Duration in eMASS

> [!quote] USSF OSB AO Memo — Section 7
> "eMASS has an 180-day limit for IATT authorizations. If an IATT is approved for longer than 180 days, an extension workflow can be submitted to extend the IATT authorization to the previously approved authorization date."
> — [[Sources/DoD-SRG/ussf-osb-ao-iatt-artifact-requirements-2026]]

> [!info] Cross-Reference: DoDI 8510.01 / DISA CPG ATC Duration
> DoDI 8510.01 and DISA CPG v6.1 both state ATC duration under IATT is **normally less than 90 days**. The eMASS 180-day limit is the system ceiling for the authorization record — the ATC itself remains governed by the <90-day DoDI requirement for DISN-connected systems.
> See [[Wiki/dod-ato-with-conditions#IATT — Authoritative Findings Summary]]

---

## Topology Requirements (Attachment 1)

> [!quote] USSF OSB AO Memo — Attachment 1
> "The System Authorization Boundary MUST be indicated by a thick red dashed line (- - - - - -) that surrounds only the items being assessed."
> — [[Sources/DoD-SRG/ussf-osb-ao-iatt-artifact-requirements-2026]]

### Structure

The topology artifact has two parts:
1. **System Authorization Boundary** — assessed items only, inside the red dashed boundary
2. **Reference Components** — inherited controls and out-of-scope components shown outside the boundary

### Required Device Labels (All Devices)

Every device on the topology must display:
1. Function Name (e.g., OWA Server, IDS, Firewall, Router)
2. Hostname
3. Software/OS Version
4. Hardware Manufacturer
5. Hardware Make/Model
6. Firmware Version
7. IP Address or IP Address Range

> [!warning] Classified Systems
> For classified topologies, providing IPs and specific technology details may reveal sensitive information. Protect the topology IAW the Security Classification Guidance program.

### Additional Topology Rules

- Topology must be **dated within 6 months of submission**
- CCSD identifiers labeled (if applicable); all circuits listed in eMASS at System > Details > Connectivity/CCSD
- PPS information flows shown on topology, mapped to PPS Worksheet
- Deduplicate: 4+ identical devices → use ellipse "..." after the third hostname

---

## POC

Mr. Christopher H. O'Dell, HQ CFC S64, DSN 692-4439
