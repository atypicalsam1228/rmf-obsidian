---
type: concept
framework: owasp-llm
status: draft
tags:
  - owasp-llm
  - llm-security
  - system-prompt
  - information-disclosure
  - LLM07
created: 2026-05-08
updated: 2026-05-08
sources:
  - "[[Sources/OWASP-LLM/LLM07-system-prompt-leakage]]"
related:
  - "[[Wiki/owasp-llm-top10-overview]]"
  - "[[Wiki/owasp-llm01-prompt-injection]]"
  - "[[Wiki/owasp-llm02-sensitive-information-disclosure]]"
---

# LLM07: System Prompt Leakage

> [!abstract] Summary
> System Prompt Leakage is the risk that system prompts, which contain application logic, guardrails, role definitions, and sometimes secrets, can be extracted by attackers. The real vulnerability is not the disclosure of the prompt text itself, but what the prompt reveals — credentials, business logic, permission structures — and the fact that security controls are being delegated to the LLM rather than enforced externally.

## Definition

> [!quote] OWASP LLM07:2025 — Description
> "The system prompt leakage vulnerability in LLMs refers to the risk that the system prompts or instructions used to steer the behavior of the model can also contain sensitive information that was not intended to be discovered. System prompts are designed to guide the model's output based on the requirements of the application, but may inadvertently contain secrets."
> — [[Sources/OWASP-LLM/LLM07-system-prompt-leakage]]

## The Core Security Insight

> [!quote] OWASP LLM07:2025 — Root Cause
> "It's important to understand that the system prompt should not be considered a secret, nor should it be used as a security control. Accordingly, sensitive data such as credentials, connection strings, etc. should not be contained within the system prompt language."
> — [[Sources/OWASP-LLM/LLM07-system-prompt-leakage]]

> [!quote] OWASP LLM07:2025 — Fundamental Risk
> "The fundamental security risk is not that these have been disclosed, it is that the application allows bypassing strong session management and authorization checks by delegating these to the LLM, and that sensitive data is being stored in a place that it should not be."
> — [[Sources/OWASP-LLM/LLM07-system-prompt-leakage]]

## Common Risk Examples

> [!quote] OWASP LLM07:2025 — Exposure of Internal Rules
> "The system prompt of the application reveals information on internal decision-making processes that should be kept confidential...For example - There is a banking application that has a chatbot and its system prompt may reveal information like: 'The Transaction limit is set to $5000 per day for a user. The Total Loan Amount for a user is $10,000'. This information allows the attackers to bypass the security controls in the application."
> — [[Sources/OWASP-LLM/LLM07-system-prompt-leakage]]

Four main exposure types:
1. **Sensitive Functionality** — reveals API keys, database credentials, architecture details
2. **Internal Rules** — reveals business logic limits that can be exploited
3. **Filtering Criteria** — reveals what the system blocks, enabling bypass attempts
4. **Permissions and Roles** — reveals role-based permission structures → privilege escalation

## Prevention Strategies

> [!quote] OWASP LLM07:2025 — Separate Sensitive Data
> "Avoid embedding any sensitive information (e.g. API keys, auth keys, database names, user roles, permission structure of the application) directly in the system prompts. Instead, externalize such information to the systems that the model does not directly access."
> — [[Sources/OWASP-LLM/LLM07-system-prompt-leakage]]

> [!quote] OWASP LLM07:2025 — External Enforcement
> "Since LLMs are susceptible to other attacks like prompt injections which can alter the system prompt, it is recommended to avoid using system prompts to control the model behavior where possible. Instead, rely on systems outside of the LLM to ensure this behavior. For example, detecting and preventing harmful content should be done in external systems."
> — [[Sources/OWASP-LLM/LLM07-system-prompt-leakage]]

> [!example] Design Principles
> - Secrets belong in a secrets manager (AWS Secrets Manager, Azure Key Vault) — not in prompts
> - Authorization logic belongs in API middleware — not delegated to the LLM
> - Guardrails belong in external classifiers/filters — not solely in prompt instructions
> - Treat the prompt as "eventually visible" and design accordingly

## Attacker Inference Without Full Extraction

> [!quote] OWASP LLM07:2025 — Inference from Behavior
> "Even if the exact wording is not disclosed, attackers interacting with the system will almost certainly be able to determine many of the guardrails and formatting restrictions that are present in system prompt language in the course of using the application, sending utterances to the model, and observing the results."
> — [[Sources/OWASP-LLM/LLM07-system-prompt-leakage]]

## Cross-Framework Mapping

> [!info] Cross-Framework
> - **NIST 800-53:** SC-28 (at rest protection for credentials), IA-5 (Authenticator management — don't store credentials in prompts), SA-8 (Security engineering principles)
> - **NIST AI RMF:** GOVERN 6.2 (Policies for AI design), MAP 2.2 (Context understanding)

## Related Notes

- [[Wiki/owasp-llm-top10-overview]]
- [[Wiki/owasp-llm01-prompt-injection]]
- [[Wiki/owasp-llm02-sensitive-information-disclosure]]
