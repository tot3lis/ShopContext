# Expected Full Reference Behavior

## Expected Result
Full Reference Mode should generate a complete draft `shop-reference.md`.

## Expected Behavior
- Preserve operation numbers exactly, including leading zeroes.
- Preserve operation names exactly.
- Preserve raw work centers exactly.
- Do not rename coded/numeric work centers as facts.
- Use separate inferred meaning fields for coded/numeric work centers.
- Treat routers as planned/intended process skeletons, not actual execution evidence.
- Treat machine lists as equipment context only, not process sequence.
- Since the machine list has no work center column, map machines by function only and downgrade confidence accordingly.
- Allow broad SMT operations to have multiple possible sub-process machines.
- Do not pretend the router explicitly separates print/place/reflow.
- Do not assume one work center equals one machine.
- Keep unmapped or uncertain equipment visible.
- Use uncertainty labels such as `Unknown`, `Possible`, `Inferred`, `Low confidence`, and `Needs user review`.
- Mark evidence sources as `Possible` unless retention is explicitly confirmed.
- Stay strictly within ShopContext Layer 1 scope.

## Expected Weak / Uncertain Areas
- `0300 Process Secondary Side SMT` and `0400 Process Primary Side SMT` are broad operations and may include DEK Horizon, MY300, and IBL VAC 645, but this must remain inferred.
- `0500 Touch Up` and `0700 Touch Up` are likely manual solder touch-up, but no direct machine is proven.
- `0600 Install Thru Holes` may involve Pillarhouse Jade, Solderjet1, manual install, or some combination, but exact mapping is unconfirmed.
- `0800 Insp` may use Koh Young Zenith Pro, Mantis Microscopes, or both.
- `0900 Test` has no listed test equipment.
- `1000 Bonding` likely maps to Nordson Dispenser, but no work center confirmation exists.
- `1100 Conformal Coat` likely maps to Conformal Coat Booth, but no work center confirmation exists.
- `1300 Final Insp` likely maps to Mantis Microscopes, but exact usage is unconfirmed.

## Expected Scope Control
The output must not perform:
- RCCA
- Root cause analysis
- Corrective action generation
- Defect trend analysis
- SPC analysis
- Machine performance analysis
- Maintenance event analysis
- ProblemPath routing
