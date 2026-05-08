---
title: "FedRAMP-High-Moderate-Low-LI-SaaS-Baseline-System-Security-Plan-(SSP)"
type: reference
framework: fedramp
source_format: converted
created: 2026-04-05
tags:
  - fedramp
  - template
---

# FedRAMP-High-Moderate-Low-LI-SaaS-Baseline-System-Security-Plan-(SSP)

> Source: `FedRAMP-High-Moderate-Low-LI-SaaS-Baseline-System-Security-Plan-(SSP).docx`

TEMPLATE REVISION HISTORY

How to contact us

For questions about FedRAMP, or for questions about this document including how to use it, contact info@FedRAMP.gov.

For more information about FedRAMP, see www.FedRAMP.gov.

SYSTEM SECURITY PLAN

### Prepared by

### Prepared for

### Document Revision History

TABLE OF CONTENTS

1	Introduction	8

2	Purpose	8

3	System Information	8

4	System Owner	10

5	Assignment of Security Responsibility	11

6	Leveraged FedRAMP-Authorized Services	12

7	External Systems and Services Not Having FedRAMP Authorization	15

8	Illustrated Architecture and Narratives	19

8.1	Illustrated Architecture	19

8.2	Narrative	22

9	Services, Ports, and Protocols	24

10	Cryptographic Modules Implemented for Data At Rest (DAR) and Data In Transit (DIT)	27

11	Separation of Duties	29

12	SSP Appendices List	31

Appendix A <Insert CSO Name> FedRAMP Security Controls	33

Appendix B <Insert CSO Name> Related Acronyms	35

Appendix C <Insert CSO Name> Information Security Policies and Procedures	36

Appendix D <Insert CSO Name> User Guide	37

Appendix E <Insert CSO Name> Digital Identity Worksheet	37

Appendix F <Insert CSO Name> Rules of Behavior (RoB)	40

Appendix G <Insert CSO Name> Information System Contingency Plan (ISCP)	40

Appendix H <Insert CSO Name> Configuration Management Plan (CMP)	41

Appendix I <Insert CSO Name> Incident Response Plan (IRP)	42

Appendix J <Insert CSO Name> Control Implementation Summary (CIS) and Customer Responsibilities Matrix (CRM) Workbook	43

Appendix K <Insert CSO Name> Federal Information Processing Standard (FIPS) 199 Categorization	44

Appendix L <Insert CSO Name>-Specific Laws and Regulations	47

Appendix M <Insert CSO Name> Integrated Inventory Workbook (IIW)	47

Appendix N <Insert CSO Name> Continuous Monitoring Plan	48

Appendix O <Insert CSO Name> POA&M	49

Appendix P <Insert CSO Name> Supply Chain Risk Management Plan (SCRMP)	49

Appendix Q <Insert CSO Name> Cryptographic Modules Table	50

SYSTEM SECURITY PLAN APPROVALS

Cloud Service Provider (CSP) Signatures

By signing this System Security Plan (SSP), we agree that it is complete and is the current version to be used for the security assessment. The FedRAMP-specific Laws and Regulations Document, as of the date of this SSP, is <Insert Version X.X>, dated <Insert MM/DD/YYYY>, and is posted on the FedRAMP Documents and Templates webpage. The CSO-related laws and regulations, beyond those required by FedRAMP, are captured in Appendix L.

## Introduction

The SSP is the “security blueprint” of a CSO. The SSP defines a CSO’s authorization boundary and describes the security controls in place to protect the confidentiality, integrity, and availability (CIA) of the system and federal data it holds.

## Purpose

This document is intended to be used by CSPs that are pursuing a Joint Authorization Board (JAB) provisional authorization to operate (P-ATO) or an agency authorization to operate (ATO) through the Federal Risk and Authorization Management Program (FedRAMP).

## System Information

Table 3.1 provides a summary of the key attributes of the CSO.

Table 3.1 System Information

## System Owner

The following individual is identified as the system owner or functional proponent/advocate for this system. The system owner is the official responsible for the overall procurement, development, integration, modification, or operation and maintenance of an information system.

