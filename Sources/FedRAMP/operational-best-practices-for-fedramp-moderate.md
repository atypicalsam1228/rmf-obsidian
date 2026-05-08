---
title: "AWS Config Conformance Pack — FedRAMP Moderate"
type: reference
framework: fedramp
source_format: converted
created: 2026-04-05
tags:
  - fedramp
  - aws-config
  - conformance-pack
---

# AWS Config Conformance Pack: FedRAMP Moderate

> Source: `Operational-Best-Practices-for-FedRAMP-Moderate.yaml`

## Parameters

| Parameter | Default | Type |
|---|---|---|
| `AccessKeysRotatedParamMaxAccessKeyAge` | `90` | String |
| `AcmCertificateExpirationCheckParamDaysToExpiration` | `90` | String |
| `BackupPlanMinFrequencyAndMinRetentionCheckParamRequiredFrequencyUnit` | `days` | String |
| `BackupPlanMinFrequencyAndMinRetentionCheckParamRequiredFrequencyValue` | `1` | String |
| `BackupPlanMinFrequencyAndMinRetentionCheckParamRequiredRetentionDays` | `35` | String |
| `DynamodbThroughputLimitCheckParamAccountRCUThresholdPercentage` | `80` | String |
| `DynamodbThroughputLimitCheckParamAccountWCUThresholdPercentage` | `80` | String |
| `Ec2VolumeInuseCheckParamDeleteOnTermination` | `true` | String |
| `GuarddutyNonArchivedFindingsParamDaysHighSev` | `1` | String |
| `GuarddutyNonArchivedFindingsParamDaysLowSev` | `30` | String |
| `GuarddutyNonArchivedFindingsParamDaysMediumSev` | `7` | String |
| `IamCustomerPolicyBlockedKmsActionsParamBlockedActionsPatterns` | `kms:Decrypt,kms:ReEncryptFrom` | String |
| `IamInlinePolicyBlockedKmsActionsParamBlockedActionsPatterns` | `kms:Decrypt,kms:ReEncryptFrom` | String |
| `IamPasswordPolicyParamMaxPasswordAge` | `90` | String |
| `IamPasswordPolicyParamMinimumPasswordLength` | `14` | String |
| `IamPasswordPolicyParamPasswordReusePrevention` | `24` | String |
| `IamPasswordPolicyParamRequireLowercaseCharacters` | `true` | String |
| `IamPasswordPolicyParamRequireNumbers` | `true` | String |
| `IamPasswordPolicyParamRequireSymbols` | `true` | String |
| `IamPasswordPolicyParamRequireUppercaseCharacters` | `true` | String |
| `IamUserUnusedCredentialsCheckParamMaxCredentialUsageAge` | `90` | String |
| `LambdaConcurrencyCheckParamConcurrencyLimitHigh` | `1000` | String |
| `LambdaConcurrencyCheckParamConcurrencyLimitLow` | `500` | String |
| `RestrictedIncomingTrafficParamBlockedPort1` | `20` | String |
| `RestrictedIncomingTrafficParamBlockedPort2` | `21` | String |
| `RestrictedIncomingTrafficParamBlockedPort3` | `3389` | String |
| `RestrictedIncomingTrafficParamBlockedPort4` | `3306` | String |
| `RestrictedIncomingTrafficParamBlockedPort5` | `4333` | String |
| `VpcSgOpenOnlyToAuthorizedPortsParamAuthorizedTcpPorts` | `443` | String |

## Config Rules

Total rules: **129**

### AccessKeysRotated

- **Config Rule:** `access-keys-rotated`
- **Source:** `ACCESS_KEYS_ROTATED`
- **Input Parameters:**
  - `maxAccessKeyAge`: `{'Fn::If': ['accessKeysRotatedParamMaxAccessKeyAge', {'Ref': 'AccessKeysRotatedParamMaxAccessKeyAge'}, {'Ref': 'AWS::NoValue'}]}`

### AcmCertificateExpirationCheck

- **Config Rule:** `acm-certificate-expiration-check`
- **Source:** `ACM_CERTIFICATE_EXPIRATION_CHECK`
- **Input Parameters:**
  - `daysToExpiration`: `{'Fn::If': ['acmCertificateExpirationCheckParamDaysToExpiration', {'Ref': 'AcmCertificateExpirationCheckParamDaysToExpiration'}, {'Ref': 'AWS::NoValue'}]}`

### AlbHttpToHttpsRedirectionCheck

- **Config Rule:** `alb-http-to-https-redirection-check`
- **Source:** `ALB_HTTP_TO_HTTPS_REDIRECTION_CHECK`

### AlbWafEnabled

- **Config Rule:** `alb-waf-enabled`
- **Source:** `ALB_WAF_ENABLED`

