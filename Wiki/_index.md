# Wiki Index

> Auto-maintained by Claude Code. LLM-created articles with citations back to `Sources/`.
> Last updated: 2026-07-06

## FedRAMP

- [[fedramp-moderate-au-logging-questionnaire]] — Full AU-1 through AU-12 application logging assessment questionnaire with evidence checklist; includes M-21-31 retention tiers and FedRAMP Moderate parameters
- [[azure-subscription-structure-fedramp-moderate]] — Azure subscription hierarchy, management plane vs data plane, required subscriptions for FedRAMP Moderate boundary, staging scoping rules, shared management plane constraints
- [[fedramp-moderate-platform-bau-requirements]] — BAU operational requirements for a FedRAMP Moderate multi-tenant platform, organized by control domain with exact quoted parameters
- [[fedramp-moderate-platform-bau-cadence-training]] — Team training guide: same BAU requirements organized by cadence (daily/weekly/monthly/quarterly/annual), with What/Why/Evidence for each task
- [[fedramp-moderate-bau-team-assignments]] — All 79 BAU tasks assigned to Engineering / ISSO / Sec Ops / Joint; Joint tasks include party-level split showing who does what
- [[fedramp-moderate-cdse-training-mapping]] — AT-2/AT-3/IR-2 training requirements mapped to CDSE courses; overlap analysis showing CAC satisfies AT-2(2) and AT-2(3); consolidated minimum course set; gaps CDSE cannot fill
- [[fedramp-baseline-overview]] — Comparison of Low / LI-SaaS / Moderate / High baselines, parameter overrides, use cases
- [[fedramp-moderate-federal-mandates]] — All federal mandate requirements baked into FedRAMP Moderate: phishing-resistant MFA, FIPS, DNSSEC, DMARC, KEV, M-21-31, BODs, Section 889, and more
- [[fedramp-soc-bau-tracker-build-lessons]] — V5→V6 gap analysis: missed hard requirements, best-practice/requirement confusion instances, M-21-31 rescission, root cause analysis, corrective actions
- [[ifs-soc-fedramp-control-verification]] — Source-verified control parameters from IFS SOC BAU session; 4 confirmed, 3 discrepancies corrected (IR-6 timeframe, AU-11 online retention, RA-10/PM-16 baseline inclusion)

- [[fedramp-training-access-prerequisites]] — AT-3/PL-4 as hard access gates before provisioning; IR-2 post-access windows; AC-2 enforcement path for missed training deadlines
- [[fedramp-access-control]] — AC family controls, FedRAMP IAM parameters, MFA requirements, AWS implementation
- [[fedramp-aws-config-conformance-packs]] — AWS Config rules for FedRAMP levels, parameter values, deployment guidance
- [[fedramp-vulnerability-management]] — RA-5 / SI-2 requirements, remediation SLAs, POA&M integration, FedRAMP 20x CVM
- [[fedramp-continuous-monitoring]] — ConMon deliverables, CA-7 requirements, monthly cycle, FedRAMP 20x changes
- [[fedramp-nist-800-53-relationship]] — How FedRAMP layers on NIST 800-53, parameter overrides, Rev 4→5 transition
- [[fedramp-authorization-process]] — Preparation → RAR → SSP/SAP/SAR → ATO/P-ATO → ConMon; FedRAMP 20x changes
- [[fedramp-documentation-requirements]] — Full package checklist, required formats, where documents are submitted (MAX.gov, designated repository, CSP secure repo)
- [[section-508-fedramp-compliance]] — Section 508 is not a FedRAMP control; enforced through FAR 39.2 procurement, not ATO; VPAT/ACR required for federal sales

## Process / Methodology

- [[source-driven-enumeration-methodology]] — 4-step process for building compliance artifacts: keyword generation from source → full control enumeration → production → accuracy check; prevents missed requirements and best-practice/requirement confusion

## NIST 800-53

- [[nist-800-53-control-families]] — All 20 control families, key controls per family, AWS implementation patterns
- [[policy-and-procedures-ssp-requirements]] — Are procedures required? Does the SSP satisfy them? Review cadences, disqualifiers, and what assessors test

## NIST 800-171 / CUI

- [[nist-800-171-cui-protection]] — CUI protection requirements, 17 families, CMMC relationship, DFARS mandate

## CMMC

- [[cmmc-siem-requirements]] — All 9 AU practices (3.3.1–3.3.9) mapped to SIEM functions; retention, log sources, AWS Config rules
- [[cmmc-remote-work-scoping]] — Home network scope decisions: alternate work sites, split tunneling, BYOD, AC.L2-3.1.12 and SC.L2-3.13.7
- [[cmmc-l2-asset-category-control-reference]] — All 14 domains mapped to asset categories (CUI, SPA, CRMA, Specialized); SPA device-type quick-reference table; CRMA exception and FIPS scoping rules
- [[cmmc-l2-iam-auth-deviation-paths]] — Alternate implementation paths for AC.L2-3.1.5 (IAM/OCP/Terraform least privilege) and IA.L2-3.5.3 (Keycloak/RedHat IDM/FIDO2/mTLS); upstream/downstream CUI flow model; SPRS/POA&M deviation mechanics; all paths grounded in NIST 800-171 and 800-63B

## OWASP LLM

- [[owasp-llm-top10-overview]] — All 10 LLM risks, cross-framework mappings to NIST AI RMF and 800-53
- [[owasp-llm01-prompt-injection]] — Direct/indirect injection, impact, prevention strategies
- [[owasp-llm02-sensitive-information-disclosure]] — PII leakage, training data exposure, proprietary algorithm disclosure
- [[owasp-llm04-data-model-poisoning]] — Training data corruption, backdoors, sleeper agents, supply chain
- [[owasp-llm05-improper-output-handling]] — XSS/SQLi/RCE from unsanitized LLM output, zero-trust output rule
- [[owasp-llm06-excessive-agency]] — Excessive functionality/permissions/autonomy, multi-agent risk, mitigations
- [[owasp-llm07-system-prompt-leakage]] — Credential exposure, business logic disclosure, external enforcement principle
- [[owasp-llm10-unbounded-consumption]] — Denial of Wallet, model extraction, rate limiting mitigations

## NIST AI RMF

- [[nist-ai-rmf-core-functions]] — Govern / Map / Measure / Manage functions, trustworthiness characteristics, federal context

## DoD / ICAM / Impact Levels

- [[dod-srg-cloud-impact-levels]] — IL2/IL4/IL5/IL6 definitions, FedRAMP+ concept, DoD PA pathway (CSP SRG V1R6)
- [[dodi-8520-04-access-management-icam]] — DoDI 8520.04: ICAM access management for DoD IT systems

## Personnel Security / US Person Requirements

- [[jira-cloud-fedramp-us-person-requirements]] — Can non-US persons maintain FedRAMP Jira Cloud? Civilian vs. DoD split, IL-based restrictions, Atlassian shared responsibility model
- [[privileged-admin-citizenship-requirements]] — Do privileged admins (e.g., YubiKey admins) need to be US-based? SRG Table 5-1 citizenship vs. geographic location distinction; IL2–IL6 breakdown; Tier investigation minimums
