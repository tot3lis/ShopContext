# Validation Report

Manual validation expectations for the ShopContext V1 scaffold. These are synthetic markdown checks, not executable tests.

## sample-router-basic.md

Expected behavior:

- Extract operations from the CSV-style router table.
- Preserve operation numbers exactly.
- Preserve operation names exactly.
- Preserve numeric work centers exactly.
- Avoid renaming numeric work centers unless the meaning is clearly labeled as inferred.
- Use `user_note` as context, not proof of actual execution.
- Infer likely plain-English meaning from operation names and notes where reasonable.
- Identify inspection and test points from operation names and notes.
- Identify likely manual operations when supported by names and notes.
- Avoid over-interpreting generic operation names such as `Inspect`.
- Treat router as planned flow, not evidence that a specific unit completed the route.

## sample-router-multiple-products.md

Expected behavior:

- Extract both product flows from the CSV-style router table.
- Preserve product-specific flows.
- Avoid flattening CCA-A and CCA-B into one fake universal route.
- Mark CCA-A Op 020 `Screen Print` and CCA-B Op 025 `Stencil Print` as possible equivalents, not proven equivalents.
- Mark CCA-A Op 030 `Place Components` and CCA-B Op 035 `Pick Place` as possible equivalents, not proven equivalents.
- Keep MRB Disposition and Rework Repair separate from standard flow unless the source says they are standard.
- Preserve numeric work centers exactly.
- Label inferred work center meanings as inferred.
- Treat user notes as context only, not proof of actual execution.

## sample-machine-list.md

Expected behavior:

- Extract machine records from the CSV-style machine export.
- Preserve machine names exactly.
- Preserve machine types exactly.
- Preserve numeric work centers exactly.
- Mark empty work centers as `Unknown`.
- Avoid assuming one work center equals one machine.
- Allow multiple machines in the same work center.
- Avoid forcing one-to-one operation-to-machine mapping.
- Flag Bench A and Bench B as ambiguous candidates for manual/final inspection.
- Flag Legacy Reflow Oven as conflicting or unmatched.
- Keep Conformal Coat Booth visible as unmapped if no router operation matches it.
- Mark evidence sources `Possible` unless retention is explicitly confirmed.
- Avoid claiming logs, images, records, recipes, or result files are retained unless explicitly stated.

## ambiguous-machine-mapping.md

Expected behavior:

- Extract operations and machines from messy CSV-style sections.
- Preserve numeric-only work centers exactly.
- Mark missing operation or machine work centers as `Unknown`.
- Preserve generic operation names such as `Assembly`, `Process`, `Inspect`, and `Test`.
- Avoid treating generic operation names as enough evidence for High confidence.
- Avoid treating numeric work center match alone as proof of mapping.
- Assign confidence per mapping row.
- Use Low or Unknown confidence where appropriate.
- Use `No dedicated machine identified` when a manual operation lacks a supported machine.
- List multiple candidate machines instead of choosing one without support.
- Keep machines with no matching operation visible.
- Preserve optional, rework, alternate, and conditional route roles separately from standard flow.
- Create targeted open questions tied to exact operations, work centers, or machines.

## CSV-Style Input Handling

- Can ShopContext extract operations from CSV-style tables?
- Can it extract machine records from CSV-style tables?
- Does it preserve raw column values exactly?

## Numeric Work Centers

- Are numeric work centers preserved exactly?
- Does the output avoid renaming numeric work centers as SMT, Test, Inspection, or other plain-English names unless labeled as inferred?
- Does it use operation names, machine types, and user notes to infer possible meaning carefully?

## Non-One-To-One Work Centers

- Does the output avoid assuming one work center equals one machine?
- Can multiple machines exist in one work center?
- Can one machine support multiple operations when supported?
- Can one operation have multiple candidate machines when unresolved?
- Does the output preserve uncertainty when a shared machine supports multiple operations but the exact relationship is unclear?

## User Notes

- Are user notes used as context?
- Does the output avoid treating user notes as proof of actual execution?
- Does it separate source-supported facts from inferred context?