### ApiGwAssociatedWithWaf

- **Config Rule:** `api-gw-associated-with-waf`
- **Source:** `API_GW_ASSOCIATED_WITH_WAF`

### ApiGwCacheEnabledAndEncrypted

- **Config Rule:** `api-gw-cache-enabled-and-encrypted`
- **Source:** `API_GW_CACHE_ENABLED_AND_ENCRYPTED`

### ApiGwExecutionLoggingEnabled

- **Config Rule:** `api-gw-execution-logging-enabled`
- **Source:** `API_GW_EXECUTION_LOGGING_ENABLED`

### ApiGwSslEnabled

- **Config Rule:** `api-gw-ssl-enabled`
- **Source:** `API_GW_SSL_ENABLED`

### AuroraResourcesProtectedByBackupPlan

- **Config Rule:** `aurora-resources-protected-by-backup-plan`
- **Source:** `AURORA_RESOURCES_PROTECTED_BY_BACKUP_PLAN`

### AutoscalingGroupElbHealthcheckRequired

- **Config Rule:** `autoscaling-group-elb-healthcheck-required`
- **Source:** `AUTOSCALING_GROUP_ELB_HEALTHCHECK_REQUIRED`

### AutoscalingLaunchConfigPublicIpDisabled

- **Config Rule:** `autoscaling-launch-config-public-ip-disabled`
- **Source:** `AUTOSCALING_LAUNCH_CONFIG_PUBLIC_IP_DISABLED`

### BackupPlanMinFrequencyAndMinRetentionCheck

- **Config Rule:** `backup-plan-min-frequency-and-min-retention-check`
- **Source:** `BACKUP_PLAN_MIN_FREQUENCY_AND_MIN_RETENTION_CHECK`
- **Input Parameters:**
  - `requiredFrequencyUnit`: `{'Fn::If': ['backupPlanMinFrequencyAndMinRetentionCheckParamRequiredFrequencyUnit', {'Ref': 'BackupPlanMinFrequencyAndMinRetentionCheckParamRequiredFrequencyUnit'}, {'Ref': 'AWS::NoValue'}]}`
  - `requiredFrequencyValue`: `{'Fn::If': ['backupPlanMinFrequencyAndMinRetentionCheckParamRequiredFrequencyValue', {'Ref': 'BackupPlanMinFrequencyAndMinRetentionCheckParamRequiredFrequencyValue'}, {'Ref': 'AWS::NoValue'}]}`
  - `requiredRetentionDays`: `{'Fn::If': ['backupPlanMinFrequencyAndMinRetentionCheckParamRequiredRetentionDays', {'Ref': 'BackupPlanMinFrequencyAndMinRetentionCheckParamRequiredRetentionDays'}, {'Ref': 'AWS::NoValue'}]}`

### BeanstalkEnhancedHealthReportingEnabled

- **Config Rule:** `beanstalk-enhanced-health-reporting-enabled`
- **Source:** `BEANSTALK_ENHANCED_HEALTH_REPORTING_ENABLED`

### CloudTrailCloudWatchLogsEnabled

- **Config Rule:** `cloud-trail-cloud-watch-logs-enabled`
- **Source:** `CLOUD_TRAIL_CLOUD_WATCH_LOGS_ENABLED`

### CloudTrailEnabled

- **Config Rule:** `cloudtrail-enabled`
- **Source:** `CLOUD_TRAIL_ENABLED`

### CloudTrailEncryptionEnabled

- **Config Rule:** `cloud-trail-encryption-enabled`
- **Source:** `CLOUD_TRAIL_ENCRYPTION_ENABLED`

### CloudTrailLogFileValidationEnabled

- **Config Rule:** `cloud-trail-log-file-validation-enabled`
- **Source:** `CLOUD_TRAIL_LOG_FILE_VALIDATION_ENABLED`

### CloudtrailS3DataeventsEnabled

- **Config Rule:** `cloudtrail-s3-dataevents-enabled`
- **Source:** `CLOUDTRAIL_S3_DATAEVENTS_ENABLED`

### CloudwatchAlarmActionCheck

- **Config Rule:** `cloudwatch-alarm-action-check`
- **Source:** `CLOUDWATCH_ALARM_ACTION_CHECK`
- **Input Parameters:**
  - `alarmActionRequired`: `true`
  - `insufficientDataActionRequired`: `true`
  - `okActionRequired`: `false`

### CloudwatchLogGroupEncrypted

- **Config Rule:** `cloudwatch-log-group-encrypted`
- **Source:** `CLOUDWATCH_LOG_GROUP_ENCRYPTED`

### CmkBackingKeyRotationEnabled

