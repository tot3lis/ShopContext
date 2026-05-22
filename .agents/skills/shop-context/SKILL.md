# ShopContext

ShopContext is a Codex Skill for creating a shop-specific manufacturing reference file. It turns routers, work orders, operation lists, work centers, machine lists, and user corrections into a reusable `shop-reference.md` file that describes how a specific shop appears to work.

ShopContext is Layer 1 of a larger RCCA Build system. It creates stable shop context only. Downstream skills may later consume the reference file to guide investigations, but ShopContext does not perform investigations itself.

## When To Use This Skill

Use ShopContext when the user wants to:

- Create a shop-specific manufacturing reference file
- Interpret routers, work orders, operation lists, work centers, or machine lists
- Build or update `shop-reference.md`
- Map operations to machines or work centers
- Identify inspection/test points in a shop flow
- Create shop context for downstream manufacturing/RCCA skills

Do not use ShopContext when the user asks to solve a defect, determine root cause, write an RCCA, or analyze historical defect trends.

## What ShopContext Is

ShopContext teaches downstream manufacturing workflows:

- What the shop builds
- How work flows through the shop
- What operation numbers mean
- What work centers exist
- What machines are used
- Where inspection and test happen
- Which steps are manual or judgment-based
- What evidence may exist at each step
- What terminology is specific to the shop

## What ShopContext Is Not

ShopContext is not:

- An RCCA solver
- A defect analyzer
- A root cause engine
- A final RCCA generator
- A machine log analyzer
- A maintenance ticket analyzer
- A historical defect database
- A full MES, QMS, or ERP integration
- A physical shop floor map

ShopContext must stay out of RCCA and root-cause scope. It does not solve defects, assign causes, evaluate containment, or recommend corrective actions.

## Inputs ShopContext Can Use

Minimum useful inputs:

- Sample routers or work orders
- Operation numbers
- Operation names
- Work centers
- Machine lists
- User notes for anything the routers do not explain

Optional useful inputs:

- Known machine-to-operation mappings
- Manual operation notes
- Inspection and test point notes
- Shop-specific acronyms or terminology
- Product family notes
- Material or process notes
- Evidence source notes

ShopContext V1 does not require defect data, machine logs, maintenance tickets, SPC exports, inspection exports, or MES/QMS/ERP integrations.

## Standard Workflow

When the user provides routers and machine lists:

1. Identify source documents provided.
2. Extract operation numbers, operation names, and work centers.
3. Determine operation sequence.
4. Group similar operations across routers.
5. Identify inspection and test points.
6. Extract machines and their stated purposes.
7. Propose operation-to-machine mappings.
8. Assign confidence levels per mapping.
9. Flag uncertain mappings for user review.
10. Generate `shop-reference.md`.
11. Include open questions instead of inventing missing facts.

Use the reference files in `references/` for extraction, mapping, confidence, and user review rules.

## Response Modes

Use Compact Validation Mode when the user asks to test, validate, review, or simulate ShopContext behavior.

Use User Setup Mode when the user provides real shop inputs for setup, such as routers, work orders, operation lists, work centers, machine lists, asset exports, or user corrections.

Use Full Reference Mode only when the user explicitly asks for the full `shop-reference.md`, finalized reference, or complete draft reference.

Compact Validation Mode should summarize results and avoid duplicating full tables.

User Setup Mode should summarize what ShopContext found, the main uncertainties, the highest-priority user questions, and the next step. It should not output the full `shop-reference.md`.

Full Reference Mode should output the complete `shop-reference.md` using the required schema.

Do not output a full ShopContext Review and a full draft `shop-reference.md` in the same response unless the user explicitly asks for both.

## Response Mode Selection

Use Compact Validation Mode when the user asks to test, validate, review, or simulate ShopContext behavior.

Use User Setup Mode when the user provides real shop inputs for setup, such as routers, work orders, operation lists, work centers, machine lists, asset exports, or user corrections.

Use Full Reference Mode only when the user explicitly asks for the full, final, complete, or generated `shop-reference.md`.

Do not output a full `shop-reference.md` during User Setup Mode.

Do not output both User Setup Mode and Full Reference Mode in the same response unless the user explicitly asks for both.

## Standard Setup Response Format

When reviewing source inputs, respond using:

# ShopContext Review

## 1. Sources Reviewed

## 2. Extracted Operation Flow

## 3. Operation Dictionary

## 4. Work Center Dictionary

## 5. Proposed Machine-To-Operation Mapping

## 6. Manual / Human Operations

## 7. Inspection And Test Points

## 8. Likely Evidence Sources By Operation

## 9. Low-Confidence Or Unmapped Items

## 10. Open Questions For User Review

## 11. Draft shop-reference.md

## Required Output

The final V1 output is `shop-reference.md`.

Do not require JSON output in V1. A future optional output may be `shop-context.json` or `shop-reference.json`, but this scaffold does not define or generate JSON as a required deliverable.

The generated `shop-reference.md` must use this section structure:

1. Shop Overview
2. Source Documents Reviewed
3. Product Families
4. Standard Operation Flow
5. Operation Dictionary
6. Work Center Dictionary
7. Machine-To-Operation Map
8. Manual / Human Operations
9. Inspection And Test Points
10. Likely Evidence Sources By Operation
11. Shop-Specific Terminology
12. Open Mapping Questions
13. Revision Notes

## Finalization Rule

If open questions remain, output a draft `shop-reference.md` and list the questions needed to finalize it.

If the user answers the open questions, update the reference and produce the finalized `shop-reference.md`.

Do not remove uncertainty unless the user or source documents resolve it.

## Downstream Handoff

The output `shop-reference.md` should be written so another manufacturing skill can read it later and understand:

- Operation sequence
- Machine names
- Work centers
- Inspection/test points
- Likely evidence sources
- Open context gaps

Do not assume the downstream skill has access to the original routers or machine lists.

## Confidence Levels

Assign confidence per machine-to-operation mapping:

- High: Direct source support or explicit user confirmation.
- Medium: Likely mapping based on operation name, work center, or process type, but not directly proven.
- Low: Weak inference that needs user review.
- Unknown: Not enough evidence to map.

Do not upgrade confidence just because the mapping seems convenient.

## Critical Rules

- Preserve operation numbers exactly as shown in source documents.
- Treat routers as process skeletons, not complete evidence sources.
- Do not invent missing shop facts.
- If the source documents do not support a claim, mark it as unknown or place it in Open Mapping Questions.
- Uncertain mappings must be flagged, not invented.
- Low-confidence or unknown mappings must create open questions.
- A confident operation extraction does not make the machine mapping confident.
- ShopContext creates reference context only. It must not perform RCCA, root cause analysis, defect trend analysis, or corrective action generation.
