# Backing up to the cloud with GitHub Desktop

Your notes already work without any of this.
This guide is for when you want a copy in the cloud, a history of every version, or to share the vault with your team.

You never need the command line.
Everything here happens in the GitHub Desktop app.

## What you need, once

1. **A GitHub account.** Free, at [github.com](https://github.com). If your company has one, ask whether to use it.
2. **GitHub Desktop.** Free, at [desktop.github.com](https://desktop.github.com).
3. **Sign in.** Open GitHub Desktop, go to **Settings** (called **Preferences** in older versions) → **Accounts**, and sign in to GitHub.

## Two words, two buttons

| You'll see | It means |
|---|---|
| **Commit to main** | Save a version of your notes, with a short note about what changed |
| **Push origin** | Send your saved versions to the cloud |

Saving a version and syncing it are two separate steps.
A commit on its own stays on your computer until you push.

## Back up a vault you already have

Use this if you downloaded the zip and have been working in Obsidian.

1. In GitHub Desktop, choose **File → Add Local Repository**.
2. Click **Choose…** and pick your vault folder, the one with `README.md` and `templates/` in it.
3. GitHub Desktop says this folder isn't a repository yet and offers to **create a repository** here. Click that.
4. In the form:
   - **Name**: anything you'll recognise, e.g. `acme-naming-inventory`.
   - **Initialize this repository with a README**: leave it unticked. The vault already has one.
   - **Git ignore**: leave it as **None**. The vault already has one.
5. Click **Create repository**.
6. Click **Publish repository** at the top.
   Keep **Keep this code private** ticked if your notes describe a client's or employer's system.
7. Click **Publish repository** in the dialog.

Your vault is now on GitHub.
You only do this once per vault.

## Start from GitHub instead

Use this if you haven't downloaded anything yet.

1. On the [starter kit's GitHub page](https://github.com/future-friendly-design/smashing-workshop-naming-starter-kit), click **Use this template → Create a new repository**.
2. Give it a name. Choose **Private** if it will describe a real system.
3. Click **Create repository**.
4. On your new repository's page, click **Code → Open with GitHub Desktop**.
5. Choose where to keep it on your computer, and click **Clone**.
6. In Obsidian, choose **Open folder as vault** and pick that folder.

## Every time you work

1. Work in Obsidian as usual. It saves your notes automatically.
2. Switch to GitHub Desktop. The **Changes** list shows every file you've touched.
3. In the **Summary** box at the bottom left, write what you did: `Inventory toggle-button`.
4. Click **Commit to main**.
5. Click **Push origin**.

Commit whenever you finish something you'd be sad to lose.
Small, frequent commits with clear summaries make the history useful later.

## Things that look alarming and aren't

- **Files in `.obsidian/` appear in Changes.** That's Obsidian saving its settings. Commit them along with your notes.
- **A file you didn't mean to change is in the list.** Untick it before committing, and it stays out of that version.
- **"Fetch origin" at the top.** That checks the cloud for changes. Harmless.

## Going back

- **To see an old version:** open the **History** tab and click any commit.
- **To undo a commit:** in **History**, right-click it and choose **Revert Changes in Commit**. This adds a new version that undoes it; nothing is lost.
- **Careful with "Discard changes".** Right-clicking a file in **Changes** offers it, and it throws away your unsaved work on that file.

## If a push is refused

This happens when the cloud has changes your computer doesn't, usually because you or a teammate worked on another machine.

1. Click **Pull origin** to bring those changes down.
2. Click **Push origin** again.

If GitHub Desktop reports a **conflict**, the same note was changed in two places.
It will list the file; open it, keep the parts you want, and commit.
If that feels like too much, ask someone before clicking anything.

## Working on a second computer

Use **Start from GitHub instead**, but go to your own repository rather than the starter kit, and skip straight to **Code → Open with GitHub Desktop**.
Click **Pull origin** before you start work each time.
