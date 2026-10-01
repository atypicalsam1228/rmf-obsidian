# FedRAMP 20x Class C — SCG: Secure Configuration Guide

**Source:** https://fedramp.gov/2026/reference/20x/c/secure-configuration-guide/  
**Scraped:** 2026-08-03  
**Rules:** 9  
**Last Updated:** 2026-06-24

Legacy mapping: Replaces CM-6 (Configuration Settings), CM-7 (Least Functionality), and traditional STIG/CIS baseline documentation requirements. Introduces provider-published Secure Configuration Guide as a customer-facing deliverable.

---

## Key Change: Provider-Published Configuration Guide (Customer-Facing)

Legacy FedRAMP: Providers document their own configuration baselines in the SSP and demonstrate STIG/CIS compliance to assessors. Agencies received no standardized configuration guidance document.

FedRAMP 20x: Providers must maintain and share a **Secure Configuration Guide** with agencies covering how to securely access, configure, operate, and decommission administrative accounts. This is a customer-facing artifact — not just internal documentation.

---

## Provider Responsibility Rules

### SCG-CSO-RSC: Recommended Secure Configuration (MUST)
**Effective:** 2026-03-01 | **Grace Period Ends:** 2026-07-01

Providers must establish and maintain secure configuration guidance covering:
- Instructions for securely accessing, configuring, operating, and decommissioning top-level administrative accounts (MUST)
- Explanations of security-related settings restricted to administrative accounts and their implications (MUST)
- Security settings guidance for privileged accounts (SHOULD)

### SCG-CSO-AUP: Use Instructions (MUST)
Providers must include instructions in their FedRAMP Certification Package explaining how to access and utilize the Secure Configuration Guide.

### SCG-CSO-PUB: Public Secure Configuration Guidance (SHOULD)
Providers should make their Secure Configuration Guide publicly available.

### SCG-CSO-SDF: Secure Defaults (SHOULD)
Providers should pre-configure all settings to recommended secure defaults for administrative and privileged accounts at initial provisioning.

---

## Enhanced Capability Rules

### SCG-ENH-CMP: Comparison Capability (SHOULD)
Providers should enable customers to compare current account settings against recommended secure baselines.

### SCG-ENH-EXP: Export Capability (SHOULD)
Providers should allow exporting security settings in machine-readable formats.

### SCG-ENH-API: API Capability (SHOULD)
Providers should offer API access for viewing and adjusting security configuration.

### SCG-ENH-MRG: Machine-Readable Guidance (SHOULD)
Providers should deliver guidance in machine-readable formats compatible with customer tools.

### SCG-ENH-VRH: Versioning and Release History (SHOULD)
Providers should track and publish version history for secure default changes over time.

---

## Legacy Comparison

| Legacy FedRAMP Moderate CM Controls | FedRAMP 20x Class C SCG |
|---|---|
| STIG/CIS baseline documented in SSP | Secure Configuration Guide as customer-facing deliverable |
| Configuration evidence shown to 3PAO | Configuration guide shared with agencies and public (SHOULD) |
| No standardized customer guidance format | Machine-readable format, API access, export capability (SHOULD) |
| CM-7: least functionality documented internally | Admin account security settings documented and shared externally |
| No version history requirement | SHOULD track and publish version history for configuration changes |