Table 4.1 <Insert CSO Name> Owner

## Assignment of Security Responsibility

The <Insert CSP Name> <Insert CSO Name> Information System Security Officer (ISSO), or equivalent, identified below, has been appointed in writing and is deemed to have significant cyber security and operational role responsibilities.

Table 5.1 <Insert CSP Name> ISSO (or Equivalent) Point of Contact

## Leveraged FedRAMP-Authorized Services

The <Insert CSO Name> leverages the FedRAMP Authorized services depicted in Table 6.1 below.

Table 6.1 Leveraged FedRAMP Authorized Services

## External Systems and Services Not Having FedRAMP Authorization

External systems/services, interconnections, application programming interfaces (APIs), and command line interfaces (CLIs) that do not have a FedRAMP authorization, at the same or greater impact level as <Insert CSO Name>, are described in Table 7.1 below.

Table 7.1 External Systems/Services, Interconnections, APIs, and CLIs Without FedRAMP Authorizations

**1- Non-FedRAMP Authorized Cloud Services, 2- Corporate Shared Services, 3- Update Services for In-Boundary Software/Services

## Illustrated Architecture and Narratives

This section contains the diagrams and narratives for the <Insert CSO Name> authorization boundary, network, and data flows. Section 8.1 provides the diagrams, and Section 8.2 provides the associated narratives.

### Illustrated Architecture

This section contains the diagram that represents the authorization boundary, network, and data flows. Following the diagram, there is a narrative that describes the <Insert CSO Name> boundary components, functionality, as well as interactions and flows among internal components and external systems/services.

or

This section contains the diagrams that represent the authorization boundary, network, and data flows. Following each of the diagrams, there is a narrative that describes the <Insert CSO Name> boundary components, functionality, as well as interactions and flows among internal components and external systems/services. If using several illustrations, each must have a narrative.

### Narrative

## Services, Ports, and Protocols

Table 9.1 lists the service names, port numbers, and transport protocols enabled in <Insert CSO Name>. These must be specifically called out per the security control requirements in CM-7, CM-7(1), RA-5, SA-4, SA-9(2), and SA-9(4).

Table 9.1 <Insert CSO Name> Services, Ports, and Protocols

## Cryptographic Modules Implemented for Data At Rest (DAR) and Data In Transit (DIT)

The use of cryptography is critical for all systems that process and/or store federal data. Federal policy requires that anywhere that cryptography is required, it must employ FIPS 140-validated cryptographic modules. The Appendix Q cryptographic modules tables specify the encryption status for <Insert CSO Name>. These tables include reference numbers that are specified in <Insert Figure Number(s) (refer to the diagrams in the SSP depicting encryption status, typically data flow, if not combined)> in Section 8 of this SSP that depict the specific data stores and flows related to <Insert CSO Name>.

<Insert CSP Name> confirms, except where clearly noted in Appendix Q, that <Insert CSO Name> employs FIPS-validated cryptographic modules (CMs) that are configured in an approved mode, which is documented in the associated Cryptographic Module Validation Program (CMVP) security policy for the FIPS-validated certificate number. Only algorithms listed, as approved, in the CM’s security policy are used. The encryption discussed, in Appendix Q, is validated by an IA during a security assessment.

## Separation of Duties

Security control AC-5, Separation of Duties, requires that CSPs identify and document the roles of all individuals who access the system and define the access authorizations that support protections from bad actors, employee collusion, fraud, etc. before damage occurs. Table 11.1 captures the roles and access privileges for all individuals or roles that access <Insert CSO Name>.

Table 11.1 <Insert CSO Name> Separation of Duties

## SSP Appendices List

Table 12.1 SSP Required Appendices

<Insert CSO Name> FedRAMP Security Controls

Please see Appendix A (separate document) for the security controls applicable to <Insert CSO Name>.

<Insert CSO Name> Related Acronyms

The acronyms that appear in this section are specific to the <Insert CSO Name> SSP.