- **Config Rule:** `cmk-backing-key-rotation-enabled`
- **Source:** `CMK_BACKING_KEY_ROTATION_ENABLED`

### CodebuildProjectEnvvarAwscredCheck

- **Config Rule:** `codebuild-project-envvar-awscred-check`
- **Source:** `CODEBUILD_PROJECT_ENVVAR_AWSCRED_CHECK`

### CodebuildProjectLoggingEnabled

- **Config Rule:** `codebuild-project-logging-enabled`
- **Source:** `CODEBUILD_PROJECT_LOGGING_ENABLED`

### CodebuildProjectSourceRepoUrlCheck

- **Config Rule:** `codebuild-project-source-repo-url-check`
- **Source:** `CODEBUILD_PROJECT_SOURCE_REPO_URL_CHECK`

### CwLoggroupRetentionPeriodCheck

- **Config Rule:** `cw-loggroup-retention-period-check`
- **Source:** `CW_LOGGROUP_RETENTION_PERIOD_CHECK`

### DbInstanceBackupEnabled

- **Config Rule:** `db-instance-backup-enabled`
- **Source:** `DB_INSTANCE_BACKUP_ENABLED`

### DmsReplicationNotPublic

- **Config Rule:** `dms-replication-not-public`
- **Source:** `DMS_REPLICATION_NOT_PUBLIC`

### DynamodbAutoscalingEnabled

- **Config Rule:** `dynamodb-autoscaling-enabled`
- **Source:** `DYNAMODB_AUTOSCALING_ENABLED`

### DynamodbPitrEnabled

- **Config Rule:** `dynamodb-pitr-enabled`
- **Source:** `DYNAMODB_PITR_ENABLED`

### DynamodbResourcesProtectedByBackupPlan

- **Config Rule:** `dynamodb-resources-protected-by-backup-plan`
- **Source:** `DYNAMODB_RESOURCES_PROTECTED_BY_BACKUP_PLAN`

### DynamodbThroughputLimitCheck

- **Config Rule:** `dynamodb-throughput-limit-check`
- **Source:** `DYNAMODB_THROUGHPUT_LIMIT_CHECK`
- **Input Parameters:**
  - `accountRCUThresholdPercentage`: `{'Fn::If': ['dynamodbThroughputLimitCheckParamAccountRCUThresholdPercentage', {'Ref': 'DynamodbThroughputLimitCheckParamAccountRCUThresholdPercentage'}, {'Ref': 'AWS::NoValue'}]}`
  - `accountWCUThresholdPercentage`: `{'Fn::If': ['dynamodbThroughputLimitCheckParamAccountWCUThresholdPercentage', {'Ref': 'DynamodbThroughputLimitCheckParamAccountWCUThresholdPercentage'}, {'Ref': 'AWS::NoValue'}]}`

### EbsOptimizedInstance

- **Config Rule:** `ebs-optimized-instance`
- **Source:** `EBS_OPTIMIZED_INSTANCE`

### EbsResourcesProtectedByBackupPlan

- **Config Rule:** `ebs-resources-protected-by-backup-plan`
- **Source:** `EBS_RESOURCES_PROTECTED_BY_BACKUP_PLAN`

### EbsSnapshotPublicRestorableCheck

- **Config Rule:** `ebs-snapshot-public-restorable-check`
- **Source:** `EBS_SNAPSHOT_PUBLIC_RESTORABLE_CHECK`

### Ec2EbsEncryptionByDefault

- **Config Rule:** `ec2-ebs-encryption-by-default`
- **Source:** `EC2_EBS_ENCRYPTION_BY_DEFAULT`

### Ec2Imdsv2Check

- **Config Rule:** `ec2-imdsv2-check`
- **Source:** `EC2_IMDSV2_CHECK`

### Ec2InstanceDetailedMonitoringEnabled

- **Config Rule:** `ec2-instance-detailed-monitoring-enabled`
- **Source:** `EC2_INSTANCE_DETAILED_MONITORING_ENABLED`

### Ec2InstanceManagedBySsm

- **Config Rule:** `ec2-instance-managed-by-systems-manager`
- **Source:** `EC2_INSTANCE_MANAGED_BY_SSM`

### Ec2InstanceNoPublicIp

- **Config Rule:** `ec2-instance-no-public-ip`
- **Source:** `EC2_INSTANCE_NO_PUBLIC_IP`

### Ec2InstanceProfileAttached

- **Config Rule:** `ec2-instance-profile-attached`
- **Source:** `EC2_INSTANCE_PROFILE_ATTACHED`

### Ec2ManagedinstanceAssociationComplianceStatusCheck

- **Config Rule:** `ec2-managedinstance-association-compliance-status-check`
- **Source:** `EC2_MANAGEDINSTANCE_ASSOCIATION_COMPLIANCE_STATUS_CHECK`

