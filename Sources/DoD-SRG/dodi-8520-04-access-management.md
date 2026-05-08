# DoDI 8520.04 — Access Management for DoD Information Systems

> **Source Type:** DoD Instruction (Authoritative — Read Only)
> **Issuing Component:** Office of the DoD Chief Information Officer
> **Effective:** September 3, 2024
> **Approved By:** Leslie A. Beavers, Acting DoD CIO
> **Releasability:** Cleared for public release
> **File:** 852004p.pdf

---

## Purpose

In accordance with the authority in DoD Directive (DoDD) 5144.02, this issuance:
- Establishes policy, assigns responsibilities, and provides direction for managing access to DoD information technology (IT) resources hosted by systems and system components by person and non-person entities (NPEs) in conformance with DoD Instruction (DoDI) 8500.01.
- Establishes policy and prescribes procedures for systems and system components — including information, control, and weapons systems — that host DoD IT resources.

---

## Section 1: General Issuance Information

### 1.1 Applicability

**Applies to:**
1. OSD, the Military Departments, the Office of the Chairman of the Joint Chiefs of Staff and the Joint Staff, the Combatant Commands, the Office of Inspector General of the Department of Defense, the Defense Agencies, the DoD Field Activities, and all other organizational entities within the DoD (referred to collectively as the "DoD Components").
2. The United States Coast Guard (USCG) for USCG-operated DoD systems and networks and for USCG systems and networks that directly affect the DoD Information Network (DoDIN) and DoD mission assurance in accordance with the January 17, 2017 Memorandum of Agreement between DoD and DHS.
3. Any digital environment and facility used to support access to digital resources where DoD or DoD-related data is stored, transited, or processed. At minimum: NIPRNET, SIPRNET, JWICS, Defense Research and Engineering networks, DoD Mission Partner Environment, contractor networks under the National Industrial Security Program, DoDIN-hosted systems, DoD data center-hosted systems, and closed operational networks.
4. DoD Components responsible for systems owned and operated by or on behalf of the DoD, including control systems, contractor-operated systems processing DoD-owned information, and commercial cloud services hosting DoD IT resources.

**Does NOT apply to:**
1. Systems processing, storing, or transmitting special access programs pertaining to intelligence sources, methods, and activities (but not including military operational, strategic, and tactical programs) under the authority of the DNI per Executive Order 13526.
2. Systems operated by the DoD Special Access Program (SAP) community.
3. Systems processing, storing, or transmitting Restricted Data and Formerly Restricted Data (Atomic Energy Act jurisdiction).
4. Systems in closed non-operational research, development, testing, and evaluation enclaves.

### 1.2 Policy

Access to DoD information systems will be managed to preserve DoD security. While DoD information systems should be as efficient and interoperable as possible, IT resource and system owners must follow the protocols in Section 3 and the procedures in this issuance for access management.

---

## Section 2: Responsibilities

### 2.1 DoD CIO
- Provides guidance for implementing access management processes, including maintaining the "DoD ICAM Reference Design."
- Coordinates with ICAM Executive Board, OSD Component heads, DoD Component heads, and Director ICAM Joint Program Integration Office.
- Develops and maintains requirements for DoD ICAM solutions, including federation of Component-level ICAM solutions.
- Develops and maintains requirements and standards for attribute definition, collection, verification, maintenance, protection, and publication.
- Approves DoD enterprise authoritative attribute services (Section 5).
- Maintains a list of approved DoD enterprise authoritative attribute services.
- Coordinates with CDAO to monitor migration to dynamic access.

### 2.2 Director, Defense Information Systems Agency (DISA)
- Establishes, operates, tests, and maintains DoD enterprise ICAM services.
- Provides cybersecurity services for DISA-operated enterprise ICAM services per DoDI 8530.01.
- Establishes, operates, tests, and maintains enterprise ICAM services managing NPE attributes.
- Coordinates with NSA/CSS to develop security requirements guides and STIGs for access management products.
- Provides subject matter expertise and technical support to DoD Components for access management implementation.

