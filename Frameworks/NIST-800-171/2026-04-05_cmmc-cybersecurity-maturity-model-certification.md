---
type: guide
framework: nist-800-171
status: final
tags:
  - cmmc
  - nist-800-171
  - cui
  - fci
  - defense-contractors
  - compliance
  - dfars
created: 2026-04-05
updated: 2026-04-05
notebooklm_notebook: "CMMC Research: Cybersecurity Maturity Model Certification — 2026-04-05"
notebooklm_id: bedc5665-740f-48cb-98ec-4431a9c608e3
---

# CMMC: Cybersecurity Maturity Model Certification

## Summary

CMMC is the DoD's program to verify that defense contractors actually implement the cybersecurity requirements they've been self-attesting to since 2017. The final DFARS rule took effect November 10, 2025, making CMMC a contractual precondition for bidding on and winning defense contracts. The program uses a three-tiered model (Levels 1-3) with phased rollout through November 2028, progressively requiring third-party and government-led assessments.

> "It's no longer a policy aspiration, but a contractual and enforceable condition of doing business." — SecurityMetrics

## The Three Certification Levels

| Level | Protects | Controls | Standards | Assessment |
|-------|----------|----------|-----------|------------|
| **Level 1** (Foundational) | FCI | 15 | FAR 52.204-21 | Annual self-assessment |
| **Level 2** (Advanced) | CUI | 110 | NIST SP 800-171 Rev 2 | Self-assessment OR C3PAO (triennial) |
| **Level 3** (Expert) | Sensitive CUI | 110 + 24 | NIST 800-171 + NIST SP 800-172 | DIBCAC government assessment (triennial) |

All levels require annual affirmation in SPRS by a senior company official. The affirmation makes the executive **personally and legally responsible** for accuracy.

### Level 1: Foundational (FCI)
- 15 basic safeguarding controls from FAR 52.204-21
- Annual self-assessment, results in SPRS
- POA&Ms are **not permitted** — all 15 controls must be fully met
- Pass/fail: no conditional status available

### Level 2: Advanced (CUI)
- 110 security requirements aligned with NIST SP 800-171 Revision 2
- Assessment type depends on program sensitivity:
  - **Self-assessment** for lower-risk programs
  - **C3PAO certification** every 3 years for prioritized acquisitions
- Conditional status requires **minimum 80% score**
- POA&Ms allowed for non-critical controls, must close within **180 days**
- Cloud service providers must have **FedRAMP Moderate** authorization
- Scores entered in SPRS (self) or eMASS (C3PAO)

### Level 3: Expert (Advanced Persistent Threats)
- All Level 2 requirements PLUS 24 enhanced controls from NIST SP 800-172
- **All Level 2 POA&Ms must be closed before Level 3 assessment begins**
- Assessed exclusively by DIBCAC (government-led)
- Conditional status requires minimum 80% score on Level 3 requirements

## POA&M Rules

### Controls That CANNOT Be on a POA&M

**Level 2 (cannot defer):**
- External Connections (CUI Data)
- Control Public Information (CUI Data)
- System Security Plan
- Escort Visitors (CUI Data)
- Physical Access Logs (CUI Data)
- Manage Physical Access (CUI Data)
- Any control with point value > 1 (except CUI encryption in some cases)

**Level 3 (cannot defer):**
- Security Operations Center
- Cyber Incident Response Team
- Threat-Informed Risk Assessment
- Supply Chain Risk Response
- Supply Chain Risk Plan
- Security Solution Rationale
- Specialized Asset Security

**Closeout:** POA&Ms must be resolved within **180 days** of Conditional status date. Failure = status expires, organization loses certification.

## Phased Implementation Timeline

| Phase | Starts | Requirements |
|-------|--------|-------------|
| **Phase 1** (current) | Nov 10, 2025 | Level 1 & Level 2 self-assessments in new solicitations. DoD may require Level 2 C3PAO for high-priority programs. |
| **Phase 2** | Nov 10, 2026 | Level 2 C3PAO certification required in nearly all applicable solicitations. Self-certification no longer sufficient for most CUI contracts. |
| **Phase 3** | Nov 10, 2027 | Level 2 C3PAO required for option periods on existing contracts. Level 3 (DIBCAC) introduced for most sensitive programs. |
| **Phase 4** | Nov 10, 2028 | Full implementation — all applicable solicitations, contracts, and option periods including pre-rollout contracts. |

