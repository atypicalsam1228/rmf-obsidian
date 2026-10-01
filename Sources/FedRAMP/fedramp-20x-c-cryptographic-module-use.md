# FedRAMP 20x Class C — CMU: Cryptographic Module Use

**Source:** https://fedramp.gov/2026/reference/20x/c/cryptographic-module-use/  
**Scraped:** 2026-08-03  
**Rules:** 3  
**Last Updated:** 2026-06-24

Legacy mapping: Replaces SC-13 (Cryptographic Protection) and IA-7 (Cryptographic Module Authentication) hard FIPS mandates with documentation requirement plus SHOULD-level FIPS guidance.

---

## Key Change: FIPS Requirement Softened from MUST to SHOULD

Legacy FedRAMP (all baselines including Moderate) required FIPS 140-2 or 140-3 validated cryptographic modules as a hard mandate (MUST). FedRAMP 20x Class C changes this: documentation of what modules are in use is MUST; using NIST CMVP validated modules is SHOULD (recommended, not mandatory).

---

## Rules

### CMU-CSO-CMD: Cryptographic Module Documentation (MUST)
**Effective:** 2026-07-04 (obtain); 2027-01-01 (maintain on an ongoing basis)

Providers must document cryptographic modules used in services protecting federal customer data, noting "whether these modules are validated under the NIST Cryptographic Module Validation Program or are update streams of such modules."

Documentation must cover all services where cryptographic protection applies.

### CMU-CSO-UVM: Using Validated Cryptographic Modules (SHOULD — Class C)
"Providers with Class C Certifications SHOULD use cryptographic modules or update streams of cryptographic modules with active validations under the NIST Cryptographic Module Validation Program."

This is a guidance-level requirement. No specific numerical threshold. Active NIST CMVP validation status is preferred.

### CMU-CSO-CAT: Configuration of Agency Tenants (SHOULD)
Providers should establish default tenant configurations using validated cryptographic modules "when such modules are available." Conditional on availability.

---

## NIST Cryptographic Module Validation Program (CMVP)

The NIST CMVP validates cryptographic modules against FIPS 140-2 and FIPS 140-3 standards. Validated modules and their certificates are searchable at: https://csrc.nist.gov/projects/cryptographic-module-validation-program

---

## Legacy Comparison

| Legacy FedRAMP Moderate SC-13 / IA-7 | FedRAMP 20x Class C CMU |
|---|---|
| FIPS 140-2 or 140-3 validated modules **REQUIRED** (MUST) | Must **document** all crypto modules — MUST |
| No documentation requirement beyond SSP notation | Documentation with CMVP validation status required |
| Hard mandate applies to all cryptographic use | SHOULD use NIST CMVP validated modules (Class C) |
| — | SHOULD configure tenant defaults to use validated modules when available |
