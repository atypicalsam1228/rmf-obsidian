---
type: concept
framework: cross-framework
status: review
tags:
  - dod-rmf
  - authorization
  - ato
  - cato
  - iatt
  - disa
  - devsecops
created: 2026-07-17
updated: 2026-07-21
sources:
  - "[[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg]]"
  - "[[Sources/DoD-SRG/dodi-8510-01-rmf-dod-it]]"
  - "[[Sources/DoD-SRG/disa-connection-process-guide-v6-1]]"
related:
  - "[[Wiki/dod-srg-cloud-impact-levels]]"
  - "[[Wiki/fedramp-authorization-process]]"
  - "[[Wiki/fedramp-continuous-monitoring]]"
---

# DoD ATO with Conditions — Authorization Decision Types

> [!abstract]
> DoD RMF produces four distinct authorization outcomes. "ATO with conditions" is a formal AO risk acceptance decision that imposes operational restrictions on a system alongside the authorization. DoDI 8510.01 (July 2022) is the governing policy. This article covers all decision types, AO authority, and the authorization package requirements.

---

## Authorization Decision Types in DoD RMF

> [!quote] DoDI 8510.01 — Authorization Decision Types
> "Final risk determination and authorization decision definitions (e.g., interim authorization to test, ATO, ATO with conditions, and denial ATO) and examples are on the RMF KS."
> — [[Sources/DoD-SRG/dodi-8510-01-rmf-dod-it]] (Section 3, Authorize step)

| Decision | Type | Production-Ready |
|---|---|---|
| **IATT** | Interim Authorization to Test — temporary, restricted | No — testing only |
| **ATO** | Full authorization, no restrictions | Yes |
| **ATO with conditions** | Full authorization + AO-imposed restrictions | Yes, within stated conditions |
| **Denial ATO** | Authorization denied | No |
| **cATO** | Continuous ATO via automated telemetry (DevSecOps context) | Yes, while feeds are green |
| **PA** | DISA Provisional Authorization for commercial CSOs | Informs Mission Owner ATO |

---

## ATO with Conditions

An ATO with conditions is a **full formal authorization decision** in which the AO accepts residual risk while imposing explicit operational restrictions. The authorization package must include the authorization decision document alongside the security plan, SAR, and all POA&Ms.

### Authorization Package Requirements

> [!quote] DoDI 8510.01 — Authorization Package Contents
> "The security authorization documentation package is the minimum information necessary for the receiving organization to accept a system. The security authorization documentation package is made up of: (a) The security plan. (b) The security assessment report. (c) All POA&Ms. (d) The authorization decision document."
> — [[Sources/DoD-SRG/dodi-8510-01-rmf-dod-it]] (Section 3, Authorize step, Task R-4)

### AO Authority to Impose Conditions and Revoke

> [!quote] DoDI 8510.01 — AO Authority
> "An AO may downgrade or revoke an authorization decision at any time if risk conditions or concerns so warrant."
> — [[Sources/DoD-SRG/dodi-8510-01-rmf-dod-it]] (Section 4, AO responsibilities, paragraph (6))

> [!quote] DoDI 8510.01 — AO Risk Determination
> "A risk determination by the AO that reflects the risk management strategy, including risk tolerance, is rendered."
> — [[Sources/DoD-SRG/dodi-8510-01-rmf-dod-it]] (Table 6, Task R-2)

Key AO authorities under DoDI 8510.01:
- **Do not delegate** authorization decisions (may delegate other tasks to AODR)
- May **downgrade or revoke** at any time if risk conditions warrant
- Must inform operators of potential impacts when risks are not fully mitigated
- Must verify system meets cyberspace operational commander requirements before authorizing

### Authorization Tasks (Table 6 from DoDI 8510.01)

> [!quote] DoDI 8510.01 — Table 6: Authorization Tasks and Outcomes
> "Task R-1: Authorization Package — An authorization package is developed for submission to the AO. (SO, Common Control Provider, Senior Agency Official for Privacy)
> Task R-2: Risk Analysis and Determination — A risk determination by the AO that reflects the risk management strategy, including risk tolerance, is rendered. (AO or AODR)
> Task R-3: Risk Response — Risk responses for determined risks are provided. (AO or AODR)
> Task R-4: Authorization Decision — The authorization for the system or the common controls is approved or denied. (AO)
> Task R-5: Authorization Reporting — Authorization decisions, significant vulnerabilities, and risks are reported to organizational officials. (AO or AODR)"
> — [[Sources/DoD-SRG/dodi-8510-01-rmf-dod-it]] (Table 6)

