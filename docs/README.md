# Documentation

The documentation for cblocher.github.io. None of it is published on the site. Jekyll skips the `docs` folder.

Last reviewed: 2026-11-04.

---

## What is here

| Document | What it covers | Read it when |
|----------|----------------|--------------|
| `architecture.md` | How the site is built and published | You want to know how a change becomes a live page |
| `tech-stack.md` | Each technology choice, the alternatives, and the reasons | You are asking "why was it done this way?" |
| `decision-log.md` | Every decision made during the rebuild, in order, with its reasoning (D01 to D31) | You need the full story behind one choice |
| `design-system.md` | Colors, type, spacing, components, and contrast numbers | You are changing how the site looks |
| `accessibility.md` | What is built in, what has been tested, and what has not | You are checking or improving accessibility |
| `content-guide.md` | How to add or change pages, images, and text | You are editing content |
| `workflow-and-maintenance.md` | Branches, merging, undoing a change, routine upkeep, and problem solving | You are changing the site or something broke |
| `redirects-and-site-map.md` | Every address, and every old address that still works | You are moving or renaming a page |
| `privacy-and-third-parties.md` | What the site collects and which outside services it contacts | You are adding an embed, font, or script |
| `known-issues.md` | What is unfinished, unverified, or not ideal | You are deciding what to work on next |
| `learning-the-tools.md` | A beginner's guide to GitHub, Jekyll, and Vale | You are learning the tools |

Elsewhere in the repo: `README.md` (the front door), `CHANGELOG.md` (what changed and when), and `_originals/manifest.md` (where each image came from).

---

## Conventions

- **Headings use sentence case.** Vale checks this.
- **Each document has a "Last reviewed" date.** Update it when you check the document, even if nothing changed.
- **The decision log is append-only.** Never edit an old entry. If a decision changes, add a new entry that points to the old one by its ID.
- **The changelog is append-only too.** Add a new dated entry at the top. Never rewrite an old one.
- **Name files in lowercase words with hyphens.**
- **Write for someone who has never seen the site.** Define a term the first time it appears.

---

## Keeping the documentation true

When you change the site, update the documents that describe it:

| If you change | Update |
|---------------|--------|
| A color, font, or spacing value | `design-system.md` |
| A layout, include, or the deploy workflow | `architecture.md` |
| A technology or tool | `tech-stack.md` and the decision log |
| An address or redirect | `redirects-and-site-map.md` |
| An embed, font, or script | `privacy-and-third-parties.md` |
| Anything notable | `CHANGELOG.md` |
