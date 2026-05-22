# Shop Reference Schema

`shop-reference.md` is the final V1 output of ShopContext. It is a stable manufacturing context file for one shop or shop area.

Do not invent missing shop facts. If the source documents do not support a claim, mark it as unknown or put it in Open Mapping Questions.

## Scope Boundary

`shop-reference.md` describes how the shop appears to operate based on provided sources.

It should not include:

- Defect investigations
- Root cause claims
- Corrective actions
- RCCA conclusions
- Historical defect trend analysis
- Machine performance analysis
- Maintenance event analysis
- SPC interpretation

If defect, maintenance, or quality data appears in the source material, only reference it as a possible future evidence source or shop context item. Do not analyze it in V1.

## Required Sections

## 1. Shop Overview

Plain-language summary of what the shop appears to build and what type of manufacturing it performs. Include product type, manufacturing style, and major process families only when supported by the sources.

## 2. Source Documents Reviewed

List every router, work order, operation list, machine list, and user note used to build the reference. Include document names, dates, revisions, or identifiers when available.

## 3. Product Families

List known product or assembly families represented by the uploaded examples. If a product family is inferred from part numbers or router names, label it as inferred.

## 4. Standard Operation Flow

Ordered list of typical operations. Preserve source order and operation numbers. If multiple product flows differ, show common flow plus product-specific branches instead of flattening all products into one universal route.

## 5. Operation Dictionary

For each operation, include:

- Operation number exactly as shown
- Operation name exactly as shown
- Work center
- Plain-English meaning
- Product families where it appears
- Notes, constraints, or source references
- Confidence in extraction if needed

## 6. Work Center Dictionary

For each work center, describe what kind of work it performs. Include known associated operations, machines, manual activities, and inspection or test responsibilities.

For numeric or coded work centers, preserve the raw work center exactly and keep any plain-English description in a separate `Inferred Meaning` field.

Example:

| Work Center | Raw Value | Inferred Meaning | Basis | Confidence |
|---|---|---|---|---|
| 1100 | 1100 | Possible SMT print/place area | Screen Print, Place Components, DEK Horizon, MY200 | Medium |

Do not rename numeric work centers as facts.

## 7. Machine-To-Operation Map

Link machines to operation numbers, operation names, and work centers. Include mapping basis, confidence, and whether user review is needed.

## 8. Manual / Human Operations

List operations where no dedicated machine is assigned or where human judgment, handling, setup, inspection, documentation, or assembly dominates the work.

## 9. Inspection And Test Points

List operations where defects are likely detected, verified, dispositioned, or formally accepted. Include inspection, AOI, test, review, and quality gates.

## 10. Likely Evidence Sources By Operation

For each operation, list records, logs, photos, notes, travelers, inspection results, test results, traceability records, machine programs, setup sheets, or other evidence that may exist. Label uncertain evidence sources as possible.

Do not claim an evidence source is retained unless the source documents or user notes confirm retention.

## 11. Shop-Specific Terminology

List acronyms, abbreviations, internal labels, machine nicknames, product family names, process names, and shop-specific terms found in the sources.

## 12. Open Mapping Questions

List specific questions for unmapped, low-confidence, contradictory, or important missing items. Tie each question to an exact operation, work center, machine, or source.

## 13. Revision Notes

Describe what changed since the last version of the reference file. For a first version, state that this is the initial draft and list the source set used.
