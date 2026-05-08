# RMF Compliance Vault — Index

> Auto-maintained by Claude Code. Last updated: 2026-05-08.

## Sources (Authoritative — Read-Only)

### FedRAMP (57 files)
- [[Sources/FedRAMP/_index|FedRAMP Sources Index]]
- **Baselines:** [[Sources/FedRAMP/fedramp-high-baseline|High]], [[Sources/FedRAMP/fedramp-moderate-baseline|Moderate]], [[Sources/FedRAMP/fedramp-low-baseline|Low]], [[Sources/FedRAMP/fedramp-li-saas-baseline|LI-SaaS]]
- **Templates:** SSP, SAP, SAR, RAR, POAM, ConMon, Package Checklist
- **Guidance:** Authorization boundary, crypto module selection, container scanning, testing requirements, authorization reuse
- **AWS Config:** Conformance packs (High/Moderate/Low/NIST) + control-to-rule mappings
- **Rev5 Playbooks:** [[Sources/FedRAMP/fedramp-rev5-ssp-playbook|SSP]], [[Sources/FedRAMP/fedramp-rev5-secure-configuration-guide|Secure Config]], [[Sources/FedRAMP/fedramp-rev5-conmon-playbook-introduction|ConMon Intro]], [[Sources/FedRAMP/fedramp-continuous-monitoring-playbook|ConMon Playbook]], [[Sources/FedRAMP/fedramp-rev5-baselines-transition-guide|Rev5 Transition Guide]]
- **FedRAMP 20x:** [[Sources/FedRAMP/fedramp-20x-collaborative-continuous-monitoring|Collaborative ConMon]], [[Sources/FedRAMP/fedramp-20x-vulnerability-detection-and-response|Vulnerability Detection & Response]]
- **Rev5 Playbooks (full set):** [[Sources/FedRAMP/fedramp-rev5-authorization-playbook-agency|Authorization]], [[Sources/FedRAMP/fedramp-rev5-preparation-playbook-agency|Preparation]], [[Sources/FedRAMP/fedramp-rev5-poam-playbook|POA&M]], [[Sources/FedRAMP/fedramp-rev5-sar-playbook|SAR]], [[Sources/FedRAMP/fedramp-rev5-conmon-documents-templates|ConMon Docs & Templates]]
- **Vulnerability Management:** [[Sources/FedRAMP/fedramp-vulnerability-scanning-requirements-rev4|Scanning Requirements Rev4]], [[Sources/FedRAMP/fedramp-rev5-vulnerability-scanning-playbook|Scanning Playbook Rev5]]
- **RFC:** [[Sources/FedRAMP/fedramp-rfc-0027-rev5-controls-baseline-update|RFC-0027]], [[Sources/FedRAMP/fedramp-rfc-0030-rev5-controls-ra-sa-sc-si-sr|RFC-0030 RA/SA/SC/SI/SR]], [[Sources/FedRAMP/fedramp-rfc-0012-cvm-community-discussion|RFC-0012 CVM]]
- **FAQs:** [[Sources/FedRAMP/fedramp-fips-mfa-requirement-faq|FIPS MFA]], [[Sources/FedRAMP/fedramp-cloud-security-control-responsibility|Control Responsibility]], [[Sources/FedRAMP/fedramp-3pao-definition-faq|3PAO Definition]]
- **DoD Cross-Reference:** [[Sources/FedRAMP/dod-srg-control-crosswalk-v1-0|DoD SRG Crosswalk v1.0]]