### 2.3 CDAO
- Establishes DoD-level data tagging standards.
- Develops policy incorporating requirements for tagging data sets and digital resources to support dynamic access.
- Establishes guidelines for digital policy implementation to support dynamic access decisions.
- Develops DoD enterprise digital policy to support dynamic access per DoDI 5200.48 and DoDM 5200.01.
- Develops governance framework for digital services, data, analytics, and AI capabilities.

### 2.4 Under Secretary of Defense for Intelligence and Security (USD(I&S))
- Coordinates with DoD CIO and intelligence/security enterprises to identify user attributes for sharing intelligence resources on DoDIN.
- Establishes DoD physical security requirements and interfaces for physical access to systems, facilities, and IT resources.
- Establishes information security and operations security policy for tagging data to support dynamic access.
- In coordination with CDAO, develops enterprise digital policy rules to support dynamic access per DoDI 5200.48 and DoDM 5200.01.

### 2.5 Director, NSA/Chief, CSS
- Coordinates with DISA to develop and maintain security requirements guides and STIGs for access management products.
- Supports DoD enterprise ICAM services through R&D and technical/security guidance.
- Provides systems engineering support and testing support, including threat assessments.
- Establishes cryptographic requirements and standards for ICAM solutions on National Security Systems.

### 2.6 Under Secretary of Defense for Personnel and Readiness (USD(P&R))
- Serves as DoD ICAM lead for person entity identities.
- Maintains DoD's enterprise person entity identity attribute repository and ICAM data management and distribution services.
- Establishes policy for collection, verification, and protection of person entity identity attributes centrally managed through DoD's enterprise repository.

### 2.7 Director, DoD Human Resources Activity (through DMDC)
- Establishes, operates, tests, and maintains enterprise ICAM services supporting management of person entity identity attributes.
- Maintains one or more data feed interfaces to provide person entity identity attributes to other DoD enterprise and Component-level ICAM services.
- Provides cybersecurity services for DMDC-operated enterprise ICAM services per DoDI 8530.01.

### 2.8 Under Secretary of Defense for Research and Engineering
- Ensures digital rules managing access to DoD scientific and technical information are implemented per DoDI 5230.24.

### 2.9 OSD and DoD Component Heads and Commandant, USCG
- Establish governance for access management, including approval processes for attribute services.
- Establish policy for access management addressing requirements in this issuance and Zero Trust policies.
- Coordinate with DoD CIO and ICAM Executive Board.
- Plan, program, and budget for access management including integrating DoD enterprise ICAM services.
- Ensure systems meet access requirements per Section 4.
- Approve Component- and USCG-level authoritative attribute services.
- Verify and maintain attribute values for DoD Component and USCG personnel.
- Participate in DoD ICAM review boards.
- Provide cybersecurity services for Component- and USCG-operated ICAM services per DoDI 8530.01.
- Coordinate with DoD CIO and CDAO to monitor and improve provisioning/de-provisioning or migration to dynamic access.

### 2.10 Chairman of the Joint Chiefs of Staff
- Identifies, reviews, and validates authorization requirements for systems supporting joint, allied, and coalition missions.
- Ensures Combatant Commanders comply with DoD information and personnel security policies regarding access and reporting unauthorized access.
- Coordinates implementation and integration of ICAM services for non-U.S. external mission partners.

---

## Section 3: IT Resource and System Protocols

### 3.1 IT and Digital Resource Protocol
- IT and digital resource owner is synonymous with the role of information system owner.
- IT and digital resource owners must implement ICAM access capabilities per Objectives 2.1 and 2.4 of the "DoD Zero Trust Strategy" and the users and data pillars of the "DoD Zero Trust Reference Architecture."
- IT and digital resource owners must document authorization requirements for all types of access per Section 4.
- IT and digital resource owners must define and document IT resources and activities subject to logging and monitoring requirements based on resource risk and mission function per Paragraph 4.4.b.

### 3.2 System Protocol
- System owners must implement technical controls to prevent escalation of privileges from general/functional privileged user access to IT privileged user access per an approved enterprise separation of duties (SOD) ruleset.
- Systems must authenticate users before granting access to any IT resources per DoDIs 8520.02 and 8520.03.
- For explicit access: system owners must implement provisioning and de-provisioning processes per 4.2.a.
- For dynamic access: system owners must only rely on attributes from approved attribute services per 4.3.
- For IT privileged users and functional privileged users (regardless of access method):
  1. Access granted must be based on least privilege, most restrictive access.
  2. System owners must retain traceability between the user and the approval process.
  3. Access and accounts must be traceable to a single user and must not be shared. Group accounts, when authorized by an authorizing official, must be traceable to an assigned sponsor.
  4. IT privileged users must use separate credentials and separate accounts when performing privileged actions.
  5. System owners must conduct access reviews per 4.2.a.(5).
