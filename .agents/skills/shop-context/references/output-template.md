# ShopContext Review

Use this format during setup when presenting extracted context, proposed mappings, and review questions before finalizing `shop-reference.md`.

## Output Length Control

ShopContext should avoid producing oversized duplicate outputs.

For simulated validation or setup review, do not output both:

- a full ShopContext Review, and
- a full draft shop-reference.md

unless the user explicitly requests the full draft reference.

Default setup/validation responses should be compact and include:

1. Validation verdict
2. Key extracted flow summary
3. Major mapping confidence issues
4. Open user questions
5. Required reference/test patches, if any
6. Optional improvements, if any
7. Ready/not ready decision

Avoid duplicating the same operation, work center, machine mapping, and evidence-source tables across multiple sections.

If the user asks for the final reference file, output the complete `shop-reference.md`.

If the user asks for validation only, output the compact validation format.

If the user asks for both validation and full reference, output both, but clearly separate them.

# ShopContext Setup Review

Use User Setup Mode when the user uploads or provides shop setup inputs such as routers, work orders, operation lists, work centers, machine lists, asset exports, or user notes.

User Setup Mode is the default for real shop setup.

In User Setup Mode, do not output the full `shop-reference.md`.

Only generate the full `shop-reference.md` when the user explicitly asks for the full, final, complete, or generated reference file.

## 1. What I Found

Short plain-language summary of the shop flow and major inputs found.

Keep this to 5-8 bullets maximum.

## 2. What I'm Unsure About

List only the major uncertain mappings or missing pieces.

Keep this to the highest-impact issues only.

## 3. Questions For You

Ask only the questions needed to improve the shop reference.

Prefer 5-10 targeted questions.

Do not ask the user to re-explain the whole shop.

## 4. Next Step

Tell the user to reply with answers/corrections.

State that the full `shop-reference.md` will only be generated when requested.

## 1. Sources Reviewed

List the routers, work orders, operation lists, machine lists, and user notes reviewed.

## 2. Extracted Operation Flow

Show the operation sequence extracted from the source documents. Preserve operation numbers exactly.

## 3. Operation Dictionary

List each operation number, operation name, work center, plain-English meaning, product family usage, and notes.

## 4. Work Center Dictionary

List each work center and the work it appears to perform.

## 5. Proposed Machine-To-Operation Mapping

Use the mapping table from `operation-machine-mapping-rules.md`.

## 6. Manual / Human Operations

List operations where no dedicated machine is assigned or where manual work, handling, judgment, signoff, setup, or inspection dominates.

## 7. Inspection And Test Points

List operations where defects are likely detected, verified, or formally accepted.

## 8. Likely Evidence Sources By Operation

List possible evidence sources by operation. Mark evidence as possible unless the source explicitly confirms it exists and is retained.

## 9. Low-Confidence Or Unmapped Items

List low-confidence mappings, unknown mappings, unmapped machines, unmapped operations, and unresolved contradictions.

## 10. Open Questions For User Review

Ask specific targeted questions tied to exact operations, work centers, machines, or source documents.

## 11. Draft shop-reference.md

Provide the draft reference file content using the required `shop-reference.md` structure.

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
# shop-reference.md

[final shop reference content]
```

If uncertainty remains, preserve it in the final file using clear labels such as Unknown, Possible, Inferred, Low confidence, or Needs user review.

Do not remove uncertainty unless the user or source documents resolve it.
