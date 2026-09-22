---
name: naming-findings
description: "Compare the inventory notes in components/ and tokens/ and write up where names disagree, one finding per note in findings/, classifying each difference as an inconsistency, a deliberate difference, a cross-domain difference, or unknown. Use when someone asks to find naming inconsistencies, compare components, check whether the system is consistent, or run the findings pass."
---

# Find where names disagree

Work from the inventory notes, not the raw exports.
The notes have been reviewed; the exports haven't.

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

## 3. Check nested components for shared names

Two instances with the same `Instance of` but differently named settings are probably two different components sharing one name.
This is easy to miss by eye and worth checking every time.

## 4. Write the notes

- One note per inconsistency or unknown, in `findings/<short-slug>.md`, from `templates/naming-finding.md`.
- Write up a deliberate difference only if someone is likely to "fix" it by mistake.
- Link each finding from the `Findings` section of every component note it involves.
- Write `findings/_summary.md` listing:
  - every finding, one line each, most consequential first
  - the deliberate differences
  - **the things that are consistent**, which are worth protecting and are easy to break without knowing

Order by consequence: a name that would make a developer build the wrong thing comes before a case-style mismatch.

## 5. Don't pick names

Set the `action` (fix-figma, fix-mapping, record-decision, ask) but don't propose the new name.
Choosing a name is a decision for people, with the alternatives recorded.
