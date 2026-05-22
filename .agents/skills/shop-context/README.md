# ShopContext

ShopContext is a Codex Skill that helps create a shop-specific manufacturing reference file.

It reads the process information you already have, such as routers, work orders, operation lists, work centers, machine lists, asset exports, and notes from people who know the shop. It turns that into a clearer reference for how the shop appears to work.

## What It Solves

Manufacturing files often explain the shop in fragments. A router may list operation numbers, a machine list may use different names, and work centers may be coded values that only make sense to local users.

ShopContext helps connect those pieces so future work can understand:

- What the shop builds
- How work flows through operations
- What operation numbers mean
- What work centers and machines are involved
- Where inspection and test happen
- Which mappings are uncertain and need confirmation

## What You Provide

Useful inputs include:

- Routers or work orders
- Operation lists
- Work center lists
- Machine or asset lists
- Notes about manual steps, inspection, test, or local terminology
- Corrections to any mapping ShopContext gets wrong

The inputs can be rough exports, copied tables, CSV files, or plain notes.

## What It Creates

ShopContext creates a draft `shop-reference.md`.

By default, it will first show a short setup review instead of the full file. The setup review explains what it understood, what is uncertain, and what questions need answers.

The full `shop-reference.md` is generated only when you ask for the full reference.

## How To Use It In Codex

Add your shop files to the conversation or point Codex to them in the repo, then ask ShopContext to review them.

Example prompt:

```text
Use ShopContext on these router and machine list files.
Do not generate the full shop-reference.md yet.
Give me the short setup review and tell me what you need me to confirm.
```

After ShopContext asks questions, reply with the answers or corrections you know. It is fine to say `unknown` for anything you cannot confirm.

When the setup review looks right, ask:

```text
Generate the full shop-reference.md.
```

## What ShopContext Does Not Do

ShopContext does not:

- Solve defects
- Determine root cause
- Write RCCAs
- Generate corrective actions
- Analyze defect trends
- Analyze SPC data
- Parse machine logs
- Analyze maintenance events
- Integrate with MES, QMS, ERP, or other data systems
- Route work to ProblemPath

It only builds stable shop context.

## For Testing

Synthetic examples are included under `tests/`. They are intentionally rough and should not contain private shop data.

Use the synthetic tests to check:

- Short setup review behavior
- Compact validation behavior
- Full `shop-reference.md` generation when explicitly requested

