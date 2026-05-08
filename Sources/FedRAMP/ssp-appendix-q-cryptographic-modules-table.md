---
title: "SSP-Appendix-Q-Cryptographic-Modules-Table"
type: reference
framework: fedramp
source_format: converted
created: 2026-04-05
tags:
  - fedramp
  - template
---

# SSP-Appendix-Q-Cryptographic-Modules-Table

> Source: `SSP-Appendix-Q-Cryptographic-Modules-Table.docx`

TEMPLATE REVISION HISTORY

How to contact us

For questions about FedRAMP, or for questions about this document including how to use it, contact info@FedRAMP.gov.

For more information about FedRAMP, see www.FedRAMP.gov.

### Appendix Q <CSO Name> Encryption Implementation Status

| Date | Version | Pages | Description | Author |
| --- | --- | --- | --- | --- |
| 06/30/2023 | 1.0 | All | Initial publication. | FedRAMP PMO |

| Data in Transit (DIT) | Data in Transit (DIT) | Data in Transit (DIT) | Data in Transit (DIT) | Data in Transit (DIT) | Data in Transit (DIT) | Data in Transit (DIT) | Data in Transit (DIT) | Data in Transit (DIT) | Data in Transit (DIT) | Data in Transit (DIT) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | Source | Source | Source | Source | Destination | Destination | Destination | Destination | Destination |  |
| Ref # | Areas of DIT | CMVP # | CM Vendr | Module Name | Areas of DIT | CMVP # | CM Vendor | Module Name | Usage | Notes |
| 1 | NGINX Server <br>  <br> <Use Case Example - Please Delete> | #4271 <br>  <br>  <br>  Embedded CM <br>  Third-party CM <br>  Uses OS CM <br>  In FIPS Mode <br>  Other <br> ______________ | Red Hat, Inc. | RHEL 8 OpenSSL | All Application Servers | #3980 <br>  <br>  <br>  Embedded CM <br>  Third-party CM <br>  Uses OS CM <br>  In FIPS Mode <br>  Other <br> ______________ | Canonical Ltd. | Ubuntu 18.04 OpenSSH Server | Load Balancer TLS to Application Server <br>  <br>  TLS 1.1 or earlier <br>  TLS 1.2 <br> TLS 1.3 <br>  Other ________ |  |
| 2 | All Application Servers <br>  <br> <Use Case Example - Please Delete> | None <br>  <br>  <br>  Embedded CM <br>  Third-party CM <br>  Uses OS CM <br>  In FIPS Mode <br>  Other <br> ______________ | CentOS 7.9 | OpenSSL 1.0.1 | PostgreSQL | #3980 <br>  <br>  <br>  Embedded CM <br>  Third-party CM <br>  Uses OS CM <br>  In FIPS Mode <br>  Other <br> ______________ | Canonical Ltd. | Ubuntu 18.04 OpenSSH Server | Application servers to common DB <br>  <br>  TLS 1.1 or earlier <br>  TLS 1.2 <br> TLS 1.3 <br>  Other ________ | Plans to move to RHEL 8. See POA&M ID 111. |
| 3 | Container traffic <br>  <br> <Use Case Example - Please Delete> | #3678 <br>  <br>  <br>  Embedded CM <br>  Third-party CM <br>  Uses OS CM <br>  In FIPS Mode <br>  Other <br> ______________ | Google | BoringCrypto | Container traffic | #3678 <br>  <br>  <br>  Embedded CM <br>  Third-party CM <br>  Uses OS CM <br>  In FIPS Mode <br>  Other <br> ______________ | Google | BoringCrypto | Istio Tetrate service mesh <br>  <br>  TLS 1.1 or earlier <br>  TLS 1.2 <br> TLS 1.3 <br>  Other ________ |  |
| # | <Fill In> <br>  <br> <Copy and Paste this Row to Complete> | <Fill In and Select Below> <br>  <br>  Embedded CM <br>  Third-party CM <br>  Uses OS CM <br>  In FIPS Mode <br>  Other <br> ______________ | <Fill In> | <Fill In> | <Fill In> | <Fill In and Select Below> <br>  <br>  Embedded CM <br>  Third-party CM <br>  Uses OS CM <br>  In FIPS Mode <br>  Other <br> ______________ | <Fill In> | <Fill In> | <Fill In and Select Below> <br>  <br>  TLS 1.1 or earlier <br>  TLS 1.2 <br> TLS 1.3 <br> Other ________ |  |

