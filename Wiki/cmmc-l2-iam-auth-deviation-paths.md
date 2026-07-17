---
type: guide
framework: nist-800-171
status: draft
tags:
  - cmmc
  - access-control/least-privilege
  - authentication/mfa
  - iam
  - deviation
  - aws
  - keycloak
  - openshift
  - nist-800-171
  - nist-800-63b
  - upstream-downstream
created: 2026-06-30
updated: 2026-06-30
sources:
  - "[[Sources/NIST-800-171/nist-800-171r3-security-requirements]]"
  - "[[Sources/NIST-800-53/nist-800-53r5-catalog]]"
related:
  - "[[Wiki/cmmc-l2-asset-category-control-reference]]"
  - "[[Wiki/cmmc-siem-requirements]]"
  - "[[Wiki/nist-800-171-cui-protection]]"
  - "[[Wiki/fedramp-access-control]]"
---

# CMMC L2 — IAM & Authentication: Deviation Paths and Alternate Implementations

> [!abstract] Summary
> This article covers alternate implementation paths for two common CMMC Level 2 friction points: **IAM least privilege** (AC.L2-3.1.5) when dynamic role creation is operationally required (OCP, Terraform), and **MFA enforcement** (IA.L2-3.5.3) in a federated Keycloak + RedHat IDM stack. All paths are grounded in official NIST publications. Covers upstream/downstream CUI flow concepts and SPRS/POA&M deviation mechanics.

---

## Upstream / Downstream — CUI Flow Model

In CMMC, upstream and downstream describe the direction CUI moves through the supply chain and the technology stack. Compliance responsibility follows the same direction.

```
DoD (Government)
      ↓  CUI flows downstream + compliance obligation flows down
Prime Contractor            ← UPSTREAM from your org
      ↓  DFARS 252.204-7021 flow-down
Your Organization
      ↓  your subcontractors/tools/cloud services must also comply
Downstream Systems          ← OCP, AWS, Keycloak consumers
```

**Upstream** = where your CUI comes from. You inherit the handling requirements and contract-specific controls the prime flows down to you via DFARS 252.204-7021.

**Downstream** = where CUI goes after you touch it. You are responsible for ensuring downstream systems — including cloud services, subcontractors, and internal tooling that processes CUI — meet CMMC Level 2 requirements.

> [!info] Identity Chain — Upstream/Downstream
> ```
> RedHat IDM          ← UPSTREAM identity source (LDAP/Kerberos)
>       ↓ federation
> Keycloak            ← Broker (enforcement point)
>       ↓ OIDC/SAML tokens
> OCP / AWS / Apps    ← DOWNSTREAM consumers
> ```
> If CUI reaches any layer, the entire chain is in scope. RedHat IDM cannot be scoped out because it is "just infrastructure" — it is the upstream identity source for all downstream access decisions.

> [!warning] Scope Boundary Risk
> Company SSO for AWS Console is upstream from all IAM role assumptions. If SSO is breached, all console access is compromised. SSO infrastructure must appear in the SSP boundary — it cannot be treated as a shared service outside the authorization boundary.

---

## Control: AC.L2-3.1.5 — Least Privilege

> [!quote] NIST SP 800-171 Rev 2, Section 3.1.5
> "Employ the principle of least privilege, including for specific security functions and privileged accounts."
> — [[Sources/NIST-800-171/nist-800-171r3-security-requirements]]

> [!quote] NIST SP 800-171 Rev 2, Section 3.1.6
> "Use non-privileged accounts or roles when accessing non-security functions."
> — [[Sources/NIST-800-171/nist-800-171r3-security-requirements]]

### The Problem

AWS PowerUser excludes IAM management. Two operational requirements demand dynamic IAM creation/modification:

1. **OCP (OpenShift Container Platform) installation** — requires `iam:CreateRole`, `iam:AttachRolePolicy`, `iam:CreateInstanceProfile`, and `iam:PassRole` to provision worker node profiles and service accounts
2. **Terraform SA** — requires IAM actions to create and manage resources as infrastructure-as-code

