# Machine List Extraction Rules

Use these rules when extracting manufacturing context from machine lists, asset lists, equipment tables, line cards, cell descriptions, or user-provided machine notes.

## Key Rule

Machine lists describe equipment context. They do not define the process sequence by themselves.

Use routers/work orders to establish operation sequence.
Use machine lists to support machine-to-operation mapping.
If a machine list conflicts with router flow, preserve both and flag the mismatch for review.

## Extracted Fields

Extract the following when present:

- Machine name
- Machine type
- Work center
- Associated operation
- Process capability
- Evidence source possibilities
- Manual notes
- Asset number, serial number, line, cell, or location

## Machine Name

- Preserve the machine name exactly as shown.
- Keep model names, nicknames, and asset identifiers if provided.
- If the machine name is ambiguous, keep the raw source text and flag for review.

## Machine Type

Identify the machine type from explicit type fields, model names, or clear descriptions. Examples include stencil printer, pick-and-place, AOI, vapor phase reflow, selective solder, CNC mill, press, tester, inspection bench, or manual station.

If type is not stated or clearly probable, mark it unknown.

## Work Center

- Extract the work center exactly as shown.
- Do not invent a work center from machine location unless the source makes that relationship clear.
- If a machine appears in a work center not found in routers, keep it and flag the mismatch.

## Associated Operation

- Use explicit associated operation fields when present.
- Do not assign a machine to an operation unless the source supports it or the mapping is clearly probable.
- If multiple machines could perform the same operation, list all candidates and flag for review.
- If a machine is listed without a matching operation, keep it in the machine dictionary and flag it as unmapped.

## Process Capability

Capture stated capabilities such as:

- Stencil print
- Placement
- AOI
- Reflow
- Soldering
- Wash
- Conformal coat
- Cure
- Electrical test
- Functional test
- Inspection
- Packaging

Do not infer detailed capability limits such as tolerance, capacity, recipe, or program unless provided.

## Evidence Source Possibilities

List possible evidence sources when supported by machine type or notes. Examples include:

- Machine program
- Setup sheet
- Run log
- Operator log
- Recipe
- Inspection image
- AOI result file
- Test result
- Calibration record
- Maintenance record

Label these as possible unless the source explicitly states they are retained.

Do not state that a log, image, record, recipe, or result file exists unless the source explicitly says it exists or is retained.

## Handling Incomplete Machine Lists

Incomplete machine lists are acceptable V1 inputs. Keep unmapped machines visible, mark missing fields as unknown, and create targeted open questions for high-value gaps.
