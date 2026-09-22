---
type: naming-convention
system: "{{title}}"
domain: ""
source: ""
source-date: ""
decided-by: ""
status: ""
recorded: "{{date}}"
recorded-by: ""
---

# {{title}}

The naming rules this system already follows, and the reason for each.
Record these **before** the findings pass.
A pattern that looks inconsistent is often a deliberate rule nobody wrote down where you could see it.

- **Domain:** ?
  *(component properties, layers, variables, tokens… One domain per note. A rule that doesn't say its domain gets applied where it doesn't belong.)*
- **Where it comes from:** ?
  *(a doc path, an ADR number, a dated message. If it's only visible in the files, write "observed, not documented".)*
- **Who decided, and when:** ?
- **Status:** set `status` to `documented` (written down somewhere) or `observed` (a pattern you can see, with no record of anyone choosing it).

Prefer a spreadsheet? [`property-conventions.csv`](property-conventions.csv) holds the same information, one row per property, and imports into Airtable or Google Sheets.

## Patterns by kind of thing

What each kind of name looks like, and why.
Delete rows that don't apply; add the ones your system has.

| Kind of thing | Pattern | Example | Why |
|---|---|---|---|
| A style choice (colour role, strength) |  |  | ? |
| A state (selected, open, focused) |  |  | ? |
| A boolean that adds an element and changes the layout |  |  | ? |
| A boolean that shows an element without changing the layout |  |  | ? |
| A capability (can be dismissed, can scroll) |  |  | ? |
| Editable text |  |  | ? |
| An icon or instance swap |  |  | ? |
| A slot for the consumer's content |  |  | ? |
| Repeated items (2nd, 3rd…) |  |  | ? |

## How prop names map to layer names

When a prop controls a layer, how do you get from one name to the other?
For example: "the layer is the prop name without `-copy`", or "the prop name matches the layer name exactly".

| Prop pattern | Layer it targets | Exceptions |
|---|---|---|
|  |  |  |

## Value vocabularies

The allowed values for props that recur across components, and what each one means.

| Prop | Values | What each value means |
|---|---|---|
|  |  |  |

## Deliberate exceptions

Places where the system breaks its own pattern on purpose, and why.
Without these, the next person decides the rule is wrong rather than bounded.

- ?

## Open questions

- ?
