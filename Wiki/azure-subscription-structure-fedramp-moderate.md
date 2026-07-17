---
type: guide
framework: fedramp
status: draft
tags:
  - fedramp/moderate
  - azure
  - cloud-architecture
  - boundary
  - subscription-design
created: 2026-06-25
updated: 2026-06-25
sources:
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
related:
  - "[[Wiki/fedramp-baseline-overview]]"
  - "[[Wiki/fedramp-access-control]]"
  - "[[Wiki/dod-srg-cloud-impact-levels]]"
  - "[[Wiki/fedramp-moderate-platform-bau-requirements]]"
---

# Azure Subscription Structure for FedRAMP Moderate

> [!abstract] Summary
> An Azure subscription is the billing and access boundary for cloud resources — the direct equivalent of an AWS Account. FedRAMP Moderate does not prescribe a specific number of subscriptions, but the boundary must clearly delineate which subscriptions process, store, or transmit CUI. The standard pattern is four subscriptions minimum (Identity, Management, Connectivity, Production), organized under a dedicated FedRAMP Management Group.

---

## What Is an Azure Subscription

An Azure subscription is a **logical billing and access boundary** inside Azure. It is the container that holds all resources (VMs, storage, databases, etc.) and is tied to a specific billing account.

| Function | Description |
|---|---|
| **Billing unit** | All resource costs roll up to one bill per subscription |
| **RBAC boundary** | Access permissions assigned at subscription scope apply to everything inside it |
| **Resource quota boundary** | Azure quota limits (CPU cores, public IPs, etc.) are per subscription |
| **Policy scope** | Azure Policies can target a subscription directly or be inherited from a Management Group above it |

### Azure Hierarchy

```
Entra ID Tenant
└── Management Group
    └── Subscription          ← billing + access boundary
        └── Resource Group
            └── Resources (VMs, storage, etc.)
```

### AWS Equivalent

| Azure | AWS |
|---|---|
| Entra ID Tenant | AWS Organization |
| Management Group | Organizational Unit (OU) |
| **Subscription** | **AWS Account** |
| Resource Group | No direct equivalent (tags + CloudFormation stacks approximate it) |

---

## Management Plane vs Data Plane

> [!info] Key Distinction
> The **management plane** is the control layer used to configure and manage Azure resources (Azure Resource Manager / ARM API). The **data plane** is where application data flows (service-specific endpoints). These are separate security boundaries with separate RBAC roles.

| | Management Plane | Data Plane |
|---|---|---|
| **Example (Storage)** | Create/delete storage account, set access policies | Read/write blobs |
| **Example (Key Vault)** | Create vault, set RBAC, manage keys | Get/set secrets |
| **Auth** | Entra ID + ARM RBAC roles | Entra ID + data roles or access keys |

