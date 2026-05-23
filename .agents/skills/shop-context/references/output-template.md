# ShopContext Output Template

Use this file to choose the response shape.

## Output Length Control

ShopContext should avoid producing oversized duplicate outputs.

For simulated validation or setup review, do not output both:

- a full ShopContext Review, and
- a full draft `shop-reference.md`

unless the user explicitly requests the full draft reference.

Default setup/validation responses should be compact and include:

1. Validation verdict or setup summary
2. Key extracted flow summary
3. Major operation-instruction, machine, work-center, or quality-gate uncertainties
4. Open user questions for review-stage use
5. Required reference/test patches, if any
6. Optional improvements, if any
7. Ready/not-ready decision

Avoid duplicating the same operation, work center, machine mapping, instruction summary, and quality-gate tables across multiple sections.

If the user asks for the final reference file, output the complete lean `shop-reference.md`.

If the user asks for validation only, output the compact validation format.

If the user asks for both validation and full reference, output both, but clearly separate them.

# ShopContext Setup Review

Use User Setup Mode when the user uploads or provides shop setup inputs such as routers, work orders, travelers, operation lists, work centers, machine lists, asset exports, operation instructions, or user notes.

User Setup Mode is the default for real shop setup.

In User Setup Mode, do not output the full `shop-reference.md`.

Only generate the full `shop-reference.md` when the user explicitly asks for the full, final, complete, draft, or generated reference file.

## 1. What I Found

Short plain-language summary of the shop flow and major inputs found.

Keep this to 5-8 bullets maximum.

## 2. What I'm Unsure About

List only the major uncertain mappings, vague operations, missing instruction links, or unresolved equipment/work-center relationships.

Keep this to the highest-impact issues only.

## 3. Questions For You

Ask only the questions needed to improve the shop reference.

Prefer 5-10 targeted questions.

Do not ask the user to re-explain the whole shop.

## 4. Next Step

Tell the user to reply with answers/corrections.

State that the full `shop-reference.md` will only be generated when requested.

# Full ShopContext Review

Use this format when the user asks for a detailed review before finalization:

## 1. Sources Reviewed

List the routers, work orders, travelers, operation lists, machine lists, operation instructions, asset exports, and user notes reviewed.

## 2. Extracted Operation Flow

Show the operation sequence extracted from the source documents. Preserve operation numbers exactly.

## 3. Operation Dictionary

List each operation number, operation name, work center, plain-English meaning, product or route usage, and notes.

## 4. Operation Instruction Summaries

Summarize attached instructions into internal process steps. Do not copy full instructions.

Flag vague operations with missing or unmatched instructions.

## 5. Work Center Dictionary

List each work center and the work it appears to perform.

## 6. Machine / Equipment Dictionary

List machines, equipment, fixtures, benches, stations, lines, cells, and tools. Preserve names and asset IDs exactly.

## 7. Proposed Operation-To-Machine / Equipment Mapping

Use the mapping table from `operation-machine-mapping-rules.md` during review.

## 8. Quality Gates

List operations or internal steps where defects may be detected, accepted, reviewed, tested, verified, or dispositioned.

## 9. Low-Confidence Or Unmapped Items

List low-confidence mappings, unknown mappings, missing operation instructions, unmapped machines/equipment, and unresolved contradictions.

## 10. Questions For User Review

Ask specific targeted questions tied to exact operations, instructions, work centers, machines, or source documents.

## 11. Draft shop-reference.md

Provide the draft reference file content using the required lean `shop-reference.md` structure only when the user explicitly asks for a full draft reference.

# ShopContext Simulated Validation

## 1. Verdict

Ready / Not Ready / Needs Patch

## 2. What Passed

Short bullets only.

## 3. What Looked Weak

Short bullets only.

## 4. Required Patches

Only list blocking changes.

## 5. Optional Improvements

List non-blocking refinements.

## 6. Ready For First Real-Use Testing?

Yes / No, with a short explanation.

# Final Output Format

When the user approves or asks for the final file, provide:

```md
# Shop Reference

## 1. Shop Type / Process Context

## 2. Standard Operation Flow

## 3. Operation Dictionary

## 4. Operation Step Summaries

## 5. Work Center Dictionary

## 6. Machine / Equipment Dictionary

## 7. Quality Gates

## 8. Shop-Specific Language
```

If uncertainty remains after review, preserve it briefly in the relevant final section using clear language such as `Unknown`, `appears to`, or `likely`.

Do not include a final open-questions section.

Do not include generic evidence-source or likely-records sections. Include records/logs only when the source explicitly confirms they are retained or used, and place them inside the relevant Operation Step Summary as `Confirmed Records / Logs`.
