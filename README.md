# Transitrix templates

Forkable starter files for common architecture and governance artefacts, written as **text you can validate** rather than pictures you can only look at.

Each template is a self-contained file. Take one, edit it, run the validator. Nothing here needs the rest of the repository.

## Templates

| Template | What it is | Rule it enforces |
|---|---|---|
| [`raci/`](raci/) | A RACI matrix — who is Responsible / Accountable / Consulted / Informed across a set of activities | Exactly one **A** per activity |

## Grab one

The whole point is that you take a single file, not a framework.

```sh
# just the RACI template
npx degit transitrix/templates/raci raci

# or clone the lot (it is deliberately small)
git clone https://github.com/transitrix/templates.git
```

Then edit it and check it:

```sh
npx @transitrix/cli validate raci/raci.blocks.transitrix.yaml --template raci
```

Requires `@transitrix/cli` **2.2.0 or newer** — the `--template` flag is not in 2.1.0.

Each template's own README explains its structure and the rule it applies.

## Why text

A RACI in a spreadsheet lets a row end up with two Accountable owners, or none, and nothing tells you. The same matrix as text can carry that rule as a **checkable invariant**: the validator fails the row the moment it breaks. You keep the familiar artefact and gain the integrity it was supposed to guarantee.

The notation these templates are written in is documented in the [Transitrix methodology](https://github.com/transitrix/methodology) — see [`notations/views/08-blocks.md`](https://github.com/transitrix/methodology/blob/main/notations/views/08-blocks.md).

## Licence

MIT — see [LICENSE](LICENSE). Use them, change them, ship them in your own repositories.

<sub>Made with [Transitrix](https://github.com/transitrix).</sub>