This separation directly satisfies [[Sources/NIST-800-53/AC-access-control#AC-5|AC-5]] (Separation of Duties) and [[Sources/NIST-800-53/AC-access-control#AC-6|AC-6]] (Least Privilege) — a DevOps engineer can have Contributor (management plane) without access to read Key Vault secrets (data plane).

---

## FedRAMP Moderate Subscription Structure

### Minimum Pattern (4 Subscriptions)

```
FedRAMP Management Group (authorized boundary)
├── Identity Subscription
├── Management Subscription
├── Connectivity Subscription
└── Production Subscription
```

### Subscription Roles

| Subscription | Purpose | Primary Controls Addressed |
|---|---|---|
| **Identity** | Entra ID Connect, domain controllers, PIM | AC-2, IA-2, IA-5 |
| **Management** | Log Analytics, Defender for Cloud, monitoring, automation | AU-2, AU-3, SI-4 |
| **Connectivity** | Hub VNet, firewall, VPN/ExpressRoute, DNS | SC-7, SC-8, AC-17 |
| **Production** | Actual workloads handling CUI | All families |

### Common Additions

| Subscription | When Required |
|---|---|
| **Staging** | Pre-production that touches real CUI — must be inside the FedRAMP boundary |
| **Sandbox/Dev** | No CUI — can sit outside the boundary |
| **Shared Services** | Common tools reused across workloads (internal APIs, shared DBs) |

---

## FedRAMP Boundary Rule

> [!danger] NEEDS SOURCE: FedRAMP boundary scoping guidance
> Authoritative boundary scoping rules from FedRAMP PMO or FedRAMP Rev 5 System Security Plan template not yet ingested. Run `/rmf-vault ingest` when available.

Any subscription that meets **any** of the following conditions is in scope:

1. Processes, stores, or transmits CUI
2. Provides security services to in-scope workloads (logging, identity, network hub)
3. Has network connectivity to in-scope workloads

Development subscriptions with no real CUI and no network path to production **may** sit outside the authorized boundary.

---

## Staging Subscription

A **staging subscription** is an Azure subscription dedicated to pre-production environments where code and infrastructure are tested before promotion to production.

**Why a separate subscription (not just a resource group):**

- **Blast radius isolation** — misconfiguration in staging cannot affect production resources
- **RBAC boundary** — developers can have broader access in staging without touching production
- **Policy flexibility** — looser policies for testing without creating production exceptions
- **Cost separation** — staging costs are cleanly separated from production billing

**FedRAMP scoping decision:**

```
FedRAMP Management Group
├── Production Subscription      ← always in scope
├── Staging Subscription         ← in scope if it touches real CUI
└── Development Subscription     ← may be outside scope if no real CUI and no network path to prod
```

> [!tip] Best Practice
> Use synthetic/anonymized test data in staging to keep it outside the FedRAMP boundary. If staging must touch real CUI for testing purposes, apply the full FedRAMP control set and include it in the SSP boundary diagram.

---

## Shared Management Plane Between Prod and Staging

Sharing management infrastructure between production and staging is common but requires strict constraints.

### What Is Safe to Share

| Component | Shareable? | Condition |
|---|---|---|
| Management Group (parent) | ✅ Yes | Both subscriptions are children — intended design |
| Entra ID Tenant | ✅ Yes | All subscriptions in the org share one tenant |
| Defender for Cloud | ✅ Yes | MG-level enrollment covers both |
| Log Analytics Workspace | ⚠️ Conditional | Only if staging is inside the FedRAMP boundary; use table-level RBAC to separate log streams |
| CI/CD Pipeline Identity | ⚠️ Conditional | Separate service principals per environment — no shared identity with write access to both |
| Key Vault | ❌ Avoid | Production secrets must not be accessible from staging |

### The FedRAMP Risk

A shared component that is compromised exposes both environments as a lateral movement path. Assessors evaluate this under:

- [[Sources/NIST-800-53/AC-access-control#AC-6|AC-6]] — Least Privilege (shared identity violates minimal access)
- [[Sources/NIST-800-53/AC-access-control#AC-5|AC-5]] — Separation of Duties (one pipeline modifying both envs)
- [[Sources/NIST-800-53/SC-system-communications-protection#SC-7|SC-7]] — Boundary Protection (lateral movement path)

> [!warning] Key Rule
> **Shared visibility is acceptable. Shared write access is not.** You can observe both environments from one place (Defender for Cloud, Log Analytics). A single identity with write access to both production and staging is a finding.

### Clean Pattern

```
Shared Management Subscription (inside FedRAMP boundary)
├── Log Analytics Workspace      ← table-level RBAC separates prod/staging logs
├── Defender for Cloud           ← MG-level, covers both
└── Automation Account           ← separate service principals per environment

Production Subscription          ← prod service principal only
Staging Subscription             ← staging service principal only
```

---

## Domain Separation (SC-3)

**SC-3 (Security Function Isolation) is NOT required at FedRAMP Moderate.** It is a HIGH baseline control.

The subscription-level isolation described in this article is driven by AC-5, AC-6, and SC-7 — not SC-3. Keycloak realm separation (admin realm vs. user realm) is similarly an AC-6/AC-5 pattern, not a domain separation requirement.

> [!info] Cross-Framework Mapping
> - SC-3 Security Function Isolation → FedRAMP HIGH only
> - SC-4 Information in Shared Resources → FedRAMP Moderate ✅
> - SC-39 Process Isolation → FedRAMP Moderate ✅
> - AC-5 Separation of Duties → FedRAMP Moderate ✅
> - AC-6 Least Privilege → FedRAMP Moderate ✅

---

## Management Group Policy Enforcement

The Management Group above the subscriptions is the **governance enforcement plane**. It handles policy inheritance, RBAC scope, and audit routing — it does not satisfy controls that require data protection or network controls at the resource level.

| Control Layer | What It Covers | What It Does NOT Cover |
|---|---|---|
| Management Group | Policy inheritance, RBAC scope, audit routing | Data-at-rest encryption, network boundary, incident response |
| Subscription | Resource quotas, billing isolation, RBAC boundary | Application-layer controls |
| Resource Group | Resource organization, scoped RBAC | Security enforcement |
| Resource | Actual control implementation | — |

See [[Wiki/fedramp-moderate-platform-bau-requirements]] for operational requirements once the subscription structure is in place.