- System owners must limit operating system and application service accounts to those needed to perform required functions:
  1. Service account access must be restricted to a specified time and disabled when not in use. NSA best practices: group managed service accounts, standalone managed service accounts, workload identities for cloud.
  2. System owners must regularly review audit logs for service accounts.
  3. Evidence of access approvals and reviews must be retained for at least 12 months beyond account deactivation for non-sensitive systems or as required by DoDI 8510.01.
  4. Access reviews for all user accounts and entitlements should occur every 12 months when required by the business or mission per DoDI 8510.01.

---

## Section 4: Implementation Procedures

### 4.1 Defining Access Requirements

#### a. IT Resource Hosting
- IT resources (data, applications, etc.) are hosted on IT systems.
- IT resource owner responsibilities: define, document, and identify authorization and access requirements; provide this information to the IT system owner.
- IT system owner responsibilities: implement and enforce authorization and access requirements provided by the IT resource owner; enforce applicable information security and operations security policies including DoDD 5205.02E, DoDIs 5200.02, 5200.46, 5200.48, 5210.83, and DoDM 5200.01.
- For dynamic access to IT resources hosted by multiple systems, the resource itself should be tagged so that appropriate policy rules can be enforced.

#### b. IT Resource Support
IT resource owners can support digital policies and data set level access controls by working with CDAO, USD(I&S), and functional leads to identify and register data holdings at the data set level.

#### c. IT Resource Owner Requirements
IT resource owners must:
1. Document authorization requirements for all types of access, applying Zero Trust guidance. Requirements may be based on laws, regulations, policies, contracts, interagency agreements, international agreements, or other sources. Applicable policies: DoDIs 5200.02, 5200.46, 5200.48, 5210.83, 8910.01, and DoDM 5200.01 Volumes 1-3.
2. Provide documented authorization and access requirements to owners of systems hosting the resource.
3. Review authorization and access requirements at least annually.

#### d. System Owner Requirements
System owners must document and enforce authorization requirements for all users aligned with resource requirements. Requirements must be approved at least annually.

**(1) Public Access**
Access to IT resources approved for public release per DoDIs 5230.09 and 5230.29 does not require authentication or authorization.

**(2) General Access**
General users must be authenticated per DoDIs 8520.02 and 8520.03 before accessing any IT resource not approved for public release.
- If the only authorization requirement is maintaining a record of who accessed the IT resource, no additional authorization is required.
- If access is authorized for the individual to whom the resource pertains (e.g., own health record, training record), the system must verify the user is that individual. System owners should use dynamic access.
- If access is based on specific defined user attributes (organizational affiliation, favorable background check, U.S. citizenship, active clearance), the system must implement processes to obtain and verify these attributes. System owners should use dynamic access and approved attribute services.
- If access requires specific approvals or locally defined attributes, the system must implement processes to provision entitlements using explicit access.

**(3) Privileged Access**
System owners must define and document roles, profiles, transactions, and activities restricted to functional and IT privileged users.

*Functional Privileged Users:* Assigned a specific position or duty within an application (e.g., approver in financial management system). Access must be traceable to a single person or NPE. When auditing of provisioning is required, system owners must provision using explicit access with an automated account provisioning system.

*IT Privileged Users (system administrators):* Have access to manage IT systems and can read/write/change/download/upload files. Must authenticate using credentials reserved for privileged actions. Must be provisioned using explicit access. Access must be traceable to a single person or NPE.

*Emergency Accounts:* Grants an already privileged user temporary, exception-based, elevated access under emergency or extraordinary circumstances.
1. Organizations must establish and document policies and procedures for emergency access use.
2. Emergency accounts must be provisioned using explicit access and protected at the same or higher level.
3. Use must be authorized through explicit access using an auditable process; approved by a designated supervisor whenever possible, or within 8 hours if circumstances do not allow pre-approval; traceable to a single person.

