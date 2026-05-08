---
title: "AWS Config Conformance Pack — FedRAMP HighPart2"
type: reference
framework: fedramp
source_format: converted
created: 2026-04-05
tags:
  - fedramp
  - aws-config
  - conformance-pack
---

# AWS Config Conformance Pack: FedRAMP HighPart2

> Source: `Operational-Best-Practices-for-FedRAMP-HighPart2.yaml`

## Parameters

| Parameter | Default | Type |
|---|---|---|
| `AcmCertificateExpirationCheckParamDaysToExpiration` | `90` | String |
| `BackupPlanMinFrequencyAndMinRetentionCheckParamRequiredFrequencyUnit` | `days` | String |
| `BackupPlanMinFrequencyAndMinRetentionCheckParamRequiredFrequencyValue` | `1` | String |
| `BackupPlanMinFrequencyAndMinRetentionCheckParamRequiredRetentionDays` | `35` | String |
| `BackupRecoveryPointMinimumRetentionCheckParamRequiredRetentionDays` | `35` | String |
| `IamPasswordPolicyParamMaxPasswordAge` | `90` | String |
| `IamPasswordPolicyParamMinimumPasswordLength` | `14` | String |
| `IamPasswordPolicyParamPasswordReusePrevention` | `24` | String |
| `IamPasswordPolicyParamRequireLowercaseCharacters` | `true` | String |
| `IamPasswordPolicyParamRequireNumbers` | `true` | String |
| `IamPasswordPolicyParamRequireSymbols` | `true` | String |
| `IamPasswordPolicyParamRequireUppercaseCharacters` | `true` | String |
| `IamUserUnusedCredentialsCheckParamMaxCredentialUsageAge` | `90` | String |
| `VpcSgOpenOnlyToAuthorizedPortsParamAuthorizedTcpPorts` | `443` | String |

## Config Rules

Total rules: **97**

### AcmCertificateExpirationCheck

- **Config Rule:** `acm-certificate-expiration-check`
- **Source:** `ACM_CERTIFICATE_EXPIRATION_CHECK`
- **Input Parameters:**
  - `daysToExpiration`: `{'Fn::If': ['acmCertificateExpirationCheckParamDaysToExpiration', {'Ref': 'AcmCertificateExpirationCheckParamDaysToExpiration'}, {'Ref': 'AWS::NoValue'}]}`

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

### BackupRecoveryPointEncrypted

- **Config Rule:** `backup-recovery-point-encrypted`
- **Source:** `BACKUP_RECOVERY_POINT_ENCRYPTED`

### BackupRecoveryPointManualDeletionDisabled

- **Config Rule:** `backup-recovery-point-manual-deletion-disabled`
- **Source:** `BACKUP_RECOVERY_POINT_MANUAL_DELETION_DISABLED`

### BackupRecoveryPointMinimumRetentionCheck

- **Config Rule:** `backup-recovery-point-minimum-retention-check`
- **Source:** `BACKUP_RECOVERY_POINT_MINIMUM_RETENTION_CHECK`
- **Input Parameters:**
  - `requiredRetentionDays`: `{'Fn::If': ['backupRecoveryPointMinimumRetentionCheckParamRequiredRetentionDays', {'Ref': 'BackupRecoveryPointMinimumRetentionCheckParamRequiredRetentionDays'}, {'Ref': 'AWS::NoValue'}]}`

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

### CloudtrailS3BucketPublicAccessProhibited

- **Config Rule:** `cloudtrail-s3-bucket-public-access-prohibited`
- **Source:** `CLOUDTRAIL_S3_BUCKET_PUBLIC_ACCESS_PROHIBITED`

### CloudtrailS3DataeventsEnabled

- **Config Rule:** `cloudtrail-s3-dataevents-enabled`
- **Source:** `CLOUDTRAIL_S3_DATAEVENTS_ENABLED`

### CloudtrailSecurityTrailEnabled

- **Config Rule:** `cloudtrail-security-trail-enabled`
- **Source:** `CLOUDTRAIL_SECURITY_TRAIL_ENABLED`

### CloudwatchAlarmActionCheck

- **Config Rule:** `cloudwatch-alarm-action-check`
- **Source:** `CLOUDWATCH_ALARM_ACTION_CHECK`
- **Input Parameters:**
  - `alarmActionRequired`: `TRUE`
  - `insufficientDataActionRequired`: `TRUE`
  - `okActionRequired`: `FALSE`

### CloudwatchLogGroupEncrypted