### POA&M Requirement

> [!quote] DoDI 8510.01 — POA&M
> "Develop and maintain a plan of action and milestones (POA&M) to address known vulnerabilities in the system, subsystems, and system components in accordance with DoDI 8531.01."
> — [[Sources/DoD-SRG/dodi-8510-01-rmf-dod-it]] (Section 2, SO responsibilities)

### DISA Provisional Authorization (PA) Conditions

DISA-issued PAs for commercial cloud offerings are granted with an expiration date and explicit conditions the Mission Owner must follow before the PA can underpin a Mission Owner ATO.

> [!quote] DoD CSP SRG V1R6 — On-Premises CSO Authorization
> "The CSO must have a DOD Interim Authority to Test (IATT), conditional ATO, or PA to connect to the network for testing and must also possess a DOD ATO (with or without conditions) before going into production following normal DOD policy."
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg]]

---

## IATT — Interim Authorization to Test

> [!quote] DoDI 8510.01 — Authorization Decisions Include IATT
> "Final risk determination and authorization decision definitions (e.g., interim authorization to test, ATO, ATO with conditions, and denial ATO)..."
> — [[Sources/DoD-SRG/dodi-8510-01-rmf-dod-it]] (Section 3, Authorize step)

An IATT is a **temporary, highly restricted** authorization for testing only — not production. In the cloud context (per DoD CSP SRG V1R6):
- Allows a CSP or Mission Owner to begin onboarding with the Connection Approval Office (CAO) and the Secure Cloud Computing Architecture (SCCA)
- Enables testing activity on DISN (NIPRNet/SIPRNet) before live deployment
- Does not authorize production workloads

> [!quote] DISA CPG v6.1 — ATC Duration Under IATT
> "Under IATT, [the Approval to Connect expiration is] normally less than 90 days per DoDI 8510.01."
> — [[Sources/DoD-SRG/disa-connection-process-guide-v6-1|DISA CPG v6.1, Section 2.10]]

> [!info] DISN Connection vs. System-Level IATT
> The DISA CPG governs DISN connection approval (SNAP/SGS registration, ATC issuance by DISA CAO). For **airgapped/isolated systems with no DISN connection**, SNAP/SGS registration, PPSM tracking IDs, CSSP alignment memos, and the DISA CAO-issued ATC are not required. The system-level IATT is issued solely by the system's AO per DoDI 8510.01.
> — [[Sources/DoD-SRG/disa-connection-process-guide-v6-1|DISA CPG v6.1, Section 2.8.3]]

---

## cATO — Continuous Authorization to Operate

> [!danger] NEEDS SOURCE — cATO Framework
> The cATO framework is defined in DoD cloud modernization documentation (§3.2.4.4, "Capabilities for the Department of Defense," 25 Nov 2020) and the DoD DevSecOps Reference Design. Neither is ingested. The description below is derived from NotebookLM analysis of those documents. Ingest DoD DevSecOps Reference Design to verify.

cATO replaces the static point-in-time assessment cycle with a **persistent, automated authorization relationship**:
- Compliance and security telemetry feed directly into AO dashboards in near real-time
- AOs can audit system compliance on demand without waiting for manual assessments
- **Dynamic:** authorization remains active only while the automated data feed validates security posture — if the feed fails or flags unacceptable risk, the authorization is immediately called into question
- Eliminates "re-authorization sprints" and annual assessment crises

> [!info] cATO and FedRAMP 20x Connection
> FedRAMP 20x's ISCM mandate (automated, high-frequency data feeds) is architecturally aligned with DoD cATO. Both replace static documentation with continuous telemetry as the trust anchor.
> See [[Wiki/fedramp-continuous-monitoring]]

---

## Comparison: Authorization Decision Types

| Dimension | Full ATO | ATO with Conditions | cATO |
|---|---|---|---|
| Assessment basis | SSP + SAR + POA&M at point in time | SSP + SAR + POA&M + AO risk conditions | Continuous automated telemetry |
| Production authorized | Yes | Yes, within AO-stated conditions | Yes, while feeds are green |
| AO can revoke | Yes, if risk conditions warrant | Yes, at any time | Yes, if feed fails or flags unacceptable risk |
| Re-authorization cycle | Periodic | Periodic, conditions reviewed | Continuous — no discrete cycle |
| POA&M posture | Accepted residual risk | May include POA&M closure milestones as conditions | Real-time POA&M visibility to AO |

---

## Remaining Sources to Ingest

| Document | Gap |
|---|---|
| DoD DevSecOps Reference Design | cATO §3.2.4.4 formal definition |
