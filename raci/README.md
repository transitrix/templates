# RACI matrix (blocks notation, matrix subset)

A forkable RACI — who is **R**esponsible / **A**ccountable / **C**onsulted / **I**nformed across a set of activities — expressed as the `blocks` notation's [matrix subset](https://github.com/transitrix/methodology/blob/main/notations/views/08-blocks.md#4a-top-level-structure--matrix-subset-grid-root) (`grid:` root).

## Fork and go

1. Grab [`raci.blocks.transitrix.yaml`](raci.blocks.transitrix.yaml) — `npx degit transitrix/templates/raci raci`, or just copy the file.
2. Edit `grid.columns` — one entry per role in your RACI (rename or add/remove roles).
3. Edit `grid.rows` — one entry per activity, with an `assign:` map giving each involved role a letter (`R`, `A`, `C`, or `I`). Omit a role from `assign` if it has no involvement in that row.
4. Validate:

   ```sh
   npx @transitrix/cli validate raci.blocks.transitrix.yaml --template raci
   ```

   (Windows PowerShell: `npx.cmd`.) Break the rule on purpose — give a row two `A`s, or none — and the validator fails it. That is the check working.

   > **Requires `@transitrix/cli` 2.2.0 or newer.** The `--template raci` flag is not in 2.1.0; on an older version the command exits with an unknown-option error rather than checking anything.

## The layout convention

- **One row = one activity.** `rows[].name` is the activity label; `rows[].id` is a document-local identifier (no whitespace).
- **One column = one role.** `columns[].name` is the role label; `columns[].id` is a document-local identifier.
- **A cell = `rows[r].assign[<column id>]`.** Its value is the RACI letter. A role not involved in an activity simply has no key in that row's `assign` — leave it out rather than writing a blank value.

## The modelling rule this template applies

**Exactly one `A` per row.** A RACI where an activity has zero Accountable owners has no one answerable for it; one with two has an ambiguous owner — and a spreadsheet lets either happen silently, which is the most common way a RACI rots.

This is a convention *this template* applies on top of the base `blocks` matrix subset. The base notation does not fix what `assign` values mean, nor constrain how many of a given value may appear in a row (see [08-blocks.md §6a](https://github.com/transitrix/methodology/blob/main/notations/views/08-blocks.md#6a-template-level-invariants-matrix-subset)). Other matrix templates — a coverage grid, a status board — would define their own rule, or none.

## Alternative: role-first orientation

The convention above puts activities on rows and roles on columns. If your RACI reads more naturally the other way around, swap them — `grid.columns` becomes the activities, `grid.rows` becomes the roles, and each row's `assign` maps activity-id → letter. The schema does not prefer one orientation over the other; pick whichever matches how your organisation already talks about the matrix.

## What this is not

This is a **document-local visual/data convention** on top of the `blocks` matrix subset — not a queryable, general-purpose RACI data model. If you need to query "who is Accountable across all activities" programmatically at scale, treat this template as a starting point to adapt, not a fixed data contract.
