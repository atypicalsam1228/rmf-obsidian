---
type: concept
framework: owasp-llm
status: draft
tags:
  - owasp-llm
  - llm-security
  - ai-security
created: 2026-05-08
updated: 2026-05-08
sources:
  - "[[Sources/OWASP-LLM/LLM01-prompt-injection]]"
  - "[[Sources/OWASP-LLM/LLM02-sensitive-information-disclosure]]"
  - "[[Sources/OWASP-LLM/LLM03-supply-chain]]"
  - "[[Sources/OWASP-LLM/LLM04-data-and-model-poisoning]]"
  - "[[Sources/OWASP-LLM/LLM05-improper-output-handling]]"
  - "[[Sources/OWASP-LLM/LLM06-excessive-agency]]"
  - "[[Sources/OWASP-LLM/LLM07-system-prompt-leakage]]"
  - "[[Sources/OWASP-LLM/LLM08-vector-and-embedding-weaknesses]]"
  - "[[Sources/OWASP-LLM/LLM09-misinformation]]"
  - "[[Sources/OWASP-LLM/LLM10-unbounded-consumption]]"
related:
  - "[[Wiki/owasp-llm01-prompt-injection]]"
  - "[[Wiki/owasp-llm06-excessive-agency]]"
  - "[[Wiki/nist-ai-rmf-core-functions]]"
---

# OWASP LLM Top 10 (2025) — Overview

> [!abstract] Summary
> The OWASP Top 10 for Large Language Model Applications (2025 edition) identifies the ten most critical security risks in LLM-powered systems. These risks are distinct from traditional web application security and require AI-specific mitigations. All 10 source documents are ingested in this vault.

## The Ten Risks

| ID | Risk | Core Concern |
|---|---|---|
| LLM01 | Prompt Injection | Malicious inputs alter LLM behavior or bypass safety controls |
| LLM02 | Sensitive Information Disclosure | LLM reveals training data, system prompts, or PII in responses |
| LLM03 | Supply Chain | Vulnerable models, datasets, or third-party plugins |
| LLM04 | Data and Model Poisoning | Corrupted training data introduces backdoors or biases |
| LLM05 | Improper Output Handling | Downstream systems blindly trust LLM output — XSS, SSRF, RCE |
| LLM06 | Excessive Agency | LLM granted too many permissions or autonomous actions |
| LLM07 | System Prompt Leakage | System prompt extracted via injection or inference |
| LLM08 | Vector and Embedding Weaknesses | Poisoned RAG data, embedding inversion attacks |
| LLM09 | Misinformation | LLM generates convincing but false information (hallucination) |
| LLM10 | Unbounded Consumption | Resource exhaustion via unrestricted LLM usage |

## LLM01 — Prompt Injection

> [!quote] OWASP LLM01:2025
> "A Prompt Injection Vulnerability occurs when user prompts alter the LLM's behavior or output in unintended ways. These inputs can affect the model even if they are imperceptible to humans, therefore prompt injections do not need to be human-visible/readable, as long as the content is parsed by the model."
> — [[Sources/OWASP-LLM/LLM01-prompt-injection]]

Two types: **direct** (user input manipulates model) and **indirect** (external data — websites, files — manipulates model). High severity in agentic systems.
See: [[Wiki/owasp-llm01-prompt-injection]]

## LLM06 — Excessive Agency

> [!quote] OWASP LLM06:2025
> "Excessive Agency is the vulnerability that enables damaging actions to be performed in response to unexpected, ambiguous or manipulated outputs from an LLM, regardless of what is causing the LLM to malfunction. Common triggers include hallucination/confabulation caused by poorly-engineered benign prompts, or just a poorly-performing model; direct/indirect prompt injection..."
> — [[Sources/OWASP-LLM/LLM06-excessive-agency]]

Root causes: excessive functionality, excessive permissions, excessive autonomy.
See: [[Wiki/owasp-llm06-excessive-agency]]

## Agentic System Risk Amplification

In multi-agent or tool-using LLM systems, several risks compound:

> [!warning] Agentic Risk Multiplier
> LLM01 (Prompt Injection) + LLM06 (Excessive Agency) is the most dangerous combination.
> An indirect prompt injection in a RAG document can hijack an agent with delete/write permissions.
> Mitigations: least-privilege tool access + human-in-the-loop for destructive actions.

## Mapping to Existing Frameworks

> [!info] Cross-Framework Mapping — OWASP LLM to NIST AI RMF
> | OWASP LLM | NIST AI RMF Function | Relevant Subcategory |
> |---|---|---|
> | LLM01 Prompt Injection | MANAGE | MG-2.2 (Manage AI risks) |
> | LLM02 Info Disclosure | GOVERN | GV-1.7 (Privacy) |
> | LLM04 Data Poisoning | MEASURE | MS-2.5 (Data quality) |
> | LLM06 Excessive Agency | MANAGE | MG-2.4 (Human oversight) |
> | LLM09 Misinformation | MEASURE | MS-2.6 (Explainability) |
> See: [[Wiki/nist-ai-rmf-core-functions]]

> [!info] Cross-Framework Mapping — OWASP LLM to NIST 800-53
> | OWASP LLM | NIST 800-53 Control |
> |---|---|
> | LLM01 Prompt Injection | SI-10 (Information Input Validation) |
> | LLM02 Info Disclosure | AC-3, SC-28 |
> | LLM05 Improper Output Handling | SI-10, SI-15 |
> | LLM06 Excessive Agency | AC-6 (Least Privilege), AC-3 |
> | LLM10 Unbounded Consumption | SC-5 (Denial of Service Protection) |

## Government Applicability

> [!info] Federal AI Governance Context
> - EO 14110 (Safe, Secure, and Trustworthy AI) requires agencies to assess AI risks
> - NIST AI RMF 1.0 is the primary federal framework for AI risk management
> - FedRAMP does not yet have an AI-specific authorization pathway — OWASP LLM risks must be addressed in the SSP under relevant 800-53 controls (SI-10, AC-6, SC-28)
> - See: [[Wiki/nist-ai-rmf-core-functions]]

## Related Notes

- [[Wiki/owasp-llm01-prompt-injection]]
- [[Wiki/owasp-llm06-excessive-agency]]
- [[Wiki/nist-ai-rmf-core-functions]]
