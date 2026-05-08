---
type: concept
framework: owasp-llm
status: draft
tags:
  - owasp-llm
  - llm-security
  - denial-of-service
  - resource-exhaustion
  - LLM10
created: 2026-05-08
updated: 2026-05-08
sources:
  - "[[Sources/OWASP-LLM/LLM10-unbounded-consumption]]"
related:
  - "[[Wiki/owasp-llm-top10-overview]]"
  - "[[Wiki/nist-800-53-control-families]]"
---

# LLM10: Unbounded Consumption

> [!abstract] Summary
> Unbounded Consumption occurs when an LLM application allows excessive, uncontrolled inference requests — enabling DoS attacks, financial exhaustion ("Denial of Wallet"), model theft via API extraction, and service degradation. High LLM compute costs make this uniquely damaging compared to traditional resource exhaustion attacks.

## Definition

> [!quote] OWASP LLM10:2025 — Description
> "Unbounded Consumption occurs when a Large Language Model (LLM) application allows users to conduct excessive and uncontrolled inferences, leading to risks such as denial of service (DoS), economic losses, model theft, and service degradation. The high computational demands of LLMs, especially in cloud environments, make them vulnerable to resource exploitation and unauthorized usage."
> — [[Sources/OWASP-LLM/LLM10-unbounded-consumption]]

## Attack Vectors

> [!quote] OWASP LLM10:2025 — Denial of Wallet
> "By initiating a high volume of operations, attackers exploit the cost-per-use model of cloud-based AI services, leading to unsustainable financial burdens on the provider and risking financial ruin."
> — [[Sources/OWASP-LLM/LLM10-unbounded-consumption]]

> [!quote] OWASP LLM10:2025 — Model Extraction via API
> "Attackers may query the model API using carefully crafted inputs and prompt injection techniques to collect sufficient outputs to replicate a partial model or create a shadow model. This not only poses risks of intellectual property theft but also undermines the integrity of the original model."
> — [[Sources/OWASP-LLM/LLM10-unbounded-consumption]]

Five main attack patterns:
1. **Variable-Length Input Flood** — varying length inputs exploit processing inefficiencies → resource exhaustion
2. **Denial of Wallet (DoW)** — high-volume API calls drain cloud AI service budgets
3. **Continuous Input Overflow** — inputs exceeding context window → excessive compute
4. **Resource-Intensive Queries** — complex prompts requiring deep reasoning → prolonged processing
5. **Model Extraction** — iterative API queries to clone model behavior

> [!quote] OWASP LLM10:2025 — Functional Model Replication
> "Using the target model to generate synthetic training data can allow attackers to fine-tune another foundational model, creating a functional equivalent. This circumvents traditional query-based extraction methods, posing significant risks to proprietary models and technologies."
> — [[Sources/OWASP-LLM/LLM10-unbounded-consumption]]

## Prevention Strategies

> [!example] Mitigations for Unbounded Consumption
> 1. **Rate limiting** — per-user, per-IP, per-API-key request limits
> 2. **Token budgets** — hard limits on input and output token counts per request
> 3. **Request queuing** — throttle concurrent requests to prevent spike exhaustion
> 4. **Cost alerts** — cloud billing alerts when LLM spend exceeds thresholds
> 5. **Authentication and quotas** — require auth for all API access; enforce daily/monthly quotas
> 6. **Anomaly detection** — flag unusual query patterns (high frequency, systematic input variation, extraction-like behavior)
> 7. **Context window limits** — reject inputs exceeding a defined maximum length

## Cross-Framework Mapping

> [!info] Cross-Framework
> - **NIST 800-53:** SC-5 (Denial of Service Protection), SI-17 (Fail-Safe Procedures), SA-9 (External System Services — billing controls)
> - **NIST AI RMF:** MANAGE 2.2 (Risk treatment), GOVERN 6.1 (Policies for responsible AI deployment)
> - **FedRAMP:** Address via SC-5 in SSP — document rate limiting and token budget controls for any LLM APIs deployed within the authorization boundary

## Related Notes

- [[Wiki/owasp-llm-top10-overview]]
- [[Wiki/nist-800-53-control-families]]
