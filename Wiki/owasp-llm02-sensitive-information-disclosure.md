---
type: concept
framework: owasp-llm
status: draft
tags:
  - owasp-llm
  - llm-security
  - information-disclosure
  - privacy
  - LLM02
created: 2026-05-08
updated: 2026-05-08
sources:
  - "[[Sources/OWASP-LLM/LLM02-sensitive-information-disclosure]]"
related:
  - "[[Wiki/owasp-llm-top10-overview]]"
  - "[[Wiki/owasp-llm01-prompt-injection]]"
  - "[[Wiki/owasp-llm07-system-prompt-leakage]]"
  - "[[Wiki/nist-ai-rmf-core-functions]]"
---

# LLM02: Sensitive Information Disclosure

> [!abstract] Summary
> LLMs can inadvertently reveal PII, proprietary algorithms, training data, credentials, or confidential business data through their responses. This risk is amplified when LLMs are fine-tuned on sensitive data or when system prompts contain secrets. Mitigations focus on data sanitization, access controls, and output filtering.

## Definition

> [!quote] OWASP LLM02:2025 — Description
> "Sensitive information can affect both the LLM and its application context. This includes personal identifiable information (PII), financial details, health records, confidential business data, security credentials, and legal documents. Proprietary models may also have unique training methods and source code considered sensitive, especially in closed or foundation models."
> — [[Sources/OWASP-LLM/LLM02-sensitive-information-disclosure]]

> [!quote] OWASP LLM02:2025 — Risk Statement
> "LLMs, especially when embedded in applications, risk exposing sensitive data, proprietary algorithms, or confidential details through their output. This can result in unauthorized data access, privacy violations, and intellectual property breaches."
> — [[Sources/OWASP-LLM/LLM02-sensitive-information-disclosure]]

## Common Vulnerability Examples

> [!quote] OWASP LLM02:2025 — Proprietary Algorithm Exposure
> "Poorly configured model outputs can reveal proprietary algorithms or data. Revealing training data can expose models to inversion attacks, where attackers extract sensitive information or reconstruct inputs. For instance, as demonstrated in the 'Proof Pudding' attack (CVE-2019-20634), disclosed training data facilitated model extraction and inversion, allowing attackers to circumvent security controls in machine learning algorithms and bypass email filters."
> — [[Sources/OWASP-LLM/LLM02-sensitive-information-disclosure]]

Three main disclosure types:
1. **PII Leakage** — personal data from training or user interactions surfaces in responses
2. **Proprietary Algorithm Exposure** — model reveals internal logic or training data (enables inversion attacks)
3. **Sensitive Business Data Disclosure** — confidential info in generated responses

## Prevention Strategies

> [!quote] OWASP LLM02:2025 — Sanitization
> "Implement data sanitization to prevent user data from entering the training model. This includes scrubbing or masking sensitive content before it is used in training."
> — [[Sources/OWASP-LLM/LLM02-sensitive-information-disclosure]]

> [!quote] OWASP LLM02:2025 — Access Controls
> "Limit access to sensitive data based on the principle of least privilege. Only grant access to data that is necessary for the specific user or process. Limit model access to external data sources, and ensure runtime data orchestration is securely managed to avoid unintended data leakage."
> — [[Sources/OWASP-LLM/LLM02-sensitive-information-disclosure]]

> [!example] Implementation Guidance
> 1. **Pre-training:** Scrub PII from training datasets using NER and regex before fine-tuning
> 2. **System prompt:** Never embed credentials, API keys, or PII — use environment variables
> 3. **Output filtering:** Scan LLM responses for PII patterns before returning to user
> 4. **RAG scoping:** Restrict retrieval to documents the requesting user has access to
> 5. **Terms of Use:** Give users the ability to opt out of having interactions used for training

## Relationship to System Prompt Leakage

LLM02 and LLM07 (System Prompt Leakage) are related — both involve unintended disclosure. LLM02 covers training data and runtime outputs; LLM07 focuses on the system prompt itself.

> [!warning] Secret Storage Anti-Pattern
> Do not store API keys, credentials, or connection strings in system prompts. They can be extracted via prompt injection (LLM01) or inference attacks.
> See: [[Wiki/owasp-llm07-system-prompt-leakage]]

## Federal / FedRAMP Context

> [!info] Federal Context — Privacy
> - Systems handling PII must address LLM02 through NIST 800-53 **PT family** (PII Processing and Transparency)
> - FedRAMP SSP should document how LLM outputs are sanitized before returning to end users
> - NIST AI RMF GOVERN 1.7 requires privacy risk management for AI systems
> - EO 14110 requires agencies to assess AI risks to privacy

## Cross-Framework Mapping

> [!info] Cross-Framework
> - **NIST 800-53:** PT-3 (Personally Identifiable Information Processing Purposes), SC-28 (Protection of Information at Rest), AC-3 (Access Enforcement)
> - **NIST AI RMF:** GOVERN 1.7 (Privacy), MEASURE 2.6 (Output quality monitoring)
> - **NIST 800-171:** 03.01.02 (Access Enforcement), 03.13.x (System protection)

## Related Notes

- [[Wiki/owasp-llm-top10-overview]]
- [[Wiki/owasp-llm01-prompt-injection]]
- [[Wiki/owasp-llm07-system-prompt-leakage]]
- [[Wiki/nist-ai-rmf-core-functions]]