<Insert CSO Name> Information Security Policies and Procedures

The <Insert CSO Name> policies and procedures are included in Appendix C, available separately.

<Insert CSO Name> User Guide

The <Insert CSO Name> user guide is included in Appendix D, available separately.

or

The <Insert CSO Name> user guide website address is <Insert CSO User Guide URL>.

<Insert CSO Name> Digital Identity Worksheet

Mapping FedRAMP Levels to NIST SP 800-63 Levels

Digital identity is the process of establishing confidence in user identities electronically presented to an information system. Authentication focuses on the identity proofing process, the authenticator management process, and the assertion protocol used in a federated environment to communicate authentication and attribute information, if applicable.

Table E.1, below, “Mapping FedRAMP Levels to NIST SP 800-63 Levels”, maps the FedRAMP impact levels (Low/LI-SaaS, Moderate, and High) to NIST SP 800-63 Digital Identity Guidelines levels:

Identity Assurance Level (IAL) - Refers to the identity proofing process

Authenticator Assurance Level (AAL) - Refers to the authentication process

Federation Assurance Level (FAL) - Refers to the strength of an assertion in a federated environment, used to communicate authentication and attribute information (if applicable), to a relying party (RP)

Table E.1 Mapping FedRAMP Levels to NIST SP 800-63 Levels

Digital Identity Level Selection

The <Insert CSP Name> has identified that they support the digital identity level that has been selected for the <Insert CSO Name>. The selected digital identity level indicated is supported for federal agency consumers of the CSO. Implementation details of the digital identity mechanisms are provided in Appendix A under control IA-2.

Table E.2 Digital Identity Level

<Insert CSO Name> Rules of Behavior (RoB)

The <Insert CSO Name> rules of behavior are included in Appendix F, attached separately.

<Insert CSO Name> Information System Contingency Plan (ISCP)

The <Insert CSO Name> information system contingency plan is included in Appendix G, attached separately.

<Insert CSO Name> Configuration Management Plan (CMP)

The <Insert CSO Name> configuration management plan is included as Appendix H, attached separately.

<Insert CSO Name> Incident Response Plan (IRP)

The <Insert CSO Name> incident response plan is included as Appendix I, attached separately.

<Insert CSO Name> Control Implementation Summary (CIS) and Customer Responsibilities Matrix (CRM) Workbook

The <Insert CSO Name> CIS and CRM workbook is included as Appendix J, attached separately.

<Insert CSO Name> Federal Information Processing Standard (FIPS) 199 Categorization

The FIPS 199 Categorization (Security Categorization) report is a key component of the security authorization package developed for submission to FedRAMP authorizing officials. The FIPS 199 Categorization report below includes the determination of the security impact level for the <Insert CSO Name> cloud environment.

Note: This report is initially completed by the CSP in anticipation of what the actual federal data that might be stored, processed, and transmitted. Each agency must do this FIPS 199 analysis for their own data flows to ensure compatibility with the overall criticality level.

The <Insert CSO Name> system has been determined to have a security categorization of <Insert CSO Security Categorization Level>, as determined in Table K.1.

Impact levels are determined for each information type based on the security objectives (confidentiality, integrity, availability). The confidentiality, integrity, and availability impact levels define the security sensitivity category of each information type. The FIPS 199 is the High watermark for the impact level of all the applicable information types.

Table K.1 uses the NIST SP 800-60 (current revision) Volume II Appendices to Guide for Mapping Types of Information and Information Systems to Security Categories to identify information types with the security impacts.

Table K.1 <Insert CSO Name> Applicable Information Types with Security Impact Levels Using NIST SP 800-60 V2 R1

<Insert CSO Name>-Specific Laws and Regulations

Table L.1 <Insert CSO Name>-specific Laws and Regulations

<Insert CSO Name> Integrated Inventory Workbook (IIW)

The <Insert CSO Name> integrated inventory workbook is included in Appendix M, attached separately.

<Insert CSO Name> Continuous Monitoring Plan

The <CSO Name> continuous monitoring plan is included in Appendix N, attached separately.