> "If your CMMC status isn't confirmed in the Supplier Performance Risk System (SPRS), you may find yourself ineligible for award before the technical evaluation even begins." — SecurityMetrics

## Legal and Compliance Risks

### False Claims Act (FCA) Liability
Misrepresenting CMMC compliance status to win or maintain contracts can trigger FCA enforcement. Senior officials must digitally sign annual affirmations, creating personal legal liability for assessment accuracy. (Source: Alston & Bird)

### Supply Chain Flow-Down
Prime contractors must verify subcontractor CMMC status in SPRS before awarding subcontracts or sharing sensitive data. This extends compliance obligations across the entire Defense Industrial Base (300,000+ companies). Unprepared subcontractors will be dropped from existing supply chains.

### FedRAMP Connection
Cloud service providers handling CUI must obtain FedRAMP Moderate authorization or equivalent. This creates a direct compliance dependency between CMMC Level 2 and FedRAMP.

## Preparation Checklist

1. **Identify your data** — determine FCI vs. CUI in your systems
2. **Determine your level** — FCI only = Level 1, CUI = Level 2, sensitive CUI = Level 3
3. **Gap analysis** against NIST SP 800-171 Rev 2 (Level 2) or FAR 52.204-21 (Level 1)
4. **System Security Plan** — critical requirement, cannot be deferred via POA&M
5. **Submit to SPRS** — self-assessment score + senior official affirmation
6. **Engage C3PAO early** — Level 2 readiness takes 6-18 months, limited assessor availability
7. **Assess subcontractors** — flow-down obligations apply to all tiers
8. **Budget for ongoing compliance** — annual affirmations, triennial reassessments

## Free Resources

| Resource | URL |
|----------|-----|
| DoD CMMC Official Site | https://dodcio.defense.gov/CMMC/ |
| CMMC Assessment Guide Level 2 (PDF) | https://dodcio.defense.gov/Portals/0/Documents/CMMC/AssessmentGuideL2v2.pdf |
| Defense Acquisition University Training | https://www.dau.edu/cybersecurity/training |
| DCISE No-Cost Cybersecurity Resources | https://www.dc3.mil/Missions/DIB-Cybersecurity/DCISE-Resources/ |
| Cyber AB Marketplace (find C3PAOs) | https://cyberab.org/marketplace |
| NIST SP 800-171 Rev 2 | https://csrc.nist.gov/pubs/sp/800/171/r2/upd1/final |
| NIST SP 800-172 | https://csrc.nist.gov/pubs/sp/800/172/final |

## Verification Notes

This research was verified through NotebookLM cross-referencing across 5 authoritative sources. All factual claims (level requirements, control counts, dates, POA&M rules) were confirmed with citations across multiple sources. No contradictions found.

## Sources

| # | Title | URL | Type |
|---|-------|-----|------|
| 1 | About CMMC - DoD CIO | https://dodcio.defense.gov/cmmc/About/ | Official (.gov) |
| 2 | Get to Know CMMC - GSA | https://www.gsa.gov/blog/2026/02/12/get-to-know-the-cybersecurity-maturity-model-certification | Official (.gov) |
| 3 | CMMC Homepage - DoD CIO | https://dodcio.defense.gov/CMMC/ | Official (.gov) |
| 4 | CMMC Compliance Roadmap - SecurityMetrics | https://www.securitymetrics.com/blog/cmmc-compliance-roadmap | Industry |
| 5 | DFARS 252.204-7021 | https://www.acquisition.gov/dfars/252.204-7021 | Regulatory |
| 6 | CMMC New Era - Alston & Bird | https://www.alston.com/en/insights/publications/2025/11/cmmc-cybersecurity-compliance-defense | Legal analysis |
| 7 | CMMC Requirements - Drata | https://drata.com/grc-central/cmmc-requirements | Industry |
| 8 | CMMC Assessment Guide - MadSecurity | https://madsecurity.com/cmmc-assessment-guide-roadmap | Industry |
| 9 | CMMC 2.0 for DoD Contractors - Elevate | https://elevateconsult.com/insights/cmmc-2-0-certification-for-dod-contractors-what-you-need-to-know-before-2026-deadlines/ | Industry |
