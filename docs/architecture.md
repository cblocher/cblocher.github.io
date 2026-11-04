# Architecture

How the site is built and published. Last reviewed: 2026-11-04.

**Audience:** the site owner, and anyone (human or AI assistant) who changes the site.

---

## The short version

The site is a set of Markdown and HTML files in a GitHub repository. When a change is merged into the `main` branch, a GitHub Actions workflow builds the files with Jekyll and publishes the result to GitHub Pages at https://cblocher.github.io.

```
Edit Markdown on a branch
        |
        v
Pull request  --->  Merge into main
                          |
                          v
   GitHub Actions: "Deploy Jekyll with GitHub Pages dependencies preinstalled"
   (.github/workflows/jekyll-gh-pages.yml)
                          |
                          v
        Jekyll build (actions/jekyll-build-pages@v1)  --->  _site
                          |
                          v
          GitHub Pages  --->  https://cblocher.github.io
```

Nothing is published until a change reaches `main`. Pushing to any other branch changes nothing on the live site.

---

## The deploy workflow

| Item | Value |
|------|-------|
| File | `.github/workflows/jekyll-gh-pages.yml` |
| Runs when | A push to `main`, or when started by hand from the Actions tab |
| Steps | Check out the repo, set up Pages, build with Jekyll, upload the result, deploy it |
| Actions it uses | `actions/checkout@v4`, `actions/configure-pages@v5`, `actions/jekyll-build-pages@v1`, `actions/upload-pages-artifact@v3`, `actions/deploy-pages@v4` |
| Concurrency | One deployment at a time. A running deployment is never cancelled. |
| Typical time | About one minute (runs 76 and 77 on 2026-11-04 each finished in about 60 seconds) |

The workflow file is GitHub's sample, unchanged.

---

## How one page is built

Take `projects/teal-usability.md`:

1. The block between the two `---` lines at the top is the **front matter**: the title, summary, images, and facts.
2. `_config.yml` says every file in `projects/` uses the `project` layout, and sets its address to `/projects/<file name>/`.
3. `_layouts/project.html` builds the page frame (title, hero image, Overview, Goal, Results, facts) and places the Markdown body inside it.
4. `_layouts/default.html` wraps that in the skip link, header, `main` region, and footer.
5. Includes in `_includes/` supply the repeated pieces: head tags, navigation, footer, figures, embeds, cards.
6. The Markdown body is converted to HTML by kramdown.
7. The finished page is written to `_site/projects/teal-usability/index.html`.

---

## Layouts and includes

| File | What it does |
|------|--------------|
| `_layouts/default.html` | The frame for every page: skip link, header, `main`, footer |
| `_layouts/project.html` | The frame for a case study: title, hero, Overview, Goal, Results, facts, body, related projects |
| `_includes/head.html` | Fonts, the stylesheet, the tab title, and the SEO plugin tags |
| `_includes/nav.html` | The header navigation |
| `_includes/footer.html` | The footer and the "Let's talk!" link |
| `_includes/figure.html` | An image with alt text and an optional caption |
| `_includes/embed.html` | A framed embed (Figma, YouTube) with a fallback link |
| `_includes/slides.html` | A numbered series of images |
| `_includes/stats.html` | Big numbers |
| `_includes/project-cards.html` | The grid of case study cards |
| `_includes/related-projects.html` | The "Read more of my case studies" section |
| `_includes/role-cards.html` | The four role cards on the About page |
| `_includes/quotes.html` | The testimonials list |
| `_includes/cert-cards.html` | The certification cards |

Data lives in `_data/coming_soon.yml` (the placeholder card).

---

## Styles

`assets/css/main.scss` imports small files from `_sass/` and Jekyll builds them into the one stylesheet, `/assets/css/main.css`. The design values (colors, fonts, spacing) are CSS custom properties in `_sass/_tokens.scss`. See `design-system.md`.

---

## Images

| Folder | What it holds | Published? |
|--------|---------------|------------|
| `_originals/` | Full-size originals, never edited, plus `manifest.md` | No |
| `assets/images/projects/<project>/` | Web copies and the 4:3 thumbnail for each case study | Yes |
| `assets/images/about/`, `roles/`, `certs/` | Images for the About page | Yes |

---

## What is published and what is not

Jekyll skips any folder that starts with an underscore, and `_config.yml` also excludes these:

- `README.md`
- `CHANGELOG.md`
- `docs/`
- `_originals/`
- `_vale/`

Files that start with a dot (`.vale.ini`, `.github/`, `.gitignore`) are skipped by default.

---

## Pages outside the layout

| File | Why it is separate |
|------|--------------------|
| `projects-ai-headline-hero.html` and `projects-doc-quest.html` | Two game demos, written as complete HTML pages with their own styles. They use Tailwind from a CDN. They stay at these addresses because the UXfolio portfolio links to them. |
| `assets/downloads/README.md` | Published as a page at `/assets/downloads/`. It belongs to the downloadable skill, and UXfolio links to its GitHub address. Do not change it. |

---

## Outside systems

| System | Role |
|--------|------|
| UXfolio (https://uxfol.io/5a5a1147) | The current version of the portfolio content. The GitHub site follows it. |
| Figma | Hosts the Teal feedback file that the Teal page embeds |
| YouTube | Hosts the video on the AI skill page |
| Google Fonts | Serves the Montserrat and Lora fonts |
| GitHub Actions and Pages | Build and host the site |

See `privacy-and-third-parties.md` for what each one receives.

---

## Previews and how they differ from the live build

There is no staging site. Only `main` is published. Previews during development were built on a separate computer with the `github-pages` gem (version 233, Jekyll 3.10), which is the same family of software that GitHub's build action uses. Results matched the live site in every case checked (titles, redirects, the default theme behavior, the stylesheet output). The exact versions were not compared line by line.

---

## Limits to keep in mind

- GitHub Pages runs only a fixed list of plugins. A plugin that is not on the list does not run.
- Pages cannot send custom response headers (security headers, caching rules) or real HTTP redirects.
- GitHub publishes size and bandwidth limits for Pages. Check GitHub's current Pages documentation before adding large files.
