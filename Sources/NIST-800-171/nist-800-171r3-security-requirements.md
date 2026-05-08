---
title: "NIST SP 800-171 Rev 3 Security Requirements"
type: reference
framework: nist-800-171
source_format: scraped
source_url: "https://csrc.nist.gov/pubs/sp/800/171/r3/final"
created: 2026-04-05
tags:
  - nist-800-171
  - cui-protection
  - rev3
---

# NIST SP 800-171 Rev 3 — Protecting Controlled Unclassified Information in Nonfederal Systems and Organizations

> Source: NIST Special Publication 800-171 Revision 3 (May 2024)
> Supersedes: SP 800-171 Rev 2
> Authors: Ron Ross, Victoria Pillitteri (NIST)

## Overview

This publication provides recommended security requirements for protecting the confidentiality of Controlled Unclassified Information (CUI) when the information is resident in nonfederal systems and organizations. The requirements apply to nonfederal system components that process, store, transmit CUI, or protect such components.

## 3.1 Access Control

### 03.01.01 Account Management

Define the types of system accounts allowed and prohibited. Create, enable, modify, disable, and remove system accounts in accordance with policy, procedures, prerequisites, and criteria.

### 03.01.02 Access Enforcement

Enforce approved authorizations for logical access to CUI and system resources in accordance with applicable access control policies.

### 03.01.03 Information Flow Enforcement

Enforce approved authorizations for controlling the flow of CUI within the system and between connected systems.

### 03.01.04 Separation of Duties

Identify the duties of individuals requiring separation. Define system access authorizations to support separation of duties.

### 03.01.05 Least Privilege

Allow only authorized system access for users (or processes acting on behalf of users) that is necessary to accomplish assigned organizational tasks.

### 03.01.06 Least Privilege — Privileged Accounts

Restrict privileged accounts on the system to [organization-defined personnel or roles]. Require that users with privileged accounts use non-privileged accounts when accessing non-security functions.

### 03.01.07 Least Privilege — Privileged Functions

Prevent non-privileged users from executing privileged functions. Log the execution of privileged functions.

### 03.01.08 Unsuccessful Logon Attempts

Enforce a limit of [organization-defined number] consecutive invalid logon attempts by a user during a [organization-defined time period].

### 03.01.09 System Use Notification

Display a system use notification message with privacy and security notices consistent with applicable CUI rules before granting access to the system.

### 03.01.10 Device Lock

Prevent access to the system by [initiating a device lock after organization-defined time period of inactivity; requiring the user to initiate a device lock].

### 03.01.11 Session Termination

Terminate a user session automatically after [organization-defined conditions or trigger events requiring session disconnect].

### 03.01.12 Remote Access

Establish usage restrictions, configuration requirements, and connection requirements for each type of allowable remote system access. Authorize each type of remote system access prior to establishing such connections.

### 03.01.16 Wireless Access

Establish usage restrictions, configuration requirements, and connection requirements for each type of wireless access to the system. Authorize each type of wireless access prior to establishing such connections.

### 03.01.18 Access Control for Mobile Devices

Establish usage restrictions, configuration requirements, and connection requirements for mobile devices. Authorize the connection of mobile devices to the system. Implement full-device or container-based encryption.

### 03.01.20 Use of External Systems

Prohibit the use of external systems unless the systems are specifically authorized. Establish security requirements to be satisfied on external systems prior to allowing use.

### 03.01.22 Publicly Accessible Content

Train authorized individuals to ensure that publicly accessible information does not contain CUI. Review the content on publicly accessible systems for CUI and remove such information.

---

## 3.2 Awareness and Training

### 03.02.01 Literacy Training and Awareness

Provide security literacy training to system users as part of initial training for new users and [organization-defined frequency] thereafter. Update security literacy training content [organization-defined frequency] and following [organization-defined events].

### 03.02.02 Role-Based Training

Provide role-based security training to organizational personnel before authorizing access to the system or CUI, before performing assigned duties, and [organization-defined frequency] thereafter.

