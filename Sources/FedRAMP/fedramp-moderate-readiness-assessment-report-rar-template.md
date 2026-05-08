---
title: "FedRAMP-Moderate-Readiness-Assessment-Report-(RAR)-Template"
type: reference
framework: fedramp
source_format: converted
created: 2026-04-05
tags:
  - fedramp
  - template
---

# FedRAMP-Moderate-Readiness-Assessment-Report-(RAR)-Template

> Source: `FedRAMP-Moderate-Readiness-Assessment-Report-(RAR)-Template.docx`

FedRAMP® Moderate Readiness Assessment Report (RAR) Template

for <Insert CSP Name>

<Insert CSO Name>

<Version X.X>

<MM/DD/YYYY>

Company Sensitive and Proprietary
For Authorized Use Only

## THIRD PARTY ASSESSMENT ORGANIZATION (3PAO) ATTESTATION

## READINESS ASSESSMENT INFORMATION

Table 0-1. System Information

*Fully Operational means that the architectural components of the system are all in place and operating as required, and the technical controls are implemented. However, for a RAR, the documentation may be partially developed.

TEMPLATE REVISION HISTORY

TABLE OF CONTENTS

## Introduction

## Purpose

This report and its underlying assessment are intended to enable FedRAMP to reach a FedRAMP Ready decision for a specific CSP’s offering, based on organizational processes and the security capabilities of the Moderate-impact information system. FedRAMP grants a FedRAMP Ready designation when the information in this report indicates the CSP is likely to achieve a FedRAMP authorization for the offering.

It is important that the overall alignment with the National Institute of Standards and Technology (NIST) definition of cloud computing according to NIST SP 800-145 are met (NOTE: This includes the requirement for the CSP to have a self-service portal). This report will also identify notable strengths and weaknesses; ability to consistently maintain a clearly defined system boundary; ability to accurately describe intra and inter-system user and sensitive metadata data flow; risks associated with interconnections used to transmit federal data/metadata or sensitive system data/metadata; and risks associated with the use of external systems and services that are not FedRAMP Authorized.

In addition, this report will clearly define customer responsibilities and outline unique or alternative implementations. It will highlight overall maturity level relative to the system type, size and complexity along with overall operational maturity relative to how long the system and required security controls have been in operation.

## Outcomes

A 3PAO should only submit this report to FedRAMP if it determines the CSP’s system is fully ready to pursue, and likely to achieve, a FedRAMP authorization at the Moderate security impact level within one (1) year from the date of submission.

Submission of this report by the 3PAO does not guarantee a FedRAMP Ready designation, nor does it guarantee a FedRAMP authorization.

During the RAR review and approval process, the FedRAMP PMO may require the CSP to perform additional actions to demonstrate readiness, which would require validation by the 3PAO. Concurrently, the FedRAMP PMO may require updates to provide clarity.

3PAOs conducting Readiness Assessments should advise CSPs that additional changes may be required after the RAR is submitted to the FedRAMP PMO for review and approval.

The FedRAMP Director will make a determination, based on the RAR, if the CSO is suitable for FedRAMP authorization.

## FedRAMP Approach and Use of This Document

The RAR identifies clear and objective security capability requirements, where possible, while also allowing for the presentation of subjective information. The clear and objective requirements enable the 3PAO to concisely identify whether a CSP is achieving the most important FedRAMP Moderate baseline requirements. The combination of objective requirements and subjective information enables FedRAMP to render a readiness decision based on a more complete understanding of the CSP’s current security capabilities.

Section 4, Capability Readiness, is organized into three sections:

Section 4.1, Federal Mandates, identifies a small set of the federal mandates a CSP must satisfy. FedRAMP will not waive any of these requirements.

Section 4.2, FedRAMP Requirements, identifies an excerpt of the most compelling requirements from the NIST Special Publication (SP) 800 document series and FedRAMP guidance. A CSP is unlikely to achieve a FedRAMP authorization if any of these requirements are not met.

Section 4.3, Additional Capability Information, identifies additional information, not tied to specific requirements, that has typically reflected strongly on a CSP’s ability to achieve a FedRAMP authorization.

## General Guidance and Instructions

## Embedded Document Guidance

This document contains embedded text intended to instruct the 3PAO on how to complete each section. These instructions ensure FedRAMP receives all the information necessary to render a FedRAMP Ready decision.

## Additional Instructions to 3PAOs

3PAOs must adhere to the following instructions when preparing the RAR:

Do NOT submit the completed Moderate RAR without first coordinating with the FedRAMP PMO via info@fedramp.gov.

On the Title Page, enter the CSP name, CSO name, version number, and date of this RAR submission. If this is a re-submission, be sure to increment the version number and adjust the date.

