---
type: concept
framework: owasp-llm
status: draft
tags:
  - owasp-llm
  - llm-security
  - excessive-agency
  - LLM06
  - agentic-ai
created: 2026-05-08
updated: 2026-05-08
sources:
  - "[[Sources/OWASP-LLM/LLM06-excessive-agency]]"
related:
  - "[[Wiki/owasp-llm-top10-overview]]"
  - "[[Wiki/owasp-llm01-prompt-injection]]"
  - "[[Wiki/nist-ai-rmf-core-functions]]"
---

# LLM06: Excessive Agency

> [!abstract] Summary
> Excessive Agency is the vulnerability where an LLM-based system is granted more functionality, permissions, or autonomy than it needs, enabling damaging actions when the model misbehaves — whether due to hallucination, prompt injection, or model error. It is the most critical risk in agentic AI deployments.

## Definition

> [!quote] OWASP LLM06:2025 — Description
> "An LLM-based system is often granted a degree of agency by its developer - the ability to call functions or interface with other systems via extensions (sometimes referred to as tools, skills or plugins by different vendors) to undertake actions in response to a prompt."
> — [[Sources/OWASP-LLM/LLM06-excessive-agency]]

> [!quote] OWASP LLM06:2025 — Core Definition
> "Excessive Agency is the vulnerability that enables damaging actions to be performed in response to unexpected, ambiguous or manipulated outputs from an LLM, regardless of what is causing the LLM to malfunction. Common triggers include:
> * hallucination/confabulation caused by poorly-engineered benign prompts, or just a poorly-performing model;
> * direct/indirect prompt injection from a malicious user, an earlier invocation of a malicious/compromised extension, or (in multi-agent/collaborative systems) a malicious/compromised peer agent."
> — [[Sources/OWASP-LLM/LLM06-excessive-agency]]

## Three Root Causes

> [!quote] OWASP LLM06:2025 — Root Causes
> "The root cause of Excessive Agency is typically one or more of:
> * excessive functionality;
> * excessive permissions;
> * excessive autonomy."
> — [[Sources/OWASP-LLM/LLM06-excessive-agency]]

### Excessive Functionality

> [!quote] OWASP LLM06:2025 — Excessive Functionality Examples
> "An LLM agent has access to extensions which include functions that are not needed for the intended operation of the system. For example, a developer needs to grant an LLM agent the ability to read documents from a repository, but the 3rd-party extension they choose to use also includes the ability to modify and delete documents."
> — [[Sources/OWASP-LLM/LLM06-excessive-agency]]

### Excessive Permissions

> [!quote] OWASP LLM06:2025 — Excessive Permissions
> "An LLM extension has permissions on downstream systems that are not needed for the intended operation of the application. E.g., an extension intended to read data connects to a database server using an identity that not only has SELECT permissions, but also UPDATE, INSERT and DELETE permissions."
> — [[Sources/OWASP-LLM/LLM06-excessive-agency]]

### Excessive Autonomy

> [!quote] OWASP LLM06:2025 — Excessive Autonomy
> "An LLM-based application or extension fails to independently verify and approve high-impact actions. E.g., an extension that allows a user's documents to be deleted performs deletions without any confirmation from the user."
> — [[Sources/OWASP-LLM/LLM06-excessive-agency]]

## Impact

Excessive Agency can affect all three dimensions of the CIA triad:
- **Confidentiality:** agent exfiltrates data it was permitted to read
- **Integrity:** agent modifies or deletes records it was permitted to read
- **Availability:** agent performs resource-intensive operations without limit

## Prevention and Mitigation

> [!example] Mitigations for Excessive Agency
> 1. **Minimal tool surface** — provide LLMs only the tools strictly needed. If the task is read-only, don't grant write tools.
> 2. **Scoped API tokens** — issue separate, least-privilege credentials per tool/function. Don't share a high-privilege service account.
> 3. **Read-before-write separation** — separate reading data from acting on data into distinct tool calls with human checkpoints between them.
> 4. **Human-in-the-loop for irreversible actions** — require explicit approval before: sending emails, deleting records, deploying code, making payments.
> 5. **Action logging and rate limiting** — log every tool invocation; rate-limit destructive operations.
> 6. **Sandboxed execution** — run agent tool calls in isolated environments (containerized, network-isolated).

## Agentic System Risk Compound

> [!warning] LLM01 + LLM06 Compound Risk
> Prompt Injection (LLM01) combined with Excessive Agency (LLM06) is the most dangerous scenario.
> An indirect injection in a document retrieved by a RAG agent can hijack the agent's tool calls —
> resulting in data exfiltration, account takeover, or infrastructure destruction.
> Both mitigations must be applied together.
> See: [[Wiki/owasp-llm01-prompt-injection]]

## Multi-Agent Systems

> [!quote] OWASP LLM06:2025 — Multi-Agent
> "direct/indirect prompt injection from...a malicious/compromised peer agent"
> — [[Sources/OWASP-LLM/LLM06-excessive-agency]]

In multi-agent architectures, a compromised sub-agent can inject instructions into an orchestrator. Each agent-to-agent communication channel is a potential injection vector.

> [!tip] Multi-Agent Trust Model
> - Treat peer agent outputs as untrusted input — validate before acting
> - Define explicit trust boundaries between orchestrators and sub-agents
> - Sub-agents should have narrower permissions than orchestrators

## Cross-Framework Mapping

> [!info] Cross-Framework
> - **NIST 800-53:** AC-6 (Least Privilege), AC-3 (Access Enforcement), AC-17 (Remote Access), AU-12 (Event Logging)
> - **NIST AI RMF:** GOVERN 6.2 (Accountability), MANAGE 2.4 (Human oversight), MANAGE 4.1 (Risk treatment)
> - **FedRAMP:** Address via AC-6 in SSP — "LLM tool invocations are subject to least-privilege constraints; write operations require human approval"

## Related Notes

- [[Wiki/owasp-llm-top10-overview]]
- [[Wiki/owasp-llm01-prompt-injection]]
- [[Wiki/nist-ai-rmf-core-functions]]
