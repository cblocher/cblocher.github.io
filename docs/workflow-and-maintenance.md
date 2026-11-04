# Workflow and maintenance

How to change the site safely, undo a change, and keep it healthy. Last reviewed: 2026-11-04.

---

## Making a change

1. **Work on a branch.** Never edit `main` directly. A branch is a safe copy. Name it for the change, such as `claude/site-title-fix`.
2. **Commit in small steps.** A commit is a saved snapshot with a short message in the imperative mood: "Fix browser tab titles," not "Fixed" or "Fixes."
3. **Check your work** before asking for a merge (see the checklist below).
4. **Open a pull request** from your branch into `main`. The compare page is `https://github.com/cblocher/cblocher.github.io/compare/main...<branch name>`.
5. **Review the Files changed tab.**
6. **Merge pull request, then Confirm merge.** Keep the default merge commit, which preserves the detailed history. Leave the branch in place until the live site is checked.
7. **Watch the deploy** at https://github.com/cblocher/cblocher.github.io/actions. The "Deploy Jekyll with GitHub Pages dependencies preinstalled" run turns green in about a minute.
8. **Check the live site** (see "After a merge").

---

## Checklist before a merge

| Check | How |
|-------|-----|
| The site builds | Build with the `github-pages` gem, or ask an assistant to build a preview and send screenshots |
| No broken links or images | Compare every link and image reference against the built files |
| Accessibility | An automated scan on every page changed, plus the checklist in `accessibility.md` |
| Headings follow the rule | `vale projects/ docs/ index.md about.md README.md` reports no warnings |
| Text matches UXfolio | Compare the changed text with the UXfolio page |
| Phone layout | View at 390 px wide. Nothing scrolls sideways. |
| Old addresses still work | If a page moved or was renamed, it has a `redirect_from` entry |
| The log is up to date | `docs/decision-log.md` and `CHANGELOG.md` have an entry |

---

## After a merge

1. The deploy run is green.
2. Open the changed pages on the live site. Use a hard refresh (Ctrl+Shift+R) to skip the browser's cache.
3. Check the tab titles, the redirects of any moved page, and `/assets/css/main.css`.
4. Check the embeds (Figma and YouTube) in a normal browser.

---

## Undoing a change

| Situation | What to do |
|-----------|------------|
| The merge looks wrong | Open the merged pull request and choose **Revert**. GitHub makes a new pull request that undoes it. Merge that one. |
| One file is wrong | Open the file on GitHub, choose **History**, open an older commit, and copy the old version, or ask an assistant to restore the file from a commit. |
| You want the site as it was before the 2026-11-04 rebuild | The commit `eccaa6d` is the site at that point, and `_originals/` plus the zip of old images also hold what existed then. |

A merge adds new versions of files. It does not erase the old ones, so history always has them.

---

## Routine maintenance

| How often | Task |
|-----------|------|
| After every merge | Check the deploy and the live pages |
| Every quarter | Click through every external link (see the list in `privacy-and-third-parties.md`). Several could not be checked automatically. |
| Every quarter | Check that the UXfolio pages and the GitHub pages still match, and sync differences (see `content-guide.md`) |
| Every six months | Review the versions of the actions in `.github/workflows/jekyll-gh-pages.yml` and update them if GitHub has retired one. A run's log shows a warning when an action is out of date. |
| Every six months | Review the allowed words in `_vale/styles/Site/Headings.yml` and add new names or brands |
| Every year | Re-run the accessibility checks and the manual tests in `accessibility.md` |
| Every year | Read GitHub's current Pages documentation for changes to limits, supported plugins, or the default Jekyll version |

---

## Backups

| What | Where it lives |
|------|----------------|
| All source files and history | GitHub (`cblocher/cblocher.github.io`) |
| Full-size images | `_originals/` in the same repo |
| The site as it was before the rebuild | Commit `eccaa6d`, and a zip of the old images downloaded on 2026-11-04 |

GitHub is the only copy of the repo unless it is cloned. A local clone is a second copy and is worth making (see `learning-the-tools.md`).

---

## Access and safety

- **No secrets are stored in the repo.** An earlier read-only check of all 21 repositories under the account (November 2026) found no secrets or credentials in any of them.
- **The owner's commit email address is public** in the git history, as it is in any public repo. GitHub's "Keep my email addresses private" account setting hides it from future commits. It does not rewrite old ones.
- **Review which apps can write to the repo** from time to time: GitHub account settings, Applications. The Claude GitHub App has push access to this repo. Remove it when it is not in use.
- **Pull requests are the control point.** Nothing reaches the live site without the owner merging a pull request.

---

## If something goes wrong

| Symptom | First step |
|---------|------------|
| The deploy run is red | Open the run on the Actions tab and read the failing step. The build step usually names the file and line. |
| The live site shows the old version | Hard refresh, then check that the deploy run finished |
| A page is missing | Check the file's `permalink` and its folder, and that it is not listed under `exclude` in `_config.yml` |
| An old link shows a "not found" page | Add the old address to `redirect_from` on the page that replaced it |
| An image is blank | Check the path in the page settings against the file in `assets/images/` |
| Fonts look wrong | Check whether the visitor's network blocks Google Fonts. The site falls back to system fonts. |
| The Figma frame is blank | Open the "Open in a new tab" link. The file may have been made private. |
