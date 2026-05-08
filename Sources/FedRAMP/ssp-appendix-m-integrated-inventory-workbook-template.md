---
title: "SSP-Appendix-M-Integrated-Inventory-Workbook-Template"
type: reference
framework: fedramp
source_format: converted
created: 2026-04-05
tags:
  - fedramp
  - template
---

# SSP-Appendix-M-Integrated-Inventory-Workbook-Template

> Source: `SSP-Appendix-M-Integrated-Inventory-Workbook-Template.xlsx`

## INSTRUCTIONS 

| - System Security Plan  <br>   - Security Assessment Plan <br>   - Security Assessment Report | - Information System Contingency Plan <br>   - Monthly Continuous Monitoring |
| --- | --- |
| Where the above documents require an inventory, include or refer to this document. |  |
| Note: This document replaces the separate inventory templates or tabs that existed in the above documents. |  |
| Instructions: |  |
| 1. The cloud service provider (CSP) must use this inventory template to capture inventory items for all components of the cloud service offering (CSO) as part of preparing for a Readiness Assessment or initial authorization of a CSO for a FedRAMP authorization. <br> 2. This inventory format must be used for assessment testing efforts by an independent assessor (IA).  <br> 3. Once a CSO is in the Continuous Monitoring phase of its lifecycle, the CSP will continue to use this template to capture and submit inventory for monthly Continuous Monitoring efforts. Be sure to "save-as" the inventory to keep month-to-month submissions of the inventory. The CSP may either include the inventory as a tab within the monthly POA&M worksheet or may just keep the inventory as a separate worksheet. <br> 4. Optional fields should be left blank indicating no data instead of inserting "n/a,"" N/A," "na" or other variants. <br>  <br> The templates referenced in these instructions are available on the FedRAMP Documents and Templates web page. |  |
| FedRAMP requires that at each security assessment and for each monthly continuous monitoring submission, the CSO inventory aligns with the scan targets. FedRAMP requires tracking in the Integrated Inventory Workbook (IIW) by container asset class, meaning the container image in the container registry, not the runtime containers. If an assessment or continuous monitoring submission is submitted and the FedRAMP review of the raw scan results does not validate the IIW, the package will be rejected and analysis of the deficiencies will be provided. <br>  <br> Here is what FedRAMP requires for the Inventory: <br> 1. For any scanned inventory item that is not a container, we expect that Column A, the Unique Asset Identifier (most likely hostname, IP, or URL for web) can be verified or found within the scans provided by the CSP. Column B is the IP address. This means that for some inventory items Column A and Column B may both be the IP address(es) for the specific component. <br> 2. For containers, there needs to be an identifiable string in the scans that maps back to the image name/version number in use as identified in the container registry. That is normally the repository/image/version# or can be represented as a checksum. This is what should be then put into the Inventory (IIW), POA&M, and on any Deviations submitted. <br> a. In Column A, the cell must contain the Repository/Image Name/Version# as the Unique Asset Identifier.  <br> b. In Column B, the cell must contain the individual hash of the container in the registry for each of the containers in production that align to that Image Name/Version. |  |

## Inventory

| DELETE COLUMN A AND ROWS 3-12  BEFORE SUBMISSION | All Inventories | OS/Infrastructure Inventory | Software and Database Inventories | Any Inventory |
| --- | --- | --- | --- | --- |
|  | UNIQUE ASSET IDENTIFIER | NetBIOS Name | Software/ Database Vendor | Diagram Label |
| GUIDANCE | Unique Identifier associated with the asset as described on the instructions page of this template and used consistently across all CSO documentation. For OS/Infrastructure and Web Application Software, this is typically an IP address or URL/DNS name as the component is identified by the scans. For a database, it is typically an IP address, URL, or database name. For containers, it is the repository/image name/version number. | If available, state the NetBIOS name of the inventory item. This can be left blank if one does not exist, or it is a dynamic field. | Name of Container, Software or Database vendor. | Label of component as it is found on the boundary diagram in the SSP. It is understood that a single component on a diagram may represent many entries in the inventory |
| Valid Values | Must be unique. | Valid NetBIOS name. | If open source (e.g., there is no "vendor), enter "Open Source" as the vendor name. |  |
| Mandatory or Optional? | Mandatory for all inventory records. | Optional, unless used as Identifier in vulnerability scans or security assessments. | Mandatory for Software and Database. Leave blank for OS/Infrastructure. | Mandatory for all assets/components |
| OS/Infrastructure Example | 123.45.78.90 |  |  |  |
| OS/Infrastructure Example | 123.45.67.98 |  |  |  |
| OS/Infrastructure Example | 123.45.67.95 |  |  |  |
| OS/Infrastructure Example | 123.45.67.96 |  |  |  |
| Software Example | 123.45.78.400 |  | Acme Software |  |
| Database Example | 123.45.78.401 |  | Oracle |  |
| Container Example | sha256:1234abcd1234abcd1234abcd1234abcd1234abcd1234abcd1234abcd1234abcd |  | IronBank |  |

## Record of Changes

| Date | Description | Version | Author |
| --- | --- | --- | --- |
| 2016-05-18 00:00:00 | Original publication | 1 | FedRAMP |
| 2016-11-01 00:00:00 | Removed Main Inventory tab, Web Application Tab and Database Inventory Tab; replaced with a single Inventory tab. Simplified layout, added required multi-purpose inventory information, eliminated little-used fields, merged select fields and provided additional guidance and examples. | 2 | FedRAMP |
| 2016-11-07 00:00:00 | Minor fixes. Removed data validation from example rows, updated example rows, and updated Mandatory/Optional guidance for Column P (Software/ Database Vendor). | 2.1 | FedRAMP |
| 2017-03-09 00:00:00 | Document renamed from "FedRAMP Inventory Workbook Template" to "SSP ATTACHMENT 13 - FedRAMP Integrated Inventory Workbook Template" | 2.2 | FedRAMP |
| 2017-06-06 00:00:00 | Updated logo | 2.2 | FedRAMP |
| 2021-09-01 00:00:00 | Fixed conditional formartting error | 2.3 | FedRAMP |
| 2022-08-23 00:00:00 | Added Column (Column T) to add in tracking of Diagram Label from SSP Boundary Diagram and changed title to Appendix M | 2.4 | FedRAMP |
| 2023-06-30 00:00:00 | Updates made to align with other authorization package artifacts and address missing elements. | 3 | FedRAMP |
| 2024-12-06 00:00:00 | Updated to align with OMB Memo M-24-15 and remove JAB/PMO references | 3.1 | FedRAMP |

