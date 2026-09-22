---
name: inventory-tokens
description: "Work out the naming grammar of a design system's variables or tokens from an export: a CSV from a Figma variables-export plugin, or a DTCG token JSON file such as Figma's own variables export. Writes one note per collection in tokens/. Use when someone shares a variables CSV or token file, or asks what naming pattern their tokens follow, which names break it, or how their tiers are structured."
---

# Extract the naming grammar from a token export

The output is one note per collection in `tokens/<collection>.md`, built from `templates/token-collection.md`.
The deliverable is the **pattern** the names follow and the **exceptions** to it, not a copy of the token list.

## Get the file, not a paste

Token exports are usually too long to paste.
Ask for the file to be saved in `exports/` and read it from there.
Keep it exactly as exported.

## Identify the format

- **CSV**: columns vary from plugin to plugin.
  Read the header row, say which columns you used for name, collection, mode, value and alias, and ask if it isn't obvious.
- **DTCG JSON**: groups are nested objects; a token is an object with `$value`, and usually `$type`.
  A `$value` like `{color.blue.500}` is an alias pointing at another token.
  Tool-specific data may sit under `$extensions`; read it, but don't assume what it holds.

Record the format and the source tool in the note's frontmatter.

## Work it out with a script

Use a short Python script for everything countable.
Don't estimate counts by reading.

1. **Collections and modes.** List each, with its token count. One note per collection.
2. **Split names into positions.**
   Use the domain's own grouping: `/` for Figma variable names, nesting for DTCG.
   Tabulate the words that appear at each position.
3. **Write the grammar.** Name each position by what it holds (category, property, role, state, scale).
   Mark a position optional if some names skip it.
4. **Tiers.** Tokens with raw values versus tokens that alias others.
   Follow the aliases to see which collections point at which.
5. **Vocabularies.** State words, scale words, emphasis words.
   Note mixed systems (`100`–`900` alongside `sm` / `md` / `lg`).
6. **Exceptions.** Every name that doesn't fit the grammar, with how it breaks.
   Group them if there are many.

## Rules for this domain

- **A delimiter that differs between domains is not a finding.**
  A Figma variable uses `/`, a DTCG path uses `.` in aliases, and CSS output might use `-`.
  Only compare names within one domain.
- **Don't invent tier names.**
  If the system doesn't name its tiers, describe them ("aliases into the Primitives collection") and ask what they are called.
- **Don't normalise.**
  If the export has `bg` in one place and `background` in another, record both exactly.
  That is a candidate finding, not a typo to correct.

## Report back

In chat: the collections found, the grammar for each in one line, the number of exceptions, and anything that looks like a finding.
