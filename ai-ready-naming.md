# AI-ready naming

"AI-ready" is one of the most common reasons people give for wanting to fix their naming.
This page is about what it actually takes.

The short version:
**names that work for an AI agent are names that work for a new teammate who can't ask anyone anything.**
There's no special syntax for machines.
What's different is that an agent can't lean over and ask "wait, which blue is this?", so everything it needs has to be in the name or written down next to it.

## An agent is a user of your design system

Anyone who touches the design system, its inputs or its outputs is part of its user experience.
Agents now touch all three: they read your Figma files, your token files and your code, and they build with what they find.

Agents are unusual users in four ways.

- **They read literally.** A word means what it most often means, everywhere.
- **They generalise from patterns.** One example becomes a rule, applied everywhere it seems to fit.
- **They fill gaps confidently.** Where the answer isn't written down, they produce a plausible one instead of a question.
- **They can't see intent.** They get the names and whatever text sits beside them. They weren't in the meeting, and the canvas doesn't tell them why.

Every one of those is also true of a new hire in their first week.
An agent just does it faster, at scale, and without looking unsure.

## How names mislead agents

These all come from real systems and from this workshop.

**Hierarchy words read as order.**
Ask an agent for "a secondary action to go back" in a system whose buttons are `primary`, `secondary` and `tertiary`, and you can end up with two secondary buttons on one screen.
The names describe rank, and rank changes with context: a secondary button next to a tertiary one is the primary action.
Names that describe visual emphasis (`strong`, `standard`, `subtle`) don't have that problem.
The same goes for `h1`–`h4` text styles used for visual size.

**Compressed names can't be decoded.**
A real set of colour tokens, with names like these, couldn't be explained by the stakeholder who owned them, by a room of designers, or by several AI tools:
`surface/txt/surf-txt-on-act-on-act-p…`, `surface/fill/fill-surf-act-on-…`, `action/txt/act-txt-on-surf-…`.
*(These examples are made up, but they have the same problems as the real ones.)*
Repeated segments, abbreviations and a distinguishing part that's cut off in the tool's panel make a name that neither people nor agents can use.

**One word with two meanings gets merged.**
`variant` is a member of a component set in Figma and a prop in many code libraries.
`content` can be a slot the consumer fills or a text layer you style.
`default` can mean the rest state, the most-used option, or a setting.
An agent picks one meaning and applies it everywhere.
Across the projects this kit draws on, one word carrying two senses was the most common naming failure of all.

**Patterns get "fixed".**
Ask an agent to make names consistent and it will normalise whatever differs.
Sometimes that difference is load-bearing:
the `/` in a Figma variable and the `.` in a token path are each required by their domain,
and a prefix like `svg-icon-start` may exist precisely to separate an icon swap from a boolean called `icon-start`.
Preparing this workshop, an AI pass over two components listed eight findings.
With the system's documented conventions in hand, three of them turned out to be deliberate rules,
and its guess about which component had the wrong default was backwards.

**Gaps get filled with inventions.**
Ask which code prop a Figma property maps to and you'll get an answer, whether or not one exists.
Ask who decided a name and you may get a plausible attribution.
A wrong answer in a table reads as settled; nobody goes back to check it.

**Missing data gets read as fact.**
An export that shows raw hex colours reads as "this component isn't tokenised", even when the variables are applied and the export simply doesn't include them.
Every tool leaves something out, and an agent can't tell an omission from an absence.

**Prescriptive names get applied everywhere.**
A token called `hero-tagline` tells an agent exactly where to use it and nowhere else.
That's right for a component-specific token, and wrong for a shared one you meant to reuse.

## What makes names AI-ready

None of these are specific to AI.
They're the same qualities that make names work for people.
Agents just make the cost of skipping them visible sooner.