- **Config Rule:** `cloudwatch-log-group-encrypted`
- **Source:** `CLOUDWATCH_LOG_GROUP_ENCRYPTED`

### DbInstanceBackupEnabled

- **Config Rule:** `db-instance-backup-enabled`
- **Source:** `DB_INSTANCE_BACKUP_ENABLED`

### DynamodbAutoscalingEnabled

- **Config Rule:** `dynamodb-autoscaling-enabled`
- **Source:** `DYNAMODB_AUTOSCALING_ENABLED`

### DynamodbInBackupPlan

- **Config Rule:** `dynamodb-in-backup-plan`
- **Source:** `DYNAMODB_IN_BACKUP_PLAN`

### DynamodbPitrEnabled

- **Config Rule:** `dynamodb-pitr-enabled`
- **Source:** `DYNAMODB_PITR_ENABLED`

### DynamodbResourcesProtectedByBackupPlan

- **Config Rule:** `dynamodb-resources-protected-by-backup-plan`
- **Source:** `DYNAMODB_RESOURCES_PROTECTED_BY_BACKUP_PLAN`

### DynamodbTableEncryptedKms

- **Config Rule:** `dynamodb-table-encrypted-kms`
- **Source:** `DYNAMODB_TABLE_ENCRYPTED_KMS`

### EbsInBackupPlan

- **Config Rule:** `ebs-in-backup-plan`
- **Source:** `EBS_IN_BACKUP_PLAN`

### EbsResourcesProtectedByBackupPlan

- **Config Rule:** `ebs-resources-protected-by-backup-plan`
- **Source:** `EBS_RESOURCES_PROTECTED_BY_BACKUP_PLAN`

### Ec2EbsEncryptionByDefault

- **Config Rule:** `ec2-ebs-encryption-by-default`
- **Source:** `EC2_EBS_ENCRYPTION_BY_DEFAULT`

### Ec2InstanceManagedBySsm

- **Config Rule:** `ec2-instance-managed-by-systems-manager`
- **Source:** `EC2_INSTANCE_MANAGED_BY_SSM`

### Ec2ManagedinstanceAssociationComplianceStatusCheck

- **Config Rule:** `ec2-managedinstance-association-compliance-status-check`
- **Source:** `EC2_MANAGEDINSTANCE_ASSOCIATION_COMPLIANCE_STATUS_CHECK`

### Ec2ManagedinstancePatchComplianceStatusCheck

- **Config Rule:** `ec2-managedinstance-patch-compliance-status-check`
- **Source:** `EC2_MANAGEDINSTANCE_PATCH_COMPLIANCE_STATUS_CHECK`

### Ec2ResourcesProtectedByBackupPlan

- **Config Rule:** `ec2-resources-protected-by-backup-plan`
- **Source:** `EC2_RESOURCES_PROTECTED_BY_BACKUP_PLAN`

### EfsEncryptedCheck

- **Config Rule:** `efs-encrypted-check`
- **Source:** `EFS_ENCRYPTED_CHECK`

### EfsInBackupPlan

- **Config Rule:** `efs-in-backup-plan`
- **Source:** `EFS_IN_BACKUP_PLAN`

### EfsResourcesProtectedByBackupPlan

- **Config Rule:** `efs-resources-protected-by-backup-plan`
- **Source:** `EFS_RESOURCES_PROTECTED_BY_BACKUP_PLAN`

### EksEndpointNoPublicAccess

- **Config Rule:** `eks-endpoint-no-public-access`
- **Source:** `EKS_ENDPOINT_NO_PUBLIC_ACCESS`

### ElasticacheRedisClusterAutomaticBackupCheck

- **Config Rule:** `elasticache-redis-cluster-automatic-backup-check`
- **Source:** `ELASTICACHE_REDIS_CLUSTER_AUTOMATIC_BACKUP_CHECK`

### ElasticsearchEncryptedAtRest

- **Config Rule:** `elasticsearch-encrypted-at-rest`
- **Source:** `ELASTICSEARCH_ENCRYPTED_AT_REST`

### ElasticsearchLogsToCloudwatch

- **Config Rule:** `elasticsearch-logs-to-cloudwatch`
- **Source:** `ELASTICSEARCH_LOGS_TO_CLOUDWATCH`

### ElbCrossZoneLoadBalancingEnabled

- **Config Rule:** `elb-cross-zone-load-balancing-enabled`
- **Source:** `ELB_CROSS_ZONE_LOAD_BALANCING_ENABLED`

### ElbLoggingEnabled

