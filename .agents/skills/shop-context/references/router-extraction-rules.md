# Router Extraction Rules

Use these rules when extracting manufacturing context from routers, work orders, travelers, operation lists, or similar process documents.

## Extracted Fields

Extract the following when present:

- Operation number
- Operation name
- Work center
- Sequence
- Product family hints
- Inspection or test points
- Manual or administrative steps
- Special notes
- Material, process, setup, or acceptance notes

## Operation Numbers

- Preserve operation numbers exactly as shown.
- Do not normalize leading zeroes away.
- Do not rewrite shop operation numbering conventions.
- If two routers use different numbers for similar work, keep both numbers and flag possible equivalence.

## Operation Names

- Preserve operation names exactly as shown.
- Add a plain-English meaning separately when supported.
- Do not assume two operations are the same just because names are similar.
- If operation names differ but appear to perform the same function, group them as possible equivalents and flag for review.

## Work Centers

- Extract work centers exactly as shown.
- Keep work center codes and descriptions if both are present.
- If a work center is missing, mark it unknown instead of deriving one without support.

## Sequence

- Determine operation sequence from operation number order, router line order, explicit predecessor/successor fields, or step sequence fields.
- If these conflict, preserve the conflict in notes and create an open question.
- Do not reorder operations solely to match a generic manufacturing flow.

## Product Family Hints

Product family hints may come from:

- Part numbers
- Assembly names
- Router names
- Work order descriptions
- Common prefixes or suffixes
- User notes

Label inferred product families as inferred unless explicitly named.

## Inspection And Test Points

Identify inspection or test points from terms such as:

- Inspection
- Final inspection
- In-process inspection
- Quality
- AOI
- X-ray
- Electrical test
- Functional test
- ATP
- ESS
- Burn-in
- Verification
- Acceptance

Do not treat every operation as an inspection point. Some operations may produce evidence without being inspection or test gates.

## Manual Or Administrative Steps

Identify likely manual or administrative steps from terms such as:

- Kit
- Material issue
- Setup
- Hand solder
- Touch-up
- Rework
- Manual assembly
- Review
- Stamp
- Signoff
- Pack
- Ship
- Close work order

Flag manual status as uncertain when the source does not clearly say whether a machine is involved.

## Alternate, Optional, And Rework Operations

If the router includes alternate, optional, conditional, rework, repair, or disposition operations, preserve them separately from the standard operation flow.

Do not treat rework or optional operations as part of the normal route unless the source clearly says they are standard.

Label these operations as:

- Standard
- Alternate
- Optional
- Rework / repair
- Administrative / closeout
- Unknown route role

If the route role is unclear, preserve the operation and create an open question.

## Grouping Similar Operations Across Routers

When multiple routers are provided:

- Group operations only when operation number, name, work center, and process meaning support the grouping.
- Preserve product-specific differences.
- Keep alternate operation numbers visible.
- Use "possible equivalent" when the function appears similar but the source does not prove equivalence.
- Avoid flattening distinct product routes into one fake universal route.

## Source Limits

Treat routers as process skeletons, not complete evidence sources. Routers show intended flow and control points, but they do not prove what happened on a specific date or unit.

Routers describe the intended or planned manufacturing flow. They do not prove that a specific unit actually followed every listed operation, skipped an operation, or experienced a delay, rework loop, machine issue, or operator deviation.

If actual execution is needed, that belongs to future evidence/data layers such as travelers, timestamps, defect records, machine logs, or operator reports.