### Azure FedRAMP (24 files) — NEW
- [[Sources/Azure-FedRAMP/_index|Azure FedRAMP Sources Index]]
- **Authorization:** [[Sources/Azure-FedRAMP/azure-all-us-regions-fedramp-high-approved|All US Regions Approved]], [[Sources/Azure-FedRAMP/azure-cloud-services-fedramp-audit-scope|Audit Scope]], [[Sources/Azure-FedRAMP/azure-fedramp-compliance-offering|Azure FedRAMP Offering]], [[Sources/Azure-FedRAMP/azure-compliance-commercial-government-dod-secret|Commercial/Gov/DoD/Secret Tiers]]
- **Azure Government:** [[Sources/Azure-FedRAMP/azure-government-fedramp-rev5-secure-configuration|Rev5 Secure Config]], [[Sources/Azure-FedRAMP/azure-government-fedramp-high-regulatory-compliance|FedRAMP High Policy (Gov)]], [[Sources/Azure-FedRAMP/azure-policy-fedramp-high-regulatory-compliance|FedRAMP High Policy (Commercial)]]
- **Encryption/FIPS:** [[Sources/Azure-FedRAMP/azure-data-encryption-at-rest|Encryption at Rest]], [[Sources/Azure-FedRAMP/azure-fips-140-2-microsoft-compliance|FIPS 140-2]], [[Sources/Azure-FedRAMP/azure-application-gateway-fips-140|App Gateway FIPS]], [[Sources/Azure-FedRAMP/azure-managed-hsm-data-control|Managed HSM]], [[Sources/Azure-FedRAMP/azure-secrets-best-practices|Secrets Best Practices]]
- **Security Monitoring:** [[Sources/Azure-FedRAMP/azure-microsoft-sentinel-best-practices|Sentinel Best Practices]], [[Sources/Azure-FedRAMP/azure-defender-for-cloud-overview-dashboard|Defender for Cloud Dashboard]], [[Sources/Azure-FedRAMP/azure-defender-for-cloud-assign-regulatory-compliance|Assign Compliance Standards]]
- **Shared Responsibility:** [[Sources/Azure-FedRAMP/azure-shared-responsibility-model|Azure Shared Responsibility Model]]
- **Blueprints/Automation:** [[Sources/Azure-FedRAMP/azure-fedramp-moderate-blueprints|FedRAMP Moderate Blueprints]], [[Sources/Azure-FedRAMP/azure-blueprints-compliance-setup|Blueprints Setup]]
- **Service Trust Portal:** [[Sources/Azure-FedRAMP/azure-service-trust-portal-getting-started|Getting Started]], [[Sources/Azure-FedRAMP/azure-fedramp-documents-service-trust-portal|FedRAMP Documents]]

### NIST 800-53 Rev 5 (3 files)
- [[Sources/NIST-800-53/_index|NIST 800-53 Sources Index]]
- [[Sources/NIST-800-53/nist-800-53r5-catalog|Structured Catalog]] — 1000+ controls, all 20 families
- [[Sources/NIST-800-53/nist-sp-800-53r5-full|Full Publication]] — 492 pages
- [[Sources/NIST-800-53/aws-config-nist-800-53r5-mappings|AWS Config Mappings]] — 926 control-to-rule mappings

### OWASP LLM Top 10 (10 files)
- [[Sources/OWASP-LLM/_index|OWASP LLM Sources Index]]
- [[Sources/OWASP-LLM/LLM01-prompt-injection|LLM01]] [[Sources/OWASP-LLM/LLM02-sensitive-information-disclosure|LLM02]] [[Sources/OWASP-LLM/LLM03-supply-chain|LLM03]] [[Sources/OWASP-LLM/LLM04-data-and-model-poisoning|LLM04]] [[Sources/OWASP-LLM/LLM05-improper-output-handling|LLM05]]
- [[Sources/OWASP-LLM/LLM06-excessive-agency|LLM06]] [[Sources/OWASP-LLM/LLM07-system-prompt-leakage|LLM07]] [[Sources/OWASP-LLM/LLM08-vector-and-embedding-weaknesses|LLM08]] [[Sources/OWASP-LLM/LLM09-misinformation|LLM09]] [[Sources/OWASP-LLM/LLM10-unbounded-consumption|LLM10]]

### NIST AI RMF 1.0 (1 file)
- [[Sources/NIST-AI-RMF/_index|NIST AI RMF Sources Index]]
- [[Sources/NIST-AI-RMF/nist-ai-rmf-1-0|AI RMF 1.0]] — Govern, Map, Measure, Manage functions with all subcategories

### NIST 800-171 Rev 3 (2 files)
- [[Sources/NIST-800-171/_index|NIST 800-171 Sources Index]]
- [[Sources/NIST-800-171/nist-800-171r3-security-requirements|Security Requirements]] — 17 families, ~143 requirements
- [[Sources/NIST-800-171/aws-config-nist-800-171-mappings|AWS Config Mappings]]