- **Config Rule:** `elb-logging-enabled`
- **Source:** `ELB_LOGGING_ENABLED`

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

### InspectorEc2ScanEnabled

- **Config Rule:** `inspector-ec2-scan-enabled`
- **Source:** `INSPECTOR_EC2_SCAN_ENABLED`

### InspectorEcrScanEnabled

- **Config Rule:** `inspector-ecr-scan-enabled`
- **Source:** `INSPECTOR_ECR_SCAN_ENABLED`

### InspectorLambdaStandardScanEnabled

- **Config Rule:** `inspector-lambda-standard-scan-enabled`
- **Source:** `INSPECTOR_LAMBDA_STANDARD_SCAN_ENABLED`

### InstancesInVpc

- **Config Rule:** `ec2-instances-in-vpc`
- **Source:** `INSTANCES_IN_VPC`

### KinesisStreamEncrypted

- **Config Rule:** `kinesis-stream-encrypted`
- **Source:** `KINESIS_STREAM_ENCRYPTED`

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

### RdsInBackupPlan

- **Config Rule:** `rds-in-backup-plan`
- **Source:** `RDS_IN_BACKUP_PLAN`

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
  - `clusterDbEncrypted`: `TRUE`
  - `loggingEnabled`: `TRUE`

### RedshiftClusterKmsEnabled

- **Config Rule:** `redshift-cluster-kms-enabled`
- **Source:** `REDSHIFT_CLUSTER_KMS_ENABLED`

### RedshiftClusterPublicAccessCheck

- **Config Rule:** `redshift-cluster-public-access-check`
- **Source:** `REDSHIFT_CLUSTER_PUBLIC_ACCESS_CHECK`

### S3BucketCrossRegionReplicationEnabled

- **Config Rule:** `s3-bucket-cross-region-replication-enabled`
- **Source:** `S3_BUCKET_CROSS_REGION_REPLICATION_ENABLED`

### S3BucketLoggingEnabled

- **Config Rule:** `s3-bucket-logging-enabled`
- **Source:** `S3_BUCKET_LOGGING_ENABLED`

### S3BucketReplicationEnabled

- **Config Rule:** `s3-bucket-replication-enabled`
- **Source:** `S3_BUCKET_REPLICATION_ENABLED`

### S3BucketServerSideEncryptionEnabled

- **Config Rule:** `s3-bucket-server-side-encryption-enabled`
- **Source:** `S3_BUCKET_SERVER_SIDE_ENCRYPTION_ENABLED`

### S3BucketVersioningEnabled

- **Config Rule:** `s3-bucket-versioning-enabled`
- **Source:** `S3_BUCKET_VERSIONING_ENABLED`

### S3DefaultEncryptionKms

- **Config Rule:** `s3-default-encryption-kms`
- **Source:** `S3_DEFAULT_ENCRYPTION_KMS`

### S3ResourcesProtectedByBackupPlan

- **Config Rule:** `s3-resources-protected-by-backup-plan`
- **Source:** `S3_RESOURCES_PROTECTED_BY_BACKUP_PLAN`

### S3VersionLifecyclePolicyCheck

- **Config Rule:** `s3-version-lifecycle-policy-check`
- **Source:** `S3_VERSION_LIFECYCLE_POLICY_CHECK`

### SagemakerEndpointConfigurationKmsKeyConfigured

- **Config Rule:** `sagemaker-endpoint-configuration-kms-key-configured`
- **Source:** `SAGEMAKER_ENDPOINT_CONFIGURATION_KMS_KEY_CONFIGURED`

### SagemakerNotebookInstanceKmsKeyConfigured

- **Config Rule:** `sagemaker-notebook-instance-kms-key-configured`
- **Source:** `SAGEMAKER_NOTEBOOK_INSTANCE_KMS_KEY_CONFIGURED`

### SagemakerNotebookNoDirectInternetAccess

- **Config Rule:** `sagemaker-notebook-no-direct-internet-access`
- **Source:** `SAGEMAKER_NOTEBOOK_NO_DIRECT_INTERNET_ACCESS`

### SecretsmanagerUsingCmk

- **Config Rule:** `secretsmanager-using-cmk`
- **Source:** `SECRETSMANAGER_USING_CMK`

### SecurityhubEnabled

- **Config Rule:** `securityhub-enabled`
- **Source:** `SECURITYHUB_ENABLED`

### SnsEncryptedKms

- **Config Rule:** `sns-encrypted-kms`
- **Source:** `SNS_ENCRYPTED_KMS`

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