### Ec2ManagedinstancePatchComplianceStatusCheck

- **Config Rule:** `ec2-managedinstance-patch-compliance-status-check`
- **Source:** `EC2_MANAGEDINSTANCE_PATCH_COMPLIANCE_STATUS_CHECK`

### Ec2ResourcesProtectedByBackupPlan

- **Config Rule:** `ec2-resources-protected-by-backup-plan`
- **Source:** `EC2_RESOURCES_PROTECTED_BY_BACKUP_PLAN`

### Ec2StoppedInstance

- **Config Rule:** `ec2-stopped-instance`
- **Source:** `EC2_STOPPED_INSTANCE`

### Ec2VolumeInuseCheck

- **Config Rule:** `ec2-volume-inuse-check`
- **Source:** `EC2_VOLUME_INUSE_CHECK`
- **Input Parameters:**
  - `deleteOnTermination`: `{'Fn::If': ['ec2VolumeInuseCheckParamDeleteOnTermination', {'Ref': 'Ec2VolumeInuseCheckParamDeleteOnTermination'}, {'Ref': 'AWS::NoValue'}]}`

### EcsTaskDefinitionMemoryHardLimit

- **Config Rule:** `ecs-task-definition-memory-hard-limit`
- **Source:** `ECS_TASK_DEFINITION_MEMORY_HARD_LIMIT`

### EcsTaskDefinitionUserForHostModeCheck

- **Config Rule:** `ecs-task-definition-user-for-host-mode-check`
- **Source:** `ECS_TASK_DEFINITION_USER_FOR_HOST_MODE_CHECK`

### EfsEncryptedCheck

- **Config Rule:** `efs-encrypted-check`
- **Source:** `EFS_ENCRYPTED_CHECK`

### EfsResourcesProtectedByBackupPlan

- **Config Rule:** `efs-resources-protected-by-backup-plan`
- **Source:** `EFS_RESOURCES_PROTECTED_BY_BACKUP_PLAN`

### ElasticBeanstalkManagedUpdatesEnabled

- **Config Rule:** `elastic-beanstalk-managed-updates-enabled`
- **Source:** `ELASTIC_BEANSTALK_MANAGED_UPDATES_ENABLED`

### ElasticacheRedisClusterAutomaticBackupCheck

- **Config Rule:** `elasticache-redis-cluster-automatic-backup-check`
- **Source:** `ELASTICACHE_REDIS_CLUSTER_AUTOMATIC_BACKUP_CHECK`

### ElasticsearchEncryptedAtRest

- **Config Rule:** `elasticsearch-encrypted-at-rest`
- **Source:** `ELASTICSEARCH_ENCRYPTED_AT_REST`

### ElasticsearchInVpcOnly

- **Config Rule:** `elasticsearch-in-vpc-only`
- **Source:** `ELASTICSEARCH_IN_VPC_ONLY`

### ElasticsearchLogsToCloudwatch

- **Config Rule:** `elasticsearch-logs-to-cloudwatch`
- **Source:** `ELASTICSEARCH_LOGS_TO_CLOUDWATCH`

### ElasticsearchNodeToNodeEncryptionCheck

- **Config Rule:** `elasticsearch-node-to-node-encryption-check`
- **Source:** `ELASTICSEARCH_NODE_TO_NODE_ENCRYPTION_CHECK`

### ElbCrossZoneLoadBalancingEnabled

- **Config Rule:** `elb-cross-zone-load-balancing-enabled`
- **Source:** `ELB_CROSS_ZONE_LOAD_BALANCING_ENABLED`

### ElbDeletionProtectionEnabled

- **Config Rule:** `elb-deletion-protection-enabled`
- **Source:** `ELB_DELETION_PROTECTION_ENABLED`

### ElbLoggingEnabled

- **Config Rule:** `elb-logging-enabled`
- **Source:** `ELB_LOGGING_ENABLED`

### ElbTlsHttpsListenersOnly

- **Config Rule:** `elb-tls-https-listeners-only`
- **Source:** `ELB_TLS_HTTPS_LISTENERS_ONLY`

### Elbv2AcmCertificateRequired

- **Config Rule:** `elbv2-acm-certificate-required`
- **Source:** `ELBV2_ACM_CERTIFICATE_REQUIRED`

### EmrMasterNoPublicIp

- **Config Rule:** `emr-master-no-public-ip`
- **Source:** `EMR_MASTER_NO_PUBLIC_IP`

### EncryptedVolumes

- **Config Rule:** `encrypted-volumes`
- **Source:** `ENCRYPTED_VOLUMES`

### FsxResourcesProtectedByBackupPlan

