# Learning GitHub, Jekyll, and Vale

A plain-language guide for the three tools behind this site, using this project's own files as the examples. Read one section at a time. You don't need to memorize anything.

This guide is not published on the site. It lives in the `docs` folder and `_config.yml` keeps it out of the build.

---

## How the three tools fit together

| Tool | What it does here | One-line picture |
|------|-------------------|------------------|
| GitHub | Stores every version of every file, and publishes the site from `main` | A filing cabinet with a complete history |
| Jekyll | Turns Markdown files into HTML pages | A printing press that adds the header and footer to every page |
| Vale | Checks your writing against rules you choose | A proofreader who never gets tired |

The flow: you write Markdown, Vale checks it, GitHub saves it, and Jekyll builds it into pages.

---

## GitHub

### The words you will meet

- **Repository (repo):** the whole project folder plus its history. This one is `cblocher/cblocher.github.io`.
- **Commit:** a saved snapshot with a short message. Every commit has an ID such as `eccaa6d`.
- **Branch:** a separate line of work. `main` is the published site. `claude/site-restructure` is where the rebuild is happening, so nothing there can break the live site.
- **Push:** send your commits to GitHub.
- **Pull request:** a request to merge one branch into another, with a chance to review first.
- **Merge:** combine a branch into another. Merging into `main` publishes it.

### Why history protects you

A merge adds new versions of files. It does not erase the old ones. The old versions stay in the history, so you can always go back. For example, the commit `eccaa6d` is the site as it was before the rebuild started.

### Things to try on the GitHub website

These are safe. They only look.

1. Open `https://github.com/cblocher/cblocher.github.io/commits/claude/site-restructure`. Each line is one commit. Click one to see exactly which lines changed (green is added, red is removed).
2. Open `https://github.com/cblocher/cblocher.github.io/compare/main...claude/site-restructure`. This shows everything that would change if the branch were merged. Read it before you ever merge.
3. Open `https://github.com/cblocher/cblocher.github.io/branches` to see all branches.

### Merging, step by step (when you are ready)

1. Open the compare page above and choose Create pull request.
2. Read the Files changed tab.
3. Choose Merge pull request. GitHub builds and publishes the site in a minute or two.
4. Check the live site. If you don't like it, the old version is still in the history.

---

## Jekyll

### The idea

You write a page once as plain text. Jekyll wraps it in the shared frame and writes out HTML. The pieces:

| Piece | Where it lives | What it does |
|-------|----------------|--------------|
| Page | `projects/teal-usability.md` | The words and the page settings |
| Layout | `_layouts/project.html` | The frame around a case study |
| Include | `_includes/figure.html` | A reusable piece, such as an image with a caption |
| Styles | `_sass/` | All the colors, fonts, and spacing |
| Settings | `_config.yml` | Site-wide settings |

### Following one page through

Take `projects/teal-usability.md`:

1. The block between the two `---` lines at the top is the **front matter**. It holds the title, summary, facts, and image paths.
2. The words below it are Markdown. `## Plan` becomes a second-level heading.
3. A line like `{% include figure.html ... %}` pulls in the figure include.
4. `_config.yml` says pages in `projects/` use the `project` layout, so Jekyll puts the page inside `_layouts/project.html`, which sits inside `_layouts/default.html`.
5. The result is written to `/projects/teal-usability/`.

### Good to know

- A folder that starts with an underscore (`_layouts`, `_includes`, `_sass`, `_originals`) is not published as itself. Jekyll uses it or skips it.
- Markdown inside an HTML block is not processed unless the block says `markdown="1"`. That is why the old pages showed raw `##`.
- `README.md` and `docs` are excluded in `_config.yml`, so they stay out of the site.

### Previewing

Pushing to a branch does not publish anything. To see a page before merging you need a build on a computer with Ruby and the `github-pages` gem, or you can ask Claude Code to build a preview and send screenshots.

---

## Vale

### The idea

Vale reads your Markdown and compares it to rules. This repo has one rule: headings use sentence case ("Why I built one," not "Why I Built One").

| File | What it is |
|------|------------|
| `.vale.ini` | Tells Vale where the rules are and which files to check |
| `_vale/styles/Site/Headings.yml` | The heading rule, plus a list of words that keep their capitals |

### Running it

Install Vale from https://vale.sh, then run this from the top folder of the repo:

```
vale projects/
```

Each result shows the file, the line, and the problem. No output means everything passed.

### When Vale flags something that is correct

Add the word to the `exceptions` list in `_vale/styles/Site/Headings.yml`. Names, brands, and acronyms (Figma, WCAG) belong there.

### What it cannot catch

- It does not check the `title:` lines in the page settings, or headings written inside layout files.
- It can miss a single stray capital in the middle of a heading.
- It checks only what a rule describes. It does not judge whether the writing is good.

### Things to try

1. Change a heading in a copy of a page to "Why I Built One" and run Vale. Watch it flag the line.
2. Add a new word to the exceptions list and run Vale again.

---

## Glossary

| Term | Meaning |
|------|---------|
| Front matter | The settings at the top of a page, between two `---` lines |
| Markdown | Plain text with simple marks (`##`, `*`) that turn into formatting |
| Liquid | The tag language Jekyll uses, such as `{% include ... %}` |
| Sass | A tidier way to write CSS, split into small files |
| Lint | To check text or code against rules, as Vale does |
| Redirect | An old address that sends visitors to the new one |