The RAR must provide:

An overview of the system;

A subjective summary of the CSP’s overall readiness, including rationale such as notable strengths and other areas for consideration;

An assessment of the CSP’s ability to meet the federal mandates identified in Section 4.1, the FedRAMP requirements identified in Section 4.2, and additional capabilities identified in Section 4.3;

A clear description and diagram of system components and services, within the authorization boundary, as well as all connections to external systems and services that are outside of the authorization boundary;

A clear Data Flow diagram(s) and description(s) that accounts for all intra and inter-boundary flow of federal information, data, and metadata. This includes all flows through the authorization boundary and to/from external systems and services and all flows between systems within the authorization boundary; and

The 3PAO’s attestation regarding the CSP’s readiness to meet FedRAMP Moderate baseline requirements within one (1) year from the date of submission.

FedRAMP will not consider a CSP for a FedRAMP Ready designation unless all the requirements in Section 4.1, Federal Mandates, are met. 3PAOs should not recommend FedRAMP Ready status for CSPs that have not met all federal mandates (Note: Meeting these requirements does not guarantee a FedRAMP Ready designation).

3PAOs must assess the system's technical, management, and operational capabilities using a combination of methods, including interview, observation, demonstration, examination, and onsite visits (e.g., in-person interviews and data center visits, as needed). 3PAOs may use CSP-provided diagrams, but must validate the diagrams as though the 3PAO created them. 3PAOs must not conduct this Readiness Assessment exclusively by reviewing a CSP's written documentation and performing interviews alone. Active validation of all information provided within this report is required.

3PAOs must complete all sections and address all elements of each question. 3PAOs must also describe observations of any missing elements (e.g., if the CSP fails to meet all of the question elements). If a capability is fully inherited, answer "yes" and write "fully inherited" in the column provided for the capability description.

Control references are provided with each of the questions in Section 4.2, FedRAMP Requirements. These references are provided to help the 3PAO understand the basis for each question; however, the 3PAO is expected to consider all relevant FedRAMP security controls and capabilities when assessing the CSP's capabilities.

FedRAMP believes a typical level of effort for conducting a Readiness Assessment for mid-size, straightforward systems is between two (2) and four (4) weeks, with the first half focused on information gathering and the second half focused on analysis and report development.

## System Information

## Authorization Boundary

An authorization boundary provides a diagrammatic illustration of a CSO’s internal services, components, and other devices, along with connections to external services and systems. Please note that external services include external cloud services that are not FedRAMP Authorized, corporate shared services, and the external entities to which the system must connect to receive updates for products installed within the system boundary.

An authorization boundary accounts for all federal information, data, and metadata that flow through a CSO. If the CSO has strong configuration management and change management built into the system development life cycle, the development environment can be outside the CSO boundary. This means that there is a 3PAO validated, reproducible and effective way to make service changes without impacting the production environment.

NOTE: The diagram must include a predominant border drawn around all system components and services included in the authorization boundary. The diagram must be easy to read and understand. If necessary, adjust the page orientation to landscape and/or use multiple diagrams to provide the best representation of the authorization boundary. If opting to use multiple diagrams, they must clearly correspond from one to another. We suggest a “parent and child” diagram structure to ensure clarity. Or the CSP may choose to create a larger area by using a larger layout size page and embedding this in the RAR. The embedded document must be easy to read and have a high resolution. The 3PAO must validate the content of the diagrams and narratives for accuracy for inclusion in the RAR and must make it clear in the RAR what (if any) content is CSP-supplied.

## Leveraged FedRAMP Authorizations

Table 3-1. Leveraged FedRAMP Authorizations

## External & Corporate Systems and Services

CSPs often establish connections to external systems and services to (i) exchange data and information or (ii) augment system functionality and operational support services. This includes corporate systems and services that are not part of the authorization boundary. FedRAMP does not consider cloud systems and services as corporate systems and services. This means that if a corporate system and/or service is a cloud system within the corporate environment, that cloud system is considered an external service and must be designated as such.

NOTE: FedRAMP defines a connection as any communication path used to push, pull, or exchange data and/or information, including application programming interfaces (APIs). For example, the collection of traffic information via a geo-location service API set or integration with a service via its API set are both considered connections. 3PAOs must identify all API sets in Section 3.4, Table 3-3.

Table 3-2. External Systems and Services

## APIs

CSPs leverage public or custom APIs for all types of categories in computing. CSPs may use publicly available API sets provided by vendors or may develop custom APIs. APIs are categorized by functions such as backup and recover or communications.

If possible, 3PAOs should request the WSDL file for SOAP APIs and OpenAPI spec for REST APIs.