**(4) Records Management Access**
Records management users must be authorized to access IT resources to perform functions including records schedule updates, rescheduling, holds, transfer, destruction, and reporting.

### 4.2 Access Requirements

#### a. Explicit Access
Explicit access requires provisioning authorizations (entitlements) to entities for specific access rights to IT resources. Establishes a "by name" account with authorizations.

**(1) Provisioning**
IT resource owners must define and document approvals necessary for entitlement provisioning, including who must approve (e.g., supervisor or security officer). System owners must implement approvals as required.

**(2) Traceability**
The auditable record must include: name and identifier of the user, date of approval, names and positions of approving individuals.
Approval information must be retained per the authorization to operate documentation.
System owners should adopt ICAM provisioning tools, such as the DoD Enterprise Automated Account Provisioning Service, **by end of Fiscal Year 2028**.

**(3) De-Provisioning**

*IT Systems Integrated to Enterprise ICAM Person Attribute Services:*
- Routine events (role removal, voluntary departure, contract termination):
  - Network access: de-provisioned within 24 hours of when known to DoD Enterprise ICAM ecosystem.
  - Physical access: de-provisioned by end of business day.
  - If notification occurs more than 5 business days after known: both network and physical access must be de-provisioned within 1 business day of notification.
- High-risk and emergency events (involuntary departure, unauthorized system use):
  - CAC must be confiscated and revoked per DoDM 1000.13 Volume 1.
  - Access must be de-provisioned no later than 2 business days after known to DoD Enterprise ICAM ecosystem.

*All Other IT Systems:*
- Routine events: Same timelines as above (24 hours network, end of business day physical).
- High-risk events: CAC confiscated and revoked; access de-provisioned no later than 2 business days after effective date.

**(4) Separation of Duties (SOD)**
System owners and IT resource owners must define and document SOD requirements, including incompatible activities and transactions (e.g., creating an invoice AND authorizing payment = SOD violation).
- Must implement automated mechanisms to verify that requests to provision conflicting entitlements require additional approvals and auditable documentation.
- Must support enforcement of SOD requirements across systems by:
  1. Mapping local system entitlements to enterprise roles.
  2. Providing local system entitlement information to centralized auditing systems.

**(5) Access Reviews**
System owners and IT resource owners must perform and document access reviews:
- Functional privileged users: at least every **12 months**
- IT privileged users: at least every **3 months**

Access reviews must:
1. Include people authorized to use emergency accounts.
2. Verify approvals are in place for all entitlements provisioned to active accounts.
3. Include review of SOD conflicts.
4. Include supervisor/system manager statement asserting each user has specific need-to-know and requires entitlements to perform their job.

Access identified during reviews that exceeds what is authorized must be suspended or terminated within **2 business days** of notice to the system owner.

Documentation related to access reviews must be retained for at least **12 months beyond account deactivation** and provided to auditors upon request.

#### b. Dynamic Access
Authorization is determined when the entity requests access to the IT resource based on the digital policy rule for the resource and user/environment attribute values. Does not require provisioning entitlements or accounts.

**(1) Digital Policy Rules**
IT resource owners must define digital policy rules for dynamic access. Rules must:
1. Specify user and environmental attributes and values that must be true to grant access.
2. Include any applicable SOD requirements.
3. Include any applicable provisions regarding functional or IT privileged users.
Where rules are defined at the IT resource level, resources must be tagged with a reference to the appropriate digital policy rule.

**(2) User Attributes**
System owners must obtain user attributes from approved authoritative attribute services per 4.3, and ensure attribute values have been verified, protected from unauthorized alteration, and meet acceptable freshness.

**(3) Environmental Attributes**
System owners must obtain environmental attributes from sources that protect those attributes to prevent unauthorized alteration.

#### c. Hybrid Access
Systems may use a combination of explicit and dynamic access processes — either through automated verification of user attributes as part of provisioning, or by incorporating provisioned entitlements with additional user/environmental attributes.

For automated provisioning/de-provisioning in hybrid access:
- Subscribe to Enterprise ICAM person identity and credentialing attribute distribution services.
- Re-verify critical access information (background investigation, clearance, need-to-know) **daily**.
- Act to de-provision entitlements within **48 hours** when changes in person attributes dictate.

