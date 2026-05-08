---
type: concept
framework: nist-ai-rmf
status: draft
tags:
  - nist-ai-rmf
  - ai-governance
  - ai-risk-management
  - govern
  - map
  - measure
  - manage
created: 2026-05-08
updated: 2026-05-08
sources:
  - "[[Sources/NIST-AI-RMF/nist-ai-rmf-1-0]]"
related:
  - "[[Wiki/owasp-llm-top10-overview]]"
  - "[[Wiki/owasp-llm01-prompt-injection]]"
  - "[[Wiki/owasp-llm06-excessive-agency]]"
  - "[[Wiki/fedramp-nist-800-53-relationship]]"
---

# NIST AI RMF 1.0 — Core Functions

> [!abstract] Summary
> The NIST AI Risk Management Framework (AI RMF 1.0, NIST AI 100-1, January 2023) organizes AI risk management into four core functions: Govern, Map, Measure, and Manage. The framework is voluntary, flexible, and designed to be used alongside — not replace — existing frameworks like NIST 800-53. It is the primary federal reference for AI risk management.

## Framework Overview

> [!quote] NIST AI 100-1 — AI RMF Purpose
> "The AI RMF is intended to be a living document. NIST will review the content and usefulness of the Framework regularly to determine if an update is appropriate; a review with formal input from the AI community is expected to take place no later than 2028."
> — [[Sources/NIST-AI-RMF/nist-ai-rmf-1-0]]

The framework is structured in two parts:
- **Part 1:** Foundational information — AI risks, trustworthiness characteristics, challenges
- **Part 2:** The Core and Profiles — four functions with subcategories and actions

## Trustworthiness Characteristics

NIST identifies seven properties of trustworthy AI systems:

> [!quote] NIST AI 100-1 — Trustworthiness Properties
> 1. Valid and Reliable
> 2. Safe
> 3. Secure and Resilient
> 4. Accountable and Transparent
> 5. Explainable and Interpretable
> 6. Privacy-Enhanced
> 7. Fair — with Harmful Bias Managed
> — [[Sources/NIST-AI-RMF/nist-ai-rmf-1-0]]

## The Four Core Functions

### GOVERN (GV)

Establishes the organizational culture, policies, processes, and accountability structures for AI risk management. Must be operationalized before the other functions.

**Key Subcategories:**
- GV-1: Policies and accountability for AI risk management
- GV-2: AI risk management into organizational processes
- GV-3: Workforce — training and responsibility
- GV-4: Organizational teams (red teams, diversity of input)
- GV-5: Policies for transparency and disclosure
- GV-6: Policies for AI in acquisition and third-party use

### MAP (MP)

Establishes context to frame AI risks. Organizations must understand the AI system's purpose, context, and who is affected before they can assess risk.

**Key Subcategories:**
- MP-1: Context is established
- MP-2: Scientific knowledge about AI risk is reflected
- MP-3: AI capabilities, limitations, and impacts are understood
- MP-4: Risks are enumerated and prioritized
- MP-5: Organizational risk tolerance is established

### MEASURE (MS)

Quantifies and analyzes AI risks using appropriate tools and methodologies. Tracks performance against trustworthiness characteristics.

**Key Subcategories:**
- MS-1: Methods and metrics for AI risk measurement are established
- MS-2: AI systems are evaluated for trustworthiness characteristics
- MS-2.5: Data quality metrics
- MS-2.6: Explainability and interpretability metrics
- MS-3: AI risks are tracked over time
- MS-4: Feedback from deployment is incorporated

### MANAGE (MG)

Activates plans to address identified AI risks. Includes treatment, response, recovery, and continuous improvement.

**Key Subcategories:**
- MG-1: Risks are prioritized and treated based on risk tolerance
- MG-2: Treatments for AI risks are applied
- MG-2.2: Residual risks are managed
- MG-2.4: Human oversight mechanisms are in place
- MG-3: Responses are defined for AI incidents
- MG-4: Lessons learned feed back into risk management

## How AI Risks Differ from Traditional Software Risks

> [!quote] NIST AI 100-1 — AI vs. Traditional Software Risk
> "Appendix B: How AI Risks Differ from Traditional Software Risks"
> — [[Sources/NIST-AI-RMF/nist-ai-rmf-1-0]]

Key differences:
- AI risks can emerge from **data quality**, not just code bugs
- **Model behavior** changes with inputs in non-deterministic ways
- **Societal harms** (bias, fairness) are within scope, not just security/safety
- **Third-party model risk** — using a pre-trained model inherits its risks

## AI RMF Profiles

The framework includes customizable Profiles for specific sectors (financial, healthcare, etc.) and use cases. Organizations create a **Current Profile** (current state) and a **Target Profile** (desired state) and work to close the gap.

## Relationship to Other Frameworks

> [!info] Cross-Framework
> - **NIST 800-53:** AI RMF complements 800-53 — use AI RMF for AI-specific risks, 800-53 for system-level security/privacy controls
> - **OWASP LLM Top 10:** OWASP provides specific attack vectors; AI RMF provides governance structure for managing them
> - **FedRAMP:** No AI-specific FedRAMP pathway yet — address AI risks via 800-53 controls (SI-10, AC-6, AU-12) with AI-specific implementation narrative in SSP
> - **EO 14110:** NIST AI RMF 1.0 is the primary implementation vehicle for federal AI safety requirements
> See: [[Wiki/owasp-llm-top10-overview]], [[Wiki/fedramp-nist-800-53-relationship]]

## Federal Context

> [!info] Federal AI Governance
> - NIST AI 100-1 is referenced in **OMB M-24-10** (Advancing Governance, Innovation, and Risk Management for Agency Use of AI)
> - Agencies must designate Chief AI Officers and inventory AI use cases
> - High-impact AI systems require rights-impact assessments
> - AI RMF Playbook at airc.nist.gov provides subcategory-level implementation guidance

## Related Notes

- [[Wiki/owasp-llm-top10-overview]]
- [[Wiki/owasp-llm01-prompt-injection]]
- [[Wiki/owasp-llm06-excessive-agency]]
- [[Wiki/fedramp-nist-800-53-relationship]]
- [[Wiki/nist-800-53-control-families]]
