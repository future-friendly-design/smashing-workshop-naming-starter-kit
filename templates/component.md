---
type: component-inventory
component: "{{title}}"
figma-name: ""
figma-node: ""
source: ""
exported: ""
inventoried: "{{date}}"
inventoried-by: ""
track: ""
status: observed
---

# {{title}}

Record what this component is called **today**, in every domain it touches.
Don't fix names here.
A disagreement goes in a finding, and a new name goes in a decision.

Some columns can be copied straight from the Specs export or the printed spec.
Others need a person's judgement.
Leave a judgement cell as `?` rather than guess: a `?` tells the next person what to ask.

## Identity

- **What it does, in one sentence:** ?
  *(Behaviour, not appearance. "Switches an option on or off", not "a grey rounded box".)*
- **Framework equivalent:** ?
- **APG pattern:** ?
- **Where the name came from:** ?
  *(framework / APG / HTML element / cross-system consensus / invented / unknown)*
- **Who decided, and when:** ?
  *(If nobody can be named, write "No decision found". That's a finding, not a gap to fill.)*

Questions this answers: C-01, C-02, C-06.

## Anatomy

The first four columns come from the export.
The last three need judgement.

| Layer (Figma name) | Type | Instance of | Only appears in | Kind | Framework part | Slot or fixed |
|---|---|---|---|---|---|---|
|  |  |  |  | ? | ? | ? |

- **Type:** container, text, or instance.
- **Only appears in:** the variants a layer exists in, if it isn't in all of them.
- **Kind:** *element* (exists in the code), *nested component* (another component of yours), or *design-only* (exists only because Figma needs it, such as a focus ring or a spacer).
- **Slot or fixed:** a slot is filled by whoever uses the component; a fixed child is yours to style.

Questions this answers: L-01, L-02, L-03, L-05.

## Props

The first six columns come from the export.
The last two need judgement.

| Figma prop | Mechanism | Values | Default | Shown/hidden by | Affects | Code prop | Design-only? |
|---|---|---|---|---|---|---|---|
|  |  |  |  |  |  | ? | ? |

- **Mechanism:** variant, boolean, text, or instance swap.
- **Shown/hidden by:** the boolean prop that hides this one, if any (e.g. `hasLabel` hides the label text).
- **Affects:** the layer a prop fills or toggles, or "styles" for a variant that restyles several layers.
- If a cell is inferred rather than read, say so: `focus-outline? (inferred)`.

Questions this answers: P-01, P-03, P-05, P-07, P-08, V-02, V-03.

## Nested component settings

Settings on nested instances, as the export lists them.
Compare these across components: two instances of `slot` whose settings have different names are probably two different components that happen to share a name.

| Layer | Instance of | Settings |
|---|---|---|
|  |  |  |

## Naming patterns observed

Describe what you see, per domain.
Two domains following different patterns is not a problem by itself.

| Domain | Case | Prefixes and suffixes | Example |
|---|---|---|---|
| Component name |  |  |  |
| Props |  |  |  |
| Values |  |  |  |
| Layers |  |  |  |

## What the source can't tell you

- ?

## Open questions

- ?

## Findings

- 
