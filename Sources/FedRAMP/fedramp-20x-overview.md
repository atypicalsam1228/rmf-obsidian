# FedRAMP 20x — Program Overview

**Source:** https://www.fedramp.gov/20x/  
**Scraped:** 2026-08-03  
**Status:** Active — Phase 3 (Wide-Scale Adoption)

---

## What It Is

FedRAMP 20x is a fundamental shift from traditional compliance-focused cloud security assessment. The program moves "beyond traditional compliance to focus on the security decisions that matter most." Rather than uniform requirements across all services, CSPs establish custom security goals and prove effectiveness through continuous measurement, with agencies making risk-based decisions aligned to specific mission needs.

## Core Principles

1. **Transparency** — CSPs share honest security information without meeting arbitrary requirement bars
2. **Flexibility** — Engineering decisions producing secure outcomes appropriate to each provider's environment are encouraged
3. **Accountability** — Assessments demonstrate business value through effectiveness analysis rather than checkbox audits
4. **Accuracy** — Reviews focus on decision effectiveness rather than questioning validity
5. **Automatic Validation** — Status, progress, and outcomes should be automatically enforced and validated whenever possible

## Certification Classes

| Class | Impact Level | Status |
|---|---|---|
| Class A | Mature security programs, minimal upfront documentation | Pilot complete; available |
| Class B | Low impact, small-scale or light-use services | Available |
| Class C | Moderate impact, common enterprise services deployed across agencies | Available (rules finalized 2026-06-25) |
| Class D | High impact | Under development, Phase 4, estimated FY27 Q1-Q2 |

**Class C is the FedRAMP Moderate equivalent.**

## Key Structural Change: Rulesets Replace Control Families

Legacy FedRAMP organized requirements by NIST 800-53 control families (AC, AU, CA, CM, etc.). FedRAMP 20x organizes requirements into 15 named **Rulesets** for Class C:

| Acronym | Ruleset Name | Rules |
|---|---|---|
| AFC | Addressing FedRAMP Communication | 16 |
| CCM | Collaborative Continuous Monitoring | 19 |
| CDS | Certification Data Sharing | 20 |
| CMU | Cryptographic Module Use | 3 |
| CPO | Certification Package Overview | 4 |
| FRC | FedRAMP Certification | 15 |
| IEC | Incident Evaluation and Communication | 8 |
| IVV | Independent Verification and Validation | 16 |
| MAS | Minimum Assessment Scope | 5 |
| MKT | Marketplace Listing | 12 |
| SCG | Secure Configuration Guide | 9 |
| SCN | Significant Change Notification | 17 |
| SDR | Security Decision Record | 4 |
| VDR | Vulnerability Detection and Response | 17 |
| VER | Vulnerability Evaluation and Reporting | 23 |

## Key Assessment Change: KSIs Replace Point-in-Time Audits

Legacy FedRAMP used annual point-in-time 3PAO control audits. FedRAMP 20x uses **Key Security Indicators (KSIs)** — automated, near-real-time measurements replacing static yearly manual assessments. Providers continuously validate security measures through automated evidence rather than periodic compliance snapshots.

## Phase Timeline

| Phase | Period | Status |
|---|---|---|
| Phase 1 | FY25 Q3-Q4 | Complete — Low pilot; 13 reviews; first authorizations July 2025 |
| Phase 2 | FY26 Q1-Q2 | Complete — Moderate pilot; 14 submissions; first cohort authorized March 6, 2026 |
| Phase 3 | FY26 Q3-Q4 | **Active** — Wide-scale adoption; submission pipeline opens FY26 Q4 |
| Phase 4 | FY27 Q1-Q2 | Planned — Class D (High) pilot |
| Phase 5 | FY27 Q3-Q4 | Planned — **Legacy Rev5 sunset; new Rev5 certifications stop June 11, 2027** |

## Policy Foundation

- **OMB M-24-15** (July 2024) — replaced previous FedRAMP policy; directs new authorization paths, automation, and government-wide cloud adoption
- **FedRAMP Authorization Act** (December 2022) — established FedRAMP in law as government-wide standardized approach

## Consolidated Rules for 2026

The authoritative rule reference is at https://fedramp.gov/2026/ — machine-readable versions available on GitHub. Rules are organized by ruleset with MUST/SHOULD/MAY classifications per rule.
