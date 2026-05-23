# ShopContext

ShopContext is a Codex skill that turns messy manufacturing shop documents into a clean `shop-reference.md` file that AI can use to understand how a specific shop works.

It is built for manufacturing environments where data is spread across routers, work orders, PRTs, work instructions, machine lists, legacy exports, and shop-specific terminology.

## Skill Location

The skill lives here:

`.agents/skills/shop-context/`

Start with:

`.agents/skills/shop-context/README.md`

## What It Does

ShopContext helps AI understand:

- operation flow
- operation meanings
- hidden steps inside vague operations
- work centers
- machines and equipment
- quality gates
- shop-specific language

## Validation

ShopContext has passed simulated validation for:

- CCA hidden-step operations
- machining multi-operation PRTs
- harness multi-part-number terminology normalization
- bad input quality with missing, conflicting, and duplicate data

## Use Case

Upload available shop files, run the ShopContext skill, and generate a reusable `shop-reference.md`.