| Quality | What it means in practice | Where it applies |
|---|---|---|
| **Matches the code where design meets code** | Use your framework's component and part names, or the [ARIA pattern](https://www.w3.org/WAI/ARIA/apg/patterns/) name, so the agent's knowledge of the framework and your names line up | Components, parts, props |
| **One word, one meaning** | Each word means one thing within a domain, and the meaning is written in a glossary | Every domain |
| **Bound to its domain** | Each domain follows its own rules for case and delimiters; nobody "normalises" across them | Every domain |
| **Readable, with the important part first** | Clarity over brevity. Avoid abbreviations nobody would guess. Put the part that tells two names apart where the tool won't truncate it | Especially Figma variables and styles |
| **Emphasis, not hierarchy** | Describe visual weight, not rank | Prop values, shared tokens, text styles |
| **Consistent within a domain** | The same state is spelled the same way on every component (`hover`, not `hover` / `hovered` / `hovering`), because an agent learns from one example | Prop values, layers |
| **Says what the picture can't** | Whether a part can be swapped, whether a zone is a slot or a fixed child, whether a layer exists only because the design tool needs it | Layers, props |
| **Descriptive where it's shared** | Shared tokens describe the possible uses; only component-specific ones prescribe a single use | Tokens |

## The names aren't enough on their own

Even perfect names can't carry their reasons.
An agent that reads `svg-icon-start` doesn't know why the `svg-` is there unless something says so.

So AI-ready is mostly about **written context, in a place an agent can read**:

| What to write down | Why an agent needs it | Where it lives in this kit |
|---|---|---|
| Your conventions, with the reason for each | So it doesn't "fix" a deliberate pattern | `conventions/`, or `templates/property-conventions.csv` |
| What each component is for, and when to use it instead of its siblings | So it picks the right component, not the first one that looks close | the Identity section of each `component` note |
| How Figma names map to code names, with doc links | So it doesn't invent the mapping | the `Code prop` and `Framework part` columns |
| Your decisions, with the names you rejected | So it doesn't propose a rejected name again as a new idea | `decisions/` |
| What each export can't show | So it doesn't read a gap as a fact | "What the source can't tell you" in every inventory note |

It's also why this kit is plain markdown in a Git repo.
Agents read repositories easily. A FigJam board or a slide deck is much harder for them to reach, and the conversation where you decided is out of reach entirely.

## How to test whether your names are AI-ready

These are quick, repeatable, and they produce findings you can record.

1. **The comprehension test.**
   Show an agent a name exactly as a user sees it (truncated, in the panel) and ask what it's for.
   Then ask a person the same question.
   If neither can say, that's a finding.
2. **The selection test.**
   Describe a piece of UI in plain words ("a quiet cancel button next to a save button, on a dark section") and ask an agent which components, props and tokens it would use.
   Check its choices against what your team would pick.
3. **The mapping test.**
   Ask an agent to map a Figma component's props to your code library's, **with a documentation link for every answer**.
   Count the answers it can't back with a link.
4. **The consistency test.**
   Run the findings pass (`naming-findings`), first without your conventions and then with them.
   The difference between the two shows how much of your system's logic exists only in people's heads.

## What not to do in the name of AI-ready

- **Don't rename everything into one "machine-friendly" format.** Agents read kebab-case, camelCase and slashes perfectly well. What they can't do is guess meaning. Changing every domain to one case destroys distinctions that each domain needs.
- **Don't add type words for the machine's sake.** Design tokens carry their type in `$type`, so a name doesn't need `color-` at the front for a tool to know it's a colour. Whether to keep it for people is a separate choice.
- **Don't let an agent do the renaming.** A name is a contract that designs, code and pipelines depend on. Renaming is a breaking change, and it goes through a decision and a release, even when an agent proposed the new name.
- **Don't accept an agent's consistency report without your conventions.** Without them, it reads every deliberate pattern as a mistake.
- **Don't trust an agent's answer where you'd expect a question.** If it can't show you where an answer came from, treat it as a `?`.

## In one sentence

An AI-ready design system is one where the names say what things are, the conventions say why they're named that way, and both are written down where an agent can read them.
