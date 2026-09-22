---
name: inventory-component
description: "Turn a Figma component export into a component inventory note in components/. Written around the Specs plugin (YAML or JSON), and works with other plugins' exports too. Use when someone pastes a Specs, Anova or other plugin export, drops one into exports/, or asks to inventory, document, or record the naming of a component."
---

# Inventory a component from a Specs export

The field guide below is for the Specs plugin.
If the export comes from another plugin, read what it actually contains, say which fields you used for layers, props and values,
and list in "What the source can't tell you" everything it leaves out. Different plugins leave out different things.

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
| `invalidVariantCombinations` | Open questions: which state combinations the designer left out on purpose. An empty list means none were recorded, not that every combination is valid in code |

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
   Fill them in only if the person has told you the framework and the answer follows from it.
   Every framework part name or code prop you fill in needs a link to the framework's documentation. No link, leave `?`.
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

## Sibling components

Figma component sets get split into sibling components to keep file performance up, usually with a shared prefix:
`button-neutral`, `button-brand`, `button-destructive`.
Several Figma components can therefore be **one** code component, and a value word in a component name (`neutral`) can be deliberate.

- If the component's name shares a prefix with other components, note the likely family in Identity: `Framework equivalent: ? (possibly one Button with button-brand, button-info…)`.
- Don't record the value word in the name as an inconsistency with a sibling that has the same value as a prop.
- Equally, don't assume every Figma component has a code counterpart. In Figma, anything published is a "component", including patterns and whole pages.

## Report back

In chat, briefly:

- the file written
- how many `?` cells are left for a person, and which matter most
- anything that looks like a finding, one line each

Don't write findings notes unless asked.
That is the `naming-findings` skill, and it works better across several components at once.
