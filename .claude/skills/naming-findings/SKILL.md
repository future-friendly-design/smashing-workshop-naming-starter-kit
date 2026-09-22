---
name: naming-findings
description: "Compare the inventory notes in components/ and tokens/ and write up where names disagree, one finding per note in findings/, classifying each difference as an inconsistency, a deliberate difference, a cross-domain difference, or unknown. Use when someone asks to find naming inconsistencies, compare components, check whether the system is consistent, or run the findings pass."
---

# Find where names disagree

Work from the inventory notes, not the raw exports.
The notes have been reviewed; the exports haven't.

## 0. Read the conventions first

If `conventions/` holds the system's documented conventions (a note, or `property-conventions.csv`), read them before comparing anything.
Many patterns that look inconsistent are deliberate rules:
a prefix that separates an instance swap from a boolean with the same layer name, camelCase `is`/`has` booleans beside kebab-case props,
a separate `isFocused` boolean instead of a `focused` state, a value word in a component name because the set was split into siblings.

- A difference that follows a documented convention is **not** a finding.
- A component that breaks a documented convention **is** a finding, and it names the side to fix: `action: fix-figma`.
- If there are no documented conventions, say so at the top of `_summary.md`. Every verdict below is then weaker, and the most useful next step may be writing the conventions down.

## 1. Group names by concept

Across all notes, group the names that refer to the same thing.
Usually:

- the same kind of layer (focus rings, labels, icons, slots, loaders)
- props that do the same job (a text prop, a show/hide boolean, an emphasis or colour choice, interaction state)
- the values of those props
- nested components with the same `Instance of`
- token positions that hold the same kind of word

## 2. Classify every difference

For each group whose names differ, pick one verdict:

| Verdict | Test |
|---|---|
| **inconsistency** | Same concept, same domain, different names |
| **deliberate-difference** | The things really do differ: they behave differently or hold different things |
| **cross-domain** | The names are on different domains, and each domain's rules require the difference |
| **unknown** | The notes can't settle it, so someone has to be asked |

Be strict about the second and third rows.
Flagging a correct difference teaches people to ignore the list.

## 3. Check for words that mislead

- **Hierarchy words used for emphasis or size:** `primary` / `secondary` / `tertiary`, or `h1`–`h4` text styles used for visual size.
  Hierarchy is order, not weight, and it changes when components are paired differently.
  These names mislead AI agents as well as people: asked for "a secondary action", an agent will happily produce two secondary buttons.
  Record it as a question for the team (V-04), not as a rename.
- **Sibling components** sharing a prefix (`button-neutral`, `button-brand`) are probably one code component split for Figma performance.
  Compare them as a family, not as unrelated components.

## 4. Check nested components for shared names

Two instances with the same `Instance of` but differently named settings are probably two different components sharing one name.
This is easy to miss by eye and worth checking every time.

## 5. Write the notes

- One note per inconsistency or unknown, in `findings/<short-slug>.md`, from `templates/naming-finding.md`.
- Write up a deliberate difference only if someone is likely to "fix" it by mistake.
- Link each finding from the `Findings` section of every component note it involves.
- Write `findings/_summary.md` listing:
  - every finding, one line each, most consequential first
  - the deliberate differences
  - **the things that are consistent**, which are worth protecting and are easy to break without knowing

Order by consequence: a name that would make a developer build the wrong thing comes before a case-style mismatch.

## 6. Don't pick names, and don't rename anything

Set the `action` (fix-figma, fix-mapping, record-decision, ask) but don't propose the new name.
Choosing a name is a decision for people, with the alternatives recorded.

Never rename anything in Figma, token files or code as part of this pass, even when asked to "fix" what you found.
A rename is a breaking change to a contract that designs, code and pipelines depend on.
Record the finding and stop.
