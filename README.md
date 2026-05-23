# ShopContext

ShopContext is a Codex skill that turns messy manufacturing shop documents into a clean `shop-reference.md` file that AI can use to understand how a specific shop works.

It is built for manufacturing environments where data is spread across routers, work orders, PRTs, work instructions, machine lists, legacy exports, and shop-specific terminology.

## Skill Location

The skill lives here:

`.agents/skills/shop-context/`

Start with:

`.agents/skills/shop-context/README.md`

## Usage Paths

### A. Use Directly From This Repo

Use this when you cloned this repository and want to run ShopContext here.

1. Clone the repo.
2. Add shop files to `user-test-files/`.
3. Open Codex from the repo root.
4. Prompt:

```text
Use the ShopContext skill to review all files in user-test-files and generate a shop-reference.md file.
```

Repo mode means the skill lives inside this cloned project.

### B. Install As A Reusable Codex Skill

Use this when you want ShopContext available from any project folder.

1. Copy `.agents/skills/shop-context` into your personal Codex skills folder:

```text
$HOME/.agents/skills/shop-context
```

2. Add shop files to `user-test-files/` in the project you are working from.
3. Prompt:

```text
Use the ShopContext skill to review all files in user-test-files and generate a shop-reference.md file.
```

Installed mode means the skill lives in your Codex toolbox and can be reused from other folders.

## Recommended Input Formats

- Recommended for V1: `.md`, `.txt`, `.csv`
- Best effort: `.xlsx`, `.pdf`
- Not recommended for V1: images, screenshots, scanned PDFs

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