Table 3-3. APIs

## Trusted Internet Connection (TIC) [SC-7(3)]

## Data Flow Diagrams

NOTE: The data flow diagram must be easily attributable to the ABD illustrated in Section 3-1. The data flow diagram must be easy to read (high resolution) and understand. The encryption and directional arrows for the data flows and stores must be on the diagram or represented via the legend. If necessary, adjust the page orientation to landscape and/or use multiple diagrams to provide the best representation of the data flows. If the diagram is complex, you may create a high-resolution diagram on a larger page size and embed the item in this section.

## Separation Measures [AC-2, AC-4, SC-7]

## Capability Readiness

## Federal Mandates

This section identifies federal requirements applicable to all FedRAMP Authorized CSOs. All requirements in this section must be met. Some of these topics are also covered in greater detail in Section 4.2, FedRAMP Requirements, below.

Table 4-1. Federal Mandates

## FedRAMP Requirements

This section identifies additional FedRAMP Readiness requirements. All requirements in this section must be met; however, alternative implementations and non-applicability justifications may be considered on a limited basis.

## Approved Cryptographic Modules [SC-13]

Table 4-2. Cryptographic Modules

## Transport Layer Security [NIST SP 800-52, most current revision]

Table 4-3. Transport Layer Security

## Identification, Authentication, and Access Control

Table 4-4. Identification, Authentication, and Access Control

## Audit, Alerting, Malware, and Incident Response

Table 4-5. Audit, Alerting, Malware, and Incident Response

## Contingency Planning and Disaster Recovery

Table 4-6. Contingency Planning and Disaster Recovery

## Configuration and Risk Management

Table 4-7. Configuration and Risk Management

## Data Center Security

Table 4-8. Data Center Security

## Policies, Procedures, and Training

Table 4-9. Missing Policy and Procedure Elements

Table 4-10. Security Awareness Training

## Additional Capability Information

FedRAMP will evaluate the responses in this section on a case-by-case basis relative to a FedRAMP Ready designation decision.

## Change Management Maturity

While the following change management capabilities are not required, they indicate a more mature change management capability and may influence a FedRAMP Readiness decision, especially for larger systems. Please note that once a CSO has been designated FedRAMP Ready, architectural, boundary or other significant changes may invalidate the CSO's FedRAMP Ready designation (a FedRAMP Ready designation and corresponding RAR are valid for one year).

Table 4-11. Change Management

## Continuous Monitoring (ConMon) Capabilities

Table 4-12. Continuous Monitoring Capabilities

Table 4-13. Continuous Monitoring Capabilities – Additional Details

## Status of System Security Plan (SSP)

Table 4-14. Maturity of the System Security Plan

Table 4-15. Controls Designated “Not Applicable”

Table 4-16. Controls with an Alternative Implementation

| Instructions: |
| --- |
| A FedRAMP recognized 3PAO must attest to the readiness of the CSP’s system. To be considered FedRAMP Ready, the CSP must meet all the requirements in Section 4.1, Federal Mandates. In addition, the 3PAO must assess the CSP’s ability to meet the requirements in Section 4.2, FedRAMP Requirements. The  |

| Instructions: |
| --- |
| Provide and validate the information below. This RAR template is intended for systems categorized at the Moderate security impact level, in accordance with the FIPS Publication 199 security categorization. <br> Delete instruction text after completion. |

| System Information | System Information |
| --- | --- |
| CSP Name: |  |
| CSO Name (and Abbreviation): |  |
| FedRAMP Unique Identifier: |  |
| Service Model: | (IaaS, PaaS, SaaS) |
| FIPS PUB 199 System Security Level: (Moderate) |  |
| Digital Identity Determination Level: | (IAL2/FAL2/AAL2, IAL3/FAL3/AAL3) |
| Fully Operational* as of: | Enter the date the system became fully operational. |
| Number of Customers (US Federal/Others): | Enter # of US Federal customers / # of other customers. |
| Deployment Model: | Public Cloud, Government-Only Cloud, Hybrid Cloud |
| System Functionality: | Briefly describe the functionality of the system and service being provided. |

