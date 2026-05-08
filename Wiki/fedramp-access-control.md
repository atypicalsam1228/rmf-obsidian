---
type: concept
framework: fedramp
status: draft
tags:
  - fedramp/moderate
  - fedramp/high
  - access-control
  - iam
created: 2026-05-08
updated: 2026-05-08
sources:
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
  - "[[Sources/FedRAMP/fedramp-high-baseline]]"
  - "[[Sources/NIST-800-53/nist-800-53r5-catalog]]"
related:
  - "[[Wiki/fedramp-baseline-overview]]"
  - "[[Wiki/fedramp-aws-config-conformance-packs]]"
  - "[[Wiki/nist-800-53-control-families]]"
---

# FedRAMP Access Control (AC Family)

> [!abstract] Summary
> The Access Control (AC) family is one of the largest and most scrutinized in FedRAMP assessments. FedRAMP Moderate requires all AC controls with specific parameter values that are more stringent than NIST defaults. This article covers key AC controls, FedRAMP-specific parameters, and AWS implementation patterns.

## Key Controls

### AC-2 — Account Management

> [!quote] FedRAMP Moderate Baseline — AC-2
> "a. Define and document the types of accounts allowed and specifically prohibited for use within the system;
> b. Assign account managers;
> c. Require prerequisites and criteria for group and role membership;
> d. Specify authorized users of the system, group and role membership, and access authorizations for each account;
> e. Require approvals for requests to create accounts;
> f. Create, enable, modify, disable, and remove accounts in accordance with defined policy;
> g. Monitor the use of accounts;
> h. Notify account managers within defined time periods when accounts are no longer required, when users are terminated or transferred, and when system usage changes..."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AC-2 — Account Management|AC-2]]

> [!example] AWS Implementation — AC-2
> - Use **AWS IAM Identity Center** for centralized account lifecycle management
> - **IAM Access Analyzer** identifies unused access — supports g (monitor) and h (notify)
> - **AWS Config rule:** `iam-user-unused-credentials-check` (90-day threshold)
> - **AWS Config rule:** `iam-user-group-membership-check` — all users must belong to a group
> - Enable **CloudTrail** to log all account creation/modification/deletion events

### AC-3 — Access Enforcement

Enforces approved authorizations for logical access to system resources in accordance with applicable access control policies.

> [!example] AWS Implementation — AC-3
> - **IAM policies** with explicit Deny for out-of-scope actions
> - **Permission boundaries** to constrain maximum effective permissions
> - **Service Control Policies (SCPs)** in AWS Organizations for org-wide enforcement
> - **Resource-based policies** on S3, KMS, and other resources

### AC-6 — Least Privilege

> [!quote] NIST 800-53 Rev5 — AC-6
> "Employ the principle of least privilege, allowing only authorized accesses for users (or processes acting on behalf of users) that are necessary to accomplish assigned organizational tasks."
> — [[Sources/NIST-800-53/nist-800-53r5-catalog#AC-6|AC-6]]

> [!example] AWS Implementation — AC-6
> - **AWS Config rules:** `iam-policy-no-statements-with-admin-access`, `iam-policy-no-statements-with-full-access`
> - **IAM Access Analyzer** findings for overly permissive policies
> - Avoid `*` actions in IAM policies; use resource ARNs
> - **EC2 instance profiles** instead of long-term access keys: `ec2-instance-profile-attached`

### AC-17 — Remote Access

FedRAMP Moderate requires explicit remote access policies with MFA and encryption.

> [!example] AWS Implementation — AC-17
> - All remote access via **AWS Systems Manager Session Manager** (no open SSH/RDP)
> - **AWS Config rule:** `restricted-ssh` — blocks port 22 in security groups
> - **Config rule:** `restricted-common-ports` — blocks 20, 21, 3389, 3306, 4333

## FedRAMP-Specific IAM Parameters

| Parameter | FedRAMP Value | Control |
|---|---|---|
| Max password age | 90 days | AC-2, IA-5 |
| Minimum password length | 14 characters | IA-5 |
| Password reuse prevention | 24 generations | IA-5 |
| Max unused credential age | 90 days | AC-2 |
| Max access key age | 90 days | AC-2, IA-5 |

> [!quote] FedRAMP Moderate Baseline — AC-1 Review Frequency
> "Review and update the current access control policy [at least every 3 years] and procedures [at least annually] and following significant changes."
> — [[Sources/FedRAMP/fedramp-moderate-baseline#AC-1 — Policy and Procedures|AC-1]]

## MFA Requirements

FedRAMP requires MFA for all privileged accounts and for all console access.

> [!info] AWS Config Rules for MFA
> - `root-account-mfa-enabled` — root account MFA (all levels)
> - `root-account-hardware-mfa-enabled` — hardware MFA for root (all levels)
> - `iam-user-mfa-enabled` — MFA for all IAM users (all levels)
> - `mfa-enabled-for-iam-console-access` — MFA for console access (all levels)

## Cross-Framework Mapping

> [!info] Cross-Framework — AC Family
> - NIST 800-171: 3.1.x (Access Control) — maps to AC-1 through AC-22
> - CMMC Level 2: AC domain (17 practices) — aligns with FedRAMP Moderate AC
> - FedRAMP High adds: AC-2(11) usage conditions, AC-2(13) disabling accounts, AC-6(9) log use of privileged functions

## Related Notes

- [[Wiki/fedramp-baseline-overview]]
- [[Wiki/fedramp-aws-config-conformance-packs]]
- [[Wiki/nist-800-53-control-families]]
