# FedRAMP 20x Class C — MAS: Minimum Assessment Scope

**Source:** https://fedramp.gov/2026/reference/20x/c/minimum-assessment-scope/  
**Scraped:** 2026-08-03  
**Rules:** 5  
**Last Updated:** 2026-06-24

Legacy mapping: Replaces SSP authorization boundary definition and the traditional boundary diagram approach. Shifts from a provider-defined boundary to a data-centric scope definition.

---

## Key Change: Data-Centric Scope Replaces Boundary Diagram

Legacy FedRAMP: The provider defines an authorization boundary in the SSP; everything inside the boundary is in scope. The boundary diagram was the authoritative scope definition.

FedRAMP 20x: Scope is defined by data flow — all resources "likely to handle federal customer data" or impact its confidentiality, integrity, or availability are in scope, regardless of whether the provider drew a boundary around them.

---

## Rules

### MAS-CSO-IIR: Identify Information Resources (MUST)
Providers must identify all information resources likely to handle federal customer data or impact its confidentiality, integrity, or availability.

**Exclusions:**
- Products installed on agency systems (not shared responsibility models)
- OMB-specified out-of-scope categories

### MAS-CSO-FLO: Information Flows and Security Categories (MUST)
Providers must clearly identify, document, and explain information flows and security categories for ALL resources in the offering. Resources may vary by security category based on information handled.

### MAS-CSO-TPR: Third-Party Information Resources (MUST — when MAS-CSO-IIR applies)
For each applicable third-party resource, providers must document:
- General usage and configuration
- Justification for use
- Mitigation measures
- Compensating controls

### MAS-CSO-MDI: Metadata Inclusion (MUST — when MAS-CSO-IIR applies)
Federal customer data metadata must be included in scope.

### MAS-CSO-SUP: Supplemental Information (MAY)
Providers may include materials about non-in-scope resources as supplements, clearly marked and separated, without FedRAMP certification.

---

## Legacy Comparison

| Legacy FedRAMP Moderate Boundary | FedRAMP 20x Class C MAS |
|---|---|
| SSP authorization boundary defined by provider | Scope = all resources likely to handle federal customer data |
| Boundary diagram is authoritative scope | Data flow and security category documentation is authoritative |
| Third-party services covered via CRM/inheritance | Third-party resources require documented usage, justification, mitigation, compensating controls |
| Metadata handling addressed within boundary | Metadata explicitly in scope |
| Supplemental info mixed with in-scope content | Supplements clearly marked and separated |
