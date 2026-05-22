# Confidence Rules

Assign confidence levels to individual extraction and mapping claims. Confidence must be assigned per mapping, not globally.

A confident operation extraction does not mean the machine mapping is confident.

Do not upgrade confidence just because the mapping seems convenient.

## High

Use High when:

- The router, work center, and machine name strongly and directly match.
- The operation name and machine type are a direct match.
- The user explicitly confirms the mapping.
- Source documents explicitly connect the operation and machine.

High confidence does not remove the need to preserve source detail.

## Medium

Use Medium when:

- The mapping is likely but not explicitly proven.
- Operation name and machine capability align, but work center is missing.
- Work center and machine capability align, but operation name is generic.
- Only one realistic candidate machine appears in the provided machine list.

Medium confidence may still need user review if the mapping is important.

## Low

Use Low when:

- The mapping is a weak guess.
- The operation is generic and the machine capability only partly matches.
- Multiple candidate machines exist and the source does not choose among them.
- The machine appears related by shop context but not by direct source support.

Low confidence should create an open question.

## Unknown

Use Unknown when:

- There is not enough evidence to map the item.
- The operation has no machine information.
- The machine has no associated operation, process type, or work center.
- Source documents contradict each other and cannot be reconciled.

Unknown confidence should create an open question when the missing item affects the reference.

## Required Practice

- Assign confidence per operation-to-machine mapping.
- Assign confidence to important inferred product families or possible equivalent operations when relevant.
- Keep low-confidence content visible but clearly labeled.
- Do not convert possible evidence sources into known evidence sources unless the source documents confirm they exist.

## Downgrade Rules

Downgrade confidence when:

- Multiple machines could reasonably perform the same operation.
- Operation names are generic, such as "process," "inspect," "test," or "assemble."
- Work centers are missing, inconsistent, or contradictory.
- A machine appears in the machine list but is not tied to an operation.
- The mapping depends only on general manufacturing knowledge instead of source evidence.
- Different routers use similar operation names for different purposes.

When in doubt, choose the lower confidence level and create an open question.
