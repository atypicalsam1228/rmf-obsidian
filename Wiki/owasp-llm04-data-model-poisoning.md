---
type: concept
framework: owasp-llm
status: draft
tags:
  - owasp-llm
  - llm-security
  - data-poisoning
  - supply-chain
  - LLM04
created: 2026-05-08
updated: 2026-05-08
sources:
  - "[[Sources/OWASP-LLM/LLM04-data-and-model-poisoning]]"
related:
  - "[[Wiki/owasp-llm-top10-overview]]"
  - "[[Wiki/nist-ai-rmf-core-functions]]"
---

# LLM04: Data and Model Poisoning

> [!abstract] Summary
> Data poisoning attacks corrupt training data, fine-tuning datasets, or embeddings to introduce vulnerabilities, backdoors, or biases into the model. Poisoning is an integrity attack — the model learns and propagates attacker-controlled behaviors. The risk extends beyond biased outputs to "sleeper agent" backdoors that activate only on specific triggers.

## Definition

> [!quote] OWASP LLM04:2025 — Description
> "Data poisoning occurs when pre-training, fine-tuning, or embedding data is manipulated to introduce vulnerabilities, backdoors, or biases. This manipulation can compromise model security, performance, or ethical behavior, leading to harmful outputs or impaired capabilities."
> — [[Sources/OWASP-LLM/LLM04-data-and-model-poisoning]]

> [!quote] OWASP LLM04:2025 — Integrity Attack Classification
> "Data poisoning is considered an integrity attack since tampering with training data impacts the model's ability to make accurate predictions. The risks are particularly high with external data sources, which may contain unverified or malicious content."
> — [[Sources/OWASP-LLM/LLM04-data-and-model-poisoning]]

## Sleeper Agent Risk

> [!quote] OWASP LLM04:2025 — Backdoor / Sleeper Agent
> "Poisoning may allow for the implementation of a backdoor. Such backdoors may leave the model's behavior untouched until a certain trigger causes it to change. This may make such changes hard to test for and detect, in effect creating the opportunity for a model to become a sleeper agent."
> — [[Sources/OWASP-LLM/LLM04-data-and-model-poisoning]]

## Attack Lifecycle Stages

Poisoning can target any stage of LLM development:
- **Pre-training** — corrupting large general-purpose training datasets
- **Fine-tuning** — injecting malicious examples into domain-specific fine-tuning data
- **Embedding** — manipulating vector representations in RAG pipelines
- **Transfer learning** — distributing a pre-poisoned model via open-source repositories

> [!quote] OWASP LLM04:2025 — Repository Risk
> "Models distributed through shared repositories or open-source platforms can carry risks beyond data poisoning, such as malware embedded through techniques like malicious pickling, which can execute harmful code when the model is loaded."
> — [[Sources/OWASP-LLM/LLM04-data-and-model-poisoning]]

## Prevention Strategies

> [!quote] OWASP LLM04:2025 — Mitigations
> "1. Track data origins and transformations using tools like OWASP CycloneDX or ML-BOM...Verify data legitimacy during all model development stages.
> 2. Vet data vendors rigorously, and validate model outputs against trusted sources to detect signs of poisoning.
> 3. Implement strict sandboxing to limit model exposure to unverified data sources.
> 6. Use data version control (DVC) to track changes in datasets and detect manipulation.
> 8. Test model robustness with red team campaigns and adversarial techniques...
> 9. Monitor training loss and analyze model behavior for signs of poisoning."
> — [[Sources/OWASP-LLM/LLM04-data-and-model-poisoning]]

> [!example] Implementation Guidance
> 1. **Model provenance:** Use ML-BOM or CycloneDX to document model origins and training datasets
> 2. **Dataset vetting:** Audit training data sources — prefer curated, provenance-tracked datasets
> 3. **Dependency scanning:** Scan model files for malicious pickling before loading (treat like a supply chain attack)
> 4. **Behavioral testing:** Red team with adversarial inputs targeting known poisoning patterns
> 5. **RAG data integrity:** Hash and version control all documents in retrieval stores; monitor for unauthorized modifications

## Relationship to Supply Chain (LLM03)

LLM04 and LLM03 (Supply Chain) overlap when poisoning occurs through third-party model/dataset distribution. Both require supply chain controls.

## Cross-Framework Mapping

> [!info] Cross-Framework
> - **NIST AI RMF:** MEASURE 2.5 (Data quality and integrity), MAP 2.3 (AI risk enumeration)
> - **NIST 800-53:** SA-12 (Supply Chain Protection), SI-7 (Software, Firmware, and Information Integrity)
> - **NIST 800-171:** 03.14.03 (Security alerts and advisories), 03.16 (Supply chain risk management)

## Related Notes

- [[Wiki/owasp-llm-top10-overview]]
- [[Wiki/nist-ai-rmf-core-functions]]