| Date | Description | Template Version | Author |
| --- | --- | --- | --- |
| 04/26/2017 | Initial release version | 1.0 | FedRAMP PMO |
| 08/28/2018 | Added clarifications throughout. Added requirements that provide better visibility into system interconnections and external services. | 1.1 | FedRAMP PMO |
| 02/13/2019 | Verbiage added to the top of the document and to the 3PAO attestation stating the expiration date of the report. | 1.2 | FedRAMP PMO |
| 07/31/2020 | Updated to include Locality checks for data centers | 1.3 | FedRAMP PMO |
| 04/1/2021 | Updated Table 4-3 Transport Layer Security to include TLS 1.3 | 1.4 | FedRAMP PMO |
| 01/4/2022 | Added clarifications throughout. Updated to clarify requirements that apply to CSPs pursuing a JAB P-ATO but do not apply to an Agency ATO. Rearranged sections to reduce duplicate information and improve document flow. Updated instructional notes. | 1.5 | FedRAMP PMO |
| 06/30/2023 | Updated to reflect FedRAMP Rev. 5 baselines. Added 3PAO validation of DNSSEC responses. | 2.0 | FedRAMP PMO |
| 5/31/2024 | Rewrote the instructions for Section 4.2.1 - Approved Cryptographic Modules [SC-13]. Removed an outdated statement, related to HTTPS Strict Transport Security (HSTS), in Section 4.2.2 - Transport Layer Security. Removed outdated JAB references throughout the document. | 2.1 | FedRAMP |

| Instructions: |
| --- |
| Before delivering the final version of the RAR, be sure to delete all italicized instructional text. <br> Delete instruction text after completion. |

| Instructions: |
| --- |
| The 3PAO must perform full authorization boundary validation for the RAR, ensure nothing is missing from the CSP-identified boundary, and ensure all included items are currently present and are part of the system inventory. To achieve this, the 3PAO must perform activities including, but not limited |

| Instructions: |
| --- |
| Insert 3PAO-validated network and architecture diagram(s) and provide a written description of the authorization boundary. The 3PAO must ensure the diagram: <br> Provides an easy to read, high resolution diagram that includes a legend. <br> It is acceptable to provide the ABD as a separate attachment. <br> Include |

| Instructions: |
| --- |
| If this Moderate system leverages another FedRAMP Authorized CSO (e.g., an IaaS that provides compute, network, and storage; or a SaaS that provides operational support services), provide the relevant details in Table 3-1 below. Please note: <br> The CSO must be listed on the FedRAMP Marketplace with a s |

| # | CSP and CSO Name | CSO Service | Authorization Type & FedRAMP Package ID | Nature of Agreement | Still Supported? Y or N |
| --- | --- | --- | --- | --- | --- |
| 1 | Provide the names of the leveraged CSP and CSO (i.e., CSO name). | Describe the features and services/subservices provided by the CSO. | Provide the CSO’s FedRAMP Package ID. |  |  |

| Instructions: |
| --- |
| 3PAOs must identify all connections to external systems and services in Table 3-2. The 3PAO should not include the leveraged services listed in Table 3-1. 3PAOs should not rely solely on CSP-provided boundary diagrams or interviews, but should use a combination of methods, such as analyzing data flo |

| # | System/Service Name | Interconnection Details | Nature of Agreement | Still Supported? Y or N | Data Types | Data Categorization | Authorized Users & Authentication Method | Compliance Programs |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Provide the name of the system or service. Include the vendor name, if different from the system or service name. | Provide connectivity details. |  |  | List the CSO data types transmitted to, stored, or processed by the system/service, including federal data/metadata and system data/metadata. | Identify the security impact level of the data (Low, Moderate, or High) in accordance with FIPS 199. | List the user roles (e.g., SecOps Engineers) authorized to access the service, and provide the authentication method. | List any certifications for this service (e.g., PCI SOC 2, CSA STAR Level 2), and provide the certification date. |
|  | Description: Describe the purpose of the external system/service and the hosting environment (e.g., corporate network, IaaS, or self-hosted). <br> Risk/Impact/Mitigation: Describe potential risks introduced by the external system/service and impact to the CSO or federal customer data if the confidentiali | Description: Describe the purpose of the external system/service and the hosting environment (e.g., corporate network, IaaS, or self-hosted). <br> Risk/Impact/Mitigation: Describe potential risks introduced by the external system/service and impact to the CSO or federal customer data if the confidentiali | Description: Describe the purpose of the external system/service and the hosting environment (e.g., corporate network, IaaS, or self-hosted). <br> Risk/Impact/Mitigation: Describe potential risks introduced by the external system/service and impact to the CSO or federal customer data if the confidentiali | Description: Describe the purpose of the external system/service and the hosting environment (e.g., corporate network, IaaS, or self-hosted). <br> Risk/Impact/Mitigation: Describe potential risks introduced by the external system/service and impact to the CSO or federal customer data if the confidentiali | Description: Describe the purpose of the external system/service and the hosting environment (e.g., corporate network, IaaS, or self-hosted). <br> Risk/Impact/Mitigation: Describe potential risks introduced by the external system/service and impact to the CSO or federal customer data if the confidentiali | Description: Describe the purpose of the external system/service and the hosting environment (e.g., corporate network, IaaS, or self-hosted). <br> Risk/Impact/Mitigation: Describe potential risks introduced by the external system/service and impact to the CSO or federal customer data if the confidentiali | Description: Describe the purpose of the external system/service and the hosting environment (e.g., corporate network, IaaS, or self-hosted). <br> Risk/Impact/Mitigation: Describe potential risks introduced by the external system/service and impact to the CSO or federal customer data if the confidentiali | Description: Describe the purpose of the external system/service and the hosting environment (e.g., corporate network, IaaS, or self-hosted). <br> Risk/Impact/Mitigation: Describe potential risks introduced by the external system/service and impact to the CSO or federal customer data if the confidentiali |
| 2 | Service Name | Interconnection Details |  |  | Data Types | Data Categorization | Authorized Users & Authentication Method | Compliance Programs |
|  | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: |
| 3 | Service Name | Interconnection Details |  |  | Data Types | Data Categorization | Authorized Users & Authentication Method | Compliance Programs |
|  | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: |

