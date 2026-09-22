# Naming inventory starter kit

A place to record what your design system's names are today, where they disagree, and what you decide to do about it.

It's an Obsidian vault and a Git repo at the same time.
You can do everything here by hand, or with Claude Code, or a mix of both.
The notes come out the same either way, because both follow the same templates.

## What's in it

| Folder | What goes there |
|---|---|
| `templates/` | The note templates, plus `property-conventions.csv` for anyone who prefers a spreadsheet |
| `exports/` | Raw exports from Figma plugins, kept exactly as exported |
| `conventions/` | Your system's own naming conventions, if it has documented ones |
| `components/` | One note per component: layers, props, values |
| `tokens/` | One note per variable collection: the naming pattern and what breaks it |
| `findings/` | One note per place where names disagree |
| `decisions/` | One record per naming decision you make |

Here because your team wants naming that's "AI-ready"? Start with [ai-ready-naming.md](ai-ready-naming.md).

## The order of work

1. **Inventory**: record what exists. Don't fix anything yet.
2. **Conventions**: if your system has written naming rules anywhere, record them, with the reason for each. If it has none, note that.
3. **Findings**: compare, and note where names disagree. Check against the conventions first: a pattern that looks inconsistent may be a deliberate rule.
4. **Decisions**: for each real finding, choose a name and record why.

Keeping these apart matters.
If you fix names while inventorying, you lose the record of what was there, and you'll be making decisions one component at a time without seeing the pattern.

## Getting started

Pick whichever feels comfortable.
Both end up in the same place.

### Just start

