---
title: "FedRAMP-POAM-Template"
type: reference
framework: fedramp
source_format: converted
created: 2026-04-05
tags:
  - fedramp
  - template
---

# FedRAMP-POAM-Template

> Source: `FedRAMP-POAM-Template.xlsx`

## Open POA&M Items

| Cloud Service Provider | Cloud Service Offering | Impact Level | POA&M Date |
| --- | --- | --- | --- |
| Enter the name of the CSP as it appears in the SSP and on the FedRAMP Marketplace | Enter the name of the CSO as it appears in the SSP and on the FedRAMP Marketplace | Enter the CSO's impact level (LI-SaaS, Low, Moderate or High) | Enter the date of this POA&M submission. At a miminum, the POA&M must be updated on a  monthly basis. |
| POAM ID | Controls | Weakness Name | Weakness Description |
| Assign a unique identifier to each POA&M item. This can be in any format or <br> naming convention that produces uniqueness. NOTE: During initial and annual assessments, assessors are instructed to use the CSP-established schema to assign a unique identifier (ID) to each RET item. | Enter the 800-53 control or controls that is/are affected by the weakness. If multiple controls are affected, separate them with commas. | Enter a short description of the weakness. For scan-related vulnerabilities, use the name provided by the scanner. | Enter a full description of the weakness and other relevant information. Security weaknesses must be accurately described so that they can be understood by the CSP and Authorizing Official (AO). <br>  <br> If a test was performed using a tool/scanner, use the description provided by the tool/scanner. |
| VS-001-AC(2) <br> PT-204-SR(2) | RA-5, SC-13, IR-3 | Red Hat Update for glibc security (RHSA-2021:4358) <br>  <br> Elevated User Privileges | The remote host contains one or more unsupported versions of Python. Lack of support implies that no new security patches for the product will be released by the vendor. As a result, it is likely to contain security vulnerabilities. |
| Mandatory | Mandatory | Mandatory | Mandatory |

## Closed POA&M Items

| POAM ID | Controls | Weakness Name | Weakness Description | Weakness Detector Source | Weakness Source Identifier | Asset Identifier | Point of Contact | Resources Required | Overall Remediation Plan | Original Detection Date | Scheduled Completion Date | Status Date | Vendor Dependency | Last Vendor Check-in Date | Vendor Dependent Product Name | Original Risk Rating | Adjusted Risk Rating | Risk Adjustment | False Positive | Operational Requirement | Deviation Rationale | Supporting Documents | Comments | Binding Operational Directive 22-01 tracking | Binding Operational Directive 22-01 Due Date | CVE |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

## Configuration Findings

| POAM ID | Controls | Weakness Name | Weakness Description | Weakness Detector Source | Weakness Source Identifier | Asset Identifier | Point of Contact | Resources Required | Overall Remediation Plan | Original Detection Date | Scheduled Completion Date | Status Date | Vendor Dependency | Last Vendor Check-in Date | Vendor Dependent Product Name | Original Risk Rating | Adjusted Risk Rating | Risk Adjustment | False Positive | Operational Requirement | Deviation Rationale | Supporting Documents | Comments | Binding Operational Directive 22-01 tracking | Binding Operational Directive 22-01 Due Date | CVE |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

## PL-2 Findings

| Deficiency ID | Deficiency Name | Deficiency Description | Remediation Plan/Description | Remediation Date |
| --- | --- | --- | --- | --- |
| Enter the ID provided by the 3PAO. | Enter the deficiency name provided by the 3PAO. | Enter the deficiency description provided by the 3PAO. | Enter the actions that will be (or have been) taken to address the deficiency. Include the version/date of the updated document, if applicable. | Enter the date that the deficiency was fully addressed. |
| AC-2, PL-2.1, PL-2.2 | AC-2e., AC-2.f, "Noncompliant ABD" | The ABD does not comply with instructions in the SSP template. It does not depict external system/services essential to the operation of the CSO and does not depict how CSP personnel and agency customers access the environment. | Updated the ABD to depict external systems/services essential to the operation of the CSO and how CSP personnel and agency customers access the environment. Re-reviewed instructions in the SSP template to ensure the ABD addresses all requirements. The updated ABD is included in version 1.2 of the SSP, dated 11/13/2025. | 2025-11-13 00:00:00 |
| Mandatory | Mandatory | Mandatory | Mandatory | Situational (enter when actions are complete) |

## Record of Changes

| Date | Description | Version | Author |
| --- | --- | --- | --- |
| 2023-08-30 00:00:00 | Updated to align with FedRAMP branding and minor editorial changes. | 2.0 | FedRAMP PMO |
| 2024-03-29 00:00:00 | Added Tab for Configuration Findings. Added Column in 'Open POA&M' tab for Service level information | 2.1 | FedRAMP PMO |
| 2025-11-17 00:00:00 | Added Instructions Tab, consolidated reporting fields, and simplified input requirements. | 3.0 | FedRAMP PMO |

