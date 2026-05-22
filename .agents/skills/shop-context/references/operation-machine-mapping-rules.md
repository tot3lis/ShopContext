# Operation-Machine Mapping Rules

Use these rules to propose operation-to-machine mappings from routers, work centers, machine lists, and user notes.

The skill must never treat a weak mapping as fact.

## Mapping Types

## Direct Name Match

Use when operation name and machine name or type directly match. Example: Operation `AOI` and machine `Koh Young AOI`.

## Work Center Match

Use when the operation and machine share the same work center, and the machine capability is consistent with the operation.

## Process Type Match

Use when the operation name and machine capability align even if work center is missing or different. Example: `Solder Reflow` and `VAC 545 Vapor Phase`.

## User-Provided Mapping

Use when the user explicitly states that a machine supports an operation. This can be High confidence unless the user note conflicts with a source document.

## Ambiguous Mapping

Use when more than one machine could support the operation, or when the source supports only a weak relationship.

## No Mapping Found

Use when no machine can be responsibly linked to the operation. Keep the operation visible and create an open question when the mapping matters.

## Manual Operation Rule

Some operations may not have a dedicated machine.

If an operation is manual, human-judgment-based, administrative, inspection-only, documentation-based, or handling-based, do not force a machine mapping.

Use `No dedicated machine identified` when appropriate.

Only suggest a manual bench, station, or tool if the source documents or user notes support it. Otherwise, flag the operation for review.

## Source / Product Context For Ambiguous Mappings

When multiple routers or products reuse the same operation number for different meanings, include a `Source`, `Product`, or `Route` column in mapping tables.

Use this only when it reduces ambiguity.

Do not merge operations across products unless the source documents or user confirms they are equivalent.

## Mapping Table Format

Use this table when presenting proposed mappings:

| Operation # | Operation Name | Work Center | Suggested Machine | Mapping Basis | Confidence | Needs User Review? |
|---|---|---|---|---|---|---|
| 020 | SMT Print | SMT | DEK Horizon | Process type + work center match | High | No |
| 030 | Pick and Place | SMT | MY200 | Process type + machine name match | High | No |
| 040 | AOI | Inspection | Koh Young AOI | Direct name match | High | No |
| 050 | Solder Reflow | Solder | VAC 545 Vapor Phase | Process type match | Medium | Yes |
| 060 | Final Inspection | Quality | Manual inspection bench | Manual operation inference | Low | Yes |

## Mapping Rules

- Assign confidence per mapping.
- Separate operation extraction confidence from machine mapping confidence.
- Do not upgrade confidence because a mapping seems convenient.
- If the operation has multiple possible machines, list all candidates.
- If the machine has no clear operation, keep it in the machine dictionary and flag it as unmapped.
- If the router and machine list conflict, preserve the conflict and ask a targeted question.
- Low or unknown confidence must create an open question.