<Insert CSO Name> POA&M

The <Insert CSO Name> plan of action and milestones (POA&M) is included in Appendix O, attached separately.

<Insert CSO Name> Supply Chain Risk Management Plan (SCRMP)

The <Insert CSO Name> supply chain risk management plan (SCRM) is included in Appendix P, attached separately.

<Insert CSO Name> Cryptographic Modules Table

The <Insert CSO Name> cryptographic modules table is included as Appendix Q, attached separately.

| Date | Version | Pages | Description | Author |
| --- | --- | --- | --- | --- |
| 06/30/2023 | 1.0 | All | Initial publication after combining "front matter" sections of the FedRAMP System Security Plan (SSP) High Baseline Template, FedRAMP System Security Plan (SSP) Moderate Baseline Template, FedRAMP System Security Plan (SSP) Low Baseline Template, and Appendix B - FedRAMP Tailored LI-SaaS Template. | FedRAMP PMO |
| 10/13/2023 | 1.1 | All | Updated header and removal of extra section break | FedRAMP PMO |

| Instructions: |
| --- |
| Before populating this template, the FedRAMP PMO recommends reviewing the CSP Authorization Playbook: Getting Started with FedRAMP (Volumes I and II) and the Agency Authorization Playbook. These documents provide a great starting point for new stakeholders and a reference resource for seasoned stake |

| Identification of Organization that Prepared this Document | Identification of Organization that Prepared this Document |
| --- | --- |
| Organization Name | <Enter Company/Organization> |
| Street Address | <Enter Street Address> |
| Suite/Room/Building | <Enter Suite/Room/Building> |
| City, State, Zip | <Enter City, State, and Zip Code> |

| Identification of Cloud Service Provider | Identification of Cloud Service Provider |
| --- | --- |
| Organization Name | <Enter Company/Organization>. |
| Street Address | <Enter Street Address> |
| Suite/Room/Building | <Enter Suite/Room/Building> |
| City, State, Zip | <Enter City, State, and Zip Code> |

| Date | Description | Version | Author |
| --- | --- | --- | --- |
| <Date> | <Revision Description> | <Version> | <Author> |
| <Date> | <Revision Description> | <Version> | <Author> |
| <Date> | <Revision Description> | <Version> | <Author> |

| Instructions: |
| --- |
| Add or remove signature boxes, as needed. Digital or wet/physical signatures are permitted.   <br> Delete this and all other instructional text from your final version of this document. |

| <Sign Here> | <Sign Here> | <Sign Here> | <Sign Here> | <Sign Here> |
| --- | --- | --- | --- | --- |
| Name | <Enter Name> | <Enter Name> | Date | <Date> |
| Title | <Enter Title> | <Enter Title> | <Enter Title> | <Enter Title> |
| Cloud Service Provider | Cloud Service Provider | <CSP Name> | <CSP Name> | <CSP Name> |
| <Sign Here> | <Sign Here> | <Sign Here> | <Sign Here> | <Sign Here> |
| Name | <Enter Name> | <Enter Name> | Date | <Date> |
| Title | <Enter Title> | <Enter Title> | <Enter Title> | <Enter Title> |
| Cloud Service Provider | Cloud Service Provider | <CSP Name> | <CSP Name> | <CSP Name> |
| <Sign Here> | <Sign Here> | <Sign Here> | <Sign Here> | <Sign Here> |
| Name | <Enter Name> | <Enter Name> | Date | <Date> |
| Title | <Enter Title> | <Enter Title> | <Enter Title> | <Enter Title> |
| Cloud Service Provider | Cloud Service Provider | <CSP Name> | <CSP Name> | <CSP Name> |

