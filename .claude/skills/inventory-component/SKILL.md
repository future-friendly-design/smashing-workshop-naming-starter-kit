---
name: inventory-component
description: "Turn a Specs plugin export (YAML or JSON) of a Figma component into a component inventory note in components/. Use when someone pastes a Specs or Anova export, drops one into exports/, or asks to inventory, document, or record the naming of a component."
---

# Inventory a component from a Specs export

The output is a note in `components/<figma-name>.md`, built from `templates/component.md`.
It records names; it does not judge or fix them.

## Before starting

1. If the export was pasted, save it verbatim to `exports/<figma-name>.yaml` (or `.json`), so the note can point at its source.
2. Read `metadata`:
   - `generator.name`, `generator.version` and `license.level` go in `source`, e.g. `"Specs 2 v1.20.0, free tier"`.
   - `lastUpdated` goes in `exported`.
   - `source.nodeId` goes in `figma-node`.
3. If `components/<figma-name>.md` exists, stop and ask before overwriting it.

## Read only what naming needs

| Export field | Goes in |
|---|---|
| `title` | The note's name and `figma-name`. **Not** the key above it, which the plugin generated |
| `anatomy.<layer>` | Anatomy table: layer, `type`, `instanceOf` |
| `anatomy.<layer>.detectedIn`, and layers added in a variant's `layout` | Anatomy "Only appears in" |
| `props.<prop>` | Props table: name, `enum` as values, `default` |
| `props.<prop>.$extensions.com.figma` | Props "Mechanism" and "Shown/hidden by" (see below) |
| `default.elements.<layer>.content.$binding` | Props "Affects", for text props |
| `default.elements.<layer>.propConfigurations` | Nested component settings table |
| `variants[].elements.<layer>.styles.visible: false` | Props "Affects", when a variant hides a layer |

Skip the style values in `variants`.
They are most of the file and none of the naming.

## Reading props

| The export shows | Mechanism |
|---|---|
| `type: string` with an `enum` | variant |
| `type: boolean` with `$extensions.com.figma.type: VARIANT` | variant, with values true / false |
| `type: boolean`, no extension | boolean |
| `type: string`, bound by `$binding` to a text layer | text |
| `type: string` with `examples` naming an icon or component | instance swap (inferred: check it in Figma) |

`$extensions.com.figma.visibilityProp: X` means a separate boolean prop, `X`, shows or hides this one.
Put `X` in "Shown/hidden by".
Note whether `X` follows the same naming pattern as the other booleans; it often doesn't.

A boolean with no `visibilityProp` pointing at it probably toggles a layer, but the export does not say which.
Write the likely layer with `? (inferred)`.

## Fill in the note

1. Export columns: copy names exactly, including case and odd spellings.
2. Judgement columns (Kind, Framework part, Slot or fixed, Code prop, Design-only?): leave `?`.
   Fill them in only if the person has told you the framework and the answer follows from it, and say where it came from.
3. Identity section: leave `?` unless the person has told you.
4. Naming patterns observed: describe the case and affixes per domain.
   Where one domain mixes patterns (some props camelCase, some kebab-case), list each pattern with its members.
5. What the source can't tell you: always fill this in. For a free Specs export, list at least:
   - variables and tokens (colours appear as raw hex even when variables are applied)
   - what each unlinked boolean toggles
   - code names
   - who decided anything
6. Open questions: anything a person could answer in a minute that the export can't.

Set `track: claude` and `inventoried-by` to the person's name plus "with Claude", if you know it.

## Report back

In chat, briefly:

- the file written
- how many `?` cells are left for a person, and which matter most
- anything that looks like a finding, one line each

Don't write findings notes unless asked.
That is the `naming-findings` skill, and it works better across several components at once.
