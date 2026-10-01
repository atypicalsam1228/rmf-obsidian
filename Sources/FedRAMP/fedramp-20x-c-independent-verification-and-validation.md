# FedRAMP 20x Class C — IVV: Independent Verification and Validation

**Source:** https://fedramp.gov/2026/reference/20x/c/independent-verification-and-validation/  
**Scraped:** 2026-08-03  
**Rules:** 16 (6 provider + 7 assessor + 3 additional)  
**Last Updated:** 2026-06-24

Legacy mapping: Replaces 3PAO annual assessment and control-by-control compliance audit. Shifts from compliance checkbox to effectiveness validation.

---

## Key Change: 3PAO Replaced by FedRAMP-Recognized Assessors

Legacy FedRAMP required Third-Party Assessment Organizations (3PAOs) accredited by A2LA under the FedRAMP 3PAO program. FedRAMP 20x uses "FedRAMP-recognized independent assessment services" — a new category that may include organizations beyond the traditional 3PAO pool. Annual assessment cadence is retained.

Assessment focus changes from: "Did the provider implement the required controls?" (compliance) to: "Did the implemented controls produce the intended security outcomes?" (effectiveness).

---

## Provider Rules

### IVV-CSO-FIA: FedRAMP Independent Assessments (MUST)
Providers must complete annual independent verification/validation assessments with FedRAMP-recognized services covering all applicable rules.

### IVV-CSO-SEI: Supply Evidence of Implementation (MUST)
Providers must demonstrate to assessors that documented security measures are actually deployed.

### IVV-CSO-SEE: Supply Evidence of Effectiveness (MUST)
Providers must show assessors that implemented controls achieve their intended security outcomes.

### IVV-CSO-ICP: Inclusion in Certification Package (MUST)
Assessment results must be included in certification packages without material alteration.

### IVV-CSO-DUS: Document Use of Representative Samples (MUST)
When sampling is used, providers must explain the sampling methodology.

### IVV-CSO-USR: Use Representative Samples (MAY)
Sampling is permitted where appropriate during verification activities.

---

## Assessor Rules

### IVV-IAS-VIM: Verify Implementation (MUST)
Assessors must verify that implemented controls match documented practices.

### IVV-IAS-VEF: Validate Effectiveness (MUST)
Assessors must validate that controls produce intended security outcomes.

### IVV-IAS-SUM: Assessment Summaries (MUST)
Assessors must provide assessment summaries for each practice reviewed.

### IVV-IAS-OSA: Overall Assessment Summary (MUST)
Assessors must supply an overall assessment results summary.

### IVV-IAS-VIP: Verify Inclusion in Package (MUST)
Assessors must confirm that assessment data appears unmodified in certification packages.

### IVV-IAS-EPX: Engage Provider Experts (MUST)
Assessors must engage provider technical experts during assessment.

### IVV-IAS-SHA: Share Improvement Guidance (MAY)
Assessors may offer improvement guidance if objectivity remains intact.

---

## Assessment Approach

Verification requires technical-level review (code inspection, configuration review — not documentation scanning). Validation demands evidence that controls work as intended in the actual production environment.

---

## Legacy Comparison

| Legacy FedRAMP 3PAO Assessment | FedRAMP 20x Class C IVV |
|---|---|
| A2LA-accredited 3PAO required | "FedRAMP-recognized independent assessment service" |
| Annual assessment | Annual assessment (same cadence) |
| Control-by-control NIST 800-53 compliance audit | Verify implementation + validate effectiveness |
| SAR (Security Assessment Report) deliverable | Assessment results included in Certification Package |
| Point-in-time snapshot | Ongoing — assessors engage with live production evidence |
| Agency-sponsored assessment | Assessment independent of agency sponsorship |