| Instructions: |
| --- |
| Complete Table 3.1 as indicated. The Digital Identity Level and FIPS PUB 199 Level should be completed after completing the corresponding appendices and determining appropriate content. <br> Service Model: Choose Infrastructure as a Service (IaaS), Platform as a Service (PaaS), Software as a Service (Saa |

| System Information | System Information |
| --- | --- |
| CSP Name: | <Insert CSP Name> <Insert CSP Abbreviation, as appropriate> |
| CSO Name: | <Insert CSO Name> <Insert CSO Abbreviation, as appropriate> |
| FedRAMP Package ID: | <Insert FedRAMP Package ID> |
| Service Model: | <Choose one: IaaS, PaaS, SaaS, IaaS/PaaS, IaaS/PaaS/SaaS, IaaS/SaaS, PaaS/SaaS, LI-SaaS> |
| Digital Identity Level (DIL) Determination (SSP Appendix E): | <Choose one: IAL3/FAL3/AAL3, IAL2/FAL2/AAL2, IAL1/FAL1/AAL1> |
| FIPS PUB 199 Level (SSP Appendix K): | <Choose one: High, Moderate, Low, LI-SaaS> |
| Fully Operational as of: | <Insert MM/DD/YYYY> |
| Deployment Model: | <Choose one: Public Cloud, Government-Only Cloud, Hybrid Cloud> |
| Authorization Path: | <Choose one: Joint Authorization Board Provisional Authorization, Agency Authorization> |
| General System Description: | <Insert CSO Name> is delivered as [a/an] [insert based on the Service Model above] offering using a multi-tenant [insert based on the Deployment Model above] cloud computing environment. It is available to [Insert scope of customers in accordance with instructions above (for example, the public, fed |

| System Owner Information | System Owner Information |
| --- | --- |
| Name | <Enter Name> |
| Title | <Enter Title> |
| Company / Organization | <Enter Company/Organization> |
| Address | <Enter Address, City, State and Zip> |
| Phone Number | <555-555-5555> |
| Email Address | <Enter Email Address> |

| Instructions: |
| --- |
| Complete Table 5.1 as indicated. If there are other personnel with key security responsibilities for the CSO, additional tables may be added. <br> The Information System Security Officer (ISSO) is the individual who is assigned responsibility for maintaining the appropriate operational security posture f |

| ISSO (or Equivalent) Point of Contact | ISSO (or Equivalent) Point of Contact |
| --- | --- |
| Name | <Enter Name> |
| Title | <Enter Title> |
| Company / Organization | <Enter Company/Organization> |
| Address | <Enter Address, City, State and Zip> |
| Phone Number | <555-555-5555> |
| Email Address | <Enter email address> |

| Instructions: |
| --- |
| Table 6.1 includes all functions, services, features, and APIs that are leveraged from FedRAMP Authorized CSOs. The FedRAMP Marketplace is the authoritative source for identifying CSOs and their services that are FedRAMP Authorized. <br> Alternatively, you may remove the below table and add it as an addi |

| # | CSP/CSO Name (Name on FedRAMP Marketplace) | CSO Service (Names of services and features - services from a single CSO can be all listed in one cell) | Authorization Type (JAB or Agency) and FedRAMP Package ID # | Nature of Agreement | Impact Level (High, Moderate, Low, LI-SaaS) | Data Types | Authorized Users/Authentication |
| --- | --- | --- | --- | --- | --- | --- | --- |

| Instructions: |
| --- |
| FedRAMP Authorized services should be used, whenever possible, since their risk is defined. In some cases, CSPs establish connections to external systems and services that lack FedRAMP authorization to exchange data and information or augment system functionality and provide operational support serv |

| # <br> (either 1, 2, or 3)** | System/ Service/ API/CLI Name (Non-FedRAMP Cloud Services) | Connection Details | Nature of Agreement | Still Supported? Y or N | Data Types | Data Categorization | Authorized Users/ Authentication | Other Compliance Programs | Description | Hosting Environment | Risk/Impact/ Mitigation |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| Instructions: |
| --- |
| Use the FedRAMP Integrated Inventory Workbook template, and ensure the inventory items are named consistently, within the diagrams and within the narratives, in the sections that follow. Ensure naming conventions are adopted throughout the entire SSP (i.e., security control implementation descriptio |

| Instructions: |
| --- |
| Choose the appropriate paragraph based on the number of diagrams; delete the other. <br> Delete this and all other instructional text from your final version of this document. |

| Instructions: |
| --- |
| In this section, provide the illustration(s) for the CSO’s authorization boundary, network architecture, and data flows. The illustration can be one all-encompassing diagram that addresses all required informational elements, or separate diagrams (Authorization Boundary Diagram [ABD], Network Diagra |

| Instructions: |
| --- |
| NARRATIVE DESCRIPTION for the ABD, DFD, and Network Diagram: <br> Whether using one or multiple diagrams, after each, provide a detailed narrative description that clearly describes the CSO and the elements of the diagram. The narrative should describe the components of the system as depicted in the diag |

| Instructions: |
| --- |
| Complete this table even if leveraging a pre-existing FedRAMP authorization. Add more rows as needed. If you are unclear as to what should be included in this table, refer to: https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml. <br> Ensure that the services, port |

| Service Name | Port # | Transport Protocol | Reference # | Purpose | Used By |
| --- | --- | --- | --- | --- | --- |

| Instructions: |
| --- |
| Use the tables in Appendix Q to document the encryption status of all areas/flows of all data, to include: data at rest, data in transit across the boundary, data in transit within the boundary, remote access mechanisms (e.g., IPSec VPN), key management, key generation, underlying system config (e.g |

| Instructions: |
| --- |
| In Table 11.1, identify and document all duty descriptions within the organization. Each duty description is listed in a separate row; if a CSP is a large and complex organization, there could be several. In the case of a CSP being large and complex, focus on the duty descriptions that apply to the  |

| Duty Description | Information Owner | Security officer | Privacy officer | Linux Admin | Windows Admin | Agency Admin | Agency Customer |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Adds/Removes Privileged Admins | X | X |  |  |  |  |  |  |  |
| Adds/Removes Non-privileged Admins |  | X | X |  |  |  |  |  |  |
| Adds/Removes Customer Privileged Admins |  |  |  |  |  |  |  |  |  |
| Adds/Removes Customer Non-privileged Admins |  |  |  |  |  |  |  |  |  |
| Enforces Physical Access Authorizations |  |  |  |  |  |  |  |  |  |
| Defines Least Privilege Needed to Perform Tasks |  |  |  |  |  |  |  |  |  |
| Reviews/Approves Policy |  |  |  |  |  |  |  |  |  |
| Enforces Policy |  |  |  |  |  |  |  |  |  |

| Instructions: |
| --- |
| FedRAMP provides templates for many of the required appendices. Some templates are available on FedRAMP’s Documents and Templates Web page; others are included within the body of the SSP Appendix. Where FedRAMP provides a template, it will be noted in the table below (“FedRAMP-provided” versus “CSP- |

| Appendix Name | Filename |
| --- | --- |
| Appendix A: FedRAMP Security Controls  <br> (FedRAMP-provided; different template for each impact level) |  |
| Appendix B: Related Acronyms  <br> (CSP-provided) | Included within the SSP |
| Appendix C: Security Policies and Procedures  <br> (CSP-provided in a zip file; not required for LI-SaaS) |  |
| Appendix D: User Guide  <br> (CSP-provided; not required for LI-SaaS) |  |
| Appendix E: Digital Identity Worksheet  <br> (FedRAMP-provided) | Included within the SSP |
| Appendix F: Rules of Behavior  <br> (FedRAMP-provided; not required for LI-SaaS) |  |
| Appendix G: Information System Contingency Plan (ISCP)  <br> (FedRAMP-provided; not required for LI-SaaS) |  |
| Appendix H: Configuration Management Plan (CMP)  <br> (CSP-provided; not required for LI-SaaS) |  |
| Appendix I: Incident Response Plan (IRP) <br> (CSP-provided; not required for LI-SaaS) |  |
| Appendix J: CIS and CRM Workbook <br> (FedRAMP-provided; different template for each impact level) |  |
| Appendix K: FIPS 199 Worksheet  <br> (FedRAMP-provided) | Included within the SSP |
| Appendix L: CSO-Specific Required Laws and Regulations  <br> (CSP-provided) |  |
| Appendix M: Integrated Inventory Workbook <br> (FedRAMP-provided) |  |
| Appendix N: Continuous Monitoring Plan <br> (CSP-provided) |  |
| Appendix O: POA&M <br> (FedRAMP-provided) |  |
| Appendix P: Supply Chain Risk Management Plan (SCRMP) <br> (CSP-provided) |  |
| Appendix Q: Cryptographic Module Table <br> (FedRAMP-provided) |  |

| Instructions: |
| --- |
| This appendix applies to all baselines (LI-SaaS, Low, Moderate, and High). <br> Select the appropriate baseline template (LI–SaaS, Low, Moderate, or High), from the FedRAMP Documents and Templates webpage, and maintain the controls as a separate attachment to the SSP. For LI-SaaS packages, Appendix A use |

| Instructions: |
| --- |
| This appendix applies to all baselines (LI-SaaS, Low, Moderate, and High). <br> Document CSO/CSP-specific acronyms in this appendix. They should also be spelled out, when first used, in the SSP. The format for this appendix is at the CSP’s discretion. <br> Delete this and all other instructional text from you |

| Instructions: |
| --- |
| This appendix is not required for LI-SaaS CSOs (see Appendix A LI-SaaS for attestation requirements). <br> Policies and procedures (P&Ps) are a critical supplement to the SSP and are required by the first control (known as the “dash ones” (e.g., AC-1)) for each control family. Policies provide the guidel |

| Instructions: |
| --- |
| Instructions: This appendix is not required for LI-SaaS CSOs. <br> The user guide explains how agency customers will use the system (e.g., if a system has a self-service portal, the user guide must explain how to use the portal).  <br> FedRAMP does not provide a template for the User Guide. Many CSPs provide  |

| Instruction: |
| --- |
| This appendix applies to all baselines (LI-SaaS, Low, Moderate, and High). <br> Complete Table E.2, below; a separate attachment is not required. Authentication solutions, provided by a CSP for CSP-personnel to access and administer the CSO, must meet digital identity requirements. Authentication solutio |

| FedRAMP Impact Level | Identity Assurance Level (IAL) | Authenticator Assurance Level (AAL) | Federation Assurance Level (FAL) |
| --- | --- | --- | --- |
| High | IAL3: In-person or supervised remote identity proofing | AAL3: Multi-factor required; authenticators and verifiers use FIPS 140-validated cryptography; authenticator must be hardware-based | FAL3: The assertion is signed and encrypted by the identity provider, such that only the relying party can decrypt it. For very high value or very high-risk situations, the subscriber (user) must provide proof of possession of a secure, cryptographic key, and a HW based device to provide verifier im |
| Moderate | IAL2: In-person or remote, potentially involving a “trusted referee” | AAL2: Multi-factor required; authenticators and verifiers use FIPS 140-validated cryptography | FAL2: Assertion is signed and encrypted by the identity provider, such that only the relying party can decrypt it |
| Low and  <br> FedRAMP LI-SaaS | IAL1: Self-asserted | AAL1: Single-factor or multi-factor; verifiers use FIPS 140-validated cryptography | FAL1: Assertion is digitally signed by the identity provider |

| Instructions: |
| --- |
| Select the lowest level that will cover all potential impacts identified from the table above.  <br> Delete this and all other instructional text from your final version of this document. |

| Digital Identity Level | Maximum Impact Profile | Selection |
| --- | --- | --- |
| Level 1: AAL1, IAL1, FAL1 | Low/LI-SaaS |  |
| Level 2: AAL2, IAL2, FAL2 | Moderate |  |
| Level 3: AAL3, IAL3, FAL3 | High |  |

| Instructions: |
| --- |
| This appendix is not required for LI-SaaS CSOs.  <br> Security control PL-4 requires CSPs to develop Rules of Behavior (RoB) that establish and describe the responsibilities and expected behavior related to the use of a CSO. <br> FedRAMP provides a RoB template that includes four example sets of rules of beha |

| Instructions: |
| --- |
| This appendix is not required for LI-SaaS CSOs.  <br> FedRAMP provides an Information System Contingency Plan (ISCP) template that must be used by a CSP.  <br> A CSP is responsible for establishing general procedures for recovering their CSO after a service disruption. Security control CP-2 requires CSPs to d |

| Instructions: |
| --- |
| This appendix is not required for LI-SaaS CSOs. <br> Security control CM-9 requires CSPs to develop a CMP, in accordance with NIST SP 800-128. FedRAMP does not provide a template for the CMP; however, NIST SP 800-128, Guide for Security-Focused Configuration Management of Information Systems, provides gu |

| Instructions: |
| --- |
| This appendix is not required for LI-SaaS CSOs. <br> Security control IR-8 requires CSPs to develop an IRP, in accordance with NIST SP 800-61. FedRAMP does not provide an IRP template; however, NIST SP 800-61, Computer Security Incident Handling Guide, provides guidance on the development of incident res |

| Instructions: |
| --- |
| This appendix applies to all baselines (LI-SaaS, Low, Moderate, and High). <br> CSPs are required to submit a single control implementation summary (CIS) and customer responsibilities Matrix (CRM) workbook as Appendix J to the SSP. FedRAMP provides one template with color-coded tabs (worksheets) for each |

| Instructions: |
| --- |
| This appendix applies to all baselines (LI-SaaS, Low, Moderate, and High). <br> Review the NIST Special Publication 800-60 Volume 2 Revision 1,“Appendix C: Management and Support Information and Information System Impact Levels,” and “Appendix D: Impact Determination for Mission-Based Information and Inf |

| Information Type | NIST SP 800-60 V2 R1 <br> Recommended Confidentiality Impact Level | NIST SP 800-60 V2 R1 <br> Recommended Integrity Impact Level | NIST SP 800-60 V2 R1 <br> Recommended Availability Impact Level | CSP Selected Confidentiality Impact Level | CSP Selected Integrity Impact Level | CSP Selected Availability Impact Level | Statement for Impact Adjustment Justification |
| --- | --- | --- | --- | --- | --- | --- | --- |

| Instructions: |
| --- |
| This appendix applies to all baselines (LI-SaaS, Low, Moderate, and High) <br> If the CSO is governed by CSP or agency-specific laws and regulations, these should be listed below. If there are no CSO-specific governing laws or regulations, simply state “N/A” in the table. <br> Delete this and all other instru |

| Number | Title | Date |
| --- | --- | --- |

| Instructions: |
| --- |
| This appendix applies to all baselines (LI-SaaS, Low, Moderate, and High). <br> Security control CM-8 requires CSPs to develop and document an inventory of system components within the authorization boundary that is at the level of granularity deemed necessary for tracking and reporting. To this end, Fed |

| Instructions: |
| --- |
| This appendix applies to all baselines (LI-SaaS, Low, Moderate, and High). FedRAMP does not provide a template for the continuous monitoring plan. CSPs should use their own desired format to develop a continuous monitoring plan, in accordance with CA-7. The FedRAMP Continuous Monitoring Strategy Gui |

| Instructions: |
| --- |
| This appendix applies to all baselines (LI-SaaS, Low, Moderate, and High), and CSPs must use the FedRAMP-provided POA&M template. <br> Delete this and all other instructional text from your final version of this document. |

| Instructions: |
| --- |
| This appendix applies to all baselines (LI-SaaS, Low, Moderate, and High). FedRAMP does not provide a template for the supply chain risk management plan. CSPs should use their own desired format to develop this plan, in accordance with SR-2. A plan format is available, for reference, in NIST SP 800- |

| Instructions: |
| --- |
| Instructions: This appendix applies to all baselines (LI-SaaS, Low, Moderate, and High) and, CSPs must use the FedRAMP provided Cryptographic Modules Table template. <br> Delete this and all other instructional text from your final version of this document. |

