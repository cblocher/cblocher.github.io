# cblocher.github.io

The source for Chris Blocher's portfolio site at https://cblocher.github.io. It is a Jekyll site that GitHub Pages builds and publishes whenever `main` changes.

The full portfolio also lives on UXfolio at https://uxfol.io/5a5a1147. This site holds the same case studies, plus the two game demos and the downloadable AI skill.

---

## Folder map

```
cblocher.github.io/
├── README.md              This file
├── _config.yml            Site title, description, plugins, defaults
├── _layouts/
│   ├── default.html       Page frame: skip link, header, main, footer
│   └── project.html       Case study frame: title, hero, facts, body, related projects
├── _includes/
│   ├── head.html          Fonts, stylesheet, SEO tags
│   ├── nav.html           Header and main navigation
│   ├── footer.html        Footer and "Let's talk" link
│   ├── figure.html        An image with alt text and a caption
│   ├── embed.html         A framed embed (such as Figma) with a fallback link
│   └── related-projects.html   "Read More of My Case Studies" cards
├── _sass/                 All styles, in small files (tokens, base, layout, cards, project, about, accessibility)
├── assets/
│   ├── css/main.scss      Builds the one stylesheet from _sass
│   ├── images/            Web-ready images, grouped by where they appear
│   └── downloads/         Published files. Do not change anything here.
├── _originals/            Full-size source images. Never edited, never published.
├── _vale/                 Writing-check rules (see Writing checks below)
├── .vale.ini              Writing-check settings
├── docs/                  Documentation (architecture, decisions, design, accessibility, and more). Not published.
├── CHANGELOG.md           What changed and when. Not published.
├── _data/                 Data files (the "Coming soon" card)
├── .github/workflows/     The deploy workflow GitHub runs on every merge to main
├── index.md               Home page
├── about.md               About page
└── projects/              One file per case study
```

Two game demos, `projects-doc-quest.html` and `projects-ai-headline-hero.html`, stay at the top level on purpose. Links on UXfolio point to those exact addresses.

---

## How to add a project

1. Put the full-size images in `_originals/<project>/`.
2. Make web copies (about 2000 pixels wide at most) in `assets/images/projects/<project>/`. Add a 4:3 thumbnail named `thumbnail.webp`, 800 x 600 pixels.
3. Copy an existing file in `projects/` and rename it, for example `projects/new-project.md`.
4. Fill in the settings between the two `---` lines at the top: `title`, `summary`, `order`, `thumbnail`, `hero`, `facts`, and `redirect_from` if the page replaces an old address.
5. Write the body in Markdown. Start sections at `##`. The page title is already the H1.
6. Add images with the figure include and always write alt text:

   ```
   {% include figure.html src="/assets/images/projects/new-project/diagram.webp" alt="What the picture shows" caption="Optional caption" %}
   ```

7. The home page and the "Read More" list pick the project up on their own, sorted by `order`.

---

## Rules that keep the site healthy

- **No inline styles.** Never write `style="..."` in a page. Add a class and style it in `_sass/`.
- **Alt text on every image.** Use `alt=""` only for a picture that adds nothing the text does not say.
- **One H1 per page.** The layout writes it from `title`. Body headings start at H2 and never skip a level.
- **Keep old addresses alive.** When a page moves, list the old address under `redirect_from` in its settings.
- **Do not change `assets/downloads/`.** It holds the README for the published skill.

---

## Writing checks

Vale checks that headings use sentence case. The settings are in `.vale.ini` and `_vale/styles/Site/Headings.yml`. Run `vale projects/` from the top folder. For how it works, and for a guide to GitHub and Jekyll, read `docs/learning-the-tools.md`.

---

## Documentation

Start at `docs/README.md`. It lists every document: architecture, technology decisions and reasons, the design system, accessibility, the content guide, workflow and maintenance, redirects, privacy, and known issues. The full record of decisions is `docs/decision-log.md`. What changed and when is in `CHANGELOG.md`.

---

## Preview

Pushing to a branch does not publish anything. Only `main` is published. To preview before merging, build the site locally with Ruby and the `github-pages` gem, or ask Claude Code to build a preview and send screenshots.
