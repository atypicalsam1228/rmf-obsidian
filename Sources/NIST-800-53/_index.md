# NIST 800-53 Rev 5 Sources

> 3 authoritative source files. Updated 2026-04-05.

## Files

- [[nist-800-53r5-catalog]] — Complete structured catalog: control ID, name, text, discussion, and related controls for all 1000+ controls across 20 families
- [[nist-sp-800-53r5-full]] — Full NIST SP 800-53 Rev 5 publication text (492 pages) including supplemental guidance, appendices, and introductory material
- [[aws-config-nist-800-53r5-mappings]] — AWS Config rule mappings for 800-53 controls (926 rules, extracted from AWS Config Developer Guide)

## Usage Notes

- For **structured control lookups**, use `nist-800-53r5-catalog.md` — it has clean per-control entries with headings suitable for wikilink anchors
- For **full context** (supplemental guidance, appendix material, definitions), use `nist-sp-800-53r5-full.md`
- The catalog was extracted from the Excel sheet in the FedRAMP baseline spreadsheet, which provides cleaner structure than PDF extraction