| Instructions: |
| --- |
| Examples of public API sets are provided in Table 3-3 and the URL below. 3PAOs must identify all public or custom CSP-leveraged API sets that allow data to flow to and from the system. Remove the examples and use the blank rows in Table 3-3 to enter the API sets. Add new rows as needed. Optionally,  |

| API/CLI | Protocol | Authentication | Encryption Algorithm(s) | Data Types | Data Categorization | Description |
| --- | --- | --- | --- | --- | --- | --- |
| CSO A  API | TCP/NN | API Key | Encryption algorithms allowed | List the CSO data types transmitted to, stored, or processed by the system/service, including federal data/metadata and system data/metadata. | Identify the security impact level of the data (Low, Moderate, or High) in accordance with FIPS 199. | Build maps which can include routes and traffic information. |
| CSO B API | TCP/NN | API Key, OAuth 2 |  |  |  | Run web apps on CSO B infrastructure |
| CSO C API | TCP/NN |  |  |  |  | Allows an application to connect CSO C service or embed parts of CSO C user experience |
| CSO D CLI | TCP/NN |  |  |  |  | Main commands for building and designing a data center Layer 2 and Layer 3 infrastructure |
| CSO E API | TCP/NN |  |  |  |  | CIM API provides a Common Information Model (CIM) interface for building management applications |

| Instructions: |
| --- |
| Describe the CSP’s ability to support an agency customer’s TIC requirements.  <br> Delete instruction text after completion. |

| Instructions: |
| --- |
| Insert 3PAO-validated data flow diagram(s) and provide a written description of the data flows. The diagram(s) must address all components reflected in the ABD. At a minimum, SSPs should include diagrams for the following logical data flows: <br> Customer user and customer admin authentication, including |

| Instructions: |
| --- |
| Assess and describe the strength of the physical and/or logical separation measures in place to provide segmentation and isolation of tenants, administration, and operations; addressing user-to-system; admin-to-system; and system-to-system relationships. There are additional capabilities required fo |

| Instructions: |
| --- |
| Only answer “Yes” if the requirement is fully and strictly met. The 3PAO must answer “No” if an alternative implementation is in place. For the FIPS-validated encryption, FedRAMP expects all moderate and above federal data and metadata to be encrypted internally, externally, and traversing the servi |

| # | Compliance Topic | Fully Compliant? | Fully Compliant? |
| --- | --- | --- | --- |
| # | Compliance Topic | Yes | No |
| 1 | Are FIPS 140-validated cryptographic modules (IAW SC-13) consistently used everywhere cryptography is required? This includes all SC-8, SC-8(1), and SC-28 required encryption. |  |  |
| 2 | Does the system fully support user authentication via agency Common Access Card (CAC) or Personal Identity Verification (PIV) credentials? |  |  |
| 3 | Is the system operating at Digital Identity Level 2 or higher? |  |  |

