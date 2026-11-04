# Tech stack decisions

Each layer of the site: what was chosen, what else could have been chosen, and why. Last reviewed: 2026-11-04.

Decision IDs (D01 and so on) point to entries in `decision-log.md`, which holds the full reasoning. Where the table says "not evaluated," no alternative was compared in this project, and the choice stands because it was already in place.

---

## Summary table

| Layer | Choice | Alternatives | Why | Trade-off |
|-------|--------|--------------|-----|-----------|
| Hosting | GitHub Pages | Netlify, Cloudflare Pages, Vercel (not evaluated) | Already in use, free, publishes straight from the repo, no server to run | No custom headers, no real redirects, fixed plugin list |
| Site generator | Jekyll 3.x as run by GitHub Pages (D05) | Eleventy, Hugo, Astro (not evaluated) | Already in use, turns Markdown into pages, no build tooling to install | Older Jekyll version, older Sass engine |
| Content format | Markdown with front matter, converted by kramdown | HTML only, a CMS | Plain text that is easy to edit, review, and check with Vale | Markdown inside HTML blocks needs `markdown="1"` |
| Templates | Liquid layouts and includes (D06) | Copying markup into every page | One place to change the header, footer, and cards | Liquid syntax to learn |
| Styles | Sass partials built into one stylesheet, CSS custom properties (D10) | One large CSS file, Tailwind, a theme | One place to change the design, no inline styles | Jekyll's older Sass engine supports `@import` only, not `@use` |
| Theme | None (D09, D28) | The default Primer theme | The site has its own layouts and styles | None |
| Fonts | Google Fonts, loaded from Google | Self-hosted fonts, system fonts | Simple, and matches the original design | Every page makes a request to Google (see the privacy document) |
| Images | WebP and PNG, resized to 2000 px at most, originals kept untouched (D15) | Automatic image pipeline | Originals are never degraded, and web copies can be rebuilt | Web copies are made by hand |
| Thumbnails | 800 by 600 pixels, whole screen fitted, 1px border from CSS (D16) | Crop to fill, device-frame mockups | Nothing is cut off, and all four are the same size | Smaller screens inside the frame |
| Redirects | `jekyll-redirect-from` plugin (D07) | A server-side redirect file | Supported by GitHub Pages, old links keep working | Redirects are page-based (meta refresh), not HTTP 301 |
| Search engine files | `jekyll-sitemap` plugin, a hand-written `robots.txt`, and a custom 404 page (D33) | Writing the sitemap by hand | The sitemap updates itself as pages are added | The `.txt` file needs a forced `git add` because of `.gitignore` |
| SEO tags | `jekyll-seo-tag` plugin, with the tab title written by hand (D30) | Writing all tags by hand | Description, sharing tags, and canonical address with little code | The plugin's own title format was wrong for this site |
| Embeds | Figma frame, YouTube from `youtube-nocookie.com` (D17) | Screenshots, plain links | Matches UXfolio, stays current | Third-party requests, and they could not be tested in the build environment |
| Carousel | None; slides are stacked and testimonials are a list (D18) | Script-based carousel | Works with keyboard and screen readers, no script to maintain | Longer page |
| Accessibility checks | axe-core in a headless browser, WCAG 2.1 A and AA rules (D11) | Manual audit only | Repeatable, catches many problems quickly | Automated tools find only some problems |
| Writing check | Vale with one heading rule (D13, D14) | CSS capitalization, a Liquid filter | Fixes the text at its source | Catches only what a rule describes |
| Version control | Git on GitHub, work on branches, merge through a pull request | Editing on `main` | Safe changes, easy undo, full history | More steps for a small edit |
| Documentation | Markdown files in `docs/`, not published (this set) | A wiki, a docs site | Lives with the code and is reviewed with it | Readers need access to the repo |

---

## Notes on the less obvious choices

### Why the site follows UXfolio

Decisions D01 and D23 cover this. UXfolio is the portfolio Chris keeps current. The GitHub site is a second copy with its own address, the two game demos, and the downloadable skill. Under D23, when the two differ, UXfolio wins. The cost is that every edit made only on the GitHub side must also be made on UXfolio, or the next sync undoes it.

### Why the default theme is turned off (D28)

The GitHub Pages toolchain adds its default theme (Primer) when none is set, and publishes that theme's 136 KB stylesheet. This site has its own layouts and styles, so `_config.yml` sets `theme: null`. A test on the live site confirmed that the old `style.css` address now returns 404.

### Why headings are typed in sentence case, not styled by CSS (D13)

CSS changes only how text looks. Screen readers, the browser tab, search results, and link previews use the typed text. CSS also has no true Title Case or sentence case. So the case is typed correctly and Vale checks it. A single value, `--heading-case` in `_sass/_tokens.scss`, remains for display-only changes.

### Why the tab title is written by hand (D30)

The SEO plugin added the whole site description to the home page title and dropped the `|` from the site title. `_includes/head.html` now writes the `<title>` tag and tells the plugin not to (`{% seo title=false %}`).

### Why Vale was built from source (D14)

GitHub release downloads were blocked in the build environment, and PyPI offered only a third-party wrapper. Vale was built from its official source (`github.com/vale-cli/vale/v3`) through Go's module proxy.

---

## Choices worth revisiting

| Question | Why it might change |
|----------|---------------------|
| Self-host the fonts | Removes a third-party request on every page |
| Move to a different host | Would allow real redirects and custom headers |
| Add a staging preview | Lets branch changes be seen at an address before merging |
| Build the game pages' styles into the repo | Removes the dependency on Tailwind's CDN |
| Add an interactive carousel for the prototype slides | Shortens the digital coach page |