- **Config Rule:** `fsx-resources-protected-by-backup-plan`
- **Source:** `FSX_RESOURCES_PROTECTED_BY_BACKUP_PLAN`

### GuarddutyEnabledCentralized

- **Config Rule:** `guardduty-enabled-centralized`
- **Source:** `GUARDDUTY_ENABLED_CENTRALIZED`

### GuarddutyNonArchivedFindings

- **Config Rule:** `guardduty-non-archived-findings`
- **Source:** `GUARDDUTY_NON_ARCHIVED_FINDINGS`
- **Input Parameters:**
  - `daysHighSev`: `{'Fn::If': ['guarddutyNonArchivedFindingsParamDaysHighSev', {'Ref': 'GuarddutyNonArchivedFindingsParamDaysHighSev'}, {'Ref': 'AWS::NoValue'}]}`
  - `daysLowSev`: `{'Fn::If': ['guarddutyNonArchivedFindingsParamDaysLowSev', {'Ref': 'GuarddutyNonArchivedFindingsParamDaysLowSev'}, {'Ref': 'AWS::NoValue'}]}`
  - `daysMediumSev`: `{'Fn::If': ['guarddutyNonArchivedFindingsParamDaysMediumSev', {'Ref': 'GuarddutyNonArchivedFindingsParamDaysMediumSev'}, {'Ref': 'AWS::NoValue'}]}`

### IamCustomerPolicyBlockedKmsActions

- **Config Rule:** `iam-customer-policy-blocked-kms-actions`
- **Source:** `IAM_CUSTOMER_POLICY_BLOCKED_KMS_ACTIONS`
- **Input Parameters:**
  - `blockedActionsPatterns`: `{'Fn::If': ['iamCustomerPolicyBlockedKmsActionsParamBlockedActionsPatterns', {'Ref': 'IamCustomerPolicyBlockedKmsActionsParamBlockedActionsPatterns'}, {'Ref': 'AWS::NoValue'}]}`

### IamGroupHasUsersCheck

- **Config Rule:** `iam-group-has-users-check`
- **Source:** `IAM_GROUP_HAS_USERS_CHECK`

### IamInlinePolicyBlockedKmsActions

- **Config Rule:** `iam-inline-policy-blocked-kms-actions`
- **Source:** `IAM_INLINE_POLICY_BLOCKED_KMS_ACTIONS`
- **Input Parameters:**
  - `blockedActionsPatterns`: `{'Fn::If': ['iamInlinePolicyBlockedKmsActionsParamBlockedActionsPatterns', {'Ref': 'IamInlinePolicyBlockedKmsActionsParamBlockedActionsPatterns'}, {'Ref': 'AWS::NoValue'}]}`

### IamNoInlinePolicyCheck

- **Config Rule:** `iam-no-inline-policy-check`
- **Source:** `IAM_NO_INLINE_POLICY_CHECK`

### IamPasswordPolicy

- **Config Rule:** `iam-password-policy`
- **Source:** `IAM_PASSWORD_POLICY`
- **Input Parameters:**
  - `MaxPasswordAge`: `{'Fn::If': ['iamPasswordPolicyParamMaxPasswordAge', {'Ref': 'IamPasswordPolicyParamMaxPasswordAge'}, {'Ref': 'AWS::NoValue'}]}`
  - `MinimumPasswordLength`: `{'Fn::If': ['iamPasswordPolicyParamMinimumPasswordLength', {'Ref': 'IamPasswordPolicyParamMinimumPasswordLength'}, {'Ref': 'AWS::NoValue'}]}`
  - `PasswordReusePrevention`: `{'Fn::If': ['iamPasswordPolicyParamPasswordReusePrevention', {'Ref': 'IamPasswordPolicyParamPasswordReusePrevention'}, {'Ref': 'AWS::NoValue'}]}`
  - `RequireLowercaseCharacters`: `{'Fn::If': ['iamPasswordPolicyParamRequireLowercaseCharacters', {'Ref': 'IamPasswordPolicyParamRequireLowercaseCharacters'}, {'Ref': 'AWS::NoValue'}]}`
  - `RequireNumbers`: `{'Fn::If': ['iamPasswordPolicyParamRequireNumbers', {'Ref': 'IamPasswordPolicyParamRequireNumbers'}, {'Ref': 'AWS::NoValue'}]}`
  - `RequireSymbols`: `{'Fn::If': ['iamPasswordPolicyParamRequireSymbols', {'Ref': 'IamPasswordPolicyParamRequireSymbols'}, {'Ref': 'AWS::NoValue'}]}`
  - `RequireUppercaseCharacters`: `{'Fn::If': ['iamPasswordPolicyParamRequireUppercaseCharacters', {'Ref': 'IamPasswordPolicyParamRequireUppercaseCharacters'}, {'Ref': 'AWS::NoValue'}]}`