### 4.3 Authoritative Attribute Service Requirements

#### a. General
- Authoritative attribute services must be approved for use at the DoD enterprise or DoD Component level.
- Owners of attribute services that obtain attributes from other systems must verify that feeder systems enforce requirements in this issuance.
- The authoritative source for person entity attributes is DMDC's "Department of Defense Enterprise Identity Attribute Service (EIAS) Person Entity Attribute Data Set Standard."

#### b. Accuracy
- Owners must define and document processes used to verify attribute values, including refresh frequency.
- Owners must make freshness information (last date data was verified) available to relying parties.

#### c. Integrity
- Attribute services must implement controls to protect attribute values commensurate with the risk level of IT resources that can be accessed (e.g., if attributes authorize access to moderate risk resources, the attribute service must be considered moderate for integrity).
- Attributes must be protected in transit to ensure data integrity and confidentiality.

#### d. Privacy and Confidentiality
- Attribute services must register relying parties and authenticate requests for attribute values.
- Must complete privacy impact assessments and obtain appropriate System of Records Notices required by the Privacy Act of 1974 (5 U.S.C. 552a), DoDI 1000.30, and DoDM 5400.11 Volume 2.

#### e. Availability
- Must document percent uptime standard either in published system documentation or through service level agreements.
- Should be modified to expose APIs that permit "just-in-time" queries for entity attributes.

### 4.4 Authorization Requirements

#### a. Access Control
System and IT resource owners must implement an authorization mechanism in addition to authentication per DoDI 8520.03. The authorization mechanism must enforce explicit, dynamic, or hybrid access methodologies and must support federated external mission partners.

#### b. Activity Logging
Per OMB Memorandum M-21-31, system owners in conjunction with IT resource owners must:
1. Define logging function requirements per Event Logging Tier 3.
2. Develop policy and procedures to communicate events based on IT resource risk and mission response process.

Audit logs must include:
- Logged and monitored system access by IT privileged users, including emergency access.
- All successful and unsuccessful requests to access identified IT resources: identity of user, IT resource requested, date and time, whether access was granted. For dynamic access, logs must also include attributes used by the digital policy.

System owners must:
- Review audit logs for inappropriate and suspicious activity **at least weekly**.
- Report security incidents and violations per DoDD 5210.50, DoDI 5200.48, and DoDM 5200.01.
- Make access logs available to support monitoring for potential insider threats or unauthorized access.
- Ensure system and IT resource privileged users **cannot modify, add, or delete audit logs** that track their activity.

#### c. Operationally Constrained Environments
Systems that cannot implement network-based access control mechanisms must implement compensating controls (physical access controls, personnel controls, or localized access control).

### 4.5 NPE Access

#### a. NPEs with Static Connectivity
NPEs may interact with each other based on static connection agreements. These agreements must include authorization information for IT resource access. NPE access must be logged and monitored for unusual behavior.

#### b. Endpoint Device Authorization
Authorization of endpoint devices may be through provisioned explicit access or dynamic access. For dynamic access, system owners must define and enforce digital policy rules for authorization of the endpoint based on verifiable endpoint device attributes (type, management state, network location, geolocation).

#### c. NPEs Acting as Users
NPEs may be processes acting as general users, IT privileged users, or functional privileged users (service accounts, monitoring tools, unattended robotic process automation bots).
1. NPEs acting as users must be authorized using the same access methodologies as person users (4.2 and 4.4).
2. NPEs must be provisioned with their own identities, credentials through DoD PKI NPE issuance portal, and unique network or application accounts. NPEs must not be assigned an identifier that also maps to a person entity.
3. Unique identifiers: NPEs acting as users must not contain system accounts/credentials with unique 10-digit or 16-digit identifiers starting with 1 through 9 (DoD ID numbers per DoDI 1000.30 and FIPS 201).
4. Where NPE attributes are not available, NPEs must be provisioned using explicit access even if person entities use dynamic access.
5. NPEs must not be used to circumvent SOD policy. Access to NPEs should be restricted to functional privileged and user accounts without conflicting SOD roles.

---