| Data at Rest (DAR) | Data at Rest (DAR) | Data at Rest (DAR) | Data at Rest (DAR) | Data at Rest (DAR) | Data at Rest (DAR) | Data at Rest (DAR) | Data at Rest (DAR) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Ref # | Areas of DAR | CMVP # | CM Vendor Name | Module Name | Usage | Encryption Type | Notes |
| 1 | PostgreSQL database <br>  <br> <Use Case Example - Please Delete> | #3980 <br>  <br>  Embedded CM <br>  Third-party CM <br>  Uses OS CM <br>  In FIPS Mode <br>  Other <br> ______________ | Canonical Ltd. | Ubuntu 18.04 OpenSSL Cryptographic Module | Volume encryption | Full disk <br>  File <br>  Record <br>  None <br>  Other ________ |  |
| 2 | App server local storage <br>  <br> <Use Case Example - Please Delete> | #2931 <br>  <br>  Embedded CM <br>  Third-party CM <br>  Uses OS CM <br>  In FIPS Mode <br>  Other <br> ______________ | Microsoft | Windows Server 2016 | OS and application binaries | Full disk <br>  File <br>  Record <br>  None <br>  Other ________ | CM is Historical, per NIST CMVP. Plans to move to Windows 2019 upon Active FIPS-140-validation achieved. See POA&M ID 123. |
| 3 | S3 buckets <br>  <br> <Use Case Example - Please Delete> | #4177 <br>  <br>  Embedded CM <br>  Third-party CM <br>  Uses OS CM <br>  In FIPS Mode <br>  Other <br> ______________ | AWS | Key Management Service (KMS) HSM | Server-side encryption with KMS keys (SSE-KMS) used to encrypt bucket | Full disk <br>  File <br>  Record <br>  None <br>  Other ________ |  |
| 4 | Hashicorp Vault Enterprise credential storage <br>  <br> <Use Case Example - Please Delete> | #3678 <br>  <br>  Embedded CM <br>  Third-party CM <br>  Uses OS CM <br>  In FIPS Mode <br>  Other <br> ______________ | Google | BoringCrypto | Storing customer and system keys and passwords | Full disk <br>  File <br>  Record <br>  None <br>  Other ________ |  |
| 5 | <Fill In> <br>  <br> <Copy and Paste this Row to Complete> | <Fill In and Select Below> <br>  <br>  Embedded CM <br>  Third-party CM <br>  Uses OS CM <br>  In FIPS Mode <br>  Other <br> ______________ | <Fill In> | <Fill In> | <Fill In> | <Select Below> <br>  Full disk <br>  File <br>  Record <br>  None <br>  Other ________ | <Fill In> |

| Other (Hashes, Digital Signatures, MFA, etc.) | Other (Hashes, Digital Signatures, MFA, etc.) | Other (Hashes, Digital Signatures, MFA, etc.) | Other (Hashes, Digital Signatures, MFA, etc.) | Other (Hashes, Digital Signatures, MFA, etc.) | Other (Hashes, Digital Signatures, MFA, etc.) | Other (Hashes, Digital Signatures, MFA, etc.) | Other (Hashes, Digital Signatures, MFA, etc.) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Ref # | Areas of Use | CMVP # | CM Vendor Name | Module Name | Usage | Encryption Type | Notes |
| 1 | MFA <br>  <br> <Use Case Example - Please Delete> | #3907 <br>  <br>  <br>  Embedded CM <br>  Third-party CM <br>  Uses OS CM <br>  In FIPS Mode <br>  Other <br> ______________ | Yubico | Yubikey | Hard token TOTP code generations |  |  |
| # | <Fill In> <br>  <br> <Use Case Example - Please Delete> | <Fill In and Select Below> <br>  <br>  Embedded CM <br>  Third-party CM <br>  Uses OS CM <br>  In FIPS Mode <br>  Other <br> ______________ | <Fill In> | <Fill In> | <Fill In> | <Fill In> | <Fill In> |

