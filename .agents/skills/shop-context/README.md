# ShopContext Repo Skill

ShopContext is a repo-scoped Codex Skill for creating a shop-specific manufacturing reference from routers, work orders, operation lists, work centers, machine lists, asset exports, and user corrections.

It is Layer 1 shop context only. It does not perform RCCA, root cause analysis, corrective action generation, defect trend analysis, SPC analysis, machine performance analysis, maintenance event analysis, data integration, or ProblemPath routing.

## Location

This skill should live at:

```text
.agents/skills/shop-context/
```

Required structure:

```text
.agents/skills/shop-context/
├── SKILL.md
├── references/
└── tests/
```

## Response Modes

- User Setup Mode: default when a user provides real shop setup files. Produces a short setup review, top uncertainties, targeted questions, and next step. Does not generate the full `shop-reference.md` unless explicitly requested.
- Compact Validation Mode: use when testing, validating, reviewing, or simulating skill behavior. Produces a compact verdict and avoids duplicate full tables.
- Full Reference Mode: use only when the user explicitly asks for the full, final, complete, or generated `shop-reference.md`.

## Fresh-Clone Test Prompts

### 1. Compact Validation Mode

```text
Use ShopContext to validate the synthetic test files under .agents/skills/shop-context/tests.
Use Compact Validation Mode only. Do not generate the full shop-reference.md.
```

Expected: compact validation verdict only.

### 2. User Setup Mode

```text
Use ShopContext on these CCA router and machine list files:
.agents/skills/shop-context/tests/real-use-cca-shop/cca_shop_router_template_3col.csv
.agents/skills/shop-context/tests/real-use-cca-shop/cca_shop_machine_list.csv
Do not generate the full shop-reference.md yet. Give the short setup review and what needs confirmation.
```

Expected: `ShopContext Setup Review` with what was found, major uncertainties, 5-10 targeted questions, and next step.

### 3. Full Reference Mode

```text
Use ShopContext Full Reference Mode on:
.agents/skills/shop-context/tests/real-use-cca-shop/cca_shop_router_template_3col.csv
.agents/skills/shop-context/tests/real-use-cca-shop/cca_shop_machine_list.csv
Generate the complete draft shop-reference.md.
```

Expected: complete draft `shop-reference.md` using the required 13-section schema.

