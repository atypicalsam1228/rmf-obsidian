# Wiki Index

> Auto-maintained by Claude Code. LLM-created articles with citations back to `Sources/`.
> Last updated: 2026-05-08 (compile pass 2)

## FedRAMP

- [[fedramp-baseline-overview]] — Comparison of Low / LI-SaaS / Moderate / High baselines, parameter overrides, use cases
- [[fedramp-access-control]] — AC family controls, FedRAMP IAM parameters, MFA requirements, AWS implementation
- [[fedramp-aws-config-conformance-packs]] — AWS Config rules for FedRAMP levels, parameter values, deployment guidance
- [[fedramp-vulnerability-management]] — RA-5 / SI-2 requirements, remediation SLAs, POA&M integration, FedRAMP 20x CVM
- [[fedramp-continuous-monitoring]] — ConMon deliverables, CA-7 requirements, monthly cycle, FedRAMP 20x changes
- [[fedramp-nist-800-53-relationship]] — How FedRAMP layers on NIST 800-53, parameter overrides, Rev 4→5 transition
- [[fedramp-authorization-process]] — Preparation → RAR → SSP/SAP/SAR → ATO/P-ATO → ConMon; FedRAMP 20x changes

## NIST 800-53

- [[nist-800-53-control-families]] — All 20 control families, key controls per family, AWS implementation patterns

## NIST 800-171 / CUI

- [[nist-800-171-cui-protection]] — CUI protection requirements, 17 families, CMMC relationship, DFARS mandate

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
