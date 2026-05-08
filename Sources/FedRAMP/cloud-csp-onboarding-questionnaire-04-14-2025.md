---
title: "Cloud CSP Onboarding Questionnaire_04-14-2025 "
type: reference
framework: fedramp
source_format: converted
created: 2026-05-08
tags:
  - fedramp
  - reference
---

# Cloud CSP Onboarding Questionnaire_04-14-2025 

> Source: `Cloud CSP Onboarding Questionnaire_04-14-2025 .docx`

Please provide a brief system description of your Cloud Service Offering (CSO):

What type of cloud service model does the CSO represent?

Infrastructure as a Service

Platform as a Service

Software as a Service

Other: _______________________

What type of Cloud deployment model does the CSO support (e.g. Private Cloud, Public Cloud, Government Federal Community Cloud, DoD Community Cloud)?

What type of service does the Cloud Service Offering (CSO) provide (e.g., IdAM, streaming, AI, etc.)?

Does this CSO have an existing Federal Risk and Authorization Management Program (FedRAMP) authorization?  (If yes, please specify if this is the same environment covered by the FedRAMP authorization or a separate cloned/mirrored environment specific for DoD.  If no, does the CSP/CSO intend to submit this CSP/CSO for FedRAMP authorization)?

Specify if this CSO is seeking an Impact Level (IL) 4 or IL5 authorization and summarize the types of DoD information the CSO will support for the purposes of determining whether Level 4 or Level 5 is appropriate (e.g. CUI, NSS, Privacy data, financial data, etc.):

Does this CSO have more than one customer?  If so, who are the customers?

Briefly describe any software, hardware, application, or other requirement that a DoD customer would need to include in their boundary to use the CSO:

Are all Cloud Service Provider (CSP) personnel who have access to the systems processing/storing DOD information, or have access to DoD information itself, U.S. Citizens, U.S. Nationals (as defined in 8 U.S. Code § 1408), or U.S. Persons (as defined in 22 CFR 120.15)?

Yes  No

If no, please explain _________________________________________

Do all the CSO support team members meet US Citizens OPM requirements for this CSO’s Impact Level?

Do all the CSO support team members meet the Security Clearance requirements outlined by OPM for this CSO’s Impact Level?

Are there any overseas Network Operations Centers (NOCs) with system administrator access to your service?

Does this CSO leverage any other CSOs?  If so, what are the services and are they authorized by the FedRAMP JAB or agency?

How is support for DOD PKI authentication by DOD privileged and nonprivileged users implemented? (See section 5.4 of the CSP SRG)

Does this CSO allow for external remote access (outside accreditation boundary) into the authorization boundary?

Does the CSO provide a private connection capability between the off-premises CSP’s/CSO’s network and DOD networks in support of connections through the Boundary Cloud Access Point (BCAP) and meet-me points? (See section 5.9.1.1, and subsections, of the CSP SRG)

Does this CSO provide non-DoD customers access to the CSO from the internet?  If so, how does the CSP’s network and/or the CSO prohibit a path from the internet to the NIPRNet across the DISA BCAP, thus creating a back door to a DOD network?

Will the CSO require any network whitelisting to allow DoD users access to the service(s) from the Internet across the DISA Internet Access Point (IAP) for access outside of the NIPRNet (see section 5.9.1.1.3 of the CSP SRG)?  If so, can routing be isolated per DoD tenant, and how?

If application/services are accessed through an Application Programming Interface (API), please describe how APIs are secured and managed.

Do system administrators use their corporate workstations for both cloud and corporate network access?  If so, is split tunneling utilized?  If “Yes”, what protections are in place to mitigate the risk exposure split tunnel sessions may present to the authorization boundary?

How does the system administrator authenticate into the authorization boundary, e.g., Yubikey, Just in Time (JIT)?

Is your service Federal Information Processing Standards (FIPS) 140-3 Compliant?  How is data protected in-transit and at-rest?

How is metadata stored?

Does the CSO collect, “data mine”, or process any customer data for the development or enhancement of any CSP’s products (e.g., AI model training)?

How are customer data and workloads isolated and separated within the same CSO infrastructure?

Where is the vulnerability data for this CSO stored?

Does the CSP ensure that all data stored and processed for the DOD resides in a facility within the 50 States, the District of Columbia, and outlying areas of the U.S. (as defined at FAR 2.101)?  (See section 5.2.1 of the CSP SRG)

Is the management plane shared amongst the authorized tenants in the boundary?

Will the CSP report all incident to the Defense Industrial Base (DIB) Cyber Incident Collection Format (ICF), and affected Mission Owners, in accordance with section 5.10 of the CSP Security Requirements Guide (SRG)?

The following are questions regarding Domain Name Services (DNS) to ensure the CSP meets the requirements outlined in the CSP SRG and DoDI 8410.01, i.e., a CSO must use a .mil for their Top-Level Domain):

Will the IL4/5 CSO require a URL for DoD customers to reach?  Yes ☐ No

Will the URL or DNS name servers need to be reachable from the public Internet?  Yes ☐ No

Does the CSO require reverse DNS for devices within their Gov Cloud Boundary?  Yes ☐ No

Does the CSO require onboarding to Enterprise Email Security Gateway (EEMSG)? Yes ☐ No

Complete the following table for any connections established between the proposed authorization boundary and external systems or services to (i) exchange data and information or (ii) augment system functionality and operational support services:

The following information outlines guidelines that the CSP must adhere to for their CSO in relation to DoD DNS:

