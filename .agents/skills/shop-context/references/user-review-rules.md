# User Review Rules

Open questions should help the user correct or confirm only the parts that matter. Do not ask the user to re-explain everything.

## When To Ask Questions

Create open questions for:

- Unmapped operations
- Unmapped machines
- Low-confidence mappings
- Unknown-confidence mappings
- Contradictory source information
- Important missing work centers
- Missing, ambiguous, or unmatched attached operation instructions
- Vague router operations that may contain multiple internal process steps
- Possible equivalent operations across routers
- Product-specific differences that may affect the reference

## Question Quality Rules

- Questions should be specific and targeted.
- Prefer yes/no or choose-between questions when possible.
- Tie each question to the exact operation, work center, or machine involved.
- Include the current proposed interpretation when helpful.
- Ask only about items that affect the usefulness or correctness of `shop-reference.md`.

## Good Question

"Does Op 050 Solder Reflow use the VAC 545 Vapor Phase machine, or is that operation handled by another reflow process?"

## Bad Question

"Explain your shop flow."

## Question Format

Use this structure when practical:

- Source item: operation, work center, machine, or product family
- Current interpretation
- Specific question
- Suggested answer options when possible

Example:

| Item | Current Interpretation | Question | Suggested Answers |
|---|---|---|---|
| Op 050 Solder Reflow | Possibly uses VAC 545 Vapor Phase | Does Op 050 use VAC 545, another reflow machine, or a manual soldering process? | VAC 545 / another reflow machine / manual process / unknown |

## Draft And Final Reference Rule

Open questions should not prevent ShopContext from producing a draft `shop-reference.md`.

If questions remain, include the best-supported reference content and clearly label uncertain, low-confidence, or unmapped items.

The draft should remain usable by AI, but users should be able to see which parts still need confirmation.

Do not remove an open question until the user or source documents resolve it.

Open questions belong in the ShopContext Review stage. Do not include a standalone open-questions section in the final `shop-reference.md`.

If uncertainty remains after user review, mark it briefly inside the relevant final section using `Unknown`, `appears to`, or `likely`.

## Question Prioritization For User Setup Mode

In User Setup Mode, do not list every possible open question.

Ask the minimum useful set of questions needed to resolve high-impact uncertainty.

Prioritize questions about:

1. Broad operation-to-machine mappings.
2. Vague operations with missing or ambiguous attached instructions.
3. Machines with multiple possible operations.
4. Operations with no mapped machine/equipment.
5. Work center meanings when the codes are not self-explanatory.
6. Quality gates, inspection points, and test points.
7. Manual vs machine-supported operations.
8. Confirmed records/logs only when a source hints at retention or the user needs the reference to preserve them.

Avoid low-value questions in the first pass.

Do not ask more than 10 questions unless the user requests a deeper review.

Optional enrichment questions, such as which records/logs are retained, should be clearly marked optional.