Deleting existing IAM users/roles breaks the platform. Full IAM Admin is overkill and fails least privilege. AWS PowerUser blocks what OCP and Terraform need.

**800-171A Assessment Examines (3.1.5):**
- List of privileged accounts and security functions
- System configuration settings and associated documentation
- Mechanisms implementing least privilege capability

The assessor validates the *outcome* (privilege is minimized), not the specific mechanism. This opens multiple compliant paths.

---

### Option A: Custom Scoped IAM Policy (Preferred — Not a Deviation)

Create a custom IAM policy granting only the specific IAM actions OCP and Terraform actually require. This is least privilege properly implemented — not a workaround.

**Minimum IAM actions for OCP installer:**

```
iam:CreateRole / iam:DeleteRole
iam:AttachRolePolicy / iam:DetachRolePolicy
iam:CreateInstanceProfile / iam:AddRoleToInstanceProfile / iam:RemoveRoleFromInstanceProfile
iam:DeleteInstanceProfile
iam:PassRole (with condition: iam:PassedToService = ec2.amazonaws.com)
iam:GetRole / iam:ListRoles / iam:ListAttachedRolePolicies
iam:CreateServiceLinkedRole
```

**NIST Grounding:**
- NIST SP 800-171 3.1.5 — scoped policy directly satisfies least privilege; the assessor sees explicit enumeration of allowed actions
- NIST SP 800-171 3.1.2 — limits system access to the types of transactions authorized users are permitted to execute

> [!example] SSP Narrative for 3.1.5
> "The OCP installer service account operates under a custom IAM policy (`ocp-installer-least-privilege`) that enumerates the minimum IAM actions required for cluster provisioning as documented in Red Hat OpenShift installation documentation. No wildcard IAM actions are permitted. The policy is version-controlled in Terraform and any modifications require change board approval."

---

### Option B: Just-in-Time (JIT) Access via IAM Identity Center

No standing IAM permissions. Permissions are granted for a defined time window, then automatically revoked. OCP installer and Terraform SA activate roles only during execution windows.

**NIST Grounding:**
- NIST SP 800-171 3.1.6 — *"use non-privileged accounts or roles when accessing non-security functions"* — JIT satisfies this by default; the role does not exist in a privileged state outside the window

> [!danger] NEEDS SOURCE: NIST SP 800-53 AC-2(2)
> "Automatically remove or disable temporary and emergency accounts after [defined time period]." — Referenced as supplemental guidance by 800-171A for 3.1.5. Source not yet ingested.
> Run `/rmf-vault ingest` to add NIST SP 800-53 Rev 5 AC-2 section.

**Tradeoff:** Terraform pipelines require an activation step before execution. Adds operational overhead but eliminates standing privilege entirely — assessors see this as stronger than Option A.

---

### Option C: Attribute-Based Access Control (ABAC) with Tag-Scoped Policies

IAM policies use resource tags as conditions. Terraform SA can operate on IAM actions only when the target resource is tagged `ManagedBy=Terraform` or `Project=OCP`. Broad action grants become narrow in practice.

**NIST Grounding:**

> [!danger] NEEDS SOURCE: NIST SP 800-162
> "ABAC can provide a more granular and flexible access control mechanism than RBAC." — Official NIST recognition of ABAC as a least privilege mechanism. Source not yet ingested.
> Run `/rmf-vault ingest` to add NIST SP 800-162.

- NIST SP 800-171 3.1.2 — limits access to types of transactions authorized users may execute; ABAC makes the transaction scope conditional on resource attributes

**Tradeoff:** Requires disciplined tagging strategy. Untagged resources fall outside scope and block legitimate operations. Tag governance must be enforced via SCP or AWS Config.

---

### Option D: Permission Boundaries as Privilege Ceiling

