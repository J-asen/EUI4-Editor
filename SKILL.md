---
name: eui4-template-editor
description: Create and revise EUI4 user-facing Markdown page template introductions from internal scenario rules and screenshot assets. Use when Codex is asked to rewrite EUI4 scenarios, v0.0.7 page templates, scenario design rules, or xx-design.md files into readable product/design/business documentation with versioned Markdown files, local image references, Ant Design-like left-text/right-image layout, and removal of internal AI/D2D/D2C/checklist/output-contract content.
---

# EUI4 Template Editor

Use this skill to turn internal EUI4 scenario rules into readable “页面模板介绍” Markdown documents.

## Core Workflow

1. Read the current output docs first, especially the latest main version in `页面模板介绍-v0.0.7`, and match its newest writing and layout conventions.
2. Read the target scenario rule file and all asset Markdown/image files before writing. Translate rules into user-facing design guidance instead of exposing production instructions.
3. Work one scenario at a time unless the user explicitly asks for batch output. After one scenario is complete, wait for confirmation before continuing.
4. Use version management for every document change: create a new version file, keep only the latest version in the output root, and archive the previous root version in `历史版本`.
5. Copy referenced images into the output folder and use short relative paths that render directly in Markdown preview.
6. Validate template count, image paths, forbidden internal terms, section order, divider formatting, template block spacing, and root/history version placement before final response.

## Default Output Rules

- Use `EUI4` as the design system name in generated docs.
- Default output root: `页面模板介绍-v0.0.7`.
- Default history root: `页面模板介绍-v0.0.7/历史版本`.
- Default image root: `页面模板介绍-v0.0.7/images/{scenario}/`.
- Default document name: `{scenario}-v{n}.md`, using the next version number or the version requested by the user.
- Use short image paths from root-level docs, for example `./images/list-page/L01-基础列表.png`.
- For the divider after the opening title intro, use `---` then `<br>` with no leading `<br>`. For later major section dividers, use `<br>` before and after `---`. Keep `如何设计` and `推荐组合` continuous without a divider between them.
- Between consecutive template blocks, add one standalone `<br>` after the previous `</table>` before the next `###` heading.
- Never delete existing files. Never batch move files. Only move the previous root latest version of the same scenario into `历史版本` when creating its next version, and never overwrite an existing history file.

## Version Management Rules

- The output root should contain only the latest Markdown version for each scenario.
- Older versions belong in `页面模板介绍-v0.0.7/历史版本`.
- When revising a document, first identify the current root latest version for that scenario, such as `empty-state-v1.md`.
- Create the next version in the root, such as `empty-state-v2.md`; do not edit the current version in place.
- After the new version is created and validated, archive the previous root version by moving that exact single file into `历史版本`.
- If `历史版本` does not exist, create it before archiving.
- If the destination history file already exists, stop and ask the user how to proceed; do not overwrite, rename silently, or delete anything.
- Do not move files from `历史版本` back to the root unless the user explicitly asks to restore or promote a version.

## Required Reading

Before writing or revising a template introduction, read `references/writing-conventions.md` for the detailed structure, HTML layout pattern, scenario numbering, image rules, and validation checklist.

## Writing Stance

Write for product managers, UX/UI designers, business readers, and implementation stakeholders. Prefer plain design language: what the template is, when to use it, how to choose it, and what to avoid. Remove internal scheduling, generation, engineering contract, and automation language.
