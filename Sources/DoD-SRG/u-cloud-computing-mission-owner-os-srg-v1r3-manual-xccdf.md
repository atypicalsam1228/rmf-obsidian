---
title: "Cloud Computing Mission Owner Operating System Security Requirements Guide"
type: reference
framework: dod-srg
source_format: converted
created: 2026-05-08
tags:
  - dod-srg
  - xccdf
  - disa
  - fedramp
---

# Cloud Computing Mission Owner Operating System Security Requirements Guide

> Source: `U_Cloud_Computing_Mission_Owner_OS_SRG_V1R3_Manual-xccdf.xml`  
> Benchmark ID: `Cloud_Computing_Mission_Owner_OS_SRG`  
> Version: `1`

## Overview

This Security Requirements Guide is published as a tool to improve the security of Department of Defense (DOD) information systems. The requirements are derived from the National Institute of Standards and Technology (NIST) 800-53 and related documents. Comments or proposed revisions to this document should be sent via email to the following address: disa.stig_spt@mail.mil.

## References


## Profiles

| Profile ID | Title |
|---|---|
| `MAC-1_Classified` | I - Mission Critical Classified |
| `MAC-1_Public` | I - Mission Critical Public |
| `MAC-1_Sensitive` | I - Mission Critical Sensitive |
| `MAC-2_Classified` | II - Mission Support Classified |
| `MAC-2_Public` | II - Mission Support Public |
| `MAC-2_Sensitive` | II - Mission Support Sensitive |
| `MAC-3_Classified` | III - Administrative Classified |
| `MAC-3_Public` | III - Administrative Public |
| `MAC-3_Sensitive` | III - Administrative Sensitive |

## Rules

### SRG-OS-000001

> Group ID: `V-259872`

<GroupDescription></GroupDescription>

#### The Mission Owner must configure the customer service portal credentials for least privilege.

> Rule ID: `SV-259872r958362_rule` | Severity: **HIGH**