## Messy Export Limitations

- Missing work centers become `Unknown`.
- Generic operation names are preserved and not over-interpreted.
- Conflicting machine/work center data is preserved and flagged.
- Unmapped machines remain visible.
- Optional/rework/alternate operations remain separate from standard flow.

## Evidence Retention Discipline

- Evidence sources are `Possible` unless retention is explicitly confirmed.
- The output does not claim logs, images, records, recipes, or result files are retained unless stated.

## Draft Output With Unresolved Questions

- Does ShopContext still produce a draft `shop-reference.md` when open questions remain?
- Are unresolved items clearly labeled?

## Uncertainty Labels

Check for use of:

- `Unknown`
- `Possible`
- `Inferred`
- `Low confidence`
- `Needs user review`

## Alternate / Optional / Rework Route Separation

- Are rework, optional, alternate, disposition, and closeout operations kept separate from standard flow?

## Router Planned-Flow Limitation

- Does the output avoid claiming that a specific unit actually followed the route?
- Does it treat routers as intended or planned process skeletons?

## Manual Operation Handling

- Does the output avoid forcing fake machine mappings for manual, administrative, inspection-only, or handling-based steps?
- Does it use `No dedicated machine identified` when appropriate?

## Confidence Behavior

- Is confidence assigned per mapping row?
- Are operation extraction confidence and machine mapping confidence kept separate?
- Are low or unknown mappings turned into targeted open questions?
- Is an optional `Source`, `Product`, or `Route` column used only when it reduces ambiguity?

## Output Length Control

- Is compact validation output the default for test, validation, review, or simulation prompts?
- Does compact validation avoid duplicating full operation, work center, mapping, and evidence tables?
- Is full `shop-reference.md` output still available when explicitly requested?
- Does the output avoid providing a full ShopContext Review and a full draft `shop-reference.md` in the same response unless explicitly requested?

## User Setup Mode

- Does User Setup Mode exist?
- Is User Setup Mode the default when a real user provides shop setup inputs such as routers, work orders, operation lists, work centers, machine lists, asset exports, or user notes?
- Does User Setup Mode avoid generating the full `shop-reference.md` by default?
- Does User Setup Mode provide a short `ShopContext Setup Review` with what was found, what is uncertain, targeted questions, and the next step?
- Does User Setup Mode ask 5-10 high-priority questions instead of every possible open question?
- Are optional evidence-retention questions clearly marked optional?
- Does User Setup Mode tell the user that the full `shop-reference.md` will only be generated when requested?
- Does Full Reference Mode still work when explicitly requested?
- Does Compact Validation Mode still work for validation/testing prompts?

## Core Logic Stability

- Does the core ShopContext logic remain unchanged?
- Are numeric work centers still preserved exactly?
- Does uncertainty remain visible using labels such as `Unknown`, `Possible`, `Inferred`, `Low confidence`, and `Needs user review`?
- Does the skill still produce a draft reference when open questions remain?

## Scope Control

Confirm the output does not perform:

- RCCA
- Root cause analysis
- Corrective action generation
- Defect trend analysis
- SPC analysis
- Machine performance analysis
- Maintenance event analysis
- Data integration
- ProblemPath routing

## Pass Criteria

The scaffold passes V1 validation when it can guide Codex to create a practical, manufacturing-specific `shop-reference.md` from rough manufacturing software exports while preserving raw source values, keeping uncertainty visible, and staying strictly within Layer 1 stable shop context.

## Public Repo Cleanup

Validation note:

- Real-use CCA shop test data was removed from the public repo test set.
- Remaining tests are synthetic examples intended for public validation.
- User Setup Mode remains the default for real shop setup inputs.
- Full Reference Mode remains available when explicitly requested.
- Compact Validation Mode remains available for validation/testing prompts.
- Scope stayed within ShopContext Layer 1.
- Required patches: none.
- Optional improvements: add future public-safe setup examples using fully synthetic data only.