### DoD SRG — Cloud Computing Y25M12 (5 files)
- [[Sources/DoD-SRG/_index|DoD SRG Sources Index]]
- [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg|CSP SRG V1R6]] — Security requirements for cloud service providers seeking DoD authorization
- [[Sources/DoD-SRG/u-cloud-computing-mission-owner-overview|Mission Owner Overview]]
- [[Sources/DoD-SRG/u-cloud-computing-mission-owner-net-srg-v1r2-manual-xccdf|Mission Owner Network SRG V1R2]] — XCCDF benchmark
- [[Sources/DoD-SRG/u-cloud-computing-mission-owner-os-srg-v1r3-manual-xccdf|Mission Owner OS SRG V1R3]] — XCCDF benchmark

## Wiki (LLM-Maintained)

Last compiled: 2026-05-08 (pass 2) — 20 articles across 6 frameworks

### FedRAMP
- [[Wiki/fedramp-baseline-overview]] — Low / LI-SaaS / Moderate / High baseline comparison, parameter overrides
- [[Wiki/fedramp-access-control]] — AC family, IAM parameters, MFA requirements, AWS implementation
- [[Wiki/fedramp-aws-config-conformance-packs]] — AWS Config rules, conformance pack parameters, deployment
- [[Wiki/fedramp-vulnerability-management]] — RA-5 / SI-2 SLAs, POA&M integration, FedRAMP 20x CVM
- [[Wiki/fedramp-continuous-monitoring]] — ConMon deliverables calendar, CA-7, FedRAMP 20x changes
- [[Wiki/fedramp-nist-800-53-relationship]] — Layering model, parameter overrides, Rev 4→5 transition
- [[Wiki/fedramp-authorization-process]] — RAR → SSP/SAP/SAR → ATO/P-ATO → ConMon pathway

### NIST 800-53
- [[Wiki/nist-800-53-control-families]] — All 20 families, key controls, AWS implementation patterns

### NIST 800-171 / CUI
- [[Wiki/nist-800-171-cui-protection]] — 17 families, CUI scope, CMMC relationship, DFARS 252.204-7012

### OWASP LLM
- [[Wiki/owasp-llm-top10-overview]] — All 10 risks, cross-framework mappings
- [[Wiki/owasp-llm01-prompt-injection]] — Direct/indirect injection, mitigations
- [[Wiki/owasp-llm02-sensitive-information-disclosure]] — PII leakage, training data exposure
- [[Wiki/owasp-llm04-data-model-poisoning]] — Training corruption, backdoors, sleeper agents
- [[Wiki/owasp-llm05-improper-output-handling]] — XSS/SQLi/RCE from unsanitized output
- [[Wiki/owasp-llm06-excessive-agency]] — Excessive functionality/permissions/autonomy, agentic risk
- [[Wiki/owasp-llm07-system-prompt-leakage]] — Credential exposure, external enforcement principle
- [[Wiki/owasp-llm10-unbounded-consumption]] — Denial of Wallet, model extraction, rate limiting

### NIST AI RMF
- [[Wiki/nist-ai-rmf-core-functions]] — Govern / Map / Measure / Manage, trustworthiness, federal context

### DoD / ICAM / Impact Levels
- [[Wiki/dod-srg-cloud-impact-levels]] — IL2/IL4/IL5/IL6, FedRAMP+, DoD PA pathway (CSP SRG V1R6)
- [[Wiki/dodi-8520-04-access-management-icam]] — DoDI 8520.04 ICAM, Zero Trust, FedRAMP CSP implications

## Quick Reference

- **Compile new material:** Drop files in `Capture/`, then run `/rmf-vault compile`
- **Query the vault:** `/rmf-vault query <question>`
- **Health check:** `/rmf-vault lint`
- **Rebuild indexes:** `/rmf-vault index`
- **Vault status:** `/rmf-vault status`
- **Skills:** `/nist-800-53`, `/fedramp`, `/nist-ai-rmf` for embedded rule lookups