**Description:** The Mission Owner must appoint specific individuals or entities to establish plans and policies for the control of privileged user access (including root account credentials) used to establish, configure, and control a Mission Owner's Virtual Private Cloud (VPC) configuration once connected to the DISA Information Systems Network (DISN). These individuals or entities establish and manage accounts and credentials used by privileged DOD users and systems to administer and control DOD cloud service offering configurations. This role is intended to operate at all DOD information Impact Levels. However, it may not apply to some Software-as-a-Service (SaaS) solutions where DOD account owners are not required to use the cloud service provider's (CSP's) Identity and Access Management (IdAM) system to administer user accounts and service configurations. false

**Check:** Review the site's approval documentation to verify that an individual or entity has been appointed to manage the cloud management service portal. This may be a group or contracted service. Verify the cloud service offering has been configured to allow only these individuals for portal service and virtual instance configuration.

If the Mission Owner has not configured the customer service portal credentials and the Mission Owner application/system privileged accounts for least privilege, this is a finding.

**Fix:** This applies to all Impact Levels.
FedRAMP Moderate, High.

Appoint an individual or entity to manage portal services. Application and enclave administrators should also be appointed. 

Configure access for these individuals to access and configure services and virtual instances.

**References:** `CCI-000015`

---

### SRG-OS-000023

> Group ID: `V-259873`

<GroupDescription></GroupDescription>

#### The Mission Owner must configure the cloud service offering (CSO)-provided customer logon banner to display the Standard Mandatory DOD Notice and Consent Banner before granting access to users that must log on.

> Rule ID: `SV-259873r958390_rule` | Severity: **MEDIUM**

**Description:** Display of a standardized and approved use notification before granting access to the operating system ensures privacy and security notification verbiage used is consistent with applicable federal laws, Executive Orders, directives, policies, regulations, standards, and guidance. System use notifications are required only for access via logon interfaces with human users and are not required when such human interfaces do not exist. The banner must be formatted in accordance with DTM-08-060. Use the following verbiage for operating system that can accommodate banners of 1300 characters: "You are accessing a U.S. Government (USG) Information System (IS) that is provided for USG-authorized use only. By using this IS (which includes any device attached to this IS), you consent to the following conditions: -The USG routinely intercepts and monitors communications on this IS for purposes including, but not limited to, penetration testing, COMSEC monitoring, network operations and defense, personnel misconduct (PM), law enforcement (LE), and counterintelligence (CI) investigations. -At any time, the USG may inspect and seize data stored on this IS. -Communications using, or data stored on, this IS are not private, are subject to routine monitoring, interception, and search, and may be disclosed or used for any USG-authorized purpose. -This IS includes security measures (e.g., authentication and access controls) to protect USG interests--not for your personal benefit or privacy. -Notwithstanding the above, using this IS does not constitute consent to PM, LE or CI investigative searching or monitoring of the content of privileged communications, or work product, related to personal representation or services by attorneys, psychotherapists, or clergy, and their assistants. Such communications and work product are private and confidential. See User Agreement for details." Use the following verbiage for operating systems that have severe limitations on the number of characters that can be displayed in the banner: "I've read & consent to terms in IS user agreem't." false

**Check:** Determine if the CSO login function is configured to present a DOD-approved banner that is formatted in accordance with DTM-08-060. Verify the use of the following verbiage for applications that can accommodate banners of 1300 characters:

"You are accessing a U.S. Government (USG) Information System (IS) that is provided for USG-authorized use only.

By using this IS (which includes any device attached to this IS), you consent to the following conditions:
-The USG routinely intercepts and monitors communications on this IS for purposes including, but not limited to, penetration testing, COMSEC monitoring, network operations and defense, personnel misconduct (PM), law enforcement (LE), and counterintelligence (CI) investigations.
-At any time, the USG may inspect and seize data stored on this IS.
-Communications using, or data stored on, this IS are not private, are subject to routine monitoring, interception, and search, and may be disclosed or used for any USG-authorized purpose.
-This IS includes security measures (e.g., authentication and access controls) to protect USG interests--not for your personal benefit or privacy.
-Notwithstanding the above, using this IS does not constitute consent to PM, LE or CI investigative searching or monitoring of the content of privileged communications, or work product, related to personal representation or services by attorneys, psychotherapists, or clergy, and their assistants. Such communications and work product are private and confidential. See User Agreement for details."

Verify use of the following verbiage for operating systems that have severe limitations on the number of characters that can be displayed in the banner:

"I've read & consent to terms in IS user agreem't."

If such a banner is not presented for all virtual machines and applications, this is a finding.

**Fix:** This applies to all Impact Levels.
FedRAMP Moderate, High.

Configure the CSO provided customer logon banner capability and any Mission Owner provided logon capability to virtual machines in accordance with DTM-08-060 for all privileged and nonprivileged customer users that must logon. Use the following verbiage for applications that can accommodate banners of 1300 characters:

"You are accessing a U.S. Government (USG) Information System (IS) that is provided for USG-authorized use only.

By using this IS (which includes any device attached to this IS), you consent to the following conditions:
-The USG routinely intercepts and monitors communications on this IS for purposes including, but not limited to, penetration testing, COMSEC monitoring, network operations and defense, personnel misconduct (PM), law enforcement (LE), and counterintelligence (CI) investigations.
-At any time, the USG may inspect and seize data stored on this IS.
-Communications using, or data stored on, this IS are not private, are subject to routine monitoring, interception, and search, and may be disclosed or used for any USG-authorized purpose.
-This IS includes security measures (e.g., authentication and access controls) to protect USG interests--not for your personal benefit or privacy.
-Notwithstanding the above, using this IS does not constitute consent to PM, LE or CI investigative searching or monitoring of the content of privileged communications, or work product, related to personal representation or services by attorneys, psychotherapists, or clergy, and their assistants. Such communications and work product are private and confidential. See User Agreement for details."

Use the following verbiage for operating systems that have severe limitations on the number of characters that can be displayed in the banner:

"I've read & consent to terms in IS user agreem't."

**References:** `CCI-000048`

---

### SRG-OS-000096

> Group ID: `V-259874`

<GroupDescription></GroupDescription>

#### The Mission Owner must configure the Infrastructure as a Service (IaaS)/Platform as a Service (PaaS) to prohibit or restrict the use of functions, ports, protocols, and/or services.

> Rule ID: `SV-259874r1132412_rule` | Severity: **MEDIUM**

**Description:** To prevent unauthorized connection of devices, unauthorized transfer of information, or unauthorized tunneling (i.e., embedding of data types within data types), Mission Owners must disable or restrict unused or unnecessary physical and logical ports/protocols on information systems. false

**Check:** For dedicated infrastructure with a DOD Information Network (DODIN) connection, review the architecture diagrams. This includes all user and management plane traffic for Impact Levels 4, 5, and 6, as well as management plane traffic for Impact Level 2 if managed/monitored from within a DOD network. 

Verify that the virtual firewall access control lists that restrict traffic flow inbound and outbound to/from the cloud service to the DODIN connection comply with the boundary requirements. Verify that all traffic from the cloud service provider (CSP) enclave and other sources are blocked by these methods.

If the cloud service offering is not configured to prohibit or restrict the use of functions, ports, protocols, and/or services as defined in the Ports, Protocols, and Services Management (PPSM) Category Assurance List (CAL) and vulnerability assessments, this is a finding.

**Fix:** This applies to all Impact Levels.
FedRAMP Moderate, High.

For dedicated infrastructure with a DODIN connection (Impact Levels 2–6), configure the IaaS/PaaS virtual firewall that restricts traffic flow inbound and outbound to/from the cloud service to the DODIN connection and block all traffic from all other sources.

To ensure protocols and services are not blocked by the above configuration, register them along with their related UDP/TCP IP ports used by the SaaS service that will traverse the Defense Information Systems Network (DISN) in the DOD PPSM registry. This includes all user and management plane traffic for Impact Levels 4, 5, and 6, as well as management plane traffic for Impact Level 2 if managed/monitored from within a DOD network.

**References:** `CCI-000382`

---

### SRG-OS-000104

> Group ID: `V-259875`

<GroupDescription></GroupDescription>

#### The cloud service offering (CSO) must be configured to use DOD public key infrastructure (PKI) to uniquely identify and authenticate organizational users (or processes acting on behalf of organizational users).

> Rule ID: `SV-259875r958482_rule` | Severity: **MEDIUM**

**Description:** To ensure accountability and prevent unauthenticated access, organizational users must be identified and authenticated to prevent potential misuse and compromise of the system. Identity Federation requirements to enable Common Access Card (CAC) authentication of nonprivileged DOD users to cloud-hosted DOD (e.g., Infrastructure as a Service [IaaS] and Platform as a Service [PaaS]) or Software as a Service (SaaS) provided systems and services is the responsibility of the CSO, procuring DOD Component, or Program Office. Mission Owners may choose to use the cloud service providers (CSP's) CAC services (based on Level), use a DOD federated offering, or install a virtual Directory Service. For Impact Levels 2–5, the CSPs must have either a DOD PKI certificate or a DOD-approved External Certification Authority (ECA) medium-assurance PKI Certificate for each person who needs to communicate with DOD via encrypted email and for admin accounts. CSPs serving Level 6 systems will already have SIPRNet tokens/NSS PKI certificates for their system administrators by virtue of the connection to SIPRNet. Satisfies: SRG-OS-000104,SRG-OS-000377 false

**Check:** This is not applicable for Impact Level 2 public clouds with nonprivileged user access to publicly releasable information unless the information owner requires authenticated access.

Verify the CSO is configured to use DOD PKI to uniquely identify and authenticate organizational users (or processes acting on behalf of organizational users).

If the CSO does not use DOD PKI to uniquely identify and authenticate organizational users (or processes acting on behalf of organizational users), this is a finding.

**Fix:** This applies to Impact Level 4/5/6.
FedRAMP Moderate, High.

Mission Owners may choose to use the CSP's CAC services (based on level), use a DOD federated offering, or install a virtual Directory Service.

**References:** `CCI-000764`, `CCI-001954`

---

### SRG-OS-000342

> Group ID: `V-259876`

<GroupDescription></GroupDescription>

#### The Infrastructure as a Service (IaaS)/Platform as a Service (PaaS) must perform centralized logging to capture and store log records.

> Rule ID: `SV-259876r958754_rule` | Severity: **MEDIUM**

**Description:** Protection of log data includes ensuring log data is not accidentally lost or deleted. Backing up audit records to a different system or onto separate media than the system being audited on an organizationally defined frequency helps to ensure that in the event of a catastrophic system failure, the audit records will be retained. This helps to ensure that a compromise of the information system being audited does not also result in a compromise of the audit records. For cloud service environments, security information and event management (SIEM) or syslog capability must be implemented by both Boundary and Mission Computer Network Defense (CND) service providers to log audit information. This requirement can be met by the operating system continuously sending records to a centralized logging server. false

**Check:** If this is a Software as a Service (SaaS) implementation, this is not a finding.

Verify the IaaS/PaaS is configured to use centralized logging to capture and store the log records produced by the virtual machine (VM) management on the IaaS/PaaS.

If the IaaS/PaaS does not perform centralized logging to capture and store the log records produced by the VM management, this is a finding.

**Fix:** This applies to all Impact Levels.
FedRAMP - Does not match DOD requirement explicitly. Allows up to seven days for offloading. Moderate, High.

Implement a solution for centralized logging to capture and store the log records produced on the IaaS/PaaS.

**References:** `CCI-001851`

---

### SRG-OS-000368

> Group ID: `V-259877`

<GroupDescription></GroupDescription>

#### For Impact Levels 4 and 5, the Mission Owner must register all cloud-based services, their CSP/CSO, and connection method in the DISA Systems/Network Approval Process (SNAP) database Cloud Module.

> Rule ID: `SV-259877r958804_rule` | Severity: **MEDIUM**

**Description:** Register all cloud-based systems and applications, including the cloud service provider (CSP)/cloud service offering (CSO) name, Mission Cyberspace Defense (MCD), and connection method in the DISA SNAP database Cloud Module. SNAP registration will enable cloud services to be connected to the DISA Information Systems Network (DISN) and is crucial for situational awareness. SNAP registration documentation must include designating a certified cybersecurity service provider (CSSP) as the Tier 2 Computer Network Defense (CND). If applicable, the IP address of the cloud service must be configured in accordance with the Mission Owner's IP registration in SNAP so they do not repurpose an already registered IP for new services without updating the SNAP registration. SNAP: https://snap.dod.mil/gcap/home.do Connection Approval: https://www.disa.mil/Network-Services/Enterprise-Connections/Connection-Approval false

**Check:** If this is a Software as a Service (SaaS) Impact Level 2 implementation, this is not applicable.

Verify the CSP's cloud service offering is registered in SNAP for the connection approval, and it is the one being used in the cloud management portal.

If the IP address registered in SNAP is not configured for use with the approved cloud environment, this is a finding.

**Fix:** This applies to Impact Levels 4 and 5.
FedRAMP Moderate, High.

Register the Infrastructure as a Service (IaaS)/Platform as a Service (PaaS) CSP's cloud service offering in SNAP for the connection approval. 

Register the IP address that the cloud service offering uses for the cloud management portal.

**References:** `CCI-001764`

---

### SRG-OS-000368

> Group ID: `V-259878`

<GroupDescription></GroupDescription>

#### For Impact Level 6, the Mission Owner must process connection approval to the SIPRNet through the DISA classified connection approval process.

> Rule ID: `SV-259878r958804_rule` | Severity: **MEDIUM**

**Description:** The DOD Mission Owner systems/applications instantiated in these Impact Level 6 CSO enclaves will be assessed and authorized in the same way as any other DOD SIPRNet enclave connection in accordance with the DISA CPG. Approval for connection to the SIPRNet will be processed through the DISA classified connection approval process as with any other SIPRNet enclave. false

**Check:** If this is not Impact Level 6, this is not applicable.

Verify with the site personnel that the CSO is registered in SNAP.

If the Mission Owner does not process connection approval to the SIPRNet through the DISA classified connection approval process. this is a finding.

**Fix:** This applies to Impact Level 6.
FedRAMP High.

Register the IaaS/PaaS CSP's cloud service offering in SNAP for the connection approval. 

Register the IP address that the cloud service offering uses for the cloud management portal.

**References:** `CCI-001764`

---

### SRG-OS-000368

> Group ID: `V-259879`

<GroupDescription></GroupDescription>

#### The Mission Owner of the Infrastructure as a Service (IaaS)/Platform as a Service (PaaS) must remove orphaned or unused virtual machine (VM) instances.

> Rule ID: `SV-259879r958804_rule` | Severity: **MEDIUM**

**Description:** Control of program execution is a mechanism used to prevent execution of unauthorized programs. Some VMs may provide a capability that runs counter to the mission or provides users with functionality that exceeds mission requirements. This includes functions and services installed at the VM level. Some of the service and helper VMs, installed by default, may be harmful or may not be necessary to support essential organizational operations (e.g., key missions, functions). Removal of such VMs is not always possible; therefore, establishing a method of preventing VM activation is critical to maintaining a secure system baseline. Methods for complying with this requirement include restricting execution of VMs in certain environments while preventing execution in other environments or limiting execution of certain VM functionality based on organizationally defined criteria (e.g., privileges, subnets, sandboxed environments, or roles). false

**Check:** If this is a Software as a Service (SaaS) implementation, this is not a finding.

If cloud VMs are managed by the cloud service provider (CSP), verify separation requirements are addressed in the Service Level Agreement (SLA).

Verify the IaaS/PaaS is configured to disable or remove cloud services and helper VMs that are no longer required based on mission requirements.

If the IaaS/PaaS has not been configured to disable or remove cloud services and helper VMs that are no longer required based on mission requirements, this is a finding.

**Fix:** This applies to all Impact Levels.
FedRAMP Moderate, High.

For IaaS/PaaS, disable or remove cloud services and helper VMs that are no longer required based on mission requirements. Cloud services and VMs are added, removed, and updated by the cloud service portal management entity via the management plane.

**References:** `CCI-001764`

---

### SRG-OS-000370

> Group ID: `V-259880`

<GroupDescription></GroupDescription>

#### The Infrastructure as a Service (IaaS)/Platform as a Service (PaaS)/Software as a Service (SaaS) must register the service/application with the DOD DMZ/IAP allowlist for internet-facing inbound and outbound traffic.

> Rule ID: `SV-259880r958808_rule` | Severity: **MEDIUM**

**Description:** Register the service/application with the DOD DMZ/IAP allowlist for both inbound and outbound traffic if traffic will cross the internet access points (IAPs). Using an allowlist provides a configuration management method for allowing the execution of only authorized software, ports, protocols, and guest virtual machines (VMs). Using only authorized software decreases risk by limiting the number of potential vulnerabilities and preventing the execution of malware. Cloud approval documentation should include allowed approved ports and protocols communications, including allowlisted mission application traffic and services access from the internet via the Defense Information Systems Network (DISN) IAP. If all or a portion of the mission owners cloud-based Level 4/5 systems/applications connected through the BCAP are to be internet accessible, traffic is required to traverse the DISN IAPs. The system's/application's URLs/IP addresses must be registered with the DOD DMZ allowlist. Traffic that will typically traverse the IAP is management traffic for Level 2 off-premises systems/applications and for user plane traffic to/from Level 4/5 systems/applications that are internet-facing. Such traffic and IP addresses may be blocked if not registered in the allowlist. false

**Check:** Request the cloud service Provisional Authorization (PA) and registration documentation. 

Verify the IaaS/PaaS/software is registered in the service/application with the DOD DMZ/IAP allowlist for both inbound and outbound traffic when traffic will cross the IAPs. 

If the system/service/application is not registered with the DOD DMZ/IAP allowlist for both inbound and outbound internet-facing traffic, this is a finding.

**Fix:** This applies to all Impact Levels.
FedRAMP Moderate, High.

Coordinate with the cybersecurity service provider (CSSP) during cloud architecture development to ensure required security-relevant data will be accessible via the cloud service provider/cloud service offering, third-party security service subscription, and/or native application programming interface capability.

Register the IaaS/PaaS/SaaS service/application with the DOD allowlist for both inbound and outbound traffic. Configure the DOD allowlist with the ports and protocols needed to support applications and services used in the cloud environment.

**References:** `CCI-001774`

---

### SRG-OS-000404

> Group ID: `V-259881`

<GroupDescription></GroupDescription>

#### For storage service offerings, the Mission Owner must configure or ensure the cloud instance uses encryption to protect all DOD files housed in the cloud instance.

> Rule ID: `SV-259881r958870_rule` | Severity: **HIGH**

**Description:** Mission systems at all Impact Levels must have the capability for DOD data to be encrypted at rest with exclusive DOD control of encryption keys and key management. Some cloud service offerings (CSOs) may facilitate this by providing a Hardware Security Module (HSM) or offering customer-dedicated HSM devices as a service. CSOs that do not provide such a capability may require Mission Owners to use encryption hardware/software on the Defense Information Systems Network (DISN) or a cloud encryption service that provides DOD control of keys and key management. Some CSOs may offer a key management service that can suffice for management of customer keys by the customer while preventing cloud service provider (CSP) access to the keys. An NSA-validated CSP key management service is required. Data-at-rest (DAR) encryption with customer-controlled keys and key management protects the DOD data stored in CSOs with the following benefits:
- Maintains the integrity of publicly released information and websites at Level 2 where confidentiality is not an issue.
- Maintains the confidentiality and integrity of CUI at Levels 4 and 5 with the following benefits:
- Limits the insider threat vector of unauthorized access by CSP personnel by increasing the work necessary to compromise/access unencrypted DOD data. Mission Owners and their Authorizing Officials should consider the benefits of DAR encryption and a cryptography-based process for data destruction and/or spill remediation at Impact Level 2 in addition to the benefit of maintaining information integrity. false

**Check:** Unless the information owner requires encryption and KMS, for Impact Level 2 public cloud with nonprivileged user access to publicly releasable information, this is not applicable.

Verify the cloud storage service is configured to use encryption and KMS to protect all DOD files housed in the virtual storage service. 

If the cloud storage service is not configured to use encryption to protect all DOD files housed in the virtual storage service, this is a finding.

**Fix:** This applies to Impact Levels 4/5/6 and applies to Impact Level 2 where the Mission Owner has control of the environment.
FedRAMP Moderate, High.

Configure the cloud instance to use encryption to protect all DOD files housed in the virtual storage service.

**References:** `CCI-002475`

---

### SRG-OS-000438

> Group ID: `V-259882`

<GroupDescription></GroupDescription>

#### The Mission Owner of the Infrastructure as a Service (IaaS) or Platform as a Service (PaaS) must remove all upgraded or replaced software and firmware components that are no longer required for operation.

> Rule ID: `SV-259882r958938_rule` | Severity: **MEDIUM**

**Description:** Adversaries may exploit previous versions of software components that are not removed from the information system after updates have been installed. Some information technology products may remove older versions of software from the information system automatically. false

**Check:** If this is software as a service (SaaS), this is not a finding.

If the Mission Owner of the IaaS or PaaS has not removed all upgraded or replaced software and firmware components that are no longer required for operation, this is a finding.

**Fix:** This applies to all Impact Levels.
FedRAMP Moderate, High.

Remove all upgraded or replaced software and firmware components that are no longer required for operation from the IaaS/PaaS.

**References:** `CCI-002618`

---

### SRG-OS-000480

> Group ID: `V-259883`

<GroupDescription></GroupDescription>

#### The Mission owner must obtain Authorizing Official (AO) authorization for each cloud service offering (CSO) implemented in support of production or development environments prior to operational use.

> Rule ID: `SV-259883r959010_rule` | Severity: **MEDIUM**

**Description:** The Mission Owner must choose a CSO that fits the operational needs and also has a DOD Provisional Authorization (PA) at the information Impact Level corresponding to the categorization of the information to be processed or stored in the CSO. The PA and supporting documentation must then be leveraged by the Mission Owner's AO in granting the required Authority to Operate (ATO) for the mission system operating within the cloud. false

**Check:** Review the approval documentation. Verify the ATO indicates the component level AO has authorized the use of the CSO.

If the Mission Owner's AO has not authorized the use of the CSO, this is a finding.

**Fix:** This applies to all Impact Levels.
FedRAMP Moderate, High.

Obtain AO authorization for each CSO implemented in support of production or development environments prior to operational use.

**References:** `CCI-000366`

---

### SRG-OS-000480

> Group ID: `V-259884`

<GroupDescription></GroupDescription>

#### The Mission Owner must select and configure an Impact Level 2 FedRAMP authorized cloud service offering (CSO) when hosting unclassified, publicly releasable DOD information.

> Rule ID: `SV-259884r959010_rule` | Severity: **MEDIUM**

**Description:** FedRAMP Moderate is the minimum security baseline for all DOD cloud services. Components and Mission Owners may host unclassified, publicly releasable DOD information on FedRAMP Moderate approved cloud services. This type of CSO is known as Impact Level 2. They may also configure an offering from the DISA PA DOD Cloud Catalog at any Impact Level for use. Low Confidentiality Impact: Mission Owners will only publish, collect, store, or process low confidentiality impact (sensitivity) personally identifiable information (PII) in a CSO minimally possessing a FedRAMP Moderate Provisional Authority to Operate (P-ATO) listed on the FedRAMP Marketplace and a DOD Level 2 Provisional Authorization (PA), with Privacy Officer approval. false

**Check:** If the CSO implementation is categorized as Impact Level 4/5/6, this is not applicable.

Review the approval documentation. Verify the cloud service offering is listed in either the FedRAMP or DISA PA DOD Cloud Catalog when hosting unclassified, publicly releasable DOD information.

If unclassified, publicly releasable DOD information is being hosted in the IaaS/PaaS and the CSO is not listed in the FedRAMP Marketplace as FedRAMP moderate (at a minimum), or the DISA PA DOD Cloud Catalog, this is a finding.

**Fix:** This applies to Impact Level 2.
FedRAMP Moderate, High.

Select and configure an Impact Level 2 CSO listed in the FedRAMP Marketplace as FedRAMP moderate, or the DISA PA DOD Cloud Catalog, when hosting unclassified, publicly releasable DOD information.

**References:** `CCI-000366`

---

### SRG-OS-000480

> Group ID: `V-259885`

<GroupDescription></GroupDescription>

#### The Mission Owner must select and configure an Impact Level 4/5 cloud service offering (CSO) listed in the DISA Provisional Authorization (PA) DOD Cloud Catalog when hosting Controlled Unclassified Information (CUI).

> Rule ID: `SV-259885r959010_rule` | Severity: **HIGH**

**Description:** Impact Level 4 accommodates Controlled Unclassified Information (CUI). This information must be protected from unauthorized disclosure. Designating information as CUI is the responsibility of the data owner and their organization. Determining the appropriate Impact Level for a specific mission with CUI will be the responsibility of the mission AO. Impact Level 5 accommodates CUI that requires a higher level of protection as deemed necessary by the information owner, public law, or other government regulations. false

**Check:** If the implementation is categorized as Impact Level 2 or 6, this is not applicable.

Review the approval documentation and the DISA PA Cloud Catalog. For clouds hosting CUI information, verify the CSO is listed as Impact Level 4 or 5.

If CUI is being hosted in the Infrastructure as a Service (IaaS)/Platform as a Service (PaaS) and the CSO is not listed in the DISA PA DOD Cloud Catalog as Impact Level 4 or 5, this is a finding.

**Fix:** This applies to Impact Level 4/5.
FedRAMP Moderate, High.

For CUI information, select and configure a CSO listed in the DISA PA DOD Cloud Catalog for use with Impact Level 4/5 or higher. 

Specify in the Service Level Agreement (SLA) with the cloud service provider (CSP) and any third-party providers compliance with applicable STIG configurations.

**References:** `CCI-000366`

---

### SRG-OS-000480

> Group ID: `V-259886`

<GroupDescription></GroupDescription>

#### The Mission Owner must select and configure an Impact Level 5 cloud service offering (CSO) listed in the DISA Provisional Authorization (PA) DOD Cloud Catalog when hosting Unclassified National Security Information (U-NSI).

> Rule ID: `SV-259886r959010_rule` | Severity: **HIGH**

**Description:** U-NSI must be housed on an Impact Level 5 CSO. This is Unclassified National Security Systems (NSS) information and data. This is because NSS-specific security requirements are included in FedRAMP+. false

**Check:** If the implementation is categorized as Impact Level 2, 4, or 6, this is not applicable.

Review the approval documentation and the DISA PA Cloud Catalog. For clouds hosting U-NSI information, verify the CSO is listed as Impact Level 5.

If U-NSI is being hosted in the Infrastructure as a Service (IaaS)/Platform as a Service (PaaS) and the CSO is not listed in the DISA PA DOD Cloud Catalog as Impact Level 5, this is a finding.

**Fix:** This applies to Impact Level 5.
FedRAMP High.

For U-NSI information, select and configure a CSO listed in the DISA PA DOD Cloud Catalog for use with Impact Level 5.

Specify in the Service Level Agreement (SLA) with the CSP and any third-party providers compliance with applicable STIG configurations.

**References:** `CCI-000366`

---

### SRG-OS-000480

> Group ID: `V-259887`

<GroupDescription></GroupDescription>

#### The Mission Owners must select and configure a cloud service offering (CSO) listed in the DISA Provisional Authorization (PA) DOD Cloud Catalog at Level 6 when hosting classified DOD information.

> Rule ID: `SV-259887r959010_rule` | Severity: **HIGH**

**Description:** Impact Level 6 is reserved for the storage and processing of classified information. Impact Level 6 information up to the SECRET level must be stored and processed in a dedicated cloud infrastructure located in facilities approved for the processing of classified information, rated at or above the highest level of classification of the information being stored and/or processed. false

**Check:** If the implementation is categorized as Impact Level 2–5, this is not applicable.

Review the approval documentation and the DISA PA Cloud Catalog. Verify the CSO is listed in the DISA PA DOD Cloud Catalog. Verify the CSO is listed in the DISA PA DOD Cloud Catalog at Level 6 when hosting classified DOD information.

If classified DOD information is being hosted in the Infrastructure as a Service (IaaS)/Platform as a Service (PaaS) and the CSO is not listed in the DISA PA DOD Cloud Catalog, Impact Level 6, this is a finding.

**Fix:** This applies to Impact Level 6.
FedRAMP Moderate, High.

Configure a cloud service offering listed in the DISA PA DOD Cloud Catalog for use with Impact Level 6 when hosting classified DOD information. 

Specify in the Service Level Agreement (SLA) with the CSP and third-party providers compliance with applicable STIG configurations.

**References:** `CCI-000366`

---

### SRG-OS-000480

> Group ID: `V-259888`

<GroupDescription></GroupDescription>

#### The Mission Owner must add all applicable compensating controls and requirements in the Service Level Agreement (SLA)/contract with the cloud service provider (CSP) or third-party provider.

> Rule ID: `SV-259888r1056071_rule` | Severity: **MEDIUM**

**Description:** The Mission Owner may tailor the SLA/contract to include any of the controls in the Cloud Computing Mission Owner SRG Overview, Table-3-1, beyond the FedRAMP and DOD Baseline and FedRAMP+ security controls. The Mission Owner is responsible for defining any parameter values associated with any added security control. These values should be based on current DOD Risk Management Framework (RMF) Technical Advisory Group (TAG) values or Committee on National Security Systems Instruction (CNSSI) 1253 values. Any change of ownership involving a CSP, whether the primary CSP or an underlying CSP on which a cloud service offering (CSO) was built, will be reviewed by the DISA Authorizing Official (AO) to assess the impacts and risks associated with the continuation of the DOD Provisional Authorization (PA). Any existing Impact Level 5/National Security System (NSS) systems will have two years from publication date of the Cloud Computing SRG, V1R1, to update to the National Institute of Standards and Technology Special Publication 800-53 Rev 5. They must submit a Plan of Acton and Milestones (POA&M) within 30 days, outlining actions to move to the High baseline requirement. When new updates for the Cloud Computing SRG are published, the Mission Owners and their Authorizing Officials (AOs) must review the controls to determine if the risk is acceptable until such time the CSP is required to comply and/or include the required compliance in the SLA/contract. false

**Check:** Verify that the SLA with the CSP and third-party providers includes all required compliance items in the Cloud Computing Mission Owner SRG.

If the Mission Owner does not add all required compensating controls and requirements in the SLA/contract with the CSP or third-party provider, this is a finding.

**Fix:** This applies to all Impact Levels.
FedRAMP Moderate, High.

Review Sections 3.3.6 and 3.3.7 of the Cloud Computing Mission Owner SRG Overview. Document all applicable compensating controls and requirements in the SLA/contract with the CSP or third-party provider.

Update the SLA/contract with any revised guidance in Cloud Computing SRG updates. If there is a period of noncompliance, document the risk.

**References:** `CCI-000366`

---


> **Summary:** 17 rules across 17 groups