Attach an IAM permission boundary to the Terraform SA and OCP installer role. The boundary is a hard ceiling — even if the role has `iam:CreateRole`, it cannot create a role with permissions exceeding its own boundary. Privilege escalation is structurally impossible.

**NIST Grounding:**
- NIST SP 800-171 3.1.5 — least privilege is demonstrated not only by what the role is granted but by what it *cannot* escalate to; permission boundaries make the ceiling explicit and auditable

**Why this works for assessors:** It is a structural enforcement mechanism, not a compensating control. The assessor can read the boundary policy directly and verify the privilege ceiling.

**Tradeoff:** Boundary policies require change management. If OCP needs a new permission, the boundary must be updated through the change process.

---

### Option E: IAM Roles Anywhere — Eliminate SA Credentials Entirely

Replace the Terraform SA's long-term IAM credentials with PKI certificate-based authentication. IAM Roles Anywhere issues temporary STS credentials via X.509 certs signed by your internal CA. RedHat IDM (Dogtag CA) can serve as the issuing CA.

**NIST Grounding:**

> [!danger] NEEDS SOURCE: NIST SP 800-63B Section 5.1.8
> "Multi-Factor Cryptographic Devices — Cryptographic authenticators used at AAL2..." — Certificate-based auth meets AAL2/AAL3 assurance. Source not yet ingested.
> Run `/rmf-vault ingest` to add NIST SP 800-63B.

> [!danger] NEEDS SOURCE: NIST SP 800-57 Part 1 Section 5.3
> Key management requirements for certificate lifecycle — validity periods, revocation (OCSP/CRL), renewal cadence. Source not yet ingested.

- NIST SP 800-171 3.5.10 — *"store and transmit only cryptographically-protected passwords"* — Roles Anywhere removes static credentials from the equation entirely; nothing to store or transmit

**Why this is the strongest path:** Eliminates the entire class of long-term credential exposure. Assessor for IA.L2-3.5.10 finds no stored credentials.

---

### Compensating Controls (All IAM Paths)

| Control | Implementation | NIST Basis |
|---|---|---|
| CloudTrail logging | All IAM API calls logged, alert on out-of-band changes | 800-171 3.3.1, 3.3.2 |
| IAM Access Analyzer | Detect overly permissive policies continuously | 800-171 3.1.5 |
| SCP (Org level) | Block IAM privilege escalation outside authorized roles | 800-171 3.1.2 |
| Terraform state | Authoritative record of all IAM resources; changes via PR only | 800-171 3.4.1 (CM baseline) |

---

## Control: IA.L2-3.5.3 — Multifactor Authentication

> [!quote] NIST SP 800-171 Rev 2, Section 3.5.3
> "Use multifactor authentication for local and network access to privileged accounts and for network access to non-privileged accounts."
> — [[Sources/NIST-800-171/nist-800-171r3-security-requirements]]

> [!quote] NIST SP 800-171 Rev 2, Section 3.5.4
> "Employ replay-resistant authentication mechanisms for network access to privileged and non-privileged accounts."
> — [[Sources/NIST-800-171/nist-800-171r3-security-requirements]]

### Authenticator Assurance Levels (NIST SP 800-63B)

> [!danger] NEEDS SOURCE: NIST SP 800-63B
> AAL definitions: AAL1 (single factor), AAL2 (MFA required — TOTP, hardware key), AAL3 (hardware cryptographic — PIV/CAC, FIDO2 hardware). CMMC Level 2 requires AAL2 minimum. Source not yet ingested.
> Run `/rmf-vault ingest` to add NIST SP 800-63B.

**Current stack assessment:**
- Company SSO → AWS Console: federated, no IAM human users ✅
- Keycloak TOTP → OCP/internal apps: AAL2 compliant ✅
- RedHat IDM: upstream identity source, in scope ✅
- 2FA enforced at Keycloak broker layer ✅

**Gap risk:** If a user or service can authenticate to OCP, AWS, or any CUI system *without* going through Keycloak (bypass), the practice fails regardless of Keycloak's configuration. Assessor will probe for bypass paths.