### IamPolicyNoStatementsWithAdminAccess

- **Config Rule:** `iam-policy-no-statements-with-admin-access`
- **Source:** `IAM_POLICY_NO_STATEMENTS_WITH_ADMIN_ACCESS`

### IamPolicyNoStatementsWithFullAccess

- **Config Rule:** `iam-policy-no-statements-with-full-access`
- **Source:** `IAM_POLICY_NO_STATEMENTS_WITH_FULL_ACCESS`

### IamRootAccessKeyCheck

- **Config Rule:** `iam-root-access-key-check`
- **Source:** `IAM_ROOT_ACCESS_KEY_CHECK`

### IamUserGroupMembershipCheck

- **Config Rule:** `iam-user-group-membership-check`
- **Source:** `IAM_USER_GROUP_MEMBERSHIP_CHECK`

### IamUserMfaEnabled

- **Config Rule:** `iam-user-mfa-enabled`
- **Source:** `IAM_USER_MFA_ENABLED`

### IamUserNoPoliciesCheck

- **Config Rule:** `iam-user-no-policies-check`
- **Source:** `IAM_USER_NO_POLICIES_CHECK`

### IamUserUnusedCredentialsCheck

- **Config Rule:** `iam-user-unused-credentials-check`
- **Source:** `IAM_USER_UNUSED_CREDENTIALS_CHECK`
- **Input Parameters:**
  - `maxCredentialUsageAge`: `{'Fn::If': ['iamUserUnusedCredentialsCheckParamMaxCredentialUsageAge', {'Ref': 'IamUserUnusedCredentialsCheckParamMaxCredentialUsageAge'}, {'Ref': 'AWS::NoValue'}]}`

### IncomingSshDisabled

- **Config Rule:** `restricted-ssh`
- **Source:** `INCOMING_SSH_DISABLED`

### InstancesInVpc

- **Config Rule:** `ec2-instances-in-vpc`
- **Source:** `INSTANCES_IN_VPC`

### KmsCmkNotScheduledForDeletion

- **Config Rule:** `kms-cmk-not-scheduled-for-deletion`
- **Source:** `KMS_CMK_NOT_SCHEDULED_FOR_DELETION`

### LambdaConcurrencyCheck

- **Config Rule:** `lambda-concurrency-check`
- **Source:** `LAMBDA_CONCURRENCY_CHECK`
- **Input Parameters:**
  - `ConcurrencyLimitHigh`: `{'Fn::If': ['lambdaConcurrencyCheckParamConcurrencyLimitHigh', {'Ref': 'LambdaConcurrencyCheckParamConcurrencyLimitHigh'}, {'Ref': 'AWS::NoValue'}]}`
  - `ConcurrencyLimitLow`: `{'Fn::If': ['lambdaConcurrencyCheckParamConcurrencyLimitLow', {'Ref': 'LambdaConcurrencyCheckParamConcurrencyLimitLow'}, {'Ref': 'AWS::NoValue'}]}`

### LambdaDlqCheck

- **Config Rule:** `lambda-dlq-check`
- **Source:** `LAMBDA_DLQ_CHECK`

### LambdaFunctionPublicAccessProhibited

- **Config Rule:** `lambda-function-public-access-prohibited`
- **Source:** `LAMBDA_FUNCTION_PUBLIC_ACCESS_PROHIBITED`

### LambdaInsideVpc

- **Config Rule:** `lambda-inside-vpc`
- **Source:** `LAMBDA_INSIDE_VPC`

### MfaEnabledForIamConsoleAccess

- **Config Rule:** `mfa-enabled-for-iam-console-access`
- **Source:** `MFA_ENABLED_FOR_IAM_CONSOLE_ACCESS`

### MultiRegionCloudTrailEnabled

- **Config Rule:** `multi-region-cloudtrail-enabled`
- **Source:** `MULTI_REGION_CLOUD_TRAIL_ENABLED`

### NoUnrestrictedRouteToIgw

- **Config Rule:** `no-unrestricted-route-to-igw`
- **Source:** `NO_UNRESTRICTED_ROUTE_TO_IGW`

### OpensearchLogsToCloudwatch

- **Config Rule:** `opensearch-logs-to-cloudwatch`
- **Source:** `OPENSEARCH_LOGS_TO_CLOUDWATCH`

### RdsEnhancedMonitoringEnabled

- **Config Rule:** `rds-enhanced-monitoring-enabled`
- **Source:** `RDS_ENHANCED_MONITORING_ENABLED`

### RdsInstanceDeletionProtectionEnabled

- **Config Rule:** `rds-instance-deletion-protection-enabled`
- **Source:** `RDS_INSTANCE_DELETION_PROTECTION_ENABLED`

