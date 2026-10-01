# USSF OSB AO — Required Artifacts for Interim Authority to Test (IATT)

**Issuing Authority:** USSF Operations Subordinate Boundary Authorizing Official (USSF OSB AO)  
**HQ:** Combat Forces Command (CFC), 150 Vandenberg Street, Suite 1105, Peterson SFB, CO 80914-4170  
**Date:** 3 June 2026  
**Supersedes:** HQ SpOC S66 memo, 10 July 2024  
**Submitted to:** ALL USSF FLDCOM  
**Signatory:** SHANE M. WARREN, Col, USSF

## References

- (a) AFI 17-101, Risk Management Framework (RMF) for Air Force Information Technology (IT), 6 February 2020 (incorporating DAFGM 2024-01, 5 September 2024)
- (b) DoDI 8510.01, 19 July 2022, RMF for DoD Systems
- (c) OMB Memorandum 02-01, 17 October 2001, Guidance for Preparing and Submitting Security Plans of Action and Milestones
- (d) P.L. 113-283, 18 December 2014, Federal Information Security Modernization Act (FISMA)
- (e) NIST SP 800-53 Rev. 5, September 2020, Security and Privacy Controls for Information Systems and Organizations
- (f) NIST SP 800-30 Rev. 1, September 2012, Guide for Conducting Risk Assessments
- (g) DoDI 8531.01, September 2020, DoD Vulnerability Management, Section 3
- (h) NIST SP 800-37 Rev. 2, December 2018, Risk Management Framework for Information Systems and Organizations
- (i) CNSSI 1253 Security Categorization and Control Selection for National Security Systems, Table D-1

---

## Section 2 — Required Artifacts (Minimum for USSF OSB AO Review)

All authorization requests shall include the following artifacts uploaded to **eMASS**:

### 2a. IT Categorization and Selection Checklist (ITCSC)
- Must be signed by the **Authorizing Official Designated Representative (AODR)**

### 2b. Security Plan
- Assessed by the USSF OSB AO
- Signed by the **Space Security Control Assessor (SCA)**

### 2c. Topology Diagram(s)
- Include all interconnection details: boundary devices, firewalls, routers, switches, DMZs
- IAW **Department of Defense Architecture Framework**
- Must be saved as PDF
- See Attachment 1 for detailed topology requirements

### 2d. Hardware and Software List(s)
- Import directly into the Assets tab using the eMASS template: **Assets > Import/Export > Hardware & Software Baseline Inventory**

### 2e. Boundary Network Device Configuration Files
- As requested by the USSF OSB AO staff

### 2f. Cybersecurity Strategy
- Applicable to all **Acquisition Category (ACAT) designated systems**

### 2g. All Relevant RMF Plans and Policies
- Must be **signed** (digital, electronic, or wet) and **dated**
- Includes: Access Control, Audit and Accountability, Configuration Management, Incident Response, etc.

### 2h. STIG Applicability List
1. List of all STIGs applicable to the information system based on technologies and architecture
2. Ensure appropriate STIGs are selected in eMASS at **System > Categorization > STIGs** prior to submission

### 2i. STIG Compliance and Vulnerability Scans
1. Analyzed and dated **within 60 days of submission**
2. Import into eMASS at **Assets > Import/Export > Import Device Scan**
3. **Exception: Initial IATTs do NOT require STIG compliance and vulnerability scans**

### 2j. Ports, Protocols, and Services (PPS) Matrix
1. Import into eMASS at **Assets > Ports/Protocols > Add**
2. For systems with a DISN connection, the **PPSM registration/tracking number** is required

### 2k. Approved Test Plan
- Signed by the **ISSM, PM, or ISO**

---

## Section 3 — Artifact List Is Minimum, Not Exhaustive

The USSF OSB AO may request additional artifacts to clarify system security control status. Paragraph 2 is the minimum required for AO risk determination — not a comprehensive list of all cybersecurity documentation.

---

## Section 4 — Initial IATT: Not All Controls Required

The USSF OSB AO staff do not expect all security controls to be addressed prior to an initial IATT request. The program office must provide adequate documentation to demonstrate:
- Appropriate security controls are in place to ensure information security
- Operational system connections required for the test are secured

Document test results for all applicable SA and SR security controls and any other tested controls; annotate status in the eMASS system record.

---

## Section 5 — Subsequent IATTs

Subsequent IATTs require:
1. An **updated test plan**
2. A **full control assessment**

---

## Section 6 — eMASS IATT Workflow Change

The separate eMASS IATT workflow is **discontinued**.

Programs shall now use the **standard eMASS workflow** for Steps 4 and 5, labeling all IATT systems with **"IATT" in the package name** for tracking and management purposes.

---

## Section 7 — eMASS IATT Authorization Duration

- eMASS has a **180-day limit** for IATT authorizations
- If an IATT is approved for longer than 180 days, an **extension workflow** can be submitted to extend to the previously approved authorization date

---

## Attachment 1 — Topology Requirements

### Two Major Parts of a System Authorization Boundary Artifact

1. **System Authorization Boundary** — items being assessed as part of the RMF package only
2. **Reference Components** — components not being assessed but required for security accountability/reference (e.g., inherited protection mechanisms shown outside the boundary)

### Required Topology Features

**Boundary Marking:**
- System Authorization Boundary MUST be indicated by a **thick red dashed line** surrounding only assessed items
- Multiple System Authorization Boundaries (red dashed boxes) are permitted on a single topology
- Do NOT place items outside the authorization boundary inside the red dashed line

**Artifact Currency:**
- Must be **clearly dated within 6 months of submission** for Security Plan Assessment

**CCSD Identifiers:**
- Command Communications Service Designator (CCSD) identifiers must be clearly labeled (if applicable)

**Internal and External Interfaces:**
- Show all external equipment/systems the system connects or communicates with
- All circuits with a CCSD (both internal and external) must be listed in the accreditation memo and added in eMASS at **System > Details > Connectivity/CCSD**

**Information Flows / PPS:**
- Information flow of all registered Ports and Protocols must be shown and labeled
- Must map to the PPS Worksheet Artifact
- Programs may submit a separate Information Flows artifact if adding flows to the topology creates clutter

**Deduplication:**
- Consolidate duplicate items (same software, hardware, firmware, subnet)
- If 4+ duplicate items: use ellipse "..." after the third hostname

**Required Device Labels (all devices MUST display):**
1. Function Name (e.g., OWA Server, Web Server, IDS, IPS, Firewall, Router)
2. Hostname (e.g., owa23.us.af.mil, 45thwebsrv)
3. Software/OS Version (e.g., Server 2012 R2 SP1, Windows 10, Oracle Database 12c)
4. Hardware Manufacturer (e.g., Dell, HP, Cisco)
5. Hardware Make/Model (e.g., PowerEdge 2950, ProLiant 2630, ISR 4221)
6. Firmware Version (e.g., IOS 12.4(25a), Phoenix BIOS 7.43a, NX-OS 6.2(2))
7. IP Address or IP Address Range (e.g., 137.12.86.52, 137.12.86.52-99)

> **NOTE:** If the system is classified, the topology must be protected IAW the Security Classification Guidance program. Providing IPs and specific technology may reveal information that should otherwise be handled securely.

---

## Attachment 2 — Timelines

*(Timelines were in graphical/table format in the original PDF and were not extracted as text.)*

---

*Source: USSF OSB AO Memorandum, 3 June 2026 — Required Artifacts for Interim Authority to Test (IATT)*
