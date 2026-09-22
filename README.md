# Naming inventory starter kit

A place to record what your design system's names are today, where they disagree, and what you decide to do about it.

It's an Obsidian vault and a Git repo at the same time.
You can do everything here by hand, or with Claude Code, or a mix of both.
The notes come out the same either way, because both follow the same templates.

## What's in it

| Folder | What goes there |
|---|---|
| `templates/` | The four note templates |
| `exports/` | Raw exports from Figma plugins, kept exactly as exported |
| `components/` | One note per component: layers, props, values |
| `tokens/` | One note per variable collection: the naming pattern and what breaks it |
| `findings/` | One note per place where names disagree |
| `decisions/` | One record per naming decision you make |

## The order of work

1. **Inventory**: record what exists. Don't fix anything yet.
2. **Findings**: compare, and note where names disagree.
3. **Decisions**: for each real finding, choose a name and record why.

Keeping these apart matters.
If you fix names while inventorying, you lose the record of what was there, and you'll be making decisions one component at a time without seeing the pattern.

## Getting started

Pick whichever feels comfortable.
Both end up in the same place.

### Just start

1. Download the zip and unzip it. Rename the folder if you like.
2. In Obsidian, choose **Open folder as vault** and pick the folder.
3. Start working. That's all you need.

When you want a backup in the cloud:

4. In **GitHub Desktop**, choose **File → Add Local Repository** and pick the folder.
5. It will say the folder isn't a repository yet and offer to **create a repository**. Click that. Leave "Initialize with README" unticked.
6. Click **Publish repository**. Keep "Keep this code private" ticked.

### Start connected

If you already use GitHub:

1. On the [starter kit's GitHub page](https://github.com/future-friendly-design/smashing-workshop-naming-starter-kit), click **Use this template** to make your own copy.
2. Click **Code → Open with GitHub Desktop** and choose where to keep it.
3. In Obsidian, choose **Open folder as vault** and pick that folder.

The full walkthrough, including what to do when something looks wrong, is in [backing-up-with-github.md](backing-up-with-github.md).

### Saving and syncing

GitHub Desktop has two buttons you'll use:

| Button | What it does |
|---|---|
| **Commit to main** | Saves a version of your notes, with a short note about what changed |
| **Push origin** | Syncs your saved versions to the cloud |

## By hand

1. In Obsidian, check **Settings → Templates** shows the template folder as `templates`.
2. In Figma, run the **Specs** plugin on a component and look at the spec it produces.
3. Create a note in `components/` named after the component, and insert the `component` template.
4. Copy the layer and prop names across, exactly as Figma has them.
5. Leave a `?` wherever you'd be guessing.
6. In **GitHub Desktop**, commit with a message like `Inventory toggle-button`, then push.

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
