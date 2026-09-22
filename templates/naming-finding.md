---
type: naming-finding
finding: "{{title}}"
domain: ""
verdict: ""
constraint: ""
action: ""
status: open
components: []
found: "{{date}}"
found-by: ""
---

# {{title}}

## What disagrees

| Where | Name |
|---|---|
|  |  |

## Same domain?

A naming rule only holds inside the domain it was made for.
A Figma variable groups with `/`, a token path groups with `.`, and neither has anything to say about a component prop.
If these names are on different domains, this is probably not a finding.

## Verdict

Set `verdict` in the properties to one of:

- **inconsistency**: the same concept, on the same domain, with different names.
- **deliberate-difference**: the things really are different, so their names should be too.
- **cross-domain**: each domain's rules require the difference.
- **unknown**: can't tell from the evidence, so someone has to be asked.

**Why:** ?

## What already settles it

Set `constraint` to what decides this, if anything:
`Tool`, `Spec`, `Framework`, `Convention`, or `Choice`.
Arguing about something a tool already settles is an argument nobody can win.

**Why:** ?

## Proposed action

Set `action` to one of: `fix-figma`, `fix-mapping`, `record-decision`, `ask`.

Don't choose the new name here.
Choosing a name is a decision, and it gets a decision record that lists the alternatives.

## Who to ask

- ?