---

## 3.3 Audit and Accountability

### 03.03.01 Event Logging

Specify the following event types selected for logging within the system: [organization-defined event types]. Review and update the event types selected for logging [organization-defined frequency].

### 03.03.02 Audit Record Content

Include the following content in audit records: what type of event occurred; when the event occurred; where the event occurred; source of the event; outcome of the event; identity of individuals, subjects, objects, or entities associated with the event.

### 03.03.03 Audit Record Generation

Generate audit records for the selected event types and audit record content specified. Retain audit records for a time period consistent with the records retention policy.

### 03.03.04 Response to Audit Logging Process Failures

Alert organizational personnel or roles within [organization-defined time period] in the event of an audit logging process failure. Take the following additional actions: [organization-defined additional actions].

### 03.03.05 Audit Record Review, Analysis, and Reporting

Review and analyze system audit records [organization-defined frequency] for indications and the potential impact of inappropriate or unusual activity. Report findings to organizational personnel or roles. Analyze and correlate audit records across different repositories.

### 03.03.06 Audit Record Reduction and Report Generation

Implement an audit record reduction and report generation capability that supports audit record review, analysis, reporting requirements, and after-the-fact investigations of incidents. Preserve the original content and time ordering of audit records.

### 03.03.07 Time Stamps

Use internal system clocks to generate time stamps for audit records. Record time stamps for audit records that meet [organization-defined granularity of time measurement].

### 03.03.08 Protection of Audit Information

Protect audit information and audit logging tools from unauthorized access, modification, and deletion. Authorize access to management of audit logging functionality to only a subset of privileged users or roles.

---

## 3.4 Configuration Management

### 03.04.01 Baseline Configuration

Develop and maintain under configuration control, a current baseline configuration of the system. Review and update the baseline configuration of the system [organization-defined frequency] and when system components are installed or modified.

### 03.04.02 Configuration Settings

Establish, document, and implement the following configuration settings for the system that reflect the most restrictive mode consistent with operational requirements: [organization-defined configuration settings].

### 03.04.03 Configuration Change Control

Define the types of changes to the system that are configuration-controlled. Review proposed configuration-controlled changes to the system, and approve or disapprove such changes with explicit consideration for security impacts.

### 03.04.04 Impact Analyses

Analyze changes to the system to determine potential security impacts prior to change implementation. Verify that the security requirements for the system continue to be satisfied after the system changes have been implemented.

### 03.04.05 Access Restrictions for Change

Define, document, approve, and enforce physical and logical access restrictions associated with changes to the system.

### 03.04.06 Least Functionality

Configure the system to provide only mission-essential capabilities. Prohibit or restrict use of the following functions, ports, protocols, connections, and services: [organization-defined functions, ports, protocols, connections, and services].

### 03.04.08 Authorized Software — Allow by Exception

Identify software programs authorized to execute on the system. Implement a deny-all, allow-by-exception policy for the execution of authorized software programs on the system.

### 03.04.10 System Component Inventory

Develop and document an inventory of system components. Review and update the system component inventory [organization-defined frequency]. Update the system component inventory as part of installations, removals, and system updates.

### 03.04.11 Information Location

Identify and document the location of CUI and the system components on which the information is processed and stored. Document changes to the system or system component location where CUI is processed and stored.

### 03.04.12 System and Component Configuration for High-Risk Areas

Issue systems or system components with the following configurations to individuals traveling to high-risk locations: [organization-defined system configurations]. Apply the following security requirements to the systems or components when the individuals return from travel: [organization-defined security requirements].

---

## 3.5 Identification and Authentication

### 03.05.01 User Identification and Authentication

Uniquely identify and authenticate system users, and associate that unique identification with processes acting on behalf of those users. Re-authenticate users when [organization-defined circumstances or situations requiring re-authentication].

### 03.05.02 Device Identification and Authentication