The CSPs must abide by all DNS guidance in DoD Instruction 8410.01 and the CSP SRG.

The CSPs must not have their DoD customers go to a commercial URL for their IL4/5 CSO.  The CSO must use a .mil domain name to build the CSO’s URL in the CSO’s IL4/5.

The CSOs must use name servers that have a .mil Fully Qualified Domain Name (FQDN) to resolve the CSO’s .mil domain to DoD IP address space.  The .mil domain must be DNSSEC signed and maintained.  Connectivity to the .mil domain name must support UDP and TCP.  Name servers hosting a .mil domain must only answer for port 53 traffic.

If the CSO requires reverse DNS for their CSO to function, DoD IP address space must resolve to .mil domain name on name servers that have a .mil FQDN.  Reverse DNS does not have to be DNSSEC signed.  Reverse DNS is required for onboarding to Enterprise Email Security Gateway (EEMSG).

The CSPs are not authorized to use a commercial, non-DoD, third-party DNS service to resolve to DoD IP address space or .mil FQDNs.

The CSPs are authorized to use commercial, non-DoD, third-party DNS service to resolve internal devices in the CSO’s Gov Cloud Boundary that do not use DoD IP address space or resolve to .mil FQDNs.

If the CSO’s .mil Second Level Domain (SLD) name must be reachable from public Internet, the following two actions need to be done:

The DNS name servers hosting the .mil SLD must in the NIPR DMZ Whitelist.

The DNS name servers hosting the .mil SLD need to be configured to be behind the DoD NIC’s .mil proxy.

The DoD IP addresses for the DNS name servers hosting the .mil domain must only answer for port 53 UDP/TCP traffic.

If the CSO’s URL needs to be reachable from public Internet, then number 6. is a requirement, and the DoD IP address for the URL must be in the NIPR DoD DMZ Whitelist.  The CSP is responsible for following all requirements in the CSP SRG for having a public facing web page.

Any device in the CSO’s Gov Cloud boundary that is configured with a DoD IP address must use the DoD NIC’s Enterprise Recursive Service (ERS) for DNS resolution.

If the CSP cannot meet any of the requirements in DODI 8410.01 and CSP SRG for their CSO, the CSP must work with the DoD NIC and DISA RE to identify and justify which requirement is unable to be met.  The CSP may be asked to deploy a POA&M to have their CSO meet the above requirements.

| # | System/Service Name | Interconnection Details | Nature of Agreement | Still Supported? Y or N | Data Types | Data Categorization | Authorized Users & Authentication Method | Compliance Programs |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Provide the name of the system or service. Include the vendor name, if different from the system or service name. | Provide connectivity details. |  |  | List the CSO data types transmitted to, stored, or processed by the system/service, including federal data/metadata and system data/metadata. | Identify the security impact level of the data (Low, Moderate, or High) in accordance with FIPS 199. | List the user roles (e.g., SecOps Engineers) authorized to access the service, and provide the authentication method. | List any certifications for this service (e.g., PCI SOC 2, CSA STAR Level 2), and provide the certification date. |
|  | Description: Describe the purpose of the external system/service and the hosting environment (e.g., corporate network, IaaS, or self-hosted). <br> Risk/Impact/Mitigation: Describe potential risks introduced by the external system/service and impact to the CSO or federal customer data if the confidentiali | Description: Describe the purpose of the external system/service and the hosting environment (e.g., corporate network, IaaS, or self-hosted). <br> Risk/Impact/Mitigation: Describe potential risks introduced by the external system/service and impact to the CSO or federal customer data if the confidentiali | Description: Describe the purpose of the external system/service and the hosting environment (e.g., corporate network, IaaS, or self-hosted). <br> Risk/Impact/Mitigation: Describe potential risks introduced by the external system/service and impact to the CSO or federal customer data if the confidentiali | Description: Describe the purpose of the external system/service and the hosting environment (e.g., corporate network, IaaS, or self-hosted). <br> Risk/Impact/Mitigation: Describe potential risks introduced by the external system/service and impact to the CSO or federal customer data if the confidentiali | Description: Describe the purpose of the external system/service and the hosting environment (e.g., corporate network, IaaS, or self-hosted). <br> Risk/Impact/Mitigation: Describe potential risks introduced by the external system/service and impact to the CSO or federal customer data if the confidentiali | Description: Describe the purpose of the external system/service and the hosting environment (e.g., corporate network, IaaS, or self-hosted). <br> Risk/Impact/Mitigation: Describe potential risks introduced by the external system/service and impact to the CSO or federal customer data if the confidentiali | Description: Describe the purpose of the external system/service and the hosting environment (e.g., corporate network, IaaS, or self-hosted). <br> Risk/Impact/Mitigation: Describe potential risks introduced by the external system/service and impact to the CSO or federal customer data if the confidentiali | Description: Describe the purpose of the external system/service and the hosting environment (e.g., corporate network, IaaS, or self-hosted). <br> Risk/Impact/Mitigation: Describe potential risks introduced by the external system/service and impact to the CSO or federal customer data if the confidentiali |
| 2 | Service Name | Interconnection Details |  |  | Data Types | Data Categorization | Authorized Users & Authentication Method | Compliance Programs |
|  | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: |
| 3 | Service Name | Interconnection Details |  |  | Data Types | Data Categorization | Authorized Users & Authentication Method | Compliance Programs |
|  | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: | Description:  <br> Risk/Impact/Mitigation:   <br> Agreements: |