---

### Option A: FIDO2/WebAuthn Hardware Security Keys (Strongest Path)

YubiKey or equivalent hardware key as the second factor. Phishing-resistant by design. Exceeds AAL2 — moves toward AAL3 posture without requiring full PIV infrastructure.

**NIST Grounding:**

> [!danger] NEEDS SOURCE: NIST SP 800-63B Section 5.1.7
> "Hardware Cryptographic Devices — A single-factor or multi-factor cryptographic device is a hardware device that performs cryptographic operations using protected cryptographic key(s) and provides the authenticator output via direct connection to the user endpoint." Explicitly listed as AAL2 and AAL3 capable. Source not yet ingested.

> [!danger] NEEDS SOURCE: NIST SP 800-63B Section 5.2.5
> "Verifier Impersonation Resistance — Authentication protocols SHALL be designed to provide verifier impersonation resistance." FIDO2 is phishing-resistant; TOTP is not. This is a genuine security upgrade. Source not yet ingested.

**Keycloak support:** Native WebAuthn support since Keycloak 8.0. No additional infrastructure required. Works with your existing Keycloak + RedHat IDM stack.

**SSP argument:** You are *exceeding* AAL2, not deviating. Assessor sees phishing-resistant MFA as stronger than minimum — no POA&M required.

---

### Option B: Derived PIV Credentials for Linux/Container Workloads

Physical PIV/CAC cannot be used in container, SSH, or OCP contexts natively. Derived PIV credentials are software certificates issued from the same PKI chain as the physical card, bound to a device or software token.

**NIST Grounding:**

> [!danger] NEEDS SOURCE: NIST SP 800-157
> "Guidelines for Derived Personal Identity Verification (PIV) Credentials — Section 2.3: Derived credentials may be issued to mobile devices or software tokens when the PIV card reader is not practical." This is the official NIST bridge for PIV in non-card-reader environments. Source not yet ingested.
> Run `/rmf-vault ingest` to add NIST SP 800-157.

**When this matters:** If a contract explicitly requires PIV and the assessor won't accept TOTP as equivalent, derived PIV is the NIST-blessed alternative. RedHat IDM (Dogtag CA) can issue derived credentials from the same enterprise PKI chain.

**Tradeoff:** Requires PKI coordination and certificate lifecycle management. RedHat IDM already provides the CA infrastructure — lower lift than standing up a new PKI.

---

### Option C: Zero Trust Network Access (ZTNA) as Structural Compensating Control

Replace implicit network trust with continuous verification. Every request to OCP, AWS Console, or internal services is evaluated against identity, device health, and request context — not just "did you pass MFA at login."

**NIST Grounding:**

> [!danger] NEEDS SOURCE: NIST SP 800-207
> "Zero trust is a set of guiding principles for workflow, system design and operations... All communication is secured regardless of network location." (Sections 2 and 3.1) Source not yet ingested.
> Run `/rmf-vault ingest` to add NIST SP 800-207.

- NIST SP 800-171 3.1.3 — *"Control the flow of CUI in accordance with approved authorizations"* — ZTNA enforces this continuously at the request level, not just at login

**Self-hosted options compatible with Keycloak:** Pomerium (native OIDC integration with Keycloak), Boundary (HashiCorp), Teleport.

**SSP argument:** ZTNA shifts the deviation conversation from "our MFA mechanism differs" to "we enforce continuous verification beyond what static MFA provides." Compensating control argument becomes significantly stronger when paired with AAL2 MFA.

---

### Option D: Certificate-Based Authentication for Service Accounts (mTLS)

Service accounts (Terraform SA, OCP service accounts, CI/CD pipelines) authenticate via mutual TLS client certificates — no passwords, no TOTP codes. Keycloak supports X.509 client certificate authentication natively.

**NIST Grounding:**

