# Transitrix templates

Forkable starter files for common architecture and governance artefacts, written as **text you can validate** rather than pictures you can only look at.

Each template is a self-contained file. Take one, edit it, run the validator. Nothing here needs the rest of the repository.

## Templates

| Template | What it is | Shape |
|---|---|---|
| [`raci/`](raci/) | A RACI matrix — who is Responsible / Accountable / Consulted / Informed across a set of activities. Enforces the one rule that makes it a RACI: exactly one **A** per activity | one file |
| [`operating-model/`](operating-model/) | A starter kit making a claim: "your operating model" is not a separate artefact to author, it is a composition of building blocks you already express — goals, capabilities, value streams, processes, organisation, information, products, applications. One minimal scenario runs through all eight, cross-referenced by real IDs | a small `canon/` tree |

## Grab one

Take what you need — one file or one folder, not a framework.

```sh
npx degit transitrix/templates/raci raci
npx degit transitrix/templates/operating-model operating-model
```

Then edit it and check it:

```sh
# single-file template: the --template flag runs its own rule
npx @transitrix/cli validate raci/raci.blocks.transitrix.yaml --template raci

# folder template: validate the whole set from inside it
cd operating-model && npx @transitrix/cli validate --scope=repo
```

Requires `@transitrix/cli` 2.2.0 or newer. For `raci`, the `--template` flag is what runs the one-Accountable rule — plain `validate` only checks the matrix is well-formed.

Each template's own README explains its structure and the conventions it applies.

## Why text

A RACI in a spreadsheet lets a row end up with two Accountable owners, or none, and nothing tells you. The same matrix as text can carry that rule as a **checkable invariant**: the validator fails the row the moment it breaks. You keep the familiar artefact and gain the integrity it was supposed to guarantee.

The notation these templates are written in is documented in the [Transitrix methodology](https://github.com/transitrix/methodology) — see [`notations/views/08-blocks.md`](https://github.com/transitrix/methodology/blob/main/notations/views/08-blocks.md).

## Licence

MIT — see [LICENSE](LICENSE). Use them, change them, ship them in your own repositories.

<sub>Made with [Transitrix](https://github.com/transitrix).</sub>