Uniquely identify and authenticate [organization-defined devices or types of devices] before establishing a system connection.

### 03.05.03 Multi-Factor Authentication

Implement multi-factor authentication for access to privileged and non-privileged accounts.

### 03.05.04 Replay-Resistant Authentication

Implement replay-resistant authentication mechanisms for access to privileged and non-privileged accounts.

### 03.05.05 Identifier Management

Receive authorization from organizational personnel or roles to assign an individual, group, role, service, or device identifier. Select and assign an identifier that identifies an individual, group, role, service, or device.

---

## 3.6 Incident Response

### 03.06.01 Incident Response Testing

Test the incident response capability for the system [organization-defined frequency] using [organization-defined test scenarios].

### 03.06.02 Incident Response Plan

Prepare and maintain a system incident response plan that addresses the following: incident identification, analysis, containment, eradication, and recovery.

### 03.06.03 Incident Response Training

Provide incident response training to system personnel [organization-defined frequency] and when system changes occur.

### 03.06.04 Incident Handling

Implement incident handling capability for security incidents that includes preparation, detection and analysis, containment, eradication, and recovery.

### 03.06.05 Incident Monitoring

Monitor and document information system security incidents [organization-defined frequency] and ensure that information system incident information is provided to organizational incident response team.

---

## 3.7 Maintenance

### 03.07.01 System Maintenance

Perform maintenance on system components in accordance with manufacturer specifications and organizational requirements. Document all maintenance activities.

### 03.07.02 Maintenance Tools

Inspect maintenance tools and equipment for improper or unauthorized modifications prior to use. Maintain a record of maintenance tools and equipment.

### 03.07.03 Maintenance Personnel

Ensure that individuals performing maintenance and diagnostic activities on the system have required access authorizations. Supervise the maintenance activities of individuals who do not possess the required access authorizations.

---

## 3.8 Media Protection

### 03.08.01 Media Access

Restrict access to system media to [organization-defined personnel or roles].

### 03.08.02 Media Labeling

Label all removable information system media and information system output indicating the maximum classification level and any other markings or restrictions.

### 03.08.03 Media Storage

Physically control and securely store removable media in [organization-defined secure storage location].

### 03.08.04 Media Transmission

Control the use of removable media on system components. Prohibit the use of portable storage devices in organizational systems unless the devices are specifically authorized.

---

## 3.9 Personnel Security

### 03.09.01 Position Categorization

Identify and document the organizational positions associated with the system and the security responsibilities assigned to those positions.

### 03.09.02 Personnel Screening

Ensure that individuals assigned to the system meet [organization-defined personnel security requirements].

### 03.09.03 Personnel Termination

Upon termination of employment, disable system access within [organization-defined time period] and retrieve all system-related property within [organization-defined time period].

### 03.09.04 Personnel Transfer

Review and confirm ongoing security responsibilities and access requirements upon transfer or reassignment of individuals to different positions within the organization.

### 03.09.05 Access Agreements

Require individuals to sign appropriate access agreements prior to being granted access to the system.

### 03.09.06 Conflicting Duties

Restrict individuals with conflicting duties or interests from exercising authority in security-relevant matters.

---

## 3.10 Physical Protection

### 03.10.01 Physical Entry and Exit

Control physical entry and exit to the facility in which the system resides by [organization-defined entry and exit controls].

### 03.10.02 Facility Monitoring

Monitor physical access to the system to detect and respond to physical security incidents.

### 03.10.03 Visitor Access

Restrict and manage physical access of visitors to the facility by requiring visitors to present valid identification.

---

## 3.11 Planning

### 03.11.01 System Security Plan

Develop, maintain, and implement a system security plan for the system in accordance with the CUI requirements and organizational risk.

---

## 3.12 Risk Assessment

### 03.12.01 Risk Assessment

Conduct a risk assessment of the system [organization-defined frequency] using [organization-defined risk assessment methodology].

### 03.12.02 Plan of Action and Milestones