> [!danger] NEEDS SOURCE: NIST SP 800-63B Section 5.1.8
> "Multi-Factor Cryptographic Devices — If the authenticator output or assertion is presented to a verifier... and the associated cryptographic key is bound to a hardware device..." Certificate on a TPM-backed device meets AAL2. Source not yet ingested.

**Why this removes service accounts from the MFA question:** Service accounts are processes/devices, not humans. NIST SP 800-171 3.5.2 requires *authentication* of users, processes, and devices — mTLS is the correct mechanism for non-human identities and is NIST-supported. This separates service account authentication from the human MFA requirement and handles each appropriately.

**Pairs with:** IAM Roles Anywhere (Option E under IAM) — both use the same PKI infrastructure; RedHat IDM as CA serves both.

---

## Deviation Mechanics — CMMC vs. FedRAMP

| | FedRAMP | CMMC Level 2 |
|---|---|---|
| Mechanism | POA&M filed with AO | POA&M + SPRS score impact |
| Approver | Authorizing Official (AO) | C3PAO assessor documents finding; DoD CO/PM accepts risk |
| Visibility | ATO package (internal) | **SPRS score published** — visible to DoD contracting officers |
| Timeline | Negotiated in ATO package | Must have remediation milestones; unclosed items affect awards |

> [!warning] SPRS Score Impact
> Every unmitigated CMMC practice finding carries a negative point value in the SPRS score submitted to the Supplier Performance Risk System. DoD contracting officers see this score during source selection. A low SPRS score without a credible POA&M can cost contract awards.

### Deviation Path Decision Tree

```
Is the current implementation functional but non-standard?
        ↓
Can you demonstrate equivalent security outcome?
        ↓ Yes
Does official NIST documentation support the alternate mechanism?
        ↓ Yes
→ Document as alternate implementation in SSP — not a deviation
        ↓ Assessor still flags it
File as Operational Requirement with:
  - Technical/business justification
  - NIST citation supporting the alternate mechanism
  - Compensating controls enumerated
  - POA&M milestone with target date
        ↓
AO/C3PAO accepts → SPRS score impact assessed per residual risk
```

---

## Consolidated Summary

| Practice | Standard Path | Alternate Path A | Alternate Path B | Primary NIST Basis |
|---|---|---|---|---|
| AC.L2-3.1.5 (least privilege) | Custom scoped IAM policy | JIT via IAM Identity Center | ABAC + tag conditions | 800-171 3.1.5 |
| AC.L2-3.1.5 (escalation prevention) | Permission boundaries | IAM Roles Anywhere (no standing creds) | SCP at org level | 800-171 3.1.5, 800-63B 5.1.8 |
| IA.L2-3.5.3 (human MFA) | TOTP via Keycloak (AAL2) | FIDO2/WebAuthn hardware key | Derived PIV (800-157) | 800-63B 5.1.7 |
| IA.L2-3.5.3 (service accounts) | Separate from human MFA | mTLS client certificates | IAM Roles Anywhere + PKI | 800-63B 5.1.8, 800-57 |
| IA.L2-3.5.4 (replay resistance) | TOTP (compliant) | FIDO2 (stronger) | Kerberos short-TTL tickets | 800-63B Section 5 |
| Overall posture | Per-control compliance | ZTNA continuous verification overlay | PAM/PIM for privileged sessions | 800-207, 800-171 3.1.5 |

> [!tip] Sources to Ingest
> The following NIST publications are referenced in this article but not yet in Sources/. Ingest them to enable full wikilink citations and vault query coverage:
> - NIST SP 800-63B (Digital Identity Guidelines — Authentication and Lifecycle Management)
> - NIST SP 800-63C (Federation and Assertions)
> - NIST SP 800-207 (Zero Trust Architecture)
> - NIST SP 800-162 (Guide to ABAC)
> - NIST SP 800-157 (Derived PIV Credentials)
> - NIST SP 800-57 Part 1 (Key Management Recommendations)
> - 32 CFR Part 170 (CMMC Program Rule)
