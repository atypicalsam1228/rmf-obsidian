---
type: pattern
framework: fedramp
status: draft
tags:
  - fedramp/moderate
  - fedramp/high
  - fedramp/low
  - aws-config
  - conformance-pack
  - implementation/aws
created: 2026-05-08
updated: 2026-05-08
sources:
  - "[[Sources/FedRAMP/operational-best-practices-for-fedramp-moderate]]"
  - "[[Sources/FedRAMP/operational-best-practices-for-fedramp-highpart1]]"
  - "[[Sources/FedRAMP/operational-best-practices-for-fedramp-low]]"
  - "[[Sources/FedRAMP/aws-config-fedramp-moderate-mappings]]"
  - "[[Sources/FedRAMP/aws-config-fedramp-high-mappings]]"
  - "[[Sources/FedRAMP/aws-config-fedramp-low-mappings]]"
related:
  - "[[Wiki/fedramp-baseline-overview]]"
  - "[[Wiki/fedramp-access-control]]"
  - "[[Wiki/fedramp-vulnerability-management]]"
---

# FedRAMP AWS Config Conformance Packs

> [!abstract] Summary
> AWS provides pre-built Config conformance packs that map directly to FedRAMP Low, Moderate, and High baselines. These packs contain managed Config rules with FedRAMP-specific parameter values and are the primary automated mechanism for continuous compliance monitoring of AWS infrastructure against FedRAMP controls.

## Conformance Pack Overview

| Baseline | Pack Name | Rule Count |
|---|---|---|
| FedRAMP Low | `Operational-Best-Practices-for-FedRAMP-Low` | ~113 |
| FedRAMP Moderate | `Operational-Best-Practices-for-FedRAMP-Moderate` | 129 |
| FedRAMP High (Part 1) | `Operational-Best-Practices-for-FedRAMP-High-Part1` | ~109 |
| FedRAMP High (Part 2) | `Operational-Best-Practices-for-FedRAMP-High-Part2` | ~109 |

> [!quote] Sources/FedRAMP/operational-best-practices-for-fedramp-moderate
> Total rules: **129**
> — [[Sources/FedRAMP/operational-best-practices-for-fedramp-moderate]]

## FedRAMP Moderate Parameters

These are the exact parameter values baked into the FedRAMP Moderate conformance pack:

> [!quote] FedRAMP Moderate Conformance Pack — Parameters
> | Parameter | Value |
> |---|---|
> | `AccessKeysRotatedParamMaxAccessKeyAge` | `90` days |
> | `IamPasswordPolicyParamMaxPasswordAge` | `90` days |
> | `IamPasswordPolicyParamMinimumPasswordLength` | `14` chars |
> | `IamPasswordPolicyParamPasswordReusePrevention` | `24` generations |
> | `IamUserUnusedCredentialsCheckParamMaxCredentialUsageAge` | `90` days |
> | `GuarddutyNonArchivedFindingsParamDaysHighSev` | `1` day |
> | `GuarddutyNonArchivedFindingsParamDaysMediumSev` | `7` days |
> | `GuarddutyNonArchivedFindingsParamDaysLowSev` | `30` days |
> | `BackupPlanMinFrequencyAndMinRetentionCheckParamRequiredRetentionDays` | `35` days |
> | `VpcSgOpenOnlyToAuthorizedPortsParamAuthorizedTcpPorts` | `443` |
> | `RestrictedIncomingTrafficParamBlockedPort1-5` | `20, 21, 3389, 3306, 4333` |
> — [[Sources/FedRAMP/operational-best-practices-for-fedramp-moderate]]

## Rule Categories

### IAM & Access (19 rules — all levels)
Key rules: `access-keys-rotated`, `iam-password-policy`, `iam-root-access-key-check`, `root-account-mfa-enabled`, `iam-user-mfa-enabled`, `mfa-enabled-for-iam-console-access`

### S3 (10-14 rules depending on level)
Key rules: `s3-bucket-public-read-prohibited`, `s3-bucket-public-write-prohibited`, `s3-default-encryption-kms`, `s3-bucket-logging-enabled`, `s3-bucket-ssl-requests-only`

High adds: `s3-bucket-cross-region-replication-enabled`, `s3-bucket-server-side-encryption-enabled`, `s3-resources-protected-by-backup-plan`

### Security Services
- `guardduty-enabled-centralized` — all levels
- `securityhub-enabled` — all levels
- `inspector-ec2-scan-enabled` — **High only**
- `inspector-ecr-scan-enabled` — **High only**
- `inspector-lambda-standard-scan-enabled` — **High only**

### Network
- `vpc-flow-logs-enabled` — Moderate and High
- `vpc-default-security-group-closed` — Moderate and High
- `eks-endpoint-no-public-access` — **High only**

## Deploying the Conformance Pack

> [!example] AWS CLI Deployment
> ```bash
> # Deploy FedRAMP Moderate conformance pack
> aws configservice put-conformance-pack \
>   --conformance-pack-name FedRAMP-Moderate \
>   --template-s3-uri s3://aws-config-rules-<region>/aws-config-conformance-packs/Operational-Best-Practices-for-FedRAMP-Moderate.yaml \
>   --delivery-s3-bucket <your-config-bucket>
> ```

> [!tip] Best Practices
> - Deploy in **all regions** where you have resources — Config rules are regional
> - Use **AWS Organizations aggregator** to collect findings centrally
> - Pipe Config findings to **Security Hub** for consolidated ConMon dashboard
> - Export noncompliant findings to S3 for monthly ConMon reporting to AO

## Relationship to FedRAMP ConMon

AWS Config conformance packs serve as the automated backbone of FedRAMP Continuous Monitoring (ConMon). Noncompliant Config findings feed directly into the POA&M tracking process.

> [!info] ConMon Integration
> Config noncompliance → Security Hub finding → POA&M item → Monthly ConMon report to AO
> See: [[Wiki/fedramp-vulnerability-management]]

## Cross-Framework Mapping

> [!info] Cross-Framework
> - Same conformance packs work for **NIST 800-53** and **NIST 800-171** baselines (separate packs exist)
> - **Azure Policy** has equivalent built-in initiatives for FedRAMP Moderate/High
> See: [[Sources/NIST-800-53/aws-config-nist-800-53r5-mappings]], [[Sources/FedRAMP/aws-config-fedramp-moderate-mappings]]

## Related Notes

- [[Wiki/fedramp-baseline-overview]]
- [[Wiki/fedramp-access-control]]
- [[Wiki/fedramp-vulnerability-management]]