Develop and maintain a plan of action and milestones for findings and vulnerabilities identified during risk assessments, security control assessments, and continuous monitoring activities.

---

## 3.13 System and Communications Protection

### 03.13.01 Information in Transit

Protect the confidentiality and integrity of CUI in transit by encrypting CUI or employing approved cryptography.

### 03.13.02 Boundary Protection

Manage information security for the system interfaces by [organization-defined boundary protection measures].

### 03.13.03 Access Control for Removable Media

Restrict the use of removable media by [organization-defined removable media restrictions].

### 03.13.04 Cryptographic Controls

Employ cryptographic mechanisms to protect the confidentiality and integrity of CUI when it is in transit and when it is stored.

### 03.13.05 Secure Name Resolution

Prevent the installation of unauthorized or unapproved wireless access points and detect the presence of unauthorized or unapproved wireless access points on the system.

### 03.13.06 Architecture and Provisioning for Name Resolution

Architect system to support secure name resolution services and implement security controls for name resolution services.

### 03.13.07 Boundary Protection — Information Security Policy and Procedures

Manage information security for system interfaces by defining and documenting the allowed information and control of flow of information between the system and other systems.

### 03.13.08 Transmission Confidentiality and Integrity

Implement cryptographic mechanisms to detect and prevent unauthorized modification of information in transit.

### 03.13.09 Terminate Network Connections

Terminate network connections associated with communications sessions at the end of sessions or after [organization-defined time period] of inactivity.

### 03.13.10 Separation of System Components

Separate user-facing system components from system components that process and store CUI to reduce the number of direct attacks against CUI.

### 03.13.11 Cryptographic Protection

Implement the following types of cryptography when used to protect the confidentiality of CUI: [organization-defined types of cryptography].

### 03.13.12 Security Function Isolation

Isolate security functions from nonsecurity functions by means of an isolated execution environment.

### 03.13.13 Removal of Information from System Media

Implement appropriate controls to ensure that CUI is removed from system media prior to disposal or release for reuse.

---

## 3.14 System and Information Integrity

### 03.14.01 Flaw Remediation

Identify, report, and correct system flaws in a timely manner. Prioritize flaws and implement patches according to risk assessments.

### 03.14.02 Malicious Code Protection

Implement malicious code protection mechanisms to detect and eradicate malicious code. Update malicious code protection mechanisms [organization-defined frequency].

### 03.14.03 Security Monitoring and Tuning

Monitor and tune security functions to ensure appropriate system and information protection.

### 03.14.04 Unauthorized Software — Detect

Monitor the system for the presence of unauthorized software using [organization-defined detection methods and tools].

### 03.14.05 Software, Firmware, and Information Integrity

Employ integrity checking mechanisms to verify the integrity of software, firmware, and information.

---

## 3.15 System and Services Acquisition

### 03.15.01 System Development Life Cycle

Acquire, develop, and maintain system components using a system development life cycle that incorporates security requirements and controls.

### 03.15.02 Security Requirements for Contractors

Include security requirements in acquisition contracts for external providers and monitor contractor compliance with security requirements.

### 03.15.03 Software and Information Integrity

Develop, implement, and maintain secure coding standards and practices for system components and applications.

---

## 3.16 Supply Chain Risk Management

### 03.16.01 Supply Chain Risk Assessment

Assess the risk to the organization and the system from potential supply chain threats.

### 03.16.02 Supply Chain Risk Management Strategy

Implement a supply chain risk management strategy for the system and organizational systems.

### 03.16.03 Supplier Agreements

Require suppliers to meet security requirements in supplier agreements and monitor supplier compliance.

---

## Available Resources

- PDF: https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-171r3.pdf
- HTML: https://nvlpubs.nist.gov/nistpubs/SpecialPublications/800-171r3/NIST.SP.800-171r3.html
- DOI: https://doi.org/10.6028/NIST.SP.800-171r3
- Assessment Procedures: SP 800-171A Rev 3