1. Download the zip, using either of these:
   - [the direct download link](https://github.com/future-friendly-design/smashing-workshop-naming-starter-kit/archive/refs/heads/main.zip), or
   - on the [starter kit's GitHub page](https://github.com/future-friendly-design/smashing-workshop-naming-starter-kit), the green **Code** button → **Download ZIP**.
2. Unzip it. The folder is called `smashing-workshop-naming-starter-kit-main`.
   Rename it to something you'll recognise, such as `acme-naming-inventory`, and move it wherever you keep your work.
3. In Obsidian, choose **Open folder as vault** and pick the folder.
4. Start working. That's all you need.

On a Mac, the folder looks like it only holds notes and folders.
It also holds two hidden folders: `.obsidian/`, which holds the vault settings, and `.claude/`, which holds the Claude Code skills.
To see them in Finder, press **Cmd + Shift + .** (full stop). Press it again to hide them.
Leave them where they are, even if you never use Claude Code.

When you want a backup in the cloud:

1. In **GitHub Desktop**, choose **File → Add Local Repository** and pick the folder.
2. It will say the folder isn't a repository yet and offer to **create a repository**. Click that. Leave "Initialize with README" unticked.
3. Click **Publish repository**. Keep "Keep this code private" ticked.

### Start connected

If you already use GitHub:

1. On the [starter kit's GitHub page](https://github.com/future-friendly-design/smashing-workshop-naming-starter-kit), click **Use this template** to make your own copy.
2. Click **Code → Open with GitHub Desktop** and choose where to keep it.
3. In Obsidian, choose **Open folder as vault** and pick that folder.

### Check the templates setting

Whichever way you started, check this once in Obsidian:
**Settings → Templates → Template folder location** should say `templates`.
If it's empty, type `templates` and close Settings.
That's what makes **Insert template** offer the kit's four templates.

The full walkthrough, including what to do when something looks wrong, is in [backing-up-with-github.md](backing-up-with-github.md).

### Saving and syncing

GitHub Desktop has two buttons you'll use:

| Button | What it does |
|---|---|
| **Commit to main** | Saves a version of your notes, with a short note about what changed |
| **Push origin** | Syncs your saved versions to the cloud |

## Getting data out of Figma

Any export that lists your components' layers and properties, or your variables' names, will do.
Save it in `exports/` exactly as it came out, so every note can point at its source.

| What you're inventorying | What to export | Goes into |
|---|---|---|
| Components: layers, props, values | A component export from the **Specs** plugin (YAML or JSON), or another plugin that exports component properties | a `component` note |
| Variables and tokens | Figma's own variables export (design token JSON), or a CSV from a variables-export plugin | a `token-collection` note |
| Anything else | A screenshot, or a copy and paste of the names | whichever note fits |

### Plugins shown in the workshop

| Plugin | What it does | Use it for |
|---|---|---|
| [Specs 2](https://www.figma.com/community/plugin/1549454283615386215/specs-2) | Exports a component's anatomy, props and values as YAML or JSON | a `component` note, by hand or with Claude |
| [Propstar](https://www.figma.com/community/plugin/1116018586739867857/propstar) | Lays out every combination of a component's variants and properties in a labelled table | seeing every prop and value at once, and spotting combinations that shouldn't exist |
| [Select Layers](https://www.figma.com/community/plugin/799648692768237063/select-layers) | Selects layers by name, type or similarity | finding typos, and every layer with a given name, across a file. Later, once a rename has been decided and scheduled, selecting every affected layer so you can rename them all at once |
| [Variables Documentation](https://www.figma.com/community/plugin/1493511839808963998/variables-documentation) | Generates tables of your variables and their values across modes | reading variable names and modes by hand |
| [Typography Documentation](https://www.figma.com/community/plugin/1582434622981020238/typography-documentation) | Lays out your local text styles with their properties | text style names |
| [Luckino](https://www.figma.com/community/plugin/1495722115809572711/luckino-variables-import-export-json-css) | Imports and exports variables as JSON and CSS | a variables export for a `token-collection` note |
| [Token Press](https://www.figma.com/community/plugin/1560757977662930693/token-press-dtcg-style-dictionary-exporter) | Exports variables as DTCG tokens and for Style Dictionary | a DTCG token file for a `token-collection` note |

Every export leaves something out.
The free tier of Specs, for example, writes colours as raw hex even where variables are applied.
Write down what your export can't show you, so nobody reads a gap as a fact.

## By hand

1. In Figma, run the **Specs** plugin on a component and look at the spec it produces.
2. Create a note in `components/` named after the component, and insert the `component` template.
3. Copy the layer and prop names across, exactly as Figma has them.
4. Leave a `?` wherever you'd be guessing.
5. If you've set up GitHub Desktop, commit with a message like `Inventory toggle-button`, then push.

For variables, export them from Figma or with a variables-export plugin, save the file in `exports/`, and fill in a `token-collection` note.

## With Claude Code

Open this folder in Claude Code.
It reads `CLAUDE.md`, which holds the rules, and has three skills available:

| Say something like | What happens |
|---|---|
| "Here's the Specs export for toggle-button" + paste | Saves the export and writes `components/toggle-button.md` |
| "Work out the naming pattern in exports/variables.json" | Writes a note per collection in `tokens/` |
| "Run the findings pass" | Compares the notes and writes up disagreements in `findings/` |

Claude leaves the judgement cells as `?`, just as you would.
Those are yours: which layers really exist in code, what the code calls each prop, and who decided what.

## Rules worth knowing whichever way you work

- **A naming rule belongs to its domain.** A Figma variable, a token path and a CSS variable use different delimiters on purpose. That isn't an inconsistency.
- **A difference isn't always an inconsistency.** A toggle button has a selected state and a button doesn't.
- **An export never shows everything.** The free Specs plugin writes colours as hex even where variables are applied. Don't read that as "not tokenised".
- **An empty field beats an invented one.** If nobody can say who decided something, write "No decision found".
- **Inventory never renames anything.** Not in Figma, not in code, not even removing emojis. A name is a contract other people's work depends on, so changing it is a breaking change that needs a decision and a release.
- **A token's tier comes from its value, not its name.** A token holding a raw value is a primitive; a token pointing at another token isn't, whatever it's called.

## License

© 2026 Future Friendly Designs Inc.
This work is licensed under [Creative Commons Attribution 4.0 International](LICENSE) (CC BY 4.0).
To view a copy of this license, visit https://creativecommons.org/licenses/by/4.0/

You are free to share and adapt the material, including commercially, as long as you give appropriate credit.
The credit applies when you share the kit or your version of it publicly.
The notes you write in it are yours.

### How to credit

If you share the kit or a version of it, for example in your own workshop, a public repo, or a blog post, include a line like this:

> Adapted from the [Naming inventory starter kit](https://github.com/future-friendly-design/smashing-workshop-naming-starter-kit) by Sam Gordashko, [Future Friendly Design](https://github.com/future-friendly-design), licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

If you haven't changed anything, write "From" instead of "Adapted from".
