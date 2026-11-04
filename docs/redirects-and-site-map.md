# Redirects and site map

Every address on the site and every old address that still works. Last reviewed: 2026-11-04.

---

## Site map

| Address | Page | Source file |
|---------|------|-------------|
| `/` | Home | `index.md` |
| `/about` | About me | `about.md` |
| `/projects/ai-skill/` | An AI skill for content design | `projects/ai-skill.md` |
| `/projects/digital-coach/` | A digital coach | `projects/digital-coach.md` |
| `/projects/teal-usability/` | Usability testing Teal | `projects/teal-usability.md` |
| `/projects/style-guide-game/` | Gamifying a style guide | `projects/style-guide-game.md` |
| `/projects-ai-headline-hero.html` | Headline Hero (game) | `projects-ai-headline-hero.html` |
| `/projects-doc-quest.html` | The Documentation Quest (game) | `projects-doc-quest.html` |
| `/assets/downloads/` | The skill's README | `assets/downloads/README.md` |
| `/assets/css/main.css` | The stylesheet | `assets/css/main.scss` and `_sass/` |

The navigation links to Home, About, and LinkedIn. Case studies are reached from the home page cards and from the "Read more of my case studies" list on each case study.

---

## Redirects

Each old address is listed under `redirect_from` in the page that replaced it. Both the folder form and the `.html` form work. The form without a trailing slash (such as `/projects-ai`) also works.

| Old address | Goes to |
|-------------|---------|
| `/projects-ai/` and `/projects-ai.html` | `/projects/ai-skill/` |
| `/projects-cabira/` and `/projects-cabira.html` | `/projects/digital-coach/` |
| `/projects-teal/` and `/projects-teal.html` | `/projects/teal-usability/` |
| `/projects-onboarding/` and `/projects-onboarding.html` | `/projects/style-guide-game/` |

All twelve forms (the eight above, plus the four without a trailing slash) were tested on the live site on 2026-11-04. Every one returned a page that sends the visitor to the right new address.

### How the redirects work

The `jekyll-redirect-from` plugin writes a small page at each old address. The page contains a meta refresh, a script, and a link. It is not an HTTP 301 redirect, because GitHub Pages cannot send one. Search engines generally follow a zero-second meta refresh, but a real 301 is stronger. See `known-issues.md`.

### Rules

1. Never remove a `redirect_from` entry once an address has been published.
2. When a page moves, list its old address under `redirect_from` in the same change.
3. Never reuse an old address for different content.

---

## Addresses that other places link to

| Link | Where it is used | Must keep working |
|------|------------------|-------------------|
| `/projects-ai-headline-hero.html` | UXfolio, onboarding case study ("Give it a try!") | Yes |
| `/projects-doc-quest.html` | UXfolio, onboarding case study ("Documentation Quest") | Yes |
| `https://github.com/cblocher/cblocher.github.io/blob/main/assets/downloads/README.md` | UXfolio, AI skill case study ("Try it") | Yes |
| `https://github.com/cblocher/cblocher.github.io/releases/download/v1.0/technical-content-design.zip` | `assets/downloads/README.md` | Yes. The v1.0 release exists, with the zip attached. |

Do not rename or move the files behind these links without updating UXfolio first.