### RdsInstancePublicAccessCheck

- **Config Rule:** `rds-instance-public-access-check`
- **Source:** `RDS_INSTANCE_PUBLIC_ACCESS_CHECK`

### RdsLoggingEnabled

- **Config Rule:** `rds-logging-enabled`
- **Source:** `RDS_LOGGING_ENABLED`

### RdsMultiAzSupport

- **Config Rule:** `rds-multi-az-support`
- **Source:** `RDS_MULTI_AZ_SUPPORT`

### RdsClusterMultiAzEnabled

- **Config Rule:** `rds-cluster-multi-az-enabled`
- **Source:** `RDS_CLUSTER_MULTI_AZ_ENABLED`

### RdsResourcesProtectedByBackupPlan

- **Config Rule:** `rds-resources-protected-by-backup-plan`
- **Source:** `RDS_RESOURCES_PROTECTED_BY_BACKUP_PLAN`

### RdsSnapshotEncrypted

- **Config Rule:** `rds-snapshot-encrypted`
- **Source:** `RDS_SNAPSHOT_ENCRYPTED`

### RdsSnapshotsPublicProhibited

- **Config Rule:** `rds-snapshots-public-prohibited`
- **Source:** `RDS_SNAPSHOTS_PUBLIC_PROHIBITED`

### RdsStorageEncrypted

- **Config Rule:** `rds-storage-encrypted`
- **Source:** `RDS_STORAGE_ENCRYPTED`

### RedshiftBackupEnabled

- **Config Rule:** `redshift-backup-enabled`
- **Source:** `REDSHIFT_BACKUP_ENABLED`

### RedshiftClusterConfigurationCheck

- **Config Rule:** `redshift-cluster-configuration-check`
- **Source:** `REDSHIFT_CLUSTER_CONFIGURATION_CHECK`
- **Input Parameters:**
  - `clusterDbEncrypted`: `true`
  - `loggingEnabled`: `true`

### RedshiftClusterKmsEnabled

- **Config Rule:** `redshift-cluster-kms-enabled`
- **Source:** `REDSHIFT_CLUSTER_KMS_ENABLED`

### RedshiftClusterPublicAccessCheck

- **Config Rule:** `redshift-cluster-public-access-check`
- **Source:** `REDSHIFT_CLUSTER_PUBLIC_ACCESS_CHECK`

### RedshiftRequireTlsSsl

- **Config Rule:** `redshift-require-tls-ssl`
- **Source:** `REDSHIFT_REQUIRE_TLS_SSL`

### RestrictedIncomingTraffic

- **Config Rule:** `restricted-common-ports`
- **Source:** `RESTRICTED_INCOMING_TRAFFIC`
- **Input Parameters:**
  - `blockedPort1`: `{'Fn::If': ['restrictedIncomingTrafficParamBlockedPort1', {'Ref': 'RestrictedIncomingTrafficParamBlockedPort1'}, {'Ref': 'AWS::NoValue'}]}`
  - `blockedPort2`: `{'Fn::If': ['restrictedIncomingTrafficParamBlockedPort2', {'Ref': 'RestrictedIncomingTrafficParamBlockedPort2'}, {'Ref': 'AWS::NoValue'}]}`
  - `blockedPort3`: `{'Fn::If': ['restrictedIncomingTrafficParamBlockedPort3', {'Ref': 'RestrictedIncomingTrafficParamBlockedPort3'}, {'Ref': 'AWS::NoValue'}]}`
  - `blockedPort4`: `{'Fn::If': ['restrictedIncomingTrafficParamBlockedPort4', {'Ref': 'RestrictedIncomingTrafficParamBlockedPort4'}, {'Ref': 'AWS::NoValue'}]}`
  - `blockedPort5`: `{'Fn::If': ['restrictedIncomingTrafficParamBlockedPort5', {'Ref': 'RestrictedIncomingTrafficParamBlockedPort5'}, {'Ref': 'AWS::NoValue'}]}`

### RootAccountHardwareMfaEnabled

- **Config Rule:** `root-account-hardware-mfa-enabled`
- **Source:** `ROOT_ACCOUNT_HARDWARE_MFA_ENABLED`

### RootAccountMfaEnabled

- **Config Rule:** `root-account-mfa-enabled`
- **Source:** `ROOT_ACCOUNT_MFA_ENABLED`

### S3AccountLevelPublicAccessBlocksPeriodic

- **Config Rule:** `s3-account-level-public-access-blocks-periodic`
- **Source:** `S3_ACCOUNT_LEVEL_PUBLIC_ACCESS_BLOCKS_PERIODIC`

### S3BucketDefaultLockEnabled