| 5 | Does the CSP and system meet federal records management requirements, including the ability to support record holds, National Archives and Records Administration (NARA) requirements, and Freedom of Information Act (FOIA) requirements? [https://www.archives.gov/records-mgmt/grs; PL 104-231, 5 USC 552] |  |  |
| --- | --- | --- | --- |
| 6 | Does the system’s external DNS solution support DNS Security (DNSSEC) to provide origin authentication and integrity verification assurances? This applies to the controls SC-20, SC-21, and SC-22 in the SSP. |  |  |

| Instructions: |
| --- |
| The RAR requires that the 3PAO validates that FIPS-validated encryption is used for all data flows and stores, internally, externally, and traversing the system boundary. Therefore, the 3PAO must ensure active FIPS 140-2 or 140-3 Validated cryptographic modules are used. FIPS 140-2 or 140-3 Complian |

| # | Cryptographic Module Type | FIPS 140-validated? | FIPS 140-validated? | Describe Any Alternative Implementations <br> (If Applicable) | Describe Missing Elements or N/A Justification |
| --- | --- | --- | --- | --- | --- |
| # | Cryptographic Module Type | Yes | No | Describe Any Alternative Implementations <br> (If Applicable) | Describe Missing Elements or N/A Justification |
| 1 | Data at Rest [SC-28] |  |  |  |  |
| 2 | Transmission [SC-8 (1), SC-12, SC-13] |  |  |  |  |
| 3 | Remote Access [AC-17 (2)] |  |  |  |  |
| 4 | Authentication [IA-5 (1)] |  |  |  |  |

| Instructions: |
| --- |
| The 3PAO must identify all protocols in use for both internal and external communications. The 3PAO may add rows to the table if appropriate but must not remove the original rows.  <br> Encryption protection of data-at-rest through encryption includes databases; the responsibility for this depends on the |

| # | The Cryptographic Module Type | Protocol In Use? | Protocol In Use? | If “yes,” please describe use for both internal and external communications |
| --- | --- | --- | --- | --- |
| # | The Cryptographic Module Type | Yes | No | If “yes,” please describe use for both internal and external communications |
| 1 | SSL (Non-Compliant) |  |  | 1 |
| 2 | TLS 1.0 (Non-Compliant) |  |  | 2 |
| 3 | TLS 1.1 (Non-Compliant) |  |  | 3 |
| 4 | TLS 1.2 (Compliant) |  |  | 4 |
| 5 | TLS 1.3 (Compliant) |  |  | 5 |

| Instructions: |
| --- |
| Only answer “Yes” if the answer is consistently “Yes.” For partially implemented areas, answer “No” and describe what is missing to achieve a “Yes” answer. If inherited, please indicate partial or full inheritance in the “Describe Capability” column. Any non-inherited capabilities must be described. |

| # | Question | Yes | No | Describe capability, supporting evidence, and any missing elements |
| --- | --- | --- | --- | --- |
| 1 | Does the system support federal user authentication via CAC/PIV credentials? [IA-8(1)] |  |  |  |
| 2 | Does the system uniquely identify and authorize organizational users (or processes acting on behalf of organizational users) in a manner that cannot be repudiated and which sufficiently reduces the risk of impersonation? [IA-2, IA-4, IA-4(4)] |  |  |  |
| 3 | Does the system require MFA for administrative accounts and functions? [IA-2, IA-2(1)] |  |  |  |
| 4 | Does the system fully comply with Digital Identity Level 2 (AAL2, IAL2, FAL2) or higher? [NIST SP 800-63] |  |  | State the Digital Identity Level and provide sufficient details demonstrating that the system complies with this level, consistent with NIST SP 800-63 and FedRAMP guidance. |
| 5 | Does the system employ automated mechanisms to support account management? [AC-2(1)] |  |  |  |
| 6 | Does the system restrict non-authorized personnel’s access to resources? [AC-6(2)] |  |  |  |
| 7 | Does the system restrict non-privileged users from performing privileged functions? [AC-6(10)] |  |  |  |
| 8 | Does the system ensure secure separation of customer data? [SC-4] |  |  | The capability description is not required here, but must be included in Section 3.7, Separation Measures. |
| 9 | Does the system ensure secure separation of customer processing environments? [SC-2] |  |  | The capability description is not required here, but must be included in Section 3.7, Separation Measures. |
| 10 | Does the system restrict access of administrative personnel in a way that limits the capability of individuals to compromise the security of the information system? [AC-2(7)] |  |  |  |

| Instructions: |
| --- |
| Only answer “Yes” if the answer is consistently “Yes.” For partially implemented areas, answer “No” and describe what is missing to achieve a “Yes” answer. If inherited, please indicate partial or full inheritance in the “Describe Capability” column. Any non-inherited capabilities must be described. |

| # | Question | Yes | No | Describe capability, supporting evidence, and any missing elements |
| --- | --- | --- | --- | --- |
| 1 | Does the system have the capability to detect, contain, and eradicate malicious software? [SI-3, MA-3 (2)] |  |  |  |
| 2 | Does the system protect audit information from unauthorized access, modification, and deletion? [AU-7, AU-9] |  |  |  |
| 3 | Does the CSP have the capability to detect unauthorized or malicious use of the system, including insider threat and external intrusions? [SI-4, SI-4 (4), SI-7, SI-7 (7)] |  |  |  |
| 4 | Does the CSP have an Incident Response Plan and a fully developed Incident Response Test Plan? [IR-3, IR-8] |  |  |  |
| 5 | Does the CSP have a plan and capability to perform security code analysis and assess code for security flaws, as well as identify, track, and remediate security flaws? [SA-11, SA-11 (1)] |  |  | If the system contains no custom software development, do not answer “Yes” or “No.” Instead, state “NO CUSTOM CODE” here. |
| 6 | Does the CSP implement automated mechanisms for incident handling and reporting? [IR-4 (1), IR-6 (1)] |  |  |  |
| 7 | Does the CSP retain online audit records for at least 90 days to provide support for after-the-fact investigations of security incidents and offline for at least one year to meet regulatory and organizational information retention requirements? [AU-7, AU-7 (1), AU-11] |  |  |  |
| 8 | Does the CSP have the capability to notify customers and regulators of confirmed incidents in a timeframe consistent with all legal, regulatory, or contractual obligations? [FedRAMP Incident Communications Procedure] |  |  |  |
| 9 | Has the CSP architected the system to allow the external DNS server to reply with valid DNSSEC responses [SC-20]? |  |  |  |
| 10 | Has the CSP ensured that the recursive server is within a FedRAMP Authorized boundary [SC-21]? |  |  |  |
| 11 | Has the CSP enabled DNSSEC requests, for domains outside the boundary, so that DNS calls maintain DNSSEC authentication and integrity [SC-20, SC-21]? |  |  |  |

| Instructions: |
| --- |
| Only answer “Yes” if the answer is consistently “Yes.” For partially implemented areas, answer “No” and describe what is missing to achieve a “Yes” answer. If inherited, please indicate partial or full inheritance in the “Describe Capability” column. Any non-inherited capabilities must be described. |

| # | Question | Yes | No | Describe capability, supporting evidence, and any missing elements |
| --- | --- | --- | --- | --- |
| 1 | Does the CSP have the capability to recover the system to a known and functional state following an outage, breach, DoS attack, or disaster? [CP-2, CP-2 (3), CP-9, CP-10] |  |  |  |
| 2 | Does the CSP have a Contingency Plan and a fully developed Contingency Plan Test Plan in accordance with NIST Special Publication 800-34? [CP-2, CP-8] |  |  |  |
| 3 | Does the system have alternate storage and processing facilities? [CP-6, CP-7] |  |  |  |
| 4 | Does the system have primary and alternate telecommunications services from different providers? [CP-8, CP-8 (2)] |  |  |  |
| 5 | Does the system have backup power generation or other redundancy? [PE-11] |  |  |  |
| 6 | Does the CSP have SLAs in place with all telecommunications providers? [CP-8 (1)] |  |  |  |

| Instructions: |
| --- |
| Only answer “Yes” if the answer is consistently “Yes.” For partially implemented areas, answer “No” and describe what is missing to achieve a “Yes” answer. If inherited, please indicate partial or full inheritance in the “Describe Capability” column. Any non-inherited capabilities must be described. |

| # | Question | Yes | No | Describe capability, supporting evidence, and any missing elements |
| --- | --- | --- | --- | --- |
| 1 | Does the CSP maintain a current, complete, and accurate baseline configuration of the information system? [CM-2] |  |  |  |
| 2 | Does the CSP maintain a current, complete, and accurate inventory of the information system software, hardware, and network components? [CM-8] |  |  |  |
| 3 | Does the CSP have a configuration management plan? [CM-9, CM-11] |  |  |  |
| 4 | Does the CSP follow a formal change control process that includes a security impact assessment? [CM-3, CM-4] |  |  |  |
| 5 | Does the CSP employ automated mechanisms to detect inventory and configuration changes? [CM-2(2), CM-6(1), CM-8(3)] |  |  |  |
| 6 | Does the CSP prevent unauthorized changes to the system? [CM-5, CM-5(1), CM-5(5)] |  |  |  |
| 7 | Does the CSP establish configuration settings for products employed that reflect the most restrictive mode consistent with operational requirements? [CM-6] |  |  | If “yes,” describe whether the configuration settings are based on Center for Internet Security (CIS) Benchmarks or United States Government Configuration Baseline (USGCB), or “most restrictive consistent with operational requirements.” |
| 8 | Does the CSP ensure that checklists for configuration settings are Security Content Automation Protocol (SCAP)-validated or SCAP-compatible (if validated checklists are not available)? [CM-6] |  |  |  |

| Instructions: |
| --- |
| For the following questions, 3PAOs may use Table 4-12 (Continuous Monitoring Capabilities – Additional Details) to enter the capability descriptions, supporting evidence and missing elements. |

| 9 | Does the CSP perform authenticated operating system/ infrastructure, web, database, and container vulnerability scans at least monthly, as applicable? [RA-5, RA-5(5), SI-2(2)] |  |  | Describe how the 3PAO validated that vulnerability scans were fully authenticated. |
| --- | --- | --- | --- | --- |
| 10 | Does the CSP demonstrate the capability to remediate High vulnerabilities within 30 days, Moderate vulnerabilities within 90 days, and Low vulnerabilities within 180 days? [RA-5, FedRAMP Continuous Monitoring Guide] |  |  | Describe how the 3PAO validated that the CSP remediates High vulnerabilities within 30 days and Moderate vulnerabilities within 90 days. |

| Instructions: |
| --- |
| Only answer “Yes” if the answer is consistently “Yes.” For partially implemented areas, answer “No” and describe what is missing to achieve a “Yes” answer. If inherited, please indicate partial or full inheritance in the “Describe Capability” column. Any non-inherited capabilities must be described. |

| # | Question | Yes | No | Describe capability, supporting evidence, and any missing elements |
| --- | --- | --- | --- | --- |
| 1 | Does the CSP restrict physical system access to only authorized personnel? [PE-2 through PE-6 (except PE-3(1)), PE-8] |  |  |  |
| 2 | Does the CSP monitor and log physical access to the information system, and maintain access records? [PE-6, PE-8] |  |  |  |
| 3 | Does the CSP monitor and respond to physical intrusion alarms and surveillance equipment? [PE-6 (1)] |  |  |  |

| Instructions: |
| --- |
| Identify missing policies and procedures. For any family with a policy or procedure gap, please describe the gap below. <br> Delete instruction text after completion. |

| Missing Policy and Procedure Elements |
| --- |

| Instructions: |
| --- |
| The 3PAO must answer the question below. <br> Delete instruction text after completion. |

| Question | Yes | No | Describe capability, supporting evidence, and any missing elements |
| --- | --- | --- | --- |
| Does the CSP train personnel on security awareness and role-based security responsibilities? |  |  |  |

| Instructions: |
| --- |
| The 3PAO must answer the questions below. <br> Delete instruction text after completion. |

| # | Question | Yes | No | If “No,” please describe how this function is accomplished. |
| --- | --- | --- | --- | --- |
| 1 | Does the CSP’s change management capability include a fully functioning Change Control Board (CCB)? |  |  |  |
| 2 | Does the CSP have and use development and/or test environments to verify changes before implementing them in the production environment? |  |  |  |

| Instructions: |
| --- |
| In the tables below, please describe the current state of the CSP’s ConMon capabilities, as well as the length of time the CSP has been performing ConMon for this system.  <br> Delete instruction text after completion. |

| # | Question | Yes | No | Describe capability, supporting evidence, and any missing elements |
| --- | --- | --- | --- | --- |
| 1 | Does the CSP have a lifecycle management plan that ensures products are updated before they reach the end of their vendor support period? |  |  |  |
| 2 | Does the CSP have the ability to scan all hosts in the inventory? |  |  |  |
| 3 | Does the CSP have the ability to provide scan files in a structured data format, such as CSV, XML, or .nessus files? |  |  |  |
| 4 | Is the CSP properly maintaining their Plan of Action and Milestones (POA&M), including timely, accurate, and complete information entries for new scan findings, vendor check-ins, and closure of POA&M items? |  |  |  |

| Instructions: |
| --- |
| In the table below, provide any additional details the 3PAO believes to be relevant to FedRAMP’s understanding of the CSP’s continuous monitoring capabilities. If the 3PAO has no additional details, please state “None.” <br> Delete instruction text after completion. |

| Continuous Monitoring Capabilities – Additional Details |
| --- |

| Instructions: |
| --- |
| In the table below, explicitly state whether the SSP is fully developed, partially developed, or non-existent. Identify any sections that the CSP has not yet developed. If the maturity of the SSP is low, or there is a high percentage that is not complete, please describe any risks the 3PAO believes  |

| Maturity of the System Security Plan |
| --- |

| Instructions: |
| --- |
| In the table below, state the number of controls identified as “Not Applicable” in the SSP. List the control identifier for each, and indicate whether a justification for each has been provided in the SSP control statement. The 3PAO should indicate whether they agree that the control is “Not Applica |

| <x> Controls are Designated “Not Applicable” |
| --- |

| Instructions: |
| --- |
| In the table below, state the number of controls with an alternative implementation. List the control identifier for each. The 3PAO should indicate whether they agree that the alternative implementation meets the control requirement and why. <br> Delete instruction text after completion. |

| <x> Controls have an Alternative Implementation |
| --- |

