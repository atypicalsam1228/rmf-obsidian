---
type: guide
framework: cross-framework
status: draft
tags:
  - dib/contractors
  - fedramp/high
  - dod-srg/il4
  - cmmc/level-2
  - CUI
  - tenant-access
created: 2026-06-08
updated: 2026-06-08
sources:
  - "[[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg]]"
  - "[[Sources/FedRAMP/fedramp-high-baseline]]"
related:
  - "[[Wiki/dod-srg-cloud-impact-levels]]"
  - "[[Wiki/jira-cloud-fedramp-us-person-requirements]]"
  - "[[Wiki/tenant-dev-environment-account-management]]"
---

# DIB Customers — CSO Requirements for CUI

> [!abstract] Summary
> Defense Industrial Base (DIB) companies are not federal agencies. FedRAMP is a federal procurement program — it does not directly govern DIB compliance. Their framework is CMMC + NIST 800-171. However, the DoD SRG explicitly addresses which CSOs DIB companies may use to protect CUI, and IL4 PA is the effective market requirement for any CSP targeting DIB customers with CUI workloads.

---

## Regulatory Framework for DIB

DIB companies are governed by:
- **NIST SP 800-171** — protection of CUI on contractor systems (required by DFARS 252.204-7012)
- **CMMC** — Cybersecurity Maturity Model Certification; Level 2 = 800-171, Level 3 = 800-172
- **DoD SRG §5.10.2** — governs which cloud services DIB companies may use for CUI

FedRAMP is not directly required of DIB companies, but the DoD SRG ties their cloud usage to the DoD PA framework.

---

## What the DoD SRG Requires

> [!quote] DoD SRG V1R6 — §5.10.2
> "For the protection of sensitive CUI/CDI, it is highly recommended that non-CSP DOD contractors use CSOs that have been granted a DOD Impact Level 4 PA. Such CSOs must not be dedicated to DOD... Access to the CSP/CSO will be via the internet or a private direct connection. The NIPRNet will not be used as a connection path."
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg#5.10.2 Non-CSP DOD Contractors and DIB Partners|SRG §5.10.2]]

> [!quote] DoD SRG V1R6 — §5.10.2
> "Non-CSP DOD contractors and DIB partners are required to comply with NIST SP 800-171 for the protection of CUI/CDI. The DOD Impact Level 4 and 5 baselines cover all the security controls referenced in SP 800-171 except CM-7(4) and IR-2(1)."
> — [[Sources/DoD-SRG/u-cloud-service-provider-v1r6-srg#5.10.2 Non-CSP DOD Contractors and DIB Partners|SRG §5.10.2]]

> [!warning] "Highly Recommended" = Effectively Mandatory
> The SRG language says "highly recommended" but CMMC C3PAO assessors treat it as a hard requirement. If a DIB company stores CUI on a CSO without an IL4 PA, that is a CMMC gap finding. CSPs without IL4 PA become a liability for DIB customer certifications.

---

## What This Means for a CSP Targeting DIB

| DIB Use Case | CSP Requirement |
|---|---|
| DIB stores/processes CUI on your platform | IL4 PA required (effectively) |
| DIB uses platform for non-CUI work only | FedRAMP Moderate / IL2 may suffice |
| DIB integrates your CSO into a contracted product/service | DoD PA at matching impact level required |
| DIB connecting via NIPRNet | IL5 PA required — IL4 PA is NOT sufficient for NIPRNet |

> [!danger] IL5 NIPRNet Restriction
> DIB companies may NOT use an IL5 PA CSO to connect to NIPRNet. IL4 PA is the correct tier for DIB CUI use cases accessed via internet or private direct connection.

---

## Rev5 Equivalency for DIB

FedRAMP High + DoD IL4 PA is the authorization path. The question is whether existing FedRAMP Rev5 High authorization satisfies DIB/CMMC expectations:

**What Rev5 High covers:**
- All 800-171 controls are a subset of NIST 800-53 Rev5 High — FedRAMP High baseline covers every 800-171 requirement except CM-7(4) and IR-2(1)
- A CSP with FedRAMP High authorization + DoD IL4 PA is considered compliant with the control set DIB customers need

**What it does NOT automatically cover:**
- CMMC itself — CMMC certification applies to the DIB company, not the CSP. The CSP's IL4 PA is evidence the platform is suitable; it does not make the DIB customer CMMC certified
- CMMC shared responsibility — the DIB customer must still implement controls on their side of the shared responsibility model
- 20x is not accepted — DoD is not accepting FedRAMP 20x at IL4; Rev5 High + DoD PA is the only valid path for DIB CUI workloads

> [!info] Cross-Framework Mapping
> - NIST 800-171 ⊂ NIST 800-53 Rev5 High (all 110 practices are covered)
> - FedRAMP High baseline ≈ IL4 control baseline (covers 800-171 minus CM-7(4) and IR-2(1))
> - CMMC Level 2 = 800-171 = satisfied by IL4 PA platform (for the CSP layer)
> - CMMC Level 3 = 800-172 = requires additional controls beyond IL4 baseline

---

## CMMC Practical Impact on CSP Sales

If your DIB customers are pursuing CMMC Level 2 or 3:
- Their C3PAO will ask what cloud services store their CUI
- A platform without IL4 PA is a CMMC gap finding for the customer
- Customers will migrate to an IL4 PA platform or ask you to get one
- IL4 PA on your platform becomes a sales prerequisite, not a differentiator

---

## Related Notes

- [[Wiki/dod-srg-cloud-impact-levels]]
- [[Wiki/jira-cloud-fedramp-us-person-requirements]]
- [[Wiki/tenant-dev-environment-account-management]]