- **Config Rule:** `s3-bucket-default-lock-enabled`
- **Source:** `S3_BUCKET_DEFAULT_LOCK_ENABLED`

### S3BucketLevelPublicAccessProhibited

- **Config Rule:** `s3-bucket-level-public-access-prohibited`
- **Source:** `S3_BUCKET_LEVEL_PUBLIC_ACCESS_PROHIBITED`

### S3BucketLoggingEnabled

- **Config Rule:** `s3-bucket-logging-enabled`
- **Source:** `S3_BUCKET_LOGGING_ENABLED`

### S3BucketPublicReadProhibited

- **Config Rule:** `s3-bucket-public-read-prohibited`
- **Source:** `S3_BUCKET_PUBLIC_READ_PROHIBITED`

### S3BucketPublicWriteProhibited

- **Config Rule:** `s3-bucket-public-write-prohibited`
- **Source:** `S3_BUCKET_PUBLIC_WRITE_PROHIBITED`

### S3BucketReplicationEnabled

- **Config Rule:** `s3-bucket-replication-enabled`
- **Source:** `S3_BUCKET_REPLICATION_ENABLED`

### S3BucketServerSideEncryptionEnabled

- **Config Rule:** `s3-bucket-server-side-encryption-enabled`
- **Source:** `S3_BUCKET_SERVER_SIDE_ENCRYPTION_ENABLED`

### S3BucketSslRequestsOnly

- **Config Rule:** `s3-bucket-ssl-requests-only`
- **Source:** `S3_BUCKET_SSL_REQUESTS_ONLY`

### S3BucketVersioningEnabled

- **Config Rule:** `s3-bucket-versioning-enabled`
- **Source:** `S3_BUCKET_VERSIONING_ENABLED`

### S3DefaultEncryptionKms

- **Config Rule:** `s3-default-encryption-kms`
- **Source:** `S3_DEFAULT_ENCRYPTION_KMS`

### SagemakerEndpointConfigurationKmsKeyConfigured

- **Config Rule:** `sagemaker-endpoint-configuration-kms-key-configured`
- **Source:** `SAGEMAKER_ENDPOINT_CONFIGURATION_KMS_KEY_CONFIGURED`

### SagemakerNotebookInstanceKmsKeyConfigured

- **Config Rule:** `sagemaker-notebook-instance-kms-key-configured`
- **Source:** `SAGEMAKER_NOTEBOOK_INSTANCE_KMS_KEY_CONFIGURED`

### SagemakerNotebookNoDirectInternetAccess

- **Config Rule:** `sagemaker-notebook-no-direct-internet-access`
- **Source:** `SAGEMAKER_NOTEBOOK_NO_DIRECT_INTERNET_ACCESS`

### SecurityhubEnabled

- **Config Rule:** `securityhub-enabled`
- **Source:** `SECURITYHUB_ENABLED`

### SnsEncryptedKms

- **Config Rule:** `sns-encrypted-kms`
- **Source:** `SNS_ENCRYPTED_KMS`

### SsmDocumentNotPublic

- **Config Rule:** `ssm-document-not-public`
- **Source:** `SSM_DOCUMENT_NOT_PUBLIC`

### SubnetAutoAssignPublicIpDisabled

- **Config Rule:** `subnet-auto-assign-public-ip-disabled`
- **Source:** `SUBNET_AUTO_ASSIGN_PUBLIC_IP_DISABLED`

### VpcDefaultSecurityGroupClosed

- **Config Rule:** `vpc-default-security-group-closed`
- **Source:** `VPC_DEFAULT_SECURITY_GROUP_CLOSED`

### VpcFlowLogsEnabled

- **Config Rule:** `vpc-flow-logs-enabled`
- **Source:** `VPC_FLOW_LOGS_ENABLED`

### VpcSgOpenOnlyToAuthorizedPorts

- **Config Rule:** `vpc-sg-open-only-to-authorized-ports`
- **Source:** `VPC_SG_OPEN_ONLY_TO_AUTHORIZED_PORTS`
- **Input Parameters:**
  - `authorizedTcpPorts`: `{'Fn::If': ['vpcSgOpenOnlyToAuthorizedPortsParamAuthorizedTcpPorts', {'Ref': 'VpcSgOpenOnlyToAuthorizedPortsParamAuthorizedTcpPorts'}, {'Ref': 'AWS::NoValue'}]}`

### VpcVpn2TunnelsUp

- **Config Rule:** `vpc-vpn-2-tunnels-up`
- **Source:** `VPC_VPN_2_TUNNELS_UP`

### Wafv2LoggingEnabled

- **Config Rule:** `wafv2-logging-enabled`
- **Source:** `WAFV2_LOGGING_ENABLED`