## Section 5: Enterprise Authoritative Attribute Services Approval Processes

Enterprise authoritative attribute services must be approved for use by DoD systems. Approval process:

1. **Sponsor compiles:** description of the attribute service; list of available attributes (name, format, possible values); how the service meets accuracy, integrity, privacy/confidentiality, and availability requirements per 4.3; supported interfaces; use restrictions; and (if DoD Component-operated) ATO status, cybersecurity services provider, and operational testing results including risk assessment per DoDI 8510.01.
2. **Sponsor submits** required information to the DoD CIO ICAM lead.
3. **DoD CIO ICAM lead** coordinates review with appropriate ICAM governance body.
4. **If recommended for approval:** DoD CIO ICAM lead develops draft approval memorandum including any restrictions.
5. **DoD CIO reviews** and signs or disapproves.
6. **If approved:** DoD CIO ICAM lead provides approval memorandum to sponsor and adds to the published list. Information is posted on https://cyber.mil/icam/.

Full list of approved enterprise authoritative attribute services: https://intelshare.intelink.gov/sites/dodcioicamdocs

---

## Glossary

| Term | Definition |
|---|---|
| access review | A process used to periodically verify that only legitimate users have access to systems and IT resources. |
| attribute service | A data repository where authorization attributes are collected and managed for a set of entities recognized as having the authority to verify the association of attributes to an identity, accessible only through a service that both provisions and serves up authorization attributes. |
| authentication | The process by which a claimed identity is confirmed using a credential. |
| authorization | The process by which a request to perform an action on an IT resource is decided, typically based on a policy. |
| digital policy rule | A rule that defines the combination of attributes under which access may take place. |
| dynamic access | The process of determining authorization when the entity requests access to the IT resource based on the digital policy rule for the IT resource and user and environment attribute values. |
| entitlement | Authorization to access one or more IT resources within an information system. |
| entity | A person, role, organization, device, or process that requests access to and uses IT resources. |
| environmental attribute | A data element that describes the situation at the time of the transaction, such as time of day, external event occurrence, physical location of the entity making the request, or threat level. |
| explicit access | The process of provisioning authorizations, known as entitlements, to entities for specific access rights to IT resources. |
| functional privileged user | A user who has approval authorities within workflows. Roles are specific to a mission area, such as human resources or finance. |
| general user | A user who does not have elevated privileges of a functional privileged user or IT privileged user. |
| IT privileged user | A user authorized to perform security-relevant functions that ordinary users are not authorized to perform. Includes system, network, or database administrators, security administrators, developers, configuration managers, release managers, and security analysts who manage audit logs. |
| IT resource | All equipment, networks, hardware, software, technical knowledge, expertise, and other resources held, owned, or used by or on behalf of the DoD. |
| mission partner | An organization with which the DoD cooperates to achieve national goals, including other U.S. Government departments/agencies, State and local governments, allies, coalition members, host nations, multinational organizations, NGOs, and the private sector. |
| NPE | A physical device, virtual machine, system, service, or process that is assigned an identifier and issued credentials to support authentication and authorization. |
| privileged user | A user authorized to perform security-relevant functions that ordinary users are not authorized to perform. |
| provisioning | Linking and unlinking access permissions for a person or NPE to a protected IT resource. |
| service account | An NPE account created to execute applications and run automated services and other processes. |
| SOD (separation of duties) | Requirement to prevent a single user from having incompatible access that could enable fraud, error, or abuse. |

---

## Key References
- DoDD 5144.02 — DoD CIO authority
- DoDI 8500.01 — Cybersecurity
- DoDI 8510.01 — Risk Management Framework for DoD Systems
- DoDI 8520.02 — Public Key Infrastructure and PK Enabling
- DoDI 8520.03 — Identity Authentication for Information Systems
- DoDI 8530.01 — Cybersecurity Activities Support to DoD Information Network Operations
- FIPS 201 — Personal Identity Verification (PIV)
- OMB Memorandum M-21-31 — Federal Government Investigative and Remediation Capabilities
- DoD Zero Trust Strategy (October 2022)
- DoD Zero Trust Reference Architecture (July 2022)
- DoD ICAM Strategy (March 2020)
- CNSS Instruction 4009 — CNSS Glossary
